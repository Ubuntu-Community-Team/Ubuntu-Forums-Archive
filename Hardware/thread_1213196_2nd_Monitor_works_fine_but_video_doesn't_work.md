---
title: "2nd Monitor works fine but video doesn't work"
date: 2009-07-14
forum: Hardware
---

### Post by Buchinho99 on 2009-07-14
I bought a new monitor today to work with my IBM Thinkpad and the I extended the range of the screen (no cloning) with that new piece!
Everything works now except Video which keeps crashing which really annoys me... even on the old laptop monitor...

Here is my Xorg.conf:
> Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection "Display"
		Virtual	2960 1050
	EndSubSection
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Here is the output of vlc when I want to play a video with it:
> [????????] x11 video output error: X11 request 132.19 failed with error code 11:
 BadAlloc (insufficient resources for operation)
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  132 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  81
  Current serial number in output stream:  82

and from totem:
> The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 154 error_code 11 request_code 132 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)


Seems to me that the programs can't find the second monitor...

---

### Post by Buchinho99 on 2009-07-14
Thanks guys,

I fixed it myself with this here: [https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4)

---

