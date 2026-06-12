---
title: "TV Tuner card: DVICO FusionHDTV DVB-T"
date: 2005-12-06
forum: Hardware &amp; Laptops
---

### Post by humphrey on 2005-12-06
I am trying to get my DVICO FusionHDTV DVB-T card to work in Ubuntu Linux. It works fine in Windows, and I want to get it to work in linux so that I don't have to reboot into Windows every time that I want to watch tv.

My kernel version is 2.6.12.

Googling tells me that there is a linux driver for this card, and that it is in the kernel, but it needs to be enabled. However, almost everything I can find is about the 2.6.11 or 2.6.10 kernels. I also came across something that said that the card should work fine the 2.6.12 kernel, and something else that said that it doesn't.

I assume that MythTV is the best program to use. However, I'm not really fussed what program I have to use, as long as it works.

I have installed tvtime, and that works perfectly with the composite input of my card.

I also have installed MythTV, however I haven't managed to get much past the installation of MythTV.

Can anybody help me to get this card working?

Do I really have to recompile the kernel? If so, does somebody who has got this card to work, have a recompiled kernel that I can use?

Thanks.

---

### Post by BambooClaw on 2006-02-05
Follow the instructions at:
[http://www.linuxtv.org/v4lwiki/index.php/How_to_build_from_CVS]("http://www.linuxtv.org/v4lwiki/index.php/How_to_build_from_CVS")

They worked for me on Breezy, for the Dvico Fusion Dual DVB-T card, so should work for your model.

---

### Post by gecko on 2006-02-26
Since I just did this myself I thought I would add a few steps to make life easier.

You need to recompile the kernel, for my kernel 2.6.12 this required reading the KernelHowTo on the Wiki pages. As per the instructions, I chose to append the current date to my kernel to distinquish it from eveything else. This has a few ramifications but is still better than not doing it. When I rebooted X would not start. I had previously installed the nvidia binary packages and these appeared to have been configured to work with the previous kernel and not the new one. To fix this was easy enough. Just uninstall then reinstall the binary packages which appears to bind them to my new kernel, After a reboot, was back in business.

I downloaded the latest snapshot of v4l from the web. Extracted it and wondered why it would not compile with my kernel. You have to do a *make distclean* which rewrites the version info to match the source of your kernel. Then you can compile. Remember to *sudo make install* not just make install... hehe. So now I have the drivers installed and I am working on the rest of it.

So to outline the process it is

1. Follow instructions on the wiki page KernelHowTo to recompile your kernel

2. Follow instructions on cvs page above to set kernel compile multimedia  options.

3. Compile, Install new kernel and reboot

4. Extract v4l packages, *make distclean*, *make*, *sudo make install*

That should be about it. 

Regards

Gecko

---

### Post by Nikusan on 2006-05-20
[QUOTE=gecko]Since I just did this myself I thought I would add a few steps to make life easier.

You need to recompile the kernel, for my kernel 2.6.12 this required reading the KernelHowTo on the Wiki pages. As per the instructions, I chose to append the current date to my kernel to distinquish it from eveything else. This has a few ramifications but is still better than not doing it. When I rebooted X would not start. I had previously installed the nvidia binary packages and these appeared to have been configured to work with the previous kernel and not the new one. To fix this was easy enough. Just uninstall then reinstall the binary packages which appears to bind them to my new kernel, After a reboot, was back in business.

I downloaded the latest snapshot of v4l from the web. Extracted it and wondered why it would not compile with my kernel. You have to do a *make distclean* which rewrites the version info to match the source of your kernel. Then you can compile. Remember to *sudo make install* not just make install... hehe. So now I have the drivers installed and I am working on the rest of it.

So to outline the process it is

1. Follow instructions on the wiki page KernelHowTo to recompile your kernel

2. Follow instructions on cvs page above to set kernel compile multimedia  options.

3. Compile, Install new kernel and reboot

4. Extract v4l packages, *make distclean*, *make*, *sudo make install*

That should be about it. 

Regards

Gecko[/QUOTE]

I followed the [KernelBuildpackageHowto]("https://wiki.ubuntu.com/KernelBuildpackageHowto") up to the build stage. When I build the source it asks a whole bunch of questions about how I want the kernel setup, the vast majority of which I have no idea how to answer. Isn't there an easier way?

---

### Post by chimpboy on 2006-05-21
Hi all,

First up, apologies if I am asking a stupid question; I did search the forum and wiki but may have missed something. I've also searched all over the web but have to admit that I am now a bit confused.

I think I may be having basically the same problem as Humphrey so I hope this isn't a thread hijack or anything.

Aim is to have MythTV running in a dedicated Ubuntu box. I feel I have done fairly well so far, considering that I have no past experience with Linux. I've got Ubuntu up and running, and can tweak Xorg.conf to have the desktop spanning the monitor & TV, or cloned with the same desktop on each.

The Kernel is 2.6.12-9-386, and I have run apt-get update and apt-get upgrade.

The next step is to get the DVB-T Lite card running, and this is where I am hitting a snag. [ps I also have a lifeview analog card installed but I am not worried about gettign that running at this point.]

"Discover" identifies "Brooktree Corporation Bt878 Video Capture" and "Brooktree Corporation Bt878 Audio Capture" no problems.

I have done "modprobe bttv" and it seems like the BTTV stuff is all there as it should be. After booting, "dmesg | grep bttv && dmesg | grep tuner" shows:

> [4294707.585000] bttv: driver version 0.9.15 loaded
[4294707.585000] bttv: using 8 buffers with 2080k (520 pages) each for capture
[4294707.593000] bttv: Bt8xx card found (0).
[4294707.593000] bttv0: Bt878 (rev 17) at 0000:00:0f.0, irq: 11, latency: 32, mmio: 0xee800000
[4294707.593000] bttv0: detected: DVICO FusionHDTV DVB-T Lite [card=128], PCI subsystem ID is 18ac:db10
[4294707.594000] bttv0: using: DVICO FusionHDTV DVB-T Lite [card=128,autodetected]
[4294707.594000] bttv0: gpio: en=00000000, out=00000000 in=00ffffff [init]
[4294707.618000] bttv0: using tuner=-1
[4294707.633000] bttv0: add subdevice "dvb0"
[4294707.618000] bttv0: using tuner=-1
[4294722.512000] saa7134[0]: there are different flyvideo cards with different tuners
[4294722.512000] saa7134[0]: out there, you might have to use the tuner=<nr> insmod
[4294722.717000] tuner 1-0061: chip found @ 0xc2 (saa7134[0])
[4294722.717000] tuner 1-0061: type set to 5 (Philips PAL_BG (FI1216 and compatibles))


There is an entry in /dev/ called video0, but nothing like dvb or anything.

The point I am at is attempting to 

run scan /usr/share/doc/dvb-utils/examples/scan/dvb-t/au-Melbourne > /root/.tzap/channels.conf

Nothing doing, though - I get 

> scanning /usr/share/doc/dvb-utils/examples/scan/dvb-t/au-Melbourne
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
main:1882: FATAL: failed to open '/dev/dvb/adapter0/frontend0': 2 No such file or directory


This makes sense, because there is nothing under /dev/dvb/ at all - /dev goes straight from /dsp to /dvd.

I have no doubt that I am missing something obvious, but for a linux noob there is a lot of material out there that looks like it *might* be relevant, but also might *not* be.

If anyone can offer me any tips, even just pointing me to some online material that should be relevant to what I am trying to achieve, I'd be grateful.

I'm sorry but I have been successful with running apt-get install for various things, apt-cache search, and I have had no trouble editing conf files with nano, and a few other things, but when it comes to things like "make" and "makedev" and so on, I am not really sure what I am meant to do.

Cheers,

Jason

---

### Post by coherent on 2006-06-22
chimpboy;

Trying running the scan command as root, either by **sudo**  or **sudo -i**

I'm no guru myself but we seem to be stuck at roughly the same spot *grin*

I have created a dvb-t file to scan for my area, but my DViCO card does not seem to be getting any signal.

The dvb-utils tool **femon** reports 0000 across the board.

*goes hunting for a bigger attena*

Please respond if you have gotten any further.

---

