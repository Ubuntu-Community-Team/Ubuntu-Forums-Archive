---
title: "Radeon IGP 345M"
date: 2005-09-15
forum: Hardware &amp; Laptops
---

### Post by Zachs23 on 2005-09-15
Hello all, I have a Radeon IGP 345m on my vaio laptop (2.4 Ghz, 512 ram (shared with video), 40 GB HD) and I wanted to get 3d accel working on ubuntu. I have tried many distro within the past few months, and ubuntu is BY FAR the best. The only thing I can't get is 3d accel. In suse it worked "out of the box" after checkmarked "3D Acceleration" in Sax2 or whatever it is called. 
       From what I have found out from searches, getting this to work might involve recompiling the kernel, etc. I know there are howto's on this forum for compiling a kernel. So I am asking someone knowledgeable about the subject to help me out by giving me a step-by-step (I am a linux newbie, but consider myself to be catching on rather fast) guide to downloading and installing what is necessary.
P.S. Suse detected my card as a Radeon 9000, or something similar. Also, I have tried the Radeon Linux drivers (Fglrx) but they do not work with this card.
Thanks in advance for the help.

---

### Post by mlomker on 2005-09-15
Are you currently using the radeon driver that comes with Hoary?  It should provide 3D in conjunction with mesa but it's not the quickest thing in the world.  I Googled IGP345 and it sounds like the same setup on other distros.

What is the output of this?

```

cat /etc/X11/xorg.conf | grep Driver
glxgears

```

---

### Post by Zachs23 on 2005-09-15
Thanks for the reply. The output of your first command stated that my video driver was "ati". Glxgears shows a dismal 117 average. I know this computer is not a gaing powerhouse, but it should be getting higher than that  :smile: (With 3d acceleration on of course).
Should I switch the drivers? If so, how?
Thanks again

---

### Post by mlomker on 2005-09-16
Try **sudo dpkg-reconfigure xserver-xorg** in a terminal.  I think it'll allow you to select a different driver and the one called 'radeon' might work better. 

My old laptop had an IGP320 and that's the driver that I used.

---

### Post by nivesh on 2007-12-31
I have the same specs on my HP ze5375US , installed gutsy its great ! same problem with 3d acceleration.

---

### Post by Troy Shanahan on 2008-01-31
Hmm, well, I'm using the same card (IGP 345M), and I can't seem to get gutsy to work at all. When I enter the setup (on the live cd) the screen is out of alignment (by about an inch on 1024 x 768 reso), and is 'distorted' for lack of a better word. It's like every second horizontal line of pixels is shifting an inch to the left and then back again. (Really fast, can't read anything the distortion's that bad, hurts your eyes after awhile, too :) )

I'm going back to dapper drake (that worked last time) but I'd like to move up to Gutsy, so if anyone could offer some insight, that'd be great. :)

EDIT: Sorry to hijack the thread a little, just thought I'd throw another issue into the mix, being the same card and all

---

