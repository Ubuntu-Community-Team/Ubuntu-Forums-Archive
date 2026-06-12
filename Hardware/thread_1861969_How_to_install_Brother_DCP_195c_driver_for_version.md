---
title: "How to install Brother DCP 195c driver for version 11.04"
date: 2011-10-16
forum: Hardware
---

### Post by Ken.B on 2011-10-16
Hi, can anyone give me a step by step instruction on how to install the driver?

---

### Post by roger_1960 on 2011-10-16
Hi

Have you looked here.

[http://solutions.brother.com/](http://solutions.brother.com/)

Their instructions have always worked for me.  Do forget to look at the "before you install" link and do the "pre required procedures" as necessary.

Roger

---

### Post by mörgæs on 2011-10-16
The command is

```
sudo apt-get install brother-lpr-drivers-bh7 brother-cups-wrapper-bh7
```

---

### Post by roger_1960 on 2011-10-16
Thanks for that -didn't know installers existed as a package  - even easier.

---

### Post by Ken.B on 2011-10-16
> **mörgæs said:**
> The command is

```
sudo apt-get install brother-lpr-drivers-bh7 brother-cups-wrapper-bh7
```

Hi, I've followed your code but it still can't detect my printer even after I reboot? Can you tell me what should I do next please?

> Hi

Have you looked here.

[http://solutions.brother.com/](http://solutions.brother.com/)

Their instructions have always worked for me.  Do forget to look at the  "before you install" link and do the "pre required procedures" as  necessary.

Roger

May I know which pre-required procedure should I choose?

I'm currently using HP MINI; 32-bit architecture; and Ubuntu 11.04.


Thanks a lot for your help!

---

### Post by mörgæs on 2011-10-16
What happens if you open 
[http://localhost:631/printers](http://localhost:631/printers)
in a browser?

---

### Post by Ken.B on 2011-10-16
> **mörgæs said:**
> What happens if you open 
[http://localhost:631/printers](http://localhost:631/printers)
in a browser?

It says "no printer".

---

### Post by mörgæs on 2011-10-17
Also after a reboot? You might need to run

```
sudo aa-complain /usr/sbin/cupsd
```

as well.

---

### Post by roger_1960 on 2011-10-17
Hi

I believe you have to do this:

Ubuntu 9.10, 10.04, 10.10, 11.4, 11.10
    1. Open "/lib/udev/rules.d/40-libsane.rules" file.
    2.Add the following two lines to the end of the device list. (Before the line "# The following rule will disable ..."):


    The lines to be added--------------------------- 


    # Brother scanners
    ATTRS{idVendor}=="04f9", ENV{libsane_matched}="yes"
     

    3. Restart the OS. 

Suggest you use > sudo gedit /lib/udev/rules.d/40-libsane.rules
to open file for editing.

This is taken from the Brother website - scanner settings for normal user.  I could not get my device (printer or scanner) recognised without this.  Also I think you need pre required procedures nos 8 and 12.

Hope it helps.  Sorry for the delay.

Roger

---

### Post by Ken.B on 2011-10-21
Thank you Roger and mörgæs for your reply, 

Can I find **sane-utils and psutils (requirement) **from the Ubuntu Software Centre?

After I installed sane-utils and psutils, do I still have to get **brscan, brscan2, brscan3 and PT-9500PC driver (related products / drivers)**?

Thank you for your advice

> 
Pre-required Procedure (8)
**Related distributions**Debian, Ubuntu[B]
Related products/drivers[/B]brscan, brscan2, brscan3[B]
Requirement[/B]**sane-utils** is required to be installed.

Pre-required Procedure (12)
**Related distributions**Distributions that does not have "psutils" by default[B]
Related products/drivers[/B]PT-9500PC driver[B]
Requirement[/B]**"psutils"** is required to be installed.

---

### Post by mörgæs on 2011-10-21
I would recommend that you use Synaptic for this. Gives a much better overview than Software Centre of what is installed and what is available.

---

### Post by Ken.B on 2011-10-23
Extract from the file

> ATTRS{idVendor}=="413c", ATTRS{idProduct}=="5250", ENV{libsane_matched}="yes"
[B]# Brother scanners
ATTRS{idVendor}=="04f9", ENV{libsane_matched}="yes"[/B]

# The following rule will disable USB autosuspend for the device
ENV{libsane_matched}=="yes", RUN+="/bin/sh -c 'if test -e /sys/$env{DEVPATH}/power/control; then echo on > /sys/$env{DEVPATH}/power/control; elif test -e /sys/$env{DEVPATH}/power/level; then echo on > /sys/$env{DEVPATH}/power/level; fi'"Did I did it correctly?

I've installed sane-utils and psutils and even restarted the notebook after putting in the bold part but it still can't locate my printer

---

