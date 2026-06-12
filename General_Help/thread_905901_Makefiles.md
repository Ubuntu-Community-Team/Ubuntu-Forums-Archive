---
title: "Makefiles"
date: 2008-08-30
forum: General Help
---

### Post by Xarver on 2008-08-30
Hi, I'm trying to make a makefile so 
when I go to the directory Coding in the terminal,
and enter make, it will run the program Level.
Here's what it's doing:
```

Action: Run terminal, enter
cd Coding

Action: Then enter 
make

Error It Says:
Makefile:1: *** missing separator.  Stop.

```
**The Makefile:**
```

g++ level.cpp -o Level
./Level

```

What's wrong???
----

But, what I think what would be easier is if someone could teach
me how to make a Makefile so when you double click the 
Level executable it would run the program automatically.

Any help appreciated!!!

P.S. There is nothing wrong with the C++ code... ;)

C++ Source
```

#include <iostream>
using namespace std;

int main()
{
	char entry;
	enum level {ONE = 100, TWO = 250, THREE = 500, FOUR = 900, FIVE = 1650, SIX = 2650, SEVEN = 3950, EIGHT = 5450, NINE = 7000};
	int myLevel = ONE;
	int myEXP = 0;
	cout << "Enter E To Up 50 Exp.\nEnter Q To Quit.\n";
	do {
		cout << "\nEntry: ";
		cin >> entry;
		if(entry == 'E' || entry == 'e') 
		{ 
			cout << myEXP << " + 50 = ";
			myEXP = myEXP + 50; cout << myEXP;
			cout << "\nYou need ";
			if(myLevel = ONE)
			{
				cout << (TWO - myEXP) << " EXP to Get to Level 2!\n";
				cin.ignore(cin.rdbuf()->in_avail() + 1);
			}else if(myLevel = TWO)
			{
				cout << (THREE - myEXP) << " EXP to Get to Level 3!\n";
				cin.ignore(cin.rdbuf()->in_avail() + 1);
			}
		}else if(entry == 'Q' || entry == 'q') { return 0; }
		else {
			cout << "Invalid Entry...\n";
			cin.ignore(cin.rdbuf()->in_avail() + 1);
		}
		
		if(myEXP == 250) { myLevel = TWO; cout << "Level 2!\n"; }
		
	}while(entry != 'Q' || entry != 'q');
	
	return 0;
}

```

//W.I.P. Code\\

---

### Post by monkeyking on 2008-08-31
I don't understand your Makefile.

My Makefiles look like

```

CC=G++

all: myMainFile

file3.o: file3.cpp file3.h
        ${CC} -c file3.cpp

myMainFile:file1.cpp file1.h file2.cpp file3.o
        ${CC} file1.cpp file3.o 

```

Remember you need to use a TAB on the line with ${CC}

Furhermore Makefiles are used for building your application.
Not some smart way of starting it.

If you want the process to be optimized,
you are better of making a wrapper bash script,
that calls make and then executes it.
This you can do easily.

---

### Post by Xarver on 2008-08-31
Mind explaining?
I'm a whole newbie to thing,
and I don't know how that makefile works.
Can you give me a link to some sort of tutorial, please?

:)

---

### Post by mike2357 on 2008-08-31
As monkeyking said, make and makefiles are for building applications.  For instance, if your application is built from 100 different compiled source code files and one of them changes, "make" will figure out which one changed and just re-compile it rather than all 100.  It uses dependencies, so that files ending in ".o" depend on source code files, which in monkeyking's example, end in ".cpp".

Typing "man make" is a good place to start.  You can type "gnu make manual" in a search engine for more extensive information.

The first rule I learned about makefiles was to avoid creating one from scratch.  It's a lot easier to make modifications to one that works.

For an example of a simple one:

[http://www.gnu.org/software/make/manual/make.html#Rule-Introduction]("http://www.gnu.org/software/make/manual/make.html#Rule-Introduction")

---

### Post by Xarver on 2008-08-31
Thanks, I'll search that on google and check out that link.
This topic will be solved as soon as I figure this out. :)

---

### Post by monkeyking on 2008-08-31
your makefile, this should be in your dir with your program
```

all:DOEVERYTHING

DOEVERYTHING: level.cpp
     g++ level.cpp -o Level

```

I'me having troubles understanding what you want to accomplish.
Can you explain what you want to do.

---

