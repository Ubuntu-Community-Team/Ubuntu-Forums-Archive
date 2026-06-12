---
title: "Logitech K800 keyboard.."
date: 2013-04-25
forum: Hardware
---

### Post by netgooroo on 2013-04-25
Hey guys,
I just obtained a K800 Logitech wireless illuminated keyboard. I have a logitech mouse that works fine and also has the unifying little star on the bottom of it so it "should" work with any new unifying logitech technoligy. However, If I plug in the new USB adaptor for the keyboard, niether one works. I have also tried the keyboard with the same adaptor that the mouse uses with no luck.

I have tried plugging everything in and rebooting with no effect.


I'm on 12.04 with latest updates.

Any help would be appreciated. 

**NOTE: I saw others were having some issues with this in the past but, as soon as I posted a reply to the thread, it was closed.** :-s

---

### Post by netgooroo on 2013-05-01
Bump...  any help with this would be appreciated or, I will have to send the keyboard back. :(

---

### Post by fmmarzoa on 2013-05-03
> **netgooroo said:**
> Bump...  any help with this would be appreciated or, I will have to send the keyboard back. :(


I don't know what is your problem, but I have received the same keyboard from Amazon just 5 minutes ago and I am writing this using it in my Ubuntu 12.04.

On the other hand I have a different problem. From some unknown reason and although my keyboard layout is in Spanish, and so it is configured in my Ubuntu, it is working as an english keyboard, so I have neither the Spanish n with tilde nor accents for vowels neither. And this is non acceptable for me at all. Anyway I am trying to solve it.

Edit----
Actually it is working fine as an Spanish keyboard within an independent console -alt+fx- but not within graphical Desktop -XWindow+Unity-. The weird thing is that I have an Spanish keyboard connected before plugin this one and it worked perfectly. Moreover, I used another different keyboard a week ago also in Spanish and also worked perfectly.

---

### Post by fmmarzoa on 2013-05-03
I managed to solve my problem a tricky workaround: I used to have only the Spanish layout, as it is the only I use, but I have added the English/US layout in second place so now I have an icon to change the layout on the top panel, and when it is set to Spanish, the keyboard works as expected.&#65279;

We will never know why I need this in first place, since I didn't need it with all my previous keyboards, but it is working fine, so it is solved and my K800 is working fine.

I think your problem with the receptor is *not* a linux related problem, but somekind of hardware incompatibility. Try the same configuration with a supported OS if you can, and contact Logitech about the problem. May be your mouse is not compatible with the new 6-device-in-one receptor of Logitech.

---

### Post by netgooroo on 2013-05-03
Thanks for the posts fmmarzoa I appreciate it. 

I have thought about the USB adapter being the problem as well but, wanted to see if there was anything else I could do before I contacted the seller about the issue. I have to say, I really like the keyboard but, if I can not get it to work, I will have to return it. 

I have tried all the USB ports on my PC with no luck so far. The keyboard does turn on and, light up fine as it should. However, It is not recognized by Ubuntu at all. 

I will continue to diagnose as I can but, so far, this doesn't look promising.

---

### Post by Lekensteyn on 2013-05-10
netgooroo, The k800 keyboard works here without issues. Are you sure that the device is paired? If not, try [https://lekensteyn.nl/logitech-unifying.html#ltunify](https://lekensteyn.nl/logitech-unifying.html#ltunify).  The kernel that is loaded for this machine is linux-image-generic-lts-quantal.

---

### Post by netgooroo on 2013-05-10
> **Lekensteyn said:**
> netgooroo, The k800 keyboard works here without issues. Are you sure that the device is paired? If not, try [https://lekensteyn.nl/logitech-unifying.html#ltunify](https://lekensteyn.nl/logitech-unifying.html#ltunify).  The kernel that is loaded for this machine is linux-image-generic-lts-quantal.

I have a wireless logitech mouse that I have used for years with the same unify emblem on it and, it has had no issies at all working with any of my installs. I appreciate your input but, looks like I may have to send the keyboard back. Not sure what else to try. Could also be a faulty keyboard.

---

### Post by Bashing-om on 2013-05-10
netgooroo; Hi !

I also confirm that logitech Wireless keyboard / mouse works with ubuntu 10.04 // Try this and see if the kernel picks it up as a new device:
Power everything down, unplug the power cord for 'bout five minutes and then plug the power cord back in and boot up ubuntu.

Is the KB now recognized ?
[INDENT=2]
just my thoughts

[/INDENT]

---

### Post by netgooroo on 2013-05-10
> **Bashing-om said:**
> netgooroo; Hi !

I also confirm that logitech Wireless keyboard / mouse works with ubuntu 10.04 // Try this and see if the kernel picks it up as a new device:
Power everything down, unplug the power cord for 'bout five minutes and then plug the power cord back in and boot up ubuntu.

Is the KB now recognized ?
[INDENT=2]
just my thoughts

[/INDENT]

Thanks bashing but, tried this and still no go. :-/ Guess I need to send it back.

---

### Post by Bucky Ball on 2013-05-10
I have Logitech keyboard and mouse, different model, working perfectly (plug and play) in Xubuntu 12.04 (and 10.04 before that). This might sound crazy but ... have you checked the batteries? My keyboard takes a couple of batteries and the mouse takes one. Maybe you got a flat one ... or maybe you've got no batteries in there. 

Apologies if this is too obvious ... just a punt.

---

### Post by Lekensteyn on 2013-05-11
Good point Bucky, the K800 has a USB connection... but that one is only used for charging the keyboard (there are no external batteries). All communication is done with the tiny USB receiver that came with the keyboard.

@netgooroo Do you see any mention of a keyboard device in dmesg?
```
dmesg | grep -C3 -i logitech
```

---

