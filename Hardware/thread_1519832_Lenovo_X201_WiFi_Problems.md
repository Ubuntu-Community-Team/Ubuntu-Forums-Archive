---
title: "Lenovo X201 WiFi Problems"
date: 2010-06-28
forum: Hardware
---

### Post by Anton32828 on 2010-06-28
I installed 64-bit 10.4 on my Lenovo X201 yesterday. It is a dual-boot with Windows 7. It installed and runs very well (with none of the black-screen issues documented on other threads). But I have noticed a wierd problem with the wi-fi applet.
 
Observed: Reported wi-fi signal varies between 60% down to 30% as reported by the indicator in the top right panel. Communications are iffy. Web pages load OK, but connections to Ubuntu Software Store and System Updater drop connection or are very slow.
 
Expected: The same laptop running Win7 consistently shows 100% signal level. An HP Mini110 laptop placed in the same location (and running 10.4 32-bit) shows 90% - 100% consistent signal level. 
 
Has anyone else noticed this?

---

### Post by doyleknight on 2010-06-29
What wireless WiFi LAN adapter is installed on your X201 ?

---

### Post by Anton32828 on 2010-06-30
It is more difficult to answer that question than I expected.

Windows 7 reports it is a "Realtek Semiconductor 11b/g/n Wireless LAN Mini PCI Express Adapter II"

The Lenovo website for my specific laptop model reports the card as Lenovo brand P/N 60Y3177

I downloaded a Linux tool called "System Profiler & Benchmarks" from the Ubuntu Software Center. It reports:

Realtek Semiconductor Co. Device 8172 Rev 10
kernel module r8192se_pci

The reported power levels on my connection are still wonky. I noticed the Win 7 driver had advanced settings to control sensitivity and transmitter power --- maybe such settings are  the issue with the linux driver or my specific installation? I don't see a tool within the standard Ubuntu software load to view or change that information.

I hope this helps. Is there a community consensus on the best way to identify hardware without disassembling one's laptop? The "System Profiler" tool looks promising but for all I know that could just be reporting the driver installed by Ubuntu, not the underlying hardware information. 

Thanks,

---

### Post by doyleknight on 2010-06-30
The lenovo website ([www.lenovo.com](www.lenovo.com)) lists the following options for wireless on the X201:

ThinkPad bgn Wireless       
	Intel Centrino Wireless-N 1000 [$0.00]  
	Intel Centrino Advanced-N 6200 (2x2 AGN) [add $20.00]  
	Intel Centrino Ultimate-N 6300 (3x3 AGN) [add $40.00]  
	Intel Centrino Advanced-N + WiMAX 6250 [add $55.00]  

so presumably your wireless is one of the above.  There are posts on Ubuntu Forum for the T410 which indicate that the Intel 6200 doesn't work, but the Intel 6300 works fine.  You might check out that thread.

---

### Post by Anton32828 on 2010-06-30
OK.  It appears my card is truly a Realtek device. The other threads show how to query the HW and driver. I know what the Lenovo build site says --- but this was a "configure to order" PC from my IT department's queue three months ago, so that probably explains the component changes. 

The threads were helpful. In the following thread the user xengorilla finds that although the kernel installs the functional Rev 10 Realtek driver (i.e. the one I have), it is known to have signal-level and connectivity flakiness. His solution was to find and install the latest driver from the Realtek site, which was Rev 13 at the time of posting. This fixes the issues for him:

[http://ubuntuforums.org/showthread.php?t=1390617&highlight=T410+Intel](http://ubuntuforums.org/showthread.php?t=1390617&highlight=T410+Intel)

Subsequently I found a very detailed thread on this topic from user u2rcrazy with a procedure from Realtek to download and install the updated drivers:

[http://ubuntuforums.org/showthread.php?t=1514883](http://ubuntuforums.org/showthread.php?t=1514883)

I see there is a new kernel update out tonight. I will check rev level of the drivers in the new kernel --- hopefully the new driver is in there. If not I will try to update my drivers over the weekend and report back. 

Thanks for your help!

---

### Post by Vincent_Lin on 2010-11-30
I hope this one is not beaten to death yet.

I have a new x201 with RealTek 8191SE chip.  64 bit 10.10 installed fine except wireless not working.  I have followed the instruction to download/complie/install dirver from RealTek site, using 8191SE_VA2 (2010-10-13 version) from this link:

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8191SE-VA2](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8191SE-VA2)

After the installation/reboot, the sympton is different from what was described here - gnome NetworkManager reports that wireless is disabled, and the checkbox to enable wireless is greyedout.  

I did put r8192se_pci into /etc/modules file before I reboot.

So it is not working.

Any help?  Is this problem resolved yet?  Or mine is a result of something I did wrong?

Thanks for the help.

Vincent

---

### Post by Vincent_Lin on 2010-12-08
Sort of embrassing, but I have to let everyone know, that, my problem was resolved.

It was due to the off setting of wlreless lan/interface card setting in BIOS.  

I read it here about rfkill command and others, and someone mentioned that BIOS settting.  This prompted me to check the setting in BIOS.  So it was off.

Reboot, Set it back to on, and it boots into working wireless - compiled r8192se_pci stuff.  Who knows, maybe the original rtl8192se driver came with ubuntu would work as well.

And this survives a reboot.  I think I am all set.

Thanks all.

Cheers,

Vincent

---

