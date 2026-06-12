---
title: "Getting a Dos Program to work for unbuntu"
date: 2009-03-06
forum: Installation &amp; Upgrades
---

### Post by BC_Kush420 on 2009-03-06
i dont know if this is the right section so post this if not someone tell me witch section i should post im lookin for help on how to get software to work for ubuntu.

anyways im trying to get a maphack for a video game to work on Ubuntu. the program runs in dos so i dont even know if it is goin to be possible but here is a link to the program 

[http://d2sector.net/downloads/index.php?dlid=96](http://d2sector.net/downloads/index.php?dlid=96)

its called EP lite


thnx

---

### Post by z.s.tar.gz on 2009-03-06
There is an app called DOSBOX, it is a dos emulator, works very well from my experience.

---

### Post by Jubward on 2009-03-06
Have you tried wine?

---

### Post by BC_Kush420 on 2009-03-06
yeah i tried wine nothin happened but ill try that other prog 4 sure

---

### Post by BC_Kush420 on 2009-03-06
where do i go to open DosBox now that i downloaded it? i cant find it anywhere?

---

### Post by z.s.tar.gz on 2009-03-06
```
sudo apt-get install dosbox
```
Paste and run in a terminal.
(Applications > Accessories)

Or, you can go to add/remove programs and search for it.

---

### Post by BC_Kush420 on 2009-03-06
whats that code mean??

sudo apt-get install dosbox


where do i enter it?

i alredy have the program downloaded i jus cant find where to open it

---

### Post by z.s.tar.gz on 2009-03-06
Ok, let me give you a crash course in package management.

In windows, if you want to install something, you search it in google and download an exe from from the developer's website.

In ubuntu (and most other linux distrobutions) you install things through a package management system, in this case apt-get.

The 'sudo' means "run as administrator", which you need to do since you will be installing programs.

The 'apt-get' is the program that downloads/installs programs.

The command modifier 'install' tells apt-get to install as opposed to remove a program.

The 'dosbox' part is what you want to install.

So, the question is: "Why do I have to use package management?" Two reasons:

1. Just sit back and let apt-get do the downloading and installing. No clicking 'next' 5 times.

2. Very low chance of viruses. Since the packages come from a repository, you have no adware or yahoo toolbars.

-----------------------------------------------

Moral of the story is, there is a program under Applications that does all that but even easier. It's called Add/Remove Software. Just search in the little box at the top, and check what you want installed.

---

### Post by yther on 2009-03-06
[SIZE="4"]Go.[/SIZE]  [Help docs for Ubuntu 8.10]("https://help.ubuntu.com/8.10/index.html")

[SIZE="4"]Read.[/SIZE]  [Adding & Removing Software]("https://help.ubuntu.com/8.10/add-applications/C/index.html")

[SIZE="4"]Learn.[/SIZE]  :)

---

### Post by BC_Kush420 on 2009-03-06
Thank u very much k i installed it Now where do i go to run it?? i cant find DOSBOX anywhere???


also this file is an EXE that opens a Dos window then runs in Dos?

u think theres any way to get this program to run on Ubuntu??

---

### Post by ve4cib on 2009-03-07
To run the program with Dosbox you'll need to open up a terminal (Accessories > Terminal)

Then you need to change directories to wherever you stored the .exe of the DOS program you want to run.  Let's say you stored it in /home/YOUR_USER_NAME/dos-programs/foo.exe

In the terminal type:

```
cd /home/YOUR_USER_NAME
```

Check that the .exe is here by executing the list command:

```
ls
```

You should see a list of every file in the current directory.  One of them should be foo.exe.

Now it's time to run it with DOSBOX.  Still in the terminal type:

```
dosbox foo.exe
```

and press enter.  The program should run just fine now.


___________________

The dosbox executable that you installed is located in your /usr/bin/ directory.  Specifically it's /usr/bin/dosbox.  Pretty much ever executable program in Ubuntu is in /usr/bin or /usr/local/bin.  Games are usually found in /usr/games or /usr/local/games.

The exact location of the executables doesn't really matter on Linux; the system maintains what's called the PATH variable.  This is basically a list of standard directories where executables are found.  When you run a program from the command-line (like "dosbox") the computer looks in every directory in PATH for an executable called "dosbox".  If it finds one it executes that.  If it can't find anything it'll tell you that the command was not found.

PATH works when you're creating menu launchers too.  Right-click on the main menu and go to the Edit Menus option.  There's a button that will let you add a new launcher.  In the textbox labeled "command" you (generally) don't need to specify exactly where an executable is.  Just its name.  The computer automagically figures out where it is by looking through PATH.

---

