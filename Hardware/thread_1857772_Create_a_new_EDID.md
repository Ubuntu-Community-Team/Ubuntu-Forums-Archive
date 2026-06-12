---
title: "Create a new EDID"
date: 2011-10-11
forum: Hardware
---

### Post by dd_dentfull on 2011-10-11
I've got a laptop with a bad EDID, and it's apparently preventing me from using the nvidia graphics driver properly.
So I want to force a new EDID I will make myself, and apply it as per [this]("http://ubuntuforums.org/showthread.php?t=316985") guide.
Anyone knows how?

---

### Post by papibe on 2011-10-11
Been there, done that. Even with an Nvidia card.

I would gladly help you with that.. starting tomorrow,.. kind late for me now.

In the meantime, could you tell us a little bit more details?

Why do you say you have a bad EDID? resolution problems? black bars?
Which Nvidia card do you have?
What brand and model is your monitor? is it a laptop monitor? is a HDTV?
How far has you gone following that method?
Did you get the EDID.BIN?
Are you dual booting? if so, does Windows have the same problem?

I'll get back to you tomorrow.

Kind Regards.

---

### Post by dd_dentfull on 2011-10-11
Thanks for the prompt response.

> Which Nvidia card do you have?
What brand and model is your monitor? is it a laptop monitor? is a HDTV?
Are you dual booting? if so, does Windows have the same problem?


Said computer is an Acer Aspire 6930G with a 16 inch 1368x768 display and an Nvidia GeForce 9600M GT. I have a dual booting Windows 7 which is working flawlessly.

> Why do you say you have a bad EDID? resolution problems? black bars?
When I installed the nvidia-current drivers I would get a corrupt screen on startup and blank screen with the 173 driver.
I tried almost anything, short of writing a new graphics driver, to no avail.

Examining the x startup log I found these two lines:
```
(WW) NVIDIA(GPU-0): The EDID read for display device DFP-0 is invalid: the
(WW) NVIDIA(GPU-0): checksum for EDID version 1 is invalid.
```
This lead me to try various windows based EDID extraction utilities without any success. 
Finally I found [this utility]("http://linuxtoolkit.blogspot.com/2009/11/using-read-edid-to-extract-useful.html") which returned the following:
```
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
	Monitor and video card combination does not support DDC2 transfers
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
Error: output block unchanged

```
So in summary, I think I got a display with a bad EDID, and I either need someone with a similar laptop send me his, or make up a new one.

I attached the full startup log.

EDIT: Forget to mention I used to run ubuntu 7.04 a long time ago without any issues.

---

### Post by papibe on 2011-10-11
Hey dd_dentfull, and welcome to the forums!

I've created custom edids for an old P4 laptop with a Geforce 4 440 (corrupt resolution), and for my Sony TV (remove extra data to stop the dummy sound signal)

Regardless of keep looking for a edid.bin from a user with the same machine (this would be a start: [laptopvideo2go.com]("http://www.laptopvideo2go.com/")), let's try to get the EDID (even if corrupted) and maybe fix it.

BTW, having Windows 7 is a very good thing in this situation.

Since you are not able to get into the desktop while using the nvidia driver, let's try to get that information on Windows. Get 'Phoenix EDID Designer' (from [here]("http://www.tucows.com/preview/329441")). Install it, then query the EDID information of your monitor, and save it in a text file. It should look similar like this:
```
EDID BYTES:
0x   00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F
    ------------------------------------------------
00 | 00 FF FF FF FF FF FF 00 3A C4 00 04 00 00 00 00
10 | 2D 0C 01 03 80 20 18 00 EA A8 E0 99 57 4B 92 25
20 | 1C 50 54 00 00 00 01 01 01 01 01 01 01 01 01 01
30 | 01 01 01 01 01 01 48 3F 40 30 62 B0 32 40 4C C0
40 | 13 00 42 F3 10 00 00 1E 00 00 00 FC 00 4E 76 69
50 | 64 69 61 20 44 65 66 61 75 6C 00 00 00 FC 00 74
60 | 20 46 6C 61 74 20 50 61 6E 65 6C 00 00 00 00 FD
70 | 00 00 3C 1D 4C 11 00 00 20 20 20 20 20 00 00 9C
```
Please paste your results using the # tags (available when replying).

Regards.

---

### Post by dd_dentfull on 2011-10-11
Well you're quick.
Please observe the image.

 [IMG]http://i1129.photobucket.com/albums/m511/dd_dent/emptyedidlist.jpg[/IMG]

As you can see, there is no EDID to extract, and as expected pressing the extract button returns an error.
Everest also displays a similar behavior, and this issue led me to believe the EDID is bad.

Despite all of this, there is something similar in the xlog file.
I can't view it properly from windows, so I'll upload it after booting into Ubuntu within the next minutes.

EDIT: Voila!

```
[    22.391] (WW) NVIDIA(GPU-0): The EDID read for display device DFP-0 is invalid: the
[    22.391] (WW) NVIDIA(GPU-0): checksum for EDID version 1 is invalid.
[    22.391] (--) NVIDIA(GPU-0): 
[    22.391] (--) NVIDIA(GPU-0): Raw EDID bytes:
[    22.391] (--) NVIDIA(GPU-0): 
[    22.391] (--) NVIDIA(GPU-0):   00 ff ff ff ff ff ff 00  4c a3 4c 32 00 00 00 00
[    22.391] (--) NVIDIA(GPU-0):   00 12 01 03 80 23 14 78  0a 87 f5 94 57 4f 8c 27
[    22.391] (--) NVIDIA(GPU-0):   27 50 54 00 00 00 01 01  01 01 01 01 01 01 01 01
[    22.391] (--) NVIDIA(GPU-0):   01 01 01 01 01 01 41 1c  56 a0 50 00 16 30 30 20
[    22.391] (--) NVIDIA(GPU-0):   25 00 61 c6 10 00 00 19  00 00 00 0f 00 00 00 00
[    22.391] (--) NVIDIA(GPU-0):   00 00 00 00 00 1e b4 02  74 00 00 00 00 fe 00 53
[    22.391] (--) NVIDIA(GPU-0):   41 4d 53 55 4e 47 0a 20  20 20 20 20 00 00 00 fe
[    22.391] (--) NVIDIA(GPU-0):   00 31 36 30 41 54 30 31  2d 41 30 35 0a 20 00 e3
```

EDIT: Also thanks for the warm welcome, and the first link you provided seems to be dead (domain available for purchase)

---

### Post by papibe on 2011-10-11
Great!... working on it, be back in a few minutes.

BTW, the link seems to be working for me. I'm going to paste it again just in case:
```

main site  http://www.laptopvideo2go.com/
forums     http://forums.laptopvideo2go.com/
```
Regards.

---

### Post by papibe on 2011-10-11
I took that and I just left the data:
```
00 ff ff ff ff ff ff 00 4c a3 4c 32 00 00 00 00
00 12 01 03 80 23 14 78 0a 87 f5 94 57 4f 8c 27
27 50 54 00 00 00 01 01 01 01 01 01 01 01 01 01
01 01 01 01 01 01 41 1c 56 a0 50 00 16 30 30 20
25 00 61 c6 10 00 00 19 00 00 00 0f 00 00 00 00
00 00 00 00 00 1e b4 02 74 00 00 00 00 fe 00 53
41 4d 53 55 4e 47 0a 20 20 20 20 20 00 00 00 fe
00 31 36 30 41 54 30 31 2d 41 30 35 0a 20 00 e3

```
Then I created a binary version using this C program:
```
#include <stdio.h>

int main()
{
  while (!feof(stdin))
  {
    unsigned char i;
    scanf("%02X ", &i);
    printf("%c", i);
  }
  return 0;
}
```
This is what parse-edid dumps:
```
$ parse-edid edid.bin 
parse-edid: parse-edid version 2.0.0
parse-edid: EDID checksum failed - data is corrupt. Continuing anyway.

	# EDID version 1 revision 3
Section "Monitor"
	# Block type: 2:0 3:f
	# Block type: 2:0 3:fe
	# Block type: 2:0 3:fe
	Identifier "SEC:4c32"
	VendorName "SEC"
	ModelName "SEC:4c32"
	# Block type: 2:0 3:f
	# Block type: 2:0 3:fe
	# Block type: 2:0 3:fe
	# DPMS capabilities: Active off:no  Suspend:no  Standby:no

	Mode 	"1366x768"	# vfreq 59.998Hz, hfreq 47.398kHz
		DotClock	72.330000
		HTimings	1366 1414 1446 1526
		VTimings	768 770 775 790
		Flags	"-HSync" "-VSync"
	EndMode
	# Block type: 2:0 3:f
	# Block type: 2:0 3:fe
	# Block type: 2:0 3:fe
EndSection

```
Do you have any technical information about your monitor? It looks like your resolutions is read OK. I don't know about the timings. Maybe it is just a problem with the checksum.

Regards.

EDIT: we are missing the horizontal and vertical rates. It should be look like this:
```
	HorizSync 29-65
	VertRefresh 0-60

```

EDIT2: and the 'Max dot clock', for example:
```
	# Max dot clock (video bandwidth) 110 MHz
```

---

### Post by dd_dentfull on 2011-10-11
Manage to get this from the Nvidia control panel.
Also windows says that the refresh rate is 60hz.

---

### Post by dd_dentfull on 2011-10-11
Is there a way for me to calculate the values you need?

---

### Post by papibe on 2011-10-11
I think I have something for you. Here's the story:

[This link]("http://en.wikipedia.org/wiki/EDID") is the definition of the binary EDID format. I thought I was going to be able to hack it, but there's so many details that I dropped that idea.

I opened the binary file using the 'Hex Editor' (available on the Software Center), and to my surprise you could clearly read that the monitor was a SAMSUNG. 

I remembered that my laptop (Toshiba A665) had a similar resolution so I got my edid info, and what do you know, it was a Samsumg!

This is from my laptop's display:
```
	Mode 	"1366x768"	# vfreq 59.998Hz, hfreq 47.398kHz
		DotClock	72.330000
		HTimings	1366 1414 1446 1526
		VTimings	768 770 775 790
		Flags	"-HSync" "-VSync"
	EndMode
```
Looks familiar?

I wrote a couple of short C programs (similar to the previous one), to compare both edids. They have very little differences:
```

bytes         description
-------------------------
 10 -  11     product ID
 16 -  17     week and year of manufacture
 84 -  88     Descriptor Block 2
118 - 123     Descriptor Block 3
127           Checksum
```
The rest are the same (timmings, resolutions, refresh rates, etc). Since product id, manufacture dates, and descriptions are just information, I have to conclude that the only problem with your edid is the checksum (byte 127).

According to the EDID description linked above, the checksum is the sum of all the bytes in the file and has to sum 0 (zero). Yours sums 30. If you replace the 127th byte (current value E3) for B3. The checksum becomes zero. I attached the new edid file (binary).

This is what is next:

Unzip the file new_acer.bin.zip. Copy new_acer.bin into your Ubuntu partition.Boot into safe mode. Login in text mode.

Backup your X configuration file:
```
$ sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```
Copy the new edid into the X11 directory:
```
$ sudo mv new_acer.bin /etc/X11/
```
Configure a new basic X config file using the new edid:
```
$ sudo nvidia-xconfig --custom-edid=/etc/X11/new_acer.bin
```
Double check that your new config file has a CustomEDID line:
```
$ grep acer /etc/X11/xorg.conf
```
The result should be something like this:
```
   Option	"CustomEDID" "DFP-1:/etc/X11/new_acer.bin"
```

Reboot normally.
I really hope this works. Please let us know hot it goes.
Kind Regards.

Note: I'm including my edid file also, just in case (toshibaA665.bin).

EDIT: It seems not any binary file can be attach. I had to zip the edids.

EDIT2: the correct file for you is called new_edid.bin, and it is inside new_edid.bin.zip

---

### Post by dd_dentfull on 2011-10-12
Not working, but...

```
[    17.749] (**) NVIDIA(0): Option "CustomEDID" "/etc/X11/new_acer.bin"
[    17.749] (WW) NVIDIA(0): No display device specified for CustomEDID
[    17.750] (WW) NVIDIA(0): "/etc/X11/new_acer.bin"; ignoring.
[    19.339] (WW) NVIDIA(GPU-0): The EDID read for display device DFP-0 is invalid: the
[    19.339] (WW) NVIDIA(GPU-0): checksum for EDID version 1 is invalid.
```

Removed old xorg.conf

```
$ sudo rm /etc/X11/xorg.conf
```

Created new one

```
$ sudo nvidia-xconfig --custom-edid=/etc/X11/new_acer.bin
```

now rebooting...

---

### Post by papibe on 2011-10-12
That may not work.

If it doesn't work: edit your config file:
```
$ gksudo /etc/X11/xorg.conf
```
Then find out with is the name of your display (probably DFP-0). Change the CustomEDID line so it looks like this:
```
Option	"CustomEDID" "**DFP-0:**/etc/X11/new_acer.bin"
```
And restart again.

Regards.

---

### Post by dd_dentfull on 2011-10-12
After another failed reboot and a quick Google search, I found that I needed to add the DFP-0 prefix to the CustomEDID command.
As I was just about to edit xorg.conf, you posted your last replay.

This is being posted from Unity. I can't stress how thankful I am for the time you spent getting through this. It's been quite fun actually.

---

### Post by papibe on 2011-10-12
Glad is working!

I know how frustrating can be having a good laptop, with a good graphic card, and not able to enjoy the experience because a faulty EDID. The first time took me months to solve it, and suddenly someone with a good spirit helped me.

I guess I'm just paying it forward

Have fun, and enjoy the forums ):P

---

