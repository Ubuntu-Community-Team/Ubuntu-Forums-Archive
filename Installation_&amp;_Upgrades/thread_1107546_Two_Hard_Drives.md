---
title: "Two Hard Drives"
date: 2009-03-26
forum: Installation &amp; Upgrades
---

### Post by SuperIntense on 2009-03-26
I want to keep my Vista on my computer and put Ubunto on my second hard drive. The problem is I do not want grub. I waould like to know if I take my windows hard drive out and install Ubunto can I put my windows back in and just pick which hard drive starts when my computer starts up? I do not want anything added or taken away from my windows.

---

### Post by daveg2 on 2009-03-27
You're doing it the way I prefer.  I take out my windows drive and put my Ubuntu drive in it's place to do the install.  Then there is no possibility of making a mistake and destroying my windows install.  Absolutely nothing is ever added or taken away from Windows.  My Windows drive is never touched by the Unix install.  Once Ubuntu is installed, I put my Windows drive back in.

What you're missing, though, is that Grub is still required.  Grub is the tool you use to decide which drive to boot.  After selecting Ubuntu, it's required to boot Ubuntu.  If you select Windows, Grub launches the original, unmodified, Windows boot loader.  The big news is that Grub is written only to the Ubuntu drive.  It doesn't modify the Windows drive in any way.  

What's really neat is that if the Windows drive fails, take it out and Ubuntu still works fine.  If the Ubuntu drive fails, take it out and Windows boots like it always did.

---

### Post by lindsay7 on 2009-03-27
I you install Ubuntu on the second drive as you mention and then put the windows drive back in the machine, how are you setting the bios to start in terms of boot order. It sounds like you have it boot to start the Unbuntu drive first. Is that correct. My other question is, when you do an ubuntu install on a single drive and grub is set up like there is only the one drive, how does it know that there is a second windows drive. One of my computers is set up with a single Ubuntu drive and I do not see or get a choice at start up.  If I were to add a windows drive to this machine would it set up like you mention and know that the windows drive was there.

Let me know.

---

### Post by Mark Phelps on 2009-03-27
Your one-OS-per-drive is exactly what I have done, also.

If you don't want to mess with GRUB, check out easyBCD at the the Neosmart forums.  That can modify the Vista boot loader menu to add Linux. It uses something they call "NeoGRUB" -- but don't know what that is. They even have how-to's that will walk you through doing that.

---

### Post by daveg2 on 2009-03-27
Mark, I prefer not to modify the Windows boot loader in any way, but that option would work the same way for selecting the OS to boot.

Lindsay, nothing is done with the BIOS.  The BIOS only knows enough to boot the primary drive.  Windows must be the primary drive or it won't boot. So when we unhook the Windows drive and put the Ubuntu drive in it's place, it is the primary drive as far as the BIOS is concerned.  As yet, there is no secondary.

When Grub installs on the primary drive during the LINUX install, it knows nothing about a secondary.  When the LINUX install is done, plug the Windows drive in the secondary position.  You then need to add a few lines of code to the Grub menu file to tell it about Windows.  

The sneaky part that Grub does for Windows is to electronically swap primary drives before calling the Windows boot loader.  Windows then is on the primary drive as far as Windows knows.

So for a Windows boot, the BIOS runs Grub on your LINUX drive, Grub swaps the drives, then runs the original untouched Windows boot loader.  That's why either drive can be removed and the remainder plugged into the primary position and you now have a single OS system with no changes needed.

---

### Post by lindsay7 on 2009-03-27
Very cool! Could you post the lines of code that you add to the grub file or post a screen shot of the grub menu.  Thanks for the help.

---

### Post by daveg2 on 2009-03-27
Here you go, Lindsay:  

# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

title Windows XP Home
map (hd1) (hd0)
map (hd0) (hd1)
root (hd1,0)
chainloader +1

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script

If you copy and paste, you'll be OK.  If not, be sure to notice that there are 2 spaces in the map lines and one in the root and the chainloader lines.  It's pretty obvious in the editing box, but didn't look so clear in the post.

---

### Post by lindsay7 on 2009-03-27
Thanks again for your help.

---

### Post by daveg2 on 2009-03-28
You're welcome.

---

### Post by SuperIntense on 2009-03-28
Where do I put this information or how do I put in this info? I want to do this but not sure where all this goes that you posted for this boot sequence

---

### Post by daveg2 on 2009-03-28
Open a terminal,
cd /boot/grub
sudo cp menu.lst menu.lst.org   # So you have a backup
sudo vi menu.lst
arrow key down to just before "### BEGIN AUTOMAGIC KERNELS LIST"
i to put you in insert mode
copy one line and paste into vi, enter to put you on the next line
repeat until done
[escape]:wq to save it and exit.

There's probably an easier to learn GUI editor on the Ubuntu menu, but I've never used it.

This thread suggests instead of sudo vi, use gksudo gedit.  That's a graphical editor that might be easier to use.  He also gives a very clear description of exactly the technique we're talking about.
[http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)

---

