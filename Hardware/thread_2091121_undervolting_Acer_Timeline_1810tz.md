---
title: "undervolting Acer Timeline 1810tz"
date: 2012-12-04
forum: Hardware
---

### Post by supernater on 2012-12-04
I have a Acer 1810tz that I'm trying to undervolt.  This laptop is already very efficient, but I just want to see how far I can push it.  The thing is... I've never undervolted anything on Linux before so I'm not sure where to start.  Window's has an app called RMclock, but from what I can see Linux only has PHC.  Is this the only thing I can use to undervolt?  I have read that undervolting can be done using the BIOS if it has the correct settings, but the BIOS that comes stock on this laptop does not appear to have these settings.  I am currently running lubuntu 12.04.  Thanks.

---

### Post by 2F4U on 2012-12-04
If the BIOS doesn't have the necessary settings, you can't use it. Here is a Wiki article about the topic:

[https://wiki.ubuntu.com/UndervoltingHowto](https://wiki.ubuntu.com/UndervoltingHowto)

The method described in the link involves either compiling the kernel or at least kernel modules.

---

### Post by supernater on 2012-12-04
Okay I got it working.  I followed the instructions here...

[http://linuxsolver.blogspot.com/2012/05/undervolting-cpu-in-ubuntu-1204.html](http://linuxsolver.blogspot.com/2012/05/undervolting-cpu-in-ubuntu-1204.html)

There were a few bumps along the way.  The first one bing that the phc kernel was never loading.  I added the linux-phc repository, updated, and installed the phc generic kernel and headers; however, when I rebooted the phc kernel didn't load  When I typed uname -r, it kept showing that I was using the generic-pae kernel.  I needed the -phc kernel so I altered the /boot/default/grub file and commented out the GRUB_HIDDEN_TIMEOUT=0 and typed sudo update-grub.  I rebooted and the grub menu came up and I selected other version -> linux-blahblahblah-phc and uname -r showed the the phc kernel loaded.

Another issue was that the Analysis tab on phctool kept showing n/a for all values.  I found that I hadn't loaded the model-specific registers (MSR) module so I typed "sudo modprobe msr", clicked the refresh button in the Analysis tab, and the n/a's were replaced with my CPU's data. 


I opened phctool, went to the voltages tab and saw two tabs, each tab had two columns, 1300MHz and 1200MHz, with the values 21 and 15 for VID respectivily.  I set the VIDs to 0 for both frequencies for both cores and hit save values.  I went to the Analysis tab and hit refresh and, for both processors, the values showed....

target VID: 0
target Vcc: 0.7125V
reached VID: 15
reached Vcc: 0.9000V

So even though I set the target VID to 0, the furthest the motherboard will allow me to go was 15.  There were quite a few posts over at the PHC forum that indicated that this is a hardware limitation that some motherboards have.  I ran the CPU burn program (using burnP6 &) and my kill-a-watt meter showed my laptop drawing 16.6 W of power (fluctuated between 16.4 and 16.9, but usually stayed at 16.6).  I set the VIDs back to their default values and ran the the CPUburn program again and my laptop drew 17.7 W of power (fluctuated between 17.3 and 18.0, but usually stayed at 17.7).  At idle I did not notice a difference in the amount of power drawn between the normal and undervolted CPU.  The power draw always seems to stay in the range of 11.2-12.0 watts.  Maybe there was a slight difference, but if there was it was barely noticable to me.

So...   should anyone else want to try this please realize that the benefits seem minimal at idle.  The only time I saw a major difference was when the CPU was at full load.  I'm thinking that there must be a better way to lower my laptops power consumption.  By just opening powertop and going to tunables and setting everything to "good", I can lower my idle power consumption to 10.2 Watts.

---

