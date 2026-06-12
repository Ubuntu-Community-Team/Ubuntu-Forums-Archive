---
title: "How can I install picam V2.1 on Ubuntu Server 22.04?"
date: 2024-03-23
forum: Hardware
---

### Post by elpidiovaldez5 on 2024-03-23
I have a rpi4b with Ubuntu Server 22.04 installed from the image on Raspberry Pi site (I need Ubuntu 22.04 in order to use ROS2/Humble).

I cannot find any clear explanation of how to use the official picam V2.1.  There is information spread over hundreds of threads and discussions.  What I have
found is contradictory or unclear.  For example there are references to 'config.txt' which do not make clear if they refer to /boot/config.txt or
/boot/firmware/config.txt.  Sometimes it is unclear if the information relates to RPi OS or Ubuntu.  Some sources suggest using start_x=1 in config.txt,
wheras others say that is completely wrong.  There are 'legacy drivers' and also libcamera based
drivers.  There is libcamera from binaries, and various other versions for building from source.  I could go on, but what is the point - it's a nightmare!

Some people do appear to have made the camera work.  Please can somebody who has actually succeeded write a definitive recipe for how to do it, starting from 
the Ubuntu Server 22.04 image.  This will benefit a huge amount of people trying to do robotics on rpi platform.

---

### Post by him610 on 2024-03-24
Back when Rpi first came available, I found a very good howto on the internet somewhere. It gave very good instructions as to how to get the camera working. 
I seem to have misplaced that particular link. I will continue to search for it. If/when I find it I will post it.
Meanwhile, you might visit the the Raspberry Pi forum, [https://forums.raspberrypi.com/viewforum.php?f=66]("https://forums.raspberrypi.com/viewforum.php?f=66") to see if there is anything of interest there.

---

