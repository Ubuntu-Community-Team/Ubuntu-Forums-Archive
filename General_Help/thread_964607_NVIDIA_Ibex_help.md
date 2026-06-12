---
title: "NVIDIA Ibex help"
date: 2008-10-31
forum: General Help
---

### Post by VengefulIce on 2008-10-31
Hi,

I know that there are many questions about the new NVIDIA drivers with intrepid ibex, but i have not found any that are a step by step process.

I have a NVIDIA GeForce FX 5200, Driver version 173

When i boot, it boots saying that it is in low graphics mode and prompts me to select reconfigure or keep low graphics.  There are various appearance bugs following the low graphics.

Does anyone have a Step-by-step process in which to fix this problem?

Thanks

---

### Post by Laibcoms on 2008-10-31
Try this, but instead of 177, get your 173.

re-quoting myself:
> 
I am not sure if this will work, but I had a problem like yours that 177 won't activate.

So I did:
1) Open Synaptic Package Manager
2) Search nvidia
3) Installed all the 177 that are not yet installed (except those with the -dev suffix)
4) Made sure nvidia-settins is installed as well
5) Restarted
6) Went to "Hardware Drivers"
7) Activated 177
8) Voila

Hope that helps.


Then

> 
gksudo nvidia-settings


---

### Post by TeXtonyx on 2008-10-31
From the 8.10 Release Notes:

nVidia "legacy" video support

The 71 and 96 series of proprietary nVidia drivers, as provided by the nvidia-glx-legacy and nvidia-glx packages in Ubuntu 8.04 LTS, are not compatible with the X.Org included in Ubuntu 8.10. Users with the nVidia TNT, TNT2, TNT Ultra, GeForce, GeForce2, GeForce3, and GeForce4 chipsets are affected and will be transitioned on upgrade to the free nv driver instead. This driver does not support 3D acceleration.

Users of other nVidia chipsets that are supported by the 173 or 177 driver series will be transitioned to the nvidia-glx-173 or nvidia-glx-177 package instead. However, unlike drivers 96 and 71, drivers 173 and 177 are only compatible with CPUs that support SSE (e.g. Intel Pentium III, AMD Athlon XP or higher). Systems with older CPUs will also be transitioned to the nv driver on upgrade. 

SSE = Athlon XP processor or newer and I think Pentium III
check your motherboard manual if in doubt. Also there are a 
lot of Howtos written for the Nvidia driver and particular
Nvidia cards which you can find in the Ubuntu Search window.

---

### Post by VengefulIce on 2008-10-31
The method described above doesn't quite work.  When i start NVIDIA Settings, it says that it appears i am not using the NVIDIA driver even though my Hardware Drivers Clearly states that the NVIDIA driver is activated and currently in use.

Any other suggestions?

I really need this issue fixed because it is impacting my system to the point where it is unusable

---

### Post by VengefulIce on 2008-10-31
After doing some research, I found a beta legacy NVIDIA Driver, via [http://www.nvnews.net/vbulletin/showthread.php?t=122139](http://www.nvnews.net/vbulletin/showthread.php?t=122139)


The problem is, I try to install it, and there are errors trying to install.
After closing the X Server and running the package, it shows


UPDATE: it shows 

No precompiled kernel interface was found to match your kernel, would you like the installer to attempt to download a kernel interface for your kernel from the NVIDIA ftp site ([ftp://download.nvidia.com](ftp://download.nvidia.com))

Yes

No matching precompiled kernel interface was found on the NVIDIA ftp site; this means that the installer will need to compile a kernel interface for your kernel.

OK

The CC version check failed:
The compiler used to compile the kernel (gcc 4.2) does not exactly match the current compiler (gcc 4.3).  The linux 2.6 kernel module loader rejects kernel modules built with a version of gcc that does not exactly match that of the compiler used to build it.  If you know what you are doing, click no.  Otherwise, select yes to abort installation, set the CC environment variable to the name of the compiler used to compile your kernel and restart installation.

---

### Post by Buschbarber on 2008-10-31
I have an HP Media Center PC, 3Ghz P4, 2Gb ram, Nvidia Gforce 6200 OC, and WinTV HVR1600.

I am running Ubuntu Ultimate 1.9 and using the Restricted Nvidia drivers v173, without any problems.

I installed Ubuntu 8.10 Desktop, on another HD. It booted up fine with the Default video drivers, but when I installed the Restricted v173 video drivers, it only boots up to a text based Login.

How can I reinstall the default drivers, again, without reinstalling the entire OS? There is no choice, in the Grub menu, for a Low Video boot.

---

### Post by VengefulIce on 2008-11-01
bump

---

### Post by Buschbarber on 2008-11-01
What does "bump" mean?

---

### Post by dagrump on 2008-11-01
buschbarber if you go ahead & log in, then try sudo apt-get -remove nvidia-glx-*, that should get rid of the nvidia driver. Reboot & you should be back to a GUI.
I'm not sure why your stuff isn't working, the machine I have issues with have dual video cards with a SLI bridge. No issues with single card boxes.

---

### Post by Buschbarber on 2008-11-01
Thanks!! I am not too good with the Command Line syntax, yet. I do not have another PC. I had a 2Ghz Celeron with an Nvidia Gforce 5200 and I had no problems with Ubuntu or Mandriva. My son has it now.

On my PC, Ubuntu Ultimate 1.9 and Ubuntu 8.04 each recognized my Nvidia card and although, it would not boot with the PC BIOS video default set to PCI, if I set it to Onboard, it would boot and switch to the Nvidia driver during the boot. 

I have to use a monitor connected to the Onboard adapter to see the Grub menu and a monitor connected to the Nvidia card to see everything else.

8.10 will not recognize my Nvidia 6200 at all so I cannot use any of the Nvidia drivers.

---

### Post by Gingaro on 2008-11-03
> **VengefulIce said:**
> Hi,

I know that there are many questions about the new NVIDIA drivers with intrepid ibex, but i have not found any that are a step by step process.

I have a NVIDIA GeForce FX 5200, Driver version 173

When i boot, it boots saying that it is in low graphics mode and prompts me to select reconfigure or keep low graphics.  There are various appearance bugs following the low graphics.

Does anyone have a Step-by-step process in which to fix this problem?

Thanks

Yes i have a step by step process..

i had the same problem and after a quick five minutes process....twas fixed. it seems that my gutsy kernel headers were getting loaded instead of my ibex ones. strange. this means that upon boot, the wrong config for the comp is loaded (i think.....it means things dont work anyway). heres how i fixed it.

i tried using envy to get my nvidia drivers working but it told me that my kernel headers were missing. bummer... so go to the synaptics package manager and search for: 

"linux-headers-2.6.27-7" 
"linux-headers-2.6.27-7-generic"
"linux-headers-generic"

and make sure that they are all installed. if they arent, install them.

next, open your terminal and type the following:
> 
sudo gedit /boot/grub/menu.lst

the text editor should open and you should be viewing the menu.lst file. at the bottom, you should see something similar to the following:

> title		*Ubuntu 8.10*, kernel **2.6.27-7-generic**
root		(hd0,0)
kernel		/boot/vmlinuz-**2.6.27-7**-generic root=UUID=403a94e4-11cd-4c27-824e-dc7ae01aab2e ro quiet splash
initrd		/boot/initrd.img-**2.6.27-7**-generic
quiet

title		*Ubuntu 8.10*, **2.6.27-7**-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-**2.6.27-7**-generic root=UUID=403a94e4-11cd-4c27-824e-dc7ae01aab2e ro single
initrd		/boot/initrd.img-**2.6.27-7**-generic

title		*Ubuntu 8.10*, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

anywhere there is mention of 2.x.xx-x-x (as in bold in the example above) then change it to 2.6.27-7

also change any mention of "Ubuntu 8.xx" to Ubuntu 8.10 (as in italics in above example.

once thats done, save and close. reset your comp... upon the gui boot....hopefully that horrible error message will have disappeared and you should have the chance to install the nvidia restricted drivers.

once thats done....reboot et voila....nice shiny graphics!:guitar:

thats what worked for me....hope it works for you!

---

### Post by VengefulIce on 2008-11-03
Hi,

I tried changing the headers, but the moment i do that and restart, the splash screen doesnt show, it is all text based.  I would prefer to have the Splash Screen show.  Is there a fix for this?

Also, I am just going to wait for the actual driver to be released, no messing around with beta drivers, but i am wondering if the driver will show up in the repositories or if i need to add any repos.

---

### Post by Gingaro on 2008-11-04
did you try updating your linux kernel to 2.6.27-7 through synaptics as well?

when you say its all text based....does it just boot to the command line?:confused: If so, type "startx" without the quotes. You could also try CTRL+ALT+backspace...that might work.

---

### Post by DouglasAWh on 2008-11-07
> **Gingaro said:**
> the text editor should open and you should be viewing the menu.lst file. at the bottom, you should see something similar to the following:

anywhere there is mention of 2.x.xx-x-x (as in bold in the example above) then change it to 2.6.27-7

also change any mention of "Ubuntu 8.xx" to Ubuntu 8.10 (as in italics in above example.

once thats done, save and close. reset your comp... upon the gui boot....hopefully that horrible error message will have disappeared and you should have the chance to install the nvidia restricted drivers.

once thats done....reboot et voila....nice shiny graphics!:guitar:

thats what worked for me....hope it works for you!

If you have multiple kernels installed, why would you change the name of them in menu.lst?  Some of my kernels are on entirely different partitions and shouldn't be interfering.

---

