---
title: "Experiences with Acer Aspire 9303"
date: 2007-05-07
forum: Hardware &amp; Laptops
---

### Post by TheScorp on 2007-05-07
I`ve been doing some quick sweeps over the forums in order not to double post this, and I am hoping someone might tell me what their experiences has been with the above mentioned laptop.

My plan is to get rid of Vista, because frankly, it doesnt work as it should and since I formerly ran gentoo I would like to try something new and different.

Has anyone tried ubuntu 64-bit and perhaps even cedega on an Acer Aspire 9303?

Edit: Added link with spec

[http://global.acer.com/products/notebook/as9300.htm](http://global.acer.com/products/notebook/as9300.htm)

---

### Post by noseaslistocalisto on 2007-06-08
I have install ubuntu feisty 32bits on my acer aspire 9303wsmi, and all works fine1! excep orbicam, but i have ound on web news about depoying drivers on it.

goo luck, u have a good and nice laptop!  ;)

---

### Post by FoefuR on 2007-08-06
I've installed the 64bit version and ubuntu is running great exept the build-in speakers won't work
When i plug the headphones in there is sound but the speakers just won't work (seems to be a problem with ALSA)
Besides the sound problem everything was recogniced fine

greetinz

---

### Post by bjorntheart on 2007-08-17
> I've installed the 64bit version and ubuntu is running great exept the build-in speakers won't work
When i plug the headphones in there is sound but the speakers just won't work (seems to be a problem with ALSA)
Besides the sound problem everything was recogniced fine

I'm having the exact same problems on my Acer 9300. My logitech usb headphones works just fine, but the built-in's don't work and the volume control on the headset don't work either

---

### Post by chantron on 2007-08-17
You can fix the sound issue by opening up a terminal and typing in alsamixer.

You'll see that the "surround" part has an "MM" at the bottom. Select surround and hit the M key to unmute it. Then hit up until the volume is high enough.

---

### Post by tgellen on 2007-08-28
I too have an Acer Aspire 9303 WSMi and I've gotten the Webcam to work ( For V4L2 software ) ... See my post at [http://ubuntuforums.org/showpost.php?p=3114742&postcount=6](http://ubuntuforums.org/showpost.php?p=3114742&postcount=6) for more details.

I've also found if I installed the latest Atheros Wifi drivers from the MADWIFI subversion repository I get a better signal (80 - 90%) instead of (40 - 60%) even though my laptop is less than 12 inches from my wireless router :)

---

### Post by bjorntheart on 2007-08-30
> **chantron said:**
> You can fix the sound issue by opening up a terminal and typing in alsamixer.

You'll see that the "surround" part has an "MM" at the bottom. Select surround and hit the M key to unmute it. Then hit up until the volume is high enough.

Thanx chantron. Worked perfectly!

I'm now faced with a problem called "headphones only work when I'm playing a cd and not when playing music files with exaile from harddrive".

Any suggestions on this one?

---

### Post by bryston on 2007-10-18
> **bjorntheart said:**
> I'm having the exact same problems on my Acer 9300. My logitech usb headphones works just fine, but the built-in's don't work and the volume control on the headset don't work either

I have a 9304 Acer and initially had the same problem with the sound.  Go to preferences in the volume icon top right and make sure all volumes are turned up high.  the volume that seems to control the speakers is surround i think not front

---

### Post by bjorntheart on 2007-10-18
Thanx Bryston

A while back I switched to Mandriva, but had a problem getting my headset to work. I got so fed-up with struggling with the headphones that I decided to switch back to Ubuntu Feisy. Headphones work fine now, but I not to worried about the laptop speakers anymore. The logitech heaphones speakers is better qualtiy than the laptop speakers. So I can do without the laptop speakser

Thanx for the reply, Cheers

---

### Post by verdomde on 2007-12-29
hey there, any of you guys had problems with the accelerated graphics drivers? My system hangs all the time cos of them

---

### Post by kioftes on 2008-03-08
Hi guys! It seems that i cannot get bluetooth to work in a 9302wsmi...any knowledge of the problem??

---

### Post by tgellen on 2008-04-30
Give Hardy a try. I've been running the 64-bit edition for a few days now and all my hardware seems to work straight out of the box. Unfortunately the 9303 doesn't have Bluetooth. I have to say Hardy is the best version of Linux yet that I've tried on this laptop. Running OpenOffice and Firefox from the LiveCD was much faster than running them in Vista installed on the Harddrive!!! Go figure.

---

