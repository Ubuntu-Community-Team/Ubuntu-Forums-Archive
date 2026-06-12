---
title: "Problems with HD 5870 driver installation"
date: 2012-10-29
forum: Hardware
---

### Post by makShot on 2012-10-29
Hi!

I installed Ubuntu 12.10 x64 on my desktop PC and now I have problems with my graphic card Radeon HD 5870.

I donwloaded the newest drive from the AMD site:  [http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English)

But I cannot install them because of the next error:

> Supported adapter detected.
Check if system has the tools required for installation.
fglrx installation requires that the system have kernel headers.  /lib/modules/3.5.0-17-generic/build/include/linux/version.h cannot be found on this system.
One or more tools required for installation cannot be found on the system. Install the required tools before installing the fglrx driver.
Optionally, run the installer with --force option to install without the tools.
Forcing install will disable AMD hardware acceleration and may make your system unstable. Not recommended.

Could someone please help me with the issue I have faced?

---

### Post by AVeryLongNickname on 2012-11-04
I have the same problem with my amd 6970's.. Did you find any solution?

(edit: I'm currently running 12.10, not 10.10 as my sig claims..)

---

### Post by J-HAX on 2012-11-05
Also having the problem with my HD6870. Just upgraded from 12.04 where I had catalyst control centre installed and working. Here is my full .log;
```
1. Supported adapter detected.
2. Check if system has the tools required for installation.
3. fglrx installation requires that the system have kernel headers.  /lib/modules/3.5.0-17-generic/build/include/linux/version.h cannot be found on this system.
4. One or more tools required for installation cannot be found on the system. Install the required tools before installing the fglrx driver.
5. Optionally, run the installer with --force option to install without the tools.
6. Forcing install will disable AMD hardware acceleration and may make your system unstable. Not recommended.
```Thanks for any help!
Cheers, Jack

---

### Post by shouthouse on 2012-11-09
I'm having this same issue with a Radeon HD 7850, exact same message and everything. I was able to get it to work earlier, however I am new and I keep screwing everything up.

Trying to install 12.11 catalyst on 12.10 ubuntu. Frustrating.
EDIT: Yes I have the headers installed.

EDIT: I have also tried what is on this page. [http://askubuntu.com/questions/159586/how-to-install-radeon-open-source-driver]("http://askubuntu.com/questions/159586/how-to-install-radeon-open-source-driver")


> Supported adapter detected.
Check if system has the tools required for installation.
fglrx installation requires that the system have kernel headers.  /lib/modules/3.5.0-17-generic/build/include/linux/version.h cannot be found on this system.
One or more tools required for installation cannot be found on the system. Install the required tools before installing the fglrx driver.
Optionally, run the installer with --force option to install without the tools.
Forcing install will disable AMD hardware acceleration and may make your system unstable. Not recommended.

---

### Post by shouthouse on 2012-11-09
Ok figured out what was going on. The install needs specific headers. So type this in and then you can install.

```
sudo apt-get install linux-headers-3.5.0-17-generic
```

But now I am having problems running that initial configuration... ala [http://osadvices.com/how-to-install-amd-catalyst-12-11-beta-driver-on-ubuntulinux-mint/]("http://osadvices.com/how-to-install-amd-catalyst-12-11-beta-driver-on-ubuntulinux-mint/")

Every time I reset into ubuntu from that i get the error message > The System is running in low-graphics mode 

Your screen, graphics card, and input device settings could not be detected correctly. You will need to configure these yourself.

---

### Post by QIII on 2012-11-09
AMD now officially wants you to use amdconfig rather than aticonfig.

Also, are you putting two dashes before "initial"?

---

### Post by shouthouse on 2012-11-09
Are you supposed to run the command before rebooting? It prompts for reboot but I don't know if I should.

Also, initial? In which line? I've ran so many tonight.

---

### Post by QIII on 2012-11-09
After you install the driver and before rebooting, 
```
sudo amdconfig --initial
```

But if you can get to your desktop at all, you can run the command at any time and then reboot.

---

### Post by shouthouse on 2012-11-09
Well since I am far too incredibly impatient for my own good, I have a whole new install up and running. I will report back!

I have read this can be a problem with having an intel motherboard and an amd gpu. IS this correct?

---

### Post by QIII on 2012-11-09
That's not a problem, unless your CPU/board has Intel graphics, and then you are in for some work.

---

### Post by shouthouse on 2012-11-09
I believe that my board has integrated 4000

I guess it would be smart to post my hardware.


Asrock Z77 Pro4-m
Intel i5 3570k
Radeon HD 7850


EDIT: GOING TO START MY OWN POST FOR MY SPECIFIC PROBLEM

---

### Post by Deadly Eyez on 2013-03-23
Hello. 
I have the same problem trying to install my AMD Radeon HD 3400 GPU.
Any solution?

Thanks.

---

### Post by ManamiVixen on 2013-03-23
[**[COLOR=#000000]Deadly Eyez[/COLOR]**]("http://ubuntuforums.org/member.php?u=364450") the HD 2XXX-4XXX are no longer compatible with Ubuntu 12.04 and onwards. Sorry.

---

### Post by Deadly Eyez on 2013-03-23
Eh, Too bad. 
My laptop keeps over heating so I asked around and people told me I have to install the GPU driver because the CPU is trying to proccess instead of the graphics card but its less effective so it over heats.

---

### Post by Raklodder on 2013-03-24
Could this be what you're looking for: "**21.10.12:** **fglrx is not working in 12.10, see bug report**" and "**04.01.13:** **no fix yet, bug reports are on fire**": [http://askubuntu.com/questions/78906/ati-amd-proprietary-fglrx-graphics-install-fails-how-can-i-resolve-the-problem](http://askubuntu.com/questions/78906/ati-amd-proprietary-fglrx-graphics-install-fails-how-can-i-resolve-the-problem)

---

