---
title: "Trouble Installing 9.04"
date: 2009-05-11
forum: Installation &amp; Upgrades
---

### Post by rockstar1009 on 2009-05-11
I'm officially stuck. I have recently upgraded my PC experience in a big way, going from a 667 MHz P3 to an 2.6 GHz AMD Phenom. On the old Pentium PC, I had trouble getting Intrepid 8.10 to install in a stand alone partition, but did eventually manage to get it to install within XP (when trying to install on a standalone partition, the install disc would spin in the disc drive for about 10 seconds, and the PC would lock up, but I was still able to run it as a Live CD). All was well with the inner-XP install until a virus began to take out XP. I then switched to Mint 6 (Felicia), which had no trouble installing on its own partition, and I was able to run Mint much more reliably, since the XP partition continued to get more corrupted.
 
Then I upgraded. The XP partition was a lost cause, so I deleted it. Having lost the product key for XP, I installed Windows 7 as a stopgap, so I could still play Windows games while I tried to find the XP key. However, 7 made Mint un-bootable. I gave up for a month or two, as I've also just recently moved, and now that I've settled into my new place, I decided to download Jaunty. Again, I'm having trouble getting the installation to take hold. I've wiped the OS HDD, keeping documents stored on a second HDD. 
 
Jaunty will complete installation, but after the rebooting step, will hang at a black screen with a blinking white cursor after the mobo splash screen.  It never loads, and doesn't respond to hitting esc., insert, ctrl+alt+del . . . nothing. I've also tried installing within Windows 7, but whenever I try to run it, I get an error, saying "try (hd0,01): ntfs5: no wubildr."  I've tried installing it side-by-side with a Windows 7 partition, and I've tried installing it fresh after deleting everything on the HDD. I've tried the 32-bit and 64-bit versions of Jaunty and the 32-bit version of Intrepid, each of which check out when testing the disc for errors. I've tried every combination of installation with each distro. And for some reason, Mint won't even install on its own now, while it installed with no issues on the old Pentium.
 
While I've used Linux enough to have a grasp of what's going on with it, I am still a complete n00b at this. I could be overlooking something simple, which happens all too often with me - it took me a week of frustration of getting my internet connection to work because I'd set my modem IP, set my PC IP, but somehow never have them both set to the same address at the same time. If anyone has any tips/tricks/how-tos, please let me know - most of the install troubles I've seen in the forum appear to be installs that never complete - mine does seem to complete, it just never wants to boot afterwards.
 
Any ideas, suggestions, or nudges in the right directions would be greatly appreciated.  Thanks! :)

---

### Post by rockstar1009 on 2009-05-13
Bump!  Any suggestions?  Thanks!

---

### Post by rockstar1009 on 2009-05-14
I've now tried Kubuntu 9.04 and have the same issues.  I've instructed Mint, Kubuntu and Ubuntu all to use the entire disk during installation, and I've noticed that when using this option, the OS will go to a primary partition while the swap will be placed in an extended partition by itself.  Before now, I was using the manual option, and my setup would always end with both the OS and the swap area together inside the extended partition.  Is this possibly causing me trouble?

I've also run a GPartEd live cd, and noticed that there will be no flags present after install.  If I choose the ext3 partition (which the OS was installed to) and flag it as "boot", it will present "OS not found" after the mobo splash screen.  If I select the extended partition the ext3 partition resides within as "boot" (when doing the manual option as detailed above), it says "invalid boot device - please insert valid boot device and press any key" or something like that.  And if I don't put up any flags, all I'm greeted with is a black screen with an infinite blinking cursor after the mobo splash screen.

And of course, as mentioned before, whenever I try to install within Windows 7, I actually get the option of choosing the OS after the splash screen, but any time I choose my Linux distro, I get the "try (hd0,0): ntfs5: no wubildr" error.

Like I said, I'm still fairly new to Linux, and am probably making a very blatant and obvious rookie mistake.  If so, any pointers would be greatly appreciated.  Thanks!  :)

---

### Post by rockstar1009 on 2009-05-14
Bump for the evening shift . . .

---

