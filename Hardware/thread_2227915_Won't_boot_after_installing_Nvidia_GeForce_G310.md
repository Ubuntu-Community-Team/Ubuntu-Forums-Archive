---
title: "Won't boot after installing Nvidia GeForce G310"
date: 2014-06-04
forum: Hardware
---

### Post by sydonym on 2014-06-04
I have an old [Compaq Presario SR2011WM]("http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00776474&cc=us&dlc=en&lc=en") that I'm trying to upgrade a little bit. I've had this machine awhile and installed Ubuntu 12.04 almost 2 years ago just messing around trying to learn a little more about computers, I've had no problems with the Linux system but don't use the machine that often; I've got a newer Dell that I use on the regular. Anyway, my nephew needs a computer and I figure if I can get a little more gusto out of this one I'd give it to him. So, I picked an additional 512mb RAM stick and a NVidia GeForce G310 (512mb) GPU off of ebay in a cost effective effort to get a little more horsepower out of this machine. I installed the RAM with no issues and that has seemed to help.

Next I downloaded and installed the driver for the GPU (although, admittedly, I'm not sure if I actually got it installed correctly), shutdown the system, disconnected the PSU, cleaned all the dust out and installed the GPU however the system will not boot, it just stays at the Compaq startup screen and there is no keyboard functionality. I can take the card out and plug back into the MOBO VGA port and everything works fine. I've double checked things a few times making sure the PCI slot is free and clear of dust/debris and still, "Card-In, no worky" - "Card-Out, worky fine"..?

The [NVidia hardware specs]("http://www.geforce.com/hardware/desktop-gpus/geforce-310/specifications") for the card shows 30.5W max power draw and a min 300W PSU requirement. The PSU in the machine shows 12V@19A, 5V@30A & 3.3V@28A with a 300W max output. There are no additional peripherals in the machine, beyond the RAM and GPU, it is bone stock. I'm a mechanical engineer and not a complete knucklehead but I am a novice with Linux so if anyone can give me some dumbed down instructions/advice, I sure would appreciate it.

---

### Post by Yellow Pasque on 2014-06-04
> Next I downloaded and installed the driver for the GPU

That's a red flag right there. Downloading drivers straight from the manufacturer is not ideal for Linux.

What exactly did you do to install the nvidia driver? (You should boot with integrated GPU and undo it.)

---

### Post by sydonym on 2014-06-04
Well to install the driver first I established the ppa repository then used the 'sudo apt-get install NVidia-current' command in the terminal screen. Then I opened up the box and put in the gpu. I followed the steps outlined here: [http://www.techlw.com/2012/03/install-nvidia-drivers-on-ubuntu-1204.html](http://www.techlw.com/2012/03/install-nvidia-drivers-on-ubuntu-1204.html)

---

