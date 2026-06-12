---
title: "[SOLVED] Install on HP Pavilion"
date: 2008-01-24
forum: Hardware &amp; Laptops
---

### Post by MacLellan on 2008-01-24
OK here it is.. 
I installed ubuntu on my laptop, everything went smoothly.

however now that I have it working here is a list of a few problems so far...

1. When booting up i get BIOS error 81 (however the system still starts fine)

2. My wireless Networking so far is not functional.
      the OS displays the option, but as far as I can tell it not going to work for me.

3. this is the biggest annoyance so far, in that my keyboard is not mapped properly
     ex.  shift + 2   will not produce an @ symbol, instead it shows "

i have just installed this os this morning, 
I am mostly looking for help with the wireless connection
any info would be great, thanks.

__________________________
HP Pavilion dv2000 (2310ca)

---

### Post by MacLellan on 2008-01-24
Quick update... I have fixed my keyboard problems...
still working on the wireless solution .

---

### Post by Yellow Pasque on 2008-01-24
It would help to know what wireless you have. Run:
```
sudo update-pciids; sudo lspci
```

---

### Post by MacLellan on 2008-01-24
01:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)

---

### Post by Yellow Pasque on 2008-01-24
That one's a pain. Go to System -> Administration -> Restricted Driver Manager and see if Ubuntu offers to install a driver for it.

---

### Post by MacLellan on 2008-01-24
That worked perfect... Thanks!
also allowed me to get drivers for graphics card.

Only problem I believe is left is my audio...
it would seem that everything is working fine, however
there is no sound out of the speakers... (built-in speakers)

---

### Post by Yellow Pasque on 2008-01-24
Start with the simple thing. Often, the PCM volume is muted on install or after a restart.
Double-click on the volume control icon at the top of the screen. Make sure the ALSA mixer is the one you're using. Go to Edit -> Preferences and select all the available options. Now sure everything is unmuted/audible.

---

### Post by MacLellan on 2008-01-24
Still nothing... 
I also just pluged in headphones to see if it was limited to my speakers, but I get no sound through the headphones either.

---

### Post by Yellow Pasque on 2008-01-24
Can you run this command for me so I know what sound chip you have?
> grep Codec /proc/asound/card0/codec#*

---

### Post by MacLellan on 2008-01-24
that returned
"Codec: Conexant CX20549 (Venice)"

---

### Post by Yellow Pasque on 2008-01-24
You're going to need a later version of ALSA.
Run the two scripts found in this post. (reboot in between as instructed)
[http://ubuntuforums.org/showpost.php?p=3603812&postcount=13](http://ubuntuforums.org/showpost.php?p=3603812&postcount=13)

---

### Post by MacLellan on 2008-01-25
I gave it a try... but am unsure if I did it right...
Is there a specific folder those files should be saved to ?

here's what I got when I typed commands:

maclellan:~$ sudo sh alsa_1.sh
[sudo] password for maclellan:
sh: Can't open alsa_1.sh
maclellan:~$ sudo sh alsa1.sh
sh: Can't open alsa1.sh
maclellan:~$ 

so I attempted to right click and 'open with other app'
then used custom command and typed the above..

yet, still no sound...    

Anything else I might try ?

Thanks for all the help.

---

### Post by MacLellan on 2008-01-25
Scratch that... I believe that did fix the audio... 
Everything now seems to be working great.. 
thanks for all the help!

---

### Post by Yellow Pasque on 2008-01-25
Awesome. Enjoy your new OS.

---

