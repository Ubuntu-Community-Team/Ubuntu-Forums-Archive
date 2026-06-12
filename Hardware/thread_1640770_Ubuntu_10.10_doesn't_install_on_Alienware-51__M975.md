---
title: "Ubuntu 10.10 doesn't install on Alienware-51  M9750"
date: 2010-12-08
forum: Hardware
---

### Post by COMTIBoy on 2010-12-08
I have an Alienware M9750 (its a 32 bit machine) which was able to run Ubuntu in the past. Since 10.04 (I think this was the build) and Ubuntu 10.10, it no longer works.  I can't even boot to a Live CD.  Just hangs at the graphic banner that says Ubuntu with a little thinking strobe showing that its doing something.  I know this is very vague but not sure how to go about gathering information.

Anybody else have an Alienware note that used to work with Ubuntu, but now failing with 10.10 ? (and the version just before that). 

Not sure what to do... (sigh )

---

### Post by COMTIBoy on 2010-12-08
when I boot from any Ubuntu 10.10 Live CD, I never get beyond the intial Ubuntu splash screen.  I can hear the typical Ubuntu music when the desktop is presented, but no desktop.  Just the Ubuntu splash screen.  I'm wondering what would have changed ?  I also notice that any new liveCD (Open SUSE 11.3 , etc...) has similar problems.  Windows 7 works like a champ though!...but want Ubuntu 10.10 on this notebook.

---

### Post by yanko87 on 2011-03-29
I have the same exact problem and so far I can only run Ubuntu 10.10 in a virtualBox under windows7....
Well I am disappointed in the Ubuntu(Linux community)..I thought this was the best and the most stable OS out there, but I guess you get what you pay for !!! you buy Windows7 and it works well you get Ubuntu10.10 for free and it does not work!!!! good job!!!!
BTW I think this is a Graphics Driver Problem!!!!
BUT THANKX UBUNTU!!!

---

### Post by d106550 on 2011-03-29
Could you be a little bit more specific as to what actually happens?

---

### Post by COMTIBoy on 2011-04-02
I haven't tried it in a while. I'll give it another whirl again.
Its sitting right next to me. From what I recall, it just hangs at a certain point. No errors, nothing. I'll be back.

---

### Post by COMTIBoy on 2011-04-02
Oh, I see my description is at the top of this email!  Things happen pretty much like it reads. I don't think I left anything out. 

Any tips, log files, anything I can provide...just let me know.  I'm not sure what to gather (or how).

---

### Post by yanko87 on 2011-04-20
I insert the dvd,ubuntu 10.10 and i just tryed with 11.04...
It boots the dvd and you see the back ground of the ubuntu and the dark gray menu bar at the top of the window and there is a power button sound and wifi.  than my built in webcam light  litghts up and stops ritght there nothing after that just idle.... any help???

---

### Post by jokker on 2011-04-22
Same issue with an alienware 9750, it seems to boot and then stops at the desktop loading, I stay with the default wallpaper on screen and the mouse cursor, that's it.
Same problem with Mint 10 and with Debian 6.01 I get a black screen.

Anyone opened a bug ?

---

### Post by jokker on 2011-04-22
Ok guys, I found the trick, in the kernel options before boot simply add nouveau.modeset=0 and the when booted, install the right drivers.

Cheers.

Jokker.

---

### Post by COMTIBoy on 2011-04-25
Cool. I'll give this a try tonight.
Thx

---

### Post by COMTIBoy on 2011-04-30
Thanks. That did the trick.

---

