---
title: "External Harddrive has to be remounted after reboot"
date: 2007-09-29
forum: Hardware &amp; Laptops
---

### Post by zhanglini on 2007-09-29
My EXTERNAL drive (I have two partitions: ext3 and FAT32) SOMETIMES disappears after reboot and has to be remounted. Is the any reason behind this? can it be fixed?

---

### Post by zhanglini on 2007-10-01
Hmmm, still trying to figure out what to do....:confused:

---

### Post by noynac on 2007-10-01
Have you tried the Gutsy beta? I had a similar problem with an external hard drive under Feisty, but it now works fine under Gutsy. So, if you haven't tried it, you may want to give Gutsy a go when the final comes out in a few weeks.

---

### Post by zhanglini on 2007-10-01
Thanks for the suggestion.
I will wait till the final version comes out in 2 weeks, I am a nooobie, beta is too much for me.

---

### Post by zhanglini on 2007-10-02
Ok, after monkeying around, I formatted my X HD into X3 and NTFS.   However, X3 only has <2Gb, instead of >100 Gb.  I haven't even copies anything yet.  Where is all the space?
This Ubuntu experience is getting frustrating....

---

### Post by mazor on 2007-10-03
hello. 

Not sure if I can be much help. But how about checking you have "evms" installed. People have been noting loss of USB devices post boot, once they removed this application. 

Symptoms are the automount works, after they unplug and replug in USB devices post boot into Ubuntu.

Mazor

---

### Post by zhanglini on 2007-10-03
Thanks for the suggestion, but I already got rid of X3/FAT partitions on my external --- I have two NTFS now.
Both of them auto mount and there is no loss of volume.
It seems Ubuntu has problem with X3 (its format) and FAT (the format it shares) but NTFS (the one winnows use) is fine.  Speaking of altruism on Ubuntu's part....

---

### Post by Linicks on 2007-10-03
> **zhanglini said:**
> 
It seems Ubuntu has problem with X3 (its format) and FAT (the format it shares) but NTFS (the one winnows use) is fine.  Speaking of altruism on Ubuntu's part....

Well, I think that is a silly statement to say the least.

I expect what is happening here is the the device is designed for MS crap, and it expects a MS file system - this I guess, makes it wake up quicker and therefore present itself to the machine/OS at boot in a timely manner.

It would not surprise me if this was a deliberate design 'feature' to slow down the device if it hasn't a MS file system.

Remember all these devices work because of GNU/Linux developer people efforts trying to get them to work, with little, or perhaps, NO technical information at all from the manufacturers.

Nick

---

