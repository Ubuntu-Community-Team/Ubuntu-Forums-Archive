---
title: "Does WinTV-HVR-950Q work with analog cable box?"
date: 2009-07-14
forum: Hardware
---

### Post by plb on 2009-07-14
I got the digital portion to work but I have an analog cable box and was wondering if it would work. I have a /dev/video0 entry but tvtime doesn't seem to bring up anything.

---

### Post by markackerman8@gmail.com on 2010-04-09
I would sure like to get it working with analog and mythtv!!!  Has anyone had any success???

and btw it works out of the box with analog and tvtime with this command:

tvtime | arecord -D hw:1,0 -r 32000 -c 2 -f S16_LE | aplay -

but please help with MythTV!!!!!

---

### Post by markackerman8@gmail.com on 2010-04-15
Boy would I ever like to find another program that will have the pvr functionality of MythTV for analog cable tv viewing.

I have a HVR-950Q which works well in TVtime but has serious issues in MythTV. I tried XBMC with TVheadend .. no luck "[WARNING]:v4l: /dev/video1: Device lacks MPEG encoder, device skipped".

Are there any other options out there??

---

