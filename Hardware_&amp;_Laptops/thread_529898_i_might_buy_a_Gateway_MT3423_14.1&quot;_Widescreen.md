---
title: "i might buy a Gateway MT3423 14.1&quot; Widescreen Notebook PC"
date: 2007-08-19
forum: Hardware &amp; Laptops
---

### Post by ry4n on 2007-08-19
Hello I'm thinking on a Gateway MT3423 14.1" Widescreen Notebook PC for my school laptop. 

[HTML]Gateway 14.1" Widescreen Notebook PC (MT3423)

GTW   MT3423
• AMD Turion 64 X2 TL-56
• 160GB hard drive
• Burns DVDs and CDs
	
• 2GB of DDR2 memory
• Built-in 802.11g wireless
• Windows Vista Home Premium
   Integrated NVIDIA® GeForce® Go 6100 graphics and 256MB
[/HTML]

I was wondering if anyone new why i should not get this for 649.99 other than it has vista(lol)

---

### Post by nosrednaekim on 2007-08-19
sorry, i'm lazy, but could you please post a link to where you are buying it from? so I can see what TYPE of wireless it is?

---

### Post by beckham on 2007-08-20
Sorry dude, I don't have any idea about this.:)

---

### Post by gils0040 on 2007-08-20
Hi,
I just bought an MT3423 a week ago. The wireless chip in it is a realtek 8185. I managed to get it working using drivers from [http://rtl-wifi.sourceforge.net/wiki/Main_Page](http://rtl-wifi.sourceforge.net/wiki/Main_Page) (I believe that these will be included in the kernel as of 2.6.23!). I heard that NDISwrapper can be used as well. The video works fine using the nvidia binary (compiz-fusion runs great :)). The screen resolution is detected correctly. Power management works great (suspend works but i have not tested hibernate). The only major problem is sound. I am currently have none but I am in the middle of trying to figure it out. It is a HDA card that uses a sigmatel stac9200 codec. It needs to use the snd-intel-hda alsa driver. If it is currently not supported I'm guessing that it will be in the next alsa release (there has been alot of work on this issue during the previous release). There are many threads in these forums about the audio problem. Let me know if you have any specific questions!

---

### Post by bmartin on 2007-08-20
> **gils0040 said:**
> It needs to use the snd-intel-hda alsa driver. If it is currently not supported I'm guessing that it will be in the next alsa release (there has been alot of work on this issue during the previous release). There are many threads in these forums about the audio problem.
I was able to get the sound working on my girlfriend's laptop by editing the /etc/modprobe.d/sound file (may or may not exist already) and adding the following two lines:
```
alias snd-card-0 snd-hda-intel
options snd-hda-intel index=0 probe_mask=3 position_fix=3
```
That was on an Acer Aspire 5050

---

### Post by ry4n on 2007-08-20
[http://www.circuitcity.com/ssm/Gateway-14-1-Widescreen-Notebook-PC-MT3423/sem/rpsm/oid/186484/catOid/-12963/rpem/ccd/productDetail.do](http://www.circuitcity.com/ssm/Gateway-14-1-Widescreen-Notebook-PC-MT3423/sem/rpsm/oid/186484/catOid/-12963/rpem/ccd/productDetail.do)

---

### Post by gils0040 on 2007-08-20
@bmartin

Doesn't work. There are many workarounds for different systems but I have been unable to find one that works for this specific system.

---

### Post by ry4n on 2007-08-20
"gils" are u saying that Ubuntu would not work on this gateway? If not what would be the problem?

---

### Post by bmartin on 2007-08-20
@gils: Fair enough. Does the card reader on your laptop work in Ubuntu? I have an ENE card reader and there's 0 support for it.

---

### Post by gils0040 on 2007-08-21
@bmartin
I haven't tried yet. Im at work right now but ill give it a shot when i get home.

@ry4n
The only problem that I am having in ubuntu is the audio right now. I have also installed debian, gentoo (64), and arch (64). I am not able to get the nvidia driver working under gentoo and arch. I suspect that this may be a bug in the 64-bit nvidia drivers. I was able to get the nvidia driver working in ubuntu easily. I haven't given up just yet on the sound. If I am able to get this working I would be very happy with this laptop.

The problem i have with the nvidia drivers when I launch Xorg (via startx or kdm) the screen turns black and locks up. I'd like to be able to use my 64 bit system the way it was meant to be used so if anyone has any suggestions or experience with this problem please let me know.
btw i have submitted a bug report to nvidia about this problem.

---

### Post by GriZzlEnLS on 2007-10-27
I have that exact model and had TONS of problems with the wireless card. Realtek doesn't seem to have the driver for that exact model. and Gateway won't help you at all. If you get it working good luck to you I never could. 
On the up side the NIC card seemed to work fine with no driver install needed.

---

