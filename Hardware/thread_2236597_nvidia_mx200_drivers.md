---
title: "nvidia mx200 drivers"
date: 2014-07-27
forum: Hardware
---

### Post by kazica on 2014-07-27
Hi I have a small problem some one kindly gave me a nvidia mx200 card and it's showing in the lcpci thing but not the software and updates bit. I've looked high and low on the internet on how to update the card and found a thread that was some what usseful. But I've come at a stump now as I can't even get the install for it to work as they've bstoped been suported by Nvidia. Really don't know what else to do any more as it's stressing me out. I can't even get this machine to use open Gl :/.

All the help is appricated thanks.

---

### Post by Axxon95 on 2014-07-27
Could you run lsmod and see if nouveau is loaded.
Also to see if at least the Open Source drivers are being utilized, install the mesa-utils package and run "glxinfo | grep OpenGL" and report back.
A lot of older cards were dropped mainly because of hardware limitations, and because of the upgrade from DRI1 to DRI2

---

### Post by kazica on 2014-07-28
from the lsmod I got this:
```
 Module                  Size  Used by
rfcomm                 53664  0 
bnep                   18895  2 
bluetooth             342206  10 bnep,rfcomm
binfmt_misc            13140  1 
snd_intel8x0           33110  1 
snd_ac97_codec        105709  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                85501  2 snd_ac97_codec,snd_intel8x0
joydev                 17101  0 
gpio_ich               13229  0 
snd_page_alloc         14230  2 snd_intel8x0,snd_pcm
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_rawmidi            25135  1 snd_seq_midi
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
hid_generic            12492  0 
snd_timer              28584  2 snd_pcm,snd_seq
snd                    60871  10 snd_ac97_codec,snd_intel8x0,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_seq_device,snd_seq_midi
serio_raw              13230  0 
lpc_ich                16864  0 
soundcore              12600  1 snd
shpchp                 32128  0 
mac_hid                13037  0 
parport_pc             31981  1 
ppdev                  17391  0 
lp                     13299  0 
parport                40836  3 lp,ppdev,parport_pc
usbhid                 46997  0 
hid                    87604  2 hid_generic,usbhid
e100                   35945  0 
psmouse                91329  0 
mii                    13654  1 e100
floppy                 55416  0 
```

From the glxinfo | grep OpenGL I got this: 
```
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Error: couldn't find RGB GLX visual or fbconfig
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Error: couldn't find RGB GLX visual or fbconfig
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
kaz@kaz-Evo-D510-SFF:~$ Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Error: couldn't find RGB GLX visual or fbconfig
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Error: couldn't find RGB GLX visual or fbconfig
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0"Xlib:: command not found
```

Not sure whats going on here. Please note I'm a tootal noob when it comes to anything linux.

---

### Post by kc1di on 2014-07-28
you need to install a driver for the card. 

you can try nouveau it's the open source driver for most nvidia cards.  
you can install it by going to a terminal and entering the following command:
```
sudo apt-get install nouveau-firmware 
```

you'll have to logout and back in for it to take affect. 

If that one dosen't work try the propriety driver
for a card that old you can  try nvidia-173

install with this command:
```
sudo apt-get install nvidia-173
```
good luck ;)

---

### Post by Axxon95 on 2014-07-28
Definitely try to get the Open Source drivers installed. And also, what version of Ubuntu are you using? That would help us out a lot.
nvidia-173 only supports GeForce 5+, so that might not work properly.
For proprietary drivers, you'd need the x.org updated legacy drivers, nvidia-96 or nvidia-76 something to that extent. But I do not see that package in apt on 14.04.
You could try Xubuntu(Ubuntu with XFCE desktop environment, less demanding on computer resources) 12.04 LTS, the drivers may still be available.

[HTML]http://old-releases.ubuntu.com/releases/xubuntu/releases/[/HTML]
If you would like to try an older LTS release of Xubuntu.

---

### Post by mörgæs on 2014-07-28
The card is so old that I doubt you will get much pleasure from it, drivers or not. 
Before investing more time in the project I suggest that you take a look at what's offered in the second hand market.

---

### Post by Yellow Pasque on 2014-07-28
> **Axxon95 said:**
> 12.04.4 LTS, the drivers may still be available.

The user would have to go to old releases section and get 12.04.1 (because any later version of Precise would have a newer X server version that's incompatible with nvidia 96.xx driver).

Of course, open nouveau driver is preferable here. Please give the /var/log/Xorg.0.log if possible (use [ code ] tags because it's a lot of text).

---

### Post by Axxon95 on 2014-07-28
> **Temüjin said:**
> The user would have to go to old releases section and get 12.04.1 (because any later version of Precise would have a newer X server version that's incompatible with nvidia 96.xx driver).

Of course, open nouveau driver is preferable here.
Thanks for clarifying the version. Was only going on vague memories.

[Attached] I popped my GeForce 4 MX 440 64MB into my legacy build, and got 1.2 OpenGL acceleration on a LiveCD Lubuntu 14.04.1. It has some minor visual glitches.
With GF4 only getting 1.2, I have doubts that GF2 will still work, even with nouveau. You could try slightly older, still supported versions of a Lightweight Ubuntu(and derivatives) or other Linux distros using a lightweight environment.

---

### Post by kazica on 2014-07-29
> **Axxon95 said:**
> Definitely try to get the Open Source drivers installed. And also, what version of Ubuntu are you using? That would help us out a lot.
nvidia-173 only supports GeForce 5+, so that might not work properly.
For proprietary drivers, you'd need the x.org updated legacy drivers, nvidia-96 or nvidia-76 something to that extent. But I do not see that package in apt on 14.04.
You could try Xubuntu(Ubuntu with XFCE desktop environment, less demanding on computer resources) 12.04 LTS, the drivers may still be available.

[HTML]http://old-releases.ubuntu.com/releases/xubuntu/releases/[/HTML]
If you would like to try an older LTS release of Xubuntu.

I'm currently using Lubutu 14.4 lts. Soo erm yeah. I'll try what the others have said first if I still get no joy I'll downgrade to 12.4. And if I get no joy from that the thing is going to Windows. And on the second hand market this is the top of the range cars that will work for the motherboard I have in my machine. I really can't afford to have a nice machine so have to have pretty out dated equipment just to be able to have a decent machine.

---

### Post by Axxon95 on 2014-07-30
I did some quick looking up, the GF2 series specifications(by hardware) says it is fully compliant with OpenGL 1.2.
As seen in my previous post, my GF4 MX440 got OpenGL 1.2 so it might not be too far fetched to see a GF2 working.

I don't know if this will work, but I have had some problems with my old AGP cards. Try reseating it.
A few times when I used my MX 440 and my FX5200s, I've had to reseat them to get them to work properly.

---

### Post by kazica on 2014-07-31
i managed to get the drivers to install but i'm stuck on a 600x800 aspect ratio to a large 22inch display ( old tv turned into monitor) I'm also at a miss on how to activate the open Gl. I tried the glxinfo | grep OpenGL info and again got this 
```
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Error: couldn't find RGB GLX visual or fbconfig
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Error: couldn't find RGB GLX visual or fbconfig
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
```

Am I going wrong someplace? I've also reseated the card and still nada.

---

### Post by kazica on 2014-07-31
from an lspci ```
01:00.0 VGA compatible controller: NVIDIA Corporation NV11 [GeForce2 MX200] (rev b2)
``` but still nothing in my software updater thingy. neouvo has been installed so have the Nvida 173 drivers so really at a loss now. Sorry for being rubish at this but i'm pretty new to it all.

---

### Post by Yellow Pasque on 2014-07-31
The nvidia 173 driver does not support your card. Remove it and reboot. Then, copy/paste your /var/log/Xorg.0.log (use code tags since it's a lot of text).

---

### Post by kazica on 2014-08-01
stupid question but my google fu isn't overly too good here so how do I uninstall the 173 drivers?

never mind I figured it out :).

---

