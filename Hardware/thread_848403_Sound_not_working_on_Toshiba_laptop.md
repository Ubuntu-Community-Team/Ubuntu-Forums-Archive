---
title: "Sound not working on Toshiba laptop"
date: 2008-07-03
forum: Hardware
---

### Post by johannalb on 2008-07-03
Hi my sound is not working on my Toshiba Equium L40-10U Laptop. I'm not sure what the sound card is. Please help?

Thanks

Johanna

---

### Post by stchman on 2008-07-03
> **johannalb said:**
> Hi my sound is not working on my Toshiba Equium L40-10U Laptop. I'm not sure what the sound card is. Please help?

Thanks

Johanna

Provide us an lspci output in this thread.  We need to know what kind of sound card you have.

---

### Post by phidia on 2008-07-03
Hi, Open a terminal (from Applications>Acessories) and type aplay -l
That hopefully will tell you what card you have.
Follow [this guide]("https://help.ubuntu.com/community/SoundTroubleshooting") for getting it working, or report back with more info.

---

### Post by CommonClone on 2008-07-03
Did you recently install Ubuntu on your laptop?  What version are you running?

---

### Post by johannalb on 2008-07-03
I installed ubuntu yesterday, the newest version, hardy heron...


Heres what I got:

LSPCI OUTPUT:

johanna@johanna-laptop:~$ lspci output
Usage: lspci [<switches>]

-v		Be verbose
-n		Show numeric ID's
-nn		Show both textual and numeric ID's (names & numbers)
-b		Bus-centric view (PCI addresses and IRQ's instead of those seen by the CPU)
-x		Show hex-dump of the standard portion of config space
-xxx		Show hex-dump of the whole config space (dangerous; root only)
-xxxx		Show hex-dump of the 4096-byte extended config space (root only)
-s [[[[<domain>]:]<bus>]:][<slot>][.[<func>]]	Show only devices in selected slots
-d [<vendor>]:[<device>]	Show only selected devices
-t		Show bus tree
-m		Produce machine-readable output
-i <file>	Use specified ID database instead of /usr/share/misc/pci.ids.gz
-D		Always show domain numbers
-M		Enable `bus mapping' mode (dangerous; root only)
-P <dir>	Use specified directory instead of /proc/bus/pci
-H <mode>	Use direct hardware access (<mode> = 1 or 2)
-F <file>	Read configuration data from given file
-G		Enable PCI access debugging
johanna@johanna-laptop:~$ 

APLAY -L:

johanna@johanna-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by phidia on 2008-07-03
Use the guide I provided the link for in my previous post. The fact that aplay -l found a card is good. You should be able to follow the guide to get sound working.

---

### Post by johannalb on 2008-07-04
I'm finding it really hard to understand the guide, I don't know what my actually card is, intel or analog, and when I click on the analog link it doesn't work :(

Also I don't have any internet working at the moment, so I don't know how I'd install it if I did find it ...

Thanks

Johanna

---

### Post by johannalb on 2008-07-06
Just bumping

---

