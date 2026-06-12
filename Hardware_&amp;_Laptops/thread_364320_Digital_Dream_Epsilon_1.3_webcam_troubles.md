---
title: "Digital Dream Epsilon 1.3 webcam troubles"
date: 2007-02-18
forum: Hardware &amp; Laptops
---

### Post by jamyskis on 2007-02-18
Hi everyone,

I seem to have a schizophrenic setup as far as my webcam is concerned...No matter what I do, I cannot get my Digital Dream Epsilon 1.3 webcam (a Jenoptik 1.3 digital camera which is doubling as a webcam). Ekiga works fine with it, and xawtv at least acknowledges that it's there, even though I only get a black picture from xawtv -nodga -device /dev/video0. Camorama (the software I really want to use) just sits there and claims it couldn't connect to /dev/video0, although no other programs have this problem.

lspci shows up the camera OK...

```

Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 06a3:ff0d Saitek PLC 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 0733:1311 ViewQuest Technologies, Inc. Digital Dream Epsilon 1.3
Bus 001 Device 001: ID 0000:0000 

```

I've installed the spca5xx drivers, which has had little effect except on Camorama (beforehand it would show a heavily corrupted image and say there was a problem fetching images from the camera before bombing out, now it just doesn't work at all) I've tried changing the permissions of the /dev/video0 device which has not helped, and the same problem occurs with camorama if I attempt to run it as root (I wouldn't usually, but this was just to check if it was a permissions problem)

Can anyone help with this? Thanks!

J

---

### Post by jamyskis on 2007-02-18
Right - progress:

I've managed to get xawtv to run using xawtv -nodga showing my image by creating the group "video" and adding myself to it. I have a feeling that this program is buggy as it originally shows a black and white image from my cam and I have to select any video format (PAL, NTSC, SECAM or AUTO) before it shows it in colour. I also can't record a video to Microsoft AVI format for whatever reason. Anyway, it works - sort of.

No such luck with Camorama yet though. Would appreciate any help. Thanks!

---

### Post by jamyskis on 2007-02-27
Anyone?

---

