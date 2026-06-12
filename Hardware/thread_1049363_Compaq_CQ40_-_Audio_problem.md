---
title: "Compaq CQ40 - Audio problem"
date: 2009-01-24
forum: Hardware
---

### Post by salem7 on 2009-01-24
The audio in my Compaq CQ40 does not work. The output of lspci|greo Audio produced the following:

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)

Can you plz assist me in getting it up and running. TQ.

---

### Post by swudee on 2009-01-24
Hi Salem7

If you searched the archives you would find the answer:p

[http://ubuntuforums.org/showthread.php?t=912896&highlight=ich9+no+sound&page=3](http://ubuntuforums.org/showthread.php?t=912896&highlight=ich9+no+sound&page=3)


The solution is quite simply.
First:
Code:

"  gksu gedit /etc/modprobe.d/alsa-base "

Then add the following to the end of the file:
Code:

"  options snd-hda-intel enable_msi=1  "

Run the first line in terminal, Without the quotation marks. (Applications/Accessories/Terminal to open the file alsa-base.
Then add the second line to the bottom of the file. save the changes and reboot. The sound should be fine:)

---

### Post by salem7 on 2009-01-24
It works! Tq very much, Swudee. I did search in the forums but couldnt find the solution. U r a life saver :D

---

