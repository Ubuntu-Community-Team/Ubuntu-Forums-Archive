---
title: "Open Office is &quot;Pulling a Microsoft&quot;"
date: 2008-09-02
forum: General Help
---

### Post by lightnb on 2008-09-02
Ok, so if I right-click a file, and say "open with Base", I want it to open with Base!

But no, Open Office tries to open the file with Calc and then gives me an error message that my file has too many rows! ...Even though I explicitly stated that it needs to be opened with Base.

How can I turn off this annoying auto-guess 'feature' So that it uses the program I specify?

---

### Post by Luke771 on 2008-09-02
use the command line:
 First of all you have to figure out what command launches the program you need.
- edit the main menu (rightclick, edit menus)
- in the edit menus interface browse to the launcher that launches your program( right click, chose edit) 
 - there it is, under 'command' you have the command you need.
- oops, there is no menu item for Base, but as the command for Calc is ooffice -calc, we'll take a wild guess and gamble that the command to launch Base is ooffice -base

Now that you know your command, open a terminal and do <command> /path/to/file

I open a terminal and type```
ooffice -base /home/luke/stuff/myfile.abc
```

...and it works! 
So we know for sure that the command is ooffice -base (probably all the open office commands work like that: ooffice -<your-app>)

As the terminal starts from my home directory, I could use a relative path (without the initial / it will start from the directory I'm in when I launch it, in this case my home dir), and as I want to close the terminal without Calc to crash, I'll add a & at the end of the line and close the terminal with the command 'exit' because closing it with the X icon in the top-right corner will kill any app launched from that terminal, so my 2 lines will be```
 ooffice -base stuff/myfile.abc & 
 exit 
```

File opened with the program I chose, terminal closed and out of the way, problem solved.

---

### Post by lightnb on 2008-09-06
That worked, thanks!

It would be great if the "open with" context menu worked that way too....

---

### Post by hyper_ch on 2008-09-06
submit a bug report :)

---

### Post by lukjad on 2008-09-06
Contrary to popular belief, fouling up is not limited to MS.

---

