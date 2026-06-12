---
title: "Error on boot - probably not GRUB2"
date: 2011-04-25
forum: Hardware
---

### Post by Manyette on 2011-04-25
I wonder if anyone would have any insight into this.  My HP G71 laptop had a keyuboard failurre.  In the process of replacing the keyboard I removed the CMOS battery. (Turns out I didn't need to do that!) After replacing the keyboard, and restoring my last backup with Clonezilla, everyting works just fine;

EXCEPT

On boot, GRUB automatically displays (Ubuntu is the only OS on the machine), and when I select the default OS (10.04.2) the screen blanks and I then get the following on the screen:

Error: No parameter furnished.
Hit any key to continue

Following this, everything boots and works normally as far as I can tell.  I have no idea where this message comes from, since is appears to be after GRUB, but I suppose it is possible.

If anyone has any guesses as to what is going on here, I would greatly appreciate your input.

---

### Post by Manyette on 2011-04-25
Downloaded the proposed kernel update, and that removed the error message. I'm still not sure why it happened, since Clonezilla has never let me down before this, but at least I know it was some file in the kernel, and not GRUB2.

---

### Post by wilee-nilee on 2011-04-25
Clonezilla saves the mbr you had on cloning and reinstalls it. So whatever the bootloader in the mbr had there before is there again lets have a look at it and everything else. Should have been reloaded by a kernel update but hard to tell. 

So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the **(#)** in the reply panel this makes code tags paste all the text in between.

Upon rereading it seems your okay is this correct?

---

### Post by Manyette on 2011-04-25
I did run bootscript, and it had no useful info.  Then I found (see the previous post) that the problem was in the Kernel files.  I'm using the latest version of Clonezilla, and I fear there is a bug in the new version. I'm going back to the previous version, which has alwasys worked well, without any similar problems.  If that doesn't show a similar problem, I'll know what is wrong.

---

### Post by wilee-nilee on 2011-04-25
> **Manyette said:**
> I did run bootscript, and it had no useful info.  Then I found (see the previous post) that the problem was in the Kernel files.  I'm using the latest version of Clonezilla, and I fear there is a bug in the new version. I'm going back to the previous version, which has alwasys worked well, without any similar problems.  If that doesn't show a similar problem, I'll know what is wrong.

I think what happened is that you got a grub update with the other updates. A grub update would reload the mbr, if you had a earlier grub loaded there from clonezilla reloading I'm not surprised to see an error. I have reloaded with clonezilla and gotten the lovely grub> prompt, only because of the change of my HD 4 OS's right now and different partition numbers.

Clonezilla nicely saves the mbr for you, but I wouldn't rely on it for complete reloading past the partition or a full HD. Fortunately reloading a mbr is quite easy, at least nowadays.

Your thinking that it is a kernel file may be correct but I have never heard that before, it seems like a assumption due to an update, look in the history for a grub update as well.

---

### Post by Manyette on 2011-04-25
You may be correct.  I have no way to be sure.  I am sure there was no grub update in that period, and I have used Clonezilla many many times in the past, without any problems. (I guess I screw up a lot!) But I am suspicious whwn a new and massively changed version of Clonezilla is used. And just loading nothing but the new kernel by enabling the proposed update function makes is seem pretty certain that it is some file in the kiernel download.  At least, that's my assumption until I can test against an earlier version of clonezilla.  It has been solid and a real gem up until this incident.

---

