---
title: "Sound problems on Dell 4150"
date: 2005-03-08
forum: Hardware &amp; Laptops
---

### Post by nate on 2005-03-08
I'm pretty familiar with setting up sound in other distros (though I'm more of a server monkey so the majority of the linux systems I use do not have sound), but I decided to try Ubuntu on a laptop yesterday. No problems getting set up except for sound.

My first question is where is alsaconf? I see alsactl and alsamixer. apt-get tells me it is  selecting alsa-utils instead of alsaconf. From the man pages, it does not seem that alsactl or alsamixer have the same functionality as alsaconf.

My second question is how do I get my sound working in Ubuntu? I'm using a Dell Inspiron 4150 that has an Intel 82801CA sound. It's AC97 and I believe it would use the snd-Intel8x0 module.

```
0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801CA/CAM AC'97 Audio Controller (rev 02)
        Subsystem: Cirrus Logic: Unknown device 5959
        Flags: bus master, medium devsel, latency 0, IRQ 7
        I/O ports at d800
        I/O ports at dc80 [size=64]
```

---

### Post by nate on 2005-03-09
sudo modprobe snd-intel8x0 runs with no errors, but alsamixer then gives the following error:

```
alsamixer: function snd_ctl_open failed for default: No such device
```

---

### Post by nate on 2005-03-09
I found the problem in /var/log/messages. It was an IRQ conflict. I disabled the parallel port and sound worked after that.

---

### Post by tommy_haaland on 2005-03-15
I got the same problem om the same laptop! How do you disable the parallell port?

---

### Post by rusi_pathan on 2005-03-16
Use the BIOS to disable the || port

---

### Post by draconas on 2005-03-17
[QUOTE=nate]I found the problem in /var/log/messages. It was an IRQ conflict. I disabled the parallel port and sound worked after that.[/QUOTE]

Thanks Nate! This worked on my Lat610 as well.

---

### Post by nanaban on 2005-03-20
I have the same sound card on my sony laptop but I can't get sound to work at all?

Does that mean I need to switch to alsa instead of esd? which one are you guys using?? I managed to get sound to work on gentoo but not ubuntu

---

