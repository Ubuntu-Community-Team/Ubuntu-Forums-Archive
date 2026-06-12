---
title: "Dual-boot Windows XP and Ubuntu 9.04"
date: 2009-07-29
forum: Installation &amp; Upgrades
---

### Post by jedimattk on 2009-07-29
Okay, here's my problem. I have Ubuntu 9.04 currently installed on my computer, and I want to dual-boot with Windows XP (for games and iTunes mainly.) The thing is, every article I've looked at so far about how to do this relies on having Windows installed first. 

Is there a way to install XP on another partition or something without uninstalling Ubuntu? The only reason I'm asking is that I've configured this installation of Ubuntu a lot, changing the settings around and customizing the desktop, not to mention installing tons of third-party software. I will uninstall Ubuntu if I must, but I'd really rather not - and if I did, is there some way to back up my system settings?

Thanks for any help you can give me.

---

### Post by merlinus on 2009-07-29
[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

---

### Post by jedimattk on 2009-07-29
Oh god I have a really big problem!! 

Occasionally, when my computer is doing something that requires a lot of memory or something, it will just shut down instantly and start emitting a two-tone beep from the CPU. I looked this up on the internet and saw that it means the computer is overheating, so I always turn it off by the back switch when it happens, let it cool down, and turn it back on. It has never been too big of a problem in the past, and as I said it only happens when I'm running very graphically-intensive games or doing something that takes a very lot of memory.

So I was following the instructions to the letter. I backed up my GRUB, resized the partition, and booted from the Windows installation CD. I selected the unpartitioned space for Windows and told it to format using the NTFS file system - all very routine. It was about 20% through when it did the shut-down thing and started emitting the two-tone siren.

I reset the system from the back switch and tried to boot from the Windows CD again. After a very long time, it popped up and told me that a certain file could not be found and that Setup could not continue. I took out the CD and rebooted again, intending to boot into Ubuntu and go from there, but - again after a very long time - it simply told me "Error loading operating system" or something like that.

I have managed to boot the computer from the Ubuntu live CD, but I don't know what to do next. I have a feeling I should clear the unpartitioned space and start over again, but I have no idea how to do that, or if I should. Please help me!!!!!

(By the way, I have never seen it overheat and do that when I have my air conditioner on. I have it on in there right now to cool the room down a bit before trying anything else. I'm sure it won't overheat again if you tell me what to do from here.)

---

### Post by LFCESP9 on 2009-07-29
An alternative to dual-booting is downloading Suns VirtualBox. I've never tried gaming but I have connected my iPod and used iTunes with Windows in VirtualBox. 
Here are instructions:
[http://www.howtoforge.com/installing-virtualbox-2.0.0-on-ubuntu-8.04-desktop](http://www.howtoforge.com/installing-virtualbox-2.0.0-on-ubuntu-8.04-desktop)

This is the link I used and it worked very well.
Good Luck and hope this helps.

---

### Post by jedimattk on 2009-07-29
You don't understand. I CANNOT BOOT INTO UBUNTU!!

I've managed to boot from the Ubuntu live CD and deleted the unfinished Windows partition, which it said was somehow damaged. I am now trying to go through the XP install again and will post back when I have results.

---

### Post by LFCESP9 on 2009-07-29
Ah, my bad. I did not see your 2nd post.

---

### Post by jedimattk on 2009-07-29
Success! I had to take the side of my computer case off with the air conditioner blowing full blast, but I managed to get all the way through the Windows installation without overheating. I've since set up my GRUB bootloader and everything is working properly.

---

### Post by LFCESP9 on 2009-07-29
Good to hear it worked!

---

