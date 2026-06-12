---
title: "Sound and wireless intenet problem on satellite A135-4666"
date: 2007-09-08
forum: Hardware &amp; Laptops
---

### Post by j12 on 2007-09-08
I got tired of just using windows vista on my laptop and I wanted something a little different so I went with ubuntu 7.04. I was very happy with it but I cannot get the sound to work. And the wireless internet stopped working. When i first installed it i was able to connect to secured wireless network when i just put in the wep key. After i restarted my computer the wireless does not work anymore. Every time i put in the key it tries to connect but then the "enter your wep key" window just pops up again. What could be the problem?

---

### Post by lisati on 2007-09-08
> **j12 said:**
>  I was very happy with it but I cannot get the sound to work. 
I use one of the Toshiba A100 range of laptops and had no sound on it after a fresh install of Ubuntu 7.04. Getting the wireless connection to work wasn't a major hassle, and I had a wired connection available as an option if WiFi didn't work.
The first step in finding a solution for the sound woes on my machine was to install the system updates.  Ubuntu usually shows some kind of icon on the screen if it recognizes that there are updates available. Failing that, you can find the option to check for updates on the System->Administration->Update manager menu (if you're using Ubuntu rather than one of the other flavours of this distro)
Once I'd updated, a restart and tweaking the volume control (and checking the "mute" settings) were enough.
Let us know if this helps.

EDIT: for the Wireless Key there are options available to help automatically enter it for you...

---

### Post by j12 on 2007-09-08
allright, installed all 100-something updates. Still no sound and the wireless still asks me over and over again for my password. Although I might have heard a very faint sound when I played a song but I am not absolutely sure.

---

### Post by j12 on 2007-09-09
Got the sound to work now, but wireless internet is still not fully functioning.

---

### Post by j12 on 2007-09-10
Does anyone know of any software or application that can help me use my wireless connection?

---

### Post by sockerbit on 2007-09-12
i like wlassistant

run terminal 

type sudo apt-get install wlassistant

enter your password

an icon will show up under applications/internet but it won't work because you have to run it using sudo so start up terminal or alt+f2 and type sudo wlassistant

it won't automatically connect but it saves your password and takes like 3 seconds to run.

---

