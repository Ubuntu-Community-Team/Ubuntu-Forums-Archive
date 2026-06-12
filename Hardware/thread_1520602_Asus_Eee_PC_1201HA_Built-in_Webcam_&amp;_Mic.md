---
title: "Asus Eee PC 1201HA Built-in Webcam &amp; Mic"
date: 2010-06-29
forum: Hardware
---

### Post by aleperno on 2010-06-29
Hello mates, I've recently purchased an Asus Eee PC 1201HA, and as usual installed in it Ubuntu 10.04 LTS.
Ive managed it to detect my 1366x768 resolution, Wifi, Bluetooth, Touchpad & Key Features, but theres is yet something I havent managed to run as desired.

-Built-In Microphone is recognized by the system and works, but it sounds very low, and if turn it up, you can hear "static or rain" and its pretty annoying.

-Built-In Webcam. aMSN manages to work perfectly with it, however, its the only one. Cheese shows very low FPS. EMESENE and Skype(most important), recognizes the device but doesnt show any image.

Any help will be welcomed, Im quite an Amateur on Ubuntu.
Pardon my English, not my native language.
Cheers.

---

### Post by Sonsum on 2010-06-29
> **aleperno said:**
> Hello mates, I've recently purchased an Asus Eee PC 1201HA, and as usual installed in it Ubuntu 10.04 LTS.
Ive managed it to detect my 1366x768 resolution, Wifi, Bluetooth, Touchpad & Key Features, but theres is yet something I havent managed to run as desired.

-Built-In Microphone is recognized by the system and works, but it sounds very low, and if turn it up, you can hear "static or rain" and its pretty annoying.

-Built-In Webcam. aMSN manages to work perfectly with it, however, its the only one. Cheese shows very low FPS. EMESENE and Skype(most important), recognizes the device but doesnt show any image.

Any help will be welcomed, Im quite an Amateur on Ubuntu.
Pardon my English, not my native language.
Cheers.

I think there just aren't the right drivers out there. I have the EXACT same problem with my internal microphone on my Samsung n120 netbook. I even have a custom kernel made specifically for Samsung Netbooks. So I just think the driver isn't out there. An external mic works great though.

And I have the same Skype issue. 

So.... If anybody knows the solution to this, that'd be great! :lolflag:

---

### Post by laket on 2010-07-06
@aleperno

found any solutions yet?
I am stuck with the same problems on the same netbook.
thx

---

### Post by aleperno on 2010-07-06
> **laket said:**
> @aleperno

found any solutions yet?
I am stuck with the same problems on the same netbook.
thx
@laket
By the moment, none.

---

### Post by harmus on 2010-10-14
Same netbook, same problems on Maverick. Sound of the internal mic is so low i have to clap my hands in front of it to hear something like a click (with mic boost fully enabled).

---

### Post by stephen70edwards on 2011-01-22
For Ubuntu on my Asus EEE 1201HAB (smaller drive version of the 1201HA), the magic words for getting the internal mic to work (e.g., with Skype) were

sudo apt-get install pavucontrol

pavucontrol

Under "Input Devices,"
Unlock the two channels
Set "Front Left" to 100% (the internal mic?)
Set "Front Right" to 0% (the external mic?)

In Skype, make sure under audio preferences you uncheck "allow Skype to adjust my mixer levels"

---

