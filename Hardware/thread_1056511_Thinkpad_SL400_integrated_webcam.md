---
title: "Thinkpad SL400 integrated webcam"
date: 2009-01-31
forum: Hardware
---

### Post by wawacito on 2009-01-31
Hello - I'm a newbie here. Just installed 8.10 onto my new Lenovo Thinkpad SL400 laptop.  Have installed all the updates that are available.  I cannot get my webcam to show up on Ekiga or Skype. 

My kernel is 2.6.27-11 generic.

"lsusb" command tells me:
Bus 008 Device 002: ID 17ef:480b Lenovo

"dmesg | less" command tells me:
[   13.943588] Linux video capture interface: v2.00
[   13.995062] thinkpad_acpi: Not yet supported ThinkPad detected!
[   14.096962] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 2
2
[   14.097047] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   14.113374] uvcvideo: Found UVC 1.00 device Integrated Camera (17ef:480b)
[   14.166562] uvcvideo: Failed to query (135) UVC control 1 (unit 0) : -32 (exp. 26).
[   14.189693] usbcore: registered new interface driver uvcvideo
[   14.189712] USB Video Class driver (v0.1.0)


Does this mean it's not supported?
Is there something I can do?

---

### Post by wawacito on 2009-02-06
I'm guessing not a lot of people are using webcams?

I've been scouring the web looking for programs that will allow video chat between linux and windows - linux still seems to be severely lacking in the video chat area - not surprising then that my webcam doesn't work i guess.

my integrated webcam doesnt work on my lenovo SL400 laptop.
i have also a Microsoft NX-6000 that works with Ekiga on my linux 8.10 desktop - but not with skype.  If I plug in that same NX-6000 to my laptop - again it doesnt work with skype - and on ekiga i can't select it - everytime i select it keeps defaulting back to the integrated webcam (which doesnt work). 

no webcams in linux?

---

### Post by wawacito on 2009-02-06
ok after several days of searching - i finally found a solution by Laurent Pinchart:

[http://www.mail-archive.com/linux-uvc-devel@lists.berlios.de/msg03442.html](http://www.mail-archive.com/linux-uvc-devel@lists.berlios.de/msg03442.html)

sudo rmmod uvcvideo
sudo modprobe uvcvideo quirks=16

my question to the forum now is:  I have to do this every time turn on the laptop.  Is there a way to make this change permanent on every boot?


By the way - it only works in Ekiga and luvcview at this point - doesn't work with Cheese and doesn't work with Skype.

---

### Post by wawacito on 2009-02-08
is there something equivalent to an "autoexec.bat" for linux?

thus far ive been the only one replying here. That makes for a rather disappointing thread.

i had been told the community support for linux was great.  especially so of the ubuntu community.  thus far my experience with ubuntu has been like pulling teeth, and the support has been non-existant except for my own exhaustive web-searches.

please - is anybody out there?

---

### Post by IndieRockSteve on 2009-03-18
> **wawacito said:**
> ok after several days of searching - i finally found a solution by Laurent Pinchart:

[http://www.mail-archive.com/linux-uvc-devel@lists.berlios.de/msg03442.html](http://www.mail-archive.com/linux-uvc-devel@lists.berlios.de/msg03442.html)

sudo rmmod uvcvideo
sudo modprobe uvcvideo quirks=16

my question to the forum now is:  I have to do this every time turn on the laptop.  Is there a way to make this change permanent on every boot?


By the way - it only works in Ekiga and luvcview at this point - doesn't work with Cheese and doesn't work with Skype.

edit your /etc/modprobe.d/options and add
options uvcvideo quirks=16

save. now when you load that module it will automatically add the module option.

---

### Post by wawacito on 2009-04-28
IndieRockSteve: thank you SOOOOO much for answering.

unfortunately there is no such file "options" in my /etc/modprobe.d/ directory.  Just 9 files that end in ".conf" most of which start with "blacklist".  

Do I just create a new file called "options" with only one line in it?

file begin
"options uvcvideo quirks=16"
file end

---

