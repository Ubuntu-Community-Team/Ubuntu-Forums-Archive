---
title: "Resume not working on HP Pavilion DV7-3160us"
date: 2012-09-29
forum: Hardware
---

### Post by Alexithymia on 2012-09-29
On resume there is a black screen with no backlight and the laptop seems to completely freeze. After wifi turns back on and the drives initialize, everything stops and the fans on full speed. Pressing caps lock does nothing and neither does numpad. Can anyone help? 

Thanks!

---

### Post by gordintoronto on 2012-09-29
What version of Ubuntu? Have you installed the Additional Drivers (nvidia-current)? Are you resuming from Suspend or Hibernate?

---

### Post by Alexithymia on 2012-09-29
> **gordintoronto said:**
> What version of Ubuntu? Have you installed the Additional Drivers (nvidia-current)? Are you resuming from Suspend or Hibernate?

I've tried 10.10, 11.04, 11.10, and 12.04. Currently on 12.04. I've installed fglrx but I have tried both that and radeon drivers (with KMS off and vga=0 in kernel parameter line). I'm attempting a resume from suspend.

---

### Post by cjhabs on 2012-09-29
Just a thought - do you have swap space configured to be at least the size of your RAM?

---

### Post by Alexithymia on 2012-09-29
> **cjhabs said:**
> Just a thought - do you have swap space configured to be at least the size of your RAM?

Swap is currently 5.7GB. None being used though. This laptop has 4GB of physical memory.

---

### Post by cjhabs on 2012-09-30
That is fine. swap is used to hold the memory contents during a suspend.
I gave up on suspending - it never restored my laptop correctly - I'll try again when I update to 12.04 although boot is supposedly much faster under 12.04 so it is not such a big deal but it would be nice to come back to my previous state.

---

### Post by gordintoronto on 2012-09-30
Actually, the swap is used during Hibernate, but not suspend. I've never had a problem with suspend and resume on my HP G62. Hibernate also works, but resuming from hibernate takes just as long as a cold boot.

---

### Post by Alexithymia on 2012-09-30
> **gordintoronto said:**
> Actually, the swap is used during Hibernate, but not suspend. I've never had a problem with suspend and resume on my HP G62. Hibernate also works, but resuming from hibernate takes just as long as a cold boot.

Well I'm not sure hibernate works, probably does considering the computer turns off after writing everything to disk. But sleep works completely fine in windows 7 and 8 (go figure).

---

### Post by Alexithymia on 2012-10-01
> **gordintoronto said:**
> Actually, the swap is used during Hibernate, but not suspend. I've never had a problem with suspend and resume on my HP G62. Hibernate also works, but resuming from hibernate takes just as long as a cold boot.

To give an update (and a bump), resuming from hibernate does not work. It'll go past GRUB but will stay stuck at the gray screen.

---

