---
title: "Is there a way to restart sound"
date: 2008-09-01
forum: General Help
---

### Post by dragos240 on 2008-09-01
I dont have sound anymore, and i have to keep restarting. Any way i can restart the speakers or something?

---

### Post by TimDaniels on 2008-09-01
> **dragos240 said:**
> I dont have sound anymore, and i have to keep restarting. Any way i can restart the speakers or something?
What version of Ubuntu, and what model and brand of PC?

*TimDaniels*

---

### Post by dragos240 on 2008-09-01
> **TimDaniels said:**
> What version of Ubuntu, and what model and brand of PC?


I use hardy 8.04 and a sony vaio model

VGN-FS760/w

---

### Post by nbayiha on 2008-09-01
[http://ubuntuforums.org/showthread.php?t=789578&highlight=youtube+sound+problem](http://ubuntuforums.org/showthread.php?t=789578&highlight=youtube+sound+problem)
follow the thread

---

### Post by dragos240 on 2008-09-03
> **nbayiha said:**
> [http://ubuntuforums.org/showthread.php?t=789578&highlight=youtube+sound+problem](http://ubuntuforums.org/showthread.php?t=789578&highlight=youtube+sound+problem)
follow the thread
dang! It worked for a day but its gone again ](*,)

---

### Post by dragos240 on 2008-09-03
> **dragos240 said:**
> dang! It worked for a day but its gone again ](*,)
Special bump :aware:

---

### Post by dragos240 on 2008-09-03
> **dragos240 said:**
> Special bump :aware:
Oh please! Is there any other way i can restart the sound!!!!!
Please...:(

---

### Post by dragos240 on 2008-09-03
> **dragos240 said:**
> Oh please! Is there any other way i can restart the sound!!!!!
Please...:( 
Sorry i quadruple posted but i really need help!

---

### Post by liontamer on 2008-10-06
[I]Hy All,

i have a similar problem sound on my vaio has just gone with a message "no audio output device installed" i nhave done all the basic manuovers like sounds etc the audio output device just seems to mhave disappeared.
It started last night when I hit the sound image to go to silent.

thanks everyone.

---

### Post by Calmatory on 2008-10-06
```
killall pulseaudio
```

Does that help in any way?

---

### Post by Yellow Pasque on 2008-10-06
```
sudo /etc/init.d/alsa-utils restart

```

---

