---
title: "DVDs misidentified as blank"
date: 2005-04-12
forum: Hardware &amp; Laptops
---

### Post by Declan on 2005-04-12
Hi all,

I'm not sure what kind of problem I have, or even if it really is a problem, or just some setting I changed by accident.
When I put in a DVD these days, the system attempts to mount it, and decides it is a blank cd.  As a result I can't play any DVD.  
In the mutimedia tab of the Removable Drives and Multimedia Storage dialogue I have "Play with Totem" enabled.

The same is true whether I try to read with Totem, Kaffeine, VLS, Ogle, Gxine, Xine or whatever.  
The drive appears to work fine for other things apart from DVDs.
(It *is* a DVD-Rom, by the way, and it did work until recently).

What am I missing/overlooking/ignoring?

Thanks,

Declan

---

### Post by Declan on 2005-04-13
I'm still trying to figure out this problem with the DVDs. 
 If I put in a data disk into the drive, the disk is properly mounted. 
If I put in a DVD (with a film on it) in, the system treats it as though it were a blank CD-R.

Am I correct in saying that a DVD is not mounted as such?
What does the system normally do when you give it a DVD with a film on it?  It doesn't mount it, what does it do?  Maybe if someone gives me a clue, I'll be better able to identify my problem, and better able to go look for a solution.

Anybody?

Thanks,

Declan

---

### Post by Declan on 2005-04-13
I don't know if this can help anyone see the problem: the output of dmesg >

dmesg | tail
  "25 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 "
hdc: packet command error: status=0x51 { DriveReady SeekComplete Error }
hdc: packet command error: error=0x30
ide: failed opcode was 100
ATAPI device hdc:
  Error: Medium error -- (Sense key=0x03)
  (reserved error code) -- (asc=0x57, ascq=0x00)
  The failed "Read Cd/Dvd Capacity" packet command was:
  "25 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 "
cdrom: This disc doesn't have any tracks I recognize!

I imagine if I knew what this meant, I'd be on my way to understanding the problem.

Declan

---

### Post by Declan on 2005-04-14
Me again, talking to myself.

I suspect the problem I've described above is easily resolved.  Any chance of a pointer from anyone?   O:)

---

### Post by wouter78 on 2005-04-21
Hi Declan,

I had (and still have) the same problem. One thing that works for me is to log out and then log in again with the dvd in the player. When I do this I get two mounts, the second is the dvd mounted as a dvd.
Maybe is is not such an elegant method, but it works.
I don't know how important it was for the dvd-playback, but I removed Totem for Gstream and installed Xine and Totem for Xine. These two work very well.

Wouter

---

### Post by Eversmann on 2005-09-25
I have the same problem with 5.04 updated with Synaptic.

I have two drives, one is a toshiba dvd-rom and the other is a pioneer dvd-rw. 

When i put a cd disc works perfectly, but with a dvd disc the CD recorder window appears and treats it like a blank-cd

I've been searching the forum and internet but just found other users with same problem and no solution.

Inserting dvds and cds on the pioneer dvd recorder works perfectly.

If i mount the drive manually works ok too.

No solution or suggestion from the devs? Is the problem fixed in Breezy?

thanks :-D

---

### Post by secstate on 2005-10-16
*bump*

I've got the same problem and no solutions.  This is with a new install of Breezy . . . pretty unfortunate a bug that's been around this long is still causing trouble in a new stable release.

---

### Post by Eversmann on 2005-10-16
Looking for a better eye-candy desktop i've installed kde and so run kubuntu.

Now i don't have problems with automount anymore. 

A problem with gnome and its automount.

---

### Post by hartertw on 2005-10-16
I'm having the exact same problem as Declan is.  Any solution would be much appreciated.  :)

---

### Post by GarciaCA on 2007-02-08
Same problem here...Ubuntu Dapper treats my verbatim DVD-RW as blank (most of the times) and ocassionally shows the data in it...in any case I can't copy files to desktop or open them for that matter. One week after migrating to ubuntu and still running into problems that need tweaking with the system...Should I give up? :(

---

