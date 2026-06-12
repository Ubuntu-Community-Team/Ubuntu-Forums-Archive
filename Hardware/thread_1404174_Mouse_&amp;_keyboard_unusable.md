---
title: "Mouse &amp; keyboard unusable"
date: 2010-02-11
forum: Hardware
---

### Post by bob20000 on 2010-02-11
Dear all, 

I run Karmic on an Asus x51r laptop. 
My Ubuntu shows massive "misbehavior" of its mouse and keyboard. I do not know whether this is   an hardware issue...

Anyway, the problem is the following. 
Sometimes, I can not type anything anymore: the curser comes back at the beginning of the line, and the text looks like nothing (this could give: gninothkeil ksolo). This happens in any text field: OpenOffice, FF, gedit, even the login field at session startup...
In the same kind of strange way, when this happens, I can not scroll down pages (FF, OOo, etc.), nor can I select a 2nd or 3rd position in a menu (Gnome's Apps for example, or any application menu).

I reported this in the french Ubuntu forum: [http://forum.ubuntu-fr.org/viewtopic.php?id=370460](http://forum.ubuntu-fr.org/viewtopic.php?id=370460)
I have been said to test the following: 
> sudo nano /etc/default/grub
then modify the line: GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" in: 
> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i8042.nomux" 
or > GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i8042.nomux i8042.reset=1"
or > GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i8042.reset"
or > GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i8042.reset i8042.nomux=1"
each time finally followed by
> sudo update-grub2 then restart. 

None of these changed a thing. 

This strange behavior appears randomly: there can be weeks without any problem, then it appears and stays for hours or days. During which the computer is obviously unusable...

Of course, I do not touch the touchpad, even accidentally...

I would really appreciate your help... this laptop is for professional purpose, and I can not stay in vacations for ages :?

Thanks!

---

### Post by bob20000 on 2010-02-12
EDIT: 
posted on Launchpad: [https://answers.launchpad.net/ubuntu/+source/yelp/+question/100800](https://answers.launchpad.net/ubuntu/+source/yelp/+question/100800)

> well, laptop is absolutely unusable. I have lines and lines of ^[[1 followed by "General error mounting filesystems. A maintenance shell will now be started" etc at boot.
Then comes the login screen, in which I can not type my PW since the curser do not stop going back at the beginning of the line...
If there is no solution, neither from ubuntu forums nor from google, then I'll have to come back to an other OS... What a pain... but I have no other option. Hope the 10.4 release will work fine for me...

---

