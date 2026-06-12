---
title: "HP Pavilion dv5-1002nr - Laptop Testing"
date: 2009-05-05
forum: Hardware
---

### Post by amascuba on 2009-05-05
Hi all,

Long time Linux user and fairly new to Ubuntu (I've been using it since 8.04 LTS) here. I bought my HP Pavilion dv5-1002nr back in November 2008, with the intent of using Ubuntu on it. For the last several months, I've been playing around with Vista and getting a feel for it, but it's time to make the switch. All my other computers are running some flavor of Linux. So this week I started doing some testing on it with Jaunty Jackalope.

Here is what I have so far:
[https://wiki.ubuntu.com/LaptopTestingTeam/HewlettPackard/Pavillion_DV5-1002NR](https://wiki.ubuntu.com/LaptopTestingTeam/HewlettPackard/Pavillion_DV5-1002NR)


I've only been running it from a LiveCD and I'm pretty confident that I will be doing a full install soon.

Almost everything works straight out of the box. There are a few exceptions, however.

Here are some of the things that stuck out:

[LIST]
[*]If you plug in a USB mouse after it's booted up, the touchpad gets disabled. After you unplug the USB mouse, the touchpad doesn't enable. If you boot Ubuntu up with the USB mouse already plugged in, both the USB mouse and touchpad work when it boots up.
[*]Bringing the notebook back up from a suspended or hibernation mode will lock up the touchpad. If you use a USB mouse, it will work.
[*]The sound card doesn't seem to function initially, but it will start working if you test the sound card or bring the notebook back up from a suspended/hibernation mode.
[*]The sound doesn't appear to play as loud as it should. Possibly using the wrong driver.
[/LIST]
To test the IrDA port I used the remote, which worked for volume control and suspend mode. I haven't tested any other functionality of the remote.

I haven't tested the built in webcam or microphone yet. That will be coming shortly.

Anyways, that's my preliminary on running the LiveCD on Ubuntu 9.04 (Jaunty Jackalope). I will be installing it soon and trying to work out any bugs, as well as keeping the wiki updated on what I've done to provide full functionality. 

Hopefully this thread is in the correct forum, if not, feel free to move it MODS. It's also my first contribution to the community. I'm sure there will be more to come.

James

---

### Post by shayaknyc on 2009-09-29
This is great. I installed 9.04 onto the same model laptop and so far I'm very pleased. I even got the webcam to work. However, for some weird reason, the built-in mic doesn't seem to work, and I'm not sure how to go about getting it to work. Webcam without sound is kinda useless.

Hope there's more progress on this...

Thanks,
S

---

### Post by josecuervo on 2009-12-21
I'm glad to find other users have a dv5-1002nr.
I need to change the booting sequence in BIOS ver F.37 8/18/09. I have an external USB Maxtor 120Gb harddisk, in which I want to install Ubuntu.
Problem: I can not change the booting order of the external USB above the harddisk.
Any ideas?

Thanks,

---

### Post by pabloda on 2010-05-04
Have you tried with new 10.04?

---

### Post by sdlynx on 2010-05-05
> **pabloda said:**
> Have you tried with new 10.04?

Mic is working along with the webcam in 10.04.  Even the flash extension for the webcam and mic are working for me, its great.

However, I cannot figure out how to get the remote to completely work.  Currently volume up and down work, along with suspend.  Also that change monitor button presumably works.  The arrows will actually let you scroll on a page as well.

---

### Post by pabloda on 2010-05-06
> **sdlynx said:**
> Mic is working along with the webcam in 10.04.  Even the flash extension for the webcam and mic are working for me, its great.

However, I cannot figure out how to get the remote to completely work.  Currently volume up and down work, along with suspend.  Also that change monitor button presumably works.  The arrows will actually let you scroll on a page as well.

Maybe you can manually map them.
And another question, can you get the compiz effects enabled?
I mean because it is an ATI card (HD3200) and Ati drivers are not very good in Ubuntu. It went fine? Which drivers did you used?

---

### Post by sdlynx on 2010-05-09
> **pabloda said:**
> Maybe you can manually map them.
And another question, can you get the compiz effects enabled?
I mean because it is an ATI card (HD3200) and Ati drivers are not very good in Ubuntu. It went fine? Which drivers did you used?

Well, in fact I have a 1251nr, so the card in mine is an nVidia GeForce 9200M, sorry.

I figure the remote/mic/webcam would be the same, but the graphics cards aren't.

---

