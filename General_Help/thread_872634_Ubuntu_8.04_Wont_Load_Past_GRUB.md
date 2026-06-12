---
title: "Ubuntu 8.04 Wont Load Past GRUB?"
date: 2008-07-28
forum: General Help
---

### Post by AlexRulz on 2008-07-28
Hi everyone, My name is alex and yeah, im brand new here. Sadly my first post is about how to get ubuntu running haha. I have always used windows but after seeing Ubuntu on APC mag i decided to burn the ISO and give it a go.

I had some issues getting it to install or even load off the live CD but once i worked out the no acpi thing it ran nicely off the cd and i had no worries getting it all installed.

The problem comes when it restarts after the install and tells me to take the disk out and press enter, then whenever i try and boot ubuntu it goes to a black screen saying "starting up" and just freezes there. If i try and run it in recovery mode it runs a long string of commands i dont understand a freezes up also. The last thing on the list says:

18.167391] Clocksource tsc unstable (delta = -299114667080

My system details are as follows:

AMD Athlon 64 X2 Dual Core 4000+
2GB RAM
Samsung 750GB HDD (2 partitions roughly 350GB each, one containing windows XP and the other Ubuntu)
ASUS M2A-VM motherboard
ATI RADEON X1050 graphics card


Anybody got any ideas? i really dont want to give up on it because windows drives me nuts.

p.s: my windows install is working fine, i'm on it right now.


Thanks anybody for your help :)

Alex G

---

### Post by gjoellee on 2008-07-28
this is a common issue for kernel 2.6.26-20 you should uninstall it and keep on using kernel 2.6.26-19

---

### Post by AlexRulz on 2008-07-28
Righto, that is ubuntu 7.01 or something is it? Sorry for my linux illiteracy :P

---

### Post by Elfy on 2008-07-28
Check the line you are using to boot ubuntu in the menu list

You want it to look like this 

> title           Ubuntu 8.04.1, kernel [COLOR="Red"]2.6.24-19-generic[/COLOR]

If you've only just installed you shouldn't have the -20 kernel. Check that - there are a few hits on a quick search of the issue.

If you are running the -19 kernel try to add this to the end of the  kernel line you are booting with 
```

clocksource=hpet
```

> ubuntu 7.01would be the version of ubuntu you are using - although it's more likely to be 7.10 or 8.04 :) the kernel is different.

---

### Post by Elfy on 2008-07-28
If you can't work out how to edit it in grub, can you boot the recovery mode? If you can you can edit it there with nano

```
nano -B /boot/grub/menu.lst
```

will open the file to edit

add it to end of kernel line - eg

> title		Ubuntu 8.04.1, kernel 2.6.24-20-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-20-generic root=UUID=ccf8f1c4-97d0-4544-a0ee-04088d5d67a9 ro quiet vga=771 splash [COLOR="#ff0000"]clocksource=hpet[/COLOR]
initrd		/boot/initrd.img-2.6.24-20-generic
quiet

To exit and save - Ctrl+O, enter and Ctrl+X

---

### Post by AlexRulz on 2008-07-28
I just restarted the machine and had a go, mine doesnt say 

Ubuntu 8.04.1, kernel 2.6.24-19-generic

Instead of the 19 on the end its a 16, so it looks like this:

Ubuntu 8.04.1, kernel 2.6.24-16-generic


FORESTPIXIE:

when i boot into recovery mode it runs a long string of what looks like POST test and freezes up, cant type anything, have to reset the machine manually.

---

### Post by Elfy on 2008-07-28
That's ok you are using an old kernel - you'll have to either boot the livecd and edit it there or you can use grub.

When you get the menu - use any arrow key to stop the countdown - I think that you use e to edit the start options - check the little menu at the bottom.

IF it is e - you will then be presented with the section for that start option  - go the the kernel line and add the clocksource line - then I'm not sure which option to boot it - you'll need to read the options you are given - I wouldn't save it if you can boot without saving.

If it boots ok then make the changes from within ubuntu - 
```
gksudo gedit /boot/grub/menu.lst
``` will open it for editing.

If you do get in you will get an update option - don't do that yet, lets try and get you booted properly first.

I have to add that I've personally never needed to add that option and am going from a thread from a couple of months afgo.

---

### Post by AlexRulz on 2008-07-30
Okay, sorry im a bit late, i had a fiddle with it and have been a bit too busy the last few days. I am in ubuntu now on the live CD, i still have my original installation of the OS on my hard disk but i am running off the CD.

Forestpixie:

I saw your post and where you told me that if i can get into ubuntu on the live CD to type that code in, but where do i type it?

---

### Post by Elfy on 2008-07-30
Open terminal (accessories menu) and open nautilus as root

```
gksudo nautilus
```

Then find the partition which has your installation on it, navigate to boot then grub - you should see the menu list in there - you can open it with the text editor.

---

### Post by AlexRulz on 2008-07-30
well, i rebooted and had a quick look, my changes were saved to the end of the kernel file but it still did the same thing just froze up at the "starting up" screen. And my recovery console is the same scrolls through a lot of stuff and says at the bottom when it stops: "clocksource tsc unstable.

It also has a few lines in there that say iomem range could not be reserved.

---

### Post by bsmith1051 on 2008-08-02
> **AlexRulz said:**
> I have always used windows but after seeing Ubuntu on APC mag i decided to burn the ISO and give it a go.
Is that 8.04 or the 'service pack' 8.04.1 ?  If it's the former you should try downloading the update and creating another Live CD.

Also, I want to tell you how sorry I am that you're having all these problems.  Unfortunately, Linux does not get the same level of compatibility testing as Windows (it's boring so no one volunteers to do it) and so it's almost inevitable that you'll have to deal with this kind of bs on occasion.

---

