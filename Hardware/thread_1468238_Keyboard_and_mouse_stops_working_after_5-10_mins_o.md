---
title: "Keyboard and mouse stops working after 5-10 mins of booting Ubuntu 10.04"
date: 2010-05-01
forum: Hardware
---

### Post by Blackie_Chan on 2010-05-01
Hi All, 

I just upgraded to 10.04 and I found that my keyboard and mouse becomes inactive after 5 - 10 minutes of booting to Linux.  I didn't have the problem when using 9.10. 

How can I fix the problem in 10.04?

The problems occurs after about 5 - 10 minutes after being on the desktop. I'll be using firefox and then notice I can't type anything, even though I can see the cursor blinking and I will not be able to move my mouse pointer. 

This morning, I was installing tvtime from the command line. While downloading dependant packages, the keyboard stopped working and my mouse pointer stopped as well. On the screen the whole installation continued by I couldn't control it. 

When the problem occurs, I usually just restart my computer.

My mouse is a Logitech wheel mouse, and my keyboard is a cheap 104 keys keyboard.

I've attached the /var/log/udev file. 

Thanks in advance.

---

### Post by akhileshnautiyal on 2010-05-01
Hi,

  I installed ubuntu 10.04 on my Laptop (HP pavilion dv6).I am also facing problem with touchpad and keyboard.
whenever I lock the touchpad by pressing the switch on it my keyboard gets locked and after that both external mouse and keyboard stop working. then I have to shut down the laptop.
can anyone help me ???

Regards,
akhielsh

---

### Post by bigdave146 on 2010-05-01
I have a similar problem.  When I build a new VM in VMware, I cant log in to it as the keyboard wont work for me to enter the password....

Will rebuild without a password for now but its annoying...

---

### Post by yktula on 2010-05-02
I have the same problem on a fresh install of Wubi 10.04 on a 32-bit system that didn't have the same problem with Wubi 9.10 .

EDIT: This could be unrelated, but every once in a while Ubuntu fails to boot and I get this error:
>  *ERROR* *Forcing* to *32M GART size* (because of *ASIC bug* ?)

ANOTHER EDIT: This problem doesn't seem to manifest itself when booting from "safe mode"(? - I forget what it's called) into failsafe X.

---

### Post by blz84 on 2010-05-06
Same problem for me, keyboard works (in my laptop), but wireless mouse stops after some time... Might it be something related to power saving? I had an issue in 9.10 that my sound card was disabled after some time of not using it because of power saving.

---

### Post by grothag on 2010-05-07
I have similar problem. Ubuntu x64 10.04. Random application stops accepting keyboard input ( mouse still works ). Than I minimize and restore application window and keyboard works again. Might be related to power save option, not sure yet.
This never happened to me on Ubuntu 9.10.

---

### Post by Myshkin100 on 2010-05-07
I'm not sure of the amount of time, but my mouse and keyboard go out to lunch as well.  I can't use ctrl-alt-F1 to jump to a console window or anything.  I can VNC into the box and control it that way, and X is running fine as is everything else.

Both mouse and keyboard are plugged into the PS2 ports.

---

### Post by yktula on 2010-05-07
> **yktula said:**
> I have the same problem on a fresh install of Wubi 10.04 on a 32-bit system that didn't have the same problem with Wubi 9.10 .

EDIT: This could be unrelated, but every once in a while Ubuntu fails to boot and I get this error:


ANOTHER EDIT: This problem doesn't seem to manifest itself when booting from "safe mode"(? - I forget what it's called) into failsafe X.

I mentioned this in the quoted post. Here's my workaround:

[LIST=1]
[*]Boot into recovery mode from GRUB
[*]Select failsafeX
[*]Select boot into failsafeX for one session
[*]Confirm the message given
[/LIST]

Voilà! It should work.

---

### Post by The_Eddster on 2010-05-11
Sometimes both my mouse and keyboard stop working soon after I boot, and sometimes it will happen hours after I boot. It seems to be random, I can't figure out whats going on. Sometimes I can't click on the menus, but I can click on the taskbar. Sometimes right-click stops working.

Anyway, this only started happening when I upgraded to ubuntu 10.04. It's pretty annoying, because I can't seem to get enough information about it to post a bug on launchpad.

---

### Post by yktula on 2010-05-16
See this: [http://ubuntuforums.org/showpost.php?p=9239557&postcount=23](http://ubuntuforums.org/showpost.php?p=9239557&postcount=23) .
The whole thread, addressing this problem, is more active than this one.

---

