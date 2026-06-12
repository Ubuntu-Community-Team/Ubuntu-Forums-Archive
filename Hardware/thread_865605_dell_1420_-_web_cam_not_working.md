---
title: "dell 1420 - web cam not working"
date: 2008-07-20
forum: Hardware
---

### Post by Boodah on 2008-07-20
Hi 
I have a Dell 1420 (vista version) laptop that I just wiped down and then installed Dells 7.04 iso on. Lots of headaches but most are resolved. I'm now trying to get the Web Cam working and any help would be appreciated

lsusb:
Bus 007 Device 002: ID 05a9:2640 OmniVision Technologies, Inc. 
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000
  
I checked and my user is added to video:

sudo adduser <user> video
The user `<user>' is already a member of `video'.

I'm a relative noobie and this has me stumped.

---

### Post by loell on 2008-07-20
the webcam is suppose to be detected , what sort of application have you tried to view your webcam?

---

### Post by Boodah on 2008-07-21
Hi Loell
I tried to test with Ekiga but it failed to detect both mic and webcam.

---

### Post by loell on 2008-07-21
install and run **xawtv** and see if you can see images.

---

### Post by Boodah on 2008-07-23
Hi Loell

I installed xawtv as suggested. When I run it from the menu nothing happens. When I run from a command line I get the following:

[FONT="Fixedsys"]This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.20-17-generic)
can't open /dev/video0: No such file or directory
v4l-conf had some trouble, trying to continue anyway
v4l2: open /dev/video0: No such file or directory
v4l2: open /dev/video0: No such file or directory
v4l: open /dev/video0: No such file or directory
no video grabber device available
[/FONT]

Thanks in advance for your help.

---

### Post by Boodah on 2008-08-05
<bump>

Does anyone have any suggestions on what i do next?

---

