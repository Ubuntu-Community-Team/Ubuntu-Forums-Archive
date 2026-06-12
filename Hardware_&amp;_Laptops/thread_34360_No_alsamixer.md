---
title: "No alsamixer?"
date: 2005-05-14
forum: Hardware &amp; Laptops
---

### Post by chytraeus on 2005-05-14
Hello,
Im a newbie. I dont know much about Linux. I am trying to learn but become more confused as i read the forums. I dont know how to load sound modules or anything like that. If someone could give me a kindergarten explanation to get my sound working that would be great.
When I type alsamixer in the command line this is the message I get.

alsamixer: function snd_ctl_open failed for default: No such file or directory

What should i do know?

---

### Post by nad on 2005-05-14
What happens when you issue the command: sudo alsactl store ?

---

### Post by chytraeus on 2005-05-14
[QUOTE=nad]What happens when you issue the command: sudo alsactl store ?[/QUOTE]

Thanks for the quick reply.

I get this answer.

alsactl: save_state:1194: No soundcards found...

Don

---

### Post by nad on 2005-05-14
I don't usually help with sound issues because it has become a thorn in the side of ubuntu. See hundreds of posts here regarding sound issues.

But, what is the ouptut of: lspci
and: lsmod | grep -i snd

---

### Post by chytraeus on 2005-05-14
When I typed in lspci this is what I got.

0000:00:00.0 Host bridge: Silicon Integrated Systems [SiS] 530 Host (rev 02)
0000:00:00.1 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev d0)
0000:00:01.0 ISA bridge: Silicon Integrated Systems [SiS] SiS85C503/5513 (LPC Br idge) (rev b1)
0000:00:01.1 ff00: Silicon Integrated Systems [SiS] ACPI
0000:00:01.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller  (rev 11)
0000:00:02.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bri dge (AGP)
0000:00:0a.0 Ethernet controller: National Semiconductor Corporation DP83815 (Ma cPhyter) Ethernet Controller
0000:00:0b.0 Multimedia audio controller: Rockwell International: Unknown device  4310
0000:00:0b.1 Communication controller: Rockwell International Riptide HSF 56k PC I Modem
0000:00:0b.2 Input device controller: Rockwell International: Unknown device 431 2
0000:01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 530/620  PCI/AGP VGA Display Adapter (rev a2)

But when I typed in lsmod | grep -i snd the command line returns and nothing else.

Don

---

### Post by nad on 2005-05-14
0000:00:0b.0 Multimedia audio controller: Rockwell International: Unknown device 4310

As I recall, the riptide is a combo device (older HP computer?) that controls both audio and the modem. It would probably be most efficient to just buy a cheap soundcard.

Well, now you know the problem. Start altavista-ing (google-ing).

---

### Post by ludi on 2005-05-14
[QUOTE=chytraeus]Hello,
Im a newbie. I dont know much about Linux. I am trying to learn but become more confused as i read the forums. I dont know how to load sound modules or anything like that. If someone could give me a kindergarten explanation to get my sound working that would be great.
When I type alsamixer in the command line this is the message I get.

alsamixer: function snd_ctl_open failed for default: No such file or directory

What should i do know?[/QUOTE]

So, you don't have sound. What kind of (and model) of sound card do you have?
First do a sudo lspci | grep audio, if something appear like
0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50) mean that the system has recognized your sound device.

Before type sudo lsmod | grep snd and see what you get. 
If you get something like 
snd_via82xx            25248  0
snd_ac97_codec         64608  1 snd_via82xx
snd_pcm_oss            47652  0
means that the modules are ok.

---

### Post by chytraeus on 2005-05-14
Thank you for your help. 

Any particular sound cards that are supported best or less troublesome?

Don

---

### Post by ludi on 2005-05-14
[QUOTE=chytraeus]Thank you for your help. 

Any particular sound cards that are supported best or less troublesome?

Don[/QUOTE]
 I think that your sound device is shared to modem.
So, your modem is working?

---

### Post by nad on 2005-05-14
Literally, a cheap soundcard. Something that says soundblaster compatible, etc. $20 or so.

I would stay away from the more expensive proprietary cards like aopen. You will just be asking for more trouble. Unless you want the latest and greatest, in which case I am not your source for info.

---

### Post by ludi on 2005-05-14
You can use sound blasters cards. You will have to compile the alsa drive to solve some issues (there is a thread/how-to to do it)
[http://ubuntuforums.org/showthread.php?t=21211](http://ubuntuforums.org/showthread.php?t=21211).
But there are others that are supported as well as sound blaster.

---

### Post by chytraeus on 2005-05-14
[QUOTE=ludi]I think that your sound device is shared to modem.
So, your modem is working?[/QUOTE]

Ludi,
That´s difficult for me to answer. I use an external modem for a dsl connection.

Also when I type sudo lsmod | grep snd the command line returns and nothing else.

---

### Post by ludi on 2005-05-14
[QUOTE=chytraeus]Ludi,
That´s difficult for me to answer. I use an external modem for a dsl connection.

Also when I type sudo lsmod | grep snd the command line returns and nothing else.[/QUOTE]
 Take a little look to your machine, and search for a modem connector (onboard).
So If I understood right, you first have setup your modem to get the sound working too.

---

### Post by chytraeus on 2005-05-14
[QUOTE=ludi]You can use sound blasters cards. You will have to compile the alsa drive to solve some issues (there is a thread/how-to to do it)
[http://ubuntuforums.org/showthread.php?t=21211](http://ubuntuforums.org/showthread.php?t=21211).
But there are others that are supported as well as sound blaster.[/QUOTE]
 Thanks to both Dan and ludi. I guess there´s a learning curve to this.

---

### Post by ludi on 2005-05-14
Some resource to setup your Rockwell/Lucent modem/audio [http://www.linuxant.com/drivers/](http://www.linuxant.com/drivers/)
and [http://www.linuxvoodoo.com/howto/HOWTO/Conexant+Rockwell-modem-HOWTO/hsf.html](http://www.linuxvoodoo.com/howto/HOWTO/Conexant+Rockwell-modem-HOWTO/hsf.html)
[http://www.linuxant.com/drivers/hsf/downloads-installer.php](http://www.linuxant.com/drivers/hsf/downloads-installer.php)
The rockwell modem/audio is unknow for me, so I can help much more than this  :-|

---

### Post by nad on 2005-05-14
If you get a no frills, nothing special soundcard, it should just work. No compiling of modules necessary. But then again, what do I know?

---

### Post by chytraeus on 2005-05-14
ludi, thanks for the links. I never would have found those. 
And a cheap soundcard is tempting too, Dan, especially if it could eliminate mucho headaches.

Don

---

### Post by ludi on 2005-05-14
[QUOTE=chytraeus]ludi, thanks for the links. I never would have found those. 
And a cheap soundcard is tempting too, Dan, especially if it could eliminate mucho headaches.

Don[/QUOTE]
 Go here
[http://www.alsa-project.org/alsa-doc/](http://www.alsa-project.org/alsa-doc/) and select the chipset that you want.
Example: [http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-Creative_Labs#matrix](http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-Creative_Labs#matrix)
You can buy whatever_card TM  but you have to know what is the chipset model.

---

### Post by chytraeus on 2005-05-14
[QUOTE=ludi]Go here
[http://www.alsa-project.org/alsa-doc/](http://www.alsa-project.org/alsa-doc/) and select the chipset that you want.
Example: [http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-Creative_Labs#matrix](http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-Creative_Labs#matrix)
You can buy whatever_card TM  but you have to know what is the chipset model.[/QUOTE]


Thanks for these links.They were verey helpful.

---

