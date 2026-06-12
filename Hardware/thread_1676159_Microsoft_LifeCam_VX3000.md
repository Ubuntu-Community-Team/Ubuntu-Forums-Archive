---
title: "Microsoft LifeCam VX3000"
date: 2011-01-26
forum: Hardware
---

### Post by oldtraveler on 2011-01-26
There is a thread in the x86 64-bit Users section of this forum about getting a Microsoft Life Cam VX3000 to work in Ubuntu.  Posts # 7 and 8 ([http://ubuntuforums.org/showthread.php?t=885795](http://ubuntuforums.org/showthread.php?t=885795)) seem to have an answer.  I would post there, but for some reason I am unable to do so even though I have a 64 bit system.

Following the advice in that thread I was able to get the Spcagui remote control set up.  I can't seem to make it take pictures however nor do I see the light go on in my camera. Am I following a useless track to solving the problem?  Is there a better way to go?

---

### Post by gordintoronto on 2011-01-26
The most recent post in that thread is 14 months old. There have been two releases of Ubuntu since then. I'm pretty sure that's why you can't post there. What version of Ubuntu are you using?

If you run lsusb, you will find what the camera really is. Then, I suggest this site:
[http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html)

What program are you trying for pictures? Cheese is the simple one most people use to test webcams.

---

### Post by oldtraveler on 2011-01-27
I am using Ubuntu 10.10

According to [http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html) the correct driver for my Microsoft LifeCam VX 300 is gspcav1.  That site doesn't tell me where to get that driver, however. Do you know?

I'm not sure what Cheese is or if I have it.

---

### Post by gordintoronto on 2011-01-27
At [http://mxhaard.free.fr/download.html](http://mxhaard.free.fr/download.html)

"for kernel up from 2.6.11 : gspcav1-20071224.tar.gz"

Ubuntu 10.10 is way past 2.6.11.

Run Administration/Synaptic Package Manager. Use "search" not "quick search". Find and install build-essential. (You tell it you want to install something, then you click "apply" to actually do the installation.) Find and install Cheese.

Find the downloaded file, double-click it and select "extract" Then you have to start Accessories/Terminal

Use ls and cd to get to the folder where the stuff got extracted. Note that in Linux, Downloads and downloads are two completely different folders.

Once you are there:
make
sudo make install

The easiest thing at this point: Reboot to load the new modules. Run Sounds & Video/Cheese to confirm that it works.

---

### Post by oldtraveler on 2011-01-28
> **gordintoronto said:**
> 
The easiest thing at this point: Reboot to load the new modules. Run Sounds & Video/Cheese to confirm that it works.

Ok.  Cheeese works, but the video is very jerky and of poor quality and there is no audio.

Now even cheese says "no device found".

---

