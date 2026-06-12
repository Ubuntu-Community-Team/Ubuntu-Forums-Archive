---
title: "Compaq nc6220 and large hard disk"
date: 2009-10-15
forum: Hardware
---

### Post by billzinn on 2009-10-15
So I believe I have finally determined why this Compaq NC-6220 won't 'boot' Ubuntu  ("loading grub... error 18") - and this is obviously because the BIOS is not able to 'translate' this 250 GB IDE properly for grub.
But as a 'rank amateur' with Ubuntu and Linux in general, I have to ask and maybe someone will 'enlighten me' as to why Windows XP SP3 will access and use the entire hard disk- and yet Ubuntu "Feisty" (9.04) cannot....?  Sorta makes my bragging about Ubuntu kinda 'loose wind'... dammit.
 
I have no doubt this is most probably due to this very 'limited' BIOS in this laptop, which is really unfortunate....  HP does not have a 'newer' BIOS flash than what this is running (hmm... possibly there's a 'rollback' that might work?  Hadn't looked at that...) - and there are not capabilities within the BIOS to reconfigure the hard disk for LBA or 'normal' or anything else, actually.  It just "auto recognizes" the hard disk.
So I guess my great idea of sticking a really big hard disk in this little pokey machine is not gonna work, if I want this operator to 'experiment' with Linux. 
Guess I'll have to go find a smaller hard disk and install on that.
 
Anyone wanna buy a brand new Seagate 2.5" 250 GB IDE...?? (jus' joking...!! big hard disks work for other uses, such as backups...)

---

### Post by billzinn on 2009-10-15
Oops.. my bad...
Ubuntu 9.04 isn't "Feisty" it's "Jaunty" - I stand corrected..
And it also appears that this laptop will not accommodate an IDE disk beyond (from what I saw in other places - mostly on European sites) that this laptop has 'difficulties' with hard drives over 60 GB when it comes to Linux and this 'limited' BIOS chip...
 
And a few more things than I really wanted to know.... 
 
Maybe I should ask her if she wants a new laptop - one that CAN accommodate a large hard disk and Ubuntu.
 
Live and learn...

---

### Post by Nick_Kats on 2011-12-31
If only I had read your post earlier. I did the same thing and now, every time I try to boot ubuntu with a 250GB disk on the HP, the grub-rescue runs.

Funny thing though, there is no problem with Windows XP :confused:

---

