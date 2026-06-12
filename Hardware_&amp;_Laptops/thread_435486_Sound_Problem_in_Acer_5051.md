---
title: "Sound Problem in Acer 5051 ?"
date: 2007-05-06
forum: Hardware &amp; Laptops
---

### Post by defri on 2007-05-06
My laptop have a sound problem after i install ubuntu 6.10 edgy. The sound never out from my speaker. 
What is the problem ? I also install XP in my laptop and my sound card known as Realtek chipset.

---

### Post by EduMaxwell on 2007-05-15
I have an Acer Aspire 5051 and had a similar problem. You may have already done this, but in ALSA mixer go to Edit > Preferences. There you will find a number of unselected options, possibly including a "surround" option. Using trial and error (by selecting certain volume controls and making sure they are NOT muted), you might find the solution to your problem without going into terminal mode. After a lot of sweat and tears and reconfigurations, I finally solved my problem with this simple approach. Try it and let me know if it works for you.

A clearer description of the same process can be found here:
[https://help.ubuntu.com/community/DebuggingSoundProblems](https://help.ubuntu.com/community/DebuggingSoundProblems)

---

### Post by thrasherbcn on 2007-09-12
Hi, can anyone here provide with a right *.alsarc* that maps all lines into the correct names? In my 5051, I have to assign the volume control to the surround line.

---

