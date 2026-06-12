---
title: "Graphics card not working with Ubuntu 12.04"
date: 2016-03-18
forum: Hardware
---

### Post by bret5 on 2016-03-18
[FONT=arial][SIZE=2]I have a desktop computer that I built that has an old hardrive that dual boots Microsoft Windows XP and Ubuntu 12.04. When I turn it on everything works fine at first. When it gets to the boot menu I select Ubuntu and it starts loading with Ubuntu 12.04 displayed on the screen. after that the screen goes completely black. I know that it is at the password screen at that point. When I enter my password I briefly get a glimpse of the red and white login screen, but then the screen goes completely white, and that is where I get stuck. The graphics card is a:

[/SIZE][/FONT]**[FONT=arial][SIZE=2]SPARKLE GeForce GTS 250 DirectX 10 SXS2501024D3-NM 1GB 256-Bit GDDR3 PCI Express 2.0 x16 HDCP Ready SLI Support Video Card. [/SIZE][/FONT]**

Any advice on how to proceed from here would be appreciated.

---

### Post by Bashing-om on 2016-03-18
bret5; Hello; Welcome to the forum .

Let's look at things before a GUI is loaded and the GUI graphics driver is a factor.
As you can reach the grub boot menu .. here, select the newest 'buntu kernel to boot, and press the 'e' key for edit mode -> boot parameters screen;
arrow down to the line starting with linux. and arrow across to "quiet splash" replace these terms with the term "text" - without the quotes. key combo ctl+x to continue the boot process to TTY1.
At the TTY1 terminal log into the system with your username and password . There will be no response to the screen when password is entered. Enter your pass word blindly and hot the enter key.

Now, once at a terminal .. we can look at the graphics situation and make reconciliation . If you can not get to a terminal... there are other factors at play here than that of the graphic's driver. At this point - booting to terminal - the GUI driver is not a factor.

When you are at terminal, and logged in we run some commands to see what the situation is, and what then we can do.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by bret5 on 2016-03-19
I followed your instructions. I am at the tty1 prompt.

---

### Post by Bashing-om on 2016-03-19
bret5; Great.

As you are at terminal, we know the kernel is in good shape so our focus is on the GUI layer that is applied on top of the kernel.
Let's see what is:
As you are at a TTY you do not have the amenities of a terminal emulator and to make it easy to transfer info, let us install a tool to make that so:
```

sudo apt install pastebinit

```

Now to tranasfer to the pastebin site some information:
Run terminal commands:
```

lspci -k | grep -EA2 'VGA|3D' | pastebinit
sudo lshw -C display | pastebinit
pastebinit /var/log/Xorg.0.log.old

```
where the results are URLs back in terminal. pass these links back here and we see
'lspci' is list PCI devices and filtered for VGA or 3D devices.
'lshw' is list hardware related to graphics and what driver - if any - is loaded.
'/var/log/ is a directory containing many many system log files, here we are interested in what X did on that last boot (old).

From all this we make sure that there is a matching driver for the graphic's card, and what the X layer is doing , particularly with the graphic's card.

[INDENT][INDENT]ain't no step for a stepper
[/INDENT][/INDENT]

---

### Post by bret5 on 2016-03-20
I am not sure whether or not the pc is connecting to the internet. How can I test the connection from tty1?

---

### Post by Bashing-om on 2016-03-20
bret5; Yuk;

Terminal commands:
```

ping -c3 8.8.8.8
ping -c3 ubuntu.com

```
both should have returns . If only 8.8.8.8 returns you have a DNS issue .

[INDENT][INDENT]hope this helps
[/INDENT][/INDENT]

---

### Post by bret5 on 2016-03-20
Thanks for your prompt reply. I have resolved the internet issue.

The line:


[COLOR=#000000][FONT=Ubuntu Mono]lspci -k | grep -EA2 'VGA|3D' | pastebinit[/FONT][/COLOR]

returned:

grep: EA2: No such file or directory
grep: VGA|3D: No such file or directory
You are trying to send an empty document, exiting. [COLOR=#000000][FONT=Ubuntu Mono]
[/FONT][/COLOR]

---

### Post by Bashing-om on 2016-03-20
bret5; Humm ...

That is real odd .. the system is not even seeing a video card ?

What returns:
```

lspci

```
and we look at all the PCI devices .

[INDENT][INDENT]smell of rotten fish ?
[/INDENT][/INDENT]

---

### Post by bret5 on 2016-03-20
lspci returned:

08:00.0 VGA compatible controller: NVIDIA Corporation G92 [GeForce GTS 250] (rev a2)

---

### Post by Bashing-om on 2016-03-21
bret5; Well ..

Now, that should not present a problem, takes the 340 version driver and still well supported.

So back to post # 4 .. what driver is installed - if any:
```

sudo lshw -C display

```

and what is X doing about a driver :
```

cat /var/log/Xorg.0.log

```

[INDENT][INDENT]soon a tale will be told
[/INDENT][/INDENT]

---

### Post by bret5 on 2016-03-21
Here we go, the first code returns:

[http://paste.ubuntu.com/15444330/](http://paste.ubuntu.com/15444330/)

The second code returns:

[http://paste.ubuntu.com/15444317/](http://paste.ubuntu.com/15444317/)

---

### Post by Bashing-om on 2016-03-21
bret5; Great !

Done all I can, can do no more this session.
Will pick this up soon as I return in my AM .

[INDENT][INDENT]progress made
[/INDENT][/INDENT]

---

### Post by tokyobadger on 2016-03-21
> **bret5 said:**
> [FONT=arial][SIZE=2]I have a desktop computer that I built that has an old hardrive that dual boots Microsoft Windows XP and Ubuntu 12.04. When I turn it on everything works fine at first. When it gets to the boot menu I select Ubuntu and it starts loading with Ubuntu 12.04 displayed on the screen. after that the screen goes completely black. I know that it is at the password screen at that point. When I enter my password I briefly get a glimpse of the red and white login screen, but then the screen goes completely white, and that is where I get stuck. The graphics card is a:

[/SIZE][/FONT]**[FONT=arial][SIZE=2]SPARKLE GeForce GTS 250 DirectX 10 SXS2501024D3-NM 1GB 256-Bit GDDR3 PCI Express 2.0 x16 HDCP Ready SLI Support Video Card. [/SIZE][/FONT]**

Any advice on how to proceed from here would be appreciated.

Can you share what other hardware is in this PC, especially motherboard and BIOS version

---

### Post by bret5 on 2016-03-21
The following are the commands and the corresponding pastebinit urls for the information you requested.

sudo dmidecode -t 2
[http://paste.ubuntu.com/15465632/](http://paste.ubuntu.com/15465632/)

lspci
[http://paste.ubuntu.com/15465678/](http://paste.ubuntu.com/15465678/)


sudo dmidecode | more
[http://paste.ubuntu.com/15465717/](http://paste.ubuntu.com/15465717/)

---

### Post by Bashing-om on 2016-03-21
bret5; OK ...

Here is the deal thus far !

You are running hybrid graphics and the problem:
> 
product: Z7/Z9 (XG20 core)
       vendor: XGI Technology Inc. (eXtreme Graphics Innovation)
##from the log file =>
20.923] (WW) Warning, couldn't open module xgi
20.923] (EE) Failed to load module "xgi" (module does not exist, 0)

21.069] (WW) NOUVEAU(0): Unable to find connected outputs - setting 1024x768 initial framebuffer

##found ??->
21.087] (II) FBDEV(1): hardware: XGI (video memory: 32768kB)

21.707] (II) AIGLX: Loaded and initialized nouveau
-----------------------
##Huh ?? ->
20.960] (**) FBDEV(5): claimed PCI slot 1@0:4:0
##Why not nouveau or XGI claiming the device ???



I will be a bit digesting what I do not know .. sorta confused as to what I am looking at.

While I am dithering about .
Insure you are authorized to access "your" desktop.
What returns:
```

ls -al .Xauthority
ls -al .ICEauthority

```
Let us rule that out as a possible causation.

[INDENT][INDENT][INDENT]the hunt is on
[/INDENT][/INDENT][/INDENT]

---

### Post by bret5 on 2016-03-21
The first command returns:

-rw------- 1 bret bret 56 mar 18 18:29 .Xauthority

The second command returns:

-rw------- 1 bret bret 7766 mar 18 18:29 .ICEauthority

---

### Post by Bashing-om on 2016-03-21
bret5; Welll...

confirmed not an authorization issue .

I am still looking to find how to deal with unfamiliar XGI  ( SIS ??) graphic set.

[INDENT][INDENT]got me to wondering
[/INDENT][/INDENT]

---

### Post by bret5 on 2016-03-21
Thanks for looking into it for me.

---

### Post by tokyobadger on 2016-03-22
Does the nvidia card work under WinXP?

If It does, next thing is to purge all your existing nvidia driver installs (in Ubuntu) and install the nvidia-340.xx branch which is the latest but last for your nvidia chipset. To do that you'd need to install the proprietary graphics PPA. BTW any reason to be running 12.04 instead of at least 14.04?

What I read about your motherboard is that it should automatically switch to the PCIe GPU if it sees one, hence the question as to whether it ever worked in WinXP.

---

### Post by bret5 on 2016-03-22
Yes, I can boot WinXP just fine. I wouldn't know how to "purge" the existing drivers. I am very new to Linux. When I built the computer and set up the dual-boot on the hard drive, 12.04 was the newest version.

---

### Post by Bashing-om on 2016-03-22
bret5; Hey ///

Still struggling to move forward on this.
Still do not know what the /var/log/Xorg.0.log file is telling us .
The system has loaded the opensource driver, nouveau, for the Nvidia card and XGI has the xgifb driver loaded.
I do not know that installing the proprietary Nvidia graphic's driver will help ... but quite possible IF the problem lies in the open source driver.

Let's try and find out what graphic's card is being used
```

lspci -nnk | grep -i vga -A3 | grep 'in use'

```

And next to know is what kernel you are running:
```

uname -a

```
See of HardWare Enablement for the X stack is an issue.

Once we make an attempt to start the GUI the  .xsession-errors file in your /home directory may provide us some hints.

[INDENT][INDENT]sometimes I wonder
[INDENT][INDENT][INDENT]other times I do not know[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by bret5 on 2016-03-23
The first code returns:

 Kernel driver in use: xgifb
kernel driver in use: nouveau

The second code returns:
[COLOR=#000000][FONT=Verdana]Linux Bret-System 3.11.0-18-generic #32~precise1-Ubuntu SMP Thu Feb 20 17:52:10 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
[/FONT][/COLOR]

---

### Post by Bashing-om on 2016-03-23
bret5; Yuk ..

Again, not what I had expected for the graphics set "in use" . One or the other .... but not both .

Now here might be the whole problem:
> 
Linux Bret-System 3.11.0-18-generic #32~precise1-Ubuntu 

That is an old old raring (13.10) kernel and I do not think it is supported in the package management system any longer .. I will verify.

What I expect to be current for your precise HWE is :
> 
Package linux-image-generic-lts-trusty

precise-updates (metapackages): Generic Linux kernel image 
3.13.0.83.75: amd64 i386


Let's consider getting your system updated !

[INDENT][INDENT]I be look'n
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2016-03-23
bret5; Uh huh ...

We are beating on a dead horse .. we need to get a live one in place. The kernel you are booting ( and the X structure as a whole) is End_Of_Life and has no support:
see:
[https://wiki.ubuntu.com/1204_HWE_EOL](https://wiki.ubuntu.com/1204_HWE_EOL)
[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

Let's work on getting this system current .
```

sudo apt-get update
sudo apt-get install --install-recommends linux-generic-lts-trusty libgl1-mesa-glx-lts-trusty xserver-xorg-lts-trusty linux-image-generic-lts-trusty
sudo apt-get upgrade
sudo apt-get dist-upgrade

```

If and I do stress the IF all goes well in the above .. and there are no errors .. then reboot the system . See now if you boot to the GUI .

If not, we start the troubleshooting procedure from square one .

[INDENT][INDENT]it is what it is
[/INDENT][/INDENT]

---

### Post by bret5 on 2016-03-23
I did all of that, and still no luck, although I did notice two error messages that I hadn't noticed before. Right after I select Ubuntu at the bootloader it says:

[    10.705900] xgifb 0000:01:04.0: Unable request memory size 2000000
[    10.705901] xgifb 0000:01:04.0: Fatal error: Unable to reserve frame buffer memory. Is there another framebuffer driver active?


Hoping that these will lead to some progress.

---

### Post by Bashing-om on 2016-03-24
bret5; Well ...

We could hope, and yes that provides a bit of a way to make progress.

We are looking at SIS graphics .. we may have to jump through some hoops .

Do we have a configuration file in place for the graphics driver ?
what returns:
```

ls -al /etc/X11/Xorg.conf

```
IF that file exists, we want to look at it and see what is contained:
```

cat /etc/X11/Xorg.conf

```
this as but a reference, not a recommendation:
[https://sites.google.com/site/easylinuxtipsproject/xgiz7z9](https://sites.google.com/site/easylinuxtipsproject/xgiz7z9)
[http://manpages.ubuntu.com/manpages/precise/man4/sis.4.html](http://manpages.ubuntu.com/manpages/precise/man4/sis.4.html)
I do continue to examine this .

[INDENT][INDENT]SIS, it is a big thing
[/INDENT][/INDENT]

---

### Post by bret5 on 2016-03-25
It is telling me:

No such file or directory

---

### Post by mörgæs on 2016-03-26
If you enter BIOS are you able to switch off the XGI graphics card, leaving only Nvidia active?

---

### Post by Bashing-om on 2016-03-26
@mörgæs; Hi !

Sure pleased you dropped in here; as I too am in a learning mode.
I do not know how these two graphic sets function and presently a bit out of my depth.
In release 12.04. is not the Xorg.conf required for this configuration ?

@bret5; See that last. We see what we can do do make things work.

drivers:
[INDENT][INDENT][INDENT]that intermediator between the kernel and the hardware
[/INDENT][/INDENT][/INDENT]

---

### Post by bret5 on 2016-03-27
I am not seeing any video options at all in bios, but I am not sure if there are video options and I just can't find them.

---

### Post by mörgæs on 2016-03-28
I would like to see the complete hardware list. Please run ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags.

Bashing-om, I an not sure that I can provide a useable answer but let's see what we find together.

---

### Post by Bashing-om on 2016-03-28
@mörgæs; :)

> 
but let's see what we find together.

puts a smile on my face .

[INDENT][INDENT]good info
[INDENT][INDENT][INDENT]to produce good results
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by bret5 on 2016-03-31
I will get back to you soon. Thanks for all of your help.

---

