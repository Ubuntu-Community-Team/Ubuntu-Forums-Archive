---
title: "Advice on installing a driver"
date: 2008-08-15
forum: General Help
---

### Post by onetiger on 2008-08-15
Hi. I'm new to Linux and have recently installed Ubuntu. I've been lucky enough to find a Linux driver called gspcav1-20071224.tar.gz for my ancient web cam which I've been unable to use since upgrading my XP to sp2. I really would appreciate some help installing this driver. The first part of the instructions are as follows :-       

*************************************************************************
The driver module can be built without modifying your kernel source tree.

Before trying to compile the driver, ensure that you've configured your
kernel, and updated the dependencies:
 make [config|menuconfig|xconfig]; make dep

Make sure, when compiling the driver, you use the same version of compiler as was used to compile your kernel. Not doing so can create incompatible binaries.

as root
goes to gspcav1 directory and run:
./gspca_build
*************************************************************************



The way I interpret those instructions, you have to go to Accessories, open a Terminal and type in "make [config|menuconfig|xconfig]; make dep" (without quotes) and that will configure my kernel and update the dependencies.  Well it doesn't work, I didn't think it would, and I'm not sure my kernel needs configuring anyway. It was only installed a couple of days ago and it's been working fine.

Secondly, how can I ensure that I use the same version of compiler as was used to compile my kernel?

Lastly, regarding the "as root
goes to gspcav1 directory and run:
./gspca_build"
I take it to mean I have to change to the root directory, browse to the gspcav1 directory and then type ./gspca_build.  Am I right?



Any advice would be gratefully received. I know how to use Add/Remove and Synaptic but this driver isn't in either.

---

### Post by Stemp on 2008-08-15
What version of Ubuntu are you using ? Because the gspca drivers are included in Ubuntu.
What Webcam is it ? 
Try this command in a Terminal to look at the USB devices.
```
lsusb
```

---

### Post by Nepherte on 2008-08-15
The tools you'll need to compile is bundled in the package 'build-essential', so install that first:
```
sudo apt-get install build-essential
```

Afterwards they tell you to navigate to the directory where you have unpacked your archive file and run this:
```
sudo ./gspca_build
```

---

### Post by onetiger on 2008-08-15
Thanks Stemp and Nepherte for your replies.

I had the info all ready to reply to you but thanks to Stemp's remark about Ubuntu having the gspca drivers I've just done another search in Synaptic, found the driver and installed it.  I'm baffled why I couldn't find it before - probably because I never expected in a million years it would be there, so I didn't look properly.

Viewquest never updated the driver past Windows 98 so when I first installed XP I managed to find an unofficial driver on the internet, written by some kind person, and it worked until I updated to SP2. I just didn't expect there'd be a Linux driver, a currently available one at that. I think this highlights the difference between the Linux community and the Windows profiteers.

Thanks again.

---

