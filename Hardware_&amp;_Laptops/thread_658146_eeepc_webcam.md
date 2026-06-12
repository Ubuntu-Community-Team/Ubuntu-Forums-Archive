---
title: "eeepc webcam"
date: 2008-01-04
forum: Hardware &amp; Laptops
---

### Post by mor22 on 2008-01-04
I've recently installed eeexubuntu on a flash drive on my eeepc.  Has anyone got the webcam to work?  There is something to do with turning the webcam on in the bios, does anyone know if this can be done with a kernel module like in xandros?  

i've read that having the webcam turned on put more load on the battery so I'd obviously only wnt to turn it on the when needed.

Any ideas much appreciated.

---

### Post by kyphi on 2008-01-05
> ...does anyone know if this can be done with a kernel module like in xandros?
Since the webcam worked perfectly well with the standard Xandros installation, it must be something that is configurable in Xubuntu.

I suggest putting the Xandros installation back and doing some research before jumping off the deep end.

---

### Post by sirobert on 2008-01-08
the place to start is to hit f2 while booting, then go to the advanced page, down to onboard devices and then enable the camera. The software used by xandros is ucview.

S

---

### Post by sirobert on 2008-01-08
just to continue, you can add a repository for all the UCView stuff at [http://www.unicap-imaging.org/download.htm](http://www.unicap-imaging.org/download.htm)
S

---

### Post by miatawnt2b on 2008-05-07
> **sirobert said:**
> just to continue, you can add a repository for all the UCView stuff at [http://www.unicap-imaging.org/download.htm](http://www.unicap-imaging.org/download.htm)
S

I added the repository for hardy of the unicap software, but when I Synaptic search for ucview or unicap, I don't get any packages.  Am I searching the wrong package name?  I am looking for a package for the unicap gtk tools.

-J

---

### Post by ggravier on 2008-06-14
The problem is NOT the applications.

It's the driver for the camera.

Many applications in Ubuntu can directly display V4L2 video streams. Skype, Ekiga... to name a few.

The problem is that under Ubuntu, the webcam doesn't have a driver... and as such, isn't seen as a USB-VC V4L2 device.

What is needed is the official driver.

Unfortunately, I wiped my Xandros distro to put Ubuntu on it. Couldn't stand OOo v2.0.4 and Skype 2.0beta... too old stuff.

---

