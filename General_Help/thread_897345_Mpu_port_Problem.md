---
title: "Mpu_port Problem"
date: 2008-08-22
forum: General Help
---

### Post by Uchiha_madara on 2008-08-22
Good morning Guys ....

I configured My Sound card but there is some questions :

1 -[SIZE="1"] when I write the > sudo modprobe snd-atiixp
    there well be a message 
    > FATAL: Error inserting snd_atiixp (/lib/modules/2.6.24-19-generic/updates/alsa/pci/snd-atiixp.ko): Unknown symbol in module, or unknown parameter (see dmesg)

when I wrote this Command the Problem was in the mpu_port?
in Alsa-base files I wrote in the end of the file :

> options snd-atiixp index =0 mpu_port=0x330
how can I know the right mpu_port ?[/SIZE]

---

