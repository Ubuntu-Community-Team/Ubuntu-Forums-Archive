---
title: "Boot option problem"
date: 2018-08-29
forum: Hardware
---

### Post by oakridge on 2018-08-29
Hello. I have had a bit of  break from Ubuntu but now I need to set up a network machine that works - Windows 10 - grrrr.
I bougut a HP Pavilion desktop with Wndows 10 home with the intention of replacing it with Ubuntu - no problem.  They have changed the BIOS and addad UEFI which I have compelely failed to negotiate to change the boot drive to the CD.  I have tried HP's forum without a lot of success.  The HP Pavillion with Windows 10 Pro which I also need has the standard BIOS I have some software on that machine which would not transfer like the Nikon camera apps.  I have already tried Currys and HP without a lot of success so I hope you can help.
Thenk you.
Malcolm Brown

---

### Post by dodot on 2018-08-29
try hitting F12 on boot to get to boot options

---

### Post by oldfred on 2018-08-29
The Windows software will not run on Ubuntu. 
So do you want to dual boot desktop?

HP is one that violates UEFI standard that says NOT to use description as part of UEFI boot. And only valid description is "Windows Boot Manager". But some with newer HP do say they have installed Ubuntu without issue.
You need to check if there is a newer UEFI from HP for your system. That may resolve a lot of issues.

I have only used flash drives for installer, and now mostly directly boot ISO with grub2 from one hard drive to install to the other drive.
But whether DVD or flash drive, your UEFI boot menu should offer two ways to boot. One usually is clearly labeled UEFI:xxx and other just xxx which is then the BIOS/CSM/Legacy boot.
How you boot install media UEFI or BIOS is then how it installs.

Lots of info on UEFI installing and explanations with links to even more info in link in my signature.
Only 9 "easy" steps to install in UEFI boot mode. And once you download ISO and have working live installer, the install to an internal drive is about 10 min. My full installs to slow external flash drives is over 45 minutes as writes to flash drive is very slow.

So are you erasing Windows? Even so, I would still so a full backup. Many have that one application (like a camera app?) that they must have and then want Windows back.

And for networking with another Windows computer, start a new thread after you have installed in the networking sub-forum. Years ago I used Samba with my XP & Ubuntu systems. But Windows updates, Windows virus updates, Windows firewall updates and my every 6 months Ubuntu update ( I now run LTS as main install), had me reconfiguring Samba all the time. So I installed Ubuntu as dual boot on Windows machine and use NFS.  That I could script install & settings so very easy to reconfigure. There are some easier ways now, that those who know networking have posted, but I have NFS working, so have not changed.

---

### Post by oakridge on 2018-08-30
Hello.  Thank you for your help but I have solved the problem in a different way.  I found out that the UEFI BIOS is heavily geared towards Windows and even uninstalling it may not let another OS operate properly.  We went back to Curry's shop and had a chat with a different person who agreed with us and took the PC back and we bought an AMD motherboard, processor, memory and video card which will fit in the case we already have.  This was actually more expensive than the PC but we know that this will work.  We have a good team going because Christine has built a large number of machines over the years for various people and I have set them up.  Hopefully all will be fine now - fingers crossed.

---

