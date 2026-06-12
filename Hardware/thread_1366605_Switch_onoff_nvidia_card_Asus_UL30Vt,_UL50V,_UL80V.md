---
title: "Switch on/off nvidia card Asus UL30Vt, UL50V, UL80V laptops"
date: 2009-12-28
forum: Hardware
---

### Post by avilella on 2009-12-28
One of the Linux users has found a solution to switch off the nvidia card in the UL30Vt models, which by the looks of the DSDT tables, will also work for the UL50Vt and UL80Vt models with nvidia card.

If you are using Linux on an Asus UL30Vt, or Asus UL50Vt or Asus UL80Vt, keep reading...

For Ubuntu Karmic, download and install this package:

[http://launchpadlibrarian.net/38458054/nvidia-g210m-acpi-source_0.1.0-1%7Eppa-karmic_all.deb](http://launchpadlibrarian.net/38458054/nvidia-g210m-acpi-source_0.1.0-1%7Eppa-karmic_all.deb)

Then once installed, run the following command on a terminal:

    sudo modprobe nvidia_g210m_acpi

Explanation:

This method uses the ACPI P0P1.VGA._OFF method, which is the same for all 3 models.

The code file, "asus_nvidia.c" is derived from "lenovo_acpi.c" by Sylvain Joyeux.

Here is the original post and another one that adds hibernation support:
[http://forum.notebookreview.com/showpost.php?p=5663702&postcount=1239](http://forum.notebookreview.com/showpost.php?p=5663702&postcount=1239)
[http://forum.notebookreview.com/showpost.php?p=5664880&postcount=1244](http://forum.notebookreview.com/showpost.php?p=5664880&postcount=1244)

asus_nvidia.c
========================================================
#include <acpi/acpi.h>
#include <linux/suspend.h>

MODULE_LICENSE("GPL");

static acpi_handle root_handle;

static int kill_nvidia(void)
{
    acpi_status status;
    // The device handle
    acpi_handle handle;
    struct acpi_object_list args;
    // For the return value
    struct acpi_buffer buffer = { ACPI_ALLOCATE_BUFFER, NULL };

    status = acpi_get_handle(root_handle, "\\_SB.PCI0.P0P1.VGA._OFF", &handle);
    if (ACPI_FAILURE(status))
    {
        printk("%s: cannot get ACPI handle: %s\n", __func__, acpi_format_exception(status));
        return -ENOSYS;
    }

    args.count = 0;
    args.pointer = NULL;

    status = acpi_evaluate_object(handle, NULL, &args, &buffer);
    if (ACPI_FAILURE(status))
    {
        printk("%s: _OFF method call failed: %s\n", __func__, acpi_format_exception(status));
        return -ENOSYS;
    }
    kfree(buffer.pointer);

    printk("%s: disabled the discrete graphics card\n",__func__);
    return 0;
}

static int power_event(struct notifier_block *this, unsigned long event,
                       void *ptr)
{
        switch (event) {
        case PM_POST_HIBERNATION:
                kill_nvidia();
                return NOTIFY_DONE;
        case PM_POST_SUSPEND:
        case PM_HIBERNATION_PREPARE:
        case PM_SUSPEND_PREPARE:
        default:
                return NOTIFY_DONE;
        }
}

static struct notifier_block power_notifier = {
        .notifier_call = power_event,
};

static int __init asus_nvidia(void)
{
    int ret = register_pm_notifier(&power_notifier);
    if (ret) return ret;
    return kill_nvidia();
}

static void dummy(void)
{
}

module_init(asus_nvidia);
module_exit(dummy);
========================================================

Makefile
========================================================
ifneq ($(KERNELRELEASE),)
  obj-m := asus_nvidia.o
else
  KERNELDIR ?= /lib/modules/$(shell uname -r)/build
  PWD := $(shell pwd)

default:
        $(MAKE) -C $(KERNELDIR) M=$(PWD) $(EXTRA_FLAGS) modules

clean:
        $(MAKE) -C $(KERNELDIR) M=$(PWD) $(EXTRA_FLAGS) clean

endif
========================================================

To compile it, simply run:

Code:

make

To install it, run as root:
Code:

cp asus_nvidia.ko /lib/modules/`uname -r`/kernel/
depmod

To try it out, run as root:
Code:

modprobe asus_nvidia

To load it on each reboot on Ubuntu, run as root:
Code:

echo asus_nvidia >>/etc/modules

That last step will be different on other distros, e.g., on Gentoo you need to append the module name to /etc/modules.autoload.d/kernel-2.6.

---

### Post by fungi on 2009-12-28
Thanks! good find.

On related note, the screen brightness issue, just noticed that the brightness controls work in splashtop.

---

### Post by elchicosinhada on 2009-12-28
Great :D
Works perfect in UL50VT with Debian.

---

### Post by tomsecret on 2009-12-31
Thanks alot, makes choosing my next laptop alot easier :)

---

### Post by blackmoon105 on 2010-01-04
Hi, I've make a .deb package (based on the source posted above) for nVidia GeeForce G210M module switch-off for Asus UL30VT, UL50V, UL80V laptops.

I don't have an Asus UL*0V yet, so please test it. Any feedback are welcome.

[http://www.sendspace.com/file/jfzr7x](http://www.sendspace.com/file/jfzr7x)
MD5: **c418685c256ba4fc52970a2df2802ecf**

---

### Post by P.Kosunen on 2010-01-04
How do i switch nvidia on?

Edit: ... It is on by default, problem is to get it route picture to the display (and disable Intel?).

---

### Post by randomas on 2010-01-05
Wow, great news, will test asap!

But, erm yes indeed, has anyone managed to get the nvidia card to work at all?

---

### Post by fungi on 2010-01-07
Don't think nvidia driver supports hybrid graphics under linux.

- [http://www.nvnews.net/vbulletin/showthread.php?t=110920&highlight=hybrid+power&page=3](http://www.nvnews.net/vbulletin/showthread.php?t=110920&highlight=hybrid+power&page=3)
- [http://www.nvnews.net/vbulletin/showthread.php?t=116088](http://www.nvnews.net/vbulletin/showthread.php?t=116088)

If im not mistaken and this is still the case we should probably poke nvidia with a stick until they cough something up.

---

### Post by hadi2 on 2010-01-15
hi 
Does this code work for me too ?
I have a dell studio xps1340 with G210m as the discrete card .
Can i switch it off this way ?

Thanks

---

### Post by marcjank on 2010-01-16
> **blackmoon105 said:**
> Hi, I've make a .deb package (based on the source posted above) for nVidia GeeForce G210M module switch-off for Asus UL30VT, UL50V, UL80V laptops.

I don't have an Asus UL*0V yet, so please test it. Any feedback are welcome.

[http://www.sendspace.com/file/jfzr7x](http://www.sendspace.com/file/jfzr7x)
MD5: **c418685c256ba4fc52970a2df2802ecf**


The deb didn't work for me.
Here's the last few lines from it:

depmod....

DKMS: install completed.
FATAL: Module rt73 not found.
dpkg: error processiong nvidia-g210m-acpi-source (--install):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 nvidia-g210m-acpi-source


Also, I'm pretty new to linux and have always had trouble getting make to work.
I made a directory with asus_nvidia.c and Makefile, with the code copied and pasted from above.  When I cd to the directory and run make, all I get is:
make: Nothing to be done for `default'.
Should I modify the make file?  I'm not sure what the code in it does.

Can someone help me out?  I'd love to get this nvidia card turned off until they have good drivers.

Thanks,
Marc

---

### Post by avilella on 2010-01-18
That's weird. If you manually download the deb file, then copy it into a new directory, then do:

ar x *.deb

then

tar xzf data.tar.gz

then go to the place where the nvidia-*.tar.gz file is

then 

tar xzf nvidia-*.tar.gz

then go to the place with the code, and run:

make

what is the result of the make command?

> **marcjank said:**
> The deb didn't work for me.
Here's the last few lines from it:

depmod....

DKMS: install completed.
FATAL: Module rt73 not found.
dpkg: error processiong nvidia-g210m-acpi-source (--install):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 nvidia-g210m-acpi-source


Also, I'm pretty new to linux and have always had trouble getting make to work.
I made a directory with asus_nvidia.c and Makefile, with the code copied and pasted from above.  When I cd to the directory and run make, all I get is:
make: Nothing to be done for `default'.
Should I modify the make file?  I'm not sure what the code in it does.

Can someone help me out?  I'd love to get this nvidia card turned off until they have good drivers.

Thanks,
Marc

---

### Post by Anjrew on 2010-01-19
> **marcjank said:**
> The deb didn't work for me.
Here's the last few lines from it:

depmod....

DKMS: install completed.
FATAL: Module rt73 not found.
dpkg: error processiong nvidia-g210m-acpi-source (--install):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 nvidia-g210m-acpi-source


Also, I'm pretty new to linux and have always had trouble getting make to work.
I made a directory with asus_nvidia.c and Makefile, with the code copied and pasted from above.  When I cd to the directory and run make, all I get is:
make: Nothing to be done for `default'.
Should I modify the make file?  I'm not sure what the code in it does.

Can someone help me out?  I'd love to get this nvidia card turned off until they have good drivers.

Thanks,
Marc


I'm having the same problem with the make command here.  What are we doing wrong?  Any help for a linux newbie would be great, would love the get the battery lasting longer in Ubuntu with this laptop.

I have the UL50Vt, in case that ends up being an issue.

---

### Post by phnom on 2010-01-20
I can't get this to work, when I try make it says "make: Nothing to be done for `default'."

I also tried the deb but no luck, I get:

>>
DKMS: install Completed.
FATAL: Module rt73 not found.
dpkg: error processing nvidia-g210m-acpi-source (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 nvidia-g210m-acpi-source
>>

---

### Post by marcjank on 2010-01-20
From terminal:

marc@marc-laptop:~/Documents/usr/src/dkms_source_tree$ make
make -C /lib/modules/2.6.31-17-generic/build M=/home/marc/Documents/usr/src/dkms_source_tree modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-17-generic'
  CC [M]  /home/marc/Documents/usr/src/dkms_source_tree/nvidia_g210m_acpi.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/marc/Documents/usr/src/dkms_source_tree/nvidia_g210m_acpi.mod.o
  LD [M]  /home/marc/Documents/usr/src/dkms_source_tree/nvidia_g210m_acpi.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-17-generic'
marc@marc-laptop:~/Documents/usr/src/dkms_source_tree$

Well how about that.  Thank you.

> **avilella said:**
> That's weird. If you manually download the deb file, then copy it into a new directory, then do:

ar x *.deb

then

tar xzf data.tar.gz

then go to the place where the nvidia-*.tar.gz file is

then 

tar xzf nvidia-*.tar.gz

then go to the place with the code, and run:

make

what is the result of the make command?

---

### Post by marcjank on 2010-01-20
After a successful make, I ran (as root):

cp nvidia_g210m_acpi /lib/modules/$(uname -r)/kernel/
depmod

modprobe nvidia_g210m_acpi

echo nvidia_g210m_acpi >>/etc/modules


I saw an immediate jump in battery life from <4hrs to 5 hours and 45 minutes on the UL50VT.

When they do get hybrid SLI nvidia drivers, I should be able to re-enable my video card by just removing nvidia_g210m_acpi from /etc/modules and restarting, correct?  Or would I want to run a modprobe -r nvidia_g210m_acpi?

I suppose it'd be good to retain the ability to turn off the card for a while.

Thanks again for the help.
I hope all the other ASUS fans get this working as well.

Marc

> **marcjank said:**
> From terminal:

marc@marc-laptop:~/Documents/usr/src/dkms_source_tree$ make
make -C /lib/modules/2.6.31-17-generic/build M=/home/marc/Documents/usr/src/dkms_source_tree modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-17-generic'
  CC [M]  /home/marc/Documents/usr/src/dkms_source_tree/nvidia_g210m_acpi.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/marc/Documents/usr/src/dkms_source_tree/nvidia_g210m_acpi.mod.o
  LD [M]  /home/marc/Documents/usr/src/dkms_source_tree/nvidia_g210m_acpi.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-17-generic'
marc@marc-laptop:~/Documents/usr/src/dkms_source_tree$

Well how about that.  Thank you.

---

### Post by marcjank on 2010-01-22
I've noticed that the video card turns back on whenever I come back from a suspend/hibernate.

Has anybody else noticed this?

Marc

---

### Post by Anjrew on 2010-01-22
I posted that I couldn't get the same results as Marc, but figured out I can't have a space in any of my folder names, once I took that out I got the same results.

---

### Post by Anjrew on 2010-01-22
> **marcjank said:**
> I've noticed that the video card turns back on whenever I come back from a suspend/hibernate.

Has anybody else noticed this?

Marc

From what it seems, the deb file code is the code before the suspend part was added.  Really I'm just hoping someone can explain me through the original instructions with getting the "nothing to be done for 'default' " error.  It seems that would solve our suspend problem with it.

---

### Post by randomas on 2010-01-22
I have the exact same problem with the .deb I even tried installing the rt73 stuff, but still no good.

---

### Post by randomas on 2010-01-22
Ok I tried a bit harder. The original code in the first post doesn't build for me, it gives me a nothing to be done for default ...

I managed to build and install successfully by opening the deb file in archive manager and extracting the makefile and nvidia_g210m_acpi.c from there, make make install and modprobe worked after that.

Hope this helps.

---

### Post by johncudd on 2010-01-26
Okay well I successfully did make, make install. But I'm not sure how to use modprobe.

---

### Post by avilella on 2010-01-29
There is now a new package that doesn't have the weird rt73 dependency:

[http://launchpadlibrarian.net/38458054/nvidia-g210m-acpi-source_0.1.0-1%7Eppa-karmic_all.deb](http://launchpadlibrarian.net/38458054/nvidia-g210m-acpi-source_0.1.0-1%7Eppa-karmic_all.deb)

Install and then run the following line to switch off:

sudo modprobe asus_nvidia

---

### Post by blum on 2010-01-29
OK so I have turned off my Nvidia card. But I still can't control the backlight - which seames like it is allways turned up to the max :-(

Anyone had any luck with controling the backlight?

---

### Post by luizfar on 2010-02-08
> **hadi2 said:**
> hi 
Does this code work for me too ?
I have a dell studio xps1340 with G210m as the discrete card .
Can i switch it off this way ?

Thanks

I have a xps1340 with the 9500m.
Yesterday I was trying to modify the code to turn off the discrete card on  my computer but I couldn't. I managed to turn off the integrated card though :D :D :D

I think tonight I will try to work on it a little bit more.
Did you try running the code for asus on your machine?

---

### Post by JuckNorris on 2010-02-15
Hi, I have a few questions regarding the Asus UL80V, is it possible to use the nvidia card internally with the display?
I tried installing the latest nvidia driver on my asus ul80v but only get a black screen after rebooting. The only driver that somewhat works is the intel driver (even though it also has lots of bugs it seems :(

Does anyone have this work? and if how?

The topic Switch on/off nvidia card is a bit confusing here :/

---

### Post by dakilla on 2010-02-23
now i have installed the deb pkg, so what do i have to do to turn on the graphic card?

 modprobe nvidia_g210m_acpi

turned it off.

 modprobe -r nvidia_g210m_acpi ??
didnt seam to do anything. do i have to restart my computer to get it started again?
and does anyone have a working driver?

---

### Post by ubuntoide on 2010-02-25
after suspend the driver delivered here, seems to not turn off the Nvidia card. Take a look at powertop to notice that. It is necessary to run rmmod nvidia_g210m_acpi and then reload the driver with modprobe to properly turn off the card. Never tried Hibernation anyway..

I installed the package in 3rd page.

Any solutions?

---

### Post by laramichaels1978 on 2010-03-04
To the owners of Asus UL30/50/80vt machines: could you please clarify whether you are able to use the nvidia card on your laptop **at all** under Linux? Can it always be enabled/disabled in the BIOS, eg?

Is this just an issue of "hot-switching" between Intel<-> Nvidia graphics while the machine is running or are you simply stuck with only using the Intel card under Linux?

Thank you for any information

~lara

---

### Post by ubuntoide on 2010-03-05
The Nvidia Card can't be disabled from the bios and the Nvidia closed-source blob doesn't support it.
We are all stuck with the Intel card alone, with the nvdia turned off thanks to the driver provided in this thread.
The upcoming Ubuntu will bring some support thanks to the Nouveau driver, nothing stellar anyway, just 2D.

---

### Post by bander013 on 2010-03-21
its strange, i think, but thus modu does not work with 2.6.33 kernell, gentoo, UL30

---

### Post by ubuntoide on 2010-03-21
any errors when loading the module?

---

### Post by McEye on 2010-03-23
The module seems to be working under 10.04 (Lucid) Beta 1 as well.

cheers
Mc

---

### Post by t0lkman on 2010-03-24
> **avilella said:**
> There is now a new package that doesn't have the weird rt73 dependency:

[http://launchpadlibrarian.net/38458054/nvidia-g210m-acpi-source_0.1.0-1%7Eppa-karmic_all.deb](http://launchpadlibrarian.net/38458054/nvidia-g210m-acpi-source_0.1.0-1%7Eppa-karmic_all.deb)

Install and then run the following line to switch off:

sudo modprobe asus_nvidia



you probably meant sudo modprobe nvidia_g210m_acpi,
does it disable nvidia g210 or enable?

because actually what I want it's enable  nvidia based video card, because I can't watch HD movies (1080p) it like slide show, though when I watch it in windows (I have dual boot) everything ok

---

### Post by dakilla on 2010-05-02
Works fine on 10.04.
i just got my g210m to work on ubuntu 9.10 on a asus ul30vt.
checking the status on 10.04. will be back with a simple howto soon.

**UPDATE:**

to get the nvidia card to work you have to do this:

this is how you get g210m to work on ubuntu 9.10 / 10.04.

1. download and install nvidia drivers. (i have only tested the ones in the repos)

2. make sure you got an Xorg.conf that is correct. ( if not, run nvidia-xconfig )

3. reboot into bios (press delete while booting)

4. change the SATA option in the bios from enhanced to compatibility. ( yea, this makes sense? NOT! )

5. boot into linux and smile!

---

### Post by marcjank on 2010-05-02
Hey Dakilla,

This sounds promising!
Did you use the proprietary drivers or Nouveou?

Thanks for letting us know,
Marc

---

### Post by dakilla on 2010-05-05
i use nvidias drivers from the repo.

---

### Post by dthoaforum on 2010-05-08
I always get a black screen after this command :(
sudo modprobe nvidia_g210m_acpi

I have UL30VT-A1 with Ubuntu 10.04 - 64 bits
Could someone please tell me what's wrong?

---

### Post by w116tjb on 2010-05-11
> **dakilla said:**
> Works fine on 10.04.
i just got my g210m to work on ubuntu 9.10 on a asus ul30vt.
checking the status on 10.04. will be back with a simple howto soon.

**UPDATE:**

to get the nvidia card to work you have to do this:

this is how you get g210m to work on ubuntu 9.10 / 10.04.

1. download and install nvidia drivers. (i have only tested the ones in the repos)

2. make sure you got an Xorg.conf that is correct. ( if not, run nvidia-xconfig )

3. reboot into bios (press delete while booting)

4. change the SATA option in the bios from enhanced to compatibility. ( yea, this makes sense? NOT! )

5. boot into linux and smile!

I can confirm that this fix worked for my UL30VT-A1. :P

One point of clarification is that booting into the BIOS requires holding F2, not Delete.

---

### Post by marcjank on 2010-05-15
Just tried the sata-compatability fix with a UL-50VT.
Was able to get to the login screen, but upon logging in, the screen froze up, turned into a jumble of boxes, and saw occasional snow.  I have not overclocked the card in any way.

Marc

---

### Post by karl3 on 2010-05-18
> **dthoaforum said:**
> I always get a black screen after this command :(
sudo modprobe nvidia_g210m_acpi 

I have UL30VT-A1 with Ubuntu 10.04 - 64 bits
Could someone please tell me what's wrong?

samo problem, also 64 bit 10.04

---

### Post by ckankiewicz on 2010-05-18
What kind of batery life do you get with the Nvidia card enabled? I'm getting 4+ hours with it disabled.

---

### Post by karl3 on 2010-05-19
about the same, a bit more than 4 hours.

however, i have a workaround idea: what do you think about installing lxde version of debian on an sd card? 

i'm thinking about using ubuntu & nvidia as my default system, and booting sd card only when you need more than 4 hours of battery life.

how much do you think sd card (instead of hard drive), GMA45, and lxde (instead of gnome) would improve battery life?

---

### Post by ckankiewicz on 2010-05-21
> **dakilla said:**
> Works fine on 10.04.
i just got my g210m to work on ubuntu 9.10 on a asus ul30vt.
checking the status on 10.04. will be back with a simple howto soon.

**UPDATE:**

to get the nvidia card to work you have to do this:

this is how you get g210m to work on ubuntu 9.10 / 10.04.

1. download and install nvidia drivers. (i have only tested the ones in the repos)

2. make sure you got an Xorg.conf that is correct. ( if not, run nvidia-xconfig )

3. reboot into bios (press delete while booting)

4. change the SATA option in the bios from enhanced to compatibility. ( yea, this makes sense? NOT! )

5. boot into linux and smile!


Confirmed working on my UL80VT.

---

### Post by MikeRostermund on 2010-05-25
I want to use the X4500MHD and HDMI output, is that something anyone tried?
Maybe it works if I use that 'hack' to activate the discrete graphics, but I don't want to use it. I just want to stick with the Intel graphics. Is this even possible?

---

### Post by sokekoke on 2010-06-11
> **dakilla said:**
> Works fine on 10.04.
i just got my g210m to work on ubuntu 9.10 on a asus ul30vt.
checking the status on 10.04. will be back with a simple howto soon.

**UPDATE:**

to get the nvidia card to work you have to do this:

this is how you get g210m to work on ubuntu 9.10 / 10.04.

1. download and install nvidia drivers. (i have only tested the ones in the repos)

2. make sure you got an Xorg.conf that is correct. ( if not, run nvidia-xconfig )

3. reboot into bios (press delete while booting)

4. change the SATA option in the bios from enhanced to compatibility. ( yea, this makes sense? NOT! )

5. boot into linux and smile!

So.. i just installed ubuntu on my UL80VT,first time using linux.

In step 1. when its said to install nvidia drivers from repos,how can i do that exactly?
I'm guessing i need to find the correct driver with synaptic, right?

 - Before this post i tried "system > administrator > hardware drivers" this will result in black screen on boot.

thanks

---

### Post by mediamind on 2010-06-11
> In step 1. when its said to install nvidia drivers from repos,how can i do that exactly?
I'm guessing i need to find the correct driver with synaptic, right?

- Before this post i tried "system > administrator > hardware drivers" this will result in black screen on boot.

Installing the Nvidia driver via the hardware drivers menu is the correct method. It's vital that you reboot and press F2 (not Delete) to enter the BIOS and select: Advanced > IDE Configuration > SATA Operation Mode. Change the configuration from "Enhanced" to "Compatible." Press F10 to save and exit. 

Keep in mind that booting under "Compatible" mode degrades the I/O performance of the hard drive. This means your system will be slower at boot up and also slower to resume from suspend (20-30 seconds). On the positive, running the Nvidia driver/card seems to shut off the Intel card which helps improve battery performance. You can confirm this by opening a terminal and entering:

```
lspci |grep VGA
```

I've yet to get the brightness keys working under the Nvidia driver - has anyone managed to fix this? My workaround for now is to add the Brightness Applet to the panel - here's a [**link to the instructions** ]("http://ubuntuforums.org/showpost.php?p=9351306&postcount=119") if you're interested.

---

### Post by manco1911 on 2010-06-16
Hi all, 

Im a bit new on deep comand line configuration.. so.. questions:
First:

After installing nvidia drivers (from System>Administration>Hardware Drivers) I got the big blank screen. 

How can i revert this ? first time i just reinstall the hole system, since it was a fresh install it didnt bother.. but i rather not do that now.. so, if someone could tell me that.. much thanks.

Second:
> **avilella said:**
> There is now a new package that doesn't have the weird rt73 dependency:

[http://launchpadlibrarian.net/38458054/nvidia-g210m-acpi-source_0.1.0-1%7Eppa-karmic_all.deb](http://launchpadlibrarian.net/38458054/nvidia-g210m-acpi-source_0.1.0-1%7Eppa-karmic_all.deb)

Install and then run the following line to switch off:

sudo modprobe asus_nvidia
Can someone confirm this is working for Ubuntu 10.04 64bits ??

Third:

Also about 10.04 64bits, has anyone tried "Dakilla" solution on 10.04 64bits system ?

Thanks in advance guys, 
and great work btw.. awesome you got it running on some systems.:p

---

### Post by hojgaard on 2010-06-16
Im running lucid 64 bit on my new ul30vt, but when i use the:

sudo modprobe nvidia_g210m_acpi

i get a blank screen. Does this just not work on 64 bit??

---

### Post by tomsecret on 2010-06-16
> **manco1911 said:**
> 
Second:

Can someone confirm this is working for Ubuntu 10.04 64bits ??


It does, I  updated the deb-package according to [http://www.mail-archive.com/asus-ul30@lists.launchpad.net/msg00104.html](http://www.mail-archive.com/asus-ul30@lists.launchpad.net/msg00104.html) so suspend/resume is supported. Maybe it is supported in the package you point to?

> **manco1911 said:**
> 
Third:

Also about 10.04 64bits, has anyone tried "Dakilla" solution on 10.04 64bits system ?



I tried it and it works on ubuntu lucid 64-bit, but I reinstalled and haven't used it since, as I don't need the nvidia card as long as there is no support for hotswitching (yet).

---

### Post by tomsecret on 2010-06-16
> **hojgaard said:**
> Im running lucid 64 bit on my new ul30vt, but when i use the:

sudo modprobe nvidia_g210m_acpi

i get a blank screen. Does this just not work on 64 bit??

I'm also on a ul30vt 64-bit ubuntu lucid, and it works here. Strange :-k. Are you sure you're not using the nvidia card?

---

### Post by hojgaard on 2010-06-16
> **tomsecret said:**
> I'm also on a ul30vt 64-bit ubuntu lucid, and it works here. Strange :-k. Are you sure you're not using the nvidia card?

Now i got it figured out... i had changed the bios settings..

Has anyone got compiz working on the intel gpu on ul30vt?

---

### Post by sokekoke on 2010-06-16
I hope someone finds a solution to making brightness +/- keys work for ausu UL series on ubuntu 10.04 i got some ebooks i need to read for an upcomming exam and screen is so brighttt! :)

---

### Post by mediamind on 2010-06-16
> I hope someone finds a solution to making brightness +/- keys work for ausu UL series on ubuntu 10.04 i got some ebooks i need to read for an upcomming exam and screen is so brighttt!

If you're using the Nvidia driver/card, as a workaround you can add the "Brightness Applet" to your panel to control the screen brightness. See [**my post on the "UL30 anyone?" thread**]("http://ubuntuforums.org/showpost.php?p=9352635&postcount=121") for more info.

---

### Post by sokekoke on 2010-06-16
> **mediamind said:**
> If you're using the Nvidia driver/card, as a workaround you can add the "Brightness Applet" to your panel to control the screen brightness. See [**my post on the "UL30 anyone?" thread**]("http://ubuntuforums.org/showpost.php?p=9352635&postcount=121") for more info.

Haha thats great! thanks for sharing, my eyes thank you :)

---

### Post by j.long on 2010-06-29
> **dakilla said:**
> Works fine on 10.04.

**UPDATE:**

to get the nvidia card to work you have to do this:

this is how you get g210m to work on ubuntu 9.10 / 10.04.

1. download and install nvidia drivers. (i have only tested the ones in the repos)

2. make sure you got an Xorg.conf that is correct. ( if not, run nvidia-xconfig )

3. reboot into bios (press delete while booting)

4. change the SATA option in the bios from enhanced to compatibility. ( yea, this makes sense? NOT! )

5. boot into linux and smile!

Confirmed on my UL50VT.  Also confirmed about pressing F2 instead of "del".

Thanks dakilla, I've tried quite a few things and finally this obscure bios setting worked.

---

### Post by Richardarkless on 2010-07-01
Hi im thinking about getting a ul80vt

I got some questions

How do I switch between the graphics cards and does this work in Ubuntu 10.04 (64bit)

What does and doesn't work with this model and what is the solutions to these problems

I really like this laptop because of the great battery life which is perfect as im going to university (UK version of university) in September

---

### Post by ckankiewicz on 2010-07-01
> **Richardarkless said:**
> Hi im thinking about getting a ul80vt
How do I switch between the graphics cards and does this work in Ubuntu 10.04 (64bit)

You can't switch, not on the fly anyway.  You have to change a bios setting (stated earlier in this thread) and install/uninstall nvidia drivers (if you want to use them) to switch between the cards.

> **Richardarkless said:**
> What does and doesn't work with this model and what is the solutions to these problems

The only thing I've found that doesn't work at all are the brightness hotkeys.  They make the brightness meter move but don't actually affect screen brightness.  I still haven't found a solution for this (please PM if you have one) and it bugs me all the time. But for that being the only unsolved problem with this laptop I'm rather satisfied.

Also, with the Nvidia card turned off using the method in this thread, I easily get 4-6 hours battery life.

---

### Post by Richardarkless on 2010-07-01
> **ckankiewicz said:**
> You can't switch, not on the fly anyway.  You have to change a bios setting (stated earlier in this thread) and install/uninstall nvidia drivers (if you want to use them) to switch between the cards.



The only thing I've found that doesn't work at all are the brightness hotkeys.  They make the brightness meter move but don't actually affect screen brightness.  I still haven't found a solution for this (please PM if you have one) and it bugs me all the time. But for that being the only unsolved problem with this laptop I'm rather satisfied.

Also, with the Nvidia card turned off using the method in this thread, I easily get 4-6 hours battery life.

ok thanks so if I set the nvidia card in the bios then it will turn the intergrated one off and turn on the nvidia one and vice versa

out of curiosity what is the integraed graphics card that is in the laptop (intel, nvidia or ati)

As for the brightness keys not working, does the applet work or isnt it seeing it capable of the brightness being changed

EDIT: I may just leave windows 7 on the laptop (instead of having ubuntu installed and xp in a vm) as it seems too much hastle, hopefully it gets less troublesome in future versions plus most of my course needs windows only apps anyway

Will still be using ubuntu on my desktop anyway

---

### Post by stub on 2010-07-07
Has anyone built a .deb or got a PPA with the patched kernel module that works with suspend/resume?

---

### Post by Ashen001 on 2010-07-13
Your post is a very useful one. Laptops are highly in demand in today&#8217;s world. You have to consider several factors prior to the purchase. Make sure that the system has the power, memory and capabilities that can meet your needs. Online research may help you to sort out any queries regarding the same.

---

### Post by Hobbes on 2010-07-22
> **stub said:**
> Has anyone built a .deb or got a PPA with the patched kernel module that works with suspend/resume?


*bump*

I am on maverick meerkat now too, don't know if that will change anything, but it made the nvidia option unusable with lag and stuff (probably the new driver and the weird gtk glitches people have been having)...

in short, I want to shut off my nvidia card again :(  hehe.

---

### Post by avilella on 2010-07-23
There is now one:

[http://linux-hybrid-graphics.blogspot.com/2010/07/how-to-test-nouveau-nvidia-hybrid.html](http://linux-hybrid-graphics.blogspot.com/2010/07/how-to-test-nouveau-nvidia-hybrid.html)

> **stub said:**
> Has anyone built a .deb or got a PPA with the patched kernel module that works with suspend/resume?

---

### Post by P.Kosunen on 2010-07-28
[http://en.gentoo-wiki.com/wiki/Vga_switcheroo](http://en.gentoo-wiki.com/wiki/Vga_switcheroo)

Anyone got this vgaswitcheroo thing working with UL-series laptop?

---

### Post by GxxP on 2010-07-29
Hello,

I'm a new owner of a Asus UL30VT and I have some problems with the nvidia graphic card and the brightness.

I installed the script and I did sudo modprobe nvidia_g210m_acpi. There is no error reported so I think it goes well but how can I check that the nvidia card is off ?
Do I have to use the script every time I reboot ? And every time I use the hibernation ?

I tried to use the brightness applet from gnome but it doesn't work :(. How can I do ?

Thanks a lot ;).

PS : Sorry for all the mistakes, I don't speak english as well as I wish :s.

---

### Post by Hobbes on 2010-08-02
It doesn't work after suspend (not sure about hibernation), at least for me.  Supposedly there is a way to make it work but I just have the .deb installed and I don't think that version works after suspend.

You can check by either checking your battery icon before and after you run it (should increase battery estimate by a couple hours), or by running "sudo powertop" in the terminal if you have it installed.  Should be less power usage.

---

### Post by Sphaerophoria on 2010-08-03
A few comments....

1) GREAT work! Thanks a lot this saved me hours of battery life

2) A really easy way to check if its on or off is to hit the brightness keys... if a libnotify popup comes up the card is on if no popup happens the card is off (at least that's my experience)

3) Has anyone managed to get this working under kernel 2.6.35? I switched to it because i was getting screen flickers on the intel card on the other kernels however when i try to use this mod on kernel 2.6.35 the laptop crashes.

Thanks a lot for your help :)

Sphaerophoria

---

### Post by mpw on 2010-08-17
Hello,
 
I just got my UL30VT and I installed Ubuntu 10.04. After installing ubuntu wants to install the nvidia propretary drivers. I installed them and Ubuntu doesn't boot any more. The screen stays black and ctrl+alt+del shuts the pc down. System seems to work, but no screen output. And I can't switch to a terminal (ctrl+alt+f1)
 
Is this because the Intel is activated and Ubuntu tries using the Nvidia?
 
Is there anyway to reactivate the Ubuntu drivers? Maybe by changing some config files from a live session?
 
Thanks for help!
 
Bye
MPW

---

### Post by ckankiewicz on 2010-08-17
> **mpw said:**
> Hello,
 
I just got my UL30VT and I installed Ubuntu 10.04. After installing ubuntu wants to install the nvidia propretary drivers. I installed them and Ubuntu doesn't boot any more.

Boot into your laptops BIOS and change the SATA mode from Enhanced to Compatibility.  That should fix your problem.

---

### Post by insulae on 2010-08-29
I Have the UL80VT-A1 and i have a problem, i am using nvidia_g210m_acpi  to disable nvidia card, work perfectly (5.5~8.8W power usage).
But if the notebook go to suspend and then back, the nvidia is UP again (more than 10W power usage), I solve this problem doing:

rmmod nvidia_g210m_acpi
modprobe nvidia_g210m_acpi

After that everything work great again, NO nvidia power consumption. But if the notebook go to suspend again FAIL, freezing the laptop. Any solution for this problem?

THANKS! (With nvidia_g210m_acpi I have 10 hours of battery [8cells x 5200mAh] yeaaa!!)

---

### Post by Sphaerophoria on 2010-09-01
> **insulae said:**
> I Have the UL80VT-A1 and i have a problem, i am using nvidia_g210m_acpi  to disable nvidia card, work perfectly (5.5~8.8W power usage).
But if the notebook go to suspend and then back, the nvidia is UP again (more than 10W power usage), I solve this problem doing:

rmmod nvidia_g210m_acpi
modprobe nvidia_g210m_acpi

After that everything work great again, NO nvidia power consumption. But if the notebook go to suspend again FAIL, freezing the laptop. Any solution for this problem?

THANKS! (With nvidia_g210m_acpi I have 10 hours of battery [8cells x 5200mAh] yeaaa!!)

don't use the deb with sleep support... i built the original and used the same command you did... it claims to add sleep support but all it does is break it so don't use it ;)

---

### Post by Sandra121289 on 2010-09-12
I have got an Asus UL80VT. But now after using modprobe nvidia_g210m_acpi
I only got a black/blank screen. I already tried switching the Sata Compabitility Mode in the BIOS but my problem stays.

Could it be, that the modprobe thing only works when the NVidia Drivers are not installed? Because I actually have them installed.

Do you maybe have an idea to get the whole modprobe thing reverted? Sorry, I'm still a Linux beginner  :-?

---

### Post by ubuntoide on 2010-09-12
First of all the nvidia_g210_acpi shuts off the nvida card itself, so if have nvidia binaries installed and Sata on Compatibility, it actually means that you are USING that card. Turning it off when is running, is not a nice idea ;)
Anyway, if you want to use only the Intel card, you have to uninstall the nvidia drivers and restore the Sata option on Advanced. 
Anyway, how did you installed the modprobe module? Via .deb or by compiling it yourself?

---

### Post by Sandra121289 on 2010-09-12
Yeah I did just that, turning it off, when it was running xD

I used the .deb .

Thanks for your reply!

---

### Post by ubuntoide on 2010-09-12
is it all ok now? 
Anyway, take a look [here]("http://ubuntuforums.org/showpost.php?p=9328344&postcount=110") for more a couple of useful tweaks on your machine :)

---

### Post by Sandra121289 on 2010-09-12
Actually it's still the same.

How should I uninstall the Nvidia Driver when I got a blank screen everytime I try to start Ubuntu? It doesn't matter if the Sata option is on Advanced or not, the blank screen stays. I can access the system with the Ubuntu Live CD but how to uninstall the driver from there, I got no idea.

Do you have an idea how to fix this?

---

### Post by ubuntoide on 2010-09-12
oh sorry, didn't get that.. Anyway there is for sure a cleaner way to boot again, but I will try this way: boot with the cd, mount the root partition and browse to /etc/X11, check if there is an xorg.conf file and simply rename it in xorg.conf.bak (I'm assuming that the nvidia driver has written in it its configuration) and reboot. Be sure to have Sata on Advanced and the system will use the Intel card

---

### Post by Sandra121289 on 2010-09-13
Thank you very much!
That saved me :)

---

### Post by Sphaerophoria on 2010-09-17
has anyone managed to get this working on 10.10 beta? When i use the mod it just crashes my laptop

---

### Post by Nicias on 2010-09-29
First off, I'm in gentoo, but that shouldn't affect things that much.  I've been using the nvidia drivers with the bios "compatibility" trick. With the screen dimmed using nvidia drivers, powertop reports as low as 9.8W. If I don't do compatibility, but use the asus_nvidia module, I can use the intel card, but I can't change the brightness, and I get about 12W power usage. Which makes me think it's still powering the nvidia card. In particular the nvidia chip still shows up in lspci.

So my question is this:

a) How can I verify if asus_nvidia is using working?
b) How can I change the brightness with the intel card?

Thanks!

---

### Post by mediamind on 2010-09-29
> a) How can I verify if asus_nvidia is using working?
You can confirm it with: lspci |grep VGA

> b) How can I change the brightness with the intel card?

Take a look at [**Cierreics' forum post**]("http://ubuntuforums.org/showpost.php?p=9328344&postcount=110").

---

### Post by Nicias on 2010-09-29
> **mediamind said:**
> You can confirm it with: lspci |grep VGA



Take a look at [**Cierreics' forum post**]("http://ubuntuforums.org/showpost.php?p=9328344&postcount=110").


In that case it isn't working. /var/log/messages indicates that it is working with: asus_nvidia: disable discrete graphics card. It still shows up in lspci.

Any thoughts?

---

### Post by mediamind on 2010-09-30
I haven't had much luck either. Might want to keep an eye on the hybrid graphics work being done [**here**]("http://linux-hybrid-graphics.blogspot.com/").

---

### Post by cullinane on 2010-10-01
I've had a UL30VT-A1 (with G210M) since early this year but I've held off on installing Ubuntu til now because of the hybrid graphics issue. Can someone just clarify for me if disabling the nvidia card works properly in Maverick? And what's the user experience like without it activated? I'm thinking in terms of something like Compiz or media playback, is it OK without the discrete graphics?

---

### Post by mediamind on 2010-10-01
> I've had a UL30VT-A1 (with G210M) since early this year but I've held off on installing Ubuntu til now because of the hybrid graphics issue. Can someone just clarify for me if disabling the nvidia card works properly in Maverick? 
Yes, I can confirm that it works well using Maverick though you must first change your SATA Operation Mode from "Enhanced" to "Compatible" in the BIOS. The key downside to this configuration is that it degrades the I/O performance of the hard drive. Booting on the stock HD takes 20-30 seconds longer as does suspend and resume from suspend. 

> And what's the user experience like without it activated? I'm thinking in terms of something like Compiz or media playback, is it OK without the discrete graphics? I generally run my VT with the Intel card. Haven't had any trouble with watching videos, including 720p on YouTube etc. You can find more info about running Maverick on the UL30VT **[here]("http://wiki.daviddarts.com/Ubuntu_Maverick_on_the_Asus_UL30VT")**.

---

### Post by cullinane on 2010-10-02
Thanks for the advice- and that link is extremely handy! I'm still mulling over what to do, but I'll make up my mind based on this guide.

---

### Post by Nicias on 2010-10-02
I've had quite some success. I now consider the switching "solved" however, I use gentoo, so I'm not sure how easy it would be to use my solutions on ubuntu. This is what I mean by "solved"

[LIST]
[*]I can chose which card to use at boot time in the bios.
[*] I don't have to do anything with config files
[*] The other card is powered down
[*] the brightness keys work for both cards (also I have an init.d service that manages brightness)
[*] all of this survives hibernate.
[/LIST]


If you want more details. Look at my [gentoo forum post]("http://forums.gentoo.org/viewtopic-p-6443050.html")

---

### Post by Sphaerophoria on 2010-10-10
Turning off the card results in crashes on the ul30vt with Ubuntu 10.10 installed. Can anyone confirm?

---

### Post by danhatch333 on 2010-10-13
Is it possible to keep the bios option as "enhanced" and pass a kernel option in grub that will treat sata as pata?(the equivalent to "compatible" in the bios, I think) 

Because if this is possible you could have 2 seperate boot options for your linux that will basically allow you to choose which graphics card to use assuming you have Nicias's solution working, but I have not tried his solution yet.

---

### Post by danhatch333 on 2010-10-14
Ok, when the bios is set to "compatible" ubuntu used the driver "ata_piix" which treats the hard drive as a pata. When tit is set to "enhanced" it treats it as sata and using the friver "ahci." You can find this out by going to "System>Administration>Disk Utility"

However, when I have the bios option set as "enhanced" and I blacklist the "ahci" driver in "/etc/modprobe.d/blacklist.conf" it still using the "ahci" driver. I found a bug report where someone said that ahci is embedded inside the kernel, but Idk if this is true, and if it is true, Idk if there is a way to disable it.

Also, I took the .deb file at the beginning of this post and extracted to get the source files. Then, I compiled it and loaded it, but it didn't disable nvidia. My bios is set to enhanced right now, and I'm using Ubuntu 10.10. I also tried a fresh reboot, but to no avail. Has anyone made a .deb of this module for 10.10.

Help would be appreciated, thanks in advanced.

---

### Post by ekarasik on 2010-10-15
I follow this thread for almost an year now, and first of all I must thank aviella,david airlie, and mkottman for the great work done for the hybrid graphics community.

As the previous posters say, the solution doesn't work for 10.10. It looks like there is a bug with nouveau, that still tries to access the nvidia card after it being turned off. Unfortunately, I lack the time to find the problem, however, I do have the solution for now:

_disable nouveau_
```
echo options nouveau modeset=0 | sudo tee -a /etc/modprobe.d/nouveau-kms.conf 

sudo update-initramfs -u
```after that, you should use acpi_call to turn off the nvidia card. [COLOR=Blue][look here for instructions ]("http://linux-hybrid-graphics.blogspot.com/2010/07/using-acpicall-module-to-switch-onoff.html")[/COLOR]
That brings us to about 8W with full brightness
With that, the nvidia card still powers up after suspend/hibernate, yet at least Ubuntu doesn't crash. As I took the initiative
to post, I am going to look for a solution to suspend. I'll update tomorrow

The .deb should probably also work (I didn't test it)

---

### Post by MNCvn on 2010-10-15
> **Sphaerophoria said:**
> Turning off the card results in crashes on the ul30vt with Ubuntu 10.10 installed. Can anyone confirm?

Yes, It works. You can follow these steps: (I'm just study from this thread)

1st step (from @ekarasik):


```

echo options nouveau modeset=0 | sudo tee -a /etc/modprobe.d/nouveau-kms.conf 

sudo update-initramfs -u

```

2sd step:


[look here for more detail instructions]("http://linux-hybrid-graphics.blogspot.com/2010/07/using-acpicall-module-to-switch-onoff.html")

After this step, you'll have a "acpi_call.ko" and "test_off.sh" (You must fix nouveau as in step 1, If you didn't this module does not work).

3rd step:

```

sudo cp acpi_call.ko /lib/modules/`uname -r`/kernel/

sudo gedit /etc/modules
```

Add this line after "lp" line: (as in my case)

```
acpi_call
```
------------------------------------------------------------------------
[B]and go to terminal type in:

```
sudo depmod
sudo modprobe acpi_call
```
[/B]
(Sorry, I've just checked and I miss this part, that is the reason the module can't load every time machine start.)
------------------------------------------------------------------------

This step help us auto load "acpi_call" module every time we boot our box.

4th step:


Make sure "test_off.sh" will call every time we boot. You can go to:

```
System > Preferences > Startup Applications > Startup Program > Add
[INDENT]
Name: whatever you want.
Command: Browse to "test_off.sh"
[/INDENT]

> Add > Close.

```
Done. Work like a charm.

MNCvn

---

### Post by ekarasik on 2010-10-15
Thanks MNCvn for explaining further :)

I'll continue your guide:

_step 5: suspend support (I won't be working on hibernate, as I never use it)_
```

sudo gedit /usr/lib/pm-utils/sleep.d/99_disable_nvidia

```paste this:
```

#!/bin/sh

case "$1" in
        resume|thaw)
        
                 /lib/modules/`uname -r`/kernel/acpi_call//test_off.sh
        ;;
esac

```[U]step 6: fixing the touchpad script by Cierreics ([look here]("http://ubuntuforums.org/showpost.php?p=9328344&postcount=110"))
[/U](for the fix, credits to [https://launchpad.net/~frederic-danis]("https://launchpad.net/%7Efrederic-danis"))
 ```

sudo gedit  /usr/share/acpi-support/power-funcs

```change 
```

    if [ x"$user" != x"" ]; then
               userhome=`getent passwd $user | cut -d: -f6`
            export XAUTHORITY=$userhome/.Xauthority
    else
        export XAUTHORITY=""
    fi

```to
```

export XAUTHORITY=`ps a | grep -v grep | grep X | sed -n 's/.*-auth \(.*\)/\1/p' | cut -f 1 -d ' '`
```

---

### Post by mirko_r on 2010-10-17
Hey!

Thanks for the good work - I tried a lot of the tips, but get a problem with disabling the nVidia card.

I boot with Intel driver enabled and nVidia not installed. When I exec the acpi_call, I get a success-message, but my keyboard and the touchpad become inaccessible. I can only restart by shutting down the notebook via the power key.

I use a UL30VT and Ubuntu 10.10 with kernel 2.35.22.

Does someone got the same issue or an idea what goes wrong?

Thanks alot!

---

### Post by ekarasik on 2010-10-18
It is just a symptom of the crash ubuntu experience when using acpi_call and nouveau enabled. The keyboard and touchpad aren't disabled - the computer just hangs :)

First, double check that SATA mode in BIOS is set to enhanced. If it is compatible, you use the nvidia card. If you use it, and then disable it, obviously it hangs. 

I see no other reason why it won't work if you used my fix. could you please copy paste here result of "lsmod" in terminal?

Another option: A more "pollitically correct" way to stop nouveau from loading
```
 gedit /etc/modprobe.d/blacklist-nvidia.conf 
```and paste there
```

blacklist nouveau
blacklist nvidia
```and after that run 

```

sudo update-initramfs -u

```

---

### Post by mirko_r on 2010-10-18
Hey!

Thanks for the answer!

First of all, I think, I am using the Intel driver and BIOS is definitely set to Enhanced.

I'll test the other way, but first the result of the lsmod:

```

Module                  Size  Used by
cryptd                  8140  0 
aes_x86_64              7936  1 
aes_generic            27631  1 aes_x86_64
parport_pc             30086  0 
dm_crypt               13381  0 
ppdev                   6804  0 
snd_hda_codec_nvhdmi    14587  4 
binfmt_misc             7984  1 
joydev                 11363  0 
snd_hda_codec_realtek   299533  1 
arc4                    1497  2 
snd_hda_intel          26019  2 
snd_hda_codec         100919  3 snd_hda_codec_nvhdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               6660  1 snd_hda_codec
ath9k                 101730  0 
snd_pcm                89104  2 snd_hda_intel,snd_hda_codec
ath9k_common            6874  1 ath9k
snd_seq_midi            5932  0 
snd_rawmidi            22207  1 snd_seq_midi
ath9k_hw              314699  2 ath9k,ath9k_common
ath                    10413  2 ath9k,ath9k_hw
snd_seq_midi_event      7291  1 snd_seq_midi
mac80211              266657  2 ath9k,ath9k_common
snd_seq                57512  2 snd_seq_midi,snd_seq_midi_event
asus_laptop            16668  0 
snd_timer              23850  2 snd_pcm,snd_seq
snd_seq_device          6912  3 snd_seq_midi,snd_rawmidi,snd_seq
sparse_keymap           3837  1 asus_laptop
uvcvideo               62379  0 
videodev               49359  1 uvcvideo
v4l1_compat            15519  2 uvcvideo,videodev
snd                    64117  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              170293  4 ath9k,ath9k_common,ath,mac80211
v4l2_compat_ioctl32    12646  1 videodev
psmouse                62080  0 
led_class               3393  2 ath9k,asus_laptop
serio_raw               4910  0 
soundcore               1240  1 snd
snd_page_alloc          8588  2 snd_hda_intel,snd_pcm
lp                     10201  0 
parport                37032  3 parport_pc,ppdev,lp
nouveau               568848  0 
i915                  330249  3 
ttm                    68212  1 nouveau
drm_kms_helper         32836  2 nouveau,i915
drm                   206161  6 nouveau,i915,ttm,drm_kms_helper
ahci                   21857  0 
libahci                26167  4 ahci
intel_agp              32080  2 i915
i2c_algo_bit            6208  2 nouveau,i915
video                  22176  1 i915
output                  2527  1 video
atl1c                  34955  0 

```**UPDATE:** I tried the blacklist way and got no errors. But when I check "lspci | grep VGA", I can see both cards - Intel and nVidia. So I think the card is powered on, isn't it[B]?

UPDATE2:[/B] When I start the notebook with the nvidia-blacklist, I can call the test_off.sh without crashing the system. But the lspci shows the two lines anymore. Is lspci the right way to check, if nVidia is powered on or off?

And: in Step 3, you copy a file called asus_nvidia.ko. Where do I find this find? I've never seen it before.
[B]
UPDATE 3:[/B] It works! But only manually. When I load the module via insmod, I can use test_off.sh and powertop shows ~8 watts instead of ~12 watts. But it doesn't work with auto loading the module. I copied acpi_call.ko into /lib/modules/2..../ and inserted acpi_call into /etc/modules. But after I start the maschine, the module doesn't load. I don't know, what's wrong with it.

Thank you for your help! :-)

---

### Post by MNCvn on 2010-10-19
> **mirko_r said:**
> Hey!

Thanks for the good work - I tried a lot of the tips, but get a problem with disabling the nVidia card.

I boot with Intel driver enabled and nVidia not installed. When I exec the acpi_call, I get a success-message, but my keyboard and the touchpad become inaccessible. I can only restart by shutting down the notebook via the power key.

I use a UL30VT and Ubuntu 10.10 with kernel 2.35.22.

Does someone got the same issue or an idea what goes wrong?

Thanks alot!

You can follow my steps above. If you didn't finish the first step, your PC will be inaccessible.

---

### Post by MNCvn on 2010-10-19
> **mirko_r said:**
> Hey!

And: in Step 3, you copy a file called asus_nvidia.ko. Where do I find this find? I've never seen it before.

Thank you for your help! :-)

Sorry for stupid cut and paste error. That's acpi_call.ko.
I fixed the post already. Thanks.

MNCvn.

---

### Post by mirko_r on 2010-10-20
Cool, that worked!
Thank you for your good support ;-))

The last thing that isn't working yet, is the suspend mode.
I copied the acpi_call files to 

[PHP]/usr/local/bin/acpi_call/test_off.sh[/PHP]

and inserted the commands from #5 to the 99_..._disable file. But everytime the maschine wakes up, the nVidia card ist powered on again.

Do you have any ideas for that issue?

---

### Post by ekarasik on 2010-10-20
sorry, my error, looks like I lacked consistency with MNCvn steps. I corrected that now.

Replace it to
```

#!/bin/sh

case "$1" in
        resume|thaw)
        /lib/modules/`uname -r`/kernel/acpi_call/test_off.sh
        ;;
esac

```(I just placed the module on a diffrent place on my PC, because with MNCvn you will have to copy the module to every new kernel you install, and I tend to test development kernels, so this is quite frasturating for me)

I hope this one will work

---

### Post by manco1911 on 2010-10-21
Hi all, im running ubuntu 10.04 on a UL30vt-a1. 
the MNCvn and ekarasik is tested on 10.10 Maverik.. but i havent found a review on 10.04. 
So, would this work on 10.04 ?

thanks for all the effort you are putting into this guys.

---

### Post by ekarasik on 2010-10-22
The acpi_call module works on 10.04 as well. Actually, on 10.04 it worked even with nouveau running, but it may cause issues. So, basically, the steps for 10.04 should be the same. If you run into any problem, feel free to ask for help :)

---

### Post by Crysler on 2010-10-26
> **MNCvn said:**
> Yes, It works. You can follow these steps: (I'm just study from this thread)

1st step (from @ekarasik):


```

echo options nouveau modeset=0 | sudo tee -a /etc/modprobe.d/nouveau-kms.conf 

sudo update-initramfs -u

```2sd step:


[look here for more detail instructions]("http://linux-hybrid-graphics.blogspot.com/2010/07/using-acpicall-module-to-switch-onoff.html")

After this step, you'll have a "acpi_call.ko" and "test_off.sh" (You must fix nouveau as in step 1, If you didn't this module does not work).

3rd step:

```

sudo cp acpi_call.ko /lib/modules/`uname -r`/kernel/

sudo gedit /etc/modules
```Add this line after "lp" line: (as in my case)

```
acpi_call
```------------------------------------------------------------------------
[B]and go to terminal type in:

```
sudo depmod
sudo modprobe acpi_call
```[/B]
(Sorry, I've just checked and I miss this part, that is the reason the module can't load every time machine start.)
------------------------------------------------------------------------

This step help us auto load "acpi_call" module every time we boot our box.

4th step:


Make sure "test_off.sh" will call every time we boot. You can go to:

```
System > Preferences > Startup Applications > Startup Program > Add[INDENT]
Name: whatever you want.
Command: Browse to "test_off.sh"
[/INDENT]> Add > Close.

```Done. Work like a charm.

MNCvn

Hello! I'm a complete noob in Ubuntu, and I want to shut down my discrete Nvidia graphics on my Asus UL80VT. I tried using this method, and I'm stuck at this part: ```
  sudo cp acpi_call.ko /lib/modules/`uname -r`/kernel/ 
```
It says ```
 radu@radu-UL80VT:~$ sudo cp acpi_call.ko /lib/modules/2.6.35-22-generic/kernel/
cp: cannot stat `acpi_call.ko': No such file or directory 
```
Any help ?

---

### Post by mirko_r on 2010-10-27
> **ekarasik said:**
> sorry, my error, looks like I lacked consistency with MNCvn steps. I corrected that now.

Replace it to
```

#!/bin/sh

case "$1" in
        resume|thaw)
        /lib/modules/`uname -r`/kernel/acpi_call/test_off.sh
        ;;
esac

```(I just placed the module on a diffrent place on my PC, because with MNCvn you will have to copy the module to every new kernel you install, and I tend to test development kernels, so this is quite frasturating for me)

I hope this one will work

Hi,

thanks for the response.

I replaced the code in the 99_nvidia file but it doesn't work either. The module is loaded, but the ./test:off.sh isn't executed when I return from suspend mode, I think.
When I execute test_off.sh in /lib/modules/`uname -r`/kernel/acpi_call/ manually, everything works fine.

Do you have any further suggestions what went wrong?

**@Crysler:** is it possible that you're in a wrong directory when you try to copy the file, i.e. you downloaded it to "Downloads" and try to copy it from /home/user/?

---

### Post by cobra11 on 2010-11-25
Can someone pleasse fix it that it will work when come from suspend? 
This code doesnt work..
[PHP]#!/bin/sh

case "$1" in
        resume|thaw)
        /lib/modules/`uname -r`/kernel/acpi_call/test_off.sh
        ;;
esac

[/PHP]

---

### Post by cobra11 on 2010-11-28
I fixed it it works from hibernation or from suspend. Acpi_call script needs to be copied to  /lib/modules/`unaame -r`/kernel/acpi_call/ than you need to create script in /etc/pm/sleep.d/ which is called 99-nvidia-off.sh and add code:
```
#!/bin/sh 

case "$1" in 
        resume|thaw) 
        /lib/modules/`uname -r`/kernel/acpi_call/test_off.sh 
        ;; 
esac  
```

---

### Post by christianco on 2010-11-28
**EDIT:** It's the BIOS - I had an early version #204 flashed. Upgrade to 211 and it works great.

-----------------------------

there is a lot in here about shutting the nvidia off, but my trouble is that I can't enable it with nvidia drivers in 10.10/32 bit (ul30vt).

When I install nvidia hardware drivers, then enter "compatibility" mode in the bios, and then boot, X server just hangs. startx from tt1 errors out: device not found. the same is true if I run dpkg-reconfigure xserver, or nvidia-xconfig to generate xorg.conf.

now here's the weird part: lspci | grep VGA reports BOTH cards active. Definitely I am using compatibility mode, so this is a big mystery to me that I haven't seen on any of the forums.

So when i delete my xorg.conf file and starx, viola, i get a full desktop. I assume that the intel card is being used by xserver, but I'm not sure how to tell exactly. Compiz can't be enabled, but Additional Drivers shows the nvidia as active. very confusing to me.

Anyway I have been hacking away at this problem for a long time now and have no clue how to fix it. All the wikis and forums just say that compatibility mode should just work with nvidia drivers enabled. Anyone else have the experience I am having or know how to fix?

thx

---

### Post by Holymoly on 2010-11-28
can someone elaborate on step 2? the part on acpicall module, im just not sure how im suppose to install it, i guess im suppose to make apci_call.ko and test_off.sh appear in /proc/acpi/call, but i cant make a folder there, sooooo...

im pretty new to linux, just installed ubuntu 10.10x64, im assuming that i should follow MNCvn and ekarasik's steps right? sry its just the steps all posted all over the thread idk which one works lol

---

### Post by TheMalinowski on 2010-12-02
i have also some problems with step 2
i'm getting an error while processing "make"
```
root@mali-netbook:~/nvg# make acpi_call
cc     acpi_call.c   -o acpi_call
acpi_call.c:1: fatal error: linux/module.h: No such file or directory
compilation terminated.
make: *** [acpi_call] Fehler 1

```

(10.10 64bit on ASUS UL80VT)

---

### Post by yanf.jiang on 2010-12-11
I followed the MNcvn's protocol (page 10), it really worked. But I want to share some  unseccessfull experience with vga_switcheroo:
[http://asusm51ta-with-linux.blogspot.com/](http://asusm51ta-with-linux.blogspot.com/)
[https://help.ubuntu.com/community/HybridGraphics](https://help.ubuntu.com/community/HybridGraphics)

(1) you might find there's no vgaswitcheroo folder in /sys/kernel/debug. To solve this, first, do not use nvidia driver, if you have installed it, just uninstall it. second: do not prevent nouveau from running. I mean in this acpi_call method, if you are using 10.10, you have to disable nouveau, see(page 9 and 10), but disabling it will cause the absence of vgaswitcheroo folder, although lspci |grep VGA still shows two cards.

(2) 
echo ON > /sys/kernel/debug/vgaswitcheroo/switch
echo OFF > /sys/kernel/debug/vgaswitcheroo/switch
these two commands do change the the status shown in the switch file, however, the OFF doesn't really power it off if you look at the power usage.

echo DIGD > /sys/kernel/debug/vgaswitcheroo/switch
echo DDIS > /sys/kernel/debug/vgaswitcheroo/switch

as default, the computer will use the intel card. However, echo DDIS never works even if you logout and login.
if you echo DIGD and logout, the system will freeze. you have to turn it off and restart it.


I am pretty new with linux. that's all I have tested.
I hope someone can help me out with this. It is really nice if we can freely switch between them.

---

### Post by didymos88 on 2010-12-11
> **cobra11 said:**
> Can someone pleasse fix it that it will work when come from suspend? 
This code doesnt work..
[PHP]#!/bin/sh

case "$1" in
        resume|thaw)
        /lib/modules/`uname -r`/kernel/acpi_call/test_off.sh
        ;;
esac

[/PHP]

Code is fine, you must be sure of three things:
- there must be test_off.sh file in that directory :)
- test_off.sh must have executable privileges 
- /usr/lib/pm-utils/sleep.d/99_disable_nvidia must have  executable privileges also!!!

If everything will be fine, after invoking:
```
cat /proc/acpi/battery/BAT0/state
```

you will see present rate around 8000 mW instead of 12000 mW

[edit] everything works on Ubuntu 10.10 64bit

---

### Post by Teodore on 2010-12-12
> **dakilla said:**
> Works fine on 10.04.
i just got my g210m to work on ubuntu 9.10 on a asus ul30vt.
checking the status on 10.04. will be back with a simple howto soon.

**UPDATE:**

to get the nvidia card to work you have to do this:

this is how you get g210m to work on ubuntu 9.10 / 10.04.

1. download and install nvidia drivers. (i have only tested the ones in the repos)

2. make sure you got an Xorg.conf that is correct. ( if not, run nvidia-xconfig )

3. reboot into bios (press delete while booting)

4. change the SATA option in the bios from enhanced to compatibility. ( yea, this makes sense? NOT! )

5. boot into linux and smile!

Finally, after 2 days i figured out why so many people's laptop is working with the above steps and mine don't.
I was using UL80VT with ubuntu 10.04.1 64 bit and i followed the steps above other than step 2 as the settings for my Xorg.conf is correct.

When i rebooted, i was prompted with a blank screen but the Ctrl-Alt-Del button is still able to reboot the system.

The problem is that i am still using an old bios version (BIOS 206) for my laptop, the new BIOS 213 can be obtain at asus download site. Once i flashed in the new bios, everything is working fine =) and now i can output to an external monitor with a little tinkering of the nvidia settings.

Thanks Dakilla!

---

### Post by josedb on 2010-12-23
Wouldn't be a good idea to add noveau to blacklist?

---

### Post by OneArtPlease on 2011-01-07
> **christianco said:**
> **EDIT:** It's the BIOS - I had an early version #204 flashed. Upgrade to 211 and it works great.

-----------------------------

there is a lot in here about shutting the nvidia off, but my trouble is that I can't enable it with nvidia drivers in 10.10/32 bit (ul30vt).

When I install nvidia hardware drivers, then enter "compatibility" mode in the bios, and then boot, X server just hangs. startx from tt1 errors out: device not found. the same is true if I run dpkg-reconfigure xserver, or nvidia-xconfig to generate xorg.conf.

now here's the weird part: lspci | grep VGA reports BOTH cards active. Definitely I am using compatibility mode, so this is a big mystery to me that I haven't seen on any of the forums.

So when i delete my xorg.conf file and starx, viola, i get a full desktop. I assume that the intel card is being used by xserver, but I'm not sure how to tell exactly. Compiz can't be enabled, but Additional Drivers shows the nvidia as active. very confusing to me.

Anyway I have been hacking away at this problem for a long time now and have no clue how to fix it. All the wikis and forums just say that compatibility mode should just work with nvidia drivers enabled. Anyone else have the experience I am having or know how to fix?

thx

I have exactly the same issue with Ubuntu 10.10 and my UL80VT in "compatibility" mode.

I wonder why there is so little information available about Maverick usage, the release is now out for 3 months!

---

### Post by danhatch333 on 2011-01-07
> 
Originally Posted by **OneArtPlease**
I have exactly the same issue with Ubuntu 10.10 and my UL80VT in "compatibility" mode.

I wonder why there is so little information available about Maverick usage, the release is now out for 3 months!     
There isn't very much information because using the nvidia card is os independent. The instructions from 10.04 work in 10.10 and slackware for that matter. Check your bios revision number and make sure it is a recent one like 213 (a little lower might be ok.)

SideNote: Before changing the bios option you have to install **and** configure nvidia drivers so it works on next startup with "compatibility"

---

### Post by mpw on 2011-01-24
Hello guys,

with this thread I got my nvidia g210m in my asus ul30vt working. So thanks to you!

I have a question:

Is it possibile to have both cards activated and use the intel for graphic output?

Background: I want the nvidia for boinc cuda crunshing. And as the windows are slowing down when the gpu crunshes while I'm working on the pc, I would like to use the intel  chip for the Xserver as it's quick enough for me.

So how can I switch to the intel graphic chip without deactivating the nvidia chip?

Bye
MPW

---

### Post by ubuntoide on 2011-01-24
By now you can't, there is some work with the PRIME project going on, but nothing usable till now.

---

### Post by _JT on 2011-01-25
> **cobra11 said:**
> I fixed it it works from hibernation or from suspend. Acpi_call script needs to be copied to  /lib/modules/`unaame -r`/kernel/acpi_call/ than you need to create script in /etc/pm/sleep.d/ which is called 99-nvidia-off.sh and add code:
```
#!/bin/sh 

case "$1" in 
        resume|thaw) 
        /lib/modules/`uname -r`/kernel/acpi_call/test_off.sh 
        ;; 
esac  
```

If you say copy the script, which of the files in the directory need to be copied? All of them?

---

### Post by cobra11 on 2011-01-31
Yes i copy whole map acpi_call to dir /lib/modules/`uname -r`/kernel/ with sudo cp command.

---

### Post by mirko_r on 2011-02-02
Hey,

I just updated my kernel to 2.6.35-25 and now I get the following error when trying to insert acpi module.

```

mirko@mr-linux:/lib/modules/2.6.35-25-generic/kernel$ sudo modprobe acpi_call
FATAL: Error inserting acpi_call (/lib/modules/2.6.35-25-generic/kernel/acpi_call.ko): Invalid module format

```

Is there anyone with the same problem? Or does anyone have an idea?

---

### Post by krushaaa on 2011-02-06
> **cobra11 said:**
> Yes i copy whole map acpi_call to dir /lib/modules/`uname -r`/kernel/ with sudo cp command.


hey do you mean the folder or the files in the folder?

cheers in advance

EDIT:
the thread answers the quetion.

---

### Post by Jontebullen on 2011-02-19
I can't get this to work! :@

I have a ul30vt with Ubuntu 10.10, I have followed this:

> **MNCvn said:**
> 
1st step (from @ekarasik):


```

echo options nouveau modeset=0 | sudo tee -a /etc/modprobe.d/nouveau-kms.conf 

sudo update-initramfs -u

```

2sd step:


[look here for more detail instructions]("http://linux-hybrid-graphics.blogspot.com/2010/07/using-acpicall-module-to-switch-onoff.html")

After this step, you'll have a "acpi_call.ko" and "test_off.sh" (You must fix nouveau as in step 1, If you didn't this module does not work).

3rd step:

```

sudo cp acpi_call.ko /lib/modules/`uname -r`/kernel/

sudo gedit /etc/modules
```

Add this line after "lp" line: (as in my case)

```
acpi_call
```
------------------------------------------------------------------------
[B]and go to terminal type in:

```
sudo depmod
sudo modprobe acpi_call
```
[/B]


several times, once after a reinstall of Ubuntu like 2 hours ago. The only thing that happens is that the mouse and keyboard freezes up the first time i run test_off.sh. I perform a hard reboot after which running test_off.sh has no effect at all. lspci |grep VGA shows both cards running.


I've also tried this: [http://linux-macbook-air-killers.blogspot.com/2009/12/solution-to-switch-off-nvidia-card-in.html](http://linux-macbook-air-killers.blogspot.com/2009/12/solution-to-switch-off-nvidia-card-in.html)
with no result at all. lspci |grep VGA shows both cards running.

Does anyone know what I can do? :confused:

---

### Post by ei8htohms on 2011-02-27
> **Jontebullen said:**
> I can't get this to work! 

... lspci |grep VGA shows both cards running.

Does anyone know what I can do? :confused:

I was just about to post that "I'm in the same boat with you," but then I did a little further testing a realized that it is working BUT "lspci |grep VGA" still shows both cards.   

I used the module from page 10 of this thread (make was successful) and installed "test_off.sh" (executable) where indicated and have it called at boot.  

I thought it was doing something, because the little libnotify pop-up had gone away when using the brightness hotkeys (Fn F5 and F6) but when I ran "lspci" I kept getting both cards so I figured the Nvidia card must still be on.

I got so frustrated with all the various steps seeming to work as they were supposed to (after MUCH wrestling with them, for a relative Linux noob like myself, compiling a module is an adventure into the unknown) but still seeing both cards with "lspci" that I decided to run PowerTop with the test_off script called at boot and then without calling it and the power consumption difference is HUGE.  It showed a consumption as low as 8.1 watts (!) before even following any PowerTop power savings recommendations after running test_off at boot and after rebooting without test_off called it was up in the 13.4 watt range.  I'd have to call that success [pats self on back]. 

I'm using a fresh install of 10.04 (64-Bit) dual booting on an Intel X25-M SSD (next to Win 7 64-Bit) in an Asus UL30VT that has already been tweaked according to David Dart's Wiki as well as a variety of SSD optimizations (discard, noatime, noop, puny swappiness), so there are a lot of extra variables in there for my specific case, but any insights into why "lspci" doesn't seem to be a good indicator of graphics card usage would be appreciated. 

For any other noobs (like me) still struggling with this, don't give up!  The power savings are most definitely worth the effort.

_john

---

### Post by Jontebullen on 2011-03-02
> **ei8htohms said:**
> I was just about to post that "I'm in the same boat with you," but then I did a little further testing a realized that it is working BUT "lspci |grep VGA" still shows both cards.   

...

_john

wow, it does seem to be working!!!
I've been checking my power usage with powertop a couple of times, and it's always been above 14, depending on what stuff i'm running of course, but I must just not have been paying much attention to what happened after i ran test_off.sh, because now, with one tab open in chromium and two terminals it went from around 14-16W down to 9-11W!!
it seems to be sitting around 10 now most of the time :) 

**Power usage (ACPI estimate): 10.9W (3.7 hours) (long term: 10.5W,/3.8h)**

I think my battery is at about 80%, so that's a maximum of *maybe* 5 hours..

---

### Post by wyatt66 on 2011-03-17
I tried what is proposed in this thread to switch off the nvidia card on my Asus UL30VT.

It worked with Ubuntu 10.04, but it is not working anymore with 10.10.

Does someone know if this is planned to be solved in 11.04 ?

If not, I think it would be very appreciated to have an easy to install package that would allow this nvidia deactivation... though I don't know how difficult it would be to implement.

---

### Post by ekarasik on 2011-04-28
Some more work to actually support switching goes here:

[https://github.com/awilliam/asus-switcheroo](https://github.com/awilliam/asus-switcheroo)

You may want to try that.

---

### Post by mirko_r on 2011-05-02
> **ekarasik said:**
> Some more work to actually support switching goes here:

[https://github.com/awilliam/asus-switcheroo](https://github.com/awilliam/asus-switcheroo)

You may want to try that.

I didn't get it to work on my UL30VT by now. 

Was someone more successful? If so, it would be nice to read a step by step instruction.

---

### Post by Nicias on 2011-05-07
Works perfectly for me. I just followed the directions in his Readme, I'm using nvidia driver not nouveau.

---

### Post by Gskellig on 2011-05-08
I'm on 11.04, currently trying to disable the nvidia graphics card.
I installed the .deb in the first post, and disabled the nvidia but "lspci |grep VGA" still shows both cards.

However PowerTOP shows about 8-10W. Is it working?

Are there any other solutions to getting switching working? Or at least a way to *easily* switch between the two cards? Requiring only a reboot instead of messing around in terminal and installing drivers?

---

### Post by unchain on 2011-05-09
> **Gskellig said:**
> I'm on 11.04, currently trying to disable the nvidia graphics card.
I installed the .deb in the first post, and disabled the nvidia but "lspci |grep VGA" still shows both cards.

However PowerTOP shows about 8-10W. Is it working?

Are there any other solutions to getting switching working? Or at least a way to *easily* switch between the two cards? Requiring only a reboot instead of messing around in terminal and installing drivers?

Try:```
sudo lshw -C video
```

It should just show the integrated card if you did everything properly. Same thing happened to me, lspci still shows both cards, but power consumption is way down and lshw shows just the integrated card.

---

### Post by hurrrtin on 2011-05-10
I want to ENABLE my nvidia card so that I can use Unity/Compiz/etc in Natty without changing the bios from Enhanced to Compatibility. Can this be done?

---

### Post by Nicias on 2011-05-11
> **hurrrtin said:**
> I want to ENABLE my nvidia card so that I can use Unity/Compiz/etc in Natty without changing the bios from Enhanced to Compatibility. Can this be done?

The readme explains how to do this. From 

[https://github.com/awilliam/asus-switcheroo/blob/master/README](https://github.com/awilliam/asus-switcheroo/blob/master/README)

starting at line 94:
```
It is also possible, though very, very alpha and extremely
not recommended for average users to use the asus-switcheroo
module as a dummy switcheroo client that allows you to run
the proprietary nvidia module.  To do this, blacklist
nouveau and rebuild your initramfs to get nouveau out of it.
Use the dummy-client=1 option for asus-switcheroo, if loaded
from initramfs, use asus-switcher.dummy-client=1.  At boot,
switch to DIS, modprobe nvidia, then start X using the nvidia
proprietary driver.  Note that the screen LVDS will go black
as soon as you switch via DIS and will not come back until X
starts.  There is no framebuffer driver in this mode, so you
will only have X.  This switch is one way, you'll need to
reboot to get Intel graphics back.

```

---

### Post by Gskellig on 2011-05-16
Nvidia card disabled- works great. I can get up to 8 hour battery life with Powertop.

Now do I reenable the nvidia card?
Ubuntu 11.04, when I switch the BIOS to "compatible" the screen just stays black after booting.

---

### Post by mpw on 2011-06-16
Hello,

I have an Asus ul30vt. Does anyone of you know where I can use two external monitors (HDMI + VGA) at once?

With the g210m of course, the intel won't be strong enough I think.

Bye
MPW

---

### Post by Wurtzinator on 2011-09-11
Heyho,

I hope there are still some people out there you can help me with my problem.

Note: I'm running Ubuntu 11.04 Natty Narwhal on my UL30VT.

I downloaded the .deb package and did what's described in the post #1!

I had the same problem as many others did with the comment: "nothing to do...."

So, then I tried what avilella suggested and it worked up to a the point where I run "make":

> 
```

ar x *.deb

then

tar xzf data.tar.gz

then go to the place where the nvidia-*.tar.gz file is

  

tar xzf nvidia-*.tar.gz

then go to the place with the code, and run:

make 

```


Heres my output after "make":

```

root@Unibook:/home/timmy/Dokumente/Nvidia turn off/usr/src/dkms_source_tree# make
make -C /lib/modules/2.6.38-11-generic/build M=/home/timmy/Dokumente/Nvidia turn off/usr/src/dkms_source_tree modules
make[1]: Betrete Verzeichnis '/usr/src/linux-headers-2.6.38-11-generic'
make[1]: *** Keine Regel, um »turn« zu erstellen.  Schluss.
make[1]: Verlasse Verzeichnis '/usr/src/linux-headers-2.6.38-11-generic'
make: *** [all] Fehler 2


```


So, it didn't compile properly.

Needless to say that these commands didn't work either:

```
cp nvidia_g210m_acpi /lib/modules/$(uname -r)/kernel/
depmod

modprobe nvidia_g210m_acpi

echo nvidia_g210m_acpi >>/etc/modules

```

Nevertheless, the first time I tried to run it, the way I just described, my battery life indeed increased from 4h to about 8h!

Then after a reboot, it was back to normal.

Now after I deleted the compiled data and ran the commands a 2nd time with pretty much the same output, it doesn't even work for one session.

Can anyone help me please?

Greetings!

---

### Post by Wurtzinator on 2011-09-13
> **Wurtzinator said:**
> Heyho,

I hope there are still some people out there you can help me with my problem.

Note: I'm running Ubuntu 11.04 Natty Narwhal on my UL30VT.

I downloaded the .deb package and did what's described in the post #1!

I had the same problem as many others did with the comment: "nothing to do...."

So, then I tried what avilella suggested and it worked up to a the point where I run "make":



Heres my output after "make":

```

root@Unibook:/home/timmy/Dokumente/Nvidia turn off/usr/src/dkms_source_tree# make
make -C /lib/modules/2.6.38-11-generic/build M=/home/timmy/Dokumente/Nvidia turn off/usr/src/dkms_source_tree modules
make[1]: Betrete Verzeichnis '/usr/src/linux-headers-2.6.38-11-generic'
make[1]: *** Keine Regel, um »turn« zu erstellen.  Schluss.
make[1]: Verlasse Verzeichnis '/usr/src/linux-headers-2.6.38-11-generic'
make: *** [all] Fehler 2


```
So, it didn't compile properly.

Needless to say that these commands didn't work either:

```
cp nvidia_g210m_acpi /lib/modules/$(uname -r)/kernel/
depmod

modprobe nvidia_g210m_acpi

echo nvidia_g210m_acpi >>/etc/modules

```Nevertheless, the first time I tried to run it, the way I just described, my battery life indeed increased from 4h to about 8h!

Then after a reboot, it was back to normal.

Now after I deleted the compiled data and ran the commands a 2nd time with pretty much the same output, it doesn't even work for one session.

Can anyone help me please?

Greetings!


Any thoughts?

---

### Post by Wurtzinator on 2011-09-14
> **Wurtzinator said:**
> Any thoughts?

:-k

---

### Post by Wurtzinator on 2011-09-19
> **Wurtzinator said:**
> :-k

Really nobody? :confused:

If anyone has an idea where else I could look for help, I would be glad!

---

### Post by christianco on 2011-12-05
Has anyone worked with the asus switcheroo with Natty or Oneiric? I'm wondering if it's worth doing on my ul30vt.

Specifically for the use of the proprietary nvidia driver, I'm wondering if this solution will fix the degraded i/o with the drive causing slow boot/wake times.

Or I've also read that there may be an upstream fix dealing with the multiplexer/hot switching? can anyone give me an idea of whether there is any kind of fix in the works for us hybrid graphics folks?

Anyway, i'm needing an update or some general info if anyone has got any.

thx

---

### Post by Svictor on 2011-12-06
Hi Christianco,
Just my 2 cents experience: after trying different methods (including vga switcheroo), I ended up using the switch "Compatible mode" in the BIOS. This is on a UL30JT, but maybe the VT has it too. It turns off the Intel card and uses only nvidia. This saves a little energy, not as much as the other way round (nvidia off, intel on), but everything on 3D is faster: unity, gnome shell... I use the proprietary nvidia driver since it offers better power management than the opensource one. I get around 5 real hours of battery life, which is fine for me. 

Alternatively, the dual graphics solution which proved easyest and most efficient in my case was [ironhide]("https://launchpad.net/~mj-casalogic/+archive/ironhide/").

---

### Post by christianco on 2011-12-06
Thanks Svictor

I would prefer to use the nvidia card in compatible mode - UL30VT has this option in the bios - but the trouble is that the compatible mode causes degradation in the HD - I think related to using PATA instead of SATA - I dunno i'm kind of fuzzy on why this happens, and what it does. For example, will it cause data corruption? I just don't know.

I do know that it takes 30 secs longer to boot and wake from sleep with the nvidia driver and compatible mode. For my current use this is not acceptable. This is why I am posting - I'm curious if there has been an improvement in the kernal that causes this problem to cease, or if the switcheroo or some other module would do the trick. I want to use the nvidia soley, but the HD degradation is causing me trouble.

thanks for the reply.

---

### Post by Svictor on 2011-12-07
In my case I couldn't notice any degradation. But I replaced the original HD with a 7200 rpm. The computer boots pretty fast (15 sec maybe), and battery life is ok. But maybe JT and VT differ in that respect

For a dual solution, vgaswitcheroo kinda worked, but you have to restart X to switch between cards. Ironhide proved more interesting for me since it could do the switching in realtime. Its ppa is here: [https://launchpad.net/~mj-casalogic/+archive/ironhide/](https://launchpad.net/~mj-casalogic/+archive/ironhide/)

---

### Post by christianco on 2011-12-07
right you are - no compatibility mode needed - ironhide works good on my ul30vt. thanks.

---

### Post by mpw on 2012-03-01
Hello,

I have an asus ul30vt too and for battery live reasons I decided to only use the intel graphic card. I already managed to automatically disable the nvidia card by adding these three lines to /etc/modules

```

nvidia_g210m_acpi
acpi_call
blacklist nvidia

```

After standby I can execute the test_off.sh to decrease the energy consumption again by switching the nvidia off.

But how I run this automatically?

[http://ubuntuforums.org/showpost.php?p=10173233&postcount=105](http://ubuntuforums.org/showpost.php?p=10173233&postcount=105)

^^This did not work at all :(

Bye
MPW

---

### Post by Hobbes on 2012-05-02
Anyone feel like testing this stuff with 12.04?

I've been running nvidia through compatibility mode for a while and everything works fine (minus slow start-up and really slow out of sleep mode slow-disk stuff).

I removed nvidia to try out intel in enhanced mode - graphics seem a bit smoother and unity working right away (unlike 11.10 for me)....

However, it is pretty much pointless if I can't disable nvidia card.
**************

Anybody have this working in 12.04? I tried installing the .deb file but got an error during the process.  Do you have to compile it yourself now? tried looking through thread but didn't see any obvious recent relevant posts...

A .deb file that 'just worked' would be great... I'd love to get this ul30vt through another year or so (despite some cracked plastic on the hinges and the bezel coming loose from the lcd, it still works alright :)

Thanks for any help!

---

### Post by tomsecret on 2012-05-06
*The following post has been edited, look at the end for my current solution to disable the nvidia geforce 210m on ul30vt*
I can confirm that the nvidia card can be switched off on Ubuntu 12.04 LTS (32-bit). What I did was download the tarball from [http://aur.archlinux.org/packages.php?ID=34499]("http://aur.archlinux.org/packages.php?ID=34499").

Then I compiled the source using:
```

wget http://aur.archlinux.org/packages/nv/nvidia-g210m-acpi/nvidia-g210m-acpi.tar.gz
tar -zxvf nvidia-g210m-acpi.tar.gz
cd nvidia-g210m-acpi/
make

```

Now 'sudo make install' didn't work, so instead I copied the 'nvidia_g210m_acpi.ko' manually. The exact path could be different for you, I used '/lib/modules/3.2.0-24-generic-pae/kernel/drivers/acpi/'

```

sudo cp nvidia_g210m_acpi.ko /lib/modules/3.2.0-24-generic-pae/kernel/drivers/acpi/
sudo depmod -a
sudo modprobe nvidia_g210m_acpi

```

Now to confirm that the module loaded you can type 'dmesg|grep nvidia' and you should get a line that reads 'kill_nvidia: disabled the discrete graphics card'. Also my power usage decreased from 15-17 W to 10-12 W (at full screen brightness), and the fan stopped running when idle. Hope it works!

Update: You should also consider removing the nvidia driver (sudo apt-get remove nvidia-current). This solved some serious lcd tearing issues I had, as well as making the desktop effects nicer (less pixelated).

Update2: I haven't found out how to load the module nvidia_g210m_acpi at startup. In ubuntu 10.04 I used /etc/rc.local,  but if I do that in 12.04 the system hangs during boot. It also hangs if I use /etc/init/rc.conf or /etc/modules. Any other suggestions? At the moment I have to manually start the module ('sudo modprobe nvidia_g210m_acpi').

Update3: For some reason my computer has started crashing during suspend when the module nvidia_g210m_acpi is loaded. This was not a problem the first days after using this module - but now it is, so I guess this solution isn't optimal, and bumblebee (or ironhide) is probably a better alternative.

Update4:
I have now stopped using the module (nvidia_g210m_acpi) since it broke suspend after some time. I've now switched to bumblebee, which seem to work very good. I installed bumblebee according to [http://www.bumblebee-project.org/install.html]("http://www.bumblebee-project.org/install.html"), and then the nvidia card is automatically disabled if you don't want to use it specifically (which is done by launching an application with through the 'optirun' program). Power consumption is similar to loading the nvidia_g210m_acpi, and stays around 10W with screen brightness at 100% and otherwise idle.

---

