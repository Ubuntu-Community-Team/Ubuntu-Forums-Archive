---
title: "Diagnosing potential hardware failure"
date: 2015-01-13
forum: Hardware
---

### Post by dpilot83 on 2015-01-13
Back in November of 2010 I had a local computer repair shop to build a desktop for me because I was busy and didn't have time to re-educate myself on what the best hardware was, etc. I provided some requirements for them (had to be able to easily handle two monitors and had to be within a certain budget) and then pretty much let them pick the hardware. To save a little money and to get things partitioned the way I wanted it, I decided to provide the Windows 7 license and install Windows on the machine.

What I ended up with was:

Antec Three Hundred Black Steel ATX Mid Tower Computer Case
Antec EarthWatts 650 Power Supply
MSI P55-CD53 motherboard (It's an IntelP55 Express board, 1156 socket)
Intel Core i5-750 2.66 GHz Processor
320 GB Seagate SATA2 7200 RPM 16MB hard drive
(2) 2GB 1600 MHz Kingston HyperX XMP 240-Pin DDR3 PC312800 SDRAM
MSI Gefoece GT 240 Graphics Card
Samsung 22x DVD R DVD Burner with LightScribe
Rosewill 802.11 b/g PCI Wireless Card

This computer has always been odd from day one. This was 4 years ago but I remember either when I installed Windows 7 or when I was installing drivers I experienced a BSOD. I stumbled through the rest of setting it up after that rather than spending any time trying to diagnose what happened. As we used the machine we would get some BSOD's occasionally but we just lived with it as it was not a machine we used a lot.

It got to the point where we used other devices far more than this one and eventually (a few days ago) I turned it on and it had to do a bunch of Windows updates because it had been sitting so long. After the Windows updates it would not boot into Windows.

My solution was going to be to create a Linux LiveCD, use it to go in and back up data that I want to keep and then update the BIOS, install Windows 7 and try updated drivers to see if things worked better.

As I have been working on the the Linux LiveCD has frozen several times. I have never had that happen before. So I thought perhaps I had a hardware problem and RAM seemed like the first place to start to me so I ran Memtest86+ overnight (21 passes I believe) and there were no errors.

Now I've switched from using the Ubuntu LiveCD to using a Live USB with persistance. I have installed lm-sensor as well as Psensor and am monitoring CPU temperatures. So far the Max temp is 35C. I'm considering doing a stress test. I was also wondering, if the LiveUSB freezes, is there someplace I can get an error log the next time I boot to get a better idea of what's going on or do I need to have Ubuntu actually installed on the hard drive to be able to get error logs?

Any thoughts on how I should go about diagnosing all of this would be very much appreciated. Thanks.

I installed pi and then ran 6 instances of pi specifying that it calculate out to 20,000,000 decimals. This caused the temperature to get as high as 99 degrees C while I was running the test but it never froze or had any other problems. 99C seems pretty hot though.

As I was creating the last post pi was still finishing up in several terminals but the cpu usage was down to maybe 30 percent and the temperature had dropped way down to perhaps 50C or less by that time. As soon as I hit post on the previous post, I moved back over to the desktop causing problems and tried to move my mouse and could not. The mouse and keyboard are unresponsive.

The mouse and keyboard are both wireless Microsoft input devices controlled by the same USB receiver. Surely it's not just receiver going haywire...

No, it's not just the receiver. I am using Psensor to display the output of lm-sensor and the graph quit moving. cpu usage is stuck at 10% and the timeline is not continuing to move so it truly did freeze. Also, I tried plugging a wired keyboard in to see if it would respond to that and it did not.

It seems like I should have experienced a failure while the temperature was high rather than low. When it froze it locked basically was providing a snapshot of temperatures at the time it froze because psensor is still visible on one of my monitors. Here is what it's saying right now which is what the temps would have been when it froze:

temp 1 28C
core 0 40C
core 1 40C
core 2 40C
core 3 40C

Max of temp1 was 28C
Max of all the cores was between 96C and 99C.

This happened while I was using the Linux off a USB drive. If I force it down by holding the power button and then boot back up is there someway I can get a log of what happened? It is set up for persistance so I don't know what all I can do with it. Thanks.

---

