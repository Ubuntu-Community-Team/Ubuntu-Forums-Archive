---
title: "launchy - open program with gedit!?"
date: 2008-08-07
forum: General Help
---

### Post by odzx on 2008-08-07
hi everyone.
I've recently removed mono from my ubuntu desktop, following this [recommendation]("http://www.theopensourcerer.com/2008/08/04/how-to-remove-mono-m-from-ubuntu-hardy-heron/"). unfortunately one of my favorite programs, gnome-do, uses mono as well, and was removed in the process. trying to find a replacement I've installed Launchy. In over all launchy works OK for me and launches most apps the way it is should. some apps nonetheless, do not launch. for example: when typing "zim", launchy finds the application as /usr/bin/zim, but instead of launching it i actually opens the file /usr/bin/zim in Gedit. this is true for some other programs as well.
This is probably some stupid thing I've overlooked, but any help would be great anyway.
Thanx :)

---

### Post by sefr0m on 2008-08-12
I having the same issue.
But open whit vim. In my ubuntu launchy open the *.sh files.

I can´t fixit

---

### Post by EiriktheRed on 2008-08-17
Same here. Very irritating problem, as it makes about half my applications unreachable from Launchy. I've posted a bug report at launchy.net

---

### Post by odzx on 2008-09-01
anyone got a solution yet?

---

### Post by humble_coffee on 2008-11-01
It seems to be a bug in Launchy. Launchy seems unable to open symbolic links and executable scripts. This means that unless the thing you're trying to open is a binary executable, the file will be opened in your default text editor.

It's not a fix, but a workaround is to edit the problematic menu items so that they point directly to the executable. To do this in Gnome, right-click on the Applications menu in the top left-corner and select 'Edit Menu'. Then find the application you want to edit and click 'Properties' You then need to change the command to the executable that launches the program. 

If the command is a symlink, to find where it is pointing, you can type "ls -l command" into a terminal, where 'command'  is the full path to the symlink. If it is a symlink it will have an 'l' next to the permissions list and have an arrow after the file name which points to the actual file. Be aware that symlinks can point to symlinks and you may have to repeat this to find the actual executable.

Also, if the command for the application is a script (or a symlink to a script) it also won't be able to execute itself. So if you have a python script, then you will need to enter "python script" as the command (where 'script' is the full path to the script).

And don't forget that you'll need to rebuild Launchy's catalog before these changes will take effect. Do this by right clicking on the launchy window and selecting "rebuild catalog".

---

### Post by odzx on 2008-11-01
> **humble_coffee said:**
> It seems to be a bug in Launchy. Launchy seems unable to open symbolic links and executable scripts. This means that unless the thing you're trying to open is a binary executable, the file will be opened in your default text editor.

It's not a fix, but a workaround is to edit the problematic menu items so that they point directly to the executable. To do this in Gnome, right-click on the Applications menu in the top left-corner and select 'Edit Menu'. Then find the application you want to edit and click 'Properties' You then need to change the command to the executable that launches the program. 

If the command is a symlink, to find where it is pointing, you can type "ls -l command" into a terminal, where 'command'  is the full path to the symlink. If it is a symlink it will have an 'l' next to the permissions list and have an arrow after the file name which points to the actual file. Be aware that symlinks can point to symlinks and you may have to repeat this to find the actual executable.

Also, if the command for the application is a script (or a symlink to a script) it also won't be able to execute itself. So if you have a python script, then you will need to enter "python script" as the command (where 'script' is the full path to the script).

And don't forget that you'll need to rebuild Launchy's catalog before these changes will take effect. Do this by right clicking on the launchy window and selecting "rebuild catalog".

in my example zim is the program i was trying to run. zim executable is /usr/bin/zim. it is a perl script. so it seems your right.
I've actualy started using deskbar instead of launchy. It works better for me, as an application launcher & search tool.
Nevertheless, thank tou very much for the reply. =D>

---

### Post by DarkoBeatsDeath on 2008-12-20
Hey,

As a workaround, you can remove all applications associated with the "application/x-shellscript" type, by going with nautilus to the directory of the file you're trying to load, right click -> Properties -> "Open With"
and remove all the applications in the list.

Ron.

---

### Post by davidsiegel on 2008-12-23
> **odzx said:**
> hi everyone.
I've recently removed mono from my ubuntu desktop, following this [recommendation]("http://www.theopensourcerer.com/2008/08/04/how-to-remove-mono-m-from-ubuntu-hardy-heron/"). unfortunately one of my favorite programs, gnome-do, uses mono as well, and was removed in the process. trying to find a replacement I've installed Launchy. In over all launchy works OK for me and launches most apps the way it is should. some apps nonetheless, do not launch. for example: when typing "zim", launchy finds the application as /usr/bin/zim, but instead of launching it i actually opens the file /usr/bin/zim in Gedit. this is true for some other programs as well.
This is probably some stupid thing I've overlooked, but any help would be great anyway.
Thanx :)

odzx, hey, I'm the author of GNOME Do. I'm really glad Do is/was one of your favorite programs. I read the recommendation for removing mono that you link to, and the basic argument seems to be that mono puts "M$" applications on your desktop. I cannot speak for other mono applications, but I am an Ubuntu user and I wrote GNOME Do on and for Ubuntu. I'm sorry if the flimsy argument you link to has ruined GNOME Do for you, as we are busily working on the next release with lots of cool new bells and whistles :)

---

### Post by zhouzheng on 2009-01-18
Hello, everyone.
I find a way to fix this problem.
Firstly, open nautilus and go to /bin, you will see a lot of application/x-shellscript files.
Secondly, right-click on one of them, select "properties"
Thirdly, add a new program "sh" in the Tab "Open with",and select "sh" as the default option to open it.

That is all, thank you, Happy new year.

---

### Post by chowd on 2009-04-13
> As a workaround, you can remove all applications associated with the "application/x-shellscript" type, by going with nautilus to the directory of the file you're trying to load, right click -> Properties -> "Open With"
and remove all the applications in the list.

I tried adding a program "sh" to the application list, as zhouzheng suggests, and this did not work for me. But the tip from the above quote from DarkoBeatsDeath worked. I also had to do this for Python scripts.

---

### Post by iddy on 2009-06-03
This worked for me by just hitting "reset" instead of removing all applications. 
Basically the same thing, but for those who are worried about side effects, having sh files without an associated program should be default for ubuntu. :)

if I have any trouble, i might try out deskbar as suggested above, launchy is kinda buggy on linux i've found

---

### Post by kakyoism on 2009-06-16
Why not just Alt-F2...
Well, on linux I use launchy for internet search, Alt-F2 takes care of applications quite flawlessly.

---

### Post by steve228 on 2009-11-23
> **DarkoBeatsDeath said:**
> Hey,

As a workaround, you can remove all applications associated with the "application/x-shellscript" type, by going with nautilus to the directory of the file you're trying to load, right click -> Properties -> "Open With"
and remove all the applications in the list.

Ron.

Simply Amazing... I was almost ready to give up on launchy because theres a few apps I use everyday and I try to open with launchy and it wouldn't work... 

Thank you very much for this.  Works 100% now(albeit you must do it for every program that bugs out)... but hopefully launchy will address the issue..

Thanks again :D

---

### Post by lekksi on 2010-03-08
Workaround removing "Open with" works for me too. It would be nice if this bug were fixed in Launchy, though.

---

