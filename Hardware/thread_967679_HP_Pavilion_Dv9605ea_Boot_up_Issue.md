---
title: "HP Pavilion Dv9605ea Boot up Issue"
date: 2008-11-02
forum: Hardware
---

### Post by Lloydus on 2008-11-02
Hi everyone,

I have just upgraded to Ubuntu 8.10 from 8.04 and on the whole this has been a great sucess. My internal broadcom wireless card to work for the first time - so bye bye external usb card!

However on boot up my laptop freezes on the ubuntu loading screen,I can unfreeze my laptop and continue boot up by holding down my power button for one second. Also I can only boot up if it is plugged into the mains, so I am unable to boot up on battery power alone. Once I have reached the login screen everything functions normally as it did in 8.04 and I can operate on just battery power.

This is a slight inconvinience but not a serious issue for me - however I would be interested to hear if anyone else has experienced this or if anyone is aware of the cause of this problem or any potential solutions.

Thanks in advance,

Lloydus

---

### Post by Ozzi on 2008-11-02
I have (see my post [here]("http://ubuntuforums.org/showthread.php?t=967627")), but I haven't found any fix to this issue.

---

### Post by Lloydus on 2008-11-02
Thanks Ozzi,

I was able to sucessfully boot up without mains power by holding down the space bar. 

If I come to hear of a fix to this problem I will post on your thread.

---

### Post by etsmith3 on 2008-11-09
> **Lloydus said:**
> Thanks Ozzi,

I was able to sucessfully boot up without mains power by holding down the space bar. 

If I come to hear of a fix to this problem I will post on your thread.

I am having the same issue. I have a DV 6636nr. I installed the 64 bit and everything seems to be working fine, just when its booting up I have to hit space bar during the loading bar in order to keep it booting.
Any one find out what causes this? Or is it only 64 bit that does it? Haven't tried the 32bit yet, figured see if i can find a fix first.

---

### Post by NESU on 2008-11-09
I am also having the same problem, except that I can continue by pressing and holding the enter key or by continuously pressing the enter key. I have a Compaq F750us and am using 8.10.

---

### Post by etsmith3 on 2008-11-09
> **NESU said:**
> I am also having the same problem, except that I can continue by pressing and holding the enter key or by continuously pressing the enter key. I have a Compaq F750us and am using 8.10.

Are you using 64bit as well? I think it works with any key is what Im gathering from other sources, not sure haven't tested yet.

---

### Post by nickmalcolm on 2008-11-10
I have the same bootup problem, on a HP dv6000 and used 64-bit ubuntu.
I just press spacebar to keep it going. I found that pressing spacebar once will keep it going for longer than pressing other keys once. Don't know why....
Haven't tried booting on battery. 

I also couldnt get the wifi to work, even with madwifi etc.

Edit:
Oh and I found it was the same problem with 32-bit aswell

---

### Post by etsmith3 on 2008-11-11
> **nickmalcolm said:**
> I have the same bootup problem, on a HP dv6000 and used 64-bit ubuntu.
I just press spacebar to keep it going. I found that pressing spacebar once will keep it going for longer than pressing other keys once. Don't know why....
Haven't tried booting on battery. 

I also couldnt get the wifi to work, even with madwifi etc.

Edit:
Oh and I found it was the same problem with 32-bit aswell

I can keep mine going only by repeatedly hitting a key or holding down a key seems to make it go faster.
It seems to lock up or pause the bar during the Ubuntu screen with the progress bar going back and forth, and again on the final loading bar that fills from left to right. I have booted up in safe mode and it seems that every time it gets done loading a certain part it freezes and any key continues it. It does this during install, running the live part on the cd, and also after the install.
Would really like to figure out whats wrong with it. I have tried different kernel boot, using KDE instead. With no luck. If anyone has any suggestions it would be much appreciated.

---

### Post by Skizz0tt on 2008-12-19
I also have a compaq f750us, upgraded from 8.04 to 8.10... now at boot i have to hold down a key, any key to get ubuntu to load.

I disabled the splash and saw that it first stops with the following message:

[    2.961046] hub 1-0:1.0: unable to enumerate USB device on port 2

---

### Post by SonicSteve on 2009-02-16
For the record I have a Compaq/ HP presario f700 series laptop also. It was fine under 8.04 HH but I also have to hold down the spacebar during bootup to keep it going. What exactly is happening during this point in the bootup that a keypress can effect. Has anyone filed a bug report?

I filed a bug report,
[https://bugs.launchpad.net/ubuntu/+bug/330353](https://bugs.launchpad.net/ubuntu/+bug/330353)

---

### Post by SonicSteve on 2009-02-16
Has anyone tried updating the BIOS of the laptop? I'll give it a look to see if Compaq even offers an updated BIOS.


EDIT

NO bios update is offered, I'm running F.08

---

### Post by amanison on 2009-03-14
Could everyone who is experiencing this problem please subscribe to the bug report sonicsteve created (see post #10), and add your details there.

---

### Post by grogo on 2009-03-16
I encountered the same issue when upgrading to 8.10 on my gf's dv6627ca.  Add "hpet=disable" to your grub boot options and voila! it works.  The only issue still outstanding for that machine is the suspend / resume, but since she doesn't care, I'm not going to spend any more time on it...

---

