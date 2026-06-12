---
title: "Monitor EDID not recognised - native resolution not allowed"
date: 2012-03-24
forum: Hardware
---

### Post by GMeister on 2012-03-24
Hi all, any help out there??

First some details;

I have 64-bit Ubuntu 11.10 installed from a LiveCD and am having problems getting the resolution I know the hardware is capable of.

GFX card:
[I]$ lspci|grep VGA
01:00.0 VGA compatible controller: nVidia Corporation GF110 [GeForce GTX 580] (rev a1)[/I]

My monitor is an LG Flatron W2243S, which unfortunately doesn't seem to have a Linux driver.  I know it supports up to 1920x1080, but via the "Displays.." GUI I can only select 1024x768.

xrandr doesn't appear to recognise the EDID information for the monitor (and throws a strange error - google'd, but couldn't find the cause):
[I]$ xrandr
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 320 x 240, current 1024 x 768, maximum 1024 x 768
default connected 1024x768+0+0 0mm x 0mm
   1024x768       50.0* 
   800x600        51.0     52.0     53.0  
   680x384        54.0     55.0  
   640x480        56.0  
   512x384        57.0  
   400x300        58.0  
   320x240        59.0  [/I]

However I know that the EDID is there, from using parse-edid:
[I]$ sudo get-edid|parse-edid
parse-edid: parse-edid version 2.0.0
get-edid: get-edid version 2.0.0

	Performing real mode VBE call
	Interrupt 0x10 ax=0x4f00 bx=0x0 cx=0x0
	Function supported
	Call successful

	VBE version 300
	VBE string at 0x11100 "NVIDIA"

VBE/DDC service about to be called
	Report DDC capabilities

	Performing real mode VBE call
	Interrupt 0x10 ax=0x4f15 bx=0x0 cx=0x0
	Function supported
	Call successful

	Monitor and video card combination does not support DDC1 transfers
	Monitor and video card combination supports DDC2 transfers
	0 seconds per 128 byte EDID block transfer
	Screen is not blanked during DDC transfer

Reading next EDID block

VBE/DDC service about to be called
	Read EDID

	Performing real mode VBE call
	Interrupt 0x10 ax=0x4f15 bx=0x1 cx=0x0
	Function supported
	Call failed

The EDID data should not be trusted as the VBE call failed
parse-edid: EDID checksum failed - data is corrupt. Continuing anyway.
parse-edid: first bytes don't match EDID version 1 header
parse-edid: do not trust output (if any).

	# EDID version 1 revision 3
Section "Monitor"
	# Block type: 2:0 3:fd
	# Block type: 2:0 3:fc
	Identifier "W2243"
	VendorName "GSM"
	ModelName "W2243"
	# Block type: 2:0 3:fd
	HorizSync 30-83
	VertRefresh 56-75
	# Max dot clock (video bandwidth) 150 MHz
	# Block type: 2:0 3:fc
	# DPMS capabilities: Active off:yes  Suspend:yes  Standby:yes

	Mode 	"1920x1080"	# vfreq 59.934Hz, hfreq 66.587kHz
		DotClock	138.500000
		HTimings	1920 1968 2000 2080
		VTimings	1080 1082 1087 1111
		Flags	"-HSync" "+VSync"
	EndMode
	Mode 	"1920x1080"	# vfreq 60.000Hz, hfreq 67.500kHz
		DotClock	148.500000
		HTimings	1920 2008 2052 2200
		VTimings	1080 1084 1089 1125
		Flags	"+HSync" "+VSync"
	EndMode
	# Block type: 2:0 3:fd
	# Block type: 2:0 3:fc
EndSection[/I]

It seems that because of the "**Failed to get size of gamma for output default**" error, I can't force the resolution via "xrandr --newmode".

Any ideas?  I'm way beyond the extent of my Linux knowledge!!!
Thanks

---

### Post by GMeister on 2012-03-24
Also worth noting, that this is with a Sandy Bridge 2600k.  Wondering if the GFX controller has a part to play here?

00:02.0 Display controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)

---

### Post by GMeister on 2012-03-24
Yet more information!

Strangely I had to hack my way into Ubuntu via "nomodeset" - I suspect this is to do with an nVidia driver problem, and since then I've installed the nVidia driver.

[I]sudo Xorg -version

X.Org X Server 1.10.4
Release Date: 2011-08-19
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-29-server x86_64 Ubuntu
Current Operating System: Linux powerpc-Z68XP-UD3P 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:56:25 UTC 2011 x86_64
Kernel command line: BOOT_IMAGE=/vmlinuz-3.0.0-12-generic root=UUID=5bbc8290-d99e-4f61-b73a-74c9ce103023 ro quiet splash nomodeset vt.handoff=7
Build Date: 29 September 2011  02:45:13AM
xorg-server 2:1.10.4-1ubuntu4 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
Current version of pixman: 0.22.2
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.[/I]

---

### Post by GMeister on 2012-03-24
OK, so progress.  Seems the NVIDIA driver doesn't get the EDID info.
From /var/log/Xorg.0.log:
[I][     6.757] (WW) NVIDIA(GPU-0): The EDID read for display device CRT-0 is invalid:
[     6.757] (WW) NVIDIA(GPU-0):     unrecognized EDID Header.
[     6.759] (II) NVIDIA(0): NVIDIA GPU GeForce GTX 580 (GF110) at PCI:1:0:0 (GPU-0)
[     6.759] (--) NVIDIA(0): Memory: 1572864 kBytes
[     6.759] (--) NVIDIA(0): VideoBIOS: 70.10.49.00.03
[     6.759] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[     6.759] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[     6.759] (--) NVIDIA(0): Connected display device(s) on GeForce GTX 580 at PCI:1:0:0
[     6.759] (--) NVIDIA(0):     CRT-0
[     6.759] (--) NVIDIA(0): CRT-0: 400.0 MHz maximum pixel clock
[     6.808] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID has been
[     6.808] (**) NVIDIA(0):     enabled on all display devices.
[     6.809] (II) NVIDIA(0): Assigned Display Device: CRT-0
[     6.809] (==) NVIDIA(0): 
[     6.809] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[     6.809] (==) NVIDIA(0):     will be used as the requested mode.
[     6.809] (==) NVIDIA(0): 
[     6.809] (II) NVIDIA(0): Validated modes:
[     6.810] (II) NVIDIA(0):     "nvidia-auto-select"
[     6.810] (II) NVIDIA(0): Virtual screen size determined to be 1024 x 768
[     6.840] (WW) NVIDIA(0): Unable to get display device CRT-0's EDID; cannot compute DPI
[     6.840] (WW) NVIDIA(0):     from CRT-0's EDID.
[     6.840] (==) NVIDIA(0): DPI set to (75, 75); computed from built-in default[/I]

---

### Post by papibe on 2012-03-24
Hi GMeister. Welcome to the forums.

It looks that your display has a corrupt EDID. Since I was 'blessed' with a laptop with a similar problem, I've learned a few tricks that can help you. I can't promise you that they will work, but I would gladly help you as much as I can.

My first idea would be to try to use another input. Sometimes there are more chances of retrieving the EDID data from a DVI, or HDMI input. Check this [thread]("http://ubuntuforums.org/showthread.php?t=1936293&highlight=vga+dvi+hdmi") as a point of reference.

If that don't work, we need to get the correct EDID data.

There is a reasonable chance that other people had faced the same problem, and may be you can find in the web a downloadable fixed EDID file that we can 'hardcode' into xorg.conf

The last resort would be to try to fix it ourselves. I would gladly help you with that if it comes to it. This is an example of the work the would need to be done: [Create a new EDID]("http://ubuntuforums.org/showthread.php?t=1857772&highlight=edid").

I hope those references point you in the right direction, and tell us if you need more help with this.

Regards.

---

### Post by GMeister on 2012-03-25
Thanks Papibe!

I think you hit the nail on the head, but unfortunately I'm not at a solution just yet.  In fact, I was looking at the possible effects of different inputs - this monitor ships with an SVGA output, which I'm having to use an adaptor to plug into the DVI port.  Short of buying a new monitor, I'm not going to be able to switch that.

So, I spotted your useful tip on (dare I say it) using my Windows OS to get hold of the EDID file.  Phoenix EDID Designer, installed and used.

Interestingly there are two EDIDs on there:

IV46BA is an Iiyama EDID:
```
0x   00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F
    ------------------------------------------------
00 | 00 FF FF FF FF FF FF 00 26 CD BA 46 4C B6 00 00
10 | 07 0E 01 03 68 22 1B 78 EA 04 A5 A3 58 4F 95 24
20 | 19 50 54 BF EF 00 81 80 71 4F 01 01 01 01 01 01
30 | 01 01 01 01 01 01 30 2A 00 98 51 00 2A 40 30 70
40 | 13 00 52 0E 11 00 00 1E 00 00 00 FF 00 31 30 30
50 | 32 36 33 30 30 34 36 36 36 38 00 00 00 FD 00 32
60 | 4B 1E 53 0E 00 0A 20 20 20 20 20 20 00 00 00 FC
70 | 00 31 37 4A 4E 31 0A 20 20 20 20 20 20 20 00 AB
```
Which by my calculations (well, see [http://www.lammertbies.nl/comm/info/crc-calculation.html](http://www.lammertbies.nl/comm/info/crc-calculation.html)) has a correct CRC.

HSD899A appears to be just a generic one, but also no fail on CRC:
```
0x   00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F
    ------------------------------------------------
00 | 00 FF FF FF FF FF FF 00 22 64 9A 89 56 0B 00 00
10 | 18 10 01 03 6C 26 1E 78 2A FD 56 A5 53 4A 9D 24
20 | 14 4F 54 AD CF 00 81 80 01 01 01 01 01 01 01 01
30 | 01 01 01 01 01 01 30 2A 00 98 51 00 2A 40 30 70
40 | 13 00 78 2D 11 00 00 1E 00 00 00 FD 00 38 4B 1E
50 | 50 0E 00 0A 20 20 20 20 20 20 00 00 00 FC 00 48
60 | 55 31 39 36 44 0A 20 20 20 20 20 20 00 00 00 FF
70 | 00 36 32 34 47 41 33 46 43 41 32 39 30 32 00 B8
```

I'm going to try and force them in anyway and see how that goes.

---

### Post by GMeister on 2012-03-25
So, quick refresh on my C programming :) and now we have:

```
$ parse-edid HSD899A.bin 
parse-edid: parse-edid version 2.0.0
parse-edid: EDID checksum passed.

	# EDID version 1 revision 3
Section "Monitor"
	# Block type: 2:0 3:fd
	# Block type: 2:0 3:fc
	Identifier "HU196D"
	VendorName "HSD"
	ModelName "HU196D"
	# Block type: 2:0 3:fd
	HorizSync 30-80
	VertRefresh 56-75
	# Max dot clock (video bandwidth) 140 MHz
	# Block type: 2:0 3:fc
	# Block type: 2:0 3:ff
	# DPMS capabilities: Active off:yes  Suspend:no  Standby:no

	Mode 	"1280x1024"	# vfreq 60.020Hz, hfreq 63.981kHz
		DotClock	108.000000
		HTimings	1280 1328 1440 1688
		VTimings	1024 1025 1028 1066
		Flags	"+HSync" "+VSync"
	EndMode
	# Block type: 2:0 3:fd
	# Block type: 2:0 3:fc
	# Block type: 2:0 3:ff
EndSection

```
and
```
$ parse-edid IVM46BA.bin 
parse-edid: parse-edid version 2.0.0
parse-edid: EDID checksum passed.

	# EDID version 1 revision 3
Section "Monitor"
	# Block type: 2:0 3:ff
	# Block type: 2:0 3:fd
	# Block type: 2:0 3:fc
	Identifier "17JN1"
	VendorName "IVM"
	ModelName "17JN1"
	# Block type: 2:0 3:ff
	# Block type: 2:0 3:fd
	HorizSync 30-83
	VertRefresh 50-75
	# Max dot clock (video bandwidth) 140 MHz
	# Block type: 2:0 3:fc
	# DPMS capabilities: Active off:yes  Suspend:yes  Standby:yes

	Mode 	"1280x1024"	# vfreq 60.020Hz, hfreq 63.981kHz
		DotClock	108.000000
		HTimings	1280 1328 1440 1688
		VTimings	1024 1025 1028 1066
		Flags	"+HSync" "+VSync"
	EndMode
	# Block type: 2:0 3:ff
	# Block type: 2:0 3:fd
	# Block type: 2:0 3:fc
EndSection
```

That's a bit weird, firstly because it seems to checksum fine, but secondly because the Modes aren't at all what I'm after.  I'll plug these into my Xorg.conf using your previous outline, then if I get 1280x1024 I'll be on my way to hacking the Hex for the modes I want ;)

---

### Post by GMeister on 2012-03-25
So there we are... 1280x1024 on the HSD899B.bin EDID.

I'm going to dig into the EDID wiki spec and hack it to support what I'm after then upload for the good of any LG Flatron W2243S users !!

Thanks Papibe for the links and work in solving the other similar issues - in the end it was your work with [creating new EDIDs]("http://ubuntuforums.org/showthread.php?t=1857772&highlight=edid") that really helped.

---

### Post by GMeister on 2012-03-25
OK - done.

Take your Modeline output from your favourite generator and goto:
[http://www.epanorama.net/faq/vga2rgb/calc.html](http://www.epanorama.net/faq/vga2rgb/calc.html)

There you can get your "front porch", "synch pulse" and other exciting parameters.

Then use the conversions outlined [here]("http://www.sevenforums.com/tutorials/7947-force-dvi-hdmi-resolutions-refresh-rates-4.html#post124522") to help edit your existing EDID via Phoenix EDID Developer.

Finally add the following to the "Screen" section of your Xorg.conf:
```
Option         "CustomEDID" "CRT-0:/etc/X11/HSD899A_test.bin"
```
where CRT-0 is the recognised output, and HSD899A_test.bin is your newly created EDID in binary format.

Hey presto!

I take no responsibility for the attached EDID and xorg.conf.

---

### Post by Asopiram on 2012-03-28
Not knowing all the technical stuff and how to write it into my xorg.conf file I found a way to fix my resolution issue that I was fighting with for quite some time.... 
I found the [SIZE="1"][COLOR="Red"]specs for my monitor online[/COLOR][/SIZE]... then with the horizontal and vertical refresh rates known I used a [COLOR="Red"]puppylinux live cd and used the xorg wizard[/COLOR] to set up my resolution (go all the way to the bottom of the selections and you will have the option to manually put in the refresh rates) , after seeing that it was good I [COLOR="Black"]copied the xorg.conf file that was created in Puppy and then pasted the monitor and screen sections into my Ubuntu xorg.conf file, rebooted and there it was the right resolution. [/COLOR]  I see that this thread was solved but I hope that this can help someone.

---

### Post by Jano1505 on 2012-06-02
[COLOR="Red"]Thanks GMeister[/COLOR] you saved my the trouble(and money) of buying a new monitor

---

### Post by psarak on 2012-12-14
i really want to say a VERY BIG thank you at GMeister! that problem is being troubling me the past 4 days. at first i thought it was an nvidia driver problem. but then i realised that the driver was working just fine. I got the exact same screen as you so when i googled the screen model your post came up! Again. THANKS A LOT mate!

---

