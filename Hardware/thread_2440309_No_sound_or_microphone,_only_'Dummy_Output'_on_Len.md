---
title: "No sound or microphone, only 'Dummy Output' on Lenovo Yoga Chromebook C630"
date: 2020-04-08
forum: Hardware
---

### Post by mrjohnc on 2020-04-08
Hi all

I've just installed Ubuntu 19.04 on my Lenovo Yoga Chromebook C630 and it works great apart from a few issues (which I've managed to fix apart from sound and microphone), here's the specs for it [https://www.lenovo.com/gb/en/laptops/yoga/yoga-c-series/Yoga-Chromebook/p/88YGCC61096](https://www.lenovo.com/gb/en/laptops/yoga/yoga-c-series/Yoga-Chromebook/p/88YGCC61096)

Basically it can't see the sound card, only 'dummy input' and can't see any microphone at all, any ideas? I'm not sure how to proceed, the only proprietary driver it says I can install is one for the Boradcom wifi...

All clues greatly appreciated

---

### Post by CelticWarrior on 2020-04-08
19.04 is out of support since January. Why did you install that release when there's 19.10 already and 20.04 LTS in a matter of days?

---

### Post by mrjohnc on 2020-04-12
This was the option that was available in the installer, I updated to 20.04 but this didn't fix the problems I'm having

---

### Post by CelticWarrior on 2020-04-12
Was it working in the 20.04 live session?

---

### Post by mrjohnc on 2020-04-12
No, wasn't working at any point, it all works fine in Chrome OS so definitely isn't a hardware issue.

What is a good method to find and install the correct drivers? I guess something like:

1. Find some kind of spec sheet for the laptop which describes the chipset for audio
2. Find out which additional things need to be installed on the laptop to make the audio and microphone work
3. Ask somewhere for it to be supported as default in future versions of Ubuntu

Is there something written that would help guide me through a process?

---

### Post by mrjohnc on 2020-04-12
So far I found a user manual and a hardware service manual but neither seem to be helpful 

[https://download.lenovo.com/consumer/mobiles_pub/yoga-chromebook-c630_ug_en_201809.pdf](https://download.lenovo.com/consumer/mobiles_pub/yoga-chromebook-c630_ug_en_201809.pdf)

[https://download.lenovo.com/consumer/mobiles_pub/yoga-chromebook-c630_hmm_201809.pdf](https://download.lenovo.com/consumer/mobiles_pub/yoga-chromebook-c630_hmm_201809.pdf)

---

### Post by CelticWarrior on 2020-04-12
It should be listed with 'lspci'.

---

### Post by mrjohnc on 2020-04-12
Thanks very much, running in ChromeOS gives me 

00:00.0 Host bridge: Intel Corporation 440FX - 82441FX PMC [Natoma]
00:01.0 Unassigned class [ffff]: Red Hat, Inc Virtio block device
00:02.0 Unassigned class [ffff]: Red Hat, Inc Virtio block device
00:03.0 Unassigned class [ffff]: Red Hat, Inc Device 105b
00:04.0 Unassigned class [ffff]: Red Hat, Inc Virtio RNG
00:05.0 Unassigned class [ffff]: Red Hat, Inc Virtio memory balloon
00:06.0 Unassigned class [ffff]: Red Hat, Inc Virtio network device
00:07.0 Unassigned class [ffff]: Red Hat, Inc Device 105e
00:08.0 Unassigned class [ffff]: Red Hat, Inc Virtio GPU
00:09.0 Unassigned class [ffff]: Red Hat, Inc Device 1053
00:0a.0 Audio device: Intel Corporation 82801AA AC'97 Audio Controller
00:0b.0 USB controller: Fresco Logic FL1000G USB 3.0 Host Controller

I assume 'Intel Corporation 82801AA AC'97 Audio Controller'?

If this is correct how do I find and install the correct driver for it?

---

### Post by CelticWarrior on 2020-04-12
I'm no expert but yes, 'Intel Corporation 82801AA AC'97 Audio Controller' should be it. And I'm baffled about something with AC'97 in its name not being supported out-of-the-box. Google didn't find anything specific.

---

### Post by mrjohnc on 2020-04-12
Yeah, its weird, I'm not sure what to do from here, any suggestions? 

I looked at Gallium OS which is based on Ubuntu but specifically for Chromebooks and it has the same issue [https://github.com/GalliumOS/galliumos-distro/issues/400](https://github.com/GalliumOS/galliumos-distro/issues/400)

---

### Post by mrjohnc on 2020-04-12
Found an Intel data sheet about the chip, leaving it here for future reference if needed [http://pdf.datasheetcatalog.com/datasheets/2300/45366_DS.pdf](http://pdf.datasheetcatalog.com/datasheets/2300/45366_DS.pdf)

---

### Post by CelticWarrior on 2020-04-12
Sorry, I have no suggestions.

---

### Post by mrjohnc on 2020-04-12
So I found an Ubuntu manual page which mentions the chipset and appears to be a driver, not sure what to do with it though, how would I install it?

[https://manpages.ubuntu.com/manpages/xenial/man4/ichsmb.4freebsd.html](https://manpages.ubuntu.com/manpages/xenial/man4/ichsmb.4freebsd.html)

---

### Post by CelticWarrior on 2020-04-12
That driver or similar is already included and it's for the SMBus, not audio.

---

### Post by mrjohnc on 2020-04-12
Damn, I thought I had something...

---

### Post by Mcdowellmountains on 2020-05-25
This may solve your problem.  I have my pixebook which I converted from chrome os to ubuntu using the following guide and process.  It allows sound through the speakers as well as through headphones on chromebooks.  It takes some time to install (about 30-40 min.) but is worth the time.  

[https://github.com/yusefnapora/pixelbook-linux](https://github.com/yusefnapora/pixelbook-linux)

---

