---
title: "Failed to initialize the NVIDIA graphics device"
date: 2008-12-12
forum: Installation &amp; Upgrades
---

### Post by kolibri on 2008-12-12
I upgraded to intrepid from Hardy.

I have a Nvidia GeForce 7300 GS, which nvidia-glx-177 is supposed to support. I just installed the latest Intrepid updates which included some NVIDIA modelalias updates, but nothing has changed.

When i turn on the computer I  get this error message:

-----------
Failed to initialize the NVIDIA graphics device
...
Run Ubuntu in low graphics mode
-------------------

Once I'm logged in the hardware drivers says that NVIDIA driver 177 is activated and currently in use.

When I try to start NVIDIA X server settings (sudo nvidia-settings)  it says
"You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. "

Sudo nvidia-xconfig gives me :
Using X configuration file: "/etc/X11/xorg.conf".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

However, when i restart the x server, or when i restart the system, it still won't let me access the NVIDIA X-server settings, and I start the loop above again, starting with the unable to initialize Nvidia graphics device.

---

### Post by kolibri on 2008-12-23
Is this not a pervasive problem and just me?

I still can't get Ubuntu to recognize that the NVIDIA driver is apparently installed correctly:  system -administration-hardware drivers says that NVIDIA accelerated graphics driver version 177 recommended is installed, activated, and currently in use, however, I cannot access nvidia-settings, and now Google Earth won't work and says: "Unknown Graphics Card"  Google Earth is unable to identify your graphics card.  This is most likely because the driver for your graphics card has not been installed.

I really don't want to have to to do a clean install of Hardy and wipe out all my customizations.

---

### Post by unseenbeing on 2008-12-28
i have this same problem too so if anyone can help that would be cool

---

### Post by snaildarter on 2009-05-07
Been pulling my hair out and wondering if anyone has found a solution to this problem.

---

### Post by Kareeser on 2009-05-07
Let me get this straight...

You all have upgraded to Intrepid from Hardy, correct?

If this is the case, please note that the driver does not update by itself... at least, manually installed, it doesn't. If you're getting this message after automatically installing drivers, I'd suggest running "sudo apt-get update ; sudo apt-get upgrade".

If the problem persists, please try manually installing a driver for your card by following the instructions here:
[http://ubuntu.kareeser.com/?p=44](http://ubuntu.kareeser.com/?p=44)

---

### Post by junglefun on 2009-09-02
> **Kareeser said:**
> Let me get this straight...

You all have upgraded to Intrepid from Hardy, correct?

If this is the case, please note that the driver does not update by itself... at least, manually installed, it doesn't. If you're getting this message after automatically installing drivers, I'd suggest running "sudo apt-get update ; sudo apt-get upgrade".

If the problem persists, please try manually installing a driver for your card by following the instructions here:
[http://ubuntu.kareeser.com/?p=44](http://ubuntu.kareeser.com/?p=44)


The link is invalid now. Do you have it somewhere else?
BTW, I'm using Jaunty and was installed directly, not an upgrade.
Graphic card: Geforce 7350 LE
(EE)NVIDIA(0): Failed to initialize the nvidia graphic device PCI:1:0:0
...
(EE)NVIDIA(0): Screen(s) found, but none have a usable configuration.

---

### Post by jumping_snake on 2009-12-10
Hello all, I'm also having this issue. I've always had it since NVIDIA drivers have been available. I have an 8600GT (PCI-E), and it's never worked correctly. I've at least been able to use two screens (which is the only thing I'm really trying to do) when NO drivers are installed, but that's just a work-around. Does anybody have any fixes for this?

I'm not a really good linux graphics guy, so I'll poke around some in the README like the error message says, etc...

Update: The error message references "Chapter 8: Common Problems" in the README. Does anybody know which REAME it's talking about? I ran this:
find / -name README | grep nvidia 
and of the 5 READMEs that came up, none were longer than about 8 paragraphs.

Update2: I've tried using Envy: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
That tells me that the driver is installed and should be working, but after restart, it continues to post the error message and I have to run in low-graphics mode.

---

### Post by drdos2006 on 2009-12-10
Had the same problem. 
The only way I was able to prove that my video card was not corrupted was to install nVidia Window drivers for 8400 GS under Windows XP 64 bit.
Even after a clean instal of Ubuntu 9.10 64 bit and clean install of 9.10 32 bit, I still could not get the card recognised. I changed over to nVidia 7400 video card, did a clean install and the problem is resolved. But I had to do a clean install. 
I also tried with Ubuntu 7 and 8.10 to see what the difference would be and discovered something interesting.
Originally had 4 drives, 2 Sata (320 G ) and 2 PATA ( 120 and 320 Gig). The 3rd HDD (120 Gigs ) was the boot disk. Due to video problems I installed U 9.10 with the 1st HDD as the boot disk. When re-installing 8.10 after 9.10 was wiped, 8.10 saw original HDD configuration, ie 3rd HDD as boot drive, not 1st HDD as in 9.10. So somewhere, this boot information is being stored on the HDD, maybe in the first boot sector, maybe not the MBR.
Try another video card, it might help you situation.

---

### Post by jumping_snake on 2009-12-11
As you mentioned, I'm able to run Windows XP 32-bit with the card just fine, so I don't believe it's the card.

Also, after reading into my error some more, it appears that the video drivers themselves are working correctly, but that my "screens" aren't. I'll continue to look into this and hopefully come out the other side :)


Update: I stopped playing with this earlier today. Booted the computer into Windows XP for a little bit, tried to restart into Ubuntu. However, right before the login screen, the system frooze. I had to hard-reboot it. This is when the unexpected happened: NVIDIA drivers worked FLAWLESSLY with my monitor. It was setup correctly, I could get into the NVIDIA display program, EVERYTHING. I tried to add my second monitor, but it wasn't detecting that it was turned on, so I restarted my system. Low and behold, the driver isn't working again.

I'll see if I can re-create the pattern/check out the logs to see what's happening that makes it work (if I can get it to do it again). Is there such a thing as a monitor that isn't supported by the NVIDIA drivers? I have a Dell 2007WFP and the Dell 2009* (whatever the new 20-inch version of the 2007 is).

---

### Post by jumping_snake on 2010-01-07
RIGHT! So after far too long, I've stumbled upon the answer to my errors: I forgot that I have a TV tuner card installed. At startup, the memory that's used to get all of the devices setup for use was too small and my TV tuner card was using too much of it...to the point that my nVidia card wasn't getting initialized.

So, after stumbling on this amazing find here:
[http://ubuntuforums.org/showthread.php?t=1002287](http://ubuntuforums.org/showthread.php?t=1002287)
and I've got it going.

These are the steps that I had to use in order to get the video card working for 9.10*:

*If you're reading this thread, I assume you've done the following and not installed any other drivers.
1) System->Administration->Hardware Drivers
2) Click on the 185 and then click activate
3) Reboot


New Steps:
Startup your system and either get to a console from the GRUB menu or boot to Ubuntu in low graphics mode and open a terminal once it's up. Once up, type the following command
```
sudo pico /etc/default/grub
```
Once inside of the file, search for this line
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```
right before the last ", put vmalloc=256M, so that the line looks like:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash vmalloc=256M"
```
Then, hit CTRL+O and ENTER, and then CTRL+X. This will bring you back to the terminal. At this point, we need the startup system to reconfigure itself, so we type the following command
```
sudo update-grub
```
Now, reboot the system

**NOTICE** If this doesn't work, try putting 192M instead of 256M. This has been reported to help as well.

What we've done is create an automatically booting proceedure that will allow us to use our video cards!

---

### Post by jayanramesh on 2010-01-07
-----------
> Failed to initialize the NVIDIA graphics device
...
Run Ubuntu in low graphics mode
-------------------

Once I'm logged in the hardware drivers says that NVIDIA driver 177 is activated and currently in use.

When I try to start NVIDIA X server settings (sudo nvidia-settings) it says
"You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. "

Sudo nvidia-xconfig gives me :
Using X configuration file: "/etc/X11/xorg.conf".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

However, when i restart the x server, or when i restart the system, it still won't let me access the NVIDIA X-server settings, and I start the loop above again, starting with the unable to initialize Nvidia graphics device.
kolibri is offline Report Post   	Reply With Quote

Dear pals,
I have got the same problem ,is there anyone on EARTH who could solve this issue?
Thank you

---

### Post by jumping_snake on 2010-01-07
Hey jayanramesh,
  Let's start from the top:

1) What version of Ubuntu are you running and what version of the driver are you trying to install? Is it 177 from an older version of Ubuntu?

2) If you look at your xorg log file, are there any errors being produced?

I'm assuming from what you copied that you have gone to System->Administration->Hardware Drivers and activated the driver.

---

### Post by elabidba on 2010-01-09
Thank you jumping_snake. I've been trying for 2 days to solve this problem. Just like you, I have a Hauppauge WinTV-HVR-1600 with NVIDIA GeForce 6150 LE on the HP Pavillion a1747c (AMD 64 X2). The vmalloc=256M fixed the problem with Ubuntu 9.10 (Karmic) and NVIDIA Linux Drivers v195.30. I actually had the problem with all the NVIDIA drivers.

Now it's time to setup the TV Tuner drivers with MythTV :)

Thanks again,
--Bassam

---

### Post by lhowaf on 2010-03-04
jumping_snake, i luv u man!
Your solution worked with my 9800 GT / HVR-1600 setup - finally (I won't tell you how long i've failed at solving this). 1 internet to you.

---

### Post by bsyapril88 on 2010-05-11
AWESOME!

I've been running around thinking it was a problem with the driver.  Who would of thought it was the dang tv tuner?

Thank you for the tip.

I was putting ubuntu 10.04 onto a hp pavilion media center pc with a Hauppauge.  I recently upgraded its graphics card to a nvidia geforce gt240.

---

### Post by kolibri on 2010-07-09
> **jumping_snake said:**
> RIGHT! So after far too long, I've stumbled upon the answer to my errors: I forgot that I have a TV tuner card installed. At startup, the memory that's used to get all of the devices setup for use was too small and my TV tuner card was using too much of it...to the point that my nVidia card wasn't getting initialized.

So, after stumbling on this amazing find here:
[http://ubuntuforums.org/showthread.php?t=1002287](http://ubuntuforums.org/showthread.php?t=1002287)
and I've got it going.

These are the steps that I had to use in order to get the video card working for 9.10*:

*If you're reading this thread, I assume you've done the following and not installed any other drivers.
1) System->Administration->Hardware Drivers
2) Click on the 185 and then click activate
3) Reboot


New Steps:
Startup your system and either get to a console from the GRUB menu or boot to Ubuntu in low graphics mode and open a terminal once it's up. Once up, type the following command
```
sudo pico /etc/default/grub
```
Once inside of the file, search for this line
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```
right before the last ", put vmalloc=256M, so that the line looks like:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash vmalloc=256M"
```
Then, hit CTRL+O and ENTER, and then CTRL+X. This will bring you back to the terminal. At this point, we need the startup system to reconfigure itself, so we type the following command
```
sudo update-grub
```
Now, reboot the system

**NOTICE** If this doesn't work, try putting 192M instead of 256M. This has been reported to help as well.

What we've done is create an automatically booting proceedure that will allow us to use our video cards!

I'd like to  try this, but I have no grub file at this location.  "search for files" named grub finds me no grub file.  Where does my grub file live?

---

### Post by pandanuma on 2010-07-16
jumping snake solved it for me.
same problem with the hauppauge tv tuner

I did everything as instructed but no luck...:confused:
256M and 192M just did not work
so after reading a lot more threads I tried:  512m
notice the lowercase  m
and this time instead of a reboot,
I powered down the computer for awhile
(don't ask, just my own personal voodoo)
turned it back on...problem solved..:popcorn:

my only serious point here is to suggest 512m if the other two dont work
and does lowercase make any difference?

I would mark this problem solved for me.

kolibri, what happened when you tried   sudo pico /etc/default/grub

---

### Post by kolibri on 2010-07-26
> **pandanuma said:**
> jumping snake solved it for me.
same problem with the hauppauge tv tuner
....

kolibri, what happened when you tried   sudo pico /etc/default/grub

It made a blank file called grub.

I have a boot/grub folder, but no single file called grub in it, and no grub files in etc/default

---

### Post by pandanuma on 2010-07-27
hmmm...are you still using ubuntu intrepid?
maybe it is time to upgrade to lucid linux
your grub file should be in /etc/default/

---

### Post by pandanuma on 2010-07-27
and further more...

stay out of /boot/grub/

check this link...
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2) 

it suggest you check your version of grub like so

```
grub-install -v
```

version 1.96 or greater means it is grub2

follow the instructions for upgrading to grub to if you only have grub

---

