---
title: "Synaptic says it's installed, but I don't see it"
date: 2009-08-10
forum: Installation &amp; Upgrades
---

### Post by traynor on 2009-08-10
Hi - I'm brand new to Ubuntu (long time in windows) and am trying to install a specific ftp program. Synaptic says it's installed but I don't see it anywhere in my menus, and it's not available in the list of "add/remove" applications in the menu.

I've seen this for a couple of other programs in the Synaptic installer also. Am I missing a step?

Thanks

---

### Post by raymondh on 2009-08-10
> **traynor said:**
> Hi - I'm brand new to Ubuntu (long time in windows) and am trying to install a specific ftp program. Synaptic says it's installed but I don't see it anywhere in my menus, and it's not available in the list of "add/remove" applications in the menu.

I've seen this for a couple of other programs in the Synaptic installer also. Am I missing a step?

Thanks

Try alt + F2 and type in the program name and run.  Some programs require that it be ran first.  Compiz, I think, is like that.

---

### Post by snowpine on 2009-08-10
Run it from the terminal; if there are any error messages, you will see them...

---

### Post by traynor on 2009-08-10
How do I "run it from the terminal"? (sorry - I'm really a newbie; I'd rather use terminal commands, but I don't know any yet)

Also, would this also explain why I was unable to upgrade to Firefox 3.5 even though I ran the apt:firefox 3-5 command?

thanks for any tips

---

### Post by snowpine on 2009-08-10
Applications->Accessories->Terminal

---

### Post by traynor on 2009-08-10
I know how to access the terminal, but what command do I type?

For example I'm showing the FTP client installed in Synaptic. Do I type "run ftp"? I tried that but it says "command not found" 

thanks for helping

---

### Post by Surkow on 2009-08-10
Typing for example the program "firefox" (or any other program name like the ftp client filezilla) in the terminal would be sufficient. They are so called aliases and link to an executable.

---

### Post by snowpine on 2009-08-10
> **traynor said:**
> I know how to access the terminal, but what command do I type?

For example I'm showing the FTP client installed in Synaptic. Do I type "run ftp"? I tried that but it says "command not found" 

thanks for helping

What did you install? Is the name of the application 'ftp'? If so, open a terminal and type:

```
ftp
```

If you want to read the manual:

```
man ftp
```

Applications only appear in your Applications menu if they have a graphical user interface... some apps are "terminal apps" meaning they must be run from the terminal. It's really hard for me to be more specific without knowing which specific app you're trying to use. :)

---

### Post by traynor on 2009-08-10
Hey! you guys are helping!

I type ftp in the terminal and I get a prompt that says "ftp>" and then I type the hostname, login id and password. heheh, now I'm at a terminal ftp prompt and have no idea what to do if I want to run ftp, but no worries. I think I get it - especially the part about "terminal" apps.

I guess if I want to get savvy in the terminal I have to learn some "unix" command lines - is that correct? Do you guys recommend a beginner's resource for learning how to run terminal commands.


Otherwise, in the 2nd part of my question here, I did try (in terminal) typing firefox, and it then loaded firefox, but it's still version 3.0.1. I am pretty sure I got version 3-5 this morning (apt:firefox 3-5) but I can't seem to load it.

Again thanks for all the help guys! I'm loving this and it runs really smoothly on my HP laptop and I can't wait to finish testing and wipe windows off the machine completely :)

---

### Post by johndoe32102002 on 2009-08-10
There are more programs in these folders from terminal that might not have GUI shortcuts:
/usr/bin
/usr/sbin

and you can list the programs with "ls" and run them with "./program"

---

### Post by Surkow on 2009-08-10
Type "fire" in the terminal and press the tab button a couple of times. It will show some suggestions. For me it shows:

```
~$ firefox
firefox      firefox-3.0
```

Which are the names of the different Firefox versions I have installed on my computer. Warning - closing the terminal will also close the program you have launched with it (type "firefox &" to move it to its own process). Starting a program with alt+f2 doesn't have that problem.

---

### Post by raymondh on 2009-08-10
For more terminal learnings ... see the first post on this [link]("http://ubuntuforums.org/showthread.php?t=171507")

Yes, both GUI and Terminal are great ways to get your system/apps going.  I am still learning both and it has helped me even in my mac-based systems.

A wise friend once told us "learn how to use the terminal and you can make a commodore 64 computer run".

Happy Ubuntu-ing.

---

