---
title: "microcode packages"
date: 2014-06-17
forum: Hardware
---

### Post by P . P . L . on 2014-06-17
Hi.

I've googled a lot trying to find an straight answer to this, is it worth installing either the intel or amd-microcode packages for the respective systems that are in synaptic for both 12.04lts & 14.04lts.

Intel system is a z77 chipset socket 1155 with a i7-2700k in it, so it's not very old. - has 12.04lts x32 installed already.

The other system has 890 AMD chipset am3 socket with a Phenom II X6 & the last BIOS update for it was 2010, so it may be out of date compared to the update in synaptic. - has 14.04lts x64 installed already.

I have red on some sites they say that the kernels have some sort of code in them already for the cpu's and that the microcode is not needed. / confused.

Would the systems work better with the codes installed then without? is it worth it.

---

### Post by lisati on 2014-06-17
The need for processor specific "microcode" (a term which means different things to different people) isn't something that I've seen that often (if at all) on the forum. 

I've run Ubuntu on machines with both AMD and Intel CPUs without the need for any extra microcode or firmware. 

One option is to use the "Try Ubuntu" option from a live CD and see how well it works with your machine before installing.

---

### Post by P . P . L . on 2014-06-18
Hi.

So I did some more digging and found this site [http://packages.ubuntu.com/search?keywords=amd64-microcode]("http://packages.ubuntu.com/search?keywords=amd64-microcode") it says that the linux-firmware that is installed by default is the same as what I was

looking at in synaptic. So there's no point to adding that to the install.

---

### Post by WinEunuchs2Unix on 2014-06-18
I'd like to add that it was recommended to install Intel Microcode for Core 2 Duo T5250 / ICH8 chipset / GM965 motherboard on my Toshiba L300 laptop (from 2007) which I did and it went flawlessly.  I also reinstalled Vista 32 and boot time went from 5 minutes to 35 seconds.  At that time I discovered a 2009 driver from Intel for the XVGA intel adapter that when install blew my mind with the "Clear View" technology that made it look like 20 thousand dollar TV you see in the mall.

While researching ACPI problems I found fan control problems Thinkpad, HP and other users were having under Kernel 3.13 and what surprised to see Intel employees posting code with their e-mail addresses in the patch headers.  I'm very impressed with the way Intel is playing ball with Linux.

---

### Post by Yellow Pasque on 2014-06-19
> **P . P . L . said:**
> it says that the linux-firmware that is installed by default is the same as what I was looking at in synaptic. So there's no point to adding that to the install.

That is for the AMD microcode package (on 13.04 and later).

For the Intel system running 12.04, it would be a good idea to install the intel-microcode package, for the peace of mind of the security fixes if nothing else. The only way I wouldn't install it is if I was doing something that Intel may not approve of (like trying to OC non K-seriec CPU's: [http://techreport.com/news/26650/asus-enables-haswell-overclocking-on-non-z-series-motherboards](http://techreport.com/news/26650/asus-enables-haswell-overclocking-on-non-z-series-motherboards) ).

> I've run Ubuntu on machines with both AMD and Intel CPUs without the need for any extra microcode or firmware. 
True, most of the errata are corner cases. It's not every day that a bug like the Phenom TLB bug is discovered.

---

### Post by P . P . L . on 2014-06-19
> **Temüjin said:**
> That is for the AMD microcode package (on 13.04 and later).

For the Intel system running 12.04, it would be a good idea to install the intel-microcode package, for the peace of mind of the security fixes if nothing else. The only way I wouldn't install it is if I was doing something that Intel may not approve of (like trying to OC non K-seriec CPU's: [http://techreport.com/news/26650/asus-enables-haswell-overclocking-on-non-z-series-motherboards](http://techreport.com/news/26650/asus-enables-haswell-overclocking-on-non-z-series-motherboards) ).


True, most of the errata are corner cases. It's not every day that a bug like the Phenom TLB bug is discovered.

Hi Temüjin.

Your right I didn't look at the intel side of things, my AMD is the one that I'm having some issues with. After looking at the page for intel it seems that they don't include the patchs in the linux-firmware
for some reason, so I'll install the ones from synaptic next reboot and see how it goes. [http://packages.ubuntu.com/search?suite=default&section=all&arch=any&keywords=intel-microcode&searchon=names]("http://packages.ubuntu.com/search?suite=default&section=all&arch=any&keywords=intel-microcode&searchon=names")

thanks.

---

