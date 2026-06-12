---
title: "No sound...Hp laptop....HP dv4-1123us please help..."
date: 2008-10-26
forum: Hardware
---

### Post by TekkieFreak on 2008-10-26
Hi everyone....so I'm still working on my sound problem.  I have an HP Pavilion dv4-1123us.  I got everything working but the webcam and the sound. I'm running intrepid.  Probably 5 years ago before I got into video editing and podcasts I wouldn't have cared much about the sound, but if I can't get it to work it's going to be a deal breaker for me. :(

According to the hardware detector program, it has Intel hda sound.  I've tried adding various lines in my /etc/modprobe.d/alsa-base file and no luck. I do get a very low-volume system sound when shutting down. There's no other sound at all though.  I've been testing sound with miro and a movie trailer that I downloaded.  Video plays great and looks beautiful and I even got DVD's to play...but no sound. 

Please any help would be appreciated.  I've exhausted every module and alsa-base line that I could find on the forums.  Again thanks for any help. 

Jilly

---

### Post by teaker1s on 2008-10-26
may be worth a look
[https://wiki.ubuntu.com/HP_dv6000_Series]("https://wiki.ubuntu.com/HP_dv6000_Series")

---

### Post by Jorge_C on 2008-10-26
Hi,

Make sure no channels are muted with alsamixer.

Besides, you can try adding "irqpoll" as a boot option, it solves my sound issues in intrepid (which isn't final yet, btw) but it makes the touchpad much less reponsive. I have an hp dv7-1090es and my sound card is an "Intel 8201I (ICH9 Family) HD Audio".

Did sound work with Hardy?

---

### Post by TekkieFreak on 2008-10-26
Teaker1s...

Apparently, just posting to the Ubuntu forums made it work. :) When I posted this message it wouldn't work.  I had added this line:

options snd-hda-intel enable_msi=1

to my 

/etc/modprobe.d/alsa-base 

Yesterday.  No luck.  Then this morning...I ran the updates and removed alsa-oss (which I installed a couple days ago and didn't seem to be helping). The lne didn't seem to help yesterday though between running updates, removing alsa-oss and rebooting...it now works. :) 

I still get a phonon error on boot saying that it's not working (I guess it's trying to play some sort of startup sound).  So, I will keep my fingers crossed and hope that it keeps working. :) 

I'm loving Kde 4. :)

---

### Post by TekkieFreak on 2008-10-26
Jorge,  Thanks.  I have written down your irqpoll...I believe I also have the ICH9 audio. For now, I am going to leave well enough alone. Since, by magic, it seems to be working.

I just got the laptop last tuesday.  I did try to boot off 8.04 and couldn't get the video working.  Yep, I'm aware intrepid is a beta....but it's so close to release I decided to give it a try.

---

### Post by teaker1s on 2008-10-26
:popcorn:

---

