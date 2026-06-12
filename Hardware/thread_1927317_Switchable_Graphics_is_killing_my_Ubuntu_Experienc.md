---
title: "Switchable Graphics is killing my Ubuntu Experience,  PLEASE HELP"
date: 2012-02-17
forum: Hardware
---

### Post by markackerman8@gmail.com on 2012-02-17
Please help,
&#8728; For 2 months and over 100 hours, I have been trying to get my new HP Envy 2195ca laptop fully working in Ubuntu with the Swichable discrete AMD/ATI HD 6850m graphics card and not the embedded Intel hd3000 low end card,  with no success.  I think perhaps I am missing something basic and don't know what it is???  I am posting a new thread as my questions in previous threads are not getting any attention - so thanks in advance.   Here is what I have tried (part thereof) :

&#8227; Installed using additional drivers - seemingly successfully - ie. says enabled, and active and green dot, but
• running ATI's CCC gives:
&#8728; There was a problem initializing Catalyst Control Center Linux edition.  It could be caused by the following.
&#8728; No AMD graphics driver is installed, or the AMD driver is not functioning properly.
&#8728; Please install the AMD driver appropriate for you AMD hardware, or configure using aticonfig.

&#8227; Installed from the amd website:    amd-driver-installer-12-1-x86.x86_64.run, (previous version over the past 2 months as well)
• created the 3 debian packages seemingly successfully and installed all three:
&#8728; fglrx_8.930-0ubuntu1_amd64.deb,    plus 2 similarly named ones
• For the first time using 12.1 today I seemingly successfully ran:
&#8728; aticonfig --initial -f, with no errors  BUTTTTTT
&#8227; after a reboot just a black screen with a few tiny white dots flicking around
• and safe mode works fine
• I can get back into Ubuntu Normal mode by deleting 
&#8728; /etc/X11/xorg.conf (perhaps I just need the right file contents for switchable graphics)
&#8227; Again PLEASE HELP. and Thanks in advance

&#8227; Here is some additional information 
• lspci -nn | grep VGA
&#8728; 00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0116] (rev 09)
&#8728; 01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Broadway [ATI Mobility Radeon HD 6800 Series] [1002:68a8]
• Recommended configuration for X.org
&#8728; No configuration is necessary for ATI driver in the modern versions of Ubuntu. You can safely take away your xorg.conf and your computer will run fine. 
•     To see if your driver uses KMS (Kernel Mode Setting), run command 
&#8728; ack@Arawn:~$ dmesg | grep drm
[    9.153946] [drm] Initialized drm 1.1.0 20060810
[    9.400960] [drm] MTRR allocation failed.  Graphics performance may suffer.
[    9.402250] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    9.402255] [drm] Driver supports precise vblank timestamp query.
[   13.040646] fbcon: inteldrmfb (fb0) is primary device
[   13.040932] fb0: inteldrmfb frame buffer device
[   13.040935] drm: registered panic notifier
[   13.049332] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0


• vgaswitcheroo 
&#8728; Never has worked and probably because there is NEVER a file called
&#8227; /sys/kernel/debug/vgaswitcheroo/switch
&#8227; root@Arawn:/home/ack# echo DIGD > /sys/kernel/debug/vgaswitcheroo/switch
• bash: /sys/kernel/debug/vgaswitcheroo/switch: No such file or directory
&#8728; root@Arawn:/home/ack# grep -i switcheroo /boot/config-3.0.*
&#8227; /boot/config-3.0.0-16-generic:CONFIG_VGA_SWITCHEROO=y
&#8728; To test if vga_switcheroo is enabled, look for the switch file: 
&#8227; ls -l /sys/kernel/debug/vgaswitcheroo/switch
• ls: cannot access /sys/kernel/debug/vgaswitcheroo/switch: No such file or directory
&#8728; never once had this switch file with or without open source/fglrx/ or no driver at all
&#8227; If you are not using the open-source radeon driver (or the nouveau driver in case of nvidia hardware), there won't be a /sys/kernel/debug/vgaswitcheroo/switch file. (ignoring hacks like asus-switcheroo and byo-switcheroo). Disabling KMS ("modeset=0") turns off this functionality too.
• hmmmmmm
&#8227; Soooo
• The last thing in my many attempts was to reinstall ubuntu to install the amd/ati driver thru additionhal drivers (post release) as I read that this was the only one to work with vgaswitcheroo.  Oddly after the reinstall of Ubuntu and no updates I saw the switch file (/sys/kernel/debug/vgaswitcheroo/switch) for my first time  (Ubuntu 3.0.0-12) (no additional driver yet).  Then I tried to install the ati driver no luck  - errors so I thought I should update Ubuntu - restart and try again.  After the restart my kernel was at 3.0.0-16 from 12, and no /sys/kernel/debug/vgaswitcheroo folder at all

I will quickly respond to any troubleshooting tips  - THANKS
Mark

---

### Post by ahallubuntu on 2012-02-17
Are there any options in your BIOS Setup regarding the video card switching?  I've not used a laptop with this option.  Perhaps you can choose always one or the other rather than allow the OS to switch it?  In that case, you could maybe try messing with that just to see if it works.

If you still have a working version of Windows installed on this thing, you might also double check there isn't a newer BIOS available from HP for this computer.  If so, I'd install it - there's some remote chance it could help the Linux driver work correctly.

---

### Post by markackerman8@gmail.com on 2012-02-17
Wow An Awesomely fast response, and a smart one, however I have exausted the BIOS options by even having an HP Advanced Case Manager trying to get the techies to build options for switchable graphics into the bios ... but still no luck, as I just checked the website again,  arghhhh, though thanks

let the troubleshooting begin LOL
Thanks Mark:p

---

### Post by restorator on 2012-02-17
As far as I know there is no driver that actually works well with switchable graphics yet. I also have a laptop with it. So far all I was able to accomplish was to get the low end Intel graphics to be the only card working. That is not what most of us want. It appears that you just cannot make the high end chipset work alone in any way. Its either the low end by itself or the low then high card kicks in which of course doesnt work for us on Ubuntu. 
I do think I read something recently about a linux driver being released very soon that hopefully will solve this, but for now I gave up as it simply wasn't worth spending a hundred hours on it. If I put in an extra hundred hours at work instead I could just buy a better laptop as it would be cheaper and easier!
I do hope they come up with a Linux driver soon as more and more laptops are coming out with this switchable graphics setup to save power and battery life.

---

### Post by markackerman8@gmail.com on 2012-02-17
Well Thanks anyway for the response, I guess my optimism has to run out.  Wow there must be thousands or millions of new computers with the intel switchable graphics.  As far as I know ALL new laptops with an intel processor and a discret higher end card for the past year has this setup.  

That must beat least 70% of all new higher end laptops 
    - hundreds of millions - 
and linux can't find a simple script to  choose 0,1, or 2 for three options (Card One, the other, or both) WOWWWWW

Well thanks again, If anyone has any better news please append this thread,

Cheers, Mark

---

### Post by tomsn2 on 2012-02-17
If in Ubuntu I would run System Profiler, or Everest in Windows and find out exactly what system board you have and such.  You may be able to download a bios from the board mfg that hp wouldn't have that would allow you to disable the on board video.

---

### Post by restorator on 2012-02-18
> **tomsn2 said:**
> If in Ubuntu I would run System Profiler, or Everest in Windows and find out exactly what system board you have and such.  You may be able to download a bios from the board mfg that hp wouldn't have that would allow you to disable the on board video.

This is a relatively new thing, although many new laptops have this "feature", and probably soon for low/mid range desktops too. It IS *onboard* video on laptop motherboards. BOTH chipsets are built into the motherboard. A fairly decent high end one might I add, if you can only get it to work right. 

It is designed to save power by only utilizing the higher end and more power hungry graphics when really needed, like for gaming or photoshop or similar. Most of the time the unit only uses the low end chip. The software itself, which is loaded only *AFTER the O/S starts up*, determines when to switch. In Windows the drivers that work, allow you to set certain programs to use the high end card upon launching them, but not until the program starts up. Even with this software on Windows, some programs (mostly older ones) still only see the currently loaded chip, the low end one. Through a bios update and changing a setting you can now disable the "switchable" instructions, which means that it only runs on the low end chip but not the better one. 
 
In any case it ALWAYS starts on the low end chip, so no matter what you do your programs detect it as a low end Intel graphics setup. Most of us would be happy to be able to disable the low end set totally, but apparently, that's not the way its wired into it. So basically until someone writes a decent driver that works well in Linux (and a better one for Windows) we that have this are out of luck. There is the Ubuntu switcheroo workaround but as the OP noted it did not work for him and I personally had no luck with it also.

---

### Post by markackerman8@gmail.com on 2012-02-19
well thanks for your effortd anyways guys 

Cheers, Mark

p.s. it is an HP motherboard, so no luck with that - good thought  though

p.s.s, I will note a friend got his amd/ati 6000m series card to work using the 12.1 version of CCC, and here is what he used (i hope it helps someone)

Hi Mark,

You wouldn't believe it, but I am actually typing this email on my dv6, sporting the Radeon Graphics Card! AMD released Catalyst 12.1 and that apparently brought switchable graphics support for the HD 6xxxM Series, at least I can confirm that it is running just fine. Here is what I did:

Download the driver from AMD's website: [http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx)

Read somewhere to make sure I had the prerequisite packages, which would be these: sudo apt-get install linux-headers-generic dkms

Because I'm running 64bit, linked the libraries: sudo ln -svT lib /usr/lib64

and then ran the .run I downloaded from the website and said I wanted to install the driver and that was it! I can access CCC and switch graphics as well (requires reboot).

Best regards,
Dominic

---

### Post by onefthemany on 2012-03-20
I had the same issue on my HP Envy 14; here is what i done:


edit the /etc/fstab and add the following lines:

tmpfs /dev/shm tmpfs defaults 0 0

none /sys/kernel/debug debugfs defaults 0 0


then edit the /etc/rc.local and add before exit0:

chown $User /sys/kernel/debug/vgaswitcheroo/switch

echo OFF> /sys/kernel/debug/vgaswitcheroo/switch

once you have done that use the attached script & drop it into your /usr/bin folder, and then drop the attached icons into home/$User/.local/share/icons folder

Note: you may want to change the $User in the /home/%User/.local/share/icons element to be the user on your machine. make sure the attached file is executable or it wont work; so either chmod or change permissions by right click.

prior to running the script ensure you have installed gxmessage

to run the script/app, open a terminal and get into root (sudo su)

then simply run the following command:

switch_between_cards

the switch 1-4 picture attached shows the process and you can see my radeon card is going from off to on to off again

references:

[https://help.ubuntu.com/community/HybridGraphics](https://help.ubuntu.com/community/HybridGraphics)

i have changed the following in my script:

gnome-session-save --logout to gnome-session-quit

removed open box opens as they were conflicting

good luck

hope this helps

---

### Post by vedovatti on 2012-05-20
Hey, I was looking for updated script to switch between cards. Thanks. It works. Just the logout doesn´t work. I have to run it manually. Any idea how to improve it? I am using ubuntu 12.04. Thanks

---

### Post by onefthemany on 2012-05-21
> **vedovatti said:**
> Hey, I was looking for updated script to switch between cards. Thanks. It works. Just the logout doesn´t work. I have to run it manually. Any idea how to improve it? I am using ubuntu 12.04. Thanks

is this intended for me?

---

### Post by vedovatti on 2012-05-22
> **onefthemany said:**
> is this intended for me?

@onefthemany
Hi, yes, it was for you. With this instrutions and script you provided I can finally switch between card. I have been looking for it since ubuntu 11.04. Anyway, the script works fine, but it doesnt logout automatically. The script switch card but doesnt run logout command (at least in Ubuntu 12.04) any idea why? or it works as well for you and its only me who has the problem?
Thank you.

---

### Post by onefthemany on 2012-05-24
> **vedovatti said:**
> @onefthemany
Hi, yes, it was for you. With this instrutions and script you provided I can finally switch between card. I have been looking for it since ubuntu 11.04. Anyway, the script works fine, but it doesnt logout automatically. The script switch card but doesnt run logout command (at least in Ubuntu 12.04) any idea why? or it works as well for you and its only me who has the problem?
Thank you.

Can you explain what your seeing and what you are trying to achieve.

Also what do you mean by "The script switch card but doesnt run logout command"

---

### Post by vedovatti on 2012-05-24
> **onefthemany said:**
> Can you explain what your seeing and what you are trying to achieve.

Also what do you mean by "The script switch card but doesnt run logout command"

Hi.
When I run the script I see the same images you have attached. So when I click on "Switch to discrete" it turns on the discrate and it supposed to run "gnome-session-quit" added in the script you provided and logout. But it does not do it. After I "Switch to discrete" I have to logout manually. Any idea to solve it? it is important for me as I will try to make a blog how to install the whole functionalities on my laptop model.
Thanks

---

### Post by onefthemany on 2012-05-24
> **vedovatti said:**
> Hi.
When I run the script I see the same images you have attached. So when I click on "Switch to discrete" it turns on the discrate and it supposed to run "gnome-session-quit" added in the script you provided and logout. But it does not do it. After I "Switch to discrete" I have to logout manually. Any idea to solve it? it is important for me as I will try to make a blog how to install the whole functionalities on my laptop model.
Thanks

sadly the logout function is out of my control as the gnome-session-quit command should work

you could issue the --no-prompt or--logout at the end and see if that works for you

however if you feel the urge to report a bug:

[http://dev.man-online.org/man1/gnome-session-quit/](http://dev.man-online.org/man1/gnome-session-quit/)

also make sure you give credit to the creator of the script in your blog

good luck

---

### Post by markackerman8@gmail.com on 2012-06-17
> **onefthemany said:**
> I had the same issue on my HP Envy 14; here is what i done:


edit the /etc/fstab and add the following lines:

tmpfs /dev/shm tmpfs defaults 0 0

none /sys/kernel/debug debugfs defaults 0 0


then edit the /etc/rc.local and add before exit0:

p.s. I am the one who started this thread months ago still no luck - and I will respond - FAST - to any request for details

chown $User /sys/kernel/debug/vgaswitcheroo/switch

echo OFF> /sys/kernel/debug/vgaswitcheroo/switch

once you have done that use the attached script & drop it into your /usr/bin folder, and then drop the attached icons into home/$User/.local/share/icons folder

Note: you may want to change the $User in the /home/%User/.local/share/icons element to be the user on your machine. make sure the attached file is executable or it wont work; so either chmod or change permissions by right click.

prior to running the script ensure you have installed gxmessage

to run the script/app, open a terminal and get into root (sudo su)

then simply run the following command:

switch_between_cards

the switch 1-4 picture attached shows the process and you can see my radeon card is going from off to on to off again

references:

[https://help.ubuntu.com/community/HybridGraphics](https://help.ubuntu.com/community/HybridGraphics)

i have changed the following in my script:

gnome-session-save --logout to gnome-session-quit

removed open box opens as they were conflicting

good luck

hope this helps
------------------------------------------------------------------

I did everything as stated above -and arghhh still no luck

It is still KILLING my Ubuntu experience 5 months later and retried again today hoping something will change

any way here is what i did from a fresh install tonight - if it helps anyone with m troubleshooting this - PLEASE

- installed fresh 12.04 Ubuntu 64 bit
- downloaded and installed amd's driver 12.4 according to the wicki
[http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29](http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29)
- after sudo amdconfig --initial -f, used switch_between_cards script seemed to work BUT logout or  reboot X fails and only cntgrl+alt+F1 works, so I had to remove /etc/X11/xorg.conf, to get back in (and no discrete card function) - arghhhhhhh

PLEASE can anyone suggest any other troubleshooting tips - now 5 months without a functional Ubuntu

p.s. I am the one who started this post many months ago with still NO success using my ATI/AMD 6850m graphics card please help - I Like games and Hate Windows

---

### Post by vedovatti on 2012-06-17
Hi there.
First you have to know what kind of hybrid (or switchable) graphics you have. There are with "MUX" and "MUXLESS". It is a big difference.
The MUXLESS are the newest hybrid graphic cards. They normally are Intel HD 3000 and second generation of core i3 i5 i7 bla bla.
The MUXED is the one I have. It is a core i5 first generation.

The MUXLESS are already supported by ATI. Check this forum: [http://ubuntuforums.org/showthread.php?t=1930450](http://ubuntuforums.org/showthread.php?t=1930450) 

The MUXED (the one I have is a ATI 5450 / Intel core i5) currently is only possible to switch with vgaswitcheroo.

Now. If you have a MUXED then here is what I did.

1) Open the file
```
sudo gedit /etc/rc.local
``` and add this:
[PHP]modprobe radeon
chown -R $USER:$USER /sys/kernel/debug
echo OFF > /sys/kernel/debug/vgaswitcheroo/switch[/PHP]
That turns off the discrete card before Ubuntu starts.


2) If you want to switch to card do this:
```
sudo gedit /etc/fstab
``` and add the following lines:
[PHP]tmpfs /dev/shm tmpfs defaults 0 0
none /sys/kernel/debug debugfs defaults 0 0[/PHP]

Then download the script that onefthemany attached to his comment. Make it executable (just right click and in the permission tab tick it). Then double click on the script switch it and logout.

When you log in again you will be using the discrete card.

Good luck

---

### Post by markackerman8@gmail.com on 2012-06-18
Thanks for your quick reply.  

I have done a bit of research and I can say with a high degree of certainty it is a MUXLESS system, based on the fact that it is a very new computer and the highest supervisor in HP Envy Tech support said so.  So  your last suggestions are sadly not likely going to work for me - thanks any way SO MUCH, 

Mark

Any more suggestions would be MUCH appreciated.

---

### Post by SevasTraSi on 2012-07-26
Hello, thanks for the script, I had to make some tweaks to get it working.

I added the following to the top of switch_between_cards
```
sudo chmod -R 705 /sys/kernel/debug/vgaswitcheroo/switch
```
to overcome some permission problems.

I then noticed the only way to ensure my graphics switched every time was to echo DIS and then DDIS, or IGD then DIGD. I realise this should be redundant but it works.

so wherever you see:
```
echo IGD > /sys/kernel/debug/vgaswitcheroo/switch

```
add the second command to make
```
echo IGD > /sys/kernel/debug/vgaswitcheroo/switch
echo DIGD > /sys/kernel/debug/vgaswitcheroo/switch

```

and the same for DIS so you get:

```
  echo DIS > /sys/kernel/debug/vgaswitcheroo/switch
  echo DDIS > /sys/kernel/debug/vgaswitcheroo/switch
```

I am not using gnome at all in my Ubuntu install as I am running awesomeWM and avoiding anything with gnome dependencies. This meant the logout line returned a gnome error.
Therefore this:
```
gnome-session-quit
```
can be swapped for the less polite:
```
sudo kill -9 `pidof X`
```
Hope this helps someone else who was struggling as I was.

---

### Post by Nevralgeek on 2012-08-22
Hi, I have some problems with vgaswitcheroo.
I've got an Acer 4820tg (ATI HD 5470 + Intel core i3 integrated gpu), and I managed to have switchable gpu working with my good old Fedora 14.
I had to wipe everything out recently, and I installed Xubuntu.

The problem is that the script doesn't work on XFCE.
I can have both card running, or only integrated Intel one. If I turn the ATI on, there is no change, both are turned on but I'm still on the Intel HD one.

What should I change in the script to make it compatible with XFCE ?

I tried to remove "gnome-session-save --logout" and I replaced it with "xfce4-session-logout --logout" but it doesn't seem to be a great idea : "the name xorg.xfce.SessionManager was not provided by any .service file".

Any idea to adapt the script ?

Thanks a lot

---

### Post by lkm32 on 2012-08-22
Hey guys,

I'm on Ubuntu 12.04 and whenever I add the chown line to rc.local and reboot it simply freezes citing something about kernel safety.

So, any fix for this?

---

### Post by onefthemany on 2012-09-21
> **vedovatti said:**
> Hey, I was looking for updated script to switch between cards. Thanks. It works. Just the logout doesn´t work. I have to run it manually. Any idea how to improve it? I am using ubuntu 12.04. Thanks

I have found the following issues when following the instructions at [https://help.ubuntu.com/community/HybridGraphics:](https://help.ubuntu.com/community/HybridGraphics:)
-----------------------------------------------------------------

To have permanent write permissions to the switch file, add the following line, replacing USERNAME with your username, to /etc/init.d/rc.local:

chown USERNAME /sys/kernel/debug/vgaswitcheroo/switch
-----------------------------------------------------------------

I do not add the above command to /etc/init.d/rc.local, i simply just chown the above file. adding the line into the rc.local file does nothing at all for me and prevents me from using the script to create a laucher and results in me running sudo su in the terminal first followed by the switchcards.sh command.

In addition to solve some dependencies I have add the following to the top of the script:

```


if [ $EUID != 0 ]; then
    gksudo "$0" "$@"
    exit $?
fi 
```

Note: Thanks to druellan (i have adapted his addition and removed the gnome-session-quit option)

Finally if you want to resolve the brightness issue on boot you can do this by issuing the following commands from terminal:

```


chown $User /sys/class/backlight/acpi_video0/brightness
echo 1 > /sys/class/backlight/acpi_video0/brightness 
```

Note: change $User with your name :)
regards

sean

---

### Post by onefthemany on 2012-09-21
> **markackerman8@gmail.com said:**
> ------------------------------------------------------------------

I did everything as stated above -and arghhh still no luck

It is still KILLING my Ubuntu experience 5 months later and retried again today hoping something will change

any way here is what i did from a fresh install tonight - if it helps anyone with m troubleshooting this - PLEASE

- installed fresh 12.04 Ubuntu 64 bit
- downloaded and installed amd's driver 12.4 according to the wicki
[http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29](http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29)
- after sudo amdconfig --initial -f, used switch_between_cards script seemed to work BUT logout or  reboot X fails and only cntgrl+alt+F1 works, so I had to remove /etc/X11/xorg.conf, to get back in (and no discrete card function) - arghhhhhhh

PLEASE can anyone suggest any other troubleshooting tips - now 5 months without a functional Ubuntu

p.s. I am the one who started this post many months ago with still NO success using my ATI/AMD 6850m graphics card please help - I Like games and Hate Windows

don't install the AMD graphics driver as it still has issues. out of the box 3D should work if you simply follow my instructions.

if however you feel the urge to use the AMD graphics driver you could try the following:

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

but if I was you I wouldn't touch it with a barge pole, as to date, I have had no success and have to terminal at boot and delete the conf file

good luck :)

---

### Post by acutbal on 2012-09-27
> **onefthemany said:**
> I have found the following issues when following the instructions at [https://help.ubuntu.com/community/HybridGraphics:](https://help.ubuntu.com/community/HybridGraphics:)
-----------------------------------------------------------------

To have permanent write permissions to the switch file, add the following line, replacing USERNAME with your username, to /etc/init.d/rc.local:

chown USERNAME /sys/kernel/debug/vgaswitcheroo/switch
-----------------------------------------------------------------

I do not add the above command to /etc/init.d/rc.local, i simply just chown the above file. adding the line into the rc.local file does nothing at all for me and prevents me from using the script to create a laucher and results in me running sudo su in the terminal first followed by the switchcards.sh command.

In addition to solve some dependencies I have add the following to the top of the script:

```


if [ $EUID != 0 ]; then
    gksudo "$0" "$@"
    exit $?
fi 
```Note: Thanks to druellan (i have adapted his addition and removed the gnome-session-quit option)

Finally if you want to resolve the brightness issue on boot you can do this by issuing the following commands from terminal:

```


chown $User /sys/class/backlight/acpi_video0/brightness
echo 1 > /sys/class/backlight/acpi_video0/brightness 
```Note: change $User with your name :)
regards

sean

Hello!!

I have the same problem, I can't switch to discrete graphics. My laptop, a HP G62, has an IGD Ati HD4250 and a DIS Ati HD5470 GPU. Also, I'm running Ubuntu 12.04 64 bits.

The "vgaswitcheroo" is active and the file "switch" in /sys/kernel/debug/vgaswitcheroo exists.

My etc/rc.local:
```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

chown albert /sys/kernel/debug/vgaswitcheroo/switch

echo OFF > /sys/kernel/debug/vgaswitcheroo/switch

exit 0
```My  etc/fstab:
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=3b4c963d-b5af-462a-b9fa-15b78a141a5c /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda7 during installation
UUID=6faa099c-6611-4ee0-9bef-58a78263b182 /home           ext4    defaults        0       2
# swap was on /dev/sda8 during installation
UUID=2979ae78-d12a-4558-8e60-32e967e6d4b1 none            swap    sw              0       0

tmpfs /dev/shm tmpfs defaults 0 0

none /sys/kernel/debug debugfs defaults 0 0
```With the command "echo OFF > /sys/kernel/debug/vgaswitcheroo/switch" I can turn off the DIS card with the benefits of less temperature and more battery life.

Furthermore, with " echo ON > /sys/kernel/debug/vgaswitcheroo/switch" I can turn on the DIS card. 

But is in this point where I get stuck. Commands "echo DIS > /sys/kernel/debug/vgaswitcheroo/switch" and "echo DDIS > /sys/kernel/debug/vgaswitcheroo/switch" don't do anything.

 Also if I try the scripts posted in this thread (similar to this one [http://asusm51ta-with-linux.blogspot.com.es/](http://asusm51ta-with-linux.blogspot.com.es/)) they don't logout automatically and if I logout manually the laptop freezes with a black screen.
```
Script page nº 1 post
albert@HPG62:~$ sudo switchcards
[sudo] password for albert: 
/usr/bin/switchcards: 76: [: :+ pwr:: unexpected operator
/usr/bin/switchcards: 81: [: :+ pwr:: unexpected operator
/usr/bin/switchcards: 85: [: :+ pwr:: unexpected operator
/usr/bin/switchcards: 91: [: :+ pwr:: unexpected operator

Script page nº 3 post
albert@HPG62:~$ switchcards
albert@HPG62:~$ 
```Then the only way to recover Ubuntu is forcing the reboot with the power button, and nothing changes:
```
root@HPG62:/home/albert# cat /sys/kernel/debug/vgaswitcheroo/switch
0: IGD:+ Pwr:0000:01:05.0
1: DIS:  :Off:0000:02:00.0
```Any idea?

Thank you very much and best regards!!

---

### Post by onefthemany on 2012-10-07
Have you tried using the gxmessage script?

---

### Post by acutbal on 2012-10-07
> **onefthemany said:**
> Have you tried using the gxmessage script?

Hello!!

Thanks a lot for your response!!!

Apologize, but I've no idea what about you are talking. Gxmessage script? What's that? 
I' ve installed a package vía Synaptic called gxmessage, perhaps you mean that?

Thanks and best regards!!!! :-D

---

### Post by onefthemany on 2012-10-11
> **nuevo iphonero said:**
> Hello!!

Thanks a lot for your response!!!

Apologize, but I've no idea what about you are talking. Gxmessage script? What's that? 
I' ve installed a package vía Synaptic called gxmessage, perhaps you mean that?

Thanks and best regards!!!! :-D

Hi,

These are the steps that I take on a clean install on my HP Envy 14 i7 with my AMD Radeon HD 6600 Series Graphics Card:

1. install gxmessage
2. put images into the /home/$user/.local/share/icons folder
3. drop the switchcards.sh using nautilus into /usr/bin folder and make it executable and change rights permission to the user and not root.
4. Add the following to the /etc/rc.local file:

VGA Switcheroo - 

chown $User /sys/kernel/debug/vgaswitcheroo/switch
echo OFF > /sys/kernel/debug/vgaswitcheroo/switch

Screen Brightness on boot to stop having to press the brightness key -

chown $User /sys/class/backlight/acpi_video0/brightness
echo 5 > /sys/class/backlight/acpi_video0/brightness

Note: You may also want to manually chown the vga and acpi files!!!

5. install main menu
6. create an app launcher and link it to the switchcards script
7. use unity to open the app launcher
8. input password
9. change to integrated to stop fan noise.

You can off course if you would like install the AMD graphics driver and then install fglrx-amdccle to have full control over your graphics card, but its not recommended as it causes all kinds of issues.

If I were you I would use the xorg open source driver!!!!

Note: Prior to installing the AMD graphics card ensure you have POSIX enabled by copying the following to your /etc/fstab file:

tmpfs /dev/shm tmpfs defaults 0 0

none /sys/kernel/debug debugfs defaults 0 0

Good Luck! :)

---

