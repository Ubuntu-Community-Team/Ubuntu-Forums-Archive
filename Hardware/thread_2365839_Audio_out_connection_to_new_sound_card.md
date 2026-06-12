---
title: "Audio out connection to new sound card"
date: 2017-07-11
forum: Hardware
---

### Post by angel mike on 2017-07-11
Have installed a Asus Xonar DG 5.1 sound card into Compag Presario SR1920 PC. Card recognized by Pulse Audio Vol and in-built card disabled in BIOS. OS Ubuntu 16.04.2
No sound - so do I need to plug a connection into the card ? Thanks

---

### Post by efflandt on 2017-07-11
You very likely need to plug either headphones or powered speaker system into the added soundcard if you disabled internal sound. In Sound Settings look at which Output devices are available.

---

### Post by angel mike on 2017-07-11
My question was meant to be about the internal connections - ie I assume there should be no need for other connection other than the 9pin plug for front panel audio. I wonder whether it could be the logitech R20 PC speakers that used to work with  Windows but not Ubuntu using the integrated sound card.

---

### Post by Yellow Pasque on 2017-07-12
Once again, give the alsa info: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)
IIRC, I had to select the output manually in alsamixer on my Xonar DG:
```
alsamixer
```

---

### Post by angel mike on 2017-07-12
Thanks Temujin for replies and link which I have already tried but will have another look. I have a Gateway PC of similar age and sound works fine with Ubuntu out of the box. I think HP machines are not that adapterable

---

### Post by Yellow Pasque on 2017-07-12
Sigh... the alsa info link means you're supposed to give us your info. Since you've put in a new soundcard, you need to do it again. It does not fix or "try" anything.

> I have a Gateway PC of similar age and sound works fine with Ubuntu out of the box. I think HP machines are not that adapterable

That makes no sense whatsoever.

---

### Post by angel mike on 2017-07-12
Sorry about that - the info link is [http://www.alsa-project.org/db/?f=256580b39545dae5dba62d095de4042ff8cefee8](http://www.alsa-project.org/db/?f=256580b39545dae5dba62d095de4042ff8cefee8)

Thanks for your patience Mike

---

### Post by angel mike on 2017-07-12
Just realized I sent my dell laptop info by mistake. Here's the link for the Compaq  [http://www.alsa-project.org/db/?f=aaa7a39ce90100ea0bd66bfd13e12c0aeb8e8cad](http://www.alsa-project.org/db/?f=aaa7a39ce90100ea0bd66bfd13e12c0aeb8e8cad).

Sorry again and hope your still with me. Mike

---

### Post by Yellow Pasque on 2017-07-12
I believe this is the setting you need to change in alsamixer. It looks like the card is currently set to output to the Front Panel (FP):
```
Simple mixer control 'Analog Output',0
  Capabilities: penum
  Items: 'Stereo Headphones' 'Stereo Headphones FP' 'Multichannel'
  Item0: 'Stereo Headphones FP'
```

---

### Post by angel mike on 2017-07-13
Brilliant Temujin - I changed a few settings in Alsamixer using the Terminal and I now have sound from the speakers plugged into the Xonar card port.
 I have to say I have no idea what I was doing in Alsamixer but it worked !
Thanks that has made my day. Will mark as solved.
Mike

---

