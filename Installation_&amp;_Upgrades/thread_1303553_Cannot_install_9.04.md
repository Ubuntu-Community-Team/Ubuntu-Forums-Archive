---
title: "Cannot install 9.04"
date: 2009-10-28
forum: Installation &amp; Upgrades
---

### Post by ohgee on 2009-10-28
Hello All- I'm very much a newbie with Ubuntu and need help in installing it.

History:
1.  I want to install the OS under WinXP Pro. 
2.  I readied a 50 GB partition on another drive that's seen by WinXP and formatted it to FAT32.
3.  I downloaded the Ubuntu 9.04-desktop-i386 and Wubi 9.04 files to the same folder on my desktop.
4.  I ran Wubi for installation in the above partition.  
5.  The installation goes smoothly but freezes at the point where the message says, "creating the virtual disks".  After approx. 15 minutes I abort the installation.

Thinking I may have downloaded corrupt files I downloaded them again, with the same results- the installation always freezes at the same point noted above.

BTW- I assume that both files are 32-bit, but am not certain.

I certainly would appreciate expert help in the installation, and would like to thank you in advance.

---

### Post by earthpigg on 2009-10-28
hi,

if you want Ubuntu on it's own partition, then you want a true dual boot and not WUBI.

if you want WUBI (and it sounds like you do), then you don't need a partition. did you try making the virtual hard disk 50gb large without having 50gb free on your primary windows partition ("C Drive")?

(Ubuntu will just be a giant 50gb or whatever file on your "C Drive" hanging out somewhere in "program files.")

---

### Post by earthpigg on 2009-10-28
also,

> 3. I downloaded the Ubuntu 9.04-desktop-i386 and Wubi 9.04 files to the same folder on my desktop.

what tools are you using to mount the .iso file without actually burning a CD-R?

this is an [extra layer of complication]("http://en.wikipedia.org/wiki/KISS_principle") that may be causing you problems, as well.

---

### Post by shababhsiddique on 2009-10-28
Hello there..welcome to the community..you'll find it vry helpful. 

I am not an xpert, just a newbie like u.. You have not mentioned ur PC configurations. You also said that after 15 min you abort the installation.!  Be patient man. stuffs like these VM's take time to install. I have experienced somewhat similar freezing while installing in USB disk. Wait i think it will work

---

### Post by ohgee on 2009-10-28
Hey, earthpigg,

I initially successfully installed 9.04 in my 50 GB partition outside of WinXP, by first making a CD from the .iso file.  It worked perfectly.  I used Acronis to dual boot between the (2) OS's.

However, I found the arrangement too cumbersome, since I wanted direct access to my Win files.  I definitely want 9.04 under Windows, but I do not want to put Ubuntu in my Windows C:\ drive.

Wubi gives me a choice where do I want to install 9.04, and I chose the 50GB partition.  Burning a CD is not required when using Wubi, since it installs the 9.04 .iso file directly.

Hey, Shababhsiddique;

I also gave it 1/2 hour to get out of the "virtual disk" phase.  No indication that it was going anywhere.

Thanks both for responding.  Got any suggestions as to where I may look further for my problem?  Are there any Ubuntu experts available I can ask?

---

