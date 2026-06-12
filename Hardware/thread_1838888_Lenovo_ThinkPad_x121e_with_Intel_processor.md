---
title: "Lenovo ThinkPad x121e with Intel processor"
date: 2011-09-04
forum: Hardware
---

### Post by paolonicolai on 2011-09-04
Hi, has anyone tried ubuntu on the new Lenovo ThinkPad x121e with Intel processor?

Look like plenty of people had tried the AMD e350 version, but I would like to know what works and what doesn't on the Intel.  Both are for sale here in the UK, and I can't decide which one to go for.

Anyone have a list of what works and what doesn't?  In particular, do the desktop effects work (compiz?) on the Intel GMA video card? What about drivers?

Thanks.

---

### Post by martinyt on 2011-09-14
Had some difficulties with the installation, but using the alternative iso it worked fine. The wireless was not working correct but that was easily fixed (google it), but there is a problem with the touch pad, which I will post a question about now. There is a fix, I just don't understand how....

But, by all means, it is a great laptop - fast and quiet.

---

### Post by prahari on 2011-12-11
I received mine 4 days ago, with the Intel Core i3-2367M. I tried first Ubuntu 11.10 from a live USB and everything worked out of the box. 

However the version I really wanted to install is 10.04.03 LTS and it took more time to get everything working. There is a lot of help in various forums though. Basically, you need to upgrade to the kernel 3.0 to get the ethernet and sound working, then install the latest graphics driver for the Intel graphics card. 

The process I followed is the following:
- Download the latest version 10.04.03 from Ubuntu web site, create a bootable USB key and reboot,

- First choose the test option and connect to a wireless network,

- During the installation, I fully erased the disk and created my own partitioning,

- Before finishing the installation, run Synaptics and install the backport kernel packages:
linux-image-generic-lts-backport-oneiric
linux-headers-generic-lts-backport-oneiric

- Add the following in Software sources to load the latest Intel graphics drivers:
deb [http://ppa.launchpad.net/glasen/intel-driver/ubuntu](http://ppa.launchpad.net/glasen/intel-driver/ubuntu) lucid main

then:
sudo apt-get update
suto apt-get upgrade

- After the laptop has rebooted, the kernel version will now be 3.0.0.x and I was able to adjust the screen resolution to the maximum (1366x768 ). I did nothing special for the sound, microphone or webcam, they worked straight away. 

Battery life approximately 4.5 - 5 hours.

All in one, I am very happy with this little machine and it is really fast compared to my previous Dell.

---

### Post by elizabeth_b on 2012-02-13
Thanks for that description prahari, good and clear and I should be able to cope fine!  I'm getting mine in "3-6 days" :)

One quick question -- presumably you mean the 64 bit version throughout?  
[]("http://ubuntuforums.org/member.php?u=162174")

---

