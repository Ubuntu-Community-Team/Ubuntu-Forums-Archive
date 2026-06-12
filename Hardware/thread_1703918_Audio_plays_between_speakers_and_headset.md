---
title: "Audio plays between speakers and headset"
date: 2011-03-09
forum: Hardware
---

### Post by Legendman3 on 2011-03-09
I know this has been asked a billion times before but i think my case is... unique in that I have a pair of ipod shuffle headphones and am using them with ubuntu 10.04. Audio plays on them and from the speakers. I would like to know how to make it so that audio only plays from the headphones. I tried before but ubuntu apparently doesnt know they are headphones. If you need any more info just ask...

---

### Post by Yellow Pasque on 2011-03-10
What kind of system do you have? Actually, it's just easier if you run the alsa-info script and post your result: [http://ubuntuforums.org/attachment.php?attachmentid=182689&d=1296839973](http://ubuntuforums.org/attachment.php?attachmentid=182689&d=1296839973)

---

### Post by Legendman3 on 2011-03-10
Oh i ran it and attached the info.txt to this post. I had the headphones plugged in when i ran it.

---

### Post by Yellow Pasque on 2011-03-10
Ok, HP G60 w/Conexant 506x codec. Try this:
```
echo "options snd-hda-intel model=hp-laptop" | sudo tee -a /etc/modprobe.d/alsa-base.conf
```
Reboot and see if it helped. If it doesn't, you may need to upgrade ALSA.

---

### Post by Legendman3 on 2011-03-10
Thanks but i found out that my sound card is the problem. Thanks anyway.

---

