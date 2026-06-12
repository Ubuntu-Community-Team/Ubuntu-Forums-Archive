---
title: "Ubuntu on GeForce 6100 / nForce 430"
date: 2007-07-28
forum: Hardware &amp; Laptops
---

### Post by chiros on 2007-07-28
Hi

I'm thinking of building a new system to install the Ubuntu server distro on, based on a dual core Athlon 64 and a Gigabyte mobo as follows:

AMD Athlon 64 X2 4400+
Gigabyte mobo GA-M61PM-S2 that according to the gigabyte site has:
   * NVIDIA® GeForce 6100 / nForce 430 chipset
   * Super I/O chip: ITE IT8716
   * Integrated Peripherals:
         1. T.I. IEEE1394 controller
         2. Realtek RTL8211 Gigabit Ethernet controller
         3. Realtek ALC883 Audio Codec

I will use SATA II/NCQ disks in a RAID configuration and will mainly use it as a LAMP server

I can see in the various forums here that quite a few people have had challenges in installing Ubuntu on similar systems; it appears that I would need to compile in a new kernel to support video and network

Question: would anyone here be able to confirm this? Any other challenges that I should expect?

Thanks!
Peter

---

### Post by shadov on 2007-08-12
chiros, have you found out anything? I'm considering buying ASRock ALiveNF6G-DVI motherboard, witch has also GeForce 6100 / nForce 430 chipset, but if Ubuntu doesn't support it out of the box I'll probably get something else.

---

### Post by daveshields on 2007-08-21
Chiros,

I just finished building a system with the ECS GeForce6100SM-M (1.0) Socket AM2 NVIDIA GeForce 6100S Micro ATX AMD Motherboard (this is how it is listed on newegg.com). This has a builtin GEForce 6100 video chipset.  I was able to install 7.04 desktop without any problems, except that the maximum video resolution was only 1024x768, whilst my monitor wanted 1280x1024.

I tried a live Suse CD and found the chipset did support that higher resolution. I then did a search on "ubuntu video card nvidia 6100 resolution" and was led to [https://answers.launchpad.net/ubuntu/+question/10156](https://answers.launchpad.net/ubuntu/+question/10156) . It suggested deleting one of the X11 configuration files. I tried that, and it worked.

Note that before doing this I had installed the nvidia "restricted" binary driver, bit it did not help.

I'll be writing more about this system soon on my blog. I wanted a cheap AMD Socket AM2 system just to learn more about Ubuntu. It cost under $200 for the case, power supply, motherboard and processor chip with fan. I didn't buy a disk as I had an old one around but a good 250 GB disk can be had for $50 or so.

I didn't buy a display as I had one around. With disk my system would have cost about $250. The comparable Dell system with a display card and 160GB hard disk costs under $400. So though one can save by building a system from scratch, you are perhaps saving only a third or so of the cost (ignoring that a homebuilt system probably has better components and  is also both fun and instructional to put together).

Ten years ago the hardware in a  basic desktop cost well over $2000 and Windows cost about $100 or so. Since then the cost of the hardware has gone down by a factor of ten whilst the cost of Windows has stayed about the same, and  more likely gone up if you factor in the cost of Office. These trends are promising for Ubuntu, though much work remains to be done.

---

### Post by daveshields on 2007-08-21
I did post a new entry about Ubuntu on my blog, though not the one promised about building my new Ubuntu box (I'll do that soon). See [http://daveshields.wordpress.com/2007/08/21/ubuntu-is-a-hill-of-beans-that-is-worth-much-more-than-a-hill-of-beans/]("http://daveshields.wordpress.com/2007/08/21/ubuntu-is-a-hill-of-beans-that-is-worth-much-more-than-a-hill-of-beans/")

---

### Post by tseliot on 2007-08-21
> **chiros said:**
> I can see in the various forums here that quite a few people have had challenges in installing Ubuntu on similar systems; it appears that I would need to compile in a new kernel to support video and network
I don't know about the network support, however I don't think you would have to recompile your kernel in order to get your graphic card to work.

---

### Post by daveshields on 2007-08-22
To follow up on my previous post, I think some insight on why deleting a configuration for X11 solves this  problem can be found in my report on my experiences using the D-Link USB KVM-Switch DKVM-20 with Ubuntu 7.04 that can be found at [http://daveshields.wordpress.com/2007/08/21/using-the-d-link-usb-kvm-switch-dkvm-20-with-ubuntu-704/]("http://daveshields.wordpress.com/2007/08/21/using-the-d-link-usb-kvm-switch-dkvm-20-with-ubuntu-704/")

---

### Post by elmagno on 2007-08-22
I've recently built 4 or 5 machines on the 6100 thru 7050 nvidia chipsets, all Biostar boards. Everything is A+ on them all, with, I am now suspecting, one exception: the onboard Realtek NIC gives very slow transfers-- 200KBs/1000KBs.

Otherwise, Feisty picks up everything. The Envy script installs the Nvidia binary driver quite well for me.

---

### Post by daveshields on 2007-09-10
I just posted a longer article on my experiences building a computer to run Ubuntu using this chip set.

It worked like a charm when I first powered it on and has been rock-solid ever since.

See [Building your own Linux Ubuntu computer using the ECS GeForce 6100SM-M motherboard]("http://daveshields.wordpress.com/2007/09/10/building-your-own-linux-ubuntu-computer-using-the-ecs-geforce-6100sm-m-motherboard/")

---

### Post by koshari on 2008-05-22
hi dave, 

would you care to say how the framerate using glxgears is, and what nvidia drivers you installed, 

cheers

---

