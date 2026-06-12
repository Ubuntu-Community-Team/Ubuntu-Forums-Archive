---
title: "compiling from terminal"
date: 2008-10-02
forum: General Help
---

### Post by lapishc on 2008-10-02
I am VERY new to the Linux world and have a collection of programs that I need to compile for use in Matlab.  The programs are a collection of C++ routines that once compiled will run in Matlab.  The directions for the use of these programs asks me to use

'execute compile.sh'

From reading the script(compile.sh) it looks like it compiles all of the routines and places them in a designated folder.

Where would I run this command from?? I have tried it from Matlab and from Terminal bit nothing seems to work....ANY SUGGESTIONS???

THANKS!

---

### Post by ibuclaw on 2008-10-02
Yeah, it's pretty straightforward.

First, I recommend that you get the build-essential package first.
```
sudo apt-get install build-essential
```
And to "execute compile.sh", you can achieve this with any of the following.
```
./compile.sh
```
The above works with all executable files.

The **./** part tells the terminal to run an executable file from within the directory you are in.

While:
```
sh compile.sh
```
Will only work with ".sh" files.

[NOTE]
You may have to run the installation using "**sudo**".

Again, this is straightforward. Just begin the command with "sudo"
```
sudo ./compile.sh
```
And enter in your password when prompted.

Regards
Iain

---

### Post by lapishc on 2008-10-02
Thanks a lot, 

Just for clarity, the difference btw './' and 'sh' is that 'sh' runs shell executable commands only...while './' will run all commands that are executable?  Just two ways separate ways of doing the same thing...right?

Thanks for your reply.

---

### Post by ibuclaw on 2008-10-02
For .sh files, yes. They do the exact same thing.

If you were to try that on a .py file, provided that the contents of the file had python source code inside, then it would fail to run, or throw errors at you.

Using **./** is the way to run files in Linux.

Regards
Iain

---

### Post by cariboo on 2008-10-02
the ./ is to indicate that you are in the same directory as the script you are trying to run,

Jim

---

### Post by mindoms on 2008-10-02
the file should be marked executeable, though.
(thats a permission thing)
```

chmod +x compile.sh
./compile.ch

```

---

### Post by SuperSonic4 on 2008-10-02
And don't forget to cd to the directory:

```
cd ~/Desktop
``` if it's stored on the desktop

---

