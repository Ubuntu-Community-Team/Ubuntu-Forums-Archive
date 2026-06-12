---
title: "Problem with sound card"
date: 2008-04-03
forum: Hardware &amp; Laptops
---

### Post by kuyangiang on 2008-04-03
I just install Ubuntu 7.10 in my laptop  ( acer aspire 5052) .I test carefully so all of driver work very well.But only sound card doesn't work.I don't know why. May you help me??? i need it very much. 

My Sound Card: Realtek ALC883 @ ATI SB450

And sorry about my English.it's too bad.:confused:

---

### Post by prshah on 2008-04-03
> **kuyangiang said:**
> I just install Ubuntu 7.10 in my laptop  ( acer aspire 5052) .I test carefully so all of driver work very well.But only sound card doesn't work.I don't know why. May you help me??? i need it very much. 
My Sound Card: Realtek ALC883 @ ATI SB450
And sorry about my English.it's too bad.:confused:

The ALC883 chipset is an Intel/Realtek combo 7.1 channel high definition audio sound "card"... try ```
sudo modprobe snd_hda_intel
``` as a starting point. You should get sound within 5-10 seconds, otherwise it's not worked and we will see what to do next.

---

### Post by kuyangiang on 2008-04-03
thanks so much,i will try

---

### Post by tikidrummer on 2008-04-04
i'm having the same problem.  no sound for me after entering the code.

---

### Post by superprash2003 on 2008-04-04
check this out [http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html](http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html)

---

