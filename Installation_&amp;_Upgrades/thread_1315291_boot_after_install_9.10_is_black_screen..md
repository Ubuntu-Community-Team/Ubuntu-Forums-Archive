---
title: "boot after install 9.10 is black screen."
date: 2009-11-05
forum: Installation &amp; Upgrades
---

### Post by yesdup on 2009-11-05
Hi all and thanks for any help in advance ...:) 

I have installed 9.10 on my Dell inspiron 2650 from the live cd. But 
in order to get the live cd to boot i used the acpi=off option. The installation seemed to go without a hitch. 

However upon reboot I have a Black screen and just a curser after 'grub'.

I have tried to edit and add the acpi=off option. But no luck.

Is there a known issue or can someone please help get this to boot please.

Thanks

---

### Post by Mujaheiden on 2009-11-05
seems like your grub is not working. Follow instructions at [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by yesdup on 2009-11-06
Thanks but those instructions failed to get past the sudo grub command on the live cd. 

The grub loads fine and offers all the editing function etc. but it wont seem to load anything graphical. The recovery boot option of grub menu will start to load  - i get a load of text but then stops after aboout 2 seconds. 

Any other suggestions please

---

### Post by xXZeroXx on 2009-11-14
Same problem here, both Ubuntu 9.10 and Debian Sid got this problem.

I think is a bug in package xserver-xorg, most precisely xserver-xorg-video-radeon/ati.

I managed to boot in both systems creating a xorg.conf and adding "NoAccel" "True" in section "Device", however, you'll get no 2D Accel which just sucks.
There's another "hack" boot into recovery mode and when it asks for the root password, press SysRq+R+S+E and continue booting.

This has worked for me, but, it may not work for you.

Good Luck!;)

---

### Post by jbhops on 2009-11-16
try turning off "Special Effects", System->Appearance->Visual Effects set this to None.  This worked for me, essentially this turns off the compiz component

---

### Post by jonny sadler on 2009-11-16
Total Ubuntu newbie here after some much needed advice please,ok,so I installed Ubuntu 9.10 on my laptop and really like it,have binned of XP altogether,now want to do the same for my desktop,tried installing using the Live CD but after initial request to choose installation,language etc am faced with a black screen.Did some digging on the forums,got confused then found Wibi,thought I'd try it and hey presto it works just fine,now I have a dual boot machine which I don't really want,would like to kiss XP goodbye again,so anyone have any ideas ?

Also if I try to install Studio will I get the same black screen ? ,could I install Studio from the Wibi version of 9.10 ?

Not very tech minded so simple instructions or help much appreciated.

Many thanks

---

