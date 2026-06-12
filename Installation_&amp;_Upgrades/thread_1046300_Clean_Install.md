---
title: "Clean Install"
date: 2009-01-21
forum: Installation &amp; Upgrades
---

### Post by themagicmanfromtrent on 2009-01-21
Hi, I have a Dual-boot with Vista and 8.10, but I want to downgrade from Ibex to Gusty.

I'm not sure how that would affect Grub. Should I restore the windows boot files first, or can i just remove Ibex, and install Gusty off the CD?

Steps anyone?

---

### Post by snowpine on 2009-01-21
You can just install Gutsy over your existing Ibex partition (use the manual partitioning option). The installer is smart enough to update your Grub with the correct options. Good luck!

---

### Post by themagicmanfromtrent on 2009-01-21
Cool, thanks, needed that re-assurance. :)

---

### Post by themagicmanfromtrent on 2009-01-21
ugh... still not feeling very confident...

[img]http://img519.imageshack.us/img519/365/screenshotinstallfi5.png[/img]

Click forward?

---

### Post by snowpine on 2009-01-21
OK, so /dev/sda5 is your Ubuntu partition. Highlight it and click Edit Partition. Answer the questions like this:

Use as: ext3
Format: yes
Mount as: /

When you are done setting up this partition and go back to the Prepare Partitions screen (the screen shown in your post above), double check that /dev/sda5 is the only partition with a check mark in the Format? column. The line should look like: /dev/sda5  ext3  /  (checked box) 45345 MB (some random number) MB

Now it is safe to click Forward. :) 

At the last step of the installer, you will have one last chance to verify the changes... if the only partitions mentioned on that screen are /dev/sda5 and /dev/sda6 (your linux swap), then you are okay.

ps If you are at all worried, make sure you've backed up everything important. Partitioning is very safe but there is always a slight chance of something going wrong. ;)

---

### Post by themagicmanfromtrent on 2009-01-21
> **snowpine said:**
> 
Mount as: /


Mount point is currently /media/sda5. I make that / ?

---

### Post by snowpine on 2009-01-21
That is correct. / means the root directory. In other words, where you want to install the Linux filesystem. You are doing the right thing asking lots of questions and taking it step by step. I wish all posters on these forums were so easy to help. :)

Just as an aside, note that /sda1 through /sda3 are all mounted in the /media folder... that is good because it gives you the "address" to access your Windows partitions from within Ubuntu.

---

### Post by themagicmanfromtrent on 2009-01-21
done. thanks a lot for the reassurance. I took it step-by-step because it's an important and sometimes irreversible change... just wanted to make sure i got it right. Thanks a lot for your support.

Solved...

---

