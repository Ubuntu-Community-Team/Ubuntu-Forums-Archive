---
title: "How do I change boot order in 9.10?"
date: 2009-11-01
forum: Installation &amp; Upgrades
---

### Post by jonobe on 2009-11-01
I can't find boot/grub/menu.lst to change the boot order when starting up.  So things have changed, but I can find no documentation on it in the ubuntu help pages, which frustratingly stop at the previous release!


Can anyone help with this?  I only want to know where the file is to change the order, or be pointed to some documentation on it.

---

### Post by darthmob on 2009-11-01
This post may help:
[http://ubuntuforums.org/showthread.php?p=8191211#post8191211](http://ubuntuforums.org/showthread.php?p=8191211#post8191211)

---

### Post by Herman on 2009-11-01
GRUBII is easier than GRUB Legacy, all you need to do is run grub-set default, you don't need to go editing files by hand.
```
sudo grub-set-default 5
```The number you set should be the number of lines down from the top of the boot entry you want selected by default with the highlight bar at boot-up.
[How To Set The Default Boot Entry for GRUB]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20Bash%20Commands.html#grub-set-default") - with grub-set-default

---

### Post by jonobe on 2009-11-01
I tried sudo grub-set-default (n)

several times, with different numbers.  No luck.  Still selects Ubuntu 9.10, at the top.  

I then looked at all the links there are on this problem.  Crikey, there's a lot of stuff on this simple little thing.

Does it really have to be so complex to tell a computer which OS it should boot up first?

The links say Grub2 is going to be so good, so flexible.  How flexible does a boot loader have to be?  Really?

Saying all that, I do really appreciate the help offered.  Any other ideas I could try?

---

### Post by efflandt on 2009-11-01
I am an old Linux user (since about 1995), but new Ubuntu user (1 week).  And while it is user friendly for the most part, you have to hunt for information about what it is doing under the hood (or bonnet as they would say in the UK).

So I am just curious if a fresh install of 9.10 installs grub2?  I just installed 9.04 a week ago on desktop and laptop, updated those in place to 9.10, and they still both use grub (not grub2).  Although grub2 is available on Synaptic Package Manager.

If 9.10 uses grub2 with fresh installation, but not with an Update Manager upgrade, maybe that is why it goes effortlessly for some, while others have boot or configuration issues.

PS: So when I had trouble with 64-bit kernel 2.6.31-14 on my 9.10 updated desktop which was still using grub, I just moved the entries in /boot/grub/menu.lst for kernel 2.6.28-16 before those and did sudo update-grub.

---

### Post by Herman on 2009-11-01
Hey, it's not working for me either, I'm pretty sure I tried that out a little while ago and it used to work, sorry for any inconvenience.
I checked in the /boot/grub directory and mine doesn't even have a /boot/grub/default file.
Maybe it's something still under development and it'll be fixed when the developers get around to it.

---

### Post by spandon on 2009-11-01
Hi,
I have found the easiest way to change OS boot order is to use Startup-Manager:
Applications, Ubuntu Software Centre then enter startup in search - then choose StartUp-Manager from list.
When installed, go to System, Admin, StartUp-Manager then change Default Operating System to the one you want ( plus any other changes available you wish to change).
The new StartUp-Manager does not have as many changes that were available in 9.04, but is better than messing about with scripts untill someone comes up with a simple non-geek script that most users can easily use and understand, as was available for earlier versions of Ubuntu.
Hope this helps you?
Don

---

### Post by soul_motor on 2009-11-01
> **spandon said:**
> Hi,
I have found the easiest way to change OS boot order is to use Startup-Manager:
Applications, Ubuntu Software Centre then enter startup in search - then choose StartUp-Manager from list.
When installed, go to System, Admin, StartUp-Manager then change Default Operating System to the one you want ( plus any other changes available you wish to change).
The new StartUp-Manager does not have as many changes that were available in 9.04, but is better than messing about with scripts untill someone comes up with a simple non-geek script that most users can easily use and understand, as was available for earlier versions of Ubuntu.
Hope this helps you?
Don
This definitely helped me.  Thank you very much!  I tried everything, and nothing else worked.  By far easiest method!

---

### Post by Hex on 2009-11-01
> **spandon said:**
> Hi,
I have found the easiest way to change OS boot order is to use Startup-Manager:
Applications, Ubuntu Software Centre then enter startup in search - then choose StartUp-Manager from list.
When installed, go to System, Admin, StartUp-Manager then change Default Operating System to the one you want ( plus any other changes available you wish to change).
The new StartUp-Manager does not have as many changes that were available in 9.04, but is better than messing about with scripts untill someone comes up with a simple non-geek script that most users can easily use and understand, as was available for earlier versions of Ubuntu.
Hope this helps you?
Don

Very useful, thank you!

---

### Post by macogw on 2009-11-01
> **efflandt said:**
> 
So I am just curious if a fresh install of 9.10 installs grub2?  I just installed 9.04 a week ago on desktop and laptop, updated those in place to 9.10, and they still both use grub (not grub2).  Although grub2 is available on Synaptic Package Manager.


Yes, that's how it works.  An in-place upgrade from grub1 to grub2 would've been too risky, so 9.04->9.10 upgraders kept grub1.

---

### Post by jonobe on 2009-11-01
> **spandon said:**
> Hi,
I have found the easiest way to change OS boot order is to use Startup-Manager:
Applications, Ubuntu Software Centre then enter startup in search - then choose StartUp-Manager from list.
When installed, go to System, Admin, StartUp-Manager then change Default Operating System to the one you want ( plus any other changes available you wish to change).
The new StartUp-Manager does not have as many changes that were available in 9.04, but is better than messing about with scripts untill someone comes up with a simple non-geek script that most users can easily use and understand, as was available for earlier versions of Ubuntu.
Hope this helps you?
Don

Thanks Don

Yes it did help - worked first time!

As you say, it will do until they come up with a 'simple non-geek script'.  Thanks.

---

### Post by the_zoor on 2009-11-01
Brilliant spandon!!

I've been searching all day for the answer. Thank you!

---

### Post by 73ckn797 on 2009-11-01
Grub2 info: [https://help.ubuntu.com/community/Grub2?action=show&redirect=GRUB2](https://help.ubuntu.com/community/Grub2?action=show&redirect=GRUB2)

---

### Post by drs305 on 2009-11-01
> **Herman said:**
> GRUBII is easier than GRUB Legacy, all you need to do is run grub-set default, you don't need to go editing files by hand.
```
sudo grub-set-default 5
```
Hey, it's not working for me either

> **jonobe said:**
> I tried sudo grub-set-default several times, with different numbers.  No luck.  Still selects Ubuntu 9.10, at the top.  

The "grub-set-default" command works in Grub 2, but only if you have the default in */etc/default/grub* set to:
> DEFAULT=saved
Once that is set, you can run the command Herman cited to change the default selection with:
```
sudo grub-set-default [COLOR="Red"]X[/COLOR]
```
[COLOR="Red"]X[/COLOR] can be either a number or an exact string from one of the menu items.

Example of how to set it up. If you don't know the number or value you wish to use, run this:
```

grep menuentry /boot/grub/grub.cfg

```
Sample return from above:
> 
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
menuentry "Ubuntu, Linux 2.6.31-12-generic" {
menuentry "Ubuntu, Linux 2.6.31-11-generic" {
menuentry "System Rescue CD" {
menuentry "Windows XP" {

Your [COLOR="Red"]X[/COLOR] options would be 0, 1, 2, 3 ,4 or any string between the quotes.
Examples:
sudo grub-set-default 1  # selects the -12 kernel
sudo grub-set-default "System Rescue CD" # selects System Rescue CD

This is one of the few times you don't have to run "sudo update-grub" to update the menu.

---

### Post by Herman on 2009-11-02
:D Cool! Thanks drs305!

---

### Post by jadonchristensen on 2009-12-29
> **spandon said:**
> Hi,
I have found the easiest way to change OS boot order is to use Startup-Manager:
Applications, Ubuntu Software Centre then enter startup in search - then choose StartUp-Manager from list.
When installed, go to System, Admin, StartUp-Manager then change Default Operating System to the one you want ( plus any other changes available you wish to change).
The new StartUp-Manager does not have as many changes that were available in 9.04, but is better than messing about with scripts untill someone comes up with a simple non-geek script that most users can easily use and understand, as was available for earlier versions of Ubuntu.
Hope this helps you?
Don

That was fast and easy, thank you.

---

### Post by houman001 on 2010-02-02
Here is an excerpt from Grub2 guide:

GRUB_DEFAULT
...
      GRUB_DEFAULT=saved Sets the default menu entry with whatever was selected last. If the menu is displayed during boot, the last entry selected will be highlighted. If no action is taken, this selection will be booted at the end of the timeout or if the menu is hidden.
...
      grub-set-default is enabled when this value is set to saved. The user can quickly change the default OS/kernel with this command.

Reading this guide worths it. It is located at: [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

