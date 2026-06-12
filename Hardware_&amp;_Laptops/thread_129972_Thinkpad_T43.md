---
title: "Thinkpad T43"
date: 2006-02-15
forum: Hardware &amp; Laptops
---

### Post by rjl on 2006-02-15
I just picked up a Thinkpad T43 and plan to get rid of windows and install either ubuntu or kubutu and was wondering if it matters from a hardware point of view.  I would like to get the dedicated keys to work to the extent possible (esp volume). 

I tried the live versions of both and they both seem fine.  I prefer kde (kmail and k3b over evolution and gnomebaker), but I could live comfortably with either ubuntu of kubuntu.

My knowledge is limited, so input would be appreciated.

Bob

---

### Post by mips on 2006-02-15
The underlying system is the same wether you use Gnome or KDE, so use what you prefer.

I found a very good T4x guide somewhere linked from these forums but don't have it book marked. In the meantime search for T42 or T43.

---

### Post by facefur on 2006-02-15
I have a T43 set up for dual boot (I have to use WinXP for work) and the Breezy install worked flawlessly from the CD ISO.  I also ran the Automatix to do updates.  That had a couple of problems, but they were easily corrected.

FWIW, I elected for Gnome, and it's working fine.

---

### Post by jimrz on 2006-02-16
no need to go either or on gnome v. kde...install ubuntu then from synaptic get kubuntu-desktop (synaptic will find all dependencies and install them as well), or vice versa (I did from ubuntu because synaptic is sooooo easy). this will give you all the goodies of both and your choice, at login, of which wm to use for the session.

---

### Post by mips on 2006-02-16
[QUOTE=jimrz]... (I did from ubuntu because synaptic is sooooo easy)... [/QUOTE]

I don't think synaptic is any 'easier' than adept. For me they are the same in functionality & ease of use.

---

### Post by rjl on 2006-02-17
Thanks to all.

I'm going to try a Kubuntu install in a few minutes.

---

### Post by vrode on 2006-02-26
can anyone share their expirience(s) regarding their thinkpad t43 w/ ubuntu. I'm mostly interested in screen resolution configuration.

I'm having issue (jaggedness) lowering my resolution from 1400x1050.


regards,
/virendra

---

### Post by zojas on 2006-03-05
1400x1050 is the native resolution, don't change it. you might want to tell X the dpi though. I measured the screen with a ruler, then added this line to the Monitor section of /etc/X11/xorg.conf:

```

DisplaySize     305     230 # 1400x1050 116x116 dpi 1400/(mm/25.4)

```

then X will know how big your monitor is. after restarting X, you can then adjust font sizes to taste.

---

