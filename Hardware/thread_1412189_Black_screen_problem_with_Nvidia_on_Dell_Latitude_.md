---
title: "Black screen problem with Nvidia on Dell Latitude E6500"
date: 2010-02-20
forum: Hardware
---

### Post by ekortrightathome on 2010-02-20
I have a Dell Latitude E6500 on which I installed Ubuntu 9.10 recently.

After changing from the public domain display driver to the proprietary driver (nvidia-173), I could use visual effects and the Nvidia TwinView to enable dual monitors.  I was very happy with the way everything worked.

Then I had some problems with rdesktop (the laptop display went black, though the external one kept working), so I tried to upgrade to a later driver version (nvidia-185) and after that it's been a black screen every time I start X.  The only thing I can do is Ctrl-Alt-F1 out of GNOME or shut the machine down by pressing the power button.

I tried reinstalling/removing/purging the nvidia-185 driver with synaptic and/or aptitude, reenabling nvidia-173, all to no avail.  I've done this after stopping gdm, or from the recovery root shell using aptitude.  

The only way I don't get a black screen is if I install nvidia-173 again and set the driver to "vesa", or remove everything and set the display to "nv"  (in which case I can't use visual effects or the dual display).

I believe something got corrupted when installing the nvidia-185 driver, but purging and reinstalling does not seem to get rid of the problem and this has corrupted even the driver version that was definitely working before the rdesktop problem.

Is there any way I can force whatever got corrupted to be overwritten?  Or do I have to reinstall Ubuntu to get my computer back to the way it was?

---

### Post by j2010 on 2010-02-21
Could you post your Xorg.0.log file to check if an error could be detected ?

---

### Post by ekortrightathome on 2010-02-21
First of all, thanks for your reply.

After reinstalling nvidia-173, I ran nvidia-xconfig, which modified my xorg.conf to read:

[INDENT][COLOR=DarkGreen]Section "Screen"
    Identifier    "Default Screen"
    Device        "Default Device"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Default Device"
    Option    "NoLogo"    "True"
    Driver    "nvidia"
EndSection

[/COLOR][/INDENT][COLOR=Black]After restarting, the Xorg.0.log file reads as in the attached file (I copied it to [/COLOR][COLOR=Black]Xorg.0.log.txt[/COLOR][COLOR=Black] before changing back to "nv").  Can you see anything that points to the problem?

[/COLOR]

---

### Post by j2010 on 2010-02-22
Your monitor look to be not detected:
```

(II) NVIDIA(GPU-0): No display devices connected; falling back to: CRT-0
(WW) NVIDIA(GPU-0): Unable to read EDID for display device CRT-0
...
(WW) NVIDIA(0): Unable to get display device CRT-0's EDID; cannot compute DPI
(WW) NVIDIA(0):     from CRT-0's EDID.

```
And edid information could not be read. 
Some solutions to try:

[LIST]
[*]Manual monitor configuration in the xorg.conf
[*]get edid information by an other way (get-edid tool of other) and use it with Option "CustomEDID" "CTR-0:/etc/X11/crt-0.bin
[*] is there any bios configuration about using external monitor without internal (Your computer is a laptop is'nt it ?)
[/LIST]
This is way I think but it should have others...

---

### Post by ekortrightathome on 2010-02-22
Actually, it's worse than that.  The Xorg.0.log that I posted was without connecting the external monitor.  After connecting the external monitor, apparently X doesn't come up at all (although it's hard to tell) and I have to shut down the machine forcibly by holding the power button.  If you can, please see the new attachment.  This happens even with the Driver set to "nv".

I don't understand why the monitor(s) are not being recognized, when everything was working fine before trying to install the later driver.  Why would trying to install a new driver force me to configure the monitor manually when using the previous version?

---

### Post by j2010 on 2010-02-22
Your internal display look to be not detected. But you external display is well detected. So:
[LIST]
[*]Is your internal display work well in console mode (during boot) ?
[*]What's happend when you hit the magic key CRT/LCD you should have on your keyboard ? Is other screen start ?
[/LIST]

I don't know why it was working before and not after driver change but there was a bug on some nvidia driver wich corrupt EDID informations on some monitors. (Edid information are information stored on the monitor to let it announce his supported features/resolutions...). So try to extract those information and let us take a look (perhaps it's an other problem... but in case of...)

Try to extract all your edid info by using 'get-edid' tool and post it. If it's not working, extract directly using i2cdump with this step:
```

sudo modprobe i2c-dev
sudo i2cdump 0 0x50
sudo i2cdump 1 0x50
sudo i2cdump 2 0x50
sudo i2cdump 3 0x50

```

---

### Post by ekortrightathome on 2010-02-22
First, yes, the laptop monitor works fine during boot.  I get the first splash screen, but after that everything goes black.  I did not try the CRT/LCD key, but will do so and post my results.
 
I will also get the information you requested.  Thanks very much for your help.

---

### Post by RRF2525 on 2010-02-22
I've been fighting a similar issue with my desktop and I too believe that the NV driver is corrupting my installation.  I've been trying to install any of the appropriate NV restricted drivers and all result in a black screen then loss-of-signal to monitor during boot -- this forces me to kill power and restart the machine to console.

Assuming that your machine will POST and load grub -- boot to a console as root and rm xorg.conf altogether.  This will at least allow you to reboot to the GUI and try again.  I've been making a b/u of the xorg file as I go before deletion...

---

### Post by ekortrightathome on 2010-02-22
I had to install the read-edid package, but here is the result:[INDENT][COLOR=DarkGreen]$ sudo get-edid
get-edid: get-edid version 2.0.0

    Performing real mode VBE call
    Interrupt 0x10 ax=0x4f00 bx=0x0 cx=0x0
    Function supported
    Call successful

    VBE version 300
    VBE string at 0x2110 "NVIDIA"

VBE/DDC service about to be called
    Report DDC capabilities

    Performing real mode VBE call
    Interrupt 0x10 ax=0x4f15 bx=0x0 cx=0x0
    Function supported
    Call successful

    Monitor and video card combination does not support DDC1 transfers
    Monitor and video card combination does not support DDC2 transfers
    0 seconds per 128 byte EDID block transfer
    Screen is not blanked during DDC transfer

Reading next EDID block

VBE/DDC service about to be called
    Read EDID

    Performing real mode VBE call
    Interrupt 0x10 ax=0x4f15 bx=0x1 cx=0x0
    Function supported
    Call failed

The EDID data should not be trusted as the VBE call failed
Error: output block unchanged
[/COLOR][/INDENT]I assume this means the EDID data is bad.  Where is this information stored?  In the graphics card itself?

By the way, the CRT/LCD key does not seem to do anything.  Also, I could find no BIOS configuration for an external monitor.

---

### Post by j2010 on 2010-02-23
So try to extract with the i2cdump tools:
```

sudo modprobe i2c-dev
sudo i2cdump 0 0x50
sudo i2cdump 1 0x50
sudo i2cdump 2 0x50
sudo i2cdump 3 0x50

```
This will:
[LIST]
[*]load the i2c-dev module onto kernel to allow /dev/i2c* entries
[*]dump i2c data from each device (it should be the "2" the good)
[/LIST]
And post result for each i2cdump command.

---

### Post by Mayfairy on 2010-02-23
Not meaning to hijack the thread but I just googled with bad EDID and stumbled upon this thread. 
I executed the get-edid and got: 

The EDID data should not be trusted as the VBE call failed
Error: output block unchanged

Then did the i2cdump as instructed and the first (0 0x50) gave all 00's while the 1 and 2 gave XX's and 3 couldn't be found.

Was just wondering how to read this figures.

---

### Post by j2010 on 2010-02-23
try the ddccontrol command to take a look about monitor detection:
```

sudo ddccontrol -p

```
I don't known what mean no i2c data. Do you have a nvidia video card ?

---

### Post by Mayfairy on 2010-02-23
I do have a Geforce4 MX420 card and some integrated SiS card that's not in use. 
The ddccontrol said there's no ddc/ci supported monitors to be found.

---

### Post by j2010 on 2010-02-23
Have you made the 
```
sudo modprobe i2c-dev
```
before 
```
sudo ddccontrol -p
```
If not no i2c dev will be available and nothing will be detected...

---

### Post by Mayfairy on 2010-02-23
Right.. I had booted the machine in between. 

Now when using the both commands in a row the ddccontrol -p flipped a black screen and stayed that way. Soon the monitor informed me that Input Not Supported. 
That's the same message I'm getting when trying to boot up the normal way.

EDIT: Removing my xorg.conf and executing gdm after that brings up the login screen as it should, but then I'm back to 800x600 resolution. 

The whole story is that I had a working 8.04 system and I installed a 9.10 on a different partition and it booted up with 800x600 resolution. The restricted drivers (v96) are installed fine but the resolution is taken down to 640x480 with an option to change to 480x320. After fiddling around a bit I realized the drivers aren't to blame but the monitor that isn't detected properly. I plugged in my Samsung 226BW monitor and it was detected ok. Then changed the resolution to reflect the maximum of the old monitor (Acer AL1916) and plugged it in instead. 
I can log in via recovery shell and execute a 'startx' command there to get a working desktop, but whenever I try to boot up without recovery or do a 'gdm' instead of 'startx' I'm getting the black screen. 
I've tried setting the VertRefresh and HorizSync numbers by hand but it doesn't work. I've tried the ones the Acer says are the right ones for that monitor and the ones that are listed on my working 8.04 system as well as those gotten via 'cvt' command when giving it the maximum resolution of the monitor. None of them work.

EDIT: Good god it's done!
I'll just link the post I made on this other topic, It includes the steps I went through to get a working system. 
[http://ubuntuforums.org/showthread.php?p=8870750#post8870750](http://ubuntuforums.org/showthread.php?p=8870750#post8870750)

---

### Post by ekortrightathome on 2010-02-23
I installed package "i2c-tools", but did not get any results:
[COLOR=DarkGreen]
[/COLOR][INDENT][COLOR=DarkGreen]$ sudo modprobe i2c-dev
$ sudo i2cdump 0 0x50
No size specified (using byte-data access)
Error: Could not open file `/dev/i2c-0' or `/dev/i2c/0': No such file or directory
$ sudo i2cdump 1 0x50
No size specified (using byte-data access)
Error: Could not open file `/dev/i2c-1' or `/dev/i2c/1': No such file or directory
$ sudo i2cdump 2 0x50
No size specified (using byte-data access)
Error: Could not open file `/dev/i2c-2' or `/dev/i2c/2': No such file or directory
$ sudo i2cdump 3 0x50
No size specified (using byte-data access)
Error: Could not open file `/dev/i2c-3' or `/dev/i2c/3': No such file or directory
$ 
[/COLOR]
[/INDENT]I think I'm missing something.

---

### Post by j2010 on 2010-02-24
Is your nvidia kernel's module is loaded when do that ?

---

### Post by ekortrightathome on 2010-02-24
> **j2010 said:**
> Is your nvidia kernel's module is loaded when do that ?

Well, it's installed. . .

[INDENT][COLOR=DarkGreen]$ dpkg --get-selections | grep nvidia
nvidia-173-kernel-source            install
nvidia-173-modaliases                install
nvidia-glx-173                    install
nvidia-glx-173-dev                install
nvidia-settings                    install
[/COLOR][/INDENT][COLOR=Black]
But I'm not sure if that's what you mean.  Beyond that, how can I tell if the module is loaded?

By the way, I ran the hardware diagnostics on the laptop, and I get an error saying that the LCD CRT EDID could not be read.
[/COLOR]

---

### Post by j2010 on 2010-02-24
> **ekortrightathome said:**
> Well, it's installed. . .

[INDENT][COLOR=DarkGreen]$ dpkg --get-selections | grep nvidia
nvidia-173-kernel-source            install
nvidia-173-modaliases                install
nvidia-glx-173                    install
nvidia-glx-173-dev                install
nvidia-settings                    install
[/COLOR][/INDENT]

With this command you list installed nvidia drivers/modules. To get LOADED kernel module, use the command:
```
sudo lsmod
```
You will see modules loaded by the kernel. If nvidia isn't in the list, hit 
```
modprobe nvidia
``` to load it and redo other actions:
```

sudo modprobe i2c-dev
sudo i2cdump 0 0x50
[..]

```
Try too:
```

sudo ddccontrol -p

```

> 
[COLOR=Black]
But I'm not sure if that's what you mean.  Beyond that, how can I tell if the module is loaded?

By the way, I ran the hardware diagnostics on the laptop, and I get an error saying that the LCD CRT EDID could not be read.
[/COLOR]
Yes your xorg's log file tell the same. Perhaps there is a hardware problem on your monitor or perhaps it's only a checksum problem than you can correct...

---

### Post by ekortrightathome on 2010-02-24
Well, it seems to be loaded, but I still don't get any i2c devices:

[INDENT][COLOR=DarkGreen]$ lsmod | grep nvidia
nvidia               7089800  0 
agpgart                34988  2 nvidia,intel_agp
$ sudo modprobe i2c-dev
$ ls -d /dev/i*
/dev/input
$ sudo i2cdump 0 0x50
No size specified (using byte-data access)
Error: Could not open file `/dev/i2c-0' or `/dev/i2c/0': No such file or directory
$ sudo modprobe nvidia
$ lsmod | grep nvidia
nvidia               7089800  0 
agpgart                34988  2 nvidia,intel_agp
$ sudo modprobe i2c-dev
$ sudo i2cdump 0 0x50
No size specified (using byte-data access)
Error: Could not open file `/dev/i2c-0' or `/dev/i2c/0': No such file or directory
$ sudo ddcontrol -p
sudo: ddcontrol: command not found
[/COLOR]
[/INDENT]

---

### Post by j2010 on 2010-02-25
> **ekortrightathome said:**
> 
$ sudo ddcontrol -p
sudo: ddcontrol: command not found

Yes there is 2 "c" in ddccontrol... Any way if it's not working and with the error message you have on hardware diagnostic, I think that your hardware is out of order. Call the dell support if your laptop is already covered by the warranty... If you can't ask then to change broken parts, you have to workarround by making a manual monitor description onto your xorg.conf.

---

### Post by ekortrightathome on 2010-03-02
Well, I talked to Dell, and after a few tries (first they asked me to update the BIOS, then resintall the video driver, all to no effect), I finally got somebody who said I needed a new LCD kit.

Fortunately, the system is under maintenance and the technician came, swapped everything out, and voila everything works again.

So I guess it was all hardware failure.

Thanks very much, j2010, for your help with this.

---

