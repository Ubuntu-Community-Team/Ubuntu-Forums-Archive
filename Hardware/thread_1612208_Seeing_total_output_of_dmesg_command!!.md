---
title: "Seeing total output of dmesg command!!"
date: 2010-11-02
forum: Hardware
---

### Post by freesparks on 2010-11-02
Hello All,

      I want to be able to read the complete output of the dmesg command.  Basically, I have used commands like:

> history > blahbla.txt

This command only prints out the history of commands used but not the entire contents of the terminal.  Also, where do I go to make it so that I am able to scroll all the way back to the beginning of my Terminal session.  I used to be so scared of the Terminal, now I've configured it like the old Unix Terminals on the SGI machines that I did not appreciate during college.  Anyway, a little nostalgia; any help always appreciated.

Best Regards,

freesparks

---

### Post by efflandt on 2010-11-02
In a bash terminal **Shift+PageUp** goes up (amazing) and **Shift+PageDn** goes back down.

If you want to read **dmesg** or anything else that is too large and scrolls off the screen, pipe it through **less**.  Less is like **more**, only better.  You can search for words withing the text by using slash (/) and then typing a search term. **q** quits.

**man less** (which is actually used to view man pages)

Examples of piping (vertical bar) through less:

**dmesg | less** (or **less /var/log/messages** would be similar with time/date)

**sudo lspci -v | less**

In fact, some time when you have nothing better to do it wouldn't hurt to read **man bash**.

---

### Post by freesparks on 2010-11-02
Hello efflandt,

  I always have problems with syntax.,, and how I should go about doing something in Linux, part of the reason why I posts is to see just how many ways something can be done.  Sometimes its just something really simple and my problem has always been that I am very meticulous.  I thank you for your help.  And, I will try not to post things that may seem trivial to the general population!!

Best Regards,

freesparks

---

