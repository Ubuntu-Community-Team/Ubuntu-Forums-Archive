---
title: "Karmic live CD and installation crashes"
date: 2009-10-29
forum: Installation &amp; Upgrades
---

### Post by SDL on 2009-10-29
Hi everyone.

I have downloaded and burned 32-bit Ubuntu 9.10 but when I use the live CD it loads the desktop and about 10 seconds later the mouse and keyboard become completely unresponsive.

If I try to install instead of using the live cd, the initial installation screen loads but I cannot choose my language before the computer crashes.

The image md5sum was fine after downloading 9.10 and I have checked the CD for errors. I have also tried Xubuntu with the same result.

I am currently using 8.10 as I had the same problem with 9.04 except that I could successfully install that version. The problem was that having installed it, I had the same crash as with the live cd after booting.

Here is a list of my hardware, please let me know if I can provide any more detail:
Processor: AMD Athlon 64, 2000 MHz (10 x 200) 3000+
Motherboard: Foxconn 755A01/K8S755A Series
RAM: 1536 MB (PC3200 DDR SDRAM)
Graphics card: NVIDIA GeForce FX 5700 (128 MB)
HDD: WDC WD1200JB-00GVC0 (111 GB)

Thanks for reading.

Stephen.

P.S. In case anyone reads through my past threads, I am still booting with ACPI=off but I have tried without this command and it makes no difference to the current problem.

---

### Post by nixed242 on 2009-10-30
Hi, I feel your pain. I have a similar computer setup to yours and I experienced the same exact issue when I ran the Live CD of Karmic and after installing it with the Alternative CD. Same problem. As soon as I boot up to the desktop, I get 10 seconds of using it before I freeze and have to hard boot. 

It's frustrating and I'm pretty ticked off about it. I was running 9.04 before and was having random freezes every now and then, probably because I Upgraded from 8.10, but not being able to boot into the desktop is an **EPIC FAIL!** 8.10 worked flawlessly for me. I've tried the boot command parameters to no avail either. When installing 8.10, I figured out that I had to disable ACPI in my bios in order for 8.10 to install. 

This is frustrating, and I hate to say it, but Windows 7's desktop probably wouldn't have crashed the first time out of the box. I'm just tired of all these work arounds for a bug. I actually tried booting in again this morning before work, and this time I disabled my Firewire drive and I was able to get into the desktop without a freeze. I still think that's not the issue though. I'm sure I'll freeze when I try to install the NVIDIA driver. 

Tonight I'm going to go back and give it another shot and hope it works. I may reinstall Karmic first as Grub doesn't seem to have been installed correctly on my system either. It searches the hard drive for 20 second before showing the boot screen. 

Anyone have a solution for us or a suggestion?

My Setup -
[B]Processor: AMD Athlon 64, 2000 MHz 3200+
Motherboard: FIC KT800-T 
RAM: 1536 MB (PC3200 DDR SDRAM)
Graphics card: NVIDIA GeForce 7600 GT (512 MB)
Trying to Install Karmic Koala 64 Bit Version[/B]

---

### Post by SDL on 2009-10-30
Thanks for your reply. It's nice to hear that I'm not suffering on my own!

It does sound a fairly similar problem although 9.04 was completely unusable for me whereas it seems it worked a bit for you.

Hopefully somebody else can help? It's depressing to think that in April I'll have to downgrade to 8.04 as 8.10 will no longer be supported and I won't be able to use the newer releases.

---

### Post by nixed242 on 2009-10-30
So I came home tonight and re-installed Ubuntu. For some reason, when I start up normally, it still crashes ont he desktop. When I boot up in Recovery Mode, go to a Command prompt, StartX, I can get into the desktop, the Nvidia Proprietary driver loads, and NOTHING CRASHES! 

Someone on IRC was kind enough to point out that it's GDM that starts up X on a normal boot using XSessions. From the Recovery Mode Command prompt, I typed in GDM and it's running fine. Could it be something in my Kernel that is causing this crash? What can I do?

---

### Post by SDL on 2009-10-31
I've installed using the alternate CD now. The same thing happens to me as to you, loading Ubuntu normally causes the crash but if I go to recovery mode and type 'gdm' it works fine.

I think seeing as the live CD issue is no longer a problem for me that I will mark this thread as solved and start a new one regarding this problem. I'll post a link here.

[Here is the new thread.]("http://ubuntuforums.org/showthread.php?p=8206633#post8206633")

---

