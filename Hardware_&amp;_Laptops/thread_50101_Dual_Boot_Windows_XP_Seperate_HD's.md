---
title: "Dual Boot Windows XP Seperate HD's"
date: 2005-07-19
forum: Hardware &amp; Laptops
---

### Post by markdone on 2005-07-19
I had a 40 GB HD with WinXP Pro only on it (it was master drive in NTFS format).  I wanted to make a linux server and be able to dual boot when necessary.  I bought a 200GB HD and made it the master HD (Jumpers and Cable) and made the old 40GB slave (jumpers and cable), then I installed Ubuntu.  I can mount the HD and view it so I know that it is working, but when I try to boot to it with GRUB it prints four lines to the screen and resets faster than I can read them.  I want Linux to have the master boot record (if possible) so that when windows gets hosed I can reformat it without losing GRUB etc.  Any suggestions to what is going on.  I would try to look it up myself, but I can't read the text because it is too fast.  Thanks in advance for the help.

Mark

---

### Post by Lord Illidan on 2005-07-19
The MBR has to belong to Windows partition, if I am not mistaken....
And you can re-install Windows without flushing Ubuntu...

Look at what I did..

I had Windows on 60 gig hdd...Fedora on 40 gig hdd..
MBR with grub installed on Windows hdd

Windows failed....

So I booted to Fedora, copied the files from Windows hdd to Fedora hdd for a back-up

Then I disconnected Fedora.

Afterwards, I re-installed Windows, which thought there was only one hard drive and it could use it all...which it did..

I then re-installed grub
And I had a dual booting system once more...and I could copy the backed-up files from fedora 2 windows with ext2fs...

---

### Post by markdone on 2005-07-19
So to fix my current setup I would make the windows drive the master again and then I install GRUB to the windows drive.  When i intall grub on the windows partition will it see the other disk and rocognize Ubuntu or do I need to print out my menu.lst file so that I can copy it?

Mark

---

### Post by YorYor on 2005-07-20
Here, check this out. Worked great for me. :)

[http://forums.gentoo.org/viewtopic.php?t=18319](http://forums.gentoo.org/viewtopic.php?t=18319)

---

### Post by markdone on 2005-07-21
[QUOTE=YorYor]Here, check this out. Worked great for me. :)

[http://forums.gentoo.org/viewtopic.php?t=18319](http://forums.gentoo.org/viewtopic.php?t=18319)[/QUOTE]


That works great.  I got my old windows HD up and running good post!!!

Mark

---

