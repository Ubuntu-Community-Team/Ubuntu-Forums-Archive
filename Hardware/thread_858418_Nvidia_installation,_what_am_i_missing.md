---
title: "Nvidia installation, what am i missing ?"
date: 2008-07-13
forum: Hardware
---

### Post by Tantalus90 on 2008-07-13
It feels like I am banging my head off a wall here.

Trying to install nvidia drivers on 

Dual Core Athlon 64 4600+
M2N Mobo with 2 GB RAM 
256 MB 8400 GS nVIDIA PCIe card and a Dell E172FPi Flatscreen monitor.

Mint Elyssa kernel 2.6.24.16 generic

(Which as far as I know is Ubuntu with extras)

And keep up ending here 

[IMG]http://img.photobucket.com/albums/v102/Tantalus/Stuff/DSCF0217.jpg[/IMG]

At this point I can not press ALT CTRL and F1 (or any of the other Fs) nor can I press CTRL ALT Backspace.

The mouse moves , the sound works but the only way to get past this is to press reboot. Nothing else will get me anywhere.

So far I have tried, enabling 3rd Party drivers - See screen above
Envy , all 3 driver versions, see screen above

All 3 solutions here 

[quote="Ron Overdrive"]Ok there's 3 ways you can do this.

1) type "sudo apt-get install nvidia-glx-new" and this will install nVidia 169.12 as version 173.14.05 is still extremely new and isn't in the Ubuntu repositories.

2) Install Envy-NG and use that to install the driver. Keep in mind Envy-NG does NOT yet support installing the latest nVidia driver (173.14.05).

3) This is more tedious, but will allow you to install the latest version till Envy-NG is updated:

In your terminal run "sudo apt-get --purge remove nvidia-glx nvidia-settings nvidia-glx-legacy" without the quotes. This will purge all existing drivers on your system. While in your terminal run "sudo apt-get install linux-headers-generic build-essential gcc xserver-xorg-dev pkg-config" again without the quotes. This will install all necessary packages for the nVidia installer.

Reboot your machine. When GRUB loads hit escape and choose the latest kernel you have with the Safe Mode option. If prompted what you want to choose Root. Now type "runlevel --set=3" without the quotes. Now run "pico /etc/default/linux-restricted-modules-common" and edit the following line to look like this: DISABLED_MODULES="nv nvidia-new". Now use the cd command to get to where you saved nVidia installer. Then type "sh NVIDIA-Linux-x86-173.14.05-pkg1.run" (assuming you're installing 173.14.05). Follow the prompts and let the installer configure your xconfig. Reboot using "shutdown -r now" and it should boot up.

Now keep in mind because we're installing it using the nVidia installer and not the repository's version, every time there is a kernel update you will need to reboot your machine into safe mode, set the runlevel to 3, and then re-run the nVidia installer to update for the new kernel. Hope this helps.[/quote]

See screen above.

And a few other attempts from the Ubuntu forum as well.

I have edited linux-restricted-modules , xorg.conf and a few others , with gedit vi and pico 

I have been at terminal prompts , runlevels and root prompts for the best part of a day and am finally at my wits end.

Now I know this card works because it was working up until last night in 1280 by 960 resolution.

Even running WoW under wine at close on 100fps. And then I borked it all  :oops: 

So please can someone put me out of my misery and tell me what I am missing here ?

And lastly , why oh why is it so blimming difficult to get an nVIDIA card working in Linux, nVIDIA even supply drivers - or maybe that is half the problem ?

Anyway thanks in advance 

Tant

---

### Post by Tantalus90 on 2008-07-22
You know this is really annoying, I post a question about an issue and it gets completely ignored.

Nvidia cards all working fine using envy or restricted drivers ? Nope didnt think so either.

In fact the boards are so full of people with nvidia problems , to be honest I am amazed nobody has written a simple, up to date, easy to find HowTo.

Some of the threads here deal with completely irrelevant operating systems and out of date drivers, other threads seem to skirt round without actually fixing the issue for 40 pages.

Please lets have some coherent effort from the Ubuntu team to get Nvidia drivers working off the bat. 

It shouldnt be this hard, if only there was some simple concise and up to date information available.

---

### Post by NikoC on 2008-07-22
Just a small remark before I actually reply: the problems you are facing are caused by the nvidia propietary drivers, and are not accessible for ubuntu developers... so you should definitely report this at the nvidia forum as well, since they are the only ones able to change the driver code (but often are reluctant or unwilling to do so)! If you chose the open source driver, i.e. nv, you should not have any problems at all...

Did you already try to install the latest drivers from nvidia.com?

---

### Post by Daelyn on 2008-07-22
> **Tantalus90 said:**
> You know this is really annoying, I post a question about an issue and it gets completely ignored.

Nvidia cards all working fine using envy or restricted drivers ? Nope didnt think so either.

In fact the boards are so full of people with nvidia problems , to be honest I am amazed nobody has written a simple, up to date, easy to find HowTo.

Some of the threads here deal with completely irrelevant operating systems and out of date drivers, other threads seem to skirt round without actually fixing the issue for 40 pages.

Please lets have some coherent effort from the Ubuntu team to get Nvidia drivers working off the bat. 

It shouldnt be this hard, if only there was some simple concise and up to date information available.

> You know this is really annoying, I post a question about an issue and it gets completely ignored.

First of all, this is a community and voluntary work. Don't "complain" just because someone don't instantly answer and devote all their time just for YOU. People put in their spare time for this. That you don't get a answer might just be that noone has this "simple" solution you ask about. This is a "free" thing. Don't expect full support. 


This is a quite spot on HOW-TO, as far as I can see. It is exactly what I would write. And for 9/10 it would work fine too.
> Originally Posted by Ron Overdrive 
Ok there's 3 ways you can do this.

1) type "sudo apt-get install nvidia-glx-new" and this will install nVidia 169.12 as version 173.14.05 is still extremely new and isn't in the Ubuntu repositories.

2) Install Envy-NG and use that to install the driver. Keep in mind Envy-NG does NOT yet support installing the latest nVidia driver (173.14.05).

3) This is more tedious, but will allow you to install the latest version till Envy-NG is updated:

In your terminal run "sudo apt-get --purge remove nvidia-glx nvidia-settings nvidia-glx-legacy" without the quotes. This will purge all existing drivers on your system. While in your terminal run "sudo apt-get install linux-headers-generic build-essential gcc xserver-xorg-dev pkg-config" again without the quotes. This will install all necessary packages for the nVidia installer.

Reboot your machine. When GRUB loads hit escape and choose the latest kernel you have with the Safe Mode option. If prompted what you want to choose Root. Now type "runlevel --set=3" without the quotes. Now run "pico /etc/default/linux-restricted-modules-common" and edit the following line to look like this: DISABLED_MODULES="nv nvidia-new". Now use the cd command to get to where you saved nVidia installer. Then type "sh NVIDIA-Linux-x86-173.14.05-pkg1.run" (assuming you're installing 173.14.05). Follow the prompts and let the installer configure your xconfig. Reboot using "shutdown -r now" and it should boot up.

Now keep in mind because we're installing it using the nVidia installer and not the repository's version, every time there is a kernel update you will need to reboot your machine into safe mode, set the runlevel to 3, and then re-run the nVidia installer to update for the new kernel. Hope this helps.


The boards might be full with peope with "nvidia" problems, but, from my own experience, it mostly ain't about the drivers or cards. There are millions of different hardware configurations and system installations bloated with "failed" attempts which can cause havoc during the installs. Also, because these binaries from nVidia are closed source, we can't investigate any in depth solutions or any other major stuff. That will have to come from nVidia. You can request help in their forum.


I would say, your problem is related to this. A few failed driver installations and you have drivers here and there, links cross over, GL libraries end up on fifty eleven places etc, etc. The easiest solution would be for you to begin from scratch, if noone comes up with a foolproof plan to erase every failed attempt and reset to standard, which is doubtful.


I, myself, have never had a single issue with the nvidia drivers. I've used the binaries from nvidia.com but, because I'm not using any graphic intensive stuff, I've the past few months just used the nvidia restricted driver. It has NEVER, ever, been a issue just to switch it on and get it working, neither has the binary caused me any headache.


As a other thing, I have two graphic cards in my laptop and have a start-up script which redirects to the correct drivers once it checks out which graphic card is used. No problems what so ever yet, and I was, and still am, a little noob since 9 months back. Reinstalled many times due to my harddrive beeing a bit dodgy, but, never had any problems with the graphics.


Last, but not least, don't take this as a rude answer just to fob you off. it's not. but, your system must be borked and the "simple" solution for you in this case is not by terminal commands, but by the means of a installation cd. Or, by talking to nVidia in their forums.

---

### Post by Tantalus90 on 2008-07-23
Thanks for replies, for the record .... I finally got it working 

Please note I tried the method described by Ron Overdrive to no avail and said so in my first post ........

No offense taken at the tone of the replies, and I do realise the contributors are all volunteers, and am grateful for the efforts they make.

The solution however was blindingly simple, supplied by starcannon in another post somewhere in the minefield of this forum.

> Re: Hardy refusing to keep nvidia drivers or monitor settings
I only had to add nvidia to my /etc/modules list, and I blacklisted nv in the /etc/default/linux-restricted-modules-common file.

so my /etc/modules file looks like this:

Code: Select all
    # /etc/modules: kernel modules to load at boot time.
    #
    # This file contains the names of kernel modules that should be loaded
    # at boot time, one per line. Lines beginning with "#" are ignored.

    fuse
    lp
    sbp2
    nvidia


and my /etc/default/linux-restricted-modules-common file looks like this:

Code: Select all

    # This file is sourced from the linux-restricted-modules-common init
    # script and is used to disable the link-on-boot feature, one module
    # at a time.  This can be useful if you want to use hand-compiled
    # versions of one or more modules, but keep linux-restricted-modules
    # installed on your system, or just to disable modules you don't use
    # and speed up your boot process by a second or two.
    #
    # Use a space-separated list of modules you wish to not have linked
    # on boot.  The following example shows a (condensed) list of all
    # modules shipped in the linux-restricted-modules packages:
    #
    # DISABLED_MODULES="ath_hal fc fglrx ltm nv"
    #

---

