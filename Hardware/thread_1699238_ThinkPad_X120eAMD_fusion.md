---
title: "ThinkPad X120e/AMD fusion?"
date: 2011-03-03
forum: Hardware
---

### Post by walt.smith1960 on 2011-03-03
Any thoughts about this new entry?  I just find Thinkpad ergonomics fit my style nicely.  I'm thinking about this little guy in a couple months.  Has anyone had any experience with this or similar hardware under Ubuntu?  Conventional wisdom is to beware of new hardware with Ubuntu.  How different is AMD fusion over the Athlon Neo in the X100e?  People seem to have gotten the X100e to work without too much tearing of hair.  Most problems I seen on the X100e seem to be BroadCom related (Imagine that:rolleyes:)
[http://reviews.cnet.com/laptops/lenovo-thinkpad-x120e/4505-3121_7-34498277.html?tag=mncol;lst;1#reviewPage1](http://reviews.cnet.com/laptops/lenovo-thinkpad-x120e/4505-3121_7-34498277.html?tag=mncol;lst;1#reviewPage1)

---

### Post by link141 on 2011-03-03
I just ordered one of these last week (friday) -- which was about as soon as one could order it. The reviews of this model were superb and I was in the market for a new laptop. Additionally, a quick search around the web seemed to indicate that lenovos have a reputation for having high compatibility with Linux.

I did a somewhat extensive google search on the compatibility of Zacate with Linux, and what I saw seemed to confirm it will work well as the AMD Linux drivers already support the GPU core.

It's funny, I was about to order the Asus eee pc 1215n, but found out there were major issues where the Ion 2 gpu won't function under linux at all (and NVidia has no plans to support it 'currently').  I then found out Asus was going to release a new model that uses Zacate, but they haven't even officially announced it yet. This, in addition to an issue with eee pc's where the PSU connector could snap off eventually dissuaded me from waiting for the new model.  I then stumbled across this thinkpad and decided to buy it.

My new x120e should arrive the week of the 14th, and I expect to be one of the first customers to receive my unit.  I'll let you know how well it works with Ubuntu then. 

Happy Laptop hunting
Link141

---

### Post by walt.smith1960 on 2011-03-04
Great, thank you.  The "classic" thinkpads have excellent Linux compatibility. I've had an R51 & R61i and everything "just worked" on both. The problem I saw with the predecessor X100e is that it was prone to running pretty warm.  Heat kills.

---

### Post by link141 on 2011-03-04
As many reviewers have stated, one of the biggest improvements from the x100e is that the x120e runs much, much cooler and has vastly better battery life.  I'm really looking forward to getting my unit. :guitar:

---

### Post by ilembitov on 2011-03-04
> **link141 said:**
> 
It's funny, I was about to order the Asus eee pc 1215n, but found out there were major issues where the Ion 2 gpu won't function under linux at all (and NVidia has no plans to support it 'currently'). 

Even with Zacate 1215 series are not the best choice. The build quality is simply too bad. I have used 1215n for a week and found many things annoying. The keyboard flexes and bounces badly (and is actually loud), the touchpad buttons are hard to press. The hard drive is surprisingly loud, too. Furthermore, you can't easily access the internals of 1215n - you'll have to disassemble the whole thing if you want to install SSD or a miniPCI-e card. With HP Pavilion dm1z, for instance, you can easily remove the whole bottom and access the whole motherboard. However, it worries me, that there are no screws in the bottom, just clips.

However, there are some good things about 1215n. The touchpad is big, and so is the screen.

Still, I have not tried dm1z so far (they're not in Russia yet), but x100e really had a better build quality.

---

### Post by mr_raider on 2011-03-04
Just ordered mine this week. Looking forward to reading other experiences of Ubuntu on x120e.

---

### Post by mysho on 2011-03-06
i want to buy x120e too, but at first i have to know if it's compatible with ubuntu, so post your experiences asap

---

### Post by linuxhobox on 2011-03-06
Just finished setting this up.

[LIST]
[*]Realtek wifi works stock w/ Natty / Maverick needs compile of rtl8192ce driver from realtek site. ([http://www.realtek.com/Downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true&SortByDesc=1](http://www.realtek.com/Downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true&SortByDesc=1))(make,make install, reboot)
[*]Bluetooth works stock w/ Natty / Maverick needs work
[*]Fglrx ati graphics  did not compile w/ Natty (is x server compatible?) / works with Maverick  see [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)  (hdmi sound works)
[*]Suspend works w/ Maverick (wifi works after suspend) / not tested with natty
[*]UEFI install worked w/ Natty / Kernel panic with Maverick
[*]UEFI install will not work from usb stick unless it emulates a cd/dvd rom ([http://en.wikipedia.org/wiki/U3](http://en.wikipedia.org/wiki/U3))
[*]Legacy Bios Install worked w/ both
[*]Microphone input does not work on install but I haven't done any troubleshooting yet.
[*]Battery life seems good so far.
[*]Hibernate not tested Natty / Maverick hibernate locks up (no solution yet)
[*] wireless function key has no effect
[*]8Gb ram installed w/ out a problem
[/LIST]

Wireless hasn't dropped in hours of use.

I don't even see the bluetooth device w/ lspci under maverick.  Bios vs Uefi issue?\

Maintenance manual linke --> [http://download.lenovo.com/ibmdl/pub/pc/pccbbs/mobiles_pdf/63y0640_02.pdf](http://download.lenovo.com/ibmdl/pub/pc/pccbbs/mobiles_pdf/63y0640_02.pdf)

---

### Post by mr_raider on 2011-03-06
> **linuxhobox said:**
> Just finished setting this up.

[LIST]
[*]Realtek wifi works stock w/ Natty / Maverick needs compile of rtl8192ce driver from realtek site. (make,make install, reboot)

[*]Bluetooth works stock w/ Natty / Maverick needs work

[*]Fglrx ati graphics  did not compile w/ Natty (is x server compatible?) / works with Maverick  see [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)  (hdmi sound works)

[*]Suspend works w/ Maverick (wifi works after suspend) / not tested with natty

[*]UEFI install worked w/ Natty / Kernel panic with Maverick

[*]UEFI install will not work from usb stick unless it emulates a cd/dvd rom ([http://en.wikipedia.org/wiki/U3]("http://en.wikipedia.org/wiki/U3"))

[*]Legacy Bios Install worked w/ both

[*]Microphone input does not work on install but I haven't done any troubleshooting yet.

[*]Battery life seems good so far.

[*]Hibernate not tested Natty / Maverick hibernate locks up (no solution yet)

[*] wireless function key has no effect

[*]8Gb ram installed w/ out a problem

[/LIST]

Wireless hasn't dropped in hours of use.

I don't even see the bluetooth device w/ lspci under maverick.  Bios vs Uefi issue?

So essentially I have a choice:

Run kernel 2.6.38 with built in wireless support, but use the open source ATI driver, or run an older kernel like 2.6.35 and install the realtek driver manually, but I still get fglrx.

How do you choose to do a BIOs vs uefi install?

---

### Post by linuxhobox on 2011-03-06
> **mr_raider said:**
> So essentially I have a choice:

Run kernel 2.6.38 with built in wireless support, but use the open source ATI driver, or run an older kernel like 2.6.35 and install the realtek driver manually, but I still get fglrx.

How do you choose to do a BIOs vs uefi install?

 The cmos/bios/lenovo setup (press enter on startup) util has options for uefi only, legacy (bios) only, and both.  Selecting uefi only gives a uefi install.   
You'll know if you did it correctly since the installer CD falls into a uefi grub menu. 
The default windows install used a bios MBR. So, to keep it you would want to not do a uefi install.   

I might pick up another hard drive and try another distro next weekend.  Natty uses xserver 1.10 which fglrx doesn't yet yet.  I could always go back once fglrx support hits.  It would be nice to have working bluetooth.   

Hibernate: I'm thinking fglrx may be causing hibernate to lock up.  Will test this once I do another install.
  I tested w/ wireless module blacklisted.  So, wireless should be fine.

---

### Post by linuxhobox on 2011-03-06
[http://fossplanet.com/f10/natty-kernel-oops-3-6-build-iso-amd64-x120e-111057/](http://fossplanet.com/f10/natty-kernel-oops-3-6-build-iso-amd64-x120e-111057/)
Found this on natty install.

Install did work for me in text mode. And booted afterwards.

---

### Post by mysho on 2011-03-07
keep posting please, your info is very useful (looks like i will not buy x120e untill it will work better with ubuntu - i don't like windows)

---

### Post by linuxhobox on 2011-03-07
The laptop does work.  I'm running maverick now.

Here is a list of things not working:
[LIST]
[*]Builtin Microphone (not tested on natty)
[*]Hibernate (not tested on natty)
[*]Bluetooth (works on natty)
[/LIST]

Suspend works great and so does wireless.

Fglrx needs support for the most recent xserver.  I did see some posts that say the open-source ati driver will support 6x ati very soon.  Don't know if the hdmi audio will work w/ out flgrx.

Overall, I'm glad I got this laptop over the sony or dm1z.  The build quality is much better.

---

### Post by Kenjitamura on 2011-03-07
I'm just starting up college classes and recognise I'll probably eventually need an ultraportable for class notes and increased productivity at school, however right now I'm only a part time student so I don't have the greatest need.  I can only hope that AMD plans to unveil the next generation of fusion APU's as fast next year as they did this year.  Zacate/Ontario are first generation, granted they perform very well, but looking at the expected features of Krishna/Wichita I find waiting for that much of an improvement in technology at the same price point worth it.  

Differences:
Ontario/Zacate only use single channel ram, this is killing the potential performance of the APU; the CPU and GPU are sharing single channel bandwidth to the system memory.  Krishna/Wichita are expected to have dual channel ram.  Ontario/Zacate uses a 40 nm production process, Krishna/Wichita will use a 28 nm production process which will allow them to fit up to four cores on the die while probably still consuming less power/yielding higher performance.  Krishna/Wichita will be using a 7xxx series gpu.  Finally, current fusion chips aren't using the new instruction sets such as AVX and FMA4; I'm hoping the second generation bobcats will have them so they're future proofed.

There is of course an added benefit for me in waiting this long, any kinks with current fusion products found in software/drivers will hopefully be worked out by the time Krishna/Wichita hit.  Even still I'm very tempted to buy an hp dm1z, I acknowledge it's not the most stable chassis design but at $428 after the student discount it does meet all the needs I have as a student.  Long battery life, responsive performance, discrete level graphics, and very compact.

---

### Post by estebanko on 2011-03-07
> **linuxhobox said:**
> The laptop does work.  I'm running maverick now.

Here is a list of things not working:
[LIST]
[*]Builtin Microphone (not tested on natty)
[*]Hibernate (not tested on natty)
[*]Bluetooth (works on natty)
[/LIST]

Suspend works great and so does wireless.

Fglrx needs support for the most recent xserver.  I did see some posts that say the open-source ati driver will support 6x ati very soon.  Don't know if the hdmi audio will work w/ out flgrx.

Overall, I'm glad I got this laptop over the sony or dm1z.  The build quality is much better.

This is really great information as I have one on order and is very determined to replace windows with working copy of Ubuntu. :)

I plan to use Skype with this which might be a problem as Microphone isn't seem to be supported. Have you given the webcam a shot? 

Thanks,
Stephen

---

### Post by linuxhobox on 2011-03-07
Webcam works fine.

Bus 002 Device 003: ID 04f2:b1b4 Chicony Electronics Co., Ltd Lenovo Integrated Camera

I'll take another look at the internal microphone.  Also, note that the external is a single jack for both microphone and headphone inputs.  Lenovo does not include an adapter.

Update: got some hissing using alsamixer to unmute an input.  snd-hda-intel mode settings?

---

### Post by EvilRobot69 on 2011-03-08
I've got most things working except the microphone. Has anyone had any luck?

---

### Post by Sven.77 on 2011-03-08
Lots of good info in this thread. Just received my x120e last night. Having trouble with the realtek wireless driver. The only rtl8192ce Linux driver I'm finding on Realtek's site is rtl8192ce-VA4. Is that the one you guys have gotten to work? Wasn't sure what the VA4 meant. I pulled it down and tried to do a make and make install, but encountered errors during the make install part. Haven't spent too much time troubleshooting that yet. Just wanted to verify that I'm barking up the right tree with the rtl8192ce-VA4 driver. Thanks!

---

### Post by linuxhobox on 2011-03-08
The file I downloaded was:
rtl8192ce_linux_2.6.0005.1116.2010.tar.gz

As for the sound,  I still don't have the microphone working.  I'll be trying to change model setting in /etc/modprobe.d/alsa-base.conf:
options-snd-hda-intel model=3stack

see [http://alsa.opensrc.org/Hda](http://alsa.opensrc.org/Hda)
for a list of possible model params.  The most recent params are also to be found in the alsa/kernel source. 

If someone gets bluetooth or the microphone working on maverick please post.

---

### Post by link141 on 2011-03-08
Thanks for all the info.  My laptop just shipped today, so there will be one more linux user messing with this thing by the end of next week ;).

I checked on think wiki and it appears the x120e uses the same sound codec as the x100e: [Link here.](http://www.thinkwiki.org/wiki/Category:X100e)  The website mentions that you can get the microphone working on the x100e by adding the following to modprobe.conf ```
options snd-hda-intel model=ideapad
``` Linuxhobox, since the codec is the same, could you try doing this on your x120e and see what happens? Also, could you check if the the headphone jack works with headphones?

As a side note, I believe the the headphone/microphone combo port just uses a standard 3.5mm three-ring headset jack (which is backwards compatible with normal headphones and speakers).

Overall, I'm relieved that this laptop is working so well with linux considering how new it is.

Thanks,
link141

---

### Post by Sven.77 on 2011-03-08
Now I understand. The link on Realtek's site for that driver says RTL8188CE. That threw me. Now I'm on the same page. I'm about to give that driver a try.

If I get the microphone working I'll post an update.

This could be a sweet little Linux laptop. Can't wait to get it working.

---

### Post by Yellow Pasque on 2011-03-08
More adventurous folk can try the xorg-edgers PPA and the 2.6.38 kernel within. It should get LAN and bluetooth working without special drivers. Or you could just use Natty..

---

### Post by linuxhobox on 2011-03-08
[COLOR=Black]no luck w/ params ideapad, lenovo-101e.

[/COLOR]

---

### Post by Yellow Pasque on 2011-03-08
You will probably need a very recent ALSA to get sound fully working. [http://ubuntuforums.org/showthread.php?t=1681577](http://ubuntuforums.org/showthread.php?t=1681577)

> ALSA: hda - add support for Lenovo ThinkPad X100e in conexant codec -- ALSA 1.0.24 changelog (maverick has 1.0.23)

---

### Post by KartDriver on 2011-03-09
I'm currently up and running on an X120E with Ubuntu 10.10.  The two problem areas for me were video and wireless, everything else, including sound worked out of the box.  I didn't opt for blue tooth since I don't need it.

Here is my lspci:

00:00.0 Host bridge: Advanced Micro Devices [AMD] Device 1510
00:01.0 VGA compatible controller: ATI Technologies Inc Device 9802
00:01.1 Audio device: ATI Technologies Inc Device 1314
00:06.0 PCI bridge: Advanced Micro Devices [AMD] Device 1514
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 42)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller (rev 40)
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (rev 40)
00:15.0 PCI bridge: ATI Technologies Inc Device 43a0
00:15.1 PCI bridge: ATI Technologies Inc Device 43a1
00:18.0 Host bridge: Advanced Micro Devices [AMD] Device 1700 (rev 43)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Device 1701
00:18.2 Host bridge: Advanced Micro Devices [AMD] Device 1702
00:18.3 Host bridge: Advanced Micro Devices [AMD] Device 1703
00:18.4 Host bridge: Advanced Micro Devices [AMD] Device 1704
00:18.5 Host bridge: Advanced Micro Devices [AMD] Device 1718
00:18.6 Host bridge: Advanced Micro Devices [AMD] Device 1716
00:18.7 Host bridge: Advanced Micro Devices [AMD] Device 1719
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
04:00.0 Network controller: Broadcom Corporation Device 0576 (rev 01)

I purchased mine with the A/B/G/N driver option thinking that it would be easier to make work than the Realtek, well as it turns out the driver that is available in 10.10 doesn't work with the 0576 Broadcom card, so I had to install the version from here: [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php) .  Wireless performance and range do seem to be very excellent with this card however.

I installed the fglrx that comes with 10.10, but got the watermark on the bottom right saying my card was unsupported but seemed to have working video acceleration.  I ended up downloading the latest e-350 Catalyst drivers directly from AMD which fixed the issue.

I had no luck with 11.04, I tried the Alpha3 and snap shot and both would lock up during installation for me.

Lastly I am having issues playing full screen flash movies, they just don't play the video... I would appreciate it if anyone has info or help for this problem.

---

### Post by linuxhobox on 2011-03-09
updated also and I had input for a short time and then nothing.
This was with 'ideapad' param.  I'll try others tomoorow.
Update:
I think it may be working but w/ a pulseaudio problem now.
So, the alsa update MAY have worked.
I can see input on the input tab of gnome-volume-control but eventually that stops working.
I'll update again when I know more.

---

### Post by mogorman on 2011-03-09
does anyone have bluetooth working?  I don't seem to even have it installed when i do an lspci or lsusb.  Can someone show the relevant lsusb or lspci with bluetooth?

```
mog@geminiman:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] Device 1510
00:01.0 VGA compatible controller: ATI Technologies Inc Device 9802
00:01.1 Audio device: ATI Technologies Inc Device 1314
00:06.0 PCI bridge: Advanced Micro Devices [AMD] Device 1514
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 42)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller (rev 40)
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (rev 40)
00:15.0 PCI bridge: ATI Technologies Inc Device 43a0
00:15.1 PCI bridge: ATI Technologies Inc Device 43a1
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 0 (rev 43)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 6
00:18.6 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 5
00:18.7 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 7
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
04:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev 01)
mog@geminiman:~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 04f2:b1b4 Chicony Electronics Co., Ltd Lenovo Integrated Camera
Bus 002 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID f617:0905  
Bus 001 Device 003: ID 046d:c00e Logitech, Inc. M-BJ58/M-BJ69 Optical Wheel Mouse
Bus 001 Device 002: ID 0409:005a NEC Corp. HighSpeed Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

---

### Post by linuxhobox on 2011-03-09
My 120e is configured w/ realtek wireless, bluetooth, and no Wimax/WAN.

Recap to help others since I've been working on this on and off since friday.
Any help on what isn't working below would be great.

I'm going to grab a spare hard drive and try more things later this week.

Some comments on Natty:

[LIST]
[*]Enabled efi only in cmos setup / No Bios install
[*]Natty04 March current build  installed using efi and text mode install w/ natty
[*]Bluetooth worked in Natty on first boot but not on later install
[*]Wireless worked w/ additional driver in Natty
[*]internal microphone works (alsa version 1.0.24)
[*]flgrx did not work (version of xorg?)
[*]webcam not tested
[*]internal microphone works
[/LIST]

So, I switched to maverick:

[LIST]
[*]compiling driver from realtek site activated wireless (see posts above for driver name)
[*]microphone input seems to need an alsa update but is not fully working (see posts above, maybe I have pulse problem now?)
[*]bluetooth seems to be disabled since it does not show up w/ lspci (it is enabled in cmos setup)
[*]hibernate does not work (freezes)
[*]suspend does work
[*]some fn function keys do not work (F3 (microphone disabe?),F6 (camera/mic)),F5 wireless kill
[*]have not tested external microphone since I don't have one handy
[*]webcam works
[*]fglrx install works
[/LIST]
Has anyone tried an lenovo intel 5100 wireless card yet?

---

### Post by linuxhobox on 2011-03-09
> **mogorman said:**
> does anyone have bluetooth working?  I don't seem to even have it installed when i do an lspci or lsusb.  Can someone show the relevant lsusb or lspci with bluetooth?



It worked in Natty (EFI).  No luck w/ Maverick.
I'm grabbing another hard drive and will reinstall Natty and try a Maverick EFI install.
May not have time to do this until the weekend.
I tried a kernel ppa w/ a 2.6.37 kernel but it killed fglrx.  I will reboot into that kernel and try a lspci.

Diff of kernel 2.6.35-28 vs 2.6.37-020637rc2-generic ppa (only diff is no wireless driver installed)
```

7c7
<       Flags: bus master, fast devsel, latency 0, IRQ 18
---
>       Flags: bus master, fast devsel, latency 0, IRQ 45
28c28
<       Memory behind bridge: ffd00000-ffdfffff
---
>       Memory behind bridge: f0300000-f03fffff
105c105
<       Prefetchable memory behind bridge: 00000000ffb00000-00000000ffcfffff
---
>       Prefetchable memory behind bridge: 00000000f0400000-00000000f05fffff
141c141
<       Expansion ROM at f00e0000 [disabled] [size=128K]
---
>       Expansion ROM at f0020000 [disabled] [size=128K]
149c149
<       Flags: bus master, fast devsel, latency 0, IRQ 10
---
>       Flags: bus master, fast devsel, latency 0, IRQ 17
152a153,154
>       Kernel driver in use: rtl8192CE
>       Kernel modules: r8192ce_pci


```So, bluetooth still isn't there.

UPDATE: did not work after another natty install.  I did boot windows one time.  Maybe that enabled it temporarily.

---

### Post by mogorman on 2011-03-09
if the kernels present no difference it must be efi setting?  how do i enable that in the bios, i am just using the stock bios settings from the laptop.  Also if you do go back to natty I am curious how the bt card shows up.  I am just worried they sent me my laptop with out bt and i will have to ship it back to lenovo.

---

### Post by linuxhobox on 2011-03-09
> **mogorman said:**
> if the kernels present no difference it must be  efi setting?  how do i enable that in the bios, i am just using the  stock bios settings from the laptop.  Also if you do go back to natty I  am curious how the bt card shows up.  I am just worried they sent me my  laptop with out bt and i will have to ship it back to lenovo.

EFI --> [http://en.wikipedia.org/wiki/Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Extensible_Firmware_Interface)

It  is a setting in 'setup' that disables legacy bios support and selects  'efi' only.  I can't take a look now since I'm using the laptop.

You  will need to use an external cd rom or a 'U3' w/ an iso image.  The usb  startup creater uses a master boot record and won't boot under pure efi  support.

usb_boot disk  look under mac intel section --> [http://en.wikipedia.org/wiki/Live_USB](http://en.wikipedia.org/wiki/Live_USB) 

Another  option would be to try to use virtualbox and set efi in settings to  make a boot disk.  It would be a little tricky but might work.

---

### Post by linuxhobox on 2011-03-10
Trying additional Natty installs on spare hard drive.

Alpha image did not work but a daily build did work.

Okay, did another EFI install and still no bluetooth.

Natty daily build must use classic desktop w/ no effect or a compiz crash will lock X.

I did do one windows boot.  Maybe that enabled it.

Has anyone done a DSDT dump yet?  I'm wondering if there is an ACPI switch.

[COLOR=Red]**Internal microphone works in NATTY!!!!!**[/COLOR]

Hibernate does not work in Natty.

So, natty only seems to get a working microphone.  Everything else seems the same as maverick with the addition of the wireless driver.

Interesting EFI links:

[http://packages.ubuntu.com/maverick/grub-rescue-efi-amd64](http://packages.ubuntu.com/maverick/grub-rescue-efi-amd64)

[http://ubuntuforums.org/showthread.php?t=869324](http://ubuntuforums.org/showthread.php?t=869324)

Maybe related? [https://bugs.launchpad.net/ubuntu/+source/toshset/+bug/261318](https://bugs.launchpad.net/ubuntu/+source/toshset/+bug/261318)

I'm thinking an acpi event is needed to enable bluetooth.

---

### Post by link141 on 2011-03-10
Thanks again for all the info.

It looks like my laptop will may arrive as early as Thursday (well I guess today :P) or Friday, so I'll soon post my experience with it as well. Can't wait :D

Perhaps I'll make a wiki page on help.ubuntu.com when I get my unit...

---

### Post by linuxhobox on 2011-03-10
Building a windows image now to test enabling bluetooth in windows.
Update:
Booted into windows, enabled bluetooth, seeing it in Ubuntu.

[COLOR=Red][B]It is a USB broadcoam adapter

[COLOR=Black]```



Bus 003 Device 002: ID 0a5c:217f Broadcom Corp. Bluetooth Controller
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass          224 Wireless
  bDeviceSubClass         1 Radio Frequency
  bDeviceProtocol         1 Bluetooth
  bMaxPacketSize0        64
  idVendor           0x0a5c Broadcom Corp.
  idProduct          0x217f Bluetooth Controller
  bcdDevice            7.48
  iManufacturer           1 
  iProduct                2 
  iSerial                 3 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength          216
    bNumInterfaces          4
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           3
      bInterfaceClass       224 Wireless
      bInterfaceSubClass      1 Radio Frequency
      bInterfaceProtocol      1 Bluetooth
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0010  1x 16 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass       224 Wireless
      bInterfaceSubClass      1 Radio Frequency
      bInterfaceProtocol      1 Bluetooth
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0000  1x 0 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0000  1x 0 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       1
      bNumEndpoints           2
      bInterfaceClass       224 Wireless
      bInterfaceSubClass      1 Radio Frequency
      bInterfaceProtocol      1 Bluetooth
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0009  1x 9 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0009  1x 9 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       2
      bNumEndpoints           2
      bInterfaceClass       224 Wireless
      bInterfaceSubClass      1 Radio Frequency
      bInterfaceProtocol      1 Bluetooth
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0011  1x 17 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0011  1x 17 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       3
      bNumEndpoints           2
      bInterfaceClass       224 Wireless
      bInterfaceSubClass      1 Radio Frequency
      bInterfaceProtocol      1 Bluetooth
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0020  1x 32 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0020  1x 32 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       4
      bNumEndpoints           2
      bInterfaceClass       224 Wireless
      bInterfaceSubClass      1 Radio Frequency
      bInterfaceProtocol      1 Bluetooth
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       5
      bNumEndpoints           2
      bInterfaceClass       224 Wireless
      bInterfaceSubClass      1 Radio Frequency
      bInterfaceProtocol      1 Bluetooth
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        2
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x84  EP 4 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0020  1x 32 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x04  EP 4 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0020  1x 32 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        3
      bAlternateSetting       0
      bNumEndpoints           0
      bInterfaceClass       254 Application Specific Interface
      bInterfaceSubClass      1 Device Firmware Update
      bInterfaceProtocol      1 
      iInterface              0 
      Device Firmware Upgrade Interface Descriptor:
        bLength                             7
        bDescriptorType                    33
        bmAttributes                        7
          Will Not Detach
          Manifestation Tolerant
          Upload Supported
          Download Supported
        wDetachTimeout                   5000 milliseconds
        wTransferSize                      64 bytes



```I'll try a usb snoop under windows to see if a usb command is used to enable/disable.
If so, we should be able to put together a script to turn this on.
If not, I'll dump the DSDT and see if it is an ACPI thing.

[COLOR=Red]The device stays enabled between reboots on maverick.
So, it looks like it needed to be enabled (in windows).
Question: How to enable in linux?
[/COLOR] [/COLOR]
[/B][/COLOR]

---

### Post by mogorman on 2011-03-10
thank you for the info.  I will try to get a windows install up again and send it that command.  Given that we don't see it in lsusb without first enabling it in windows I would assume its an acpi command being sent across the bus.  Anyways good luck and happy hunting.

---

### Post by Yellow Pasque on 2011-03-10
Check rfkill man page and see if that's what;s blocking it.

---

### Post by mogorman on 2011-03-10
rfkill list all and rfkill list return nothing also rfkill unblock bluetooth did nothing as well

---

### Post by removesstains on 2011-03-10
> **KartDriver said:**
> I'm currently up and running on an X120E with Ubuntu 10.10.  The two problem areas for me were video and wireless, everything else, including sound worked out of the box.  I didn't opt for blue tooth since I don't need it.

Here is my lspci:

00:00.0 Host bridge: Advanced Micro Devices [AMD] Device 1510
00:01.0 VGA compatible controller: ATI Technologies Inc Device 9802
00:01.1 Audio device: ATI Technologies Inc Device 1314
00:06.0 PCI bridge: Advanced Micro Devices [AMD] Device 1514
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 42)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller (rev 40)
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (rev 40)
00:15.0 PCI bridge: ATI Technologies Inc Device 43a0
00:15.1 PCI bridge: ATI Technologies Inc Device 43a1
00:18.0 Host bridge: Advanced Micro Devices [AMD] Device 1700 (rev 43)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Device 1701
00:18.2 Host bridge: Advanced Micro Devices [AMD] Device 1702
00:18.3 Host bridge: Advanced Micro Devices [AMD] Device 1703
00:18.4 Host bridge: Advanced Micro Devices [AMD] Device 1704
00:18.5 Host bridge: Advanced Micro Devices [AMD] Device 1718
00:18.6 Host bridge: Advanced Micro Devices [AMD] Device 1716
00:18.7 Host bridge: Advanced Micro Devices [AMD] Device 1719
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
04:00.0 Network controller: Broadcom Corporation Device 0576 (rev 01)

I purchased mine with the A/B/G/N driver option thinking that it would be easier to make work than the Realtek, well as it turns out the driver that is available in 10.10 doesn't work with the 0576 Broadcom card, so I had to install the version from here: [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php) .  Wireless performance and range do seem to be very excellent with this card however.

I installed the fglrx that comes with 10.10, but got the watermark on the bottom right saying my card was unsupported but seemed to have working video acceleration.  I ended up downloading the latest e-350 Catalyst drivers directly from AMD which fixed the issue.

I had no luck with 11.04, I tried the Alpha3 and snap shot and both would lock up during installation for me.

Lastly I am having issues playing full screen flash movies, they just don't play the video... I would appreciate it if anyone has info or help for this problem.


Can you tell me how you installed the Broadcom driver? i suck at tar.gz files and have no idea how to compile them.

---

### Post by linuxhobox on 2011-03-10
This looks interesting:

```

3-4:1.2: No such file or directory
3-4:1.3: No such file or directory
/:  Bus 04.Port 1: Dev 1, Class=root_hub, Driver=ohci_hcd/5p, 12M
[COLOR=Red]/:  Bus 03.Port 1: Dev 1, Class=root_hub, Driver=ohci_hcd/5p, 12M
    |__ Port 4: Dev 2, If 0, Class='bInterfaceClass 0xe0 not yet handled', Driver=btusb, 12M
    |__ Port 4: Dev 2, If 1, Class='bInterfaceClass 0xe0 not yet handled', Driver=btusb, 12M
    |__ Port 4: Dev 2, If 2, Class=vend., Driver=, 12M
    |__ Port 4: Dev 2, If 3, Class=app., Driver=, 12M[/COLOR]
/:  Bus 02.Port 1: Dev 1, Class=root_hub, Driver=ehci_hcd/5p, 480M
    |__ Port 2: Dev 2, If 0, Class=stor., Driver=usb-storage, 480M
    |__ Port 5: Dev 3, If 0, Class='bInterfaceClass 0x0e not yet handled', Driver=uvcvideo, 480M
    |__ Port 5: Dev 3, If 1, Class='bInterfaceClass 0x0e not yet handled', Driver=uvcvideo, 480M
/:  Bus 01.Port 1: Dev 1, Class=root_hub, Driver=ehci_hcd/5p, 480M


```

and 
lspci | grep -i usb 
l
when bluetooth was disabled:
```

00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller (prog-if 10 [OHCI])
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller (prog-if 20 [EHCI])
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller (prog-if 10 [OHCI])
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller (prog-if 20 [EHCI])

```

with bluetooth enabled
```

00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller (prog-if 10 [OHCI])
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller (prog-if 20 [EHCI])
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller (prog-if 10 [OHCI])
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller (prog-if 20 [EHCI])

```

The same number of usb devices.

and rfkill list (bt enabled)

```

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

```

---

### Post by linuxhobox on 2011-03-10
DSDT decompiled dump for anyone that is interested.

I've still got these outstanding:

[LIST]
[*]hibernate freezes machine
[*]internal microphone in maverick <EDIT: fixed -- see later post>
[*]bluetooth enable/disable with out windows <EDIT: may be working w/ 2.6..37 see later post possibly kills microphone>
[*]EDIT: 64 bit guest OS does not work in w/ VirtualBox 4.04 but VMWare works
[/LIST]
Fortunately,

 *     Compiler ID      "PTEC"

no MS compiler.  I'm guessing PTEC means phoenix technoloogies

---

### Post by kelpdip on 2011-03-10
Does anyone have Natty (Alpha 3, 07-03-2011) live working without install? Mine hangs somewhere between x and the shell. It seems to work before the attempt -- sound, wifi shown by launching firefox before launching the live os. I'm not really willing to install until live works.

Any way to pull logs from a USB drive when attempting a live session?

This is my first time using Win7, and I'm pleasantly surprised, but would still like to get back to what I'm used to.

```
00:00.0 Host bridge: Advanced Micro Devices [AMD] Device 1510
00:01.0 VGA compatible controller: ATI Technologies Inc Device 9802
00:01.1 Audio device: ATI Technologies Inc Device 1314
00:06.0 PCI bridge: Advanced Micro Devices [AMD] Device 1514
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 42)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller (rev 40)
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (rev 40)
00:15.0 PCI bridge: ATI Technologies Inc Device 43a0
00:15.1 PCI bridge: ATI Technologies Inc Device 43a1
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 0 (rev 43)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 6
00:18.6 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 5
00:18.7 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 7
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
04:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev 01)
```

```
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 04f2:b1b4 Chicony Electronics Co., Ltd Lenovo Integrated Camera
Bus 002 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 1307:0163 Transcend Information, Inc. 256MB/512MB/1GB Flash Drive
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

---

### Post by linuxhobox on 2011-03-10
I never got Natty alpha to boot.

The daily will hang because of a compiz crash if you try to run unity.

If you nstall in text mode, then you should/may be able run in classic mode without effects. 

Daily build --> [http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

I used one from last weekend.  Other than the microphone, maverick seems to have just as much functionality plus fglrx.

I would imagine there should be some way to boot directly into classic mode w/ a live cd.

this might be related : [https://bugs.launchpad.net/ubuntu/+source/unity/+bug/696999](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/696999)

Although, your live install session looks more stable.  Did you use alpha 3?

---

### Post by Yellow Pasque on 2011-03-11
Maybe you should try Xubuntu..

---

### Post by kelpdip on 2011-03-11
Thanks. Compiz/unity problems do seem like a likely culprit. I was using the alpha 3, not the daily. That screenshot is from clicking the "release notes" link in the installer dialog. I wanted to check wifi/sound.

When I have some time I'll look into adding parameters to the live session which I think is possible. I'd be happy with gnome shell and no compiz.

> **linuxhobox said:**
> I never got Natty alpha to boot.

The daily will hang because of a compiz crash if you try to run unity.

If you nstall in text mode, then you should/may be able run in classic mode without effects. 

Daily build --> [http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

I used one from last weekend.  Other than the microphone, maverick seems to have just as much functionality plus fglrx.

I would imagine there should be some way to boot directly into classic mode w/ a live cd.

this might be related : [https://bugs.launchpad.net/ubuntu/+source/unity/+bug/696999](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/696999)

Although, your live install session looks more stable.  Did you use alpha 3?

---

### Post by linuxhobox on 2011-03-11
Got the internal microphone working w/ maverick

[LIST]
[*]upgraded alsa in maverick (follow link on page three of this thread) -->[http://ubuntuforums.org/showthread.php?t=1681577](http://ubuntuforums.org/showthread.php?t=1681577)
[*]add the red line below in the hooks section of /usr/share/alsa/alsa.conf
[/LIST]
```

@hooks [
        {
                func load
                files [
                       [COLOR=Red] "/usr/share/alsa/pulse.conf"[/COLOR]
                        "/etc/asound.conf"
                        "~/.asoundrc"
                ]
                errors false
        }
]


```
[LIST]
[*]reinstall pulseaudio to fix configs
[*]do not have model=ideapad for hda-snd-intel param
[/LIST]

---

### Post by mr_raider on 2011-03-11
My wireless under maverick seems to be crapping out. I can build the driver, but here is the result of make install:


```
nabeel@dv2 ~/rtl8192ce_linux_2.6.0005.1116.2010 $ sudo make install
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-25-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-25-generic'
make[1]: Entering directory `/home/nabeel/rtl8192ce_linux_2.6.0005.1116.2010/HAL/rtl8192'
make -C /lib/modules/2.6.35-25-generic/build M= CC=gcc modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.35-25-generic'
  CHK     include/linux/version.h
  CHK     include/generated/utsrelease.h
make[3]: *** No rule to make target `kernel/bounds.c', needed by `kernel/bounds.s'.  Stop.
make[2]: *** [prepare0] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.35-25-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/nabeel/rtl8192ce_linux_2.6.0005.1116.2010/HAL/rtl8192'
make: *** [install] Error 2

```

```
nabeel@dv2 ~/rtl8192ce_linux_2.6.0005.1116.2010 $ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] Device 1510
00:01.0 VGA compatible controller: ATI Technologies Inc Device 9802
00:01.1 Audio device: ATI Technologies Inc Device 1314
00:06.0 PCI bridge: Advanced Micro Devices [AMD] Device 1514
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 42)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller (rev 40)
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (rev 40)
00:15.0 PCI bridge: ATI Technologies Inc Device 43a0
00:15.1 PCI bridge: ATI Technologies Inc Device 43a1
00:18.0 Host bridge: Advanced Micro Devices [AMD] Device 1700 (rev 43)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Device 1701
00:18.2 Host bridge: Advanced Micro Devices [AMD] Device 1702
00:18.3 Host bridge: Advanced Micro Devices [AMD] Device 1703
00:18.4 Host bridge: Advanced Micro Devices [AMD] Device 1704
00:18.5 Host bridge: Advanced Micro Devices [AMD] Device 1718
00:18.6 Host bridge: Advanced Micro Devices [AMD] Device 1716
00:18.7 Host bridge: Advanced Micro Devices [AMD] Device 1719
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
04:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8176 (rev 01)

```

---

### Post by linuxhobox on 2011-03-11
[QUOTE=mr_raider;10548420]My wireless under maverick seems to be crapping out. I can build the driver, but here is the result of make install:


```
nabeel@dv2 ~/rtl8192ce_linux_2.6.0005.1116.2010 $ sudo make install
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-25-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[1]: Leaving directory `/usr/src/linu** No rule to make target `kernel/bounds.c', needed by `kernel/bounds.s'.  Stop.x-headers-2.6.35-25-generic'
make[1]: Entering directory `/home/nabeel/rtl8192ce_linux_2.6.0005.1116.2010/HAL/rtl8192'
make -C /lib/modules/2.6.35-25-generic/build M= CC=gcc modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.35-25-generic'
  CHK     include/linux/version.h
  CHK     include/generated/utsrelease.h
make[3]: *** No rule to make target `kernel/bounds.c', needed by `kernel/bounds.s'.  Stop.
make[2]: *** [prepare0] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.35-25-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/nabeel/rtl8192ce_linux_2.6.0005.1116.2010/HAL/rtl8192'
make: *** [install] Error 2

```try:
```

sudo su
make clean
make
make install

```I'm thinking a shell variable may not be defined when you 'sudo make install'

Also, make sure your have 'build-essential' and relevant kernel header packages installed.
You could also install the rel event kernel sources to be on the safe side.
Although, it built for me w/ only the headers.

```
apt-get install linux-headers-`uname -r`
apt-get install build-essential

```

---

### Post by mr_raider on 2011-03-11
That did it. Really stupid. I always thought that su and sudo were the same.

---

### Post by estebanko on 2011-03-11
> **linuxhobox said:**
> Got the internal microphone working w/ maverick

[LIST]
[*]upgraded alsa in maverick (follow link on page three of this thread) -->[http://ubuntuforums.org/showthread.php?t=1681577](http://ubuntuforums.org/showthread.php?t=1681577)
[*]add the red line below in the hooks section of /usr/share/alsa/alsa.conf
[/LIST]
```

@hooks [
        {
                func load
                files [
                       [COLOR=Red] "/usr/share/alsa/pulse.conf"[/COLOR]
                        "/etc/asound.conf"
                        "~/.asoundrc"
                ]
                errors false
        }
]


```
[LIST]
[*]reinstall pulseaudio to fix configs
[*]do not have model=ideapad for hda-snd-intel param
[/LIST]

Huge thanks to linuxhobox my microphone is working. Now this machine does everything I need. :)

This laptop is turning out to be a real fun little machine.

---

### Post by link141 on 2011-03-11
My laptop just arrived about 15 minutes ago.  I going to wait until my dad gets done work to open it.  When I do, I'll try net-booting a live cd and see what happens...:popcorn:

---

### Post by mrprefect on 2011-03-11
just got my x120e today and installed maverick, same issues as most with video and wireless.

Starting with wireless am I doing something wrong. I downloaded and installed the rtl8192ce and it looks like it loads comes up when I do an lsmod but for some reason it doesn't seem to see my wireless network.

Not really sure what to do now....

---

### Post by link141 on 2011-03-11
Just opened this thing up.  It's AWESOME!

I'm proceeding to backup the windows partition, then I'll netboot a live cd and see if I can install Kubuntu Maverick.

By the way, here are my specs:
AMD E-350
2GB ram (will upgrade to 6GB soon)
B/G/N wireless
320GB 7200rpm drive

Everything else is the same as the base model.

---

### Post by thinkling on 2011-03-11
I got mine today as well and just finished setting up maverick. I'm new to linux, and the easiest way to get wireless working was from this PPA (found in the Ubuntu community documentation pages): [https://launchpad.net/~lexical/+archive/hwe-wireless](https://launchpad.net/~lexical/+archive/hwe-wireless)

For video, AMD has easy-to-follow instructions in their release notes on their driver download page here: [http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English)

---

### Post by skomra on 2011-03-11
Also received mine today, it's nice! I tried to install natty into the 238 GB windows partition (deleting windows), while leaving the 20GB partition that I assumed was the windows recovery. (There's also third 1.7GB (swap?) partition).

Anyway, something went wrong and I the 20GB partition disappeared. So... I wiped the whole hard drive and installed maverick. I wasn't going to ever use Windows, I just wanted to leave it in case I ever sold/gave it away down the road. 

Everything seems to be working so far except the AMD unsupported hardware ghost in the bottom right corner.

---

### Post by linuxhobox on 2011-03-11
> **mrprefect said:**
> just got my x120e today and installed maverick, same issues as most with video and wireless.

Starting with wireless am I doing something wrong. I downloaded and installed the rtl8192ce and it looks like it loads comes up when I do an lsmod but for some reason it doesn't seem to see my wireless network.

Not really sure what to do now....


try
```

sudo iwconfig
sudo iwlist wlan0 scan

```
from the command line to make sure its not a Network Manager problem.
the first command should show a wireless interface (wlan0)
the second should do a scan for APs

That is, if you have not already done so.

---

### Post by linuxhobox on 2011-03-11
Has anyone successfully booted a 64 bit guest OS in VirtualBox?

I've got a kernel panic on ubnuntu 64 bit and freebsd 64bit.

I've still got win 7 on my spare hard disc.  I'm thinking I'll check and make sure it is not a hardware thing.

Update: windows 7 64 bit also bluescreens on ubuntu 64 host.

Update2: Qemu/kvm freezes

If anyone has a windows partitiion w/ XP Mode, could you try and run it to see if amd-v is working.

EDIT: AMD-V has been enabled in bios.

---

### Post by mr_raider on 2011-03-12
AMD-v is turned off by default in BIOS.

---

### Post by linuxhobox on 2011-03-12
> **mr_raider said:**
> AMD-v is turned off by default in BIOS.
Sorry, forgot to mention that I already turned it on.
Still, every 64 bit OS I try kernel panics in the guest  64 bit OS during boot.

On a brighter note,  I tried an external microphone/headphone and they both work.

---

### Post by mrprefect on 2011-03-12
> **linuxhobox said:**
> try
```

sudo iwconfig
sudo iwlist wlan0 scan

```
from the command line to make sure its not a Network Manager problem.
the first command should show a wireless interface (wlan0)
the second should do a scan for APs

That is, if you have not already done so.

Here is the results

```

root@garglblaster:~# iwlist
Usage: iwlist [interface] scanning [essid NNN] [last]
              [interface] frequency 
              [interface] channel 
              [interface] bitrate 
              [interface] rate 
              [interface] encryption 
              [interface] keys 
              [interface] power 
              [interface] txpower 
              [interface] retry 
              [interface] ap 
              [interface] accesspoints 
              [interface] peers 
              [interface] event 
              [interface] auth 
              [interface] wpakeys 
              [interface] genie 
              [interface] modulation 

root@garglblaster:~# iwlist wlan0 scan
wlan0     Scan completed :


```

---

### Post by linuxhobox on 2011-03-12
> **mrprefect said:**
> Here is the results

```

root@garglblaster:~# iwlist
Usage: iwlist [interface] scanning [essid NNN] [last]
              [interface] frequency 
              [interface] channel 
              [interface] bitrate 
              [interface] rate 
              [interface] encryption 
              [interface] keys 
              [interface] power 
              [interface] txpower 
              [interface] retry 
              [interface] ap 
              [interface] accesspoints 
              [interface] peers 
              [interface] event 
              [interface] auth 
              [interface] wpakeys 
              [interface] genie 
              [interface] modulation 

root@garglblaster:~# iwlist wlan0 scan
wlan0     Scan completed :


```

run 'sudo iwconfig wlan0'
You definitely aren't seeing anything on the scan.
So, network manager isn't the culprit.

also try:
```

lspci -k | grep r8192ce_pci

```

you should see

```

    Kernel modules: r8192ce_pc

```

Then run
```

#lspci -vvnn | grep -i real
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 03)
04:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:8176] (rev 01)
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:8195]

```

---

### Post by linuxhobox on 2011-03-12
> **linuxhobox said:**
> Has anyone successfully booted a 64 bit guest OS in VirtualBox?

I've got a kernel panic on ubnuntu 64 bit and freebsd 64bit.

I've still got win 7 on my spare hard disc.  I'm thinking I'll check and make sure it is not a hardware thing.

Update: windows 7 64 bit also bluescreens on ubuntu 64 host.

Update2: Qemu/kvm freezes

If anyone has a windows partitiion w/ XP Mode, could you try and run it to see if amd-v is working.

EDIT: AMD-V has been enabled in bios.

Looks like this is a major problem 64 Bit Guests also panic under windows.
32 bit does work fine.

I'm going to try vmware next.

I don't have win 7 professional and don't feel like installing.
Could someone try XP mode?

---

### Post by dfmutz on 2011-03-12
Has anyone been able to get the unity interface functioning in maverick? After installing the ati drivers per the ati wiki and installing compiz I was finally able to get Unity to load (before it gave me device driver error) but when ever I enter the interface the windows flip upside down. I have checked the fglrxinfo and per the ati install wiki everything is fine. Also, to get rid of the AMD ghost icon, uninstall the drivers maverick lists and follow ati install wiki: [http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide)

Thanks for any help in advance!!!

Specs: x120e, 4gb RAM, E-350 APU, Realtek wifi 8192ce, bluetooth 3.0, maverick installed with Wubi

---

### Post by mogorman on 2011-03-12
Hi I just wanted to say that you do not need windows to enable bluetooth.  I upgraded my system to the 2.6.37 kernel in debian and in doing so upgraded to latest thinkpad_acpi which supports this laptop and was able to get bluetooth enabled using it.  Unfortunately doing so mest up the sound so that i have no headphone jack and still no microphone input.   Oh well getting closer to having it all working.

---

### Post by dfmutz on 2011-03-12
Also FYI, if you install the realtek drivers after a fresh install without using system update first, the drivers are lost and have to be reinstalled. If anyone knows what cuases this or how to fix it, I would greatly appreciate it.

---

### Post by linuxhobox on 2011-03-12
> **dfmutz said:**
> Also FYI, if you install the realtek drivers after a fresh install without using system update first, the drivers are lost and have to be reinstalled. If anyone knows what cuases this or how to fix it, I would greatly appreciate it.

Just a guess.
The kernel may have been updated and since the driver was compiled manually, no module will exist for the new kernel.  I suppose someone could set up dkms.

---

### Post by linuxhobox on 2011-03-12
> **mogorman said:**
> Hi I just wanted to say that you do not need windows to enable bluetooth.  I upgraded my system to the 2.6.37 kernel in debian and in doing so upgraded to latest thinkpad_acpi which supports this laptop and was able to get bluetooth enabled using it.  Unfortunately doing so mest up the sound so that i have no headphone jack and still no microphone input.   Oh well getting closer to having it all working.

Did you try compiling an alsa update for the new kernel?

Is fglrx working w/ 2.6.37?

---

### Post by linuxhobox on 2011-03-12
> **linuxhobox said:**
> Looks like this is a major problem 64 Bit Guests also panic under windows.
32 bit does work fine.

I'm going to try vmware next.

I don't have win 7 professional and don't feel like installing.
Could someone try XP mode?

VMWare workstation looks like it is installing win 7 64 Ent now on windows.

Hopefully, this is a virtualbox/qemu problem and not harware.

On to vmware/linux 64 host next. (if this works)

UPDATE:

[LIST]
[*]  VMWare Workstation 7.1 Win64 Host / Win 64 Guest Installs and Runs
[*]VMWare WS 7.1 Win64 Host / Ubuntu 64
[/LIST]
Time to power off and try Ubuntu 10.04 AMD64 host.

Update2:

[LIST]
[*]VMWare booted Natty 64bit on maverick host
[*]VMWare WS 71 + Win 7 64 guest + Maverick host == success
[*]VMWare WS 7.1 + Maverick 64 guest + Maverick host == success
[/LIST]
So, looks like VMWare is the way to go for 64 bit guest OSes.

Update3:
VBox for 32bit seems to play nice with VMware for 64bit guests

---

### Post by mrprefect on 2011-03-12
> **linuxhobox said:**
> run 'sudo iwconfig wlan0'
You definitely aren't seeing anything on the scan.
So, network manager isn't the culprit.

also try:
```

lspci -k | grep r8192ce_pci

```

you should see

```

    Kernel modules: r8192ce_pc

```

Then run
```

#lspci -vvnn | grep -i real
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 03)
04:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:8176] (rev 01)
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:8195]

```


Well I had already looked at all the things suggested here, I don't often post unless I'm really stuck.

The problem is actually hardware, this morning while I was trying to get this working suddenly 1/4 of the keyboard stopped working, enter, delete, and several other keys. Has to be hardware so I grabbed another x120e (I bought 3 for work) and threw the HDD in this one and everything is working...

I guess just be careful the quality might not be there on all these units. On the broken unit I also saw a few other things missing, like the HDD was not screwed in just slid in the slot. So I think this one shouldn't have made it through QC.

Thanks for everyones help.

---

### Post by linuxhobox on 2011-03-12
> **mrprefect said:**
> Well I had already looked at all the things suggested here, I don't often post unless I'm really stuck.

The problem is actually hardware, this morning while I was trying to get this working suddenly 1/4 of the keyboard stopped working, enter, delete, and several other keys. Has to be hardware so I grabbed another x120e (I bought 3 for work) and threw the HDD in this one and everything is working...

I guess just be careful the quality might not be there on all these units. On the broken unit I also saw a few other things missing, like the HDD was not screwed in just slid in the slot. So I think this one shouldn't have made it through QC.

Thanks for everyones help.
Just thought I would suggest.
90% of my wireless problems on ubuntu end up being network manager.

That sucks.
Mine had everything screwed in and with the exception of the wireless antenna seaming crimped to the card and the second stick of ram installing very tight.
Virtualbox kernel panicking AMD64 guests is also a bit odd but I got VMWare working.

Send it back and make lenovo eat the shipping!

Kernel Oops w/ natty info --> [http://www.linux-archive.org/ubuntu-kernel-team/497999-natty-kernel-oops-3-6-build-iso-amd64-x120e.html](http://www.linux-archive.org/ubuntu-kernel-team/497999-natty-kernel-oops-3-6-build-iso-amd64-x120e.html)

---

### Post by quantumkit on 2011-03-12
anyone get the webcam working with Skype? it just keeps crashing when I test the webcam in skype option.

---

### Post by dfmutz on 2011-03-12
Have you upgraded the asla as per linuxhobo's post on page 5. I didn't try before it but I know it works after doing that.

---

### Post by dfmutz on 2011-03-12
also for anyone else that likes using track point over touch pad, install GPointingDevices and follow this guide, FYI the button for vertical scrolling is 2 not 4 like it defaults to.

---

### Post by quantumkit on 2011-03-12
> **dfmutz said:**
> Have you upgraded the asla as per linuxhobo's post on page 5. I didn't try before it but I know it works after doing that.

ya...I did.

The microphone works. The webcam worked on other software, e.g. cheese webcam booth. But Skype still crashes w/webcam. FYI, I'm 10.10

---

### Post by mr_raider on 2011-03-12
> **dfmutz said:**
> also for anyone else that likes using track point over touch pad, install GPointingDevices and follow this guide, FYI the button for vertical scrolling is 2 not 4 like it defaults to.

what guide?

---

### Post by mr_raider on 2011-03-12
> **quantumkit said:**
> anyone get the webcam working with Skype? it just keeps crashing when I test the webcam in skype option.

works for me. What's your kernel?

---

### Post by dfmutz on 2011-03-12
odd, are you using i386 or x64 architecture?

---

### Post by mr_raider on 2011-03-12
> **dfmutz said:**
> odd, are you using i386 or x64 architecture?

x64

---

### Post by dfmutz on 2011-03-12
I have x64 installed too of ubuntu 10.10 and have no trouble having skype see my webcam. Do you receive any error messages?

---

### Post by tacit1 on 2011-03-13
Got an X120e running 10.10 Maverick.

Ergonomics are great; keyboard is **flawless**, touchpad is very sensitive with excellent travel on the left and right buttons, and trackpoint scroll is awesome.

The chassis is very well built with no creaking and minimal flex. I love the protruding battery as it provides an excellent hold and balance point while standing.  I don't understand the common bias against the protruding battery in reviews, as it just adds to the ergonomics and makes this device truly portable.

With kernel 2.6.35-27-generic the fan stays on.  It's not distracting as it emits a very soft sound that can be easily tuned out.  I am hopeful that in the future we can combine temperature monitoring, CPU throttling, and fan control.

The screen was a very sore point when I first installed Ubuntu, but with some tweaks in Catalyst it looks great.  

I have the following color/brightness settings in Catalyst to make the LCD look more crisp:

Green: 0.95
Red: 0.67
Blue: 0.86

Brightness: 0
Contrast: 79
Saturation: 72
Hue: 0

The Fn+F7 key combination works to toggle the display from internal to external.

I am getting an occasional display crash with kernel 2.6.35-27-generic & Catalyst 11.2 which disables everything including TTY switching.  I was able to determine this as a display problem as I was running the X120e as a Samba server and after losing control I was still able to upload, rename, and move files on the X120e.

There are some major performance improvements coming in 2.6.38 [Phoronix: The Direction Of ATI Radeon Graphics In Ubuntu 11.04]("http://www.phoronix.com/scan.php?page=article&item=ubuntu_1104_radeon&num=1") with the open-source ATI driver so I hope that fixes the crash and enables one to make the necessary color/performance tweaks available with Catalyst 11.2.

Bluetooth, wireless, and graphics did not work properly out of the box.  Installing the rtl8192ce_linux_2.6.0005.1116.2010 driver from the realtek site worked just fine.  Note it is the **CE**, not the SE driver that you want.  I have added ```
insmod /lib/firmware/r8192ce_pci.ko
``` to ```
/etc/rc.local
``` for automatic loading.

For some reason I cannot bind CTRL-ALT-SHIFT-UP to move windows (up) between workspaces using the Gnome keyboard shortcuts.  Can anyone confirm this?

---

### Post by linuxhobox on 2011-03-13
> **quantumkit said:**
> ya...I did.

The microphone works. The webcam worked on other software, e.g. cheese webcam booth. But Skype still crashes w/webcam. FYI, I'm 10.10

I installed on the command line w/ natty and a virtual and wound up with broken dependencies that I needed to fix.  After that it ran great.  You could try checking to make sure you don't have any broken packages in synaptics  (it's under the edit menu).

I usually push skype out to a virtual since I don't like a distributed server farm node running on a portable laptop.

On another note, looks like fglrx for natty should hit in the next week or so --> [http://www.clubdoconline.com/news/press-release/amd-catalyst-11-3-driver-to-release-fixing-11-2-grapchics-freezing-issues/](http://www.clubdoconline.com/news/press-release/amd-catalyst-11-3-driver-to-release-fixing-11-2-grapchics-freezing-issues/)

---

### Post by dfmutz on 2011-03-13
Is anyone else having issues with adobe flash or have a better alternative for 10.10 x64? Mine is real buggy and there is no audio and I know my audio works fine. Thanks for the help guys.

---

### Post by link141 on 2011-03-13
I have almost everything working on my thinkpad thanks to linuxhobox and the other people on this thread.  I installed Kubuntu 10.10 via SD card as netboot is extremely difficult to get working with the router I have.

[SIZE="3"]What works:[/SIZE]
B/G/N Wireless: using self-compiled proprietary drivers. Using command-line utilities as Network-manager will drop connection every 5-10 minutes.
Graphics: Downloaded and installed latest catalyst driver following help.ubuntu.com howto. 3D works really well.
Sound (w/ headphone 'sense' and microphone): Updated alsa using script referred to on page 5
Trackpoint Scrolling: Instructions can be found on thinkwiki
Touchpad works out of box
All FN+ keys I tested (sound control, media player controls, brightness) work out of box
SD Card reader: Works out of box
Webcam: Works out of box as V4L2 device (can be set to all resolutions from 1280x720 to 160x120 in cheese)
Sleep Mode: Started working.  I'll have to test every scenario with the wireless to see if this interferes with suspend.

[SIZE="3"]Not tested[/SIZE]
Hibernate
HDMI Video and Audio (There is an entry for the Audio in the sound mixer)

I'll give more info and perhaps compile everything in this thread into a howto for people just getting their x120e now (and for future reference) when my school work subsides.

All in all, Linux is working really well on this machine.  If anyone needs help or wants any specific info, feel free to ask.

Link141

---

### Post by link141 on 2011-03-13
> **dfmutz said:**
> Is anyone else having issues with adobe flash or have a better alternative for 10.10 x64? Mine is real buggy and there is no audio and I know my audio works fine. Thanks for the help guys.

I installed flash on Kubuntu 10.10 64-bit from the repos (a dialog popped up and asked me if I wanted to install it).  It seems to be working quite well on my machine (although it currently isn't using hardware acceleration), and the audio quality for me is really good.  Did you update alsa?

---

### Post by dfmutz on 2011-03-13
I have done the update like linuxhobo posted and I originally had the flash square installed for x64 and later uninstalled it and used the one from the repos with the same issue of laggy playback and no audio. I have tested the playback with rhythmbox and skype with no issues. I think the lag is the issue in flash but not 100% sure either.

---

### Post by linuxhobox on 2011-03-13
> **dfmutz said:**
> I have done the update like linuxhobo posted and I originally had the flash square installed for x64 and later uninstalled it and used the one from the repos with the same issue of laggy playback and no audio. I have tested the playback with rhythmbox and skype with no issues. I think the lag is the issue in flash but not 100% sure either.
Flash w/ amazon instant video and hulu with HDMI out.
I watched one movie on each.
I haven't tested since updating alsa.

---

### Post by skomra on 2011-03-13
> **link141 said:**
> 
[SIZE="3"]What Doesn't[/SIZE]
Sleep Mode: Almost works, but doesn't wake up properly.


This is my first laptop so I'm a totally inexperienced in this regard. I'm having a sleep problem too, where if I leave it for a while on battery and come back the sleep light is blinking and I'm forced to restart.

I never booted it into windows so I don't know what the expected behavior is. If sleep worked properly what would wake up the machine? Just pressing any key?

I'm not really concerned with if sleep works or not I just don't want to have to keep rebooting the machine. Is there a setting to disable sleep? I looked at gnome-power-manager settings but nothing there jumped out at me.

---

### Post by link141 on 2011-03-13
> **skomra said:**
> This is my first laptop so I'm a totally inexperienced in this regard. I'm having a sleep problem too, where if I leave it for a while on battery and come back the sleep light is blinking and I'm forced to restart.

I never booted it into windows so I don't know what the expected behavior is. If sleep worked properly what would wake up the machine? Just pressing any key?

I'm not really concerned with if sleep works or not I just don't want to have to keep rebooting the machine. Is there a setting to disable sleep? I looked at gnome-power-manager settings but nothing there jumped out at me.

On windows, the sleep light turns on as a solid green when the laptop goes into sleep mode.  On Kubuntu, it does the same thing, but doesn't wake up correctly.  I think this might be a driver issue, but I have yet to troubleshoot it.

I don't use gnome, but I'm sure you can disable sleep when the lid is closed.  Try right clicking the battery icon and looking for 'When laptop lid is closed' in the dialog.

---

### Post by linuxhobox on 2011-03-14
> **link141 said:**
> On windows, the sleep light turns on as a solid when the laptop goes into sleep mode.  On Kubuntu, it does the same thing, but doesn't wake up correctly.  I think this might be a driver issue, but I have yet to troubleshoot it.

I don't use gnome, but I'm sure you can disable sleep when the lid is closed.  Try right clicking the battery icon and looking for 'When laptop lid is closed' in the dialog.

I've had the laptop for more than a week now and suspend (sleep) has never locked it up.  I usually press the power button to wake up. 

 Hibernate has always locked up.

I haven't tried Kubuntu only Gnome.

I've loaded both Natty and Maverick w/ same results.

Do you guys have the broadcom card or WAN?

---

### Post by skomra on 2011-03-14
link141 - thanks! 
linuxhobox - Thanks very much for your posts here, they got me up and running!
> **linuxhobox said:**
> 
Do you guys have the broadcom card or WAN?

No broadcom or WAN here. If I do a suspend from the off button menu, I can return from that. I just can't return from the state that the power management labels as sleep ("Put computer to sleep when inactive for ..0:10")

Here's a video of the blinking light!:
  [http://vimeo.com/21007095]("http://vimeo.com/21007095")

	      0A71928  	VBB AMD FUSION PRCS E-350	 	 	 	 
 	      45M3092  	VBB GENWIN7HOMEPREM64	 	 	 	 
 	      0A59607  	SBB GEN WIN7 HOME PRM64 US EN	 	 	 	 
 	      0A59514  	SBB 11.6HD ANTGLR-MIDNIGHTBLCK	 	 	 	 
 	      0A59521  	SBB AMD RDNHD6310GRPFSNPRE-350	 	 	 	 
 	      45M4569  	VBB 2GBPC3-10600DDR3 1333SODMM	 	 	 	 
 	      60Y6217  	SBB KEYBOARD US ENGLISH	 	 	 	 
 	      0A59527  	SBB 250GB HRDDSK DRVE,5400RPM	 	 	 	 
 	      60Y6210  	SBB 6 CELL LI-ION BAT2.6 AH	 	 	 	 
 	      41W1787  	SBB CPK NORTH AMERICA	 	 	 	 
 	      75Y1724  	SBB THINKPADB/G/N	 	 	 	 
 	      44C7950  	SBB INT WRLSSWDAREANTWRK UPGR

---

### Post by linuxhobox on 2011-03-14
> **skomra said:**
> 
No broadcom or WAN here. If I do a suspend from the off button menu, I can return from that. I just can't return from the state that the power management labels as sleep ("Put computer to sleep when inactive for ..0:10")


Looking at the gnome power management site -->[http://projects.gnome.org/gnome-power-manager/](http://projects.gnome.org/gnome-power-manager/)

They list various kinds of sleep.  From site:

```

 And they support various actions to match users needs: 
 
[LIST]
[*]Sleep to RAM (Suspend)
[*]**[COLOR=Red]Sleep to Disk (Hibernate)[/COLOR]**
[*]Shutdown
[*]Blank screen
[/LIST]

```Maybe, the computer is hibernating.  Since hibernation doesn't work, the laptop would lock up.  This isn't the default behavior for gnome power management.

But launching gconf-editor. I see this:
```

/apps/gnome-power-manager/actions/sleep_type_battery = hibernate

```The valid values are:
```

The type of sleeping that should be performed when the computer is inactive.
 Possible values are "hibernate", "suspend" and "nothing".

```Try changing this to suspend and see if that helps.

I'll try and test this later.

KDE powerdevil information is here --> [http://docs.kde.org/stable/en/kdebase-workspace/kcontrol/powerdevil/index.html](http://docs.kde.org/stable/en/kdebase-workspace/kcontrol/powerdevil/index.html)

---

### Post by link141 on 2011-03-14
> **linuxhobox said:**
> Do you guys have the broadcom card or WAN?

I went with the 802.11 B/G/N pci_e card (realtek) -- I think most people that bought this laptop probably did.  I didn't get mobile broadband or bluetooth with my machine.

Sleep mode is now working for me. I unloaded the wireless module and tried sleep mode again three times, and it woke up correctly (and very quickly) all three times.  When I loaded the module back into the kernel, sleep mode still worked correctly.  I think the suspend problems I was having may have only occured when the wireless was connected to a network, but I still have to test this...

Now I just have to stop playing with this thing and put myself into sleep mode :p.

---

### Post by link141 on 2011-03-14
Here is a great link with instructions for configuring the trackpoint at [_think wiki_](http://www.thinkwiki.org/wiki/How_to_configure_the_TrackPoint).

[SIZE="3"]Enable Vertical scrolling:[/SIZE]
Type the following into the terminal (from thinkwiki):
```
xinput set-int-prop 12 "Evdev Wheel Emulation" 8 1
xinput set-int-prop 12 "Evdev Wheel Emulation Button" 8 2
xinput set-int-prop 12 "Evdev Wheel Emulation Timeout" 8 200
```
Ubuntu uses the .xsessionrc in your home directory to "remember" these settings after a reboot.

[SIZE="3"]Set sensitivity and speed of trackpoint on any recent linux os:[/SIZE]
NOTE: The path to the files that set these parameters is different on the x120e than it is on older thinkpads (I think it is serio4/serio5 -- I'll have to double check the paths when I get home). Also, you first have to make the files writable by *other* users.
```
sudo chmod o+w /sys/devices/platform/i8042/serio4/serio5/speed
sudo chmod o+w /sys/devices/platform/i8042/serio4/serio5/sensitivity
echo -n 120 > /sys/devices/platform/i8042/serio4/serio5/speed 
echo -n 250 > /sys/devices/platform/i8042/serio4/serio5/sensitivity
```
120 and 250 can be any numbers you like from 0 to 255 (inclusive).

For more info, check out the link to thinkwiki.

---

### Post by linuxhobox on 2011-03-14
On my first install, I was always having pm-utils unload the modules.

Doesn't look like I'm doing it this time.

EDIT:This works
create file 12_remove_wifi
in directory /etc/pm/sleep.d
```

#!/bin/bash
case $1 in
    hibernate)
        rmmod r8192ce_pci
        ;;
    suspend)
    rmmod r8192ce_pci
    ;;
    thaw)
        modprobe r8192ce_pci
        ;;
    resume)
    modprobe ath_pci
        modprobe r8192ce_pci
    ;;
    *)  echo "somebody is calling me totally wrong."
        ;;
esac

```

The other soolution froze my system.

Hmmm, mybe I'll take another look at hibernate.


EDIT: The information below is useful but doesn't work.
SUSPEND_MODULES must also be set eleswhere
For those who want to have the modules unload see here -->[https://wiki.archlinux.org/index.php/Pm-utils#Advanced_Configuration](https://wiki.archlinux.org/index.php/Pm-utils#Advanced_Configuration)

and add the module name 'r8192ce_pci' to 'SUSPEND_MODULES'

I should probably do this also since it cuts down on wireless problems.

/etc/pm/config.d/module file with ontents:
```

SUSPEND_MODULES="r8192ce_pci"

```i

someone please speak up if ubuntu defines this somewhere else

---

### Post by estebanko on 2011-03-14
I'm having intermittent microphone issues. Whenever I start apps that use microphone like Skype, Google Voice Chat, microphone stops working. That is when you open Sound Preference, before opening the apps, you can see microphone indicator moving but after starting the apps indicator no longer moves. 

I have ran Alsa update script per linuxhobox suggestion and changed alsa.conf. 

Interestingly, once it stops working, suspending and waking it backup gets it going again. :)

Has anyone seen flaky microphone issues? 

Thanks,
Stephen

---

### Post by Zak Smith on 2011-03-14
For background, my "old" laptop is a IBM Z61t (14.1" WXGA+, 2GB), which has been running Ubuntu since I got it in 2006 (started wit 6.06 LTS maybe?).

My x120e showed up last Wednesday.  I installed 10.10 Desktop 32-bit.    I had to install the Realtek drivers which worked without drama.  Getting the video to work was more complicated.  *Do not* install the proprietary driver via Ubuntu.  It will work OK but the "watermark" is present.  To get the 11.2 Catalyst driver from AMD to install properly, you will first have to totally uninstall any of the Ubuntu-supplied Radeon components, which is a pain.    Until I installed the 11.2 video driver, it would not resume from suspend.  With the new version, it suspends/resumes fine.  

I have not debugged hibernate, but a couple tests indicates it doesn't work for me.

Sound worked from the box.  Did not test mic or camera.

I replaced the factory HDD with an Intel 510 series SSD (120GB).  This thing is blindingly fast.  Boot times seem like they are less than 10 seconds from the power button to the keychain-manager password prompt-- but I haven't actually timed it.

Using thinkpad_acpi, the fan control works; however, the fan speed reported is bogus. Setting the fan speed to 7 (fast) actually reports a slower speed than 1 (default/slow).

Average reported CPU temperature is 50-53 degrees.  On my old Z61t, it's typically 45.  The fan does run at low speed most of the time. This isn't a big deal, but if you put your ear up to it, it is moving and there's the faint fan sound.   I will probably write a control program to set a duty cycle on the fan so it doesn't have to spin all the time.

I did have a problem with the x120e, though.  After working perfectly and quietly for several days, the fan started to make scraping/vibrating noises on Sunday morning.  It sounds like it's either rubbing something or the bearings or spindle is going bad.  It sounds like a tiny little diesel engine is idling in there, not cool.   I called Lenovo and they're going to replace the fan, which means it'll be out of commission for a few weeks.  Bummer, but overall I am impressed with the machine.

---

### Post by skomra on 2011-03-14
> **linuxhobox said:**
> 
/apps/gnome-power-manager/actions/sleep_type_battery = hibernate


Changing that to suspend did it! Thanks!

---

### Post by linuxhobox on 2011-03-14
> **estebanko said:**
> I'm having intermittent microphone issues. Whenever I start apps that use microphone like Skype, Google Voice Chat, microphone stops working. That is when you open Sound Preference, before opening the apps, you can see microphone indicator moving but after starting the apps indicator no longer moves. 

I have ran Alsa update script per linuxhobox suggestion and changed alsa.conf. 

Interestingly, once it stops working, suspending and waking it backup gets it going again. :)

Has anyone seen flaky microphone issues? 

Thanks,
Stephen

Did you reinstall pulseaudio?

The same thing was happening to me since pulse was not properly configured as the default audio device.  Reinstalled and it worked fine.

---

### Post by estebanko on 2011-03-15
> **linuxhobox said:**
> Did you reinstall pulseaudio?

The same thing was happening to me since pulse was not properly configured as the default audio device.  Reinstalled and it worked fine.

I'm not having much luck with following. Did you use: 

sudo apt-get --reinstall install pulseaudio

to reinstall pulseaudio?

---

### Post by quantumkit on 2011-03-15
The skype/gtalk crashes with webcam is finally solved by reinstalling AMD Catalyst driver :D

---

### Post by linuxhobox on 2011-03-15
> **estebanko said:**
> I'm not having much luck with following. Did you use: 

sudo apt-get --reinstall install pulseaudio

to reinstall pulseaudio?
I used Synaptic to do it but command line should have worked.
Must be something else.
CHeck /usr/share/alsa/pulse-alsa.conf to see if pulse is being set as the default sound card.

Found this link on how to enable bluetooth with kernel 2.6.38 and thinkpad_acpi kernel module
link --> [https://wiki.archlinux.org/index.php/IBM_ThinkPad_X120e](https://wiki.archlinux.org/index.php/IBM_ThinkPad_X120e)
```

echo "disable" > /proc/acpi/ibm/bluetooth

```

---

### Post by thinkpadx on 2011-03-15
First off, I'd like to say thanks for all the information in this thread.  It's helped me out a lot.

I've spent the last few days trying to get natty up and running and successfully got everything working with the 2.6.38-6 kernel. I noticed something interesting and thought I would get everyones opinion. 

```

thinkpadx@pong:~$ uname -a
Linux pong 2.6.38-6-generic #34-Ubuntu SMP Tue Mar 8 14:15:57 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
thinkpadx@pong:~$ cat /proc/cpuinfo 
processor    : 0
vendor_id    : AuthenticAMD
cpu family    : 20
model        : 1
model name    : AMD E-350 Processor
stepping    : 0
cpu MHz        : 800.000
cache size    : 512 KB
physical id    : 0
siblings    : 2
core id        : 0
cpu cores    : 2
apicid        : 0
initial apicid    : 0
fpu        : yes
fpu_exception    : yes
cpuid level    : 6
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf pni monitor ssse3 cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch ibs skinit wdt npt lbrv svm_lock nrip_save pausefilter
bogomips    : 3193.70
TLB size    : 1024 4K pages
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate

processor    : 1
vendor_id    : AuthenticAMD
cpu family    : 20
model        : 1
model name    : AMD E-350 Processor
stepping    : 0
cpu MHz        : 800.000
cache size    : 512 KB
physical id    : 0
siblings    : 2
core id        : 1
cpu cores    : 2
apicid        : 1
initial apicid    : 1
fpu        : yes
fpu_exception    : yes
cpuid level    : 6
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf pni monitor ssse3 cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch ibs skinit wdt npt lbrv svm_lock nrip_save pausefilter
bogomips    : 3193.22
TLB size    : 1024 4K pages
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate

```
Am I correct in saying the kernel thinks the CPUs are clocked at 800MHz?

---

### Post by Zak Smith on 2011-03-15
/proc/cpuinfo reports the *current* cpu speed, so it's normal.

---

### Post by thinkpadx on 2011-03-15
Oh, I should've known that.  Thanks for your quick response!

I have one more question,  is there an ETA on when the Catalyst drivers will support the latest Xorg server?  I've done some minor googling and haven't come up with much.

---

### Post by Zak Smith on 2011-03-15
> **thinkpadx said:**
> Oh, I should've known that.  Thanks for your quick response!

I have one more question,  is there an ETA on when the Catalyst drivers will support the latest Xorg server?  I've done some minor googling and haven't come up with much.

Catalyst 11.2 works, see my comments in this post in the prior page of this thread
[http://ubuntuforums.org/showthread.php?p=10560027#post10560027](http://ubuntuforums.org/showthread.php?p=10560027#post10560027)
This link has some helpful info (and some bad info - the .deb install flow does not work)
[http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide)

The trick to getting the AMD-provided 11.2 script to work is that all the Radeon related drivers (from Ubuntu or otherwise) must be removed before you run their installer.

---

### Post by tibman on 2011-03-15
I just got the thinkpad x120e and I am trying to install the standard Ubuntu 10.10 x64 but the installer keeps crashing. Anyone else have the same issue or tried x64?

---

### Post by mr_raider on 2011-03-15
> **tibman said:**
> I just got the thinkpad x120e and I am trying to install the standard Ubuntu 10.10 x64 but the installer keeps crashing. Anyone else have the same issue or tried x64?

Are you trung to install directly of from within the live CD.

---

### Post by tibman on 2011-03-15
> **mr_raider said:**
> Are you trung to install directly of from within the live CD.

Yes, I used the latest "Universal-USB-Installer" to put Ubuntu 10.10 x64 on a 4 gig USB. Loaded fine, all the features work well, but it locks up on install every time. I even downloaded another copy, didn't fix it. 

Anyone have any ideas?

---

### Post by linuxhobox on 2011-03-16
> **Zak Smith said:**
> Catalyst 11.2 works, see my comments in this post in the prior page of this thread
[http://ubuntuforums.org/showthread.php?p=10560027#post10560027](http://ubuntuforums.org/showthread.php?p=10560027#post10560027)
This link has some helpful info (and some bad info - the .deb install flow does not work)
[http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide)

The trick to getting the AMD-provided 11.2 script to work is that all the Radeon related drivers (from Ubuntu or otherwise) must be removed before you run their installer.
I don't think fglrx 11.2 will work with natty's xorg server it is too new.  The 11.4 preview is out for windows and linux should follow by the time of natty's official release (there was a link earlier in this thread).

Or were you able to patch 11.2 for Natty?

---

### Post by linuxhobox on 2011-03-16
> **tibman said:**
> Yes, I used the latest "Universal-USB-Installer" to put Ubuntu 10.10 x64 on a 4 gig USB. Loaded fine, all the features work well, but it locks up on install every time. I even downloaded another copy, didn't fix it. 

Anyone have any ideas?

Try a text based install.  It is easier to see what is breaking.  Just switch consoles (alt+ctrl+f[1-7]).

.

---

### Post by tibman on 2011-03-16
> **linuxhobox said:**
> Try a text based install.  It is easier to see what is breaking.  Just switch consoles (alt+ctrl+f[1-7]).

.
I have been able to do a text install via ubuntu alternative live cd but when I load that to a usb, the install keeps asking me to insert the ubuntu disk. 
How can I do a text based install_ (q mark is not working from the live cd

---

### Post by fignew on 2011-03-16
> **linuxhobox said:**
> 
Found this link on how to enable bluetooth with kernel 2.6.38 and thinkpad_acpi kernel module
link --> [https://wiki.archlinux.org/index.php/IBM_ThinkPad_X120e](https://wiki.archlinux.org/index.php/IBM_ThinkPad_X120e)
```

echo "disable" > /proc/acpi/ibm/bluetooth

```

Hey there.
I've updated the Archlinux wiki with some more goodies.

My X120e is running Arch pretty much perfectly. Looking forward to seeing how much the CPU can be undervolted when the utilities start supporting Fusion processors. :popcorn:

---

### Post by mr_raider on 2011-03-16
> **tibman said:**
> Yes, I used the latest "Universal-USB-Installer" to put Ubuntu 10.10 x64 on a 4 gig USB. Loaded fine, all the features work well, but it locks up on install every time. I even downloaded another copy, didn't fix it. 

Anyone have any ideas?

Where/when does it lock up?

---

### Post by removesstains on 2011-03-16
I got pretty much everything working in mine. I'm actually running Linux Mint 10 64-bit. so its basically Ubuntu 10.10. 

i love this little beast. i added a ssd and a 4gb stick of ram so i'm at 6gb total. This thing flys, it boots up crazy fast and i haven't tweaked any of the boot settings yet. 

I installed the Catalyst 11.2 no problem. suspend worked no problems either. What i need to do is find a good how-to on getting the GPU acceleration to work properly. I'm still having screen tearing on 720p youtube streams, even when i turned the option on in the ATI settings. Does any one have a link to a easy to follow how-to on getting the GPU acceleration set up? 

below is the links i used to get things working. 

Broadcom drivers (i have the a/b/g/n card in mine, i followed the readme to install it, make sure you do this 1st.)

[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

Graphics driver

[http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide)

Sound fix (headphones, mic’s, reinstall pulse audio when done. i reinstalled it in the synaptic manager)

[http://ubuntuforums.org/showthread.php?t=1681577](http://ubuntuforums.org/showthread.php?t=1681577)

---

### Post by tibman on 2011-03-16
> **mr_raider said:**
> Where/when does it lock up?

I load up the live image, click install, go past the first page asking for language and the second page that verifies "power source, internet connection, ect" I click forward and it just hangs. A few seconds later I see an application problem pop up in the top bar, it reads "sorry, the program "parted_server" closed unexpectedly". For some reason it is also unable to report the problem.....

I can't stand windows on this netbook..... Why do you torture me Ubuntu! 

I would use the x86 version but I just installed 4 gig's of ram and would like to utilize it all.

---

### Post by tibman on 2011-03-16
> **tibman said:**
> I load up the live image, click install, go past the first page asking for language and the second page that verifies "power source, internet connection, ect" I click forward and it just hangs. A few seconds later I see an application problem pop up in the top bar, it reads "sorry, the program "parted_server" closed unexpectedly". For some reason it is also unable to report the problem.....

I can't stand windows on this netbook..... Why do you torture me Ubuntu! 

I would use the x86 version but I just installed 4 gig's of ram and would like to utilize it all.


I found the culprit, Mark this solved: Universal USB Installer please jump off a bridge.
This is not the first time I have had this problem, but I never knew what caused it in the past, it just worked on some computers and not on others. I used "Startup disk creator" to create my live USB and it installed in less than 15 min. Let it be known.

---

### Post by tibman on 2011-03-16
> **tacit1 said:**
> Got an X120e running 10.10 Maverick.

Ergonomics are great; keyboard is **flawless**, touchpad is very sensitive with excellent travel on the left and right buttons, and trackpoint scroll is awesome.

The chassis is very well built with no creaking and minimal flex. I love the protruding battery as it provides an excellent hold and balance point while standing.  I don't understand the common bias against the protruding battery in reviews, as it just adds to the ergonomics and makes this device truly portable.

With kernel 2.6.35-27-generic the fan stays on.  It's not distracting as it emits a very soft sound that can be easily tuned out.  I am hopeful that in the future we can combine temperature monitoring, CPU throttling, and fan control.

The screen was a very sore point when I first installed Ubuntu, but with some tweaks in Catalyst it looks great.  

I have the following color/brightness settings in Catalyst to make the LCD look more crisp:

Green: 0.95
Red: 0.67
Blue: 0.86

Brightness: 0
Contrast: 79
Saturation: 72
Hue: 0

The Fn+F7 key combination works to toggle the display from internal to external.

I am getting an occasional display crash with kernel 2.6.35-27-generic & Catalyst 11.2 which disables everything including TTY switching.  I was able to determine this as a display problem as I was running the X120e as a Samba server and after losing control I was still able to upload, rename, and move files on the X120e.

There are some major performance improvements coming in 2.6.38 [Phoronix: The Direction Of ATI Radeon Graphics In Ubuntu 11.04]("http://www.phoronix.com/scan.php?page=article&item=ubuntu_1104_radeon&num=1") with the open-source ATI driver so I hope that fixes the crash and enables one to make the necessary color/performance tweaks available with Catalyst 11.2.

Bluetooth, wireless, and graphics did not work properly out of the box.  Installing the rtl8192ce_linux_2.6.0005.1116.2010 driver from the realtek site worked just fine.  Note it is the **CE**, not the SE driver that you want.  I have added ```
insmod /lib/firmware/r8192ce_pci.ko
``` to ```
/etc/rc.local
``` for automatic loading.

For some reason I cannot bind CTRL-ALT-SHIFT-UP to move windows (up) between workspaces using the Gnome keyboard shortcuts.  Can anyone confirm this?


I am somewhat of a beginner, is there an easier way to install the drivers for the realtek wireless card?? now I wish I paid a little extra to get the broadcom card...

Of course it didn't mention who made which card when I customised this netbook...

---

### Post by CPCollin on 2011-03-16
> **tibman said:**
> I am somewhat of a beginner, is there an easier way to install the drivers for the realtek wireless card?? now I wish I paid a little extra to get the broadcom card...

Of course it didn't mention who made which card when I customised this netbook...

The realtek driver for the [SIZE=1]RTL8192ce card has been added to [/SIZE]2.6.38-1.27, fixed in Natty.

If you look at this LP bug [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/686333](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/686333) you can see some people packaged as a PPA for easy installing. Just look up how to add a ppa or use 11.04 beta.

---

### Post by mr_raider on 2011-03-16
> **removesstains said:**
>  

I installed the Catalyst 11.2 no problem. suspend worked no problems either. What i need to do is find a good how-to on getting the GPU acceleration to work properly. I'm still having screen tearing on 720p youtube streams, even when i turned the option on in the ATI settings. Does any one have a link to a easy to follow how-to on getting the GPU acceleration set up? 


My understanding is GPU acceleration for flash doesn't work in Linux, only windows.

I can get GPU acceleration to work in VLC using VA-API though.

---

### Post by link141 on 2011-03-17
> **mr_raider said:**
> My understanding is GPU acceleration for flash doesn't work in Linux, only windows.

I can get GPU acceleration to work in VLC using VA-API though.

I believe the GPU acceleration is enabled in the linux preview release of flash player (codename) 'square'.  However, there is a tick box that says 'enable hardware acceleration in the release in the repositories, but it obviously doesn't do anything.  If I check the video rendering mode on youtube (right click and open a widget), it says 'unknown rendering device' or something to that effect.

I remember installing square on another one of my machines, and all youtube videos were tinged green with the open source ATI drivers.  It'd be interesting to see if hardware acceleration actually works in the preview release...

---

### Post by mr_raider on 2011-03-17
> **link141 said:**
> I believe the GPU acceleration is enabled in the linux preview release of flash player (codename) 'square'.  However, there is a tick box that says 'enable hardware acceleration in the release in the repositories, but it obviously doesn't do anything.  If I check the video rendering mode on youtube (right click and open a widget), it says 'unknown rendering device' or something to that effect.

I remember installing square on another one of my machines, and all youtube videos were tinged green with the open source ATI drivers.  It'd be interesting to see if hardware acceleration actually works in the preview release...

How do you install the square tar.gz?

---

### Post by link141 on 2011-03-17
> **mr_raider said:**
> How do you install the square tar.gz?

I remember it being a pain in the tux to get it functioning :cry:.  I basically had to go through a trial and erro routine of copying and linking the library into a bunch of locations in /usr/lib.  What made it worse was that the file had to have a specific name to get it to work with Firefox.  I eventually got it to work, but I'll have to check exactly what I did when I get home.  Will be getting on a train now...

Good luck.

---

### Post by linuxhobox on 2011-03-17
> **link141 said:**
> I remember it being a pain in the tux to get it functioning :cry:.  I basically had to go through a trial and erro routine of copying and linking the library into a bunch of locations in /usr/lib.  What made it worse was that the file had to have a specific name to get it to work with Firefox.  I eventually got it to work, but I'll have to check exactly what I did when I get home.  Will be getting on a train now...

Good luck.

I usually install per user.

download.tar.gz is achive contaiining plugin
```

mkdir ~/.mozilla/plugins
tar -xzvf download.tar.gz
cp libflashplayer.so ~/.mozilla/plugins

```start firefox

Check to see that plugin was loaded:
```

lsof ~/.mozilla/plugins/libflashplayer.so

```you should see it loaded by firefox-bin

also enter
about : plugins (no spaces -- without spaces becomes emotocon in forums about:plugins)
in the address bar to check that it is working

link --> [http://plugindoc.mozdev.org/linux-amd64.html#flash](http://plugindoc.mozdev.org/linux-amd64.html#flash)

---

### Post by samanthad on 2011-03-21
I got sound to work through my headphones what with running the script to upgrade ALSA to 1.0.24 and then re-adding the line within /usr/share/alsa/alsa.conf and it works. My microphone works and my speakers switch between speakers and headphones.

BUT

The moment I play a flash video with sound my microphone stops working and the computer sticks to whatever it was on when the sound started (speakers or headphones) and refuses to change, even when all applications stop using Pulse. I think it has to do with Flash being an ALSA application.

This is a 64-bit Maverick install with the beta Flash player "square," by the way.

---

### Post by jimmyfergus on 2011-03-21
The hibernate issue is being addressed.  Seems there's a kernel update coming, plus it needs a file added to /etc/pm/config.d with the contents:

```
HIBERNATE_MODE="shutdown"
```

([https://bugs.launchpad.net/null/+bug/737208](https://bugs.launchpad.net/null/+bug/737208))

---

### Post by estebanko on 2011-03-21
> **samanthad said:**
> I got sound to work through my headphones what with running the script to upgrade ALSA to 1.0.24 and then re-adding the line within /usr/share/alsa/alsa.conf and it works. My microphone works and my speakers switch between speakers and headphones.

BUT

The moment I play a flash video with sound my microphone stops working and the computer sticks to whatever it was on when the sound started (speakers or headphones) and refuses to change, even when all applications stop using Pulse. I think it has to do with Flash being an ALSA application.

This is a 64-bit Maverick install with the beta Flash player "square," by the way.

I'm in same boat. Tried reinstalling ALSA with the script but without much luck. After much searching and compiling, I'm waiting for Natty to come out. Everything else is great though :)

---

### Post by omriasta on 2011-03-22
> **quantumkit said:**
> anyone get the webcam working with Skype? it just keeps crashing when I test the webcam in skype option.
Anyone with skype camera issues, make sure you have the following lines inside /usr/bin/skype-wrapper

export XLIB_SKIP_ARGB_VISUALS=1
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so  /usr/bin/skype "$@"

---

### Post by codedivine on 2011-03-22
Hi everyone!

Thanks for all the info everyone has provided so far. Looks like a good machine. I am thinking of buying this. I will be going for E350, Realtek card (only option in Canada) and will install fglrx. 

Can anyone provide any battery life estimates using Ubuntu?

---

### Post by linuxhobox on 2011-03-23
> **codedivine said:**
> Hi everyone!

Thanks for all the info everyone has provided so far. Looks like a good machine. I am thinking of buying this. I will be going for E350, Realtek card (only option in Canada) and will install fglrx. 

Can anyone provide any battery life estimates using Ubuntu?
Varies a bit.
With dimmed screen:

[LIST]
[*]I'm getting 5:30-7.5 hrs moderate usage
[*]Heavy usage 4 to 6
[*]Letting it sleep w/ very light usage I can go 8 to 12 hours (including sleep time).
[/LIST]

---

### Post by samanthad on 2011-03-23
> **codedivine said:**
> Hi everyone!

Thanks for all the info everyone has provided so far. Looks like a good machine. I am thinking of buying this. I will be going for E350, Realtek card (only option in Canada) and will install fglrx. 

Can anyone provide any battery life estimates using Ubuntu?

I get at least 7 hours on a charge without even nursing it (screen medium and surfing on wifi). I can easily go through an 8-10 hour workday without my charger and it's kind of become a game for me to try and see if I can expend the battery and I've yet to actually do so in real life. The battery monitor's estimates are also extremely accurate on my machine, IME, and it's also able to tell you how many watts are being used (average ~7.5). The computer starts giving battery critical warnings when I have over an hour of battery left which I think is hilarious.

---

### Post by samanthad on 2011-03-23
> **samanthad said:**
> I got sound to work through my headphones what with running the script to upgrade ALSA to 1.0.24 and then re-adding the line within /usr/share/alsa/alsa.conf and it works. My microphone works and my speakers switch between speakers and headphones.

BUT

The moment I play a flash video with sound my microphone stops working and the computer sticks to whatever it was on when the sound started (speakers or headphones) and refuses to change, even when all applications stop using Pulse. I think it has to do with Flash being an ALSA application.

This is a 64-bit Maverick install with the beta Flash player "square," by the way.

Update: I hadn't noticed this before but if you start the first flash movie BEFORE you plug in your headphones (and it seems to reset when the computer goes to sleep) headphone/speaker switching works normally and the microphone is operational. It only happens when you have the headphones in when you first start the app for the first time.

Still a bug just a much less serious one. Still puzzling... :confused:

---

### Post by samanthad on 2011-03-23
Oh, one thing I noticed and forgot to mention earlier having to do with the video driver and sleeping:

I was initially having trouble with the computer going to sleep. It would go to sleep and then not wake properly. It seemed to come out of sleep but the display would never turn back on. I figured it was the display driver and I had installed flgrx from Ubuntu's restricted drivers, got the watermark issue, and "fixed" it with replacing the perpetrating file with a file from the official installer.

Anyway, when I installed with the official installer from the get-go I never had any trouble and the graphics card seems to benchmark a bit better, too!

Don't use Ubuntu's installer for flgrx!

---

### Post by mr_raider on 2011-03-24
> **linuxhobox said:**
> Varies a bit.
With dimmed screen:

[LIST]
[*]I'm getting 5:30-7.5 hrs moderate usage
[*]Heavy usage 4 to 6
[*]Letting it sleep w/ very light usage I can go 8 to 12 hours (including sleep time).
[/LIST]

my experience is similar. Am I to believe these numbers are better than windows?

---

### Post by dfmutz on 2011-03-24
not by much, if you check out Engadget's report: [http://www.engadget.com/2011/02/07/lenovo-thinkpad-x120e-review/](http://www.engadget.com/2011/02/07/lenovo-thinkpad-x120e-review/) you can see in the performance section their rundown test which is a movie looped with 65 percent brightness and wifi off it lasted 4:56 and normal usage netted close to six hours. Personally I have run it for almost 6 hours with normal usage and still had about 25% battery left using windows. I would say the gain is minimal at best.

---

### Post by codedivine on 2011-03-25
Mine is on order now :)
Thanks everyone for the info on battery life. I am upgrading from the original X100e, which will serve as my plugged-in desktop once X120e arrives.

---

### Post by link141 on 2011-03-25
I ordered (and received) my x120e with a smaller battery and instead opted for the larger and faster HD (didn't realize you could get one cheaper online at that point).  I haven't had much time to play around with it with school, but I seem to be getting 3-4 hours on a single charge under normal use (even with sleeping).

Even if I take it to my college campus, I figured that I wouldn't need to use the laptop for more than 3 or four hours and would usually have a wall outlet nearby anyway. Do you think it's worth buying the larger battery for its gain in life over the smaller one?

This is unrelated, but the x120e has a very sensitive accelerometer (like all Thinkpads) to detect when the unit is dropped.  Under Windows, this motion will trigger the hard drive to park the heads in less than 500 ms to reduce data loss.  There seems to be a working application to do the same under Linux.

However, the accelerometer is total overkill in terms of sensitivity, so it can be used to play Neverball :D! [_[COLOR="RoyalBlue"]Video on T41[/COLOR]_](http://www.youtube.com/watch?v=2JE2Np45h0o)

---

### Post by Keozon on 2011-03-27
Got my x120e a few days ago, went though a couple different distros (starting with Natty, went to arch, then fedora, now on maverick). Bluetooth works fine, as long as windows turns it on, first. You can then turn it on and off in Ubuntu, although I haven't tested if you can turn it off, reboot, and still see it. I will check that after I post this.

Buetooth appears to drain about 1W of power, and, although untested, I imagine the wifi drains 1-2Watts. That means that this thing uses about 5w doing minimal tasks. Pretty impressive.

A few things I ran into: If you accidentally install AMD's proprietary drivers on Mav. x64 after installing the drivers listed in the "Additional Drivers" GUI, you'll get some WICKED screen tearing. I dragged a terminal across the screen, and half the terminal was still on the other side of the screen for a bit. To fix this, just go into the Additional Drivers GUI and disable the ATI driver. This will unfortunately disable the good one from AMD, but after a restart, if you install AMD's again it will work properly.

So far, Adobe Flash Square seems to be working fine for me. Haven't experienced any instability, and full screen video works fine (appears to drain substantially more battery life than in windows, however.)

All in all, battery life is adequate, although, for me, Windows seems to do better. Linuxhobox, are you running 32 or 64 bit? "Moderate usage" is arbitrary, but I would say I get about an hour less battery than you. 

TrackPoint scrolling is enabled and working flawlessly (HORIZONTAL, too. WIndows doesn't support that, at least out of box). I used GPointingDevices to get it working.

Wireless, as stated previously, appears to be extremely stable. My previous experience with realtek was positive as well (my print server has a realtek chip in it, and it's never gone down), so no surprises there. 

I have not yet tested the webcam, but will soon. Audio output works perfectly, haven't gotten microphone working yet, but I haven't tried terribly hard either. I mostly plan on using a BT headset for audio chat, and I will test that soon as well, when I test the camera.

Also, it appears (in the USA, anyway) that the faster, larger 320 7200RPM HDD is now standard, as is the six cell, so those of you who got it later will get a better deal. I emailed Lenovo, hoping to get some sort of reimbursement for such a substantial change in hardware for the same price, but haven't gotten a response yet, as its the weekend. 

WIll post back soon.

EDIT UPDATE:
720p streaming flash fullscreen playback is a LITTLE choppy. Still watchable, but I wouldn't want it to be an action movie. Fullscreen 420p seemed to be fine, with perhaps a slightly low frame rate. I have yet to test either of these two resolutions in windows for comparison. I also don't have any local HD videos to test fullscreen. Anyone have something they could test? An HD blender file perhaps?
BLuetooth DOES work even after it is turned off, and ubuntu restarts. It does, however, start turned on. No big deal there. Should be easily fixable with a little rc.local magic.

Bluetooth mic worked fine immediately after syncing with computer. Seemed a bit quiet, but I think that's the limitation of the headset. Samsung WEP450 to be exact. After syncing mic, bluetooth icon disappeared. The application still launches fine through the menu, however. Syncing a BT mouse does not make the icon disappear. Strange.

Webcam worked fine with cheese. 

Swiching to windows for 720p video comparison.

UPDATE EDIT:
720p playback via youtube is barely noticeably better on windows. However, my first test on Ubuntu was on Chromium. Firefox and Opera both play the video substantially smoother. That surprised me. Using firefox/opera instead of Chromium got rid of any frame rate drops, but still had a little tearing. Nothing that major, however.

---

### Post by linuxhobox on 2011-03-28
> **Keozon said:**
>  Linuxhobox, are you running 32 or 64 bit? "Moderate usage" is arbitrary, but I would say I get about an hour less battery than you. 

Config:  750GB 7200 rpm drive, 8gb memory, bluetooth, 64 bit maverick
Moderate Usage:  web browsing, minor usb rsync, doc editing, flash video

It did take the battery a few weeks of cycles to gain 20-45 minutes.

---

### Post by Crath on 2011-03-29
Can we set up some sort of wiki page for this laptop that explains how to get each bit working with natty and/or maverick? Reading through 14 pages over and over and picking out what sounds like it works is a bit tricky :P

---

### Post by icouldmakeyousmile on 2011-03-29
A wiki would be a good idea, as much as I liked the journey of discovery as updates came in. Ignoring the false starts and stuffups, here's a summary of what I did after a fresh install of Maverick (Realtek wireless, no bluetooth sorry):

Wireless
- download and run RTL8192 wireless drivers from Realtek
(rtl8192ce_linux_2.6.0005.1116.2010.tar.gz)
[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8192CE-VA4](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8192CE-VA4)

Video
- do not install fglrx via Additional Drivers
- download and run drivers from AMD
(ati-driver-installer-11-2-x86.x86_64.run)
[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English)

Audio
- upgrade alsa using the upgrade script linked below
- modify alsa.conf
- pulseaudio hasn't been reinstalled, but it's seems fine so far
[http://ubuntuforums.org/showpost.php?p=10547545&postcount=45](http://ubuntuforums.org/showpost.php?p=10547545&postcount=45)

Sleep
- run gconf-editor
- modify apps > gnome-power-manager > actions > sleep_type_battery to 'suspend'

Everything else has been installed from Ubuntu Software Center (including Flash from Adobe).

Things that work (in vague order that I remember going 'yay, this works!'): wifi, video, speakers, Flash in browser, internal and external microphone, webcam, Fn keys, VGA and HDMI out, Unity, sleep (haven't hibernated yet, but most people seem to be saying it's not working)

---

### Post by sebasjm on 2011-03-29
just got my x120e and installed 10.10 (maverick). wifi works and hdmi with audio works well, too.

Using it with my Sony TV ... as previous posts indicate you need to install catalyst 11.2 and NOT the ubuntu drivers.

Temperature is amazing ... machine stays very very cool to the touch and sensors reports temps between 49 and 58 deg (Celsius) when watching movies.

if you hdtv has over/under scan issues you need to go into preferences -> ati catalyst control center (administrative) and adjust the settings for your tv.

---

### Post by Crath on 2011-03-31
I installed 10.04 on my brand new x120e and couldn't get most things to work like wifi. Then, I installed 11.04 Alpha 3 and had quite a bit of issues as well. Mostly with graphics and staying stable. I just installed 11.04 Beta 1 which was released today and it's almost PERFECT! Will edit this post with a full run down soon.

---

### Post by kelpdip on 2011-04-01
Running 11.04 beta1 live off usb drive right now. Everything works (cam, audio, trackpoint/pad) except bluetooth. Unity is weak, but that is a design problem I guess. Is there any reason to mess with the AMD video drivers? Power saving features?

Edit: BT works if enabled from windows. Just need to set up the hotkey. Unity has potential, but is too buggy and lacking in features at the moment.

---

### Post by linuxhobox on 2011-04-01
> **kelpdip said:**
> . Is there any reason to mess with the AMD video drivers? Power saving features?.

Does HDMI audio out work?  That's usually my main reason for using fglrx.  The opensource driver's hdmi audio didn't work well w/ switchable graphics.

I might give this a try this weekend.

---

### Post by Crath on 2011-04-01
> **kelpdip said:**
> Running 11.04 beta1 live off usb drive right now. Everything works (cam, audio, trackpoint/pad) except bluetooth. Unity is weak, but that is a design problem I guess. Is there any reason to mess with the AMD video drivers? Power saving features?

Edit: BT works if enabled from windows. Just need to set up the hotkey. Unity has potential, but is too buggy and lacking in features at the moment.
I didn't like Unity much as well. It had too many shadow / fade effects. I just logged in with Ubuntu Classic (No Effects) which is exactly what I want.

As for the AMD drivers, I noticed when playing an html5 video or using the webcam, the cpu was hammered, but once I got the amd driver installed (which was very easy) the cpu usage was barely anything during html5 videos (didnt try webcam yet) so I'd say yes, both a faster experience overall (general usage, too) and power savings.

---

### Post by Engine_number_9 on 2011-04-02
> **Crath said:**
> As for the AMD drivers, I noticed when playing an html5 video or using the webcam, the cpu was hammered, but once I got the amd driver installed (which was very easy) the cpu usage was barely anything during html5 videos (didnt try webcam yet) so I'd say yes, both a faster experience overall (general usage, too) and power savings.

Which drivers did you install? I installed the ones provided by the additional drivers tool and while they seemed to install correctly they took me back to classic mode, and I was not able to log into unity afterwards but was taken to gnome classic.

Edit: there seems to be a [bug]("https://bugs.launchpad.net/ubuntu/+source/unity/+bug/685682") filed for this

---

### Post by Engine_number_9 on 2011-04-03
Having used my system since I upgraded to natty beta 1, I find it quite slow. I am on the entry level E-240 system and the cpu goes from to 100% when I load a webpage. I do not use the proprietary driver as it does not work as of yet. 

Is the system likely to be faster when I get the proprietary drivers installed?

Otherwise I would definately recommend going for the E-350 model, if you are planning on buying the x120e.

---

### Post by omriasta on 2011-04-03
Lenovo claims (the feature also exists in BIOS) that the yellow USB port should charge devices even when the laptop is off. Does this work for anyone?
I tried a few devices and made sure the feature is enabled in BIOS without any success.
Please reply if this works for you.

---

### Post by bleedpurple on 2011-04-03
I've had my x120e for about a week.  I just managed to get ubuntu netbook remix installed on a partition.  I am a fairly inexperienced user.  Can you explain what I need to do to get the wireless working?

---

### Post by bleedpurple on 2011-04-03
> **linuxhobox said:**
> Just finished setting this up.

[LIST]
[*]Realtek wifi works stock w/ Natty / Maverick needs compile of rtl8192ce driver from realtek site. (make,make install, reboot)
[*]Bluetooth works stock w/ Natty / Maverick needs work
[*]Fglrx ati graphics  did not compile w/ Natty (is x server compatible?) / works with Maverick  see [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)  (hdmi sound works)
[*]Suspend works w/ Maverick (wifi works after suspend) / not tested with natty
[*]UEFI install worked w/ Natty / Kernel panic with Maverick
[*]UEFI install will not work from usb stick unless it emulates a cd/dvd rom ([http://en.wikipedia.org/wiki/U3](http://en.wikipedia.org/wiki/U3))
[*]Legacy Bios Install worked w/ both
[*]Microphone input does not work on install but I haven't done any troubleshooting yet.
[*]Battery life seems good so far.
[*]Hibernate not tested Natty / Maverick hibernate locks up (no solution yet)
[*] wireless function key has no effect
[*]8Gb ram installed w/ out a problem
[/LIST]

Wireless hasn't dropped in hours of use.

I don't even see the bluetooth device w/ lspci under maverick.  Bios vs Uefi issue?\

Maintenance manual linke --> [http://download.lenovo.com/ibmdl/pub/pc/pccbbs/mobiles_pdf/63y0640_02.pdf](http://download.lenovo.com/ibmdl/pub/pc/pccbbs/mobiles_pdf/63y0640_02.pdf)



Can you explain how to get the wireless to work? I've had my x120e for about a week and just got 10.10 installed on it this evening but can't get the wireless to work.  Ifconfig indicates no wireless adapter present.

---

### Post by linuxhobox on 2011-04-03
> **bleedpurple said:**
> Can you explain how to get the wireless to work? I've had my x120e for about a week and just got 10.10 installed on it this evening but can't get the wireless to work.  Ifconfig indicates no wireless adapter present.
I compiled but there is a ppa out there.
You can search posts or download driver ('ce' suffix for linux).

link --> [http://www.realtek.com/Downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true&SortByDesc=1](http://www.realtek.com/Downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true&SortByDesc=1)

---

### Post by bleedpurple on 2011-04-04
> **bleedpurple said:**
> Can you explain how to get the wireless to work? I've had my x120e for about a week and just got 10.10 installed on it this evening but can't get the wireless to work.  Ifconfig indicates no wireless adapter present.

I was able to muddle through this after I posted the above by looking at the Lenovo forums.

1) Go to [https://launchpad.net/~lexical/+archive/hwe-wireless](https://launchpad.net/~lexical/+archive/hwe-wireless)
2) Click on "View package details"
3) Expand the rtl8192ce-dkms maverick package by clicking on it.
4) Download rtl8192ce-dkms_2.6.0003.0628.2010ubuntu2_all.deb

This worked even though when I ran lspci I saw that my wireless card was slightly different.

---

### Post by omriasta on 2011-04-04
> **omriasta said:**
> Lenovo claims (the feature also exists in BIOS) that the yellow USB port should charge devices even when the laptop is off. Does this work for anyone?
I tried a few devices and made sure the feature is enabled in BIOS without any success.
Please reply if this works for you.

I will reply to myself on this one in case anyone was wondering....
I guess one of the engineering geniuses at Lenovo decided that the "always on" yellow usb port should only work if the laptop is plugged in, thus making it more of a "sometimes on" usb port.
If I have an outlet to plug my laptop in, why wouldn't I just charge my phone from that outlet. Also if my laptop was plugged in, why would I care if it's on/off?
Correct me if I'm wrong but my assumption was that the port would actually be "Always ON" and that I would be able to charge my phone from my laptop battery. Using this laptop as a 5V AC adapter is just stupid (my phone charger is a bit smaller...)
It might actually be useful if we could use our laptop battery (which is a bit larger) to charge our puny cell phone batteries but I guess the folks at Lenovo don't agree.
Is there anyway to rewrite the BIOS so that it charges even when unplugged or would that empty the battery even when not in use?

---

### Post by omriasta on 2011-04-04
> **Crath said:**
> Can we set up some sort of wiki page for this laptop that explains how to get each bit working with natty and/or maverick? Reading through 14 pages over and over and picking out what sounds like it works is a bit tricky :P

Started something here, I'm no expert with wiki's but please contribute and fix anything I f$%#ed up :)
[http://www.thinkwiki.org/wiki/Ubuntu_10.10_Installation_instructions_for_the_ThinkPad_X120e]("http://www.thinkwiki.org/wiki/Ubuntu_10.10_Installation_instructions_for_the_ThinkPad_X120e")

---

### Post by Zak Smith on 2011-04-04
I've had my x120e for not quite a month.   I got the E350 version with 2GB and then replaced the factory HDD with the Intel 510 series SSD (120GB).   It's running Ubuntu 10.10 and everything works that I've tested other than "Hibernate".    

It's the perfect size for trips and to use around the house.  Very nice little laptop.   I have the smaller 3-cell battery for the smallest physical package size.  I get right around 3:00-3:30 battery life doing boring stuff like running firefox, mutt, offlineimap, and emacs.  

I do recommend running thinkfan.   With a little tweaking of the temperature breakpoints, I've made it run without the fan the majority of the time, IE, when the temperature is less than 55-56 degrees.

Speaking of the fan, I did have an issue after running the machine for about 3 days, it started making a terrible sound, kind of like a diesel idling.  Lenovo repaired it in about 2.5 days door to door.

---

### Post by icouldmakeyousmile on 2011-04-04
> **omriasta said:**
> Lenovo claims (the feature also exists in BIOS) that the yellow USB port should charge devices even when the laptop is off. Does this work for anyone?
I tried a few devices and made sure the feature is enabled in BIOS without any success.
Please reply if this works for you.

I've gotten that USB port working when the laptop is in standby, and plugged into power.

---

### Post by kelpdip on 2011-04-04
> **omriasta said:**
> I guess one of the engineering geniuses at Lenovo decided that the "always on" yellow usb port should only work if the laptop is plugged in, thus making it more of a "sometimes on" usb port. If I have an outlet to plug my laptop in, why wouldn't I just charge my phone from that outlet. Also if my laptop was plugged in, why would I care if it's on/off?
Correct me if I'm wrong but my assumption was that the port would actually be "Always ON" and that I would be able to charge my phone from my laptop battery. Using this laptop as a 5V AC adapter is just stupid (my phone charger is a bit smaller...)
It might actually be useful if we could use our laptop battery (which is a bit larger) to charge our puny cell phone batteries but I guess the folks at Lenovo don't agree.

Supplying 5v usb from the battery 12v without using the power supply (laptop on) would be an engineering mess, and no laptops do this. There are devices that can, but they have a manual switch and dedicated transformer that would not fit well in a small laptop like the x120.

Edit: devices like [this]("http://www.amazon.com/Brunton-Lithium-Polymer-Storage-Device/dp/B0018BCYR2/ref=sr_1_1?ie=UTF8&s=sporting-goods&qid=1301963080&sr=1-1") or [this one straight from china]("http://www.dealextreme.com/p/9600mah-rechargeable-portable-emergency-power-with-phone-adapters-53689")

---

### Post by zerohedge on 2011-04-05
> **kelpdip said:**
> Supplying 5v usb from the battery 12v without using the power supply (laptop on) would be an engineering mess, and no laptops do this. There are devices that can, but they have a manual switch and dedicated transformer that would not fit well in a small laptop like the x120.

Edit: devices like [this]("http://www.amazon.com/Brunton-Lithium-Polymer-Storage-Device/dp/B0018BCYR2/ref=sr_1_1?ie=UTF8&s=sporting-goods&qid=1301963080&sr=1-1") or [this one straight from china]("http://www.dealextreme.com/p/9600mah-rechargeable-portable-emergency-power-with-phone-adapters-53689")


Actually, my MacBook Pro is quite happy to charge my iPhone while on battery power, so some laptops do this. I just ordered the x120e, so that is extremely dissapointing to find out it can not. I thought this was a standard feature on laptops (this will be my first non-Apple laptop). I got this just to run Ubuntu.

---

### Post by swaq on 2011-04-05
I can't seem to get the suspend to work properly in Xubuntu 10.10. It will suspend and wake back up the first time, but the second time I try it the screen will stay black and I have to force shutdown... I've tried disabling the monitor sleep/off and disabling the screensaver, but the problem persists. Thoughts?

---

### Post by GrannyTux on 2011-04-06
You might want to check out Red Flag Deals I just got my x120e w/ e-350 for $415.00 red flag has a lot of coupond sales. Now I have to wait for 10 day for shipment :-(

---

### Post by linuxhobox on 2011-04-06
> **swaq said:**
> I can't seem to get the suspend to work properly in Xubuntu 10.10. It will suspend and wake back up the first time, but the second time I try it the screen will stay black and I have to force shutdown... I've tried disabling the monitor sleep/off and disabling the screensaver, but the problem persists. Thoughts?

try creating a file /etc/pm/sleep.d/12_remove_wifi
```

#!/bin/bash
case $1 in
    hibernate)
        rmmod r8192ce_pci
        ;;
    suspend)
        rmmod r8192ce_pci
    ;;
    thaw)
         modprobe r8192ce_pci
        ;;
    resume)
    modprobe ath_pci
         modprobe r8192ce_pci
    ;;
    *)  echo "somebody is calling me totally wrong."
        ;;
esac

```

this will load/unload the wifi module.
I had a few failed wake-ups before I did this.

---

### Post by dfmutz on 2011-04-06
For anyone with playback problems, I would suggest you get the newest bios for the x120e. It increases the video memory from 64 MB to 384 MB. Even with two gigs of ram with Ubuntu I think the performance increase would be worth it. I have 4 gigs and it has immensely improved the video playback performance. Here is the link for the CD bios update:

[http://www-307.ibm.com/pc/support/site.wss/document.do?sitestyle=lenovo&lndocid=MIGR-74392](http://www-307.ibm.com/pc/support/site.wss/document.do?sitestyle=lenovo&lndocid=MIGR-74392)

---

### Post by zmydlarz on 2011-04-06
I've tried many times over the last 2 days to download this new BIOS 1.11 but the Lenovo utility keeps quitting halfway through. It was able to pull down all the other drivers though.

---

### Post by dfmutz on 2011-04-06
I downloaded it from the site directly and used the cd bios update. When I tried it in windows I was getting errors due to the fact that the bios is in hybrid bios mode and the win tool is meant to be used with uefi. Apparently the bios defaults to the bios setting over uefi and not the other way around. But when I used the CD I had no issues. Since then I reinstalled windows and turned off the old bios and use uefi only. I am hoping to reinstall ubuntu in the next day or two and see how well it plays with uefi, from my understanding it should play nice... lets hope at least.

---

### Post by drfox on 2011-04-06
I got my x120e a few days ago and really like it. I'm running into just 2 problems so far:
1. Wireless N doesn't work. I can connect to mixed APs but not to an N-only AP. 

2. (Solved) This is actually more annoying: when I boot Ubuntu, the touchpad and lower "mouse" buttons work fine, but once I log into GDM, they cease functioning. The pointing device and upper "mouse" buttons continue to function. When I go into gsynaptics or system settings, the "disable touchpad" check box is not checked. In order to get my touchpad to work again, I have to check the box and then uncheck it. NOTE: It happened consistently until I *uninstalled* gsynaptics and gpointing-device-settings. I had installed them thinking I needed them, and they must have been interfering with the normal gnome settings.

Does anyone have solutions to either (or both!!! :D) of these problems?
TIA, Larry

---

### Post by CPCollin on 2011-04-07
I made a wiki page to start consolidating all these issues:

[https://help.ubuntu.com/community/X120e](https://help.ubuntu.com/community/X120e)

Please help contribute and fill it out.

---

### Post by swaq on 2011-04-07
> **linuxhobox said:**
> try creating a file /etc/pm/sleep.d/12_remove_wifi
```

#!/bin/bash
case $1 in
    hibernate)
        rmmod r8192ce_pci
        ;;
    suspend)
        rmmod r8192ce_pci
    ;;
    thaw)
         modprobe r8192ce_pci
        ;;
    resume)
    modprobe ath_pci
         modprobe r8192ce_pci
    ;;
    *)  echo "somebody is calling me totally wrong."
        ;;
esac

```

this will load/unload the wifi module.
I had a few failed wake-ups before I did this.

Thanks for the response. I tried this last night. I was able to suspend from the menu and press the power button to wake up three times in a row without problem. Then I was able to shut the lid two times and reopen it to wake up just fine. However, the third time I shut the lid it did not enter the sleep state (the case light stayed on the battery icon) and I had to force shutdown again to regain control of the machine. :(

Also, I later tried to suspend from the menu and then close the lid. When I reopened the lid it woke up fine, but then a few minutes later the wireless disconnected and I wasn't able to reconnect it except by rebooting the laptop...

---

### Post by Engine_number_9 on 2011-04-08
> **dfmutz said:**
> For anyone with playback problems, I would suggest you get the newest bios for the x120e. It increases the video memory from 64 MB to 384 MB. Even with two gigs of ram with Ubuntu I think the performance increase would be worth it. I have 4 gigs and it has immensely improved the video playback performance. Here is the link for the CD bios update:

[http://www-307.ibm.com/pc/support/site.wss/document.do?sitestyle=lenovo&lndocid=MIGR-74392](http://www-307.ibm.com/pc/support/site.wss/document.do?sitestyle=lenovo&lndocid=MIGR-74392)

How did you install it using the iso file considering that there is no CD-drive? 

Would it be possible to use unetbootin to make a bootable USB-drive and run the ISO from there?

---

### Post by Engine_number_9 on 2011-04-08
> **Engine_number_9 said:**
> How did you install it using the iso file considering that there is no CD-drive? 

Would it be possible to use unetbootin to make a bootable USB-drive and run the ISO from there?

It seems to work just fine using the .exe file from the wiki page

---

### Post by icouldmakeyousmile on 2011-04-09
> **Engine_number_9 said:**
> It seems to work just fine using the .exe file from the wiki page

I assume you're dualbooting Windows? As I'm Windowless on this laptop, I was determined to do this upgrade without wasting a CD-R and digging out my 5.25" CD drive. I tried out unetbootin, Universal USB installer and a few esoteric virtual CD driver/app combos, in the end YUMI on a Windows machine did the trick.

But I would like to know to create a bootable USB BIOS upgrade from Ubuntu.

---

### Post by link141 on 2011-04-09
> **CPCollin said:**
> I made a wiki page to start consolidating all these issues:

[https://help.ubuntu.com/community/X120e](https://help.ubuntu.com/community/X120e)

Please help contribute and fill it out.

Thank you! I've been meaning to do this, but never got around to it.

I've added some links to the Bios updates under the "AMD Video Drivers" section for Natty.  I also added a comment that laptops that have shipped after a certain date (like mine) may already have 384MB of video memory enabled by default.

Also, I changed the comment on the microphone status to say that it is working out of box on the latest Natty (I just tested it on Kubuntu 11.04 beta 1).

As an unrelated matter, I'd like to mention that I installed Kubuntu 11.04 Beta 1 yesterday, and it is working much better overall than Kubuntu 10.10. I did run into a few issues with the installer and grub, but I was able to straighten them out.

I'm thinking about adding more info under the Maverick section... Is it worth it with the release of Natty being so close?

EDIT: Sorry, I missed the externel links section with the bios update link at the bottom of the page.

---

### Post by linuxhobox on 2011-04-09
> **icouldmakeyousmile said:**
> 
But I would like to know to create a bootable USB BIOS upgrade from Ubuntu.

Easy way:

[LIST=1]
[*]get a usb flash drive drive w/ u3 support (manufactured before 2009)
[*]apt-get install u3-tools
[*]u3-tools -l <iso-image> <device>
[*]reboot and select emulated cd rom
[/LIST]
Other way (haven't done this).
Would also be a bit tricky.

[LIST=1]
[*]extract files from update image
[*]find out how to create a uefi bootable pc dos environment
[*]kick-off extracted files
[/LIST]


Some of the newer seagate and westerdigital usb hd drives also emulate a cd rom.  If anyone knows how to load you own iso let me know.
link--> [http://www.dedoimedo.com/computers/passport-vcd.html](http://www.dedoimedo.com/computers/passport-vcd.html)

---

### Post by link141 on 2011-04-09
I added more information to the help.ubuntu wiki. I put up realtek wireless compilation/installation instructions for Maverick, put up installation instructions for Maverick, added relevant video information, and added a few external links.

Thanks to CPCollin for creating the Wiki page in the first place.

Here's the link: [https://help.ubuntu.com/community/X120e](https://help.ubuntu.com/community/X120e)

Critique welcome.

---

### Post by dfmutz on 2011-04-11
linuxhobo I tried to do the extraction and uefi PC dos like environment to do the update via USB and I haven't found anything that can do it. I don't know of any versions of dos that let alone support uefi and none that could boot the files. Plus, the files don't exactly extract easily. I did not try to do a U3 style boot, seeing as I have to have windows installed too. BTW, anyone know a good way to install ubuntu and still use the windows bootloader? I have tried using EasyBCD in the past but it never worked. If anyone knows anything I would appreciate the info!!

---

### Post by linuxhobox on 2011-04-11
> **dfmutz said:**
> linuxhobo I tried to do the extraction and uefi PC dos like environment to do the update via USB and I haven't found anything that can do it. I don't know of any versions of dos that let alone support uefi and none that could boot the files. Plus, the files don't exactly extract easily. I did not try to do a U3 style boot, seeing as I have to have windows installed too. !

 I ran the iso image from an old cruzer using the u3 emulated cdrom.  
It seemed to use some version of PCDos to do the install.
Maybe, try running the installer on virtualbox and clone the environment to a virtual disk and then clone that to a usb drive?

Must be an easier way.  Just thinking....

---

### Post by CPCollin on 2011-04-12
What are people using for thinkfan settings / configuration? Let's try to find the best balance of fan and cooling for this machine!

Also, the internal mic still does not work for me on 11.04, though I expected it to work out of the box with more recent ALSA and Pulseaudio. Anyone have it working on 11.04?

Please contribute to documentation: [https://help.ubuntu.com/community/X120e](https://help.ubuntu.com/community/X120e)

---

### Post by drfox on 2011-04-12
> **CPCollin said:**
> What are people using for thinkfan settings / configuration? Let's try to find the best balance of fan and cooling for this machine!

Also, the internal mic still does not work for me on 11.04, though I expected it to work out of the box with more recent ALSA and Pulseaudio. Anyone have it working on 11.04?

Please contribute to documentation: [https://help.ubuntu.com/community/X120e](https://help.ubuntu.com/community/X120e)

The mic works fine for me OOTB, running 11.04. I do have LXDE installed alongside Gnome, so it is possible some other driver came along with it, but I doubt it. Skype is working fine, both audio and video.
Larry

---

### Post by CPCollin on 2011-04-12
> The mic works fine for me OOTBStill does not work for me with 11.04, I have made sure the mic is not muted, boosted levels, and reinstalled pulseaudio but the internal mic still shows no levels in sound preferences or sound recorder.

---

### Post by link141 on 2011-04-13
Does your mic work in Windows (assuming you still have it installed)?  If so, when did you install Natty, and what version of alsa are you using?

I know you said it's unmuted, but I'd double check that it's really unmuted by opening alsamixer in a terminal with "alsamixer -c 1" (the analog sound hardware is seen as a second card). Hit tab once and take a look at the capture levels.

---

### Post by link141 on 2011-04-13
> **CPCollin said:**
> What are people using for thinkfan settings / configuration? Let's try to find the best balance of fan and cooling for this machine!
[https://help.ubuntu.com/community/X120e](https://help.ubuntu.com/community/X120e)

Just out of curiosity, what temperature is your CPU averaging on Natty?  Mine stays around 60C with normal use, which seems a bit hot (but no where near the max of 90C).  I think I'll log the temperature over time on both windows and Linux and compare the two...

Just a warning: I saw many people online saying NOT to lower the fan usage as the processor really does need that level of cooling.  If anything, I'd see if I could make it run more to keep it cooler.

---

### Post by CPCollin on 2011-04-13
It works in windows. I installed Natty around the 23rd of March, and have kept up with updates. Checked alsamixer and nothing is muted, capture/ mic levels are at 100%.

The microphone worked for me in Ubuntu just before posting this message, but sound output did not. The mic did not work after rebooting, but the output sound does. Definitely strange.

My temps hover around 54C while doing minor work.

---

### Post by linuxhobox on 2011-04-14
Anyone try fglrx 11.3 w/ Natty yet?

[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&#9001;=English]("http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English")

---

### Post by icouldmakeyousmile on 2011-04-15
> **linuxhobox said:**
> Easy way:

[LIST=1]
[*]get a usb flash drive drive w/ u3 support (manufactured before 2009)
[*]apt-get install u3-tools
[*]u3-tools -l <iso-image> <device>
[*]reboot and select emulated cd rom
[/LIST]
Other way (haven't done this).
Would also be a bit tricky.

[LIST=1]
[*]extract files from update image
[*]find out how to create a uefi bootable pc dos environment
[*]kick-off extracted files
[/LIST]


Some of the newer seagate and westerdigital usb hd drives also emulate a cd rom.  If anyone knows how to load you own iso let me know.
link--> [http://www.dedoimedo.com/computers/passport-vcd.html](http://www.dedoimedo.com/computers/passport-vcd.html)

Other possible option for those without a U3 USB flash drive, I found the Linux equivalent to the YUMI utility I used: [http://www.pendrivelinux.com/multiboot-create-a-multiboot-usb-from-linux/]("http://www.pendrivelinux.com/multiboot-create-a-multiboot-usb-from-linux/").

Sadly I'm in no mood to upgrade my BIOS again, so won't be testing this out but it did successfully create a multiboot USB for 2 other ISOs I wanted.

As for flgrx 11.3, I'm willing to try it out but have already installed via Additional Drivers. Does natty have the same problem as maverick of screwing up if you went Additional Drivers before the offical AMD driver?

---

### Post by link141 on 2011-04-15
> **linuxhobox said:**
> Anyone try fglrx 11.3 w/ Natty yet?

[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&#9001;=English]("http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English")

Yes, I'm using it now on Kubuntu Natty Beta 1.

[QUOTE=icouldmakeyousmile]Does natty have the same problem as maverick of screwing up if you went Additional Drivers before the offical AMD driver?[/QUOTE]

No, I installed it with "Additional Drivers" on Kubuntu and it seems to be working fine.

However, there seems to be a bug where the OS occasionally locks up when using GPU accelerated applications (flash, games).  I'm not sure if it's a problem with Catalyst 11.3, or if it's just because Natty is Beta still...

---

### Post by link141 on 2011-04-15
> **CPCollin said:**
> It works in windows. I installed Natty around the 23rd of March, and have kept up with updates. Checked alsamixer and nothing is muted, capture/ mic levels are at 100%.

The microphone worked for me in Ubuntu just before posting this message, but sound output did not. The mic did not work after rebooting, but the output sound does. Definitely strange.

My temps hover around 54C while doing minor work.

I wonder if your problem is a configuration issue, as the microphone shows up in alsamixer...

---

### Post by zerohedge on 2011-04-15
So, my x120e arrived today. I vomited a little dealing with Windows 7, but knew the pain would be brief as Ubuntu would come to my x120e's rescue. I downloaded 64-bit beta 2 and the USB installer (on my Mac, I will never let Windows touch the internet). I put both of them on an SD card, and then put that in the x120e. I created the installer, then booted into Ubuntu off the SD card. Everything seemed fine, it created the partition, my user info, and sorted settings. At the end was a picture of a couple Narwahls, and then...a black screen of gibberish. No idea what to do from here. Maybe I should just wait until April 28th?

---

### Post by mr_raider on 2011-04-15
ANyone have issues with wifi connecting to a WEP connection? I can connect to the network, but accessing websites is very slow.

I'm using maverick, 2.6.35 kernel and the realtek driver

---

### Post by sleep20 on 2011-04-16
> **zerohedge said:**
> So, my x120e arrived today. I vomited a little dealing with Windows 7, but knew the pain would be brief as Ubuntu would come to my x120e's rescue. I downloaded 64-bit beta 2 and the USB installer (on my Mac, I will never let Windows touch the internet). I put both of them on an SD card, and then put that in the x120e. I created the installer, then booted into Ubuntu off the SD card. Everything seemed fine, it created the partition, my user info, and sorted settings. At the end was a picture of a couple Narwahls, and then...a black screen of gibberish. No idea what to do from here. Maybe I should just wait until April 28th?
I had the same problem you were having. The message was "grub-install efi-dummy failed."  

To  fix it, you need to go into the computer's BIOS and, under the boot  tab, change the uEFI settings to try 'legacy' first. Then everything will install fine.

---

### Post by zerohedge on 2011-04-16
> **sleep20 said:**
> I had the same problem you were having. The message was "grub-install efi-dummy failed."  

To  fix it, you need to go into the computer's BIOS and, under the boot  tab, change the uEFI settings to try 'legacy' first. Then everything will install fine.


Thank you so much! The install worked, although it hung on restart. I did a hard power off, and then it rebooted fine (and has restarted fine since). Sleep/wakeup is also fine.

I'm approaching this the same as I did 10.04 (the first flavor of Linux I tried, and only for 20 minutes via virtual box in OSX). 10.04 really impressed me. It was the most intuitive OS I had ever seen, and I had a trance stream, browser up and mahjong game going immediately. The layout was crsytal clear. 11.04, on the other hand, has been a total nightmare. After spending a few hours with this (no googling allowed) I am quite frustrated. It's a UI disaster, makes no sense. The Fisher Price side bar makes it worse. Maybe I'll find where my applications are tomorrow. My goal was to be hosting Aleph One games on this tomorrow, but at this point, I'll just be glad to find the application folder. I'll throw in the towel, and start googling how to do stuff with this. Horrific turn from the stunning 10.04. My goodness.

In terms of performance, this is painfully slow. It makes Windows looks like a speed demon. Application launches take forever, screen redraws are awful (you can see blank white flashes from pop-down windows, etc). I opened the Evolution email client which took down the whole system, and had to restart. I trashed that and put Thunderbird on, which works great. To what degree this is the x120e, and what degree it's 11.04 B2, I don't know. My overall experience so far leads me to believe this is at least 3 years away from being usable for the general public. I certainly would not recommend 11.04 to a non-tech junkie (although I would have 10.04). Stability and performance enhancements to come don't address the incomprehensible UI.

---

### Post by linuxhobox on 2011-04-16
> **icouldmakeyousmile said:**
> Other possible option for those without a U3 USB flash drive, I found the Linux equivalent to the YUMI utility I used: [http://www.pendrivelinux.com/multiboot-create-a-multiboot-usb-from-linux/](http://www.pendrivelinux.com/multiboot-create-a-multiboot-usb-from-linux/).

Sadly I'm in no mood to upgrade my BIOS again, so won't be testing this out but it did successfully create a multiboot USB for 2 other ISOs I wanted.

 
Hadn't looked at this before.  Cool tool.

Don't know if this will work with uefi since it uses syslinux and doesn't create a uefi partition on the usb flash drive. 

I'll give this a try w/ 'legacy' disabled in the cmos setup utility and see how it goes.

---

### Post by linuxhobox on 2011-04-16
> **zerohedge said:**
> 
I'm approaching this the same as I did 10.04 (the first flavor of Linux I tried, and only for 20 minutes via virtual box in OSX). 10.04 really impressed me. It was the most intuitive OS I had ever seen, and I had a trance stream, browser up and mahjong game going immediately. The layout was crsytal clear. 11.04, on the other hand, has been a total nightmare. After spending a few hours with this (no googling allowed) I am quite frustrated. It's a UI disaster, makes no sense. The Fisher Price side bar makes it worse. Maybe I'll find where my applications are tomorrow. My goal was to be hosting Aleph One games on this tomorrow, but at this point, I'll just be glad to find the application folder. I'll throw in the towel, and start googling how to do stuff with this. Horrific turn from the stunning 10.04. My goodness.


Google around a bit.

Unity can be purged and/or other desktops can be installed (gnome3, kubuntu-desktop, etc).

Unity definitely needs some work and it does seem to be mistake to not have an alternative installed by default.  Even 'classic' mode doesn't completely disable unity.

---

### Post by zerohedge on 2011-04-16
> **linuxhobox said:**
> Google around a bit.

Unity can be purged and/or other desktops can be installed (gnome3, kubuntu-desktop, etc).

Unity definitely needs some work and it does seem to be mistake to not have an alternative installed by default.  Even 'classic' mode doesn't completely disable unity.

These were my first impressions, but I will be delving deeper into it when I get up. One thing I'm VERY happy about is that the multi-touch works in Ubuntu for two finger scrolling. In Windows, it's unusable. I thought it was the trackpad, but that's not the case. The drivers for Ubuntu are just far superior. The updates yesterday also made a big difference, and I like the new icons. The window behavior has also been drastically improved. As a friend of mine said, "Welcome to Linux."

---

### Post by legoman666 on 2011-04-16
> **zerohedge said:**
> These were my first impressions, but I will be delving deeper into it when I get up. One thing I'm VERY happy about is that the multi-touch works in Ubuntu for two finger scrolling. In Windows, it's unusable. I thought it was the trackpad, but that's not the case. The drivers for Ubuntu are just far superior. The updates yesterday also made a big difference, and I like the new icons. The window behavior has also been drastically improved. As a friend of mine said, "Welcome to Linux."

I had the same experience with the 2 finger scrolling in Windows. Completely unusable. Works perfect in Ubuntu.

---

### Post by zerohedge on 2011-04-16
I'm running 11.04 Beta 2, and most things seems to work okay (instability aside). A sore spot is the wifi card, which recognizes networks but can not connect to them (both open and password protected). I need to buy whoever did the touchpad drivers a beer.

---

### Post by samanthad on 2011-04-17
I filed a bug regarding the X120e's issues w/rt not switching between speakers and headphones reliably. I'm trying to reproduce the bug but it's being elusive.  Attached files are of a working system with broken system to follow.

[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/764062](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/764062)

Bug is for 11.04 Beta 2

---

### Post by CPCollin on 2011-04-18
> **link141 said:**
> I wonder if your problem is a configuration issue, as the microphone shows up in alsamixer...

Yes it must have been. I messed around saving out the alsacfg and got it to work.  I believe it was a botched setting (or lack of setting) from an earlier Alpha install.

---

### Post by CPCollin on 2011-04-18
Do we need to install any additional packages to enable video acceleration while using the fglrx drivers?

What needs to be done to enable XvBA  / VA-API acceleration?

---

### Post by legoman666 on 2011-04-18
> **CPCollin said:**
> Do we need to install any additional packages to enable video acceleration while using the fglrx drivers?

What needs to be done to enable XvBA  / VA-API acceleration?

fglrx from the repository doesn't work. You need to install the binary package from AMD's website.

---

### Post by CPCollin on 2011-04-18
> **legoman666 said:**
> fglrx from the repository doesn't work. You need to install the binary package from AMD's website.

What do you mean fglrx does not work? Fglrx from the repository works fine in 11.04 in the sense that nothing breaks, all looks well enough.

I'm not sure about acceleration though, is that what you mean? The fglrx in the 11.04 repo does not have XvBA / VA-API acceleration but the one on AMD's site does?

---

### Post by CPCollin on 2011-04-18
> **link141 said:**
> Yes, I'm using it now on Kubuntu Natty Beta 1.



No, I installed it with "Additional Drivers" on Kubuntu and it seems to be working fine.

However, there seems to be a bug where the OS occasionally locks up when using GPU accelerated applications (flash, games).  I'm not sure if it's a problem with Catalyst 11.3, or if it's just because Natty is Beta still...

Are you still running fglrx 11.3 ? When I installed from the software center it was an early 11.4 version.

Are you still having acceleration problems? (I'd like to get XvBA / VA-API running for supported applications)

---

### Post by bnlt on 2011-04-18
I just got a x120e with ubuntu 10.10 pre-installed.
In the "Software sources", I found two source, detail of the first one:

Type: Binary
URI: [http://lenove.archive.canonical.com/updates/](http://lenove.archive.canonical.com/updates/)
Distribution: maverick-sutton
Components: public

The second one with Type: Source


And there also some software can be found in "Ubuntu Software Center" - "Installed Software" - "Other":
(All the License and Updates are Unknown, and some can't be found on the web)

alsa-driver-hda-mav-ubuntu-audio-dev-dkms
version:2.6.35.27.201103061605sutton3

Canonical-oem-keyring

fglrx
version:2:8.821-0ubuntu1sutton1

fglrx-amdcccle
version:2:8.821-0ubuntu1sutton1

fglrx-modaliases
version:2:8.821-0ubuntu1sutton1

fluendo-eula
version:0.6

lenovo-thinkpad-default-settings
version:0.10

rtl8192ce-dkms
version:2.6.0005.1116.2010-0sutton3

thinkdpad-acpi-dkms
version:2.6.35.28sutton1

Hope theses information be helped

---

### Post by cha5on on 2011-04-19
Has anyone else had a problem with the wireless dropping frequently and occasionally causing the system to hard-lock during reconnect?  I'm running an up-to-date 11.04 setup, and although I realize I shouldn't expect everything to work prerelease, I'd seen reports that people were finding success with the x120e and natty.

More specifically, I've tried connecting to two mixed-b/g/n networks, one unencrypted and one using a type of WPA2 Enterprise.  Both connections are successfully initiated, but the connection quality is poor while connected (upward of 10% lost packets despite being in relatively close proximity to the AP, a problem not seen on other machines).  Also, the system hard-locks about 1 out of 10 times while reconnecting.  FWIW, I don't have this problem in Windows 7 connecting to the unencrypted one (Win7 doesn't connect to the WPA2 one at all), so I'm guessing it's a driver problem, but dmesg and the logfiles don't seem to have anything useful.

---

### Post by link141 on 2011-04-19
> **CPCollin said:**
> Are you still running fglrx 11.3 ? When I installed from the software center it was an early 11.4 version.

Are you still having acceleration problems? (I'd like to get XvBA / VA-API running for supported applications)

I made a mistake, I believe I am running the same fglrx as you (it's from the repos and the driver version in the catalyst control center is greater than what it should have for 11.3).  XvBA/VA-API should be enabled by default in the proprietary driver.  You may have to install libva1, but it was installed by default on my system.  However, after installing vainfo to see if VA-API was working, I was getting errors with the VA-API fglrx backend starting (something like "XFree86 DRI extension not found", have to check).  I'm not sure why it's throwing this error, but it may help explain why VA-API isn't working. There's always something you need to fix when installing Linux on a bleeding edge laptop :rolleyes:.

EDIT: Perhaps I need to install some XVBA libs? I read a post on another thread that it works on this APU with the latest XVBA and VA libs installed. Will try when I get the chance.

---

### Post by samanthad on 2011-04-19
> **cha5on said:**
> Has anyone else had a problem with the wireless dropping frequently and occasionally causing the system to hard-lock during reconnect?  I'm running an up-to-date 11.04 setup, and although I realize I shouldn't expect everything to work prerelease, I'd seen reports that people were finding success with the x120e and natty.

More specifically, I've tried connecting to two mixed-b/g/n networks, one unencrypted and one using a type of WPA2 Enterprise.  Both connections are successfully initiated, but the connection quality is poor while connected (upward of 10% lost packets despite being in relatively close proximity to the AP, a problem not seen on other machines).  Also, the system hard-locks about 1 out of 10 times while reconnecting.  FWIW, I don't have this problem in Windows 7 connecting to the unencrypted one (Win7 doesn't connect to the WPA2 one at all), so I'm guessing it's a driver problem, but dmesg and the logfiles don't seem to have anything useful.

I've been having hard-lockup problems who's symptoms are very similar to yours (identical). I hadn't associated it with network dropping until now. However, in hindsight it was most unstable when on networks with weak signals. I will investigate it further.

What makes you think that it's the network reconnecting that is causing the problem? Also, manually connecting and reconnecting doesn't seem to destabilize my system at all.

---

### Post by CPCollin on 2011-04-19
> **link141 said:**
> 
EDIT: Perhaps I need to install some XVBA libs? I read a post on another thread that it works on this APU with the latest XVBA and VA libs installed. Will try when I get the chance.

That would be great, please let me know what you find and I'll try it too and update the wiki.

[https://help.ubuntu.com/community/X120e](https://help.ubuntu.com/community/X120e)

---

### Post by thelaughingmagi on 2011-04-20
Im having an issue getting any version of ubuntu to install on my x120e. When i try 11.04 x64 both the daily image and the normal amd64 one it gets through the entire process then fails to install grub2. the installer will always hang on installing the grub2 package. Ive tried to isntall from cds and usb drives neither seems to work correctly. Any ideas?

---

### Post by samanthad on 2011-04-20
> **thelaughingmagi said:**
> Im having an issue getting any version of ubuntu to install on my x120e. When i try 11.04 x64 both the daily image and the normal amd64 one it gets through the entire process then fails to install grub2. the installer will always hang on installing the grub2 package. Ive tried to isntall from cds and usb drives neither seems to work correctly. Any ideas?

Well, 11.04 is still in beta. I got it installed by upgrading from 10.10.

---

### Post by thelaughingmagi on 2011-04-20
> **samanthad said:**
> Well, 11.04 is still in beta. I got it installed by upgrading from 10.10.
 
 
I cant even get it to boot the image for 10.10 both 32 and 64 bit. I thought there was something wrong with the netbook so i tried fedora and no issues i got it installed and mostly working just couldnt get sound id rather use ubuntu but im having so many issues.... I have yet to try 10.10 via cd which i intend to do when i get home ill update if that corrects it otherwise im kinda at a loss

---

### Post by link141 on 2011-04-20
[QUOTE=thelaughingmagi]Im having an issue getting any version of ubuntu to install on my x120e. When i try 11.04 x64 both the daily image and the normal amd64 one it gets through the entire process then fails to install grub2. the installer will always hang on installing the grub2 package. Ive tried to isntall from cds and usb drives neither seems to work correctly. Any ideas?[/QUOTE]

I ran into this same problem with the installer (AMD64) locking up, and grub not working afterwards (but only on Kubuntu 11.04).  I thought it was a problem with the normal installer, so I downloaded the alternate installer and made a boot SD card from it.  That one didn't lock up during the install, but it still had the problem with grub.

To fix this, I used the grub that came with the alternate cd iso (via SD card) to manually boot the new system.  Once I did that, I manually removed the package grub-efi, installed grub-pc, and updated the grub config.  If your interested in doing this, let me know, and I can give you exact instructions.

Apparently, this issue is caused by a bios setting pertaining to efi booting that confuses the grub-installer into installing the efi version(see earlier posts in this thread).  This means you should be able to change the setting and reinstall Ubuntu successfully.

---

### Post by link141 on 2011-04-20
> **cha5on said:**
> Has anyone else had a problem with the wireless dropping frequently and occasionally causing the system to hard-lock during reconnect?  I'm running an up-to-date 11.04 setup, and although I realize I shouldn't expect everything to work prerelease, I'd seen reports that people were finding success with the x120e and natty.

More specifically, I've tried connecting to two mixed-b/g/n networks, one unencrypted and one using a type of WPA2 Enterprise.  Both connections are successfully initiated, but the connection quality is poor while connected (upward of 10% lost packets despite being in relatively close proximity to the AP, a problem not seen on other machines).  Also, the system hard-locks about 1 out of 10 times while reconnecting.  FWIW, I don't have this problem in Windows 7 connecting to the unencrypted one (Win7 doesn't connect to the WPA2 one at all), so I'm guessing it's a driver problem, but dmesg and the logfiles don't seem to have anything useful.

I too am getting occasional hard lock-ups, but I'm not sure if the issue is related to wireless. I'm using a b/g router at home, and haven't tried the laptop with wireless n yet.

---

### Post by jwdoll on 2011-04-20
> **samanthad said:**
> I've been having hard-lockup problems who's symptoms are very similar to yours (identical). I hadn't associated it with network dropping until now. However, in hindsight it was most unstable when on networks with weak signals. I will investigate it further.

What makes you think that it's the network reconnecting that is causing the problem? Also, manually connecting and reconnecting doesn't seem to destabilize my system at all.


I've been having these lockups as well. I've spent a fair amount of time running 11.04 with wireless disabled and have never had it crash during that time.

---

### Post by samanthad on 2011-04-20
> **jwdoll said:**
> I've been having these lockups as well. I've spent a fair amount of time running 11.04 with wireless disabled and have never had it crash during that time.

There's a bug report [https://bugs.launchpad.net/unity/+bug/743861](https://bugs.launchpad.net/unity/+bug/743861) for Unity that has similar symptoms but could very well be a different bug. Let's go ahead and make a new bug report on launchpad! This is definitely a reproducable bug.

Right now I'm working in the lab with my computer connected to the ethernet to confirm your findings.

---

### Post by cha5on on 2011-04-20
> **samanthad said:**
> What makes you think that it's the network reconnecting that is causing the problem? Also, manually connecting and reconnecting doesn't seem to destabilize my system at all.

I don't have any problems when not using wireless, and every time the system hard-locks on wireless I see the NetworkManager bar icon stuck partway through its 'connecting' animation.

It's good to know other people are having the problem and that my machine's not just an isolated case!  I can see about putting together a bug report something this evening or perhaps tomorrow.

---

### Post by thelaughingmagi on 2011-04-20
> **link141 said:**
> I ran into this same problem with the installer (AMD64) locking up, and grub not working afterwards (but only on Kubuntu 11.04). I thought it was a problem with the normal installer, so I downloaded the alternate installer and made a boot SD card from it. That one didn't lock up during the install, but it still had the problem with grub.
 
To fix this, I used the grub that came with the alternate cd iso (via SD card) to manually boot the new system. Once I did that, I manually removed the package grub-efi, installed grub-pc, and updated the grub config. If your interested in doing this, let me know, and I can give you exact instructions.
 
Apparently, this issue is caused by a bios setting pertaining to efi booting that confuses the grub-installer into installing the efi version(see earlier posts in this thread). This means you should be able to change the setting and reinstall Ubuntu successfully.
 
If you could that would be great. I could use the directions thanks.

---

### Post by duncanmak on 2011-04-21
I was able to install Natty by using the beta 2 DVD image, and installing it using the textual interface via a USB stick / SD card.

I tried a combination of various images. I tried beta2-desktop, beta2-alternate and two daily builds from this past weekend. I ran into problems with all these images, it would either a) crash during grub installation because of a conflict between grub-efi and grub-pc, b) crash during package installation because of libpulse-mainloop-glib0, c) kernel panic, or d) unable to proceed because there were no suitable kernels to install.

The only solution to the mess is to install only the minimal system without ubuntu-desktop, using the Beta2 DVD image. This was the only combination that allowed me to finish the installation cleanly. Once I got past that, I booted into the system and installed ubuntu-desktop from the console.

---

### Post by zerohedge on 2011-04-21
> **cha5on said:**
> Has anyone else had a problem with the wireless dropping frequently and occasionally causing the system to hard-lock during reconnect?  I'm running an up-to-date 11.04 setup, and although I realize I shouldn't expect everything to work prerelease, I'd seen reports that people were finding success with the x120e and natty.

More specifically, I've tried connecting to two mixed-b/g/n networks, one unencrypted and one using a type of WPA2 Enterprise.  Both connections are successfully initiated, but the connection quality is poor while connected (upward of 10% lost packets despite being in relatively close proximity to the AP, a problem not seen on other machines).  Also, the system hard-locks about 1 out of 10 times while reconnecting.  FWIW, I don't have this problem in Windows 7 connecting to the unencrypted one (Win7 doesn't connect to the WPA2 one at all), so I'm guessing it's a driver problem, but dmesg and the logfiles don't seem to have anything useful.

Yes, I am having the same issue.  I've spent a while trying to figure out how to report a bug and have given up for the time being. Hopefully others with the x120e, and familiar with this process, are reporting this stuff.

---

### Post by zerohedge on 2011-04-21
> **duncanmak said:**
> I was able to install Natty by using the beta 2 DVD image, and installing it using the textual interface via a USB stick / SD card.

I tried a combination of various images. I tried beta2-desktop, beta2-alternate and two daily builds from this past weekend. I ran into problems with all these images, it would either a) crash during grub installation because of a conflict between grub-efi and grub-pc, b) crash during package installation because of libpulse-mainloop-glib0, c) kernel panic, or d) unable to proceed because there were no suitable kernels to install.

The only solution to the mess is to install only the minimal system without ubuntu-desktop, using the Beta2 DVD image. This was the only combination that allowed me to finish the installation cleanly. Once I got past that, I booted into the system and installed ubuntu-desktop from the console.

As discussed earlier in this thread, you just need to set your BIOS to "legacy" first for the uefi setting. Then it installs without issue. :KS

---

### Post by jankyHellface on 2011-04-21
> **samanthad said:**
> There's a bug report [https://bugs.launchpad.net/unity/+bug/743861](https://bugs.launchpad.net/unity/+bug/743861) for Unity that has similar symptoms but could very well be a different bug. Let's go ahead and make a new bug report on launchpad! This is definitely a reproducable bug.

Right now I'm working in the lab with my computer connected to the ethernet to confirm your findings.

This bug is not just with unity. It happens to me on kubuntu 11.04 beta 3 as well. 

I get system freezes whenever I use wireless at school, but don't get them on my home network. I originally thought it had something to do with fglrx and compositing, but the crashes continue even with compositing turned off. I think I may try WICD to see if that fixes the issue.

---

### Post by jwdoll on 2011-04-21
> **jankyHellface said:**
> 
I get system freezes whenever I use wireless at school, but don't get them on my home network.


Does your home network happen to be b/g and your school network n? For one reason or another I've had a similar experience with my home and school networks.

---

### Post by jankyHellface on 2011-04-22
> **jwdoll said:**
> Does your home network happen to be b/g and your school network n? For one reason or another I've had a similar experience with my home and school networks.

I think you're right about that. I have a mixed b/g/n router at home but I just checked and it's connected using g. 

Do you know of a way to force the driver to use b/g for the time being?

---

### Post by CPCollin on 2011-04-22
> **jankyHellface said:**
> 
Do you know of a way to force the driver to use b/g for the time being?
Your router probably has settings to force it to use g mode only.

---

### Post by thelaughingmagi on 2011-04-22
> **zerohedge said:**
> As discussed earlier in this thread, you just need to set your BIOS to "legacy" first for the uefi setting. Then it installs without issue. :KS
 
 
That didnt work for me i still get all the way though the install process till installing grub2 package the it insta fails. The system files are there but there is no boot loader

---

### Post by link141 on 2011-04-22
> **thelaughingmagi said:**
> If you could that would be great. I could use the directions thanks.
Here it goes...

Boot off your USB boot stick.  You should be presented with a grub menu. (I'm assuming you will as the development version I used behaved this way).  Hit c for a command line and enter the following, where:[LIST]
[*]PART# is the partition you have your boot files on (numbering starting from 1)
[*]sdX is the linux device for your partition (replace X with a number)
[*]<TAB>s represent where you can use tab auto-completion to auto-type the names (just hit the tab key when you get to them)[/LIST]:
```
set root=(hd1,PART#)
linux /boot/vmlinuz<TAB> root=/dev/sdX 
initrd /boot/initrd.<TAB>
boot
```

When your are able to boot your machine, open a terminal and type the following commands:
```
sudo apt-get remove grub-efi grub-efi-amd64 &&\
sudo apt-get install grub-pc &&\
sudo update-grub
```

After this, try rebooting and see what happens.  The next time you log in, I recommend doing an immediate upgrade.  Let me know if you have any problems as I am recalling the grub commands from memory

Good luck.

---

### Post by jankyHellface on 2011-04-22
> **CPCollin said:**
> Your router probably has settings to force it to use g mode only.

Since it's a school network, I don't have access to the router.

Edit: nevermind, it doesn't look like we can access modulations through iwconfig. So, no dice with forcing b/g.

---

### Post by KEMATSE2 on 2011-04-22
Has anyone tried using the realtek supplied driver for wireless with Natty? I would think that might solve the problem. My school network uses wireless n and it was a nightmare with Natty Beta 1 but not with Maverick (with the realtek driver) as far as I remember. I would try it but I don't have the time to re-install at the moment... (school has a way of distracting you from the real important things)

---

### Post by duncanmak on 2011-04-22
> **zerohedge said:**
> As discussed earlier in this thread, you just need to set your BIOS to "legacy" first for the uefi setting. Then it installs without issue. :KS

I wanted to get faster boot times by using UEFI, though.

---

### Post by duncanmak on 2011-04-22
> **thelaughingmagi said:**
> That didnt work for me i still get all the way though the install process till installing grub2 package the it insta fails. The system files are there but there is no boot loader

You can try my method of using the Beta2 DVD and installing it in text mode, without installing ubuntu-desktop.

Also, if you opt for EFI, remember to make a dedicated EFI partition at the beginning of your disk. It took me an entire weekend to learn that lesson.

---

### Post by samanthad on 2011-04-24
Bug filed for the hard-crashes that seem to be caused by the wireless.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/769812](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/769812)

---

### Post by zerohedge on 2011-04-26
> **samanthad said:**
> Bug filed for the hard-crashes that seem to be caused by the wireless.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/769812](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/769812)

Same issue here.

---

### Post by SnappyU on 2011-04-26
> **duncanmak said:**
> You can try my method of using the Beta2 DVD and installing it in text mode, without installing ubuntu-desktop.

Also, if you opt for EFI, remember to make a dedicated EFI partition at the beginning of your disk. It took me an entire weekend to learn that lesson.

Meaning?  Should it be fat32 or ntfs or ext3/4?  Or is there an EFI partition type?

---

### Post by duncanmak on 2011-04-26
> **SnappyU said:**
> Meaning?  Should it be fat32 or ntfs or ext3/4?  Or is there an EFI partition type?

Yes there is.

---

### Post by SnappyU on 2011-04-27
Does anyone else know how to setup grub efi properly?  Any howtos link?  Thx in advance!

---

### Post by linuxhobox on 2011-04-28
> **SnappyU said:**
> Meaning?  Should it be fat32 or ntfs or ext3/4?  Or is there an EFI partition type?

If you use the text based installer, it should set it up for you. 

 EFI can use a GUID partition table ( [http://en.wikipedia.org/wiki/Extensible_Firmware_Interface#Disk_support](http://en.wikipedia.org/wiki/Extensible_Firmware_Interface#Disk_support) ) ( [http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table) ).  
This isn't a standard 'DOS' MBR.

---

### Post by wm_brant on 2011-04-28
I've been following this thread since I received my X120e, but I figured that I could wait until 11.04 was released.

So - how does the official release install and run? Any problems?

---

### Post by dfmutz on 2011-04-29
I have installed 11.04 and so far everything works (haven't tried web-cam) including wifi and graphics with the base drivers. My problem is I am trying to dual boot Ubuntu and windows 7 and can only get one or the other boot (depending on which boot-loader is installed). I have the BIOS in UEFI mode only and don't want to change this as the my hard disk is now gpt. I have a grub boot log but frankly don't know how to understand it. Any help is appreciated!! I also would like to use the grub boot-loader as I know it plays nicer with windows than the windows boot-loader does with Ubuntu. The boot log is as follows:

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => No boot loader is installed in the MBR of /dev/sda
 => Syslinux is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

sda6: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot/grub/grub.cfg

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 64.0 GB, 64023257088 bytes
255 heads, 63 sectors/track, 7783 cylinders, total 125045424 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                   1   125,045,423   125,045,423  ee GPT


GUID Partition Table detected.

Partition           Start           End          Size System
/dev/sda1           2,048       206,847       204,800 System/Boot Partition
/dev/sda2         206,848       468,991       262,144 Microsoft Windows
/dev/sda3         468,992   114,558,975   114,089,984 Linux or Data
/dev/sda4     114,558,976   115,535,538       976,563 System/Boot Partition
/dev/sda5     115,535,539   123,045,304     7,509,766 Linux or Data
/dev/sda6     123,045,305   125,045,305     2,000,001 Linux Swap

Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 4009 MB, 4009754624 bytes
255 heads, 63 sectors/track, 487 cylinders, total 7831552 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *            128     7,831,551     7,831,424   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/mapper/cryptswap1 594c0a7d-a18c-4f85-ac23-ce1fdf37ab46   swap                                     
/dev/sda1        2CCC-912B                              vfat                                     
/dev/sda3        E8C0D649C0D61D9E                       ntfs                                     
/dev/sda4        67C0-5CD5                              vfat                                     
/dev/sda5        d2976126-443a-4468-b752-547e626d1c69   ext4                                     
/dev/sda: PTTYPE="gpt" 
/dev/sdc1        90D9-F2B2                              vfat       PENDRIVE                      
/dev/sdc: PTTYPE="dos" 
error: /dev/sdb: No medium found

=============================== "ls -R /dev/mapper/" output: ===============================
/dev/mapper:
control
cryptswap1

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda4        /boot/efi                vfat       (rw)
/dev/sdc1        /media/PENDRIVE          vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)


=========================== sda5/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod efi_gop
  insmod efi_uga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_gpt
insmod ext2
set root='(/dev/sda,gpt5)'
search --no-floppy --fs-uuid --set=root d2976126-443a-4468-b752-547e626d1c69
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_gpt
insmod ext2
set root='(/dev/sda,gpt5)'
search --no-floppy --fs-uuid --set=root d2976126-443a-4468-b752-547e626d1c69
set locale_dir=($root)/boot/grub/locale
set lang=en_US
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_gpt
    insmod ext2
    set root='(/dev/sda,gpt5)'
    search --no-floppy --fs-uuid --set=root d2976126-443a-4468-b752-547e626d1c69
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=d2976126-443a-4468-b752-547e626d1c69 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_gpt
    insmod ext2
    set root='(/dev/sda,gpt5)'
    search --no-floppy --fs-uuid --set=root d2976126-443a-4468-b752-547e626d1c69
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=d2976126-443a-4468-b752-547e626d1c69 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/11_Windows ###
menuentry “Windows 7&#8243; {
set root=(hd0,3)
chainloader +1
}
### END /etc/grub.d/11_Windows ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_gpt
    insmod ext2
    set root='(/dev/sda,gpt5)'
    search --no-floppy --fs-uuid --set=root d2976126-443a-4468-b752-547e626d1c69
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_gpt
    insmod ext2
    set root='(/dev/sda,gpt5)'
    search --no-floppy --fs-uuid --set=root d2976126-443a-4468-b752-547e626d1c69
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=d2976126-443a-4468-b752-547e626d1c69 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda4 during installation
UUID=67C0-5CD5  /boot/efi       vfat    defaults        0       1
# swap was on /dev/sda6 during installation
#UUID=13dd6f25-fd54-42bf-a8ba-75200d196383 none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0

=================== sda5: Location of files loaded by Grub: ===================


  60.6GB: boot/grub/grub.cfg
  62.6GB: boot/initrd.img-2.6.38-8-generic
  60.7GB: boot/vmlinuz-2.6.38-8-generic
  62.6GB: initrd.img
  60.7GB: vmlinuz

=========================== sdc1/boot/grub/grub.cfg: ===========================


if loadfont /boot/grub/font.pf2 ; then
    set gfxmode=auto
    insmod efi_gop
    insmod efi_uga
    insmod gfxterm
    terminal_output gfxterm
fi

set menu_color_normal=white/black
set menu_color_highlight=black/light-gray

menuentry "Try Ubuntu without installing" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Install Ubuntu" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Check disc for defects" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  boot=casper integrity-check quiet splash --
    initrd    /casper/initrd.lz
}

=================== sdc1: Location of files loaded by Grub: ===================


    ??GB: boot/grub/grub.cfg
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdc1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 08 60 04  |.X.SYSLINUX...`.|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 80 00 00 00  |........?.......|
00000020  80 7f 77 00 d0 1d 00 00  00 00 00 00 02 00 00 00  |..w.............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 b2 f2 d9 90 4e  4f 20 4e 41 4d 45 20 20  |..)....NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 fa fc 31 c9 8e d1  |  FAT32   ..1...|
00000060  bc 76 7b 52 06 57 1e 56  8e c1 b1 26 bf 78 7b f3  |.v{R.W.V...&.x{.|
00000070  a5 8e d9 bb 78 00 0f b4  37 0f a0 56 20 d2 78 1b  |....x...7..V .x.|
00000080  31 c0 b1 06 89 3f 89 47  02 f3 64 a5 8a 0e 18 7c  |1....?.G..d....||
00000090  88 4d bc 50 50 50 50 cd  13 eb 5c 8b 55 aa 8b 75  |.M.PPPP...\.U..u|
000000a0  a8 c1 ee 04 01 f2 81 fa  b7 07 73 2b f6 45 b4 7f  |..........s+.E..|
000000b0  75 25 38 4d b8 74 20 66  3d 21 47 50 54 75 10 80  |u%8M.t f=!GPTu..|
000000c0  7d b8 ed 75 0a 66 ff 75  ec 66 ff 75 e8 eb 0f 51  |}..u.f.u.f.u...Q|
000000d0  51 66 ff 75 bc eb 07 51  51 66 ff 36 1c 7c b4 08  |Qf.u...QQf.6.|..|
000000e0  cd 13 72 13 20 e4 75 0f  c1 ea 08 42 89 16 1a 7c  |..r. .u....B...||
000000f0  83 e1 3f 89 0e 18 7c fb  bb aa 55 b4 41 8a 16 74  |..?...|...U.A..t|
00000100  7b cd 13 72 10 81 fb 55  aa 75 0a f6 c1 01 74 05  |{..r...U.u....t.|
00000110  c6 06 45 7d 00 66 b8 00  40 18 00 66 ba 00 00 00  |..E}.f..@..f....|
00000120  00 bb 00 7e e8 10 00 66  81 3e 24 7e d4 ff 73 72  |...~...f.>$~..sr|
00000130  75 76 ea 38 7e 00 00 66  03 06 60 7b 66 13 16 64  |uv.8~..f..`{f..d|
00000140  7b b9 10 00 eb 2b 66 52  66 50 06 53 6a 01 6a 10  |{....+fRfP.Sj.j.|
00000150  89 e6 66 60 b4 42 e8 7f  00 66 61 8d 64 10 72 01  |..f`.B...fa.d.r.|
00000160  c3 66 60 31 c0 e8 70 00  66 61 e2 da c6 06 45 7d  |.f`1..p.fa....E}|
00000170  2b 66 60 66 0f b7 36 18  7c 66 0f b7 3e 1a 7c 66  |+f`f..6.|f..>.|f|
00000180  f7 f6 31 c9 87 ca 66 f7  f7 66 3d ff 03 00 00 77  |..1...f..f=....w|
00000190  17 c0 e4 06 41 08 e1 88  c5 88 d6 b8 01 02 e8 37  |....A..........7|
000001a0  00 66 61 72 01 c3 e2 c9  31 f6 8e d6 bc 68 7b 8e  |.far....1....h{.|
000001b0  de 66 8f 06 78 00 be df  7d e8 09 00 31 c0 cd 16  |.f..x...}...1...|
000001c0  cd 19 f4 eb fd 66 60 ac  20 c0 74 09 b4 0e bb 07  |.....f`. .t.....|
000001d0  00 cd 10 eb f2 66 61 c3  8a 16 74 7b cd 13 c3 42  |.....fa...t{...B|
000001e0  6f 6f 74 20 65 72 72 6f  72 0d 0a 00 00 00 00 00  |oot error.......|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdb

---

### Post by legoman666 on 2011-04-29
I installed 10.10 alongside Win7 using the wubi installer and then upgraded it to 11.04. It works great. I get a list of which to load when I boot the machine and both of them work. When I upgraded from 10.10 to 11.04, the graphics didn't work until I installed fglrx.

---

### Post by mavster on 2011-04-29
Hi everybody,

I wanted to be able to get video acceleration to play 1080p files.

I have tried 11.04 final in both 32 and 64 bit versions but I have problem with xvba.....it says it cannot be installed due to broken packages but when I try to fix it it gives me an error.

So I have tried this:

Installed 64bit version (Might work with 32bit too)
Did NOT install Ati drivers from repository but used the ones from the ATi website instead.
Installed xvba and libva1 from splitted desktop.....latest version (Feb 26th if I remember)

Vainfo from splitted desktop libva1 works (The one from repos is giving me an error)

Now when I launch VLC with GPU accel enabled I can play 1080p files with the CPU barely reaching 50%.

The problem is that now I am having a bunch of other errors......

Has anybody been able to get GPU video accel without errors?

---

### Post by link141 on 2011-04-29
> **mavster said:**
> Hi everybody,

I wanted to be able to get video acceleration to play 1080p files.

I have tried 11.04 final in both 32 and 64 bit versions but I have problem with xvba.....it says it cannot be installed due to broken packages but when I try to fix it it gives me an error.

So I have tried this:

Installed 64bit version (Might work with 32bit too)
Did NOT install Ati drivers from repository but used the ones from the ATi website instead.
Installed xvba and libva1 from splitted desktop.....latest version (Feb 26th if I remember)

Vainfo from splitted desktop libva1 works (The one from repos is giving me an error)

Now when I launch VLC with GPU accel enabled I can play 1080p files with the CPU barely reaching 50%.

The problem is that now I am having a bunch of other errors......

Has anybody been able to get GPU video accel without errors?

I was having the same issue with the libva1 packages in the Repos and modified the dependencies of one problematic package to install everything (it pointed to an obsolete package).  However, the libva packages from the repositories still did not work.

I'm glad to hear that you got XvBA working with the latest packages as I was going to install from source next.

What kinds of errors are you getting? They probably can't be too bad if you can watch 1080p videos without issue.

---

### Post by mavster on 2011-04-30
> **link141 said:**
> I was having the same issue with the libva1 packages in the Repos and modified the dependencies of one problematic package to install everything (it pointed to an obsolete package).  However, the libva packages from the repositories still did not work.

I'm glad to hear that you got XvBA working with the latest packages as I was going to install from source next.

What kinds of errors are you getting? They probably can't be too bad if you can watch 1080p videos without issue.

Biggest problem is that I cannot install new software from the software center since it is telling me that I need to fix broken packages.....which are indeed xvba and libva from splitted desktop :(

---

### Post by link141 on 2011-04-30
> **mavster said:**
> Biggest problem is that I cannot install new software from the software center since it is telling me that I need to fix broken packages.....which are indeed xvba and libva from splitted desktop :(

Did you install from the sources available at splitted-desktop, or did you find Debian packages?  If you installed from packages, they may be pointing to package dependencies that are newer than the versions in the repositories.

If the latter is the case, there are a few ways to fix this (after properly removing the problem packages):
1) You could build from source and bypass the packaging system altogether.
2) Build from source and make packages with the check-install program
3) Somehow hack the dependencies for the new packages. I did this for the broken package in the repos (that still doesn't work :roll:), but it required me to build a new package from the source package.

I plan on building from source and making packages with check-install (or even try making real packages) when I'm done with college finals.  If I get around to it soon enough, I'll let you know what happens.

---

### Post by jwdoll on 2011-05-01
Have others noticed that with 11.04 and fglrx that dragging windows is very choppy/low framerate and with screen tearing? The default driver was much smoother, but when coming back from suspend the taskbar/launcher failed to refresh until compiz --replace.

---

### Post by wm_brant on 2011-05-02
> **wm_brant said:**
> I've been following this thread since I received my X120e, but I figured that I could wait until 11.04 was released.

So - how does the official release install and run? Any problems?

I'll answer my own question - the install went without a hitch*, and everything *I use* seems to be working fine. I use my X120e for writing and light web browsing, and all that is working well. Wireless works, the SD card reader reads and writes. Moving windows around isn't particularly smooth, but I'm running the base install, with the standard AMD blob. I expect that following the tips here will take care of that issue.

I've not checked out HD video, and I personally don't use either the camera or the mic, so I have no idea if those work or not.

* Everything that is, once I found out that 11.04 is having problems installing off of SanDisk thumb drives that have the U3 software on them. Once I found out about that issue and removed the U3 software, all went well. After only about 10 hours of hair-pulling...

---

### Post by jwdoll on 2011-05-02
> **jwdoll said:**
> Have others noticed that with 11.04 and fglrx that dragging windows is very choppy/low framerate and with screen tearing? The default driver was much smoother, but when coming back from suspend the taskbar/launcher failed to refresh until compiz --replace.
Oh, if you were having the problem with choppy window moving/compiz effects, this link has a super simple fix.

[http://ubuntu4beginners.blogspot.com/2011/04/unity-choppy-with-ati-graphics-card-and.html](http://ubuntu4beginners.blogspot.com/2011/04/unity-choppy-with-ati-graphics-card-and.html)

---

### Post by mrsfixit on 2011-05-03
> **wm_brant said:**
> I'll answer my own question - the install went without a hitch*, and everything *I use* seems to be working fine. I use my X120e for writing and light web browsing, and all that is working well. .

How well does that machine work on a site like the Huffington Post?

I am using an Acer netbook with one of the first generation single core Atom cpu's and that site brings this thing to it's knees. It's nearly unusable. 

I am hoping the X120e will be quite a bit faster...

You're using 11.04- doesn't that one have a different interface? Can one install 11.04 with just a plain Gnome desktop like with with previous versions?

Just wondering, and glad to hear everything is working for you. :P

---

### Post by wm_brant on 2011-05-03
> **mrsfixit said:**
> How well does that machine work on a site like the Huffington Post?

I am using an Acer netbook with one of the first generation single core Atom cpu's and that site brings this thing to it's knees. It's nearly unusable. 

I am hoping the X120e will be quite a bit faster...

You're using 11.04- doesn't that one have a different interface? Can one install 11.04 with just a plain Gnome desktop like with with previous versions?

Just wondering, and glad to hear everything is working for you. :P

Tthe Huffington Post worked  fine on the X120e (it did not feel much different than on my large desktop  system), but please keep in mind that I use Firefox with AdBlock Plus,  so I would not see any flash ads. 

I even busted out my old Dell Mini 9 which the X120e replaced. The Mini 9 is very comparable to your Acer, both being early Atom-based netbooks. It had no issues with the Huffington Post website although again, I was blocking ads.

I will say that 11.04 on the Mini 9 is noticeably faster than 10.10 Netbook Remix was. 

I do have a couple of recommendations for you:
1. If you are not currently using AdBlock Plus, give it a try. You might not feel the need for a new computer quite as much.
2. The E-350 processor and video combination is faster than an  Atom-based system, but it is slower than any other current non-Atom  based system. The E-350 provides more than adequate power for what I  need, along with the ability to run a long time on batteries. If you  really don't need the long battery life, you should probably consider a  system with a little more 'oomph'. Having said that, I really like my  X120e. But then again, I'm responding to your message on my big four-CPU  desktop system. I don't have to live with the X120e all the time...

  -- Bill

---

### Post by mrsfixit on 2011-05-04
> **wm_brant said:**
> Tthe Huffington Post worked  fine on the X120e (it did not feel much different than on my large desktop  system), but please keep in mind that I use Firefox with AdBlock Plus,  so I would not see any flash ads. 

I even busted out my old Dell Mini 9 which the X120e replaced. The Mini 9 is very comparable to your Acer, both being early Atom-based netbooks. It had no issues with the Huffington Post website although again, I was blocking ads.

I will say that 11.04 on the Mini 9 is noticeably faster than 10.10 Netbook Remix was. 

I do have a couple of recommendations for you:
1. If you are not currently using AdBlock Plus, give it a try. You might not feel the need for a new computer quite as much.
2. The E-350 processor and video combination is faster than an  Atom-based system, but it is slower than any other current non-Atom  based system. The E-350 provides more than adequate power for what I  need, along with the ability to run a long time on batteries. If you  really don't need the long battery life, you should probably consider a  system with a little more 'oomph'. Having said that, I really like my  X120e. But then again, I'm responding to your message on my big four-CPU  desktop system. I don't have to live with the X120e all the time...

  -- Bill

Hi Bill, thanks for the response. :)

I do use Firefox and AdBlock. I also use Flashblock.

But I am not using 11.04, that netbook is still running 9.10 because I haven't gotten around to upgrading it. That's 9.10 full version- NOT netbook remix... maybe the netbook remix is faster?

How much RAM do you have in your Mini 9? I only have 1 GB, which I never thought was enough.

I would prefer a system with more "oomph". I'd really like the Alienware M11x or the 11" Acer Timeline X with the core i7, but the hybrid nVidia video card on those systems is troublesome with Ubuntu from what I read on these forums.

I've thought about it, and I just *can't* go back to having to use Windows... :razz:

I would prefer a core i, even a core i3, but I'd like to stick with something 11.6", and something that will definitely work with Ubuntu. I was looking at a little HP I think it was, but it lacked an ethernet port and that was a deal breaker for me.

---

### Post by wm_brant on 2011-05-05
> **mrsfixit said:**
> Hi Bill, thanks for the response. :)

I do use Firefox and AdBlock. I also use Flashblock.

But I am not using 11.04, that netbook is still running 9.10 because I haven't gotten around to upgrading it. That's 9.10 full version- NOT netbook remix... maybe the netbook remix is faster?

How much RAM do you have in your Mini 9? I only have 1 GB, which I never thought was enough.

I would prefer a system with more "oomph". I'd really like the Alienware M11x or the 11" Acer Timeline X with the core i7, but the hybrid nVidia video card on those systems is troublesome with Ubuntu from what I read on these forums.

I've thought about it, and I just *can't* go back to having to use Windows... :razz:

I would prefer a core i, even a core i3, but I'd like to stick with something 11.6", and something that will definitely work with Ubuntu. I was looking at a little HP I think it was, but it lacked an ethernet port and that was a deal breaker for me.

My Mini 9 has the early-Atom-limited max of 2GB in it. I kept an eye on RAM usage in the Mini 9, and 2GB has always been adequate. However, I did upgrade the X120e to 4GB.

I agree with you on the 11" size factor. The Mini 9 had  - not surprisingly - a 9" display, which meant it had a 9" keyboard. I can't type on a 9" keyboard - I always used an external keyboard that was 3" wider than the computer. The X120e's 11" keyboard is very good, and big enough to type on comfortably. I would not want to go any smaller, and (to my way of thinking) there's no need for the keyboard  be any larger.

  -- Bill

---

### Post by mrsfixit on 2011-05-05
> **wm_brant said:**
> My Mini 9 has the early-Atom-limited max of 2GB in it. I kept an eye on RAM usage in the Mini 9, and 2GB has always been adequate. However, I did upgrade the X120e to 4GB.

I agree with you on the 11" size factor. The Mini 9 had  - not surprisingly - a 9" display, which meant it had a 9" keyboard. I can't type on a 9" keyboard - I always used an external keyboard that was 3" wider than the computer. The X120e's 11" keyboard is very good, and big enough to type on comfortably. I would not want to go any smaller, and (to my way of thinking) there's no need for the keyboard  be any larger.

  -- Bill

I always liked the 9" display, but then as a female, I have wee little hands and I can manage well enough with the tiny keyboard. :)

I only have 1 GB of ram, that could be causing some issues. I will have to check the system monitor next time I load the Huffington Post site and see how the memory usage is.

I have a 5 year old 14" Acer Aspire notebook with a single core 900 Mhz Celeron. That one is running 9.04, and it's much, much faster than the netbook but I put 2 GB's of ram in that system. So maybe the extra gig makes a difference.

Can you play Hulu videos on your x120e? How well do they play? I can't play them at all with the netbook. They stutter and are very choppy. The bigger Acer notebook plays them just fine.

I agree with you about the 4 GB's of ram. Any machine I get will either have that amount, or I will upgrade. 

Upgrading ram on a laptop is soooo easy... it usually takes me longer to get it out of the box than it does to install it... LOL

Thank you for your responses, you are helping me out quite a bit. :)

---

### Post by wm_brant on 2011-05-05
> **mrsfixit said:**
> I always liked the 9" display, but then as a female, I have wee little hands and I can manage well enough with the tiny keyboard. :)

I only have 1 GB of ram, that could be causing some issues. I will have to check the system monitor next time I load the Huffington Post site and see how the memory usage is.

I have a 5 year old 14" Acer Aspire notebook with a single core 900 Mhz Celeron. That one is running 9.04, and it's much, much faster than the netbook but I put 2 GB's of ram in that system. So maybe the extra gig makes a difference.

Can you play Hulu videos on your x120e? How well do they play? I can't play them at all with the netbook. They stutter and are very choppy. The bigger Acer notebook plays them just fine.

I agree with you about the 4 GB's of ram. Any machine I get will either have that amount, or I will upgrade. 

Upgrading ram on a laptop is soooo easy... it usually takes me longer to get it out of the box than it does to install it... LOL

Thank you for your responses, you are helping me out quite a bit. :)

I tried to play a Hulu video on the X120e, but Hulu was complaining about the ads not displaying properly - probably because my wireless connection isn't super fast here in the kitchen. 

I went to YouTube instead (they both use Flash) and played an HD video -  'Epic Mealtime' where someone made a grilled bacon cheese sandwich tower - deep fat fried and slathered in cheese whiz no less. I watched it in 720p and it rendered perfectly on the X120e - I did not see any skips.

Hope this helps - please let me know if I can be of more assistance.

  -- Bill

---

### Post by mrsfixit on 2011-05-05
> **wm_brant said:**
> I tried to play a Hulu video on the X120e, but Hulu was complaining about the ads not displaying properly - probably because my wireless connection isn't super fast here in the kitchen. 

I went to YouTube instead (they both use Flash) and played an HD video -  'Epic Mealtime' where someone made a grilled bacon cheese sandwich tower - deep fat fried and slathered in cheese whiz no less. I watched it in 720p and it rendered perfectly on the X120e - I did not see any skips.

Hope this helps - please let me know if I can be of more assistance.

  -- Bill

Thanks very much Bill. :)

---

### Post by Crath on 2011-05-06
I am having an issue where the laptop keeps freezing. I've replaced the hard drive with a brand new one from lenovo as well as the ram. Syslog doesn't have anything at all when it freezes. Ctrl+alt+backspace doesn't work when it happens. Running 11.04 final. Same thing happened when I ran 11.04 beta 1.

Any suggestions? Thanks

---

### Post by KEMATSE2 on 2011-05-06
Crath, I have been having the same problem with my x120e as well. Posts in this thread have lead my to believe that these freezes are a caused by the realtek wireless firmware. I've tried a range of linux distributions and have come to the conclusion that it is an issue limited to the 2.6.28 kernel and it's own support of the hardware because I had the same issue with Arch. I'd suggest to either try Ubuntu 10.10 or perhaps Crunchbang Statler (I like openbox). It might be possible to blacklist the offending modules and build the ones from the realtek website but I haven't tried it. I'm personally waiting until a bug fix comes through so I can move to the new kernel and use all the features of my notebook without a headache.

---

### Post by jankyHellface on 2011-05-06
> **Crath said:**
> I am having an issue where the laptop keeps freezing. 

It's a problem with the realtek wireless driver. There's a bug report [here]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/769812"). Post there to see if we can get this bug more attention.

---

### Post by elomire678 on 2011-05-06
Maybe someone might be able to figure this out here, but on my x120e with Ubuntu Natty my microphone stops working after about 2 minutes of use. I then have to reboot to get it to start working again. Quite annoying.

---

### Post by Crath on 2011-05-07
> **jankyHellface said:**
> It's a problem with the realtek wireless driver. There's a bug report [here]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/769812"). Post there to see if we can get this bug more attention.

I've subscribed and marked the bug as "affecting me too".

> **KEMATSE2 said:**
> Crath, I have been having the same problem with my x120e as well. Posts in this thread have lead my to believe that these freezes are a caused by the realtek wireless firmware. I've tried a range of linux distributions and have come to the conclusion that it is an issue limited to the 2.6.28 kernel and it's own support of the hardware because I had the same issue with Arch. I'd suggest to either try Ubuntu 10.10 or perhaps Crunchbang Statler (I like openbox). It might be possible to blacklist the offending modules and build the ones from the realtek website but I haven't tried it. I'm personally waiting until a bug fix comes through so I can move to the new kernel and use all the features of my notebook without a headache.

Is there any way to "disable" this module from running? I would be ok for now if I could keep the computer from freezing at work, since I use ethernet only. Thanks!

Also, people have mentioned this may be a kernel panic. Wouldn't I see this in syslog?

---

### Post by jankyHellface on 2011-05-07
> **Crath said:**
> 
Is there any way to "disable" this module from running? I would be ok for now if I could keep the computer from freezing at work, since I use ethernet only. Thanks!

Can't you disable wireless altogether through network manager (also by using fn+f5) while using ethernet? If you are not connecting to wireless networks, and are still seeing your machine crash, then it might be another issue.

---

### Post by cha5on on 2011-05-08
> **Crath said:**
> Is there any way to "disable" this module from running? I would be ok for now if I could keep the computer from freezing at work, since I use ethernet only. Thanks!

Also, people have mentioned this may be a kernel panic. Wouldn't I see this in syslog?

You should be able to click on the NetworkManager icon and disable wireless.  When I've done this, I haven't had problems with the system locking up.

I also haven't been seeing useful information on lockup in the system logs, but maybe I've just forgotten where to look, or perhaps the default setup doesn't log this kind of thing (doubtful).

---

### Post by elomire678 on 2011-05-08
> **Crath said:**
> I've subscribed and marked the bug as "affecting me too".



Is there any way to "disable" this module from running? I would be ok for now if I could keep the computer from freezing at work, since I use ethernet only. Thanks!

Also, people have mentioned this may be a kernel panic. Wouldn't I see this in syslog?

Why not just disable the wireless in the bios? I ran into the problems with the wifi locking up mine. Luckily I had an old Dell Mini 10v sitting around and replaced the Realtek card in my x120e with its Broadcom card (after flashing the cracked uefi bios). Works perfectly now. Unfortunately that's not a fix for everyone else, but if you have another MiniPCIe wifi card sitting around. Otherwise disable it in the bios and just use ethernet.

---

### Post by jankyHellface on 2011-05-08
> **elomire678 said:**
> Why not just disable the wireless in the bios? I ran into the problems with the wifi locking up mine. Luckily I had an old Dell Mini 10v sitting around and replaced the Realtek card in my x120e with its Broadcom card (after flashing the cracked uefi bios). Works perfectly now. Unfortunately that's not a fix for everyone else, but if you have another MiniPCIe wifi card sitting around. Otherwise disable it in the bios and just use ethernet.

This is an option I am considering. With Intel 5100 mini-pcie cards going for ~$10 on ebay, it would make sense just to order a new card instead of having to deal with buggy drivers.

---

### Post by Crath on 2011-05-08
> **elomire678 said:**
> Why not just disable the wireless in the bios?

I need to use the WiFi at home.


On an unrelated note, I noticed when I would put the brightness above about 80% the colors would change. Some greys would even go to white, it was weird. You can fix this by disabling "vari-bright" in the power play section of catalyst control center.

---

### Post by legoman666 on 2011-05-09
I let Ubuntu 11.04 update itself a few days ago. Since then I have not been able to get the proprietary graphics drivers to work. I was running 11.3. I just updated to 11.5 and it still doesn't work. After Ubuntu boots I get dumped to a command prompt. I assume either the kernel or x-org was updated and this broke the drivers. Anyone know how to fix?

---

### Post by link141 on 2011-05-10
> **Crath said:**
> On an unrelated note, I noticed when I would put the brightness above about 80% the colors would change. Some greys would even go to white, it was weird. You can fix this by disabling "vari-bright" in the power play section of catalyst control center.

I am having the same problem on Kubuntu Natty.  I'm glad you found a solution as this is annoying.

Not sure if this is related, but I also run into erratic behavior when changing the brightness in which the the display brightness will go all the way down if I try to turn it down one notch or visa versa.  Also, sometimes the brightness won't change when I use the FN keys (but the on-screen brightness indicator still shows up).  At other times, I can change the brightness fine.  I don't know if this only occurs an Kubuntu.

---

### Post by dfmutz on 2011-05-10
Hey is anyone else having weird screen issues with the 11.5 flgrx drivers from AMD? I installed it yesterday and when I booted up it said I could only run classic. Then I looked at the catalyst menu but didn't change anything which caused it to go to the login menu. I then logged back in and had the unity interface but I have some odd lines at the top of my screen. Anyone else have this issue?? In the mena time I am rolling back to 11.4 to see if it helps.

---

### Post by thinkpadx on 2011-05-10
> **jankyHellface said:**
> It's a problem with the realtek wireless driver. There's a bug report [here]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/769812"). Post there to see if we can get this bug more attention.


I'm sure this isn't the right way to solve this issue. I was able to get wireless working (so far so good) by following the directions here: [http://ubuntuforums.org/showpost.php?p=10783011&postcount=3]("http://ubuntuforums.org/showpost.php?p=10783011&postcount=3")

One small change I did was after adding the repository and closing the window.  I went back in and edited the repository to pull maverick instead of natty.  It installed just fine with no errors and wireless is no longer freezing my computer when trying to load the rtl8192ce module.

---

### Post by JustinForce on 2011-05-15
> **Crath said:**
> On an unrelated note, I noticed when I would put the brightness above about 80% the colors would change. Some greys would even go to white, it was weird. You can fix this by disabling "vari-bright" in the power play section of catalyst control center.

Vari-Bright™ was driving me ***crazy!*** Thank you so much for this tip! You don't know how much you've helped me.

---

### Post by jankyHellface on 2011-05-15
> **thinkpadx said:**
> I'm sure this isn't the right way to solve this issue. I was able to get wireless working (so far so good) by following the directions here: [http://ubuntuforums.org/showpost.php?p=10783011&postcount=3]("http://ubuntuforums.org/showpost.php?p=10783011&postcount=3")

This seems to be working out pretty well. I switched to xfce today and did this after... Haven't had a crash yet. Thanks a lot for the tip!

---

### Post by schimschone on 2011-05-16
> **jankyHellface said:**
> This seems to be working out pretty well. I switched to xfce today and did this after... Haven't had a crash yet. Thanks a lot for the tip!

I keep getting the following error:

"Failed to fetch [http://ppa.launchpad.net/lexical/hwe-wireless/ubuntu/dists/natty/main/source/Sources](http://ppa.launchpad.net/lexical/hwe-wireless/ubuntu/dists/natty/main/source/Sources)  404  Not Found
Failed to fetch [http://ppa.launchpad.net/lexical/hwe-wireless/ubuntu/dists/natty/main/binary-amd64/Packages](http://ppa.launchpad.net/lexical/hwe-wireless/ubuntu/dists/natty/main/binary-amd64/Packages)  404  Not Found
Some index files failed to download. They have been ignored, or old ones used instead."

And when I search for rtl8192ce-dkms nothing comes up.

Thanks in advance.

---

### Post by jankyHellface on 2011-05-16
> **schimschone said:**
> I keep getting the following error:

"Failed to fetch"

And when I search for rtl8192ce-dkms nothing comes up.

Did you switch natty to maverick in your sources? Just did a apt-get update and it pulled from the server.

---

### Post by link141 on 2011-05-16
An update on my progress with this machine:

Haven't got XvBA working yet.  It appears I have the driver installed correctly (after much work), but VLC crashes when I try to use GPU acceleration.  I built a special MPlayer with VAAPI support (from splitted-desktop), but that crashes as well.  I don't think I have all of the required packages installed correctly...  I'll try with another distro like Arch and see what happens.

Since this machine doesn't have a disk drive, I'm using CDEMU with the few games that I need to use cd with.  The official PPA doesn't have packages for Natty yet, so I built 64-bit Natty packages following the instructions on the CDEMU website.  Everything works correctly except for the gcdemu frontend (which isn't required).  If anyone wants these packages, let me know (they are around 1MB all-together).

I configured the track point using the files in /sys/ and an .xsessionrc file.  I made the trackpoint more sensitive and set the middle button to scroll.  I made a boot script to set the sensitivity and made it an init script, however, this script doesn't work and I can't find out why.

Most games seem to work fine on this machine, but Mupen64plus gets weird video behavior (stuttering, slow performance, etc).  Need to investigate this more as Project64 can emulate the same games very well on Win7 and in Wine.

As for the wireless, I have my thinkpad connected with ethernet and wireless disabled to avoid lockups.  I haven't tried the above workaround yet, but I wonder if the drivers I compiled for Maverick are different than the stock drivers.  If so, then maybe we can use the former as another workaround.

---

### Post by schimschone on 2011-05-17
Okay so here's the lowdown on my x120e, 

I installed the wifi fix tonight (appreciate the help Janky), but now it appears to have become less stable.. freezing when the screen-saver comes up, a behavior that hadn't shown itself prior. Additionally my headphone jack doesn't seem to work, and I can't seem to print with my HP OfficeJet 6500A+.

Hit me with any solutions you have, I have to relearn my whole linux repertoire every 3-years or so.. because once I have it stable I don't ever have to mess with my boxes. 

Any help would be appreciated.

---

### Post by devguy on 2011-05-17
> **link141 said:**
> An update on my progress with this machine:

Haven't got XvBA working yet.  It appears I have the driver installed correctly (after much work), but VLC crashes when I try to use GPU acceleration.  I built a special MPlayer with VAAPI support (from splitted-desktop), but that crashes as well.  I don't think I have all of the required packages installed correctly...  I'll try with another distro like Arch and see what happens.

I have the DM1z, and I added the splitted systems libva + others to my system, as well as got special vaapi builds of vlc and xbmc.  What I noticed, is that if I run either of those programs and then try to watch a video that should be hardware accelerated, the application crashes.  However, if I launch either application from the terminal, then it works perfect.  So, for the short term, I just made new icons on the desktop that launch the program in the terminal.

Any idea why it should work from the terminal, and not otherwise?

---

### Post by D3C3PT1ON on 2011-05-17
> **thinkpadx said:**
> I'm sure this isn't the right way to solve this issue. I was able to get wireless working (so far so good) by following the directions here: [http://ubuntuforums.org/showpost.php?p=10783011&postcount=3]("http://ubuntuforums.org/showpost.php?p=10783011&postcount=3")

One small change I did was after adding the repository and closing the window.  I went back in and edited the repository to pull maverick instead of natty.  It installed just fine with no errors and wireless is no longer freezing my computer when trying to load the rtl8192ce module.

i installed the driver and i'm still having random crashes from the wifi. I notice that sometimes when opening up my laptop from sleep it will stay black and unresponsive i think it maybe due to the wifi driver trying to reconnect and i have also notice that one time when the screen froze my wifi icon was frozen into the circle logo trying to reconnect; i think it it must of lost connection and was trying to connect before crashing. And i also notice more frequent crashes in my schools network compare to my home network.

---

### Post by sophistihip on 2011-05-17
So my x120e came in today. I got the e350, 4gb ram, bluetooth, 6 cell. I booted into Windows 7 (Pro) and clicked around for a bit. I downloaded the v1.12 bios update in exe format, since I used my single usb stick to create an ubuntu startup disk. The bios install went smoothly. I had to hit enter at startup and enter the bios config in order to move my usb disk up in the boot order since it didn't show it in the boot option list (it just showed harddisk and network boot). I left everything else default, including EFI first. I installed 11.04 desktop i386.

I tried to do a manual partition because I had read that Ubuntu wants a /boot/efi partition of type efi, or something like that, but I didn't see any way to do that, so I did a standard full disk install. This install went smoothly and finished successfully. Wireless works, bluetooth works, fn buttons for brightness, volume, mute, disable radio, check battery status all work. I'm willing to bet the rest work too but haven't tested them yet. I installed the proprietary fglrx drivers as suggested in additional drivers even though I heard they wouldn't work. They work just fine for me. Suspend works, haven't tried hibernate since I never use it.

tl;dr everything went better than expected.

That being said.. This machine still feels sluggish. I was able to play a 1080p xvid avi file in windows and while it was a bit... precarious, it worked, but now it struggles to play 720p smoothly.

Overall I like the machine, fit and finish is excellent, this is my first thinkpad. I do miss the gestures trackpad of my macbook pro. The screen is underwhelming, the color shift bothers me, and overall the machine feels much closer to a netbook than reviewers would have you believe. Still though, it's going to be a great fit for my needs :D I still can't believe that you actually get 5-6 hours of battery life out of this thing under use.

---

### Post by jankyHellface on 2011-05-18
> **schimschone said:**
> Okay so here's the lowdown on my x120e, 

I installed the wifi fix tonight (appreciate the help Janky), but now it appears to have become less stable.. 

Not sure about stability on my machine as I haven't had time to fully test it with my schools wifi (where 85% of my crashes occurred). But so far, my machine has been relatively solid.

In terms of your issue, if it's less stable I would say you can turn off the driver in the additional drivers dialog and/or just uninstall the driver through synaptic.

---

### Post by sophistihip on 2011-05-18
I'm having the intermittent issue where compiz is pinning my cpu at 100%. Anybody ran into this before? Maybe the fglrx drivers aren't working after all. I may try setting up the ones from AMD's site tonight.

I've read a lot that the proprietary drivers don't work. What does that mean exactly? Does it mean that they simply don't install? That they destabilise the system? That they work but don't provide hardware acceleration? I'm trying to figure out the best way to get hardware acceleration working. What options do we have on linux right now. I've read about UVD2 and UVD3 as well as xvba. What is the best/current solution?

It appears that I'm running v 8.84.6, I'm not sure how that correlates to the 11.x series of numbers.

---

### Post by lakerssuperman on 2011-05-19
For those that are having sluggish performance and slow window dragging with the Catalyst driver, I have set "Tear Free" in the Catalyst Control Center and disabled "Sync to Vblank" in the Compiz Settings manager and I have a smooth tear free desktop.  When I leave both enabled, the desktop gets very slow and laggy.  You might want to give this a try if you haven't yet.

---

### Post by sophistihip on 2011-05-19
Well I spent a day working on it and reading up on the state of fusion on linux. Out of the box I had a great desktop experience with the proprietary drivers, but the system choked even on 480p youtube videos when they were in full screen. There's a lot of talking about this and that with graphics drivers but what nobody seems to make clear is the fact that there is no gpu accelerated anything on linux at this time, aside from maybe specific support in mplayer or vlc if you jump through a lot of hoops and roll everything yourself. I really hate giving up, but I don't have to work on this machine so I'm going to stick with windows until media support strengthens a bit, maybe in time for 11.10.

---

### Post by lakerssuperman on 2011-05-19
As long as you have VAAPI installed and the XVBA-Video package from Splitted Desktop 

[http://www.splitted-desktop.com/~gbeauchesne/xvba-video/](http://www.splitted-desktop.com/~gbeauchesne/xvba-video/)

you should be able to get acceleration from any player that supports VAAPI, Mplayer (and it's various front ends like Gnome Mplayer, Smplayer), VLC and XBMC if you install it from 

[https://launchpad.net/~lars-opdenkamp/+archive/xbmc-pvr?field.series_filter=maverick](https://launchpad.net/~lars-opdenkamp/+archive/xbmc-pvr?field.series_filter=maverick))

Flash is still currently a no go, but there should be VAAPI support coming in Flash 10.3 in the near future.

Good luck with everything.

---

### Post by thinkpadx on 2011-05-20
For those of you having problems with video playback. I would check your BIOS version and upgrade if it's outdated.  There was a release that addressed some video playback issues.

From the BIOS release notes:
> Version 1.11
BIOS: 1.11 / ECP: 1.05
(New) Increase the dedicated video memory size from 64MB to 384MB to improve the performance of video playback.


You can download the BIOS upgrade here: [Lenovo Support - Thinkpad x120e]("http://www-307.ibm.com/pc/support/site.wss/product.do?subcategoryind=0&familyind=591133&brandind=10&doccategoryind=0&modelind=0&doctypeind=9&validate=true&partnumberind=0&template=/productpage/landingpages/productPageLandingPage.vm&operatingsystemind=49979&machineind=0")

If I remember correctly, I used the .iso and burned it to a USB drive and booted it.  It was tricky but once updated everything seemed to run smoother.

Looks like there's also another update passed the one I installed.  I'm still on version 1.11 so I guess it's time for another BIOS upgrade. If I have any problems I'll make sure to let everyone know.

---

### Post by afxmac on 2011-05-21
Got mine from the US after Easter (Lenovo does not sell it in Germany), got a German keyboard installed (easy) and added a 4GB module to beef it up to 6GB and it runs quite nicely (11.4, 64bit, ubuntu supplied OEM ati drivers) apart from a few quirks. It came with BIOS 1.11 already installed.

I use XFCE with a very thin skin to save screen space (Unity and Gnome are quite wasteful).

When waking up from sleep, it often shows the login prompt and just when I start to type the password, it goes to sleep again. Hitting FN wakes it up again and I can log in regularly.


The display gamut sucks and it is quite sensitive to viewing angle, but for a small portable it is ok.

I have calibrated/profiled the display with a ColorMunki (this is my travelling image tank) but every sleep looses the calibration setting in the X server resulting in the blue shifted display again. Just running gnome-color-manager once will load the calibration, but that has to be done after each resume....
(Profile is attached for those that want a more neutral display than the shipped state)

The hot-key display brightness has strange steps. between full brightness (160cd) and the next lower step there are 60cd, the next step down is then less than 20cd (measured with the ColorMunki).
Is there a way to adjust the brightness steps? My target would be 120cd...


I'd love to switch off the silly touchpad mouse buttons that are way too close to the edge, as in my typical usage scenarios the get constantly pressed by my belt or belly.
Have not found a way to do this, so I used gpointing-device-settings to switch it off and configure the trackpoint for scrolling. But that does not survive reboots/sleeps. And the scroll behaviour of the trackpoint works only in Gnome, not in XFCE....


The network (I use the shipped realtec driver for WLAN) seems to be sluggish in accepting connections when I try to SSH in. 
(I have a T61 running 10.10 that has no issues in this WLAN)
Outbound connections also often seem to have a longer delay for the initial connection than on my T61.


Sound works fine though I had to explicitly map the keys for mute and volume in XFCE.


Have not found a way yet to reliably see the grub menu. sometimes I can get it to show sometimes not. I wonder why my box has both grub-pc and grub-efi installed (my BIOS is set to EFI):
ii  grub-common                               1.99~rc1-13ubuntu3
ii  grub-efi                                  1.99~rc1-13ubuntu3 
ii  grub-efi-amd64                            1.99~rc1-13ubuntu3 
rc  grub-pc                                   1.99~rc1-13ubuntu3

Can I just nuke the pc version?

cheers
afx

---

### Post by link141 on 2011-05-22
> **afxmac said:**
> When waking up from sleep, it often shows the login prompt and just when I start to type the password, it goes to sleep again. Hitting FN wakes it up again and I can log in regularly.

I believe this is a problem with the open source radeon driver.  I'm using this driver on Arch Linux and am getting strange behavior coming out of sleep. However, on Kubuntu, I'm using the proprietary driver and sleep is working perfectly.

> **afxmac said:**
> 
I'd love to switch off the silly touchpad mouse buttons that are way too close to the edge, as in my typical usage scenarios the get constantly pressed by my belt or belly.
Have not found a way to do this, so I used gpointing-device-settings to switch it off and configure the trackpoint for scrolling. But that does not survive reboots/sleeps. And the scroll behaviour of the trackpoint works only in Gnome, not in XFCE....


If you only want to use the trackpoint, you can switch off only the touchpad and the lower buttons by entering: ```
synclient TouchpadOff=1
``` in a terminal.

You can also set the trackpoint to scroll by entering into a terminal:```

xinput set-int-prop "TPPS/2 IBM TrackPoint" "Evdev Wheel Emulation" 8 1
xinput set-int-prop "TPPS/2 IBM TrackPoint" "Evdev Wheel Emulation Button" 8 2
xinput set-int-prop "TPPS/2 IBM TrackPoint" "Evdev Wheel Emulation Timeout" 8 200

```

You can make these settings persistent by putting them into a file named .xsessionrc in your home directory.  This should work in any desktop environment on *ubuntu (but not on all distros).  I did this to enable trackpoint scrolling on Kubuntu.

Additionally, you can set the trackpoint sensitivity, speed, negative inertia, etc, by echoing values to files in the /sys/devices/platform/i8042/serio4/serio5/ directory:```

cd /sys/devices/platform/i8042/serio4/serio5/
sudo chmod ugo+rw speed sensitivity inertia
echo -n 120 > speed
echo -n 240 > sensitivity
...

```

You should be able to make these settings persistent by adding them to a boot script.  However, I've been having trouble getting ubuntu to do this as it uses upstart.  I do have it working on Arch Linux though.

Source: [_ThinkWiki_](http://www.thinkwiki.org/wiki/How_to_configure_the_TrackPoint)

> **afxmac said:**
> 
Have not found a way yet to reliably see the grub menu. sometimes I can get it to show sometimes not. I wonder why my box has both grub-pc and grub-efi installed (my BIOS is set to EFI):
ii  grub-common                               1.99~rc1-13ubuntu3
ii  grub-efi                                  1.99~rc1-13ubuntu3 
ii  grub-efi-amd64                            1.99~rc1-13ubuntu3 
rc  grub-pc                                   1.99~rc1-13ubuntu3

Can I just nuke the pc version?

If you are sure you have efi set up correctly, you should be able to just remove the pc version.  I had my thinkpad set to use the non-efi bootloader, and the ubuntu installer incorrectly set it to use efi.  So in my case, I removed the grub-efi and grub-efi-amd64 packages and installed grub-pc.  Now it uses the standard grub.

---

### Post by afxmac on 2011-05-22
> **link141 said:**
> I believe this is a problem with the open source radeon driver.  I'm using this driver on Arch Linux and am getting strange behavior coming out of sleep. However, on Kubuntu, I'm using the proprietary driver and sleep is working perfectly.
This is the ATI driver that Ubuntu supplies via the proprietary driver download, not the open source driver.

Thanks for the xinput commands.
I stumbled across loads of old xconf.org entries that lead to a non starting X server. This works.

> If you are sure you have efi set up correctly, you should be able to just remove the pc version.  I had my thinkpad set to use the non-efi bootloader, and the ubuntu installer incorrectly set it to use efi.  So in my case, I removed the grub-efi and grub-efi-amd64 packages and installed grub-pc.  Now it uses the standard grub.
Never played with an EFI bios before, so I am a bit reluctant to play in this area...

cheers
afx

---

### Post by srs5694 on 2011-05-22
[quote=afxmac]Have not found a way yet to reliably see the grub menu. sometimes I can get it to show sometimes not. I wonder why my box has both grub-pc and grub-efi installed (my BIOS is set to EFI):
ii grub-common 1.99~rc1-13ubuntu3
ii grub-efi 1.99~rc1-13ubuntu3
ii grub-efi-amd64 1.99~rc1-13ubuntu3
rc grub-pc 1.99~rc1-13ubuntu3[/quote]

What utility or command produced that output? The "ii" and "rc" strings that precede each entry are probably critical. My hunch is that "ii" means it's installed and "rc" means that it's not, but without knowing what program produced that output, I can't check the documentation to be sure of that.

My experience with Ubuntu 11.04 on an Intel motherboard with UEFI boot support is that GRUB 2 is unreliable. I've had much better luck with ELILO. There's a version in the Ubuntu repositories, but I installed the latest 3.14 version from source downloaded from the [Sourceforge download page.](http://sourceforge.net/projects/elilo/files/elilo/) If you install the package from the repositories, it includes a setup command that you can use like this:

```
elilo -b /dev/sda1 --autoconf --efiboot --root /dev/sda2 -v

```

Change /dev/sda1 to your EFI System Partition, if necessary (it probably is /dev/sda1), and /dev/sda2 to your Ubuntu root partition. The --efiboot option requires that you also install the efibootmgr package. This option sets up an EFI entry for ELILO. IIRC, you've got to unmount the EFI System Partition (normally mounted at /boot/efi) before you run this command.

Once this is done, you should re-mount the EFI System Partition ("sudo mount -a" should do this; verify it by typing "df" and looking for an entry for /boot/efi) and check (and perhaps modify) the ELILO configuration file, which will probably be /boot/efi/EFI/ubuntu/elilo.conf. Here's my elilo.conf file, as an example:

```

prompt
timeout=50
default=linux

image=vmlinuz-2.6.38-8-generic
        label=linux
        initrd=initrd.img-2.6.38-8-generic
        read-only
        root=/dev/sda2
        append="reboot=a,w"

```

This example boots just one kernel. Your file could be identical to this one, except you should modify your root= line to point to your Linux root filesystem. The "reboot=a,w" option works around a bug that causes the kernel to panic when rebooting the computer. You might or might not have the same bug, and you might not care about such a panic, so you might not need this.

If you decide to try this out, it's possible to do this with minimal risk because it's possible to install two EFI boot loaders side-by-side. In other words, your GRUB setup will continue to work if you try ELILO. (I don't know, however, if the Ubuntu packages for each conflict. If they do, you'd need to install outside of the Ubuntu package system.)

One caveat: ELILO loads Linux kernels, and AFAIK nothing else. Thus, if you're dual-booting with Windows, you'll need to use something else to launch Windows. If your EFI's options are convenient enough, its built-in boot loader should work. If not, you might give [rEFIt](http://refit.sourceforge.net/) a try. Installing it requires copying the /usr/lib/refit/refit directory tree to the EFI System partition's EFI subdirectory, and perhaps copying /usr/lib/refit/x64/refit.efi over /boot/efi/EFI/refit/refit.efi. You should then be able to launch it from your EFI, and if desired make it the default boot selector. When launched, rEFIt scans for other EFI boot loaders and shows them to you in a menu, so you'd be able to pick between Windows, ELILO, and GRUB (if you leave it installed). On my UEFI systems, rEFIt has some video glitches but works OK. Telling it to use text mode rather than its default GUI mode eliminates the video glitches.

---

### Post by jankyHellface on 2011-05-22
I've been using xubuntu for a bit and it seems to be quite a bit more solid than kubuntu 11.04. One nagging annoyance, however, is that the function keys don't work correctly. It seems xubuntu doesn't have the drivers for the x120e keyboard. 

Has anyone figured out how to get it to work properly? Is it a matter of installing lenovo-acpi? If so, where would I find a compiled version?

---

### Post by afxmac on 2011-05-23
> **jankyHellface said:**
> I've been using xubuntu for a bit and it seems to be quite a bit more solid than kubuntu 11.04. One nagging annoyance, however, is that the function keys don't work correctly. It seems xubuntu doesn't have the drivers for the x120e keyboard. 
It is not drivers but mapping. Use Settings->Keyboard->shortcuts to set up the missing keys.

cheers
afx

---

### Post by afxmac on 2011-05-23
> **srs5694 said:**
> What utility or command produced that output? The "ii" and "rc" strings that precede each entry are probably critical. My hunch is that "ii" means it's installed and "rc" means that it's not, but without knowing what program produced that output, I can't check the documentation to be sure of that.
Doooooh.

Having an RPM past, I keep forgetting that on debian systems cfg files still can hang around and be marked in the package listing (dpkg -l output), package is marked as removed but config files still present)

cheers
afx

---

### Post by languedoctor on 2011-05-23
Sorry if I missed it earlier (this thread *is* 30 pages, though :) )

Is there anyone here who has had success configuring ubuntu on the substantially similar Lenovo Ideapad S205?

Given the size of this thread, it seems like the safe move would just be to go for the x120e. Lenovo has some nice deals on the fusion-equipped Ideapad S right now, though...

---

### Post by jankyHellface on 2011-05-23
> **afxmac said:**
> It is not drivers but mapping. Use Settings->Keyboard->shortcuts to set up the missing keys.

Tried this out, but I get nothing with volume buttons using 'amixer set Master 10+ unmute". When I use the command in the terminal I receive the error "amixer: Unable to find simple control 'Master', 0" I then checked the sound prefs and the master channel is active in my setup. Not sure what's up here.

---

### Post by link141 on 2011-05-24
> **jankyHellface said:**
> Tried this out, but I get nothing with volume buttons using 'amixer set Master 10+ unmute". When I use the command in the terminal I receive the error "amixer: Unable to find simple control 'Master', 0" I then checked the sound prefs and the master channel is active in my setup. Not sure what's up here.

This laptop has what alsa sees as two sound cards.  The first one (card 0), is for the HDMI digital output and doesn't have a volume control (other than mute).  The second card (card 1) is the actual sound chip that controls the laptop speakers, headphone/mic jack, and internal microphone.

Try this for card 1:
```
amixer -c 1 set Master 10+ unmute
```

---

### Post by jankyHellface on 2011-05-24
> **link141 said:**
> 
Try this for card 1:
```
amixer -c 1 set Master 10+ unmute
```

That worked perfectly... thanks!

---

### Post by Timothy Benton on 2011-05-24
Maybe this is relevant to the UEFI booting issue:
[http://askubuntu.com/questions/37999/what-is-different-about-the-mac-iso-image](http://askubuntu.com/questions/37999/what-is-different-about-the-mac-iso-image)

---

### Post by mochalkin on 2011-05-25
Hello all!

Just a small note from a guy trying to install Ubuntu on x120e but fails..

I've just received my x120e with AMD E-240 processor, all stock. I'm having some hard times installing Ubuntu and Xubuntu 11.04 on the laptop - yesterday I had some crashes during installation (installer just crashed for no reason, I was dropped to console and laptop simply freezed). I tried all variants - i386 version, amd64. Finally somehow I managed to install Ubuntu 11.04 amd64 and even booted it fine. First thing I ran was system update and reboot afterwards and guess what, after system reboot system is not working anymore - I just see a blank black screen, monitor lid is ON. Nothing helps - I cannot get to GRUB prompt (I believe due to UEFI stuff).

So today I decided to give a try for Xubuntu 11.04 i386. I unpacked the installation ISO to USB flash drive (pen drive) I'm using to boot off installation process. The installation process began, and all seemed good, but near the end of process I got a pop-up saying that Ubiquity crashed. I opened console window (system was still running) and checked messaged in /var/log/partman and /var/log/syslog, I can't recall exactly what was there, but what I remember is that root filesystem (/) was mounted with "aufs" filesystem and it was 100% full (124mb), I could not create any file in /root for example.
Now I'm sitting here and trying to restart Xubuntu 11.04 installation, but it simply fails (but somehow it worked 20 minutes ago!). After booting I choose "English" as a language and then I'm choosing "Install Xubuntu", I see Xubuntu logo and then I get a console message:

Kernel panic - not syncing: Attempted to kill init!
Pid: 1, comm: init Not tainted 2.6.38-8-generic #42-Ubuntu
Call Trace:
... blah blah ..


How is it possible that same distro, same hardware, same usb pen drive, etc worked several minutes ago and now it is not?:confused:

I'm not willing to give up on this!](*,)

---

### Post by mochalkin on 2011-05-25
I was able to install Xubuntu finally - I had to recreate the USB flash drive from the iso image and install it once again. So far it works fine. Some problems with Fn keys thought, will have to dig around it.

---

### Post by jankyHellface on 2011-05-25
> **mochalkin said:**
> Some problems with Fn keys thought, will have to dig around it.
I don't use the multimedia function keys, but volume keys were important. In order to set them, go into settings >> Settings manager >> Keyboard >> Shortcuts tab. map these shortcuts to your volume buttons: 
```
Mute: amixer -c 1 set Master toggle
Volume down: amixer -c 1 set Master 5- unmute 
Volume up: amixer -c 1 set Master 5+ unmute
```

---

### Post by bill_mchale on 2011-05-27
> **languedoctor said:**
> Sorry if I missed it earlier (this thread *is* 30 pages, though :) )

Is there anyone here who has had success configuring ubuntu on the substantially similar Lenovo Ideapad S205?

Given the size of this thread, it seems like the safe move would just be to go for the x120e. Lenovo has some nice deals on the fusion-equipped Ideapad S right now, though...

I am interested in this laptop as well (4Gb of ram plus 750Gb harddrive).  It also looks like it will be available considerably sooner than the x120e.

So far, the only issue I have seen is that it doesn't play well with grub2 but does work ok with grub version 1.

Overall, I would bet that there should be no unsolvable problems, but I would love it if someone besides me was to evaluate it :).

--
Bill

---

### Post by link141 on 2011-05-27
> **bill_mchale said:**
> So far, the only issue I have seen is that it doesn't play well with grub2 but does work ok with grub version 1.
Grub 2 works fine, I'm using it right now (grub-pc, one install) with 3 linux distros.  The only issue with grub2 is the initial configuration.  The efi-boot feature of the bios confuses the installer and tends to load the wrong version of grub.  This can be fixed by manually booting the fresh install, removing the grub efi package, and installing grub-pc.  Alternatively, you can disable efi-boot in bios.  However, I can't vouch for using grub-efi in efi boot mode since I use grub-pc.

> **bill_mchale said:**
> 
Overall, I would bet that there should be no unsolvable problems, but I would love it if someone besides me was to evaluate it :).
The only major issue I have with Ubuntu and Kubuntu on this machine is the wireless driver causing system lock-ups.  However, there are a few workarounds I haven't tried that may fix this.  

I'm using Arch Linux right now and it doesn't have this problem with the latest stock drivers.  There are a few minor annoyances that I've run into, but I've already fixed most of them.  So overall, I would rate the x120e as having very high compatibility with Linux.

If you need help with any specific issues, I be glad to try and help :).

---

### Post by bhspencer on 2011-05-28
I am also having the random freezing that is apparently caused by the rtl8192ce wireless driver. I am getting at least 2 hard crashes a day. If anyone finds a solution to this problem I would love to know about it.

---

### Post by bhspencer on 2011-05-30
With the current hard lock caused by the wireless driver I think it is fair to say that ubuntu 11.04 out of the box is not compatible with the X120e. Currently I have not yet found a solution to this hard lock issue. Please, anyone...

---

### Post by link141 on 2011-05-30
> **bhspencer said:**
> With the current hard lock caused by the wireless driver I think it is fair to say that ubuntu 11.04 out of the box is not compatible with the X120e. Currently I have not yet found a solution to this hard lock issue. Please, anyone...

Relax.  This version of the wireless driver does not work very well.  Considering this is *very* new hardware, Ubuntu works very well.  With the latest stock version of the realtek driver on Arch (which should make it's way to ubuntu at some point) I do not experience any freezing what so ever.

If you look (search) at previous posts in this thread, you will be able to see what some others have done as work-arounds.  So far (if I remember correctly) I have read that some people have it working on natty with a special version of the driver via ppa (after disabling the bad one).  You may also want to try downloading the driver directly from realtek's website and compiling from source.  I did this on Maverick, and the wireless behaved fairly well.  I'm not sure if this will prevent the freezing on Natty though.

Take a look at  [_this page_](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/769812).  There is at least one work-around listed in the comments that may solve this problem.

---

### Post by jankyHellface on 2011-05-31
> **link141 said:**
> Relax.  This version of the wireless driver does not work very well.  Considering this is *very* new hardware, Ubuntu works very well.  With the latest stock version of the realtek driver on Arch (which should make it's way to ubuntu at some point) I do not experience any freezing what so ever.

If you look (search) at previous posts in this thread, you will be able to see what some others have done as work-arounds.  So far (if I remember correctly) I have read that some people have it working on natty with a special version of the driver via ppa (after disabling the bad one).  You may also want to try downloading the driver directly from realtek's website and compiling from source.  I did this on Maverick, and the wireless behaved fairly well.  I'm not sure if this will prevent the freezing on Natty though.

Take a look at  [_this page_](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/769812).  There is at least one work-around listed in the comments that may solve this problem.

Also, take a look at [this bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/749871") as the x120e bug posted earlier is now marked as a duplicate of the newer bug. Specifically, they mention that using the pre 2.6.34 compat diver on the realtek page makes for a more stable system. 

I just installed it today after 3 crashes. Fingers crossed that it provides more stability.

---

### Post by bhspencer on 2011-06-01
Was it necessary to uninstall the stock driver before installing the pre 2.6.34 driver? If so how did you uninstall the stock driver?

---

### Post by jankyHellface on 2011-06-01
> **bhspencer said:**
> Was it necessary to uninstall the stock driver before installing the pre 2.6.34 driver? If so how did you uninstall the stock driver?

Nope, just follow the instructions in the readme file. It's pretty simple. 

Also, after I installed it, it showed up in additional drivers and I activated it. (Not sure if this is really needed as it was more stable after a reboot)

So far, so good. No hard crashes due to wireless in 2 days.

---

### Post by bhspencer on 2011-06-02
Sadly a few hours after installing the pre 2.6.34 driver I got one of the hard crashes.

So either its not the driver or the problem is with both versions of the driver.

I was thinking it might be the video driver but I get the same random hard crash with both the stock driver and catalyst 11.5. So I think that rules out the video driver.

---

### Post by angie1153 on 2011-06-02
where i can find ThinkPad?

---

### Post by jankyHellface on 2011-06-02
> **bhspencer said:**
> Sadly a few hours after installing the pre 2.6.34 driver I got one of the hard crashes.

So either its not the driver or the problem is with both versions of the driver.

I was thinking it might be the video driver but I get the same random hard crash with both the stock driver and catalyst 11.5. So I think that rules out the video driver.

Yes. I've had 2 crashes since I installed the pre 2.6.34 driver. But it is still leaps and bounds above the kernel driver shipped with 2.6.38. (where I couldn't go more than an hour or 2 without a crash) 

My understanding is that there are 2 bugs causing crashes on our machines. One with wireless and the other with fgrlx when sleeping. I haven't experienced the fgrlx bug as often in xfce as I did with kde but it's still there.

There are open bugs for each of these issues, and I guess it's a wait and see situation until someone either figures out how to build the newer drivers from the realtek site or bugs in the kernel are ironed out.

---

### Post by link141 on 2011-06-05
I don't know why I didn't think of this before, but we could potentially workaround the wireless issues by using ndiswrapper with the xp driver.  Our card is even listed under working devices: [http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Realtek_RTL8192E](http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Realtek_RTL8192E)

Sure, it's not the best solution, but it may prove to be quite usable (no crashes) until the linux driver/kernel issues are fixed on natty.  I'm almost certain this issue will be fixed by the next ubuntu release at the latest as the stock driver works in Arch Linux with no problems.

I'll try ndiswrapper on ubuntu and post my results.

EDIT: Didn't work with XP driver.  Ndiswrapper installs fine and shows the driver being installed but does not create the interface.  Not sure why.  Maybe I'll try the Win2k, vista and 7 drivers...

---

### Post by samanthad on 2011-06-05
> **link141 said:**
> I'm using Arch Linux right now and it doesn't have this problem with the latest stock drivers.  There are a few minor annoyances that I've run into, but I've already fixed most of them.  So overall, I would rate the x120e as having very high compatibility with Linux.

Are you referring to the driver provided by this package: [http://aur.archlinux.org/packages.php?ID=46797](http://aur.archlinux.org/packages.php?ID=46797)? Because the Arch Linux wiki claims that the kernel driver, which is what Ubuntu uses, also has trouble on Arch and that you need to install that third party driver to get it to work right: [https://wiki.archlinux.org/index.php/IBM_ThinkPad_X120e](https://wiki.archlinux.org/index.php/IBM_ThinkPad_X120e). The thing is that the driver supplied by that package is the same driver which was used in Ubuntu 10.10, it's the realtek proprietary driver which now seems to conflict with the kernel drivers under Ubuntu. I don't think we're going to see that trickle down.

---

### Post by link141 on 2011-06-07
> **samanthad said:**
> Are you referring to the driver provided by this package: [http://aur.archlinux.org/packages.php?ID=46797](http://aur.archlinux.org/packages.php?ID=46797)? Because the Arch Linux wiki claims that the kernel driver, which is what Ubuntu uses, also has trouble on Arch and that you need to install that third party driver to get it to work right: [https://wiki.archlinux.org/index.php/IBM_ThinkPad_X120e](https://wiki.archlinux.org/index.php/IBM_ThinkPad_X120e). The thing is that the driver supplied by that package is the same driver which was used in Ubuntu 10.10, it's the realtek proprietary driver which now seems to conflict with the kernel drivers under Ubuntu.

No, I'm referring to the out-of-the-box kernel driver that came with 2.6.38.  Personally, I have not had a single hard-lock with it at all on Arch.  So I wasn't aware that this driver (the 2.6.38 kernel driver) may have the same issue.

However, I do not use network-manager on arch.  I instead wrote a boot script to configure wireless with ifconfig, iwconfig and dhcpcd when I power on the laptop (right now, I'm using it with only one router at home).  Perhaps I'm not having hard-locks as I'm using only a single access point per session? (the command line utils probably don't scan for access points periodically as network-manager does).

The kernel driver is also kind of flaky in that it will usually fail to work with dhcp coming out of suspend...  I might end up trying the AUR on arch and see how the proprietary driver works.  As for ubuntu (and debian) I'm still trying to get the proprietary driver to finish compiling and install.

And yes, I know that one had to use the proprietary driver on Maverick to get support for this card as I personally wrote the instructions on the X120e page on help.ubuntu.com.  Technically Maverick didn't use even use this driver by default as you couldn't even get this driver using the restricted driver manager.

If I can't get the proprietary driver to install (and work), AND I need to use Natty AND the proprietary driver doesn't work well on arch AND the issues with the other driver aren't fixed after a while (I mean six months to a year) I guess I will have to bite the bullet and buy the A/B/G/N thinkpad x120e wlan card from somewhere.  However I find this scenario highly unlikely so I'm not worried. Also, I can simply downgrade to Maverick and use the working proprietary driver.

If I do get the card working reasonably well on Natty, I will be sure to share my process with you.

> **samanthad said:**
> I don't think we're going to see that trickle down.
cat quote.txt > /dev/null

Have a nice day,
link141

---

### Post by tista on 2011-06-08
Hi all.

I'm a X120e user.
then I've opened own blog:
[http://tista-blog.blogspot.com/]("http://tista-blog.blogspot.com/")

today I had applied oneiric kernel and fglrx. and also wifi driver from Realtek. ;)
4Q 2010 to 1Q 2011, I was a member of GMA500 Team for Ubuntu.
yeah I had been contributing some drivers, patchworks, and some support in forum.

if you guys could succeeded with my method of wifi, I would make some packages for dkms.

Cheers.

---

### Post by link141 on 2011-06-09
> **tista said:**
> Hi all.

I'm a X120e user.
then I've opened own blog:
[http://tista-blog.blogspot.com/]("http://tista-blog.blogspot.com/")

today I had applied oneiric kernel and fglrx. and also wifi driver from Realtek. ;)
4Q 2010 to 1Q 2011, I was a member of GMA500 Team for Ubuntu.
yeah I had been contributing some drivers, patchworks, and some support in forum.

if you guys could succeeded with my method of wifi, I would make some packages for dkms.

Cheers.

Hi,

Awesome!!

I got the module to build, but there is a known issue with the installation process.

I'll follow your instructions and see if it will install manually.

Thanks and I'll let you know how it goes...

EDIT: :guitar:IT WORKS!!:guitar: THANK YOU =D> !!!

I built the module with:
```
make
sudo make install
```
Then followed the instructions on your blog:
(The driver is in HAL/rtl8192 after compilation)
```

sudo cp r8192ce_pci.ko /lib/modules/2.6.38-8-generic/updates/dkms/
sudo depmod -a

```

From there, it showed up with ifconfig -a.  I was able to modprobe the driver and configure wireless from the command line -- I didn't even have to reboot.

If this works for enough people, I can update the wiki with these instructions for the time being...

---

### Post by tista on 2011-06-09
> **link141 said:**
> Hi,

Awesome!!

I got the module to build, but there is a known issue with the installation process.

I'll follow your instructions and see if it will install manually.

Thanks and I'll let you know how it goes...

EDIT: :guitar:IT WORKS!!:guitar: THANK YOU =D> !!!

I built the module with:
```
make
sudo make install
```
Then followed the instructions on your blog:
(The driver is in HAL/rtl8192 after compilation)
```

sudo cp r8192ce_pci.ko /lib/modules/2.6.38-8-generic/updates/dkms/
sudo depmod -a

```

From there, it showed up with ifconfig -a.  I was able to modprobe the driver and configure wireless from the command line -- I didn't even have to reboot.

If this works for enough people, I can update the wiki with these instructions for the time being...

Hi Link141. ;)

Thanks for your following up.
that driver's Makefile might not be fitted to Ubuntu, so today we should copy kernelspace driver into dkms directory manually. so ASAP I would make deb package for dkms on my PPA if opened. ;) although we should rebuild this driver via dkms when we install new kernel, that would be better than manually installations. and that's right that you had run the command "ifconfig -a" without rebooting. but if once we registered any new balacklistings,  rebooting is the best way to avoid kernelspace conflicts within similar drivers. ;)

and hopefully I'm happy with you could update the Wiki after the other guys could make it work this method...

Cheers.

---

### Post by jankyHellface on 2011-06-11
Hey guys, thanks a lot for working on this issue. I'm glad you all have seen progress. Just a quick question on building and using the newer kernel module as I'm having a bit of trouble locating the correct .ko module.

> **link141 said:**
> 
(The driver is in HAL/rtl8192 after compilation)
```

sudo cp r8192ce_pci.ko /lib/modules/2.6.38-8-generic/updates/dkms/
sudo depmod -a

```

I'm a bit confused as to how you got this to work. I downloaded the >= 2.6.35 kernel drivers from the realtek site and I don't get any modules named r8192ce_pci.ko nor do I get a HAL directory after a make install. There are three directories for ce, de and se versions of the drivers each named similarly to rtl8192ce.ko. 


Now, after building the compat (< 2.6.35) module I get a HAL directory with that .ko file, but this driver has no issues building and installing on our machines. Could it be that you're building the old compat drivers? Or am I looking in the wrong directory?

Once again, thanks a lot for working on this!

---

### Post by tista on 2011-06-11
> **jankyHellface said:**
> Hey guys, thanks a lot for working on this issue. I'm glad you all have seen progress. Just a quick question on building and using the newer kernel module as I'm having a bit of trouble locating the correct .ko module.



I'm a bit confused as to how you got this to work. I downloaded the >= 2.6.35 kernel drivers from the realtek site and I don't get any modules named r8192ce_pci.ko nor do I get a HAL directory after a make install. There are three directories for ce, de and se versions of the drivers each named similarly to rtl8192ce.ko. 


Now, after building the compat (< 2.6.35) module I get a HAL directory with that .ko file, but this driver has no issues building and installing on our machines. Could it be that you're building the old compat drivers? Or am I looking in the wrong directory?

Once again, thanks a lot for working on this!

Hi jankyHellface. ;)

Thanks for your trials.
well... I've opened the branch for rtl8192ce by using RealTek codes. it's the one what I'm using to build the driver.

have you ever used bzr branch?
yeah that's easy to download the codes:
```
bzr branch lp:~tista/+junk/r8192ce_pci
```
1. cding the downloaded directory named "r8192ce_pci".
2. run "make".
3. copy the kernel module into dkms directory and run "depmod -a".
4. if want, you should force the native drivers to be registered in blacklists via /etc/modprobe.d/blacklist.conf (named "rtl8192ce" and "rtlwifi").
5. reboot.

give it a try! :)

tista

---

### Post by tista on 2011-06-12
Hi all.

today I've opened the PPA for X120e. especially rtl8192ce and the next would be fglrx for oneiric.
now wifi driver starring at Natty as target, but soon I would add it for oneiric.

then my PPA is pending publications...
[https://launchpad.net/~tista/+archive/x120e/]("https://launchpad.net/~tista/+archive/x120e/")
after a couple of hours, the binary packages would be uploaded completely.

finally you guys could add my ppa to your system, and run apt-get install r8192ce-pci... the dkms system would build kernel module automatically and installing it to target directory properly. ;)

and here is my deb package:
[https://launchpad.net/~tista/+archive/x120e/+build/2563768]("https://launchpad.net/~tista/+archive/x120e/+build/2563768")
if you guys want it soon, DL it manually and install it via dpkg.

Cheers.

**EDIT:**
now it's ready for publish...
give my ppa a try!!

---

### Post by linuxhobox on 2011-06-12
Didn't see anyone post this one:

[http://forums.mydigitallife.info/threads/20223-Remove-whitelist-check-add-ID-s-to-break-hardware-restrictions-mod-requests.?p=440679&viewfull=1#post440679](http://forums.mydigitallife.info/threads/20223-Remove-whitelist-check-add-ID-s-to-break-hardware-restrictions-mod-requests.?p=440679&viewfull=1#post440679)

Modded bios with wifi whitelist and slic removed.

Use at you own risk.  I have not tried it.

This will allow non-blessed wifi cards to get past the bios lock.

---

### Post by baranovdmi on 2011-06-12
Hello,

  does anyone experience the problems with resuming from suspend? On resume laptop powers on, coolers are begin to work but nothing continues. I have no idea why?
 
  kernel 2.6.38 (no X system installed), Realtek modules are added to blacklist.conf just in a fire case.

---

### Post by tista on 2011-06-12
> **baranovdmi said:**
> Hello,

  does anyone experience the problems with resuming from suspend? On resume laptop powers on, coolers are begin to work but nothing continues. I have no idea why?
 
  kernel 2.6.38 (no X system installed), Realtek modules are added to blacklist.conf just in a fire case.

@baranovdmi

If I remember well, opensourced radeon driver couldn't. so you might give a try fglrx.

and you didn't seems to install X, umm did you mean Wayland? if so, you should keep radeon driver for it and there's few chances to succeed suspend/resume on radeon I suppose...

or if you use this laptop with VT console, also fglrx wouldn't match for it. because fglrx couldn't handle KMS framebuffer properly so you see the wrong resolutions on VT. fglrx can only handle up to 1024x768 maybe... in opposite, radeon driver would be OK on VT as correct resolution.

Cheers.

---

### Post by baranovdmi on 2011-06-12
> **tista said:**
> 
If I remember well, opensourced radeon driver couldn't. so you might give a try fglrx.

and you didn't seems to install X, umm did you mean Wayland? if so, you should keep radeon driver for it and there's few chances to succeed suspend/resume on radeon I suppose...

or if you use this laptop with VT console, also fglrx wouldn't match for it. because fglrx couldn't handle KMS framebuffer properly so you see the wrong resolutions on VT. fglrx can only handle up to 1024x768 maybe... in opposite, radeon driver would be OK on VT as correct resolution.


Thank you for reply. No X -- I meant that I have system base installation only without any graphics support (and no Wayland too; virtual terminals only). Seems that I do not need fglrx because they are intended for X-system as far as I understand (I have never used Radeon video adapters before).

Is there any way to debug why laptop does not resume? I already tried to blacklist all modules related to sound and communications but w/o any result to make it work...

If it does matter I do not use UEFI and I have 32 bit system installation. BIOS v1.11. But hibernate works well.

The funny thing is if to resume laptop from suspend immediately (1-5 secs later), it resumes ok! If a bit later -- the problem I described.

---

### Post by baranovdmi on 2011-06-12
> **baranovdmi said:**
> does anyone experience the problems with resuming from suspend? On resume laptop powers on, coolers are begin to work but nothing continues. I have no idea why?

Seems I've managed to track the problem down. The issue was in passed 'nomodeset' kernel boot argument. With that one resume hasn't worked.

---

### Post by afxmac on 2011-06-12
> **tista said:**
> give my ppa a try!!

I tried and got a freeze pretty quickly ;-(

Looks like the PPA version does not take care of the older module right?
```
lsmod|egrep 81
r8192ce_pci           503622  0 
rtl8192ce             122961  0 
rtlwifi                85089  1 rtl8192ce
mac80211              294370  2 rtl8192ce,rtlwifi
r8169                  48022  0 

```

cheers
afx

---

### Post by tista on 2011-06-12
> **afxmac said:**
> I tried and got a freeze pretty quickly ;-(

Looks like the PPA version does not take care of the older module right?
```
lsmod|egrep 81
r8192ce_pci           503622  0 
rtl8192ce             122961  0 
rtlwifi                85089  1 rtl8192ce
mac80211              294370  2 rtl8192ce,rtlwifi
r8169                  48022  0 

```

cheers
afx

Hi afx.

you should do blacklisting to avoid native driver both "rtl8192ce" and "rtlwifi"
after all, check it out whether it still conflicts.

my PPA has only the driver instead of any configurable script... did you see in previous posts?

Cheers.

P.S:
basically I've never experienced such freeze causing wifi driver before...???
even if under the multiple similar drivers were loaded.... dkms must be loaded always as highest priority even if exactly same-named drivers existed.

---

### Post by tista on 2011-06-13
Hi all.

now I'm rebuilding deb package of r8192-pci...
so sorry for that the package didn't work properly as dkms installations because of some lack of sources and mixed pre-build binaries...

so please you guys wait until updating finished... ;)

Cheers.

tista

**P.S:**
now finished updating!!
yeah give a try the latest: r8192ce ver.0006.0321.2011~natty6
if you already put kernel module manually, first could you rm it? dkms checks module's own version so if the same, dkms would avoid building and/installing...

and on known issues, the native drivers named "rtl8192ce" and "rtlwifi" must be blacklisted.

---

### Post by afxmac on 2011-06-13
> **tista said:**
> you should do blacklisting to avoid native driver both "rtl8192ce" and "rtlwifi"
after all, check it out whether it still conflicts.
Overlooked that (me lazy, thinking anything coming in via a repo is plug&play for the masses... ;-)
I actually removed the system module after I had seen the dupe and since then it has been running fine.

I'll blackist it now so that the next Ubuntu update will not enable it again..

> basically I've never experienced such freeze causing wifi driver before...???
even if under the multiple similar drivers were loaded.... dkms must be loaded always as highest priority even if exactly same-named drivers existed.
Well, it might have been just the original driver which we want to get rid of because of freezes...

Interestingly enough, I find that your module often results in a drop of indicated network strength. A symptom of power saving? (Have not noticed any loss of speed...)

I just noticed now that your PPA also shows a new fglrx. What was the reason again for that? (So far the stock one works ok for me).

cheers
afx

---

### Post by tista on 2011-06-13
> **afxmac said:**
> Overlooked that (me lazy, thinking anything coming in via a repo is plug&play for the masses... ;-)
I actually removed the system module after I had seen the dupe and since then it has been running fine.

I'll blackist it now so that the next Ubuntu update will not enable it again..


Well, it might have been just the original driver which we want to get rid of because of freezes...

Interestingly enough, I find that your module often results in a drop of indicated network strength. A symptom of power saving? (Have not noticed any loss of speed...)

I just noticed now that your PPA also shows a new fglrx. What was the reason again for that? (So far the stock one works ok for me).

cheers
afx

OK afx.
let's explain.

1st, now I'm using gnome3 on Natty, so because of some reasons I had to purge nm-applet. then on conman, wave strength is showed quite well... but I didn't know how nm-applet showed... :P

2nd, fglrx on my PPA gives you guys the chance to build against 2.6.39 kernel. yeah that's oneiric's one. ;)
I'm also a man of kernel freak. so now I'm fighting against 3.0.0 kernel to build fglrx! its package has the patch made by me to fix compilation errors against newer kernel and today this fglrx would be OK to be built on 3.0.0 kernel, but unfortunately 3.0.0 couldn't handle a framebuffer of fglrx even if I had employed libkms and libdrm2... in opposite, radeon driver would be loaded well on 3.0.0 as KMS driver. ;) 

Regards.

tista

---

### Post by baranovdmi on 2011-06-14
Hello,

  any success in making HDAPS module work for X120E?
  I got the following in dmesg (and the same while trying to read hdaps value via sysfs):

```
kernel: thinkpad_ec: thinkpad_ec_read_row: failed requesting row: (0x11:0x00)->0xfffffff0
```

As far as I know it did not work even for its successor -- x100e :(.

---

### Post by tista on 2011-06-15
> **baranovdmi said:**
> Hello,

  any success in making HDAPS module work for X120E?
  I got the following in dmesg (and the same while trying to read hdaps value via sysfs):

```
kernel: thinkpad_ec: thinkpad_ec_read_row: failed requesting row: (0x11:0x00)->0xfffffff0
```

As far as I know it did not work even for its successor -- x100e :(.

Hi baranovdmi. ;)

Unfortunately I won't use HDD because of speed, so I've already replaced HDD to SSD (Crucial RealSSD C300 128GB). although SSD didn't have so much storage area, it improves speed, unti-G, and power-saving...
Then I had modded some configurations for controlling commit cycle.

Finally as far as I know does anybody need such HDAPS on HDD?

Cheers.

---

### Post by baranovdmi on 2011-06-15
@tista:

  SSD is a real great think. But
    1. I am using LUKS encryption for some partitions on my HDD and I think that permanent write cycles of re-encrypted data may damage SSD fast enough rather than HDD.
    2. SSD is still expensive and currently it is hard enough to figure out which one is the best for such money.

  Oh! HDAPS can also be used as a joystick device not to protect HDD only :)

---

### Post by tista on 2011-06-16
Hi guys. ;)

today I've updated fglrx to 8.861 latest version!!
[https://launchpad.net/~tista/+archive/x120e]("https://launchpad.net/~tista/+archive/x120e")

so what are the differences?
yeah I didn't notice the differences between it and 8.850... :sad:
but small bug fixes would be applied maybe.

expecially on my PPA, kernel 2.6.39 had been approved! if you guys are interested in, give it a try... :P

Cheers.

---

### Post by tista on 2011-06-17
> **baranovdmi said:**
> @tista:

  SSD is a real great think. But
    1. I am using LUKS encryption for some partitions on my HDD and I think that permanent write cycles of re-encrypted data may damage SSD fast enough rather than HDD.
    2. SSD is still expensive and currently it is hard enough to figure out which one is the best for such money.

  Oh! HDAPS can also be used as a joystick device not to protect HDD only :)

@baranovdmi

OK. I saw the situation...
well.. if you guys need any newly kernel module, patchworks, backporting, and/or anything like that, let me know!
I might support you maybe... ;)

Cheers.

---

### Post by tista on 2011-06-18
> **baranovdmi said:**
> Seems I've managed to track the problem down. The issue was in passed 'nomodeset' kernel boot argument. With that one resume hasn't worked.

Hi baranovdmi. ;)

so sorry for delayed replying...
yeah today I've tried suspend/resume on single user mode (without any X)...
well it was OK on my X120e.
here is my log on pm-suspend:
[http://paste.ubuntu.com/629141/]("http://paste.ubuntu.com/629141/")

and resumed successfully... obviously I've used latest kernel 3.0.0-999 (rc3 based) daily-built, latest radeon (3D works with Mesa 7.11-git development state) & Gallium3D driver, and my r8192ce wifi driver. yep I didn't use fglrx anymore.

when booting, login into VT, run "sudo pm-suspend". that's all.
oh forgot to mention, I've applied these parameters in grub as kernel options:
```
single  elevator=deadline radeon.modeset=1
```

does anybody give a try suspend/resume without fglrx and track these problems down? ;)

Cheers.

---

### Post by tista on 2011-06-19
> **baranovdmi said:**
> @tista:

  SSD is a real great think. But
    1. I am using LUKS encryption for some partitions on my HDD and I think that permanent write cycles of re-encrypted data may damage SSD fast enough rather than HDD.
    2. SSD is still expensive and currently it is hard enough to figure out which one is the best for such money.

  Oh! HDAPS can also be used as a joystick device not to protect HDD only :)

@baranovdmi

I've uploaded tp_smapi dkms module on my PPA...
[https://launchpad.net/~tista/+archive/x120e/+packages]("https://launchpad.net/~tista/+archive/x120e/+packages")
and I've checked it out.
these might need an entry  in /etc/modules. yeah called "tp_smapi" and "hdaps" maybe.

```
 input: ThinkPad HDAPS joystick emulation as /devices/virtual/input/input11
input: ThinkPad HDAPS accelerometer data as /devices/virtual/input/input12
hdaps: driver successfully loaded.
```

so if you guys had same problems on HDAPS, please give it a try and let me know the results... ;)

regards.

---

### Post by baranovdmi on 2011-06-20
**@tista**, thank you for your efforts!

> **tista said:**
> 
so if you guys had same problems on HDAPS, please give it a try and let me know the results... ;)

``hdapsd'' is an application which is responsible for HDD heads parking when accelerometer raises signals; it fully relies on ``hdaps'' module. If you run:
```
sudo hdapsd -d /dev/sda --vervbose
```
the following errors are raised to console:
```
kernel: thinkpad_ec: thinkpad_ec_read_row: failed requesting row: (0x11:0x00)->0xfffffff0
```
Unfortunately that means that hdaps module is not working :(.

P.S. Possibly it is better to add "x120e" support to DMI list in thinkpad_ec.c via debian/patches I think. But anyway it is cool!

---

### Post by baranovdmi on 2011-06-20
> **tista said:**
> 
here is my log on pm-suspend:

I had the same log :) nothing criminal was there but it just had had not resume.

> **tista said:**
> 
does anybody give a try suspend/resume without fglrx and track these problems down? ;)

Previously I was using 'radeon' kernel module, enabled KMS and "nomodeset=0" - I suppose that was the problem because of KMS. But I am not sure.

> **tista said:**
> 
yep I didn't use fglrx anymore.

Does hardware acceleration work ok with Gallium 3D? And what about power-saving? I have heard that open-source`ed radeon module is worse rather fglrx in powersaving (= fglrx is much better when laptop works on battery).

---

### Post by tista on 2011-06-20
> **baranovdmi said:**
> **@tista**, thank you for your efforts!


``hdapsd'' is an application which is responsible for HDD heads parking when accelerometer raises signals; it fully relies on ``hdaps'' module. If you run:
```
sudo hdapsd -d /dev/sda --vervbose
```
the following errors are raised to console:
```
kernel: thinkpad_ec: thinkpad_ec_read_row: failed requesting row: (0x11:0x00)->0xfffffff0
```
Unfortunately that means that hdaps module is not working :(.

P.S. Possibly it is better to add "x120e" support to DMI list in thinkpad_ec.c via debian/patches I think. But anyway it is cool!

yep. I also saw such error in dmesg... :sad:
and I already applied X120e patch for thinkpad_ec.c. so it didn't seem to be caused DMI register... I'm afraid that scanned addresses were missed... 

so I'm referring to survey someone who could solve this issues...
Thanks.

---

### Post by tista on 2011-06-20
> **baranovdmi said:**
> I had the same log :) nothing criminal was there but it just had had not resume.

really? I didn't have any ideas...


> Previously I was using 'radeon' kernel module, enabled KMS and "nomodeset=0" - I suppose that was the problem because of KMS. But I am not sure.

the KMS was always enable on my X120e with radeon driver. and if so, the results would depend on kernel module of radeon. yep it's equal to kernel dependencies.


> Does hardware acceleration work ok with Gallium 3D? And what about power-saving? I have heard that open-source`ed radeon module is worse rather fglrx in powersaving (= fglrx is much better when laptop works on battery).

right. it works on HD6310. ;)
but you guys need some advanced development states to employ new libdrm2, libkms, dri, and Gallium3D. today I'm using Gallium3D & radeon for running gnome-shell/Unity/Mutter. but fglrx has damned known bug on Gnome-Shell/Mutter.

and finally talking about power-saving, maybe radeon might waste 20% to 30% in battery-life. yep you're right that fglrx might be better to run on laptop...

Regards.

---

### Post by baranovdmi on 2011-06-20
**@tista:** Thank you for your efforts.

BTW, does anyone have problemless Youtube playback using fglrx? Seems that hardware acceleration does not work for Youtube :( But from the other side, 'glxgears' shows me about 250fps. But video is played slowly especially while fullscreen. Any idea?

Thanks,

---

### Post by legoman666 on 2011-06-20
Tista,
Any chance on getting those wireless drivers compiled for 10.10? I refuse to upgrade to the travesty of 11.04 and Plymouth.

---

### Post by baranovdmi on 2011-06-21
> **legoman666 said:**
> Tista,
Any chance on getting those wireless drivers compiled for 10.10? I refuse to upgrade to the travesty of 11.04 and Plymouth.

Why just not compile them on your own? It is pretty easy :) You just download *.tar.gz and *.dsc files from PPA, then do the following:
```

# dpkg-source -x <package-name.dsc>
# cd package-name/
# dpkg-buildpackage -us -uc -nc

```
After that compiled driver is located on parent dir (i.e., on ".."); you can install it to the system via *``dpkg -i <package-name>.deb''*

Here I assume that you have already installed 10.10 and you can live for 3-5 minutes w/o wireless connection ;).

---

### Post by tista on 2011-06-21
Hi guys.

@legoman666

OK. so does anyone else need Maverick package? anyway, I would upload this for Maverick ASAP. but unfortunately for a long time I hadn't worked with .35 kernel, after uploading, if you guys notice some build issues and/or load issues, let me know. ;)

P.S:
just now I've updated package for maverick, so give it a try!
[https://launchpad.net/~tista/+archive/x120e/]("https://launchpad.net/~tista/+archive/x120e/")

---

### Post by tista on 2011-06-21
> **baranovdmi said:**
> **@tista:** Thank you for your efforts.

BTW, does anyone have problemless Youtube playback using fglrx? Seems that hardware acceleration does not work for Youtube :( But from the other side, 'glxgears' shows me about 250fps. But video is played slowly especially while fullscreen. Any idea?

Thanks,

@baranovdmi

well.. I suppose some solutions.
1. fglrx improves VA-API video accel.
2. fglrx could work with the xvba frontend for VA-API.
3. patched mplayer playbacks via vaapi accel.
4. gecko-mediaplayer is the embedded player in Web Browser with gnome-player.

then, glxgears didn't show the performance on video playback except you play via "gl".
and such gl benchmarks strongly depends on diplay vsync option and silicon power...
if you guys want to refer to the performance seriously, you should use phoronix test suite. ;)

cheers.

---

### Post by baranovdmi on 2011-06-21
> **tista said:**
> well.. I suppose some solutions.

**@tista**
Have I understood you clearly that to make YouTube play Ok (without any delays I experience now) with fglrx driver I should install **xvba**?

Thanks.

---

### Post by legoman666 on 2011-06-21
> **baranovdmi said:**
> Why just not compile them on your own? It is pretty easy :) You just download *.tar.gz and *.dsc files from PPA, then do the following:
```

# dpkg-source -x <package-name.dsc>
# cd package-name/
# dpkg-buildpackage -us -uc -nc

```
After that compiled driver is located on parent dir (i.e., on ".."); you can install it to the system via *``dpkg -i <package-name>.deb''*

Here I assume that you have already installed 10.10 and you can live for 3-5 minutes w/o wireless connection ;).

I thought these were somehow different than those. Don't they fix the lockups associated with being connected to wifi?

Thanks Tista!

---

### Post by tista on 2011-06-21
> **baranovdmi said:**
> **@tista**
Have I understood you clearly that to make YouTube play Ok (without any delays I experience now) with fglrx driver I should install **xvba**?

Thanks.

OK. let's explain details... ;)

1. video acceleration on fglrx needs VA-API basically. so you should add this Guido's ppa to employ all latest libva:
[https://launchpad.net/~guido-iodice/+archive/kernel-and-drivers]("https://launchpad.net/~guido-iodice/+archive/kernel-and-drivers")

2. also install xvba-va-driver from above ppa or mine.

3. check the output of vainfo. if you have not any errors, it means you're OK to use video accel via vaapi and xvba.

4. you should get mplayer vaapi-patched from somewhere. and gnome-mplayer is the helpful frontend of this.

5. install gecko-mediaplayer from main repository, and configure gnome-mplayer to play via vaapi.

6. if you run firefox, you should employ one of flashplayer-replacers plug-ins to use gecko-mediaplayer instead of default flash-player.

7. that's all. you could play online movies via vaapi-acceled gecho-mediaplayer.

give a try! ;)

---

### Post by baranovdmi on 2011-06-24
Does anyone experience the problems with r8192ce_pci? Sometimes (I have not managed to find a regularity when it happens) Wi-Fi cannot be cannot from the first or even second attempt, dmesg prints about "auth timeout" (Wi-Fi AccessPoint is OK since it serves enterprise users).

And how to disable r8192ce_pci debug output in dmesg? It annoys me :)

P.S. Reproduced with Wicd connection manager as well with the pure wpa_supplicant (I know that Wicd works over wpa_supplicant :)).

P.P.S. And sometimes it just disconnects :(

---

### Post by tista on 2011-06-25
Hi guys.

I also want more experiences you guys had on r8192ce_pci kernel module...
and agreed with baranovdmi's post atout the flood of messages on dmesg.
now I'm tracking the solutions down for it. :)

and does anybody tried and experienced the issues on what kind of encryptions of wifi?
I only employed WEP128 on X120e instead of WPA2 enterprise or so... 

@baranovdmi

Thanks a lot.
yeah that's right. Wicd works well.  then I already moved to Oneiric and 3.0 kernel. 
on Oneiric, network indicator and network manager had changed dramatically and nm-applet works well against r8192_pci and generic rtl8192ce native driver, too!! ;)
but don't forget that I'm using WEP only...

the generic driver rtl8192ce on 3.0 kernel would work better than on 2.6.x though the up/down transmitting speed had been slower a bit than my r8192ce_pci. now I'm packaging it for Oneiric, but it's under testing state... so if you guys want oneiric, first you should try native driver in kernel!

cheers.

---

### Post by baranovdmi on 2011-06-27
@tista

Kernel 3.0 -- is a great idea! Thank you for the tip :). I moved to latest 3.0 too and seems that generic Wireless driver works good with WEP and WPA2Ent as well!

Does Fn-F3 (mute microphone) hotkey works for you (I mean does it generate any event)? Mine's one does not :(. showkey reports 240 keycode (accordingly to the include/linux/input.h it is UNKNOWN key code). acpi_listen shows nothing. Hence it is impossible for me to bind this key. 
I've already tested it with `evtest` application, it shows the same 240 keycode. thinkpad_acpi seems does not handle it :(

---

### Post by tista on 2011-06-27
> **baranovdmi said:**
> @tista

Kernel 3.0 -- is a great idea! Thank you for the tip :). I moved to latest 3.0 too and seems that generic Wireless driver works good with WEP and WPA2Ent as well!

Does Fn-F3 (mute microphone) hotkey works for you (I mean does it generate any event)? Mine's one does not :(. showkey reports 240 keycode (accordingly to the include/linux/input.h it is UNKNOWN key code). acpi_listen shows nothing. Hence it is impossible for me to bind this key. 
I've already tested it with `evtest` application, it shows the same 240 keycode. thinkpad_acpi seems does not handle it :(

Hi baranovdmi. ;)

Yeah kernel 3.0 seems to be nice!! 
I'm also happy with your success on both WEP and WPA2...
but one thing. in case that on running battery power, the speed might be decreased significantly. :sad:
I suppose it caused power-saving algorithm or something like that.

and then, mine is also damned to avoid any events on "Mic Mute" by Fn+F3.... :sad:
once we changed the state of Mic Mute by volume-applet on Gnome3, it had effectiveness for Mute. but Fn keys did nothing. yeah damned. I suppose some reasons:

* ALSA driver didn't handle properly.
* Thinkpad's acpi protocols didn't work on Mic Mute events.
* X120e has also HDMI Video/Audio output, so it might be a bit clutter to control volume/mute.
* the latest kernel 3.0 didn't even handle key events to transport to firmware in kernelspace and/or vendor.
* ...etc.

the first, we have better to track acpi events scripts down on power-management I think. the second, to search the fixes for ALSA tweaks for its audio driver. yep ALSA sometimes made us mad especially blacklisting and/or driver's options might be the evil...

cheers.

P.S:
acpi_listen says Fn+F3 as 
```
ibm/hotkey HKEY 00000080 0000101b
```

checked via evtest...
AT2 keyboard and Thinkpad special keys:

[Fn+Esc]=Mute speaker -> code 113 OK
[Fn+F1]=volume down speaker -> code 114 OK
[Fn+F2]=volume up speaker -> code 115 OK
**[Fn+F3]=Mute Mic -> code 240**
[Fn+Delete]=backlight down -> code 224 OK
[Fn+Home]=backlight up -> code 225 OK
[Fn+End]=battery info -> code 236 OK

**P.S #2:**

I've got it!! :)

**/etc/acpi/x120e-mic-mute.sh**
```
#!/bin/sh

test -f /usr/share/acpi-support/state-funcs || exit 0

. /etc/default/acpi-support
. /usr/share/acpi-support/power-funcs

amixer -c 1 sset Capture mute toggle
```

**/etc/acpi/events/x120e-mic-mute**
```
# /etc/acpi/events/x120e-mic-mute
# This is called when the user presses the Mic-Mute button and calls.

event=ibm/hotkey HKEY 00000080 0000101b
action=/etc/acpi/x120e-mic-mute.sh
```

give a try with above 2 files!!

---

### Post by baranovdmi on 2011-06-27
@tista

Thank you for the great research, but I do not have the following :(
> **tista said:**
> acpi_listen says Fn+F3 as 
```
ibm/hotkey HKEY 00000080 0000101b
```


acpi_listen prints nothing, even the event file has been added to acpid configuration (+ acpid was restarted).

---

### Post by tista on 2011-06-27
> **baranovdmi said:**
> @tista

Thank you for the great research, but I do not have the following :(


acpi_listen prints nothing, even the event file has been added to acpid configuration (+ acpid was restarted).

OMG...
so it might be the kernel issues? 
I could recommend the Oneiric's kernel 3.0-2-generic or so, but it needs newer module-init-tools, too. on Natty, I don't think such upgrading could make this machine stable. :sad:

I'm currently using Oneiric and Radeon instead of fglrx...
if you had much time, could you download OO image and test it on USB-stick to run without installations?

obviously mine had worked above workaround on Oneiric. ;)

P.S:
"acpi_osi=Linux" and/or some other acpi kernel options didn't make any differences...

Regards.

---

### Post by codedivine on 2011-06-27
I am dual-booting Win7 that came with the laptop and Ubuntu 11.04 (AMD64). If I attempt into boot into Ubuntu from GRUB, the computer hangs. I finally figured out that adding "acpi=off noapic nolapic" to the boot parameters solves the problems but if I do so, then there is a number of other problems:
1. Only 1 CPU core is recognized in Ubuntu. (cat /proc/cpuinfo only shows 1 CPU)
2. No battery information is available when I disconnect from power supply. I guess this is due to turning off acpi?

Does someone else have this problem? I found at least one other person reporting this:
[http://www.spinics.net/lists/linux-acpi/msg32746.html](http://www.spinics.net/lists/linux-acpi/msg32746.html)

Help? I am running Kubuntu btw.

---

### Post by baranovdmi on 2011-06-28
@tista
Seems it cannot be kernel 3.0 issue since it hasn't worked before as well :( I suppose the problem in some another place. I've also tried to run acpid with /dev/input/eventXX (responsible for thinkpad-extra buttons) only, and when I run acpi_listen and pressed Fn-F3, it crashed...

One more issue. Which kernel module is responsible for SD card reader?
```

lsusb | grep -i card
Bus 002 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader

```
No messages in dmesg are shown when I insert SD card -> I suppose some module is not loaded.

Thanks.

---

### Post by tista on 2011-06-28
> **baranovdmi said:**
> @tista
Seems it cannot be kernel 3.0 issue since it hasn't worked before as well :( I suppose the problem in some another place. I've also tried to run acpid with /dev/input/eventXX (responsible for thinkpad-extra buttons) only, and when I run acpi_listen and pressed Fn-F3, it crashed...

One more issue. Which kernel module is responsible for SD card reader?
```

lsusb | grep -i card
Bus 002 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader

```
No messages in dmesg are shown when I insert SD card -> I suppose some module is not loaded.

Thanks.

Hi baranovdmi. ;)

Thanks for your research...
OK. I'm thinking which packages did it provide such keymap. acpi-support,  xorg-input,  linux-firmware, or something like that... anyway we should continue to track this issue down on natty, right?

and second, on mine:
```
Bus 002 Device 005: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader
```
then it works well with automounting/autoregistered on Oneiric.
and here is the output of lshw when I had inserted SDcard:
[http://paste.ubuntu.com/634646/]("http://paste.ubuntu.com/634646/")
any differences with yours?

cheers.

**P.S:**
oh forgot to mention.
here is the output of lsmod:
[http://paste.ubuntu.com/634836/]("http://paste.ubuntu.com/634836/")

---

### Post by tista on 2011-06-29
> **codedivine said:**
> I am dual-booting Win7 that came with the laptop and Ubuntu 11.04 (AMD64). If I attempt into boot into Ubuntu from GRUB, the computer hangs. I finally figured out that adding "acpi=off noapic nolapic" to the boot parameters solves the problems but if I do so, then there is a number of other problems:
1. Only 1 CPU core is recognized in Ubuntu. (cat /proc/cpuinfo only shows 1 CPU)
2. No battery information is available when I disconnect from power supply. I guess this is due to turning off acpi?

Does someone else have this problem? I found at least one other person reporting this:
[http://www.spinics.net/lists/linux-acpi/msg32746.html](http://www.spinics.net/lists/linux-acpi/msg32746.html)

Help? I am running Kubuntu btw.

Hi codedivine. ;)

well... did you already tried to boot from USB or something other devices with Natty installation image? I had never experienced such issues on both internal SSD and/or Install media.

and then, exactly these problems caused that you had avoided acpi features.

cheers.

---

### Post by Crath on 2011-06-29
Has anyone successfully changed out the wireless card with something else? I wouldn't mind making the effort, beats dealing with all this driver crap!

---

### Post by tista on 2011-07-05
Hi guys.

did you see this news:
[http://otbp.blogspot.com/2011/06/lenovo-x121e-incoming-soon.html]("http://otbp.blogspot.com/2011/06/lenovo-x121e-incoming-soon.html")

In Japan, it would be released in 4Q Jul, maybe... ;)
yeah I'm willing to buy to update my X120e!

and of cource I would choose Fusion API... because I don't like Intel graphics chipset.
it seems  X121e would be very similar to X120e on the motherboard.

If I've got it, I would report something.

cheers.

---

### Post by tista on 2011-07-19
Hi guys.

Today I've updated my PPA to employ new mesa drivers from oibaf's ppa...
[https://launchpad.net/~tista/+archive/x120e]("https://launchpad.net/~tista/+archive/x120e")
Yes. Open sourced Radeon driver had approved gnome-shell/unity, accelerated video playback via VDPAU, suspend/resume, almost seems to beat fglrx!! :)

although its performance of 3D is now a bit lower than fglrx, but it's not so bad.

you could install mesa conventional packages and "libg3dvl-mesa" too. well known, fglrx would conflicts with it, so first you should purge fglrx at all. and today wayland from main repos is still under old sources, so it didn't work on such newest mesa environments, if you need current wayland branch, give it a try from official git tree. ;) then you guys knew, fglrx didn't improve any KMS features, so wayland never work on it, never!

but an issue I've experienced. whenever X120e had recovered from blank screen by using power-saving, always backlight flickered rapidly.... it takes a bit long time it had been remained, umm around 2 or 3 minutes or so... after that, backlight gets normal. :sad:

cheers.

---

### Post by Yarikx on 2011-07-20
Hi, i installed your packages in debian wheezy. i use radeon driver. After reboot xorg started normally, but glxgears dont work
Error: couldn't get an RGB, Double-buffered visual
Do you know how what can be wrong?

---

### Post by zombolo on 2011-07-20
> **tista said:**
> Hi guys.

Today I've updated my PPA to employ new mesa drivers from oibaf's ppa...
[https://launchpad.net/~tista/+archive/x120e]("https://launchpad.net/~tista/+archive/x120e")
Yes. Open sourced Radeon driver had approved gnome-shell/unity, accelerated video playback via VDPAU, suspend/resume, almost seems to beat fglrx!! :)



May you post a guide to use hardware accelleration for playing HD videos with these drivers?
Is Totem able to handle them?

---

### Post by tista on 2011-07-20
> **Yarikx said:**
> Hi, i installed your packages in debian wheezy. i use radeon driver. After reboot xorg started normally, but glxgears dont work
Error: couldn't get an RGB, Double-buffered visual
Do you know how what can be wrong?

Hi Yarikx. ;)

as far as I know debian, but I'm using these packages so could you compare with mine?

* Mesa series here:
[http://paste.ubuntu.com/648623/]("http://paste.ubuntu.com/648623/")

*Radeon drivers here:
[http://paste.ubuntu.com/648625/]("http://paste.ubuntu.com/648625/")

cheers.

EDIT:
oh forgot to mention.
let me see your /var/log/Xorg.0.log! :)

---

### Post by tista on 2011-07-20
> **zombolo said:**
> May you post a guide to use hardware accelleration for playing HD videos with these drivers?
Is Totem able to handle them?

Hi Zombolo. ;)

unfortunately Totem didn't do... :sad:
I suppose mplayer families did. I'm running mplayer/gnome-mplayer/gecko-mediaplayer. but yesterday I've found the errors on vdpau... so now I'm using XvMC.

in mplayer, set parameters "-vo xvmc" into your playback commands, or in gnome-mplayer, set video-output to "xvmc". and before done that, you should add a line into /etc/XvMCConfig:
```
/usr/lib/dri/libXvMCr600.so
```
and restart the system.

cheers.

---

### Post by zombolo on 2011-07-21
> **tista said:**
> Hi Zombolo. ;)

in mplayer, set parameters "-vo xvmc" into your playback commands, or in gnome-mplayer, set video-output to "xvmc". and before done that, you should add a line into /etc/XvMCConfig:
```
/usr/lib/dri/libXvMCr600.so
```
and restart the system.

cheers.

Sorry for the stupid question: I am missing XvMCConfig and libXvMCr600 (I got r600_dri.so in /usr/lib/dri).
I have to install a specific package for them?
Many thanks in advance!

EDIT: solved installing libg3dvl-mesa :D
EDIT 2: I followed your guide, but with mplayer I was unable to play any video. :/

---

### Post by tista on 2011-07-21
> **zombolo said:**
> Sorry for the stupid question: I am missing XvMCConfig and libXvMCr600 (I got r600_dri.so in /usr/lib/dri).
I have to install a specific package for them?
Many thanks in advance!

EDIT: solved installing libg3dvl-mesa :D
EDIT 2: I followed your guide, but with mplayer I was unable to play any video. :/

@zombolo

Thanks for your report.

then I've also experienced some unstable crash on mplayer via xvmc... damned... :sad:
well.. or vdpau seems to land on our radeon. but needs some tweaks for system.

yeah we had to make sym-link to use.
* you already had this binary:
```
/usr/lib/vdpau/libvdpau_r600.so.1
```
* so you should make link like this:
```
cd /usr/lib && sudo ln -sf vdpau/libvdpau_r600.so.1 libvdpau_nvidia.so
```
* refresh ldconfig.
```
sudo ldconfig
```

and then in mplayer, set the output device as "-vo vdpau" could you do that?

give it a try.

but one thing. still gnome-mplayer seemed to fail to play any movies via vdpau. I suppose some errors in video-filter employed under gnome-mplayer's decisions.

Regards.

---

### Post by joexner on 2011-07-21
Is anyone else getting "Not all updates can be installed" when they run update-manager? It then asks me if I want to do a partial upgrade. The available updates are the new kernel and Ubuntu One.

Over the weekend I saw this for the first time and let it do the partial upgrade, and it borked my bootloader. I couldn't fix it so I just saved off my data (from the 32-bit rescue) and reinstalled from scratch. However, even after completely reinstalling, I still see this error when I run update-manager, and it won't let me update to the new kernel.

Any thoughts, or diagnostics I can run to see why it wants to do a partial?

I'm running the AMD64 Ubuntu 11.04, btw.

---

### Post by tista on 2011-07-21
> **joexner said:**
> Is anyone else getting "Not all updates can be installed" when they run update-manager? It then asks me if I want to do a partial upgrade. The available updates are the new kernel and Ubuntu One.

Over the weekend I saw this for the first time and let it do the partial upgrade, and it borked my bootloader. I couldn't fix it so I just saved off my data (from the 32-bit rescue) and reinstalled from scratch. However, even after completely reinstalling, I still see this error when I run update-manager, and it won't let me update to the new kernel.

Any thoughts, or diagnostics I can run to see why it wants to do a partial?

I'm running the AMD64 Ubuntu 11.04, btw.

Hi Joexner.

I have some questions, OK?

* is that really machine-specific problem? or could you install Natty to any other machines by using your downloaded image?
* did you use btrfs for root filesystem?
* to run update-namager, have you already tired from command-line? "gksu update-manager -d". after some initial installations, we might need to upgrade whole system like "distribution upgrade".
* where did you install grub2? MBR or PBR? and/or did you had some other OS like Wxxxows?

anyway, I've already shifted to Oneiric, so I didn't have any convictions for that. :sad:

cheers.

---

### Post by joexner on 2011-07-21
> **tista said:**
> 
* is that really machine-specific problem? or could you install Natty to any other machines by using your downloaded image?

I haven't tried this specific image before, except for when I used it to  install 11.04 in April when it was released on this same laptop, and it's worked fine (aside from the occasional wireless-related lockup) from then until last weekend. I kinda figured that the AMD64 repo's were out of whack, but I haven't seen any mentions of this problem cropping up this weekend.
> **tista said:**
> 
* did you use btrfs for root filesystem?

Nope, I went with the default ext4
> **tista said:**
> 
* to run update-namager, have you already tired from command-line? "gksu update-manager -d". after some initial installations, we might need to upgrade whole system like "distribution upgrade".

I ran update-manager from the command line with the same result.
> **tista said:**
> 
* where did you install grub2? MBR or PBR? and/or did you had some other OS like Wxxxows?

I just went with the default partition and GRUB options, whatever they are. I'd imagine it's on the MBR, as I'm not dual-booting or anything and I don't have any other OS installed.

---

### Post by tista on 2011-07-22
> **joexner said:**
> I haven't tried this specific image before, except for when I used it to  install 11.04 in April when it was released on this same laptop, and it's worked fine (aside from the occasional wireless-related lockup) from then until last weekend. I kinda figured that the AMD64 repo's were out of whack, but I haven't seen any mentions of this problem cropping up this weekend.

Nope, I went with the default ext4

I ran update-manager from the command line with the same result.

I just went with the default partition and GRUB options, whatever they are. I'd imagine it's on the MBR, as I'm not dual-booting or anything and I don't have any other OS installed.

@joexner

Ah, OK...

so could you try to run "sudo dpkg --configure -a" on partial installed system?
this command could solve the unresolved stages of package installations... it takes much time, maybe because that command gonna check whole packages out. ;)

cheers.

---

### Post by legoman666 on 2011-07-22
I am experiencing very slow wifi:
I don't know exactly when this started, but it's been troubling me for at least 3 weeks. My wifi performance is terrible. At first I thought it was the wireless router being dumb, but none of the other clients on the same network are experiencing the same issue. I experience this problem on all wireless routers that I've tried (3 or 4).

It's not a problem with the internet connection, when I tried to copy a file from my x120e over wireless N to a wired computer on the same network, the transfer went about 200-500kb/s for maybe a minute and then failed. I should see around 3-5MB/s. ssh'ing into another machine on the same network was painfully slow. It was faster to just physically go downstairs to the remote computer and run the commands on it.

Additionally, internet is pathetically slow to load new pages. Occasionally it just times out completely (especially on https pages). The actual transfer speed is reasonable (3-5Mb/s), but it takes 20-30 seconds to even start sometimes.

I have the RTL8188CE wireless chip and I using the rtl8192ce driver from Tista's repo on Ubuntu 11.04 with all the latest updates.

Any ideas?

---

### Post by tista on 2011-07-22
> **legoman666 said:**
> I am experiencing very slow wifi:
I don't know exactly when this started, but it's been troubling me for at least 3 weeks. My wifi performance is terrible. At first I thought it was the wireless router being dumb, but none of the other clients on the same network are experiencing the same issue. I experience this problem on all wireless routers that I've tried (3 or 4).

It's not a problem with the internet connection, when I tried to copy a file from my x120e over wireless N to a wired computer on the same network, the transfer went about 200-500kb/s for maybe a minute and then failed. I should see around 3-5MB/s. ssh'ing into another machine on the same network was painfully slow. It was faster to just physically go downstairs to the remote computer and run the commands on it.

Additionally, internet is pathetically slow to load new pages. Occasionally it just times out completely (especially on https pages). The actual transfer speed is reasonable (3-5Mb/s), but it takes 20-30 seconds to even start sometimes.

I have the RTL8188CE wireless chip and I using the rtl8192ce driver from Tista's repo on Ubuntu 11.04 with all the latest updates.

Any ideas?

Hi Legoman666. ;)

Thanks for your report.

well... let me see your output of lsmod. if you already installed pastebinit, run this command:
```
lsmod | pastebinit
```
and then, pastebinit would give us the URL link to Ubuntu Paste, so you could post its link here...

I'm afraid that you didn't do blacklisting native drivers.

umm... another suggestions. could you give kernel-3.0 a try?
[http://kernel.ubuntu.com/~kernel-ppa/mainline/]("http://kernel.ubuntu.com/~kernel-ppa/mainline/")
kernel-3.0 has more stable on native rtl8192ce drivers than 2.6.x... so first your should purge my PPA's driver, and next install the kernel-3.0-rc2 or higher. 

cheers.

---

### Post by legoman666 on 2011-07-23
Thanks for the reply, here's the pastebin: [http://paste.ubuntu.com/650587/](http://paste.ubuntu.com/650587/)

I tried blacklisting the default drives and then installing yours, but when I did that, my wifi stopped working altogether. Do the two drivers have the same name or something?

I'll give the new kernel a try in a bit if you don't see anything glaringly wrong in my lsmod. Cheers.

---

### Post by tista on 2011-07-23
> **legoman666 said:**
> Thanks for the reply, here's the pastebin: [http://paste.ubuntu.com/650587/](http://paste.ubuntu.com/650587/)

I tried blacklisting the default drives and then installing yours, but when I did that, my wifi stopped working altogether. Do the two drivers have the same name or something?

I'll give the new kernel a try in a bit if you don't see anything glaringly wrong in my lsmod. Cheers.

@legoman666

OK.
it seems to fail to load my module and still native one stays...

my module named "r8192ce_pci". so you could see this in /lib/modules/YOUR_KERNEL_VERSION/updated/dkms directory.

if it existed, let the command run:
```
sudo modprobe r8192ce_pci
```
and if you gave without any errors, set the default loading list into /etc/modules.
yeah you should add the name of kernel module as "r8192ce_pci".

if it's not existed, you might have to rebuild the dkms again.
first, you could give this command a try:
```
sudo dpkg-reconfigure r8192ce
```
or still you had given any errors on it, I might need to see your make.log...

cheers.

---

### Post by legoman666 on 2011-07-23
Many thanks for the help. 
```
/lib/modules/2.6.38-10-generic/updates/dkms$ ls
fglrx.ko  hdaps.ko  r8192ce_pci.ko  thinkpad_ec.ko  tp_smapi.ko
```

So the driver is indeed there, but I don't know if it's using it. I ran lspci -v, see the output here: [http://paste.ubuntu.com/650716/](http://paste.ubuntu.com/650716/)

The very last entry is the relevant one. I'm not sure if it's using the correct driver or not since it lists both rtl8192ce and r8192ce_pci, it's so hard to tell in Ubuntu...

---

### Post by tista on 2011-07-23
> **legoman666 said:**
> Many thanks for the help. 
```
/lib/modules/2.6.38-10-generic/updates/dkms$ ls
fglrx.ko  hdaps.ko  r8192ce_pci.ko  thinkpad_ec.ko  tp_smapi.ko
```

So the driver is indeed there, but I don't know if it's using it. I ran lspci -v, see the output here: [http://paste.ubuntu.com/650716/](http://paste.ubuntu.com/650716/)

The very last entry is the relevant one. I'm not sure if it's using the correct driver or not since it lists both rtl8192ce and r8192ce_pci, it's so hard to tell in Ubuntu...

Thanks for your tracking.

OK. umm... we had some way to trace this problem.

1. search the "srcversion" of wifi modules what is currently used on your system.
```
cat /sys/class/net/wlan0/device/driver/module/srcversion
```

2. compare module's one.
```
sudo modinfo r8192ce_pci | grep srcversion
```
or
```
sudo modinfo rtl8192ce | grep srcversion
```

that's all. the srcversion sometimes useful to track the module's source version down...

so which your current wifi driver used? ;)

cheers.

---

### Post by legoman666 on 2011-07-23
When I ran the first command you listed, I got the following output: 
```
cat /sys/class/net/wlan0/device/driver/module/scrversion
cat: /sys/class/net/wlan0/device/driver/module/scrversion: No such file or directory

```

---

### Post by tista on 2011-07-23
> **legoman666 said:**
> When I ran the first command you listed, I got the following output: 
```
cat /sys/class/net/wlan0/device/driver/module/scrversion
cat: /sys/class/net/wlan0/device/driver/module/scrversion: No such file or directory

```

...OMG

so let me see your output of "ls /sys/module". here is the module list currently registered on system.

mine is here:
[http://paste.ubuntu.com/650955/]("http://paste.ubuntu.com/650955/")

regards.

---

### Post by legoman666 on 2011-07-24
> **tista said:**
> ...OMG

so let me see your output of "ls /sys/module". here is the module list currently registered on system.

mine is here:
[http://paste.ubuntu.com/650955/]("http://paste.ubuntu.com/650955/")

regards.

[http://paste.ubuntu.com/651237/](http://paste.ubuntu.com/651237/)

Thanks for the continued support.

---

### Post by Yarikx on 2011-07-24
Does anybody has working hdaps?

---

### Post by tista on 2011-07-24
> **legoman666 said:**
> [http://paste.ubuntu.com/651237/](http://paste.ubuntu.com/651237/)

Thanks for the continued support.

OK. now it seems to be similar situation with mine. :)
so how could you see the any good differences on performance than before?


too seriously, let me know your these files:
/etc/modules
/var/log/dmesg

cheers.

---

### Post by wm_brant on 2011-07-25
> **joexner said:**
> Is anyone else getting "Not all updates can be installed" when they run update-manager? It then asks me if I want to do a partial upgrade. The available updates are the new kernel and Ubuntu One.

Over the weekend I saw this for the first time and let it do the partial upgrade, and it borked my bootloader. I couldn't fix it so I just saved off my data (from the 32-bit rescue) and reinstalled from scratch. However, even after completely reinstalling, I still see this error when I run update-manager, and it won't let me update to the new kernel.

Any thoughts, or diagnostics I can run to see why it wants to do a partial?

I'm running the AMD64 Ubuntu 11.04, btw.

A week or two ago I also saw the same thing, and went through the same process including doing a re-install after applying the updates 'cuz of the 'borked' bootloader. When I prompted for updates after the re-install, I de-selected the GRUB2 updates and the other updates were applied without a problem. The system worked fine after the updates (well, except for wi-fi, but we all know about that.)

However, my X120e is again asking me to apply a partial update, and I was wondering if this issue had been resolved. I guess I'm glad to hear I'm not the only one who has had the same issue.

---

### Post by legoman666 on 2011-07-25
> **tista said:**
> OK. now it seems to be similar situation with mine. :)
so how could you see the any good differences on performance than before?


too seriously, let me know your these files:
/etc/modules
/var/log/dmesg

cheers.

/etc/modules:
```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
rtc
r8192ce_pci
```

and /var/log/dmesg: [http://paste.ubuntu.com/651759/](http://paste.ubuntu.com/651759/)

performance is the same as before, I'm seeing around 50kb/s download with downloads that take forever to start. I was trying to use Google Earth and it was basically unusable.

---

### Post by tista on 2011-07-25
> **legoman666 said:**
> /etc/modules:
```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
rtc
r8192ce_pci
```

and /var/log/dmesg: [http://paste.ubuntu.com/651759/](http://paste.ubuntu.com/651759/)

performance is the same as before, I'm seeing around 50kb/s download with downloads that take forever to start. I was trying to use Google Earth and it was basically unusable.

seems r8192ce_pci were loaded normally...

I'm experiencing around 1.4 MB/sec (equal to 11.4 Mbps) on speed via b/g wireless... without any special settings... :sad:

---

### Post by joexner on 2011-07-26
> **tista said:**
> @joexner

Ah, OK...

so could you try to run "sudo dpkg --configure -a" on partial installed system?
this command could solve the unresolved stages of package installations... it takes much time, maybe because that command gonna check whole packages out. ;)

cheers.

```
sudo dpkg --configure -a
```...completes in under a second, and doesn't fix the problem. Should I apply the partial upgrade, and then run dpkg, or is dpkg not working correctly? I'm reluctant to run the partial and then try this, because if it fails, I'm stuck with a non-booting system again.

> **wm_brant said:**
> A week or two ago I also saw the same thing, and went through the same process including doing a re-install after applying the updates 'cuz of the 'borked' bootloader. When I prompted for updates after the re-install, I de-selected the GRUB2 updates and the other updates were applied without a problem. The system worked fine after the updates (well, except for wi-fi, but we all know about that.)

However, my X120e is again asking me to apply a partial update, and I was wondering if this issue had been resolved. I guess I'm glad to hear I'm not the only one who has had the same issue.

I'm glad it's not just me too.

---

### Post by tista on 2011-07-27
> **joexner said:**
> ```
sudo dpkg --configure -a
```...completes in under a second, and doesn't fix the problem. Should I apply the partial upgrade, and then run dpkg, or is dpkg not working correctly? I'm reluctant to run the partial and then try this, because if it fails, I'm stuck with a non-booting system again.



I'm glad it's not just me too.

Oh I see.
so that means you didn't have any unfinished installations before going with partial updates... and yes. the command in my previous one should be run on partial updated system with unfinished installations.

anyway I suppose current grub2 on Natty had anything wrong with updates? :sad: or general bug hides in it and/or initramfs-tools?

I've seen wm_brant's post, too.
yeah that's smart what you had de-selected grub2 updates. ;) and after any other apps had been updated normally, then you might be better to let grub2 update finally..

anyone had other tips?

cheers.

---

### Post by wm_brant on 2011-07-27
> **tista said:**
> 

I've seen wm_brant's post, too.
yeah that's smart what you had de-selected grub2 updates. ;) and after any other apps had been updated normally, then you might be better to let grub2 update finally..



I followed your recommendation to let grub2 update with the other updates that were on the spike... Same problem - system won't boot again after updates:
"error: invalid arch independent ELF magic."
"grub rescue>"

So... problem still exists. Some reading seems to hint that the combination of AMD64 and UEFI are causing Update to pull the AMD64 grub code and substitute generic.

Update: time to quit mucking about with this as the Brits would say. Filed a bug: 817157

---

### Post by srs5694 on 2011-07-27
> **wm_brant said:**
> I followed your recommendation to let grub2 update with the other updates that were on the spike... Same problem - system won't boot again after updates:
"error: invalid arch independent ELF magic."
"grub rescue>"

So... problem still exists. Some reading seems to hint that the combination of AMD64 and UEFI are causing Update to pull the AMD64 grub code and substitute generic.

Update: time to quit mucking about with this as the Brits would say. Filed a bug: 817157

There are a couple of other current threads reporting similar problems, such as [this one.](http://ubuntuforums.org/showthread.php?t=1805759) IIRC, there's an existing bug report on the issue, although I don't have the URL or bug number handy. IMHO, the best workaround at the moment is to install a boot loader (GRUB 2 or ELILO) outside of the package system; but this requires more know-how than many people have, especially since this is a UEFI boot loader, not a more common BIOS boot loader.

---

### Post by afxmac on 2011-07-29
Hmm, why can't I load tp_smapi?

```
root@pixel:/home/afx# modprobe tp_smapi
FATAL: Error inserting tp_smapi (/lib/modules/2.6.38-11-generic/updates/dkms/tp_smapi.ko): No such device or address
root@pixel:/home/afx# ls -la /lib/modules/2.6.38-11-generic/updates/dkms/
total 4760
drwxr-xr-x 2 root root    4096 2011-07-29 07:49 .
drwxr-xr-x 3 root root    4096 2011-07-21 19:58 ..
-rw-r--r-- 1 root root 3990136 2011-07-21 19:58 fglrx.ko
-rw-r--r-- 1 root root   36040 2011-07-29 07:49 hdaps.ko
-rw-r--r-- 1 root root  765608 2011-07-21 20:00 r8192ce_pci.ko
-rw-r--r-- 1 root root   16120 2011-07-29 07:49 thinkpad_ec.ko
-rw-r--r-- 1 root root   49408 2011-07-29 07:49 tp_smapi.ko
root@pixel:/home/afx# 
```
 
(I want to use it to set up the battery thresholds similar to what I am doing on my t61)

cheers
afx

---

### Post by tista on 2011-07-29
> **afxmac said:**
> Hmm, why can't I load tp_smapi?

```
root@pixel:/home/afx# modprobe tp_smapi
FATAL: Error inserting tp_smapi (/lib/modules/2.6.38-11-generic/updates/dkms/tp_smapi.ko): No such device or address
root@pixel:/home/afx# ls -la /lib/modules/2.6.38-11-generic/updates/dkms/
total 4760
drwxr-xr-x 2 root root    4096 2011-07-29 07:49 .
drwxr-xr-x 3 root root    4096 2011-07-21 19:58 ..
-rw-r--r-- 1 root root 3990136 2011-07-21 19:58 fglrx.ko
-rw-r--r-- 1 root root   36040 2011-07-29 07:49 hdaps.ko
-rw-r--r-- 1 root root  765608 2011-07-21 20:00 r8192ce_pci.ko
-rw-r--r-- 1 root root   16120 2011-07-29 07:49 thinkpad_ec.ko
-rw-r--r-- 1 root root   49408 2011-07-29 07:49 tp_smapi.ko
root@pixel:/home/afx# 
```
 
(I want to use it to set up the battery thresholds similar to what I am doing on my t61)

cheers
afx

Hi afx. ;)

Just now I'm uploading tp_smapi-dkms for oneiric. and also tried on local machine...

here is the log on modprobing 3 modules (hdaps, thinkpad_ec, and tp_smapi).
```
[   75.087348] thinkpad_ec: thinkpad_ec 0.40 loaded.
[   75.112311] thinkpad_ec: thinkpad_ec_read_row: failed waiting for data: (0x13:0x00)->0xfffffff0
[   75.112319] hdaps init failed at: hdaps_get_ec_mode failed
[   75.112768] input: ThinkPad HDAPS joystick emulation as /devices/virtual/input/input11
[   75.112987] input: ThinkPad HDAPS accelerometer data as /devices/virtual/input/input12
[   75.113098] hdaps: driver successfully loaded.
[  131.964619] tp_smapi 0.40 loading...
[  131.966663] tp_smapi successfully loaded (smapi_port=0xb0).
```

[INDENT]Yeah it seems to succeed to probe modules on kernel 3.0.0-7-generic-pae.
because of some reasons, I've used to prefer to 32bit PAE kernel instead of 64. basically I always need a lot of development environments on notebook, so I usually run 32bit kernel. exactly the performance while building would be decreased a bit compared with 64bit kernel thogh. ;)
[/INDENT]

but I didn't test some features on such modules, at leaset on oneiric, it would be loadable without any special tunings...

cheers.

**P.S:**

OMG... yeah once after rebooting, the issues had been reproduced... seems to fail to load... :sad:
so oneiric helps us nothing at all.

---

### Post by afxmac on 2011-07-29
Moin tista,

> **tista said:**
> Just now I'm uploading tp_smapi-dkms for oneiric. and also tried on local machine...
Still running stock 11.4 (apart from your network and video driver) here....

But why should the module fail that way? I don't understand the loading error at all....


Funny that you mention PAE... My T61 runs a PAE kernel....

cheers
afx

---

### Post by tista on 2011-07-29
> **afxmac said:**
> Moin tista,


Still running stock 11.4 (apart from your network and video driver) here....

But why should the module fail that way? I don't understand the loading error at all....


Funny that you mention PAE... My T61 runs a PAE kernel....

cheers
afx

@afx

now I'm trying some parameters on thinkpad_ec.
so could you give this option a try?
```
thinkpad_ec.force_io=1
```
add that parameter into GRUB_CMDLINE_LINUX (or _DEFAULT) on /etc/default/grub and run update-grub. after all, reboot.

let's fight against it!! ;)

cheers.

**P.S:**
here is my desktop using awn-hdaps-applet:
[IMG]http://img705.imageshack.us/img705/5203/screenshotat20110729180.jpg[/IMG]

seems OK? I don't know whether it works or not, because in almost cases  I'm using SSD...

---

### Post by legoman666 on 2011-07-31
Got a guide for getting hdasp working on 11.04? I have the hdaspd package installed and the HDASP gnome panel app compiled, installed, and in use. It doesn't move though even when I give my laptop a good shake.

Any tips? Or maybe it's working now? Is there a way to check and see if it's active.

---

### Post by tista on 2011-07-31
> **legoman666 said:**
> Got a guide for getting hdasp working on 11.04? I have the hdaspd package installed and the HDASP gnome panel app compiled, installed, and in use. It doesn't move though even when I give my laptop a good shake.

Any tips? Or maybe it's working now? Is there a way to check and see if it's active.

Hi legoman666.

Umm unfortunately not yet...

and here is another discussions:
[http://comments.gmane.org/gmane.linux.acpi.ibm-acpi.devel/2693]("http://comments.gmane.org/gmane.linux.acpi.ibm-acpi.devel/2693")
yeah I agree at all. EC is now dramatically changed... so it supposed it's too hard to use it on X100e/X120e, maybe also X121e... we might have to do huge cody for that.

but in case with mine, I had to do "hard-reset" to keep hdaps alive in every reboot/poweroff... yep, unplugged AC adapter, detached battery, and wait around 30sec to be reset.  so this way is now completely useless...

even when power is on, I didn't know whether it works or not, at least above hard-reset could load hdaps kernel module normally... even if you guys installed hdapsd daemon, that's meaningless that the kernel modules are dead. :sad:

finally today our X120e/X121e/X100e seems to be dropped from the entires in thinkpad_ec/tp_smapi/hdaps at all... even if I had added DMI entry into souces. it needs completely scratched sources.

---

### Post by mr_raider on 2011-08-01
Has anyone successfully installed NAtty on the x120e using GPT table and UEFI mode? Either from USB or CD?

If so, I would welcome some guidance. My install from USB borks at the end and GRUB fails to install.

---

### Post by tista on 2011-08-02
Hi guys.

today I've updated fglrx to latest 8.872, but I couldn't recommend to run this version... :sad:
yep, this version sometimes may break Unity desktop. not only gnome-shell but also unity?! yeah it suppose mesa/GL libraries had changed the compatibilities... I think today fglrx is completely useless for me!! :sad:

and more worth, on oneiric with radeon environments, may fail to install... damned!! so I had to wait until ubuntu official team had released "working" states... openSuSE seems to succeed packaging it against kernel 3.0, but still oneiric repository didn't.

finally, **please do not update to 8.872 if you guys registered my PPA!!**

cheers.

---

### Post by legoman666 on 2011-08-02
> **tista said:**
> Hi guys.

today I've updated fglrx to latest 8.872, but I couldn't recommend to run this version... :sad:
yep, this version sometimes may break Unity desktop. not only gnome-shell but also unity?! yeah it suppose mesa/GL libraries had changed the compatibilities... I think today fglrx is completely useless for me!! :sad:

and more worth, on oneiric with radeon environments, may fail to install... damned!! so I had to wait until ubuntu official team had released "working" states... openSuSE seems to succeed packaging it against kernel 3.0, but still oneiric repository didn't.

finally, **please do not update to 8.872 if you guys registered my PPA!!**

cheers.

It's a good thing I saw this message, I was in the middle of running apt-get upgrade.

---

### Post by tista on 2011-08-02
> **legoman666 said:**
> It's a good thing I saw this message, I was in the middle of running apt-get upgrade.

Hi legoman666. ;)

yeah you're lucky...
now I'm doing test running on oneiric, so I've found the lack of important stuff!! :sad:
```
name of display: :0
display: :0  screen: 0
[color=red]direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)[/color]
server glx vendor string: ATI
server glx version string: 1.4
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group
client glx vendor string: Mesa Project and SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_framebuffer_sRGB, 
    GLX_MESA_copy_sub_buffer, GLX_MESA_multithread_makecurrent, 
    GLX_MESA_swap_control, GLX_OML_swap_method, GLX_OML_sync_control, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_EXT_texture_from_pixmap, 
    GLX_INTEL_swap_event
GLX version: 1.4
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_MESA_multithread_makecurrent, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group, 
    GLX_EXT_texture_from_pixmap
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: AMD Radeon HD 6300 series Graphics
OpenGL version string: 1.4 (2.1 (4.1.10907 Compatibility Profile Context))
OpenGL extensions:
```

yep, drm is died completely?! OMG... so any 3D desktop environments would slip away!
I wanna say "who decided to let this version release?". today AMD/ATI team seems a monkey train... no gnome-shell, no unity and no wayland, what a hell!

cheers.

**EDIT: Aug 03**
Just now I'm uploading new revision named 2:8.872~natty2...
yeah fixed dkms compilation error by purging patches.
and if you guys really want to try it, run this command before installing fglrx:
* if you run with amd64 ->
```
sudo update-alternatives --remove-all x86_64-linux-gnu_gl_conf
```
* or i686 ->
```
sudo update-alternatives --remove-all i386-linux-gnu_gl_conf
```

above commands could fix installation error on 8.872. but as far as I know why this version needed such tricks... or on Natty, it might not be needed... anyway it'd be better to solve alternatives before install...

---

### Post by VCSkier on 2011-08-05
I know this is somewhat OT from where this discussion has been going, but I'm considering buying this laptop/netbook, and was hoping to get some relative performance qualifications. I'm debating between this, and an Intel Atom N570 based netbook. I'm not a gamer, so high end graphics are not a priority at all, but I would like smooth video playback (hulu, youtube, etc.). Otherwise, I'm looking for a stable, quick, and responsive system that will be able to comfortably be able to latest releases of Ubuntu for the next few years.

Last time I used fglrx, I found it buggy and generally frustrating. Since then, I've only used open-source drivers (radeon and intel), and have found them to be more stable and feature complete for simple compositing and basic desktop acceleration. So I'm alittle concerned that needing to depend on fglrx may compromise some system stability, and possibly introduce some buggy behaviors.

Can anyone here comment on how I could expect this system to perform at these types of tasks, as compared to the more common Intel Atom N570 chipset. My primary areas of concern are (in order of importance) stability, power enough for future releases, and video playback.

Thanks in advance!

---

### Post by tista on 2011-08-06
> **VCSkier said:**
> I know this is somewhat OT from where this discussion has been going, but I'm considering buying this laptop/netbook, and was hoping to get some relative performance qualifications. I'm debating between this, and an Intel Atom N570 based netbook. I'm not a gamer, so high end graphics are not a priority at all, but I would like smooth video playback (hulu, youtube, etc.). Otherwise, I'm looking for a stable, quick, and responsive system that will be able to comfortably be able to latest releases of Ubuntu for the next few years.

Last time I used fglrx, I found it buggy and generally frustrating. Since then, I've only used open-source drivers (radeon and intel), and have found them to be more stable and feature complete for simple compositing and basic desktop acceleration. So I'm alittle concerned that needing to depend on fglrx may compromise some system stability, and possibly introduce some buggy behaviors.

Can anyone here comment on how I could expect this system to perform at these types of tasks, as compared to the more common Intel Atom N570 chipset. My primary areas of concern are (in order of importance) stability, power enough for future releases, and video playback.

Thanks in advance!

Hi VCSkier. ;)

1st, I think even if you were a gamer or not, high performance graphics must be needed... because today we're running various 3D desktop experiences on our Ubuntu, Unity, Gnome-shell, Mutter, Cream and even Wayland. if so, What were the advantages Intel Integrated Graphics had? Nothing!! From 4Q last year, I've been working for GMA500 graphic driver contributing on GMA500 Team, then Intel had done anything to help us? never... That's the reason why I really hate Intel products.

2nd, fglrx on Thinkpad X100e/X120e seems to work well. before you said such "buggy", let the detailed reports send to developers/contributers I think. because I didn't have any ideas what's wrong fglrx runs on your machine, right?  

3rd, my PPA has some Radeon drivers experimental states, exactly today radeon on oneiric/natty beats fglrx completely I suppose, too. but expecially in case "stability", I 've never experienced fglrx runs madly buggy... although obviously fglrx 8.872 goes wrong on Unity today. the previous 8.861 works nice on Unity, xvba backended VA-API, Power-saving, and so...

4th, "future releases", no one knows what happens in this future though. but at least for 2 or 3 years I think this laptop works well on any 3D desktops even on XWayland. and if I were a developer of window-manager, I won't make any new "metacity-addicted" old fashion desktops. I think these're almost dead.

5th, for the video playback, unfortunately I didn't really matter for that... that's enough the states of XV working for me. because I'm running this laptop as a "small development bench", you know. 

cheers.

---

### Post by VCSkier on 2011-08-06
Thanks for the information. That is helpful.

It was years ago that I tried fglrx and found it unstable - back in 2006 I think.

It's good to hear that it has improved. Did I understand you correctly that you think that fglrx is generally running Unity better than the radeon driver on this hardware?

---

### Post by SwitchBlade on 2011-08-06
Tista,looking at installing your driver for the realtek wifi to stop my crashing problems but note on your launchpad page it says to blacklist the existing drivers.  This is new territory for me and I've not really had to fiddle with anything for hardware in Ubuntu since Dapper on my X41 tablet, so could you confirm where/how I do the blacklisting before I install the driver from your PPA?

---

### Post by tista on 2011-08-06
> **VCSkier said:**
> Thanks for the information. That is helpful.

It was years ago that I tried fglrx and found it unstable - back in 2006 I think.

It's good to hear that it has improved. Did I understand you correctly that you think that fglrx is generally running Unity better than the radeon driver on this hardware?

@VCSkier

Ah... OK. yeah exactly in past fglrx till 2009 seemed unstable.
and partially yes. but if you give it a try, please remember that current version 8.872/catalyst-11.7 is quite unstable damnded. :sad: but the previous 8.861/catalyst-11.6 worked well with Unity. and well known, fglrx couldn't improve to run Gnome-Shell, OK?

my experiences were here:

* Unity --- 
[LIST]
[*]fglrx - almost good (except ver.8.872).
[*]radeon - good (with mesa7.12)[/list]

* Gnome-Shell ---
[list]
[*]fglrx - too bad
[*]radeon - good[/list]

* Boot ---
[list]
[*]fglrx - a bit slow
[*]radeon - fast[/list]

* Longer Battery Life ---
[list]
[*]fglrx - good
[*]radeon - bad[/list]

* 3D rendering ---
[list]
[*]fglrx - good
[*]radeon - not so bad[/list]

* Suspend/Resume ---
[list]
[*]fglrx - good
[*]radeon - good[/list]

* Wayland/KMS ---
[list]
[*]fglrx - too bad
[*]radeon - good[/list]

* Future works ---
[list]
[*]fglrx - not hope too much!
[*]radeon - very exciting![/list]

ciao. ;)

---

### Post by tista on 2011-08-06
> **SwitchBlade said:**
> Tista,looking at installing your driver for the realtek wifi to stop my crashing problems but note on your launchpad page it says to blacklist the existing drivers.  This is new territory for me and I've not really had to fiddle with anything for hardware in Ubuntu since Dapper on my X41 tablet, so could you confirm where/how I do the blacklisting before I install the driver from your PPA?

Hi SwitchBlade. ;)

OK. let's explain for it.

first, my module named "r8192ce_pci" is constructed in Realtek site's sources instead of current kernel's one. and this sources were used to be employed in previous 2.6.35 or older kernel. but today linux-kernel team had employed some newer and a bit simpler sources to build "rtl8192ce" and "rtlwifi" modules. these new drivers sometimes (almost always?) seem to be unstable and get slow speed... :sad: but now kernel-3.0 series seems good! ;) if so, oneiric would be the good solutions for madly wifi problems.

2nd, my module is designed as "all-in-one" stand alone module without any other dependents. so simply you guys could load it as:
```
sudo modprobe r8192ce_pci
```
or once you registered it in /etc/modules, every booting came with this module automatically.

3rd, today unfortunately my modules had to be loaded without any other "conflicting" modules. :sad: so you guys should do "blacklisting" such unused (built-in-native) modules. then which are the evil? yeah named "rtl8192ce" and "rtlwifi".  the baby step are something like below:
[LIST=1]
[*]cding into blacklisting directory : ```
cd /etc/modprobe.d
```
[*]create new file for wifi : ```
gksu gedit realtek.conf
```
[*]paste them into above file : 
```
blacklist rtl8192ce
blacklist rtlwifi
```
[*]rebooting...
[/LIST]

cheers.

---

### Post by SwitchBlade on 2011-08-07
Thanks for the baby steps tista.  All done and lsmod shows just your driver running.  It definitely seems to be connecting to the access point faster now.  Nice one.

---

### Post by tista on 2011-08-07
> **SwitchBlade said:**
> Thanks for the baby steps tista.  All done and lsmod shows just your driver running.  It definitely seems to be connecting to the access point faster now.  Nice one.

You're welcome SwitchBlade. ;)

unfortunately today we've experienced the floods of logs appeared in dmesg causing the debug parameters of my module... yeah seems too much logs! :sad: I would polish this in some day...

cheers.

---

### Post by tista on 2011-08-09
Hi guys.

now we're reporting bug on fglrx-8.872/catalyst-11.7...
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/819144]("https://bugs.launchpad.net/ubuntu/+source/unity/+bug/819144")

and also my PPA had uploaded new revision!! ;)
yeah we had experienced ugly installation error on oneiric, so I added patches for installation process... but don't forget about this patch could not solve unity corruptions anymore, OK? :P

then I'm working here as well:
[http://ubuntuforums.org/showthread.php?t=1773851]("http://ubuntuforums.org/showthread.php?t=1773851")

cheers all.

---

### Post by legoman666 on 2011-08-11
When I try to install your fglrx driver from the ppa I get the following error:
```
dpkg: dependency problems prevent configuration of fglrx-amdcccle:
 fglrx-amdcccle depends on fglrx; however:
  Package fglrx is not configured yet.
dpkg: error processing fglrx-amdcccle (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 fglrx
 fglrx-amdcccle
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Thanks for your hard work.

---

### Post by tista on 2011-08-11
> **legoman666 said:**
> When I try to install your fglrx driver from the ppa I get the following error:
```
dpkg: dependency problems prevent configuration of fglrx-amdcccle:
 fglrx-amdcccle depends on fglrx; however:
  Package fglrx is not configured yet.
dpkg: error processing fglrx-amdcccle (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 fglrx
 fglrx-amdcccle
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Thanks for your hard work.

@legoman666

Thanks for your reporting... ;)

so... you did it on Natty or Oneiric? if Natty, it might be needed different approaches compared with Oneiric. and I suppose your posted log seems to have some lack especially the section of installation on fglrx package, right? then let me see your /var/log/dpkg.log as well, OK?

unfortunately now I'm working for oneiric and soon I would purge natty packages...

cheers.

---

### Post by joexner on 2011-08-11
> **srs5694 said:**
> There are a couple of other current threads reporting similar problems, such as [this one.]("http://ubuntuforums.org/showthread.php?t=1805759") IIRC, there's an existing bug report on the issue, although I don't have the URL or bug number handy. IMHO, the best workaround at the moment is to install a boot loader (GRUB 2 or ELILO) outside of the package system; but this requires more know-how than many people have, especially since this is a UEFI boot loader, not a more common BIOS boot loader.

Soo...any progress on this? I *still* see the "partial update" being offered.

---

### Post by tista on 2011-08-11
Hi guys.

I have some sad news...

1. tp-smapi version 0.41 had landed. --- but at least on my local testing, there's nothing to help our laptop... :sad:
2. fglrx 8.880 testing version released. --- but also this version didn't have any advantages from 8.872... :sad:

the latest fglrx had already landed on my PPA for oneiric, however I'm not willing to port for natty, OK?

OT:
yesterday X121e came to my home and today I'm using it!!
I was afraid the typing feel became worth, Bingo!! I prefer to X120e's keyboard than X121e's one... damned.
but some keys gets more larger size (Esc, Delete), and Delete key moved to the edge of top-right. that's nice!! and I bought 3cell battery, 99% remaining shows around 2.5 hours on fglrx...

cheers.

---

### Post by legoman666 on 2011-08-12
> **tista said:**
> @legoman666

Thanks for your reporting... ;)

so... you did it on Natty or Oneiric? if Natty, it might be needed different approaches compared with Oneiric. and I suppose your posted log seems to have some lack especially the section of installation on fglrx package, right? then let me see your /var/log/dpkg.log as well, OK?

unfortunately now I'm working for oneiric and soon I would purge natty packages...

cheers.

I'm running Natty.

---

### Post by afxmac on 2011-08-12
On my 11.4 64bit box I also get configure errors from fglrx and fglrx-amdcccle as shown above.

the log has nothing special:
```
2011-08-12 20:12:52 startup packages configure
2011-08-12 20:12:52 configure fglrx 2:8.872~natty6 <none>
2011-08-12 20:12:52 status half-configured fglrx 2:8.872~natty6

```

cheers
afx

---

### Post by tista on 2011-08-12
Hi legoman666, afxmac.

OK... umm... if you run this command before installing fglrx and fglrx-amdcccle:
```
sudo update-alternatives --remove-all gl_conf
```
could we make any differences?

tista

---

### Post by afxmac on 2011-08-13
> **tista said:**
> ```
sudo update-alternatives --remove-all gl_conf
```
could we make any differences?
Oh yes!

thx
afx

---

### Post by trungvkvk on 2011-08-13
I'm thinking fglrx may be causing hibernate to lock up.  Will test this once I do another install.
  I tested w/ wireless module blacklisted.  So, wireless should be fine.
i new use ubuntu.

---

### Post by VCSkier on 2011-08-13
So I ordered my x120e yesterday, and I'm really excited about it. My thoughts are that I'll wipe the HD, and then dual-boot Natty and Oneiric, both 64-bit. I'm thinking I'll run fglrx driver on Natty, and Radeon on the Oneiric, because Oneiric will have all the lastest packages OOTB. Does this make sense?

When I go to install Natty, what's the easiest way to get the best version of fglrx? Is there a repo somewhere with fglrx 8.861, or will I have to install it from ATI?

Thank you all, especially tista, for your help and advice on this.

---

### Post by tista on 2011-08-13
> **trungvkvk said:**
> I'm thinking fglrx may be causing hibernate to lock up.  Will test this once I do another install.
  I tested w/ wireless module blacklisted.  So, wireless should be fine.
i new use ubuntu.

Hi trungvkvk.

Oh what a pity....:sad:  unfortunately I didn't used to do hibernate but suspend. since I had poor brain for it, does anybody tried it? any ideas? ;)
if you got a workaround, let us know!

cheers.

---

### Post by tista on 2011-08-13
> **VCSkier said:**
> So I ordered my x120e yesterday, and I'm really excited about it. My thoughts are that I'll wipe the HD, and then dual-boot Natty and Oneiric, both 64-bit. I'm thinking I'll run fglrx driver on Natty, and Radeon on the Oneiric, because Oneiric will have all the lastest packages OOTB. Does this make sense?

When I go to install Natty, what's the easiest way to get the best version of fglrx? Is there a repo somewhere with fglrx 8.861, or will I have to install it from ATI?

Thank you all, especially tista, for your help and advice on this.

Hi VCSkier.

Yeah really excited! 
and dual booting plan is nice...

I'm thinking about fglrx 8.861 on natty, too. to be honest, I suppose fglrx had not stepped forward so much from 8.85x... :sad: yep, almost same issues, almost same performances, so we might not have to upgrade in hurry. finally, you first run natty with fglrx 8.85x to check the performances out! ;)

cheers.

P.S
maybe phoronix forum had some advanced discussions about the performances of fglrx and a bit more technical talking, I only used to read oibaf's thread for radeon driver...

---

### Post by VCSkier on 2011-08-14
And the best way to get 8.85x would be from ati's website?

---

### Post by tista on 2011-08-14
> **VCSkier said:**
> And the best way to get 8.85x would be from ati's website?

Here is the famous 8.850 package built by X-edgers team:
[http://www.ubuntuupdates.org/packages/show/298581]("http://www.ubuntuupdates.org/packages/show/298581")

and Natty has 8.840 in main repository, so first you could install 8.840 and then upgrade it to 8.850 from X-swat's PPA... or directly install 8.850 from PPA:
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates]("https://launchpad.net/~ubuntu-x-swat/+archive/x-updates")

OK?

cheers.

---

### Post by VCSkier on 2011-08-15
Good info. I'll probably hop on the x-updates repository - it looks to me like they are trying to serve users like me. I'd like to stay away from the most bleeding edge packages.

My system is scheduled to be delivered sometime tomorrow. So on both Oneiric and 11.04 I'll install the x-updates ppa for graphics, and your (tista's) ppa for wifi drivers, and I'm expecting a pretty stable and well functioning system.

Thanks!

---

### Post by SwitchBlade on 2011-08-16
Has anyone got multiple monitors working properly with this.  Connecting to a 1920x1200 monitor via HDMI it's only allowing a maximum resolution of 1600x1200.  Connecting to the smaller monitor I normally use my laptop with via VGA 1024x768 the screen on it overlays the screen of the laptop even though I've moved it over to the left, managed to fix this by logging into Gnome2 and moving it though.  Now though when I boot up with it unplugged the system is unusable with a mouse (can't click anything) and the space still exists to the left.  It seems to be failing epically.  This worked perfectly fine before in Natty with my X60 tablet which had Intel GMA graphics.

I'm guessing the problem is the catalyst drivers as the Ubuntu Monitors tool has no effect on my screens and I have to resort to using Catalyst to move them which doesn't seem to work very well.

---

### Post by ProNux on 2011-08-17
I have the Fujitsu PH521 with Zacate E-350 on it.  Running Natty Live USB, all hardware are working, even CPU scaling.


This might be out of the topic.

I have a problem after installing Ubuntu, no show of the GRUB. After googling, I think this is related to EFI (never heard of this before).  I have installed to many Ubuntu machines (dual boot) before ever since Hardy.

Is it safe to keep on experimenting on this EFI / BIOS thing?  I am still reading on the internet.  Any link on how to do it right is well appreciated.  Thanks.

---

### Post by tista on 2011-08-18
> **SwitchBlade said:**
> Has anyone got multiple monitors working properly with this.  Connecting to a 1920x1200 monitor via HDMI it's only allowing a maximum resolution of 1600x1200.  Connecting to the smaller monitor I normally use my laptop with via VGA 1024x768 the screen on it overlays the screen of the laptop even though I've moved it over to the left, managed to fix this by logging into Gnome2 and moving it though.  Now though when I boot up with it unplugged the system is unusable with a mouse (can't click anything) and the space still exists to the left.  It seems to be failing epically.  This worked perfectly fine before in Natty with my X60 tablet which had Intel GMA graphics.

I'm guessing the problem is the catalyst drivers as the Ubuntu Monitors tool has no effect on my screens and I have to resort to using Catalyst to move them which doesn't seem to work very well.

Hi SwitchBlade. ;)

what a pity.. :sad:
so... if you could, let me see your Xorg.0.log while connecting external HDMI display... or what the xrandr said for HDMI? unfortunately since I've never tried HDMI with such higher resolution...

and yep, it seems to be caused catalyst.

cheers.

---

### Post by VCSkier on 2011-08-18
@ProNux

I'm not an expert on the issue, but on my laptop, I found that after installing 11.04, Update Manager wanted to do a "Partial Upgrade," which includes a dist-upgrade that removes the grub-efi-amd64 package and replaces it with the standard grub package. Obviously, if we are going to keep using EFI, we need to be using a grub setup that supports that, so I denied the partial upgrade, but let Update Manager install everything else. On my system then, everything boots properly.

This seems to be a bug just in 11.04. Oneiric, on the same laptop, isn't having the same problem. Hope this helps!

---

### Post by SwitchBlade on 2011-08-20
@ProNux 

I had issues with the x120e with this as I just shrank the default windows partition and installed Ubuntu alongside to dual boot.  After installing Ubuntu and grub it still booted to Windows, I even tried booting from a live USB, chrooting to my Ubuntu install and reinstalling grub.  What eventually solved it was disabling EFI booting in the BIOS, re-installing Windows from the rescue partition and then re-installing grub.  After which it all worked fine.  I'm guessing Ubuntu didn't replace Window's default EFI boot settings.

@ tista I'll paste those logs up once when I can get a chance to try hooking that screen up again, probably Tuesday.  Very annoying booting to Windows to watch full HD videos on a big screen atm, my original plan was only to boot to windows when I wanted to game when away from home.

---

### Post by joexner on 2011-08-22
> **VCSkier said:**
> @ProNux

I'm not an expert on the issue, but on my laptop, I found that after installing 11.04, Update Manager wanted to do a "Partial Upgrade," which includes a dist-upgrade that removes the grub-efi-amd64 package and replaces it with the standard grub package. Obviously, if we are going to keep using EFI, we need to be using a grub setup that supports that, so I denied the partial upgrade, but let Update Manager install everything else. On my system then, everything boots properly.

This seems to be a bug just in 11.04. Oneiric, on the same laptop, isn't having the same problem. Hope this helps!

I was having the same problems on my x120e until recently, but I noticed this weekend that the partial upgrade option went away and updated my kernel safely. Yay!

---

### Post by Crath on 2011-08-22
> **SwitchBlade said:**
> Has anyone got multiple monitors working properly with this.  Connecting to a 1920x1200 monitor via HDMI it's only allowing a maximum resolution of 1600x1200.  Connecting to the smaller monitor I normally use my laptop with via VGA 1024x768 the screen on it overlays the screen of the laptop even though I've moved it over to the left, managed to fix this by logging into Gnome2 and moving it though.  Now though when I boot up with it unplugged the system is unusable with a mouse (can't click anything) and the space still exists to the left.  It seems to be failing epically.  This worked perfectly fine before in Natty with my X60 tablet which had Intel GMA graphics.

I'm guessing the problem is the catalyst drivers as the Ubuntu Monitors tool has no effect on my screens and I have to resort to using Catalyst to move them which doesn't seem to work very well.

I was able to get it working with these instructions: [http://shanereustle.com/blog/force-screen-resolutions-on-ubuntu.html](http://shanereustle.com/blog/force-screen-resolutions-on-ubuntu.html)

---

### Post by VCSkier on 2011-08-22
> **joexner said:**
> I was having the same problems on my x120e until recently, but I noticed this weekend that the partial upgrade option went away and updated my kernel safely. Yay!

Me too. Everything's up to date now, and working.

One trivial thing I would like to improve though, is the resolution of plymouth while booting. The plymouth screen displays during the boot sequence, but resolution is really low, maybe 640x400. I used to adjust this with Startup-Manager, but it appears not to support grub-efi.

I'm actually using the grub installation from Oneric to dual boot. When I boot Oneric (which is using the radeon driver) plymouth displays beautifully, but when I boot 11.04, which I use far more commonly (using the fglrx driver) I get the ugly plymouth. Any tips?

---

### Post by tista on 2011-08-22
> **VCSkier said:**
> Me too. Everything's up to date now, and working.

One trivial thing I would like to improve though, is the resolution of plymouth while booting. The plymouth screen displays during the boot sequence, but resolution is really low, maybe 640x400. I used to adjust this with Startup-Manager, but it appears not to support grub-efi.

I'm actually using the grub installation from Oneric to dual boot. When I boot Oneric (which is using the radeon driver) plymouth displays beautifully, but when I boot 11.04, which I use far more commonly (using the fglrx driver) I get the ugly plymouth. Any tips?

@VCSkier

OK. let's explain for that...

First, radeon opensourced driver improves KMS features. it means that the initial vesa framebuffer had been loaded on the early stage of boot by kernel itself. while booting before kicking Xorg, the kernel modules of Graphic drivers were loaded and try to configure the various monitors via EDID or Video-BIOS. so in almost cases, radeon made successfully configure the correct resolutions, v-blank timing, display sizes, and so. and then, plymouth uses such "configured" primary vesa-fb to draw splash screen.

On the other hand, fglrx is the famous proprietary driver without any improvements of KMS features (we often said it "UMS"). its kernel module didn't do anything for vesa-fb. fglrx is always starting configurations after kicking Xorg, you know. so the plymouth couldn't use correct resolutions, color gradients, etc.

Finally, we also try to load "Yet another vesa framebuffer" for splash. as you know, something like "uvesafb" or like that. once you had embedded it into initramfs, the kernel would employ it as the primary vesa framebuffer instead of any other UMS drivers. but unfortunately today we're willing to purge such implementations from kenrel... why? yeah we would make the new features for it on kernel. we says it "multiple KMS framebuffer". this technology applies a bit difference to the previous stuff like uvesafb, but the results would be the same we hope... so oneiric kernel might or might not be succeeded to use the uvesafb while booting, but at least we only had the such choice for that today...

cheers.

---

### Post by baranovdmi on 2011-08-24
Hello there :),

  I have installed latest 11.10 AMD64 build on my x120e. Also I've installed fglrx driver. fglrx glx module is not loaded and as result I receive 2D unity and the following in the logs:
```

[    35.691] (EE) fglrx(0): atiddxDriScreenInit failed, GPS not been initialized. 
[    35.691] (WW) fglrx(0): ***********************************************************
[    35.691] (WW) fglrx(0): * DRI initialization failed                               *
[    35.692] (WW) fglrx(0): * kernel module (fglrx.ko) may be missing or incompatible *
[    35.692] (WW) fglrx(0): * 2D and 3D acceleration disabled                         *
[    35.692] (WW) fglrx(0): ***********************************************************
[    35.692] (II) fglrx(0): FBADPhys: 0x0 FBMappedSize: 0x10000000
[    35.733] (II) fglrx(0): FBMM initialized for area (0,0)-(1600,8191)
[    35.733] (II) fglrx(0): FBMM auto alloc for area (0,0)-(1600,1600) (front color buffer - assumption)
[    35.733] (II) fglrx(0): Largest offscreen area available: 1600 x 6591
[    35.734] (==) fglrx(0): Backing store disabled
[    35.734] (II) Loading extension FGLRXEXTENSION
[    35.734] (==) fglrx(0): DPMS enabled
[    35.734] (II) fglrx(0): Initialized in-driver Xinerama extension
[    35.734] (WW) fglrx(0): Textured Video not supported without DRI enabled.
[    35.734] (II) LoadModule: "glesx"
[    35.735] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/glesx.so
[    35.736] (II) Module glesx: vendor="X.Org Foundation"
[    35.736]    compiled for 1.4.99.906, module version = 1.0.0
[    35.736] (II) Loading extension GLESX
[    35.736] (II) fglrx(0): GLESX enableFlags = 576
[    35.736] (II) LoadModule: "amdxmm"
[    35.736] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/amdxmm.so
[    35.737] (II) Module amdxmm: vendor="X.Org Foundation"
[    35.737]    compiled for 1.4.99.906, module version = 2.0.0
[    35.737] (EE) fglrx(0): XMM failed to open CMMQS connection.(EE) fglrx(0): 
[    35.737] (EE) fglrx(0): XMM failed to initialize

```

But:
```

# modinfo fglrx | egrep 'author|description'
description:    ATI Fire GL
author:         Fire GL - ATI Research GmbH, Germany

```
kernel module is loaded. Could please anyone point me out where the problem is? I'd like to use fglrx due its powersave capabilities.

Oh. One more thing. As a "bonus" my laptop cannot restart correctly: it freezes forever with the black screen. I suppose because of kernel's fglrx and X.org's fallback module conflict.

---

### Post by afxmac on 2011-08-24
Grrr, suddendly my wireless connection is next to useless. 
AP is still the same, no changes there.

Though the signal indicator shows me 4 bars, my pings and other traffic do not got trough.
In syslog I see the following:
```

Aug 24 19:29:54 pixel kernel: [ 2867.840266] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
Aug 24 19:29:54 pixel kernel: [ 2867.940071] ====>to send ADDBAREQ!!!!!
Aug 24 19:29:54 pixel kernel: [ 2868.292980] ====>rx ADDBARSP from :00:24:fe:40:62:9f
Aug 24 19:29:54 pixel kernel: [ 2868.292991] rtllib: OnADDBARsp(): Recv ADDBA Rsp. BA invalid, DELBA!
Aug 24 19:29:55 pixel kernel: [ 2868.900282] ====>to send ADDBAREQ!!!!!
Aug 24 19:29:55 pixel kernel: [ 2868.902679] ====>rx ADDBARSP from :00:24:fe:40:62:9f
Aug 24 19:29:59 pixel kernel: [ 2872.852324] ====>rx ADDBAREQ from :00:24:fe:40:62:9f
Aug 24 19:29:59 pixel kernel: [ 2872.852348] ====>to send ADDBARSP
Aug 24 19:30:02 pixel kernel: [ 2875.947031] LPS Enter: notify AP we are dozing ++++++++++ SendNullFunctionData
Aug 24 19:30:13 pixel kernel: [ 2886.804120] ====>rx ADDBAREQ from :00:24:fe:40:62:9f
Aug 24 19:30:13 pixel kernel: [ 2886.804143] ====>to send ADDBARSP
Aug 24 19:30:18 pixel kernel: [ 2891.941383] LPS Enter: notify AP we are dozing ++++++++++ SendNullFunctionData
Aug 24 19:30:20 pixel kernel: [ 2893.700215] ====>to send ADDBAREQ!!!!!
Aug 24 19:30:20 pixel kernel: [ 2893.702761] ====>rx ADDBARSP from :00:24:fe:40:62:9f
Aug 24 19:30:22 pixel kernel: [ 2895.944145] LPS Enter: notify AP we are dozing ++++++++++ SendNullFunctionData
Aug 24 19:30:30 pixel kernel: [ 2903.943930] LPS Enter: notify AP we are dozing ++++++++++ SendNullFunctionData
Aug 24 19:30:42 pixel kernel: [ 2915.944646] LPS Enter: notify AP we are dozing ++++++++++ SendNullFunctionData
Aug 24 19:30:48 pixel kernel: [ 2921.943661] LPS Enter: notify AP we are dozing ++++++++++ SendNullFunctionData

```

Apart from the regular natty updates and those from Tistas repo, nothing system oriented is installed.

cheers
afx

---

### Post by tista on 2011-08-24
> **baranovdmi said:**
> Hello there :),

  I have installed latest 11.10 AMD64 build on my x120e. Also I've installed fglrx driver. fglrx glx module is not loaded and as result I receive 2D unity and the following in the logs:


But:
```

# modinfo fglrx | egrep 'author|description'
description:    ATI Fire GL
author:         Fire GL - ATI Research GmbH, Germany

```
kernel module is loaded. Could please anyone point me out where the problem is? I'd like to use fglrx due its powersave capabilities.

Oh. One more thing. As a "bonus" my laptop cannot restart correctly: it freezes forever with the black screen. I suppose because of kernel's fglrx and X.org's fallback module conflict.

Hi baranovdm.

Thanks for your nice trials to oneiric...
well... umm... if I remembered well, modinfo couldn't concern whether the module is now loaded or not. yeah such work is for the command "lsmod", right? modiinfo shows driver's details in kernel and/or dkms instead of the state it's loaded or unloaded... so you gonna try lsmod. ;)

cheers.

---

### Post by baranovdmi on 2011-08-24
**tista**
Thanks for the tip, anyway after sevel hours fighting against the proprietary blob I decided to get rid of it :). I installed Gallium3D driver from xorg-edges PPA and it works cool! Seems I'd prefer it to amd's blob.

But:
I recieve the error in Xorg.log:
```

[    29.300] (II) Loading /usr/lib/xorg/modules/drivers/fglrx_drv.so
[    29.300] (EE) Failed to load /usr/lib/xorg/modules/drivers/fglrx_drv.so: /usr/lib/xorg/modules/drivers/fglrx_drv.so: cannot open shared object file: No such file or directory
[    29.300] (EE) LoadModule: Module fglrx does not have a fglrxModuleData data object.

```
Why it tries to load the module which was uninstalled? There are no configs where it might be specified (the same for /usr/share/X11):
```

$ grep fglrx /etc/X11/* -R | wc -l
grep: /etc/X11/Xsession.d/10fglrx: No such file or directory
1

```

**Second** important question for me: are there any advices and tips about video powersaving? Any options for X.org? I am free to cut some video quality to get more battery life...

And unity 3D is not so responsive, any advices what features can be disabled to make it faster? Also time frame between login screen and desktop loading draw ups about 5-7 sec!

---

### Post by tista on 2011-08-25
> **baranovdmi said:**
> **tista**
Thanks for the tip, anyway after sevel hours fighting against the proprietary blob I decided to get rid of it :). I installed Gallium3D driver from xorg-edges PPA and it works cool! Seems I'd prefer it to amd's blob.

@baranovdmi

Yeah that's right! Gallium is really cool... ;)

> But:
I recieve the error in Xorg.log:
```

[    29.300] (II) Loading /usr/lib/xorg/modules/drivers/fglrx_drv.so
[    29.300] (EE) Failed to load /usr/lib/xorg/modules/drivers/fglrx_drv.so: /usr/lib/xorg/modules/drivers/fglrx_drv.so: cannot open shared object file: No such file or directory
[    29.300] (EE) LoadModule: Module fglrx does not have a fglrxModuleData data object.

```
Why it tries to load the module which was uninstalled? There are no configs where it might be specified (the same for /usr/share/X11):
```

$ grep fglrx /etc/X11/* -R | wc -l
grep: /etc/X11/Xsession.d/10fglrx: No such file or directory
1

```

OK... could you check the /etc/alternatives directory out? some symlinks might be remained...

> **Second** important question for me: are there any advices and tips about video powersaving? Any options for X.org? I am free to cut some video quality to get more battery life...

I'm using granola for linux to save the power...
[http://tista-blog.blogspot.com/2011/08/lets-saving-power-with-granola.html]("http://tista-blog.blogspot.com/2011/08/lets-saving-power-with-granola.html")

That's nice for CPU scaling, battery life, heat, and almost better than cpufreqd.
And the kernel option "pcie_aspm=force" I used. 

> And unity 3D is not so responsive, any advices what features can be disabled to make it faster? Also time frame between login screen and desktop loading draw ups about 5-7 sec!

Same issue +1.
today unity-3D is quite slow... damned!! especially after login from lightdm, it takes around 7 seconds until it's ready to use... actually much slower than gnome-shell... and after loading, compiz makes me mad for speed, you know! :sad: I've experienced such ugly slow on other GPU machines, so it might be caused compiz.

cheers.

---

### Post by tista on 2011-08-25
> **afxmac said:**
> Grrr, suddendly my wireless connection is next to useless. 
AP is still the same, no changes there.

Though the signal indicator shows me 4 bars, my pings and other traffic do not got trough.
In syslog I see the following:
```

Aug 24 19:29:54 pixel kernel: [ 2867.840266] rtl8192_hw_wakeup(): RF Change in progress! schedule wake up task again
Aug 24 19:29:54 pixel kernel: [ 2867.940071] ====>to send ADDBAREQ!!!!!
Aug 24 19:29:54 pixel kernel: [ 2868.292980] ====>rx ADDBARSP from :00:24:fe:40:62:9f
Aug 24 19:29:54 pixel kernel: [ 2868.292991] rtllib: OnADDBARsp(): Recv ADDBA Rsp. BA invalid, DELBA!
Aug 24 19:29:55 pixel kernel: [ 2868.900282] ====>to send ADDBAREQ!!!!!
Aug 24 19:29:55 pixel kernel: [ 2868.902679] ====>rx ADDBARSP from :00:24:fe:40:62:9f
Aug 24 19:29:59 pixel kernel: [ 2872.852324] ====>rx ADDBAREQ from :00:24:fe:40:62:9f
Aug 24 19:29:59 pixel kernel: [ 2872.852348] ====>to send ADDBARSP
Aug 24 19:30:02 pixel kernel: [ 2875.947031] LPS Enter: notify AP we are dozing ++++++++++ SendNullFunctionData
Aug 24 19:30:13 pixel kernel: [ 2886.804120] ====>rx ADDBAREQ from :00:24:fe:40:62:9f
Aug 24 19:30:13 pixel kernel: [ 2886.804143] ====>to send ADDBARSP
Aug 24 19:30:18 pixel kernel: [ 2891.941383] LPS Enter: notify AP we are dozing ++++++++++ SendNullFunctionData
Aug 24 19:30:20 pixel kernel: [ 2893.700215] ====>to send ADDBAREQ!!!!!
Aug 24 19:30:20 pixel kernel: [ 2893.702761] ====>rx ADDBARSP from :00:24:fe:40:62:9f
Aug 24 19:30:22 pixel kernel: [ 2895.944145] LPS Enter: notify AP we are dozing ++++++++++ SendNullFunctionData
Aug 24 19:30:30 pixel kernel: [ 2903.943930] LPS Enter: notify AP we are dozing ++++++++++ SendNullFunctionData
Aug 24 19:30:42 pixel kernel: [ 2915.944646] LPS Enter: notify AP we are dozing ++++++++++ SendNullFunctionData
Aug 24 19:30:48 pixel kernel: [ 2921.943661] LPS Enter: notify AP we are dozing ++++++++++ SendNullFunctionData

```

Apart from the regular natty updates and those from Tistas repo, nothing system oriented is installed.

cheers
afx

Hi afx. ;)

what a pity... :sad:
for me, I could see the cycle "dozing" & "awaking"... now I didn't have any clue.
does anyone had any ideas? ;)

regards.

---

### Post by baranovdmi on 2011-08-25
**@tista**

> OK... could you check the /etc/alternatives directory out? some symlinks might be remained...

Yes, they definitely are, but all symlinks which point to fglrx are invalid since there no such path anymore. Should they be removed manually by 'unlink' or whatever?

```
lrwxrwxrwx 1 root root  22 2011-08-24 19:42 x86_64-linux-gnu_10fglrx -> /usr/lib/fglrx/10fglrx
lrwxrwxrwx 1 root root  28 2011-08-24 19:42 x86_64-linux-gnu_amdconfig -> /usr/lib/fglrx/bin/amdconfig
lrwxrwxrwx 1 root root  30 2011-08-24 19:42 x86_64-linux-gnu_amdnotifyui -> /usr/lib/fglrx/bin/amdnotifyui
lrwxrwxrwx 1 root root  22 2011-08-24 19:42 x86_64-linux-gnu_ati_conf -> /usr/lib/fglrx/etc/ati
lrwxrwxrwx 1 root root  28 2011-08-24 19:42 x86_64-linux-gnu_aticonfig -> /usr/lib/fglrx/bin/aticonfig
lrwxrwxrwx 1 root root  29 2011-08-24 19:42 x86_64-linux-gnu_atieventsd -> /usr/lib/fglrx/bin/atieventsd
lrwxrwxrwx 1 root root  27 2011-08-24 19:42 x86_64-linux-gnu_atiodcli -> /usr/lib/fglrx/bin/atiodcli
lrwxrwxrwx 1 root root  25 2011-08-24 19:42 x86_64-linux-gnu_atiode -> /usr/lib/fglrx/bin/atiode
lrwxrwxrwx 1 root root  31 2011-08-24 19:42 x86_64-linux-gnu_fgl_glxgears -> /usr/lib/fglrx/bin/fgl_glxgears
lrwxrwxrwx 1 root root  31 2011-08-24 19:42 x86_64-linux-gnu_fglrx_dri -> /usr/lib/fglrx/dri/fglrx_dri.so
lrwxrwxrwx 1 root root  48 2011-08-24 19:42 x86_64-linux-gnu_fglrx_drv -> /usr/lib/fglrx/xorg/modules/drivers/fglrx_drv.so
lrwxrwxrwx 1 root root  28 2011-08-24 19:42 x86_64-linux-gnu_fglrxinfo -> /usr/lib/fglrx/bin/fglrxinfo
lrwxrwxrwx 1 root root  24 2011-08-24 19:42 x86_64-linux-gnu_fglrx_modconf -> /lib/fglrx/modprobe.conf
lrwxrwxrwx 1 root root  38 2011-08-24 19:42 x86_64-linux-gnu_grub_fb_blacklist -> /usr/share/fglrx/fglrx.grub-gfxpayload
lrwxrwxrwx 1 root root  29 2011-08-24 19:42 x86_64-linux-gnu_libAMDXvBA_cap -> /usr/lib/fglrx/libAMDXvBA.cap
lrwxrwxrwx 1 root root  29 2011-08-24 19:42 x86_64-linux-gnu_libaticalcl.so -> /usr/lib/fglrx/libaticalcl.so
lrwxrwxrwx 1 root root  31 2011-08-24 19:42 x86_64-linux-gnu_libaticalcl.so_lib32 -> /usr/lib32/fglrx/libaticalcl.so
lrwxrwxrwx 1 root root  29 2011-08-24 19:42 x86_64-linux-gnu_libaticalrt.so -> /usr/lib/fglrx/libaticalrt.so
lrwxrwxrwx 1 root root  31 2011-08-24 19:42 x86_64-linux-gnu_libaticalrt.so_lib32 -> /usr/lib32/fglrx/libaticalrt.so
```

> I'm using granola for linux to save the power..
Looks cool, but seems to be again proprietary, is not it?

> compiz makes me mad for speed, you know!

Do not you know will Unity 3D work w/o compiz?

Thanks,

---

### Post by tista on 2011-08-25
@baranovdmi

> Yes, they definitely are, but all symlinks which point to fglrx are invalid since there no such path anymore. Should they be removed manually by 'unlink' or whatever?

If these links were un-linked, feel free to purge manually... 

> Looks cool, but seems to be again proprietary, is not it?

Yep, but quite different from fglrx! :P

> Do not you know will Unity 3D work w/o compiz?

Oh really?! if could, what a nice! at least all what I know is wayland plan or so... I also hope "client side compositor" for gtk3 on wayland. it must be very faster rendering for everything... or recently qt4 engine had been polished dramatically as well, I suppose Unity-2D would beat 3D in almost cases of our general desktop experiences... finally our  radeon drivers would be the best solutions for the next generation like XWayland!! :P

cheers.

---

### Post by afxmac on 2011-08-25
> **tista said:**
> Hi afx. ;)

what a pity... :sad:
for me, I could see the cycle "dozing" & "awaking"... now I didn't have any clue.

Though I did the reboot dance in-between, this was still an issue. 
Later that night after another reboot and some cable based use it worked just fine. 
Guess we have to chalk this down to random flakiness for now ;-(

cheers
afx

---

### Post by tista on 2011-08-25
> **afxmac said:**
> Though I did the reboot dance in-between, this was still an issue. 
Later that night after another reboot and some cable based use it worked just fine. 
Guess we have to chalk this down to random flakiness for now ;-(

cheers
afx

@afx

I've noticed the updates on Realtek site!! :P
[http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8192CE-VA4]("http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8192CE-VA4")
so ASAP I would sync the new sources and packaging... in this time, may I choose "2.6.35 (and later)"? the version is 0004.0816.2011 released in Aug.23...

stay-tuned!! ;)

tista

**EDIT #1**
Just now I've uploaded the new release named "r8192ce_35.0004.0816.2011~natty2" for natty!
soon build would be finished and you could give it a try on natty...

In this time, 2 modules were made. 1st is "r8192ce_pci" and 2nd is "rtlwifi_pci". I suppose these sources would be almost same as what oneiric kernel is applied... though I have to suggest blacklisting as same method in previous version unfortunately, seems good for testing them on my oneiric now...

In this period, I didn't think it would be needed for oneiric, but if anyone want it, I would do after! ;)

**EDIT #2**
Oh forgot to mention. because of the versioning, first you should purge previous one, and then install the current one. if you guys ignored that, r8192ce_pci module didn't update to the current build since the previous one had more higher revision...

---

### Post by afxmac on 2011-08-26
Hi tista,

only seen your edits today and I am a bit confused. 
I assume I need to
dpkg -r r8192ce-pci 
and then apt-get install r8192ce-pci ?

[I]edit: I missed the name difference so it was 
dpkg -r r8192ce-pci
apt-get install r8192ce

Still no idea about the problem below....[/I]

But until I get to that stage I am still stumbling around with some other dependency problems. 
I see 

update-alternatives: error: alternative xorg_extra_modules can't be slave of gl_conf: it is a slave of x86_64-linux-gnu_gl_conf

in my install logs which then leads to a slew of non configured mesa libs.
Hmm, was that removal of alternatives for gl_conf a bit too drastic? 

cheers
afx

---

### Post by tista on 2011-08-26
> **afxmac said:**
> Hi tista,

only seen your edits today and I am a bit confused. 
I assume I need to
dpkg -r r8192ce-pci 
and then apt-get install r8192ce-pci ?

[I]edit: I missed the name difference so it was 
dpkg -r r8192ce-pci
apt-get install r8192ce

Still no idea about the problem below....[/I]

@afx

I think it is enough to run apt-get?
sudo apt-get purge r8192ce
and then, 
sudo apt-get install r8192ce

> But until I get to that stage I am still stumbling around with some other dependency problems. 
I see 

update-alternatives: error: alternative xorg_extra_modules can't be slave of gl_conf: it is a slave of x86_64-linux-gnu_gl_conf

in my install logs which then leads to a slew of non configured mesa libs.
Hmm, was that removal of alternatives for gl_conf a bit too drastic? 

cheers
afx


so... what version did you install fglrx? it seems higher than 8.872 (because of the alternatives problem). and today, 8.881 solved a lot of problems on oneiric, so could you download it on official site, then making package, and install it? obviously that 8.881 should be better than mine... ;) now I'm working for gnome3/gnome-shell on git, so few time to package 8.881 on my PPA... :sad:

cheers.

---

### Post by afxmac on 2011-08-27
> **tista said:**
> I think it is enough to run apt-get?[/zquote]
Sure, that dpkg use is just a habit. 

> 
so... what version did you install fglrx? it seems higher than 8.872 (because of the alternatives problem). 

2:8.872~natty6 

[quote]8.881 solved a lot of problems on oneiric, so could you download it on official site, then making package, and install it? obviously that 8.881 should be better than mine... ;) now I'm working for gnome3/gnome-shell on git, so few time to package 8.881 on my PPA... :sad:
Would you have a pointer to packaging for beginners?
I assume I need to start from the ati-driver-installer-11-8-x86.x86_64.run file from ATI.

thx
afx

---

### Post by tista on 2011-08-27
> **afxmac said:**
> [QUOTE=tista;11191111]I think it is enough to run apt-get?[/zquote]
Sure, that dpkg use is just a habit. 



2:8.872~natty6 


Would you have a pointer to packaging for beginners?
I assume I need to start from the ati-driver-installer-11-8-x86.x86_64.run file from ATI.

thx
afx

Hi afx.

OK.

For example, in 8.880 preview driver could be built deb package for natty via this command:
```
sudo ./AMD_Catalyst_Preview_driver_OpenGL_4.2_beta_support_8.88.8-x86.x86_64.run --buildpkg Ubuntu/natty
```

or if you need source pakcage, run this:
```
sudo ./AMD_Catalyst_Preview_driver_OpenGL_4.2_beta_support_8.88.8-x86.x86_64.run --buildpkg Ubuntu/source
```

crossing fingers! ;)

---

### Post by afxmac on 2011-08-27
Hmm, where would I find the run file you mentioned? I only have 
ati-driver-installer-11-8-x86.x86_64.run 
But that accepts the build option and creates three debs. But when I try to install them, I run into errors related to the alternatives file:```
# dpkg -i fglrx_8.881-0ubuntu1_amd64.deb fglrx-dev_8.881-0ubuntu1_amd64.deb fglrx-amdcccle_8.881-0ubuntu1_amd64.deb
(Reading database ... 314505 files and directories currently installed.)
Preparing to replace fglrx 2:8.872~natty6 (using fglrx_8.881-0ubuntu1_amd64.deb) ...
Removing all DKMS Modules
Done.
Unpacking replacement fglrx ...
Preparing to replace fglrx-dev 2:8.872~natty6 (using fglrx-dev_8.881-0ubuntu1_amd64.deb) ...
Unpacking replacement fglrx-dev ...
Preparing to replace fglrx-amdcccle 2:8.872~natty6 (using fglrx-amdcccle_8.881-0ubuntu1_amd64.deb) ...
Unpacking replacement fglrx-amdcccle ...
Setting up fglrx (2:8.881-0ubuntu1) ...
update-alternatives: error: alternative aticonfig can't be slave of gl_conf: it is a slave of x86_64-linux-gnu_gl_conf
dpkg: error processing fglrx (--install):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of fglrx-dev:
 fglrx-dev depends on fglrx; however:
  Package fglrx is not configured yet.
dpkg: error processing fglrx-dev (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of fglrx-amdcccle:
 fglrx-amdcccle depends on fglrx; however:
  Package fglrx is not configured yet.
dpkg: error processing fglrx-amdcccle (--install):
 dependency problems - leaving unconfigured
Processing triggers for ureadahead ...
Errors were encountered while processing:
 fglrx
 fglrx-dev
 fglrx-amdcccle
```

cheers
afx

---

### Post by tista on 2011-08-27
> **afxmac said:**
> Hmm, where would I find the run file you mentioned? I only have 
ati-driver-installer-11-8-x86.x86_64.run 
But that accepts the build option and creates three debs. But when I try to install them, I run into errors related to the alternatives file:```
# dpkg -i fglrx_8.881-0ubuntu1_amd64.deb fglrx-dev_8.881-0ubuntu1_amd64.deb fglrx-amdcccle_8.881-0ubuntu1_amd64.deb
(Reading database ... 314505 files and directories currently installed.)
Preparing to replace fglrx 2:8.872~natty6 (using fglrx_8.881-0ubuntu1_amd64.deb) ...
Removing all DKMS Modules
Done.
Unpacking replacement fglrx ...
Preparing to replace fglrx-dev 2:8.872~natty6 (using fglrx-dev_8.881-0ubuntu1_amd64.deb) ...
Unpacking replacement fglrx-dev ...
Preparing to replace fglrx-amdcccle 2:8.872~natty6 (using fglrx-amdcccle_8.881-0ubuntu1_amd64.deb) ...
Unpacking replacement fglrx-amdcccle ...
Setting up fglrx (2:8.881-0ubuntu1) ...
update-alternatives: error: alternative aticonfig can't be slave of gl_conf: it is a slave of x86_64-linux-gnu_gl_conf
dpkg: error processing fglrx (--install):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of fglrx-dev:
 fglrx-dev depends on fglrx; however:
  Package fglrx is not configured yet.
dpkg: error processing fglrx-dev (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of fglrx-amdcccle:
 fglrx-amdcccle depends on fglrx; however:
  Package fglrx is not configured yet.
dpkg: error processing fglrx-amdcccle (--install):
 dependency problems - leaving unconfigured
Processing triggers for ureadahead ...
Errors were encountered while processing:
 fglrx
 fglrx-dev
 fglrx-amdcccle
```

cheers
afx

@afx

good packaging! ;)
and OK.

run this first:
```
sudo update-alternatives --remove-all x86_64-linux-gnu_gl_conf
```
and then:
```
sudo dpkg -i fglrx_8.881-0ubuntu1_amd64.deb fglrx-amdcccle_8.881-0ubuntu1_amd64.deb
```

give a try... :-)

---

### Post by afxmac on 2011-08-27
Nuking the alternatives did the trick.

(now how did it get into that state????)

thx
afx

---

### Post by tista on 2011-08-28
Hi guys.

A couple of days ago, I've uploaded newbie driver r8192ce for Natty. 
In that time, I employed upstream sources updated most recently on Realtek site, from that time I've been testing this driver on oneiric seriously...

[good]
* for contributers, this version might help us nicely to package, file, versioning, and so.
* by separated, got higher modularity, good to handle a lot of sources.
* battery powered connecting seems to be better than before.

[bad]
* these're the flood of logs showed in dmesg still.
* the link quality b/g/n goes worse a bit.
* an average of down/up speed were slightly decreased and unstable.
* sometimes link was down suddenly, obviously that would be more frequently than the previous one on AC power.

after you guys had tested, let me know whether I should keep these sources alive or rollback to the previous! ;)

cheers.

---

### Post by baranovdmi on 2011-08-29
Hey, tista!

> **tista said:**
> 
Oh really?! if could, what a nice! at least all what I know is wayland plan or so... I also hope "client side compositor" for gtk3 on wayland. it must be very faster rendering for everything... or recently qt4 engine had been polished dramatically as well, I suppose Unity-2D would beat 3D in almost cases of our general desktop experiences... finally our  radeon drivers would be the best solutions for the next generation like XWayland!! :P
cheers.
Sorry that's my English :D I meant to ask if it was possible to run Unity 3D w/o compiz. I hate the performance of my current desktop :( Unity 2D is not fast also. Any tweaks? One or two extra days and seems I will get rid of it on my X120e. I miss the performance of Gnome2.

On system boot I receive the following messages from Grub:
```
No video mode activated.
Incompatible license
```

These messages are stay for 3-4 secs and then splashscreen (Plymouth, right?) starts. How to fix this?

And how to stop display brightness dramatic change when grub starts? Why the previous brightness level is not saved?

---

### Post by tista on 2011-08-29
> **baranovdmi said:**
> Hey, tista!


Sorry that's my English :D I meant to ask if it was possible to run Unity 3D w/o compiz. I hate the performance of my current desktop :( Unity 2D is not fast also. Any tweaks? One or two extra days and seems I will get rid of it on my X120e. I miss the performance of Gnome2.

Hi baranovdmi. ;)

well. No problem. since really bad English is mine... :P

and unfortunately unity-3D is designed as compiz plug-ins, so today we could never separate them. in the past, the early unity had used to be developed on mutter/clutter 3D renderings as stand alone apps, but that one was more horrible thing!! :sad: 

today many devs are willing to polish their "Look&Feel" until future freeze come, in most cases, such sequence makes us ugly mad especially "Performance&Stability". that's very now I think. as known well, compiz scores the worst performance I've never seen before!! so I have not any clue for performance tuning in this period... so sorry...

otherwise, recently I'm using gnome-shell and pantheon on radeon driver. gnome-shell isn't so fast, but rich, sexy, and smoothly! ;) and then, pantheon is the default shell for elementary. in other words, it's similar to classic gtk2 shell about speed since it works on metacity, lightweight panel, tiny dock, and special tuned apps designed for elementary OS. every stuff are developed by Vala language for front-end of C++/C. I often use Vala as well. :P it makes great performance advantages than python, perl, even by Qt4!

> On system boot I receive the following messages from Grub:
```
No video mode activated.
Incompatible license
```

These messages are stay for 3-4 secs and then splashscreen (Plymouth, right?) starts. How to fix this?

And how to stop display brightness dramatic change when grub starts? Why the previous brightness level is not saved?

Yeah that's unsolved issue on kernel. because now we didn't have any acpi handler working on our beloved X120e/X121e. even if  thinkpad-acpi module had been loaded, it couldn't handle an embedded controller on our PC... :sad: so I'm waiting linux-next team or someone develops/scratches acpi codes for latest lenovo laptops.

cheers.

---

### Post by mr_raider on 2011-08-29
Since installing 11.04 x64 on my x120, I have had random freezes where the screen become unresponsive, the mouse does not move, and I have to power cycle the laptop to reboot. Ctrl-alt-del, ctrl-alt-backspace and ctral-alt-f1 don't work.

I mnaually upgraded to catalyst 11.8, with no improvent. I tried Unity, gnome and gnome classic with no improvement. This problem was not there in 10.10.

Any ideas?

---

### Post by linuxcss on 2011-08-30
Mr_Raider  ... in 10.10 any issues?
Does audio work without stutters or freeze ups when playing flash?
Does suspend/resume work? As in wifi working after resuming etc?

thanx

---

### Post by mr_raider on 2011-08-30
> **linuxcss said:**
> Mr_Raider  ... in 10.10 any issues?
Does audio work without stutters or freeze ups when playing flash?
Does suspend/resume work? As in wifi working after resuming etc?

thanx

The only issue I had in 10.10 was xbmc crashing on exit. I was also unable to run certain adobe air applications. Other than that it was fine.

---

### Post by thebluesgnr on 2011-08-31
Hi everyone,

I recently bought an HP dm1z laptop, which uses the same chipset as this Thinkpad (which unfortunately is unavailable over here). Anyway, I was wondering if this laptop has a similar problem to mine: really high CPU usage by Xorg when using the radeon driver. 

I thought it might be related to compiz or gnome-shell but the problem is still there while running a "fallback" gnome-session with metacity. I've tried Ubuntu 11.10, Fedora 15 and 16-alpha, and even the vesa drivers perform better (but shows artifacts under text mode). 

This problem hurts the performance of the system pretty badly, and battery life as well.

fglrx works much better, but shows artifacts with gnome-shell (which I love) and sometimes the display color/contrast/saturation levels look really weird and I have no idea what's causing that or how to get it back.

Anyway, I was just wondering if this is a general problem with the AMD E-350+Radeon 6310HD combo under Linux or if it's specific to my laptop.

Thanks!

---

### Post by tista on 2011-08-31
Hi guys. 

I'm back from the battlefield of gnome-shell 3.1.90 new release... ;)

@thebluesgnr

OMG... although I've never seen such "resource hungry" with radeon... :sad:
so let me see your Xorg.0.log!

cheers.

---

### Post by mr_raider on 2011-08-31
IMHO, the best combo for this laptop is 10.10 with fglrx. It was the most stable build by far. 10.4 was rock solid too but you had to compile your own wireless drivers.

---

### Post by thebluesgnr on 2011-08-31
> **tista said:**
> Hi guys. 

I'm back from the battlefield of gnome-shell 3.1.90 new release... ;)

@thebluesgnr

OMG... although I've never seen such "resource hungry" with radeon... :sad:
so let me see your Xorg.0.log!

cheers.

I reinstalled oneiric with the latest daily-live image and now the radeon driver seems to be working fine! The issue was either fixed in the last few days or I'm going crazy with all the distributions testing, which is quite possible. :)

I'll give another try with Fedora 15 and 16 to see if there's a specific problem there. If so, I'll pursue a solution with their bugzilla and other resources. 

Thanks for the help! Your posts in this topic have been invaluable, even if I own a different but similar laptop.

---

### Post by tista on 2011-08-31
> **thebluesgnr said:**
> I reinstalled oneiric with the latest daily-live image and now the radeon driver seems to be working fine! The issue was either fixed in the last few days or I'm going crazy with all the distributions testing, which is quite possible. :)

I'll give another try with Fedora 15 and 16 to see if there's a specific problem there. If so, I'll pursue a solution with their bugzilla and other resources. 

Thanks for the help! Your posts in this topic have been invaluable, even if I own a different but similar laptop.

Hi thebluesgnr.

Ah OK.. I'm glad to hear. and to be honest, I was a user of fedora from core1! :P
I also think it's important that we have to make some chance to try various distributions at least 3 or 4 since we couldn't understand which distro would be the best for ourselves without any "testings"... 

For senior users, couples of "distro testings" sometimes makes sense and gives clearly answers to debug, report, and file the bugs. ;)

regards.

---

### Post by tista on 2011-09-01
Hi guys.

today I'm starting to make thinkpad_acpi dkms package!! :P
yeah we've experienced some unlucky issue on our beloved X120e/X121e, so I'd like to fix it. just now I pulled the latest source from linux-next git tree, then I made package oneiric first. soon natty's one would land...

PPA is here:
[https://launchpad.net/~tista/+archive/x120e]("https://launchpad.net/~tista/+archive/x120e")

I would keep my eyes open for this module...

**EDIT**
Just now I'm adding "hdaps" module into this package...
```
[    4.154626] hdaps: inverting axis (3) readings
[    4.154633] hdaps: LENOVO ThinkPad X120e detected
[    4.155313] input: hdaps as /devices/platform/hdaps/input/input7
[    4.155414] hdaps: driver successfully loaded
```

seems GOOD! ;)
soon I would upload the latest version...

see ya.

---

### Post by VCSkier on 2011-09-01
Yay for acpi package! Thanks Tista.

I tried to install it though, and got this.```
reed@Natty-ThinkPad-X120e:~$ sudo apt-get install thinkpad-acpi-dkms 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  thinkpad-acpi-dkms
0 upgraded, 1 newly installed, 0 to remove and 2 not upgraded.
Need to get 0 B/65.9 kB of archives.
After this operation, 307 kB of additional disk space will be used.
Selecting previously deselected package thinkpad-acpi-dkms.
(Reading database ... 130744 files and directories currently installed.)
Unpacking thinkpad-acpi-dkms (from .../thinkpad-acpi-dkms_0.1.0-git20110901.a50245af~natty3_all.deb) ...
Setting up thinkpad-acpi-dkms (0.1.0-git20110901.a50245af~natty3) ...

Creating symlink /var/lib/dkms/thinkpad-acpi-dkms/0.1.0/source ->
                 /usr/src/thinkpad-acpi-dkms-0.1.0

DKMS: add Completed.

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
make KERNELRELEASE=2.6.38-11-generic -C /lib/modules/2.6.38-11-generic/build M=/var/lib/dkms/thinkpad-acpi-dkms/0.1.0/build....(bad exit status: 2)

Error! Bad return status for module build on kernel: 2.6.38-11-generic (x86_64)
Consult the make.log in the build directory
/var/lib/dkms/thinkpad-acpi-dkms/0.1.0/build/ for more information.
0
0
reed@Natty-ThinkPad-X120e:~$ 

```That doesn't seem quite right to me. What am I doing wrong?

Obviously, I'm trying to install this on 11.04.

---

### Post by tista on 2011-09-01
> **VCSkier said:**
> Yay for acpi package! Thanks Tista.

I tried to install it though, and got this.```
reed@Natty-ThinkPad-X120e:~$ sudo apt-get install thinkpad-acpi-dkms 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  thinkpad-acpi-dkms
0 upgraded, 1 newly installed, 0 to remove and 2 not upgraded.
Need to get 0 B/65.9 kB of archives.
After this operation, 307 kB of additional disk space will be used.
Selecting previously deselected package thinkpad-acpi-dkms.
(Reading database ... 130744 files and directories currently installed.)
Unpacking thinkpad-acpi-dkms (from .../thinkpad-acpi-dkms_0.1.0-git20110901.a50245af~natty3_all.deb) ...
Setting up thinkpad-acpi-dkms (0.1.0-git20110901.a50245af~natty3) ...

Creating symlink /var/lib/dkms/thinkpad-acpi-dkms/0.1.0/source ->
                 /usr/src/thinkpad-acpi-dkms-0.1.0

DKMS: add Completed.

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
make KERNELRELEASE=2.6.38-11-generic -C /lib/modules/2.6.38-11-generic/build M=/var/lib/dkms/thinkpad-acpi-dkms/0.1.0/build....(bad exit status: 2)

Error! Bad return status for module build on kernel: 2.6.38-11-generic (x86_64)
Consult the make.log in the build directory
/var/lib/dkms/thinkpad-acpi-dkms/0.1.0/build/ for more information.
0
0
reed@Natty-ThinkPad-X120e:~$ 

```That doesn't seem quite right to me. What am I doing wrong?

Obviously, I'm trying to install this on 11.04.

Hi VCSkier.

OK...
let me see your /var/lib/dkms/thinkpad-acpi-dkms/0.1.0/build/make.log?
this file usually records all of build log...

I might fix build error on natty kernel.

cheers.

---

### Post by ProNux on 2011-09-02
I have an "almost similar" notebook, Fujitsu PH521 with AMD Fusion APU E-350.  I tried live-USB, and surprisingly, all of my hardware are detected.  CPU stepping works well.

ONLY PROBLEM:  Ubuntu won't start after install due to UEFI BIOS issues.

---

### Post by VCSkier on 2011-09-02
/var/lib/dkms/thinkpad-acpi-dkms/0.1.0/build/make.log
```
DKMS make.log for thinkpad-acpi-dkms-0.1.0 for kernel 2.6.38-11-generic (x86_64)
Thu Sep  1 20:02:11 EDT 2011
make: Entering directory `/usr/src/linux-headers-2.6.38-11-generic'
  LD      /var/lib/dkms/thinkpad-acpi-dkms/0.1.0/build/built-in.o
  CC [M]  /var/lib/dkms/thinkpad-acpi-dkms/0.1.0/build/thinkpad_acpi.o
/var/lib/dkms/thinkpad-acpi-dkms/0.1.0/build/thinkpad_acpi.c: In function ‘brightness_init’:
/var/lib/dkms/thinkpad-acpi-dkms/0.1.0/build/thinkpad_acpi.c:6300:7: error: ‘struct backlight_properties’ has no member named ‘type’
/var/lib/dkms/thinkpad-acpi-dkms/0.1.0/build/thinkpad_acpi.c:6300:15: error: ‘BACKLIGHT_PLATFORM’ undeclared (first use in this function)
/var/lib/dkms/thinkpad-acpi-dkms/0.1.0/build/thinkpad_acpi.c:6300:15: note: each undeclared identifier is reported only once for each function it appears in
make[1]: *** [/var/lib/dkms/thinkpad-acpi-dkms/0.1.0/build/thinkpad_acpi.o] Error 1
make: *** [_module_/var/lib/dkms/thinkpad-acpi-dkms/0.1.0/build] Error 2
make: Leaving directory `/usr/src/linux-headers-2.6.38-11-generic'
```

---

### Post by VCSkier on 2011-09-04
> **ProNux said:**
> I have an "almost similar" notebook, Fujitsu PH521 with AMD Fusion APU E-350.  I tried live-USB, and surprisingly, all of my hardware are detected.  CPU stepping works well.

ONLY PROBLEM:  Ubuntu won't start after install due to UEFI BIOS issues.

On my system (ThinkPad X120e), the system boots fine as long as it's using the grub-efi-amd64 package. There was a while there where 11.04 was trying to remove it in favor of the default grub package whenever I would do a dist-upgrade, but that's not the case anymore.

Beyond that ProNux, I have no idea what could be causing your problem.

---

### Post by tista on 2011-09-05
> **VCSkier said:**
> /var/lib/dkms/thinkpad-acpi-dkms/0.1.0/build/make.log
```
DKMS make.log for thinkpad-acpi-dkms-0.1.0 for kernel 2.6.38-11-generic (x86_64)
Thu Sep  1 20:02:11 EDT 2011
make: Entering directory `/usr/src/linux-headers-2.6.38-11-generic'
  LD      /var/lib/dkms/thinkpad-acpi-dkms/0.1.0/build/built-in.o
  CC [M]  /var/lib/dkms/thinkpad-acpi-dkms/0.1.0/build/thinkpad_acpi.o
/var/lib/dkms/thinkpad-acpi-dkms/0.1.0/build/thinkpad_acpi.c: In function ‘brightness_init’:
/var/lib/dkms/thinkpad-acpi-dkms/0.1.0/build/thinkpad_acpi.c:6300:7: error: ‘struct backlight_properties’ has no member named ‘type’
/var/lib/dkms/thinkpad-acpi-dkms/0.1.0/build/thinkpad_acpi.c:6300:15: error: ‘BACKLIGHT_PLATFORM’ undeclared (first use in this function)
/var/lib/dkms/thinkpad-acpi-dkms/0.1.0/build/thinkpad_acpi.c:6300:15: note: each undeclared identifier is reported only once for each function it appears in
make[1]: *** [/var/lib/dkms/thinkpad-acpi-dkms/0.1.0/build/thinkpad_acpi.o] Error 1
make: *** [_module_/var/lib/dkms/thinkpad-acpi-dkms/0.1.0/build] Error 2
make: Leaving directory `/usr/src/linux-headers-2.6.38-11-generic'
```

@VCSkier

Sorry for my delayed reply... 
and thanks so much for your log! ;)

Yeah is seems to need some patchworks for natty kernel, so I'm going to install natty kernel on my oneiric and try to build on it...

see u soon.
cheers.

---

### Post by VCSkier on 2011-09-05
Thanks Tista.

If it turns out to require much work, don't worry about it. I'll be transitioning to Oneric in October anyway.

---

### Post by VCSkier on 2011-09-15
Where could I find some information on the performance/battery life differences between the standard radeon driver and the gallium3d driver for the 6310, specifically on Oneiric? Would anyone here be able to share their experience?

I've been using fglrx on 11.04, mainly because of the improved battery life, and I suspect that I'll need to continue to use fglrx on Oneiric, but I do think I will probably want to switch to an open source driver eventually. I just want to be aware of my options.

Thanks.

---

### Post by tista on 2011-09-17
> **VCSkier said:**
> Where could I find some information on the performance/battery life differences between the standard radeon driver and the gallium3d driver for the 6310, specifically on Oneiric? Would anyone here be able to share their experience?

I've been using fglrx on 11.04, mainly because of the improved battery life, and I suspect that I'll need to continue to use fglrx on Oneiric, but I do think I will probably want to switch to an open source driver eventually. I just want to be aware of my options.

Thanks.

Hi VCSkier.

Umm... that might be a bit hard to explain for.. ;)
Reason1. standard radeon driver uses "swrast" renderer for AIGLX. it means avoiding any hardware-accels on any types of GPU... so swrast wastes a lot of resources to draw 3D. exactly the performances on swrast is horrible thing! :S

Reason2. Gallium3D has 2 sides of rendering for AIGLX. 1st is, for example, on our HD6310, "AMD PALM" codes. it means hardware accelerated GPU specific codes. I'm using it. 2nd is based on llvmpipe, in other words, it means "accelerated swrast". but in almost cases, seems better to draw 3D than standard swrast obviously... why 2 sides? yeah sometimes on tricky GPU couldn't load 1st one, so 2nd one must be needed for such GPU. 

In past, our 6310 could get llvmpipe for 3D desktop experiences, then now, seems we had no choice to use llvmpipe for Unity, Gnome-shell, Mutter, and so... basic glx tools would be OK, but it never be anything special today...

Finally on my X121e with running oneiric, fglrx could increase the battery life around 10 or 15% compared with radeon/Gallium3D exactly. but the differences were not so huge... :)
To be honest, I really want to experience ubuntu 12.04 release instead of Oneiric!! yep, "Wayland" would be comming! but in this period, fglrx NEVER approve wayland, if we have to run fglrx in the future, we might never get any future works on our desktops...

cheers.

---

### Post by VCSkier on 2011-09-22
Good information. Thanks Tista.

So it does indeed sound like I will continue to use fglrx through Oneric. Hopefully next year when 12.04 is released, some of the resource usage issues will be resolved and the r600g driver will be a good alternative on our hardware.

Let's keep our fingers crossed.

---

### Post by usvi on 2011-09-26
Hello,

I have been now running Kubuntu 11.04 in my X120e E-350 with 8 gigs of RAM and 3G modem. I have to say that I'm impressed.

I earlier had lock-ups, but I think that blacklisting  rtl8192ce module has done the trick for me. I have not had any lock-ups since. Now I'm using r8192ce_pci for WLAN. I'm also using ATI's proprietary driver package 11.8 and pcie_aspm=force kernel option. For sound this module option was needed in /etc/modprobe.d/alsa-base.conf: options snd-hda-intel index=1

Even the 3G works fine (of course I had to extract the binaries from Windows installation); knetwork-manager is very fast to connect; this is unbelievable considering how poorly it was performing in 10.04. I'm now really looking forward into seeing how good 12.04 LTS will be.

---

### Post by tista on 2011-09-27
> **usvi said:**
> Hello,

I have been now running Kubuntu 11.04 in my X120e E-350 with 8 gigs of RAM and 3G modem. I have to say that I'm impressed.

I earlier had lock-ups, but I think that blacklisting  rtl8192ce module has done the trick for me. I have not had any lock-ups since. Now I'm using r8192ce_pci for WLAN. I'm also using ATI's proprietary driver package 11.8 and pcie_aspm=force kernel option. For sound this module option was needed in /etc/modprobe.d/alsa-base.conf: options snd-hda-intel index=1

Even the 3G works fine (of course I had to extract the binaries from Windows installation); knetwork-manager is very fast to connect; this is unbelievable considering how poorly it was performing in 10.04. I'm now really looking forward into seeing how good 12.04 LTS will be.

Hi usvi,

Thanks for your reports! ;)
And you mean that 3G works on Gobi2000 module? Wow cool!! :P
Yeah on Lucid, 3G was really horrible... :S but now it seems to be polished the codes on both kernel-space/user-space, right? Unfortunately I didn't use 3G yet, but near the future I would employ it...

And Yep, 12.04 would make an amazing evolution in any places, I believe. then we're lucky that 12.04 means LTS as well.

cheers.

---

### Post by usvi on 2011-10-01
> **tista said:**
> Hi usvi,

Thanks for your reports! ;)
And you mean that 3G works on Gobi2000 module? Wow cool!! :P
Yeah on Lucid, 3G was really horrible... :S but now it seems to be polished the codes on both kernel-space/user-space, right? Unfortunately I didn't use 3G yet, but near the future I would employ it...


Yeah, Qualcom Gobi 2000:

```
Bus 001 Device 002: ID 05c6:9205 Qualcomm, Inc.
```In fact, this post was submitted using the internal 3G. My Gobi 2000 is actually borrowed from an old X100e. Interestingly, they aren't selling X120e's to Europe, so I had to buy one from eBay and also get a Finnish keyboard for it from Lenovo FRU sales. As the Gobi module in use was originally sold in Finland, it is not operator-locked. This may simplify debugging a bit.

I guess I forgot to mention that the 3G needs gobi-loader installed. I previously had installed the gobi-loader-tp version from__[]("https://launchpad.net/%7Elinrunner/+archive/ppa") [https://launchpad.net/~linrunner/+archive/thinkpad-extras](https://launchpad.net/~linrunner/+archive/thinkpad-extras) , but for testing I now installed the plain version from Natty repos, and it seems to work also. If this is only a lucky shot, I can always go back to the -tp version.

---

### Post by ubunaut on 2011-10-04
Installed fine off USB with daily 11.10 cd image. The open source video driver has been working ok, except that OpenGL for things like CairoDock is very slow. 
So I enabled proprietary video card driver through Additional Drivers, and now the system will no longer fully boot.
It stops at a black screen with no text and a cursor.
In recovery mode, it says:
```
Loading Linux 3.0.0-12-generic ...
Loading initial ramdisk ...
error: no suitable mode found.
Booting however
```
Nothing else happens.

Is it better to install fglrx through command line, or maybe download directly from ATI?

---

### Post by usvi on 2011-10-04
> **ubunaut said:**
> Installed fine off USB with daily 11.10 cd image. The open source video driver has been working ok, except that OpenGL for things like CairoDock is very slow. 
So I enabled proprietary video card driver through Additional Drivers, and now the system will no longer fully boot.
It stops at a black screen with no text and a cursor.
In recovery mode, it says:
```
Loading Linux 3.0.0-12-generic ...
Loading initial ramdisk ...
error: no suitable mode found.
Booting however
```Nothing else happens.

Is it better to install fglrx through command line, or maybe download directly from ATI?
 
For my 11.04 I installed directly from ATI. I used the option to not install directly the drivers, but first generate distribution-specific .deb files and then install them from command line. Remember to use sudo to start the ATI installer. The installer may fail initially, you need to check logs about which programs the installer needs, then install them and try re-running. Repeat if necessary.

---

### Post by kelpdip on 2011-10-04
> **mr_raider said:**
> Since installing 11.04 x64 on my x120, I have had random freezes where the screen become unresponsive, the mouse does not move, and I have to power cycle the laptop to reboot. Ctrl-alt-del, ctrl-alt-backspace and ctral-alt-f1 don't work.

I found that these keys do not work even if the system is responsive. Any program / os misbehaviour requires a hard power off. Is this a x120 problem or a natty bug? In the dozens of times I have performed hard poweroff, the filesystem seems to be fine, so ext4 is apparently a step up from the old days of rebuilding the journal from scratch.

It still feels wrong to kill power for something as simple as a minor shell glitch.

---

### Post by kelpdip on 2011-10-06
Well, the ctrl-alt-backspace bug was just a bad default setting in 11.04. Settings/keyboard/layout/restart xserver key was unchecked.
Installing 11.10 beta seems to have fixed the random freezes anyway. 11.10 beta is far more usable than 11.04 because of this.

---

### Post by tista on 2011-10-07
> **kelpdip said:**
> Well, the ctrl-alt-backspace bug was just a bad default setting in 11.04. Settings/keyboard/layout/restart xserver key was unchecked.
Installing 11.10 beta seems to have fixed the random freezes anyway. 11.10 beta is far more usable than 11.04 because of this.

@kelpdip,

No... C-A-BS is NOT recommended today... :/
This had been discussed for a long time, and today ubuntu didn't apply it as default. so I could never say that "bad default"... killall Xorg is now "old-fashion" behavior in case you had employed any display-manager with graphical session.

User should not killall Xorg directly but user should call the signal to restart display-manager as pressing C-A-Del on ubuntu.

---

### Post by kelpdip on 2011-10-08
If the display manager is misbehaving, ctrl-alt-bkspc can't be worse than hard poweroff, which is what I've been using up until now. Although, the filesystem seems to have survived dozens of hard poweroffs so far, which does increase my confidence in the modern linux fs. I assume the lack of negative effects is part of the reason they disabled the bkspc interrupt in the last version.

---

### Post by VCSkier on 2011-10-13
Is there any indication as to when the regression that caused the current fglrx driver to break for us will be resolved? It seems weird to me that it would be broken for this long on a relatively new graphics chipset.

---

### Post by Corgan on 2011-10-13
I've done three fresh installs of 11.10 on my new X120e running an E-350 with the Radeon HD6310. Things I've found:

- Wireless has, so far, worked well.
- Webcam works
- Pointer works

My major problem lays in the graphics handling. Native resolution on the device is fine, and the open source driver does well enough to extend the display. It does NOT, however, allow disabling of the laptop display and using the HDMI out display only. Both displays go blank for me, before reverting back to old settings.

In trying to install the 3rd party drivers via the "Additional Drivers" dialogue, the following happens upon reboot:

- external displays cannot be detected
- Gnome-Shell becomes corrupt (glitched colors, no screenshot, sorry)

In trying to remove the driver via the "Additional Drivers" window, gnome-shell no longer works, reverting to the fallback environment.

Installing from the driver provided by ATI on their website, also fails to properly install. The utilities cannot be found using the default installation.

I would have collected the errors, but with reinstallations and needing a working machine TONIGHT, it was a bother to keep track of.

---

### Post by VCSkier on 2011-10-15
For whatever reason, the most recent releases of the fglrx driver have not been working on the x120e. Tista recommend that we use the 8.850/11.5 release. I've been using it for a while now, with no real problems. It's available in the X Updates ppa.

Edit: I guess I should mention I'm still on Natty, for now. I assume the graphics situation would be at least as good on Oneiric, assuming the same driver version was being used. I'll be upgrading soon, when I have some free time.

---

### Post by jankyHellface on 2011-10-17
Please keep us updated on your experiences with gnome-shell, 11.10 and the x120e (what works, what doesn't, etc). I don't have time to check it out right now (and need a fully functional laptop), but when I do switch it would be great to know everyone's experiences and tips

---

### Post by VCSkier on 2011-10-17
I tried to do a fresh install of 11.10 today, and I ran into a couple problems. The first was a new set of efi related issues. I got it resolved and booting, but I had to manually create a FAT partition, and mount it at /boot/efi.

Now on to the issue I haven't resolved. I want to be using the fglrx driver (unfortunately), but can't seem to get it installed and working properly. First, I tried using the x-updates ppa like I had on Natty, because it has version 8.850/11.5, the version I have working well on Natty. When I tried to install it on Oneiric though, apt wanted to remove a ton of core packages, including unity and xorg - obviously not an option. After some poking around, it seems that there is an libglx related package that is reporting that it breaks fglrx 8.850, the version I was trying to install.

I thought maybe if I used the 11.6 release then, I would be okay, because it too was working on the x120e. Unfortunately, I couldn't find an Oneiric build of Catalyst 11.6, so I tried to build it myself, something I had never attempted before. Needless to say, it didn't work, and I broke something in the process. :( Obviously it was because of my own ignorance, but now Unity won't load, in 2D or 3D, and I'm rather stuck.

Can anyone point me to an Oneiric build of 8.861/11.6, or perhaps help me figure out how to install 8.850/11.5 without removing everything else? Thanks so much!

---

### Post by VCSkier on 2011-10-18
I've got an update. After googling around and following various user's suggestions, I have a working Unity desktop again. It does not appear to be accelerated though. Listed in "System Info," my graphics driver is shown as "VESA: WRESTLER."

I used the .run file and the script from ati to build the .deb binaries for fglrx 8.861, and it seemed to install fine (with no error codes). So why then, am I still using a vesa driver? Any ideas?

---

### Post by tista on 2011-10-19
> **VCSkier said:**
> I've got an update. After googling around and following various user's suggestions, I have a working Unity desktop again. It does not appear to be accelerated though. Listed in "System Info," my graphics driver is shown as "VESA: WRESTLER."

I used the .run file and the script from ati to build the .deb binaries for fglrx 8.861, and it seemed to install fine (with no error codes). So why then, am I still using a vesa driver? Any ideas?

Hi VCSkier,

been a while... ;)

Now I'm moving on with precise! lol
And Yeah "VESA: WRESTLER." on fglrx would be normal. because such proprietary driver didn't provide much of informations to system. Usually this "name" were given from Mesa/OpenGL renderer name instead of 2D drivers name. ;) So our HD6310 with radeon/gallium would show the name as "AMD PALM", and fglrx would do as "VESA: WRESTLER". And unfortunately sometimes such closed source drivers name might be slightly different from the output of glxinfo, but don't worry about it. it's normal as well...

Finally Catalyst is the worst complicated driver package on Ubuntu!! :/ Yep, it's so hard to contribute. So you're right to make own packages from the AMD sources, I think. Today this packaging script would work fine so far on Oneiric, but don't forget about that you would be ugly whenever you want to purge fglrx from system completely. :sad: Because uninstallation script didn't implement all of installed stuffs and alternatives.

cheers.

---

### Post by JebusWankel on 2011-10-19
Has anyone figured out how to use gpu acceleration with Flash? I'm on 
Flash 11.0.1.152-0oneiric1
fglrx-updates 2:8.881-0ubuntu6
xvba-video 0.8.0-1
Chrome 14.0.835.202

I've gotten vaapi working with vlc and hardware acceleration selected in flash settings, yet high def youtube videos are a slideshow and full screen standard def flash videos are a little rough.

My performance is probably not as good since I've the single core e-240 processor, but I at least want flash to play as smoothly as vlc does.

---

### Post by VCSkier on 2011-10-20
Correct me if I'm wrong, but I don't think Adobe Flash supports supports XvBA or VA-API. Therefore, I don't think any hardware graphics acceleration is possible with Adobe Flash on an ATI or Intel gpu.

Gnash and Lightspark I think can do VA-API acceleration. Alternatively, you can use a Firefox extension like FlashVideoReplacer to replace youtube flash videos with standards-friendly plugin, like gecko-mediaplayer, which supports VA-API acceleration.

Hope that helps!

---

### Post by VCSkier on 2011-10-20
@JebusWankel

I didn't notice when I first posted, but are you correct in saying that you're using fglrx 8.881? Did you install that from the repositories? Did you have to do anything additional to get it working? I thought we had to be using an older release of fglrx with the AMD 6310.

I installed 8.861 from ATI, but I'm still not sure it's installed right. when I run vainfo, this is the output:
```
reed@Oneiric-ThinkPad-X120e:~$ vainfo
libva: libva version 0.32.0
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
libva: va_getDriverName() returns 0
libva: Trying to open /usr/lib/dri/fglrx_drv_video.so
libva error: /usr/lib/dri/fglrx_drv_video.so init failed
libva: va_openDriver() returns -1
vaInitialize failed with error code -1 (unknown libva error),exit

```

Is that normal?

---

### Post by JebusWankel on 2011-10-20
I had no problem installing the fglrx-update except that I couldn't install it through jockey, so I installed it through synaptic. I uninstalled fglrx first, if that helps.

Is there more to installing lightspark or gnash than installing them with synaptic? Firefox and Chrome seem to both still be using adobe.

```
$ vainfo
libva: libva version 0.32.0
libva: User requested driver 'xvba'
libva: Trying to open /usr/lib/va/drivers/xvba_drv_video.so
libva: va_openDriver() returns 0
vainfo: VA API version: 0.32
vainfo: Driver version: Splitted-Desktop Systems XvBA backend for VA-API - 0.8.0
vainfo: Supported profile and entrypoints
      VAProfileH264High               :	VAEntrypointVLD
      VAProfileVC1Advanced            :	VAEntrypointVLD

```
For the record, I wrote the Oneiric section of the [x120e wiki page]("https://help.ubuntu.com/community/X120e#A11.10_Oneiric_Ocelot")

---

### Post by VCSkier on 2011-10-20
I don't have gnash or lightspark running on my system right now, though I did have gnash going for a little while. At the time it seemed too unstable for my purposes (it's a shared computer), but maybe it's improved.

If I recall though, I had to fully remove Adobe Flash first, including any libflashplayer.so files that got copied around during install. Something like this would probably work...
```
sudo rm -f /usr/lib/mozilla/plugins/libflashplayer.so
sudo rm -f /usr/lib/firefox-addons/plugins/libflashplayer.so
```

Your vainfo output is interesting. It looks very different from mine. When I have some free time, maybe this weekend, I think I'll try to install fglrx 2.881. First though, I'll have to find out how to remove all the mess I made trying to install 8.861...

If that doesn't work, I may just go ahead and try the Gallium3D driver. VA-API acceleration and improved battery life were really the only reasons I wanted fglrx anyway.

---

### Post by JebusWankel on 2011-10-20
Nevermind, just had to uninstall flash to get lightspark working. It seems like it's not quite there yet.

---

### Post by VCSkier on 2011-10-25
Is there a way to reset update-alternatives? I messed around a bit with that command trying to get fglrx 8.861 to work, and now after uninstalling it, I can't get back to a working X environment. :/

---

### Post by VCSkier on 2011-10-31
@JebusWankel

I still can't get va-api working on Oneiric. I installed xvba-video 0.8.0-1 from splitted-desktop, and I have fglrx 8.881 installed and working. Still, my vainfo looks like this:
```
$ vainfo
libva: VA-API version 0.32.0
Xlib:  extension "XFree86-DRI" missing on display ":0".
libva: va_getDriverName() returns 0
libva: Trying to open /usr/lib/dri/fglrx_drv_video.so
libva: va_openDriver() returns -1
vaInitialize failed with error code -1 (unknown libva error),exit

```
Do I need to manually set it to look for the xvba driver, or something?

---

### Post by JebusWankel on 2011-11-01
@VCSkier: Try step 2 from here: [http://forum.xbmc.org/showthread.php?t=99154](http://forum.xbmc.org/showthread.php?t=99154)

In lieu of flash video acceleration, it seems I can stream youtube videos with VLC. Sometimes VLC doesn't request the right format of video (only .mp4's can be accelerated with VAAPI), so I can force the correct video format to be downloaded with [youtube-dl]("apt:youtube-dl"). [get-flash-videos]("apt:get-flash-videos") might prove fruitful too.

---

### Post by VCSkier on 2011-11-03
Thanks. It looks like that helped. I seem to be getting closer, but not quite there yet...
```
vainfo 
libva: VA-API version 0.32.0
libva: User requested driver 'xvba'
libva: Trying to open /usr/lib/va/drivers/xvba_drv_video.so
libva: va_openDriver() returns 0
vainfo: VA-API version: 0.32 (libva 1.0.15)
vainfo: Driver version: Splitted-Desktop Systems XvBA backend for VA-API - 0.8.0
vainfo: Supported profile and entrypoints
      VAProfileH264High               :	VAEntrypointVLD
      VAProfileVC1Advanced            :	VAEntrypointVLD
```
All that looks good, to me at least, but Gnome MPlayer still won't play video when I set output to "vaapi" in the preferences - it will play sound, but no video. Any thoughts?

---

### Post by usvi on 2011-11-11
> **usvi said:**
> Hello,

I have been now running Kubuntu 11.04 in my X120e E-350 with 8 gigs of RAM and 3G modem. I have to say that I'm impressed.

I earlier had lock-ups, but I think that blacklisting  rtl8192ce module has done the trick for me. I have not had any lock-ups since. Now I'm using r8192ce_pci for WLAN. I'm also using ATI's proprietary driver package 11.8 and pcie_aspm=force kernel option. For sound this module option was needed in /etc/modprobe.d/alsa-base.conf: options snd-hda-intel index=1

Even the 3G works fine (of course I had to extract the binaries from Windows installation); knetwork-manager is very fast to connect; this is unbelievable considering how poorly it was performing in 10.04. I'm now really looking forward into seeing how good 12.04 LTS will be.

A couple of problems I have noticed. Every now and then it seems that the cpu somehow "bursts". This is noticeable by the keyboard inputting about 10 additional characters. Also when listening to music the music occasionally skips. I think the issues are related. I haven't updated in a while though.

The 3G, while being extremely fast to connect, disconnects the devices internally:

```

[36216.214364] usb 1-5: USB disconnect, address 22
[36216.214920] qcserial ttyUSB0: Qualcomm USB modem converter now disconnected from ttyUSB0
[36216.214978] qcserial 1-5:1.1: device disconnected
[36216.215379] qcserial ttyUSB1: Qualcomm USB modem converter now disconnected from ttyUSB1
[36216.215412] qcserial 1-5:1.2: device disconnected
[36216.215676] qcserial ttyUSB2: Qualcomm USB modem converter now disconnected from ttyUSB2
[36216.215737] qcserial 1-5:1.3: device disconnected
[36216.690167] usb 1-5: new high speed USB device using ehci_hcd and address 23
[36216.842954] usb 1-5: config 1 has an invalid interface number: 1 but max is 0
[36216.842969] usb 1-5: config 1 has no interface number 0
[36216.850481] qcserial 1-5:1.1: Qualcomm USB modem converter detected
[36216.850848] usb 1-5: Qualcomm USB modem converter now attached to ttyUSB0
[36220.204646] usb 1-5: USB disconnect, address 23
[36220.220666] qcserial ttyUSB0: Qualcomm USB modem converter now disconnected from ttyUSB0
[36220.220730] qcserial 1-5:1.1: device disconnected
[36221.910144] usb 1-5: new high speed USB device using ehci_hcd and address 24
[36222.068575] qcserial 1-5:1.1: Qualcomm USB modem converter detected
[36222.068988] usb 1-5: Qualcomm USB modem converter now attached to ttyUSB0
[36222.070465] qcserial 1-5:1.2: Qualcomm USB modem converter detected
[36222.070783] usb 1-5: Qualcomm USB modem converter now attached to ttyUSB1
[36222.071904] qcserial 1-5:1.3: Qualcomm USB modem converter detected
[36222.072282] usb 1-5: Qualcomm USB modem converter now attached to ttyUSB2
[37695.060428] usb 1-5: USB disconnect, address 24
[37695.060992] qcserial ttyUSB0: Qualcomm USB modem converter now disconnected from ttyUSB0
[37695.061049] qcserial 1-5:1.1: device disconnected
[37695.061450] qcserial ttyUSB1: Qualcomm USB modem converter now disconnected from ttyUSB1
[37695.061481] qcserial 1-5:1.2: device disconnected
[37695.061739] qcserial ttyUSB2: Qualcomm USB modem converter now disconnected from ttyUSB2
[37695.061786] qcserial 1-5:1.3: device disconnected
[37695.380154] usb 1-5: new high speed USB device using ehci_hcd and address 25
[37695.532833] usb 1-5: config 1 has an invalid interface number: 1 but max is 0
[37695.532848] usb 1-5: config 1 has no interface number 0
[37695.539406] qcserial 1-5:1.1: Qualcomm USB modem converter detected
[37695.539718] usb 1-5: Qualcomm USB modem converter now attached to ttyUSB0
[37699.014566] usb 1-5: USB disconnect, address 25
[37699.030564] qcserial ttyUSB0: Qualcomm USB modem converter now disconnected from ttyUSB0
[37699.030624] qcserial 1-5:1.1: device disconnected
[37699.950300] usb 1-5: new high speed USB device using ehci_hcd and address 26
[37700.108205] qcserial 1-5:1.1: Qualcomm USB modem converter detected
[37700.108528] usb 1-5: Qualcomm USB modem converter now attached to ttyUSB0
[37700.110487] qcserial 1-5:1.2: Qualcomm USB modem converter detected
[37700.110854] usb 1-5: Qualcomm USB modem converter now attached to ttyUSB1
[37700.113095] qcserial 1-5:1.3: Qualcomm USB modem converter detected
[37700.113462] usb 1-5: Qualcomm USB modem converter now attached to ttyUSB2
[38622.796088] usb 1-5: USB disconnect, address 26

```

---

### Post by usvi on 2011-11-11
About bursting, this seems to happen with every burst:

```

[41089.001941] atkbd serio0: Unknown key pressed (translated set 2, code 0xf1 on isa0060/serio0).
[41089.001956] atkbd serio0: Use 'setkeycodes e071 <keycode>' to make it known.
[41089.012511] atkbd serio0: Unknown key released (translated set 2, code 0xf1 on isa0060/serio0).
[41089.012525] atkbd serio0: Use 'setkeycodes e071 <keycode>' to make it known.
[41089.492011] thinkpad_acpi: THERMAL ALERT: unknown thermal alarm received
[41089.495476] thinkpad_acpi: temperatures (Celsius): 58 0 58 0 0 0 30 0
[41089.495504] thinkpad_acpi: unhandled HKEY event 0x6040
[41089.495512] thinkpad_acpi: please report the conditions when this event happened to ibm-acpi-devel at lists.sourceforge.net
[41091.148860] EXT4-fs (dm-0): re-mounted. Opts: errors=remount-ro,commit=0
[41091.155906] EXT4-fs (sda5): re-mounted. Opts: commit=0

```

---

### Post by JebusWankel on 2011-11-11
dunno what to tell you VCSkier. I broke my vaapi with the last update to fglrx-updates. I decided to try the xvba-video-driver package from the repos (which required removing the splitted-desktop version, and constituted a downgrade). Unfortunately that forced me to switch back from fglrx-updates to fglrx, and I still don't have vaapi. Looks like I'll have to downgrade to the previous version of fglrx-updates and upgrade back xvba.

---

### Post by kmakaron on 2011-11-12
Hello there.
Can someone else test this situation on x120e.
When turn-on the laptop press F1 to enter BIOS setup. Then toggle one of the options,...say AMD-V. Save and Exit the changes, and then boot directly into Ubuntu. 
I have problem with booting Linux hanging on the message "Booting the kernel...". It happens when either when I enter the BIOS setup, or Reboot into Linux after Windows7. In order to boot Linux, I have to it turn-off. I will be grateful if someone confirm this issue. I am with BIOS version 1.13.

---

### Post by VCSkier on 2011-11-14
> **JebusWankel said:**
> dunno what to tell you VCSkier. I broke my vaapi with the last update to fglrx-updates. I decided to try the xvba-video-driver package from the repos (which required removing the splitted-desktop version, and constituted a downgrade). Unfortunately that forced me to switch back from fglrx-updates to fglrx, and I still don't have vaapi. Looks like I'll have to downgrade to the previous version of fglrx-updates and upgrade back xvba.

So, if you don't mind, what version of fglrx-updates are you using? If I understand correctly, you have it working using xvba-video 0.8.0-1 (from splitted-desktop), not xvba-va-driver 0.7.8-1ubuntu1 (from the Ubuntu repository). Is that correct?

---

### Post by usvi on 2011-11-16
> **kmakaron said:**
> Hello there.
Can someone else test this situation on x120e.
When turn-on the laptop press F1 to enter BIOS setup. Then toggle one of the options,...say AMD-V. Save and Exit the changes, and then boot directly into Ubuntu. 
I have problem with booting Linux hanging on the message "Booting the kernel...". It happens when either when I enter the BIOS setup, or Reboot into Linux after Windows7. In order to boot Linux, I have to it turn-off. I will be grateful if someone confirm this issue. I am with BIOS version 1.13.

Yeah, I remember I have hanging if I first boot to Windows 7, then in reboot try to boot Ubuntu. I need to use the power button to switch it off and back on. Then I am able to boot Linux. Don't remember the exact hang phase, but it indeed might be the "Booting the kernel...". This happens always when I try to boot Ubuntu after Windows.

---

### Post by JebusWankel on 2011-11-17
@VCSkier, I don't even know anymore. When I had vaapi working, I was definitely using the splitted-desktop package. I think the fglrx-updates package was at the same version as fgrlx, so I tried to install that. No matter what I do, I get the same results from vainfo now:
> $ vainfo
libva: libva version 0.32.0
libva: User requested driver 'xvba'
libva: Trying to open /usr/lib/va/drivers/xvba_drv_video.so
libva error: /usr/lib/va/drivers/xvba_drv_video.so init failed
libva: va_openDriver() returns -1
vaInitialize failed with error code -1 (unknown libva error),exit


Been researching related bugs,
[https://bugs.launchpad.net/ubuntu/+source/xvba-video](https://bugs.launchpad.net/ubuntu/+source/xvba-video)
[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer-updates](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer-updates)
but I haven't figured anything out.

Maybe it's a permissions problem. What are the permissions of your /usr/lib/va/drivers/xvba_drv_video.so?

---

### Post by VCSkier on 2011-11-18
Interesting. My vainfo output isn't showing any error codes, like your is.```
$ vainfo
libva: VA-API version 0.32.0
libva: User requested driver 'xvba'
libva: Trying to open /usr/lib/va/drivers/xvba_drv_video.so
libva: va_openDriver() returns 0
vainfo: VA-API version: 0.32 (libva 1.0.15)
vainfo: Driver version: Splitted-Desktop Systems XvBA backend for VA-API - 0.8.0
vainfo: Supported profile and entrypoints
      VAProfileH264High               :	VAEntrypointVLD
      VAProfileVC1Advanced            :	VAEntrypointVLD
```

Here are the permissions on the xvba file...```
$ ls -l /usr/lib/va/drivers/xvba_drv_video.so
-rw-r--r-- 1 root root 120016 2011-06-14 07:08 /usr/lib/va/drivers/xvba_drv_video.so
```

---

### Post by JebusWankel on 2011-11-26
So it's not a permissions issue...

Here's my output from 

```
$ fglrxinfo
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  139 (ATIFGLEXTENSION)
  Minor opcode of failed request:  66 ()
  Serial number of failed request:  13
  Current serial number in output stream:  13

```

I posted a question to the libva mailing list, we'll see what happens.

---

### Post by T64 on 2011-11-28
Hey,
for 2 weeks now I am the owner of a cool Thinkpad x121e with an AMD E-450 CPU. I am using Ubuntu 11.10 64-bit and just tried to read through this thread and understand everything, but now I am really confused:

Can someone summarize for me, what driver I should use for 1. graphics and 2. WLAN to get the best performance? And did someone managed it to get hibernate and hdaps working with these drivers?

I would be really happy if someone could help me :-)
Tim

---

### Post by steve7777777 on 2011-11-30
> **T64 said:**
> Hey,
for 2 weeks now I am the owner of a cool Thinkpad x121e with an AMD E-450 CPU. I am using Ubuntu 11.10 64-bit and just tried to read through this thread and understand everything, but now I am really confused:

Can someone summarize for me, what driver I should use for 1. graphics and 2. WLAN to get the best performance? And did someone managed it to get hibernate and hdaps working with these drivers?

I would be really happy if someone could help me :-)
Tim

Have you seen this?

[https://help.ubuntu.com/community/X120e](https://help.ubuntu.com/community/X120e)

May be for the E-350, but I think it should work.

---

### Post by T64 on 2011-12-03
Yeah, I have seen this page, but they recommend the fglrx driver and I'm not sure if this is really the fastest option. And the solution of Ubuntu 11.04 to get hibernate working also doesn't work.
However, thanks for the tip.
Tim

---

### Post by joexner on 2011-12-04
Has anyone had any success flashing a non-whitelisted BIOS from Linux? I want to install a new wireless card. I found a non-whitelisted BIOS, but it just has the image, not a bootable installer.

---

### Post by T64 on 2011-12-08
I really don't know if it will work, but did you try the [UltimateBootCD]("http://www.ultimatebootcd.com/download.html")? But please google it before, so that you don't break your bios...

---

### Post by JebusWankel on 2011-12-14
Dunno what you mean by a non-whitelisted BIOS, but I updated the BIOS from the Lenovo support site iso. I used my new favorite method to create a bootable usb stick: I have a U3 flash drive and replaced the iso on it using the [u3-tool]("apt:u3-tool") package. It's the easiest way to make a bootable usb drive and it's also the most dependable I've found.

---

### Post by JebusWankel on 2011-12-14
For the record, I finally got va-api gpu video acceleration working again. I installed the latest drivers from the amd website, Catalyst 11.12, which just came out yesterday, and installed them using these instructions [http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide"), though I didn't really do anything special. Then I just installed the xvba-video package from splitted desktop. Didn't even have to add any sym-links anywhere.

---

### Post by T64 on 2011-12-15
I just installed the new fglrx 11.12 driver and it works quite well, but then I tried to install all the xvba and libva packages and ran into version number problems. So I edited all the version number of these packeges and build new .deb files and installed these. This works really good, because you can install every other pogramm without having problems, for example vlc.
But if I start VLC with GPU acceleration and open a video file it crashes with a segfault. Has anyone the same problem and found a solution for that?

Error in terminal:
> Blocked: call to setlocale(6, "")
Warning: call to rand()
Warning: call to rand()
Warning: call to rand()
Warning: call to rand()
Warning: call to rand()
[0xe7b2f0] qt4 interface warning: Input option: file-caching=300
[0x12c3bd0] mp4 stream warning: unknown box type iods (incompletely loaded)
[0x12c3bd0] mp4 stream warning: unknown box type btrt (incompletely loaded)
[0x12c3bd0] mp4 stream warning: unknown box type gsst (incompletely loaded)
[0x12c3bd0] mp4 stream warning: unknown box type gstd (incompletely loaded)
[0x12c3bd0] mp4 stream warning: unknown box type gssd (incompletely loaded)
[0x12c3bd0] mp4 stream warning: unknown box type gspu (incompletely loaded)
[0x12c3bd0] mp4 stream warning: unknown box type gspm (incompletely loaded)
[0x12c3bd0] mp4 stream warning: unknown box type gshh (incompletely loaded)
[0x15ae110] mp4 demux warning: control query 14 unimplemented
[0x12cbdf0] faad decoder warning: decoded zero sample
libva: libva version 0.32.0-sds2
Xlib:  extension "XFree86-DRI" missing on display ":0".
libva: va_getDriverName() returns 0
Speicherzugriffsfehler  # <- Segfault

---

### Post by joexner on 2011-12-16
> **JebusWankel said:**
> Dunno what you mean by a non-whitelisted BIOS, but I updated the BIOS from the Lenovo support site iso. I used my new favorite method to create a bootable usb stick: I have a U3 flash drive and replaced the iso on it using the [u3-tool]("apt:u3-tool") package. It's the easiest way to make a bootable usb drive and it's also the most dependable I've found.

Basically, I bought an Intel 5100 wireless PCI-E card and want to use it in my X120e. The Lenovo BIOS checks every add-on card in the system against a "whitelist" of Lenovo-approved hardware, and refuses to boot if you've attached a card that's not on the list.

There is no legal barrier to removing the whitelist from your computer's BIOS, but it is kind of a pain in the butt to do so. There are Internet forums that specialize in meeting people's requests in this area: [https://encrypted.google.com/search?q=x120e+bios+whitelist](https://encrypted.google.com/search?q=x120e+bios+whitelist)

However, the couple of de-whitelisted BIOS'es that I've found for the x120e use Windows tools to flash the BIOS, instead of the usual bootable CD/USB stick image. I've had this on the back burner for a while, but I wondered if anyone else had any tips for when I get back around to it.

---

### Post by Ibidem on 2011-12-26
> **joexner said:**
> Basically, I bought an Intel 5100 wireless PCI-E card and want to use it in my X120e. The Lenovo BIOS checks every add-on card in the system against a "whitelist" of Lenovo-approved hardware, and refuses to boot if you've attached a card that's not on the list.

There is no legal barrier to removing the whitelist from your computer's BIOS, but it is kind of a pain in the butt to do so. There are Internet forums that specialize in meeting people's requests in this area: [https://encrypted.google.com/search?q=x120e+bios+whitelist](https://encrypted.google.com/search?q=x120e+bios+whitelist)

However, the couple of de-whitelisted BIOS'es that I've found for the x120e use Windows tools to flash the BIOS, instead of the usual bootable CD/USB stick image. I've had this on the back burner for a while, but I wondered if anyone else had any tips for when I get back around to it.
[http://www.thinkwiki.org/wiki/How_to_change_the_BIOS_bootsplash_screen](http://www.thinkwiki.org/wiki/How_to_change_the_BIOS_bootsplash_screen)
was where I started. 
Basically, I extract the hard drive image from a "bootable update cd", mount the FAT partition, copy the flashing tools +bios to a freedos bootable drive/image & replace what needs replacing (you could just boot the hard drive image from the HDD, if you can look that up...), and flash.

---

### Post by T64 on 2012-01-07
@JebusWankel: What libva version did you use to get va-api working? The new one from splitted desktop or just the original from ubuntu?

---

### Post by JebusWankel on 2012-01-23
I used the version of libva in the ubuntu repos

---

### Post by cleon62395 on 2012-01-25
i have had z61t(9443) no problems with this computer until i installed ubuntu 10.10 does anyone know a way to fix the audio problem or any drivers i can download thanks

---

### Post by kelpdip on 2012-04-13
The 12.04 beta now seems to be at a point where the default install is more stable than 11.04/11.10, if anyone is interested in upgrading. It is beta of course, but it has become significantly smoother over the past couple months, with all drivers working - proprietary and free - and suspend working reliably.

To those coming from 10.04, gnome has been simplified to the point that it is no longer ideal for laptops, but kde seems to have increased in stability and speed to the point it that kubuntu is a good choice for the x120.

---

### Post by kajukatri on 2012-04-14
Another X120e user here.  been trying to get working compiz-fusion on 11.10. but so far no luck. 
i have installed the latest 12.3 fglrx. and fglrx command shows correct version of Ati. and fglrx gears work perfectly.
Basically i want to have Classic Gnome with compiz effect. no metacity. and for that i have installed gnome fallback and removed unity completely. 
but replacing compiz --replace crash my all window and not able to close them. 
Looks like i have to try 10.10 then. Any idea on above ?

---

### Post by wnelson on 2012-04-14
I have a ideapad b575. I have had the very best with 12.04 it support more recent hardware.

Walt

---

### Post by kolinab on 2012-04-17
> **kelpdip said:**
> The 12.04 beta now seems to be at a point where the default install is more stable than 11.04/11.10, if anyone is interested in upgrading. It is beta of course, but it has become significantly smoother over the past couple months, with all drivers working - proprietary and free - and suspend working reliably.

To those coming from 10.04, gnome has been simplified to the point that it is no longer ideal for laptops, but kde seems to have increased in stability and speed to the point it that kubuntu is a good choice for the x120.
@kelpdip,

Thanks for that info. I have just caught up on this (long) thread and have been deciding whether to install fglrx from AMD on 11.10, or wait and see how things are with 12.04. I am using the fglrx from 'Additional Drivers' and am happy with everything EXCEPT resuming from suspend.

**On your 12.04 installation, are you using proprietary driver from 'Additional Drivers' or straight from AMD?** I tried installing Precise Beta 2 a couple of weeks ago but the install halted on me multiple times in the same place (desktop and alternate) and I decided to wait for the final release. 

Thanks to everyone for your contributions to this thread!

For now I'm thinking of removing the 'additional drivers' fglrx from 11.10 and installing straight for AMD just to see how it goes . . . All this video acceleration talk is a step beyond me right now so I'll leave it all be for the time being.

---

### Post by kolinab on 2012-04-17
Tonight I finally figured out how to disable bluetooth on startup for my x120e. See the solution here, attributed to the arch wiki for the x120e:

[http://ubuntuforums.org/showthread.php?t=1924279](http://ubuntuforums.org/showthread.php?t=1924279)

---

### Post by hovrashko on 2012-07-12
I have a different problem with my x60. The USB ports sometimes turn itself off. Does anybody knows how to fix it? 

Thanks

---

### Post by joris1977 on 2012-10-15
I just bought an Intel Centrino Ultimate-N 6300 wireless card and plan to use it with my x120e. 

Anyone else using this card and have some tips?

Because I just noticed that I have to flash the bios with a hacked version to use this card and that seems a bit silly & I don't really like to use untrusted sources on my computers.... 

I didn't have any troubles with the default card (broadcom) but the reception is just not very good. I don't see many wireless routers in the air and have to be close to the router to able to connect. I was annoyed that my friend with a mac could connect to the wireless in a bar without any problem while I had to move around to get a connection. 

Hope the Intel 6300 fixes this. I am not using 3G so I have a extra free antenna in the x120e that I want to use.


Ok a follow up:  I flashed the bios with a hacked one to avoid the whitelist issues. After that I installed the new wifi card. An Intel Centrino Ultimate-N 6300. It has 3 antenna connectors instead of two on the original broadcom card, but I could easily use an extra antenna from the not used WWLAN.

Ubuntu detected the new card right away and the results are beyond my expactations.. I am not sure if this is because of the better open source drivers or because of the extra antenna. Probably a little bit of both,  but I can see at least 4 times more wireless networks and the reception is very good. A very good upgrade!

---

### Post by Mogen317 on 2012-10-27
As a heads up: using the fglrx drivers on 12.10 as of this time will disable the unity shell, leaving a blank desktop as the only gui.

Noted here: [https://bugs.launchpad.net/fglrx/+bug/1068661](https://bugs.launchpad.net/fglrx/+bug/1068661)

---

### Post by Mogen317 on 2012-10-27
installing the 12.11 catalyst beta driver worked for me:
[http://askubuntu.com/questions/206288/how-can-i-get-the-amd-driver-running-on-ubuntu-12-10-amd-radeon-hd-7310-amd-vi](http://askubuntu.com/questions/206288/how-can-i-get-the-amd-driver-running-on-ubuntu-12-10-amd-radeon-hd-7310-amd-vi)

---

### Post by faronium on 2012-11-21
I recently bought one of these used and installed the ubuntu gnome remix 12.10. I had used one for travel on loan from work and was really happy with it.  I then installed the beta AMD graphics drivers as described in the previous post. When I got home, I tried to plug it into my external monitor (1920 x 1080) and was given an error stating that the max supported resolution is 1920 x 1920. So, I have to choose between the laptop monitor or my external. Is that the best it can do? I thought these could easily handle dual monitors or at least drive the laptop and an external simultaneously.  Would the generic ubuntu driver do better? I seem to recall the loaner driving both displays with 11.10 installed and a generic graphics driver in the unity desktop.

I'm very poor at diagnosing graphics problems, but if anyone could lead the way, I would appreciate it, or suggest what diagnostics to post.

Thanks

---

