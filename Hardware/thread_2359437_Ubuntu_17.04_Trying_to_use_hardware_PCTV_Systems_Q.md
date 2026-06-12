---
title: "Ubuntu 17.04: Trying to use hardware: PCTV Systems QuatroStick 510e"
date: 2017-04-24
forum: Hardware
---

### Post by pete-br on 2017-04-24
I have installed Ubuntu 17.04 on my new pc. To watch television I would like to use my usb tv stick: PCTV Systems QuatroStick 510e to watch both analog tv and digital dvb-c.
Here is a link to the manual of my device: [ftp://ftp.pctvsystems.com/TV/documentation/Hardware_quick_start_quide/PCTV_Quatro_Stick_510e_quick_start_guide.pdf](ftp://ftp.pctvsystems.com/TV/documentation/Hardware_quick_start_quide/PCTV_Quatro_Stick_510e_quick_start_guide.pdf)

I was hoping for an out-of-the box experience, but things didn't turn out like that.
In the software center if found and installed 'Digital TV Setup'.
It found my hardware, but couldn't find any channels.
Something had to be wrong...

I thought it could be a hardware problem and thought about using 'dmesg' to detect such problems.
At first there was a complaint in the logs of a missing firmware file
After searching for it I found: [http://www.hauppauge.de/pctv-downloads/firmware/tv-tuner/510e/dvb-demod-drxk-pctv.fw](http://www.hauppauge.de/pctv-downloads/firmware/tv-tuner/510e/dvb-demod-drxk-pctv.fw)
Somewhere I found instructions to download that file and copy it over to /lib/firmware.
That is what I did and the error went away.

In dmesg there are still 2 problems reported with my QuatroStick:
1:
em28xx 5-4:1.0: New device Pinnacle Systems PCTV 510e @ 480 Mbps (2304:0242, interface 0, class 0)
em28xx 5-4:1.0: Audio interface 0 found (Vendor Class)
em28xx 5-4:1.0: Video interface 0 found: isoc
em28xx 5-4:1.0: DVB interface 0 found: isoc
2:
em28xx 5-4:1.0: Currently, V4L2 is not supported on this model
em28xx 5-4:1.0: dvb set to isoc mode.

These entries appear in red in dmesg.

So far the 'Digital TV Setup' application has not been able to find any channels.


I have found that anything related to analog video and digital TV should be on the LinuxTV website:
[https://www.linuxtv.org/wiki/index.php/Main_Page](https://www.linuxtv.org/wiki/index.php/Main_Page)
And my device is listed under 'old data' in this compatibility list:
[https://www.linuxtv.org/wiki/index.php/DVB-C_USB_Devices](https://www.linuxtv.org/wiki/index.php/DVB-C_USB_Devices)
They don't seem to have a forum or anything.

I have found something indicating that my 510e device is close to equal a 520e device:
[https://redmine.blare-ids.org/projects/kblare/repository/revisions/fa5527cd3f428845d7950e6b2bab6babcbcd907b](https://redmine.blare-ids.org/projects/kblare/repository/revisions/fa5527cd3f428845d7950e6b2bab6babcbcd907b)


I am hoping someone can tell me what to do next. I can't find a way to make my device work.

---

### Post by pete-br on 2017-04-25
I've made progress on my search.

As 'dmesg' calls my device by name I figured it has some driver for it even when it complains about not supporting V4L2.
So, maybe, it would be possible to do something with it and the commandline might give me more clues.


I have installed the "w-scan" package (sudo apt-get install w-scan). That is w-scan with a hyphen, not an underscore.
And that way I was able to use the command 'w_scan -fc -x > dvbscan.txt'
Here is a page that has more information about that command:
[https://www.linuxtv.org/wiki/index.php/Dvbscan](https://www.linuxtv.org/wiki/index.php/Dvbscan)

Unfortunately thing aren't working as expected.
The scan takes about 15 minutes to completed. At the end of the scan a file dvbscan.txt is created but remains completely empty.
I find that strange because during the scan I see names of tv/radio channels appear in the terminal.
It is scanning, it finds things, but doesn't want to save anything it found to a file.
I have tried different variations including and excluding a country/different countries option, but nothing worked.


Besides that I have also installed the package "xawtv".
That adds the 'scantv' command for scanning for analog tv channels.
It however doesn't work at all. It doesn't "see" my tv card (yet).

---

### Post by pete-br on 2017-04-28
I gave it a try using Kaffeine. After fiddling around with settings it finally found digital tv channels.

But still no analog reception. Most of the digital channels are encrypted and cannot be used. I really need to get analog working. Digital is just a nice added option. All the important channels are available in analog. If anyone has a suggestion?

When i run the 'scantv' command it outputs:
vid-open-auto: failed to open an analog TV device
vid-open: could not find a suitable videodev
no analog TV device available

In Windows everything works perfectly.

---

### Post by pete-br on 2017-04-28
Apparently my TV stick is using a chip for analog TV which has not support for Linux: Micronas AVF 4910.
That concludes my search. As there is no support, I will not be able to watch analog television on Linux.
Since the device is several years old, support probably will never come.
I don't know what I will do next. I'll call this thread "solved", but without solution.

---

