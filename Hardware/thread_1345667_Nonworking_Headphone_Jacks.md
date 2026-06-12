---
title: "Nonworking Headphone Jacks"
date: 2009-12-04
forum: Hardware
---

### Post by ramidavis on 2009-12-04
Hello, i am using ubuntu 9.10 on a hp pavilion dv7 2185dx. Previously, i had been using ubuntu 9.04, but had _no_ sound at all, so i was glad to see that working in my new 9.10 install, but now it appears there is still a sound issue. When you plug in headphones, they are ignored and sound continues through the speakers, and the headphones do not put out any sound. In 9.04, i had to build a alsa snapshot and apply it to every new system kernel, is there a similar thing i can do to get headphones working in 9.10? Other then this tiny bug, i am loving ubuntu.

---

### Post by gradinaruvasile on 2009-12-04
Right click on the speaker icon and open the sound preferences from there. There is a tab named Output - that contains a drop down list (connector) that allows you to manually select the output source. Try setting to headphones from there.

---

### Post by ramidavis on 2009-12-04
Under the output tab, i have;
choose a device for sound output:
(.) internal audio analog sterio
stereo
() r700 audio device [radeon hd 4000 series] digital stereo (hdmi)
stereo

--------------------

settings for the selected device:
balance: _________[]_________
........left|.................|...................|right


I have no drop down list (connector)

---

### Post by Kojans on 2009-12-04
Did you install a mixer, for instance the ALSA mixer?

---

### Post by ramidavis on 2009-12-04
I have what ever the ubuntu 9.10 disc installed, nothing else. Just downloaded gnome alsa mixer from ubuntu software center, now what?

---

### Post by Kojans on 2009-12-04
Start the mixer from Applications-> Sound & Video, and try if moving the faders gets you sound on the headphones, and no sound on the speakers

---

### Post by ramidavis on 2009-12-04
Ok, if i use alsa mixer, **not** the one in my panel, i can turn down the main speaker, and still get sound out the headphones. Can i make that program my default, instead of having to launch it from menu>sound>gnome alsa mixer every time i want to use my headphones?
Tell me why i need a custom program to do something the OS should be doing by itself? If you plug in headphones, the speaker should mute, and all output should then be through the headphones only. As much as i love linux, bugs like this really make me ***not*** want to tell people about it... Is it _really that hard_ to make linux realise that it does not need to have sound blasting out the speaker **and** the headphones at the *same time*!?

---

