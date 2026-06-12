---
title: "AVerTV GO 007 installation"
date: 2005-06-17
forum: Hardware &amp; Laptops
---

### Post by peter07 on 2005-06-17
I have a big problem with AverTV GO 007. I'm new Ubuntu user and I don't know how install this TV card. Please help.

---

### Post by stepper on 2005-06-17
Try to make sense of [this thread](http://ubuntuforums.org/showthread.php?t=41123)  and your card number is 57 I think. Maybe you can come up with the solution.

---

### Post by peter07 on 2005-06-25
[QUOTE=stepper]Try to make sense of [this thread](http://ubuntuforums.org/showthread.php?t=41123)  and your card number is 57 I think. Maybe you can come up with the solution.[/QUOTE]

I have tried, but with no good results - sorry. I still have problems with this card. I can't watch TV and I can't listen to the radio :(

---

### Post by andlinux21 on 2006-03-07
I just purchased the card today I will try to install it and see what problems i run into and post them here:cool:

---

### Post by darthchaosofrspw on 2008-01-16
> **peter07 said:**
> I have a big problem with AverTV GO 007. I'm new Ubuntu user and I don't know how install this TV card. Please help.

sudo modprobe saa7134
sudo modprobe saa7134-alsa

You have to issue a special command in the console to get the audio to play without any other connections. You can to hook up a stereo Y adapter to connect a VCR to the computer's line-in jack and keep the TV tuner program (such as tvtime) on channel 3 and use the VCR like a cable box.

---

