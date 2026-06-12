---
title: "lenovo thinkpad x200s no sound on internal speakers"
date: 2015-06-10
forum: Hardware
---

### Post by esther4 on 2015-06-10
Dear community!

I'm quite a newbe to ubuntu and linux in general. Now I've got a x200s thinkpad that runs on ubuntu 14.04.2. The problem is the internal speakers don't work, headset does. There is extensive information on that problem in the forums, but none of it worked so far. Now I'm tired of trying out for hours and therefore seeking your support. 

What I did so far: I followed this instruction [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto) giving me 
cat /proc/asound/card0/codec* | grep Code 
Codec: Conexant CX20561 (Hermosa)

Then "sudo gedit /etc/modprobe.d/alsa-base.conf" and added the line 
"options snd-hda-intel model=thinkpad" at the end of the document popping up in the editor. 

As is it didn't work I also tried "
"options snd-hda-intel model=lenovo", 
"options snd-hda-intel model=generic" and  "options snd-hda-intel power_save=10 power_save_controller=N"Afterwards i always did 
sudo alsa force-reload

and restarted the PC.

Ah yes and the alsamixer I also checked, noting in muted or disabled. 

Do you have an idea, what I could do?

Thanks so much for helping.
All the best
Esther

---

