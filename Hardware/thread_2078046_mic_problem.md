---
title: "mic problem"
date: 2012-10-30
forum: Hardware
---

### Post by khanzz on 2012-10-30
I am a newbie to Linux and just installed ubuntu 12.04 on my Lenovo G480
Everything is working perfectly but mic is not working. I would appreciate any suggestions and instructions.

---

### Post by madinc on 2012-10-30
> **khanzz said:**
> I am a newbie to Linux and just installed ubuntu 12.04 on my Lenovo G480
Everything is working perfectly but mic is not working. I would appreciate any suggestions and instructions.

Did you check the sound settings??

---

### Post by khanzz on 2012-10-30
> **madinc said:**
> Did you check the sound settings??

Yeh sound settings seem fine to me.

---

### Post by madinc on 2012-11-01
> **khanzz said:**
> Yeh sound settings seem fine to me.

Try checking this type in terminal:

```
alsamixer
```

---

### Post by khanzz on 2012-11-01
> **madinc said:**
> Try checking this type in terminal:

```
alsamixer
```

I resolved the issue. Thank you for your time and concern

---

### Post by rjv23 on 2012-11-05
hi, can you share how you fixed this problem.  I have the same mic issue with the g480 and have tired many things - checked most settings, but can't find the problem, tks in advance

---

### Post by rjv23 on 2012-11-06
for anyone with the same problem, after alot of looking this is related to the g480  audio HDA Intel PCH Input Device**.  **I tried this fix: 
  	 	 	 	 	 	   

Add the line: options snd-hda-intel model=auto to /etc/modprobe.d/alsa.conf , then manually select the capture device on the application (Skype).  

also, don't allow skype to control the levels.   use a volume control like Qasmixer or alsamixer to control the input volume.
this worked for me, tks

---

