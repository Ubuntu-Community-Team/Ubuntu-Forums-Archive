---
title: "HVR1300 supported?"
date: 2007-01-13
forum: Hardware &amp; Laptops
---

### Post by Gryzom on 2007-01-13
I've spent the last week googling and searching these forums to try and get my HVR 1300 tv card to work with ubuntu 6.10 to no avail :(

Does anyone know if this card is supported at all? From what I've read, people in other distros appear to have got it working, but I've not found anything ubuntu related (unless I've missed something obvious?)

Are there any specific modules I need to add beyond what ships with ubuntu 6.10? As it looks like the cx module doesn't recognise the hvr 1300 by default. Also what application should I be using to view the tv once the driver side is up and running? Will tvtime work? (eventually I want to use mythtv, but for now a simple app will do)

Also, I'm more concerned about getting the analog side on this card running than I am the DVB side. 

Edit: 
**Quick Update: **

Done a bit more digging and installed the latest v4l-dvb as described at [http://linuxtv.org/wiki/index.php/How_to_install_DVB](http://linuxtv.org/wiki/index.php/How_to_install_DVB) and now dmesg shows it detecting the HVR1300

> 
[17179590.740000] CORE cx88[0]: subsystem: 0070:9601, board: Hauppauge WinTV-HVR1300 DVB-T/Hybrid MPEG Encoder [card=56,autodetected]
[17179590.740000] TV tuner 63 at 0x1fe, Radio tuner -1 at 0x1fe
[17179590.752000] cx2388x alsa driver version 0.0.6 loaded
[17179590.796000] cx2388x cx88-mpeg Driver Manager version 0.0.6 loaded
[17179590.904000] tveeprom 0-0050: Hauppauge model 96019, rev C6A0, serial# 430996
[17179590.904000] tveeprom 0-0050: MAC address is 00-0D-FE-06-93-94
[17179590.904000] tveeprom 0-0050: tuner model is Philips FMD1216ME (idx 100, type 63)
[17179590.904000] tveeprom 0-0050: TV standards PAL(B/G) PAL(I) SECAM(L/L') PAL(D/D1/K) ATSC/DVB Digital (eeprom 0xf4)
[17179590.904000] tveeprom 0-0050: audio processor is CX882 (idx 33)
[17179590.904000] tveeprom 0-0050: decoder processor is CX882 (idx 25)
[17179590.904000] tveeprom 0-0050: has radio, has IR receiver, has IR transmitter
[17179590.904000] cx88[0]: hauppauge eeprom: model=96019
[17179590.904000] input: cx88 IR (Hauppauge WinTV-HVR130 as /class/input/input3
[17179590.904000] cx88[0]/0: found at 0000:02:01.0, rev: 5, irq: 201, latency: 32, mmio: 0xf9000000
[17179590.936000] tuner 0-0061: chip found @ 0xc2 (cx88[0])
[17179590.940000] tuner 0-0061: type set to 63 (Philips FMD1216ME MK3 Hybrid Tuner)
[17179590.940000] tuner 0-0063: chip found @ 0xc6 (cx88[0])
[17179590.976000] wm8775 0-001b: chip found @ 0x36 (cx88[0])
[17179590.984000] cx88[0]/0: registered device video0 [v4l2]
[17179590.984000] cx88[0]/0: registered device vbi0
[17179590.984000] cx88[0]/0: registered device radio0


But I do not have a /dev/dvb directory and using tvtime with a channel scan hasn't found any of the analog channels either. 

Any thing I'm missing?

EDIT: After doing "sudo modprobe cs88_dvb" I now have a populated /dev/dvb/adapter0 directory, but still no /dev/v4l device which I think is the one I need to access the analog part of the hvr1300

---

### Post by Dubstar_04 on 2007-01-17
I have been having the same problem for ages. I have not found the solution as yet. It does work in linux and with mythtv as i had mythdora installed and it worked great!! let me know if you find a solution.

I added a second card to check that its not just the hauppauge one. The second card is a compro t 300 and is acting in the same way. I have both of them showing up and they both can be seen as analogue cards in mythtv but not dvb parts. and i still have no dev/dvb folder. 

Please help as its driving me crazy!!

---

### Post by Dubstar_04 on 2007-01-29
Problem sorted.

Update V4L drivers and sudo modprobe cx88-dvb and it all works fine. 

If anyone requires help just let me know

---

### Post by cowley on 2007-01-29
Hi

YES! PLEASE!! any help here would be appreciated... i havenot used ubuntu for ages and am now looking to use it with mythtv with hvr1300 card, so how do i update the v4l?

Many thanks

Simon

---

### Post by Dubstar_04 on 2007-01-29
ok this worked for me:

```

sudo apt-get install mercurial linux-headers-$(uname -r) build-essential


hg clone http://linuxtv.org/hg/v4l-dvb


cd v4l-dvb


sudo make


sudo make install


Reboot
```



When you reboot, open a new terminal and type:

```
sudo modprobe cx88-dvb
```

You should then have a new folder in /dev/ (/dev/dvb/adaptor0)

called 'dvb' and that should be populated with a folder valled adapted0 which will be populated itself.

The dvb folder will only be created once the card is working.

once you have the dvb folder you can follow the indtuctions from here:

> [http://parker1.co.uk/mythtv_ubuntu.php](http://parker1.co.uk/mythtv_ubuntu.php)

and that got mythtv up and running for me.

One thing I did have to do was add the sudo modprobe cx88-dvb to the 'modules' file however i have forgotten where this was as i only use linux at the weekend, in the week I have a old windows mce machine running media portal and it wipes the floor with mythtv  :) . I'm expecting something a little different from the mythtv 0.21 release. 

let me know if that works for you, if so maybe it could be added to the wiki as there is no info at all for the Hauppauge HVR 1300.

---

### Post by cowley on 2007-01-29
Hi i def will let you know! fingers crossed. now trying it

How do u get on with media portal? u prefer that to mythtv? i find it quite unstable (mediaportal that is) what specs do you run that on?

Thanks

Simon

---

### Post by Dubstar_04 on 2007-01-29
I have 2 dedicated htpc's running media portal, I find it more stable that mythtv and a damn site easier to setup. 

One machine id a AMD 3000+ with 512mb ram, 1 x 40gb HDD and 2 x 250gb HDDs
and that had an ATI radeon 9600 256mb video card that is played through a 26'' HD TV and is nothing short of breath taking.

The other is cobbled together from old bits, pentium P3 2Gb processor 512mb ram 1 x 250GB HDD and a cheap as chips nvidia video card playing into a regular 21'' tv.

Both are stable and get used every day!!

I really do enjoy playing with mythtv and linux is something new to mess about with while its cold outside!!

I've got a feeling that the new mythtv release is going to be something special, and i know that all the next O/S's are coming with beryl installed as standard!!  It might well leave media portal standing!!

---

### Post by cowley on 2007-01-29
Hi

well may have a play with that too, had it on a good machine, but think maybe that would run better on a dedicated machine that isnt being used for work/play internet etc

Back to mythtv - those instructions seemed to do the trick, had to create a uk-tacolneston file tho - got the tuner details from here if anyone needs some others...

[http://www.wolfbane.com/articles/uka1cmap.htm](http://www.wolfbane.com/articles/uka1cmap.htm)

Thanks

Simon

---

### Post by Dubstar_04 on 2007-01-31
cowley

you up and running now?? Did you manage to add the 

>  cx88-dvb

to the /etc/modules.conf ?

I had to do this to start initialise the dvb on boot!!

I am having problems with jerky playback and its driving me mad, I think its a graphics driver thing, as if i open the system properties box and move an open window it sends the cpu usage up to 100% the only thing is i can't work out how to solve it as its on board graphics (savage)!! 

Whats annoys me more is that i have an nvidia fx 5200 128mb card in a box on top of the pc and the agp slot is duff!! Might be time for a new motherboard!!

---

### Post by sebrock on 2007-04-17
> **Dubstar_04 said:**
> I have 2 dedicated htpc's running media portal, I find it more stable that mythtv and a damn site easier to setup.

OK, it may be easier to install... but more stable? thats crazytalk :D

---

### Post by AndrewWalker on 2007-04-17
Don't know if it is relevant/useful but I'm also using Gentoo and the drivers are built into kernel 2.6.19, not sure if Ubuntu is using that new a kernel though.
I've got the dvb part working great in Gentoo but have never managed to get the analog tv or radio parts to work at all. I've also never worked out if the hardware mpeg decoder is working or not, there were issues with it.
Hope this post wasn't completely useless to you!

---

