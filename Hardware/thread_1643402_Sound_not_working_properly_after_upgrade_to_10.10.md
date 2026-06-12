---
title: "Sound not working properly after upgrade to 10.10"
date: 2010-12-11
forum: Hardware
---

### Post by roobinatube on 2010-12-11
Hi,

I have been running mint 9 xfce (based on lucid) on my laptop, with no problems, however today I upgraded by installing kubuntu 10.10.

After this upgrade, the sound doesnt work properly. I can hear sound from my speakers, but when I plug in headphones, the sound doesnt stop from the speakers, and doesnt play from the headphones either.

I have a lenovo G555. ALSA says codec cx20585 is used.

I remember fixing this issue before using this post [http://ubuntuforums.org/showpost.php?p=9906171&postcount=24](http://ubuntuforums.org/showpost.php?p=9906171&postcount=24) however the conexant driver doesnt compile in 10.10... I have found other threads without solution about this driver in 10.10.

Other laptop models in bug reports have had success with option model=ideapad [COLOR="Lime"]but this doesnt work for me[/COLOR].

[COLOR="lime"]When I use the alsa-base.conf options from the thread above[/COLOR], when I open alsamixer, it gives me a "MIC_B" which is the mic that worked for me in 10.04. I can set this mic to capture, but cannot raise the volume of it from 0. There is also another capture column which I can change, but this makes no difference.

Any help would be incredibly well received!

Roo

---

### Post by Sef on 2010-12-12
> I have been running mint 9 xfce (based on lucid) on my laptop, with no problems, however today I upgraded by installing kubuntu 10.10.


Have you upgraded to Kubuntu 10.10 by installing with a Live CD or Live USB, or some other way? If the latter, then please tell how you upgraded.

---

### Post by roobinatube on 2010-12-12
Thank you for your reply.

I upgraded using the lice cd, put on a usb pen with unetbootin.

I should have been clearer, when I said upgraded, i didnt really mean upgraded. I did a completely clean install.

I formatted the root partition, and although i didnt format the home partition (I wanted to be able to copy documents over easily), I changed my username so that I had a clean home directory with no old config files from xfce etc.

Therefore this is completely clean install of kubuntu 10.10.

Also I made a mistake in my first post I just spotted, I will edit that.

Thanks again
Roo

---

### Post by roobinatube on 2010-12-12
I have come across multiple posts that seem to think that the G555 uses Conexant 5069 such as [http://www.linuxquestions.org/questions/syndicated-linux-news-67/lxer-fedora-13-fixing-sound-and-video-for-the-lenovo-g555-838110/]("http://www.linuxquestions.org/questions/syndicated-linux-news-67/lxer-fedora-13-fixing-sound-and-video-for-the-lenovo-g555-838110/")

Could the problem be that ALSA isnt recognising that the correct codec? I thought that the alsa-base.conf options I added were for that purpose, but whatever I add ASLA still says cx20585...

Roo

---

