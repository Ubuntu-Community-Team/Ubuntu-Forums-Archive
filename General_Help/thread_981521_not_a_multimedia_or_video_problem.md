---
title: "not a multimedia or video problem"
date: 2008-11-13
forum: General Help
---

### Post by stealthc on 2008-11-13
gee thanks for dumping my issue in a less busy forum.
This is more of a general issue with executing the installer.
My computer doesn't recognize .run extension.
Not like it did with my last install of the exact same version of ubuntu.
So I don't know what's going on but I'd sure as heck like to know how I can fix the file associations so that a .run package actually runs.
By default my computer kept trying to open it with gedit.  This is WRONG.  This file should be capable of running.
I tried to run it from terminal and it doesn't know how to do that either.
Please don't move my post into an unrelated section again.  It doesn't matter if it's a game, this has nothing to do with the fact that it's a game, it's ANY .run file I try to run that won't work.

---

### Post by binbash on 2008-11-13
@terminal
chmod +x filename.run
sudo sh filename.run (or sh filename.run Or ./filename.run)

Edit : BE SURE you are in the folder which contains .run file else sudo sh /home/blabla/blabla/filename.run etc)

---

### Post by taurus on 2008-11-13
First, make sure you are in the same directory of the file that you want to run.  Assuming it's in ~/Desktop (or $HOME/Desktop).

Applications -> Accessories -> Terminal
```
cd ~/Desktop
```
Then, you need to change permission so it can be executed, replacing filename.run with the actual name of the program.

```
chmod 755 filename.run
```
Now, just run it.

```
./filename.run
```

---

### Post by stealthc on 2008-11-13
> **taurus said:**
> First, make sure you are in the same directory of the file that you want to run.  Assuming it's in ~/Desktop (or $HOME/Desktop).

Applications -> Accessories -> Terminal
```
cd ~/Desktop
```
Then, you need to change permission so it can be executed, replacing filename.run with the actual name of the program.

```
chmod 755 filename.run
```
Now, just run it.

```
./filename.run
```

running it "filename.run" while in the Desktop directory (where the file is) using terminal results in "command not found".

---

### Post by taurus on 2008-11-13
Where is that file located and what is the name of that file?  I hope you didn't run it by using _filename.run_ because _filename.run_ is just an example, okay.

---

### Post by stealthc on 2008-11-13
> **binbash said:**
> @terminal
chmod +x filename.run
sudo sh filename.run (or sh filename.run Or ./filename.run)

Edit : BE SURE you are in the folder which contains .run file else sudo sh /home/blabla/blabla/filename.run etc)

This worked on wolfenstien enemy territory and I got it to install fine.
But it didn't work on the quake wars .run file, I get an error from the command saying:
ETQW-demo-client-1.1-full.r5.x86.run: 1: Syntax error: "(" unexpected


though what seemed to have fixed it was to use sudo filename.run
having sh in there prevented it from working.

Very weird.
And there's still the issue why it wouldn't just let me open the file from the desktop and the installer would run, like it did the first time.  I sure wish I could fix that so I don't have to use the terminal whenever I want to install a .run file.

---

### Post by binbash on 2008-11-13
> **stealthc said:**
> This worked on wolfenstien enemy territory and I got it to install fine.
But it didn't work on the quake wars .run file, I get an error from the command saying:
ETQW-demo-client-1.1-full.r5.x86.run: 1: Syntax error: "(" unexpected


though what seemed to have fixed it was to use sudo filename.run
having sh in there prevented it from working.

Very weird.
And there's still the issue why it wouldn't just let me open the file from the desktop and the installer would run, like it did the first time.  I sure wish I could fix that so I don't have to use the terminal whenever I want to install a .run file.

try with ./filename.run
you have to use terminal sorry.(tho the installer may come with gui and you will see that after giving the command @ terminal)

---

