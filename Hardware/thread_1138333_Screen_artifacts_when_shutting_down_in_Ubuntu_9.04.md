---
title: "Screen artifacts when shutting down in Ubuntu 9.04 with nVidia restricted drivers"
date: 2009-04-26
forum: Hardware
---

### Post by GeoMX on 2009-04-26
I've installed Ubuntu 9.04 64 bits on my XPS M1330 laptop (this Dell model have some known issues with the nVidia graphics processor).

I have this problem: when rebooting or shutting down, the screen would show some vertical lines, similar to the ones tha appeared when my system started having issues with the nVidia graphics chip sometime ago (sorry I didn't take a picture, I'll try to get one). The lines appear when the system is just about to finish rebooting or shutting down.

I notice these video artifacts after enabling the nVidia restricted driver, they don't appear when it's disabled.

Thanks in advance for your help.

---

### Post by ugriffin on 2009-04-26
What version is your driver?

---

### Post by GeoMX on 2009-04-26
I tried the nvidia-glx-180 package.
Thinking about it, I'll try a previous version, I didn't have any issues with Ubuntu 8.10 and the previous nvidia package (173, if I'm correct). Also, this is the first time I'm trying the 64 bit version.

---------
Update:

Just tried nvidia-glx-173, same issues. Disabled them and no problem :confused:. I'd like to find out whether it's a driver issue (some bugs or problems with the 64 bit version) or some sympthoms of the [nVidia issues]("http://en.community.dell.com/blogs/direct2dell/archive/2008/09/12/nvidia-gpu-update-limited-warranty-enhancement-details.aspx") appearing again (last time I had the motherboard replaced since the nVidia chip is soldered to it) :(.
Guess no "fancy effects" nor graphics intensive applications (I'm planning on doing some OpenGL programs) while I can find it out.

Any information/advice will be appreciated, thanks.

---

### Post by supersonictt on 2009-04-28
> **GeoMX said:**
> I tried the nvidia-glx-180 package.
Thinking about it, I'll try a previous version, I didn't have any issues with Ubuntu 8.10 and the previous nvidia package (173, if I'm correct). Also, this is the first time I'm trying the 64 bit version.

---------
Update:

Just tried nvidia-glx-173, same issues. Disabled them and no problem :confused:. I'd like to find out whether it's a driver issue (some bugs or problems with the 64 bit version) or some sympthoms of the [nVidia issues]("http://en.community.dell.com/blogs/direct2dell/archive/2008/09/12/nvidia-gpu-update-limited-warranty-enhancement-details.aspx") appearing again (last time I had the motherboard replaced since the nVidia chip is soldered to it) :(.
Guess no "fancy effects" nor graphics intensive applications (I'm planning on doing some OpenGL programs) while I can find it out.

Any information/advice will be appreciated, thanks.



Hey everybody... I have the same problem, ubuntu 9.04 64bit, i tried 3 drivers for nvidia, 173, 180.44 and 180.51 (the later is downloaded from nvidia website) and the problem presists...
And yes this problem wasn't there in ubuntu 8.10...

Any updates will be given here :)

Thanks.

---

### Post by atlas95 on 2009-04-28
It is just a heat problem...nothing to do... same with my m1330 with 8400gs, motherboard allready change 4 times. Nothing to do, Nvidia 8400gs is a f**cking graphic cheap with heat problem.
:)

---

### Post by GeoMX on 2009-05-01
I know the nVidia chip suffers from overheating
But, in this case, why the artifacts appear only when using the nVidia restricted drivers? That's what annoys me, does it mean using these drivers will damage my system? Or can I safely use them?

---

### Post by pattuxio on 2009-05-05
Same problem here on a Dell M1330. When using the NVidia drivers I also get artifacts when shutting down or rebooting 9.04 64-bit.
Nice detail is that my motherboard has been replaced yesterday because of artifacts first only appearing in Linux (on reboot) and when time progressed in the last two weeks they also showed up during normal work and in Windows sessions (games). Did not see the relation between 9.04 and the artifacts earlier. Just thought it was the well known heat problem. Maybe it is, but 9.04 is causing (accelerating) it in my case. Switching to Windows running heavy graphic dependend games doesn't cause artifacts with my new motherboard anymore. Switching back to Ubuntu (and rebooting from Ubuntu) makes them appear again. Switching to the "free" non-Nvidia drivers fixes the heat problem.
 
A warning: Ubuntu 9.04 with the NVidia drivers can kill your M1330. When you see artifacts, quickly turn off your notebook. It can fry your hardware. The M1330 has proven to be crappy hardware.
 
Anyone with the same experiences on 32-bit?

---

### Post by GeoMX on 2009-05-15
I've been avoiding using Ubuntu with the nVidia restricted drivers for now, I'll try the 32 bit version when possible and update here.

We are all running the 64 bit version, guess the 32 bit version does not suffer of this?

---

### Post by TomGier on 2009-05-15
> **GeoMX said:**
> We are all running the 64 bit version, guess the 32 bit version does not suffer of this?

Sorry but 32 bit Jaunty also suffers from this. I'm using the 173.14.16 driver from the Ubuntu repos and I have the same issue when shutting down or rebooting my 32 bit Jaunty.

---

### Post by GeoMX on 2009-05-15
> **TomGier said:**
> Sorry but 32 bit Jaunty also suffers from this. I'm using the 173.14.16 driver from the Ubuntu repos and I have the same issue when shutting down or rebooting my 32 bit Jaunty.

I've just confirmed this, the 32 bit version has the same problem :(.

---

### Post by NESFreak on 2009-05-16
It happened to me for a short time. But only when shutting down. Instead of turning off, i'd get all vertical psychedelically coloured stripes. It never happened on intrepid to me, and for some reason it only happened five times, all in the same week. For some reason now everything works fine again.

---

### Post by GeoMX on 2009-05-19
Could you give some more details? What driver version are you using, Ubuntu 32 or 64 bit?

---

### Post by GeoMX on 2009-06-22
Are there any news on the subject? Thanks for any information :).

---

### Post by stenliq on 2009-07-16
No news, I can only confirm it on ThinkPad R61 with Nvidia Quadro NVS 140M. Does it look like this too in your case?

[http://img83.imageshack.us/img83/9625/dsc00529.jpg](http://img83.imageshack.us/img83/9625/dsc00529.jpg)
[http://img259.imageshack.us/img259/5975/dsc00530q.jpg](http://img259.imageshack.us/img259/5975/dsc00530q.jpg)

It's really annoying. It happens with all nVidia drivers. I can download it from repository or Nvidia webpage. Result is the same - messy screen.

Let's hope it won't be in 9.10. But bug in Launchpad is marked for expiration without solution :(

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/377120](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/377120)

---

### Post by stenliq on 2009-07-16
Bad news, everyone...
I've just installed Karmic Alpha2 and artifacts are still there :(

---

### Post by GeoMX on 2009-07-27
> **stenliq said:**
> Does it look like this too in your case?

[http://img83.imageshack.us/img83/9625/dsc00529.jpg](http://img83.imageshack.us/img83/9625/dsc00529.jpg)
[http://img259.imageshack.us/img259/5975/dsc00530q.jpg](http://img259.imageshack.us/img259/5975/dsc00530q.jpg)

Not exactly, I used to get some vertical colored lines, but every now and then I get a kind of gray screen that slowly turns to white :confused:, I'd try to get a camera and take a picture.

> **stenliq said:**
> Bad news, everyone...
I've just installed Karmic Alpha2 and artifacts are still there :(
:(, I hope someone gets the time to work on this.

---

### Post by GeoMX on 2009-09-15
I switched back to Ubuntu 8.04, I'll wait for the 10.04 release to update. If you try 9.10, please let me know if it is fixed :).

---

