---
title: "WUBI vs Frugal install? Differences etc?"
date: 2008-08-13
forum: General Help
---

### Post by nooby on 2008-08-13
I've had Ubuntu in a wubi install but took it away cause failed 
to do shut down cleanly so it forced me to do hard reboot holding 
down the power button more than four seconds. 

Which caused me to loose windows to fail to boot. 

So I felt bad about it. Since then I have tested something named 
frugal install. It is kind of similar in that one use a menu.lst 
as I guess wubi also had? In the menu.lst now I have frugal 
install of Nimblex linux, Vector SOHO Preview linux, Zenwalk live linux, GoblinX linux, three or four different Puppy linux and have had SliTaz and many more. DSL, Austrumi, Alixe, Knoppix, Kanotix, etc

All tolerating each other just fine. 
[B]
So my questions is. If these work together just fine would it 
not be possible to do a frugal install instead of a WUBI 
install of Ubuntu 8.04.1 live cd/dvd iso? 
[/B]
I mean is Ubuntu so different that it is impossible to do frugal install?

**Are there any Ubuntu version that work in frugal install?**

---

### Post by nooby on 2008-08-14
While I wait for someone to give their way of doing it I used google 
to find how others have done it. This is the only one i've found. 

> title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)

root		(hd0,5)

kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=5d64478e-4b2e-4c06-a74f-1a06d77a03fa ro single

initrd		/boot/initrd.img-2.6.24-19-generic

[http://community.plus.net/forum/index.php?action=printpage;topic=64956.0]("http://community.plus.net/forum/index.php?action=printpage;topic=64956.0")

But I barely understand it. Is this a real frugal or is it a kind of full install but done trough frugal means. 

I mean this part looks different. 
root=UUID=5d64478e-4b2e-4c06-a74f-1a06d77a03fa

Suppose I download the latest? Ubuntu 8.10 what uuid number doeas that one have? How does one find out?

---

### Post by nooby on 2008-08-21
I have tried to get to know WUBI a bit better but it is way 
above my capacity to get. 

Ago, you and tuxcantfly had a disagreement about how to set up 
wubi some years ago??? 

But if I got it both of you did support that it should be loop-mounted. 

Is that that which make WUBI different from the Knoppix cheat code 
iso frugal install which don't do partition and don't do any loop 
mounted formatting in ext2 or 3 either? 

[B]Is it possible for Ubuntu live cd iso to do like they do with DSL 
and Knoppix and Puppy and many slackware distros like Nimblex, Zenwalk, 
Goblinx, Vector, SliTaz and others or is Ubuntu lacking something they 
have.  ntfs-3g write capacity or what?[/B]

---

### Post by ago on 2008-08-21
A loopinstallation is like a frugal installation but customized for your hardware as opposed to be a "generic" install (which is optimized for "portability"). In fact a loopinstallation is exactly like a real installation. That of course also means that a loop installation is far faster than a frugal installation.

So the frugal installation has little advantages over a loop installation other than the fact that the installation itself is quicker 
(since there is no linux side installation) and it takes less space (the squashfs is compressed). 

By the way, wubi already supports frugal installation (not r/w although it can be changed by adding a persistent file)... Run wubi.exe from windows, then when you reboot press ESC and choose the last option... That is a frugal installation... If you want it permanent simply make it the default boot option in ubuntu\install\boot\grub\menu.lst. Note the demo mode option is deleted after a linux side loop installation.

---

### Post by nooby on 2008-08-21
Thanks for your reply. 

Your the expert so I have to trust your words. 
and you guys spent one or two years on refining it so 
you know incredibly more about such than me. 

But I still feel safer doing it the way I do now. Manually.
To let wubi script take over I don't trust. Sorry. 

As a noob one have very little resources to repair if 
something goes wrong.

---

### Post by ago on 2008-08-21
The risks are the same... If you want a frugal installation to be rw you will have to mount the ntfs partition containing the cow file in r/w mode. Hence in case of hard reboot that could become corrupted just as well.

---

