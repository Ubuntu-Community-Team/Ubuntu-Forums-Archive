---
title: "Compaq Presario B1800 series laptop"
date: 2006-10-12
forum: Hardware &amp; Laptops
---

### Post by saurabh.sid on 2006-10-12
I tried Ubuntu 6.06 on my new Compaq Presario B1800 laptop. Installation was a "breeze" but there is no sound. I tried some googling.. but solutions were too complicated for me to understand.. I love linux.. i used it on my previous Dell latitude d600 laptop.. but i am forced to use windows on my new machine because I always like to have music playing when i work..

i tried a few other 1 cd linux distros..with the same problem.. havent tried fedora/suse because i dont want to download and burn 5 cds..
i will try to install Ubuntu 6.10 test version today..
does anyone have another solution.. another distro.. or an easy fix to sound problem..help help help..

---

### Post by sujit.mishra on 2007-04-20
Hi Sid,
Can you pls let me know if you were able to get resolution 1280x768...?

---

### Post by tanle on 2008-05-05
Hi all,

I also have this laptop model but my soundcard is not working at all on the new version of ubuntu 8.04, it claim that it has dected it, but there are no sound coming through, any hints please help.

thanks in advance,

Tan

---

### Post by clarezoe on 2008-06-22
> **tanle said:**
> Hi all,

I also have this laptop model but my soundcard is not working at all on the new version of ubuntu 8.04, it claim that it has dected it, but there are no sound coming through, any hints please help.

thanks in advance,

Tan

Hi, I have this laptop, and I had my soundcard working under 8.04 by adding

```
options snd-intel8x0 ac97_quirk=6
```option in the file

```
/etc/modprobe.d/alsa-base
```
hope this helps.

---

