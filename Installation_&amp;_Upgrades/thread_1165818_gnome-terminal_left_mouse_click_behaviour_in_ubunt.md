---
title: "gnome-terminal left mouse click behaviour in ubuntu 9.04"
date: 2009-05-21
forum: Installation &amp; Upgrades
---

### Post by jbellis113 on 2009-05-21
I've just installed Ubuntu 9.04.  In gnome-terminal, when I left mouse click to the right of the last character on a line, the rest of the line is highlighted (and used as the clipboard contents).

How do I make it so the rest of the line is not highlighted on a mouse left click?

In ubuntu 8.10, gnome-terminal, upon a left mouse click would not select the remainder of the line.

---

### Post by tcab on 2009-06-02
Yes - I get this ugly behaviour too.  When clicking on a terminal window in order to change window focus and type my next command, I invariably get a "reverse video" selection effect past the end of the line.

I've tried playing with color schemes but to no avail.  If the background is white (default) the ugly highlight effect is black.  If the background is black (my preferred) the highlight is white.

The only way to avoid it is to either mouse click carefully on some text (which usually highlights a character anyway, not ideal).  

Or activate the terminal window with a RIGHT click, but then be careful to slide your mouse off the popup menu otherwise you end up triggering the first item in that menu, which is to open up a brand new terminal window.  Alarming!  In fact the popup menu is way too trigger happy, just right clicking and releasing the mouse opens a new terminal window - even though you don't feel like youve actively selected anything.  The relevant menu item is not even highlighted - yet it gets triggered - I think this is another bug.

Its all really quite annoying.

---

### Post by dbatothestars on 2009-06-10
I am getting this same behaviour running virtualbox on windows XP with ubuntu 904 as a guest.  This means that I can snapshot the unix host and revert back to that point in time.  Interestingly, the left-click selects whole line only occurs after a length of time.  I've tried to isolate the triggering events, but no joy so far.
It's worse than annoying, as the X paste buffer is nuked every time you click on another window.

---

### Post by jbgron on 2009-06-15
I have the same problem.  I spend all day on the terminal so this is extremely fu**ing annoying!  I hate to say it but I've actually installed Konsole until this bug is fixed.

---

### Post by dbatothestars on 2009-06-26
is this an install of Ubuntu, or through a virtual machine?  I'd like to elminate virtual box as a suspect!
> **jbgron said:**
> I have the same problem.  I spend all day on the terminal so this is extremely fu**ing annoying!  I hate to say it but I've actually installed Konsole until this bug is fixed.

---

### Post by JorritSchippers on 2009-06-27
I have this problem in VMware, so it might be VM related.

---

### Post by jbellis113 on 2009-06-29
I'm running Ubuntu 9.04 as a guest machine using Sun VirtualBox 2.2.4.  Windows XP is the Host.

---

### Post by jbgron on 2009-06-29
This is happening natively for me, although I do have VMWare Server and VirtualBox installed.  I can't believe this is not fixed already, this makes gnome-terminal unusable for me, I have to use Konsole.

---

### Post by jbellis113 on 2009-07-02
I've just upgraded to VirtualBox 3.0.  Problem has gone away!

---

### Post by austindougli on 2009-08-28
The latest VMware Workstation update, 6.5.3 build 185404, seems to fix the problem.  I installed the new release and installed the updates vmware tools, rebooted and the issue went away.

Now if only they would fix the issue of Gnome Terminal not remembering its settings.

---

### Post by jbellis113 on 2010-01-17
This problem (see OP) has re-appeared for me in Ubuntu 9.10, using VirtualBox 3.1.2.  Anyone else experiencing this?

---

### Post by m.afifi on 2010-02-05
Yes same behaviour for me on VBOX 3.1.2

Uname -a

2.6.31-19-generic #56-Ubuntu SMP Thu Jan 28 02:39:34 UTC 2010 x86_64 GNU/Linux

---

### Post by provoko on 2010-10-09
I have the latest latest of everything and it still happens....

---

### Post by insulanus on 2011-03-27
I found the bug report for this behaviour:

[https://bugs.launchpad.net/ubuntu/+source/gnome-terminal/+bug/445084](https://bugs.launchpad.net/ubuntu/+source/gnome-terminal/+bug/445084)

---

