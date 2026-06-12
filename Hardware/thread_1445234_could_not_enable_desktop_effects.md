---
title: "could not enable desktop effects"
date: 2010-04-02
forum: Hardware
---

### Post by asif_1088119 on 2010-04-02
i have intel dg41rq motherboard and using 9.04 jaunty.i am not a complete newbie.

i am facing a bit difficulty to activate visual effects.

you can have a look at this...

[COLOR="DarkRed"]Gathering information about your system...

 Distribution:          Ubuntu 9.04
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
 Driver in use:         intel
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [FAIL]

There has been (at least) one error detected with your setup:
 Error: Software Rasterizer in use [/COLOR]

     

 [COLOR="rgb(139, 0, 0)"][COLOR="Green"]*-display UNCLAIMED     
       description: VGA compatible controller
       product: 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm bus_master cap_list
       configuration: latency=0[/COLOR][/COLOR]


COLOR="Indigo"]Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1366x768) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: present. 
Software rasterizer detected, abortingaborting and using fallback: /usr/bin/metacity[/COLOR]

---

### Post by asif_1088119 on 2010-04-05
anyone can help?

---

### Post by asif_1088119 on 2010-04-06
anyone?

---

### Post by asif_1088119 on 2010-04-08
Bump

---

### Post by lidex on 2010-04-08
Are you using an external monitor now or previously?

---

### Post by asif_1088119 on 2010-04-08
i hav only one connection of my monitor with my cpu..the other connection goes directly to power...my monitor is hp 1859 18.5" lcd...thats all i know...btw..thnx for reply

---

### Post by DrMelon on 2010-04-08
Intel Integrated Graphics cards often have poor performance.

---

### Post by asif_1088119 on 2010-04-08
what to do now?

---

### Post by stilling on 2010-04-08
maybe if you add your username to video group will help

sudo usermod -a -G video USERNAME

or

gpasswd -a user video


hope this helps

---

### Post by asif_1088119 on 2010-04-08
what does it do@stilling
can u please explain it??

---

### Post by stilling on 2010-04-08
it adds your username in video group that is all just try reboot and try again

---

### Post by asif_1088119 on 2010-04-11
bump
any specific solution???

---

### Post by asif_1088119 on 2010-04-11
i found a solution.i need to update my driver.intel came up with their latest release under name "Intel 2010Q1 graphics package" which includes xf86-video-intel 2.11.0 release.i would like to know how to get deb of that driver.they are providing source git tree.but i m not expert enough to compile that.

---

### Post by lidex on 2010-04-11
You might try this:
[http://www.webupd8.org/2009/05/graphic-video-drivers-ubuntu-repository.html]("http://www.webupd8.org/2009/05/graphic-video-drivers-ubuntu-repository.html")

---

