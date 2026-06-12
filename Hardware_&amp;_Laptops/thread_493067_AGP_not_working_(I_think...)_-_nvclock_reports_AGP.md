---
title: "AGP not working (I think...) - nvclock reports AGP 0x Disabled"
date: 2007-07-05
forum: Hardware &amp; Laptops
---

### Post by psyopper on 2007-07-05
Hi all,

I have a PNY GeForce 6200 256 meg that is supposed to support AGP 4x and AGP 8x. My motherboard only supports AGP 4x. 

The card is currently installed and working properly, Compiz Fusion looks great and I've been playing Warsow and UT2004 at expected levels of gameplay. Well, sort of, I am having some performance issues in UT2K4 that may be related to my question. 

Recently I've been toying around with Conky and was using nvclock to report some stats (temp, clock speeds, etc) to conky. I got more curious about nvclock and noticed this section when I ran nvclock -i in the terminal:

-- AGP info --
Status:         Disabled
Rate:           0X
AGP rates:      4X 8X 
Fast Writes:    Disabled
SBA:            Disabled

It appears that my AGP is disabled? How could this be true if it seems to be working fine? 

Is there a way to see if I actually do have AGP enabled, and at what speed?

If it turns out that I don't have AGP enabled, how do I enable/configure it?

EDIT - More information:

brad@Ubuntu:~$ cat /proc/driver/nvidia/agp/status
Status:          Disabled

AGP initialization failed, please check the ouput  
of the 'dmesg' command and/or your system log file 
for additional information on this problem.

brad@Ubuntu:~$ dmesg | grep "AGP"
[   17.964000] agpgart: AGP aperture is 64M @ 0xe0000000
[   32.664000] NVRM: not using NVAGP, an AGPGART backend is loaded!

---

### Post by psyopper on 2007-07-05
It looks like [this post at Gentoo Wiki has the answers]("http://gentoo-wiki.com/HARDWARE_Nvidia_Driver_AGP_FastWrite_and_Side_Band_Addressing").

Can anyone confirm that I won't totally break my system doing this?

---

### Post by psyopper on 2007-07-05
RESOLVED:

I found a number of other posts relating to this same problem. I tried a few different things to force AGPGART to not load and force NvAGP to load, none of which succeeded:

[http://ramikayyali.com/archives/2005/11/27/nvidia]("http://ramikayyali.com/archives/2005/11/27/nvidia")
[http://ubuntuforums.org/showthread.php?t=410745]("http://ubuntuforums.org/showthread.php?t=410745")
[http://http://gentoo-wiki.com/HARDWARE_Nvidia_Driver_AGP_FastWrite_and_Side_Band_Addressing]("http://http://gentoo-wiki.com/HARDWARE_Nvidia_Driver_AGP_FastWrite_and_Side_Band_Addressing")

Again, none of these worked. What did work is this:

In /etc/X11/xorg.conf I changed 
    Option         "NvAGP" "1"
to
    Option         "NvAGP" "2"

Option 1 forces the driver to use NvAGP
Option 2 forces the driver to use AGPGART
(Option 3 forces AGPGART if available, otherwise use NvAGP)

Now when I  cat /proc/driver/nvidia/agp/status I get the following:

Status:          Enabled
Driver:          AGPGART
AGP Rate:        8x
Fast Writes:     Disabled
SBA:             Enabled

Whish is just how it should look for this card. Sort of... It's supposed to be a 4x port on the mobo but is reporting 8x. We'll see if I have any performance issues...

---

