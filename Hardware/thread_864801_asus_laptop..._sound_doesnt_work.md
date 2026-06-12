---
title: "asus laptop... sound doesnt work"
date: 2008-07-20
forum: Hardware
---

### Post by mikey5556 on 2008-07-20
hey ive just downloaded ubuntu and its great, much faster than vista. I'm still getting used to things and working out how to do stuff but one thing i cant seem to get working is the sound. I've tried fiddling with the settings but no matter what i get no sound.

My laptop is an Asus M51Se with inbuilt speakers. Do i need to download a linux driver or something ( nothing on the asus site about it).

Thanks

---

### Post by lancest on 2008-07-20
[Follow this]("http://ubuntuforums.org/showpost.php?p=4675505&postcount=8"): 

Start with this:
sudo apt-get install module-assistant

Also you may need something in your  /etc/modprobe.d/alsa-base
like:
So gedit /etc/modprobe.d/alsa.base
I had to put: options snd_hda_intel model=3stack in there at bottom
(Likely yours is different just Google your notebook model)
lsmod may provide some clues.

---

### Post by rohan182 on 2008-07-20
> **lancest said:**
> 
I had to put: options snd_hda_intel model=3stack in there at bottom
(Likely yours is different just Google your notebook model)
lsmod may provide some clues.

Im having the same problem but i have the M51Sn 

what exactly am i googling.. lsmod gave me the snd_hda_intel but not sure about the "model=3stack" part...

sorry, linux n00b :S

---

### Post by lancest on 2008-07-20
If you search Google using your laptop model and Ubuntu you will often find the answer. [This might do it for your model]("http://ubuntuforums.org/showthread.php?t=753679")
See bottom.

---

### Post by rohan182 on 2008-07-20
> **lancest said:**
> If you search Google using your laptop model and Ubuntu you will often find the answer. [This might do it for your model]("http://ubuntuforums.org/showthread.php?t=753679")
See bottom.

yay i have sound... just had to add 2 lines to the alsa-base file but it was written for a lenovo laptop.. strange but it works so i dont care :D

thanks :)

---

### Post by mikey5556 on 2008-07-24
hey thanks for replying

um i installed the alsa thing but googling my laptop didnt turn up any clues for what to put in the last line. Is there any other way to find out or has anyone else fixed this problem with the same laptop model as mine?

thanks

---

### Post by jagathkris on 2010-09-10
My headphone output and mic is not working. internal speaker is working fine. my lap is ASUS A42F series. please help..

---

