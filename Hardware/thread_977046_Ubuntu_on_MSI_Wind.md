---
title: "Ubuntu on MSI Wind"
date: 2008-11-09
forum: Hardware
---

### Post by NoobToast on 2008-11-09
Im looking at buying a [MSI Wind]("http://www.newegg.com/Product/Product.aspx?Item=N82E16834152074"), what i wanna do is install Ubuntu on it. Pretty much what im wondering is if its going to recognize everything on it, wifi, touch pad, webcam, etc...

---

### Post by NoobToast on 2008-11-10
Nobody tried it?!?!? I find it hard to believe...

---

### Post by JAGelius on 2008-11-10
Well, I'm looking around here to find someone who has solved the wifi-issue in 8.10. I guess you have to compile the driver, but I need instructions.

Also the webcam can give you trouble, but there are workarounds for that too.

---

### Post by benhur99ph on 2008-11-10
Look here --- > [Ubuntu_8.04_Hardy_Heron on the MSI Wind]("http://wiki.msiwind.net/index.php/Ubuntu_8.04_Hardy_Heron") it covers alot regarding Ubuntu on the MSI Wind. Though this is based on Hardy.

---

### Post by jepong on 2008-12-23
> **JAGelius said:**
> Well, I'm looking around here to find someone who has solved the wifi-issue in 8.10. I guess you have to compile the driver, but I need instructions.

Also the webcam can give you trouble, but there are workarounds for that too.

wifi issues? take a look here... [http://boskastrona.ovh.org/index_en.html]("http://boskastrona.ovh.org/index_en.html")

---

### Post by Zorael on 2008-12-23
I have an Advent 4211, cheapo rebranded Wind, came with XP installed. I replaced the internal wifi card with a proper Intel 4965AGN so I needn't worry about compiling drivers, though that isn't really hard to do. You'd have to do it once every kernel update, but as long as you keep the files on your harddrive it's just a minutes' effort.

Sound works, touchpad works, special keys work (toggle touchpad, brightness up/down, volume up/down, toggle webcam, toggle bluetooth/wifi, sleep). Advent bioses do not support the Fn-key overclocking thing, so I can't comment on that one.

All in all, works great. I just wish I didn't have that awful Sentelic mousepad. Use [unetbootin](http://unetbootin.sourceforge.net/) to prepare a live usb stick, then hit F12 when starting up to boot from it. Don't wipe the service partition; if anything, make a backup of it once you have your Linux installed. In case stuff goes bad.

(That's probably piracy. Nowadays, just because you bought something doesn't mean you own it. Sick.)

---

### Post by phil02 on 2008-12-28
I am using Intrepid with the Netbook remix packages on my Wind.
To make the Ralink b/g/n wireless card work I installed the ppa from [https://bugs.launchpad.net/bugs/210725](https://bugs.launchpad.net/bugs/210725).
To configure the touchpad I used the GPL Sentelic driver.  See [http://forums.msiwind.net/default-msiwind/sentelic-linux-drivers-released-under-gnu-gpl-t4828.html](http://forums.msiwind.net/default-msiwind/sentelic-linux-drivers-released-under-gnu-gpl-t4828.html)

---

