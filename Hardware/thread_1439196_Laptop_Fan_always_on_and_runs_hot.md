---
title: "Laptop Fan always on and runs hot"
date: 2010-03-25
forum: Hardware
---

### Post by JoaoMachado on 2010-03-25
I have an HP G60 with a Core 2 processor.

When the laptop is cold the fan is on very low and as the laptop is run for about an hour not even doing anything just sitting there, it starts to get hot on the palm rest and the fan speed starts to increase and never decreases.

I installed CPU scaling and that is working fine, usually running at 1.2GHz.

I have lm_sensors installed, coretemp module is loading but there is no reference to coretemp in /etc/sensors3.conf. 

Sensors output:
> joao@HP-G60:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +56.0°C  (crit = +103.0°C)                  
temp2:       +56.0°C  (crit = +120.0°C)                  

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +52.0°C  (high = +105.0°C, crit = +105.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +52.0°C  (high = +105.0°C, crit = +105.0°C)

This laptop runs so perfect, this is the only thing keeping me from never going back to Windoze!


Ubuntu Lucid Lynx

---

### Post by stringtheorem on 2010-03-25
This could well be a build up of dust. I had a similar problem with my old Fujitsu laptop. I cleaned up the fans and afterwards it was running at great low temps.

Another thought, has your laptop lost the rubber bungs at the bottom; if so, the chassis may be sitting on the desk top blocking the fans. Try propping it up on a couple of books to test it out.

---

### Post by RedSingularity on 2010-03-25
Have you installed the proper graphics drivers?  Not doing so can cause the fan to run at high speeds.

---

### Post by JoaoMachado on 2010-03-26
@ stringtheorem, not dust, in Win7 it is perfectly quiet.

@ RedSingularity, looks like I am using the intel driver.

lsmod:
> 
led_class               2864  1 ath5k
soundcore               6620  1 snd
intel_agp              24181  1 
i2c_algo_bit            5028  1 i915
agpgart                31724  2 drm,intel_agp
snd_page_alloc          7172  2 snd_hda_intel,snd_pcm
coretemp                4289  0 
video                  17375  1 i915
output                  1871  1 video
lp                      7028  0 
parport                32635  2 ppdev,lp
usb_storage            39425  0 
ahci                   31912  2 
r8169                  34172  0 
mii                     4381  1 r8169


---

### Post by sarahcollin on 2010-03-26
> **stringtheorem said:**
> This could well be a build up of dust. I had a similar problem with my old Fujitsu laptop. I cleaned up the fans and afterwards it was running at great low temps.

Another thought, has your laptop lost the rubber bungs at the bottom; if so, the chassis may be sitting on the desk top blocking the fans. Try propping it up on a couple of books to test it out.
yes try it it might help

---

### Post by RedSingularity on 2010-03-26
What is the output of 

lspci | grep VGA

---

### Post by JoaoMachado on 2010-04-05
> **RedSingularity said:**
> What is the output of 

lspci | grep VGA

Here is my output.

> joao@HP-G60:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
joao@HP-G60:~$ 


---

### Post by RedSingularity on 2010-04-05
And what does your xorg file look like?

---

### Post by JoaoMachado on 2010-04-05
Well, I don't have an xorg.conf only a xorg.conf.failsafe.
/etc/X11/
> **there are these files:**

app-defaults <folder>
cursors <folder>
fonts <folder>
xinit <folder>
xkb <folder>
Xresources <folder>
Xsession.d <folder>
default-display-manager
rgb.txt
X
xorg.conf.failsafe
Xsession
Xwrapper.conf

Did Lucid Lynx change the location of the file?

---

### Post by RedSingularity on 2010-04-05
Try using this command and then check for the file again.

sudo dpkg-reconfigure xserver-xorg

---

### Post by JoaoMachado on 2010-04-06
> **RedSingularity said:**
> Try using this command and then check for the file again.

sudo dpkg-reconfigure xserver-xorg

The command did not return any errors, but it also didn't seem like it did anything, just returned back to the prompt really quickly and there is still no xorg.conf file in /etc/X11/

John

---

### Post by RedSingularity on 2010-04-06
How about this command?

sudo Xorg -configure

---

### Post by RedSingularity on 2010-04-06
And if that doesnt work visit [this](http://www.osguides.net/operation-systems/217-how-to-create-xorgconf-in-ubuntu-910.html) webpage and follow the instructions.

---

### Post by JoaoMachado on 2010-04-10
Well, I decided to try out Fedora 12 live cd...lo and behold it runs at normal temps even on the CD. 

So I decided to reinstall Ubuntu Lucid Lynx from scratch ( I was running from one of the first Alpha releases) and ran through all of the updates and now no excessive heat is gone and everything works nice!

Joao

:guitar::)

---

### Post by RedSingularity on 2010-04-10
Interesting.  I guess it was a problem with the Alpha package you were using.

---

