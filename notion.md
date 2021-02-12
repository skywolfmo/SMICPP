# C++

Status: Waiting Test
Type: Computer Science

### Planning:

[C++ Plan](https://www.notion.so/fb7ff99279c041f39f5903c09303dafc)

### Quick Notes

- OOP
    - Encapsulation

        Abstraction means, showcasing only the required things to the outside world while hiding the details. Continuing our example, Human Being's can talk, walk, hear, eat, but the details are hidden from the outside world. We can take our skin as the Abstraction factor in our case, hiding the inside mechanism.

    - Inheritance

        Considering HumanBeing a class, which has properties like hands, legs, eyes etc, and functions like walk, talk, eat, see etc. Male and Female are also classes, but most of the properties and functions are included in HumanBeing, hence they can inherit everything from class HumanBeing using the concept of Inheritance.

    - Polymorphism

        Polymorphism is a concept, which allows us to redefine the way something works, by either changing how it is done or by changing the parts using which it is done. Both the ways have different terms for them.

        If we walk using our hands, and not legs, here we will change the parts used to perform something. Hence this is called **Overloading**.

        And if there is a defined way of walking, but I wish to walk differently, but using my legs, like everyone else. Then I can walk like I want, this will be called as **Overriding**.

    - Abstraction

        The way of representing things in our real life, everything we see even if it was made of different material we try to find a simple representation of it. An example of that is the fact of finding different types of dogs, but in the end, we try to find which representation we can give them in order to represent them.

    - Class

        Here we can take Human Being as a class. A class is a blueprint for any functional entity which defines its properties and its functions. Like Human Being, having body parts, and performing various actions.

    - Objects

        My name is Abhishek, and I am an instance/object of class Male. When we say, Human Being, Male or Female, we just mean a kind, you, your friend, me we are the forms of these classes. We have a physical existence while a class is just a logical definition. We are the objects.

    - Exception Handling

        Exception handling is a feature of OOP, to handle unresolved exceptions or errors produced at runtime.

- Storage
    - Global variables

        These are defined at the starting , before all function bodies and are available throughout the program.

        ```cpp
        using namespace std;
        int globe;      // Global variable
        void func();
        int main()
        {
            .....
        }
        ```

    - Local variables

        They are defined and are available within a particular scope. They are also called **Automatic variable** because they come into being when scope is entered and automatically go away when the scope ends.

        The keyword **auto** is used, but by default all local variables are auto, so we don't have to explicitly add keyword auto before variable dedaration. Default value of such variable is **garbage**.

    - Register variables

        This is also a type of local variable. This keyword is used to tell the compiler to make access to this variable as fast as possible. Variables are stored in registers to increase the access speed.

        But you can never use or compute **address of register variable** and also , a register variable can be declared only within a **block**, that means, you cannot have global or static register variables.

    - Static variables

        Static variables are the variables which are initialized & allocated storage only once at the beginning of program execution, no matter how many times they are used and called in the program. A static variable retains its value until the end of program.

        ```cpp
        void fun()
        {
            static int i = 10;
            i++;
            cout << i;
        }
        int main()
        {
            fun();      // Output = 11
            fun();      // Output = 12
            fun();      // Output = 13
        }
        ```

        As, `i` is static, hence it will retain its value through function calls, and is initialized only once at the beginning.

        Static specifiers are also used in classes, but that we will learn later.

    - Extern variables

        This keyword is used to access variable in a file which is declared & defined in some other file, that is the existence of a global variable in one file is declared using extern keyword in another file.

        ![https://www.studytonight.com/cpp/images/extern-keyword.gif](https://www.studytonight.com/cpp/images/extern-keyword.gif)

- Functions
    - Call by Address (*Pointer)

        n this we pass the address of the variable as arguments. In this case the formal parameter can be taken as a reference or a pointer, in both the case they will change the values of the original variable.

        ```
        void calc(int *p);

        int main()
        {
            int x = 10;
            calc(&x);     // passing address of x as argument
            printf("%d", x);
        }

        void calc(int *p)
        {
            *p = *p + 10;
        }
        ```

    - Call by Value

        In this calling technique we pass the values of arguments which are stored or copied into the formal parameters of functions. Hence, the original values are unchanged only the parameters inside function changes.

        ```cpp
        void calc(int x);

        int main()
        {
            int x = 10;
            calc(x);
            printf("%d", x);
        }

        void calc(int x)
        {
            x = x + 10 ;
        }
        ```

    - Cal by Reference (&)

        In this calling technique we pass the reference of the arguments which apply all the changes to the passed value, any change applied will affect the original value of the argument.

        ```cpp
        void calc(int &x);

        int main()
        {
            int x = 10;
            calc(x);
            printf("%d", x);
        // Will print 20;
        }

        void calc(int &x)
        {
            x = x + 10 ;
        }
        ```

        It is used as a replacement to the call by value if used with the *const* prefix like:

        ```cpp
        void calc(const int &x);
        ```

- Reference vs Pointers

    References are often confused with pointers but three major differences between references and pointers are −

    - You cannot have NULL references. You must always be able to assume that a reference is connected to a legitimate piece of storage.
    - Once a reference is initialized to an object, it cannot be changed to refer to another object. Pointers can be pointed to another object at any time.
    - A reference must be initialized when it is created. Pointers can be initialized at any time.
- Class
    - Access Control
        - Public Access Modifier

            Public, means all the class members declared under **public** will be available to everyone. The data members and member functions declared public can be accessed by other classes too. Hence there are chances that they might change them. So the key members must not be declared public.

            ```cpp
            class PublicAccess
            {
                // public access modifier
                public:   
                int x;            // Data Member Declaration 
                void display();   // Member Function decaration
            }
            ```

        - Private Access Modifier

            Private keyword, means that no one can access the class members declared **private**, outside that class. If someone tries to access the private members of a class, they will get a **compile time error**. By default class variables and member functions are private.

            ```cpp
            class PrivateAccess
            {
                // private access modifier
                private:   
                int x;            // Data Member Declaration 
                void display();   // Member Function decaration
            }

            ```

        - Protected Access Modifier

            Protected, is the last access specifier, and it is similar to private, it makes class member inaccessible outside the class. But they can be accessed by any subclass of that class. (If class A is **inherited** by class B, then class B is subclass of class A. We will learn about inheritance later.)

            ```cpp
            class ProtectedAccess
            {
                // protected access modifier
                protected: 
                int x;            // Data Member Declaration 
                void display();   // Member Function decaration
            }

            ```

    - Functions And Methods
        - Member Functions

            ```cpp
            class Cube
            {
                public:
                int side;
                int getVolume()
                {
                    return side*side*side;      //returns volume of cube
                }
            };
            ```

            ```cpp
            class Cube
            {
                public:
                int side;
                int getVolume();
            }

            // member function defined outside class definition
            int Cube :: getVolume()
            {
                return side*side*side;
            }
            ```

        - Friend Functions

            ```cpp
            class WithFriend
            {
                int i;
                public:
                friend void fun(); // global function as friend
            };

            void fun()
            {
                WithFriend wf;
                wf.i=10;  // access to private data member
                cout << wf.i;
            }

            int main()
            {
                fun(); //Can be called directly
            }
            ```

            ```cpp
            class Other
            {
                void fun();
            };

            class WithFriend
            {
                private:
                int i;
                public:
                void getdata();  // Member function of class WithFriend
                
                // making function of class Other as friend here
                friend void Other::fun();   
                
                // making the complete class as friend
                friend class Other;  
            };
            ```

            Friend Functions is a reason, why C++ is not called as a pure Object Oriented language. Because it violates the concept of Encapsulation.

        - Inline Functions

            Inline functions are actual functions, which are copied everywhere during compilation, like preprocessor macro, so the overhead of function calling is reduced. All the functions defined inside class definition are by default inline, but you can also make any non-class function inline by using keyword **inline** with them.

            For an inline function, declaration and definition must be done together. For example,

            ```
            inline void fun(int a) 
            { 
                return a++; 
            }
            ```

            # **Some Important points about Inline Functions**

            1. We must keep inline functions small, small inline functions have better efficiency.
            2. Inline functions do increase efficiency, but we should not make all the functions inline. Because if we make large functions inline, it may lead to **code bloat**, and might affect the speed too.
            3. Hence, it is adviced to define large functions outside the class definition using scope resolution `::` operator, because if we define such functions inside class definition, then they become inline automatically.
            4. Inline functions are kept in the Symbol Table by the compiler, and all the call for such functions is taken care at compile time.

            # **Limitations of Inline Functions**

            1. Large Inline functions cause Cache misses and affect performance negatively.
            2. Compilation overhead of copying the function body everywhere in the code on compilation, which is negligible for small programs, but it makes a difference in large code bases.
            3. Also, if we require address of the function in program, compiler cannot perform inlining on such functions. Because for providing address to a function, compiler will have to allocate storage to it. But inline functions doesn't get storage, they are kept in Symbol table.
        - Overloading

            ```
            // first definition
            int sum(int x, int y=0)
            {
                cout<< x+y;
            }

            // second overloaded defintion
            double sum(double x, double y)
            {
                cout << x+y;
            }

            int main()
            {
                sum (10,20);
                sum(10.5,20.5);
            }
            ```

        - Overriding

            Check inheritance

- Inheritance
    - Example

        ```cpp
        class Animal
        { 
            public:
            int legs = 4;
        };

        // Dog class inheriting Animal class
        class Dog : public Animal
        { 
            public:
            int tail = 1;
        };

        int main()
        {
            Dog d;
            cout << d.legs;
            cout << d.tail;
        }
        ```

    - Visibility

        [Table showing all the Visibility Modes](https://www.notion.so/a926b086c93f4c2b8fb5796e5fa7abee)

        - Public Inheritance

            This is the most used inheritance mode. In this the protected member of super class becomes protected members of sub class and public becomes public.

            ```cpp
            class Subclass : public Superclass
            ```

        - Private Inheritance

            In private mode, the protected and public members of super class become private members of derived class.

            ```cpp
            class Subclass : Superclass   // By default its private inheritance
            ```

        - Protected Inheritance

            In protected mode, the public and protected members of Super class becomes protected members of Sub class.

            ```cpp
            class subclass : protected Superclass
            ```

    - Types of Inheritance
        - Single Inheritance

            In this type of inheritance one derived class inherits from only one base class. It is the most simplest form of Inheritance.

            ![https://www.studytonight.com/cpp/images/single-inheritance.jpg](https://www.studytonight.com/cpp/images/single-inheritance.jpg)

        - Multiple Inheritance

            In this type of inheritance a single derived class may inherit from two or more than two base classes.

            ![https://www.studytonight.com/cpp/images/multiple-inheritance.jpg](https://www.studytonight.com/cpp/images/multiple-inheritance.jpg)

        - Hierarchical Inheritance

            In this type of inheritance, multiple derived classes inherits from a single base class.

            ![https://www.studytonight.com/cpp/images/hierarchical-inheritance.jpg](https://www.studytonight.com/cpp/images/hierarchical-inheritance.jpg)

        - Multilevel Inheritance

            In this type of inheritance the derived class inherits from a class, which in turn inherits from some other class. The Super class for one, is sub class for the other.

            ![https://www.studytonight.com/cpp/images/multilevel-inheritance.jpg](https://www.studytonight.com/cpp/images/multilevel-inheritance.jpg)

        - Hybrid (Virtual) Inheritance

            Hybrid Inheritance is combination of Hierarchical and Mutilevel Inheritance.

            ![https://www.studytonight.com/cpp/images/hybrid-inheritance.jpg](https://www.studytonight.com/cpp/images/hybrid-inheritance.jpg)

    - Constructor Call

        # **Constructor call in Multiple Inheritance in C++**

        Its almost the same, all the Base class's constructors are called inside derived class's constructor, in the same order in which they are inherited.

        ```cpp
        class A : public B, public C ;

        ```

        In this case, first class B constructor will be executed, then class C constructor and then class A constructor.

- Polymorphism
    - Definition

        Polymorphism means having multiple forms of one thing. In inheritance, polymorphism is done, by method overriding, when both super and sub class have member function with same declaration bu different definition.

- Operators Overriding

    ```cpp
    #include<iostream.h>
    #include<conio.h>
    class Time
    {
        int hr, min, sec;
        public:
        // default constructor
        Time()
        {
            hr=0, min=0; sec=0;
        }
        
        // overloaded constructor
        Time(int h, int m, int s)
        {
            hr=h, min=m; sec=s;
        }
        
        // overloading '<<' operator
        friend ostream& operator << (ostream &out, Time &tm); 
    };

    // define the overloaded function
    ostream& operator << (ostream &out, Time &tm)
    {
        out << "Time is: " << tm.hr << " hour : " << tm.min << " min : " << tm.sec << " sec";
        return out;
    }

    void main()
    {
        Time tm(3,15,45);
        cout << tm;
    }
    ```

    ```cpp
    class Time
    {
        int hr, min, sec;
        public:
        // default constructor
        Time()
        {
            hr=0, min=0; sec=0;
        }
        
        // overloaded constructor
        Time(int h, int m, int s)
        {
            hr=h, min=m; sec=s;
        }
        
        //overloading '==' operator
        friend bool operator==(Time &t1, Time &t2);
    };

    /* 
        Defining the overloading operator function
        Here we are simply comparing the hour, minute and
        second values of two different Time objects to compare
        their values
    */
    bool operator== (Time &t1, Time &t2)
    {
        return ( t1.hr == t2.hr && t1.min == t2.min && t1.sec == t2.sec );
    }

    void main()
    {
        Time t1(3,15,45);
        Time t2(4,15,45);
        if(t1 == t2)
        {
            cout << "Both the time values are equal";
        }   
        else 
        {
            cout << "Both the time values are not equal";
        }
    }
    ```

---