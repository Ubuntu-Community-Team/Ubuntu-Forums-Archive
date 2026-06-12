---
title: "Working ALSA setup for Asus EEE 1000HE"
date: 2009-06-19
forum: Hardware
---

### Post by O'buntu on 2009-06-19
Hi everybody,

     Well, here it is, my first thread.  It has taken me close to a month to iron out the problems with ALSA on 9.04, and finally I have found a configuration that works for my 1000HE.  Oh, and if you're out there, greetings to Sonic Shrimps...I hope you can use this.  ;)

     The basics:

          -I have tested this on Kernels 2.6.27-7, 2.6.27-11, 2.6.28-11 and 2.6.28-13 on 8.10, 8.10, 9.04 and 9.04 respectively.

          -I am using the standard Ubuntu install, not the netbook remix, but I would imagine this should work the same for all Ubuntus since they're pretty much the same 'under the hood'.

-The audio chipset for my 1000HE is identified as ALC269, and ICH7 depending on where you look; I suspect most if not all 1000HE have this chipset.

          -I'm currently running the latest Elmurato scripts with very little customization.  The <Fn><F10, F11 and F12> keys working with this script for the volume up and down on the Master channel.  Thanks a billion for these Elmurato!

          -I've tried configuring the ALSA included with 8.10, 9.04 and manually compiling the source for 1.0.18, 1.0.19 and 1.0.20 for the Drivers, Firmware, Libraries and Utilities as outlined elsewhere in these forums.

          -Many configurations work partially, but only one that I've found works completely.



     The working config:

          -Download at least the drivers, firmware and utils source .bz2 files from the ALSA project website for 1.0.19.

          -After extracting the contents into separate directories, compile and install the above packages, using sudo and the following commands respectively...
               
./configure --with-cards=hda-intel
               make
               make install

           *NOTE: --with-cards=hda-intel is only really necessary for compiling the drivers package, but it didn't hurt me to include it for every package*

          -After compiling these and rebooting, edit the /etc/modprobe.d/alsa-base.conf file to include the following line at the end of the file

options snd-hda-intel model=basic

          -Reboot once more, and enjoy your working 1000HE sound!



Please feel free to tell me if I've left anything out, or could improve this.  It was a huge headache figuring out which ALSA version and settings would work, so I hope this alleviates some suffering for other 1000HE users.

Cheers!
O'Buntu

P.S., to the developers of Ubuntu, all millions of you, thanks for a truly excellent free operating system.  Long live open-source!

---

### Post by exactt on 2009-06-29
[http://ubuntuforums.org/showthread.php?t=1113178](http://ubuntuforums.org/showthread.php?t=1113178)

pointed me to .deb packages for alsa 1.0.19

now i have problems with the mic. have you checked if your mic is working?

---

### Post by O'buntu on 2009-07-06
Thanks for the heads-up exactt.  I have found the same here, switching between all recording sources (internal mic, mic, and line-in) there seems to be no input.  It is notable that I hear nothing when I put the input playback channels up to the top from the speakers, but with the headphones in, I do hear hiss.  No input on sound though.  Not sure exactly why (a little beyond my depth), but if I find an answer I'll put it here.  I haven't actually tested the use of an external mic, and since everything works fine in XP, I doubt it's the hardware, but rather the software mapping to the hardware that is the breaking point here.

Anybody else with an idea?

Also, the front channel seems to default to 81% no matter what I do.  Even using alsactl store 0 does nothing to help.  It keeps the channels where they should be right up until a reboot, at which point they go back to their 'original' defaults.

---

### Post by exactt on 2009-08-07
i filed a bug report for the microphone issue: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/410212](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/410212)

p.s. i also found out that updating the bios actually helps the whole sound (output) issue. at the moment i am back to alsa 1.0.18...

---

