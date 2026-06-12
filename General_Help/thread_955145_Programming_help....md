---
title: "Programming help..."
date: 2008-10-21
forum: General Help
---

### Post by Shiv4m on 2008-10-21
I want to learn programming languages especially C++, is there any way to get visual basic or any programming software onto Ubuntu?

---

### Post by DGortze380 on 2008-10-21
> **Shiv4m said:**
> I want to learn programming languages especially C++, is there any way to get visual basic or any programming software onto Ubuntu?

ubuntu comes with gcc installed (if for whatever reason it's not):

```

sudo apt-get install gcc

```

Type your C program into a plain text file.

use the command line to compile
```

g++ myFile.cpp -o myFile

```

then run it

```

./myFile

```

For starting out, that's all you need. If you want a full blown IDE, just search the programming section here for recommendations.

---

### Post by Shiv4m on 2008-10-21
Thanks this is C++ right?

---

### Post by DGortze380 on 2008-10-21
> **Shiv4m said:**
> Thanks this is C++ right?

Right. 

C++ is a compiled language. Write the source in a plain text file. Use gcc to compile it into an executable. Run the executable. Simple as that (well, for the basics anyways).

I would suggest looking at: [http://www.cprogramming.com/](http://www.cprogramming.com/)

---

### Post by Shiv4m on 2008-10-21
Ok I run "sudo apt-get install gcc' and it says I already have it, but I don't see it anywhere? 

How can I get it?

---

### Post by DGortze380 on 2008-10-21
> **Shiv4m said:**
> Ok I run "sudo apt-get install gcc' and it says I already have it, but I don't see it anywhere? 

How can I get it?

It's a command line utility, it should be installed by default. Copy and paste this into a text file on your desktop called helloworld.cpp

```

#include <iostream>

using namespace std;

int main()
{

cout << "Hello World" << endl;

return 0;
}

```

then open a terminal, navigate to the desktop and type

```

g++ helloworld.cpp -o helloworld

```

that takes the source file helloworld.cpp and compiles it into the binary executable helloworld.
then to run it:

```

./helloworld

```

---

### Post by Shiv4m on 2008-10-21
Lol I'm so lost, I tried "cd Desktop" to navigate to it is that correct?

---

### Post by DGortze380 on 2008-10-21
> **Shiv4m said:**
> Lol I'm so lost, I tried "cd Desktop" to navigate to it is that correct?

yes, that's right.

---

### Post by Shiv4m on 2008-10-21
This is what I get:

[IMG]http://img508.imageshack.us/my.php?image=screenshotshivamshivamlwm4.png[/IMG]
[http://img508.imageshack.us/my.php?image=screenshotshivamshivamlwm4.png](http://img508.imageshack.us/my.php?image=screenshotshivamshivamlwm4.png)

And yes helloworld.ccp is created.

---

### Post by xphlo on 2008-10-21
> 
g++ myFile.cpp -o myFile

Thats the command line way. If you are new to c++, using g++ from the command line (make files for that matter) will give you more power, and will deepen your understanding with time.

You can get c++ IDE's ;Anjuta, Eclipse-C++ (eclipse with CDE plugin).

The IDEs can handle makefiles, linking, compiling for you, but will allow you to glance over these important lower-level facilities. These are fundamental to linux/c++, and knowing how they work together is a very good thing.

I would start with small projects, use a text editor (gedit, kate), and learn to use g++ from the command line. Once you begin to understand how things work together, then you can choose to move to an IDE or stick with your text editor. If you like text editors, and want to move past gedit/kate, check out vim or emacs. Vim and emacs take time to get familiar with, but can be very powerful once you get into the groove.

Personally, I dont like most IDE's. I use vim and a couple of terminals for nearly all of my programming.

Good Place to start is Google, but an alternative is ...
[http://www.yolinux.com/TUTORIALS/LinuxTutorialC++.html](http://www.yolinux.com/TUTORIALS/LinuxTutorialC++.html)

---

### Post by DGortze380 on 2008-10-21
> **Shiv4m said:**
> This is what I get:

[IMG]http://img508.imageshack.us/my.php?image=screenshotshivamshivamlwm4.png[/IMG]
[http://img508.imageshack.us/my.php?image=screenshotshivamshivamlwm4.png](http://img508.imageshack.us/my.php?image=screenshotshivamshivamlwm4.png)

And yes helloworld.ccp is created.

cpp

as in c plus plus

not ccp

---

### Post by Le-Froid on 2008-10-21
To compile C++ programs go to the directory of the file (for example, if its in /home/Shiv4m/Desktop, type cd $HOME/Desktop) and type "g++ <filename> <applications name>", then run the application by typing "./<application name>" in a terminal.

For C programs type "gcc <filename> <application>"

For C# programs type "mcs <filename> <application>"

For anything else you can check on synaptic[the package manager] and it should give the name of the compiler.

edit: according to your picture, the file isn't in your desktop folder.

---

### Post by Shiv4m on 2008-10-21
Ok thanks a lot I need to find some tutorials on how to start all this :P

---

