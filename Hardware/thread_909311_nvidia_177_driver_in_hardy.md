---
title: "nvidia 177 driver in hardy?"
date: 2008-09-03
forum: Hardware
---

### Post by bro on 2008-09-03
Does anybody know if the latest nvidia drivers are coming to hardy? From envyng I now get 173 while they are testing with 177 in Intrepid. 
n

---

### Post by Bucky Ball on 2008-09-03
Try going to System->Administration->Hardware Drivers. Deselect the nvidia driver in there (or select if it is unticked).

If you deselected, select again and it should download the new nvidia drivers.

If it doesn't, open a terminal and copy and paste this in:

**sudo apt-get install nvidia-new-glx**

See if that works for you. :)

---

### Post by bro on 2008-09-03
I'm not so sure that is a wise thing to do. I am using nvidia drivers now (173.xx) but do not have this box ticked in hardware drivers. The reason is I have envyng installed which downloads and installs the latest drivers for me (because Ubuntu's thickbox does not do this). 
So the question is: are the latest 177.xx nvidia drivers going to be added for hardy **via envyng**?

---

### Post by Bucky Ball on 2008-09-03
Don't think you can use them both together, no. But I would have thought that if the latest drivers are installed for you, this would have been ticked (no expert though). Try:

locate nvidia-glx-new

In a terminal and see if it is there. Maybe you are getting some kind of conflict.

You may want to post in Video/multimedia forum for more specific info from heads that are closer to the pulse on this topic.

EnvyNG is the right version, though, for 8.04. Here is the page and details from the creator:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

You can easily find the proposed changes and apps for Intrepid from a google search. Cheers :)

---

### Post by Duranxl on 2008-10-13
> **bro said:**
> 
So the question is: are the latest 177.xx nvidia drivers going to be added for hardy **via envyng**?

I'd like to know this too
I've never had any luck installing nvidia drivers outside of EnvyNG

---

### Post by billfromhk on 2008-10-27
I am actually trying this on Intrepid 8.10 Release Candidate.

I tried to install the latest nvidia driver for my acer aspire 4530 laptop. It failed to get the lock for some reasons. Here's the log from the terminal.

```
billh@billaspire:~$ sudo apt-get nvidia-glx-173
[sudo] password for billh: 
E: Invalid operation nvidia-glx-173
billh@billaspire:~$ sudo apt-get install nvidia-glx-173
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  dkms fakeroot nvidia-173-kernel-source nvidia-settings patch
Suggested packages:
  diff-doc
The following NEW packages will be installed:
  dkms fakeroot nvidia-173-kernel-source nvidia-glx-173 nvidia-settings patch
0 upgraded, 6 newly installed, 0 to remove and 0 not upgraded.
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory
billh@billaspire:~$ 

```

In addition, I tried the System -> Administration -> Hardware Drivers to install the new nVidia driver. Both the nVidia drivers version 173 and 177 showed up on a list for Activation. But clicking the activation will bring to a downloading bar that is always 0%.

Any ideas where can I get the nVidia driver?

---

### Post by bro on 2008-10-28
I had the same in Intrepid (download didn't really work) but it worked when I tried again / maybe I rebooted in between. Or installed updates first.. Dunno (sorry 'bout that) but fool around and it will work with automatic driver installer.

---

