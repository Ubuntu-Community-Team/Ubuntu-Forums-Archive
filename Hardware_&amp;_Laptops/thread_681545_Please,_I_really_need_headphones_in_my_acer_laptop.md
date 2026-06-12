---
title: "Please, I really need headphones in my acer laptop, but they dont work on ubuntu."
date: 2008-01-29
forum: Hardware &amp; Laptops
---

### Post by the_analyzer on 2008-01-29
My laptop
Extensa 5210 acer.
I dont know what to do?
anyone? help me please? I love ubuntu but I cannot work withou the headphones.

note: the speakers of the laptop are fine.

---

### Post by shanepardue on 2008-01-29
I also am experiencing this problem with an Acer laptop.

---

### Post by oldsoundguy on 2008-01-29
sounds like a sound driver issue.  Check to see if there is an upgrade for your sound chip.

---

### Post by the_analyzer on 2008-02-02
> **oldsoundguy said:**
> sounds like a sound driver issue.  Check to see if there is an upgrade for your sound chip.

where?

---

### Post by the_analyzer on 2008-02-02
Should we post this as a bug?

---

### Post by shanepardue on 2008-02-02
> **the_analyzer said:**
> Should we post this as a bug?
This worked for me - [http://ubuntuforums.org/showpost.php?p=4016762&postcount=7](http://ubuntuforums.org/showpost.php?p=4016762&postcount=7)

---

### Post by the_analyzer on 2008-02-03
HEY, can you tell what did you do exactly, I mean, I dont know how to install that modules generic etc etc, 

anyway I installed OSSv4 and I removed alsa-mixer, but know headphones work but I have two more problems.

1. there is no volum control in the upper-right side of the screen

2. When I plug in the headphones they do not mute the speakers. 

regards.

---

### Post by shanepardue on 2008-02-03
```
sudo aptitude install linux-backports-modules-generic
sudo gedit /etc/modprobe.d/alsa-base
```
add this line to that file
```
options snd-hda-intel model=acer
```

---

### Post by the_analyzer on 2008-02-11
yes I did those. But I have the same problems. 

1. When I plug the headphones, the speakers dont mute. 

2. I dont have any volume control.

3. The volume is not that high that is in the vista.

4. When I start the system, I do not listen anymore that sound in the beginning.

5. When I see videos from you tube (via firefox) I dont listen sound at all. (with normal files mp3, etc I can listen)

What should I do? Help, 
Best Regards

---

