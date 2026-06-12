---
title: "[SOLVED] Cant get 1280x800 resolution on laptop."
date: 2006-06-06
forum: Hardware &amp; Laptops
---

### Post by chrismyers on 2006-06-06
Hi there,

My Medion MD95564 laptop wont achieve 1280x800 screen resolution. It will only do 1024x768.

Does anyone know how to fix this in Dapper?

lspci produces the following info about my graphics card:

0000:00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04) (prog-if 00 [VGA])
        Subsystem: Mitac: Unknown device 8048
        Flags: bus master, fast devsel, latency 0, IRQ 209
        Memory at d0000000 (32-bit, non-prefetchable) [size=512K]
        I/O ports at e000 [size=8]
        Memory at a0000000 (32-bit, prefetchable) [size=256M]
        Memory at d0080000 (32-bit, non-prefetchable) [size=256K]
        Capabilities: [d0] Power Management version 2

0000:00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
        Subsystem: Mitac: Unknown device 8048
        Flags: bus master, fast devsel, latency 0
        Memory at d0100000 (32-bit, non-prefetchable) [size=512K]
        Capabilities: [d0] Power Management version 2

I hope someone can help....

Many thanks.

---

### Post by ruffneck on 2006-06-06
Try:

Enable Universe Repositories in Synaptic then reload. Install the "915resolution" package. 

Open up a terminal and run the following command:

```
sudo 915resolution -l
```

Look for the mode that gets you "1280x800, 32 bits/pixel"

example - "Mode **7e** : 1280x800, 32 bits/pixel" for me.

Finally, do:

```
sudo gedit /etc/default/915resolution
```

Set the correct Mode and use XRESO=1280, YRESO=800

Save, Logout of X and do a Ctrl+Alt+Backspace.

---

### Post by wjp.reg on 2006-06-06
Worked like ruffneck said..

On my new Lenovo 3000 N100 with Intel945 Graphics chipset.

Thanks much!!

---

### Post by kiwiboyus on 2006-06-06
Sweet! Thanks for the fix this issue  :KS 
I am now running 1280x800 on my Acer Laptop 

I'm really starting to love Dapper, I just need to figure out my issue with
WPA wifi  ](*,) :wink:

---

### Post by chrismyers on 2006-06-07
[QUOTE=ruffneck]Try:

Enable Universe Repositories in Synaptic then reload. Install the "915resolution" package. 

Open up a terminal and run the following command:

```
sudo 915resolution -l
```

Look for the mode that gets you "1280x800, 32 bits/pixel"

example - "Mode **7e** : 1280x800, 32 bits/pixel" for me.

Finally, do:

```
sudo gedit /etc/default/915resolution
```

Set the correct Mode and use XRESO=1280, YRESO=800

Save, Logout of X and do a Ctrl+Alt+Backspace.[/QUOTE]


Cheers ruffneck. I finally got it working with some extra work.

sudo 915resolution -l didnt provide me with a res of 1280x800. I realised that I had originally upgraded from a beta of 6.06 & allthough it sould be up to date I guessed that there was a deeper problem. 

I reinstalled Dapper & tried your suggestion. It worked great.

Many thanks.

---

### Post by rex_drecor on 2006-06-08
Hi, I had the same problem,  I insalled KDE to see if it was any different, and found a "control panel" sort of settings screen. Changed the monitor to a 'Generic 1024x768 Flat panel' and it worked, Checked and it works with gnome as well :)

Wish I had seen your way first!

I hate being new at stuff! :-\"

---

### Post by chrismyers on 2006-10-26
Update for Edgy Eft...

I followed the above & I also had to reconfigure by doing:

sudo dpkg-reconfigure xserver-xorg

I accepted all the defaults exept "Emulate 3 button Mouse" which fixed my res problem. It also had the added bonus of enabling the scroller on the right-hand side of my touchpad.

P.S.

I would appreciate any tips on answering the reconfigure options, as I just tried guesswork & I probably didnt set optimal options for my system. :-?

---

### Post by LaVache on 2006-10-30
I second the process in chrismeyers' recent update for 6.10

I added the 915Resolution package, configured it as above, but to get it to work I also had to run:

sudo dpkg-reconfigure xserver-xorg

Now its working at 1280x1024.

---

### Post by chrismyers on 2006-10-31
> **LaVache said:**
> Now its working at 1280x1024.

Surely you mean 1280x800? :-k

---

### Post by LaVache on 2006-11-01
Surely I don't.  ;) 

I followed the methods in this thread to enable higher resoultion for external monitor support from my laptop when docked, hence the 1280x1024 in my post.  

An update too -- I switched to the vesa driver due to screen artifacts I was getting with the i810 driver.

---

### Post by mocoloco on 2006-11-01
> **kiwiboyus said:**
> Sweet! Thanks for the fix this issue  :KS 
I am now running 1280x800 on my Acer Laptop 

I'm really starting to love Dapper, I just need to figure out my issue with
WPA wifi  ](*,) :wink:

Off the thread topic, but the default network monitor applet doesn't do WPA, install network-manager-gnome (or knetworkmanager in KDE) and your WPA should work beautifully.  Worked for me :-D

---

### Post by dmt195 on 2006-11-07
Thanks ruffneck and others for the tips. I wondered if you could offer any help to my situation.
I have an HP WXGA laptop running Edgy. I followed your tips and got it in the correct resolution. Unfortunatley if I reboot I always have to do the alt+ctr+backspace to reset X into the right mode. Is there a way of getting this to happen automatically?!
TIA. 

PS - I'm loving Edgy otherwise and have fully migrated for the first time. :cool: Feels good!

---

### Post by James Maxwell on 2006-11-26
This would seem to work but only with intel chips. is there an equivelent. my graphics processor is an sism760gx.

---

### Post by jefferson101 on 2006-11-28
Thanks ruffneck, I was having this same problem with my laptop, and was able to fix it in like 5 minutes thanks to your help.

---

### Post by willhelmwr on 2007-05-09
I love my Kubuntu in 1280x800! But why do i have to change it each time I start play with it? Same as wifi...:(

---

### Post by inik on 2007-10-12
working fine on my fujitsu siemens amilo pro 3205 (1280x800) running gutsy 7.10
thanks

---

