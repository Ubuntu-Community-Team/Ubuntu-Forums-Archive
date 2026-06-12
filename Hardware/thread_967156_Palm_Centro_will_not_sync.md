---
title: "Palm Centro will not sync"
date: 2008-11-01
forum: Hardware
---

### Post by Luther11 on 2008-11-01
I got my Palm Centro in May, and it worked perfectly with 8.04. Now, I've done a clean install of 8.10, and it won't sync at all. I've followed 2 sets of instructions on Ubuntu Documentation, and nothing works. I can see the Palm in lsusb, but I can't see what device file it's on. Looking in /dev, I don't have any pilot or ttyUSB* devices.](*,)

And on top of that, I haven't been able to get any phone signal today, so I might have to replace the phone.:frown:

Any help would be greatly appreciated.

---

### Post by DaysInn on 2008-11-02
Same problem here to with a number of palm devices. There has been a bug report made and you are not the only one. Here is the link to the bug report. [https://bugs.launchpad.net/ubuntu/+source/gnome-pilot/+bug/280876]("https://bugs.launchpad.net/ubuntu/+source/gnome-pilot/+bug/280876")

---

### Post by Luther11 on 2008-11-02
Thank you. Now I'm not alone in my misery.8-[ I posted the above technical details in a comment on the bug report.

---

### Post by plain_jim on 2008-11-07
If it was a fresh install, you may not have pilot-link installed. It was installed by default in Hardy, but NOT in my Ibex install. The one you get from Synaptic works.

Then, look at this page:

[http://kaybyrd.com/?p=56](http://kaybyrd.com/?p=56)

I use jpilot (also available from Synaptic Package Manager). I found that if I did the stuff on that page under "JPilot" and "Automatic Modprobe Visor", jpilot did fine (you have to start the sync at the handheld first, then click the jpilot sync icon). On my Hardy install, I also got Evolution to sync, but I had duplicate-entry weirdness, so I went back to jpilot. The only thing I wish jpilot had is datebook categories.

Anyway, make sure pilot-link is installed, and then do the stuff on the kaybyrd page. (My "serial port" under the jpilot file/preferences/settings is /dev/ttyUSB1, but YMMV.)

---

### Post by meanburrito920 on 2008-11-10
I am having the same problem with my Palm T3. I was able to sync fine in 8.04 after modprobing visor and usbserial. Now on 8.10 I can see in the system logs that my palm is visible on /dev/ttyUSB1 but pilot-link isn't seeing it for some reason...

---

### Post by meanburrito920 on 2008-11-10
The issue seems to be resolved.

---

### Post by Ivo Moelans on 2008-11-11
The issue indeed seems resolved. My Treo 650 syncs perfectly with JPilot. (I have to start the sync at the Treo first, then click the JPilot sync icon, although JPilot says the contrary)

---

