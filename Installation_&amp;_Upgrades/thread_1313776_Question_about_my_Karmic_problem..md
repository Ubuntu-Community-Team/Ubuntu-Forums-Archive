---
title: "Question about my Karmic problem."
date: 2009-11-04
forum: Installation &amp; Upgrades
---

### Post by Roasted on 2009-11-04
I have a problem with Karmic where it fails to acknowledge my 4 hard drives during installation. It'll pick up the main 2 drives, but it thinks the other 2 drives are raid - which is absolutely not true.

Secondly, after I install karmic, anything I edit in fstab with hard drives backfires and errors out when they actually try to mount.

Question is this: I know I could just get updates to fix fstab whenever they get published. Okay, fine. But my problem where the hard drives fail to be recognized during the installation... that happens on the LiveCD level, something that doesn't see updates.

Is it possible that Ubuntu will release a revised Karmic LiveCD iso that might cure this problem? Or is it likely I'll be waiting until 10.04 to do any upgrading?

---

### Post by Ginsu543 on 2009-11-04
I had similar problems as you did but was able to work around it by removing dmraid from my system. You can do this by typing "sudo apt-get remove dmraid" (without quotes) in Terminal or going into Synaptic and removing dmraid and its dependent files manually. I too had the issue of the installer thinking that two of my drives were in RAID when I didn't even have the RAID option turned on in BIOS. Once I removed dmraid, however, everything began to work normally.

---

### Post by Roasted on 2009-11-04
> **Ginsu543 said:**
> I had similar problems as you did but was able to work around it by removing dmraid from my system. You can do this by typing "sudo apt-get remove dmraid" (without quotes) in Terminal or going into Synaptic and removing dmraid and its dependent files manually. I too had the issue of the installer thinking that two of my drives were in RAID when I didn't even have the RAID option turned on in BIOS. Once I removed dmraid, however, everything began to work normally.

Gosh I wish I could remember what I did, but I feel like I did that and at that point fstab was still erroring out...

---

### Post by wylovan on 2009-11-14
> **Ginsu543 said:**
> I had similar problems as you did but was able to work around it by removing dmraid from my system. You can do this by typing "sudo apt-get remove dmraid" (without quotes) in Terminal or going into Synaptic and removing dmraid and its dependent files manually. I too had the issue of the installer thinking that two of my drives were in RAID when I didn't even have the RAID option turned on in BIOS. Once I removed dmraid, however, everything began to work normally.

Thanks Ginsu, this is exactly what I needed.  After the 9.04 -> 9.10 my system was completely hosed.  I was so very close to reinstalling (and the current installation started w/ 6.10).  I wasn't convinced it would even help.  Thankfully I found your post, which identified [FONT=Courier New]dmraid [/FONT]as the culprit.  Once I removed it all is working well again.

Cheers to you!

---

### Post by Ginsu543 on 2009-11-14
> **wylovan said:**
> Thanks Ginsu, this is exactly what I needed.  After the 9.04 -> 9.10 my system was completely hosed.  I was so very close to reinstalling (and the current installation started w/ 6.10).  I wasn't convinced it would even help.  Thankfully I found your post, which identified [FONT=Courier New]dmraid [/FONT]as the culprit.  Once I removed it all is working well again.

Cheers to you!
Excellent! Can't take too much credit as I found out about dmraid by combing through these forums. Just passing on the knowledge and the positive result. This is what I love about Ubuntu/Linux: people helping one another get the most out of their computing experience.

---

### Post by Roasted on 2009-11-14
Ginsu - I don't understand. Do you run apt-get remove dmraid during the LiveCD and then run the installer? Or do you install Ubuntu on one drive, remove dmraid, and then add the drives via fstab?

Is this a problem with the linux kernel or ubuntu karmic itself? Because I remember booting my system to a GParted  LiveCD and I had the same issue in the partition editor with how it viewed my drives. Very weird.

---

### Post by Ginsu543 on 2009-11-14
The former, not the latter. You boot into Ubuntu using the LiveCD (try out without installing). Once you're at the desktop, open Terminal and run sudo apt-get remove dmraid. This will remove dmraid from memory (obviously not from your hard drive since you haven't actually installed the OS). Then exit Terminal and run the installer. I'm not sure, but I think it may be a problem with the partitioning software within the installer or maybe with dmraid itself.

---

