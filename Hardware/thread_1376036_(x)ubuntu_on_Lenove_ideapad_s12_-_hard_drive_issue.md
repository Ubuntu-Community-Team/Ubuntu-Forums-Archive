---
title: "(x)ubuntu on Lenove ideapad s12 - hard drive issue"
date: 2010-01-08
forum: Hardware
---

### Post by slentzen on 2010-01-08
I have installed both ubuntu and xubuntu 9.10 on my Lenovo ideapad s12. My problem starts already during boot. The first 10 seconds everything boots just fine, but then the system comes to a complete stop and nothing happens unless I touch a button or the mousepad, and then the boot continues.

When the computer is done booting, and in graphical mode, everything works just fine, except that after approximately 30 seconds of not touching the laptop, the activity of my hard drive stops again. If I am copying a file, the process stops, untill touching a key and then continues for another minute. This problem affects everything on the laptop, if downloading, files stops downloading after a minute unless I am active on the laptop.

I have searched around and found the following issue mentioned: [HTML]http://ubuntuforums.org/showthread.php?p=5031046[/HTML]

The workarounds using hdparm 255 has stopped the load cycle count issue on my laptop. But I am still having the problem with all disk activity stopping after af few seconds of leaving the computer alone.

I hope someone can help me, so that i dont have to sit at the computer touching the touchpad in order to copy a file or have anything done.

Thanks

---

### Post by golam on 2010-01-29
I had exactly the same issue of hard drive stalling with 
Kubuntu Karmic (9.10) on ideapad s12.  To solve this, you
need to change SATA controller mode from "AHCI" to "Compatibility"
in the BIOS.

Please do the following steps


(1) Press F2 to enter setup after turning on the machine

(2) Go to "Configurations"

(3) Change "SATA controller working mode" from "AHCI" to
"Compatibility"

(4) Press F10 to "Save and exit"


Then you are done. Ubuntu rocks on this machine!

Cheers,

---

### Post by Epaminond on 2010-02-12
Had the same problem. Solved by adding nolapic and acpi=on to GRUB_CMDLINE_LINUX_DEFAULT section of /etc/defalut/grub.

---

### Post by Dedi Landsman on 2010-03-31
Hi, I have bought Lenovo s12 [Intel atom], i installed on it Easy Peasy [which is Ubuntu 9.04, i tried before to do Ubuntu NR but it was so buggy, so i opt for Easy Peasy]. I'm experiencing exactly the same problem with the minor freeze described here in the thread. I want to ask you guys, so far which solution proved to do the best: the one described by #2 golam, or #3 Epaminond?
A second Q i Have: Is how to get the wireless working?
Thank you very much for any help

---

### Post by Epaminond on 2010-05-04
It seems that there's no such a problem in Ubuntu 10.04.
To get wireless working you have to install Broadcom restricted drivers.

---

### Post by Dedi Landsman on 2010-05-06
Hi, thanks. Good to know that the Lenovo S12 [Intel Atom] works well with Ubuntu 10.04. I had serious problems with testing it with 9.10, so i had to insall on it Easy Peasy which is in fact EEEbuntu 9.04, Generally it works well with it. I had an issue with installing the required driver for wireless: Broadcom STA. it is not found with 9.04 Jaunty in either Synaptic nor in Hardware Drivers [but it does in 9.10 Karmic, waiting out of the box to be activated in Hardware Drivers], i had to compile from source with problems, described a little at [http://s10lenovo.com/viewtopic.php?f=41&t=4167&p=28616#p28616](http://s10lenovo.com/viewtopic.php?f=41&t=4167&p=28616#p28616)
anyway good to know the machine is doing well with the Lynx 10.04. Does the Broadcom STA drivers also waiting to be activated out of the box in 10.04?

---

### Post by Epaminond on 2010-05-08
Yes they do. But you have to make sure you're connected to the internet first. No compiling from source. :)

---

