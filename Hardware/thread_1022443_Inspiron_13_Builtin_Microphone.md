---
title: "Inspiron 13 Builtin Microphone"
date: 2008-12-26
forum: Hardware
---

### Post by r351574nc3 on 2008-12-26
I have an inspiron 13 with a builtin microphone. Does anyone know whether this microphone is connected to the sigmatel chipset? Or does it have its own audio controller? 

The reason I ask is because the alsa only gives one option for microphone input source (Front Mic.) I can find no other way to use the builtin microphone. There's only one input source and no other audio controller. Any ideas?

---

### Post by r351574nc3 on 2008-12-27
bump

---

### Post by zangiev on 2009-02-05
Do you know how to make it work?

---

### Post by r351574nc3 on 2009-02-05
Sorry. Still waiting to hear back on that one.

---

### Post by Giovano on 2009-12-14
any news ???
man this is insane, where can we find help about that ?????

---

### Post by Giovano on 2009-12-20
ALLLELUIA !!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
it is working now.

edit /etc/modprobe.d/alsa-base.conf 

and put the option model=dell-bios in this line :


options snd-hda-intel model=dell-bios power_save=10 power_save_controller=N





merci simon!!!!!!!!!!!!!!

---

