---
title: "My &quot;missing&quot; [?] nVidia GT 325M card"
date: 2010-03-01
forum: Hardware
---

### Post by angrykeyboarder on 2010-03-01
My brand spanking [new laptop]("http://j.mp/cWjiSd") comes with nVidia "[optimus]("http://www.nvidia.com/object/optimus_technology.html")" technology.

While I wasn't expecting Linux support (yet) I was expecting Ubuntu to recnogize my nVidia GeForce GT 325M card.

If I read the output of LSPCI correctly, it does not.  

EDIT: On my 32nd glance I did note some reference to nVidia somethingorother there. :)  But how do I know if Ubuntu is utilizing it (or the on-board Intel graphics)?

```
-+-[0000:3f]-+-00.0  Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers
 |           +-00.1  Intel Corporation Core Processor QuickPath Architecture System Address Decoder
 |           +-02.0  Intel Corporation Core Processor QPI Link 0
 |           +-02.1  Intel Corporation Core Processor QPI Physical 0
 |           +-02.2  Intel Corporation Core Processor Reserved
 |           \-02.3  Intel Corporation Core Processor Reserved
 \-[0000:00]-+-00.0  Intel Corporation Core Processor DRAM Controller
             +-01.0-[0000:01]----00.0  nVidia Corporation Device 0a35
             +-02.0  Intel Corporation Core Processor Integrated Graphics Controller
             +-16.0  Intel Corporation 5 Series/3400 Series Chipset HECI Controller
             +-1a.0  Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller
             +-1b.0  Intel Corporation 5 Series/3400 Series Chipset High Definition Audio
             +-1c.0-[0000:02]--
             +-1c.1-[0000:03]----00.0  Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express)
             +-1c.2-[0000:04-05]--
             +-1c.3-[0000:06]----00.0  NEC Corporation Device 0194
             +-1c.4-[0000:07]--
             +-1c.5-[0000:08]----00.0  Atheros Communications Device 1063
             +-1d.0  Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller
             +-1e.0-[0000:09]--
             +-1f.0  Intel Corporation Mobile 5 Series Chipset LPC Interface Controller
             +-1f.2  Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller
             +-1f.3  Intel Corporation 5 Series/3400 Series Chipset SMBus Controller
             \-1f.6  Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem

```

Any suggestions?

Thanks.

---

### Post by labinnsw on 2010-03-08
I think what you want to know is if Ubuntu is using the NVIDIA driver. If you have no other graphics card installed, then all your GUIs are using your graphics card.

To check if the NVIDIA driver is being used. Go to System >> Administration >> Hardware Drivers. If the driver is being used, you will see something like the attached.
[ATTACH]149378[/ATTACH]

[If it is not there, see post No. 79 here.]("http://ubuntuforums.org/showthread.php?p=8924129#post8924129")

---

### Post by gb5088 on 2010-04-13
I am interested in the exact same laptop (Asus N61JV) and wondered about Ubuntu compatibility. Evidently the nVidia card has this new Optimus feature that automatically switches between the nVidia card and the built-in Intel graphics, depending on whether it's needed and (I think) whether you're on battery power. This is complex and will take the Linux programmers awhile to figure out.

In the meantime, what happens is Ubuntu IGNORES the nVidia card and runs off the Intel graphics. I got this from a review in AnandTech (see  [http://www.anandtech.com/show/2962/asus-n61j-x2-optimus-gt325m-meets-arrandale](http://www.anandtech.com/show/2962/asus-n61j-x2-optimus-gt325m-meets-arrandale)). I think these guys are reliable but am open to people who may know more about this.

Here's what the AnandTech reviewer said in the comments section:

[INDENT][I]I did actually test what happens with Optimus laptops and Linux. Even using an older 9.04 installation of Ubuntu, everything works as expected... which is to say, you can run Linux but you won't get the Optimus GPU.
...
If you're one of the few people that want to run Linux and use a discrete GPU, then Optimus is definitely not going to make you happy. If all you want is to dual-boot Linux and you're okay with running it off the Intel IGP, you'll be fine.[/I]
[/INDENT]

I'm in the latter category (just want to dual-boot Linux and am happy with Intel graphics), so this is OK with me. Besides, I suspect that Linux programmers will figure it out and provide drivers for the GT 325M (and other Optimus video cards) before too long.

---

### Post by angrykeyboarder on 2010-10-03
> **labinnsw said:**
> 

[....If it is not there, see post No. 79 here.]("http://ubuntuforums.org/showthread.php?p=8924129#post8924129")

Yeah, whatever...

---

### Post by Pifilatakanemu on 2011-04-05
Is there any solution to this problem?  Thanks!

---

### Post by photodoc on 2011-05-23
OK, I think this will be a new variation of an old theme:
 
Machine - Alienware M15x running windows 7 64 bit, Ubuntu running in a VirtualBox. I'm doing this to run Freesurfer for MRI analysis. Initially it worked fine, but when I upgraded Ubuntu to the latest release, I lost all my high resolution display capability. I tried following all the online instructions for downloading and installing the latest NVIDIA linux drivers for the card in my machine, but when I did the installation informed me that it had failed to detect a GPU compatible with the driver it was attempting to install. This happened whether I tried to install the 32 or 64 bit driver - and now when I boot up I get an immediate "Ubuntu is running in low-graphics mode" error with 
 
(EE) NVIDIA: Failed to load the NVIDIA kernel module.
Please check your
(EE) NVIDIA: system's kernal log for additional error messages.
(EE) Failed to load module "nvidia" (module-specific error, 0)
(EE) No drivers available.
 
After which it will give me the option to boot up one time with a generic driver with a maximum resolution of 800x600. 
 
I have rebooted to the console login, removed the old xconfig files, sudo installed every NVIDIA linux driver version I could find, starting at 270 (the most recent release I think) and working backwards. It seems as far as Ubuntu is concerned, I'm not running an NVIDIA card at all. Any suggestions?

---

