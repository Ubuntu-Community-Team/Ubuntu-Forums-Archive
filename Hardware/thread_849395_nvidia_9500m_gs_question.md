---
title: "nvidia 9500m gs question"
date: 2008-07-04
forum: Hardware
---

### Post by wolfwood2x on 2008-07-04
I have an Asus G1Sn-X1 with an NVIDIA GeForce G9500M GS.
I tried to get it working under Hardy without much luck. I even tried several hacks that were supposed to work with that specific card. Has anyone had any luck with this laptop and chipset? 

Does anyone know if this card will be supported in the next major release? Im stuck in vista right now as I have not been able to get any distro to work with this graphics card. =/

---

### Post by add2700 on 2008-07-04
I have the same laptop, and I dunno how soon it will get a fix. I too have tried the hacks with no luck.
I'm running 64bit 8.04

---

### Post by starcannon on 2008-07-04
You can try my guide, I don't own any 9 series nvidia cards, but I'd try it this way first if I bought one.

[http://ubuntuforums.org/showthread.php?t=813931&highlight=nvidia](http://ubuntuforums.org/showthread.php?t=813931&highlight=nvidia)

---

### Post by StormPCs on 2008-07-05
> **wolfwood2x said:**
> I have an Asus G1Sn-X1 with an NVIDIA GeForce G9500M GS.
I tried to get it working under Hardy without much luck. I even tried several hacks that were supposed to work with that specific card. Has anyone had any luck with this laptop and chipset? 

Does anyone know if this card will be supported in the next major release? Im stuck in vista right now as I have not been able to get any distro to work with this graphics card. =/

I have the same laptop and I too am running Hardy 8.04 AMD64 (64 bit), and my machine runs perfectly.

I believe you need to download and install the 200+ updates immediately after installing the OS but before you download and enable the nVidia driver.  It was a no-brainer installation.

Exactly how did you install the OS?

---

### Post by wolfwood2x on 2008-07-05
> **StormPCs said:**
> I have the same laptop and I too am running Hardy 8.04 AMD64 (64 bit), and my machine runs perfectly.

I believe you need to download and install the 200+ updates immediately after installing the OS but before you download and enable the nVidia driver.  It was a no-brainer installation.

Exactly how did you install the OS?

I used the live disk for hardy 8.04 that was provided on the main website. I tried the install and drivers for it several times before giving up. The install process is not what I am complaining about. Once the operating system is installed I can not get the video drivers working correctly. 

I have read several dozen threads where people claim to have the same video chipset and have it working but all the "hacked" drivers out there do not seem to install or work correctly.

---

### Post by add2700 on 2008-07-05
I tried the server install, the 32 bit, and the 64bit. The problem is related to having 4GB RAM. Anything more than 3 and the kernel doesn't know how to address it. There are some people that have been able to patch their kernel, but I've tried it 15-20 times with no luck.

---

### Post by StormPCs on 2008-07-05
> **add2700 said:**
> I tried the server install, the 32 bit, and the 64bit. The problem is related to having 4GB RAM. Anything more than 3 and the kernel doesn't know how to address it. There are some people that have been able to patch their kernel, but I've tried it 15-20 times with no luck.

I am only on 2.6.24.19 I believe. All I did was installed the OS from the CD I made from the ISO image that I downloaded, rebooted and did all updates before I clicked on the icon, downloaded the proprietary driver and then checked the box to enabled the driver. It was that simple.

I am on the 201 BIOS (which is standard). I did upgrade my CPU from a T5550 to a T9300, and my 4gigs of RAM has been upgraded with high performance memory that runs at 4-4-4-12 instead of 5-5-5-15. Everything else is stock.

What BIOS are you using?

---

### Post by wolfwood2x on 2008-07-05
Storm,

I tried that too and had no luck. You must be lucky.. everyone else I have talked to cant get the nvidia drivers working for some reason.

 On a side note were you able to get the side lamps working? I am curious if they will function under wine maybe.

---

### Post by add2700 on 2008-07-06
Heya, I'm having a hell of a time getting the nvidia driver to work on my g1sn with 4GB RAM. I've tried all the kernel patches, I'm currently at 2.6.25.10-ultimate 64bit but can't get the nvidia drivers to load. How did you do it?

---

### Post by StormPCs on 2008-07-06
Have you guys tried taking one stick of RAM out to see if the 4GB is an issue?  My 4GB works fine but others seem to think it's a problem.

The first time I installed Ubuntu I could not get the nVidia driver to work properly but the next two times I did it exactly as my previous post states and it was fine.

---

### Post by add2700 on 2008-07-06
Ok finally got 1680X1050 resoltuion using the nvidia driver on a 32bit install of 8.04 on my ASUS G1sn-A1 laptop. Here are the exact steps I took, but I take no responsibility if you don't get it to work and have to reinstall.

1. Start with a fresh install of ubuntu 8.04 32 bit, and run all the advertised patches. 
2. Next, follow theses steps, taken from the good people at [nvnews]("http://www.nvnews.net/vbulletin/showpost.php?p=1673409&postcount=27"):

# Install Kernel Sources
sudo apt-get build-dep linux-image-2.6.24-19-rt
sudo apt-get source linux-image-2.6.24-19-rt

# Install Kernel Modules Sources
sudo apt-get build-dep linux-ubuntu-modules-2.6.24-19-rt
sudo apt-get source linux-ubuntu-modules-2.6.24-19-rt

#**<!-- Download the 512 patch if your card has 512 RAM, or the 256 if your card has 256 RAM-->**
#**<!-- RENAME the file from .txt to .diff as show below, and if your card has 256 RAM don't forget to alter the command accordingly-->**
# Apply NVRM patch
sudo patch -p0 < NVRM_512M_fix.diff

# Build debs for linux-image & linux-headers
cd linux-2.6.24/
# Modify flavours in debian/rules.d/amd64.mk (rt instead of generic)
sudo CONCURRENCY_LEVEL=2 fakeroot debian/rules custom-binary-rt
cd ..

# Build 
cd linux-ubuntu-modules-2.6.24-2.6.24/
# Modify flavours in debian/rules.d/amd64.mk (rt instead of generic)
sudo CONCURRENCY_LEVEL=2 fakeroot debian/rules binary-debs
cd ..

3. Lastly, run the deb packages you created above in this order:
You should then install the 4 debs :
linux-image-rt
linux-headers-rt
linux-headers-lum-rt
linux-ubuntu-modules-rt

Thanks again to the people at [nvnews.net]("http://www.nvnews.net").

---

### Post by TheTrlak on 2008-07-06
Hmm I have the same laptop as well and experiance the same issue, in my case the newest drivers seem to not install stating my kernel was built using a different version of GCC.

---

### Post by wolfwood2x on 2008-07-07
> **add2700 said:**
> Ok finally got 1680X1050 resoltuion using the nvidia driver on a 32bit install of 8.04 on my ASUS G1sn-A1 laptop. Here are the exact steps I took, but I take no responsibility if you don't get it to work and have to reinstall.

1. Start with a fresh install of ubuntu 8.04 32 bit, and run all the advertised patches. 
2. Next, follow theses steps, taken from the good people at [nvnews]("http://www.nvnews.net/vbulletin/showpost.php?p=1673409&postcount=27"):

# Install Kernel Sources
sudo apt-get build-dep linux-image-2.6.24-19-rt
sudo apt-get source linux-image-2.6.24-19-rt

# Install Kernel Modules Sources
sudo apt-get build-dep linux-ubuntu-modules-2.6.24-19-rt
sudo apt-get source linux-ubuntu-modules-2.6.24-19-rt

#**<!-- Download the 512 patch if your card has 512 RAM, or the 256 if your card has 256 RAM-->**
#**<!-- RENAME the file from .txt to .diff as show below, and if your card has 256 RAM don't forget to alter the command accordingly-->**
# Apply NVRM patch
sudo patch -p0 < NVRM_512M_fix.diff

# Build debs for linux-image & linux-headers
cd linux-2.6.24/
# Modify flavours in debian/rules.d/amd64.mk (rt instead of generic)
sudo CONCURRENCY_LEVEL=2 fakeroot debian/rules custom-binary-rt
cd ..

# Build 
cd linux-ubuntu-modules-2.6.24-2.6.24/
# Modify flavours in debian/rules.d/amd64.mk (rt instead of generic)
sudo CONCURRENCY_LEVEL=2 fakeroot debian/rules binary-debs
cd ..

3. Lastly, run the deb packages you created above in this order:
You should then install the 4 debs :
linux-image-rt
linux-headers-rt
linux-headers-lum-rt
linux-ubuntu-modules-rt

Thanks again to the people at [nvnews.net]("http://www.nvnews.net").

Can you elaborate on what this whole process is doing?
more to the point what is 
"sudo CONCURRENCY_LEVEL=2 fakeroot debian/rules custom-binary-rt"

That command does not seem to do anything
"sudo: fakeroot: command not found"

---

### Post by wolfwood2x on 2008-07-07
> **StormPCs said:**
> I am only on 2.6.24.19 I believe. All I did was installed the OS from the CD I made from the ISO image that I downloaded, rebooted and did all updates before I clicked on the icon, downloaded the proprietary driver and then checked the box to enabled the driver. It was that simple.

I am on the 201 BIOS (which is standard). I did upgrade my CPU from a T5550 to a T9300, and my 4gigs of RAM has been upgraded with high performance memory that runs at 4-4-4-12 instead of 5-5-5-15. Everything else is stock.

What BIOS are you using?

If I do the normal install of 32bit and then get all the updates. I can see the proprietary driver. If I check it to enable it and restart I get a warning about my machine running in low res mode and it wont let me choose a higher resolution than 800x600 and it prompts for a driver.

---

### Post by StormPCs on 2008-07-08
> **wolfwood2x said:**
> If I do the normal install of 32bit and then get all the updates. I can see the proprietary driver. If I check it to enable it and restart I get a warning about my machine running in low res mode and it wont let me choose a higher resolution than 800x600 and it prompts for a driver.

Sorry...it appears that only 2GB of my 4GB was operational, which is why it installed correctly.  It appears the kernel rebuild is necessary until nVidia makes a driver for Linux that loads properly.

add2700:

Can you post the code showing the install of the debs?  Also, will this work on the 64bit 8.04?  Thanks.

---

### Post by add2700 on 2008-07-08
Yes, I have tested and it does work with both 32bit and 64bit Hardy Heron I'm very happy to say. Just follow the directions step by step, using the command prompt. YOu can be in any directory to start, I chose to be in my home directory. 
Again, note that when you download the txt patch, rename it to have a **.diff** extension. This is what I missed the first 20 times.
ALso, before you start you have to install fakeroot with:
sudo apt-get install fakeroot

After oyu complete all the steps, you will have a bunch of .debs but you only need to run these:
linux-image-rt
linux-headers-rt
linux-headers-lum-rt
linux-ubuntu-modules-rt

They might look more like this:
linux-**image**-2.6.24.19-**rt**

Then install envy:

sudo apt-get install envy and do a manual install of the latest NVIDIA drivers using envy.
Then reboot, and you should come up in 1680 by default and be able to use compiz.

NOTE: Ubuntu updater will want you to install it's own deb packages of the same name again but just ignore them, or else the patch will break.

---

### Post by StormPCs on 2008-07-09
How do I install the last 4 debs?

Also, what changes do I need to make to the code for 64 bit Ubuntu?:confused:

Thanks in advance.

---

### Post by wolfwood2x on 2008-07-09
add2700 you sir are my personal hero...
after your steps the only thing i had to do was tweak xorg.conf to see another mode other than 640x480


Thank you so very much!

---

### Post by StormPCs on 2008-07-09
I have 8 debs, not 4.  Not sure which to install.

---

### Post by StormPCs on 2008-07-10
I figured it out...thanks very much for the help guys.  I do have a question though:  I keep getting prompted to update one of the debs that I loaded.  If I allow this will it break the patch?:confused:

Thanks again guys,,,you rock!:guitar:

---

### Post by wolfwood2x on 2008-07-10
add2700 indicated that it would indeed break the patch. I would not recommend doing that. 

> NOTE: Ubuntu updater will want you to install it's own deb packages of the same name again but just ignore them, or else the patch will break. 

Cheers

---

### Post by add2700 on 2008-07-10
Yes, DO NOT install any of ubuntu's patches of the same name as you created. Apparently you can't tell ubuntu to not advertise those individual patches.

---

### Post by StormPCs on 2008-07-10
Is there any chance they will address this issue in future kernel releases?  It's sort of a big deal,

---

### Post by splinterpaw on 2008-07-24
> **add2700 said:**
> Yes, DO NOT install any of ubuntu's patches of the same name as you created. Apparently you can't tell ubuntu to not advertise those individual patches.

It's too bad it's not it's not possible to tell Ubuntu to ignore those patches.  Having the notification icon up all the time is a bit annoying.

---

### Post by apollo88 on 2008-08-03
Hi add2700,

I'm following your indications but I can't go on after executing the line:

> **add2700 said:**
> 
...

sudo CONCURRENCY_LEVEL=2 fakeroot debian/rules custom-binary-rt

...



it gives me the following error:

/usr/bin/fakeroot: 166: debian/rules.d: Permission denied

don't know what else to do... Thanks in advance for any help,

Apollo

---

### Post by mcurran on 2008-08-06
apollo:  Did you make sure to have all the dependencies/packages (build-essential, configure-debian, and fakeroot)?  Did you do apt-get update first?

If it's a permission error, maybe you do not have root privelages.  Try typing sudo -s, then password, cd to the Desktop/or wherever the kernel is, and then try again.

I was wondering if anybody knew what to type for that line; if you want to use the generic kernel instead of rt.  Is it just...

sudo CONCURRENCY_LEVEL=2 fakeroot debian/rules custom-binary-debs, just like the modules?

I have a Core2Duo and I'm not sure if I should use generic instead of rt.  I have successfully used both with this patch, but I'm not sure what will better utilize my CPU.

Also, I don't even know if it matters what I type for the initial download, because I seem to get all versions of the kernel when I create the debs anyways.

---

### Post by VernieR on 2008-08-07
Well, I have an ASUS G1Sn too with 3Gb of RAM. I have the same driver issues, but the kernel patch doesn't seem to make any difference.
I don't know what I'm doing wrong.. (I'm running Ubuntu 8.04 32 bit)

Does anyone know if and when either kernel or nvidia drivers get fixed?

Oh and is there a way to run the vesa or nv drivers in 1680x1050, that would be sufficient. I can do without 3d for now. Browsing these forums in 800x600 is a pain.

---

### Post by wolfwood2x on 2008-08-12
> **VernieR said:**
> Well, I have an ASUS G1Sn too with 3Gb of RAM. I have the same driver issues, but the kernel patch doesn't seem to make any difference.
I don't know what I'm doing wrong.. (I'm running Ubuntu 8.04 32 bit)

Does anyone know if and when either kernel or nvidia drivers get fixed?

Oh and is there a way to run the vesa or nv drivers in 1680x1050, that would be sufficient. I can do without 3d for now. Browsing these forums in 800x600 is a pain.

Not sure when or if Nvidia will fix the drivers. However, after running the kernel patch I still had to use envy to install the correct video driver and manually edit my xorg.conf in order to get anything other than 800x600 working. Have you already done that as well and still can not get it to work?

---

### Post by apollo88 on 2008-08-16
Hi everybody,
I just wanted to thank you all for your help... IT'S WORKING!!!
Thanks for sharing your knowledge...
Apollo

---

### Post by VernieR on 2008-08-17
OK, it works now. I used the fix after a clean install. Last time I had been fiddling around with drivers before I tried to patching the kernel. I guess thats was the problem. Thanks to all, and now lets hope we get a proper fix in future kernel or nvidia drivers :)

---

### Post by Hideaki on 2008-10-11
This problem still persist on Ubuntu 8.10 Beta. I'm currently building a 2.6.27 kernel with the instructions found a few posts back and the patch, hopefully it will work.

Has there been any talk about fixing this issue without the need for a kernel patch and recompilation?

---

### Post by Nekomancer on 2008-10-16
> **add2700 said:**
> 
After oyu complete all the steps, you will have a bunch of .debs but you only need to run these:
linux-image-rt
linux-headers-rt
linux-headers-lum-rt
linux-ubuntu-modules-rt

They might look more like this:
linux-**image**-2.6.24.19-**rt**



Hello. Ive been doing the procedure to fix the problem. I got to the part to where i have to 'install' the debs. Unfortunately at this step i only found 2 debs: the linux-image-rt and the linux-headers-rt. Maybe im not sure where the compiler put them.

Im really really new to ubuntu, so im probably missing something. Should there be more debs?

Finally. It took me a while to find out how to install a deb. For newbies this is not something obvious. Maybe its worthwhile to mention that you install them with:

```
sudo dpkg -i <package.deb>
```

EDIT: I got help from a friend and i think one of the steps was compiled wrong because after we tried it again, we found all the debs. 

At first Ubuntu did load the driver for 9500m gs, but it would only allow 600x400 resolution. We had to use envy to fix it after some trial-error.

I still don't have 3D or OpenGL but at least i have 1600x800 resolution (against the 800x600 which i had at first).

---

### Post by mcurran on 2008-11-03
Nekomancer:  You need to install the nvidia drivers after you have installed the new kernel image (all these steps you just did) - If you're new to Ubuntu, you should just download/use EnvyNG.

Wolfwood:  If you want to just use the vesa driver, do "sudo displayconfig-gtk, or sudo displaysettings-gtk (not sure which)" but you'll then be able to setup your monitor/vesa driver correctly...

---

### Post by splinterpaw on 2008-11-04
Has anyone had any luck on getting this to work with the 8.10 final release?  When I try to get the RT sources for 2.6.27-7 (the current version I have of the kernel) it says they are not available.

I had this working fine with 8.03 before upgrading and really need to get it working again.  I would like to keep 8.10 as I do like several of the changes made and would hate to have to reinstall everything....

---

### Post by JaCkYL_CpX on 2008-11-05
I have this same laptop duel booted with the newest Ubuntu release with total frustration. I have reinstalled Ubuntu numerous times tried the fixes I ended up rebuilding a kernal that had no drivers instead to no avail...I am new to linux but no where near new to computers I work in the IT field.  I have had numerous Linux folks from my place of employment try to figure this out including a linux admin for our company we are all scratching our heads is there a simple total newb install way to make this video card work? I am trying to make the full switch over to linux but i am a gamer so taking 2 gig out of a system i purchased with 4 gig just doesnt make any logical sense to me.
 Thanks for your patience and any replies the last time i tried switching over to learn linux i couldnt get anywhere either which is dissappointing....

---

### Post by splinterpaw on 2008-11-06
Found a post about this in another thread, [http://ge.ubuntuforums.com/showthread.php?t=939580](http://ge.ubuntuforums.com/showthread.php?t=939580).  Going to give the suggestions there a try and see if I am able to get it working.  I will post here and let everyone know how it goes.

---

### Post by Hideaki on 2008-11-07
I posted a brief overview of the process under Intrepid in this thread: [http://ge.ubuntuforums.com/showthread.php?t=939580](http://ge.ubuntuforums.com/showthread.php?t=939580) as mentioned in the post above me. I'll write more clear instructions for getting your laptop running on Intrepid.

You will also find the modified patch file for the new 2.6.27 kernel, attached to this post.

These instructions are based on add2700's post, which are based on a post in nvnews.net =P

-----------------------------------------
**# A few notes before we start:**
 - I have only tested this under 64-bit Ubuntu 8.10, but it presumably works under 32-bit Ubuntu as well.
 - After you have finish compiling and installing your kernel, Update Manager might want to overwrite it with its own version of it. Make sure not to do this!
 - You will have to do this process _every time Ubuntu releases a kernel update_(or until it the issue is fixed by the OEM...if ever). If you do not wish to go through the process again, make sure not to update your kernel(linux-image, or linux-header packages).

**# Install necessary packages**
sudo apt-get install fakeroot
sudo apt-get build-dep linux-image-2.6.27-*****-generic

**# Install Kernel Sources**
sudo apt-get source linux-image-2.6.27-*****-generic

**# * NOTE: Replace the * with the latest 2.6.27 revision number(9 as of right now).**

**#<!-- Download the 512 patch if your card has 512 RAM, or the 256 if your card has 256 RAM-->**
#<!-- RENAME the file from .txt to .diff as show below, and if your card has 256 RAM don't forget to alter the command accordingly-->
**# Apply NVRM patch**
sudo patch -p0 < NVRM_512M_fix.diff

**# Build debs for linux-image & linux-headers**
cd linux-2.6.27/
sudo CONCURRENCY_LEVEL=2 fakeroot debian/rules binary-debs flavours=generic

**# Lastly, run the deb packages you created above in this order:**
linux-image-generic
linux-headers-generic

---

### Post by JaCkYL_CpX on 2008-11-08
I would like to thank everyone for the input on this card and the issues I do hope soon they get a fix out for this but after two weeks multiple installs the instructions listed above work now I am just afraid to download any updates of any sort ..... Also I would like to state this video card with acceleration does not talk well with two monitors extended desktop it flakes out and also locks up x windows on numerous occasions when switched between desktops but anyways yay for acceleration 
Thanks

---

### Post by Hideaki on 2008-11-13
> **JaCkYL_CpX said:**
> I would like to thank everyone for the input on this card and the issues I do hope soon they get a fix out for this but after two weeks multiple installs the instructions listed above work now I am just afraid to download any updates of any sort ..... Also I would like to state this video card with acceleration does not talk well with two monitors extended desktop it flakes out and also locks up x windows on numerous occasions when switched between desktops but anyways yay for acceleration 
Thanks

The dual-screen issue is kind of odd. I use my laptop with a projector all the time, and it works just fine. What utility are you using for handling multiple screens? Using the nvidia x server settings is probably your best bet, it works great.

---

### Post by mcurran on 2008-11-19
Get lost JaCkYL_CpX.  This is one of the only solutions for us with these nvidia cards and 3+ GB of RAM, and nobody cares if you're too lazy to recompile.  I'm completely greatful for Fourmiii taking the time to share this information - Fourmiii, you're the man!

Does anyone know if this patch will be necessary for x64 releases, and if so; will it work, or just break the x64 architecture, since we're using i386 code in the patch?

---

### Post by plunder on 2008-11-19
I have an Acer Aspire 6920G, I'm running the nVidia 9500 as well, ubuntu 8.10 desktop x64, worked right out of the box, it does catergorize it as a Restricted Hardware Driver. No problems with video yet.... wish I could say the same for sound.

---

### Post by lorenfb on 2008-11-22
Attempting to load 8.10 results in system crash shortly before
install completion. Tried the direct install twice with same
results. Appears to run off of 8.10 CD O.K. Version 7.10 crashes
immediately when the video driver is tested during the CD load.
Version 8.10 appears to make BIOS changes during the install.

System:
HP Slimline - AMD Quad 9100, 4GB RAM, NVIDIA 9500GS/512MB, SATA 250GB

Based on previous posts, it appears that the 4GB RAM and the 9500GS
video may be the sources of the problem for both 7.10 and 8.10. 

Had hoped to use a direct eSATA 8.10 install to selectively utilize
Ubuntu without having a partitioned drive, but any 8.10 install is 
problematic. So, it's back to using Vista.

---

### Post by add2700 on 2008-11-25
I did an upgrade to 8.10 on my ASUS laptop with NVIDIA 9700 and it rocks with 1680X1050 res.

---

### Post by drdeath691 on 2008-11-27
Just wanted to say Thanks a lot to all inputs in this post. I was able to get MY laptop up and going using the Patch. I tried a fresh install using latest updates but it didn't work. Using the patch was the only thing that worked for me. My only issue is that I can't get 1680x1050 resolution. I know my laptop and video card can support it but I just can't figure it out. Any help would be great.

Current Xorg.Conf:

# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@crested)  Mon Nov  3 08:46:04 UTC 2008

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "AUO"
    HorizSync       30.0 - 75.0
    VertRefresh     60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9500M GS"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

---

### Post by add2700 on 2008-11-27
Sorry people, 8.10 does run 1680 res in basic mode but not with the NVIDIA driver so it's slow. Going to try to recompile again.

---

### Post by splinterpaw on 2008-12-03
Updated the Ubuntu kernal recently on my G1SN and am having problems running the command: 

sudo apt-get source linux-image-2.6.27-9-generic

Regardless of what version I put in for this command, the following is returned:

Unable to find a source package for linux

Any ideas if something changed with the recent updates?  This did work before with the 2.6.27-7 kernal but does not seem to be working now.

---

### Post by splinterpaw on 2008-12-09
> **splinterpaw said:**
> Updated the Ubuntu kernal recently on my G1SN and am having problems running the command: 

sudo apt-get source linux-image-2.6.27-9-generic

Regardless of what version I put in for this command, the following is returned:

Unable to find a source package for linux

Any ideas if something changed with the recent updates?  This did work before with the 2.6.27-7 kernal but does not seem to be working now.
Finally had a chance to play with this and figured it out.  It turns out that not all of the needed repositories were active on my install, therefore it could not find the image.  I have activated the necessary repositories and it is working now.

---

### Post by kyllikki on 2008-12-14
> - You will have to do this process every time Ubuntu releases a kernel update(or until it the issue is fixed by the OEM...if ever). If you do not wish to go through the process again, make sure not to update your kernel(linux-image, or linux-header packages).

In compliment to this post is it possible for somebody to describe how to prevent the linux-image and linux-header packages from getting updated?  I have tried 'locking' these packages in Synaptic but no such luck - they still get overridden if an update is ran.

---

### Post by siddtharth on 2008-12-15
I have the same problem only difference is I have 3gb RAM and NVIDIA 7600Go with has 128MB dedicated memory. I tried to modify the 256MB patch and changed 'r->end = 0xd0000000' to 'r->end = 0xc8000000' to created 128MB gap, but this didn't work so can you tell me if this is the correct way to do this for my config ? I have attached out put of `dmesg`

---

### Post by Rinias on 2008-12-18
What is the status of this "fix" for 8.10, please ?

I am considering doing this (Asus G1Sn-B1 with 8.10 amd64), but if it is not working, I think I'd rather stick with nv instead of going through the headache of doing a kernel recompile in a system that doesn't like that sort of thing (think Synaptic updates). After all, if I wanted to recompile things, I'd go with a different flavor...

And if the fix is simply to patch the kernel, why has this not yet been done ? How hard could it be to patch the kernel for this and use some kind of hardware detection in the restricted drivers dialogue in order to give us what we need ? Ie, installing the correctly patched kernel and then the nvidia driver via the Hardware Drivers dialogue ?

I think I'll give it a go anyway, and I'll post back here with my success (or lack thereof) in a bit...

Rinias

PS : Anyone know why the generic kernel (2.6.27-9) would have Xen (and thus be non-compatible with the standard nvidia .run package install method) ?
( PPS : Is the rt kernel necessary to this method or will any kernel do ? ) ==> Reading the all of the original post would be good...

[quote="add2700"]```
# Modify flavours in debian/rules.d/amd64.mk (rt instead of generic)
sudo CONCURRENCY_LEVEL=2 fakeroot debian/rules custom-binary-rt
```[/quote]

Fourniii from the nvnews forums also makes a note :
> 
Here's the new way of doing it, note the editing of amd64.mk to only build the rt flavour.

I'll be outside if you're looking for me :s

PPS (v2) : add2700, I see that you updated for 8.10 x86_64 on the nvnews forums. You added two links, one to backports.ubuntu and the other to Envy. The backports link doesn't seem to work, is there somewhere else I can access this information ?

---

### Post by Rinias on 2008-12-18
Ok, so Im following :

[quote="add2700"]# Install Kernel Sources
sudo apt-get build-dep linux-image-2.6.24-19-rt
sudo apt-get source linux-image-2.6.24-19-rt

# Install Kernel Modules Sources
sudo apt-get build-dep linux-ubuntu-modules-2.6.24-19-rt
sudo apt-get source linux-ubuntu-modules-2.6.24-19-rt

#<!-- Download the 512 patch if your card has 512 RAM, or the 256 if your card has 256 RAM-->
#<!-- RENAME the file from .txt to .diff as show below, and if your card has 256 RAM don't forget to alter the command accordingly-->
# Apply NVRM patch
sudo patch -p0 < NVRM_512M_fix.diff

[...][/quote]

Except that :

[LIST=1]
[*]I switched from linux-image-2.6.24-19-rt to linux-image-2.6.27-3-rt and there are no linux-ubuntu-modules* so I installed linux-restricted-modules-2.6.27-3-rt
[*]Inspection of the .diff file gives :
```
diff -Naur linux-2.6.24.orig/arch/x86/pci/i386.c linux-2.6.24/arch/x86/pci/i386.c
--- linux-2.6.24.orig/arch/x86/pci/i386.c	2008-06-03 20:24:26.000000000 -0400
+++ linux-2.6.24/arch/x86/pci/i386.c	2008-06-03 20:25:40.000000000 -0400
```
Needless to say, these files do not exist. What is interesting is that the command 
```
sudo patch -p0 < NVRM_512M_fix.diff
```
is not given with a cd into a directory and when prompted with the "File to patch :" from the patch command (because the error is that the file is not found - which is normal), I cannot figure out what to enter.
[/LIST]

Furthermore, the kernels in /usr/src are not built, so there are no i386.c files (nor any other *.c 's - just Makefiles), but no instructions on building are given for the fix. Where this another system, I'd go along with my usual make oldconfig && make menuconfig, etc., etc. but this is Ubuntu and I've broken it before with such tactics...

So - any update on these instructions ? Anyone have any information that might prove useful ?

Thanks in advance,

Rinias

---

### Post by twisted_steel on 2008-12-18
Sorry to go slightly off topic, but can the others with the G1SN laptop who are running into the issue add any missing information from Splinterpaw's bug on Launchpad?

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/288843](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/288843)

Thanks.

---

### Post by Rinias on 2008-12-19
> **twisted_steel said:**
> Sorry to go slightly off topic, but can the others with the G1SN laptop who are running into the issue add any missing information from Splinterpaw's bug on Launchpad?

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/288843](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/288843)

Thanks.

Thank you - I posted my dmesg and iomem (the OP never did, it seems). Hopefully this will be resolved shortly. It is rather bothersome, considering the fact that this problem is known for many different distros and that it is not new.

Rinias

---

### Post by twisted_steel on 2008-12-20
> **Rinias said:**
> Thank you - I posted my dmesg and iomem (the OP never did, it seems). Hopefully this will be resolved shortly. It is rather bothersome, considering the fact that this problem is known for many different distros and that it is not new.

Rinias

I'm really not sure what the status is on trying to fix the overall allocation problem, but I figured that we could at least try to make sure there are enough related bug reports out there to help.

---

### Post by Rinias on 2008-12-21
> **twisted_steel said:**
> I'm really not sure what the status is on trying to fix the overall allocation problem, but I figured that we could at least try to make sure there are enough related bug reports out there to help.

Indeed.

I've had no luck with the patching. As far as I can tell, the kernel must be compiled to have the i386.c (in arch/x86/pci). When I compile the kernel, I do in fact get this file. The problem thereafter is - for me - two-fold :

- I cannot know where to insert the lines in i386.c (the position changes from kernel version to kernel version...) so I cannot manually apply the patch.
- I don't have any idea how, in Ubuntu, to simply use the changed files to repackage a kernel in a .deb for installation purposes (assuming that I knew the exact location for the patch code).

I can confirm, however, that there is no fix with 2.6.27-11-generic which came out yesterday.

Rinias

---

### Post by twisted_steel on 2008-12-21
> **Rinias said:**
> - I don't have any idea how, in Ubuntu, to simply use the changed files to repackage a kernel in a .deb for installation purposes (assuming that I knew the exact location for the patch code).

I found two sets of instructions that might be of use:
- [http://ubuntuforums.org/showthread.php?t=56835](http://ubuntuforums.org/showthread.php?t=56835)
- [http://www.howtoforge.com/roll_a_kernel_debian_ubuntu_way](http://www.howtoforge.com/roll_a_kernel_debian_ubuntu_way)

---

### Post by Hideaki on 2008-12-24
If you look further back in this thread you will see that I posted updated instructions on how to get the patch working with the latest kernels.

[http://ubuntuforums.org/showpost.php?p=6122978&postcount=37](http://ubuntuforums.org/showpost.php?p=6122978&postcount=37)

---

### Post by couzin2000 on 2009-01-06
Hi all,

I'm looking to buy an **ASUS M51Sn-B1**, with the same **NVidia 9500GS** chip, and the same **4Gb of RAM**. Anyone heard that this problem would occur on this laptop as well?

I'm sure it'll be solved eventually, but in the meantime, is there a bugreport that can be followed? I'd like to see what's going on with this.

Thanks

---

### Post by rrsn on 2009-01-06
Hello add2700, I have the Asus G1Sn with 4GB Ram e nVidia 9500M.

I follow your steps to instal de 9500M in Ubuntu 8.04 32Bit and works perfects. But it just recognized 3GB Ram.

So, if I install Ubuntu 8.04 64Bit or Ubuntu 8.10 64Bit, Will I need follow your steps again to install nVidia 9500M or it will recognized and works alone?

Tks
Roberto

> **add2700 said:**
> Ok finally got 1680X1050 resoltuion using the nvidia driver on a 32bit install of 8.04 on my ASUS G1sn-A1 laptop. Here are the exact steps I took, but I take no responsibility if you don't get it to work and have to reinstall.

1. Start with a fresh install of ubuntu 8.04 32 bit, and run all the advertised patches. 
2. Next, follow theses steps, taken from the good people at [nvnews]("http://www.nvnews.net/vbulletin/showpost.php?p=1673409&postcount=27"):

# Install Kernel Sources
sudo apt-get build-dep linux-image-2.6.24-19-rt
sudo apt-get source linux-image-2.6.24-19-rt

# Install Kernel Modules Sources
sudo apt-get build-dep linux-ubuntu-modules-2.6.24-19-rt
sudo apt-get source linux-ubuntu-modules-2.6.24-19-rt

#**<!-- Download the 512 patch if your card has 512 RAM, or the 256 if your card has 256 RAM-->**
#**<!-- RENAME the file from .txt to .diff as show below, and if your card has 256 RAM don't forget to alter the command accordingly-->**
# Apply NVRM patch
sudo patch -p0 < NVRM_512M_fix.diff

# Build debs for linux-image & linux-headers
cd linux-2.6.24/
# Modify flavours in debian/rules.d/amd64.mk (rt instead of generic)
sudo CONCURRENCY_LEVEL=2 fakeroot debian/rules custom-binary-rt
cd ..

# Build 
cd linux-ubuntu-modules-2.6.24-2.6.24/
# Modify flavours in debian/rules.d/amd64.mk (rt instead of generic)
sudo CONCURRENCY_LEVEL=2 fakeroot debian/rules binary-debs
cd ..

3. Lastly, run the deb packages you created above in this order:
You should then install the 4 debs :
linux-image-rt
linux-headers-rt
linux-headers-lum-rt
linux-ubuntu-modules-rt

Thanks again to the people at [nvnews.net]("http://www.nvnews.net").

---

### Post by mcurran on 2009-01-08
For those of you getting the error message asking which file to patch:  Make sure you have all the dependencies fourmii listed:

build-essential
fakeroot
configure-debian

This is just a suggestion, but I believe I was missing build-essential or something when I got that message.  If you don't have that app., then x doesn't know what that patch command is saying.

---

### Post by mcurran on 2009-01-24
Does anyone know why the latest kernel 2.6.27-11-generic builds an amd64 kernel with these instructions?  Is it O.K. to install on my G1Sn (Intel)?

---

### Post by mcurran on 2009-02-06
I tried to install the latest 64-Bit kernel (2.6.27-11-generic) and they download correctly; however my system decides to build 2.6.27-12-generic packages on it's own from these.  This would be fine and all, but there isn't any 2.6.27-12 headers yet and so they won't install without those dependencies available.  Does anyone have any suggestions on how I can force my system to only build the previous release 2.6.27-11-generic (image and headers)?

Please let me know.

Thanks,

Mike

---

### Post by mcurran on 2009-02-07
Sorry to keep bumping this thread, but has anybody gotten this to work within the last week.  There's still an error when trying to install the deb linux-headers package.  It's saying they're not installed or available 2.6.27-12-generic (amd64)!!!!

---

### Post by Flaw on 2009-02-17
Gonna continue bumping this since I'm suffering from this too. I take it that the fixes posted before were only for x86, so what should I do with a x86_64 then? 
What I do know is that the drivers do not work with a fully up-to-date 64bit system without somesort of a workaround, aaaaand that's pretty much it. Any pointers from here on would be appreciated.
(Also running a G1Sn with 9500M GS and 3GB of ram, altough I removed 1GB just to get it working for now.)

---

### Post by proalan on 2009-02-17
Nvidia seem to be making giant strides backwards. Their drivers don't even work with the graphics card listed as supported. I'm having to run linux on virtualbox these days.

With regards to the g1sn, ASUS's official stance is they don't support linux even though the problem lies indirectly with the faulty BIOS. There are no plans to release a fixed BIOS going by their forums.

---

### Post by Rinias on 2009-02-23
> **Flaw said:**
> Gonna continue bumping this since I'm suffering from this too. I take it that the fixes posted before were only for x86, so what should I do with a x86_64 then? 
What I do know is that the drivers do not work with a fully up-to-date 64bit system without somesort of a workaround, aaaaand that's pretty much it. Any pointers from here on would be appreciated.
(Also running a G1Sn with 9500M GS and 3GB of ram, altough I removed 1GB just to get it working for now.)

Sorry for never responding, but thank you Hideaki, your instructions do indeed work.

For Flaw and mcurran, follow the instructions here : [http://ubuntuforums.org/showpost.php?p=6122978&postcount=37](http://ubuntuforums.org/showpost.php?p=6122978&postcount=37)

The kernel version is currently 2.6.27-11(-generic) just like in the instructions. Following the instructions to the letter (replacing * by 11) and applying the correct patch does indeed work, though the bothersome update manager always wants you to update to 2.6.27-11-generic.

Note also that you will have to go up one directory from your build directory (linux-2.6.27 -- so cd .. would do the trick) to install the packages (sudo dpkg -i linux-image-2.6.27-11-generic-blahblahblah.deb linux-headers-2.6.27-11-generic-blahblahblah.deb).

Rinias

PS : I've tried setting apt to hold the kernel versions but they still end up in the update manager and I don't see a way to blacklist the packages. Too bad, really...

---

### Post by darkzerox on 2009-03-13
This might be a dumb question, but what to do AFTER these instructions ([http://ubuntuforums.org/showpost.php?p=6122978&postcount=37](http://ubuntuforums.org/showpost.php?p=6122978&postcount=37))? From my understanding, that doesn't actually install any drivers. Is it then safe to install the drivers from System > Admin > Hardware Drivers? Or should I install the official drivers from the nvidia website?

---

### Post by Rinias on 2009-03-15
> **darkzerox said:**
> This might be a dumb question, but what to do AFTER these instructions ([http://ubuntuforums.org/showpost.php?p=6122978&postcount=37](http://ubuntuforums.org/showpost.php?p=6122978&postcount=37))? From my understanding, that doesn't actually install any drivers. Is it then safe to install the drivers from System > Admin > Hardware Drivers? Or should I install the official drivers from the nvidia website?

That's exactly right.

Just so everyone knows, this problem turns out to be an IOMEM issue and there is now someone working on it. Hopefully there will be a solution in the kernel in the near future.

Rinias

---

### Post by Graziello on 2009-04-01
But for people who has 32 bit cpu with an nvdidia 9500m gs and 4 gb ram is there a solution? Because this patch doesn't work :(

---

### Post by proalan on 2009-04-01
I've been watching this topic for months now, apparently this issue will be addressed in future kernels [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/288843](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/288843)

I'm just another linux refugee looking forward to returning when it finally works.

---

### Post by VernieR on 2009-04-05
I have just applied this patch to 9.04 beta. Works like a charm. Since 9.04 uses a newer kernel version 2.6.28 I had to change this in the patch file.

Now lets hope it gets fixed soon :)

---

### Post by bkief12 on 2009-04-07
> **Hideaki said:**
> I posted a brief overview of the process under Intrepid in this thread: [http://ge.ubuntuforums.com/showthread.php?t=939580](http://ge.ubuntuforums.com/showthread.php?t=939580) as mentioned in the post above me. I'll write more clear instructions for getting your laptop running on Intrepid.

You will also find the modified patch file for the new 2.6.27 kernel, attached to this post.

These instructions are based on add2700's post, which are based on a post in nvnews.net =P

-----------------------------------------
**# A few notes before we start:**
 - I have only tested this under 64-bit Ubuntu 8.10, but it presumably works under 32-bit Ubuntu as well.
 - After you have finish compiling and installing your kernel, Update Manager might want to overwrite it with its own version of it. Make sure not to do this!
 - You will have to do this process _every time Ubuntu releases a kernel update_(or until it the issue is fixed by the OEM...if ever). If you do not wish to go through the process again, make sure not to update your kernel(linux-image, or linux-header packages).

**# Install necessary packages**
sudo apt-get install fakeroot
sudo apt-get build-dep linux-image-2.6.27-*****-generic

**# Install Kernel Sources**
sudo apt-get source linux-image-2.6.27-*****-generic

**# * NOTE: Replace the * with the latest 2.6.27 revision number(9 as of right now).**

**#<!-- Download the 512 patch if your card has 512 RAM, or the 256 if your card has 256 RAM-->**
#<!-- RENAME the file from .txt to .diff as show below, and if your card has 256 RAM don't forget to alter the command accordingly-->
**# Apply NVRM patch**
sudo patch -p0 < NVRM_512M_fix.diff

**# Build debs for linux-image & linux-headers**
cd linux-2.6.27/
sudo CONCURRENCY_LEVEL=2 fakeroot debian/rules binary-debs flavours=generic

**# Lastly, run the deb packages you created above in this order:**
linux-image-generic
linux-headers-generic

I follow this step for step and i am down to 
**# Lastly, run the deb packages you created above in this order:**
linux-image-generic
linux-headers-generic

and i get bash: linux-image-generic: command not found
when it try to run it with or without sudo 

Thank,
Bkief

---

### Post by bkief12 on 2009-04-07
Okay so i figured out i need to do

> sudo dpkg -i linux-image-generic 

but the package is not found 

> dpkg: error processing linux-image-generic (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 linux-image-generic

Where is the package??

---

### Post by Rinias on 2009-04-07
> **Rinias said:**
>  

[blah blah blah]

Note also that you will have to go up one directory from your build directory (linux-2.6.27 -- so cd .. would do the trick) to install the packages (sudo dpkg -i linux-image-2.6.27-11-generic-blahblahblah.deb linux-headers-2.6.27-11-generic-blahblahblah.deb).


[more blah blah blah]

That help ?

---

### Post by Rinias on 2009-04-07
Quoting the instructions from Hideaki (thanks again!), and adding the "cd" line :


> **Hideaki said:**
> I posted a brief overview of the process under Intrepid in this thread: [http://ge.ubuntuforums.com/showthread.php?t=939580](http://ge.ubuntuforums.com/showthread.php?t=939580) as mentioned in the post above me. I'll write more clear instructions for getting your laptop running on Intrepid.

You will also find the modified patch file for the new 2.6.27 kernel, attached to this post.

These instructions are based on add2700's post, which are based on a post in nvnews.net =P

-----------------------------------------
**# A few notes before we start:**
 - I have only tested this under 64-bit Ubuntu 8.10, but it presumably works under 32-bit Ubuntu as well.
 - After you have finish compiling and installing your kernel, Update Manager might want to overwrite it with its own version of it. Make sure not to do this!
 - You will have to do this process _every time Ubuntu releases a kernel update_(or until it the issue is fixed by the OEM...if ever). If you do not wish to go through the process again, make sure not to update your kernel(linux-image, or linux-header packages).

**# Install necessary packages**
sudo apt-get install fakeroot
sudo apt-get build-dep linux-image-2.6.27-*****-generic

**# Install Kernel Sources**
sudo apt-get source linux-image-2.6.27-*****-generic

**# * NOTE: Replace the * with the latest 2.6.27 revision number(9 as of right now).**

**#<!-- Download the 512 patch if your card has 512 RAM, or the 256 if your card has 256 RAM-->**
#<!-- RENAME the file from .txt to .diff as show below, and if your card has 256 RAM don't forget to alter the command accordingly-->
**# Apply NVRM patch**
sudo patch -p0 < NVRM_512M_fix.diff

**# Build debs for linux-image & linux-headers**
cd linux-2.6.27/
sudo CONCURRENCY_LEVEL=2 fakeroot debian/rules binary-debs flavours=generic

**# Lastly, run the deb packages you created above in this order:**

cd .. **<== missing**

linux-image-generic
linux-headers-generic

---

### Post by Rinias on 2009-04-07
> **proalan said:**
> I've been watching this topic for months now, apparently this issue will be addressed in future kernels [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/288843](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/288843)

I'm just another linux refugee looking forward to returning when it finally works.

This is indeed the old post. As I said in an earlier post, the problem is actually with IOMEM.

Here is the bug page for the IOMEM bug :

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/342926](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/342926)

On a side note, I tested OpenSolaris the other day and had absolutely no problems with the driver... Go figure.

Rinias

---

### Post by Graziello on 2009-04-09
> **Rinias said:**
> This is indeed the old post. As I said in an earlier post, the problem is actually with IOMEM.

Here is the bug page for the IOMEM bug :

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/342926](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/342926)

On a side note, I tested OpenSolaris the other day and had absolutely no problems with the driver... Go figure.

Rinias

Yes, but i hope TJ will patch the kernel as soon as possible otherwise i can only use linux on virtualbox

---

### Post by Rinias on 2009-04-13
> **Graziello said:**
> Yes, but i hope TJ will patch the kernel as soon as possible otherwise i can only use linux on virtualbox

TJ says it will be in the kernel at the earliest by .30 or .31

I don't know what that means in terms of when it will arrive, but it can't be too long now.

Rinias

PS : bkief12, did you find your packages ?

---

### Post by siddtharth on 2009-04-16
My hardware is a little different, I have sony vaio with nvidia 7600 GO which has 128MB memory, so my question is what should I change in the patch file, I'm using ubuntu 9.04 --Thanks!

---

### Post by Graziello on 2009-04-17
Are you sure you have the same problem? Have you more than 4gb of ram?

---

### Post by siddtharth on 2009-04-17
Yes I have the same problem, and no I have 3gb RAM. I have one 2GB memory and one 1GB memory, when I have 2GB it works just fine, but when I make it 3GB it breaks.

---

### Post by Graziello on 2009-04-17
Ok. I don't know if the patch work with your video card. You can try. You must modify the patch with your kernel version.
Remember you must have a 64 bit CPU

---

### Post by siddtharth on 2009-04-17
yes I do have a 64 bit CPU and 64 bit ubuntu 9.04 and I had tried that patch and it did not work. Is there anything else that I can try ? I also tried to modify the address range in that patch to make a gap of 128MB instead of 512MB, but it still doesn't work :(

---

### Post by Graziello on 2009-04-17
I don't know, i'm sorry

---

### Post by rrsn on 2009-04-24
I read all topic but cant find a way to install my nVidia 9500M.

I have installed Ubuntu 8.10 32bit, my notebook is ASUS G1Sn with nVidia GeForce 9500M 512MB.

There is a way to install, like a step-by-step?

tks a lot
Roberto

---

### Post by rrsn on 2009-04-25
> **Hideaki said:**
> I posted a brief overview of the process under Intrepid in this thread: [http://ge.ubuntuforums.com/showthread.php?t=939580](http://ge.ubuntuforums.com/showthread.php?t=939580) as mentioned in the post above me. I'll write more clear instructions for getting your laptop running on Intrepid.

You will also find the modified patch file for the new 2.6.27 kernel, attached to this post.

These instructions are based on add2700's post, which are based on a post in nvnews.net =P

-----------------------------------------
**# A few notes before we start:**
 - I have only tested this under 64-bit Ubuntu 8.10, but it presumably works under 32-bit Ubuntu as well.
 - After you have finish compiling and installing your kernel, Update Manager might want to overwrite it with its own version of it. Make sure not to do this!
 - You will have to do this process _every time Ubuntu releases a kernel update_(or until it the issue is fixed by the OEM...if ever). If you do not wish to go through the process again, make sure not to update your kernel(linux-image, or linux-header packages).

**# Install necessary packages**
sudo apt-get install fakeroot
sudo apt-get build-dep linux-image-2.6.27-*****-generic

**# Install Kernel Sources**
sudo apt-get source linux-image-2.6.27-*****-generic

**# * NOTE: Replace the * with the latest 2.6.27 revision number(9 as of right now).**

**#<!-- Download the 512 patch if your card has 512 RAM, or the 256 if your card has 256 RAM-->**
#<!-- RENAME the file from .txt to .diff as show below, and if your card has 256 RAM don't forget to alter the command accordingly-->
**# Apply NVRM patch**
sudo patch -p0 < NVRM_512M_fix.diff

**# Build debs for linux-image & linux-headers**
cd linux-2.6.27/
sudo CONCURRENCY_LEVEL=2 fakeroot debian/rules binary-debs flavours=generic

**# Lastly, run the deb packages you created above in this order:**
linux-image-generic
linux-headers-generic

Nice, did work perfect in my Ubuntu 8.10 32bit. I have aply the path in Linux 2.6.27-14-generic

Next step is apply on Ubunt 9.04 :lolflag:

---

### Post by Graziello on 2009-04-25
Nice because you have a 64 bit CPU, no way with a 32 bit CPU ](*,)](*,)

---

### Post by rrsn on 2009-04-25
> **Graziello said:**
> Nice because you have a 64 bit OS, no way with a 32 bit OS ](*,)](*,)

No way, I have install on Ubuntu 8.10 32Bit and work perfect.

Did you have problem to apply path on Ubuntu 8.10 32Bit?

---

### Post by Graziello on 2009-04-25
Sorry, 64 bit CPU not OS

---

### Post by YesImaLinuxWanabee on 2009-05-04
Im running Ubuntu 8.04 64 bit edition on an Asus G1Sn with a 512MB 9500m GS and Im having some troubles with the directions in post #11.

I can get to the step where I download the txt file and rename it to a diff file, but when i do this step:
> #**<!-- Download the 512 patch if your card has 512 RAM, or the 256 if your card has 256 RAM-->**
#**<!-- RENAME the file from .txt to .diff as show below, and if your card has 256 RAM don't forget to alter the command accordingly-->**
# Apply NVRM patch
sudo patch -p0 < NVRM_512M_fix.diffI get a prompt asking me for the file to patch.
Why am I getting this and what file am I supposed to patch?

---

### Post by mikedep333 on 2009-05-04
I don't know if this is relevant, but I have an Asus F8Sn-D1 with a Geforce 9500m GS.

It "just works" with 8.10, 9.04, and I think with 8.04 too.

---

### Post by Rinias on 2009-05-10
> **YesImaLinuxWanabee said:**
> Im running Ubuntu 8.04 64 bit edition on an Asus G1Sn with a 512MB 9500m GS and Im having some troubles with the directions in post #11.

I can get to the step where I download the txt file and rename it to a diff file, but when i do this step:
I get a prompt asking me for the file to patch.
Why am I getting this and what file am I supposed to patch?

What kernel version are you trying to patch, which patch did you download and are you following the directions exactly, ie without switching directories ?

The patch only works for the kernel specified in the patch, which can be determined by the first line in the .diff :

```
diff -Naur linux-2.6.27.orig/arch/x86/pci/i386.c linux-2.6.27/arch/x86/pci/i386.c
--- linux-2.6.27.orig/arch/x86/pci/i386.c	
```

If you're not patching 2.6.27, then you will need to go into the linux kernel directory and navigate to

```
arch/x86/pci/
```

[edit]**Note :** The linux kernel directory is going to be where you are working. Typically, if you haven't changed anything and simply opened a terminal, you will be working in your home directory (to find out where you are, use the command **pwd**(which stands for "**p**resent **w**orking **d**irectory") and it will tell you). The commands given will download the linux kernel into this directory, so open up a file manager and find the linux-2.6.27 folder (or linux-2.6.28 or whatever version it is) and then go into **arch/x86/pci/**. You will find what you need in there.[/edit]

and open the file **i386.c** in a text editor. The next thing you must do is find the section like this :

```
 				r = &dev->resource[idx];
 				if (!r->flags)
 					continue;
 				pr = pci_find_parent_resource(dev, r);
 				if (!r->start || !pr ||
 				    request_resource(pr, r) < 0) {
```

and insert

```
				if ((r->start == 0xbdf00000) && (r->end == 0xddefffff)) {
					r->start = 0xc0000000;
					r->end = 0xe0000000;
				}
```

after **continue;** so that it looks like :

```
 				r = &dev->resource[idx];
 				if (!r->flags)
 					continue;
				if ((r->start == 0xbdf00000) && (r->end == 0xddefffff)) {
					r->start = 0xc0000000;
					r->end = 0xe0000000;
				}
 				pr = pci_find_parent_resource(dev, r);
 				if (!r->start || !pr ||
 				    request_resource(pr, r) < 0) {
```

Save the file and continue with the instructions and all should turn out well.

Rinias

NB : If you do it this way, then you are skipping the 

```
sudo patch -p0 < NVRM_512M_fix.diff
```

step.

---

### Post by Malart on 2009-05-13
3. Lastly, run the deb packages you created above in this order:
You should then install the 4 debs :

if i understand this, after the 2 builds, i install those 4 packages in that order

what exactly do i type to do this
(i am pretty much an utter noob in the command line, sorry)


and once i am done, do i simply download/install the nvidia driver under system>administration>hardware drivers?

---

### Post by YesImaLinuxWanabee on 2009-05-14
LOL I figured out what I was doing wrong. I was running the diff file from the wrong location. All I needed to do was move the diff file to the directory I had built the kernel packages in.

Thanks for the help all. I now have Ubuntu 8.04 64 bit running on my laptop. Now I'm going to try to do this in Ubuntu 8.10 and maybe 9.04

---

### Post by Rinias on 2009-05-19
> **Malart said:**
> 3. Lastly, run the deb packages you created above in this order:
You should then install the 4 debs :

if i understand this, after the 2 builds, i install those 4 packages in that order

what exactly do i type to do this
(i am pretty much an utter noob in the command line, sorry)

You have two options, actually. The first is to click on the packages (or right-click and run with GDebi), the second is to continue using the command line.

From your working/build directory (that's the linux directory, the one with the kernel that you cd'ed into) :

```
cd ..
sudo dpkg -i linux-image*
sudo dpkg -i linux-headers*

```

You can also use the command **ls** to make sure there is only one linux-image and linux-headers package - otherwise the commands I just gave you will install all the linux-image and linux-headers packages in that directory, which could lead to problems...


> **Malart said:**
> 
and once i am done, do i simply download/install the nvidia driver under system>administration>hardware drivers?

That is exactly right. After which, you reboot and everything should work!

Rinias

---

### Post by YesImaLinuxWanabee on 2009-05-22
Has anyone had luck getting Ubuntu 9.04 working with the NVidia 9500m GS yet? I have installed it on my laptop and I have, by default, a 1680x1050 resolution, which is good. Way better that 800x600 or 640x480, but the NVidia drivers are not installed so there is no 3D accelleration. 

I think I am going to try installing the drivers, but I don't think they are going to work. I suppose i should ask, is there a way to ***uninstall*** the drivers if they don't work?

edit:
The drivers didn't work. I tried version 180 and 173 with no luck. I found out to uninstall the drivers its the same process as installing, just click "remove" instead of "activate".

---

### Post by wolfwood2x on 2009-05-24
Has anyone had any luck with the patch in 9.04 yet? Or does anyone know when the 30 kernel will drop?

---

### Post by wolfwood2x on 2009-05-24
> **VernieR said:**
> I have just applied this patch to 9.04 beta. Works like a charm. Since 9.04 uses a newer kernel version 2.6.28 I had to change this in the patch file.

Now lets hope it gets fixed soon :)
 

What did you have to change in the patch file?

---

### Post by YesImaLinuxWanabee on 2009-05-25
@ wolfwood2x
I do believe all you need to do is edit the diff file. Just change the kernel number to the correct one. i.e. :  
original = linux-2.6**.27**.orig/arch/x86/pci/i386.c  
new = linux-2.6**.28**.orig/arch/x86/pci/i386.c
But I have not tested it nor dug around to see if its right.

@ anyone
Is there any way to hide or keep updates from the automatic updates manager?

---

### Post by wolfwood2x on 2009-05-27
> **YesImaLinuxWanabee said:**
> @ wolfwood2x
I do believe all you need to do is edit the diff file. Just change the kernel number to the correct one. i.e. :  
original = linux-2.6**.27**.orig/arch/x86/pci/i386.c  
new = linux-2.6**.28**.orig/arch/x86/pci/i386.c
But I have not tested it nor dug around to see if its right.


That is what I ended up trying after posting my question here. It worked. I do appreciate the response anyway.

---

### Post by YesImaLinuxWanabee on 2009-05-27
@wolfwood2x

no problem. that is why i joined this forum, to get and give help. I just tryed editing the diff file like I had said and it was successful for me as well. I now have a 1680x1050 resolution, nvidia drivers 180.44 installed, and full 3D support! :o


@anyone

I'm going to attach the diff file i used to patch ubuntu 9.04 kernel version 2.6.28-11-generic if anyone wants it.:popcorn:

---

### Post by siddtharth on 2009-05-27
> **YesImaLinuxWanabee said:**
> @wolfwood2x

no problem. that is why i joined this forum, to get and give help. I just tryed editing the diff file like I had said and it was successful for me as well. I now have a 1680x1050 resolution, nvidia drivers 180.44 installed, and full 3D support! :o


@anyone

I'm going to attach the diff file i used to patch ubuntu 9.04 kernel version 2.6.28-11-generic if anyone wants it.:popcorn:

I have the same problem only difference is that my laptop has Nvidia 7600 GO card which has 128MB memory and I tried modify the diff file so that it creates a space of 128MB but it didn't work, can someone post a diff file for this card ?
Thanks!

---

### Post by zonxt on 2009-05-29
well... what can i say - oh, yes i know: thank you! i've been following this post for almost a month now, but until tonight i didn't have success in patching my kernel (i've tried 3-4 times, but i was getting different errors, which thankfully you lads have covered throughout your posts). i'm using ubuntu 9.04. next step: enable compiz and then sort out this nasty cpu whine. once again, thank you all.

---

### Post by skarcito on 2009-06-26
WELL DONE thank you so much man ... :popcorn:

---

### Post by 9a3eedi on 2009-06-27
This guide actually worked! Thanks! I was stuck with getting the graphics card to work.. I didn't want to run Ubuntu on 640x480! Now I got compisiting running. Thanks again!

I wonder if I could do the same thing with Gentoo Linux....

---

### Post by Rinias on 2009-06-29
> **9a3eedi said:**
> I wonder if I could do the same thing with Gentoo Linux....

You sure can!

You just need to patch the kernel and then build as normal, don't follow the Ubuntu kernel build line. That's what I did with Slackware, and it works fine (TwinView, etc.).

Hopefully, the changes to the kernel will be released soon, and this will be history!

Rinias

PS : Oh, and you obviously don't need fakeroot, etc. You just need your standard system (assuming you can build packages), you need to patch the kernel (either with a patch file or the way I described earlier in this thread), make and install and then do your nVidia build.

---

### Post by Rinias on 2009-08-10
Working through this process on Linux Mint, I found :

```
                               if (!r->flags)
                                        continue;
                                pr = pci_find_parent_resource(dev, r);
                                if (!r->start || !pr ||
                                    request_resource(pr, r) < 0) {
                                        dev_warn(&dev->dev, "BAR %d: can't allocate resource\n",$
                                        /*
                                         * Something is wrong with the region.
                                         * Invalidate the resource to prevent
                                         * child resource allocations in this
                                         * range.
                                         */
                                        r->flags = 0;
                                }
```

in the 2.6.28-11-generic kernel.

Don't know if it has anything to do with the problem, but 2.6.31 is in development now, so hopefully TJ will be able to get it in soon (if it isn't already - I've searched some changelogs with no luck...)

Here's to wishful thinking !

Rinias

---

### Post by genux05 on 2009-09-21
I am using a acer 9815 aspire laptop.. and shall also try out this patch to see if it works with my 4GB of ram upgrade.. 

since hopefully it will just create a new kernel option in grub then should do not harm :).

was wondering if anyone else had tried it that is not a 9500m gs card ? and got on k ?

I am using kubuntu 9.10 btw.. and really like it.

---

