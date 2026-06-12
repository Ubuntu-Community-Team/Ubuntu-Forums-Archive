---
title: "preventing programs from using all resources"
date: 2008-09-22
forum: General Help
---

### Post by Ulrik04 on 2008-09-22
A friend send me a program containing a neverending while(true){} loop, and it made my system totally crash, I could move around the mouse, but i couldn't do anything else, not even ctrl+alt+backspace or any other. Therefore i thought, is there a way to prevent a program from using all system resources? In Windows, a while(true){} loop just makes the program crash, why doesn't it in Ubuntu? And it's not only with these kind of programs, I've also tried normal programs crashing the whole system. Is there any way?

---

### Post by strider1551 on 2008-09-22
Sounds like a good friend you got there!  You could adjust the niceness of the program.  For example:
```

nice 19 ./program_that_sucks.sh

```

Some reference:
[Manipulate process priority]("http://blogs.techrepublic.com.com/opensource/?p=140")
[man nice]("http://www.manpagez.com/man/1/nice/")
[man renice]("http://www.manpagez.com/man/8/renice/")

As far as everything crashing, it's been a while since I've been in that situation myself.  In fact, I find Linux to handle crashed process far better than Windows, but that's just my own experience.  Anyway, hopefully you can drop to a terminal with Ctrl+Alt+F1 and kill the process, or restart gnome, or whatever (Ctrl+Alt+F7 to get back).

---

### Post by medic2000 on 2008-09-22
No,no,no...There are many ways:

1-) In Ubuntu it's just far more flexible than windows. First searh for "kill and killall" command. Also you can use "top" terminal program to kill the processes.

2-)Also you can add a applet to panel that you can click to it,then to the non-responding program you can kill it insantly. No waiting like windows.(Note: Clicking the close button of program several times gets you the "force quit" window also) 

3-)There is a "system monitor" program similar to "ctrl+alt+delete" program in Windows. You can find it in System-Administration. 

4-)And also if the graphical system fails completely meaning that you can't click any button, can't move the mouse, black screen etc... then you can restart the graphical server(X-server) by pressing the shortcut "ctrl+alt+backspace". This will only restart the X-server.Your main system will not be touched.(Not that every part of Linux system runs seperately-when something happens just restart that part-This is a huge advantage that Windows doesn't have and will never have)

5-)For another option like strider said you can switch to a another terminal ctrl+alt+F1(F2,F3,F4,F5,F6) and kill the process then return your terminal(ctrl+alt+F7)

Never forget that in Windows environment so many programs can reach the "kernel-the heart of system" and when a program fails it drifts kernel so the entire system to death.In Linux kernel is moddable,just remove the failed mode or program and kernel will continue it's work.

---

### Post by spibou on 2008-09-22
> **Ulrik04 said:**
> A friend send me a program containing a neverending while(true){} loop, and it made my system totally crash, I could move around the mouse, but i couldn't do anything else, not even ctrl+alt+backspace or any other. Therefore i thought, is there a way to prevent a program from using all system resources? In Windows, a while(true){} loop just makes the program crash, why doesn't it in Ubuntu? And it's not only with these kind of programs, I've also tried normal programs crashing the whole system. Is there any way?

In what language was the programme written? I just tried
```
int main(void) { while (1) ; return 0 ; }
```
It used up 97% of CPU time but it didn't affect the responsiveness of the computer in the slightest. Perhaps your friend sent you a fork bomb (in which case there's more to it than **while(true){}**) or your computer has some other problem. I'm also surprised to hear that a programme with a neverending loop crashes in Windows, can anyone else confirm this?

---

### Post by Ulrik04 on 2008-09-23
the code was in C++ and
```

int i = 1;
while(i == 1){
std::cout << "\a";
}

```

And I know about the ways to quit unresponding programs, but this was really freezing the system, making me unable to do anything at all...

---

### Post by medic2000 on 2008-09-23
the code was in C++ and
```

int i = 1;
while(i == 1){
std::cout << "\a";
}

```

> **Ulrik04 said:**
> And I know about the ways to quit unresponding programs, but this was really freezing the system, making me unable to do anything at all...

Pardon me for the wrong answer.It was 4 at late night :)

---

