---
title: "Analog Tv tuner card configuration help needed"
date: 2008-09-28
forum: Hardware
---

### Post by fasoulas on 2008-09-28
I have a tv tuner card of the conceptronic brand

The chip that it is on the card is(after issuing the command sudo /bin/lspci -v):

01:02.0 Multimedia controller: Philips Semiconductors SAA7133/SAA7135 Video Broadcast Decoder (rev d1)
	Subsystem: Philips Semiconductors KWorld V-Stream Studio TV Terminator
	Flags: bus master, medium devsel, latency 64, IRQ 23
	Memory at cacfb000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: [40] Power Management version 2

the command is from another thread that is about a different tv card
[http://ubuntuforums.org/showthread.php?t=787023](http://ubuntuforums.org/showthread.php?t=787023)

how can i configure this card to work on my ubuntu instalation???

Please help

---

### Post by fasoulas on 2008-10-09
Can anyone help me ??????

---

### Post by cariboo on 2008-10-09
I have a MSI TV@nywhere that has a saa7134 chipset I had it working right away, but I could never get the settings to stick after a reboot. 

I had a look here:

[http://www.linuxtv.org/v4lwiki/index.php/KWorld_Studio_TV_Terminator](http://www.linuxtv.org/v4lwiki/index.php/KWorld_Studio_TV_Terminator)

and it has all the settings needed to get you tv tuner working the way it should.

Step 1: Open a Applications-->Accessories-->Text Editor
and add the following:

```
options saa7134 card=65 tuner=54

```

save the files as **saa7134**

Copy the above file to /etc/modprobe.d. In a Applications-->Accessories-->Terminal type:

```
sudo cp saa7134 /etc/modprobe.d/
```
Enter your password when asked.

Step 2: In the same terminal type:

```
sudo rmmod saa7134_alsa
```

If you type the command correctly you won't see any output. Next in the same terminal type:

```
sudo rmmod saa7134
```

This removes the saa7134 module from the kernel.

Step 3. Again in the terminal type:

```
sudo modprobe saa7134
```

Again if you typed the command correctly, it will not echo anything back. What this does is reinstalls the saa7134 module with the options you created in the text editor.

You can now intall a program to watch Tv on your computer. I prefer TvTime, it is available in the repositories and you can use Add/Remove Programs, Synaptic Package Manager and of course the command line to install it.

Jim

---

### Post by fasoulas on 2008-10-09
thanks for the reply  i installed tv time but i cant see anything...
By the way what tv stanterd do i have to chooose i think is pal but it has many variants

---

