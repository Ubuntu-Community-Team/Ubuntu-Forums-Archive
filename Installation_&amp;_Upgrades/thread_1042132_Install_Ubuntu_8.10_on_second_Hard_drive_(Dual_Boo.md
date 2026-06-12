---
title: "Install Ubuntu 8.10 on second Hard drive (Dual Boot)"
date: 2009-01-17
forum: Installation &amp; Upgrades
---

### Post by Yacobito230 on 2009-01-17
Hello.  I am a complete new to Ubuntu and Linux so I apologize if I don't provide enough information right away.  So, I have a desktop that is running Windows XP Prof. on its own hard drive.  I have a second 80Gb hard drive I wanted to put Ubuntu on.  I downloaded the standard desktop edition and burned my iso.

While trying to install I came across a message that said something to the fact that I could not boot from the CD, so it installed something that I am assuming told my HD to give me the option to boot to Ubuntu CD at start-up. Once I restarted I had the option to boot to Ubuntu and so I did.  I ran through the installation fine, took out the CD and rebooted.  

I choose Ubuntu and after a couple minutes just came to black screen with white lettering, which looked very DOS like and just sat there.  I will try to find out what it says exactly, but I suspect my option to boot to Ubuntu is still directing me to the CD, not the new install on my second hard drive.   

Any help would be greatly appreciated.  Again, I new to Linux, but I can try to find any information that is relevant to help trouble shoot my issue. Thanks! 

Jacob

---

### Post by thezood on 2009-01-17
> **Yacobito230 said:**
> 
I choose Ubuntu and after a couple minutes just came to black screen with white lettering, which looked very DOS like and just sat there.  I will try to find out what it says exactly, but I suspect my option to boot to Ubuntu is still directing me to the CD, not the new install on my second hard drive.
Yeah, that information is important. The DOS like lettering could be a number of things. It's probably Ubuntu in text mode which is the stage before the graphical interface is started (that stage 'normal' users should never have to bother with, in the best of worlds). 

It's probably not the installation cd (however, you never know). The installation process creates a small program called 'grub', a boot loader, on your first hard drive. This is the menu that you chose Ubuntu from and that should direct the boot process to your Ubuntu drive when you select Ubuntu from the menu. The installation program that was installed from Windows should be gone by then. Also, if it were the installation CD, you'd be presented with the Live CD all over again.

The problem could be with your hardware being unrecognized (perhaps the graphics card) or something could have gone wrong with the installation. Please come back with what that DOS-like lettering says, especially the last lines. Can you type something there or is the computer frozen? Does Windows boot okay? What kind of PC do you use? Do you know what make your graphics card is?

At last, if you don't have any important things on the second hard drive that you wanted to use with Ubuntu, you could always reformat it and reinstall it. If you have the energy. :)

---

### Post by Yacobito230 on 2009-01-17
Thank you for the response.  Below is the exact screen and test that comes up.  Below that are the specs on my computer.  I recently put it together myself with some left over Christmas cash and processor from an older computer.  It runs Windows really well. 

Screen--------------------------------

Loading, please wait

BusyBox v1.10.2 (Ubuntu 1:1.10.2-1Ubuntu6) built-in shell (ash)
Enter 'help' for list of built-in commands.

(initframfs)_


Computer Specs-------------------------


Processor: P4 2.4 Ghz 400MHz FSB
Motherboard: Biostar P4M900M4 Socket 478 Motherboard 
Video Card: e-GeForce 8400 GS 512MB DDR2 PCIe Graphics Card
RAM: 4 GB

---

### Post by Yacobito230 on 2009-01-17
Oh yeah, one more thing.  The computer is not frozen.  I can type "help" and get the list of commands I can use.  I just have no idea where to go from here.  

-Jacob

---

### Post by thezood on 2009-01-17
After reading around a bit, I found some things. However, I haven't experienced this myself so if someone else has some tips, feel free to step in.

What you used to install Ubuntu was WUBI, if I understand you correctly. Apparently, this is a known bug of that system. WubiGuide ([https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)) and several threads here on the forum suggests that you try to repair your Windows file system first. To do that, run 'chkdsk /f' in Windows (Start->Run). Reboot into Windows to run the check. When the check is done and the Windows desktop shows up, reboot and try to boot Ubuntu again.

If that doesn't work, just write your results here again and we'll try something else.

EDIT: Reading some more, I realised this wasn't necessarily WUBI related and you probably didn't install WUBI at all.
Try this instead: 
- Press CTRL-ALT-F7. If you have a graphical interface, it should open then.
- Press CTRL-ALT-F2, CTRL-ALT-F3 and CTRL-ALT-F4 to open your other terminals. See if you see more information, error messages and stuff like that.
- Type 'return' or 'exit' at the prompt and press enter. If you're lucky, the boot process will continue.

Sorry for the confusion.

---

