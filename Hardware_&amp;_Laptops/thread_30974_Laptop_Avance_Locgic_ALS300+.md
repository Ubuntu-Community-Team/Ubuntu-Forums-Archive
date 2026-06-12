---
title: "Laptop Avance Locgic ALS300+"
date: 2005-05-01
forum: Hardware &amp; Laptops
---

### Post by AndyT on 2005-05-01
Hi, I hope you guys can help.

I'm a new Linux user altogether so when something goes wrong I have no idea of any commands or where to start debugging a problem.

I've recently installed Hoary on a old laptop and the sound isn't working (which I heard is a common problem). Now reading on old posts and the wiki it seems Hoary has not loaded any sound modules at all. I have no volumn control and no esd threads running.

I know the make and chipset of my soundcard (Avance Logic ALS300+) and it seems to be supported in linux. Unfortunately, the alsa project website seems to be down as I cannot get onto it to find the modules needed to get my soundcard running.

Any suggestions or a course of action?

---

### Post by lucus on 2005-05-01
i have an entirely different laptop setup, but what i had to do to get sound running
was 
modprobe snd-opl3sa2 dma1=1 dma2=0 fm_port=0x388 irq=5 isapnp=0 midi_port=0x330 port=0x538 sb_port=0x220 wss_port=0x530

so a similar modproibe command might help you out.... not sure really... but hey it is a start, right?

---

### Post by AndyT on 2005-08-13
anyonw here know what I should modprobe to get this working? is there a generic soundblaster driver I can try or a place I can look?

---

### Post by s_p_a_r_k_y on 2005-08-13
hi there, when I run in to problems with sound I go to my best friend knoppix and boot that up. The latest knoppix is at version 4. If knoppix can detect the sound card try this, 

mount your root partition or home partition (they should be on the desktop as hda1Xso).

Then from the command line type this in.

```

su <enter>
lsmod > /mnt/hdaX/lsmod.txt

```
this will store the output of lsmod into lsmod.txt. Substitute the X with the correct hard drive you are using.

THen when you reboot, you can open up lsmod.txt and look for things with snd ... compare it to the output of lsmod under ubuntu

---

### Post by AndyT on 2005-08-16
That's a very good idea. Thanks! :)

---

### Post by mina_ehab8 on 2006-09-22
i ned itttttttttttttttttttttttttttttttttttttttttttt:cool:

---

### Post by ashwillis on 2006-10-21
mina_ehab8, ALSA supports the ALS300+. I know because I wrote the driver myself. I don't use Ubuntu right now, but do you know what kernel you are running? ALS300+ support has been included in the kernel since version 2.6.17

---

