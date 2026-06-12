---
title: "Acer aspire m5620 webcam driver"
date: 2008-11-24
forum: Hardware
---

### Post by theinfiniteadam on 2008-11-24
I've been trying for a couple of days to get my webcam working on an acer aspire 5100 laptop with 8.10 installed on it. I found the set of drivers from the svn repo on sourceforge, but nothing i've done will make the webcam work. I'm not a noob, but I'm not exactly adept at this sort of thing.

I know I have the right files (560x drivers), because lsusb gives back the correct corresponding device.

Bus 003 Device 002: ID 0402:5602 ALi Corp. Video Camera Controller
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


 When I try to install from the main branch of the drivers, I type

make load
make
sudo make install

None of that returns any errors, and the light on my webcam is now permanently on. When I open up ekiga, however, I get the following message: 

"Error while opening video device /dev/video0
A moving logo will be transmitted during calls. Notice that you can always transmit a given image or the moving logo by choosing "Picture" as video plugin and "MovingLogo" or "StaticPicture" as device.

There was an error while opening the device. Please check your permissions and make sure that the appropriate driver is loaded."



... So, It seems that there is an error somewhere along the line. A similar message is given in camorama, a webcam viewer.


So, to sum things up, acer aspire laptop, webcam driver not working, but the light is on. I've followed all instructional threads on this, and I'm not sure what the problem is. 

Can someone assist me in getting my webcam working?

If you'd like, I'll post the entire terminal text about my install.

---

### Post by sjbaugh on 2008-11-24
Have you seen the webcam issues in:

[http://ubuntuforums.org/showthread.php?t=966436](http://ubuntuforums.org/showthread.php?t=966436)

---

### Post by theinfiniteadam on 2008-11-25
I have, but it isn't what I need. Thank you for your consideration, though.

---

### Post by theinfiniteadam on 2008-11-28
Bump

---

### Post by t4e on 2008-11-28
i have the same problem, someone please help :sad:

---

### Post by theinfiniteadam on 2008-11-30
*BUMP*

Will someone take the time out of their busy schedule and give this thread some thought? I'm at a loss for what to do.

---

