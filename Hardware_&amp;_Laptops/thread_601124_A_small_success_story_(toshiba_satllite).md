---
title: "A small success story (toshiba satllite)"
date: 2007-11-02
forum: Hardware &amp; Laptops
---

### Post by guruofquality on 2007-11-02
My sister got a cheap Toshiba Satellite L35-S2366. I put feisty on the laptop, and almost everything worked. My only gripes being: the headphone sound did not work, and the sleep and hibernate did not work if the ac adaptor was not plugged in.

Since upgrading to gutsy, the sleep/hibernate has broken entirely... And interestingly enough, the headphone jack worked, but the main speakers did not.

For the sleep/hibernate stuff, I tried s2disk/s2both with no success. I dont know what to try next, the sleep/hibernate worked in feisty(provided ac was plugged in). Can anyone point me in the right direction?

----------------------------------------------------

But wait! There is good news (for me). I got the sound working today, 100% speakers and headphone jack. I followed this guide: [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto) which  told me to:

1) cat /proc/asound/card0/codec#* | grep Codec

I got:
>> Codec: Realtek ALC861-VD
>> Codec: Generic 11c1 Si3054

2) Then, look for ALC861 in [http://www.mjmwired.net/kernel/Documentation/sound/alsa/ALSA-Configuration.txt](http://www.mjmwired.net/kernel/Documentation/sound/alsa/ALSA-Configuration.txt)

I found the following: 

>>ALC861VD/660VD
>> 3stack	3-jack
>> 3stack-dig	3-jack with SPDIF OUT
>> 6stack-dig	6-jack with SPDIF OUT
>> 3stack-660	3-jack (for ALC660VD)
>> 3stack-660-digout 3-jack with SPDIF OUT (for ALC660VD)
>> lenovo	Lenovo 3000 C200
>> dallas	Dallas laptops
>> auto		auto-config reading BIOS (default)

3) Edit /etc/modprobe.d/alsa-base and append: "options snd-hda-intel model=MODEL", without quotes to the end of the file. MODEL is one of the potential models in the left column above.

I entered a potential model name, rebooted, and tested the sound. It took a few tries, but it turns out that "dallas" works for this particular laptop. Whatever "Dallas laptops" may be...

So, I hope that this may benefit someone else with one of those weird toshiba laptops and driver issues... Now all I have left to solve is the mystery of the hibernate/sleep functionality, but a small victory with the sound sure feels reassuring!

---

### Post by tupac on 2007-11-12
just wanted to let you know you made somebody happy.

I had  been fighting for month trying to have those headphones working. I had tried everything including adding a  model option to the snd-hda module  but where I got the list (in the file /usr/share/doc/alsa-base/driver/ALSA-configuration) dallas was not listed.

I'm really gratefull,

regards

Vittorio

---

