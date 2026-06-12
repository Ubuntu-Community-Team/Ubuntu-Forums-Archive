---
title: "HP dv4t 1400 sound problems"
date: 2009-09-06
forum: Hardware
---

### Post by ubunt22rock on 2009-09-06
Hi

I have looked at almost ALL posts for HP dv series here and my sound problems still persist,

My sound card is an intel 82801l. I dont know i have provided sufficient info about my card but that what I have now.

mine is a heavily customized laptop. so it doesnt have a proper model name. looks like "1400" in hp dv4t 1400 means : "customized, so DIE"

The problem is this:

1. Sometimes I get no sound whatsoever.

2. At other times. Only during the log in screen, an irritating drumbeat repeats as if its some scratched CD playing. and if i reduce the volume it stops COMPLETELY and then it becomes like the above state: no sound whatsoever.

I hope someone can help me with this.

---

### Post by ubunt22rock on 2009-09-09
bump

---

### Post by ubunt22rock on 2009-09-10
Bump bump

---

### Post by ubunt22rock on 2009-09-11
bump

---

### Post by ldt116 on 2009-10-02
do anyone know how to fix this. I have exactly the same problem.

---

### Post by federico on 2009-10-02
So, I have a dv4t and had the same problems. 
I tried the following and things started working:

I added the following line to the file /etc/modprobe.d/alsa-base.conf


options snd_hda_intel model=hp-dv4 enable_msi=1  

and then I rebooted the computer and things were working.

I have been getting constant complaints from the system saying something like the STAC92XX audio system is not working, so I have had to select Pulse audio as the preferred output.

I hope this helps.

---

### Post by ldt116 on 2009-10-03
> **federico said:**
> So, I have a dv4t and had the same problems. 
I tried the following and things started working:

I added the following line to the file /etc/modprobe.d/alsa-base.conf


options snd_hda_intel model=hp-dv4 enable_msi=1  

and then I rebooted the computer and things were working.

I have been getting constant complaints from the system saying something like the STAC92XX audio system is not working, so I have had to select Pulse audio as the preferred output.

I hope this helps.

yes, it work. Thank you.

---

### Post by cobrahicks on 2009-10-04
> **federico said:**
> So, I have a dv4t and had the same problems. 
I tried the following and things started working:

I added the following line to the file /etc/modprobe.d/alsa-base.conf


options snd_hda_intel model=hp-dv4 enable_msi=1  

and then I rebooted the computer and things were working.

I have been getting constant complaints from the system saying something like the STAC92XX audio system is not working, so I have had to select Pulse audio as the preferred output.

I hope this helps.

Adding the line worked for beautifully for my dv4 1465dx
havent got any complain about STAC92XX or anything

Thanks for the advice

---

### Post by federico on 2009-10-04
Glad it worked. 
For what is worth,I updated to kubuntu 9.10 beta, and now my pulseaudio is not working and STAC92XX is doing the trick. Unfortunately, the updated version of skype does not accept any audio device other than pulse audio, so I am going to have to live without skype for a while.
I wish I understood what is going on!

---

