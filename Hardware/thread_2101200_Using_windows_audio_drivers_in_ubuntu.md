---
title: "Using windows audio drivers in ubuntu?"
date: 2013-01-04
forum: Hardware
---

### Post by mrphud on 2013-01-04
Hi all,

I have recently read that it is possible to use windows drivers in ubuntu to help hardware run properly. What I am reading is that ndiswrapper and ndisgtk allow the .inf file to be used in linux. There is a video of this working fine for a wireless adapter and just the .inf file, but would this work for an audio card? I would think that an audio card would be more complex.

Now to the more specific question. My hardware is a hercules game theater xp and I was able to extract the .exe driver file using wine. I noticed that there is indeed a .inf file, but there is also a slew of other files that look important. I can add the files if necessary (since they are not proprietary). Any suggestions?

---

### Post by Mark Phelps on 2013-01-04
Sorry but (1) Wine can NOT be used to install Windows drivers, and (2) what you read was the ONE instance (networking drivers) in which Windows drivers can be used in Linux.  You must have Linux drivers for everything else.

---

### Post by mrphud on 2013-01-05
This is what I figured. I know wine cannot install, but what it did was open the .exe file that had the .inf, .oso, etc. files in it. Thanks for the reply.

---

### Post by Yellow Pasque on 2013-01-05
You should elaborate on what's wrong with your sound and provide information: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by mrphud on 2013-01-13
> **Temüjin said:**
> You should elaborate on what's wrong with your sound and provide information: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

[http://ubuntuforums.org/showthread.php?t=1529236](http://ubuntuforums.org/showthread.php?t=1529236) and [http://ubuntuforums.org/showthread.php?t=1516293](http://ubuntuforums.org/showthread.php?t=1516293) are previous threads where I have tried to address this. It has to do with the CS46xx driver.

---

