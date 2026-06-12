---
title: "Can't load toshiba_acpi module"
date: 2010-03-24
forum: Hardware
---

### Post by toomuchcomputertime on 2010-03-24
Hello community,

I have a Toshiba L505D-S5965, and I am trying to get the multimedia and fn (function) keys to work. The multimedia keys work with Linux Mint (a Ubuntu derivative), and as I remember, the fn keys work with Puppy Linux, but I can't get them to work in Ubuntu. I think this is because I cannot load the toshiba_acpi module, but I am not sure. I just updated the bios to try and fix it, but it did not change anything. I am running Ubuntu 9.10 i686, Windows Vista, and Linux Mint 7 X86-64. I have been having this problem since I installed. 

Any help would be appreciated, I think there are many other people having the same problem.:p

Thanks!!!

---

### Post by toomuchcomputertime on 2010-03-25
The reason I am trying to load the acpi is because I want to be able to see my battery status, turn on and off the wifi, and use the fn keys. When I run toshset, I get
<code>
me@ubuntu:~$ sudo toshset
required kernel toshiba support not enabled.
</code>

Can anyone help me on this? 
Thanks, I have been trying to solve this for several weeks.

---

### Post by colinwhipple on 2010-03-26
Try reviewing this message thread:

[http://ubuntuforums.org/showthread.php?t=1301101&highlight=l505d](http://ubuntuforums.org/showthread.php?t=1301101&highlight=l505d)

---

### Post by toomuchcomputertime on 2010-03-27
Thanks, I am 'trying' to compile the kernel, I have never successfully compiled anything, despite being an avid Linux user (primarily puppy until getting this refurbished laptop). Hopefully this will fix the problems, and not make any new ones!

---

### Post by colinwhipple on 2010-03-28
> **toomuchcomputertime said:**
> Thanks, I am 'trying' to compile the kernel, I have never successfully compiled anything, despite being an avid Linux user (primarily puppy until getting this refurbished laptop). Hopefully this will fix the problems, and not make any new ones!

This was my first kernel compile.  Ivan's instructions in the other message thread are very good.

Colin

---

### Post by toomuchcomputertime on 2010-03-29
Thanks Colin, I am using Ivan's instructions, I just decided to upgrade to 10.04 before I compiled, so I am compiling now. I will post an update whether it is sucesful or not.

Thanks again.

---

### Post by toomuchcomputertime on 2010-03-29
I recompiled the kernel, and it is working well, but I still don't have Toshiba acpi support. Any other ideas? 

Thanks

---

### Post by toomuchcomputertime on 2010-04-05
Just an update to clarify, I am trying to make my fn keys turn on and off the wireless chip (instead of rebooting and changing the BIOS), and also get the battery monitor working. I cannot change any power options for the battery, all I have are AC power options. Further, it would be nice to be able to change the screen brightness with the fn keys (sometimes the gnome brightness applet works, sometimes it doesn't).

Thanks.

---

