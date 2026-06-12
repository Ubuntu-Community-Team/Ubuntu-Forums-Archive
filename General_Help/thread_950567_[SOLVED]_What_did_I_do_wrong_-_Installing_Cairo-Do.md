---
title: "[SOLVED] What did I do wrong - Installing Cairo-Dock"
date: 2008-10-17
forum: General Help
---

### Post by fs_tigre on 2008-10-17
Hi,

First of all I&#8217;m new to linux (Ubuntu) so please go easy on me and secondly I want to say that I&#8217;m impressed with the system it is awesome I&#8217;m coming from window and osx and honestly I&#8217;m ready to say bye, bye to window and keep osx and ubuntu, any way I have a question.

Last night I was trying to install Cairo-Dock using the instructions provided here([https://help.ubuntu.com/community/CairoDock](https://help.ubuntu.com/community/CairoDock)) in the forum. The problem is that I don&#8217;t even know if it was installed or not, since at the end I didn&#8217;t get any message.

These are the steps I went through:
1-	Executed the following command on the shell:

**sudo gedit /etc/apt/sources.list**

2-	Added the following code at the end of the sources.list:

**deb [http://repository.cairo-dock.org/ubuntu](http://repository.cairo-dock.org/ubuntu) hardy cairo-dock**

3-	Saved changes made to the sources.list

4-	Typed:

**wget -q [http://repository.cairo-dock.org/ubuntu/cairo-dock.gpg](http://repository.cairo-dock.org/ubuntu/cairo-dock.gpg) -O- | sudo apt-key add -** 

5-	Typed 

[B]sudo apt-get update
sudo apt-get install cairo-dock cairo-dock-plug-ins[/B]

It seems that when I typed the code in step number five it started downloading something but after the download nothing did happen no errors no messages It only said the it was taking place I don&#8217;t know what was taking place or what this meant and I end up closed the shell, so I don&#8217;t have any idea what was downloaded or how close am I to have the dock installed.

How do I know if it has been installed? Any idea?

Thank you very much to all working on the Ubuntu system it rocks,
fs_tigre

---

### Post by lolp12 on 2008-10-17
man look i new here but i can tell you that the cairo dock its sucks really look try somethink new like kiba dock is better

---

### Post by Guardian2008 on 2008-10-17
Why is kiba better?
It might help others if you qualify your opinion.

Have you tried installing cairo-dock using the Synaptic Package Manager?

---

### Post by christophermluna on 2008-10-17
Hey there, fs_tiger

I am also new to Ubuntu and slightly less new to Linux.  We may or may not have had the same problem.  You could check this thread:

[http://ubuntuforums.org/showthread.php?t=949641](http://ubuntuforums.org/showthread.php?t=949641)

It might be the same issue I had with missing libraries.

---

### Post by ruipalmeira on 2008-10-17
why don't you just install .debs for cairo-dock.. [www.getdeb.org](www.getdeb.org), search for it, and other progs u might think are usefull..

it installs everything you need to run Cairo-Dock... and if this person is coming from OSX, that's the way to go.. really

---

### Post by fs_tigre on 2008-10-17
Thank you all, I found the problem, I didn't do the last part of the tutorial(First Launch).

Thanks,
fs_tigre

---

