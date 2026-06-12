---
title: "Advice Needed: Xandros to Ubuntu EEE 8.04"
date: 2008-09-04
forum: Hardware
---

### Post by Bridge51 on 2008-09-04
Hi all! I have a new EEE PC 901 running linux, Xandros. I want to update to Hardy Heron. 

I've heard the best way to do this is to download the Ubuntu EEE 8.04 ISO from [www.ubuntu-eee.com](www.ubuntu-eee.com) 's website, and just install that via flash drive/usb.

Is this the best option for getting Ubuntu on my computer? I've heard installing Ubuntu can cause wireless problems, shutdown problems, FN key problems, etc. Does the EEE version take care of this, or is there a better way? Heck, the EEE version might not even be best for EEE! 

Thanks in advance for any help you can provide. I'm brand new to Linux, with the exception of looking at the liveCD prior to my eee pc getting here. I'll check back often, so feel free to ask for any specs or whatever! Thanks!

---

### Post by lechroom on 2008-09-04
If you have two 4GB external storage devices at hand (two USB keys, or a key and some SD card), you may want to install Ubuntu-EEE directly on the key/SD, instead of erasing the Xandros partitions on the SSD. That's what I did at first, because of the same concerns as yours.

Only one caveat in this case: suspend won't work in this case (because of some option in the stock kernel that prevents USB devices to automount after waking the eee from its suspend state). Of course, when installed on the SSD, Ubuntu goes to suspend mode without any problems.

Shutdown must be fixed with the current (8.04) version of Ubuntu-eee. It's a matter of 5 seconds using a terminal, but there's also an all-in-one tweaking script that does the job for you.

---

### Post by Bridge51 on 2008-09-04
Gotcha. Are there any wireless problems with Ubuntu-EEE? I don't mind fixing the shutdown thing. Not having internet is another problem though

---

### Post by Menschenfresser on 2008-09-04
Yes, the default ubuntu and eee-ubuntu won't be able to connect neither to wifi nor through a cable. You can either follow the instructions on the eee-ubuntu wiki to get all the drivers installed or (what I did myself and would strongly suggest to others) is to install the customized kernels from here:

[http://array.org/ubuntu/](http://array.org/ubuntu/)

After that, everything else works like a charm. Just don't forget to turn on the webcam in the BIOS and to uncomment the line regarding cdrom in fstab or it won't let you mount usb sticks.

I hope that helps

---

### Post by Bridge51 on 2008-09-04
> **Menschenfresser said:**
> Yes, the default ubuntu and eee-ubuntu won't be able to connect neither to wifi nor through a cable. You can either follow the instructions on the eee-ubuntu wiki to get all the drivers installed or (what I did myself and would strongly suggest to others) is to install the customized kernels from here:

[http://array.org/ubuntu/](http://array.org/ubuntu/)


That worked perfectly. I'm currently at work, so I can't test the wireless, but before when I went into manual connections, it just said the point to point, now it shows wired and wireless as well. You da best :-)

---

### Post by parsim on 2008-09-13
> **Bridge51 said:**
> Hi all! I have a new EEE PC 901 running linux, Xandros. I want to update to Hardy Heron. 

I've heard the best way to do this is to download the Ubuntu EEE 8.04 ISO from [www.ubuntu-eee.com](www.ubuntu-eee.com) 's website, and just install that via flash drive/usb.

Is this the best option for getting Ubuntu on my computer? I've heard installing Ubuntu can cause wireless problems, shutdown problems, FN key problems, etc. Does the EEE version take care of this, or is there a better way?

I installed Ubuntu EEE 8.04.1 on my 901 yesterday, and it was brilliant. Easy install and pretty much everything worked immediately, including wireless.

I don't believe there's any need to mess around with customized kernels & fixes any more, because Ubuntu EEE 8.04.1 takes care of all that for you.

---

### Post by linhlh on 2008-10-25
Sorry to bump this. I just got linux eee yesterday so I have a question.
  If I install Ubuntu EEE directly on the USB, that means I have to plug USB in whenever I want to boot and use Ubuntu ? If I don't, then it will use the default Xandros ?

---

### Post by solitude123 on 2008-10-25
I have my Motorola Rokr e6. Supports fully linux operating system. I installed ubuntu eee version. Now its speed is much faster and playing many types of media.

---

### Post by CapnChkn on 2008-10-25
I have installed HH LTS on my Eee PC 701 and it works great!  The main problem I have right now is space.  This is a 4 Gb SSD, and the install without other software uses 75% of the drive.

The install doesn't allow the Antheros drivers to work, so using the ethernet port and cable is a must.  I then went to [https://launchpad.net/niceeepc]("https://launchpad.net/niceeepc") and ran the Niceeepc script for download there.  I've run it several ways, I had to install again several times as my drive filled up and borked the modified OS, and it always seems to work.  This install I decided to use the standard kernel.

I've installed all the "optimized for the Eee PC" distro's of Linux, and this is the only one (Though it's the desktop/standard installation. The script then optimized it.) that actually works, runs WINE, Truecrypt, and Synergy all at the same time, and connects to the Wi-Fi using the packaged chipset.

At least for me...

---

### Post by surfed on 2008-10-25
> **linhlh said:**
> Sorry to bump this. I just got linux eee yesterday so I have a question.
  If I install Ubuntu EEE directly on the USB, that means I have to plug USB in whenever I want to boot and use Ubuntu ? If I don't, then it will use the default Xandros ?

No. Installing Ubu-eee will install it to your hard drive, boot from it etc.

---

### Post by cynon83 on 2008-10-27
> **parsim said:**
> I installed Ubuntu EEE 8.04.1 on my 901 yesterday, and it was brilliant. Easy install and pretty much everything worked immediately, including wireless.

I don't believe there's any need to mess around with customized kernels & fixes any more, because Ubuntu EEE 8.04.1 takes care of all that for you.

Since I just got my 901 today, I'd love to know what you did, or where you got your info on how to do it from...

---

### Post by surfed on 2008-10-27
wireless does NOT work with intrepid on the eee1000 series

---

