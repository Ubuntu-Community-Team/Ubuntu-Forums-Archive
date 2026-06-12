---
title: "Acer Timeline 4810TG on Jaunty - ATI Driver"
date: 2009-08-17
forum: Installation &amp; Upgrades
---

### Post by anandharaj on 2009-08-17
Hi,

========================================
Laptop Model: Acel Timeline 4810TG
BIOS version: 1.23
CPU: Intel Core 2 Duo SU9400
Graphic: Intel and ATI Radeon HD4330
OS: Ubuntu Jaunty 32bit
========================================


Does anyone successfuly install the ATI driver on Acer Timeline 4810TG? Today i notice that my graphic driver that active is Intel not ATI. Then i decided to install the ATI driver from System -> Administration -> Hardware Driver. Upon reboot, there is no display - looks like the system is hang. Then install the driver from ATI/AMD website - also same thing happen, no display. Based on Xorg log (attached), it seems like related to BIOS. Then i change the "Switchable graphic" from "Switchable" to "Discrete". This changes make the system boot as normal. Looks like its working perfectly until i discover some wired color problem in facebook (attached). Finally, i decided to remove all and use the Intel driver. :(

**question, what actually mean by "Switchable" and "Discrete" graphic property in BIOS?**

I take further steps to try install ATI driver again. Below is the steps.
```
sudo dpkg --purge xorg-driver-fglrx
```
```
sudo rm -r /etc/ati
```
```
sudo reboot
```

After the reboot, ATI Driver get disappear in System -> Administration -> Hardware Driver. So, i have no choice to install from terminal.
```
sudo apt-get install xorg-driver-fglrx xorg-driver-fglrx-dev
```
```
sudo aticonfig --initial
```
```
sudo reboot
```

This time the color in facebook looks as normal - no more the gray format. But checking System -> Administration -> Hardware Driver, it saying the driver version is not the latest (attached). Clicking the "Activate" button -> reboot -> Same problem in facebook. So, i repeated the same process above without activating in "Hardware Driver"

**question, what actually being install from "Hardware Driver" even there is no changes in version after install. (ATI Info attached)**

Besides the graphic problem, im facing problem with Brightness control. After done changes as per in forum (code below), Fn + brightness key is working. But, every reboot the brightness is back to default which is full. How to make the brightness setting is saved and use it upon reboot?
```
xrandr --output LVDS --set BACKLIGHT_CONTROL native
```

---

### Post by miegiel on 2009-08-18
> what actually mean by "Switchable" and "Discrete" graphic property in BIOS?

Ok, I don't have the ATI card in my 3810T, but I did read a bit about it before I decided not to get the 3810TG.

In *switchable* mode (in vista anyway) the ATI card gets switched off in battery mode and switched on when the power is connected. I'm not sure how ubuntu handles this. But I faintly recall a post somewhere saying the ATI card is always on in this mode.

In *discrete* mode I believe the ATI card is turned off and you're using the intel card.

Oh ... and don't take my word for it :twisted: verify what happens with both BIOS settings.

Something to be aware of: The ATI card sucks alot more power and under normal circumstances you don't really need it. maybe when you're playing a 3D game. Compiz runs fine on the intel card (in case you're wondering).

---

### Post by anandharaj on 2009-08-18
Hi, Thanks for the reply. I can confirm that **"discrete mode"** will disable the Intel card. This is  the different i see in Xorg log file - no Intel card.

Actually i dont mind use Intel card as i dont play game much, except FarmVille in Facebook. Playing this game in full-screen more, the graphic is not stable (something like flickering)

---

### Post by khelben1979 on 2009-08-18
Have you tried to install the latest driver directly from the ATI/AMD homepage?

---

### Post by csipuka on 2009-08-18
> **anandharaj said:**
> Hi,

========================================
Laptop Model: Acel Timeline 4810TG
BIOS version: 1.23
CPU: Intel Core 2 Duo SU9400
Graphic: Intel and ATI Radeon HD4330
OS: Ubuntu Jaunty 32bit
========================================

Hi,

I have the same configuration, but th BIOS only 1.20
I can confirm the Discrete means the ATI card will be active.
Currently the X does not support the dynamic card usage change.
When I have used the Intel card, the  laptop was so hot, so I have changed to the discrete card. It is definetly cooler.
Additionally I use the proprietary ATI driver (9.7), and here is the link howto install:
[http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide)
Csipu

---

### Post by markbuntu on 2009-08-18
The driver that hardware manager offers is the 9.3 driver which does not fully support the 4330. The 4300 series came out after this driver was released. So, you really do need a newer driver from ati.

---

### Post by anandharaj on 2009-08-18
Hi Guys, Thanks for the reply.

@khelben1979
Yes, i did install the latest driver from ATI/AMD website. Also same issue in Facebook (I think PNG images). But now it seems like browser related issue (Firefix 3.5). Rebooting second time, the image color become gray in facebook. Then i decided to try in Firefox 3.0 and its seems to be fine. 

So, Firefox 3.5 with Intel dont have issue but problem with ATI card. Can someone confirm this?

---

### Post by yawie on 2009-09-09
Hello,

I would like to stay in switchable mode in the bios and only use the intel card (or at least the card providing the longest power time).

You think in switchable mode the ati card is completly turned off ?

---

### Post by jacktow on 2009-09-09
I just purchased an Acer Timeline 8371 with discrete ATI graphics and I'm not quite liking it.

I was under the impression that one could choose which graphics card to use by changing a BIOS option. Turns out I was wrong. The switchable graphics option seems to keep both cards on and thus my machine runs hot and my battery, based on my estimate, would not even last 2 hours!

I'm currently using Karmic alpha 6 and by default, it loads both i915 and radeon drivers. I blacklisted radeon driver and further did the following which I thought would turn off the bus on which ATI sits:

```
echo 1 > /sys/bus/pci/devices/0000:01:00.0/remove
```

NOTE: I got the device id by looking at the output of "lspci"

Doing that caused the ATI card to no longer show up on lspci and its traces vanished everywhere, and YET, no changes in the temperature nor the pathetic battery life.

Any ideas? or else I might end up exchanging this unit with the non-discrete version (which would be very difficult, considering I've unpacked everything and pulled out all the stickers, etc. :) )

NOTE: I've attached the output of "lshw" and "lspci" for those who can make use of it

---

### Post by jacktow on 2009-09-11
OK, so I ended up setting the BIOS graphics option to "Discrete" mode and installing ATI's proprietary driver and using its Low Power mode. I get about 4 hours of battery life. NOT GOOD ENOUGH!

It's at least usable now. Here's my thought on the issue. The only problem here is a crappy BIOS. All we need is an option in the BIOS to allow switching to Integrated graphics just like Lenovo T400 does ([http://www-307.ibm.com/pc/support/site.wss/document.do?lndocid=MIGR-70495#g5](http://www-307.ibm.com/pc/support/site.wss/document.do?lndocid=MIGR-70495#g5)).

Now, we can either wait and hope for such an option to show up in future BIOS updates from acer, or we can ask acer to consider it. I'm yet to find an email address where I can contact acer!

---

### Post by jacktow on 2009-09-11
**GOOD NEWS EVERYONE**

I found a tiny code on the net [written by Sylvain on opensuse forums]("http://forum.suse.co.in/index.php?t=msg&goto=48357&rid=0&S=d553a5457a9e277b218e9e12541a85d3"). It's a kernel module that uses ACPI functionality to completely turn off the ATI card! It's just awesome.

So here're the steps to a lot more energy efficient laptop:

1. Save the following as **lenovo_acpi.c**:
```

/* Linux kernel module that disables the discrete graphics board for Lenovo
 * U330. Other lenovo laptops could work, but I don't know.
 *
 * Copyright (c) 2009: Sylvain Joyeux <sylvain.joyeux@m4x.org>
 */
#include <acpi/acpi.h>

MODULE_LICENSE("GPL");

static acpi_handle root_handle;

static int __init kill_ati(void)
{
    int i;
    acpi_status status;
    // The device handle
    acpi_handle handle;
    // The package elements
    union acpi_object package_elements[3];
    // The arguments to ATPX
    union acpi_object atpx_arg_elements[2];
    struct acpi_object_list atpx_arg;
    // For the return value of ATPX
    struct acpi_buffer buffer = { ACPI_ALLOCATE_BUFFER, NULL };

    status = acpi_get_handle(root_handle, "\\_SB_.PCI0.OVGA.ATPX", &handle);
    if (ACPI_FAILURE(status))
    {
        status = acpi_get_handle(root_handle, "\\_SB_.PCI0.OVGA.XTPX", &handle);
        if (ACPI_FAILURE(status))
        {
            printk("lenovo_acpi: cannot get ACPI handle: %s\n", acpi_format_exception(status));
            return -ENOSYS;
        }
        printk("lenovo_acpi: in discrete graphics mode\n");
        return 0;
    }

    for (i = 0; i < 3; ++i)
    {
        package_elements[i].type = ACPI_TYPE_INTEGER;
        package_elements[i].integer.value = 0;
    }

    atpx_arg.count = 2;
    atpx_arg.pointer = &atpx_arg_elements[0];

    atpx_arg_elements[0].type = ACPI_TYPE_INTEGER;
    atpx_arg_elements[0].integer.value = 2;

    atpx_arg_elements[1].type = ACPI_TYPE_PACKAGE;
    atpx_arg_elements[1].package.count = 3;
    atpx_arg_elements[1].package.elements = &package_elements[0];
    
    status = acpi_evaluate_object(handle, NULL, &atpx_arg, &buffer);
    if (ACPI_FAILURE(status))
    {
        printk("lenovo_acpi: ATPX method call failed: %s\n", acpi_format_exception(status));
        return -ENOSYS;
    }
    kfree(buffer.pointer);

    printk("lenovo_acpi: disabled the discrete graphics card\n");
    return 0;
}

static void dummy(void)
{
}

module_init(kill_ati);
module_exit(dummy);


```

2. Save the following as **Makefile**:

```
ifneq ($(KERNELRELEASE),)
  obj-m := lenovo_acpi.o
else
  KERNELDIR ?= /lib/modules/$(shell uname -r)/build
  PWD := $(shell pwd)

default:
	$(MAKE) -C $(KERNELDIR) M=$(PWD) $(EXTRA_FLAGS) modules

clean:
	$(MAKE) -C $(KERNELDIR) M=$(PWD) $(EXTRA_FLAGS) clean

endif

```

3. In the same folder, run the following shell commands:

```

make
sudo cp lenovo_acpi.ko /lib/modules/`uname -r`/kernel/
sudo depmod
echo lenovo_acpi | sudo tee -a /etc/modules > /dev/null

```

4. Restart and choose **"Switchable" graphics in the BIOS**

Next time your linux boots, it should shut down the ATI card. Easiest way to check is to look at the battery life estimate.

All the credit goes to Sylvain for his fabulous hack - I just copied it here, so don't thank me.

*NOTE: You need to compile this for each new kernel you install - I know too little to make it work with all kernels (see dkms)*

*Reference: [http://forum.suse.co.in/index.php?t=msg&goto=48357&rid=0&S=d553a5457a9e277b218e9e12541a85d3](http://forum.suse.co.in/index.php?t=msg&goto=48357&rid=0&S=d553a5457a9e277b218e9e12541a85d3)*

---

### Post by deltaromeo on 2009-09-13
Thanks jacktow!  This worked for me using Acer Timeline 5810TG on 64-bit Ubuntu with kernel 2.6.3.0  Was previously running the latest Catalyst drivers and getting battery life of about 2.5 maybe 3 hrs - Now it's indicating I'll have over 4 and I reckon (or am hoping) it's being conservative as it adjusts to the changes slowly!

The prob with this kernel is it doesn't let me change the brightness at all!  Maybe I'll move down to 2.6.3.0RCx ... or something.

---

### Post by jacktow on 2009-09-13
What release of ubuntu are you using? I installed the latest testing release (Karmic Alpha 5), and everything including the brightness control works like a charm. The only major broken feature is suspend to RAM.

Your battery life might drop a little by changing to Karmic at this stage, because of some kernel scheduler performance problems, but not so much so to considerably upset you ;-)

---

### Post by deltaromeo on 2009-09-13
I'm using Jaunty.  I haven't looked at Karmik yet, maybe I'll give that a go but I'm sure at least one of the kernels somewhere between 2.6.29 - 31 worked perfectly with the brightness controls! 

I don't usually tinker this far so I've learnt quite a bit..I'd never have thought to stick code there that was written for a different make of laptop!

---

### Post by tuukkah on 2009-09-24
> **deltaromeo said:**
> Thanks jacktow!  This worked for me using Acer Timeline 5810TG on 64-bit Ubuntu with kernel 2.6.3.0  Was previously running the latest Catalyst drivers and getting battery life of about 2.5 maybe 3 hrs - Now it's indicating I'll have over 4 and I reckon (or am hoping) it's being conservative as it adjusts to the changes slowly!


Big thanks to jacktow from me as well! I've reported this as a bug: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/435906](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/435906)

I've also reported some other bugs that affect Timeline machines: [https://bugs.launchpad.net/~tuukkah]("https://bugs.launchpad.net/%7Etuukkah")

---

### Post by sasquatch_parmesan on 2009-10-01
> **jacktow said:**
> OK, so I ended up setting the BIOS graphics option to "Discrete" mode and installing ATI's proprietary driver and using its Low Power mode. I get about 4 hours of battery life. NOT GOOD ENOUGH!

It's at least usable now. Here's my thought on the issue. The only problem here is a crappy BIOS. All we need is an option in the BIOS to allow switching to Integrated graphics just like Lenovo T400 does ([http://www-307.ibm.com/pc/support/site.wss/document.do?lndocid=MIGR-70495#g5](http://www-307.ibm.com/pc/support/site.wss/document.do?lndocid=MIGR-70495#g5)).

Now, we can either wait and hope for such an option to show up in future BIOS updates from acer, or we can ask acer to consider it. I'm yet to find an email address where I can contact acer!

I have the 8371g.

I've been in contact with acer about this, and they pointed out BIOS version 1.07 available on their support site. I downgraded from 1.11 and sure enough i could now select the integrated display adapter. But this bios is older and has hardware virtualization disabled unlike newer versions. This was a disadvantage for me, so I upgraded to the 1.11 bios again, and am using the discrete adapter with the latest driver from ati. I'm getting 5 hours+ of battery life.

They said BIOS 1.13 was going to be released soon, which they told me to try. Haven't seen it yet on their site though, but one can hope..

---

### Post by jacktow on 2009-10-01
> **sasquatch_parmesan said:**
> I have the 8371g.

I've been in contact with acer about this, and they pointed out BIOS version 1.07 available on their support site. I downgraded from 1.11 and sure enough i could now select the integrated display adapter. But this bios is older and has hardware virtualization disabled unlike newer versions. This was a disadvantage for me, so I upgraded to the 1.11 bios again, and am using the discrete adapter with the latest driver from ati. I'm getting 5 hours+ of battery life.

They said BIOS 1.13 was going to be released soon, which they told me to try. Haven't seen it yet on their site though, but one can hope..

Well I don't know what you told them to get such a reply from Acer, all I got was "Linux is not supported" and when I told them XP had the same issue, they had already locked on the L word.

Also, I'm usually wary of upgrading/downgrading my BIOS firmware (horrible past experiences) so I guess I wait for someone to try it out first. If and when you install it on yours, please let us know how it goes.

Thanks

---

### Post by sasquatch_parmesan on 2009-10-02
> **jacktow said:**
> Well I don't know what you told them to get such a reply from Acer, all I got was "Linux is not supported" and when I told them XP had the same issue, they had already locked on the L word.

Also, I'm usually wary of upgrading/downgrading my BIOS firmware (horrible past experiences) so I guess I wait for someone to try it out first. If and when you install it on yours, please let us know how it goes.

Thanks

I've tried bios 1.07, 1.10 and 1.11. 1.07 supports selecting the integrated adapter. No problem flashing the bios. I used freedos running from usb and the dos flashing program included in the bios file on the acer site. Had to use 2 flags to the flashing program because i had a newer version, and it didn't want to downgrade unless i forced it to.

---

### Post by miegiel on 2009-10-02
meh ... wrong thread ](*,)

---

### Post by netimen on 2009-10-08
lspci returns for me:
```
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
01:00.0 VGA compatible controller: ATI Technologies Inc M92 LP [Mobility Radeon HD 4300 Series]

```

Does that mean I have both adapters turned on? (notebook is quite hot in the left part and battery lifetime estimate is ~2h)

A question about that fix by Sylvian: if I use it, can I afterwards enable the ATI adapter?

---

### Post by miegiel on 2009-10-08
> **netimen said:**
> lspci returns for me:
```
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
01:00.0 VGA compatible controller: ATI Technologies Inc M92 LP [Mobility Radeon HD 4300 Series]

```

Does that mean I have both adapters turned on? (notebook is quite hot in the left part and battery lifetime estimate is ~2h)

A question about that fix by Sylvian: if I use it, can I afterwards enable the ATI adapter?

Yes (don't know about the fix, I've got the timeline without ATI graphics).

---

### Post by eiriklf on 2009-10-09
Thought I'd post a little note here that by combining the skript posted here earlier and switchconf, I can now switch from Intel to ATI graphics quite easily, (just reboot, change adapter in bios, and then i made a choice for intel and one for ATI in grub). So thanks a lot

Now I only need to get suspend to ram working...

---

### Post by netimen on 2009-10-09
Tried to use the fix, but failed: I followed the instructions, but lspci tells that ATI card still is on and power estimate still is 2hrs

lsmod | grep lenovo returns:
```
lenovo_acpi             9604  0
```
dmesg | grep lenovo returns:
```
[   29.500233] lenovo_acpi: disabled the discrete graphics card
```
but lspci | grep VGA returns
```
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
01:00.0 VGA compatible controller: ATI Technologies Inc M92 LP [Mobility Radeon HD 4300 Series] (rev ff)

```

---

### Post by jacktow on 2009-10-10
> **netimen said:**
> Tried to use the fix, but failed: I followed the instructions, but lspci tells that ATI card still is on and power estimate still is 2hrs

lsmod | grep lenovo returns:
```
lenovo_acpi             9604  0
```
dmesg | grep lenovo returns:
```
[   29.500233] lenovo_acpi: disabled the discrete graphics card
```
but lspci | grep VGA returns
```
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
01:00.0 VGA compatible controller: ATI Technologies Inc M92 LP [Mobility Radeon HD 4300 Series] (rev ff)

```

What's your laptop model and BIOS version? (I don't really have any idea how to help you with that, but that info would be useful for someone else).

---

### Post by netimen on 2009-10-11
Acer Aspire Timeline 4810G, BIOS version 1.28. What version do you have?

---

### Post by jacktow on 2009-10-11
> **netimen said:**
> Acer Aspire Timeline 4810G, BIOS version 1.28. What version do you have?

Mine's an Acer Travelmate Timeline 8371G, BIOS 1.10 - one of the replies above shows it works on 5810G as well, so I would be highly sure it works on your hardware, but as of now can't think of any reason why it doesn't.

---

### Post by netimen on 2009-10-12
> **jacktow said:**
> Mine's an Acer Travelmate Timeline 8371G, BIOS 1.10 - one of the replies above shows it works on 5810G as well, so I would be highly sure it works on your hardware, but as of now can't think of any reason why it doesn't.
Can this be caused by kernel version?

---

### Post by jacktow on 2009-10-12
> **netimen said:**
> Can this be caused by kernel version?

Hmm, yeh - some idea is better than none. My kernel is 2.6.31 I think (latest on karmic beta).

---

### Post by netimen on 2009-10-12
hm, my version is 2.6.28-15-generic

---

### Post by jacktow on 2009-10-20
Version **1.13** of BIOS for Acer Travelmate Timeline 8371G is now available on Acer's support website.

I'm currently doing some critical work on my laptop, so can't take the risk of messing it up right now. If anyone is willing to try out this new BIOS and see what's changed (they don't include a simple changelog!) and whether the new Integrated Graphics options is added.

---

### Post by jacktow on 2009-10-20
OK - I went ahead and upgraded to 1.13.
Guess what? No Integrated option :(

I found a rather unusual thing. Previously I had set a password for my harddisk. It was same as my boot password and the old BIOS never asked me for the HD password, only the boot. I thought it automatically tries the same password on the HD.

BUT, the new BIOS actually asks for the HD password separately! That makes me wonder if the old BIOS was even honouring my password. Then again, as far as I know the HD password is stored in the HD itself (it's actually a feature of the HD). So how can the BIOS bypass it. I'm not sure, I'm just trying to make sense of my observations. Any insight would be good to hear.
[I]
NOTE: I also noticed a slight jump in my power consumption - it could be paranoia =p[/I]

---

### Post by miegiel on 2009-10-20
> **jacktow said:**
> OK - I went ahead and upgraded to 1.13.
Guess what? No Integrated option :(

I found a rather unusual thing. Previously I had set a password for my harddisk. It was same as my boot password and the old BIOS never asked me for the HD password, only the boot. I thought it automatically tries the same password on the HD.

BUT, the new BIOS actually asks for the HD password separately! That makes me wonder if the old BIOS was even honouring my password. Then again, as far as I know the HD password is stored in the HD itself (it's actually a feature of the HD). So how can the BIOS bypass it. I'm not sure, I'm just trying to make sense of my observations. Any insight would be good to hear.

[I]
NOTE: I also noticed a slight jump in my power consumption - it could be paranoia =p[/I]

1st of all if you update your BIOS you should always reset the BIOS to it's default values before flashing. And after flashing it's recommended to load the BIOS defaults again, reboot the BIOS and then set it up the way you want it. Obviously this includes clearing all passwords you've set in the BIOS ;)

On my 3810T I get prompted for the HDD password and the BIOS password if they are not identical. If they are identical I only get prompted for the BIOS password. I think the BIOS remembers that they are identical when you set the passwords so that it won't make you enter it twice. I've cleared the BIOS password [1] without clearing the identical HDD password and (no big supprise) I got prompted to enter the HDD password. So the HDD security was being used even though I never got prompted for the HDD password.

I assume your passwords aren't identical, even if they seem to be identical. Or the BIOS doesn't know they are identical because that information was wiped while flashing the BIOS.

*[1] I was trying to figure out why the HDD security didn't work properly. It turned out I had to turn on AHCI in the BIOS to use HDD security.*

---

### Post by cnkk on 2009-10-29
Hey Guys.
Well I've the same problem with my 4810TG :/
My Bios version is 1.23 (theres a 2.30 on acers site, should i upgrade ?)
I used this lenovo hack and well, my laptop is much cooler now but the fan is working the whole time... and when i do lspci | grep VGA it return both intel and ati.
I've got the newest kernel version. karmic koala
I also noticed that i cannot change the brightness when im in switchable mode (which is required by lenovo script)
any ideas? Its really bad that theres so less compability with this laptop :/
hope someone can help
have a nice day
greets


Edit:
There also are a lot of (error) messages coming up when i boot ubuntu like (Xorg.0.log):[SIZE=1][I]
...
...
(II) intel(0): EDID for output VGA1
(II) intel(0): EDID for output LVDS1
(II) intel(0): Manufacturer: LGD  Model: 201  Serial#: 0
(II) intel(0): Year: 2009  Week: 0
(II) intel(0): EDID Version: 1.3
(II) intel(0): Digital Display Input
(II) intel(0): Max Image Size [cm]: horiz.: 31  vert.: 17
(II) intel(0): Gamma: 2.20
(II) intel(0): No DPMS capabilities specified
(II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.584 redY: 0.352   greenX: 0.338 greenY: 0.551
(II) intel(0): blueX: 0.157 blueY: 0.137   whiteX: 0.313 whiteY: 0.329
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 75.1 MHz   Image Size:  310 x 174 mm
(II) intel(0): h_active: 1366  h_sync: 1414  h_sync_end 1446 h_blank_end 1564 h_border: 0
(II) intel(0): v_active: 768  v_sync: 771  v_sync_end 776 v_blanking: 800 v_border: 0
(II) intel(0):  LG Display
(II) intel(0): Monitor name: LP140WH2-TLA1
(II) intel(0): EDID (in hex):
(II) intel(0):     00ffffffffffff0030e4010200000000
(II) intel(0):     00130103801f11780a8845955a568d28
(II) intel(0):     23505400000001010101010101010101
(II) intel(0):     010101010101561d56c6500020303020
(II) intel(0):     350036ae100000190000000000000000
(II) intel(0):     00000000000000000000000000fe004c
(II) intel(0):     4720446973706c61790a2020000000fc
(II) intel(0):     004c503134305748322d544c41310039
(II) intel(0): EDID vendor "LGD", prod id 513
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1366x768"x0.0   75.10  1366 1414 1446 1564  768 771 776 800 -hsync -vsync (48.0 kHz)
(II) intel(0): Not using default mode "640x350" (vrefresh out of range)
(II) intel(0): Not using default mode "640x400" (vrefresh out of range)
(II) intel(0): Not using default mode "720x400" (vrefresh out of range)
(II) intel(0): Not using default mode "640x480" (vrefresh out of range)
(II) intel(0): Not using default mode "640x480" (vrefresh out of range)
(II) intel(0): Not using default mode "640x480" (vrefresh out of range)
(II) intel(0): Not using default mode "800x600" (vrefresh out of range)
(II) intel(0): Not using default mode "800x600" (vrefresh out of range)
(II) intel(0): Not using default mode "800x600" (vrefresh out of range)
(II) intel(0): Not using default mode "800x600" (vrefresh out of range)
(II) intel(0): Not using default mode "1024x768" (vrefresh out of range)
(II) intel(0): Not using default mode "1024x768" (vrefresh out of range)
(II) intel(0): Not using default mode "1024x768" (vrefresh out of range)
(II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
(II) intel(0): Not using default mode "1280x960" (hsync out of range)
(II) intel(0): Not using default mode "1280x960" (vrefresh out of range)
(II) intel(0): Not using default mode "1280x1024" (hsync out of range)
(II) intel(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) intel(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) intel(0): Not using default mode "1600x1200" (hsync out of range)
(II) intel(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) intel(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) intel(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) intel(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) intel(0): Not using default mode "1792x1344" (hsync out of range)
(II) intel(0): Not using default mode "1792x1344" (vrefresh out of range)
(II) intel(0): Not using default mode "1856x1392" (hsync out of range)
(II) intel(0): Not using default mode "1856x1392" (vrefresh out of range)
(II) intel(0): Not using default mode "1920x1440" (hsync out of range)
(II) intel(0): Not using default mode "1920x1440" (vrefresh out of range)
(II) intel(0): Not using default mode "832x624" (vrefresh out of range)
(II) intel(0): Not using default mode "1152x864" (hsync out of range)
(II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
(II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
(II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
(II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
(II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
(II) intel(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "1400x1050" (hsync out of range)
(II) intel(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) intel(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) intel(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) intel(0): Not using default mode "1440x900" (hsync out of range)
(II) intel(0): Not using default mode "1600x1024" (hsync out of range)
(II) intel(0): Not using default mode "1680x1050" (hsync out of range)
(II) intel(0): Not using default mode "1680x1050" (hsync out of range)
(II) intel(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) intel(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) intel(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) intel(0): Not using default mode "1920x1080" (hsync out of range)
(II) intel(0): Not using default mode "1920x1200" (hsync out of range)
(II) intel(0): Not using default mode "1920x1440" (vrefresh out of range)
(II) intel(0): Not using default mode "2048x1536" (hsync out of range)
(II) intel(0): Not using default mode "2048x1536" (vrefresh out of range)
(II) intel(0): Not using default mode "2048x1536" (vrefresh out of range)
(II) intel(0): Printing probed modes for output LVDS1
(II) intel(0): Modeline "1366x768"x60.0   75.10  1366 1414 1446 1564  768 771 776 800 -hsync -vsync (48.0 kHz)
(II) intel(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): EDID for output DP1
(WW) AT Translated Set 2 keyboard: unable to handle keycode 464
...
...[/I][/SIZE]

---

### Post by cnkk on 2009-11-03
no ideas?
its very painful for the batterylife without beeing able to turn off the brightness

---

### Post by csipuka on 2009-11-03
> **cnkk said:**
> no ideas?
its very painful for the batterylife without beeing able to turn off the brightness
I have tried out this lenovo trick, but there was no bin difference against ATI. The laptop was cool, and the battery life estimated ~5h (~13W regarding powertop). With Jaunty it was a bit more than 6h (~10W).
I cannot change the brightness, neither with FN key nor with xbacklight. The brightness was not on max as I saw, but on 20-30%.

---

### Post by conicalb on 2009-11-04
Awesome this worked on my u330.  Went form 28w to 16w.  My watt use may be higher then others as I replaced my stock hardrive with a 320GB 7200 rpm harddrive.

Thanks for the post.

---

### Post by cnkk on 2009-11-07
did anyone find  a method to change the brightness with acer 4810T(G) ?

---

### Post by maxistar on 2009-11-10
> **cnkk said:**
> did anyone find  a method to change the brightness with acer 4810T(G) ?
Solved! I used suggestion from this post [http://ubuntuforums.org/showthread.php?t=1165087&page=49](http://ubuntuforums.org/showthread.php?t=1165087&page=49)
for my 64bit version of carmic on my 4810TG. I is working fine for me. Brightness control is working NOW!!! Not sure if it will work for 32bit though.

---

### Post by netimen on 2009-11-10
> **jacktow said:**
> OK, so I ended up setting the BIOS graphics option to "Discrete" mode and installing ATI's proprietary driver and using its Low Power mode.

How did you set that low-power mode?

---

### Post by krychek on 2009-11-12
Is this high power consumption reported on launchpad?
I also have this problem with this laptop among many others. The internal microphone doesn't work, the wifi connection keeps dropping after half minute, the hdmi port doesn't work, x won't start if I install the closed ati driver, the touchpad on/off button only turns it off but can't turn it back on. Are you having these problems too? They all should be reported.

Edit: I just reread the whole thread and found that it's already reported:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/435906](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/435906)

---

### Post by krychek on 2009-11-13
I filed two more bugs:
Internal mic doesn't work: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/481424](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/481424)
Wireless connection keeps disconnecting: [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/481432](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/481432)

---

### Post by krychek on 2009-11-13
After I installed the proprietary Ati driver (either with Jockey or the latest one from Ati website) X won't start. I get only a text login screen flashing in front of me. Xorg.0.log says "board vendor info: third party graphics adapter - NOT original ATI". I find this pretty strange.

BTW the cdrom eject button doesn't work either.

Update: After changing the Display setting in BIOS my Ati card is working, power consumption is better, HDMI port is working, brightness adjusting is working.

---

### Post by Deliaz on 2009-11-22
thanks a lot, but i have some troubles:
```
deliaz@book:~$ sudo xrandr --output LVDS --set BACKLIGHT_CONTROL nativ
X Error of failed request:  BadRROutput (invalid Output parameter)
  Major opcode of failed request:  150 (RANDR)
  Minor opcode of failed request:  15 (RRGetOutputProperty)
  Serial number of failed request:  26
  Current serial number in output stream:  26

```

---

### Post by carmdg on 2009-11-24
Ive got the 4810t with switchable graphics. Currently as a dual boot, with 9.10 what effect if any will the switchable graphics fix have? I.E will it effect the acer power saving software in win 7, such as changing between the two automatically.

Also with that fix do the graphics automatically switch when necessary in ubuntu? Sorry I dont really Understand the code.

---

### Post by krychek on 2009-12-01
Does any of you have a problem with switching the screen to an external monitor? When I try it sometimes I get black screen on both monitors and the external one won't even work until I disconnect it from the power supply. It's pretty strange. I'm using the latest Ati driver (9.11), v1.31 BIOS and LSL 3230T Fujitsu-Siemens monitor.

---

### Post by uncle_pete on 2009-12-04
I apologize if I should be able to find the answer somewhere else....

I'm trying to run the acpi mod on my U330 in Karmic and it seems to be breaking something... When I restart after doing it I get what I think is a 'kernel panic' as the computer tries to start up.  I didn't get much out of scanning through the printout when it quit. Any suggestions on what should be my first action?  

To get things working again I went in the recovery console and commented out 'lenovo_acpi' in the /etc/modules file and then ran depmod, this was just my guess at keeping the mod from running based on a quick look at the man files for the shell commands.  

I believe I had the mod working in Jaunty last night, but never checked to make sure the ati card was actually turned off, although I had just downloaded Karmic and wanted to give it a try.... 

Also, when I ran the shell commands it was necessary for me to put in the actual '2.6.31.15-generic' instead of the 'uname-r' as that was not working and I believe this was a reasonable solution as that's the kernel being currently used.  Thanks for any help

---

### Post by originalmike on 2009-12-15
Who knows how to use the lenovo script with dkms?

---

### Post by marcuskall on 2009-12-19
The lenovo_acpi module fix works fine for me. According to powertop the power usage goes down from 24W to 15W.

$ sudo dmidecode -s system-product-name
Aspire 4810T
$ sudo dmidecode -s system-version
V1.30

The bios settings is "Switchable graphics"

One problem I have is that after a suspend to ram the power usage goes back to 24W and I have to do a "rmmod lenovo_acpi && modprobe lenovo_acpi" to get back to low power usage.

Any one who knows how to auto enable the module fix after a suspend to ram?

---

### Post by Deliaz on 2010-01-04
**jacktow** thanx. lenovo_acpi is awesome (~4+ hours)

---

### Post by loll31 on 2010-01-11
> **originalmike said:**
> Who knows how to use the lenovo script with dkms?

Hi,

I made a pkg available on [my personal page]("http://ljr.free.fr/blog/2009/11/02/lenovo-u330-sous-linux/") ([rpm link]("http://ljr.free.fr/archives/lenovo_u330/lenovo_acpi-0.1.0-1dkms.noarch.rpm")).

To use it under ubuntu, you must install dkms and alien before.
Under root (or sudo) :
apt-get install dkms alien
alien --script [lenovo_acpi-0.1.0-1DKMS.noarch.rpm]("http://ljr.free.fr/archives/lenovo_u330/lenovo_acpi-0.1.0-1dkms.noarch.rpm")
dpkg -i lenovo-acpi_0.1.0-2_all.deb

To load the module, you can test with 'sudo modprobe lenovo_acpi'.
Check before/after the benefits under powertop (apt-get install if needed).

Add module in /etc/modules to load it automatically at boot time !
Have fun.

PS: it runs well for Lenovo U330 and Acer Timeline 4810TZG (su4300/ati/4Go/500go).

---

### Post by wdwd on 2010-01-26
Hi everyone,
 I am new to Ubuntu and am having a bit of trouble trying to disable my discrete graphics on my Lenovo U33o, I don't understand how to install the script. I cant figure out how to save it. I see there is a package that will install it but i cant figure how to. Any help would be greatly appreciated. Thanks...

---

### Post by dmkg on 2010-01-28
I am trying to implement the Lenovo-code as suggested by** jacktow** in his "**GOOD NEWS EVERYONE"**-post. I am doing this on a fresh install of Karmic (Ubuntu 9.10) on the Acer Timeline 4810TG. 

As I run the following code:     
          ```
make
sudo cp lenovo_acpi.ko /lib/modules/`uname -r`/kernel/
sudo depmod
echo lenovo_acpi | sudo tee -a /etc/modules > /dev/null 

```...everything seems to work fine. I only get an output from the 'make' command, the rest are silent, but with no errors.
 
     Output from Make:     
         > make -C /lib/modules/2.6.31-14-generic/build M=/home/jollyroger  modules
         make[1]: Entering directory `/usr/src/linux-headers-2.6.31-14-generic'
           Building modules, stage 2.
           MODPOST 1 modules
         make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-14-generic'
None-the-less, there is no effect upon restart. As i run 'lspci' both the ATI and Intel devices are running. 
Does anyone have any idea what is going wrong? or any similar experience?

Note - this is my first time doing any 'make'-stuff, and if there is any essential setup-procedures or packages needed to be installed in orden to use 'make' - that could be the problem...

---

### Post by loll31 on 2010-01-28
Just try 
  modprobe lenovo_acpi
or insmod /directory_where_is/lenovo_acpi

Normally, ati card chould be off (check with powertop and lspci)

---

### Post by wdwd on 2010-02-01
Hello everyone again,
 Is there any one who can give me detailed instructions on how to install this code on my lenovo u330, I really need help  I am missing something along the way I cant disable my ATI graphics card and my battery life is horrible, I am very new to Ubuntu and detailed instructions would be helpful thanks again.. I have searched up and down but i cant figure it out..

---

### Post by miegiel on 2010-02-01
> **wdwd said:**
> Hello everyone again,
 Is there any one who can give me detailed instructions on how to install this code on my lenovo u330, I really need help  I am missing something along the way I cant disable my ATI graphics card and my battery life is horrible, I am very new to Ubuntu and detailed instructions would be helpful thanks again.. I have searched up and down but i cant figure it out..

Is the u330 lenovo's equivalent of the timeline? Don't really know the model :D

If it is [this script]("http://ubuntuforums.org/showthread.php?p=8736103#post8736103") might help. It didn't do me much good, but people with ATI graphics in their timelines did post it makes a difference.

---

### Post by wdwd on 2010-02-01
It didn't work but thanks for your efforts, I appreciate it.

---

### Post by jekristiansen on 2010-02-06
Hi everyone!

I have another timeline from acer, wich is 5810TG Core Solo with both Intel & ATI Radeon HD 4330 card, with 512 MB internal.
Does anyone know if there is a stable graphic driver in the repos yet for the Timeline series?

---

### Post by jacktow on 2010-02-07
> **sasquatch_parmesan said:**
> I've tried bios 1.07, 1.10 and 1.11. 1.07 supports selecting the integrated adapter. No problem flashing the bios. I used freedos running from usb and the dos flashing program included in the bios file on the acer site. Had to use 2 flags to the flashing program because i had a newer version, and it didn't want to downgrade unless i forced it to.

what flags did you use on the flash program to force it to flash to an earlier version?

---

### Post by miegiel on 2010-02-08
> **jacktow said:**
> what flags did you use on the flash program to force it to flash to an earlier version?

I don't know, but */?* is often the help flag, though sometimes it's */h -?* or *-h*. If not, try running the .exe without flags or other instructions (like what BIOS file to use).

---

### Post by colorprint on 2010-03-10
Is there any way to use the discrete ATI video, and to switch between the ATI and intel video?
I have similar problem with ATI video in my new HP tm2 laptop...

---

### Post by cnkk on 2010-03-20
what the heck? the new kernel update killed the lenovo script? does anyone knows specific information?

---

### Post by jacktow on 2010-03-23
On an unrelated note but important nonetheless: Suspend issue is solved!
See these links for details:
[http://ubuntuforums.org/showthread.php?t=1165087&page=74]("http://ubuntuforums.org/showthread.php?t=1165087&page=74")
[https://help.ubuntu.com/community/AspireTimeline/Fixes#Suspend%20to%20RAM]("https://help.ubuntu.com/community/AspireTimeline/Fixes#Suspend%20to%20RAM")
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/405120/comments/94]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/405120/comments/94")

---

### Post by loll31 on 2010-05-04
I'm testing the new switchroo functionnality which permits to switch between VGA cards under X11. The switch needs logoff/login at this time !

My source is this blog page for asus M51 : [http://asusm51ta-with-linux.blogspot.com/]("http://asusm51ta-with-linux.blogspot.com/").

To summarize, the switch seems to work but there is still a problem with 4810TZG : on discrete mode, the integrated card does not seem to be switch off as it should if the PC is on battery mode :-( So 20w, it's half the time far away power source... 
Also it's hot and noisy... I think its a BIOS problem as it does this job automatically when un/plug the power cord.
Btw you can avoid the reboot now !

But running on intel card, consumption is around 10w (with optimization) under Fedora 13 / 2.6.33 (1w more than my better score under ubuntu 10.04 / 2.6.32 :-( ).

Switchroo adds a management interface thru sysfs. It's only on debug mode at this time.
 
```
$ cat /sys/kernel/debug/vgaswitcheroo/switch 
0:+:Pwr:0000:00:02.0    < integrated card
1: :Off:0000:01:00.0    < discrete card
```

Thru the script switch_cards.sh + desktop link, it's possible to swith cards or check status. 

Info from patch :
> From: Dave Airlie <airlied@linux.ie>
Date: Mon, 1 Feb 2010 15:38:10 +1000
Subject: [PATCH] vga_switcheroo: initial implementation (v13)

Many new laptops now come with 2 gpus, one to be used for low power
modes and one for gaming/on-ac applications. These GPUs are typically
wired to the laptop panel and VGA ports via a multiplexer unit which
is controlled via ACPI methods.

4 combinations of systems typically exist - with 2 ACPI methods.
Intel/ATI - Lenovo W500/T500 - use ATPX ACPI method
ATI/ATI - some ASUS - use ATPX ACPI Method
Intel/Nvidia - - use _DSM ACPI method
Nvidia/Nvidia -  - use _DSM ACPI method.

TODO:
This patch adds support for the ATPX method and initial bits
for the _DSM methods that need to written by someone with
access to the hardware.
Add a proper non-debugfs interface - need to get some proper
testing first.

v2: add power up/down support for both devices
on W500 puts i915/radeon into D3 and cuts power to radeon.

v3: redo probing methods, no DMI list, drm devices call to
register with switcheroo, it tries to find an ATPX method on
any device and once there is two devices + ATPX it inits the
switcher.

v4: ATPX msg handling using buffers - should work on more machines

v5: rearchitect after more mjg59 discussion - move ATPX handling to
    radeon driver.
v6: add file headers + initial nouveau bits (to be filled out).

v7: merge delayed switcher code.

v8: avoid suspend/resume of gpu that is off

v9: rearchitect - mjg59 is always right. - move all ATPX code to
radeon, should allow simpler DSM also proper ATRM handling

v10: add ATRM support for radeon BIOS, add mutex to lock vgasr_priv

v11: fix bug in resuming Intel for 2nd time.

v12: start fixing up nvidia code blindly.

v13: blindly guess at finishing nvidia code
mount debugfs

/sys/kernel/debug/vgaswitcheroo/switch - should exist if ATPX detected
 + 2 cards.

DIS - immediate change to discrete
IGD - immediate change to IGD
DDIS - delayed change to discrete
DIGD - delayed change to IGD
ON - turn on not in use
OFF - turn off not in use

Tested on W500 (Intel/ATI) and T500 (Intel/ATI)

Signed-off-by: Dave Airlie <airlied@redhat.com>

---

### Post by telefunken on 2010-05-31
I'm trying to install the lenovo module on my Acer 3820TG (Intel/Ati) but keep getting;

```
$ sudo modprobe lenovo_acpi
FATAL: Error inserting lenovo_acpi (/lib/modules/2.6.32-22-generic/updates/dkms/lenovo_acpi.ko): Kernel does not have module support
```

This is with a newly installed Lucid...what gives?

---

### Post by fperwth on 2010-06-11
I had the same problem with my new Acer TimelineX 3820TG.
In dmesg there was an error message > lenovo_acpi: cannot get ACPI handle: AE_NOT_FOUND

If you take a look at the source code, this means that neither the _SB_.PCI0.OVGA.ATPX nor the _SB_.PCI0.OVGA.XTPX ACPI-whatever were found, likely because of the different hardware.

On this page ([http://linux-hybrid-graphics.blogspot.com/2010/06/more-linux-switchable-methods.html](http://linux-hybrid-graphics.blogspot.com/2010/06/more-linux-switchable-methods.html)), I found some other ACPI paths and tried them out.
Using _SB.PCI0.P0P2.PEGP._OFF finally worked. Now I only got a warning in dmesg that some Method call only took 0 instead of the 2 given arguments, so I changed that to in the source code from [jacktow's post]("http://ubuntuforums.org/showthread.php?p=7933876#post7933876"):

The changes I did are:
Replace line 26:
```
status = acpi_get_handle(root_handle, "\\_SB_.PCI0.OVGA.ATPX", &handle);
```
with
```
status = acpi_get_handle(root_handle, "\\_SB.PCI0.P0P2.PEGP._OFF", &handle);
```

and replace line 45
```
atpx_arg.count = 2;
```
with
```
atpx_arg.count = 0;
```

It works for me, no error message, no more hot air coming out of the right ventilation slot and about 10 watts less power consumption according to powertop.

**Important:**
Do *not* put the lenovo_acpi into /etc/modules!
When I did this, the screen just turned black while booting,.
Instead I put ```
modprobe lenovo_acpi
``` into /etc/rc.local (just before the "exit 0") and it works now.

---

### Post by avilella on 2010-06-12
This is the list of calls to turn on/off the switchable graphics card in Linux so far:
status = acpi_get_handle(root_handle, "\\_SB.PCI0.P0P1.VGA._OFF", &handle);
status = acpi_get_handle(root_handle, "\\_SB_.PCI0.OVGA.ATPX", &handle);
status = acpi_get_handle(root_handle, "\\_SB_.PCI0.OVGA.XTPX", &handle);
status = acpi_get_handle(root_handle, "\\_SB.PCI0.P0P2.PEGP._OFF", &handle);
status = acpi_get_handle(root_handle, "\\_SB.PCI0.MXR0.MXM0._OFF", &handle);
status = acpi_get_handle(root_handle, "\\_SB.PCI0.PEG1.GFX0._OFF", &handle);
status = acpi_get_handle(root_handle, "\\_SB.PCI0.PEG1.GFX0.DOFF",
&handle);

If you haven't tried the switchable graphics feature in Linux yet, have a look at your DSDT.dsl file. With a bit of luck, you may be able to identify one of the methods above.

---

### Post by telefunken on 2010-06-14
Well I tried you version of the module, but I still have the original problem. The module seems to build fine, I copy the module,

```
sudo cp lenovo_acpi.ko /lib/modules/2.6.32-22-generic/kernel/
```

and I run depmod. Still I get this error, 

```
$ sudo modprobe lenovo_acpi
FATAL: Error inserting lenovo_acpi (/lib/modules/2.6.32-22-generic/updates/dkms/lenovo_acpi.ko): Kernel does not have module support
```

I must be missing something obvious?

---

### Post by fperwth on 2010-06-19
Try to run "dmesg" or "dmesg | grep lenovo", most likely there will be an error message with more information about what went wrong.

It seems that in this case "Kernel does not have module support" just means that the modules init function (*kill_ati()*) returned something other than 0, because it ran into an error.

---

### Post by telefunken on 2010-06-22
> **fperwth said:**
> Try to run "dmesg" or "dmesg | grep lenovo", most likely there will be an error message with more information about what went wrong.

It seems that in this case "Kernel does not have module support" just means that the modules init function (*kill_ati()*) returned something other than 0, because it ran into an error.

I get this error;

```
$ dmesg | grep lenovo
[   17.264513] lenovo_acpi: cannot get ACPI handle: AE_NOT_FOUND
```

I double checked the files for your edits, and they where there.
I did a make clean && make and copied it over again, ran depmod and tried to modprobe it again with the same error...I just don't get it, we should have the same handlers since we have the same hardware?!

Thanks for the help so far, hate being forced to use win only to get enough battery time!

---

### Post by fperwth on 2010-06-22
Which 3820TG do you have? The one with the i3 CPU or the i5 version? They come with different ATi chipsets, as far as I know.
Mine (i5) has a ATI Radeon HD 5650 1024MB DDR3:
```
02:00.0 VGA compatible controller: ATI Technologies Inc Redwood [Radeon HD 5600 Series] (rev ff)
```

If you have another card, maybe you could try some of the other functions mentioned in avilella's post above, hopefully one of them works.

To be sure I don't have missed something in my original post, here is my complete source code: (I have renamed the module to timelinex_acpi)
```

/* 
 * timelinex_acpi.c
 * 
 * Linux kernel module that disables the discrete graphics board for Acer
 * Aspire TimelineX 3820TG (Core i5). Other TimelineX laptops could work, but I don't know.
 *
 * Based on the original lenovo_acpi.c by Sylvain Joyeux <sylvain.joyeux@m4x.org>, 2009
 */
#include <acpi/acpi.h>

MODULE_LICENSE("GPL");

static acpi_handle root_handle;

static int __init kill_ati(void)
{
    int i;
    acpi_status status;
    // The device handle
    acpi_handle handle;
    // The package elements
    union acpi_object package_elements[3];
    // The arguments to ATPX
    union acpi_object atpx_arg_elements[2];
    struct acpi_object_list atpx_arg;
    // For the return value of ATPX
    struct acpi_buffer buffer = { ACPI_ALLOCATE_BUFFER, NULL };

    status = acpi_get_handle(root_handle, "\\_SB.PCI0.P0P2.PEGP._OFF", &handle); //     status = acpi_get_handle(root_handle, "\\_SB_.PCI0.OVGA.ATPX", &handle);
    if (ACPI_FAILURE(status))
    {
        status = acpi_get_handle(root_handle, "\\_SB_.PCI0.OVGA.XTPX", &handle);
        if (ACPI_FAILURE(status))
        {
            printk("timelinex_acpi: cannot get ACPI handle: %s\n", acpi_format_exception(status));
            return -ENOSYS;
        }
        printk("timelinex_acpi: in discrete graphics mode\n");
        return 0;
    }

    for (i = 0; i < 3; ++i)
    {
        package_elements[i].type = ACPI_TYPE_INTEGER;
        package_elements[i].integer.value = 0;
    }

    atpx_arg.count = 0; //     atpx_arg.count = 2;
    atpx_arg.pointer = &atpx_arg_elements[0];

    atpx_arg_elements[0].type = ACPI_TYPE_INTEGER;
    atpx_arg_elements[0].integer.value = 2;

    atpx_arg_elements[1].type = ACPI_TYPE_PACKAGE;
    atpx_arg_elements[1].package.count = 3;
    atpx_arg_elements[1].package.elements = &package_elements[0];
    
    status = acpi_evaluate_object(handle, NULL, &atpx_arg, &buffer);
    if (ACPI_FAILURE(status))
    {
        printk("timelinex_acpi: ATPX method call failed: %s\n", acpi_format_exception(status));
        return -ENOSYS;
    }
    kfree(buffer.pointer);

    printk("timelinex_acpi: disabled the discrete graphics card\n");
    return 0;
}

static void dummy(void)
{
}

module_init(kill_ati);
module_exit(dummy);

```

---

### Post by telefunken on 2010-06-22
I really don't know what I messed up in the code, but I copy/pasted yours, rebuilt the module as timelinex_acpi, and now it works!

I gotta recharge my battery and see how many hours I got now, without the module it was about 3+ hours in Ubuntu, and 8+ hours in Win7...

Thanks!

---

### Post by fperwth on 2010-06-22
Nice to hear that it is working now!

For the battery time, I really like this KDE plasmoid: [http://kde-look.org/content/show.php/?content=123767](http://kde-look.org/content/show.php/?content=123767)

---

### Post by telefunken on 2010-06-24
With fully charged battery, Ubuntu claims to have 7-9 hours worth of battery life, that's a great improvement. If I could get it to control screen brightness it might almost be on par with win7...

Going OT a bit, but if you have any tips/tricks/tweaks to get more battery out of the 3820TG, please share :)

---

### Post by fperwth on 2010-06-24
Here is a something about the brightness, it works for me: [http://ubuntuforums.org/showthread.php?p=9291657#post9291657](http://ubuntuforums.org/showthread.php?p=9291657#post9291657)

In case you also have problems with quirky graphics on the boot splash and non-working Ctrl+Alt+F1 consoles, try [this fix](http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/).

The powertop tool shows some nice power saving tips.

There are some more commands at [http://linux-macbook-air-killers.blogspot.com/2010/01/how-to-run-linux-on-acer-timeline-3810t.html](http://linux-macbook-air-killers.blogspot.com/2010/01/how-to-run-linux-on-acer-timeline-3810t.html) , but except for the wireless power saving I have not tried them yet.

---

### Post by avilella on 2010-06-29
One of the hybrid-graphics-linux Launchpad team members has created a Linux kernel module to call ACPI methods through /proc/acpi/call. The code is here:
[http://github.com/mkottman/acpi_call](http://github.com/mkottman/acpi_call)
You can try it by installing the module and calling it like this:
git clone [http://github.com/mkottman/acpi_call.git](http://github.com/mkottman/acpi_call.git)
cd acpi_call
make
sudo insmod acpi_call.ko
./test_off.sh

Cheers

---

### Post by Kvik on 2010-07-06
Anyone tried it on ubuntu 10.04, i'll have my Acer timeline 4810TG next week, and it look's like alot of tweeking to get the battery time

---

### Post by echosystm on 2010-07-08
I'd also like to hear the current status of this model. Does everything work out of the box?

---

### Post by mosär on 2010-07-08
Negative, I just got my 4810TG (with ATI) and some things do not work out of the box (installed lucid):
  - Suspend to Disk (Suspend to RAM worked for me)
  - Reenable Touchpad after disable
  - Graphic card switching (I disabled the ATI card with the kernel module mentioned above, it's still visible in lspci, but energy consumption in powertop looks better.)

See [http://help.ubuntu.com/community/AspireTimeline/Fixes](http://help.ubuntu.com/community/AspireTimeline/Fixes) for some fixes.

---

### Post by s7ev1n on 2010-07-09
Go for Acer 3820TG, everything is working for me now.

---

### Post by csipuka on 2010-07-11
> **mosär said:**
> Negative, I just got my 4810TG (with ATI) and some things do not work out of the box (installed lucid):
  - Suspend to Disk (Suspend to RAM worked for me)
  - Reenable Touchpad after disable
  - Graphic card switching (I disabled the ATI card with the kernel module mentioned above, it's still visible in lspci, but energy consumption in powertop looks better.)

See [http://help.ubuntu.com/community/AspireTimeline/Fixes](http://help.ubuntu.com/community/AspireTimeline/Fixes) for some fixes.

Hm, I have the same configuration, but everything has worked out of the box. Suspend and touchpad is fine, and I use ATI (that's why I bought with ATI). I can use the it up to 6 hours from battery.

---

### Post by qetuR on 2010-07-15
> **s7ev1n said:**
> Go for Acer 3820TG, everything is working for me now.

Everything works? Well, at least the graphic switching...?

---

### Post by fennol on 2010-08-07
any hints for 2.6.35 kernel? i have instaled it for best support Intel HD in i3. but ```
user@user-laptop:~/hints/atioffcp$ sudo modprobe lenovo_acpi FATAL: Error inserting lenovo_acpi (/lib/modules/2.6.35-020635rc1-generic/updates/dkms/lenovo_acpi.ko): Kernel does not have module support

```

upd:
rename to timelinex_acpi. cp to kernel. and it works. 
3820tg \ i3

---

### Post by Cerasi on 2010-08-21
Hi, I've just started running Lucid on an IdeaPad Y460, with Intel GMA and an ATI Radeon HD 5600. I'd like to be able to turn off the ATI card when I boot up with switchable graphics (the BIOS offers "switchable" and "discrete" settings), but I can't get any of these modules to work. I first tried the original lenovo_acpi module, but when I try to load it I get this error:

```
$ sudo modprobe lenovo_acpi
FATAL: Error inserting lenovo_acpi (/lib/modules/2.6.32-24-generic/updates/dkms/lenovo_acpi.ko): Kernel does not have module support

$ dmesg | grep lenovo
[   15.846137] lenovo_acpi: cannot get ACPI handle: AE_NOT_FOUND
[ 1157.076571] lenovo_acpi: cannot get ACPI handle: AE_NOT_FOUND

```This is the same error that telefunken and fpwerth had, so I tried the timelinex_acpi module as well. timelinex_acpi loaded without errors and shows up when I do lsmod, BUT it doesn't turn off the ATI card. Even though the module reports that the discrete card has been turned off, lspci says it's still active.

```

$ dmesg | grep acpi
[   20.610105] timelinex_acpi: disabled the discrete graphics card

$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 12)
01:00.0 VGA compatible controller: ATI Technologies Inc Redwood [Radeon HD 5600 Series] (rev ff)
```Does anybody have suggestions about what I should do to make this work? Since I have very little experience with kernel modules, my strategy so far has been to randomly try things and see if they work ](*,). I'm running out of ideas though, and I need some help from knowledgeable people.

---

### Post by qetuR on 2010-08-24
After a couple of weeks with this laptop, i find it very good. I like absolutely everything.

I even got a proper way to use the graphics, it's not as good as in Windows, but atleast it works.

I am not 100% sure what kinda graphics it is using at the moment, but the battery time is really better.

I use the drivers from ATis homepage, I found them more updated then the ones that came with the propratary driver menu.

If I have the cable plugged in when I start the computer, I get the advanced graphics. If i plugg it out and restarts X (i have enabled ctrl+alt+backspace), I get the Intel graphics and the battery is improved. If I want to get better graphics I simply plugg in the powercord and restarts X again.

Voila! I can now have up to 8h of battery time with surfing, using wifi and medium brightness on screen with a 9cell battery.

---

### Post by smokyink on 2010-08-27
I bought the timelineX 3820TG a couple of days ago and I want to compile the linux-2.6.34 Kernel with switcheroo.

But when I get to the step to "cd /sys/kernel/debug/vgaswitcheroo" (from this blog : thttp://asusm51ta-with-linux.blogspot.com/) the folder doesn't exist :( 

Maybe I did something wrong ? Can anyone confirm that the method works ?

Also I am wandering if I can use somehow the ati 5650 proprietary driver when using the ati card. Is that posible ?

I also have a problem with the "Two finger scroll" on the touch pad. The option in mouse settings is disabled and for pretty much any other solution (including the one with xinput settings) my mouse becomes very jumpy once I put 2 fingers on the touch pad.
 Can anyone confirm that the "Two finger scroll" works ?

btw I use 64 bit ubuntu Ubuntu. Do you guys also use the 64bit version ?

---

### Post by qetuR on 2010-08-31
> **smokyink said:**
> I bought the timelineX 3820TG a couple of days ago and I want to compile the linux-2.6.34 Kernel with switcheroo.

But when I get to the step to "cd /sys/kernel/debug/vgaswitcheroo" (from this blog : thttp://asusm51ta-with-linux.blogspot.com/) the folder doesn't exist :( 

Maybe I did something wrong ? Can anyone confirm that the method works ?

Also I am wandering if I can use somehow the ati 5650 proprietary driver when using the ati card. Is that posible ?

I also have a problem with the "Two finger scroll" on the touch pad. The option in mouse settings is disabled and for pretty much any other solution (including the one with xinput settings) my mouse becomes very jumpy once I put 2 fingers on the touch pad.
 Can anyone confirm that the "Two finger scroll" works ?

btw I use 64 bit ubuntu Ubuntu. Do you guys also use the 64bit version ?

Yeah, I use 64 bit. I have not experienced any odd things. I wont be expecting it either because I can use all the application I want today. Flash works, Java works with OpenJDk, all the compilers work great, and with wine 1.2 I can run alot of Windows games. Heroes of Newerth works like a charm in Linux, and what else can I ask for? :)

Regarding the multitouch difficulties;: [http://ubuntuforums.org/showpost.php?p=9372745&postcount=2](http://ubuntuforums.org/showpost.php?p=9372745&postcount=2)

It helped me.

---

### Post by phaedrus54 on 2010-10-24
Question:

Has anyone else had the GPU disabling code (ie the lenovo_acpi.c) stop working?  I upgraded my Ubuntu 10.10 kernel (now 2.6.35-22-generic #35-Ubuntu), recompiled and reapplied the kernel module. Now my battery usage seems to be back to prior usage levels (ie 2.5 hrs rather than my previous 5 hrs).

I'm using a HP Tm2t w/ a Radeon Mobility 4550 & Intel integrated graphics chip.

Any help or troubleshooting tips are appreciated.

-Cheers

---

### Post by mylan4 on 2010-10-26
I have Acer 3820TG (Core i5 430M with ATI 5650) and the newest Ubuntu 10.10.
When I disabled the ATI using these scripts: [http://ubuntuforums.org/showpost.php?p=7933876&postcount=11](http://ubuntuforums.org/showpost.php?p=7933876&postcount=11) with these modifications: [http://ubuntuforums.org/showpost.php?p=9446283&postcount=65](http://ubuntuforums.org/showpost.php?p=9446283&postcount=65) the first impression was fine - right fan slot was cold and battery life was over 5h, but the problem appeared - **sleep mode and hibernation stopped working** - my notebook either doesn't "fall asleep" or when it does it doesn't wake up. How come? Could anyone help me with this? Thanks. :(

---

### Post by hotwax on 2010-10-27
anyone willing to remote desktop with me and apply these changes to my acer 3820tg???? i cant seem to get it working. i have the ubuntu 10.10 2.6.35.22 kernel

---

### Post by f4lkon on 2010-11-08
@mylan4:

paste this into the terminal

sudo gedit /etc/modprobe.d/blacklist.conf 

and add following string at the end


blacklist radeon

reboot.

@hotwax

its really easy. do this

open up terminal and type

gedit timelinex_acpi.c

past following code inside and save.

```
/* 
 * timelinex_acpi.c
 * 
 * Linux kernel module that disables the discrete graphics board for Acer
 * Aspire TimelineX 3820TG (Core i5). Other TimelineX laptops could work, but I don't know.
 *
 * Based on the original lenovo_acpi.c by Sylvain Joyeux <sylvain.joyeux@m4x.org>, 2009
 */
#include <acpi/acpi.h>

MODULE_LICENSE("GPL");

static acpi_handle root_handle;

static int __init kill_ati(void)
{
    int i;
    acpi_status status;
    // The device handle
    acpi_handle handle;
    // The package elements
    union acpi_object package_elements[3];
    // The arguments to ATPX
    union acpi_object atpx_arg_elements[2];
    struct acpi_object_list atpx_arg;
    // For the return value of ATPX
    struct acpi_buffer buffer = { ACPI_ALLOCATE_BUFFER, NULL };

    status = acpi_get_handle(root_handle, "\\_SB.PCI0.P0P2.PEGP._OFF", &handle); //     status = acpi_get_handle(root_handle, "\\_SB_.PCI0.OVGA.ATPX", &handle);
    if (ACPI_FAILURE(status))
    {
        status = acpi_get_handle(root_handle, "\\_SB_.PCI0.OVGA.XTPX", &handle);
        if (ACPI_FAILURE(status))
        {
            printk("timelinex_acpi: cannot get ACPI handle: %s\n", acpi_format_exception(status));
            return -ENOSYS;
        }
        printk("timelinex_acpi: in discrete graphics mode\n");
        return 0;
    }

    for (i = 0; i < 3; ++i)
    {
        package_elements[i].type = ACPI_TYPE_INTEGER;
        package_elements[i].integer.value = 0;
    }

    atpx_arg.count = 0; //     atpx_arg.count = 2;
    atpx_arg.pointer = &atpx_arg_elements[0];

    atpx_arg_elements[0].type = ACPI_TYPE_INTEGER;
    atpx_arg_elements[0].integer.value = 2;

    atpx_arg_elements[1].type = ACPI_TYPE_PACKAGE;
    atpx_arg_elements[1].package.count = 3;
    atpx_arg_elements[1].package.elements = &package_elements[0];
    
    status = acpi_evaluate_object(handle, NULL, &atpx_arg, &buffer);
    if (ACPI_FAILURE(status))
    {
        printk("timelinex_acpi: ATPX method call failed: %s\n", acpi_format_exception(status));
        return -ENOSYS;
    }
    kfree(buffer.pointer);

    printk("timelinex_acpi: disabled the discrete graphics card\n");
    return 0;
}

static void dummy(void)
{
}

module_init(kill_ati);
module_exit(dummy);
```


then type in terminal 

gedit Makefile

and paste following code inside

```
ifneq ($(KERNELRELEASE),)
  obj-m := timelinex_acpi.o
else
  KERNELDIR ?= /lib/modules/$(shell uname -r)/build
  PWD := $(shell pwd)

default:
	$(MAKE) -C $(KERNELDIR) M=$(PWD) $(EXTRA_FLAGS) modules

clean:
	$(MAKE) -C $(KERNELDIR) M=$(PWD) $(EXTRA_FLAGS) clean

endif
```


save and paste in terminal 

make
sudo cp timelinex_acpi.ko /lib/modules/`uname -r`/kernel/
sudo depmod
echo timelinex_acpi | sudo tee -a /etc/modules > /dev/null

done.

dont forget to

paste this into the terminal

sudo gedit /etc/modprobe.d/blacklist.conf

and add following string at the end

---

### Post by hotwax on 2010-11-10
thanks for the reply f4lkon but when i try to save

sudo gedit modprobe.d/blacklist.conf

and add following string at the end
blacklist radeon

"could not find the file /home/manuel/modprobe.d/blacklist.conf
please type the file location correctly and try again"

---

### Post by f4lkon on 2010-11-11
the file blacklist.conf is in /etc/modprobe.d/

sudo gedit /etc/modprobe.d/blacklist.conf 

you are lookin in your home folder

---

### Post by hotwax on 2010-11-17
thanks f4lkon,finally got it to work :)

---

### Post by smokyink on 2010-11-26
Just wanted to check what minimal power usage do you guys get from powertop..

I have timelinex 3820tg and the lowest I ever get is 13 till 14W.

I have the descrete gpu off, usb ports, wifi and sound to powersave, hdd to powersave, bluetooth disabled, camera disabled, cpu governer on "on demand"... yet the 14W consumption yelds 4.5h of battery...

Is there any way to find out what is sucking the juice out of my battery ?

Any help is greatly appreciated :)

---

### Post by fhusexxx on 2010-12-11
Hello,

I tried to make the modules but I took this:

make -C /lib/modules/2.6.35-23-generic-pae/build M=/home/kex  modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-23-generic-pae'
make[2]: *** No rule to make target `/home/kex/timelinex_acpi.c', needed by `/home/kex/timelinex_acpi.o'.  Stop.
make[1]: *** [_module_/home/kex] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-23-generic-pae'
make: *** [default] Error 2

How can I solve this?

Thanks.

---

### Post by fhusexxx on 2010-12-13
> **fhusexxx said:**
> Hello,

I tried to make the modules but I took this:

make -C /lib/modules/2.6.35-23-generic-pae/build M=/home/kex  modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-23-generic-pae'
make[2]: *** No rule to make target `/home/kex/timelinex_acpi.c', needed by `/home/kex/timelinex_acpi.o'.  Stop.
make[1]: *** [_module_/home/kex] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-23-generic-pae'
make: *** [default] Error 2

How can I solve this?

Thanks.

Sorry! It was my fault misspelled the filename. :(

---

### Post by Korken on 2011-01-17
> **f4lkon said:**
> @mylan4:

paste this into the terminal

sudo gedit /etc/modprobe.d/blacklist.conf 

and add following string at the end


blacklist radeon

reboot.

@hotwax

its really easy. do this

open up terminal and type

gedit timelinex_acpi.c

past following code inside and save.

```
/* 
 * timelinex_acpi.c
 * 
 * Linux kernel module that disables the discrete graphics board for Acer
 * Aspire TimelineX 3820TG (Core i5). Other TimelineX laptops could work, but I don't know.
 *
 * Based on the original lenovo_acpi.c by Sylvain Joyeux <sylvain.joyeux@m4x.org>, 2009
 */
#include <acpi/acpi.h>

MODULE_LICENSE("GPL");

static acpi_handle root_handle;

static int __init kill_ati(void)
{
    int i;
    acpi_status status;
    // The device handle
    acpi_handle handle;
    // The package elements
    union acpi_object package_elements[3];
    // The arguments to ATPX
    union acpi_object atpx_arg_elements[2];
    struct acpi_object_list atpx_arg;
    // For the return value of ATPX
    struct acpi_buffer buffer = { ACPI_ALLOCATE_BUFFER, NULL };

    status = acpi_get_handle(root_handle, "\\_SB.PCI0.P0P2.PEGP._OFF", &handle); //     status = acpi_get_handle(root_handle, "\\_SB_.PCI0.OVGA.ATPX", &handle);
    if (ACPI_FAILURE(status))
    {
        status = acpi_get_handle(root_handle, "\\_SB_.PCI0.OVGA.XTPX", &handle);
        if (ACPI_FAILURE(status))
        {
            printk("timelinex_acpi: cannot get ACPI handle: %s\n", acpi_format_exception(status));
            return -ENOSYS;
        }
        printk("timelinex_acpi: in discrete graphics mode\n");
        return 0;
    }

    for (i = 0; i < 3; ++i)
    {
        package_elements[i].type = ACPI_TYPE_INTEGER;
        package_elements[i].integer.value = 0;
    }

    atpx_arg.count = 0; //     atpx_arg.count = 2;
    atpx_arg.pointer = &atpx_arg_elements[0];

    atpx_arg_elements[0].type = ACPI_TYPE_INTEGER;
    atpx_arg_elements[0].integer.value = 2;

    atpx_arg_elements[1].type = ACPI_TYPE_PACKAGE;
    atpx_arg_elements[1].package.count = 3;
    atpx_arg_elements[1].package.elements = &package_elements[0];
    
    status = acpi_evaluate_object(handle, NULL, &atpx_arg, &buffer);
    if (ACPI_FAILURE(status))
    {
        printk("timelinex_acpi: ATPX method call failed: %s\n", acpi_format_exception(status));
        return -ENOSYS;
    }
    kfree(buffer.pointer);

    printk("timelinex_acpi: disabled the discrete graphics card\n");
    return 0;
}

static void dummy(void)
{
}

module_init(kill_ati);
module_exit(dummy);
```


then type in terminal 

gedit Makefile

and paste following code inside

```
ifneq ($(KERNELRELEASE),)
  obj-m := timelinex_acpi.o
else
  KERNELDIR ?= /lib/modules/$(shell uname -r)/build
  PWD := $(shell pwd)

default:
	$(MAKE) -C $(KERNELDIR) M=$(PWD) $(EXTRA_FLAGS) modules

clean:
	$(MAKE) -C $(KERNELDIR) M=$(PWD) $(EXTRA_FLAGS) clean

endif
```


save and paste in terminal 

make
sudo cp timelinex_acpi.ko /lib/modules/`uname -r`/kernel/
sudo depmod
echo timelinex_acpi | sudo tee -a /etc/modules > /dev/null

done.

dont forget to

paste this into the terminal

sudo gedit /etc/modprobe.d/blacklist.conf

and add following string at the end
When I do this my screen goes black after reboot. I have a Acer TimelineX 3820TG wth i5 M430 CPU and Radeon HD 5470.
What am I doing wrong?

---

### Post by Marc128000 on 2011-01-18
Hello,
Thought I'd drop in and share some info. My laptop is an HP Envy 14. However it has the same graphics issues. You will NOT be able to use the ATI Catalyst drivers as of right now. They are simply not compatible with the switchable ('hybrid') graphics right now. 

The switchable graphics were designed to give a nice balance of power and battery life. The way its supposed to work is that during normal desktop browsing or when the GPU (discrete) graphics are not needed the higher powered graphics card is turned off. Once you start a game or other graphics intensive application the higher powered video card turns on and turns off the integrated (low power) card. This type of design currently only works well in windows. While using linux or Apple's OS x you must turn the card on, tell the system to switch then restart (log in/log out) the xserver.

Hope that was helpful.

On my blog I've got a tutorial on how to set this system up to work well under linux. The setup right now is mostly just to optimize battery life. I also have a post showing the power savings. It can easily make a 20w to 30w difference in power usage.

[http://linuxenvy.blogspot.com/](http://linuxenvy.blogspot.com/)

---

### Post by mino.sk on 2011-01-26
Well, I have Acer 3820TG (U 10.10 Maverick Meerkat) and have used this code: [http://ubuntuforums.org/showpost.php?p=9446283&postcount=65](http://ubuntuforums.org/showpost.php?p=9446283&postcount=65) as well as have blacklisted radeon - [http://ubuntuforums.org/showpost.php?p=10091777&postcount=90](http://ubuntuforums.org/showpost.php?p=10091777&postcount=90) and now everything works fine unless I hibernate - after restore, the Radeon graphics heats again - why? What keeps it turning on?

---

### Post by mino.sk on 2011-02-08
I have solved my problem by creating a file radeon in /etc/pm/sleep.d which contains this:
```

#!/bin/sh

case "$1" in
    thaw)
        modprobe -r lenovo_acpi
        modprobe lenovo_acpi      #restartuje modul lenovo_acpi => opat sa vykonaju prikazy vypinajuce Radeon
        ;;
esac

```This file is executed after wakeup from hibernation (S4). The module lenovo_acpi is "restarted" which means that commands powering the ATI card off contained in the module are executed again therefore solving the problem with heating!

Now I have only problem with duration of getting to and from hibernation - it takes about 3 minutes! (but has nothing to do with ATI imho)
//Solved too: TuxOnIce - [https://launchpad.net/~tuxonice/+archive/ppa]("https://launchpad.net/%7Etuxonice/+archive/ppa") - increased speed of hibernating rapidly! However, I needed to include lenovo_acpi in kernel again. But now, STR, hibernation etc. works, ATI is down... GREAT!

---

### Post by krestean on 2011-03-03
*wrong model*

---

### Post by vgdev on 2011-07-01
Is this thread closed?

Anyway i'd like to aske a few questions : ) I'm completly new to linux and ubuntu. I've just installed ubuntu 11.04 on my acer aspire 3820tg, but so far i have experienced  some problems with my system. 
- Radeon HD graphics-driver doesn't work properly
- I can't adjust background brightness 
- Switching between my two gpu-s isn't possible
- The computer uses way to much power when the battery is used a power-source

I know that there is a lot of information in this thread concerning these problems, but my understanding of ubuntu/linux isn't that good yet:confused:. I'd hope that someone could make a short summary or some kind of step-by-step guide (or a link to one), so it would be easier for me to make this work! :) That would be very helpful! Thanks!

---

### Post by Nittalope on 2012-11-02
Hi vgdev, it's been a long time, but if you are still interested:

- Radeon HD graphics-driver doesn't work properly: if nobody has news it will never really work properly. You should stick with the open drivers, which works quite well.
- adjusting brightness? You should open terminal and write:
> sudo gedit /etc/default/grub 

# just put this:

> #GRUB_CMDLINE_LINUX=""
GRUB_CMDLINE_LINUX="acpi_osi=Linux"

and then 

> sudo update-grub

and it will work after a restart.

Switching between the two gpu is not possible, but look for "switcharoo" on google and you'll find something. Usually you can turn off the ATI card to achieve better battery life.

Too much power consumtion? Look at the switcharoo, 'cause the ATI card is one of the problems, notably the biggest one.

Suerte!

---

