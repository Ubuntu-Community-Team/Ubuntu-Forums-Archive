---
title: "Is there such a thing like an &quot;Ubuntu TV&quot;"
date: 2015-11-21
forum: Hardware
---

### Post by stefan_03 on 2015-11-21
Hey folks,

I am thinking about buying a TV. If it is a Smart TV, it has to be one with an open source operating system. Panasonic has Firefox OS, which is not what I am looking for. While researching I found Ubuntu TV.

Is there a real "Ubuntu TV" ? All I can see is an .iso file, where I can flash some Ubuntu version on my computer. But I do not want to use a Raspberry Pi conntected to my or something like that, I would want to have a TV where Ubuntu is already installed and can be used with a remote control or even with an Android app over my phone.

[IMG]http://www.blogcdn.com/de.engadget.com/media/2012/01/img6954-1326262525.jpg[/IMG]

How did he manage it? :D

Thanks in advance!

---

### Post by ian-weisser on 2015-11-22
Ubuntu TV is a software product Canonical tried to sell to TV manufacturers, one of the earliest fruits of the convergence effort. The picture seems a typical convention booth mockup, intended to  interest manufacturers (Canonical's customers), from those days.

No manufacturer has shipped the software, so you cannot purchase Ubuntu TV hardware.

Ubuntu TV was built on 12.04 and the corresponding version of Unity, and pre-dates the current fad of Snappy and embedded devices. Every year or so, some Canonical employee says that they really must get around to updating Ubuntu TV and shopping it to manufacturers again.

Most users who want a 'smart TV' use an attached computer running Mythbuntu or ordinary Ubuntu. Of course, that's not what you seem to want.

---

### Post by Bucky Ball on 2015-11-22
Buy a [Raspberry Pi]("https://www.raspberrypi.org/products/") or an [Odroid]("http://www.hardkernel.com/main/main.php"), install a spin of Ubuntu, plug it into your TV. You have a Ubuntu TV! :D

I have an Odroid with Lubuntu and Kodi working faultlessly with my TV (running as a media server mostly). Prior to that I was running a RPi with RaspBMC. Also faultless.

You can buy programmable dongles for remote control to use with either (or your regular computer for that matter).

PS: As for your photo and the question: it was managed probably exactly how I've described above. Just plug a computer in (and as there is no Ubuntu TV that I know of, perhaps that is the ONLY way).

PPS: [THIS]("https://www.flirc.tv/") is what I was looking for. FLIRC for remote control. I have one somewhere which hasn't been used in awhile, but when it was, faultless also.

---

### Post by QIII on 2015-11-22
I just put together one of [these]("http://www.hardkernel.com/main/products/prdt_info.php?g_code=G143599699669").  It has an IR receiver you can use with a remote.  It is very inobtrusive:

[ATTACH=CONFIG]265718[/ATTACH]

I know you don't want to attach an R Pi or something, but that is the only way you'll get "Ubuntu TV" for the moment.

(By the way, I made some modifications to my unit:  I fabricated a custom cooling solution that still fits in the case and allows the CPU to run at 100% indefinitely without throttling and I added a USB3 panel mount port to use the other USB3 port that would otherwise be unavailable inside the case.  That is why so many of us are attracted to these things -- you can modify them to suit your needs, just like Linux!)

---

### Post by stefan_03 on 2015-11-22
Ok thanks, this answers my questions. I don't want to deal with Raspberry Pi stuff yet, so it is no option for me right now.

---

### Post by Bucky Ball on 2015-11-22
> **stefan_03 said:**
> Ok thanks, this answers my questions. I don't want to deal with Raspberry Pi stuff yet, so it is no option for me right now.

You could always grab a cheap old or new netbook with HDMI, install the flavour of choice and plug that in. Ubuntu TV! Or just plug your computer in. Good luck and hope one day your Ubuntu TV will be realised. :)

---

### Post by stefan_03 on 2015-12-02
> **Bucky Ball said:**
> You could always grab a cheap old or new netbook with HDMI, install the flavour of choice and plug that in. Ubuntu TV! Or just plug your computer in. Good luck and hope one day your Ubuntu TV will be realised. :)
I will probably do that, to test it. Have to figure out how to use a remote control for that. If I can achieve watching Ubuntu TV with a remote control on my TV with an old pc, the raspberry thing may be a long term solution, I guess :)

---

### Post by Bucky Ball on 2015-12-02
Read a previous post of mine. Flirc is what you're looking for for remote. There's a link a few posts ago. :)

---

### Post by coldraven on 2015-12-03
If you choose Kodi as your media centre there are two Android apps for remote control

Kore is free and is a nice remote control, it shows the Artist and artwork etc.
Yatse is not free but allows you to stream video from your phone to your TV

---

### Post by SeijiSensei on 2015-12-03
My LG TV runs a version of Linux as its operating system.  It has the usual clients for Netflix, etc., and a DLNA client which you could use with a server running minidlna to stream media to the TV.

---

### Post by stefan_03 on 2015-12-07
> **Bucky Ball said:**
> Read a previous post of mine. Flirc is what you're looking for for remote. There's a link a few posts ago. :)
Thanks, I did not realize that they send to Europe as well.

Just another thing: there seems to be no Ubuntu TV iso file on the main ubuntu.com page - is it just Ubuntu 12.04 + a few extra packages? Is there already a 14.04 version as well? Support for 12.04 ends in 16 months...

Another thing: anyone familiar with "Sky" ? It's German PayTV, they have their own digital receiver. Can I connect it to my RasPi and include it somehow into my Ubuntu TV? And are there apps like Netflix, Google Music & co, or do I have to access them via browser? I can hardly find information about this. Is the project Ubuntu TV still alive?

---

### Post by Bucky Ball on 2015-12-07
Install 14.04 LTS. Ubuntu or any other flavour. Then tweak it. There is no 'Ubuntu TV' iso.

Someone can possibly identify the exact program being used in your screenshot and you can install that. I use Kodi myself. It's in the repos. Doesn't look like your pic but effectively does the same.

---

### Post by mastablasta on 2015-12-09
> **stefan_03 said:**
> Ok thanks, this answers my questions. I don't want to deal with Raspberry Pi stuff yet, so it is no option for me right now.

with Rpi I had "media center" up and running in about 20 mins or something. all I had to do was install (re-image) Openelec/Kodi on the SD card. tell it where the movies and shows are on the hard disk I plugged to it and that was it. it updated the database from internet and I was good to go. for TV there are plugins that are easy easy to install (select, click install). no smartphone needed as TV recognised Kodi and Tv remote worked fine. I have an 6 year old LG TV. later on I setup subtitles plugin and transmission plugin.

when the Pi goes I will replace it with version2. I am very satisfied with it. and latest version of Openelec/Kodi improved performance so much that everything is working very fast and it uses very little power. RPi has 4 or 5W, hard disk is not that much more if it even is more.

---

