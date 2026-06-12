---
title: "Sound Blaster Audigy SE in 9.10"
date: 2009-11-26
forum: Hardware
---

### Post by Largaroth on 2009-11-26
Hi all, I've been experiencing some problems with my sound card in Ubuntu 9.10 (it worked just fine in Linux mint 7 which uses Jaunty as a base unless I am mistaken).

```
lspci -v | grep audio
```

returns
```
03:02.0 Multimedia audio controller: Creative Labs CA0106 Soundblaster
```

So I know it recognizes my card... But try as I might, it will not play sound.

When I run
```
alsamixer
```
(AlsaMixer v1.0.20)

It tells me the card and chip are "CA0106", so no problems there, and I have maxed all the levels and unmuted everything.

Any suggestions ?

---

### Post by kostkon on 2009-11-26
Try disabling or enabling (depending on your setup) the *Analog/Digital* switch in alsamixer.

---

### Post by coldsystem on 2009-11-26
> **kostkon said:**
> Try disabling or enabling (depending on your setup) the *Analog/Digital* switch in alsamixer.


try  The  opensound system driver  : 
[http://unixmen.com/linux-tutorials/documentations-a-howto/524-ac97-audio-controller](http://unixmen.com/linux-tutorials/documentations-a-howto/524-ac97-audio-controller)

---

### Post by Largaroth on 2009-11-26
I don't know if it was the Digital/Analog switch (IEC958) but it worked, even though sound didn't work with it switched off yesterday... But I had tried several tweeks since deactivating it, so I guess one of them must have worked.

Thanks a lot Kostkon, I appreciate it =)

---

### Post by absentspace on 2009-12-20
I have the same card and was having similar problems, 

Check the output settings on the card. 

Mine was originally set to stereo, and I know it can be set to off.

Go to:
System > Preferences > Sound 
Click the Hardware Tab. 
Check the Profile Dropdown menu for the output you want.

---

### Post by aj1140 on 2009-12-22
I am having this problem too. What do you mean when you say to enable/disable the analog/digital switch?


Help is greatly appreciated:)

---

