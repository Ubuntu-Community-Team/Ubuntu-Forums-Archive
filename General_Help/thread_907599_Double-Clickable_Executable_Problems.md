---
title: "Double-Clickable Executable Problems"
date: 2008-09-01
forum: General Help
---

### Post by Xarver on 2008-09-01
Hi, I found out how to make a double clickable executable.
The only problem is, I don't know what program should open it.
I tried making it run in the Autorun Prompt but it just opens and closes.
I'm trying to run a C++ application compiled with g++

Any help, please?

---

### Post by Xarver on 2008-09-07
I really want this solved, please? :)

---

### Post by mike2357 on 2008-09-07
The problem may be that you're trying your C++ program, which may be non-GUI, in a GUI environment such as Gnome.

Try running your program by opening a Terminal Window (Applications -> Accessories -> Terminal) and typing in your program name.  If the name of the program is "testing", you may need to type ./testing  

The ./ means to run in the current directory.  Otherwise, give type in a full path name, such as /home/myname/testing

---

### Post by MaxIBoy on 2008-09-07
[SIZE="1"]Right click on the file, go to properties, then permissions, select "allow executing of the file as a program," tell us if it doesn't work.
[/SIZE]

EDIT: Nevermind, that other guy is right. Run it from the terminal.


If you must have it double-clickable, create a textfile in the same program as your program, name it Run-It.sh, and copy and paste the following into it:
```
!# /bin/bash
./NameOfYourProgram
```

Then double-click the .sh file and select "run in terminal."

---

### Post by Xarver on 2008-09-08
I know how to run it in the terminal, just so you know.
Just want it double clickable.

And MaxIBoy, Thanks!
It works perfect.

Shell script is awesome.
I'll learn it now. :)

```

!# /bin/bash\

g++ helloworld.cpp -o HelloWorld
./HelloWorld

```

---

### Post by ryanhaigh on 2008-09-08
You won't be able to run the application (and see it) without openning a terminal first, this means you can't just double-click it. What you can do is create a launcher to open a terminal and then run your app.

Right click on the desktop create launcher, use whatever you want for name etc, but for the command use something like:
```
gnome-terminal -x "/usr/bin/nano" 
```
Replacing /usr/bin/nano with the path to your executable.

---

