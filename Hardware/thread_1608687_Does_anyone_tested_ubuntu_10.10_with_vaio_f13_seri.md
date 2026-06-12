---
title: "Does anyone tested ubuntu 10.10 with vaio f13 series ?"
date: 2010-10-29
forum: Hardware
---

### Post by HMD69 on 2010-10-29
Hi all,
I want to buy a vaio f13.But I have heard vaio laptops may be incompatible with ubuntu.
Does anyone tested f13 series of vaio with ubuntu 10.10?

Thanks in advance....

---

### Post by hoogland on 2010-11-09
I am running Ubuntu 10.10 on a VAIO F13 series notebook. You have to ensure that you use the NVIDIA 256.53 drivers otherwise you will get a black screen. You can check out: 

[http://code.google.com/p/vaio-f11-linux/](http://code.google.com/p/vaio-f11-linux/)

for help with some setup issues.

Wireless and bluetooth work w/o problems.

---

### Post by HMD69 on 2010-11-11
> **hoogland said:**
> I am running Ubuntu 10.10 on a VAIO F13 series notebook. You have to ensure that you use the NVIDIA 256.53 drivers otherwise you will get a black screen. You can check out: 

[http://code.google.com/p/vaio-f11-linux/](http://code.google.com/p/vaio-f11-linux/)

for help with some setup issues.

Wireless and bluetooth work w/o problems.
Thank you,
What is model of your vaio?
When does black screen appear?If it is shown all the time how do I install nvidia driver?;)

---

### Post by hoogland on 2010-11-21
Sony Vaio F13Z1E/BI.

After login install 256.53 drivers. Do not install the NVIDIA updates until the next NVIDIA driver release (after 260.19.21)which is reported to fix the black screen issue.

---

### Post by gpremer on 2010-11-22
Hi, I've played around with various 260.19.xx drivers and I indeed can't get them to work.

Unfortunately, I don't know where to find the 256.53 drivers as ubuntu deb's. It seems all package repositories either have 260.19 or 195.36.

Do you know where I can find the proper ones for my new Vaio VPC F13?

Thx
Geert

Edit:
I found the version of nvidia-settings I looking for at [https://launchpad.net/ubuntu/maverick/amd64/nvidia-settings/256.53-0ubuntu1](https://launchpad.net/ubuntu/maverick/amd64/nvidia-settings/256.53-0ubuntu1). This version works fine.

---

### Post by jorgemc on 2010-11-27
Just got it a few days ago, brand new vpcf13c5e. I did a CD install of UBUNTU 10.10 (amd64) Maverick Meerkat (USB did not work at all) and I have been having the same problems with nvidia drivers. Only 256.53 work for me. Not even the latest 260.19.21.
I really have not made much testing here with everything, but this is what I have been able to see so far:
Right now Ethernet, Wifi and Bluetooth seem to be working perfectly.
Touchpad not really and neither do the special keys ASSIST S1 VAIO. In the other hand, music control buttons and Display Off do work fine.
Sound is ok and as stated before video hw acceleration works with drivers 256.53.
CD/DVD works fine (didnt get bluray), also eSATA is ok.
Havent tried card readers yet so I will try to get you posted.
All 4 cores and the two threads per core seem to be detected alright (CPU0 - CPU7).
Well, I hope this helps someone. I will try to keep you posted if I find out anything else.
:)

---

### Post by batseb on 2010-12-20
Hello, I am about to buy a Vaio F13X5E to primarily use it under ubuntu and I wanted to know if you experience other issues with this laptop:
-does the nvidia driver works ok ?
-what about trackpad, speakers and microphone ?
-is the fan noisy ? is it easy to reduce the noise when just working on a text editor without any performance requirement ?


thanks a lot for you answers !!

---

### Post by tcdb on 2011-01-15
Hi batseb,

I picked up a F13 yesterday to be used mainly as a work (Ubuntu 10.10) machine and for occasion StarCraft (Win7).

Ubuntu seemed to install fine until I did the restricted nvidia drivers update and got the blank screen problem listed above. After wasting a heap of time reading various solutions, I tried the latest nvidia drivers and installed as per nvidia's instructions - works fine now.

Other problems noticed so far:
*No built in microphone, possible solution listed at [http://code.google.com/p/vaio-f11-linux/](http://code.google.com/p/vaio-f11-linux/) but I have yet to try it. This would be nice to get going when I find time.
*No trackpad. Not to big a deal for me, given the size of this machine, it is more a desktop replacement and I can not see myself sitting with this brick on my lap using the trackpad.
*Screen brightness worked after following steps on the above vaio-f11-linux page.

Other non problems:
*No problems with speakers.
*Fan is always on, but quiet with low CPU. Playing SC in Win7 resulted in a very busy/loud fan, but still acceptable given the load put on the machine.

---

