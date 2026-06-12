---
title: "x31 Audio Problem"
date: 2007-06-19
forum: Hardware &amp; Laptops
---

### Post by wedge2k on 2007-06-19
I have an odd one here.  For the longest time my audio worked perfectly in all flavors of (k)ubuntu, but lately something odd has happened.  The modules are still loading, the system believes that sound is coming out of my speakers, yet none does.  I've checked and made sure nothing's muted or what not.  Then one day I was testing some audio and hit the my hardware volume buttons and i could hear the music for a fraction of a second.  So i keep trying and sure enough its like theres something blocking the audio until the sound of the "beep" when i change the volume comes out do i hear anything.  

Any thoughts?  
```
wedge@mini-wedge:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 4: Intel ICH - IEC958 [Intel 82801DB-ICH4 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Need any info just let me know.

---

### Post by ykanello on 2007-06-21
Hi I have a Toshiba Satellite to install Ubuntu for a friend and I run into the same issue!!! 
I have the same card:
 ```
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 4: Intel ICH - IEC958 [Intel 82801DB-ICH4 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

Everything seems peachy, but there is no sound, nor the headphones which I tried as well. 
From some other post I was directed to a link I can't find yet, I will update if it works, or not just for reference, that i need to add this to 
```
echo  "options snd-intel8x0 ac97_quirk=2">> /etc/modprobe.d/alsa-base 
```

This is not my laptop and I have to return it soon, so I prolly stay late trying to fix it, updating this post.

Ok, I searched the forums again, and I found the post. It was saying to play around with Alsa mixer unmuting things (?) and read 'this' and the this was the link:
[https://wiki.ubuntu.com/HardwareSupportComponentsSoundCardsIntel]("http://https://wiki.ubuntu.com/HardwareSupportComponentsSoundCardsIntel")
I did what it says, but I have 6.10 installed. So I am upgrading as I edited the previous post. 
I will upgrade reboot (new kernel) and home all goes well.

---

### Post by ykanello on 2007-06-22
I had no luck what so ever. 
I read a lot of articles, but no luck. Everything seems to be in order, except that there is absolutely no sound coming out.
I have attached the out of lspci, and lsmod.
But there is no problem there. 
The card is recognized, and there is not a single error message anywhere....
Good morning anyways :)

---

### Post by ykanello on 2007-06-25
I had no luch with ubuntu. I installed openSuse 10.2, and the sound worked as expected.
I need to return the laptop so I will leave it with opensuse :(

---

