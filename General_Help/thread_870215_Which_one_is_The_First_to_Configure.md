---
title: "Which one is The First to Configure ????"
date: 2008-07-25
forum: General Help
---

### Post by Uchiha_madara on 2008-07-25
Good Evening Lovely Members :


I need to ask ?

Which one is the First to Configure the sound card :

HDA or the Sound card ...

My Laptop is "CELERON intel inside"
but the High Definition Audio is ATI

so I don't Know which is the Module here to Begin with ?

snd-hda-intel or snd-atiixp ?

and i face a problem with alsa-base

i don't Know what to write inside it "mpu_port=????" "index=????"


i hope that the Question is Clear

---

### Post by Uchiha_madara on 2008-07-25
Please help

---

### Post by hal8000 on 2008-07-25
> **Uchiha_madara said:**
> Good Evening Lovely Members :


I need to ask ?

Which one is the First to Configure the sound card :

HDA or the Sound card ...

My Laptop is "CELERON intel inside"
but the High Definition Audio is ATI

so I don't Know which is the Module here to Begin with ?

snd-hda-intel or snd-atiixp ?

and i face a problem with alsa-base

i don't Know what to write inside it "mpu_port=????" "index=????"


i hope that the Question is Clear

Post the output of:
lspci | grep audio
lspci | grep snd

If you think you know the chipset then you can use modprobe:

sudo modprobe  snd-hda-intel

will load the above kernel modules. Test your soundcard
with a wav file or CD. The change is ot permanent.

One you find the required kernel modules you can add it to
/etc/modules

to start on boot.
Hope that helps

---

### Post by nikgare on 2008-07-25
What problem are you having?

---

