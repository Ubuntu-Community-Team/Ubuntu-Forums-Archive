---
title: "Tascam US-122L in Ubuntu 10.10 Maverick Meerkat"
date: 2011-02-28
forum: Hardware
---

### Post by signal1980 on 2011-02-28
Hello all...

I'm running the latest build of Ubuntu and trying to install my Tascam us-122L. Have been snooping around the various guides and they all seem to suggest that some degree of support for this soundcard is available natively, yet when I post this command into the terminal I get back only:

$ cat /proc/asound/modules

0 snd_hda_intel
1 snd_hda_intel

...which are obviously my onboard cards. My understanding was that Ubuntu should recognise the card already, but that I would have to manually report the soundcard to the 0 or 1 slot, which is fine, but as you can see it doesn't recognise the card is there.

Sad to have to say out loud to you all that I'm a complete noob, but there we are :)

appropriate libsound-plugins and firmware (as far as I'm aware, and according to the package manager) are already installed.

Any ideas. good people...?

Many thanks x

EDIT: Green USB light comes on, but the card is still not listed after entering:

$ cat /proc/asound/modules 

...into the terminal. 

I know this has been a hotly debated issue for a while now, and it may be time, as somebody already suggested, to consign the device to the 'unsupported' category. But as so many people have it working already, I feel confident I could just follow the existing guides and get it to work if I could first get the computer to recognise it. Only none of the guides talk about that problem.

Thanks for any help.

---

### Post by tchakabam on 2011-03-19
You tried this one? 

[http://www.linuxmusicians.com/viewtopic.php?f=6&t=1073](http://www.linuxmusicians.com/viewtopic.php?f=6&t=1073)

---

### Post by Feareilo on 2011-03-21
I am having the same problem. I think it might be related with the firmware. I upgraded my US-122L to the latest firmware and drivers in Windows. Now I want to use it in Ubuntu but it is not working. The Briata walkthrough seemed very easy... but the unit is not recognized in proc/asound/modules and nothing seems to work. If you ever get around this, please share how you did.

---

### Post by Feareilo on 2011-03-31
Just to let everyone know, I downloaded and downgraded to the oldest firmware (0.2, I think) using Win*dose* XP and guess what... Ubuntu 10.04 64bit recognized the card! I haven't thoroughly tested it as this is not the computer I want to use it in. However, I think this is a relevant finding. Hope it helps you.

---

### Post by deoanam2002 on 2012-01-10
This worked for me on the plain ol' US-122 on Ubuntu Studio 10.10:
[http://resteasy.info/index.php/2-installing-tascam-us-122-on-ubuntu-1010-maverick](http://resteasy.info/index.php/2-installing-tascam-us-122-on-ubuntu-1010-maverick)

---

### Post by mikeb93 on 2012-06-04
I can't get the 122l working. Tried dozens of tutorials

lsusb:
```
Bus 001 Device 010: ID 0644:800e TEAC Corp. TASCAM US-122L
```

cat /procasound/cards:
```
 2 [U0x93a0x262c   ]: USB-Audio - USB Device 0x93a:0x262c
                      USB Device 0x93a:0x262c at usb-0000:00:13.1-2, full speed
 3 [US122L         ]: USB US-122L - TASCAM US-122L
                      TASCAM US-122L (644:800e if 0 at 001/010)
```

cat /procasound/modules:
```
 3 snd_usb_us122l
```

any1 any ideas?

---

