---
title: "Intel 5100 Wifi is not working after upgrade to Karmic Koala"
date: 2009-11-24
forum: Hardware
---

### Post by Cheater512 on 2009-11-24
After upgrading a laptop to Karmic Koala, the previously working wireless is now dead.

Card: Intel Wifi Link 5100
Driver: iwlagn
Kernel: 2.6.31-15-generic

Dmesg errors:
iwlagn 0000:08:00.0: MAC is in deep sleep!. CSR_GP_CNTRL = 0x4020014C
iwlagn 0000:08:00.0: MAC is in deep sleep!. CSR_GP_CNTRL = 0x4020014C
(etc... approx 50 lines a second for 60 seconds)
iwlagn 0000:08:00.0: Failed to init APMG
iwlagn 0000:08:00.0: PCI INT A disabled
iwlagn: probe of 0000:08:00.0 failed with error -110

It will not show up with iwconfig -a and the rf kill switch has no effect.

It worked out of the box with Intrepid Ibex, with no problems.
Also if I choose the 2.6.28-15-generic kernel in grub, the wifi works fine (although X chews 100% cpu and the touch pad doesnt work with that kernel).

Googling has found several reports of the same error, but not in a similar situation and I havent found any solution.

Does anyone have a solution or any additional debug steps I can take?
Thanks

---

### Post by cutterjohn on 2009-11-25
Not that this will help you, but hey! It's a reply.

Anyways, I've got the Intel 5100 WiFi link express card as well, however mine IS working. (MSI GT725, 9.10 x86-64)

That said, it is NOT working nearly as well as it did under 9.04 (x86-64).  The driver frequently crashes, and leaves a ton of spammed messages in /var/log/messages.  I get frequent disconnects/reconnects under anything more than a light load, etc.

I think that there may be a bug entry in launchpad already, which you might want to search for, although I don't understand why your 5100 isn't working at all while mine makes a feeble attempt at it.

Oh and to add to this pulseaudio is leaking like a sieve, was up to 2.4GB RESIDENT one day when I checked, and 2.1GB this morning(finally had to reboot as all DRAM AND VM was being sucked down which made the machine incredibly sluggish).

iwlagn was chewing up 100% CPU.

And to top it all off, I get to have the wonderful experience of using those awful AMD catalyst driver...

Anyways, I think that 9.10 was half-baked and not really ready for release the more that I use it now.  It's no where near as stable at 9.04 was, and even that wasn't one of their best releases...

---

### Post by coffeecat on 2009-11-25
This is not going to help much, but just to prove the ymmv principle, I have the Intel 5100 wireless chipset in the Sony laptop I'm posting from now, running Karmic. Wireless has been as steady as a rock with the 2.6.31-14 kernel and ditto for the short time I've been using the 2.6.31-15 kernel. Also, it's no better and no worse than with Jaunty - i.e. excellent in both. The Karmic I'm posting from was a fresh install, not an upgrade, but I did try dist-upgrading Jaunty and again wireless was just fine.

But perhaps your dist-upgrade did go wrong. Why not boot up with the Karmic live CD and try connecting while in the live session? If it works fine it won't help you trouble-shoot your present problems but you might be tempted to backup your data and do a fresh install. It might be quicker in the long run.

> **cutterjohn said:**
> Anyways, I think that 9.10 was half-baked and not really ready for release the more that I use it now. It's no where near as stable at 9.04 was, and even that wasn't one of their best releases...

Well - again ymmv. I've installed Karmic on 2 desktops, 2 laptops, 1 netbook and 1 VirtualBox machine in a MacOS host. They all run just fine and the worst issue I've had is with flaky wireless in one laptop with an Atheros chipset - definitively solved by the simple expedient of installing the backported wireless kernel modules.

I'm truly sorry to hear of your bad experiences on one particular set of hardware but to call Karmic "half-baked" on the basis of that is to generalise from the particular. Oh - and Jaunty was for me the best release until Karmic came along. I wonder if your problems aren't more down to MSI rather than Jaunty/Karmic.

---

### Post by Kobin on 2009-11-30
I have Intel 5100 working here by adding acpi=off as a boot option.
It is not a good solution for laptops, but I hope a fix will be provided soon.

I like using Ubuntu because of easy access to software, and easy configuration of devices. But I agree that karmic is really not the best release yet. On one laptop I have had problems with wireless (this intel 5100 that worked in 9.04) and nvidia gt240m showing 6 small screens (Solved by generating xorg.conf with nvidia-xconfig and then applying the fix described in the Archlinux wiki [http://wiki.archlinux.org/index.php/Nvidia#Corrupted_screen:_.22Six_screens.22_issue]("http://wiki.archlinux.org/index.php/Nvidia#Corrupted_screen:_.22Six_screens.22_issue")

After upgrading another laptop: No webcam! And that was also working under 9.04.

Ubuntu has before been the obvious choice for installing on family and friends computers, and I hope it will again.
The best solution would be if I could always choose LTS in these situations, but then you have problems of old Openoffice which means problems with opening documents created in Office 2007, and an old firefox with to many bugs.
Right now you really need to be good at hiding the problems of Ubuntu, to convince people that it is a good system. So my suggestion would be to have a better LTS concept where at least the packages you need to exchange documents and files with other people is updated or drop the 6 month release cycle for maybe a one year and then do it right.

My intension is not to push Ubuntu down but rather I wish for a better future for Ubuntu.

EDIT: I have found another solution which gives powermanagement back. Instead of adding acpi=off in /boot/grub/grub.cfg add pci=use_crs
It works on Acer Aspire 5739G, but unfortunately I do not yet know what this boot option really does. If anyone could explain I would be very grateful. I have yet to discover anything not working on this laptop now, so for now I will keep this option.

---

### Post by ram130 on 2009-12-02
> **Kobin said:**
> I have Intel 5100 working here by adding acpi=off as a boot option.
It is not a good solution for laptops, but I hope a fix will be provided soon.

I like using Ubuntu because of easy access to software, and easy configuration of devices. But I agree that karmic is really not the best release yet. On one laptop I have had problems with wireless (this intel 5100 that worked in 9.04) and nvidia gt240m showing 6 small screens (Solved by generating xorg.conf with nvidia-xconfig and then applying the fix described in the Archlinux wiki [http://wiki.archlinux.org/index.php/Nvidia#Corrupted_screen:_.22Six_screens.22_issue]("http://wiki.archlinux.org/index.php/Nvidia#Corrupted_screen:_.22Six_screens.22_issue")

After upgrading another laptop: No webcam! And that was also working under 9.04.

Ubuntu has before been the obvious choice for installing on family and friends computers, and I hope it will again.
The best solution would be if I could always choose LTS in these situations, but then you have problems of old Openoffice which means problems with opening documents created in Office 2007, and an old firefox with to many bugs.
Right now you really need to be good at hiding the problems of Ubuntu, to convince people that it is a good system. So my suggestion would be to have a better LTS concept where at least the packages you need to exchange documents and files with other people is updated or drop the 6 month release cycle for maybe a one year and then do it right.

My intension is not to push Ubuntu down but rather I wish for a better future for Ubuntu.

EDIT: I have found another solution which gives powermanagement back. Instead of adding acpi=off in /boot/grub/grub.cfg add pci=use_crs
It works on Acer Aspire 5739G, but unfortunately I do not yet know what this boot option really does. If anyone could explain I would be very grateful. I have yet to discover anything not working on this laptop now, so for now I will keep this option.

Well said and I totally agree. I just got the same laptop 2 days ago and will try your solution also. But I'm curious about one thing, are you having any WIFI signal problems?

---

### Post by Kobin on 2009-12-03
No Wifi works with no problems after adding the option pci=use_crs.

I did not test wired connection though.

If you find a solution for the blurry screen when shutting down or killing X after installing nvidia drivers, please let me know. It is just a detail, but it looks bad.

---

### Post by ram130 on 2009-12-04
I have  a problem with my Wifi in Windows 7, im only 10m away from the router and it disconnects. It shows 3 to 4 bars but won't connect unless im near the router. Hmm, i guess i am a alone on this one, sending it back for repair. I hope they fix this wifi problem in Ubuntu soon. You should post it as a bug though.

---

### Post by seccanj on 2009-12-05
> **Kobin said:**
> 
It works on Acer Aspire 5739G, but unfortunately I do not yet know what this boot option really does. If anyone could explain I would be very grateful. I have yet to discover anything not working on this laptop now, so for now I will keep this option.

Hi Kobin,
I have just bought your same Aspire 5739G and installed Karmic in dual boot, but it is a nightmare... I can't figure out how to make the LAN work (I'm writing from another machine) nor the Intel 5100 - though I'll try your suggesitons rightaway. 
I couldn't make the NVidia drivers work (I'm going to try our your suggestions here as well), same 9 small screens and scarily flickering.

Any hint on how you made the LAN work (Atheros AR8132) ? I have found the driver that is referred to in many posts ([http://partner.atheros.com/Drivers.aspx](http://partner.atheros.com/Drivers.aspx) which btw is not working, but I found the same binaries elsewhere with google), patched and built it, but it keeps not working.
I have just upgraded to the latest kernel... yet nothing.
This particular issue is really preventing me from using the Ubuntu system.
Any other hint you may have on how you made the rest of the hw working would be really appreciated.
Thanks!
Roberto

---

### Post by seccanj on 2009-12-05
Wow, adding the  pci=use_crs option to GRUB did the trick!
Not only it fixed the Wi-fi, but most importantly it fixed the ethernet!

Following a suggestion I actually added the pci=use_crs option to the GRUB_CMDLINE_LINUX_DEFAULT variable in /etc/default/grub and then ran update-grub so that future kernel updates will keep the change.

Now down to the NVidia fix you suggested...

Thanks!

---

### Post by seccanj on 2009-12-05
And yes! NVidia issue fixed too.
I installed the latest (190) driver from NVidia, which eventually made me go through nvidia-xconfig.
I then applied the option you recommend into /etc/X11/xorg.conf
Thanks again!

---

### Post by ram130 on 2009-12-05
> **seccanj said:**
> And yes! NVidia issue fixed too.
I installed the latest (190) driver from NVidia, which eventually made me go through nvidia-xconfig.
I then applied the option you recommend into /etc/X11/xorg.conf
Thanks again!

Hey can you sumarize everything you did. To fix: the Ethernet, wifi, and nvidia drivers. ;)

---

### Post by seccanj on 2009-12-05
> **ram130 said:**
> Hey can you sumarize everything you did. To fix: the Ethernet, wifi, and nvidia drivers. 

Sure. This procedure worked fine on my Acer Aspire 5739G.
I'm running Ubuntu 9.10 Karmic 64 bit, updated to the latest 2.6.31-16 kernel.
(To update your system without yet network connectivity, follow [this guide]("http://my.opera.com/ubuntunerd1/blog/how-to-create-an-ubuntu-update-cd-dvd"). No need to burn a CD, just use an USB stick.)

To fix WiFi and LAN. I have an Atheros AR8131 Ethernet card and an Intel 5100 WiFi.
From a terminal:

1) sudo gedit /etc/default/grub
2) Replace the line:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
with
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pci=use_crs"
then save and close.
3) sudo update-grub
4) Reboot your system

To fix the NVidia 6 small screens and bad resolution problems. I have an NVidia GEFORCE GT 240M.

1) Make sure you are not using the NVidia driver. Go to System/Administration/Hardware Drivers  and make sure the "NVidia accelerated graphics driver" is disables (grey bullet). If not, disable it and restart your system.
2) Go to the NVidia support site and download the latest driver:
[http://www.nvidia.it/Download/index.aspx](http://www.nvidia.it/Download/index.aspx)
You will be downloading a file ending with a ".run" extension
3) Open a terminal, cd into the directory where you downloaded the driver and give it execution persmission.
For example:
cd Downloads
chmod +x NVIDIA-Linux-x86_64-190.42-pkg2.run
4) Now you need to shut down the ghraphical environment before installing the drivers.
Press Ctrl+Alt+F1 to go to a terminal-only session, then shut down the X server with:
sudo /etc/init.d/gdm stop
5) Do a backup of your graphical environment settings file:
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.GOOD 
6) Now you can install the driver by running the program you downloaded:
sudo ./NVIDIA-Linux-x86_64-190.42-pkg2.run
7) Accept the license and go through the wizard. Also agree to the OpenGL stuff
8) At the end of the wizard you'll be asked if you want to run the nvidia-xconfig program. Agree to it.
This will create a xorg.conf file customized for your environment.
9) Before restarting the system, fix the problem with the 6 screens by editing the xorg.conf file and setting this special "Option":
sudo vi /etc/X11/xorg.conf

and add this option anywhere into the section labeled "Device", for example: 

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    Option         "ModeValidation" "NoTotalSizeCheck"
EndSection

10) Save and close
11) Reboot your system:
sudo shutdown -r now


Hope this helps!
Ciao,
Roberto

================================
I used to be schizophrenic, but we're OK now.

---

### Post by ram130 on 2009-12-05
> **seccanj said:**
> Sure. This procedure worked fine on my Acer Aspire 5739G.

To fix WiFi and LAN. I have an Atheros AR8131 Ethernet card and an Intel 5100 WiFi.
From a terminal:

1) sudo gedit /etc/default/grub
2) Replace the line:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
with
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pci=use_crs"
then save and close.
3) sudo cd Downloadsupdate-grub
4) Reboot your system

To fix the NVidia 6 small screens and bad resolution problems. I have an NVidia GEFORCE GT 240M.

1) Make sure you are not using the NVidia driver. Go to System/Administration/Hardware Drivers  and make sure the "NVidia accelerated graphics driver" is disables (grey bullet). If not, disable it and restart your system.
2) Go to the NVidia support site and download the latest driver:
[http://www.nvidia.it/Download/index.aspx](http://www.nvidia.it/Download/index.aspx)
You will be downloading a file ending with a ".run" extension
3) Open a terminal, cd into the directory where you downloaded the driver and give it execution persmission.
For example:
cd Downloads
chmod +x NVIDIA-Linux-x86_64-190.42-pkg2.run
4) Now you need to shut down the ghraphical environment before installing the drivers.
Press Ctrl+Alt+F1 to go to a terminal-only session, then shut down the X server with:
sudo /etc/init.d/gdm stop
5) Do a backup of your graphical environment settings file:
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.GOOD 
6) Now you can install the driver by running the program you downloaded:
sudo ./NVIDIA-Linux-x86_64-190.42-pkg2.run
7) Accept the license and go through the wizard. Also agree to the OpenGL stuff
8) At the end of the wizard you'll be asked if you want to run the nvidia-xconfig program. Agree to it.
This will create a xorg.conf file customized for your environment.
9) Before restarting the system, fix the problem with the 6 screens by editing the xorg.conf file and setting this special "Option":
sudo vi /etc/X11/xorg.conf

and add this option anywhere into the section labeled "Device", for example: 

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    Option         "ModeValidation" "NoTotalSizeCheck"
EndSection

10) Save and close
11) Reboot your system:
sudo shutdown -r now


Hope this helps!
Ciao,
Roberto

================================
I used to be schizophrenic, but we're OK now.

thank you so much! .. I am gonna try this when my laptop comes back from repair.. hmm 2 weeks time..I'm sure those who are buying it will easily find this thread and note your steps. One more question though, if I install ubuntu will it mess up the recovery partition it has in anyway that will prevent me from doing a complete restart windows just in case?

---

### Post by coffeecat on 2009-12-05
**seccanj**, you might want to edit this line:

> **seccanj said:**
> 3) sudo cd Downloadsupdate-grub

I presume you mean 'sudo update-grub', but I can see what happened. I've often done something similar myself. :)

---

### Post by seccanj on 2009-12-06
Right :-) fixed thanks

---

### Post by seccanj on 2009-12-06
> **ram130 said:**
> I am gonna try this when my laptop comes back from repair.. hmm 2 weeks time..

:-) I know what it means to be waiting for your brand new hw stuff to come :-)

> **ram130 said:**
> One more question though, if I install ubuntu will it mess up the recovery partition it has in anyway that will prevent me from doing a complete restart windows just in case?

No it won't. 
This is what I did. I decided to keep the Windows 7 system (I paid for that after all right? :-) ) so during the Ubuntu installation I reduced the windows partition to 250 GB (that storage can be used from inside Ubuntu too anyway) and created a new partition into the unused storage. 
The recovery system is not touched by this operation.
Then you have to make sure you select the option "Use then larger unused partition" when asked about where to install Ubuntu.
Ciao!

---

### Post by hoofdbaas on 2009-12-07
I tried the suggested GRUB change but alas no success on an Acer 7730 G. Both the lan and wan don´t connect

Pieter

---

### Post by ram130 on 2009-12-08
> **seccanj said:**
> :-) I know what it means to be waiting for your brand new hw stuff to come :-)



No it won't. 
This is what I did. I decided to keep the Windows 7 system (I paid for that after all right? :-) ) so during the Ubuntu installation I reduced the windows partition to 250 GB (that storage can be used from inside Ubuntu too anyway) and created a new partition into the unused storage. 
The recovery system is not touched by this operation.
Then you have to make sure you select the option "Use then larger unused partition" when asked about where to install Ubuntu.
Ciao!

you kno my pain!! i feel like asking for my money back cause of the run around they gave me..i mean had to go through their 'steps' no matter how i said its not software related..

That last step you mention got me  a lil confused, i checked the cd and the only option i see matching what you said was "install side by side" option which also keeps it and lets you pick the size..on a partition drive with Windows.

---

### Post by linux4africa on 2009-12-09
Add acpi=off to your grub param list.

On startup in the grub menu, e (to edit), 4 lines down, Ctrl-e and add acpi=off, Ctrl-x to boot with that option.

---

### Post by seccanj on 2009-12-12
> **hoofdbaas said:**
> I tried the suggested GRUB change but alas no success on an Acer 7730 G. Both the lan and wan don´t connect

Pieter

You may want to first try with an Ubuntu live CD and, in the first screen before starting the system (where it says "try Ubuntu without changing your system"), press F6 for extra options and check the "acpi=off" option, as suggested earlier in this thread. Then start.

I found this working before trying out the other solutions.

Let us know :-)
Roberto

======================================
I used to be schizophrenic, but we're OK now.

---

### Post by seccanj on 2009-12-12
> **ram130 said:**
> That last step you mention got me  a lil confused, i checked the cd and the only option i see matching what you said was "install side by side" option which also keeps it and lets you pick the size..on a partition drive with Windows.

You're right, this is the option if you didn't already partition the drive before starting the installation, and so the installer makes it for you.
In my case I did it before, so I had that other option available.

Ciao,
Roberto

---

### Post by linux4africa on 2009-12-12
Upgrade to 2.6.31-17 - it works again with this version.

---

### Post by Slotkenov on 2009-12-21
I also have an Atheros AR8131 and tried you steps.

Only I changed this line:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
with
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i915.modeset=0 pci=use_crs"

I need the i915.modeset=0 so I will have visual instead of a black screen. But unfortunately my network still doesn't work.

When I do:
ping 192.168.0.1
I get:
connect: Network is unreachable

Am I missing something or doing something wrong?

Thanks for any help!

---

### Post by Aironjack on 2010-01-20
There is a bug report for Intel cards not working in karmic. If any of you are still having problems like me, please submit it here, so it gets fixed faster.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/496640]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/496640")

Thanks

---

