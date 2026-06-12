---
title: "Compaq Deskpro sound problems. Again."
date: 2007-02-07
forum: Hardware &amp; Laptops
---

### Post by DoktorNo on 2007-02-07
I have old Compaq Deskpro box, with Pentium III (propably 300Mhz) and 128MB of RAM. Of course on Xubuntu 6.06, and I'am looking forward to change it into 'thin client' in LTSP network.

The biggest concern is lack of sound, this box has old ISA ES16XX soundcard. I have tryed alsaconf, and it did't found any soundcard. I have tried modprobe snd-es1688 and snd-es16xx. Nothing.

Any ideas?

---

### Post by Waappu on 2007-02-07
Hi

Have you read this post?
[http://ubuntuforums.org/showthread.php?t=12525&highlight=deskpro](http://ubuntuforums.org/showthread.php?t=12525&highlight=deskpro)

---

### Post by DoktorNo on 2007-02-07
Yes, but remedies seems to be for older relases of Ubuntu. But I will try them.

---

### Post by Waappu on 2007-02-07
Hi

I fix my problem on Edgy with that post

---

### Post by Waappu on 2007-02-07
Open text editor in terminal
```
gksudo gedit /etc/modprobe.d/soundcard
```
insert these lines to file and save
```

alias sound-slot-0 snd-card-0
alias snd-card-0 snd-es18xx
options snd-es18xx enable=1 isapnp=0 port=0x220 mpu_port=0x388 fm_port=0x330 irq=5 dma1=1 dma2=0
```

Then type in terminal
```
sudo modprobe snd-es18xx
```

---

### Post by DoktorNo on 2007-02-07
No problem, I'll try this. What about the quality of sound? I have no experience with this boxes. Does the sound is outputted through build-in speaker?

---

### Post by Waappu on 2007-02-07
Hi

Yes , sound comes from internal speaker. I just get it working so I'm still testing =)

---

### Post by Waappu on 2007-02-07
Hi

Look also this
[http://ubuntuforums.org/showthread.php?t=204876&highlight=deskpro+shutdown](http://ubuntuforums.org/showthread.php?t=204876&highlight=deskpro+shutdown)

---

### Post by DoktorNo on 2007-02-07
> **Waappu said:**
> Hi

Look also this
[http://ubuntuforums.org/showthread.php?t=204876&highlight=deskpro+shutdown](http://ubuntuforums.org/showthread.php?t=204876&highlight=deskpro+shutdown)

So far there were no problems with software shutdown. Do you have lack of shutdown after pressing the power button?

---

### Post by Waappu on 2007-02-08
> **DoktorNo said:**
> So far there were no problems with software shutdown. Do you have lack of shutdown after pressing the power button?
Hi

My problem is that if I want reboot that box just hangs. Software shutdown and pressing power button is OK.

---

### Post by DoktorNo on 2007-02-08
Whoa! I had just made it! The sound is working now perfectly! But there are two catches:

First one: in /etc/modprobe.d/ there is a file named 'sound', and it has the same function as 'soundcard'. I have applied the snd-es18xx modprobe rules here, and it worked.

Second one: some users on box could have no permission to play sound. Check the /etc/group file, and add (if needed) users to 'sound' group.

BTW: what sucks on Compaq Deskpro's sound card, if fact, that they do not provide signal for headphones or passive speakers...

---

### Post by Waappu on 2007-02-08
Hi

Just tip for those who plan install Ubuntu to compaq deskpro if sounds not working with live cd.

I did new install for my box. I booted from livecd and then did those steps I post before. And after that I start install. After install when I boot from hd sound working OK =)

Still problem with restart... Maybe I create new post for that

---

### Post by DoktorNo on 2007-02-08
> **Waappu said:**
> 
I did new install for my box. I booted from livecd and then did those steps I post before. And after that I start install. After install when I boot from hd sound working OK =)

Still problem with restart... Maybe I create new post for that

Explanation is simple: the Ubuntu is copying to the fresh install on HDD the config files from Live. Its resonable, because if they worked on Live CD, they would work after installation.

Its amazing, that I have no problems with resart, despite the fact, that we have the same box (or maybe not, mine is PIII).

Thanks for help!

---

