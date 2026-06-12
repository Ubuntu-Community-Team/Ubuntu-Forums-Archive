---
title: "NVidia GeForce4 440MX"
date: 2005-03-21
forum: Hardware &amp; Laptops
---

### Post by mnaah on 2005-03-21
I just downloaded Kubuntu hoary preview - and I'm very impressed - after trying several, I think I've found one to settle down with after the final release.

I'm aware that this isn't the greatest graphics card in the world, but I've been getting a problem with the screen on the high resolutions (up to 1280x1024).  Basically, there are small random flashing horizontal lines on my screen.

Is this just a case of me need in the nvidia drivers (which I won't get until I install in a few weeks) or something else?

---

### Post by artinla on 2005-03-21
I am only guessing, but that sure sounds like the card is either bad or being clocked higher than it should be.  

I don't know of any way to change the clock speed in Linux like you can in Windows.

The new driver may be the answer.  There is a good howto on this site.

Art

---

### Post by jery_wang2002 on 2005-03-22
My card is NVidia GeForce4 440MX too.

And it has exactly the problem you have (random short horizontal line flickering across screen). But the difference is that the resolution was set 1600x1200

It is fine when I set 1280x1024

It is definitely NOT card problem. My card was alright all the time even at 1600x1200 when I was using fedora core 3 until I convert to ubuntu yesterday.

I guess the problem is something unique in Ubuntu.

Btw, I use the driver from NVidia web site 6629 and the latest on the website when I  use fedora core 3 and it has no problem.

---

### Post by mnaah on 2005-03-22
yeah, my display has been fine with SUSE 9.2, Knoppix 3.6 and SimplyMEPIS 3.3test03.....thanks for the info...

---

### Post by dizzie on 2005-03-22
$ sudo apt-get install nvidia-glx
$ sudo apt-get install nvidia-settings
$ sudo nvidia-glx-config enable

Sorted ;-)

My GF 440 works well doing this :)

No harm done, if it f*cks up the xorg.conf, there is a backup (does that when installing the driver)

Good luck, glx is nice :)

---

