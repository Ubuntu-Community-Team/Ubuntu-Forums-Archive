---
title: "Building a Computer - Looking for Advice"
date: 2011-06-13
forum: Hardware
---

### Post by Dan Again on 2011-06-13
I am planning on building a computer with my brother's help, but am looking for advice from others who might have experience.

I plan on building this computer to replace an existing laptop that I keep hooked up to my television. I use it to view media stored on my hard drive and also for net surfing, including viewing streaming videos from YouTube, etc.

I would like the new computer to be able to perform the tasks mentioned above so that I can free my laptop back up and I am also looking for more hard disk space and hopefully some enhanced features. Here's a list of some of the things I am looking for...
[LIST]
[*]HDMI out
[*]Large hard disk (I'm thinking 2T)
[*]Wifi compatible
[*]The ability to record HDTV to my hard disk (not an extremely high priority for me, but definitely a preference if it is not too challenging or expensive)
[*]The other features mentioned above - accessing media from my hard disk (primarily music and HD video) and net surfing with the capability to stream HD video
[*]Remote control capability
[/LIST]
Thanks in advance for your help!

---

### Post by ratcheer on 2011-06-13
I just bought a pre-built custom computer and, once I got all the kinks worked out, I am quite happy with it. I read lots of reviews and stuff before I made my selection. It seems that Intel Sandy Bridge based systems are the top performers, right now, as well as ATI video systems.

My system has a Gigabyte Z68A motherboard, which supports SATA III and USB 3. I got a 1 TB Seagate SATA III hard drive. You should probably go for two 1 TB drives in a RAID 0 configuration instead of a single 2 TB drive, because video file processing really puts a load on the disk system. I chose an Intel Core i5 at 3.3 gHz, you might want to get an i7.

What were my problems? Two that are worth mentioning. First, I had a lot of trouble installing Ubuntu because the CD/DVD drive was plugged into a SATA III port. Windows 7 worked fine with it, but no Linux distro would mount it (Ubuntu, Fedora, even Parted Live). It was finally fixed by opening the case and moving the DVD drive cable to a SATA II port. Second, Ubuntu decided to choose the wrong driver for the onboard NIC. I had to locate the correct driver from Taiwan, make a new module, blacklist the old module, and force initramfs to load the new module. Now it is working perfectly.

Good luck. It is almost overwhelming with the huge variety of available components, but that is also part of why it is so much fun.

Tim

---

### Post by Dan Again on 2011-06-13
Thanks, Tim! I understand very little of what you've written, but I'm sure it will be very useful once my brother helps me decipher it (he has much experience with this than I do).

---

### Post by ratcheer on 2011-06-13
Sorry, one never knows to whom one is talking until there is a little back-and-forth.

I was mainly just saying that for video file handling and processing, you may want to make sure you get the latest high performance features. Without spending an arm and a leg, of course.

Tim

---

### Post by Yellow Pasque on 2011-06-13
It sounds like you want a Mythbuntu setup. The mythtv wiki will help a lot, but start here: [http://www.mythbuntu.org/](http://www.mythbuntu.org/)

---

### Post by Dan Again on 2011-06-14
No need to apologize, Tim - I was just explaining why I didn't have much to say in response to your reply. Your input was well received and I really appreciate you taking the time to share your experiences and offer some advice.

Temüjin, that looks VERY interesting and like a total match with what I'm looking for. Thank you!

---

### Post by CaptainMark on 2011-06-14
when i built my current setup from scratch i was almost dissapointed with how easily it all just worked, ive never had a single problem with it, and i built it with not cutting edge but very good spec (at the time) for £300, superb value. id advise a nvidia gpu, asus and amd on the mobo/cpu combo. corsiar memory, pnasonic hdd, alfa usb wireless adapter, 
and ive never had a single driver issue in 3 years

---

### Post by Dan Again on 2011-06-17
So will I be able to record HD TV that I receive through my cable box? Also, does a Mythbuntu set up allow me to use programs like Banshee or is it strictly for PVR stuff?

---

