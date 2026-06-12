---
title: "Bad sectors only in Ubuntu"
date: 2011-11-26
forum: Hardware
---

### Post by davethewave83 on 2011-11-26
I removed Windows from a family member's PC and convinced them to use Ubuntu instead. After I did this, I saw that the disk utility program shows that there are 817 bad sectors remapped on the 1TB drive. 

I couldn't make heads or tails out of how to run badblocks myself but followed a guide online, it said there were no problems found. 

The hard drive is a 1TB Seagate so I used the SeaTools for Dos program and it found no problems with the drive. I then re-installed windows and did a scan on the drive with surface test, it reported no problems. 

I also used an old program called spinrite, which reported no errors on the drive (but crashed later on due to the large size of the drive causing an overflow) 

so no other program or utility I've used is able to detect bad sectors, just the Ubuntu disk utility. 

I have an exact matching 1TB model (same model number and size) which says there are no problems, even in ubuntu. 

anyone have any idea what's up and why these bad blocks would show up in one program and not others?

Seagate says I can RMA it, but if there's nothing wrong with the drive they can refuse my RMA and send it back to me. I'm not sure I wan to go through all that if nothing is wrong with it, however, on the flip side I don't wan to use a potentially failing drive.

---

### Post by dandnsmith on 2011-11-27
I wouldn't care to be held to it, but I believe most tests will deem the HDD working if any bad blocks have been successfully mapped (as any read/write sequences will automatically be diverted to the working blocks by the hardware).

---

### Post by trundlenut on 2011-11-27
Try booting with UBCD and under the diagnotics entry under HDD try the bottom option (ViVard I think) and let that have a look at the hard drive.  I have a laptop and the windows 7 install on it claimed that the hard drive was 100% OK but when I tried to install Ubuntu gparted complained about bad sectors.

---

