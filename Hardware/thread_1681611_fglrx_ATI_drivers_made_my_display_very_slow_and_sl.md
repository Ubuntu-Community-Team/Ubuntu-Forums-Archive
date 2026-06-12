---
title: "fglrx ATI drivers made my display very slow and sluggish"
date: 2011-02-04
forum: Hardware
---

### Post by narayan.g8 on 2011-02-04
My Acer Aspire Laptop with AMD Athlon x2 64bit processor, and integrated ATI radeon HD 3200, is running Ubuntu 10.10(32 bit). The display has always been slow and sluggish but after I recently installed the proprietary fglrx drivers from:

[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.7&product=2.7.4.3.5.3.1&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.7&product=2.7.4.3.5.3.1&lang=English)

 by just running the binary with root previlages, the display is even worse with huge lags in browser scrolling and window tearing.. I also tried,

aticonfig --initial

The desktop effects are automatically disabled and cannot be enabled and I get the message "Desktop effects couldn't be enabled". Iam not sure if the drivers are even loaded as it feels like the display is being rendered without the graphics card..
 
Please help, this is truly awful.. am I missing something or are ATI drivers and graphics cards really crappy? The previouly  installed drivers seemed to be somewhat better.

---

### Post by shelterit on 2011-04-07
Late reply. I have the same, and my story goes like this ;

Had 10.04 and it worked great, upgraded to 10.10 and it worked even better, but then I downloaded the latest driver from ATI, installed, and everything since has been a nightmare.

The state of ATI drivers on Linux is in a terrible state, and there's several options depending on what model you've got, but the two main ones are ;

-glfx (ATI proprietary driver)
-ati (xorg open-source free driver)

More info on Radeon in general ;
  [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

Sometimes there's a conflict between these two ;
  [https://wiki.ubuntu.com/X/Troublesho...thRadeonDriver](https://wiki.ubuntu.com/X/Troublesho...thRadeonDriver)

Depending on your model, there's also a patched version of the -glfx drivers for improved performance ;
  [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

For some relevant news on the latest ATI official drivers ;
  [http://www.phoronix.com/scan.php?pag...item&px=OTI3MQ](http://www.phoronix.com/scan.php?pag...item&px=OTI3MQ)

Hope some of this info helps you out. Mine went from unusable, to tolerable, to usable, but it's still not as snappy as the first install or the 10.04 install. I'm giving the ATI official driver patch next and see how that goes down, but only got a source link to it, and don't really know how to apply it. I'll snoop around.

---

### Post by misterbiskits on 2011-04-07
Install the driver[ manually]("http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Installing_the_drivers_manually") from a fresh ubuntu install.

This has been the only working solution I have found for installing ATI proprietary drivers.  It has worked for me on three different HD cards where Ubuntu's "activate driver" function has failed miserably.

---

