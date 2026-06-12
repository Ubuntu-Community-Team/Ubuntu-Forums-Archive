---
title: "ASUS nVidia not showing second monitor properly?"
date: 2013-03-26
forum: Hardware
---

### Post by Jamie_Edwards on 2013-03-26
Hi guys,

I've recently changed my graphics card to the ASUS nVidia GeForce 210 and I'm having huge problems.

When I first installed the drivers for it, everything c**ked up. as it didn't have that nvidia-xconf thing. Fine, no biggy. So I reinstalled Ubuntu and tried again using a tutorial on the internet. This went OK. and it's now "working".

What isn't working however is that my second monitor is completely the wrong resolution to how it should be. I have a 15" screen at 1024x768 and a 19" HDTV monitor which should be at 1920x1080 but instead it's something like 800x600. Oh and the Displays app also says that the HDTV is 'Unknown'.

I've looked at a few threads and one said it could be the HDMI cable, but I know it isn't because after I read it I tried the cable in both my XBox and my parents laptop and it displayed fine.

Any idea's on what I could do?

A fewe details about my setup:

Ubuntu 12.10 64-bit
ASUS nVidia GeForce 210
Philips 15" Monitor (1024x768)
Technika 19" HDTV (supposed to be 1920x1080 but at the moment 800x600)

Thanks guys.

---

### Post by Jamie_Edwards on 2013-03-26
No one knows how I can solve this?

---

### Post by papibe on 2013-03-26
Hi Jamie_Edwards.

Could you tell us about the card's outputs, the cables you are using, and what inputs are plug in on the monitors?

Regards.

---

### Post by Jamie_Edwards on 2013-03-26
The card has three ports: VGA, HDMI and DVI-I to which I'm using the VGA and a DVI to HDMI adapter ( but I had a go at using the HDMI slot with the same result.

---

### Post by papibe on 2013-03-26
Thanks.

Could you please post the content of these files:
```
/etc/X11/xorg.conf

/var/log/Xorg.0.log
```
Paste them separately here: [http://paste.ubuntu.com/]("http://paste.ubuntu.com/"), and post back the links to them.

Regards.

---

### Post by Jamie_Edwards on 2013-03-26
xorg.conf:
[http://paste.ubuntu.com/5651083/](http://paste.ubuntu.com/5651083/)

Xorg.0.log:
[http://paste.ubuntu.com/5651091/](http://paste.ubuntu.com/5651091/)

There you go.

---

### Post by Jamie_Edwards on 2013-03-26
Reading through the text I noticed this on line 640-641:

    The EDID read for display device DFP-0 is invalid:     [  9954.350] (WW) NVIDIA(GPU-0):     unrecognized EDID Header.

That doesn't sound too good...

---

### Post by papibe on 2013-03-26
```
[    32.231] (WW) NVIDIA(GPU-0): The EDID read for display device DFP-0 is invalid:
[    32.231] (WW) NVIDIA(GPU-0):     unrecognized EDID Header.
[    32.231] (--) NVIDIA(GPU-0): 
```
The card can't get the TV's internal timings (EDID).

I would try another TV input, and making sure the cable is well connected. Some TV manufactures publish that data, and it may be possible to get it into a file and hardcode it into your xorg.conf

What is your TV's brand and model? 

Regards.

---

### Post by Jamie_Edwards on 2013-03-26
The model is Technika and the model is LCD19-218

---

### Post by Jamie_Edwards on 2013-03-27
OK, after finding a few other posts about this kind of issue ( with yourself helping ) I've managed to find a few things out...

It does seem to be a dead/corrupt EDID and after doing 
```

sudo get-edid > filename

```

I got the following:
[http://paste.ubuntu.com/5652329/](http://paste.ubuntu.com/5652329/)

Then after doing
```

sudo parse-edid

```

I got the following:
[http://paste.ubuntu.com/5652333/](http://paste.ubuntu.com/5652333/)

I also tried using that Phoenix EDID Editor but it threw a "Disk Full" error.

Finally I think that this:
[http://paste.ubuntu.com/5652343/](http://paste.ubuntu.com/5652343/)

Is the EDID for the HDTV ( which is also labeled as DFP-0 )

---

### Post by papibe on 2013-03-27
I think I got something.

I took the raw EDID data:
```
00 00 ff ff ff ff ff 00 0e d4 80 10 33 41 32 01
20 11 01 03 80 46 28 78 0a ee 91 a3 54 4c 99 26
0f 50 54 00 00 00 01 01 01 01 01 01 01 01 01 01
01 01 01 01 01 01 02 3a 80 d0 72 38 2d 40 10 2c
45 80 df a4 21 00 00 1e 8c 0a d0 8a 20 e0 2d 10
10 3e 96 00 df a4 21 00 00 18 00 00 00 fc 00 43
56 54 45 20 54 56 0a 20 20 20 20 20 00 00 00 fd
00 30 3e 0e 46 0f 00 0a 20 20 20 20 20 20 01 96

```
I used this code:
```
#include <stdio.h>

int main()
{
	unsigned char i;

	scanf("%02x ", &i);
	while (!feof(stdin))
	{
		printf("%c", i);
		scanf("%02x", &i);
	}
	return 0;
}
```
And got this:
```
$ ./hex2bin < edid.txt | parse-edid 
parse-edid: parse-edid version 2.0.0
**[COLOR="#FF0000"]parse-edid: EDID checksum failed - data is corrupt. Continuing anyway.[/COLOR]**

	# EDID version 1 revision 3
Section "Monitor"
	# Block type: 2:0 3:fc
	Identifier "CVTE TV"
	VendorName "CVT"
	ModelName "CVTE TV"
	# Block type: 2:0 3:fc
	# Block type: 2:0 3:fd
	HorizSync 14-70
	VertRefresh 48-62
	# Max dot clock (video bandwidth) 150 MHz
	# DPMS capabilities: Active off:no  Suspend:no  Standby:no

	Mode 	"1920x1080"	# vfreq 50.000Hz, hfreq 56.250kHz
		DotClock	148.500000
		HTimings	1920 1968 2012 2640
		VTimings	1080 1084 1089 1125
		Flags	"+HSync" "+VSync"
	EndMode
	Mode 	"720x480"	# vfreq 59.940Hz, hfreq 31.469kHz
		DotClock	27.000000
		HTimings	720 736 798 858
		VTimings	480 489 495 525
		Flags	"-HSync" "-VSync"
	EndMode
	# Block type: 2:0 3:fc
	# Block type: 2:0 3:fd
EndSection
```
That sounds like the correct info for a TV (1920x1080 res), but with a invalid checksum.

This problem is very similar to this [thread]("http://ubuntuforums.org/showthread.php?t=1857772&highlight=edid"). Take a look at it and see if you can continue the steps. If not, let us know so we can give you more directions.

Regards.

---

### Post by Jamie_Edwards on 2013-03-27
As I said, I can't use Phoenix EDID Editor because it's throwing an error saying "Disk Full" :L

---

### Post by Jamie_Edwards on 2013-03-27
I tried using Phoenix on my parents laptop but I haven't got a clue in what to do and how to use it and if it means I'm needing to attach my HDTV to it then I can't :L

---

### Post by Jamie_Edwards on 2013-03-28
Right new update to trying to get my monitor to work....

I tried going into nvidia-settings, clicked on DFP-0 and then to my dismay, the "Acquire EDID" button was greyed out signalling I can't use it. However on a whim I read in another post that the OP had his running through a VGA switch ( much the same as mine ) but got better results by removing his cable from that switch and putting it into its own port.

I shut my computer down and did the same only to find it was to no avail. I then did some more searching and found another post talking about a custom bash script that would extract the edid, decode it and then allow you to edit it and write it back to the monitor memory. I gave it a try and sure enough it "worked" ( well it didn't as you'll see ). The script is this:
[https://github.com/bulletmark/edid-rw](https://github.com/bulletmark/edid-rw)

I then did as it said using
```

sudo ./edid-rw 0 | edid-decode

```

and got this:
```

Traceback (most recent call last):
  File "./edid-rw", line 141, in <module>
    main()
  File "./edid-rw", line 129, in main
    edid = [dev.read(i) for i in range(EDID_HDR)]
  File "./edid-rw", line 48, in read
    return self.smb.read_byte_data(EDID_ADDR, n)
IOError: [Errno 5] Input/output error
Extracted contents:
header:          00 00 00 00 00 00 00 00
serial number:   00 00 00 00 00 00 00 00 00 00
version:         00 00
basic params:    00 00 00 00 00
chroma info:     00 00 00 00 00 00 00 00 00 00
established:     00 00 00
standard:        00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
descriptor 1:    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
descriptor 2:    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
descriptor 3:    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
descriptor 4:    00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
extensions:      00
checksum:        00

No header found
[COLOR=#ff0000]Manufacturer: @@@ Model 0 Serial Number 0[/COLOR]
EDID version: 0.0
Analog display, Input voltage level: 0.7/0.3 V
Sync: 
Image size is variable
Gamma: 1.00
Monochrome or grayscale display
Established timings supported:
Standard timings supported:
non-conformant standard timing (0 horiz)
non-conformant standard timing (0 horiz)
non-conformant standard timing (0 horiz)
non-conformant standard timing (0 horiz)
non-conformant standard timing (0 horiz)
non-conformant standard timing (0 horiz)
non-conformant standard timing (0 horiz)
non-conformant standard timing (0 horiz)
Manufacturer-specified data, tag 0
Manufacturer-specified data, tag 0
Manufacturer-specified data, tag 0
Manufacturer-specified data, tag 0
Checksum: 0x0
EDID block does not conform at all!
    Bad year of manufacture
    Manufacturer name field contains garbage

```

That doesn't look good, so I tried having a stab at my Philips:
```

Extracted contents:
header:          00 ff ff ff ff ff ff 00
serial number:   41 0c 13 08 cb 7d 03 00 1d 0d
version:         01 03
basic params:    0e 1e 17 78 ea
chroma info:     7e a5 a0 58 4e 96 25 1e 50 54
established:     bf ee 00
standard:        01 01 01 01 01 01 01 01 01 01 01 01 01 01 01 01
descriptor 1:    64 19 00 40 41 00 26 30 18 88 36 00 33 e6 10 00 00 18
descriptor 2:    00 00 00 ff 00 20 43 58 20 20 32 32 38 38 31 31 0a 20
descriptor 3:    00 00 00 fc 00 50 68 69 6c 69 70 73 20 31 35 30 42 0a
descriptor 4:    00 00 00 fd 00 38 4c 1e 3f 08 00 0a 20 20 20 20 20 20
extensions:      00
checksum:        91

[COLOR=#0000cd]Manufacturer: PHL Model 813 Serial Number 228811[/COLOR]
EDID version: 1.3
Analog display, Input voltage level: 0.7/0.3 V
Sync: Separate Composite SyncOnGreen 
Maximum image size: 30 cm x 23 cm
Gamma: 2.20
DPMS levels: Standby Suspend Off
RGB color display
First detailed timing is preferred timing
Established timings supported:
  720x400@70Hz
  640x480@60Hz
  640x480@67Hz
  640x480@72Hz
  640x480@75Hz
  800x600@56Hz
  800x600@60Hz
  800x600@72Hz
  800x600@75Hz
  832x624@75Hz
  1024x768@60Hz
  1024x768@70Hz
  1024x768@75Hz
Standard timings supported:
Detailed mode: Clock 65.000 MHz, 307 mm x 230 mm
               1024 1048 1184 1344 hborder 0
                768  771  777  806 vborder 0
               -hsync -vsync
Serial number:  CX  228811
 Monitor name: Philips 150B
Monitor ranges: 56-76HZ vertical, 30-63kHz horizontal, max dotclock 80MHz
Checksum: 0x91
EDID block does not conform at all!
    Bad year of manufacture

```

That looks better. But it's from my working monitor. As you can see from the highlight that the Philips monitor is picked up properly whereas Ubuntu hasn't got a clue about the Technika... Anyway. I extracted the DFP monitor to a binary file and opened it in vim to find nothing. Nothing at all.

I have no clue in what to do now. I can't edit the edid because a) I don't know how to and b) because there is nothing there.

---

### Post by papibe on 2013-03-28
I just want to make sure of a couple of things before going forward.

If I understand correctly the Phillips monitor is set up properly and have a max resolution of 1024x768. If that is correct. The raw  EDID data that you can see on the log you linked on post #6 has to be from the TV.

As you can see in post #11, I took that data and parsed it manually using parse-edid that comes on the package read-edid. The parsed data confirms that the max resolution is full HD: 1920x1080, but also that it is corrupt.

With that in mind, the first thing that I would try is to adjust the last byte to correct the checksum (explained on post #10 of the thread that I linked).

Are we on the same page?

Let me know so we can move in that direction, if that's OK with you of course. 
Regards.

---

### Post by Jamie_Edwards on 2013-03-28
Thank you for being patient with me thus far. 

After sitting down and really trying to get my head around it, I really don't know what I'm supposed to be doing. I haven't got a working edid.bin file that I could use and what's more is, I don't know what I'm supposed to do to make the checksum valid. You stated in the other post:

> According to the EDID description linked  above, the checksum is the sum of all the bytes in the file and has to  sum 0 (zero). Yours sums 30. If you replace the 127th byte (current  value E3) for B3. The checksum becomes zero.


How do I get to editing that in the first place, and what do I edit it to? I really do not know I'm supposed to do :S

---

### Post by papibe on 2013-03-29
This is a the EDID data from your Xorg.0.log saved as edid.txt:
```
00 00 ff ff ff ff ff 00 0e d4 80 10 33 41 32 01
20 11 01 03 80 46 28 78 0a ee 91 a3 54 4c 99 26
0f 50 54 00 00 00 01 01 01 01 01 01 01 01 01 01
01 01 01 01 01 01 02 3a 80 d0 72 38 2d 40 10 2c
45 80 df a4 21 00 00 1e 8c 0a d0 8a 20 e0 2d 10
10 3e 96 00 df a4 21 00 00 18 00 00 00 fc 00 43
56 54 45 20 54 56 0a 20 20 20 20 20 00 00 00 fd
00 30 3e 0e 46 0f 00 0a 20 20 20 20 20 20 01 96
```
To convert that to a binary file, I've used this C program called hex2bin.c
```
#include <stdio.h>

int main()
{
	unsigned char i;

	scanf("%02x ", &i);
	while (!feof(stdin))
	{
		printf("%c", i);
		scanf("%02x", &i);
	}
	return 0;
}
```
And compiled into hex2bin:
```
gcc hex2bin.c -o hex2bin
```
To calculate the checksum I've used this program called checksum.c:
```
#include <stdio.h>

int main()
{
  unsigned char sum;
  int i;

  sum = 0;
  for( i = 0; i < 128; i++)
  {
    unsigned char byte;

    scanf("%c", &byte);
    // printf("%X\n", byte);
    sum += byte;
  }
  printf("%x\n", sum);
  return 0;
}
```
That I compiled into checksum:
```
gcc - checksum.c -o checksum
```
Then I can check the sum by doing:
```
$ ./hex2bin < edid.txt | ./checksum
```
Which gives:
```
1
```
So we have 1 instead of 0. The purpose of the last byte is that the sum gives 0. If you replace the last byte from 96 to 95. The sums become 0 ;)

I edited the text file and saved as corrected_edid.txt. Then I double check the sum is correct:
```
$ ./hex2bin < corrected_edid.txt | ./checksum 
0

```
Now I save that into a binary file like this:
```
./hex2bin < corrected_edid.txt > edid.bin
```
Which is the file compressed and attached,

Would you be able to complete the next steps?

Let me know if you need more help with that.
Regards.

---

### Post by Jamie_Edwards on 2013-03-29
Update...

Despite doing everything you've stated both in this post and the other post, it's still using the EDID from the actual TV and not from the custom edid?

After I rebooted, the display is still 800x600 so I did a little digging....
```
:~$ grep technika /etc/X11/xorg.conf
    Option         "CustomEDID" "/etc/X11/technika_edid.bin"

```

OK so it's there. But why is it not using it!?! just for kicks I have a look in Xorg.0.log and started searching to see if it would be loaded...
```

[    14.708] (**) NVIDIA(0): Option "CustomEDID" "/etc/X11/technika_edid.bin"

```

Oh so it is. If you want to see the file I posted it on pastebin...
[http://paste.ubuntu.com/5658181/](http://paste.ubuntu.com/5658181/)

Any ideas?




Edit...
I noticed later on in the other post that you saud the OP should place DFP-0: into the CustomEDID option. I did so and though it didn't work with -0 I tried -1 and well this happened in Xorg.0.log:
```

[    29.014] (WW) NVIDIA(GPU-0): Unable to use EDID file '/etc/X11/technika_edid.bin': file
[    29.014] (WW) NVIDIA(GPU-0):     format not recognized

```

At least I know that and it's now turned into the problem X(

---

### Post by papibe on 2013-03-29
:(

Yes, if there are several monitors involved, you should use the name of the monitor. According to your logs the proper name would be DFP-1

Did you unzip the attachment?

Could you post the result of this command?
```
parse-edid < /etc/X11/technika_edid.bin
```
You may need to install this first:
```
sudo apt-get install read-edid
```
Regards.

---

### Post by Jamie_Edwards on 2013-03-29
Funny, the output is
```

:~$ sudo parse-edid < /etc/X11/technika_edid.bin
bash: /etc/X11/technika_edid.bin: Permission denied

```

Umm, something's telling me that xorg hasn't got the permission it needs to access the file?

---

### Post by papibe on 2013-03-29
Try this:
```
 sudo chmod 755 /etc/X11/technika_edid.bin 
```
Then check if permissions are OK:
```
 ls -l /etc/X11/technika_edid.bin
```
Then try again the parse command (you don't need sudo btw).

Regards.

---

### Post by Jamie_Edwards on 2013-03-29
Still the same outcome :L

Xorg.0.log is stating that the file format is wrong?

Edit...

Could it need a .raw extension instead?

---

### Post by Jamie_Edwards on 2013-03-30
Any ideas? :L

---

### Post by Jamie_Edwards on 2013-03-31
Couold it be the fact I'm using 12.10 and not 12.04?

What I mean by that is, if I install 12.04 will the problem hopefully resolve itself?

---

### Post by Jamie_Edwards on 2013-04-01
Right now now that I've changed back to 12.04 and read through the steps, I'm getting the following from Xorg.0.log:
```

[  3649.048] (WW) NVIDIA(GPU-0): Unable to use EDID file '/etc/X11/edid.bin': file format not
[  3649.048] (WW) NVIDIA(GPU-0):     recognized
[  3649.078] (WW) NVIDIA(GPU-0): The EDID read for display device DFP-1 is invalid:
[  3649.078] (WW) NVIDIA(GPU-0):     unrecognized EDID Header.

```

The second time I unzipped the EDID file you provided, it came out with the right permissions which are as follows:
[http://paste.ubuntu.com/5668084/](http://paste.ubuntu.com/5668084/)

I really want to know why the EDID header is unrecognised :L and more importantly, how to fix it.

---

### Post by Jamie_Edwards on 2013-04-02
Update...

Right, I've had a play around in xorg.conf and this is what I did...

I opened up the file and put the following in:

```

Option        "NoEDID"        "True"
#Option       "UseEDID"       "False"

```

The reason behind me commenting out the "UseEDID" option is so I could test each out one by one. When I restarted with the above. It had the same outcome as before, so I opened Xorg.0.log and had a look. I noticed that it looked as though it was loading the above for CRT-1 ( which is my fully functioning Philips monitor ) and then complain it wasn't the right file format.

So I uncommented the "UseEDID" and rebooted again to find a very ugly change, my Philips was exactly the same as my Technika TV. Again I looked in Xorg.0.log and found that it won't probe either monitors EDID's, so I deleted the two new options ( leaving the custom-edid one ) and rebooted to find my Philips back to normal... Could it be that Ubuntu is trying to load the EDID for my Philips and as a result not recognising it and not bothering with my Technika?

If you're wondering, here's my new xorg.conf file:
[http://paste.ubuntu.com/5672388/](http://paste.ubuntu.com/5672388/)

Thanks.

---

### Post by papibe on 2013-04-02
Could you post the result of this command?
```
parse-edid < /etc/X11/technika_edid.bin
```
Regards.

---

### Post by Jamie_Edwards on 2013-04-03
Here it is:
[http://paste.ubuntu.com/5673449/](http://paste.ubuntu.com/5673449/)

---

### Post by Jamie_Edwards on 2013-04-04
Anything?

---

### Post by Jamie_Edwards on 2013-04-06
I really need this fixed so I can use the CUDA function of the card with Blender 3D, otherwise I'm going to need to change back to my previous card.

Any idea's?

---

### Post by Jamie_Edwards on 2013-04-21
[COLOR=#C61919]**papibe, have you managed to figure out what's happening yet?**[/COLOR]

---

