---
title: "Headphone jack doesn't work (HDA VIA VT82xx )"
date: 2008-09-15
forum: Hardware
---

### Post by L4tt3 on 2008-09-15
Hello.

I've installed Hardy Heron in my laptop (Fujitsu Amilo Li 1705, Intel Celeron 1,6 GHz, 768 mt RAM)few weeks ago. 

Everything seems to work quite well except the headphone jack. There's no headphone switch tab on the volume control or alsamixer. The sound stops coming through the laptop speakers when I Plug headphones into the headphone jack and also no sound's coming from the headphones. Kinda weird, eh?

I've also tried to add some "options snd-hda-intel model=x" lines in the alsabase but none of them seems to help. 

Does anyone of you have a solution? Any tips, help, anything?

Here's some information of my soundchip:

```
 *-multimedia
                description: Audio device
                product: VIA High Definition Audio Controller
                vendor: VIA Technologies, Inc.
                physical id: 1
                bus info: pci@0000:04:01.0
                version: 10
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=HDA Intel latency=0 module=snd_hda_intel
```

---

### Post by 02walshe on 2009-07-16
I'm also getting the same issue. I'm using Kubuntu 9.04, and nothing is working. Every 'fix' that requires compiling, only stops because of some error! And now, KDE has decided my audio card doesn't even exist!

does anyone have an answer? :cry:

---

### Post by Nero147 on 2009-07-16
If you put in 
asoundconf list
what is the output?

---

### Post by 02walshe on 2009-07-16
nothing. 

eoin@SeilalaMapusua:~$ asoundconf list
eoin@SeilalaMapusua:~$ sudo asoundconf list
Please note that you are attempting to run asoundconf as a privileged superuser, which may have unintended consequences.

eoin@SeilalaMapusua:~$ sudo asoundconf list
Please note that you are attempting to run asoundconf as a privileged superuser, which may have unintended consequences.

eoin@SeilalaMapusua:~$ asoundconf list
eoin@SeilalaMapusua:~$ asoundconf list
eoin@SeilalaMapusua:~$
eoin@SeilalaMapusua:~$


See what I mean?

---

### Post by 02walshe on 2009-07-18
Does anyone know how I can restore my sound card to a working order at least?

---

### Post by varun1786 on 2009-07-19
I have the same card on my acer aspire.

Try putting your laptop on standby for sme 10 sec and log-in again. If it does n work on the first try repeat it quite a few times. I did it sme 5 tme's and surprise surprise it started working. 

dono how or why but it did. Sme tme's when i'm logging in my usb mouse also doesn work i hav to unplug it and fix it back on.

But i had the same issues with windows also.

---

