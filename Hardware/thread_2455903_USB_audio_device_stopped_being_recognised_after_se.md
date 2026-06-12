---
title: "USB audio device stopped being recognised after several weeks of no issues"
date: 2020-12-30
forum: Hardware
---

### Post by chrysanthemum2 on 2020-12-30
Hi all,
I have an external USB audio device which I've been using with 20.04 for a few weeks now (and for many months before with previous versions) and today it has stopped being recognised and doesn't show up in 'lsusb' or 'pavucontrol'. I didn't even shut down my computer overnight, just suspended it, and yet, this morning it's no longer recognised. It's a Behringer UMC404HD.

So far I have tried:
[LIST]
[*]Commenting out and uncommenting the 'options snd-usb-audio index=-2' line in /etc/modprobe.d/alsa-base.conf, and restarting alsa with 'sudo alsa force-reload' after each. 
[*]Restarting computer after both of the above. 
[*]Looking for the device in 'aplay -l' and 'lsusb', where it's no longer shown. 
[*]Restarting pulse audio using 'pulseaudio -k && pulseaudio' and 'killall pulseaudio'. 
[*]Unplugging and replugging the device, both from the computer and from the wall socket. 
[*]Running 'dmesg' both before and after plugging the device, and the output is identical. 
[*]Plugging the device into another computer (my laptop) which runs an older version of Ubuntu, same issue, not recognised. 
[/LIST]

Any ideas what's going on and how to fix? Thanks in advance.

---

### Post by CatKiller on 2020-12-30
Have you tried unplugging and replugging the USB cable? [s]Does the device show up in lsusb?[/s] Do you get messages about the device in dmesg when you plug it in? You want to try to narrow down whether you've got a sound problem or a hardware problem.

Edit: just noticed that you said it *doesn't* show up in lsusb, which means it's a hardware issue rather than a sound configuration one.

---

### Post by chrysanthemum2 on 2020-12-30
> **CatKiller said:**
> Have you tried unplugging and replugging the USB cable? [s]Does the device show up in lsusb?[/s] Do you get messages about the device in dmesg when you plug it in? You want to try to narrow down whether you've got a sound problem or a hardware problem.

Edit: just noticed that you said it *doesn't* show up in lsusb, which means it's a hardware issue rather than a sound configuration one.

Yes I've tried unplugging and replugging the device, no difference. I don't think I see the device in the output of dmesg, but I might be missing it. I can copypasta the output here if helpful, but it is pretty long.

---

### Post by CatKiller on 2020-12-30
You can use ```
sudo dmesg | tail
``` to see the last few lines. Do it before and after you plug it in, and you can compare the outputs to see if you're getting anything as a result of plugging it in.

Then it's the usual troubleshooting steps: does it work on a different computer, does it work if you use a different cable, and so on, to see where exactly the problem lies.

---

### Post by chrysanthemum2 on 2020-12-30
> **CatKiller said:**
> You can use ```
sudo dmesg | tail
``` to see the last few lines. Do it before and after you plug it in, and you can compare the outputs to see if you're getting anything as a result of plugging it in.

Then it's the usual troubleshooting steps: does it work on a different computer, does it work if you use a different cable, and so on, to see where exactly the problem lies.

Thanks! OK so I can confirm the output of that command before and after plugging the USB audio device in are identical. I have since also tried to plug the device into my laptop (which still runs an older version of Ubuntu) and it also is not recognised.

Perhaps I should add that it's a Behringer UMC404HD. I only have the one cable which fits the device as the connector on the end which goes into the device has some non-standard connection, unlike the standard USB at the other end which goes into the computer.

Did you get any snow in Southend btw? I'm in NW London and none yet but heard East Anglia and Essex got some.

---

### Post by CatKiller on 2020-12-30
> **chrysanthemum2 said:**
> Thanks! OK so I can confirm the output of that command before and after plugging the USB audio device in are identical. I have since also tried to plug the device into my laptop (which still runs an older version of Ubuntu) and it also is not recognised. 

So it does seem like it's a problem with the unit, or the connection, rather than a problem with your computer. You could try powering it off the mains rather than over USB, if you haven't already, to see if it makes a difference. 

> Perhaps I should add that it's a Behringer UMC404HD. I only have the one cable which fits the device as the connector on the end which goes into the device has some non-standard connection, unlike the standard USB at the other end which goes into the computer. 

From a quick squiz at a picture, it *looks like* a USB B connector, but it might be different. If it is weird in some fashion you might be able to get a replacement from Behringer or some audio equipment spares people. 

> Do you get any snow in Southend btw? I'm in NW London and none yet but heard East Anglia and Essex got some.

Not yet, although the weather forecast says it's a possibility. This part of the country is pretty dry generally, so we often miss out on weather.

---

### Post by chrysanthemum2 on 2020-12-30
> **CatKiller said:**
> So it does seem like it's a problem with the unit, or the connection, rather than a problem with your computer. You could try powering it off the mains rather than over USB, if you haven't already, to see if it makes a difference. 

 

From a quick squiz at a picture, it *looks like* a USB B connector, but it might be different. If it is weird in some fashion you might be able to get a replacement from Behringer or some audio equipment spares people. 



Not yet, although the weather forecast says it's a possibility. This part of the country is pretty dry generally, so we often miss out on weather.

Thanks. You may be right about it being a USB-B. I'll see if I have a spare one of those around. I have now restarted the device by unplugging and replugging it from the wall socket, and no change.

---

### Post by chrysanthemum2 on 2020-12-30
Update: I found I had a spare USB-B cable which fit fine and now it has re-appeared on pavucontrol and works again! Woohoo! Thanks so much for all your help and an early happy new year!

---

### Post by CatKiller on 2020-12-30
No worries: glad you got it working again, and it was an easy fix.

---

