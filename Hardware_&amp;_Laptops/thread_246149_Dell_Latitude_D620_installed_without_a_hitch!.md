---
title: "Dell Latitude D620 installed without a hitch!"
date: 2006-08-28
forum: Hardware &amp; Laptops
---

### Post by spiral777 on 2006-08-28
This morning my new D620 showed up at my house, and I happily installed Ubuntu on it.
 
I first loaded up the Live CD and walked thru setting up wireless on it, just to make sure it could see everything. No problems there, just had to google once to figure out how to give it a SSID number thru the terminal. It worked just fine.
 
Satisfied with that, I popped out the Live CD, loaded up the Alternate install CD and wiped out all the old Dell partitions. I set it up for a 20gb main partition, a 78 gb home partition, and a 2gb swap. Installation went on without a hitch, and as soon as I had it up and running, I upgraded the kernal to the 686-SMP and installed all my updates.
 
At this moment everything appears to be working without a hitch. Wireless is up, suspend and hibernate work without problems, closing the lid powers down the LCD, all the USB ports work, screen width was correctly identified (Although it did originally see it as 1280x800, it was easy to set it to 1440x900).
 
Is there anything else I can check to see whether everything is working?

---

### Post by chaag on 2006-08-30
How did you get wireless working?

I have tried bcm43xx-fwcutter and ndiswrapper with no success.

Currently, I have ndiswrapper loaded and happy:
chaag@chaag-laptop1:/etc/ndiswrapper$ ndiswrapper -l
Installed ndis drivers:
bcmwl5          driver present, hardware present

But dmesg shows that the kernel does not like the driver:
[17179592.612000] ndiswrapper version 1.8 loaded (preempt=yes,smp=no)
[17179592.704000] ndiswrapper (import:239): unknown symbol: ntoskrnl.exe:'strrchr'
[17179592.704000] ndiswrapper (import:239): unknown symbol: ntoskrnl.exe:'MmFreeContiguousMemorySpecifyCache'
[17179592.704000] ndiswrapper (import:239): unknown symbol: ntoskrnl.exe:'MmAllocateContiguousMemorySpecifyCache'
[17179592.704000] ndiswrapper (import:239): unknown symbol: ntoskrnl.exe:'MmGetPhysicalAddress'
[17179592.704000] ndiswrapper (load_sys_files:218): couldn't prepare driver 'bcmwl5'
[17179592.704000] ndiswrapper (load_wrap_driver:112): loadndiswrapper failed (65280); check system log for messages from 'loadndisdriver'


thanks:

---

### Post by Exclamation on 2006-09-01
I have the same problem and need to get it working before sunday because im leaving for school. hp dv2020ca. broadcom 4311. tried ndiswrapper + bcm413xx.

ndiswrapper error:
[  457.538859] ndiswrapper version 1.8 loaded (preempt=yes,smp=yes)
[  457.544145] ndiswrapper (import:239): unknown symbol: ntoskrnl.exe:'strrchr'
[  457.544169] ndiswrapper (import:239): unknown symbol: ntoskrnl.exe:'MmFreeContiguousMemorySpecifyCache'
[  457.544176] ndiswrapper (import:239): unknown symbol: ntoskrnl.exe:'MmAllocateContiguousMemorySpecifyCache'
[  457.544182] ndiswrapper (import:239): unknown symbol: ntoskrnl.exe:'MmGetPhysicalAddress'
[  457.544287] ndiswrapper (load_sys_files:218): couldn't prepare driver 'bcmwl5'
[  457.544763] ndiswrapper (load_wrap_driver:112): loadndiswrapper failed (65280); check system log for messages from 'loadndisdriver'


great distro and community here btw. im sure someone has the answer.

---

### Post by spiral777 on 2006-09-01
I have the Intel 3945 and it just worked without a hitch out of the box. I did use the alternate install CD, so I don't knkow if that made a difference, but it connected right away without me having to do anything other than put in the SSID.

---

### Post by chaag on 2006-09-01
> **Exclamation said:**
> I have the same problem and need to get it working before sunday because im leaving for school. hp dv2020ca. broadcom 4311. tried ndiswrapper + bcm413xx.

ndiswrapper error:
[  457.538859] ndiswrapper version 1.8 loaded (preempt=yes,smp=yes)
[  457.544145] ndiswrapper (import:239): unknown symbol: ntoskrnl.exe:'strrchr'
[  457.544169] ndiswrapper (import:239): unknown symbol: ntoskrnl.exe:'MmFreeContiguousMemorySpecifyCache'
[  457.544176] ndiswrapper (import:239): unknown symbol: ntoskrnl.exe:'MmAllocateContiguousMemorySpecifyCache'
[  457.544182] ndiswrapper (import:239): unknown symbol: ntoskrnl.exe:'MmGetPhysicalAddress'
[  457.544287] ndiswrapper (load_sys_files:218): couldn't prepare driver 'bcmwl5'
[  457.544763] ndiswrapper (load_wrap_driver:112): loadndiswrapper failed (65280); check system log for messages from 'loadndisdriver'


great distro and community here btw. im sure someone has the answer.

I had to install ndiswrapper form source.

Here are the instructions:
[Compiling the latest version of ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#head-c1ebf95637d110c5f01b9a1383d137f79d8cbddb")

Works great for me now. Actually it seems better than the wireless on my old D600

---

### Post by marteinn on 2006-09-01
What kind of a video card do you have.  I installing to D620 as well and Im having problems with it.

Mybe there is now how lacking.

regards
Marteinn

---

### Post by Exclamation on 2006-09-01
Thanks chaag, trying it out now.

---

### Post by Exclamation on 2006-09-01
ok, got a bit further,

[ 1087.189658] ndiswrapper version 1.23 loaded (preempt=yes,smp=yes)
[ 1087.196309] ndiswrapper (check_nt_hdr:149): kernel is 64-bit, but Windows driver is not 64-bit;bad magic: 010B
[ 1087.196319] ndiswrapper (load_sys_files:214): couldn't prepare driver 'bcmwl5'
[ 1087.196864] ndiswrapper (load_wrap_driver:113): loadndiswrapper failed (65280); check system log for messages from 'loadndisdriver'

---

### Post by Exclamation on 2006-09-01
ok, so basicly now all i need is a 64 bit driver for the 4311 broadcom.
Ive been looking all over and cant find one.
Hopefully someone in the forums will know...

---

### Post by reedatschool on 2006-09-01
I installed the 64 bit drivers without a hitch for the Broadcom 4311 by going to the existing windows installation and copying the driver from the programs files/broadcom directory.  Copy them into a directory in Uubntu and run Ndiswrapper to install.  I am running a Presario V3018CL which is slightly different, but I would imagine the drivers are probably the same. 

To be honest though you may want to stick with the 32 bit until Edgy comes out.  There are some issues like getting flash to work in 64 bit that can really ruin the whole experience.

Reed Harding

---

### Post by tallguy240 on 2007-05-10
Could you tell me how you got the resolution set to 1440x900? The display manger only allows me to set to 1200x800 but when I look at my xorg.conf file the 1440x900 resolution settings are there.

Thanks 
Tallguy240

---

### Post by chaag on 2007-05-10
I think it had to do with DefaultDepth, but honestly, I don't recall. Here is the relevant section of my xorg.conf. 

Note: using the nvidia driver was not required for the higher resolution

Section "Screen"

        #DefaultDepth   16
        #DefaultDepth   32
    Identifier     "External Screen"
    Device         "NVIDIA Corporation NVIDIA Default Card"
    Monitor        "External Monitor"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       1
        Modes      "1440x900"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1440x900"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1440x900"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1440x900"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1440x900"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1440x900"
    EndSubSection
    SubSection     "Display"
        Depth       32
        Modes      "1440x900"
    EndSubSection
EndSection

---

