---
title: "Multiple Bluetooth Conflict"
date: 2008-05-21
forum: Hardware
---

### Post by sinnerou on 2008-05-21
I just made the switch to ubuntu and I like it so far.  I spent the better part of a day getting my plantronics 590 headset working and it does, however, I use a microsoft 8000 bluetooth mouse as well and they interfere with each other.  The mouse floats when using the headset and the sound cuts out when using the mouse.  I have been unable to fix this.  I think hciconfig looks promising but I can't get it sorted.  Any help would be appreciated.

Thanks

---

### Post by prokher on 2009-10-02
Same problem with my thinkpad x200s, logitech bluetooth mouse and sony headset. :(

---

### Post by bovender on 2009-11-02
Hi,

same here:
[LIST][*]Headset: Plantronics 590[*]Mouse: Logitech V470[/LIST]

It's great how the A2DP stereo profile works out of the box in Ubuntu; however this interference problem is a bit annoying. I just recently switched over to Ubuntu (now 9.10) from Windows XP; the very same hardware setup worked flawlessly with XP, no conflicts at all.

Any help would be greatly appreciated.


edit: added "stereo profile"

---

### Post by jthirt on 2009-11-21
I experience the same symptoms with:

[LIST]
[*]**Headset**: Motorola S9
[*]**Mouse**: Logitech V470
[/LIST]

Each work fine individually, but audio becomes inaudible once mouse is used. 

I can't find any guidance to try and address this. I am using a Samsung NC10 netbook running Karmic NBR and I was hoping I could get rid of wired accessories! :p

Yeah, there is a touchpad, but I'm not good at using it... :redface:

JT

---

### Post by dmears on 2009-12-07
Add me to the list:
 
Motorola S805 headset
Apple Wireless Keyboard
Asus Bluetooth Dongle (Broadcom based).

---

### Post by sputnikeee on 2010-02-01
I hope this thread is not gone & forgotten.  Same occurs here between:  Logitech MX-1000 bluetooth mouse & Plantronics 220 Headset. Haven't tried my bluetooth stereo (in storage) yet, but I fear the worst.  Cursor floats across screen as either mic or speaker has audio occurring.  Eventually headset wins the battle, Blueman drops the mouse connection.  Works the same w/cheapo USB bluetooth dongle f/Hong Kong and my $35 high class model.  Asus eee pc 1000HE running eeebuntu (but really upgraded to Ubuntu 9.10 kernel).

---

### Post by dmears on 2010-02-16
Success! If you're having this issue, I suggest you follow this thread:
 
[https://bugs.launchpad.net/pulseaudio/+bug/405294](https://bugs.launchpad.net/pulseaudio/+bug/405294)
 
I was able to resolve my issue by setting the hciconfig as described there. I haven't made the change "persistent" yet, since I rarely reboot and don't mind manually updating the BT config. 
 
Hope this helps.

---

### Post by bovender on 2010-02-16
Confirmed -- thanks, dmears!

I just entered this in a console window:

```
sudo hciconfig hci0 lm master; sudo hciconfig hci0 lp hold,sniff,park
```

BT Mouse and BT headphones work smoothly now.

---

### Post by jthirt on 2010-02-17
Wow! It does the job indeed. :p

It wasn't obvious at first. Probably because I did things in a strange sequence as both devices were already connected. But then it started to work fine. 

It needs to be reset after suspend apparently. 

Anyone knows how to set these changes so that they are persistent?

I wish I found fixes for my Android too, it suffers some BT hicups as well... :(

JT

---

