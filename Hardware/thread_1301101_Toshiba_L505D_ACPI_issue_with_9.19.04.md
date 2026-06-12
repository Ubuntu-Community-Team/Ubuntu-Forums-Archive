---
title: "Toshiba L505D ACPI issue with 9.1/9.04"
date: 2009-10-25
forum: Hardware
---

### Post by mikep554 on 2009-10-25
I ran into some problems installing 9.10 RC, I also had the same problems with 9.04 so this isn't anything specific to 9.1.

I have a Toshiba L505D-S5992 laptop. It has an Amd Turion II and Ati Radeon 4100 graphics. I had to run the install by selecting the "acpi=off" option from the F6 menu, and I also had to add "acpi=off" to the Grub kernel options to get the installed system to boot. If I don't use "acpi=off", I see a bunch of errors flying by, but the startup dies with the following: '/sbin/modprobe -b acpi:lnxvideo:' unexpected exit with status 0x0009.

While I can get the system up by turning off the acpi option, I'm assuming I'm going to be missing some acpi functionality which might be pretty nice to have on a laptop. Any ideas/suggestions?

---

### Post by mikep554 on 2009-10-25
Some additional information: running lspci gives me the following info for my video hardware:

01:05.0 VGA compatible controller: ATI Technologies Inc Device 9712

lspci -nn gives this:

01:05.0 VGA compatible controller [0300]: ATI Technologies Inc Device [1002:9712]

I read a thread on a debian board that seemed to indicate the current open source ATI drivers don't have support for this chipset, which would explain why I can only run 1024x768 resolution once I am in gnome.

But why would I have to disable acpi? Can the hardware detection not deal with an unknown device?

---

### Post by vishnumrao on 2009-10-29
Just got the Toshiba L505D-S5992. I too have the same problem.

I can boot of the 9.10 live USB only with acpi=off.

I have not installed 9.10 desktop-i386 final. Will install only if there is a solution to the above!

Suggestions anyone?

---

### Post by uli100 on 2009-11-03
I do have a similar problem with a Toshiba X200 and 9.10. 9.04 used to work perfectly. I've installed 9.10 final. Neither the installed version nor the live cd boots without "acpi=off". Without it, I see the error message related to "modprobe -b :acpi:LNXVIDEO:". I tried to boot the latest "grml" which has a 2.6.31 kernel, too. It aborts with the same error message.

Note: My machine has an Intel CPU and a nvidia graphics card.

01:00.0 VGA compatible controller [0300]: nVidia Corporation G84 [GeForce 8700M GT] [10de:0409] (rev a1)

Any idea? How shall I continue?

Best regards, Uli

---

### Post by klemes on 2009-11-03
Nothing definite just a suggsestion.Try the 'noapic' kernel boot option.
Just a thought ,though this could fix your problem since it's laptop related.

---

### Post by batterybaby on 2009-11-03
since your toshiba laptop has juest been bought for not long ,you could turn to after-service for professional help.

---

### Post by klemes on 2009-11-03
Also try acpi=debug and maybe flashing/upgrading  the BIOS on your motherboards.

---

### Post by calimancer on 2009-11-03
I have the same problem with my new Toshiba L505D-S5992 trying to install and use Kubuntu 9.10. I also had to add "acpi=off" to the Grub. In other forum found that there is a problem with DSDT.

Here is how to fix DSDT:
[http://ubuntuforums.org/showthread.php?t=1036051&page=10](http://ubuntuforums.org/showthread.php?t=1036051&page=10)

I disassemble my dsdt.dat file, recompile it with iasl and it has 4 errors:

 
[SIZE=2]/home/cali/DSDT.dsl  9164:                 Alias (^AGP.VGA.UDCS, UDSC)[/SIZE]
   [SIZE=2]Error    4064 - Object not found or not accessible from scope ^  (UDSC)[/SIZE]
     [SIZE=2]
[/SIZE]
  [SIZE=2]/home/cali/DSDT.dsl  9165:                 Alias (^AGP.VGA.LCD, PLCD)[/SIZE]
    [SIZE=2]Error    4064 - ^ Object not found or not accessible from scope (PLCD)[/SIZE]
   [SIZE=2] [/SIZE]
   [SIZE=2]/home/cali/DSDT.dsl  9166:                 Alias (^PB2.VGA.UDCS, UDS1)[/SIZE]
   [SIZE=2]Error    4064 - Object not found or not accessible from scope ^  (UDS1)[/SIZE]
   [SIZE=2] [/SIZE]
   [SIZE=2]/home/cali/DSDT.dsl  9167:                 Alias (^PB2.VGA.LCD, PLC1)[/SIZE]
   [SIZE=2][FONT=&quot][SIZE=2]Error    4064 - ^ Object not found or not accessible from scope (PLC1)
[/SIZE]
[/FONT][/SIZE][SIZE=2][FONT=&quot][/FONT][/SIZE][SIZE=2][FONT=&quot]
[/FONT][/SIZE]They are related to video but I don't know how to repair them.
My laptop came with an ATI Radeon 4200 instead the ATI Radeon 4100 that says in the specificactions.

[SIZE=2][FONT=&quot][/FONT][/SIZE]

---

### Post by uli100 on 2009-11-04
On my X200 (... which probably suffers from the same issues), I tried these:

[LIST]
[*]noapic --> no improvement
[*]acpi=debug --> no improvement, (almost) same output as before
[*]remove "spash" and "quiet" --> immediate reboot
[/LIST]
So: Still no solution unfortunately.

Best regards, Uli

---

### Post by mikep554 on 2009-11-05
Batterybaby: My laptop came with Win 7, so no support from Toshiba.

Klemes: I haven't found a download for a an updated BIOS, but would love to find one if it would help.

It's a real bummer because I don't get any laptop functionality such as a battery meter, suspend on lid close or function keys without ACPI. Also, the system won't power off when I shut it down, it just kind of hangs at a black screen.

I do appreciate the responses though!

---

### Post by raygj on 2009-11-05
> **calimancer said:**
> I have the same problem with my new Toshiba L505D-S5992 trying to install and use Kubuntu 9.10. I also had to add "acpi=off" to the Grub. In other forum found that there is a problem with DSDT.

Here is how to fix DSDT:
[http://ubuntuforums.org/showthread.php?t=1036051&page=10](http://ubuntuforums.org/showthread.php?t=1036051&page=10)

I disassemble my dsdt.dat file, recompile it with iasl and it has 4 errors:

 
[SIZE=2]/home/cali/DSDT.dsl  9164:                 Alias (^AGP.VGA.UDCS, UDSC)[/SIZE]
   [SIZE=2]Error    4064 - Object not found or not accessible from scope ^  (UDSC)[/SIZE]
     [SIZE=2]
[/SIZE]
  [SIZE=2]/home/cali/DSDT.dsl  9165:                 Alias (^AGP.VGA.LCD, PLCD)[/SIZE]
    [SIZE=2]Error    4064 - ^ Object not found or not accessible from scope (PLCD)[/SIZE]
   [SIZE=2] [/SIZE]
   [SIZE=2]/home/cali/DSDT.dsl  9166:                 Alias (^PB2.VGA.UDCS, UDS1)[/SIZE]
   [SIZE=2]Error    4064 - Object not found or not accessible from scope ^  (UDS1)[/SIZE]
   [SIZE=2] [/SIZE]
   [SIZE=2]/home/cali/DSDT.dsl  9167:                 Alias (^PB2.VGA.LCD, PLC1)[/SIZE]
   [SIZE=2][FONT=&quot][SIZE=2]Error    4064 - ^ Object not found or not accessible from scope (PLC1)
[/SIZE]
[/FONT][/SIZE][SIZE=2][FONT=&quot][/FONT][/SIZE][SIZE=2][FONT=&quot]
[/FONT][/SIZE]They are related to video but I don't know how to repair them.
My laptop came with an ATI Radeon 4200 instead the ATI Radeon 4100 that says in the specificactions.

[SIZE=2][FONT=&quot][/FONT][/SIZE]

just a thought,
you might try to use the "Microsoft Windows 2000" section of ACPI's DSDT table.
try rebooting instead of adding "acpi=off" to the Grub add 
acpi_os_name="Windows 2000"
to the grub.
eg.on grub os selection menu screen.press "e"key(edit)and scroll down to line that has "splash" on it and add
acpi_os_name="Windows 2000"
to the left of "splash"
eg.
acpi_os_name="Windows 2000" splash.
then press "esc" to back out to grub os menu and press "return" to boot up.
see if this works for you.
if you're using grub2 then press 'e'key to edit and 'ctrl'key + 'x'key to boot.
also you chould try one of these :-
acpi_os_name="Windows 2006 SP1"
or
acpi_os_name="Windows 2006"
or
acpi_os_name="Windows 2001 SP2"
or
acpi_os_name="Windows 2001 SP1"
or
acpi_os_name="Windows 2000"
or
acpi_os_name="Microsoft Windows NT"

---

### Post by uli100 on 2009-11-06
What about this: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/459837](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/459837) ?

It seems to handle my bug quite good. I'll test the proposed solution soon (... I'll have to free some disk space to recompile the kernel). Please note that in the headline, the bug refers to Toshiba X200. If you follow the links of the ticket, you'll see that it happens for other laptops as well. Maybe you're lucky and your bug is fixed, too?

Update: I recompiled the kernel using the patch mentioned above. Now I can boot without specifying "acpi=off".

Best regards, Uli

---

### Post by arnieh on 2009-11-07
I own a Toshiba Satelite P200 with a Ati Radeon HD2400 videocard and got the same error at boot: "/sbin/modprobe -b acpi:LNXVIDEO unexpected exit with status 0x0009" 
After this error the system seems to hang for about 180 seconds.

I solved this by simply uninstalling the splash screens:

sudo apt-get remove usplash xsplash

---

### Post by mikep554 on 2009-11-08
Arnieh: Removing usplash and xsplash didn't change the problem for me.

Uli: I've never had to compile a custom kernel. Would you have a link with instructions that could walk a newb through it?

---

### Post by mikep554 on 2009-11-08
RayGJ: The acpi_os_name=xxxxxxx didn't change the behavior for my system.

---

### Post by colinwhipple on 2009-11-08
> **uli100 said:**
> What about this: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/459837](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/459837) ?

It seems to handle my bug quite good. I'll test the proposed solution soon (... I'll have to free some disk space to recompile the kernel). Please note that in the headline, the bug refers to Toshiba X200. If you follow the links of the ticket, you'll see that it happens for other laptops as well. Maybe you're lucky and your bug is fixed, too?

Update: I recompiled the kernel using the patch mentioned above. Now I can boot without specifying "acpi=off".

Best regards, Uli

I went to this site:

[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)

and one of the things they say is that if you don't know what you are doing  that is a reason NOT to attempt to compile a custom kernel.

So my question is, can I get your recompiled kernel, or, alternatively, how likely is it that the fix will find its way into the mainstream kernel?

Thanks,
Colin

---

### Post by cwarner7_11 on 2009-11-08
Interesting thread- I just purchased a Toshiba Satellite L505-SP6984R which is Intel based, and have had no trouble loading either Ubuntu 9.04 (32-bit) and Ubuntu 9.10 (64-bit)- everything worked out of the box.  However, when running a specialized software package Salome-MECA (CAELinux), I have some graphics issues (windows don't refresh properly in certain modes).  First thought was a problem with memory swapping, but nothing is getting swapped to the swap partition, and memory usage is not stressed (3G memory).  CAELinux forum threads suggest the Intel chipsets are not the best solution for graphics for this application, but it seems I no longer have a choice.  So, trying to research how to tweak the graphics performance, I have really confused myself.  
According to Linux Graphics Drivers web page, version 2.4.0 of xf86-video-intel, released 2008-7-23, includes support of the Intel 4 Series chipset, but in the documentation, I find nothing regarding this particular chipset.
My Toshiba L505 is reportedly using a VGA compatible controller, "Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)", "Subsystem:  Toshiba America Info Systems Device ff11" (from "System Information" run on the Laptop).
According to the specification document from Toshiba, the chipset is actually a GL40 Express Chipset.  I find no documentation regarding how the various designations are related.  Is the GL40 a subset of the 4 Series set?  I find no documentation on the Linux Graphics Drivers web page mentioning either the Mobile 4 Series or the GL40 Chipset, other than the release note cited above.
Graphics information includes a note about "Graphics Media Accelerator 4500M"
Following note included as footnote to Graphics:
" Graphics (Graphics Processing Unit).
GPU performance may vary depending on product model, design configuration, applications, power management settings and features utilized. GPU performance is only optimized when operating in AC power mode and may decrease considerably when operating in battery power mode.

"Total Available Graphics Memory is the total of, as applicable, Dedicated Video Memory, System Video Memory and Shared System Memory. Shared System Memory will vary
depending on system memory size and other factors."

So, any suggestions on where to go next to figure out if I can tweak the graphics performance?  Any idea how to translate all the different hardware designators, or at least figure out what is really installed?

---

### Post by mikep554 on 2009-11-11
> **colinwhipple said:**
> I went to this site:

[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)

and one of the things they say is that if you don't know what you are doing  that is a reason NOT to attempt to compile a custom kernel.

Colin, I think the argument goes "don't compile your own kernel because you might blow up your system". I'm OK with blowing up this particular system, as it has no irreplacable data. Besides, if you follow that reasoning, no one would ever compile their first kernel.

In fact, that link you included has some pretty good instructions. I think I will try that tonight!

---

### Post by colinwhipple on 2009-11-11
Mike,

Please let us know how well it works for you. 

Colin

---

### Post by mikep554 on 2009-11-12
Sorry, but no joy. I got a bunch of errors and no .deb kernel install package.

---

### Post by colinwhipple on 2009-11-12
> **mikep554 said:**
> Sorry, but no joy. I got a bunch of errors and no .deb kernel install package.

I have found a set of karmic-specific instructions:

[http://blog.avirtualhome.com/2009/11/03/how-to-compile-a-kernel-for-ubuntu-karmic/](http://blog.avirtualhome.com/2009/11/03/how-to-compile-a-kernel-for-ubuntu-karmic/)

Colin

---

### Post by mrojas73 on 2009-11-14
> **calimancer said:**
> I have the same problem with my new Toshiba L505D-S5992 trying to install and use Kubuntu 9.10. I also had to add "acpi=off" to the Grub. In other forum found that there is a problem with DSDT.

Here is how to fix DSDT:
[http://ubuntuforums.org/showthread.php?t=1036051&page=10](http://ubuntuforums.org/showthread.php?t=1036051&page=10)

I disassemble my dsdt.dat file, recompile it with iasl and it has 4 errors:

 
[SIZE=2]/home/cali/DSDT.dsl  9164:                 Alias (^AGP.VGA.UDCS, UDSC)[/SIZE]
   [SIZE=2]Error    4064 - Object not found or not accessible from scope ^  (UDSC)[/SIZE]
     [SIZE=2]
[/SIZE]
  [SIZE=2]/home/cali/DSDT.dsl  9165:                 Alias (^AGP.VGA.LCD, PLCD)[/SIZE]
    [SIZE=2]Error    4064 - ^ Object not found or not accessible from scope (PLCD)[/SIZE]
   [SIZE=2] [/SIZE]
   [SIZE=2]/home/cali/DSDT.dsl  9166:                 Alias (^PB2.VGA.UDCS, UDS1)[/SIZE]
   [SIZE=2]Error    4064 - Object not found or not accessible from scope ^  (UDS1)[/SIZE]
   [SIZE=2] [/SIZE]
   [SIZE=2]/home/cali/DSDT.dsl  9167:                 Alias (^PB2.VGA.LCD, PLC1)[/SIZE]
   [SIZE=2][FONT=&quot][SIZE=2]Error    4064 - ^ Object not found or not accessible from scope (PLC1)
[/SIZE]
[/FONT][/SIZE][SIZE=2][FONT=&quot][/FONT][/SIZE][SIZE=2][FONT=&quot]
[/FONT][/SIZE]They are related to video but I don't know how to repair them.
My laptop came with an ATI Radeon 4200 instead the ATI Radeon 4100 that says in the specificactions.

[SIZE=2][FONT=&quot][/FONT][/SIZE]

Saludos compatriota!

---

### Post by ivanmmj on 2009-11-25
Unfortunately, I'm in the same boat with my Toshiba L505D-S5983.
The problem is only there with the AMD chipsets/IGP's.

Hope we can work together to fix this.

---

### Post by colinwhipple on 2009-11-26
Mike reported this as a bug here:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/472183](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/472183)

I don't know how the process works, but it can't hurt for others to go there and post their agreement with his post.

Colin

---

### Post by cgharty on 2009-12-04
The new kernel release 2.6.32 has fixed this problem for me. You can find deb install packages and instructions here.

[http://www.ramoonus.nl/2009/12/03/linux-kernel-2-6-32-installation-guide-for-ubuntu-linux/]("http://www.ramoonus.nl/2009/12/03/linux-kernel-2-6-32-installation-guide-for-ubuntu-linux/")

Cheers

---

### Post by magnetpest2k7 on 2009-12-05
Hello i though the new kenel release would solve my problem but it dint ifact now the video driver of my L505D-S5986 is not getting activated. Hope there is a solution . Still i have to turn off acpi=off and boot and then change in the grub file. and ofcourse there is only one processor running and complete power options disabled.

My config is amd athlon 2 M300 with ATI radon 4100

---

### Post by colinwhipple on 2009-12-06
> **cgharty said:**
> The new kernel release 2.6.32 has fixed this problem for me. You can find deb install packages and instructions here.

[http://www.ramoonus.nl/2009/12/03/linux-kernel-2-6-32-installation-guide-for-ubuntu-linux/]("http://www.ramoonus.nl/2009/12/03/linux-kernel-2-6-32-installation-guide-for-ubuntu-linux/")

Cheers

The new release did not fix it for me.  I still had to add acpi=off as a boot parameter, and then when the boot completed my wifi access didn't work.

Colin

---

### Post by cgharty on 2009-12-06
> **colinwhipple said:**
> The new release did not fix it for me.  I still had to add acpi=off as a boot parameter, and then when the boot completed my wifi access didn't work.

Colin

Sorry to hear. I will keep an eye out for any solutions or workarounds. 

Chris

---

### Post by colinwhipple on 2009-12-06
> **cgharty said:**
> Sorry to hear. I will keep an eye out for any solutions or workarounds. 

Chris

The message it comes to a halt on includes the following:

kernel_thread_helper+0x7/0x30

Colin

---

### Post by sanderd17 on 2009-12-10
I get the same with an ATI 2400 card on a toshiba P200
Do I have to report this in the bug report too?

---

### Post by Linux_Lurker on 2009-12-10
Hey guys, I just figured this one out, here's my response pasted from another thread:

*******************************************



Hello,

I've been lurking around this thread for about a month, because I have the same laptop and the same problem.  Tonight, I finally fixed my Kubuntu 9.10 install by doing this:

At boot:

Hit 'e' to edit grub, change this line:

ro  quiet splash

to look like this:

ro acpi_os_name="Windows 2006 SP1" acpi_osi="Windows 2006 SP1" pci=noacpi hpet=off  quiet splash

it now boots up with minimal fuss.  Before I was using just acpi=off, I'd get only one core running, stuck at 2ghz.  Now, both cores work, and idle at 800mhz, and the temps at the CPU are way down.

To make permanent:

sudo nano /etc/default/grub

change this line:

GRUB_CMDLINE_LINUX=""

to look like:

GRUB_CMDLINE_LINUX="acpi_os_name=\"Windows 2006 SP1\" acpi_osi=\"Windows 2006 SP1\" pci=noacpi hpet=off"

now run:

sudo update-grub

now you have a laptop that works properly.  I haven't thoroughly tested every ACPI feature, but I believe it's finally good enough, I'm not going to cry if a few ACPI functions aren't working....

---

### Post by magnetpest2k7 on 2009-12-11
Oh that was a good one both the cores are working now, but for me when I changed the grub as per you instruction my mouse is not working now!:( and i dint make a copy of my grub file can you please post a solution.

---

### Post by sanderd17 on 2009-12-11
Hibernate is'n working but at least the shutdown is normal. Although I don't want to be using windows to run linux I'll use it until a fix comes out.

---

### Post by Linux_Lurker on 2009-12-11
> **magnetpest2k7 said:**
> Oh that was a good one both the cores are working now, but for me when I changed the grub as per you instruction my mouse is not working now!:( and i dint make a copy of my grub file can you please post a solution.

The mouse not working is going to be a display driver and/or X11 thing.  I'm running the xorg-driver-fglrx driver (activated from the "proprietary drivers" dialog), what are you running?  

Here is how I got my mostly working system:

Kubuntu was installed from the 32-bit alternate install CD with acpi=off from the F6 menu

All updates were installed

ATI proprietary driver was installed from "hardware drivers"

The options in my initial post were changed.....


I also may have installed some ACPI related apps from synaptic, but I don't think those were the deal-breaker...  I can go back and figure out what they were if needed.

---

### Post by Linux_Lurker on 2009-12-12
OK, apparently I only thought the touch pad worked(I always use a USB mouse, I hate touchpads), although I will see what can be done to fix it...

Something else to note:  Installing the 2.6.32 kernel might fix some of the issues, there were a few commits to /drivers/acpi/pci_root.c that were supposed to fix some of this stuff.  I however, had nothing but trouble with those kernels when I tried to either compile my own, or use the one from the Ubuntu Kernel team...

EDIT:  Oh, I almost forgot:  apparently the hpet=off isn't necessary, I'd leave that part out.  I'm also going to do some more research to see if there's a better option than "Windows 2006 SP1" for the acpi OS spoofing.

---

### Post by magnetpest2k7 on 2009-12-12
thank you @linux_lurker

I doubt whether kernel 2.6.32 solves any problem. It has not recogonized the display ATI driver and when i go and activate display driver from proprietary drivers it dosent get activated in ubuntu with kernel 2.6.32. by the way I am running 64bit ubuntu karmic 9.10

---

### Post by magnetpest2k7 on 2009-12-12
I find just adding pci=noacpi makes the 2 processor work. but again my mouse doesn't work. hence quiet splash pci=noacpi will solve the problem but I dont know what to do if got to make my laptop mouse pad working.

---

### Post by Linux_Lurker on 2009-12-13
I thought for sure that the obscure:

i8042.noacpi=1

boot switch would fix this, but apparently not...

I tried a ton of different boot switches, but nothing but acpi=off made the touchpad work.  If anybody else wants to pursue this, I'd try using pci=noacpi, in combination with every other X=noacpi switch you can find, surely disabling some other part of ACPI would fix the touchpad...

---

### Post by seenthelite on 2009-12-17
Same problems on Toshiba P500 PSPG8A.

---

### Post by colinwhipple on 2009-12-21
I tried booting from the alpha of the next Ubuntu version, Lucid Lynx, on my L505D-S5983, but no joy.  I had to use the acpi=off option to get it to boot up.

Colin

---

### Post by Linux_Lurker on 2009-12-23
Just a quick update:

A few minor quirks were fixed by changing the acpi osi/osname to "Windows 2001".

Also, boot-up and shutdown were smoothed out considerably by adding:

pci=assign-busses   (it seems to circumvent a few pauses in the boot process, probably because of hardware errors and timeouts)

, and last but not least, they made it 3gb of ram by mismatching a 1gb and 2gb stick of ram, since my gf has the same laptop, I traded my 1gb stick for her 2gb stick, and now both laptops have snappier performance(she doesn't begin to use 2gb of ram, much less 3gb).

There were some toshiba laptop specific acpi fixes in the latest kernel, although I haven't tried it out yet.

Finally, I've gotten 32bit and 64bit Ubuntu and 32bit Kubuntu all running well enough, but 32bit Ubuntu wins for best/most reliable performance.

---

### Post by colinwhipple on 2009-12-24
> **Linux_Lurker said:**
> Just a quick update:

A few minor quirks were fixed by changing the acpi osi/osname to "Windows 2001".

Also, boot-up and shutdown were smoothed out considerably by adding:

pci=assign-busses   (it seems to circumvent a few pauses in the boot process, probably because of hardware errors and timeouts)

, and last but not least, they made it 3gb of ram by mismatching a 1gb and 2gb stick of ram, since my gf has the same laptop, I traded my 1gb stick for her 2gb stick, and now both laptops have snappier performance(she doesn't begin to use 2gb of ram, much less 3gb).

There were some toshiba laptop specific acpi fixes in the latest kernel, although I haven't tried it out yet.

Finally, I've gotten 32bit and 64bit Ubuntu and 32bit Kubuntu all running well enough, but 32bit Ubuntu wins for best/most reliable performance.

Lurker,

Is the "pci=assign-busses" in addition to or instead of the "pci=noacpi" you previously recommended?  I don't know if these settings are exclusive or can work together.

Colin

---

### Post by colinwhipple on 2009-12-24
I have been trying some of the new kernels:

2.6.32
2.6.32.2
2.6.33-rc1

obtained from here:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

with no success.  The only way I can get the boot to finish is with the acpi=off option, but then I can't get a wifi connection.

Colin

---

### Post by Linux_Lurker on 2009-12-24
Colin:

pci=assign-busses is in addition to pci=noacpi.  Startup and shutdown are lightning fast now, shutdown takes about literally 5 seconds, it's impressive.


As far as wifi, try changing your router settings, I've had no problems with my wifi.  I don't use encryption, I just turn off the SSID broadcast, so the name of the network becomes the password(I also use a MAC address table).  I've always found the stronger encryption to be problematic in Linux.

---

### Post by Linux_Lurker on 2009-12-24
Oh, here's my explanation of those:

pci=noacpi means:  do not use acpi for assigning pci IRQs

pci=assign-busses:  kernel will override any IRQ assignments done by the firmware


Currently, I can't get my touchpad or the software battery meters to work, but other than that, everything is fine.

Performance was somewhat increased by installing cpufreq-utils from the repository, and then converting these 2 rpm packages to deb packages using sudo alien -k [filename]

[http://support.amd.com/us/Pages/dynamicDetails.aspx?ListID=c5cd2c08-1432-4756-aafa-4d9dc646342f&ItemID=188](http://support.amd.com/us/Pages/dynamicDetails.aspx?ListID=c5cd2c08-1432-4756-aafa-4d9dc646342f&ItemID=188)

[http://support.amd.com/us/Pages/dynamicDetails.aspx?ListID=c5cd2c08-1432-4756-aafa-4d9dc646342f&ItemID=101](http://support.amd.com/us/Pages/dynamicDetails.aspx?ListID=c5cd2c08-1432-4756-aafa-4d9dc646342f&ItemID=101)

It seems to do a better job now of ramping up to 2ghz when you're actually doing something, 2d webpage scrolling and 3d compiz effects are both smoother.  I can currently run a full-on compiz desktop without any issues, at acceptable FPS.

---

### Post by Linux_Lurker on 2009-12-24
> **colinwhipple said:**
> I have been trying some of the new kernels:

2.6.32
2.6.32.2
2.6.33-rc1

obtained from here:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/")

with no success.  The only way I can get the boot to finish is with the acpi=off option, but then I can't get a wifi connection.

Colin

One more final thought, I see this kernel driver and kernel driver patch on AMD's website. 

[http://support.amd.com/us/Pages/dynamicDetails.aspx?ListID=c65b1ad6-e123-482e-a417-2d39f6e728d2&ItemID=25](http://support.amd.com/us/Pages/dynamicDetails.aspx?ListID=c65b1ad6-e123-482e-a417-2d39f6e728d2&ItemID=25)

[http://support.amd.com/us/Pages/dynamicDetails.aspx?ListID=c65b1ad6-e123-482e-a417-2d39f6e728d2&ItemID=26](http://support.amd.com/us/Pages/dynamicDetails.aspx?ListID=c65b1ad6-e123-482e-a417-2d39f6e728d2&ItemID=26)

I have no idea if it's already present in the kernel or not.  The one is a patch file against a much older kernel, so you'd probably have to dig up that kernel, patch, and then add the patched source file to the new kernel(unless it's already in the kernel?).  It's alot of work to check/implement/compile a custom kernel with custom patches, and it still may not fix the problem, but after a quick browsing through the source code, it looks extremely relevant to the problem with this laptop.  Just to clarify for everyone:  ACPI itself is NOT the problem, it's conflicts in the PCI bus, whenever ACPI attempts to route the video card's bus.

Also, I wonder if OpenSUSE would do any better?  AFAIK, pci=noapci would still be necessary to boot, however, OpenSUSE is sponsored by AMD, so I would certainly expect AMD hardware to be well supported.

---

### Post by colinwhipple on 2009-12-31
I have tried several other distros, including SUSE, Fedora, and Mandriva.  Ubuntu works the best with my Toshiba L505D-S5983.  Some of the others, Fedora 12 for example, won't even boot to a desktop for me.  Fedora 11 will, using the pci=noacpi boot option, but not Fedora 12.

Colin

---

### Post by Linux_Lurker on 2009-12-31
> **colinwhipple said:**
> I have tried several other distros, including SUSE, Fedora, and Mandriva.  Ubuntu works the best with my Toshiba L505D-S5983.  Some of the others, Fedora 12 for example, won't even boot to a desktop for me.  Fedora 11 will, using the pci=noacpi boot option, but not Fedora 12.

Colin

Thanks for trying out the other distros, I assume this will eventually have a fix in the kernel, probably by the time Lucid is released.

---

### Post by colinwhipple on 2010-01-03
I have a problem with recovering from Sleep mode.  My Power Management options are to put the computer to Sleep when it is inactive for 2 hours.  When I come back to the computer, the middle light of the three in front is blinking amber.  Opening the lid, moving the mouse or pressing a key has no effect.  Pressing the power button briefly causes the amber light to change to steady green, and there is a short sound like the hard drive is powering up, but nothing else.  The computer is nonresponsive to the mouse and keyboard and the screen remains blank.  Even pressing the numlock and capslock keys does not change those toggle lights.

My only choice seems to be to hold down the power button so the computer restarts.

My boot options are as follows:

acpi_os_name="Windows 2001" acpi_osi="Windows 2001" pci=noacpi pci=assign-busses

Any ideas?  Not shutting down properly is not a good idea in the long run.

My system is a Satellite L505D-S5983.

Colin

---

### Post by ivanmmj on 2010-01-07
> **Linux_Lurker said:**
> Hey guys, I just figured this one out, here's my response pasted from another thread:

*******************************************



Hello,

I've been lurking around this thread for about a month, because I have the same laptop and the same problem.  Tonight, I finally fixed my Kubuntu 9.10 install by doing this:

At boot:

Hit 'e' to edit grub, change this line:

ro  quiet splash

to look like this:

ro acpi_os_name="Windows 2006 SP1" acpi_osi="Windows 2006 SP1" pci=noacpi hpet=off  quiet splash

it now boots up with minimal fuss.  Before I was using just acpi=off, I'd get only one core running, stuck at 2ghz.  Now, both cores work, and idle at 800mhz, and the temps at the CPU are way down.

To make permanent:

sudo nano /etc/default/grub

change this line:

GRUB_CMDLINE_LINUX=""

to look like:

GRUB_CMDLINE_LINUX="acpi_os_name=\"Windows 2006 SP1\" acpi_osi=\"Windows 2006 SP1\" pci=noacpi hpet=off"

now run:

sudo update-grub

now you have a laptop that works properly.  I haven't thoroughly tested every ACPI feature, but I believe it's finally good enough, I'm not going to cry if a few ACPI functions aren't working....
This worked fine with 9.10 (well.... as fine as it could while still having ACPI issues) but now with 10.04 I'm back to only acpi=off working.

---

### Post by Linux_Lurker on 2010-01-09
Colin:   I never use sleep mode, all of my normal starting-up/shutting-down works well, but I've never been a fan of sleep mode, so I don't have any good advice for troubleshooting it.

Ivan:  Lucid hasn't worked out very well for me, I probably won't try again until closer to release time.


All:  I think the very latest kernel may have a fix:

commit e93166f10c741f247c7e172936811bad558b4135
Author: Joerg Roedel <joerg.roedel@amd.com>
Date:   Mon Dec 21 15:51:23 2009 +0100

    x86/amd-iommu: Fix initialization failure panic
    
    commit 0f764806438d5576ac58898332e5dcf30bb8a679 upstream.
    
    The assumption that acpi_table_parse passes the return value
    of the hanlder function to the caller proved wrong
    recently. The return value of the handler function is
    totally ignored. This makes the initialization code for AMD
    IOMMU buggy in a way that could cause a kernel panic on
    initialization. This patch fixes the issue in the AMD IOMMU
    driver.
    
    Signed-off-by: Joerg Roedel <joerg.roedel@amd.com>
    Signed-off-by: Greg Kroah-Hartman <gregkh@suse.de>




I haven't yet tried to compile my own, but I'd love to say that I think that may
be our problem.

---

### Post by colinwhipple on 2010-01-09
> **Linux_Lurker said:**
> Colin:   I never use sleep mode, all of my normal starting-up/shutting-down works well, but I've never been a fan of sleep mode, so I don't have any good advice for troubleshooting it.

Ivan:  Lucid hasn't worked out very well for me, I probably won't try again until closer to release time.


All:  I think the very latest kernel may have a fix:

commit e93166f10c741f247c7e172936811bad558b4135
Author: Joerg Roedel <joerg.roedel@amd.com>
Date:   Mon Dec 21 15:51:23 2009 +0100

    x86/amd-iommu: Fix initialization failure panic
    
    commit 0f764806438d5576ac58898332e5dcf30bb8a679 upstream.
    
    The assumption that acpi_table_parse passes the return value
    of the hanlder function to the caller proved wrong
    recently. The return value of the handler function is
    totally ignored. This makes the initialization code for AMD
    IOMMU buggy in a way that could cause a kernel panic on
    initialization. This patch fixes the issue in the AMD IOMMU
    driver.
    
    Signed-off-by: Joerg Roedel <joerg.roedel@amd.com>
    Signed-off-by: Greg Kroah-Hartman <gregkh@suse.de>




I haven't yet tried to compile my own, but I'd love to say that I think that may
be our problem.

When you say "latest kernel" do you mean Lucid Lynx or a Karmic 2.6.33-xx update?

Colin

---

### Post by Linux_Lurker on 2010-01-09
This one right here:

[http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.32.3.tar.bz2](http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.32.3.tar.bz2)

---

### Post by colinwhipple on 2010-01-09
> **Linux_Lurker said:**
> This one right here:

[http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.32.3.tar.bz2](http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.32.3.tar.bz2)

I had downloaded and installed from here:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32.3/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32.3/)

Is there an advantage to compiling from source on my own system (which I have never done)?

Colin

---

### Post by Linux_Lurker on 2010-01-09
> **colinwhipple said:**
> I had downloaded and installed from here:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32.3/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.32.3/")



Well, that would certainly be easier, wouldn't it?  :D

> **colinwhipple said:**
> 
Is there an advantage to compiling from source on my own system (which I have never done)?


Not really(unless you have a good reason to), when you compile it yourself, it is missing any Ubuntu-specific packages that the Ubuntu devs included.  It's not too hard, but it takes a long time, even on a fast machine, and you generally need to answer a whole bunch of questions that you may not know the answer to.  I already started compiling(on my Phenom II 940BE desktop, laptops get HOT when you try to do something like that), but I also just DLed the Ubuntu version, I guess I'll try both.

So, did that fix anything?  Did you try it without any boot switches?

PS:  If you wanted to roll your own kernel, it'd go like:

sudo apt-get install kernel-package fakeroot build-essential ncurses-dev
Download source
Extract tarball
cd [kernel source directory]
make oldconfig
//answer a buttload of questions
make menuconfig

//this will take a loooooonnnnngggggg time
 CONCURRENCY_LEVEL=4 fakeroot make-kpkg --initrd --append-to-version=-custom kernel_image kernel_headers
//4 is the number of cores on my desktop's CPU, change as needed for your machine

cd ..; ls

//install the kernel
sudo dpkg -i [image.deb]; sudo dpkg -i [headers.deb]

---

### Post by colinwhipple on 2010-01-09
> **Linux_Lurker said:**
> Well, that would certainly be easier, wouldn't it?  :D

So, did that fix anything?  Did you try it without any boot switches?

....



I tried the download of the prebuilt kernel, and got an error message about:

...kernel_thread_helper...

I get that kind of message with your additional boot options and without any.  With acpi=off I can boot it up.

Colin

---

### Post by Linux_Lurker on 2010-01-09
> **colinwhipple said:**
> I tried the download of the prebuilt kernel, and got an error message about:

...kernel_thread_helper...

I get that kind of message with your additional boot options and without any.  With acpi=off I can boot it up.

Colin

Same here.  I only tried the Ubuntu pre-compiled kernel, I doubt the kernel I compiled would do any better.  If you can hunt down a Ubuntu 2.6.31.11 kernel, that may help.  AFAIK, that particular commit isn't included in the 2.6.31 kernel series yet, but after reading the .9/.10 changelogs, that same AMD kernel dev has been doing tonnes of commits around IOMMU, ACPI, etc...

---

### Post by colinwhipple on 2010-01-09
> **Linux_Lurker said:**
> Same here.  I only tried the Ubuntu pre-compiled kernel, I doubt the kernel I compiled would do any better.  If you can hunt down a Ubuntu 2.6.31.11 kernel, that may help.  AFAIK, that particular commit isn't included in the 2.6.31 kernel series yet, but after reading the .9/.10 changelogs, that same AMD kernel dev has been doing tonnes of commits around IOMMU, ACPI, etc...

No joy with 2.6.31.11.  With no boot options it takes a long time to get to a text mode login.  Then after logging in I do a "startx", and end up with a blank screen.

With these boot options:

acpi_os_name="Windows 2001" acpi_osi="Windows 2001" pci=noacpi pci=assign-busses 

It gets to the Gnome desktop, but WiFi doesn't work.  A wired connection does work, which is what I am using now.

Colin

---

### Post by Linux_Lurker on 2010-01-16
I'm not sure if this kernel corresponds to any of the kernels that Colin tried, but, I enabled pre-release updates in software-sources, and there is a new kernel in the pipe called

linux-headers-2.6.31.18-generic-pae(yours may not be pae, the pae is only installed if you have ~4gb or more of ram).

I see the following patches from Ubuntu devs in the release notes:

  * ACPI / PCI: Fix NULL pointer dereference in acpi_get_pci_dev() (rev. 2)
    - LP: #480144

  * ACPI: Clarify resource conflict message

  * ACPI video: ignore buggy _BQC

  * ACPI video: work-around BIOS AML bug in _BQC
    - LP: #428910

  * [Upstream] acpi: video: Loosen strictness of video bus detection code
    - LP: #333386

  * usb: amd5536udc: fixed shared interrupt bug and warning oops
    - LP: #494633

  * x86/amd-iommu: attach devices to pre-allocated domains early
    - LP: #503430

  * x86/amd-iommu: un__init iommu_setup_msi
    - LP: #503430

  * x86, apic: Enable lapic nmi watchdog on AMD Family 11h
    - LP: #503430

  * x86/amd-iommu: Workaround for erratum 63
    - LP: #480144

  * x86/amd-iommu: Un__init function required on shutdown
    - LP: #480144

  * x86/amd-iommu: fix broken check in amd_iommu_flush_all_devices



It looks like any number of those could fix the problem.  I won't have time to try it this weekend, but it's just a matter of enabling pre-release updates in software-sources, and then running update-manager if anyone else wants to try.

---

### Post by colinwhipple on 2010-01-16
Lurker,

Thanks, but it's the same-old.  I need the boot options for it to work.

Colin

---

### Post by kingofnerds on 2010-01-19
I was able to get my L505D-S5983 working properly by compiliing a patch into my kernel to copy the dsdt table at the beginning of the boot process before the bios has  a chance to re-write it. Everything works including the touchpad and battery meter.  currently, I only have linux installed on a 16gb flash drive, but I am preparing to install onto a hard drive partition.  I am using Linux Mint 8 with my custom kernel package.  I will put the package on my ftp server in a little whlie and put a link here. Although I only have an 800k upload speed right now, I figure, perhaps someone with a little more bandwidth could host it later. 

The patch I added to my kernel is from the following link:
[http://bugzilla.kernel.org/attachment.cgi?id=23958](http://bugzilla.kernel.org/attachment.cgi?id=23958)
[http://bugzilla.kernel.org/show_bug.cgi?id=14679](http://bugzilla.kernel.org/show_bug.cgi?id=14679), the bug has not had anything done on it since december, but the patch still works.

---

### Post by newbie84 on 2010-01-19
> **kingofnerds said:**
> I was able to get my L505D-S5983 working properly by compiliing a patch into my kernel to copy the dsdt table at the beginning of the boot process before the bios has  a chance to re-write it. Everything works including the touchpad and battery meter.  currently, I only have linux installed on a 16gb flash drive, but I am preparing to install onto a hard drive partition.  I am using Linux Mint 8 with my custom kernel package.  I will put the package on my ftp server in a little whlie and put a link here. Although I only have an 800k upload speed right now, I figure, perhaps someone with a little more bandwidth could host it later. 

The patch I added to my kernel is from the following link:
[http://bugzilla.kernel.org/attachment.cgi?id=23958](http://bugzilla.kernel.org/attachment.cgi?id=23958)
[http://bugzilla.kernel.org/show_bug.cgi?id=14679](http://bugzilla.kernel.org/show_bug.cgi?id=14679), the bug has not had anything done on it since december, but the patch still works.

 Please give us a link of your custom linux kernel when you upload it.  
 Please elaborate how to apply patches.  
 Thank you very much.

---

### Post by ivanmmj on 2010-01-19
Sweet. Going to try compiling it. Patching it now. (Building it on 10.04 and also patching it with BFS just to test that out, too. Not for this problem, but still...)


EDIT: The Patch command is hanging with either this patch or the BFS patch and isn't doing anything... :-/

haha, my fault.. I know why it wasn't working... It's too embarrassing to say...

---

### Post by ivanmmj on 2010-01-19
That didn't work.
Maybe I did something wrong...

EDIT: 2.6.32 doesn't work with either the patch nor the kernel switches. I'm going to try it again with the latest 2.6.31 kernel.


EDIT2: 9.10 with 2.6.31.12
 with the patch DOES work. (Didn't try BFS this time.)

---

### Post by kingofnerds on 2010-01-20
Yeah, I was using the 2.6.31 kernel for my linux mint. I have not yet managed to get it onto my ftp server yet, but when I do, I will put the link here. Mint 8 is based off of ubuntu 9.10, so the kernel package may work for that version as well.

I had never patched a kernel before, but from reading that bug release, it is the only solution that I could find. I am not sure if i can find the documents that I used for the patching, and the compiling, but I did modify the directions in my head a little as I performed them.

---

### Post by ivanmmj on 2010-01-20
I tried it again, this time on a 2.6.32 kernel and it worked just as well as it did on the 2.6.31. It's all working properly. It can even see my battery.

---

### Post by colinwhipple on 2010-01-20
I would like to try doing a kernel patch to solve this problem, but the instructions I can find on the Internet leave me confused.  If someone can point me to clear step-by-step instructions, I would be most appreciative.

Colin

---

### Post by ivanmmj on 2010-01-20
OK, 10.04 works fine with the patch, also.

I'll try to upload them and post them here. (If I can find somewhere that will hold something that massive.) If not, I'll try to write up a walkthrough on how to compile your own kernel with the patch.

---

### Post by kingofnerds on 2010-01-20
I finally got my kernel for linux mint that I made onto my ftp server, the url is [ftp://kingofnerds.servemp3.com/kernels/](ftp://kingofnerds.servemp3.com/kernels/)

Remember I don't have a very fast upload speed, so it will take a while to download.

---

### Post by colinwhipple on 2010-01-20
> **kingofnerds said:**
> I finally got my kernel for linux mint that I made onto my ftp server, the url is [ftp://kingofnerds.servemp3.com/kernels/](ftp://kingofnerds.servemp3.com/kernels/)

Remember I don't have a very fast upload speed, so it will take a while to download.

Thanks.

In the past when I have installed a kernel, there has been a headers...all and a headers...i386.

Is the headers...all not necessary?

Colin

---

### Post by ivanmmj on 2010-01-20
Here's a quick walkthrough on how to compile your own:

(But the one posted above should work fine for all ubuntu 9.10 based systems.)


Right click on [http://bugzilla.kernel.org/attachment.cgi?id=23958]("http://bugzilla.kernel.org/attachment.cgi?id=23958") and save it to your desktop.

```
sudo -s
apt-get update
apt-get install kernel-package libncurses5-dev fakeroot wget bzip2
cd /usr/src
```

For 9.10:
```
wget http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.31.12.tar.bz2
tar xjf linux-2.6.31.12.tar.bz2
ln -s linux-2.6.31.12 linux
```

For 10.04
```
wget http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.32.4.tar.bz2
tar xjf linux-2.6.32.4.tar.bz2
ln -s linux-2.6.32.4 linux
```

```

cd /usr/src/linux
patch -p1 < ~/Desktop/bug14679_copy_dsdt.patch
cp /boot/config-`uname -r` ./.config 
make menuconfig
```
NOTE: That's p1 as in the number ONE, not a lower case L.
-Load an Alternate Configuration File
-Hit OK
-Exit
-Hit Yes

```
make-kpkg clean
fakeroot make-kpkg --initrd --append-to-version=-l505d kernel_image kernel_headers
cd /usr/src
ls -l
nautilus /usr/src
```

Then install both deb files in there.

Make sure that you remove any extra Grub kernel switches you've added.

---

### Post by raven920 on 2010-01-20
It works! Thank you very much for the compiling guide, it really works!, right now I'm installing the graphics driver, when I finish doing I'll upload my own build to a faster server than the given before (:P)

---

### Post by Linux_Lurker on 2010-01-20
Brilliant! (although I've not had a chance to try it).  I'll see if I can get us a kernel uploaded.

---

### Post by Linux_Lurker on 2010-01-20
OK, I did get it working, but I screwed up my kernel compile.  Basically, I ran

sudo apt-get install git-core kexec-tools makedumpfile crash libncurses5 libncurses5-dev

(BTW, I already had most of the other dependencies installed, I don't remember what all they are, sorry)


 cloned the Ubuntu source GIT tree with 

cd [my kernel source directory]

git clone git://kernel.ubuntu.com/ubuntu/ubuntu-karmic.git karmic

cd Karmic

git tag | grep Ubuntu*

cd [appropriate kernel version from last command]

git checkout Ubuntu-2.6.31-17.54 -b ACPIfix

Ubuntu-2.6.31-17.54cp /boot/config-$(uname -r) .

cp /boot/config-$(uname -r) .

patch -p1 < ~/Desktop/bug14679_copy_dsdt.patch

make menuconfig

[made some changes/optimizations for AMD CPU...]

make-kpkg clean

git add .

git commit -a -m "L505d modifications"

//Note:  I picked 4 because I did this on my quad-core desktop, choose 2 for a 
//dual-core
 CONCURRENCY_LEVEL=4 fakeroot make-kpkg --initrd --append-to-version=-l505d kernel_image kernel_headers


To make 2 .deb packages.  However, I think I ****** up a couple of options, you should be able to compile to a much smaller package, but I'm not sure how(more like 60mb instead of 400mb).  I don't have much experience compiling Ubuntu kernels, usually I just compile vanilla kernels from kernel.org.  If somebody knows how to compile a Ubuntu kernel minus all of the extra stuff, please let me know, and I'll try to get a smaller kernel .deb uploaded.

---

### Post by colinwhipple on 2010-01-21
ivanmmj:

Thanks.  It is working for me.

Colin

---

### Post by ivanmmj on 2010-01-21
I decided to  mess around with the kernel and created a small kernel (30mb) package that works and is FAST... It's set up with no debugging, compiled to use AMD instructions, etc etc...

Anyone want a copy of it? (It's for 10.04, though, as it's based off the 2.6.32 kernel.)

---

### Post by colinwhipple on 2010-01-21
> **ivanmmj said:**
> I decided to  mess around with the kernel and created a small kernel (30mb) package that works and is FAST... It's set up with no debugging, compiled to use AMD instructions, etc etc...

Anyone want a copy of it? (It's for 10.04, though, as it's based off the 2.6.32 kernel.)

I would like to have it.

Colin

---

### Post by colinwhipple on 2010-01-21
Power management is working better for me with the kernel compiled using ivanmmj's instructions.

Colin

---

### Post by ivanmmj on 2010-01-21
[http://justkitchen.info/kernel/linux-headers-2.6.32-l505d-speed_2.6.32-l505d-speed-10.00.Custom_amd64.deb](http://justkitchen.info/kernel/linux-headers-2.6.32-l505d-speed_2.6.32-l505d-speed-10.00.Custom_amd64.deb)
[http://justkitchen.info/kernel/linux-image-2.6.32-l505d-speed_2.6.32-l505d-speed-10.00.Custom_amd64.deb](http://justkitchen.info/kernel/linux-image-2.6.32-l505d-speed_2.6.32-l505d-speed-10.00.Custom_amd64.deb)


There you go.

---

### Post by paxster on 2010-01-21
Could someone post a quick install to kernel patch guide for this? I've been wanting to install Ubuntu on my new laptop (L505-S5983) but am wary without the full picture...
Thanks in advance.

---

### Post by Linux_Lurker on 2010-01-21
> **ivanmmj said:**
> [http://justkitchen.info/kernel/linux-headers-2.6.32-l505d-speed_2.6.32-l505d-speed-10.00.Custom_amd64.deb](http://justkitchen.info/kernel/linux-headers-2.6.32-l505d-speed_2.6.32-l505d-speed-10.00.Custom_amd64.deb)
[http://justkitchen.info/kernel/linux-image-2.6.32-l505d-speed_2.6.32-l505d-speed-10.00.Custom_amd64.deb](http://justkitchen.info/kernel/linux-image-2.6.32-l505d-speed_2.6.32-l505d-speed-10.00.Custom_amd64.deb)


There you go.

Awesome.  If you have time, could you possibly upload some x86 kernel packages too?  Thanks again.

---

### Post by ivanmmj on 2010-01-21
> **paxster said:**
> Could someone post a quick install to kernel patch guide for this? I've been wanting to install Ubuntu on my new laptop (L505-S5983) but am wary without the full picture...
Thanks in advance.

Press F6 at the beginning.
Choose ACPI=off.
Boot.
Install.
Boot into the hard disk.
Install my DEB files.
Open up the terminal.
```
sudo nano /etc/default/grub
```
Change GRUB_CMDLINE_LINUX back to nothing so you get:
```
GRUB_CMDLINE_LINUX=""
```
Restart. Done.

That's the easiest way to do it without having to compile the kernel from scratch. If not, then substitute the "install my deb files" for the walkthrough that I created earlier.


> **Linux_Lurker said:**
> Awesome.  If you have time, could you possibly upload some x86 kernel packages too?  Thanks again.

I'll see if I can get some time later tomorrow. Do you want it in 9.10 format (2.6.31) or 10.04 format (2.6.32)?

---

### Post by paxster on 2010-01-21
> **ivanmmj said:**
> Press F6 at the beginning.
Choose ACPI=off.
Boot.
Install.
Boot into the hard disk.
Install my DEB files.
Open up the terminal.
```
sudo nano /etc/default/grub
```
Change GRUB_CMDLINE_LINUX back to nothing so you get:
```
GRUB_CMDLINE_LINUX=""
```
Restart. Done.

That's the easiest way to do it without having to compile the kernel from scratch. If not, then substitute the "install my deb files" for the walkthrough that I created earlier.

perfect! thank you.
I like to say I know just enough to make myself dangerous...

---

### Post by colinwhipple on 2010-01-22
> **ivanmmj said:**
> [http://justkitchen.info/kernel/linux-headers-2.6.32-l505d-speed_2.6.32-l505d-speed-10.00.Custom_amd64.deb](http://justkitchen.info/kernel/linux-headers-2.6.32-l505d-speed_2.6.32-l505d-speed-10.00.Custom_amd64.deb)
[http://justkitchen.info/kernel/linux-image-2.6.32-l505d-speed_2.6.32-l505d-speed-10.00.Custom_amd64.deb](http://justkitchen.info/kernel/linux-image-2.6.32-l505d-speed_2.6.32-l505d-speed-10.00.Custom_amd64.deb)


There you go.

These also work for me.  Thanks.

Colin

---

### Post by Linux_Lurker on 2010-01-23
> **ivanmmj said:**
> 
I'll see if I can get some time later tomorrow. Do you want it in 9.10 format (2.6.31) or 10.04 format (2.6.32)?

9.10, please.  Also, if you don't mind, I'd like to know how you did it, for future reference...

---

### Post by ivanmmj on 2010-01-24
> **Linux_Lurker said:**
> 9.10, please.  Also, if you don't mind, I'd like to know how you did it, for future reference...

The speed up? Or the fix for the ACPI?

---

### Post by Linux_Lurker on 2010-01-25
> **ivanmmj said:**
> The speed up? Or the fix for the ACPI?

I was referring to getting the kernel to compile to ~30mb instead of the ~400mb that it compiles to by default.    I haven't even been able to google that one....

---

### Post by ivanmmj on 2010-01-26
> **Linux_Lurker said:**
> I was referring to getting the kernel to compile to ~30mb instead of the ~400mb that it compiles to by default.    I haven't even been able to google that one....

Oh, just disable all the kernel hacking stuff (it's all debugging stuff.)

I created a new patched kernel:
Updated to 2.6.32.6
Still patched with ACPI
Patched to use the BFScheduler instead of the standard scheduler.

I'll see how that runs for a few days and report back.

As far as building x86 kernels, I need to do a little research. I've always failed at cross-platform compiling of kernels.

---

### Post by Linux_Lurker on 2010-01-26
Awesome, I'll get an x86 kernel compiled and uploaded some time this week.  Thanks.

---

### Post by Linux_Lurker on 2010-01-28
Here is an x86 version:

[http://www.sendspace.com/file/qpa732](http://www.sendspace.com/file/qpa732)

---

### Post by paxster on 2010-01-29
> **Linux_Lurker said:**
> Here is an x86 version:

[http://www.sendspace.com/file/qpa732](http://www.sendspace.com/file/qpa732)

Is this x86 and 9.10?

---

### Post by newbie84 on 2010-01-29
> **Linux_Lurker said:**
> Here is an x86 version:

[http://www.sendspace.com/file/qpa732](http://www.sendspace.com/file/qpa732)

  Do you have an x86_64 version for kernel 2.6.31 ?

---

### Post by Linux_Lurker on 2010-01-29
Sorry, I should've clarified:

It is the Ubuntu 9.10 kernel source (latest released kernel) with the patch, and I've removed the kernel hacking stuff, as well as some unnecessary drivers.

newbie:  I don't have an x64 version for 2.6.31, I thought Ivan had already uploaded one earlier?  I thought he uploaded a 32 and a 31 version...

---

### Post by Linux_Lurker on 2010-01-29
> **Linux_Lurker said:**
> 
I thought he uploaded a 32 and a 31 version...

Nevermind, I was wrong...  Somebody with an x64 system should do it, after a little research, apparently cross-compiling is a bit unreliable..


Also, is anybody else running the new Catalyst 10.1 drivers?  Compiz performance went from ~30fps to ~20fps....

---

### Post by colinwhipple on 2010-01-29
> **Linux_Lurker said:**
> Sorry, I should've clarified:

It is the Ubuntu 9.10 kernel source (latest released kernel) with the patch, and I've removed the kernel hacking stuff, as well as some unnecessary drivers.

newbie:  I don't have an x64 version for 2.6.31, I thought Ivan had already uploaded one earlier?  I thought he uploaded a 32 and a 31 version...

Please tell us what the removal process was.

Colin

---

### Post by Linux_Lurker on 2010-01-29
The removal process is:

cd into the kernel source directory
make oldconfig
make menuconfig

[go remove all of the stuff under "kernel hacking", then go into the various driver directories and remove drivers for devices not present in your hardware]

make-kpkg clean




FYI, there is a horrible performance regression in the Catalyst 10.1 driver, uninstalling and reinstalling 9.12 made it go from max ~20fps, min 15fps to max 60fps, min 30fps...

---

### Post by ivanmmj on 2010-02-04
I'll compile a x86_64 2.6.31. Give me a few hours. (At work.)

---

### Post by ivanmmj on 2010-02-04
[http://justkitchen.info/kernel/linux-image-2.6.31.12-l505d-nodebug_2.6.31.12-l505d-nodebug-10.00.Custom_amd64.deb](http://justkitchen.info/kernel/linux-image-2.6.31.12-l505d-nodebug_2.6.31.12-l505d-nodebug-10.00.Custom_amd64.deb)
[http://justkitchen.info/kernel/linux-headers-2.6.31.12-l505d-nodebug_2.6.31.12-l505d-nodebug-10.00.Custom_amd64.deb](http://justkitchen.info/kernel/linux-headers-2.6.31.12-l505d-nodebug_2.6.31.12-l505d-nodebug-10.00.Custom_amd64.deb)

Ask and thou shall recieve.
2.6.31.12 with the ACPI patch and the kernel debugging disabled.

---

### Post by colinwhipple on 2010-02-06
> **ivanmmj said:**
> I'll compile a x86_64 2.6.31. Give me a few hours. (At work.)

Am I correct in thinking that to compile an AMD64 kernel I basically just need to do the compile procedure on a running AMD64 system?  So I download an AMD64 kernel, use acpi=off as a boot option (or the more complex options that Lurker indicated) and then do the compile procedure that Ivan gave us, and I will end up with my own AMD64 kernel on my L505D-S5983?

Colin

---

### Post by ivanmmj on 2010-02-06
> **colinwhipple said:**
> Am I correct in thinking that to compile an AMD64 kernel I basically just need to do the compile procedure on a running AMD64 system?  So I download an AMD64 kernel, use acpi=off as a boot option (or the more complex options that Lurker indicated) and then do the compile procedure that Ivan gave us, and I will end up with my own AMD64 kernel on my L505D-S5983?

Colin

Yes

---

### Post by colinwhipple on 2010-02-06
> **ivanmmj said:**
> Yes

Thanks.  That seems to have worked.  Now I have a self-compiled 64-bit kernel running in its own partition.

Colin

---

### Post by colinwhipple on 2010-02-07
> **Linux_Lurker said:**
> The removal process is:

cd into the kernel source directory
make oldconfig
make menuconfig

[go remove all of the stuff under "kernel hacking", then go into the various driver directories and remove drivers for devices not present in your hardware]

make-kpkg clean



There is a step in Ivan's kerrnel compile instructions to "Load an Alternate Configuration File".  I guess you do that BEFORE removing the kernel hacking stuff?

Colin

---

### Post by ivanmmj on 2010-02-07
> **colinwhipple said:**
> There is a step in Ivan's kerrnel compile instructions to "Load an Alternate Configuration File".  I guess you do that BEFORE removing the kernel hacking stuff?

Colin

Correct. First you load up the configuration THEN you make the changes to it.

---

### Post by colinwhipple on 2010-02-07
Thanks.

I get a lot of messages during the compilation.  The most common one is about frame sizes exceeding 1024 bytes.

I have no idea how big a problem that is.

Colin

---

### Post by Linux_Lurker on 2010-02-07
> **colinwhipple said:**
> Thanks.

I get a lot of messages during the compilation.  The most common one is about frame sizes exceeding 1024 bytes.

I have no idea how big a problem that is.

Colin

That's nothing to worry about, warnings aren't a big deal as long as they don't break something.

In regards to the configuration file:   You can just do the steps as I said, "make oldconfig" copies the old configuration, then checks for any new items missing from the config file, you don't need any additional steps.


In other news:  I just tried the latest Lucid daily build(made a Live USB disk), apparently they have the open source ATI driver working properly with 3d acceleration and Compiz on the Radeon 4100/4200 IGP.  Furthermore, it has vastly superior 2d performance when scrolling webpages, etc... than the ATI Catalyst closed-source driver.  It did still require acpi=off to boot, though.  I think I'm going to try Ivan's kernel on a Lucid install, it performed so much better than Karmic...

---

### Post by colinwhipple on 2010-02-07
> **Linux_Lurker said:**
> That's nothing to worry about, warnings aren't a big deal as long as they don't break something.

In regards to the configuration file:   You can just do the steps as I said, "make oldconfig" copies the old configuration, then checks for any new items missing from the config file, you don't need any additional steps.



Thanks for the clarification.  I was assuming too much.

Colin

---

### Post by Linux_Lurker on 2010-02-07
I tried installing Lucid64 on the spare partition of my laptop, and upon installing Ivan's kernel, it won't boot.  I'd venture to guess that Ivan's kernel is now older than the kernel that I installed with the latest daily build(which for whatever reason, broke it), does anybody have the latest Lucid kernel source compiled with the patch?

Or for that matter, does anybody know where to get the latest kernel source for Lucid?  I downloaded the linux-source package for Lucid, but it didn't dump anything in /usr/src when I installed it, unless it just moved the source tarball elsewhere

If not, I'll compile it on my desktop, but I'll have to do it from the Live CD, since my desktop isn't currently running 64 bit Ubuntu.

---

### Post by Linux_Lurker on 2010-02-07
Nevermind, I got the source from GIT.  I think I'm just going to install 32 bit, and compile on my Karmic desktop(assuming they haven't changed GCC so much that it won't compile on Karmic).

---

### Post by Linux_Lurker on 2010-02-07
OK, I compiled my own kernel from the latest Lucid source, and still was unable to boot into the OS.  I really don't understand why the kernel that comes with it will boot, but when I compile the same source with that patch, that it fails(unless the source file has changed enough to make the patch fail)...   Of course, Lucid is pretty buggy ATM, it could be something pertaining to other problems...

Does anybody else have similar experiences with Lucid?  Or a success story?

---

### Post by colinwhipple on 2010-02-08
> **Linux_Lurker said:**
> OK, I compiled my own kernel from the latest Lucid source, and still was unable to boot into the OS.  I really don't understand why the kernel that comes with it will boot, but when I compile the same source with that patch, that it fails(unless the source file has changed enough to make the patch fail)...   Of course, Lucid is pretty buggy ATM, it could be something pertaining to other problems...

Does anybody else have similar experiences with Lucid?  Or a success story?

I had 64bit Lucid installed, and tried a compilation with the patch, but I had strange problems.  I replaced the Lucid with 64bit Karmic, and am running on that now.

Colin

---

### Post by Linux_Lurker on 2010-02-08
> **colinwhipple said:**
> I had 64bit Lucid installed, and tried a compilation with the patch, but I had strange problems.  I replaced the Lucid with 64bit Karmic, and am running on that now.

Colin

Thanks, it looks like Lucid's having problems early on, it's to be expected.  My initial trial of Lucid was very promising, I'm stoked about the work they've done on the open-source radeon driver, I'm sure it will be even better by the time it's released.

---

### Post by colinwhipple on 2010-02-08
Is sound working for people using the patched kernel?  It is working for me in 64-bit Karmic, but not in 32-bit.

Colin

---

### Post by ivanmmj on 2010-02-10
> **Linux_Lurker said:**
> I tried installing Lucid64 on the spare partition of my laptop, and upon installing Ivan's kernel, it won't boot.  I'd venture to guess that Ivan's kernel is now older than the kernel that I installed with the latest daily build(which for whatever reason, broke it), does anybody have the latest Lucid kernel source compiled with the patch?

Or for that matter, does anybody know where to get the latest kernel source for Lucid?  I downloaded the linux-source package for Lucid, but it didn't dump anything in /usr/src when I installed it, unless it just moved the source tarball elsewhere

If not, I'll compile it on my desktop, but I'll have to do it from the Live CD, since my desktop isn't currently running 64 bit Ubuntu.

I'm running Lucid without a problem (albeit, with yet another kernel that I compiled with a lot of optimizations and the BFscheduler. Smooth as can be.

I'm going to try building a kernel with the Ubuntu kernel instead of the normal kernel and see what happens.

---

### Post by ivanmmj on 2010-02-11
The kernel that I built from Ubuntu's kernel git didn't boot properly. I may have been one of the patches that I ran on it, though... (Performance enhancing patches that I run on my current kernel.)

---

### Post by Linux_Lurker on 2010-02-13
Colin:  Audio worked fine for me on either, I'm not sure what to tell you.


Ivan:  It's possible that there is a Ubuntu kernel bug not present in the vanilla kernel, I'm going to try compiling the latest mainline kernel with the patch, I'll report back my findings.

---

### Post by colinwhipple on 2010-02-13
> **Linux_Lurker said:**
> Colin:  Audio worked fine for me on either, I'm not sure what to tell you.



I have been getting inconsistent results.  Sometimes my sound doesn't work, so I restart, and then it does work.  

I am trying to figure out what might be different.

Colin

---

### Post by colinwhipple on 2010-02-13
I did a recompile of the kernel, and when I did a "sudo update-grub" I got the following error message:

/etc/default/grub: 25: Syntax error: EOF in backquote substitution

I assume this means the grub file is corrupted somehow, but I don't know how to fix it.  What should I do?

Update:  Never mind, I found it.

---

### Post by colinwhipple on 2010-02-14
I installed 64-bit Lucid in another partition yesterday.  I got in okay with acpi=off, and compiled a new kernel with the patch, using linux-2.6.32.8.tar.bz2.

The compile (excluding the kernel hacking stuff) seemed to go okay, but when I tried to boot into the new kernel I got the following:

"ext3-fs: sda7: couldn't mount because of unsupported optional features"

I had installed Lucid in an ext4 partition.  Was that a mistake?

Colin

---

### Post by Linux_Lurker on 2010-02-14
Gentlemen, I think I've found a permanent solution to our problem(even if the kernel gets broken again, or the patch becomes outdated).  Deep in the acpi options in menuconfig, there is an option to provide a path to a DSDT table.  Since we know that Karmic with the patch generates a correct DSDT table, we only need to dump it, and manually specify a path to the DSDT table.  I'm going to test this (hopefully) some time today, but if one of you has the time(and know-how), feel free to go ahead and try it.

---

### Post by Linux_Lurker on 2010-02-14
I'm not sure why, but I've failed 3 times today on 3 different kernels.  If somebody wants to give it a try, just:


cd [kernel source directory]

make oldconfig
make menuconfig

go to acpi options, then acpi (....) [at the bottom], then put in something like the below for the path to DSDT option:

/l505d/dsdt.dat


DO NOT PATCH THIS KERNEL


then run(on your patched Karmic system with working everything)

sudo mkdir /l505d
sudo cat /sys/firmware/acpi/tables/DSDT > /l505d/dsdt.dat

then  compile and install your Lucid and/or .32 kernel, and install.  That l505d directory must be present on the laptop with that dsdt file before rebooting after an install of your new kernel.

---

### Post by colinwhipple on 2010-02-14
> **Linux_Lurker said:**
> I'm not sure why, but I've failed 3 times today on 3 different kernels.  If somebody wants to give it a try, just:


cd [kernel source directory]

make oldconfig
make menuconfig

go to acpi options, then acpi (....) [at the bottom], then put in something like the below for the path to DSDT option:

/l505d/dsdt.dat


DO NOT PATCH THIS KERNEL


then run(on your patched Karmic system with working everything)

sudo mkdir /l505d
sudo cat /sys/firmware/acpi/tables/DSDT > /l505d/dsdt.dat

then  compile and install your Lucid and/or .32 kernel, and install.  That l505d directory must be present on the laptop with that dsdt file before rebooting after an install of your new kernel.

I thought that when you did:

make oldconfig

you were bringing in the previous patch.

Nicht wahr?

Colin

---

### Post by Linux_Lurker on 2010-02-14
> **colinwhipple said:**
> I thought that when you did:

make oldconfig

you were bringing in the previous patch.

Nicht wahr?

Colin

Nein, definitiv nicht :-P

the *config options are configuration for compiling the kernel, they don't change the actual source code of the kernel, they just decide what modules are compiled, and whether they are compiled as modules, or into the monolithic kernel.  

Applying the patch actually changes the source code of the kernel.   However, a patch must be applied to the same version of the source file that it was written for.  If enough changes are made to that source file, the patch will eventually fail.  We are something like ~10 kernel revisions past the one where that patch was written, I'd be hesitant to use it.  However, that dsdt table is timeless, as long as we can reference it instead of asking the BIOS for it, it will always work.

---

### Post by colinwhipple on 2010-02-14
> **Linux_Lurker said:**
> Nein, definitiv nicht :-P

the *config options are configuration for compiling the kernel, they don't change the actual source code of the kernel, they just decide what modules are compiled, and whether they are compiled as modules, or into the monolithic kernel.  

Applying the patch actually changes the source code of the kernel.   However, a patch must be applied to the same version of the source file that it was written for.  If enough changes are made to that source file, the patch will eventually fail.  We are something like ~10 kernel revisions past the one where that patch was written, I'd be hesitant to use it.  However, that dsdt table is timeless, as long as we can reference it instead of asking the BIOS for it, it will always work.

I tried it, and the compile failed:

/l505d/dsdt.dat:2132:1: warning: null character(s) ignored
/l505d/dsdt.dat:2132: error: stray ‘\24’ in program
/l505d/dsdt.dat:2132: error: stray ‘\1’ in program
/l505d/dsdt.dat:2132: error: stray ‘\10’ in program
/l505d/dsdt.dat:2132: error: stray ‘\22’ in program
/l505d/dsdt.dat:2132: error: stray ‘\1’ in program
/l505d/dsdt.dat:2132: error: stray ‘\’ in program
/l505d/dsdt.dat:2132: error: stray ‘\10’ in program
/l505d/dsdt.dat:2133: error: stray ‘\226’ in program
make[3]: *** [drivers/acpi/osl.o] Error 1
make[2]: *** [drivers/acpi] Error 2
make[1]: *** [drivers] Error 2
make[1]: Leaving directory `/usr/src/linux-2.6.31.12'
make: *** [debian/stamp/build/kernel] Error 2

Colin

---

### Post by colinwhipple on 2010-02-14
Help me understand what we are doing here.  Shouldn't:

sudo mkdir /l505d

have resulted in creating a top-level directory named l505d?

But I don't see one when I do "Places" and then click on "File System:.

Colin

Update:  But I when I start nautilus from within a terminal where I have done sudo -s I can see the directory, and the file within it.

---

### Post by Linux_Lurker on 2010-02-15
colin:  You should be able to see it from anywhere, but it takes sudo-ing to create it on that level.


I'm not sure why I can't get a kernel to compile, anybody else have any luck?

Ivan, where are you? :D :P

---

### Post by Nemo137 on 2010-02-15
Hello,
Is this issue cropping up with all L505D models? I have an L505D-S5965 and have been thinking about switching to Linux (I ran it for a while on an old laptop, and liked it). I'd seen other places people claiming that the S5965 took to Linux, but I wanted to ask in this thread first, especially since I can't get mine to run the LiveCD for me to check.

Thanks.

---

### Post by Linux_Lurker on 2010-02-16
Nemo:  I'm not sure about other models, there are many variables involved.

Colin:  Apparently there's a bug in the module that loads a DSDT table, which is causing the kernel compile to fail.  I'm not sure if there are still any other ways to manually specify a DSDT table(like a bootswitch), but IMHO, that's the L505d-S5983 community's best chance of being able to continue using the latest kernels, even if the patch stops working.

I'd hate to have to choose between ACPI and the new Radeon Open-Source driver when Lucid comes out :(

---

### Post by colinwhipple on 2010-02-17
> **Linux_Lurker said:**
> I'm not sure why, but I've failed 3 times today on 3 different kernels.  If somebody wants to give it a try, just:


cd [kernel source directory]

make oldconfig
make menuconfig

go to acpi options, then acpi (....) [at the bottom], then put in something like the below for the path to DSDT option:

/l505d/dsdt.dat


DO NOT PATCH THIS KERNEL


then run(on your patched Karmic system with working everything)

sudo mkdir /l505d
sudo cat /sys/firmware/acpi/tables/DSDT > /l505d/dsdt.dat

then  compile and install your Lucid and/or .32 kernel, and install.  That l505d directory must be present on the laptop with that dsdt file before rebooting after an install of your new kernel.

I have been trying to read up on DSDTs.

Is the DSDT at /sys/firmware/acpi/tables created by Ubuntu during the install, based on what it finds on our system?  What is the likelihood that it has errors in it?

Colin

---

### Post by Linux_Lurker on 2010-02-17
> **colinwhipple said:**
> I have been trying to read up on DSDTs.

Is the DSDT at /sys/firmware/acpi/tables created by Ubuntu during the install, based on what it finds on our system?  What is the likelihood that it has errors in it?

Colin

The DSDT is at:

/sys/firmware/acpi/tables/DSDT

It's what is read from the BIOS at boot time.  Apparently, Linux get's a bad DSDT table at boot time without the patch due to some kind of "modifications" made by the BIOS while copying it from Flash memory(although Windows gets one that works just fine...).  However, that patch causes the CPU to grab the DSDT early rather than wait for the BIOS to give it to it, which results in a DSDT that works just fine...

I'm inclined to say that either Insyde or Toshiba is sabotaging Linux, IMHO, or at the very least, Microsoft ACPI tools are sabotaging Linux....

However, I'm pretty sure that our DSDT grabbed with the patch is reasonably free of errors, you could try decompiling, then re-compiling the dsdt with IASL.   IASL will tell you if it recompiled correctly, and will then do optimizations upon recompiling.

---

### Post by Linux_Lurker on 2010-02-21
Just a quick update, I was able to compile the latest .32 series kernel with the patch, selecting the option to embed a DSDT table was actually causing the failure.  It works for now, and allows me to run the latest open-source Radeon driver in Karmic.  Apparently, the bugs in Lucid are actually specific to Lucid, not the .32 series kernel.

---

### Post by colinwhipple on 2010-02-21
> **Linux_Lurker said:**
> Just a quick update, I was able to compile the latest .32 series kernel with the patch, selecting the option to embed a DSDT table was actually causing the failure.  It works for now, and allows me to run the latest open-source Radeon driver in Karmic.  Apparently, the bugs in Lucid are actually specific to Lucid, not the .32 series kernel.

I guess I am not surprised to learn I don't understand this process very well.

I downloaded:  linux-2.6.32.8.tar.bz2

Then I ran the next two lines of Ivan's instructions substituting the appropriate file designation for the originals.

I did the next three lines of the instructions as is and then ran make menuconfig, loading the alternate configuration file.

But when I did make-kpkg clean I saw a lot of references to the 31.12 version, not the 32.8.

Can you tell me what I missed doing, or did wrong?

Colin

---

### Post by colinwhipple on 2010-02-22
> **colinwhipple said:**
> I guess I am not surprised to learn I don't understand this process very well.

I downloaded:  linux-2.6.32.8.tar.bz2

Then I ran the next two lines of Ivan's instructions substituting the appropriate file designation for the originals.

I did the next three lines of the instructions as is and then ran make menuconfig, loading the alternate configuration file.

But when I did make-kpkg clean I saw a lot of references to the 31.12 version, not the 32.8.

Can you tell me what I missed doing, or did wrong?

Colin

I think this may be the answer to my question:

[http://www.cromwell-intl.com/unix/linux-kernel.html](http://www.cromwell-intl.com/unix/linux-kernel.html)

 Your distribution or earlier work by yourself or other administrators may have already installed kernel source under a directory named /usr/src/linux-oldrelease  with a symbolic link pointing to it. Find out, and if necessary, remove that link:

# cd /usr/src
# ls -l
# rm linux

Colin

---

### Post by colinwhipple on 2010-02-23
There is a new BIOS file available for download:

[http://www.csd.toshiba.com/cgi-bin/tais/support/jsp/modelContent.jsp?modelFilter=L505D-S5983&rpn=PSLV6U&category=&selCategory=3&moid=2439388&os=&ct=SB&selFamily=1073768663](http://www.csd.toshiba.com/cgi-bin/tais/support/jsp/modelContent.jsp?modelFilter=L505D-S5983&rpn=PSLV6U&category=&selCategory=3&moid=2439388&os=&ct=SB&selFamily=1073768663)

Version 1.10 - 2010-02-01

    * Added the LG LP156WH1-TLC2 brightness table.
    * Updated the VBIOS to fix an LG LP156WH2_TLA1 "display scratch commas garbage" issue
    * Disabled HDMI audio and HDMI output on SKUs without HDMI.
    * Modified the HDD password algorithm.

---

### Post by Linux_Lurker on 2010-02-23
> **colinwhipple said:**
> There is a new BIOS file available for download:

[http://www.csd.toshiba.com/cgi-bin/tais/support/jsp/modelContent.jsp?modelFilter=L505D-S5983&rpn=PSLV6U&category=&selCategory=3&moid=2439388&os=&ct=SB&selFamily=1073768663](http://www.csd.toshiba.com/cgi-bin/tais/support/jsp/modelContent.jsp?modelFilter=L505D-S5983&rpn=PSLV6U&category=&selCategory=3&moid=2439388&os=&ct=SB&selFamily=1073768663)

Version 1.10 - 2010-02-01

    * Added the LG LP156WH1-TLC2 brightness table.
    * Updated the VBIOS to fix an LG LP156WH2_TLA1 "display scratch commas garbage" issue
    * Disabled HDMI audio and HDMI output on SKUs without HDMI.
    * Modified the HDD password algorithm.


Have you tried it yet?  Any difference?

---

### Post by colinwhipple on 2010-02-23
> **Linux_Lurker said:**
> Have you tried it yet?  Any difference?

I installed it, but no difference.

I booted from a Karmic AMD64 flashdrive, and when it eventually got to the desktop, the mouse was frozen.

Colin

---

### Post by Linux_Lurker on 2010-02-23
> **colinwhipple said:**
> I installed it, but no difference.

I booted from a Karmic AMD64 flashdrive, and when it eventually got to the desktop, the mouse was frozen.

Colin

TBH, I distrust Insyde and Toshiba, it wouldn't be the first time a major OEM has sabotaged Linux in order to suck-up to Microsoft.  I don't expect them to ever release any BIOS updates that fix this.  If you need a copy of the original BIOS, I believe I have on my hard-drive somewhere.


Also, here is the latest 2.6.32.9 Kernel compiled with the patch, it runs fine so far in Karmic, and the graphics are great using the open-source driver.

[http://www.sendspace.com/file/4kp0n9](http://www.sendspace.com/file/4kp0n9)


EDIT:  Oops, that's the 32 bit vanilla kernel, FYI.

---

### Post by colinwhipple on 2010-02-24
> **Linux_Lurker said:**
> TBH, I distrust Insyde and Toshiba, it wouldn't be the first time a major OEM has sabotaged Linux in order to suck-up to Microsoft.  I don't expect them to ever release any BIOS updates that fix this.  If you need a copy of the original BIOS, I believe I have on my hard-drive somewhere.


Also, here is the latest 2.6.32.9 Kernel compiled with the patch, it runs fine so far in Karmic, and the graphics are great using the open-source driver.

[http://www.sendspace.com/file/4kp0n9](http://www.sendspace.com/file/4kp0n9)


EDIT:  Oops, that's the 32 bit vanilla kernel, FYI.

The other website I have been looking at has this instruction:

=================
The tar archive may have created files owned by some random UID other than 0, meaning root.  This is not good! Fix it and make sure that everything has worked so far:

# chown -R root:root linux-release
# ls -laF
=================

I wonder how important that is, or how likely to make a difference.

---

### Post by colinwhipple on 2010-02-25
I installed the 32.9 kernel in 64-bit Karmic, with the ACPI patch.  I had to reboot a couple of time to get power management working properly, and the ATI Catalyst 9-12 driver had an unpleasant ripple effect, so I un-installed that.  But now things seem to be working fine.

The 32.8 and 32.9 kernels seem to have fixed the Linux/Firefox autocomplete bug.

---

### Post by nickjzee on 2010-03-02
Any luck with this guys?  I'm having the same issue with a Toshiba L505D GS6000.

---

### Post by Linux_Lurker on 2010-03-03
> **nickjzee said:**
> Any luck with this guys?  I'm having the same issue with a Toshiba L505D GS6000.

Within the last ~5 pages or so, myself and Ivan and (I think Colin) have all uploaded Linux kernels that fix the problem for us, they may fix your problems as well.

---

### Post by mikep554 on 2010-03-03
Hey all, I'm the OP of this thread. I had given up on this issue months ago and was just running my laptop permanently with acpi=off, which was kind of a bummer. However, I checked back here a couple of days ago and saw all the progress that you guys had made.

I'm happy to say I followed the very fine kernel compiling instructions, and my laptop boots without acpi=off. I have all the little luxuries like power management (not really a luxury on a laptop) and hotkey support. Even Toshiba's stupid volume knob works!

Thanks a lot to everybody who contributed to this thread, and boo-hiss on Toshiba for having a bios that works fine with Windows but kills Linux.

---

### Post by mikep554 on 2010-03-04
Since the kernel patch resolved my problem and appears to solve for others as well, I'm marking this thread solved.

BTW, my laptop will now hibernate (suspend to disk) and suspend to ram flawlessly. Waking from either state takes no longer than Windows 7 takes for the same functions, and it works just as smoothly.

---

### Post by ivanmmj on 2010-03-04
I wonder if the .33 kernel works without modification? I don't have Ubuntu installed at the moment so I can't try it out. Maybe I'll mess with it tonight.

---

### Post by colinwhipple on 2010-03-04
> **ivanmmj said:**
> I wonder if the .33 kernel works without modification? I don't have Ubuntu installed at the moment so I can't try it out. Maybe I'll mess with it tonight.

I tried it this evening and got this:

The UTS Release version in include/linux/version.h
	   "" 
does not match current version:
	   "2.6.33-l505d33" 
Please correct this.

===============

Update:  From what I can find out, kernel-package ver. 12.032 is required.

---

### Post by colinwhipple on 2010-03-05
I was able to compile 2.6.33 with the L505d patch in Lucid Alpha 3, and get it to boot.  The Wifi doesn't work, though.  Wifi in 2.6.32.8 still works.

---

### Post by tee_eff_em on 2010-03-06
> **mikep554 said:**
> Hey all, I'm the OP of this thread. I had given up on this issue months ago and was just running my laptop permanently with acpi=off, which was kind of a bummer. However, I checked back here a couple of days ago and saw all the progress that you guys had made.

I'm happy to say I followed the very fine kernel compiling instructions, and my laptop boots without acpi=off. I have all the little luxuries like power management (not really a luxury on a laptop) and hotkey support. Even Toshiba's stupid volume knob works!

Thanks a lot to everybody who contributed to this thread, and boo-hiss on Toshiba for having a bios that works fine with Windows but kills Linux.

FWIW I thought I should chime in too with many thanks. I have been lurking on this thread awhile, but too kernel naive to contribute anything useful.

I've not compiled any kernels myself, but have had satisfactory success using the [post=8704230]l505d-speed[/post] kernel, and with the options pci=noacpi pci=assign-busses rather than acpi=off. I tried the [post=8774097]nodebug[/post] version, but the splash screen and alternate consoles were corrupted somehow, making me nervous (not to mention making life difficult on those occasions I needed another console).

My only issue now is that, though the system can sleep and/or hibernate, upon waking the wifi can only establish a weak and unsuable connection, preventing me from utilizing sleep/hibernate anyway. (But probably not a topic for this thread -- though I suppose I should test it under an unpatched kernel sometime)


To reiterate my kernel-naivete: Why is all this such a crapshoot?


And to reiterate my reason for de-lurking: Kudos to all who worked toward these solutions!

[Edit: Neglected to note my specific problematic model, the same as several others here: Satellite L505D-S5983 ]

---

### Post by Linux_Lurker on 2010-03-06
> **tee_eff_em said:**
> 

To reiterate my kernel-naivete: Why is all this such a crapshoot?



Well, it comes down to a couple things:

Linux kernels fresh from kernel.org are as bleeding-edge as software can be, the code is often so fresh that it hasn't been tested at all, even by the author.  Distros take somewhat older kernels and test/patch them to be more stable.  If every non-public alpha of the Windows kernel was available to the public, I think you'd find that bleeding-edge Linux kernels are actually more stable.

Also, some hardware vendors sabotage Linux, plain and simple, either by deliberate mischief, or by naively using Microsoft approved ACPI tools...

---

### Post by asharma6 on 2010-03-11
I have L505D S5983, which I just bought this week. I came with Win7 and a 320 GB hard drive. I went through the pain of partitioning my hard drive and installing Win 7 only to find I couldn't install Ubuntu. Then I came to this forum and it took me quite a while but the instructions provided by ivanmmj on how to compile the patched kernel was excellent. I followed the instruction and my laptop works perfectly, thanks a lot. Infact, I am so impressed and thankful I just registered to say thank you.

Also I found at a lot of places which said Install Ubuntu with acpi=off option the first time but then no one gave instructions as to how to boot after the installation, I had nearly given up but I found the instructions to that too in this or one of the other forums which was good.

Once again thanks to all the people.

---

### Post by ivanmmj on 2010-03-16
The proper thing to do will be to take our working DSDT table, decompile it, fix any issues with it and then recompile it and insert it into the kernel (like was mentioned by others in here.)
I decompiled it and tried to recompile it but I'm running into errors. (Even our working DSDT table is buggy...)
I'm going to see if I can get some help in fixing up the table properly and then see if it will allows to boot a proper Ubuntu kernel.

---

### Post by spudder on 2010-03-16
I to have a Toshiba L505D-5986. I am running 9.10 on a flash drive I made. I was unable to get control of my keyboard when I installed. I also run the ACIP=OFF,. I also choose the EDD=ON in F-6 which let's me use the keyboard. But I still get no where when I try to install and use my hard drive. Big Time Bummer,  thanks Spudder

---

### Post by ivanmmj on 2010-03-16
> **spudder said:**
> I to have a Toshiba L505D-5986. I am running 9.10 on a flash drive I made. I was unable to get control of my keyboard when I installed. I also run the ACIP=OFF,. I also choose the EDD=ON in F-6 which let's me use the keyboard. But I still get no where when I try to install and use my hard drive. Big Time Bummer,  thanks Spudder

Install any of the kernels that we've posted and let us know if any of them work.

---

### Post by sbailey85 on 2010-03-16
Hello everyone. First of all i would like to thank everyone for their work on this issue. Been wanting to go back to linux after years away and the ACPI issue was haunting me for weeks now. Now i am up and running everything working great. I just have one problem its really bugging me.. Nothing serious or anything just annoying.. Everytime i apt-get install a package it installs the new package fine. But each time It tries to install my deb file i made through the instructions given in this thread. Anyone know how i could remedy this? Nothing serious just annoying . Of course the update fails but this is what it gives me.  ```
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms
run-parts: executing /etc/kernel/postinst.d/nvidia-common
run-parts: /etc/kernel/postinst.d/nvidia-common exited with return code 20
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.31.12-l505d.postinst line 1186.
dpkg: error processing linux-image-2.6.31.12-l505d (--configure):
 subprocess installed post-installation script returned error exit status 2
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
 Any help would be greatly appreciated. Otherwise thank you so much for all your work once again.

---

### Post by colinwhipple on 2010-03-17
> **sbailey85 said:**
> Hello everyone. First of all i would like to thank everyone for their work on this issue. Been wanting to go back to linux after years away and the ACPI issue was haunting me for weeks now. Now i am up and running everything working great. I just have one problem its really bugging me.. Nothing serious or anything just annoying.. Everytime i apt-get install a package it installs the new package fine. But each time It tries to install my deb file i made through the instructions given in this thread. Anyone know how i could remedy this? Nothing serious just annoying . Of course the update fails but this is what it gives me.  ```
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms
run-parts: executing /etc/kernel/postinst.d/nvidia-common
run-parts: /etc/kernel/postinst.d/nvidia-common exited with return code 20
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.31.12-l505d.postinst line 1186.
dpkg: error processing linux-image-2.6.31.12-l505d (--configure):
 subprocess installed post-installation script returned error exit status 2
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
 Any help would be greatly appreciated. Otherwise thank you so much for all your work once again.

I have the same problem.  The kernel still boots, but it seems to slow down updates and new installs.

Colin

---

### Post by Lykopis on 2010-03-18
I have a L505D-LS5007 with the same problem.
I tried several different Distros, but no luck.
Your Kernel works on a  L505D-LS5007 as well.
it's not perfect but everything seems to work Ok.
I haven't tried the sleep or hibernate modes yet as I don't use them.
One small note: I would update the kernel images from Ubuntu first.
Then use the custom kernel at least on 9.1 anyway.
Thanks Guys for a great job on this.

---

### Post by vl@dmeister on 2010-03-18
First off, I'd like to thank everybody who contributed to this forum (specially to Colin, Linux_Lurker and ivanmmj for the kernels and compiling instructions).:D

i finally got karmic running on my toshiba L505D-ES5025. So far, my keyboard, wifi and touchpad have been working fine. I did however run into some issues with compiling my own kernel. I'm still kinda feeling my way around linux. Some of the software updates i can't seem to install after my own kernel compilation. I ended up installing Ubuntu via Wubi for the mean time, and after that installed ivanmmj's deb files.

Thanks again everybody. good job :P

---

### Post by Linux_Lurker on 2010-03-22
> **sbailey85 said:**
> ... Of course the update fails...

Actually, it doesn't fail(not usually anyways)...  Ubuntu just freaks out when you compile your own kernel, usually the update actually succeeded, despite that message at the end.   I'm sure there's just a setting that has to be made in the kernel config to make the errors go away, but I have no idea what it is.

---

### Post by ivanmmj on 2010-03-25
There's a new patch that I'm going to try on the Ubuntu kernel from git. If it works, it would be the first time we got an Ubuntu kernel working. I also submitted a request to get some help with created a fixed DSDT table to load.

---

### Post by ivanmmj on 2010-03-26
The patch worked! I am currently running Ubuntu with the Ubuntu kernel compiled from the Ubuntu git.

---

### Post by ivanmmj on 2010-03-26
[http://justkitchen.info/kernel/linux-image-2.6.32.10+drm33.1-l505d-fix-00002-gc70930f-dirty_2.6.32.10+drm33.1-l505d-fix-00002-gc70930f-dirty-10.00.Custom_i386.deb](http://justkitchen.info/kernel/linux-image-2.6.32.10+drm33.1-l505d-fix-00002-gc70930f-dirty_2.6.32.10+drm33.1-l505d-fix-00002-gc70930f-dirty-10.00.Custom_i386.deb)
[http://justkitchen.info/kernel/linux-headers-2.6.32.10+drm33.1-l505d-fix-00002-gc70930f-dirty_2.6.32.10+drm33.1-l505d-fix-00002-gc70930f-dirty-10.00.Custom_i386.deb](http://justkitchen.info/kernel/linux-headers-2.6.32.10+drm33.1-l505d-fix-00002-gc70930f-dirty_2.6.32.10+drm33.1-l505d-fix-00002-gc70930f-dirty-10.00.Custom_i386.deb)

---

### Post by colinwhipple on 2010-03-26
> **ivanmmj said:**
> The patch worked! I am currently running Ubuntu with the Ubuntu kernel compiled from the Ubuntu git.

Could you tell what should replace the line from your previous instructions like this one:

wget [http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.32.10.tar.bz2](http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.32.10.tar.bz2)

Would any other alteration be needed?

Thanks for all your help,
Colin

---

### Post by ivanmmj on 2010-03-26
> **colinwhipple said:**
> Could you tell what should replace the line from your previous instructions like this one:

wget [http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.32.10.tar.bz2](http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.32.10.tar.bz2)

Would any other alteration be needed?

Thanks for all your help,
Colin

Instead of using wget, you have to know how to use git.
I'll try to put a walkthrough together, later. ^_^

---

### Post by colinwhipple on 2010-03-26
The new "comment 75" patch worked for me in 64bit Karmic, compiling the standard linux 32.10 kernel.

[https://bugzilla.kernel.org/show_bug.cgi?id=14679](https://bugzilla.kernel.org/show_bug.cgi?id=14679)

It actually seems a bit zippier, but that may be my imagination.

Colin

---

### Post by ivanmmj on 2010-03-27
> **colinwhipple said:**
> The new "comment 75" patch worked for me in 64bit Karmic, compiling the standard linux 32.10 kernel.

[https://bugzilla.kernel.org/show_bug.cgi?id=14679](https://bugzilla.kernel.org/show_bug.cgi?id=14679)

It actually seems a bit zippier, but that may be my imagination.

Colin

Same patch that works with the Ubuntu kernel from GIT. Did you see the comment about improving DSDT table extraction? I'm looking forward to something like this being built in.

---

### Post by colinwhipple on 2010-03-28
Looking at various explanations of Grub2, I don't see a way to add a kernel boot option, like "acpi=copy_dsdt" for a specific kernel.  Am I missing something?

I can only find the way to add it for all kernels, using "GRUB_CMDLINE_LINUX="".

This is the best explanation of Grub2 I can find:

[https://wiki.edubuntu.org/Grub2#/etc/grub.d/folder](https://wiki.edubuntu.org/Grub2#/etc/grub.d/folder)

=====

I did a little more looking and found this:

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

Go down to Section 6, "Adding entries to Grub 2".  Basically, you open grub.cfg and copy the entry you want to add a kernel boot option to.  Then, as root, open the file /etc/grub.d/40_custom, paste your entry at the end of the file, and add the boot option.  I also added a bit more verbiage to the name of the menuentry so I would recognize it at boot time.  Save and run "sudo update-grub".  Reboot and enjoy.

Also, if you have Startup-Manager installed you can easily make this Grub menu entry the default at boot time.

Colin

---

### Post by oryan_dunn on 2010-03-29
My Dad has this laptop (L505D-S5983) and wants me to put Ubuntu on it.  I tried Karmic, but had problems, and with Lucid I get the kernel_thread_helper error unless I boot with acpi=off.

Will this fix be in the final release of Lucid?  I'd like to have a really simple install for him, so he can manage the install himself; preferably, no custom kernels.

---

### Post by JDuBZisFADED on 2010-03-30
Hello first off I would like to say thank you for fixing the acpi errors allowing me to have a semi-functional laptop. My last issue with my Karmic installation in the lack of wireless drivers. I approached this situation by downloading the drivers for windows 7 yet i am unable to extract any driver files (.inf,.sys) due to the format of the exe. It requires me to extract data1.cab,data2.cab, and data1.hdr which i have concluded to be impossible to extract based on my extensive google research and attempts of extraction. My laptop model is L505D-GS6000 and I am stuck without wifi. This is the link to the download page of my model from Toshiba. It is an Atheros Wireless Lan Driver version 1.0.2.2. 


What I am using:

Ubuntu 9.10
Toshiba L505D-GS6000
absolutely no wifi/no recognition of my chip
This kernel located on page 9 > **Linux_Lurker said:**
> Here is an x86 version:

[http://www.sendspace.com/file/qpa732](http://www.sendspace.com/file/qpa732)
a limited amount of Ubuntu knowledge

---

### Post by Linux_Lurker on 2010-04-03
Colin:  Could you share your 64bit kernel?  When I've tried to compile it for 64 bit, my system is unbootable(apparently an error with the hard-drive???), even though 32-bit works fine.   I desperately need to get 64 bit Ubuntu running on my laptop, I need to run 64-bit Windows server in VirtualBox for a development project I'm working on.

Oryan:  I really doubt it will be in the stock kernel before Ubuntu 10.10 is out, but I'd love to be proved wrong.

Jdubz:  I'm not too much of an expert on wireless, but if you compile the latest kernel from kernel.org, there is a lot of new Atheros drivers, many of which aren't selected by default.   It may just be a matter of compiling something that's already in the kernel.   When you do the "make menuconfig" part, you can select all of the appropriate Atheros stuff to be built as modules.

---

### Post by colinwhipple on 2010-04-04
> **Linux_Lurker said:**
> Colin:  Could you share your 64bit kernel?  When I've tried to compile it for 64 bit, my system is unbootable(apparently an error with the hard-drive???), even though 32-bit works fine.   I desperately need to get 64 bit Ubuntu running on my laptop, I need to run 64-bit Windows server in VirtualBox for a development project I'm working on.

Oryan:  I really doubt it will be in the stock kernel before Ubuntu 10.10 is out, but I'd love to be proved wrong.

Jdubz:  I'm not too much of an expert on wireless, but if you compile the latest kernel from kernel.org, there is a lot of new Atheros drivers, many of which aren't selected by default.   It may just be a matter of compiling something that's already in the kernel.   When you do the "make menuconfig" part, you can select all of the appropriate Atheros stuff to be built as modules.

I don't mind sharing my kernel, but I don't have anywhere to put it; I don't have server space or a website anywhere, unless Charter Cable has given me some space that I just don't know about.

I could burn a CD and mail it to you.  Any other suggestions?

Colin

---

### Post by colinwhipple on 2010-04-04
Lurker,

Charter Cable does provide some server space, but its only 20 megs.  Not enough.

Is there a reasonable way to do a direct transfer, maybe using Bitorrent?

Colin

---

### Post by Linux_Lurker on 2010-04-04
> **colinwhipple said:**
> Lurker,

Charter Cable does provide some server space, but its only 20 megs.  Not enough.

Is there a reasonable way to do a direct transfer, maybe using Bitorrent?

Colin

I appreciate it, but you don't need to go to too much trouble.  Instead, could you give me an exact rundown of how you compiled it, like:

Which kernel source
Which (if any) menuconfig options you changed
Which OS you compiled in

Also, did you turn off the kernel-hacking options in menuconfig ?   I did, but I'm beginning to wonder if that's the problem.

Cheers

---

### Post by colinwhipple on 2010-04-04
> **Linux_Lurker said:**
> I appreciate it, but you don't need to go to too much trouble.  Instead, could you give me an exact rundown of how you compiled it, like:

Which kernel source
Which (if any) menuconfig options you changed
Which OS you compiled in

Also, did you turn off the kernel-hacking options in menuconfig ?   I did, but I'm beginning to wonder if that's the problem.

Cheers

I have 2.6.32.10 from:

[http://www.kernel.org/pub/linux/kernel/v2.6/](http://www.kernel.org/pub/linux/kernel/v2.6/)

compiled and running in both 64Bit Karmic and 64bit Beta1 of Lucid Lynx.  I haven't been able to get any of the 2.6.33 variants running properly.  

I pretty much followed Ivan's instructions except for adding this:

chown -R root:root linux-2.6.32.10

right after:

ln -s linux-2.6.32.10 linux

based on what I read on another web site.

The only option I changed in menuconfig is to turn off most of the kernel-hacking stuff.  In a couple of places these was no response to my pressing "n", so I left those.

I didn't try to get rid of any hardware drivers, or change any options except the kernel-hacking stuff.

Hope this helps,
Colin

---

### Post by colinwhipple on 2010-04-07
Since I have been using the "Comment 75" patch from here:

[https://bugzilla.kernel.org/show_bug.cgi?id=14679](https://bugzilla.kernel.org/show_bug.cgi?id=14679)

when I compile a kernel for my L505D-S5983 I have been going into my grub.cfg file, and I have noticed that the menuentrys for the kernels I compile under Lucid Lync, Beta1, don't have an initrd line.  The other menuentrys, including the one I compile under Karmic do have that line.

Not having the line doesn't prevent the kernels from booting, so I am wondering why this is happening and what the significance is.

Colin

---

### Post by colinwhipple on 2010-04-07
This:

Comment #80 From  Len Brown   2010-04-06 01:22:44  -------

FYI,
I will apply the patch from comment #75 to linux when it comes
via next ACPICA update, which should be within the next week or so.

was posted here:

[https://bugzilla.kernel.org/show_bug.cgi?id=14679](https://bugzilla.kernel.org/show_bug.cgi?id=14679)

---

### Post by dlatubu on 2010-04-25
ubuntu with 10.4 on toshiba L505D-S5992
I cannot load on this laptop with win 7, that I want to get rid off. 
I cannot access the HDD because of the viruses. So what how can i proceed to burn a disk with the hacks that you are suggesting here in this forum?
Thanks
David

---

### Post by oryan_dunn on 2010-04-25
> **colinwhipple said:**
> This:

Comment #80 From  Len Brown   2010-04-06 01:22:44  -------

FYI,
I will apply the patch from comment #75 to linux when it comes
via next ACPICA update, which should be within the next week or so.

was posted here:

[https://bugzilla.kernel.org/show_bug.cgi?id=14679](https://bugzilla.kernel.org/show_bug.cgi?id=14679)

So I wonder how long it'll take that patch to hit ubuntu?

---

### Post by sanderd17 on 2010-04-26
> **dlatubu said:**
> ubuntu with 10.4 on toshiba L505D-S5992
I cannot load on this laptop with win 7, that I want to get rid off. 
I cannot access the HDD because of the viruses. So what how can i proceed to burn a disk with the hacks that you are suggesting here in this forum?
Thanks
David
The easiest is when you load the disc and you come on the first screen, you can uncheck options like "acpi" en "noapic". If that works, you should be able to start the computer (with some bugs like not being able to suspend or not having sound). If that doesn't work, the patches described here won't work eather and there is another problem.

---

### Post by Linux_Lurker on 2010-04-26
Somebody please correct me if I'm wrong, but....

That patch still hasn't made it into the kernel yet, has it?  (unless I'm missing it, 2.6.33.3 doesn't have it)

Gaaaaahh...   That's getting really annoying...   I'm planning on getting a new laptop whenever AMD releases their Fusion CPU early next year, I'm starting to believe this laptop still won't have proper non-hacked Linux support by the time that happens.

---

### Post by colinwhipple on 2010-04-27
I think they are getting closer:

[https://patchwork.kernel.org/patch/91236/](https://patchwork.kernel.org/patch/91236/)

---

### Post by sbailey85 on 2010-04-28
Quick comment regarding this patch discussed in this forum... Any body having any trouble installing it to the lynx kernel mentioned on pg 8. I have tried to install lynx with that kernel and patch and it gives me kernel panic  unable to mount vfs drive or something similar. Anyone know a fix for that?

---

### Post by raven920 on 2010-04-29
> **colinwhipple said:**
> I think they are getting closer:

[https://patchwork.kernel.org/patch/91236/](https://patchwork.kernel.org/patch/91236/)

I just installed Lucid Final, can I download the Ubuntu Kernel and apply that patch to it? Will it work?

Thank you for your answer.

---

### Post by colinwhipple on 2010-04-29
> **raven920 said:**
> I just installed Lucid Final, can I download the Ubuntu Kernel and apply that patch to it? Will it work?

Thank you for your answer.

Dunno.  The patch I have used comes from here:

[https://bugzilla.kernel.org/show_bug.cgi?id=14679](https://bugzilla.kernel.org/show_bug.cgi?id=14679)

Colin

---

### Post by raven920 on 2010-04-30
> **colinwhipple said:**
> Dunno.  The patch I have used comes from here:

[https://bugzilla.kernel.org/show_bug.cgi?id=14679](https://bugzilla.kernel.org/show_bug.cgi?id=14679)

Colin

Will it work on the ubuntu kernel?

---

### Post by Lykopis on 2010-04-30
[ivanmmj]("http://ubuntuforums.org/member.php?u=229208") complied a 32 bit Ubuntu Kernel here:
[http://ubuntuforums.org/showthread.php?t=1301101&highlight=toshiba&page=16](http://ubuntuforums.org/showthread.php?t=1301101&highlight=toshiba&page=16)

scroll down to post 157,158 & 159.
So yeah the patch works on a Ubuntu kernel.
But I could only get it to work on Ubuntu 10.04

---

### Post by Lykopis on 2010-04-30
> **Linux_Lurker said:**
> Somebody please correct me if I'm wrong, but....

That patch still hasn't made it into the kernel yet, has it?  (unless I'm missing it, 2.6.33.3 doesn't have it)

Gaaaaahh...   That's getting really annoying...   I'm planning on getting a new laptop whenever AMD releases their Fusion CPU early next year, I'm starting to believe this laptop still won't have proper non-hacked Linux support by the time that happens.

Lurker:
I have tried kernels 2.6.32 - 2.6.34 and none of them have the patch yet.
I think we might see the patch as part of the 2.6.34 kernel when it's in stable release.

Edit: I just looked through the source code for Kernel 2.6.34-rc5-next-20100430 (ACPI)
and it looks like the Toshiba patch is in there. 

Unfortunately this is one of the downsides of Linux when it comes to new hardware.
There is a lag for new drivers to make stuff work right. The Toshiba bio's are in that 
category at the moment. So expect that sometimes really new hardware will not to have 
full Linux support right away.

---

### Post by colinwhipple on 2010-04-30
> **raven920 said:**
> Will it work on the ubuntu kernel?

The problem in answering this is that there is not just one kernel.  What I have been patching and compiling is different versions of the linux kernel, found here:

[http://www.kernel.org/pub/linux/kernel/v2.6/](http://www.kernel.org/pub/linux/kernel/v2.6/)

I have been successful in patching and compiling some of the 2.6.31 and 2.6.32 series kernels.  But I have not been able to get any of the 2.6.33 series kernels to compile and work properly.

Colin

---

### Post by earnoth on 2010-04-30
I've got a Toshiba Satellite L505D-GS6000 and encountered with 9.10 the same acpi problems everyone else was.  Booting with "acpi=off" and "--noapic" options allowed me to install and later boot, and the kernel from ivanmmj was a nice fix that seemed to allow proper ACPI (as well as multi-core, the fresh install didn't seem to have multi-core support). 

I also downloaded and compiled the native vendor driver for the Wifi card (Realtek RTL8191SE).  That worked too, though the Gnome Network Manager proved to be a bit finicky.  

Next, however, I encountered the strangest of errors - spontaneous reboots.  This has happened to me five times in the last 18 hours, with no apparent consistency of what I was doing at the time.  I consulted every log in /var/log that was written around the time-frames of the reboots, but didn't find anything akin to a crash or panic.

I'm dual-booting in Win7 (the manufacturer install) and the problem doesn't seem to extend to there, so I suspect it is not a hardware issue.

Has anyone else experienced this?  What else can I possibly do to troubleshoot this and find a fix?

As a side note, I also can't get the ATI Radeon proprietary drivers installed.  The native Ubuntu installer fails, and when I tried to manually install a direct download from AMD's support site, I had my fifth spontaneous reboot.

I'd hate to have to return this laptop (I'm still within the 14 days BestBuy window) but at this point, I'm sorely tempted to anyway as this is the worst Toshiba in terms of Linux comaptibility that I've bought in 12 years.

Any help would be greatly appreciated. 

Thanks,
-Eric

---

### Post by rdingraham on 2010-04-30
I am using a Toshiba Satellite L505D-LS5004, laptop.  I am running 10.4 Lucid, 64 bit. I managed to install and boot using the acpi=off option.  Then I tried to compile and install  a new kernel, using the instructions by ivanmmj on page 8 of this thread.  Everything went smoothly, apparently without a hitch. I used the 2 original deb files he posted:

linux-headers-2.6.32-l505d-speed_2.6.32-l505d-speed-10.00.Custom_amd64.deb
&
linux-image-2.6.32-l505d-speed_2.6.32-l505d-speed-10.00.Custom_amd64.deb

These also installed with no problem.

However, when I then tried to reboot, I received error messages:

[   0.719716] pci 0000.03.000: Bar6: no parent found for of device [0xfffe0000-0xffffffff]
[   1.271937]Kernel panic - notsyncing: VFS: Unable to mount root fs on unknown-block(0,0)

At that point the boot froze.

#1) Anyone know what went wrong?
#2) Any suggestions? (e.g., is there a different kernel for 10.4, 64 bit, or is there something I need to edit?)

Please:   I am not a computer newbie, and I have been using Ubunti since Hardy, but we are in a realm here which is at the limit of my capabilities. So please, if you can help, be specific.

Thanks everyone who has participated in this thread. Damn to hell Toshiba.

Bob Ingraham

---

### Post by colinwhipple on 2010-04-30
Bob,

I don't have an answer for you, but I will say that I have had more success with Karmic than with Lucid Lynx.  I have both installed on my L505D-S5983, and I spend most of my time in 64bit Karmic.

Even though the final of Lucid is out, I think it is still a bit raw, so to speak.

Colin

---

### Post by Linux_Lurker on 2010-05-01
> **Lykopis said:**
> 
Unfortunately this is one of the downsides of Linux when it comes to new hardware.
There is a lag for new drivers to make stuff work right. The Toshiba bio's are in that 
category at the moment. So expect that sometimes really new hardware will not to have 
full Linux support right away.


Cheers.   I really blame Toshiba and Insyde, TBH.   I've built tons of desktop PCs for myself and others, I never have this kinds of problem with desktop parts, and a nice tier-1 motherboards like Asus and Gigabyte.   Even when the CPU/chipset are very new, I've still had no problem getting Linux up and running.   I'm going to do a bit more research on my next laptop purchase to make sure Linux has proper out-of-the-box support.



rdingraham:   I get that problem using 64 bit Linux, but 32 bit works fine.   I've given up on getting 64 bit working properly on that laptop.   I've tried every which way to get 64 bit running on there(for the sake of being able to run a 64 bit Windows Server  VM), but I just gave up and committed that project to my desktop PC.

---

### Post by rdingraham on 2010-05-01
> **Linux_Lurker said:**
> 
rdingraham:   I get that problem using 64 bit Linux, but 32 bit works fine.   I've given up on getting 64 bit working properly on that laptop.   I've tried every which way to get 64 bit running on there(for the sake of being able to run a 64 bit Windows Server  VM), but I just gave up and committed that project to my desktop PC.

Linux_Lurker:  Over the weekend, I'll try a full install of 10.4 32 bit.  Do you recommend that I stick with ivanmmj's original two kernel deb files (the one's posted on page 8, message 79 of this thread), or have you had bettor success with any of the subsequent kernels that were posted?  

Thanks, Bob Ingraham

---

### Post by Lykopis on 2010-05-01
> **Linux_Lurker said:**
> I'm going to do a bit more research on my next laptop purchase to make sure Linux has proper out-of-the-box support. 

Might I suggest looking into a Dell or IBM (AKA Lenovo) as I understand it both support Linux very well.

---

### Post by Lykopis on 2010-05-01
> **Linux_Lurker said:**
> Cheers.   I really blame Toshiba and Insyde, TBH.   I've built tons of desktop PCs for myself and others, I never have this kinds of problem with desktop parts, and a nice tier-1 motherboards like Asus and Gigabyte.   Even when the CPU/chipset are very new, I've still had no problem getting Linux up and running.

  I agree on the Insyde BIOS being the problem and while I understand what's happening to the DSTS table on a Toshiba laptop it's really complicated as it seems to have something to do with the firmware corrupting that table outside the OS, hence ACPI fails. Even Lin Ming who made the patch said it was crazy to have Two ACPI tables on the 505 machines especially since one was badly broken. So was this Toshiba's way to tie you to win 7? As I understand it some of these machines won't even run Windows XP!

---

### Post by Linux_Lurker on 2010-05-01
> **rdingraham said:**
> Linux_Lurker:  Over the weekend, I'll try a full install of 10.4 32 bit.  Do you recommend that I stick with ivanmmj's original two kernel deb files (the one's posted on page 8, message 79 of this thread), or have you had bettor success with any of the subsequent kernels that were posted?  

Thanks, Bob Ingraham

I'd recommend going for one of the later kernels we compiled, atleast 32.9 or later.   The current 10.04 kernel is based off of 32.9 (AFAIK), therefore, you wouldn't want to risk breaking something by running an older kernel than what the distro came with.  I can re-up any of mine if the sendspace link has expired.

---

### Post by Linux_Lurker on 2010-05-01
> **Lykopis said:**
> Might I suggest looking into a Dell or IBM (AKA Lenovo) as I understand it both support Linux very well.


Cheers for the suggestions.   I've had a love/hate relationship with Dell in the past, but TBH, they are one of the few OEMs who openly say "We like Ubuntu".

---

### Post by rdingraham on 2010-05-02
> **Linux_Lurker said:**
> I'd recommend going for one of the later kernels we compiled, atleast 32.9 or later.   The current 10.04 kernel is based off of 32.9 (AFAIK), therefore, you wouldn't want to risk breaking something by running an older kernel than what the distro came with.  I can re-up any of mine if the sendspace link has expired.

No joy in mudville.  I re-installed the 32 bit Lucid, and downloaded the 32 bit 2.6.33 kernel. Rebooted into the 2.6.33 kernel (with acpi=off), and compiled a new kernel with the patch.  No go. Would not boot with the new kernel.

I think I'll take Colin's advice and go back to Karmic and try that.  If that doesn't work, I'll just wait for a (hopefully soon) fix in an official kernel release.  Meantime I can still use my old, beat-up Compaq Presario, on which Lucid installed flawlessly.

Bob Ingraham

---

### Post by Linux_Lurker on 2010-05-02
> **rdingraham said:**
> No joy in mudville.  I re-installed the 32 bit Lucid, and downloaded the 32 bit 2.6.33 kernel. Rebooted into the 2.6.33 kernel (with acpi=off), and compiled a new kernel with the patch.  No go. Would not boot with the new kernel.

I think I'll take Colin's advice and go back to Karmic and try that.  If that doesn't work, I'll just wait for a (hopefully soon) fix in an official kernel release.  Meantime I can still use my old, beat-up Compaq Presario, on which Lucid installed flawlessly.

Bob Ingraham


Actually, I should've been more specific;  I've never gotten the .33 kernel to work, so, I should've said:  a later .32 kernel.

Also, I forgot to say that I can get 64 bit Karmic running using the pci=noacpi switch, the only caveat being that the touchpad and battery meter won't work.

---

### Post by Lykopis on 2010-05-02
rdingraham: I was planning on trying the Kernel posted here:
(post 159)

[http://ubuntuforums.org/showthread.php?t=1301101&highlight=toshiba&page=16](http://ubuntuforums.org/showthread.php?t=1301101&highlight=toshiba&page=16)

I tested it on another install and it seemed to work without breaking anything.
But then that was on a copy of Lucid Beta.
Unfortunately the link seems dead also.
I just get a placeholder now.

---

### Post by sbailey85 on 2010-05-02
I have the latest kernel working fine with lucid with the copy_dsdt patch from the bugzilla page on 64 bit. what issues is everyone running into? I had issues at first where my kernel would not work. After investigating my grub.cfg i noticed there was no initrd file. I then had to create the initrd file and run update-grub which then added the initrd file to my grub.cfg file and it booted like a charm. Once i got that to work the wireless driver did not get compiled into the kernel as well. I had to recompile the kernel after adding the wireless driver as a module. After that everything is working like a charm. I hope this helps someone out.

---

### Post by colinwhipple on 2010-05-02
> **sbailey85 said:**
> I have the latest kernel working fine with lucid with the copy_dsdt patch from the bugzilla page on 64 bit. what issues is everyone running into? I had issues at first where my kernel would not work. After investigating my grub.cfg i noticed there was no initrd file. I then had to create the initrd file and run update-grub which then added the initrd file to my grub.cfg file and it booted like a charm. Once i got that to work the wireless driver did not get compiled into the kernel as well. I had to recompile the kernel after adding the wireless driver as a module. After that everything is working like a charm. I hope this helps someone out.

What is the process to create the initrd file?  When I compiled a kernel in Karmic that was automatic, from the instructions Ivan provided.

Colin

Colin

---

### Post by sbailey85 on 2010-05-02
> **colinwhipple said:**
> What is the process to create the initrd file?  When I compiled a kernel in Karmic that was automatic, from the instructions Ivan provided.

Colin

Colin

Yea it was automatic as well for me in karmic.. But for some reason either the newer kernel or lucid makes it so it doesnt happen the command to make a new one is update-initramfs -c(to create new) -k 2.6.33.3-l505d for me... the part after k is for the kernel you want the initrd file made for

---

### Post by colinwhipple on 2010-05-02
> **sbailey85 said:**
> Yea it was automatic as well for me in karmic.. But for some reason either the newer kernel or lucid makes it so it doesnt happen the command to make a new one is update -c(to create new) -k 2.6.33.3-l505d for me... the part after k is for the kernel you want the initrd file made for

When I did this in the /usr/src directory:

update -c -k 2.6.32.12-l505d

I get this:

No command 'update' found, did you mean:
 Command 'uupdate' from package 'devscripts' (main)
 Command 'lupdate' from package 'libqt4-dev' (main)
 Command 'lupdate' from package 'qt3-dev-tools' (main)
update: command not found

Colin

---

### Post by sbailey85 on 2010-05-02
> **colinwhipple said:**
> When I did this in the /usr/src directory:

update -c -k 2.6.32.12-l505d

I get this:

No command 'update' found, did you mean:
 Command 'uupdate' from package 'devscripts' (main)
 Command 'lupdate' from package 'libqt4-dev' (main)
 Command 'lupdate' from package 'qt3-dev-tools' (main)
update: command not found

Colin

my bad the command is update-initramfs sorry about that dont know how i did that :) :confused:

---

### Post by colinwhipple on 2010-05-02
> **sbailey85 said:**
> my bad the command is update-initramfs sorry about that dont know how i did that :) :confused:

Thanks.  That worked for me.

Colin

---

### Post by raven920 on 2010-05-03
I compiled the latest linux-source (A.K.A. the ubuntu kernel) with the copy_dsdt patch, installed it and created the new intramfs file. It works pretty well.

Thank you for your help, I hope they include this patch on the mainstream kernel someday soon.

---

### Post by taserian on 2010-05-03
I seem to be having some trouble getting the compile from #71 to work correctly. I'm on 10.04, and went through the whole kernel patch. My volume control is working correctly, and it boots without the acpi=off option, but my touchpad is no longer working. I need to use an external mouse. Also, the functions enabled by FN+F* for brightness, touchpad on/off, etc. still don't work; I thought the patch would fix them.

I tried downloading the already-compiled kernels that ivanmmj has posted, but the pages don't seem to be working correctly. Does anyone have a recent kernel compile that I can download, and hopefully fix this problem? BTW, my Toshiba is an L505D-ES5025, but I don't think it's that different from the other options with the BIOS problem.

EDIT: I've just noticed that even though the volume control works and registers changes in the volume applet in the top right corner, I'm getting no sound at all. I guess kernel compiling isn't for me. Anyone with a valid kernel that I can download?

---

### Post by rdingraham on 2010-05-04
[QUOTE=sbailey85;9221836] I then had to create the initrd file and run update-grub which then added the initrd file to my grub.cfg file and it booted like a charm. 

This may be a stupid question, but once I run your command to add the initrd file, do I then simply type "update-grub" in the terminal? Or is there more to it?

Bob

---

### Post by raven920 on 2010-05-04
> **rdingraham said:**
> [QUOTE=sbailey85;9221836] I then had to create the initrd file and run update-grub which then added the initrd file to my grub.cfg file and it booted like a charm. 

This may be a stupid question, but once I run your command to add the initrd file, do I then simply type "update-grub" in the terminal? Or is there more to it?

Bob

Yes, that's it, you only need to run update-grub and you are ready to go.

---

### Post by johnproyal on 2010-05-04
I feel like an idiot that I even have to ask this, but how does one go about compiling their own kernel? I read this entire thread (some parts a couple times) but it went over my head a bit. I'm very new to Linux.

Thanks for this thread, though. If I understood most of what was being said, I imagine it would have helped me a lot. :p

---

### Post by colinwhipple on 2010-05-04
> **johnproyal said:**
> I feel like an idiot that I even have to ask this, but how does one go about compiling their own kernel? I read this entire thread (some parts a couple times) but it went over my head a bit. I'm very new to Linux.

Thanks for this thread, though. If I understood most of what was being said, I imagine it would have helped me a lot. :p

The basic instructions are in the first post on Page 8 of this thread.  Ivan's instructions are very good.

There is other stuff scattered around on the thread subsequent to that.

Colin

---

### Post by rdingraham on 2010-05-04
Unbelievable!!!  It's alive and working.  Compiled the kernel, ran the command to insert the initrd file, and updated the grub.  Booted into 10.04 Lucid 64 bit without a hitch!  Don't know if everything is working yet.  I don't need the touchpad, and I can do without the wireless at least for a while,  I'll have to check it all out.

A great thanks to all of you.

Bob

---

### Post by rdingraham on 2010-05-05
After further checking...

Most things are working fine, with a few exceptions.

Touchpad is dead, but I never use it.

Wireless is dead.  Eventually need to get this fixed, but can live without it for now.  Spend 90% of internet time at a location with hard-wired ethernet connection.

Strangest problem concerns the network. I can get on the internet, and I added my network printer (which has a fixed IP address) with no problem.  But I cannot see any of the other computers on the network, and they can't see my Toshiba. (Some are linux, some are Windows) I installed Samba, and all the Samba-related files, joined the local Workgroup, but no go.  My Compaq laptop, which is running 32 bit Lucid, has no problem accessing the same internal network, with the same network and Samba settings. It sees, and is seen, by the other computers.

Can see the battery & the heat sensors. USB ports work fine.  All the rest is OK.

One question.  When I ran Update Manager, it wanted to install a new version of linux-libc-dev, which "provides headers for the linux kernel."  If I install it, will it screw up my custom kernel?

Any one else run into this network problem, or have any idea what the problem might be?

Thanks.

Bob

---

### Post by sebastian.ricaldoni on 2010-05-05
Hi. I have a brand new Toshiba L505-GS5037. I just finished installing Lucid (with ACPI=off). Anyway, acpi=off was only required during the installation. Once installed I load Linux with no problem. I do however, have the same problem...only 1 core is being used. I read in this thread that although the issue with the number of cores gets fixed, the mousepad and, what is more important, the wireless stops working?
Can you confirm me that please?

Thanks a lot.
Sebastian

---

### Post by sbailey85 on 2010-05-05
> **rdingraham said:**
> After further checking...

Most things are working fine, with a few exceptions.

Touchpad is dead, but I never use it.

Wireless is dead.  Eventually need to get this fixed, but can live without it for now.  Spend 90% of internet time at a location with hard-wired ethernet connection.

Strangest problem concerns the network. I can get on the internet, and I added my network printer (which has a fixed IP address) with no problem.  But I cannot see any of the other computers on the network, and they can't see my Toshiba. (Some are linux, some are Windows) I installed Samba, and all the Samba-related files, joined the local Workgroup, but no go.  My Compaq laptop, which is running 32 bit Lucid, has no problem accessing the same internal network, with the same network and Samba settings. It sees, and is seen, by the other computers.

Can see the battery & the heat sensors. USB ports work fine.  All the rest is OK.

One question.  When I ran Update Manager, it wanted to install a new version of linux-libc-dev, which "provides headers for the linux kernel."  If I install it, will it screw up my custom kernel?
  
Any one else run into this network problem, or have any idea what the problem might be?

Thanks.

Bob

Hello Bob,
When i first installed lucid with the custom kernel my wireless stopped working as well... What wireless card is our laptop using. Mine is the RTL8187SE i had to go back into the kernel configurations and recompile with my driver selected as a module. For some reason the configuration i copied did not transfer the wireless card.

---

### Post by colinwhipple on 2010-05-05
> **sebastian.ricaldoni said:**
> Hi. I have a brand new Toshiba L505-GS5037. I just finished installing Lucid (with ACPI=off). Anyway, acpi=off was only required during the installation. Once installed I load Linux with no problem. I do however, have the same problem...only 1 core is being used. I read in this thread that although the issue with the number of cores gets fixed, the mousepad and, what is more important, the wireless stops working?
Can you confirm me that please?

Thanks a lot.
Sebastian

I have only have a problem with wireless if I compile and install a 2.6.33 series kernel.  With 2.6.32 or below wireless works for me.

Colin

---

### Post by wnemay on 2010-05-05
> **sebastian.ricaldoni said:**
> Hi. I have a brand new Toshiba L505-GS5037. I just finished installing Lucid (with ACPI=off). Anyway, acpi=off was only required during the installation. Once installed I load Linux with no problem. I do however, have the same problem...only 1 core is being used. I read in this thread that although the issue with the number of cores gets fixed, the mousepad and, what is more important, the wireless stops working?
Can you confirm me that please?

Thanks a lot.
Sebastian

I have a Toshiba L505 laptop, and have had nothing but trouble installing Ubuntu 9.10 or 10.04 on it.  I finally figured it out and made a quick writeup to help others with this problem.  ACPI=OFF is not the way to go, it causes a lot of other issues.  You want ACPI=HT.
[http://www.wnemay.com/2010/linux/ubuntu-10-04-with-acpi-issue-on-my-toshiba-l505-laptop]("http://www.wnemay.com/2010/linux/ubuntu-10-04-with-acpi-issue-on-my-toshiba-l505-laptop/")/

---

### Post by mseney on 2010-05-05
> **wnemay said:**
> I have a Toshiba L505 laptop, and have had nothing but trouble installing Ubuntu 9.10 or 10.04 on it.  I finally figured it out and made a quick writeup to help others with this problem.  ACPI=OFF is not the way to go, it causes a lot of other issues.  You want ACPI=HT.
[http://www.wnemay.com/2010/linux/ubuntu-10-04-with-acpi-issue-on-my-toshiba-l505-laptop]("http://www.wnemay.com/2010/linux/ubuntu-10-04-with-acpi-issue-on-my-toshiba-l505-laptop/")/

Hey thanks that worked! I'll use this until a Kernel is released via the Ubuntu Update Manager that addresses this problem. Everything works except for not having a battery meter but I can live with that for now. My Laptop is a Toshiba Satellite L505D-S5983.

---

### Post by raven920 on 2010-05-05
That's strange, everything works for me, the touchpad, the wireless, the battery status, everything.

I got a Toshiba Satellite L505D-SP6905R and everything works right with the latest ubuntu kernel + the copy_dsdt patch.

---

### Post by rdingraham on 2010-05-06
> **sbailey85 said:**
> Hello Bob,
When i first installed lucid with the custom kernel my wireless stopped working as well... What wireless card is our laptop using. Mine is the RTL8187SE i had to go back into the kernel configurations and recompile with my driver selected as a module. For some reason the configuration i copied did not transfer the wireless card.

Running the command "lspci -v | less" at the terminal prompt tells me that the wireless card is RTL8101E/RTL8102D.  I'm not sure why there are 2 numbers separated by a slash.

I would love to run the fix which you have used, if you want to tell me how to do it.  But, if you are willing, you will have to be specific.  I can follow instructions, but I can't figure this stuff out myself.

I solved my network problem.  Somehow the smb.conf file got completely corrupted. I restored the back-up, changed the name of the workgroup, and everything works fine.  The disabled wireless is the only remaining problem.

Bob

---

### Post by Lykopis on 2010-05-08
> **wnemay said:**
> I have a Toshiba L505 laptop, and have had nothing but trouble installing Ubuntu 9.10 or 10.04 on it.  I finally figured it out and made a quick writeup to help others with this problem.  ACPI=OFF is not the way to go, it causes a lot of other issues.  You want ACPI=HT.
[http://www.wnemay.com/2010/linux/ubuntu-10-04-with-acpi-issue-on-my-toshiba-l505-laptop]("http://www.wnemay.com/2010/linux/ubuntu-10-04-with-acpi-issue-on-my-toshiba-l505-laptop/")/

While acpi=ht will get both cores to function all other acpi functoins remain off including fan and thermal. Frequency scaling is disabled so the cores run at full speed at all times, highly risking thermal damage. sooner or later you will damage you laptop with acpi=ht. Just don't do it! Do it the right way and complie or have someone compile a kernel with the "copy_dsdt" patch. I use the patch and it works. My cores rest at 800 Mhz and jump to 2 Ghz under load. the fans power on and off indicating acpi is at least mostly working.
Don't look for a short cut with this issue because you will pay in the end if you do.

---

### Post by Linux_Lurker on 2010-05-09
To those having Lucid networking problems:

Lucid borks the network on all of my computers, even my desktop I built myself, that had otherwise been working fine.   Lucid made some major changes to the networking(that "Upstart" application).

My L505D laptop is still running 32bit Ubuntu 9.10 + vanilla 2.6.32.9 kernel, with automatic updates turned off, I probably won't upgrade to any OS until this patch is included in a stock kernel.  I think that Karmic + 2.6.32.9 is the best combination for L505D, everything works, whereas I just can't justify recommending Lucid or 2.6.33 at this point in time.   

I switched my desktop PC to OpenSuse for now, despite my feelings about Novell and Microsoft collaboration and licensing agreements.   I wanted to love Fedora, but I found it to be unstable beyond reason.

---

### Post by rdingraham on 2010-05-09
I have now gotten the wireless working by following the instructions located at [http://www.linwik.com/wiki/using+the+realtek+8172+and+8192se+wireless+control ler+with+ubuntu+9.10]("http://www.linwik.com/wiki/using+the+realtek+8172+and+8192se+wireless+control ler+with+ubuntu+9.10")

So, except for the touchpad which I never use, I now have a fully functioning 64 bit Ubuntu 10.4 running on a Toshiba Satellite L505D.

For those new to this thread, this involved 4 steps.

1) First, with the help of colinwhipple (see [http://ubuntuforums.org/showthread.php?t=1460445&highlight=ingraham]("http://ubuntuforums.org/showthread.php?t=1460445&highlight=ingraham")), I figured out how to get past the error screen using ACPI=off.

2) Following precisely ivanmmj's instructions in post #71 of this thread, I installed the dsdt patch and compiled a new kernel.

3) Following sbaily85's instructions in posts #198 through #202 of this thread, I inserted the initrd file.

4) With the help of chili555 (see [http://ubuntuforums.org/showthread.php?p=9264406#post9264406]("http://ubuntuforums.org/showthread.php?p=9264406#post9264406")), and using the instructions from [http://www.linwik.com/wiki/using+the+realtek+8172+and+8192se+wireless+control ler+with+ubuntu+9.10]("http://www.linwik.com/wiki/using+the+realtek+8172+and+8192se+wireless+control ler+with+ubuntu+9.10"), I installed a module for the wireless.

Everything works, even the little web cam thingy.

Toshiba can go to hell.

A big thank you to everyone, and for anyone else with the same problem, if you carefully follow all of the instructions, it should work for you.

Bob I.

---

### Post by HeX0R on 2010-05-10
Hi rdingraham,
i just tried to install Ubuntu 10.04 64bit on my A505-s6033.
but after i followed ivanmmj's instructions i gut a "Kernal panik" error...

can i do something with this? 
BTW, you can see the battery status?

Thanks a lot!

---

### Post by rdingraham on 2010-05-10
> **HeX0R said:**
> Hi rdingraham,
i just tried to install Ubuntu 10.04 64bit on my A505-s6033.
but after i followed ivanmmj's instructions i gut a "Kernal panik" error...

can i do something with this? 
BTW, you can see the battery status?

Thanks a lot!

I am not the best person to give advice.  My technical knowledge of these matters is limited.  However, I also got a "kernel panic" message after installing the the new custom kernel.  Step #3 from my previous post (inputting the initrd file) solved that problem. Boot back into Ubuntu with acpi=off and do step #3.

Yes, I can see the battery, the heat sensors, everything.

Bob I.

---

### Post by HeX0R on 2010-05-10
> **rdingraham said:**
> 

Yes, I can see the battery, the heat sensors, everything.

Bob I.

Yeeeeeeeeeee.... i will try this tomorrow i hope i will be success...

BTW, in step 2, you did all the compile thing? or you just installed the .deb files that ivanmmj compiled & uploaded?
i ask because i already did that and this toke many hours and i formated the Ubuntu partition after the panic error...
But I kept a copy of these two files ... so... i am have to do this whole process or just install those to deb files??
or maybe to install deb files that ivanmmj uploaded, or i will cant install them, i think those a 32 bit files.... 
Thank you!!!

---

### Post by rdingraham on 2010-05-10
> **HeX0R said:**
> Yeeeeeeeeeee.... i will try this tomorrow i hope i will be success...

BTW, in step 2, you did all the compile thing? or you just installed the .deb files that ivanmmj compiled & uploaded?
i ask because i already did that and this toke many hours and i formated the Ubuntu partition after the panic error...

I did the complete compile of the kernel.  Took me about 1 1/2 to 2 hours. Others may know how to do it faster.  When it is finished recompiling, it gives you 2 NEW deb files (which are listed right before the end of the compiling process in the terminal window).  Those are the ones I installed.  In my case they are named linux-headers-2.6.32.4-l505d_2.6.32.4-l505d-10.00.Custom_amd64.deb and linux-image-2.6.32.4-l505d_2.6.32.4-l505d-10.00.Custom_amd64.deb

Others have done it in other ways, but this is what worked for me. Note, even after installing the new deb files, I still needed to do the initrd thing for the whole thing to work.  

Bob

---

### Post by sbailey85 on 2010-05-10
Here is a link to my compiled kernel deb files. This is for a toshiba l505-s5983 wireless and everything is working good 

[http://dl.dropbox.com/u/6916351/linux-headers-2.6.33.3-l505d_2.6.33.3-l505d-10.00.Custom_amd64.deb](http://dl.dropbox.com/u/6916351/linux-headers-2.6.33.3-l505d_2.6.33.3-l505d-10.00.Custom_amd64.deb)

[http://dl.dropbox.com/u/6916351/linux-image-2.6.33.3-l505d_2.6.33.3-l505d-10.00.Custom_amd64.deb](http://dl.dropbox.com/u/6916351/linux-image-2.6.33.3-l505d_2.6.33.3-l505d-10.00.Custom_amd64.deb)

This is for 64bit in case you didn't notice in the file name

---

### Post by tinnyskillz on 2010-05-11
Can Someone Please Compile Ubuntu 10.04 Kernel Deb Files For The Toshiba L505D-S5983 32Bit. I Do Not Know How To Compile It Myself. I Would Really Appreciate It. :confused:

---

### Post by sbailey85 on 2010-05-12
> **tinnyskillz said:**
> Can Someone Please Compile Ubuntu 10.04 Kernel Deb Files For The Toshiba L505D-S5983 32Bit. I Do Not Know How To Compile It Myself. I Would Really Appreciate It. :confused:
pg 8 of this thread has the easiest instructions i have seen in regards to compiling an ubuntu kernel and creating deb files.

---

### Post by HeX0R on 2010-05-12
@rdingraham,
Can you PLEASE write the directly instruction you wrote to get it work?
i got lost here...

for some reason the X server dosent wont to run and i asked for my login before any GUI was appear...  

am i mention that i new to linux!?!?


-Is there a way that i can use my DEB files i compiled earlier?  
or not matter what i need to compile those thing...

BTW, what those deb files at all?

Thanks!

---

### Post by HeX0R on 2010-05-13
> **HeX0R said:**
> @rdingraham,
Can you PLEASE write the directly instruction you wrote to get it work?
i got lost here...

for some reason the X server dosent wont to run and i asked for my login before any GUI was appear...  

am i mention that i new to linux!?!?


-Is there a way that i can use my DEB files i compiled earlier?  
or not matter what i need to compile those thing...

BTW, what those deb files at all?

Thanks!
Yee... i dune its all from scratch and now all working properly...
even the touch pad on/off button...

Thank you all!!!!!!!!

BTW, how can i check the web cam?!

---

### Post by tee_eff_em on 2010-05-13
I am just about set to take a stab at (nervously) rolling my own kernel, but before I  do, I thought I would ask:
> **sbailey85 said:**
> Here is a link to my compiled kernel deb files. This is for a toshiba l505-s5983 wireless and everything is working good 

[http://dl.dropbox.com/u/6916351/linux-headers-2.6.33.3-l505d_2.6.33.3-l505d-10.00.Custom_amd64.deb](http://dl.dropbox.com/u/6916351/linux-headers-2.6.33.3-l505d_2.6.33.3-l505d-10.00.Custom_amd64.deb)

[http://dl.dropbox.com/u/6916351/linux-image-2.6.33.3-l505d_2.6.33.3-l505d-10.00.Custom_amd64.deb](http://dl.dropbox.com/u/6916351/linux-image-2.6.33.3-l505d_2.6.33.3-l505d-10.00.Custom_amd64.deb)

This is for 64bit in case you didn't notice in the file name

When I use this kernel, the boot stops on a backtrace (I don't know which log, if any, to retrieve it from) -- What kernel switches (if any) should I be using with this kernel?

In the meantime, I can continue to use:

[LIST]
[*]the l505d-speed kernel from [post=8704230]post #79[/post] with "pci=noacpi pci=assign-busses", but the touchpad is "jumpy" which is annoying
[*]or the most recent non-tweaked Lucid kernel (2.6.32.something?) with "acpi=off", with tolerable touchpad behavior, but only one processor, no fan, no battery meter, et cetera
[/LIST]


Thanks for any assistance!

---

### Post by rdingraham on 2010-05-15
> **HeX0R said:**
> Yee... i dune its all from scratch and now all working properly...
even the touch pad on/off button...

Thank you all!!!!!!!!

BTW, how can i check the web cam?!

Install Cheese Webcam from the Software Center. Very easy to use.

Congratulations on getting it all working.

Bob I.

---

### Post by ki-84 on 2010-05-16
HI Everybody... I've been following this thread for a while and up to this weekend, I found the courage to install Ubuntu in this laptop. My Laptop is a Satellite L505D-S986, and since I didn't research enough I bought it thinking that will be no problem installing Linux. My level in Linux is kind of Amateur-ish...

Anyway........ long history short I followed the same instructions from rdingraham with Lucid 64bits.

> **rdingraham said:**
> 
For those new to this thread, this involved 4 steps.

1) First, with the help of colinwhipple (see [http://ubuntuforums.org/showthread.php?t=1460445&highlight=ingraham](http://ubuntuforums.org/showthread.php?t=1460445&highlight=ingraham)), I figured out how to get past the error screen using ACPI=off.

2) Following precisely ivanmmj's instructions in post #71 of this thread, I installed the dsdt patch and compiled a new kernel.

3) Following sbaily85's instructions in posts #198 through #202 of this thread, I inserted the initrd file.

Toshiba can go to hell.

A big thank you to everyone, and for anyone else with the same problem, if you carefully follow all of the instructions, it should work for you.

Bob I.

Since I compiled it with Kernel 2.6.32.13, there was no problem with my wireless card. But... I did have a problem with the graphic card.

Apparently, Jockey doesn't find the fglrx module, and Abort the process. I already install the damn module from Software Center, and I even installed the Catalyst from ATI with no results.

This is the log generated when I'm try to install it.

```

Errors during DKMS module removal
Errors during DKMS module removal

Creating symlink /var/lib/dkms/fglrx/8.723/source ->
                 /usr/src/fglrx-8.723

DKMS: add Completed.
You can use the --kernelsourcedir option to tell DKMS where it's located, or you could install the linux-headers-2.6.32.13-l505d package.
[Error] Kernel Module : Failed to build fglrx-8.723 with DKMS
[Error] Kernel Module : Removing fglrx-8.723 from DKMS

------------------------------
Deleting module version: 8.723
completely from the DKMS tree.
------------------------------
Done.

```

Since the kernel is modified, I'm thinking I didn't do it right enough. My Video Card is the ATI HD4200.

Has anybody had this problem with this new kernel compiled, if it was, can somebody explain me what to do.

By the way, thank you everybody for making this patch and instructions. This has been a long road, I'm hoping kernel 2.6.34 have this patch integrated and get supported by Ubuntu.

Long live to Linux, and I'm also agree, Toshiba can go to HELL

---

### Post by ojhologram on 2010-05-16
Thanks sbailey85, your compiled kernel works very very good! ...I have a Toshiba L505D-SP6905R. 

> **sbailey85 said:**
> Here is a link to my compiled kernel deb files. This is for a toshiba l505-s5983 wireless and everything is working good 

[http://dl.dropbox.com/u/6916351/linux-headers-2.6.33.3-l505d_2.6.33.3-l505d-10.00.Custom_amd64.deb](http://dl.dropbox.com/u/6916351/linux-headers-2.6.33.3-l505d_2.6.33.3-l505d-10.00.Custom_amd64.deb)

[http://dl.dropbox.com/u/6916351/linux-image-2.6.33.3-l505d_2.6.33.3-l505d-10.00.Custom_amd64.deb](http://dl.dropbox.com/u/6916351/linux-image-2.6.33.3-l505d_2.6.33.3-l505d-10.00.Custom_amd64.deb)

This is for 64bit in case you didn't notice in the file name

---

### Post by hardwired112 on 2010-05-16
> **ivanmmj said:**
> Here's a quick walkthrough on how to compile your own:

(But the one posted above should work fine for all ubuntu 9.10 based systems.)


Right click on [http://bugzilla.kernel.org/attachment.cgi?id=23958](http://bugzilla.kernel.org/attachment.cgi?id=23958) and save it to your desktop.

```
sudo -s
apt-get update
apt-get install kernel-package libncurses5-dev fakeroot wget bzip2
cd /usr/src
```For 9.10:
```
wget http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.31.12.tar.bz2
tar xjf linux-2.6.31.12.tar.bz2
ln -s linux-2.6.31.12 linux
```For 10.04
```
wget http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.32.4.tar.bz2
tar xjf linux-2.6.32.4.tar.bz2
ln -s linux-2.6.32.4 linux
``````

cd /usr/src/linux
patch -p1 < ~/Desktop/bug14679_copy_dsdt.patch
cp /boot/config-`uname -r` ./.config 
make menuconfig
```NOTE: That's p1 as in the number ONE, not a lower case L.
-Load an Alternate Configuration File
-Hit OK
-Exit
-Hit Yes

```
make-kpkg clean
fakeroot make-kpkg --initrd --append-to-version=-l505d kernel_image kernel_headers
cd /usr/src
ls -l
nautilus /usr/src
```Then install both deb files in there.

Make sure that you remove any extra Grub kernel switches you've added.

Hey guys. I installed ubuntu 10.04 on my L505D laptop, and of course disabling acpi allows ubuntu to boot.

I am a linux novice, and part of the instructions here confused me. everything else seems pretty self explanatory, but what does this mean:

"Then install both deb files in there."

---

### Post by colinwhipple on 2010-05-16
> **hardwired112 said:**
> Hey guys. I installed ubuntu 10.04 on my L505D laptop, and of course disabling acpi allows ubuntu to boot.

I am a linux novice, and part of the instructions here confused me. everything else seems pretty self explanatory, but what does this mean:

"Then install both deb files in there."

In Nautilus, click on the header file and then the image file, and the package installer should bring them up.  You should then have a button that says "Install Package".

Colin

---

### Post by hardwired112 on 2010-05-16
now that i think about it i think i have misinterpreted that post. i am not trying to compile my own, im trying to install the kernel/patch. i have downloaded the following three files from

[http://www.ramoonus.nl/2009/12/03/linux-kernel-2-6-32-installation-guide-for-ubuntu-linux/](http://www.ramoonus.nl/2009/12/03/linux-kernel-2-6-32-installation-guide-for-ubuntu-linux/)

linux-headers-2.6.32-020632_2.6.32-020632_all
linux-headers-2.6.32-020632-generic_2.6.32-020632_i386
linux-image-2.6.32-020632-generic_2.6.32-020632_i386

all i need to do is sudo dpkg -i <filename> right?

Also, that page says DKMS automatically installs nvidia drivers. I have an amd video card. is that going to cause a problem?

Thank you so much in advance for any help you might be able to provide. I am literally lost when it comes to linux.

---

### Post by colinwhipple on 2010-05-16
> **hardwired112 said:**
> now that i think about it i think i have misinterpreted that post. i am not trying to compile my own, im trying to install the patch. i have downloaded the following three files from

[http://www.ramoonus.nl/2009/12/03/linux-kernel-2-6-32-installation-guide-for-ubuntu-linux/](http://www.ramoonus.nl/2009/12/03/linux-kernel-2-6-32-installation-guide-for-ubuntu-linux/)

linux-headers-2.6.32-020632_2.6.32-020632_all
linux-headers-2.6.32-020632-generic_2.6.32-020632_i386
linux-image-2.6.32-020632-generic_2.6.32-020632_i386

all i need to do is sudo dpkg -i <filename> right?

I don't think you can patch already-compiled files.  You patch the source code, then compile the patched code.

Colin

---

### Post by hardwired112 on 2010-05-16
im sorry. i think what i meant to say was install the kernel.

---

### Post by colinwhipple on 2010-05-16
> **hardwired112 said:**
> im sorry. i think what i meant to say was install the kernel.

I use Nautilus (as root) to install the kernel (the header and image files).  Click on the files, and it brings up the Installer.  Very simple, which suits me just fine.

Colin

---

### Post by hardwired112 on 2010-05-17
i installed the three deb packages in the order it said to and did grub-update, and restarted. the new kernel was added to grub, but did not fix the issue... any other suggestions?

i have a toshiba L505D laptop, it will not boot unless ACPI is disabled... i refuse to keep acpi disabled permanently, it just cannot be good for my hardware.

---

### Post by m00nraker on 2010-05-17
I too could not get the deb files to boot so i compiled a kernel and that did not work either.  I compiled my own kernel for 9.10 and everything worked on the first boot.  I thought the toshiba anti-linux roller coaster was over for me but i guess that i was wrong.

---

### Post by colinwhipple on 2010-05-17
> **hardwired112 said:**
> i installed the three deb packages in the order it said to and did grub-update, and restarted. the new kernel was added to grub, but did not fix the issue... any other suggestions?

i have a toshiba L505D laptop, it will not boot unless ACPI is disabled... i refuse to keep acpi disabled permanently, it just cannot be good for my hardware.

If you installed the files your previous message stated, it wouldn't work.  You have to patch and compile source code according to Ivan's instructions, and then install the compiled files.

Colin

---

### Post by ericwwheeler on 2010-05-18
I tried the instructions for the 10.4 on a friend's new L505d-s5983 and got the following output:

kathy@kathy-desktop:/usr/src/linux$ cp /boot/config-`uname -r` ./.config 
cp: cannot create regular file `./.config': Permission denied
kathy@kathy-desktop:/usr/src/linux$ make menuconfig
make: *** No rule to make target `menuconfig'.  Stop.
kathy@kathy-desktop:/usr/src/linux$ sudo -s
root@kathy-desktop:/usr/src/linux# cd /usr/src/linux
root@kathy-desktop:/usr/src/linux# patch -p1 < ~/Desktop/bug14679_copy_dsdt.patch
patching file drivers/acpi/acpica/tbxface.c
Hunk #1 FAILED at 55.
Hunk #2 FAILED at 486.
Hunk #3 FAILED at 496.
Hunk #4 FAILED at 533.
4 out of 4 hunks FAILED -- saving rejects to file drivers/acpi/acpica/tbxface.c.rej
root@kathy-desktop:/usr/src/linux# cp /boot/config-`uname -r` ./.config 
root@kathy-desktop:/usr/src/linux# make menuconfig
make: *** No rule to make target `menuconfig'.  Stop.
root@kathy-desktop:/usr/src/linux# wget [http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.32.4.tar.bz2](http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.32.4.tar.bz2)
--2010-05-18 12:10:30--  [http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.32.4.tar.bz2](http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.32.4.tar.bz2)
Resolving [www.kernel.org](www.kernel.org)... 204.152.191.37, 149.20.20.133
Connecting to [www.kernel.org|204.152.191.37|:80](www.kernel.org|204.152.191.37|:80)... connected.
HTTP request sent, awaiting response... 200 OK
Length: 64372500 (61M) [application/x-bzip2]
Saving to: `linux-2.6.32.4.tar.bz2'

100%[======================================>] 64,372,500   475K/s   in 3m 14s  

2010-05-18 12:13:45 (325 KB/s) - `linux-2.6.32.4.tar.bz2' saved [64372500/64372500]

root@kathy-desktop:/usr/src/linux# tar xjf linux-2.6.32.4.tar.bz2

root@kathy-desktop:/usr/src/linux# ln -s linux-2.6.32.4 linux
root@kathy-desktop:/usr/src/linux# cd /usr/src/linux
root@kathy-desktop:/usr/src/linux# patch -p1 < ~/Desktop/bug14679_copy_dsdt.patch
patching file drivers/acpi/acpica/tbxface.c
Hunk #1 FAILED at 55.
Hunk #2 FAILED at 486.
Hunk #3 FAILED at 496.
Hunk #4 FAILED at 533.
4 out of 4 hunks FAILED -- saving rejects to file drivers/acpi/acpica/tbxface.c.rej
root@kathy-desktop:/usr/src/linux# cp /boot/config-`uname -r` ./.config 
root@kathy-desktop:/usr/src/linux# make menuconfig
make: *** No rule to make target `menuconfig'.  Stop.
root@kathy-desktop:/usr/src/linux# cp /boot/config-`linux-2.6.32.4` ./.config
linux-2.6.32.4: command not found
cp: cannot stat `/boot/config-': No such file or directory
root@kathy-desktop:/usr/src/linux# make-kpkg clean
The program 'make-kpkg' is currently not installed.  You can install it by typing:
apt-get install kernel-package
root@kathy-desktop:/usr/src/linux# fakeroot make-kpkg --initrd --append-to-version=-l505d kernel_image kernel_headers
/usr/bin/fakeroot: line 176: make-kpkg: command not found
root@kathy-desktop:/usr/src/linux# cd /usr/src
root@kathy-desktop:/usr/src# ls -l
total 28
drwxr-xr-x  4 root root 4096 2010-05-18 10:55 fglrx-8.723.1
drwxr-sr-x  4 root src  4096 2010-05-18 12:14 linux
drwxr-xr-x 24 root root 4096 2010-04-29 07:44 linux-headers-2.6.32-21
drwxr-xr-x  7 root root 4096 2010-04-29 07:45 linux-headers-2.6.32-21-generic
drwxr-xr-x 24 root root 4096 2010-05-18 11:11 linux-headers-2.6.32-22
drwxr-xr-x  7 root root 4096 2010-05-18 11:12 linux-headers-2.6.32-22-generic
drwxr-xr-x 23 root root 4096 2010-05-18 11:41 linux-headers-2.6.33.3-l505d
root@kathy-desktop:/usr/src# nautilus /usr/src

Is there any way you could help me figure out what I need to do to get this laptop patched.  I have minimal compiling experience, obviously.  I have tried numerous times to do this and have re-installed a few times to start the instructions over, any help would be greatly appreciated.

---

### Post by colinwhipple on 2010-05-18
One general suggestion:  I copy and pasted Ivan's commands into a text file which I saved, and then repasted them as needed into a terminal window when I was doing the compile.  I only typed into the terminal window the very simple ones that I was unlikely to type incorrectly.

After you did:

sudo -s

Did you do these commands:

apt-get update
apt-get install kernel-package libncurses5-dev fakeroot wget bzip2

Your error messages suggest you didn't, or maybe left out a portion.

Is the patch file in the desktop?

I am no expert on this stuff.  You will be better off if someone else jumps in  with help.

Colin

---

### Post by wildcard_seven on 2010-05-18
Hey guys.  

If you are open to an alternative, and willing to rot your freaking eyes out reading manuals and scouring forums, you might try openBSD. It's another UNIX flavor that installs perfectly and cleanly on this laptop. 


[IMG]http://www.mtv.com/content/ontv/movieawards/2008/images/flipbooks/2008-highlights/flipbook/06_waynes-world-garth.jpg[/IMG]

:guitar::guitar::guitar::guitar:

---

### Post by ericwwheeler on 2010-05-19
> **colinwhipple said:**
> One general suggestion:  I copy and pasted Ivan's commands into a text file which I saved, and then repasted them as needed into a terminal window when I was doing the compile.  I only typed into the terminal window the very simple ones that I was unlikely to type incorrectly.

After you did:

sudo -s

Did you do these commands:

apt-get update
apt-get install kernel-package libncurses5-dev fakeroot wget bzip2

Your error messages suggest you didn't, or maybe left out a portion.

Is the patch file in the desktop?

I am no expert on this stuff.  You will be better off if someone else jumps in  with help.

Colin
I did not see those commands-I am running those now and will go through the instructions again. Yes I do have the patch file on the Desktop

---

### Post by ericwwheeler on 2010-05-19
Hey Colin

I did the apt-get update and installed that kernel-package stuff successfully and then tried the post #71 procedure again and got this output:

root@kathy-desktop:~# wget [http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.32.4.tar.bz2](http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.32.4.tar.bz2)
--2010-05-19 22:15:18--  [http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.32.4.tar.bz2](http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.32.4.tar.bz2)
Resolving [www.kernel.org](www.kernel.org)... 149.20.20.133, 204.152.191.37
Connecting to [www.kernel.org|149.20.20.133|:80](www.kernel.org|149.20.20.133|:80)... connected.
HTTP request sent, awaiting response... 200 OK
Length: 64372500 (61M) [application/x-bzip2]
Saving to: `linux-2.6.32.4.tar.bz2.1'

100%[======================================>] 64,372,500   286K/s   in 5m 16s  

2010-05-19 22:20:35 (199 KB/s) - `linux-2.6.32.4.tar.bz2.1' saved [64372500/64372500]

root@kathy-desktop:~# tar xjf linux-2.6.32.4.tar.bz2
root@kathy-desktop:~# ln -s linux-2.6.32.4 linux
root@kathy-desktop:~# cd /usr/src/linux
root@kathy-desktop:/usr/src/linux# patch -p1 < ~/Desktop/bug14679_copy_dsdt.patch
patching file drivers/acpi/acpica/tbxface.c
Hunk #1 FAILED at 55.
Hunk #2 FAILED at 486.
Hunk #3 FAILED at 496.
Hunk #4 FAILED at 533.
4 out of 4 hunks FAILED -- saving rejects to file drivers/acpi/acpica/tbxface.c.rej
root@kathy-desktop:/usr/src/linux# 

I can't figure out why it is failing to work, I'm glad this is not my laptop because it would be finding a new home.  I appreciate all the work that has gone into the post as well as your response.
Eric

---

### Post by colinwhipple on 2010-05-20
> **ericwwheeler said:**
> Hey Colin

I did the apt-get update and installed that kernel-package stuff successfully and then tried the post #71 procedure again and got this output:

root@kathy-desktop:~# wget [http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.32.4.tar.bz2](http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.32.4.tar.bz2)
--2010-05-19 22:15:18--  [http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.32.4.tar.bz2](http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.32.4.tar.bz2)
Resolving [www.kernel.org](www.kernel.org)... 149.20.20.133, 204.152.191.37
Connecting to [www.kernel.org|149.20.20.133|:80](www.kernel.org|149.20.20.133|:80)... connected.
HTTP request sent, awaiting response... 200 OK
Length: 64372500 (61M) [application/x-bzip2]
Saving to: `linux-2.6.32.4.tar.bz2.1'

100%[======================================>] 64,372,500   286K/s   in 5m 16s  

2010-05-19 22:20:35 (199 KB/s) - `linux-2.6.32.4.tar.bz2.1' saved [64372500/64372500]

root@kathy-desktop:~# tar xjf linux-2.6.32.4.tar.bz2
root@kathy-desktop:~# ln -s linux-2.6.32.4 linux
root@kathy-desktop:~# cd /usr/src/linux
root@kathy-desktop:/usr/src/linux# patch -p1 < ~/Desktop/bug14679_copy_dsdt.patch
patching file drivers/acpi/acpica/tbxface.c
Hunk #1 FAILED at 55.
Hunk #2 FAILED at 486.
Hunk #3 FAILED at 496.
Hunk #4 FAILED at 533.
4 out of 4 hunks FAILED -- saving rejects to file drivers/acpi/acpica/tbxface.c.rej
root@kathy-desktop:/usr/src/linux# 

I can't figure out why it is failing to work, I'm glad this is not my laptop because it would be finding a new home.  I appreciate all the work that has gone into the post as well as your response.
Eric

You need to do the wget command after you change to the /usr/src directory.  The source code file will end up in the directory you issue that command from.  You are saving it in the wrong place the way you are doing it.  Doing things in the right order is very important.

---

### Post by wildcard_seven on 2010-05-20
anybody try 10.04?

---

### Post by Lykopis on 2010-05-20
> **wildcard_seven said:**
> anybody try 10.04?
Yes 10.04 has the same issues with this hardware.
I run 10.04 and had to build a kernel with the copy_dsdt patch.

Edit:
I believe all Toshiba A505 & L505d's will have this dsdt problem.

---

### Post by tee_eff_em on 2010-05-20
> **tee_eff_em said:**
> I am just about set to take a stab at (nervously) rolling my own kernel, but before I  do, I thought I would ask:


When I use this kernel, the boot stops on a backtrace (I don't know which log, if any, to retrieve it from) -- What kernel switches (if any) should I be using with this kernel?

In the meantime, I can continue to use:

[LIST]
[*]the l505d-speed kernel from [post=8704230]post #79[/post] with "pci=noacpi pci=assign-busses", but the touchpad is "jumpy" which is annoying
[*]or the most recent non-tweaked Lucid kernel (2.6.32.something?) with "acpi=off", with tolerable touchpad behavior, but only one processor, no fan, no battery meter, et cetera
[/LIST]


Thanks for any assistance!

Well, FTR I did compile a kernel (2.6.33.4) with the copy_dsdt patch, but still could not run it -- I forget now whether it was the same condition as the second bullet above, or a just plain kernel panic. :(

Soooooo, I spent the better part of a day re-installing 9.10, and am happily back to using the -l505d-speed kernel (with a non-"jumpy" touchpad).

[SIZE=1]Aside: Is there a "right" way to get rid of old kernels that still reside under /boot and in the grub menu, but dpkg no longer recognizes as being installed? Thanks.[/SIZE]

---

### Post by Lykopis on 2010-05-20
> **tee_eff_em said:**
> [SIZE=1] Aside: Is there a "right" way to get rid of old kernels that still reside under /boot and in the grub menu, but dpkg no longer recognizes as being installed? Thanks.[/SIZE] 
 you might try the update-grub command.
I think about the only other thing you could do is edit grub manually.

---

### Post by colinwhipple on 2010-05-20
> **tee_eff_em said:**
> Well, FTR I did compile a kernel (2.6.33.4) with the copy_dsdt patch, but still could not run it -- I forget now whether it was the same condition as the second bullet above, or a just plain kernel panic. :(

Soooooo, I spent the better part of a day re-installing 9.10, and am happily back to using the -l505d-speed kernel (with a non-"jumpy" touchpad).

[SIZE=1]Aside: Is there a "right" way to get rid of old kernels that still reside under /boot and in the grub menu, but dpkg no longer recognizes as being installed? Thanks.[/SIZE]

Do they show up in Synaptic as still installed?  They can be uninstalled from there.

Colin

---

### Post by ericwwheeler on 2010-05-21
> **colinwhipple said:**
> You need to do the wget command after you change to the /usr/src directory.  The source code file will end up in the directory you issue that command from.  You are saving it in the wrong place the way you are doing it.  Doing things in the right order is very important.

Hey Colin,

I tried the wget command and here is the output:

root@kathy-desktop:/usr/src/linux# wget patch -p1 < ~/Desktop/bug14679_copy_dsdt.patch
wget: invalid option -- '1'
Usage: wget [OPTION]... [URL]...

Try `wget --help' for more options.
root@kathy-desktop:/usr/src/linux# patch -p1 < ~/Desktop/bug14679_copy_dsdt.patch
patching file drivers/acpi/acpica/tbxface.c
Hunk #1 FAILED at 55.
Hunk #2 FAILED at 486.
Hunk #3 FAILED at 496.
Hunk #4 FAILED at 533.
4 out of 4 hunks FAILED -- saving rejects to file drivers/acpi/acpica/tbxface.c.rej
root@kathy-desktop:/usr/src/linux# wget
wget: missing URL
Usage: wget [OPTION]... [URL]...

Try `wget --help' for more options.
root@kathy-desktop:/usr/src/linux# :confused:


I will keep trying till I get this fixed or yall get tired of trying to help :)

---

### Post by colinwhipple on 2010-05-21
The wget command should have been used from the /usr/src directory, not from the /usr/src/linux directory.  And it should have been used on the linux source file, not the patch file.

Assuming the patch file is already on your desk top (is it visible there?), the following is the complete procedure I used from within a terminal window:

sudo -s
apt-get update
apt-get install kernel-package libncurses5-dev fakeroot wget bzip2


cd /usr/src
ls -l
rm linux

wget [http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.32.4.tar.bz2](http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.32.4.tar.bz2)
tar xjf linux-2.6.32.4.tar.bz2
ln -s linux-2.6.32.4 linux
chown -R root:root linux-2.6.32.4

cd /usr/src/linux
patch -p1 < ~/Desktop/bug14679_copy_dsdt.patch
cp /boot/config-`uname -r` ./.config 
make menuconfig

-Load an Alternate Configuration File
-Hit OK
-Exit
-Hit Yes

make-kpkg clean
fakeroot make-kpkg --initrd --append-to-version=-l505d kernel_image kernel_headers
cd /usr/src
ls -l
nautilus /usr/src

From within Nautilus both the header and image files should be visible.

Double-click on the header file and the Package Installer should open. Click on Install Package and wait for it to install.  Then Close the Installer.  

Double-click on the image file and the Package Installer should open again.  Click on Install Package and wait for it to install.  Then Close the Installer.

You should then be able to reboot and choose the patched kernel.

Colin

---

### Post by ericwwheeler on 2010-05-21
root@kathy-desktop:~# apt-get install kernel-package libncurses5-dev fakeroot wget bzip2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
kernel-package is already the newest version.
libncurses5-dev is already the newest version.
fakeroot is already the newest version.
wget is already the newest version.
bzip2 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 8 not upgraded.
root@kathy-desktop:~# cd /usr/src
root@kathy-desktop:/usr/src# ls -l
total 28
drwxr-xr-x  4 root root 4096 2010-05-18 10:55 fglrx-8.723.1
drwxr-sr-x  4 root src  4096 2010-05-18 12:14 linux
drwxr-xr-x 24 root root 4096 2010-04-29 07:44 linux-headers-2.6.32-21
drwxr-xr-x  7 root root 4096 2010-04-29 07:45 linux-headers-2.6.32-21-generic
drwxr-xr-x 24 root root 4096 2010-05-18 11:11 linux-headers-2.6.32-22
drwxr-xr-x  7 root root 4096 2010-05-18 11:12 linux-headers-2.6.32-22-generic
drwxr-xr-x 23 root root 4096 2010-05-18 11:41 linux-headers-2.6.33.3-l505d
root@kathy-desktop:/usr/src# rm linux
rm: cannot remove `linux': Is a directory
root@kathy-desktop:/usr/src# wget [http://www.kernel.org/pub/linux/kernel/v.26/linux-2.6.32.4.tar.bz2](http://www.kernel.org/pub/linux/kernel/v.26/linux-2.6.32.4.tar.bz2)
--2010-05-21 19:50:27--  [http://www.kernel.org/pub/linux/kernel/v.26/linux-2.6.32.4.tar.bz2](http://www.kernel.org/pub/linux/kernel/v.26/linux-2.6.32.4.tar.bz2)
Resolving [www.kernel.org](www.kernel.org)... 149.20.20.133, 204.152.191.37
Connecting to [www.kernel.org|149.20.20.133|:80](www.kernel.org|149.20.20.133|:80)... connected.
HTTP request sent, awaiting response... 404 Not Found
2010-05-21 19:50:28 ERROR 404: Not Found.

root@kathy-desktop:/usr/src# wget [http://www.kernel.org/pub/linux/kern...6.32.4.tar.bz2](http://www.kernel.org/pub/linux/kern...6.32.4.tar.bz2)
--2010-05-21 19:53:55--  [http://www.kernel.org/pub/linux/kern...6.32.4.tar.bz2](http://www.kernel.org/pub/linux/kern...6.32.4.tar.bz2)
Resolving [www.kernel.org](www.kernel.org)... 149.20.20.133, 204.152.191.37
Connecting to [www.kernel.org|149.20.20.133|:80](www.kernel.org|149.20.20.133|:80)... connected.
HTTP request sent, awaiting response... 404 Not Found
2010-05-21 19:53:55 ERROR 404: Not Found.

root@kathy-desktop:/usr/src# tar xjf linux-2.6.32.4.tar.bz2
tar: linux-2.6.32.4.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Exiting with failure status due to previous errors
root@kathy-desktop:/usr/src# wget [http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.32.4.tar.bz2](http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.32.4.tar.bz2)
--2010-05-21 19:57:47--  [http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.32.4.tar.bz2](http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.32.4.tar.bz2)
Resolving [www.kernel.org](www.kernel.org)... 149.20.20.133, 204.152.191.37
Connecting to [www.kernel.org|149.20.20.133|:80](www.kernel.org|149.20.20.133|:80)... connected.
HTTP request sent, awaiting response... 200 OK
Length: 64372500 (61M) [application/x-bzip2]
Saving to: `linux-2.6.32.4.tar.bz2'

100%[======================================>] 64,372,500   602K/s   in 2m 59s  

2010-05-21 20:00:47 (352 KB/s) - `linux-2.6.32.4.tar.bz2' saved [64372500/64372500]

root@kathy-desktop:/usr/src# ln -s linux-2.6.32.4 linux
ln: creating symbolic link `linux/linux-2.6.32.4': File exists
root@kathy-desktop:/usr/src# chown -R root:root linux-2.6.32.4
chown: cannot access `linux-2.6.32.4': No such file or directory
root@kathy-desktop:/usr/src# 

Hey Colin, not sure why 'File exists' then 'No such file or directory'  got any ideas why that might be?

---

### Post by colinwhipple on 2010-05-21
> **ericwwheeler said:**
> root@kathy-desktop:~# apt-get install kernel-package libncurses5-dev fakeroot wget bzip2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
kernel-package is already the newest version.
libncurses5-dev is already the newest version.
fakeroot is already the newest version.
wget is already the newest version.
bzip2 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 8 not upgraded.
root@kathy-desktop:~# cd /usr/src
root@kathy-desktop:/usr/src# ls -l
total 28
drwxr-xr-x  4 root root 4096 2010-05-18 10:55 fglrx-8.723.1
drwxr-sr-x  4 root src  4096 2010-05-18 12:14 linux
drwxr-xr-x 24 root root 4096 2010-04-29 07:44 linux-headers-2.6.32-21
drwxr-xr-x  7 root root 4096 2010-04-29 07:45 linux-headers-2.6.32-21-generic
drwxr-xr-x 24 root root 4096 2010-05-18 11:11 linux-headers-2.6.32-22
drwxr-xr-x  7 root root 4096 2010-05-18 11:12 linux-headers-2.6.32-22-generic
drwxr-xr-x 23 root root 4096 2010-05-18 11:41 linux-headers-2.6.33.3-l505d
root@kathy-desktop:/usr/src# rm linux
rm: cannot remove `linux': Is a directory
root@kathy-desktop:/usr/src# wget [http://www.kernel.org/pub/linux/kernel/v.26/linux-2.6.32.4.tar.bz2](http://www.kernel.org/pub/linux/kernel/v.26/linux-2.6.32.4.tar.bz2)
--2010-05-21 19:50:27--  [http://www.kernel.org/pub/linux/kernel/v.26/linux-2.6.32.4.tar.bz2](http://www.kernel.org/pub/linux/kernel/v.26/linux-2.6.32.4.tar.bz2)
Resolving [www.kernel.org](www.kernel.org)... 149.20.20.133, 204.152.191.37
Connecting to [www.kernel.org|149.20.20.133|:80](www.kernel.org|149.20.20.133|:80)... connected.
HTTP request sent, awaiting response... 404 Not Found
2010-05-21 19:50:28 ERROR 404: Not Found.

root@kathy-desktop:/usr/src# wget [http://www.kernel.org/pub/linux/kern...6.32.4.tar.bz2](http://www.kernel.org/pub/linux/kern...6.32.4.tar.bz2)
--2010-05-21 19:53:55--  [http://www.kernel.org/pub/linux/kern...6.32.4.tar.bz2](http://www.kernel.org/pub/linux/kern...6.32.4.tar.bz2)
Resolving [www.kernel.org](www.kernel.org)... 149.20.20.133, 204.152.191.37
Connecting to [www.kernel.org|149.20.20.133|:80](www.kernel.org|149.20.20.133|:80)... connected.
HTTP request sent, awaiting response... 404 Not Found
2010-05-21 19:53:55 ERROR 404: Not Found.

root@kathy-desktop:/usr/src# tar xjf linux-2.6.32.4.tar.bz2
tar: linux-2.6.32.4.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Exiting with failure status due to previous errors
root@kathy-desktop:/usr/src# wget [http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.32.4.tar.bz2](http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.32.4.tar.bz2)
--2010-05-21 19:57:47--  [http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.32.4.tar.bz2](http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.32.4.tar.bz2)
Resolving [www.kernel.org](www.kernel.org)... 149.20.20.133, 204.152.191.37
Connecting to [www.kernel.org|149.20.20.133|:80](www.kernel.org|149.20.20.133|:80)... connected.
HTTP request sent, awaiting response... 200 OK
Length: 64372500 (61M) [application/x-bzip2]
Saving to: `linux-2.6.32.4.tar.bz2'

100%[======================================>] 64,372,500   602K/s   in 2m 59s  

2010-05-21 20:00:47 (352 KB/s) - `linux-2.6.32.4.tar.bz2' saved [64372500/64372500]

root@kathy-desktop:/usr/src# ln -s linux-2.6.32.4 linux
ln: creating symbolic link `linux/linux-2.6.32.4': File exists
root@kathy-desktop:/usr/src# chown -R root:root linux-2.6.32.4
chown: cannot access `linux-2.6.32.4': No such file or directory
root@kathy-desktop:/usr/src# 

Hey Colin, not sure why 'File exists' then 'No such file or directory'  got any ideas why that might be?

Yeah, what a total snafu.

"/usr/src/linux" should not be a directory, it should be a symbolic link.  Somewhere along the line you created it as a directory.  Its contents, and then it, should be deleted somehow.  Using Nautilus as root would probably be the easiest way.

Then do the "ln -s linux-2.6.32.4 linux" command to create the symbolic link and go from there.

It's hard to say what else has gotten messed up.  You may want to blow away this whole installation of Ubuntu and start over.

I don't recall, are you running 10.4 or 9.10?  9.10 is easier to make work on these Toshiba laptops.  That is what I am using.

Colin

---

### Post by taserian on 2010-05-22
> **sbailey85 said:**
> Here is a link to my compiled kernel deb files. This is for a toshiba l505-s5983 wireless and everything is working good 

[http://dl.dropbox.com/u/6916351/linux-headers-2.6.33.3-l505d_2.6.33.3-l505d-10.00.Custom_amd64.deb](http://dl.dropbox.com/u/6916351/linux-headers-2.6.33.3-l505d_2.6.33.3-l505d-10.00.Custom_amd64.deb)

[http://dl.dropbox.com/u/6916351/linux-image-2.6.33.3-l505d_2.6.33.3-l505d-10.00.Custom_amd64.deb](http://dl.dropbox.com/u/6916351/linux-image-2.6.33.3-l505d_2.6.33.3-l505d-10.00.Custom_amd64.deb)

This is for 64bit in case you didn't notice in the file name

When installing the linux-image .deb from above, the following shows when updating grub.cfg:
```

Found linux image: /boot/vmlinuz-2.6.33.3-l505d
Found linux image: /boot/vmlinuz-2.6.32-22-generic
Found initrd image: /boot/initrd.img-2.6.32-22-generic
```Is the lack of an initrd image line for the newer kernel a problem?

---

### Post by colinwhipple on 2010-05-22
> **taserian said:**
> When installing the linux-image .deb from above, the following shows when updating grub.cfg:
```

Found linux image: /boot/vmlinuz-2.6.33.3-l505d
Found linux image: /boot/vmlinuz-2.6.32-22-generic
Found initrd image: /boot/initrd.img-2.6.32-22-generic
```Is the lack of an initrd image line for the newer kernel a problem?

There are instructions earlier in this thread for creating the initrd image.

Colin

---

### Post by Copy Master on 2010-05-22
Hi, I'm newbie here. I've reading a lot this thread, because it helped me to install and run 9.1 64 bit, but now, I installed 10.04 64 bit. Same history, acpi off to install and first run, I downloaded a new compiled and patched kernel, but I got the famous "Kernel panic" at boot. So, I have compiled my own kernel, and surprise !!! The kernel panic again. Anybody can help me to solve this? :)

---

### Post by ericwwheeler on 2010-05-22
> **colinwhipple said:**
> Yeah, what a total snafu.

"/usr/src/linux" should not be a directory, it should be a symbolic link.  Somewhere along the line you created it as a directory.  Its contents, and then it, should be deleted somehow.  Using Nautilus as root would probably be the easiest way.

Then do the "ln -s linux-2.6.32.4 linux" command to create the symbolic link and go from there.

It's hard to say what else has gotten messed up.  You may want to blow away this whole installation of Ubuntu and start over.

I don't recall, are you running 10.4 or 9.10?  9.10 is easier to make work on these Toshiba laptops.  That is what I am using.

Colin
Hey Colin,  I took your advice and re-installed 9.10 and followed the instructions and am now up and running.  I will search this thread to see if there's a way to keep the kernel from automatically updating until this is added.  Thank you for your patient persistence.:guitar:

---

### Post by tee_eff_em on 2010-05-23
> **colinwhipple said:**
> Do they show up in Synaptic as still installed?  They can be uninstalled from there.

Colin

Nope, not in Synaptic either.

Would it be wrong and/or dangerous to simply remove the unwanted images, et cetera from /boot/ and re-run update-grub?

---

### Post by colinwhipple on 2010-05-23
> **tee_eff_em said:**
> Nope, not in Synaptic either.

Would it be wrong and/or dangerous to simply remove the unwanted images, et cetera from /boot/ and re-run update-grub?

I don't know.  As long as you leave the images you are using, my guess is that it should be safe...

Colin

Colin

---

### Post by ericwwheeler on 2010-05-23
Hey Colin,

The kernel that I compiled for the l505d is it compatiable with Ubuntu packages? Can you install stuff like Pidgin and Libdvd for dvd playback?  I tried installing that stuff and got error messages saying that it failed.  Do you think that the dsdt patch might be included in later kernels of Ubuntu?

---

### Post by colinwhipple on 2010-05-23
> **ericwwheeler said:**
> Hey Colin,

The kernel that I compiled for the l505d is it compatiable with Ubuntu packages? Can you install stuff like Pidgin and Libdvd for dvd playback?  I tried installing that stuff and got error messages saying that it failed.  Do you think that the dsdt patch might be included in later kernels of Ubuntu?

It should be compatible.  Sometimes on my system I get a message that an install failed, and then it turns out it didn't, and the software can be run from the Applications or System menu.  Take a look.

The patch is supposed to be included in a future kernel, according to Comment #80 here:

[https://bugzilla.kernel.org/show_bug.cgi?id=14679](https://bugzilla.kernel.org/show_bug.cgi?id=14679)

I keep monitoring here:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

but I haven't seen it in any CHANGES summary yet.

Colin

---

### Post by Masevig on 2010-05-25
Hi, I sign up this account to say TANKS to all!
Everything is working good! Wifi, webcam, ACPI (brigtness control, suspend, volume and music control, dual core with hyper threading...etc.
The kernels downloaded from some posts don´t works for me, then I compiled several kernels until get the fully functionality.

*[COLOR="Green"]You can download it from:[/COLOR]*
[http://www.coxei.com.ar/Cosas/linux-headers-2.6.32.11+drm33.2-l505-acpi-rtl8191se-64bits-generic_2.6.32.11+drm33.2-l505-acpi-rtl8191se-64bits-generic-10.00.Custom_amd64.deb]("http://www.coxei.com.ar/Cosas/linux-headers-2.6.32.11+drm33.2-l505-acpi-rtl8191se-64bits-generic_2.6.32.11+drm33.2-l505-acpi-rtl8191se-64bits-generic-10.00.Custom_amd64.deb")
[http://www.coxei.com.ar/Cosas/linux-image-2.6.32.11+drm33.2-l505-acpi-rtl8191se-64bits-generic_2.6.32.11+drm33.2-l505-acpi-rtl8191se-64bits-generic-10.00.Custom_amd64.deb]("http://www.coxei.com.ar/Cosas/linux-image-2.6.32.11+drm33.2-l505-acpi-rtl8191se-64bits-generic_2.6.32.11+drm33.2-l505-acpi-rtl8191se-64bits-generic-10.00.Custom_amd64.deb")

Compiled on Toshiba L505-GS5037 (intel, but "my" kernel is generic) using the official Ubuntu´s  .config (.config-2.6.32-22-generic) and the linux-source from repository (lucid).
Bytes ):P


PD: don´t forget the following commands (after install the packets):
[I]sudo update-initramfs -c -k 2.6.32.11+drm33.2-l505-acpi-rtl8191se-64bits-generic
sudo update-grub[/I]

---

### Post by HeX0R on 2010-05-25
Hello all,
i was to lazy to do all this procedure a several times...
so i toke all the commands and put them in little ugly script.
if someone here also lazy you can use it :)

This script working on Ubuntu 10.04 64bit and Mint 9 64bit (Know by testing).

if you use it you need to run him as administrator and to be interactive with him until the "make menuconfig" command.

maybe some one alse have the time to edit this script to a "normal" one until the next update...


[Download the script here]("http://www.multiupload.com/ROGMFJ53W7")

---

### Post by sbailey85 on 2010-05-25
> **HeX0R said:**
> Hello all,
i was to lazy to do all this procedure a several times...
so i toke all the commands and put them in little ugly script.
if someone here also lazy you can use it :)

This script working on Ubuntu 10.04 64bit and Mint 9 64bit (Know by testing).

if you use it you need to run him as administrator and to be interactive with him until the "make menuconfig" command.

maybe some one alse have the time to edit this script to a "normal" one until the next update...


[Download the script here]("http://www.multiupload.com/ROGMFJ53W7")


Thank you very much for the script.. I am not currently using ubuntu but i will save this just in case i decide to go back! Thanks again.. you have probably made many peoples lives alot easier :guitar:

---

### Post by corelulos on 2010-05-25
> **HeX0R said:**
> Hello all,
i was to lazy to do all this procedure a several times...
so i toke all the commands and put them in little ugly script.
if someone here also lazy you can use it :)

This script working on Ubuntu 10.04 64bit and Mint 9 64bit (Know by testing).

if you use it you need to run him as administrator and to be interactive with him until the "make menuconfig" command.

maybe some one alse have the time to edit this script to a "normal" one until the next update...


[Download the script here]("http://www.multiupload.com/ROGMFJ53W7")

Thanks for the script file. It worked well. All I had to do otherwise was install my wireless driver. 
Worked on my l505d gs6000

---

### Post by tinnyskillz on 2010-05-25
Is there one for 32bit systems ? :)

---

### Post by HeX0R on 2010-05-26
> **corelulos said:**
> Thanks for the script file. It worked well. All I had to do otherwise was install my wireless driver. 
Worked on my l505d gs6000

Opss sorry, forgot to mention that its not included... :(
and the video also...

---

### Post by andydch on 2010-05-26
> **HeX0R said:**
> Hello all,
i was to lazy to do all this procedure a several times...
so i toke all the commands and put them in little ugly script.
if someone here also lazy you can use it :)

This script working on Ubuntu 10.04 64bit and Mint 9 64bit (Know by testing).

if you use it you need to run him as administrator and to be interactive with him until the "make menuconfig" command.

maybe some one alse have the time to edit this script to a "normal" one until the next update...


[Download the script here]("http://www.multiupload.com/ROGMFJ53W7")

in my grub2 file, i have set GRUB_CMDLINE_LINUX="acpi=off"
after run the script, should i set empty for that line?

thanks

---

### Post by galley3175 on 2010-05-26
Is this fix hardware specific?  I have a Toshiba E205-S1904 with the same issue.  I have to have acpi-off at boot if I want to load Lucid?  Can I use the same patch?  

Thanks,

Galley3175

---

### Post by HeX0R on 2010-05-26
> **andydch said:**
> in my grub2 file, i have set GRUB_CMDLINE_LINUX="acpi=off"
after run the script, should i set empty for that line?

thanks

I case the patch will success, yes, you have to cut out this settings to not harm your hardware.

But be aware, do this change before you run the script otherwise you will have to run the "update-grub" command after the script.

Have luck!

---

### Post by HeX0R on 2010-05-26
> **galley3175 said:**
> Is this fix hardware specific?  I have a Toshiba E205-S1904 with the same issue.  I have to have acpi-off at boot if I want to load Lucid?  Can I use the same patch?  

Thanks,

Galley3175

"Is this fix hardware specific?": 
Usually for Toshiba Satellite. 
you can see more details about thus patch here:
[The original bug report.]("https://bugzilla.kernel.org/show_bug.cgi?id=14679")

"I have to have acpi-off at boot if I want to load Lucid?"
i dont know, you can try or wait to answer from someone else, sorry im not familiar with Lucid.

"Can I use the same patch?"
if you dont have important information on the system you can just try it.
Eventually the script just install newer kernel.

---

### Post by andydch on 2010-05-27
> **HeX0R said:**
> I case the patch will success, yes, you have to cut out this settings to not harm your hardware.

But be aware, do this change before you run the script otherwise you will have to run the "update-grub" command after the script.

Have luck!

Hi HeXor,

I got problem after apply your script & reboot my laptop. The screen drop to shell.
What should I do so I can go to login screen?

When apply your script, in the middle of process, before kernel compiling process, I have to let setting as is or I have to change something?

My laptop is Toshiba Satellite L510 with Intel Core i3, ISADORA as main OS.

Thanks

---

### Post by galley3175 on 2010-05-27
I followed the steps, and I was able to boot up my E205-S1904.  It hung on boot though.  I think it could be that the kernel was AMD specific, and not compatible with the Intel i5.  Is this fix processor specific?  The Intel i5 is a 64 bit processor, but not an AMD.

Thanks,

Galley3175

---

### Post by andydch on 2010-05-27
> **corelulos said:**
> Thanks for the script file. It worked well. All I had to do otherwise was install my wireless driver. 
Worked on my l505d gs6000

hi corelulos,

just run the script? or u change some setting?

---

### Post by andydch on 2010-05-27
> **Masevig said:**
> Hi, I sign up this account to say TANKS to all!
Everything is working good! Wifi, webcam, ACPI (brigtness control, suspend, volume and music control, dual core with hyper threading...etc.
The kernels downloaded from some posts don´t works for me, then I compiled several kernels until get the fully functionality.

You can download it from:
[http://www.coxei.com.ar/Cosas/linux-headers-2.6.32.11+drm33.2-l505-acpi-rtl8191se-64bits-generic_2.6.32.11+drm33.2-l505-acpi-rtl8191se-64bits-generic-10.00.Custom_amd64.deb](http://www.coxei.com.ar/Cosas/linux-headers-2.6.32.11+drm33.2-l505-acpi-rtl8191se-64bits-generic_2.6.32.11+drm33.2-l505-acpi-rtl8191se-64bits-generic-10.00.Custom_amd64.deb)
[http://www.coxei.com.ar/Cosas/linux-image-2.6.32.11+drm33.2-l505-acpi-rtl8191se-64bits-generic_2.6.32.11+drm33.2-l505-acpi-rtl8191se-64bits-generic-10.00.Custom_amd64.deb](http://www.coxei.com.ar/Cosas/linux-image-2.6.32.11+drm33.2-l505-acpi-rtl8191se-64bits-generic_2.6.32.11+drm33.2-l505-acpi-rtl8191se-64bits-generic-10.00.Custom_amd64.deb)

Compiled on Toshiba L505-GS5037 (intel, but "my" kernel is generic) using the official Ubuntu´s  .config (.config-2.6.32-22-generic) and the linux-source from repository (lucid).
Bytes ):P


PD: don´t forget the following commands (after install the packets):
[I]sudo update-initramfs -c -k 2.6.32.11+drm33.2-l505-acpi-rtl8191se-64bits-generic
sudo update-grub[/I]

Thanks you so much, **Masevig** :guitar:
It works on my Toshiba Satellite L510 with Intel Core I3. My OS is ISADORA.

:)

---

### Post by ludovit on 2010-05-29
Thanks to ivanmmj,

Installed two .deb kernel headers and kernel, rebooted and works like a charm.

Thanks again thousand times. I was afraid to get stuck with pile of cr*p

Windows 7.

Everything works volume wheel, suspend, downloaded wireless driver from 

Realtek and compiled and and works fine also. Now I have fully functional

laptop..

Toshiba L505D-GS6000...dual core AMD Turion 2.0 Ghz :):):guitar:

---

### Post by JDuBZisFADED on 2010-05-30
> **ludovit said:**
> Thanks to ivanmmj,

Installed two .deb kernel headers and kernel, rebooted and works like a charm.

Thanks again thousand times. I was afraid to get stuck with pile of cr*p

Windows 7.

Everything works volume wheel, suspend, downloaded wireless driver from 

Realtek and compiled and and works fine also. Now I have fully functional

laptop..

Toshiba L505D-GS6000...dual core AMD Turion 2.0 Ghz :):):guitar:

Hello I also have the same model laptop as you. Our realtek internal chip is rtl8191 and i have tried many things to get it to work. ive downloaded the driver from realtek and compiled and installed according to this thread on the first post: [http://forums.opensuse.org/get-help-here/hardware/434035-realtek-rtl8191-8192se-wifi-drivers.html](http://forums.opensuse.org/get-help-here/hardware/434035-realtek-rtl8191-8192se-wifi-drivers.html) . the drivers install and i am able to use my wireless network but upon a restart i lose all of my progress and my wireless is not recognized until i redo the entire process. please help me find a permanent solution it would be great thanks in advance.

---

### Post by ludovit on 2010-05-30
JDuBZisFADED

1st...  Download two .deb files from page 9 post #81 and install.
        Then follow post #82 instructions.
        Then download correct driver. 8191 is incorrect.
        download from Realtek RTL8192SE driver.        rtl8192se_linux_2.6.0015.0127.2010.tar
       Unzip (extract) the file .

2nd...  make sure you have build essentials.

 ```
sudo apt-get install build-essential

```
       

       Once you get all this done go to download directory where is the
       unziped rtl8192 . Once inside rtl8129se_linux_2.6.0015.01276.2010
       directory

```
 make
```
 ```
sudo -s make install
```

If everything goes well without error, reboot and you should have wireless
working.

Let me know how it went.

I will be  more than happy to help you if you have any troubles to get it done.> 

---

### Post by ludovit on 2010-05-30
JDuBZisFADED

Are you running OpenSuse? or Ubuntu?

I have wireless working good on both OpenSuse 11.2x64 bit and now
on Ubuntu 10.04x64 bit

---

### Post by JDuBZisFADED on 2010-06-01
thank you man for the quick response.

i have used the script that was provided a couple pages back. Ive had wireless running on my 9.1 install but 10.04 seems to be giving me trouble. Im gunna go ahead and do what you suggest and pray it works. if it doesnt work, I might reinstall since I havent done much on it yet and try again with your suggestions.

---

### Post by Lykopis on 2010-06-01
Good news for those of us who don't mind compiling your own kernel.
2.6.35-rc1 from [http://www.kernel.org/ ]("http://www.kernel.org/")is out and can boot these laptops, 
and the source is here:
[http://www.kernel.org/pub/linux/kernel/v2.6/testing/linux-2.6.35-rc1.tar.bz2](http://www.kernel.org/pub/linux/kernel/v2.6/testing/linux-2.6.35-rc1.tar.bz2)  
They are a little rough around the edges and give some error massages at boot.
But still seem to work good. 
You will need to add the wireless driver from the drivers/staging folders.
I have this running on 10.04 right now.
I will keep you up to date on problems I run into.
I used ivanmmj's build instructions from page 8 of this thread but left out:

patch -p1 < ~/Desktop/bug14679_copy_dsdt.patch

This worked for me after I added the wireless driver with a little help from here:

[http://www.bitbenderforums.com/vb22/showthread.php?postid=296303](http://www.bitbenderforums.com/vb22/showthread.php?postid=296303)

----edit to fix typo----

---

### Post by JDuBZisFADED on 2010-06-01
ludovit:

everything is working now thank you. i ended up reinstalling because i had already done what you said but i love the kernel by ivan. he means it when he says speed, it is a very light kernel. i just used the simple commands to get wifi working and bam! my laptop is fully finctional 


again, thank you

---

### Post by colinwhipple on 2010-06-01
> **Lykopis said:**
> Good news for those of us who don't mind compiling your own kernel.
2.6.35-rc1 from [http://www.kernel.org/ ]("http://www.kernel.org/")is out and can boot these laptops, 
and the source is here:
[http://www.kernel.org/pub/linux/kernel/v2.6/testing/linux-2.6.35-rc1.tar.bz2](http://www.kernel.org/pub/linux/kernel/v2.6/testing/linux-2.6.35-rc1.tar.bz2)  
They are a little rough around the edges and give some error massages at boot.
But still seem to work good. 
You will need to add the wireless driver from the drivers/staging folders.
I have this running on 10.04 right now.
I will keep you up to date on problems I run into.
I used ivanmmj's build instructions from page 8 of this thread but left out:

patch -p1 < ~/Desktop/bug14679_copy_dsdt.patch

This worked for me after I added the wireless driver with a little help from here:

[http://www.bitbenderforums.com/vb22/showthread.php?postid=296303](http://www.bitbenderforums.com/vb22/showthread.php?postid=296303)

----edit to fix typo----

According to the Changes log, a compiled version is here:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.35-rc1-lucid/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.35-rc1-lucid/)

I am going to try it tonite.

Colin

---

### Post by Lykopis on 2010-06-01
> **colinwhipple said:**
> According to the Changes log, a compiled version is here:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.35-rc1-lucid/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.35-rc1-lucid/")

I am going to try it tonite.

Colin 

Thanks Colin,
I tried the Ubuntu kernel still had no wireless support.
But my results may not reflect others as I have a L505D-LS5007,
and the wireless device is a RTL8187se. So I would still need to compile a module/driver for it.

---

### Post by Lykopis on 2010-06-01
Ok, just updated Ubuntu while using the 2.6.35-rc1 kernel and all updates took without a problem.

---

### Post by colinwhipple on 2010-06-01
> **Lykopis said:**
> Thanks Colin,
I tried the Ubuntu kernel still had no wireless support.
But my results may not reflect others as I have a L505D-LS5007,
and the wireless device is a RTL8187se. So I would still need to compile a module/driver for it.

Mine is an 8187se also, and wireless does not work with the downloaded Ubuntu kernel.

Colin

---

### Post by Lykopis on 2010-06-03
Colin: 
The kernel source code contains the driver for the 8187se in the drivers/staging folder.
I guess you could pull it out and compile it as a module. I never tried it though.
What I did was download the source from kernel.org, then I used the instruction here:

[http://www.bitbenderforums.com/vb22/showthread.php?postid=296104#post296104](http://www.bitbenderforums.com/vb22/showthread.php?postid=296104#post296104)

to use menuconfig to configure the kernel source adding the wireless driver. 
Other than that I used ivanmmj's build instructions from page 8 of this thread but left  out:

patch -p1 < ~/Desktop/bug14679_copy_dsdt.patch

to compile the source code, and that has worked out well for me.

---

### Post by Lykopis on 2010-06-05
Update:
Run sensors-detect, it said module k10temp was missing.
recompiled kernel adding Drivers/Hardware Monitoring support with menuconfig for AMD Phenom/Sempron/Turion/Opteron temperature sensor and Driver/Staging for my wireless device. Mine is RTL8187 yours may be different.
This added a chip-set temperature sensor to the system and got the wireless going. 
This was just a bit of fine tuning, it's probably not necessary though. 

Sleep and hibernate work, but after you hit the power button you need to wait till you see the mouse cursor then press the space bar or move the mouse to get the unlock prompt.  

The special function keys:

mute:                works 
lock:                  no go  
power plan:           ?
sleep:                works
hibernate:          no go
output:                 ?
brightness:         works
wireless on/off:   no go
touch pad on/off: no go
volume control:   works

---

### Post by colinwhipple on 2010-06-05
> **Lykopis said:**
> Update:
Run sensors-detect, it said module k10temp was missing.
recompiled kernel adding Drivers/Hardware Monitoring support with menuconfig for AMD Phenom/Sempron/Turion/Opteron temperature sensor and Driver/Staging for my wireless device. Mine is RTL8187 yours may be different.
This added a chip-set temperature sensor to the system and got the wireless going. 
This was just a bit of fine tuning, it's probably not necessary though. 

Sleep and hibernate work, but after you hit the power button you need to wait till you see the mouse cursor then press the space bar or move the mouse to get the unlock prompt.  

The special function keys:

mute:                works 
lock:                  no go  
power plan:           ?
sleep:                works
hibernate:          no go
output:                 ?
brightness:         works
wireless on/off:   no go
touch pad on/off: no go
volume control:   works

Thanks.  Doing this gave me a wireless connection with 2.6.34.

Now I need to figure out how to connect to my network printer in Lucid.  It keeps asking me to log into the network to add the printer.  I didn't have to do that in Karmic.

Colin

---

### Post by Lykopis on 2010-06-05
> **colinwhipple said:**
> Thanks.  Doing this gave me a wireless connection with 2.6.34.

Now I need to figure out how to connect to my network printer in Lucid.  It keeps asking me to log into the network to add the printer.  I didn't have to do that in Karmic.

Colin
I don't really know how to help you there.
The last time I had to set up a network printer was in OpenSuSe
 and I had to open CUPS to make it work.
Heres the cups website:

[http://www.cups.org/](http://www.cups.org/)

I don't think you need to install it.
 Just use a web browser and go here:

 [http://localhost:631]("http://localhost:631/")

This will give you access to just about anything that has to do with your printer.
Sorry I can't be more help on this one.

---

### Post by Lykopis on 2010-06-10
Tried 2.6.35-rc2 from Ubuntu though it's for the upcoming Ubuntu-Maverick it still works. you still get error messages at boot, but will boot-up none the less. The errors are probably from features not in Lucid. Wireless works, CPU scaling works, Temperature monitoring works, and special function keys work as stated above. 

You can get it here:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.35-rc2-maverick/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.35-rc2-maverick/")

I think the next release of Ubuntu may well support these laptops.

I think we can say ("solved")

---

### Post by rdingraham on 2010-06-10
> **Lykopis said:**
> Tried 2.6.35-rc2 from Ubuntu though it's for the upcoming Ubuntu-Maverick it still works. you still get error messages at boot, but will boot-up none the less. The errors are probably from features not in Lucid. Wireless works, CPU scaling works, Temperature monitoring works, and special function keys work as stated above. 

Let me be clear on this.  Are you saying that the 2.6.35-rc2 kernel works (with error messages), including wireless and heat sensors, WITHOUT having to compile a new kernel or change the initrd settings?

Bob I

---

### Post by colinwhipple on 2010-06-10
> **rdingraham said:**
> Let me be clear on this.  Are you saying that the 2.6.35-rc2 kernel works (with error messages), including wireless and heat sensors, WITHOUT having to compile a new kernel or change the initrd settings?

Bob I

I just tried it, and it works for me in 32-bit Lucid.  I did put in the acpi=copy_dsdt boot option.

I haven't tried sensors, but WiFi works, and power management seems to work.

I did get more than the usual startup error messages.

Colin

---

### Post by Lykopis on 2010-06-10
I would still do the update-initramfs and update-grub commands. I never really looked into that part of it to see if they worked right.

---

### Post by Lykopis on 2010-06-10
> **rdingraham said:**
> Let me be clear on this.  Are you saying that  the 2.6.35-rc2 kernel works (with error messages), including wireless  and heat sensors, WITHOUT having to compile a new kernel or change the  initrd settings?

Bob I
 
No you wouldn't need to recompile this kernel it's an Ubuntu kernel, but like Colin I am running a 32 bit copy of Lucid.
Also I am not using any boot options to start the kernel.

---

### Post by colinwhipple on 2010-06-10
> **Lykopis said:**
> No you wouldn't need to recompile this kernel it's an Ubuntu kernel, but like Colin I am running a 32 bit copy of Lucid.
Also I am not using any boot options to start the kernel.

That surprises me.  I just tried, and I didn't need the boot option either.

Colin

---

### Post by colinwhipple on 2010-06-10
I also tried it in 64-bit Karmic.  It boots up, but there is no mouse pointer.

According to this:

[https://patchwork.kernel.org/patch/91236/](https://patchwork.kernel.org/patch/91236/)

the 2.6.35.rc1 and 2.6.35.rc2 kernels check for Toshiba Satellite A505 and L505D models and apply the dsdt fix when found.

Colin

---

### Post by rdingraham on 2010-06-10
Installed the 2.6.35-020635rc2 kernel and headers, on my 64 bit Lucid.  It did boot up out of the box, the first kernel to do that without requiring re-compiling.  However, the wireless is broken, as is the touchpad.  Opening up System/Administration/Hardware Drivers, it does not even find my Realtek RTL819x WiFi card; also, it "sees" but will not load my ATI/AMD FGLRX graphics driver.  The custom kernel I have been using will do all of these things, except for the touchpad.

Anyway, its great to see that they are making progress on this, so hopefully it will all be solved.

Bob I.

---

### Post by Lykopis on 2010-06-10
> **rdingraham said:**
> Installed the 2.6.35-020635rc2 kernel and headers, on my 64 bit Lucid.  It did boot up out of the box, the first kernel to do that without requiring re-compiling.  However, the wireless is broken, as is the touchpad.  Opening up System/Administration/Hardware Drivers, it does not even find my Realtek RTL819x WiFi card; also, it "sees" but will not load my ATI/AMD FGLRX graphics driver.  The custom kernel I have been using will do all of these things, except for the touchpad.

Anyway, its great to see that they are making progress on this, so hopefully it will all be solved.

Bob I.
I have found that the touchpad can't be turned on & off with the special function keys when using Linux. I had to use Window$ to activate the touchpad. 
At first I had to compile a module/driver for wireless. It's really not that hard.
I followed this tutorial but changed the codes & used source for my wireless.

[https://help.ubuntu.com/community/WifiDocs/Device/Realtek%208172](https://help.ubuntu.com/community/WifiDocs/Device/Realtek%208172)

Here is a few more on compiling source code for Linux. 
[http://www.maximumpc.com/article/howtos/howto_compile_programs_from_source_linux?page=0%2C0](http://www.maximumpc.com/article/howtos/howto_compile_programs_from_source_linux?page=0%2C0)

[http://www.cyberciti.biz/tips/linux-how-to-compile-program.html](http://www.cyberciti.biz/tips/linux-how-to-compile-program.html)

And I like this one because it's full of info
[http://www.howtoforge.com/](http://www.howtoforge.com/)

---

### Post by Linux_Lurker on 2010-06-11
Hello All,

Good to see that so much progress has been made...  Can anybody confirm if the Maverick Meerkat daily builds are:

1. Stable, and
2. Have the appropriate kernel in them yet

If nobody knows, I'll give it a try either tonight, or sometime this weekend...

---

### Post by Linux_Lurker on 2010-06-11
Actually, right now, I'm posting this from the latest Maverick 32bit daily build.  It boots up perfectly, and the wireless, touchpad and battery meter all work.

---

### Post by colinwhipple on 2010-06-11
> **Linux_Lurker said:**
> Actually, right now, I'm posting this from the latest Maverick 32bit daily build.  It boots up perfectly, and the wireless, touchpad and battery meter all work.

Did you use any boot options?  I tried the daily build a couple of days ago, and couldn't get it to boot up.  It dumped me to a command prompt.

Colin

---

### Post by Linux_Lurker on 2010-06-11
> **colinwhipple said:**
> Did you use any boot options?  I tried the daily build a couple of days ago, and couldn't get it to boot up.  It dumped me to a command prompt.

Colin

No boot options and no special kernel, just popped the CD in, and it worked right off.  I'm making a 64 bit USB startup disk right now, I'll let you know how that works...

---

### Post by Linux_Lurker on 2010-06-11
...and now, I'm posting this from the 64 bit Maverick daily build live CD.  Everything works, touchpad, wireless, and battery meter.  

Excellent work, everybody...

:guitar:

---

### Post by colinwhipple on 2010-06-11
> **Linux_Lurker said:**
> ...and now, I'm posting this from the 64 bit Maverick daily build live CD.  Everything works, touchpad, wireless, and battery meter.  

Excellent work, everybody...

:guitar:

I was able to get a CD to boot.  A USB stick didn't.

Colin

---

### Post by rdingraham on 2010-06-12
Tried the Maverick Alpha Live CD.  Touchpad still doesn't work (maybe it's broken).  Everything else, including the wireless does.  One caveat, however.  When Lucid came out, I was able to boot off the Lucid Live CD, but once I installed it on my hard drive, it crashed on boot-up.  Also, I think I read somewhere (I could be wrong) that Maverick is going to run on the 2.6.34 kernel, not the 2.6.35 kernel that we have been trying.  So I think we will have to wait and see.  It is progress though.

Bob I.

---

### Post by Lykopis on 2010-06-12
> **rdingraham said:**
> Tried the Maverick Alpha Live CD.  Touchpad still doesn't work (maybe it's broken).

Bob I.
Bob:
I had the same problem at first.
If you still have Window$ on the machine try logging into Window$ and using the special function keys to re-enable the touchpad it's usually marked "FN" press it then a key usually something like F1 to F9. on mine it's FN + F9, some of the FN (special function) keys don't work in Linux, the Touchpad is one of them, hence you need Windows to "FIX" it.

---

### Post by Linux_Lurker on 2010-06-12
> **colinwhipple said:**
> I was able to get a CD to boot.  A USB stick didn't.

Colin

Actually, I found that previous versions of Ubuntu can't make a proper Maverick USB boot disk, I had to install 32 bit from a CD, then make the 64 bit USB startup disk from the 32 bit Maverick install.   Alternately, you could burn a 32 bit live CD, and make the boot disk there.   Currently, the 64 bit image is about 712mb, so it won't fit on a CD, you need a DVD to burn it(which I'm all out of right now...)

---

### Post by Linux_Lurker on 2010-06-12
> **rdingraham said:**
> Maverick is going to run on the 2.6.34 kernel, not the 2.6.35 kernel

Not true, it will in fact run on .35.   The current kernel listed in grub is 2.6.35-2, based on 35-RC1.

---

### Post by colinwhipple on 2010-06-12
I am up and running with 32-bit Maverick, which I installed from a CD.  WiFi works and power management seems to work.  The only problem so far is the one I was unable to resolve in Lucid.  I can't get a connection to my printer, which is connected to my Netgear router.  With Karmic, I was able to connect to it without problem.

The kernel version is:

2.6.35-2-generic

Colin

---

### Post by Linux_Lurker on 2010-06-12
> **colinwhipple said:**
> which is connected to my Netgear router


TBH, I believe that the Netgear router could be the culprit(even if something works in Windows, but not Linux).   I have a Netgear router, plenty of times I've blamed a networking issue on Linux, when it was actually that stupid router all along.   Sometime soon, I'm going to buy an Asus router, and install Tomato firmware on it.

---

### Post by rdingraham on 2010-06-12
> **Lykopis said:**
> Bob:
I had the same problem at first.
If you still have Window$ on the machine try logging into Window$ and using the special function keys to re-enable the touchpad it's usually marked "FN" press it then a key usually something like F1 to F9. on mine it's FN + F9, some of the FN (special function) keys don't work in Linux, the Touchpad is one of them, hence you need Windows to "FIX" it.

I wiped Windows 7 from the hard drive when I installed Lucid.  I currently have Windows XP installed in VirtualBox.  It works fine, but only some of the function keys work, and the FN+F9 Touchpad key is one that does not work.  Its no big deal;  I don't use the touchpad very much anyway.

> **Linux_Lurker said:**
> Not true, it will in fact run on .35.   The current kernel listed in grub is 2.6.35-2, based on 35-RC1.

Great to hear. I wasn't sure my info was correct. Thanks for setting me straight.

> **colinwhipple said:**
> I am up and running with 32-bit Maverick, which I installed from a CD.  WiFi works and power management seems to work.  The only problem so far is the one I was unable to resolve in Lucid.  I can't get a connection to my printer, which is connected to my Netgear router.  With Karmic, I was able to connect to it without problem.

The kernel version is:

2.6.35-2-generic

Colin

Again, sounds great.  Thanks everyone.

Bob I.

---

### Post by colinwhipple on 2010-06-12
I tried again to look for a solution to my printer problem, by doing a search of these forums for "network printer".  This time I found someone with a similar problem who came up with a solution.

So all is looking pretty good with Maverick.

Colin

---

### Post by Linux_Lurker on 2010-06-13
A word of warning to everyone:

They've not started making the big changes in 10.10 yet, I expect it to become very broken in the next few months.  If you want to keep a stable system, I would **strongly **recommend turning off automatic updates.  If you want to update, download a new daily build, test it as a live CD, then do a clean install.

Yours Truly,
Experienced Tester of Alpha Builds

---

### Post by Lykopis on 2010-06-13
> **Linux_Lurker said:**
> A word of warning to everyone:

They've not started making the big changes in 10.10 yet, I expect it to become very broken in the next few months.  If you want to keep a stable system, I would **strongly **recommend turning off automatic updates.  If you want to update, download a new daily build, test it as a live CD, then do a clean install.

Yours Truly,
Experienced Tester of Alpha Builds

I would agree there, 10.10 will get real messy later on.
It seems to run good on my machine.
:guitar:

---

### Post by ktemkin on 2010-06-15
You should be able to install just the kernel used in Maverick, instead of having to install Maverick itself.

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.35-rc3-maverick/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.35-rc3-maverick/)

This should greatly increase stability compared to running development builds of maverick.

---

### Post by Lykopis on 2010-06-17
> **ktemkin]You should be able to install just the kernel used in Maverick, instead  of having to install Maverick itself.

[http://kernel.ubuntu.com/~kernel-ppa...-rc3-maverick/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.35-rc3-maverick/")

This should greatly increase stability compared to running development  builds of maverick.     [/QUOTE]



[QUOTE=Lykopis said:**
> Tried 2.6.35-rc2 from Ubuntu though it's for the upcoming Ubuntu-Maverick it still works. you still get error messages at boot, but will boot-up none the less. The errors are probably from features not in Lucid. Wireless works, CPU scaling works, Temperature monitoring works, and special function keys work as stated above. 

You can get it here:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.35-rc2-maverick/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.35-rc2-maverick/")

I think the next release of Ubuntu may well support these laptops.

I think we can say ("solved")

As I said these kernels create boot-up errors on 10.04,  although they still work.
But thanks anyway ktemkin.
What I am thinking about doing is use a rc1 that I complied as a start and compile a rc2 or rc3,
and see what happens.

---

### Post by Linux_Lurker on 2010-06-17
Hey everyone, please read this...

Apparently, the new kernel and open-source drivers cause 780/880 IGPs to run quite hot, partly due to an incomplete ACPI implementation, and partly because the kernel devs are admitting that they're not sure how the IGP voltage is supposed to work.   I notice that it runs far hotter (the ever reliable hand on the laptop exhaust vent method) with 35-RC1 than it does on my good ol' reliable 31 series kernel with the proprietary driver.

Now, you could just use the proprietary driver instead, however, mine won't install, it errors out.   Does anybody know any tricks to get the proprietary driver to work?

worth repeating:
[B]
You may be risking damage to your IGP with the current Maverick kernel.
[/B]

---

### Post by colinwhipple on 2010-06-18
> **Linux_Lurker said:**
> Hey everyone, please read this...

Apparently, the new kernel and open-source drivers cause 780/880 IGPs to run quite hot, partly due to an incomplete ACPI implementation, and partly because the kernel devs are admitting that they're not sure how the IGP voltage is supposed to work.   I notice that it runs far hotter (the ever reliable hand on the laptop exhaust vent method) with 35-RC1 than it does on my good ol' reliable 31 series kernel with the proprietary driver.

Now, you could just use the proprietary driver instead, however, mine won't install, it errors out.   Does anybody know any tricks to get the proprietary driver to work?

worth repeating:
[B]
You may be risking damage to your IGP with the current Maverick kernel.
[/B]

I guess I'll stick to good old-fashioned 64-bit Karmic, even if it is ancient technology.  :):)

Colin

---

### Post by Lykopis on 2010-06-18
> **Linux_Lurker said:**
> Hey everyone, please read this...

Apparently, the new kernel and open-source drivers cause 780/880 IGPs to run quite hot, partly due to an incomplete ACPI implementation, and partly because the kernel devs are admitting that they're not sure how the IGP voltage is supposed to work.   I notice that it runs far hotter (the ever reliable hand on the laptop exhaust vent method) with 35-RC1 than it does on my good ol' reliable 31 series kernel with the proprietary driver.

Now, you could just use the proprietary driver instead, however, mine won't install, it errors out.   Does anybody know any tricks to get the proprietary driver to work?

worth repeating:
[B]
You may be risking damage to your IGP with the current Maverick kernel.
[/B]
Though I haven't tried it myself yet, this might provide a solution.

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver)

This goes into Linux issues with the ATI driver

[http://www2.ati.com/drivers/linux/linux_8.12.10.html#176637](http://www2.ati.com/drivers/linux/linux_8.12.10.html#176637)

---

### Post by tee_eff_em on 2010-06-18
> **Linux_Lurker said:**
> Hey everyone, please read this...

Apparently, the new kernel and open-source drivers cause 780/880 IGPs to run quite hot, partly due to an incomplete ACPI implementation, and partly because the kernel devs are admitting that they're not sure how the IGP voltage is supposed to work.   I notice that it runs far hotter (the ever reliable hand on the laptop exhaust vent method) with 35-RC1 than it does on my good ol' reliable 31 series kernel with the proprietary driver.

Now, you could just use the proprietary driver instead, however, mine won't install, it errors out.   Does anybody know any tricks to get the proprietary driver to work?

worth repeating:
[B]
You may be risking damage to your IGP with the current Maverick kernel.
[/B]

I continue to be naive -- What is IGP?

I am still running (re-installed) Karmic 9.10 with kernel 2.6.35-rc3 (boot options: acpi=copy_dsdt nosplash nomodeset), and am looking forward to trying to (re)upgrade to Lucid 10.04 soon.

Neither conky nor hand-on-the-laptop-exhaust-vent indicates any appreciable temperature rise from my previous kernel of choice (2.6.32-l505d-speed).

---

### Post by Lykopis on 2010-06-18
> **tee_eff_em said:**
> I continue to be naive -- What is IGP?

I am still running (re-installed) Karmic 9.10 with kernel 2.6.35-rc3 (boot options: acpi=copy_dsdt nosplash nomodeset), and am looking forward to trying to (re)upgrade to Lucid 10.04 soon.

Neither conky nor hand-on-the-laptop-exhaust-vent indicates any appreciable temperature rise from my previous kernel of choice (2.6.32-l505d-speed).
 
tee_eff_em:
I am kinda with you on the heat issue. I run M$-Window$-7 as well as 10.04 Ubuntu with Kernel 2.6.35-rc2. rc2 seems to control the CPU fans better. But heat output is about the same between M$-Window$-7 and 10.04 Ubuntu with Kernel 2.6.35-rc2. rc2

What is IGP?
Basically it's your graphics adapter,AKA video card.
Heres a few examples:
[http://ati.amd.com/products/radeon9100igp/](http://ati.amd.com/products/radeon9100igp/)
[http://ati.amd.com/products/radeonigp/rigp340m.html](http://ati.amd.com/products/radeonigp/rigp340m.html)

You can find which video card you have by typing  lspci at the terminal and look for something like "VGA compatible adapter" in the list.
This is how mine shows up:
01:05.0 VGA compatible controller: ATI Technologies Inc M860G [Mobility Radeon 4100]

---

### Post by Lykopis on 2010-06-22
Ok I admit I'm not an expert on these things, But I think I might have found the reason the 2.6.35-rc1,rc2,rc3 kernels won't allow the use of the ATI proprietary drivers. A little tinkering revealed that the firmware is not compiled into the Kernels on the Ubuntu site. Maybe someone out there can help us figure this one out.

---

### Post by tee_eff_em on 2010-06-22
> **Lykopis said:**
> tee_eff_em:
I am kinda with you on the heat issue. I run M$-Window$-7 as well as 10.04 Ubuntu with Kernel 2.6.35-rc2. rc2 seems to control the CPU fans better. But heat output is about the same between M$-Window$-7 and 10.04 Ubuntu with Kernel 2.6.35-rc2. rc2

What is IGP?
Basically it's your graphics adapter,AKA video card.
Heres a few examples:
[http://ati.amd.com/products/radeon9100igp/](http://ati.amd.com/products/radeon9100igp/)
[http://ati.amd.com/products/radeonigp/rigp340m.html](http://ati.amd.com/products/radeonigp/rigp340m.html)

You can find which video card you have by typing  lspci at the terminal and look for something like "VGA compatible adapter" in the list.
This is how mine shows up:
01:05.0 VGA compatible controller: ATI Technologies Inc M860G [Mobility Radeon 4100]

Thanks. 'lspci' reports
01:05.0 VGA compatible controller: ATI Technologies Inc Device 9713
so maybe the "780/880" heat problem reported above does not apply to my system?


In other discoveries: When I ran the l505d-speed kernel, if the system ever went into suspend, I could wake it up, but the wireless connection could never re-establish. (And, IIRC, I could **not** wake up from a hibernation state (or at least it was no better than from suspension))
Now, running 2.6.35-rc3, suspension will not awaken (or at least the screen will not), but I **can** successfully hibernate, awaken, **and** the wireless re-establishes!

---

### Post by colinwhipple on 2010-06-22
> **tee_eff_em said:**
> Thanks. 'lspci' reports
01:05.0 VGA compatible controller: ATI Technologies Inc Device 9713
so maybe the "780/880" heat problem reported above does not apply to my system?


In other discoveries: When I ran the l505d-speed kernel, if the system ever went into suspend, I could wake it up, but the wireless connection could never re-establish. (And, IIRC, I could **not** wake up from a hibernation state (or at least it was no better than from suspension))
Now, running 2.6.35-rc3, suspension will not awaken (or at least the screen will not), but I **can** successfully hibernate, awaken, **and** the wireless re-establishes!

To get the screen back after suspension, try the Ctrl-Alt-F1 and Ctrl-Alt-F7 keys.  I don't remember which order.  I just try them successively.

Colin

---

### Post by JDuBZisFADED on 2010-06-22
> **Lykopis said:**
> Ok I admit I'm not an expert on these things, But I think I might have found the reason the 2.6.35-rc1,rc2,rc3 kernels won't allow the use of the ATI proprietary drivers. A little tinkering revealed that the firmware is not compiled into the Kernels on the Ubuntu site. Maybe someone out there can help us figure this one out.


do you think that if i took the firmware driver source and added it into the .35-rc3 source code i could compile the driver into the kernel manualy. or will it not be added when i compile?

---

### Post by Lykopis on 2010-06-23
> **JDuBZisFADED said:**
> do you think that if i took the firmware driver source and added it into the .35-rc3 source code i could compile the driver into the kernel manualy. or will it not be added when i compile?

I am not positive on this but I think there is an option to compile in the firmware into the kernel in menuconfig. Also when I tried to use the proprietary driver in the 10.10 daily build it failed as well. So even the developers haven't fixed this yet. I would try leaving out the open-source driver for ATI and activate the VGA FB (frame-buffer) driver as a module in menuconfig. Compile the Kernel then try to activate the  proprietary driver from ATI that way.
ATM I am running 10.10 daily build and in it's current configuration it's stable as a rock on my machine so I am kinda like not wanting to mess with it.
But maybe someone out there would like to give it a try...

---

### Post by Lykopis on 2010-06-23
My reasoning for the above comes from here. Though for the Nvidia driver I think it may apply to us as well...

[http://blog.avirtualhome.com/2010/04/17/configuration-tips-for-the-ubuntu-lucid-kernel/](http://blog.avirtualhome.com/2010/04/17/configuration-tips-for-the-ubuntu-lucid-kernel/)

Configuration Changes
nVidia &#8211; Nouveau driver

I&#8217;ll start with the most important one I had to make when I was building the Ubuntu Lucid kernel.
The Ubuntu Lucid kernel has the option to use the Open Source drive Nouveau, which is the driver for nVidia cards, enabled. Although very nice, the 3D-acceleration is in experimental stage. I rather run the proprietary driver by nVidia and that&#8217;s where I ran into trouble after my first kernel compilation. When the Nouveau driver is being used you can not install the proprietary driver. The installation will stop by stating that a driver is being used which interferes with the installation of the proprietary driver. There is no mention of the Nouveau driver but that is the one that&#8217;s blocking the installation. You can blacklist the Nouveau driver or disable the Nouveau driver in the kernel.

Just disable the ATI driver Instead of the Nvidia one

---

### Post by JDuBZisFADED on 2010-06-24
> **Lykopis said:**
> I am not positive on this but I think there is an option to compile in the firmware into the kernel in menuconfig. Also when I tried to use the proprietary driver in the 10.10 daily build it failed as well. So even the developers haven't fixed this yet. I would try leaving out the open-source driver for ATI and activate the VGA FB (frame-buffer) driver as a module in menuconfig. Compile the Kernel then try to activate the  proprietary driver from ATI that way.
ATM I am running 10.10 daily build and in it's current configuration it's stable as a rock on my machine so I am kinda like not wanting to mess with it.
But maybe someone out there would like to give it a try...

are you using the stock kernel. if not could you provide the .debs . i want to get my wireless drivers and ati drivers back but i love my meerkat

---

### Post by tee_eff_em on 2010-06-24
> **colinwhipple said:**
> To get the screen back after suspension, try the Ctrl-Alt-F1 and Ctrl-Alt-F7 keys.  I don't remember which order.  I just try them successively.

Colin

Yeah, I'd tried the various consoles, but no joy.


On the upside, I bit the bullet today and re-upgraded to 10.04 Lucid -- Wheeeee! The 2.6.35-rc3 kernel is working fine! (Much better than the "jumpy touchpad" problems I'd experienced with 10.04/l505d-speed)

---

### Post by Lykopis on 2010-06-25
> **JDuBZisFADED said:**
> are you using the stock kernel. if not could you provide the .debs . i want to get my wireless drivers and ati drivers back but i love my meerkat

I am using the meerkat stock Kernel my wireless works, but I can't use the proprietary driver from ATI.
Unfortunately I don't have a site with enough space for a whole kernel otherwise compiling a kernel would not be hard . 

A really good quick and dirty guide to compiling a kernel can be found here:
 [http://ubuntuforums.org/showthread.php?t=1301101&highlight=toshiba&page=8](http://ubuntuforums.org/showthread.php?t=1301101&highlight=toshiba&page=8)

A how to for using menuconfig to configure a kernel, like adding a module/driver so forth before compiling can be found here:
(you need to scroll down the page a little)
[http://www.bitbenderforums.com/vb22/showthread.php?postid=296303#post296303](http://www.bitbenderforums.com/vb22/showthread.php?postid=296303#post296303)

If you don't get it don't worry then, just go with the instructions on page 8 of this thread, it should still work.

To get your wireless working these 2 sites might help:
[http://www.linwik.com/wiki/using+the+realtek+8172+and+8192se+wireless+controller+with+ubuntu+9.10](http://www.linwik.com/wiki/using+the+realtek+8172+and+8192se+wireless+controller+with+ubuntu+9.10)

[https://help.ubuntu.com/community/WifiDocs/Device/Realtek%208172](https://help.ubuntu.com/community/WifiDocs/Device/Realtek%208172)

Beyond that I'm really not sure if I can help you.
Can you run lspci in a terminal and post all references to Realtek (there should be 2).
Then run lsmod in a terminal and post the output here.
Maybe we can see if the wireless module is loading on your machine.
I must have a different wireless device in this machine than you.
The L505's and A505's do come in a variety of configurations.

> **tee_eff_em said:**
> Yeah, I'd tried the various consoles, but no  joy.


On the upside, I bit the bullet today and re-upgraded to 10.04 Lucid --  Wheeeee! The 2.6.35-rc3 kernel is working fine! (Much better than the  "jumpy touchpad" problems I'd experienced with  10.04/l505d-speed)

I found that I needed to use the power switch (Yeah ???) to resume my machine from a suspend to ram and it worked for me without a restart,  power-down or power-cycle, might be worth a try...

---

### Post by JDuBZisFADED on 2010-06-25
> **Lykopis said:**
> I am using the meerkat stock Kernel my wireless works, but I can't use the proprietary driver from ATI.
Unfortunately I don't have a site with enough space for a whole kernel otherwise compiling a kernel would not be hard . 

A really good quick and dirty guide to compiling a kernel can be found here:
 [http://ubuntuforums.org/showthread.php?t=1301101&highlight=toshiba&page=8](http://ubuntuforums.org/showthread.php?t=1301101&highlight=toshiba&page=8)

A how to for using menuconfig to configure a kernel, like adding a module/driver so forth before compiling can be found here:
(you need to scroll down the page a little)
[http://www.bitbenderforums.com/vb22/showthread.php?postid=296303#post296303](http://www.bitbenderforums.com/vb22/showthread.php?postid=296303#post296303)

If you don't get it don't worry then, just go with the instructions on page 8 of this thread, it should still work.

To get your wireless working these 2 sites might help:
[http://www.linwik.com/wiki/using+the+realtek+8172+and+8192se+wireless+controller+with+ubuntu+9.10](http://www.linwik.com/wiki/using+the+realtek+8172+and+8192se+wireless+controller+with+ubuntu+9.10)

[https://help.ubuntu.com/community/WifiDocs/Device/Realtek%208172](https://help.ubuntu.com/community/WifiDocs/Device/Realtek%208172)

Beyond that I'm really not sure if I can help you.
Can you run lspci in a terminal and post all references to Realtek (there should be 2).
Then run lsmod in a terminal and post the output here.
Maybe we can see if the wireless module is loading on your machine.
I must have a different wireless device in this machine than you.
The L505's and A505's do come in a variety of configurations.



I found that I needed to use the power switch (Yeah ???) to resume my machine from a suspend to ram and it worked for me without a restart,  power-down or power-cycle, might be worth a try...

yeah i know how to compile. thanks. i think im just having trouble patching the bug patch. i have a 8191se realtek chip btw. so your saying you can boot into the maverick kernel without turning acpi=off. if so please point me to where you got it or did it come in your iso? with my lappy i try to boot and get a gang of acpi errors. are u 64 or 32bit? thanks for the responses. your a very helpful guy

---

### Post by Lykopis on 2010-06-26
> **JDuBZisFADED said:**
> yeah i know how to compile. thanks. i think im just having trouble patching the bug patch. i have a 8191se realtek chip btw. so your saying you can boot into the maverick kernel without turning acpi=off. if so please point me to where you got it or did it come in your iso? with my lappy i try to boot and get a gang of acpi errors. are u 64 or 32bit? thanks for the responses. your a very helpful guy
  
Ok First I am running (32-bit) 10.10 Maverick daily build, the Kernel is based on 2.6.35-rc1 or rc2 
depending on how well you keep it updated, (updating 10.10 is not really advisable at the moment).
This kernel will boot these machines without a lot of problems, I don't need any kernel commands to boot my L505D-LS5007 with it. 

If you wish to try the daily build it can be had here:
[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)
You will probably need a DVD for the burn and I can't promise it will work (could be badly broken as it's a alpha build)

The Maverick kernel can be had here:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/")
(Scroll to the bottom of the page)
They create some boot errors when used with Lucid 10.04.
But, they still seemed work Ok for me. 

What I would do is download the 10.10 live CD daily build and test it.
If it worked without problems install it and use it but not update it.
If it's too badly broken then resort to the 2.6.35-rc1 ,rc2 or rc3 kernel with 10.04 Lucid
If you still have ACPI errors with 2.6.35-rc.. kernels try adding acpi=copy_dsdt to the kernel commands.

---

### Post by JDuBZisFADED on 2010-06-27
> **Lykopis said:**
> Ok First I am running (32-bit) 10.10 Maverick daily build, the Kernel is based on 2.6.35-rc1 or rc2 
depending on how well you keep it updated, (updating 10.10 is not really advisable at the moment).
This kernel will boot these machines without a lot of problems, I don't need any kernel commands to boot my L505D-LS5007 with it. 

If you wish to try the daily build it can be had here:
[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)
You will probably need a DVD for the burn and I can't promise it will work (could be badly broken as it's a alpha build)

The Maverick kernel can be had here:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/")
(Scroll to the bottom of the page)
They create some boot errors when used with Lucid 10.04.
But, they still seemed work Ok for me. 

What I would do is download the 10.10 live CD daily build and test it.
If it worked without problems install it and use it but not update it.
If it's too badly broken then resort to the 2.6.35-rc1 ,rc2 or rc3 kernel with 10.04 Lucid
If you still have ACPI errors with 2.6.35-rc.. kernels try adding acpi=copy_dsdt to the kernel commands.



thanks alot man i definately appreciate it. i certainly cant wait until we are officially supported. i would expect by meerkats october release our patches will be inplemented into generic kernel

---

### Post by Lykopis on 2010-06-27
> **JDuBZisFADED said:**
> thanks alot man i definately appreciate it. i certainly cant wait until we are officially supported. i would expect by meerkats october release our patches will be inplemented into generic kernel

Not a problem, a lot of people here helped me get this up and running and I think we owe all of them a big hand of thanks. 
Yeah: I think the next release of Ubuntu will support these machines, and we won't need to resort to hacks and pre-releases to make things work.
Also it is note-worthy that Ubuntu and Fedora are the only Distro's I have found working with the 2.6.35-rc.. kernels, so they will probably be the first to support the L505 and A505 laptops.

:guitar:

---

### Post by Screwtape on 2010-06-29
Hi, all-
I've tried following Ivan's instructions on my L505D-GS6000 (brand new) and I keep getting a "kernel panic" message. This has happened twice. I think something is going wrong with Nautilus - when I run the "nautilus /usr/src" command, it opens a window in Ubuntu that has both .deb files in it. I install the .deb files but when I close the Terminal window it tells me that a process is still running and if I close the window I will kill it. After waiting a while, I close the window, kill the process, and reboot, only to get a message saying "kernel panic" and that linux can't find my hard drive. Then I get kicked to a command prompt that doesn't know any commands.

Am I just not waiting long enough to shut the Terminal window after starting Nautilus?

Thanks for any help, guys. I'm a little primitive yet and would love to understand what I'm doing wrong. If you think you can help but don't have the specs you need, please say so.

---

### Post by Lykopis on 2010-06-29
> **Screwtape said:**
> Hi, all-
I've tried following Ivan's instructions on my L505D-GS6000 (brand new) and I keep getting a "kernel panic" message. This has happened twice. I think something is going wrong with Nautilus - when I run the "nautilus /usr/src" command, it opens a window in Ubuntu that has both .deb files in it. I install the .deb files but when I close the Terminal window it tells me that a process is still running and if I close the window I will kill it. After waiting a while, I close the window, kill the process, and reboot, only to get a message saying "kernel panic" and that linux can't find my hard drive. Then I get kicked to a command prompt that doesn't know any commands.

Am I just not waiting long enough to shut the Terminal window after starting Nautilus?

Thanks for any help, guys. I'm a little primitive yet and would love to understand what I'm doing wrong. If you think you can help but don't have the specs you need, please say so.

Ok first what version of Ubuntu are you using?
if your using 10.04 Lucid try the 2.6.35-rc3 kernel from here:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.35-rc3-maverick/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.35-rc3-maverick/")

Please read very carefully!!!! 

Download the headers file:
 linux-headers-2.6.35-020635rc3_2.6.35-020635rc3_all.deb

and the correct Kernel image for your install, 32 or 64 bit, one or the other you won't need both:

linux-image-2.6.35-020635rc3-generic_2.6.35-020635rc3_amd64.deb  --- is for 64 bit installs
linux-image-2.6.35-020635rc3-generic_2.6.35-020635rc3_i386.deb --- is for 32 bit installs

You can install them after you download them by double clicking on the files in Nautilus
 (don't try to use Nautilus from a terminal here just go to the menu > Places > Downloads ) .
You will be ask for your password, to proceed with the install. 
Hope I made that one clear.... and only confused myself????

Being for the up coming 10.10 maverick They create some boot errors when used with Lucid 10.04.
But, they still seemed work Ok for me, though I wasn't able to use the proprietary driver from ATI.

If you still have a problem feel free to ask...

---

### Post by rdingraham on 2010-07-01
I just tried the 2.6.35-rc3 kernel.  Boots up without a hitch, except for a few minor error messages.  However, NO WIRELESS.

For the last month I have been using the linux-image-2.6.33.3-l505d, with a customized wireless fix that I got off a Realtek webpage that has now been taken down.  This configuration has worked fine.

If you have a suggestion on how to get the wireless working in 2.6.35-rc3, I'd love to hear it.  Otherwise its back to the 2.6.33.3-l505d kernel.

I am operating a 64 bit machine, Ubuntu 10.4, Toshiba L505D-LS5004.

Bob I.

---

### Post by Lykopis on 2010-07-01
> **rdingraham said:**
> I just tried the 2.6.35-rc3 kernel.  Boots up without a hitch, except for a few minor error messages.  However, NO WIRELESS.

For the last month I have been using the linux-image-2.6.33.3-l505d, with a customized wireless fix that I got off a Realtek webpage that has now been taken down.  This configuration has worked fine.

If you have a suggestion on how to get the wireless working in 2.6.35-rc3, I'd love to hear it.  Otherwise its back to the 2.6.33.3-l505d kernel.

I am operating a 64 bit machine, Ubuntu 10.4, Toshiba L505D-LS5004.

Bob I.
Bob: if you could let me know what wireless device you have maybe I could direct you to a cure or find the source code for it. 
Could you compile it if I gave you the source?
Personally if linux-image-2.6.33.3-l505d was working for you, then you might be well off to use it.

---

### Post by rdingraham on 2010-07-01
> **Lykopis said:**
> Bob: if you could let me know what wireless device you have maybe I could direct you to a cure or find the source code for it. 
Could you compile it if I gave you the source?
And were you having problems with the linux-image-2.6.33.3-l505d Kernel?

1) The set-up I have with the 2.6.33.3-l505d kernel works fine. No problems. However, initially I had to tweak it by going through several steps, covered earlier in this thread, including the dsdt patch and adding an initrd file, in order to get it to boot.

2) My wireless device is a Realtek Semiconductor Co., Ltd. Device [10ec:8172] (rev 10), which works with the module r8192se_pci.  

Initially, the wireless did not work with the l505d kernel. 

I followed the instructions on this page: [http://www.linwik.com/wiki/using+the+realtek+8172+and+8192se+wireless+controller+with+ubuntu+9.10]("http://www.linwik.com/wiki/using+the+realtek+8172+and+8192se+wireless+controller+with+ubuntu+9.10"). Then I downloaded and installed the 8192_se driver, and then ran the command sudo modprobe r8192se_pci. 

The wireless has worked perfectly ever since with the l505d kernel. 

I was hoping I wouln't have to go through all that again with the latest 2.6.35-020635rc3 kernel.  Any advice would be appreciated.

Bob I.

---

### Post by Lykopis on 2010-07-01
Ok from what I see here there is a driver for the r8192e, r8192su and r8192u but not for the r8192se_pci in the Kernel.
 It looks like you would need to reinstall the wireless driver to get it to work. 
I doubt the r8192e driver would work with the r8192se_pci device.

Also you might try the daily build from here:
[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

It has more drivers in it than the rc3 kernel.
I believe r8192se_pci might be one of them.
You will probably need a DVD for the burn and I can't promise it will  work (could be badly broken as it's a alpha build)
What I would do is download the 10.10 live CD daily build and test it.
If it worked without problems you could install it and use it but not update it.
At the moment that is what I am doing and it seems ok, even compiz works

---

### Post by Comodín on 2010-07-01
Hi to all!

I´m new to Ubuntu und just installed Ubuntu 10.04 64 bit on my Satelite L505D S5992 (dual boot with Windows 7 64 bit) and afterwards I installed the kernel patches (DEB-files) from Ivanmmj (thank you!!). The DEB-files named “linux-headers-2.6.32-l505d-speed_2.6.32-l505d-speed-10.00.Custom_amd64”

Everything works fine, but I have a question and hope somebody can help me. When I boot up, I get some error messages and I am wondering where they come from. The messages are:

> pci 0000:03:00.0: BAR 6: no parent found for of device [0xfffe0000-0xfff]
mount: mounting none on /dev  failed: No such device
init: unreadahead main process (350) terminated with status 5

And afterwards Ubuntu will boot up with, as far I can see, full functionality. I´m just curious to know what´s going on.

---

### Post by Lykopis on 2010-07-01
> **Comodín said:**
> Hi to all!

I´m new to Ubuntu und just installed Ubuntu 10.04 64 bit on my Satelite L505D S5992 (dual boot with Windows 7 64 bit) and afterwards I installed the kernel patches (DEB-files) from Ivanmmj (thank you!!). The DEB-files named “linux-headers-2.6.32-l505d-speed_2.6.32-l505d-speed-10.00.Custom_amd64”

Everything works fine, but I have a question and hope somebody can help me. When I boot up, I get some error messages and I am wondering where they come from. The messages are:

pci 0000:03:00.0: BAR 6: no parent found for of device  [0xfffe0000-0xfff]
mount: mounting none on /dev  failed: No such device
init: unreadahead main process (350) terminated with status 5                      

And afterwards Ubuntu will boot up with, as far I can see, full functionality. I´m just curious to know what´s going on.

Well let me see:
```

pci 0000:03:00.0: BAR 6: no parent found for of device  [0xfffe0000-0xfff]

```I am not 100% sure but it looks like you have a device with no driver, but I have on way of telling you what it is at the monent .

```

mount: mounting none on /dev  failed: No such device

```Ok normally "/dev"  refers to some device such as hard-drive, cd-rom and so forth.
Make sure "all" of your hardware is working, 
test your CD-Rom drive the SD-card slot, Microphone and built-in camra if you have them. 
Also these first two errors could be related, so let us know if something doesn't work maybe one of us here has the answer.

```

init: unreadahead main process (350) terminated with status 5                       

```To be honest I don't know what this one means I have seen it on a number of installs and it doesn't seem to cause problems.

---

### Post by Faethin on 2010-07-04
I just want to say THANK YOU GUYS, Ivan, Linux Lurker, Colin, SBaily, Lykus, thank you everyone for your great help! :D I compiled a new kernel following Ivan's instructions and created its correspondent initrd according to SBaily's while listening to the commentary of Colin, Lurker and Lykus (sorry I know that's not your real nick, but I'm talking about you, guy with the wolf his avatar ;))

My laptop is a Toshiba L505D-(don't remember :p) 32-bit running on Ubuntu 10.04. Volume control, battery display, hibernation and stand-by, complete shut-down, everything works! Thank you Ubuntu community!

---

### Post by Linux_Lurker on 2010-07-04
Hey guys, FWIW, I believe they've fixed the IGP thermal issues in the latest Maverick daily builds, with the 35-6 kernel, most of the time, the laptop is running at near ambient temperature.  I'm running a Maverick build from circa last Tuesday, and everything works, except that I can't connect to an unsecured wireless network(I tried mine and a neighbors).  However, I turned wireless security on, and I can connect fine...

---

### Post by Linux_Lurker on 2010-07-04
Even better news, guys...  Today's daily build even has the wireless fixed, as well as an even newer kernel.   

Also, in response to a PM that was sent to me, even though Toshiba removed the original L505d BIOS from the download page, they failed to remove it from their server ;)

[http://cdgenp01.csd.toshiba.com/content/support/downloads/slv6v100.exe](http://cdgenp01.csd.toshiba.com/content/support/downloads/slv6v100.exe)

---

### Post by oryan_dunn on 2010-07-04
What is the need for this bios?  Will the latest maverick work without it?

---

### Post by Linux_Lurker on 2010-07-04
> **oryan_dunn said:**
> What is the need for this bios?  Will the latest maverick work without it?

I never installed the 1.1.0 BIOS, but according to Colin, the 1.1.0 BIOS broke some of the features on the laptop (probably on purpose, apparently Toshiba and/or Insyde Software hate Linux).   Maverick may work without it, maybe somebody who's tried Maverick with the 1.1.0 BIOS could tell you better than I could.

EDIT:  The reason this matters, is because some newer model L505D laptops are coming with the 1.1.0 BIOS pre-installed.

---

### Post by colinwhipple on 2010-07-05
> **Linux_Lurker said:**
> I never installed the 1.1.0 BIOS, but according to Colin, the 1.1.0 BIOS broke some of the features on the laptop (probably on purpose, apparently Toshiba and/or Insyde Software hate Linux).   Maverick may work without it, maybe somebody who's tried Maverick with the 1.1.0 BIOS could tell you better than I could.

EDIT:  The reason this matters, is because some newer model L505D laptops are coming with the 1.1.0 BIOS pre-installed.

Lurker,

I don't remember that the 1.1 Bios broke anything.  It just didn't have any impact on the DSDT bug.

Colin

---

### Post by rdingraham on 2010-07-05
[QUOTE=Linux_Lurker;9546365]Even better news, guys...  Today's daily build even has the wireless fixed, as well as an even newer kernel.   

If you are referring to the v2.6.35-rc4 kernel, posted July 5, I just tried it, and it still does not include support for my Realtek r8192se_pci driver.  The wireless may work on your system, but not on mine.

---

### Post by Lykopis on 2010-07-05
> **rdingraham said:**
> 
If you are referring to the v2.6.35-rc4 kernel, posted July 5, I just tried it, and it still does not include support for my Realtek r8192se_pci driver.  The wireless may work on your system, but not on mine.

Bob: as I understand it the [http://kernel.ubuntu.com/~kernel-ppa/mainline/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/") kernels don't contain the Ubuntu patches. You can confirm if your kernel contains these enhancements by going to--  /lib/modules/"your Kernel number here"/kernel --and looking for a folder named ubuntu. The driver for the Realtek r8192se_pci device is in that folder on the Ubuntu kernel.

---

### Post by seth1991 on 2010-07-05
Hello all,

I realize this is probably an annoying question (as I have read all of these posts and not come to a definitive conclusion), but would these fixes work for a Toshiba Satellite L505-S5990 with the Intel Core 2 Duo processor? If so, where should I begin (if you don't mind me asking...)?

I used to have Ubuntu on my IBM Thinkpad and it worked flawlessly; it was stolen last year and I've been stuck with Windows 7 on my newer laptop. I really want to convert back; I just don't know where to start. I'm not a wizard at getting everything working perfectly; I just want to know if there has been anyone else that has done it on this (or a similar) laptop. I'm willing to put in the work to get it functioning; I miss my days with Ubuntu :(

Thanks!
Seth

---

### Post by rdingraham on 2010-07-06
> **Lykopis said:**
> Bob: as I understand it the [http://kernel.ubuntu.com/~kernel-ppa/mainline/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/") kernels don't contain the Ubuntu patches. You can confirm if your kernel contains these enhancements by going to--  /lib/modules/"your Kernel number here"/kernel --and looking for a folder named ubuntu. The driver for the Realtek r8192se_pci device is in that folder on the Ubuntu kernel.

OK. Here's the deal.  I have three kernels presently installed:

1) 2.6.32-23-generic - This has a folder /lib/modules/"your Kernel number here"/kernel/Ubuntu and it lists a driver r8192se_pci.ko, but the wireless does NOT work with this kernel.

2) The new kernel 2.6.35-020635rc4.  This does not even have a /lib/modules/"your Kernel number here"/kernel/Ubuntu folder and the wireless does NOT work with this either.

3) Ivan's custom 2.6.32.4-l505d kernel.  This also does not have a /lib/modules/"your Kernel number here"/kernel/Ubuntu folder.  However the wireless DOES work.  I got it to work using the method described in one of my recent posts.

I know I can probably get one of the Maverick kernels to work (with the wireless) if I go through the same procedure I did with Ivan's kernel, but frankly I don't want to bother, as long as Ivan's kernel already works.  What I am hoping for is a new kernel in which my wireless will work without having to mess with it.  

Thanks for the comments.

Bob I.

---

### Post by oryan_dunn on 2010-07-06
I tried out one of the recent maverick daily builds on my dad's laptop and everything worked out of the box.  Now the question, will these fixes make their way in lucid 10.04.1?  If possible, I'd like to install an LTS for him and still remain in the realm of the package manager.

---

### Post by Lykopis on 2010-07-06
> **seth1991 said:**
> Hello all,

I realize this is probably an annoying question (as I have read all of these posts and not come to a definitive conclusion), but would these fixes work for a Toshiba Satellite L505-S5990 with the Intel Core 2 Duo processor? If so, where should I begin (if you don't mind me asking...)?

I used to have Ubuntu on my IBM Thinkpad and it worked flawlessly; it was stolen last year and I've been stuck with Windows 7 on my newer laptop. I really want to convert back; I just don't know where to start. I'm not a wizard at getting everything working perfectly; I just want to know if there has been anyone else that has done it on this (or a similar) laptop. I'm willing to put in the work to get it functioning; I miss my days with Ubuntu :(

Thanks!
Seth
Seth:
what I would do is this:
Install 32 bit Ubuntu 10.04
Press F6 at the beginning. 
Choose ACPI=off. 
Boot. 
Install.  
(I would duel boot this to Ubuntu and Win 7 as it's easier to recover if Ubuntu doesn't workout for you.)
Boot into the hard disk. 
Install DEB files from post #159. 
Open up the terminal. 

Code: 
 
sudo gedit /etc/default/grub 
 
Change GRUB_CMDLINE_LINUX so you get: 
Code: 
 
GRUB_CMDLINE_LINUX="acpi=copy_dsdt"

Code: (in terminal)
 
sudo update-grub
 
close terminal

Restart. Done.

---

### Post by Linux_Lurker on 2010-07-06
> **oryan_dunn said:**
> I tried out one of the recent maverick daily builds on my dad's laptop and everything worked out of the box.  Now the question, will these fixes make their way in lucid 10.04.1?  If possible, I'd like to install an LTS for him and still remain in the realm of the package manager.

Highly unlikely...   Chances are, every 10.04.x build will still have the .32 series kernel, with a few backported features here and there...  Anything specific to a newer kernel is pretty much not going to make it in there, they really need to rethink their LTS strategy....   I'd tried 8.04.4 not that long ago, it reeeeeallly sucked, your better off with the bleeding edge Ubuntu...  10.10 is shaping up to be a good one, just like 8.10 was....

---

### Post by seth1991 on 2010-07-06
> **oryan_dunn said:**
> I tried out one of the recent maverick daily builds on my dad's laptop and everything worked out of the box.  Now the question, will these fixes make their way in lucid 10.04.1?  If possible, I'd like to install an LTS for him and still remain in the realm of the package manager.

After reading this post, I did the same thing and tried out a LiveCD of the recent Maverick Daily Builds on my Core2Duo Toshiba Satellite L505-S5990. Everything appears to work perfectly (touchpad, wireless, brightness controls, mute, volume wheel).

I do have one question though: has the ACPI issue been taken care of with this version? I suppose I mean, will the fan kick on and cool the processor off? This is probably a very dumb question, but I kind of thought that the ACPI control entailed all of the controls (brightness, wireless, etc.). 

If so, is this version I am currently running stable? I am a college student that loves Ubuntu for its ease as an amazing OS. I really want to switch back, just want to make sure this potential ACPI issue wouldn't mean a fried processor in a year or two (or less...).

Thanks!
Seth

EDIT: Just heard the fan kick in! Woot! Still though, is all well with it (from a ubuntuforums expert :D opinion)?!

---

### Post by Linux_Lurker on 2010-07-07
@seth:  It should be OK, the recent Maverick builds have cooled things off quite a bit, I think the thermal issues are 90% sorted now.  Besides, I wouldn't worry about thermals too much, unless one or two things are wrong:

1.  The CPU is stuck at max clockspeed, or
2.  The CPU, NorthBridge, or SouthBridge are being over-volted

Otherwise, laptop hardware can handle the heat, there isn't enough electrical potential in a 35w CPU to do any real damage.

---

### Post by seth1991 on 2010-07-07
> **Linux_Lurker said:**
> @seth:  It should be OK, the recent Maverick builds have cooled things off quite a bit, I think the thermal issues are 90% sorted now.  Besides, I wouldn't worry about thermals too much, unless one or two things are wrong:

1.  The CPU is stuck at max clockspeed, or
2.  The CPU, NorthBridge, or SouthBridge are being over-volted

Otherwise, laptop hardware can handle the heat, there isn't enough electrical potential in a 35w CPU to do any real damage.

Linux_Lurker:

Great! Thanks for the response. I don't think it's stuck at max clockspeed (it wasn't getting hot and from the monitor you can add to the top panel, it was varying from low to mid CPU usage with the option of power-saving schemes). I'm not sure about the over-volting business; how could I find out about that?

Everything seems to work well (perfectly, I want to say :) ). My only other question would be: can this computer (under the Maverick Daily Build) install updates via the super easy update manager without failing? If this cannot be answered without trying, how can I do this easily (perhaps thru LiveCD?)?

Thanks so much, all!

---

### Post by Linux_Lurker on 2010-07-08
Actually, there is a 3rd condition that could be real bad....

3.  The CPU fan isn't coming on at all (not sure if that's still possible)...   Even on low speed, it should provide "enough" cooling, even if temps aren't ideal.

> **seth1991 said:**
> 
Everything seems to work well (perfectly, I want to say :) ). My only other question would be: can this computer (under the Maverick Daily Build) install updates via the super easy update manager without failing? If this cannot be answered without trying, how can I do this easily (perhaps thru LiveCD?)?


My suggestion would be:   Don't worry about the updates ;)

Anybody who has tested Alpha builds before, knows that they always manage to completely brick your OS at some point with an update(heck, they even do that when you're not running an alpha build...).   Since I've never had anything approximating a virus in Linux before, I wouldn't worry about not being up-to-date, this isn't Windows ;) .  If your OS is stable, turn off updates altogether.  If you want to upgrade, download the latest daily build, and test it as a live cd.  If it works, then it's safe to upgrade.

---

### Post by seth1991 on 2010-07-08
Linux_Lurker: 

Thanks for being such a great help! The CPU fan had been cutting on and off with the LiveCD run of the Daily Build. 

One question: How would I go about cutting off updates? I'm sure I could find this solution through Google; but if you wouldn't mind sharing, myself and others could find this information beneficial if and when they try to do a similar setup.

Thanks!
Seth

---

### Post by Lykopis on 2010-07-09
> **seth1991 said:**
> Linux_Lurker: 

Thanks for being such a great help! The CPU fan had been cutting on and off with the LiveCD run of the Daily Build. 

One question: How would I go about cutting off updates? I'm sure I could find this solution through Google; but if you wouldn't mind sharing, myself and others could find this information beneficial if and when they try to do a similar setup.

Thanks!
Seth
  Go to the System menu > Administration > Synaptic Package Manager.
1. It will ask for your Password > enter it
2. When Synaptic opens use the settings pull-down menu open the "Repositories" setting.
3. click the updates tab, Uncheck the  "Check for updates' box. 
4. Click the close button.
5. Exit Synaptic ---- Done!

---

### Post by JDuBZisFADED on 2010-07-11
I was curious to see if anyone has had success installing wireless drivers with any of the recent daily builds of meerkat. The disk is not a live cd and i dont want to edit my partitions and install if i dont have to.

sorry for not providing my hardware info.

l505d-gs6000

rtl8192 realtek wireless chip

---

### Post by Lykopis on 2010-07-11
> **JDuBZisFADED said:**
> I was curious to see if anyone has had success installing wireless drivers with any of the recent daily builds of meerkat. The disk is not a live cd and i dont want to edit my partitions and install if i dont have to.

sorry for not providing my hardware info.

l505d-gs6000

rtl8192 realtek wireless chip

You can get the daily build live CD from here:
[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

Ubuntu 10.10 does support the rtl8192se, rtl8192u,rtl8192su and the rtl8192e,
But I don't know about the rtl8192.
All I can say is try the live build from the link above and see.

---

### Post by paxster on 2010-07-12
Hey all
I've been following this thread and by installing the 2.6.35 release candidate kernel I've been able to boot without acpi=off. However, I don't have any wireless. I have the 8187se chipset and have run into problems compiling the driver from source. I can compile other drivers, but not the 8187se. Any suggestions?

EDIT: 10.04 32 bit

---

### Post by Lykopis on 2010-07-13
> **paxster said:**
> Hey all
I've been following this thread and by installing the 2.6.35 release candidate kernel I've been able to boot without acpi=off. However, I don't have any wireless. I have the 8187se chipset and have run into problems compiling the driver from source. I can compile other drivers, but not the 8187se. Any suggestions?

EDIT: 10.04 32 bit

I am not sure why you don't have wireless, my device is a 8187se and I have wireless with the new kernels out of the box. I would suggest you try a live CD from the link in post #369 and let us know if you have wireless with the 10.10 daily build.(how ever if you install the daily alpha builds you do so at your own risk) You should have wireless with the 2.6.36-rc-- kernels in 10.10 Maverick live CD. Then post back with the results, maybe we can get you up and running in 10.04 once I know for sure the problem is in the 10.04 kernel setup.

---

### Post by gialorga on 2010-07-14
> **raven920 said:**
> That's strange, everything works for me, the touchpad, the wireless, the battery status, everything.

I got a Toshiba Satellite L505D-SP6905R and everything works right with the latest ubuntu kernel + the copy_dsdt patch.

Hi 'raven920'. ¿Can you help me?... I've got the same laptop (Toshiba L505D - SP6905R), and I wanna install a linux distro, but I tried and I couldn't... So can you explain me how did you install Linux in your Laptop (Step by step)?.... Thanks in advance.... 'gialorga'...

---

### Post by JDuBZisFADED on 2010-07-15
Just a heads up people. The newest daily build includes a new kernel. this one is based off of 2.6.35-rc5. i am making a live cd right now and will probably come back to say how it went. if i dont i want to hear some responses on how it worked out for you as far as wireless and ati driver support

---

### Post by archiegoodwin on 2010-07-16
> **JDuBZisFADED said:**
> Just a heads up people. The newest daily build includes a new kernel. this one is based off of 2.6.35-rc5. i am making a live cd right now and will probably come back to say how it went. if i dont i want to hear some responses on how it worked out for you as far as wireless and ati driver support

I tried the rc5 kernel yesterday, and my rtl8192se wireless driver still does not work.  However, Lykopis says in post #369 that Ubuntu 10.10 WILL support rtl8192se, so I have hope.

Bob I.

---

### Post by JDuBZisFADED on 2010-07-16
alright thanks. thats too bad

---

### Post by Lykopis on 2010-07-16
Just tried daily build watch out for kernel 2.6.35-8.
It caused problems on my machine.
It sometimes locked the CPU's at full speed.
Wouldn't shut-down properly.
Various other problems.
Kernel 2.6.35-7 works very well though.

---

### Post by JDuBZisFADED on 2010-07-16
> **Lykopis said:**
> Just tried daily build watch out for kernel 2.6.35-8.
It caused problems on my machine.
It sometimes locked the CPU's at full speed.
Wouldn't shut-down properly.
Various other problems.
Kernel 2.6.35-7 works very well though.


thanks for the heads up. is that kernel based on rc5? if not then i hope we dont start backtracking. and btw for those of you with realtek rtl8192/91 i can confirm that wireless does work with the daily build from 2 days ago so it should still be working. just build the drivers the way you did in 10.04 and it should be working. im soo excited for my perfect 10.10 meerkat. its shaping up to be the best os ive ever used. i find functionality and stability to have actually been improved upon from the LTS release of 10.04

---

### Post by Lykopis on 2010-07-16
> **JDuBZisFADED said:**
> thanks for the heads up. is that kernel based on rc5? if not then i hope we dont start backtracking. 
I am not sure on that, But I advise that if you use 10.10 that you add  the CPU Frequency Scaling Monitor to one of your panels. Your CPU should rest at about 800 MHz and go up when under load. If your CPU's stay maxed out you risk thermal damage.

---

### Post by archiegoodwin on 2010-07-17
> **Lykopis said:**
> I advise that if you use 10.10 that you add  the CPU Frequency Scaling Monitor to one of your panels. Your CPU should rest at about 800 MHz and go up when under load. If your CPU's stay maxed out you risk thermal damage.

I have a question.  I added the CPU Frequency Scaling Monitor applet, and it shows my CPU as 2GHz (!) and 100%.  However, when I open up System Monitor from the menu, it shows my CPU load as fluctuating (over time) between 7% and 26%.  In terms of temperature, the range pretty much stays between 35 degrees (C) and 55 degrees, depending on what's loaded.  It never hits 60 degrees.

Is there something I don't understand about the CPU Frequency Scaling Monitor?  Is it really 100%?

This is on the rc5 kernel.   Thanks.

Bob I.

---

### Post by Lykopis on 2010-07-17
> **archiegoodwin said:**
> I have a question.  I added the CPU Frequency Scaling Monitor applet, and it shows my CPU as 2GHz (!) and 100%.  However, when I open up System Monitor from the menu, it shows my CPU load as fluctuating (over time) between 7% and 26%.  In terms of temperature, the range pretty much stays between 35 degrees (C) and 55 degrees, depending on what's loaded.  It never hits 60 degrees.

Is there something I don't understand about the CPU Frequency Scaling Monitor?  Is it really 100%?

This is on the rc5 kernel.   Thanks.

Bob I.
Left click on the applet and choose the Ondemand setting.
Your CPU should drop to a resting of about 800 MHz.

Ok I will try to explain this:

System Monitor shows in the resources tab
1. CPU load/history in percentage
2. Memory and Swap History in  percentage
3. Network History in KiB/s 

The CPU Frequency Scaling Monitor shows:
CPU  Frequency in  percentage and frequency (40% = 800MHz, 70% = 1.40 GHz, 100% = 2GHz on my machine, Your system is probably the same)

---

### Post by Linux_Lurker on 2010-07-17
Just as an FYI, the recent daily builds have tons of problems (the aforementioned breakage I warned of earlier).  Sporadic boot failures and occasional failures to load the Radeon driver.

To the question of the CPU being stuck at 2ghz:   That is a bug that has been coming and going for years, Ubuntu sets the CPU to 2ghz during boot, about 60 seconds after boot it's supposed to switch the speed back to dynamic switching.   However, sometimes it doesn't happen, so you have to click on the applet and change it back yourself.  DO NOT leave it stuck on 2ghz, that is really bad.....

---

### Post by Lykopis on 2010-07-18
> **Linux_Lurker said:**
> Just as an FYI, the recent daily builds have tons of problems (the aforementioned breakage I warned of earlier).  Sporadic boot failures and occasional failures to load the Radeon driver. 
I agree the best solution at this point seems to be install Lucid 10.04 32 bit and use the kernel and headers from post # 159

---

### Post by UncleAelfrich on 2010-07-18
I have a brand new Satellite l505d-gs6000 (great price $500 at Best Buy).

I installed today's Meerkat Daily Build 64 bit (2.6.35-8-generic)  [today = July 18, 2010]

Previously, I had updated Bios to 1.1

I had some problems getting it to work, BUT

It seems to be working fine now.

The wireless networking works. The touchpad works.

I installed the CPU frequency scaling monitor and it rests at 800MHZ but goes up to 2.2 when I open a program. In System Monitor it says that both CPUs are working.

The ATI driver was a real pain. I looked at a bug report and added 

> [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/) maverick main

to my software sources.

I installed the drivers and got all kinds of crashes. Ultimately what I did was uninstall all the ati drivers I could (including gnome ati drivers). I had to launch ubuntu in failsafex mode, but then I installed (or re-installed) fxglrx. This still wouldn't allow me to set the proper configuration. So then I dropped to a command line and

```
sudo aticonfig --initial -f
```

and lo and behold it worked.

Everything seems to be working, but since I am  no where near an expert I can only say everything appears to be working. I will let you know if I experience any problems. However, I would appreciate any advice if I am seeing things correctly so far. Eventually, I will want to install virtualbox so I can run a 32bit Windows XP installation.

TWO Questions:
1. When the advice is to turn off updates, does that mean not to update any packages [e.g.; "sudo apt-get upgrade"]? I should instead try the Live CD of the daily build before I install it? What risks (security) might I encounter with this strategy?

2. This laptop is actually for my wife. I'm trying to convert her to Ubuntu. I want to install the Hello Kitty theme from eyecandy. How do I do this? *I figured this one out.*

I hope this adds to the conversation

---

### Post by Lykopis on 2010-07-19
Welcome to the L505 zoo UncleAelfrich:
I wouldn't worry too much about the risks with turning off the updates. 
I've never had anything that remotely resembles a virus with Linux.
Linux by default uses a very good firewall call IP-Tables, 
it's about 100 times better than that thing MS-Windows calls a firewall.
Rest your mind Linux is very secure by nature.
 
My largest problems with the daily build was:
1. The CPU's sticking at max.
2. Shut-down problems.  

As Linux_Lurker said the CPU sticking is a bug that comes and goes.
The shut-down problems come from ACPI issues. 

My advice at this point in terms of stable and updatability is to use Lucid 10.04 32 bit and download the kernel and header files from post #159.
That  kernel is an Ubuntu kernel with the copy_dsdt patch added.
You will need to edit GRUB and add acpi=copy_dsdt to the kernel command line.
There is instructions on how to edit GRUB in this thread, but I will repost them if you need them. 
This seems to produce a very stable, update-able and usable system for the L505 machines. 
I would be very cautious about using the daily build with a newbie convert who does not yet know how to recover from a system failure, and might lose important data. 10.04 is considered a stable release. Use it instead your wife will have a much better starting out experience.

---

### Post by UncleAelfrich on 2010-07-19
I will consider re-installing everything for her. The main thing that she will need is to run Windows in virtualbox for the programs (Quickbooks) which she uses in her bookkeeping practice. I had not begun that process yet, so it won't be that difficult, (I hope).

---

### Post by Lykopis on 2010-07-19
> **UncleAelfrich said:**
> I will consider re-installing everything for her. The main thing that she will need is to run Windows in virtualbox for the programs (Quickbooks) which she uses in her bookkeeping practice. I had not begun that process yet, so it won't be that difficult, (I hope).
A quick run down of what you have to do to install 10.04 on a L505 is posted here:
[http://ubuntuforums.org/showpost.php?p=9554796&postcount=360](http://ubuntuforums.org/showpost.php?p=9554796&postcount=360)

And here:
[http://ubuntuforums.org/showpost.php?p=8704506&postcount=83](http://ubuntuforums.org/showpost.php?p=8704506&postcount=83)

let us know if you need any help.

---

### Post by archiegoodwin on 2010-07-19
> **Linux_Lurker said:**
> To the question of the CPU being stuck at 2ghz:   That is a bug that has been coming and going for years, Ubuntu sets the CPU to 2ghz during boot, about 60 seconds after boot it's supposed to switch the speed back to dynamic switching.   However, sometimes it doesn't happen, so you have to click on the applet and change it back yourself.  DO NOT leave it stuck on 2ghz, that is really bad.....

I have the CPU Frequency Scaling Monitor 2.30.0 applet installed in the panel.  When I click it, It gives me a number of choices.  At the top, it says: 2 GHz, 1.20 GHz, 800 MHz. At the bottom, it says: Conservative, Ondemand, Performance, Powersave.  No matter what I choose from any of these choices, the applet still reads 2GHz (100%).  If I choose Ondemand, for example, it will show a check mark next to Ondemand, but the applet still reads 2GHz (100%).  Am I missing something?

I tried this on both the rc5 kernel and also Ivan's post #159 kernel. Same result.

Bob I.

---

### Post by Lykopis on 2010-07-20
Sounds like ACPI is still off, You can do a quick confirm by opening the system monitor and count the CPU cores if you see only one then most likely you have ACPI turned off.  

System > Administration > System Monitor resources tab.

there are 2 places that I know of that GRUB holds settings (maybe more)

1.   /ect/grub.d
You will find from 5 to 7 files here. they are all text 

2. /ect/default/grub (text file)

look for a line that says "acpi=off" somewhere in one of these files. 
/ect/default/grub is the most likely spot to look.
remove the command and follow the update grub instructions in this thread.

---

### Post by archiegoodwin on 2010-07-20
> **Lykopis said:**
> Sounds like ACPI is still off, You can do a quick confirm by opening the system monitor and count the CPU cores if you see only one then most likely you have ACPI turned off.  System > Administration > System Monitor resources tab.

there are 2 places that I know of that GRUB holds settings (maybe more)
1.   /ect/grub.d
You will find from 5 to 7 files here. they are all text 
2. /ect/default/grub (text file)

look for a line that says "acpi=off" somewhere in one of these files. 
/ect/default/grub is the most likely spot to look.
remove the command and follow the update grub instructions in this thread.

In the System Monitor resources tab, there is only one graph line in the CPU History box.  Should there be two?
Under the CPU history box, there is a small orange box which says CPU, with the % of load.  Should there be two?

My  /ect/default/grub file has no mention of acpi.  It reads as follows:

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

And none of the files in the /ect/grub.d folder includes the acpi=off command.

---

### Post by Lykopis on 2010-07-20
Here is a screenie for you, this is what you should see in the resources tab;
you will need to edit----> GRUB_CMDLINE_LINUX=""
to read----> GRUB_CMDLINE_LINUX="acpi=copy_dsdt"
in /ect/default/grub 
then run update-grub 
As stated in [http://ubuntuforums.org/showpost.php?p=9554796&postcount=360](http://ubuntuforums.org/showpost.php?p=9554796&postcount=360)
then boot up should be normal.

---

### Post by archiegoodwin on 2010-07-20
> **Lykopis said:**
> Here is a screenie for you, this is what you should see in the resources tab;
you will need to edit----> GRUB_CMDLINE_LINUX=""
to read----> GRUB_CMDLINE_LINUX="acpi=copy_dsdt"
in /ect/default/grub 
then run update-grub 
As stated in [http://ubuntuforums.org/showpost.php?p=9554796&postcount=360](http://ubuntuforums.org/showpost.php?p=9554796&postcount=360)
then boot up should be normal.

Thanks for the help, but still no go.
Here is my new grub file:

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="acpi=copy_dsdt"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

Booted into the rc5 kernel and then into Ivan's custom kernel.  On both, the System Monitor Resources tab still shows only one CPU and the CPU Frequency Scaling Monitor still shows 2 GHz 100%.

?

Bob I.

---

### Post by Lykopis on 2010-07-20
Ok open ---> /boot/grub/grub.cfg 
Copy it here for me[COLOR=Red] but don't edit it.[/COLOR]

---

### Post by archiegoodwin on 2010-07-20
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 39d004ef-5d79-47d6-bc44-100b60f91260
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 39d004ef-5d79-47d6-bc44-100b60f91260
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-020635rc5-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 39d004ef-5d79-47d6-bc44-100b60f91260
	linux	/boot/vmlinuz-2.6.35-020635rc5-generic root=UUID=39d004ef-5d79-47d6-bc44-100b60f91260 ro acpi=copy_dsdt  quiet splash
	initrd	/boot/initrd.img-2.6.35-020635rc5-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-020635rc5-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 39d004ef-5d79-47d6-bc44-100b60f91260
	echo	'Loading Linux 2.6.35-020635rc5-generic ...'
	linux	/boot/vmlinuz-2.6.35-020635rc5-generic root=UUID=39d004ef-5d79-47d6-bc44-100b60f91260 ro single acpi=copy_dsdt
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-020635rc5-generic
}
menuentry 'Ubuntu, with Linux 2.6.32.4-l505d' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 39d004ef-5d79-47d6-bc44-100b60f91260
	linux	/boot/vmlinuz-2.6.32.4-l505d root=UUID=39d004ef-5d79-47d6-bc44-100b60f91260 ro acpi=copy_dsdt  quiet splash
	initrd	/boot/initrd.img-2.6.32.4-l505d
}
menuentry 'Ubuntu, with Linux 2.6.32.4-l505d (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 39d004ef-5d79-47d6-bc44-100b60f91260
	echo	'Loading Linux 2.6.32.4-l505d ...'
	linux	/boot/vmlinuz-2.6.32.4-l505d root=UUID=39d004ef-5d79-47d6-bc44-100b60f91260 ro single acpi=copy_dsdt
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32.4-l505d
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 39d004ef-5d79-47d6-bc44-100b60f91260
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=39d004ef-5d79-47d6-bc44-100b60f91260 ro acpi=copy_dsdt  quiet splash
	initrd	/boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 39d004ef-5d79-47d6-bc44-100b60f91260
	echo	'Loading Linux 2.6.32-23-generic ...'
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=39d004ef-5d79-47d6-bc44-100b60f91260 ro single acpi=copy_dsdt
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-23-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 39d004ef-5d79-47d6-bc44-100b60f91260
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 39d004ef-5d79-47d6-bc44-100b60f91260
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

---

### Post by Lykopis on 2010-07-20
Ok I don't see a problem there that should stop  booting  rc5 but the kernel from ivanmmj in post #159 should be --- 2.6.32.10+drm33.1-l505d-fix-00002-gc70930f-dirty --- and it's 32 bit  You might have the wrong kernel loaded

---

### Post by archiegoodwin on 2010-07-20
Jeez, this is turning into a real nightmare.  OK, you might be right about the 2.6.32.4-l505d kernel being 32 bit. I'm not 100% sure.  To tell you the truth, I've lost track.  However, I have another of Ivan's custom kernels, 2.6.33.3-l505d, which I am positive is 64 bit.  I just installed it, and it booted up fine.  Here is the new grub.cfg file:

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 39d004ef-5d79-47d6-bc44-100b60f91260
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 39d004ef-5d79-47d6-bc44-100b60f91260
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-020635rc5-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 39d004ef-5d79-47d6-bc44-100b60f91260
	linux	/boot/vmlinuz-2.6.35-020635rc5-generic root=UUID=39d004ef-5d79-47d6-bc44-100b60f91260 ro acpi=copy_dsdt  quiet splash
	initrd	/boot/initrd.img-2.6.35-020635rc5-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-020635rc5-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 39d004ef-5d79-47d6-bc44-100b60f91260
	echo	'Loading Linux 2.6.35-020635rc5-generic ...'
	linux	/boot/vmlinuz-2.6.35-020635rc5-generic root=UUID=39d004ef-5d79-47d6-bc44-100b60f91260 ro single acpi=copy_dsdt
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-020635rc5-generic
}
menuentry 'Ubuntu, with Linux 2.6.33.3-l505d' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 39d004ef-5d79-47d6-bc44-100b60f91260
	linux	/boot/vmlinuz-2.6.33.3-l505d root=UUID=39d004ef-5d79-47d6-bc44-100b60f91260 ro acpi=copy_dsdt  quiet splash
	initrd	/boot/initrd.img-2.6.33.3-l505d
}
menuentry 'Ubuntu, with Linux 2.6.33.3-l505d (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 39d004ef-5d79-47d6-bc44-100b60f91260
	echo	'Loading Linux 2.6.33.3-l505d ...'
	linux	/boot/vmlinuz-2.6.33.3-l505d root=UUID=39d004ef-5d79-47d6-bc44-100b60f91260 ro single acpi=copy_dsdt
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.33.3-l505d
}
menuentry 'Ubuntu, with Linux 2.6.32.4-l505d' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 39d004ef-5d79-47d6-bc44-100b60f91260
	linux	/boot/vmlinuz-2.6.32.4-l505d root=UUID=39d004ef-5d79-47d6-bc44-100b60f91260 ro acpi=copy_dsdt  quiet splash
	initrd	/boot/initrd.img-2.6.32.4-l505d
}
menuentry 'Ubuntu, with Linux 2.6.32.4-l505d (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 39d004ef-5d79-47d6-bc44-100b60f91260
	echo	'Loading Linux 2.6.32.4-l505d ...'
	linux	/boot/vmlinuz-2.6.32.4-l505d root=UUID=39d004ef-5d79-47d6-bc44-100b60f91260 ro single acpi=copy_dsdt
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32.4-l505d
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 39d004ef-5d79-47d6-bc44-100b60f91260
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=39d004ef-5d79-47d6-bc44-100b60f91260 ro acpi=copy_dsdt  quiet splash
	initrd	/boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 39d004ef-5d79-47d6-bc44-100b60f91260
	echo	'Loading Linux 2.6.32-23-generic ...'
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=39d004ef-5d79-47d6-bc44-100b60f91260 ro single acpi=copy_dsdt
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-23-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 39d004ef-5d79-47d6-bc44-100b60f91260
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 39d004ef-5d79-47d6-bc44-100b60f91260
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

The 2.6.33.3-l505d kernel boots up fine.  However, System Monitor still shows only one CPU.  I am positive that both the 2.6.33.3-l505d kernel and the rc5 kernel are 64 bit.

Also, the wireless is again broken with the 2.6.33.3-l505d kernel. It only works with the 2.6.32.4-l505d kernel, because that was the one I applied the realtek patch (or whatever it was) to.  Anyway, it seems to me the CPU is the bigger problem, so it would be nice to fix that first.

Bob

---

### Post by Lykopis on 2010-07-20
Well seems you had better luck with the daily build than I did. It got really broken on my system. My current configuration is Lucid 10.04 32 bit. using the kernel from post #159.
that proved to be very stable on me. I even got compiz running with lots of eye candy.
All I can say at this point is if the daily build works then you might have to use it.  

Anyway I hate to leave you in distress, but it's 1:00 AM here and I need to get up early in the morning.  :( 
Do stay with this thread though, we are always moving towards new solutions for these machines.

---

### Post by UncleAelfrich on 2010-07-20
> **Lykopis said:**
> I wouldn't worry too much about the risks with turning off the updates. . . . 
 
My largest problems with the daily build was:
1. The CPU's sticking at max.
2. Shut-down problems.  

As Linux_Lurker said the CPU sticking is a bug that comes and goes.
The shut-down problems come from ACPI issues. 

My advice at this point in terms of stable and updatability is to use Lucid 10.04 32 bit and download the kernel and header files from post #159.
That  kernel is an Ubuntu kernel with the copy_dsdt patch added.
You will need to edit GRUB and add acpi=copy_dsdt to the kernel command line.
There is instructions on how to edit GRUB in this thread, but I will repost them if you need them. 
This seems to produce a very stable, update-able and usable system for the L505 machines. 
I would be very cautious about using the daily build with a newbie convert who does not yet know how to recover from a system failure, and might lose important data. 10.04 is considered a stable release. Use it instead your wife will have a much better starting out experience.

I did what you suggested. However, the problem with the 10.04 kernel (even as ivanmmj patched it) is that the rtl8192se wireless driver doesn't work, which it did with the 10.10 daily build I installed.

As I said before, my laptop didn't seem to display the problems you mentioned regarding cpu sticking and shutdown. Could that be because your laptop has the Athlon II processor and mine has the Turion II processor? [my laptop = l505d-gs6000]

My inclination is to go back to the 10.10 build that seemed to work, unless I can be pointed to a kernel that has a working patch for my wireless card.

I would appreciate any suggestions or comments. Thanks.

---

### Post by Lykopis on 2010-07-20
> **UncleAelfrich said:**
> 

As I said before, my laptop didn't seem to display the problems you mentioned regarding cpu sticking and shutdown. Could that be because your laptop has the Athlon II processor and mine has the Turion II processor? [my laptop = l505d-gs6000]

My inclination is to go back to the 10.10 build that seemed to work, unless I can be pointed to a kernel that has a working patch for my wireless card.

I would appreciate any suggestions or comments. Thanks.
At this point I am inclined to agree with you. It seems option 2 (Daily Build 10.10) is your best choice.  I know others have had the problems you describe with the gs6000. If you install 10.10 just make sure your system is completely stable before you turn it over to your wife.  The reason I stayed with Linux over MS-Windows was because I had a really good/pleasant first exposure to it (and a Linux Geek for a neighbor) .  A good first impression is really important to keep a person hooked on a Linux box

---

### Post by archiegoodwin on 2010-07-20
In the ongoing quest for Ubuntu-Toshiba functionality:

Today I downloaded and burned to disk the latest 10.10 (64 bit) build, and then booted off the disk into Ubuntu.  No error messages, smooth boot-up, AND the wireless worked flawlessly from scratch.  However, System Monitor Resources still only shows one CPU core running.

At this point, I did a little checking around, and according to what I found, my laptop (Satellite L505D-LS5004) has an AMD Sempron M100 Processor, and it seems that this is actually a **single core** processor.  So maybe there isn't supposed to be a second CPU in System Monitor?

Two questions:

1) If this indeed is a single core processor, how do I resolve the CPU Frequency Scaling being set at 2GHz (100%)? [see earlier posts]

2) Anyone think it is safe to install the 10.10 build, and, if so, as an upgrade or a clean install?

I really want to solve this CPU frequency scaling problem.  I don't want to fry my laptop.

Bob I.

---

### Post by Lykopis on 2010-07-20
> **archiegoodwin said:**
> In the ongoing quest for Ubuntu-Toshiba functionality:

Today I downloaded and burned to disk the latest 10.10 (64 bit) build, and then booted off the disk into Ubuntu.  No error messages, smooth boot-up, AND the wireless worked flawlessly from scratch.  However, System Monitor Resources still only shows one CPU core running.

At this point, I did a little checking around, and according to what I found, my laptop (Satellite L505D-LS5004) has an AMD Sempron M100 Processor, and it seems that this is actually a **single core** processor.  So maybe there isn't supposed to be a second CPU in System Monitor?

Two questions:

1) If this indeed is a single core processor, how do I resolve the CPU Frequency Scaling being set at 2GHz (100%)? [see earlier posts]

2) Anyone think it is safe to install the 10.10 build, and, if so, as an upgrade or a clean install?

I really want to solve this CPU frequency scaling problem.  I don't want to fry my laptop.

Bob I.
A little research says that CPU is a single core. The AMD site doesn't really say much about it though. So yeah you would have only one CPU showing in the system monitor. I believe you said that with 10.10 Daily Build your CPU rested at 800 MHz? You can test it with the live CD. Just add the CPU Frequency Scaling Monitor to one of the panels. If the CPU scales properly and you don't have start-up, stability, or shut-down/suspend problems after it's installed then I would think it's a safe install. I would do a clean install so you would need to backup any important data you have on the machine. If the scaling issue crops up, I am sorry I don't have an answer as to how to fix that one. For me it was necessary to drop back to Lucid, but that didn't work for you so I would be lost, maybe someone else here has an answer.

---

### Post by archiegoodwin on 2010-07-20
> **Lykopis said:**
>  I believe you said that with 10.10 Daily Build your CPU rested at 800 MHz? You can test it with the live CD. Just add the CPU Frequency Scaling Monitor to one of the panels. If the CPU scales properly and you don't have start-up, stability, or shut-down/suspend problems after it's installed then I would think it's a safe install. I would do a clean install so you would need to backup any important data you have on the machine.

Just tried it again (from the CD). Installed the panel Frequency Scaling applet.  Voila!  Scaling Monitor shows 800 MHz 
(40%).

So with the Maverick Live CD, wireless works, CPU Scaling works, and no error messages at boot-up or shut-down.

I'll probably do the full install, but wait a day or so, to see if anyone jumps in with a good reason not to.  I assume if I do the install, it would be best to hold off on all updates until at least the beta comes out.

Bob I.

---

### Post by Lykopis on 2010-07-20
Sounds Good:
I may have gotten you 2---- archiegoodwin and UncleAelfrich mixed up a bit if I did I apologize. hope you enjoy Ubuntu  :popcorn:

---

### Post by archiegoodwin on 2010-07-23
Just thought people might be interested in this.  Wiped my hard drive and installed the Maverick Alpha (with the rc9 kernel) three days ago.  Been using it as my everyday operating system since. A report for those interested:

The alpha is perfectly usable, with pretty much full functionality.  Some breakage and crashes, but that is to be expected.  The only program that I use which will not function, is virtualbox. It won't install.  I'm sure all of this will be fixed by the beta or final release.

In terms of the Toshiba problem, everything is fixed, with one exception.  No boot-up or shut down error messages;  wireless works out of the box;  frequency scaling works (resting at 800 MHz), and the laptop seems to be running a little bit cooler (40 to 45 degrees, as opposed to 50+ degrees);  Network printing no problem;  Audio & video fine. Everything OK.

The only thing still not working, on my system, is the ATI graphics driver.  It would not install.

Anyway,  it seems that 10.10 will fix all of the Toshiba problems, so good news for everyone.

Bob I.

---

### Post by Linux_Lurker on 2010-07-23
> **archiegoodwin said:**
> Some breakage and crashes, but that is to be expected.


Actually, if you can find a daily build circa June 30th, there pretty much isn't any breakage at all.  I reinstalled the June 30th daily build after trying one from around July 15th, they broke quite a lot of stuff around that time....

---

### Post by Lykopis on 2010-07-28
> **Linux_Lurker said:**
> Actually, if you can find a daily build circa June 30th, there pretty much isn't any breakage at all.  I reinstalled the June 30th daily build after trying one from around July 15th, they broke quite a lot of stuff around that time....

  For those of you who are having trouble with current Daily Builds 
you can find the Alpha 2 (June 30th - July 1)  build here:

[http://cdimage.ubuntu.com/releases/10.10/alpha-2/](http://cdimage.ubuntu.com/releases/10.10/alpha-2/)

All though I think you will have to use the alternate install:

32 bit:
 [http://cdimage.ubuntu.com/releases/10.10/alpha-2/maverick-alternate-i386.iso](http://cdimage.ubuntu.com/releases/10.10/alpha-2/maverick-alternate-i386.iso)

64 bit:
[http://cdimage.ubuntu.com/releases/10.10/alpha-2/maverick-alternate-amd64.iso](http://cdimage.ubuntu.com/releases/10.10/alpha-2/maverick-alternate-amd64.iso)

---

### Post by archiegoodwin on 2010-08-05
Anyone tried the Alpha 3 yet?  Any thing to report?

---

### Post by Lykopis on 2010-08-05
> **archiegoodwin said:**
> Anyone tried the Alpha 3 yet?  Any thing to report?
Not yet but I downloaded the Ubuntu Kernel 2.6.35-14 from the repo and added it to alpha 2. it's stable now, as kernel 2.6.35 is now finalized. Might download and try alpha 3 soon though.

alpha-3 here:
[http://cdimage.ubuntu.com/releases/10.10/alpha-3/](http://cdimage.ubuntu.com/releases/10.10/alpha-3/)

---

### Post by archiegoodwin on 2010-08-05
> **Lykopis said:**
> Not yet but I downloaded the Ubuntu Kernel 2.6.35-14 from the repo and added it to alpha 2. it's stable now, as kernel 2.6.35 is now finalized. Might download and try alpha 3 soon though.

alpha-3 here:
[http://cdimage.ubuntu.com/releases/10.10/alpha-3/](http://cdimage.ubuntu.com/releases/10.10/alpha-3/)

Can I ask where you downloaded the 2.6.35-14 Kernel from?  The last kernel listed on the Ubuntu PPA site at [http://kernel.ubuntu.com/~kernel-ppa/mainline/]("http://kernel.ubuntu.com/~kernel-ppa/mainline/") is the v2.6.35-rc6-maverick/ kernel.  Is that the same thing?  Or can you point me to the right place?

Bob I.

---

### Post by Lykopis on 2010-08-06
> **archiegoodwin said:**
> Can I ask where you downloaded the 2.6.35-14 Kernel from?  The last kernel listed on the Ubuntu PPA site at [http://kernel.ubuntu.com/~kernel-ppa/mainline/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/") is the v2.6.35-rc6-maverick/ kernel.  Is that the same thing?  Or can you point me to the right place?

Bob I.
I used Synaptic Package Manager on 10.10 alpha 2 but only allowed it to download the new kernel & header files that matched my installation.

You can find the 2.6.35 kernel on the PPA site here:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.35-maverick/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.35-maverick/")

Keep in mind though that the PPA kernels are pretty much plain kernels without the Ubuntu add-ons & patches.
I also tried this Kernel under 10.04 with good results; but it still gives 10.04 some boot-up errors as I said before.

---

### Post by Linux_Lurker on 2010-08-08
> **archiegoodwin said:**
> Anyone tried the Alpha 3 yet?  Any thing to report?   LOL, complete and utter failure.  Won't even get to the boot screen, gives a message like 
"invalid keyword in config file"

.  It's been that way for about a week or so, don't know why they haven't fixed it yet.

---

### Post by Linux_Lurker on 2010-08-12
> **Linux_Lurker said:**
> LOL, complete and utter failure.  Won't even get to the boot screen, gives a message like 
"invalid keyword in config file"

.  It's been that way for about a week or so, don't know why they haven't fixed it yet.


OK, after some digging around, you can make the live CD for Alpha 3 work.  It will fail to start, at the boot prompt, type "live" (without quotes), and it will boot into live mode.   It works pretty well, but I'm not sure if it can be successfully installed...

---

### Post by Lykopis on 2010-08-13
Linux_Lurker: 
Are you testing the 64 bit or 32 bit version of Ubuntu 10.10? 
I tested the 32 bit version alpha 3 Live-CD and it booted just fine for me. 
I never tried to install it though.
My problem with recent daily builds has been after an install to my 
hard-drive then it wouldn't boot.

---

### Post by Linux_Lurker on 2010-08-13
I need the 64 bit version, I have some code that I can only test on Windows Server 2008, which is 64-bit only, and AMD-V support is disabled on this laptop, which means I need 64 bit Linux.  I haven't tried the 32 bit.

---

### Post by Lykopis on 2010-08-13
I don't know if it would help you, but you might try the full install DVD for 10.10.
It's a really hefty download though--- 4.7 gig!
[http://cdimage.ubuntu.com/releases/10.10/alpha-3/maverick-dvd-amd64.iso](http://cdimage.ubuntu.com/releases/10.10/alpha-3/maverick-dvd-amd64.iso)

---

### Post by Linux_Lurker on 2010-08-25
> **Linux_Lurker said:**
> OK, after some digging around, you can make the live CD for Alpha 3 work.  It will fail to start, at the boot prompt, type "live" (without quotes), and it will boot into live mode.   It works pretty well, but I'm not sure if it can be successfully installed...

FYI, you can make a Linux live USB key work properly by going into the /syslinux/syslinux.cfg file and removing the word "UI" from the last line.  The current daily build seems very stable thus far.

---

### Post by orthopod on 2010-08-26
used fresh instal, and works perfectly - everything - cpu freq scaling, battery, fans, wireless, graphics, sound, hibernate
no grub arguments needed either

---

### Post by Lykopis on 2010-08-26
Yes current Ubuntu 10.10 seems stable. 
I have had problems with the policykit app. not closing properly at shutdown or logout requiring a force quit.

---

### Post by gyromaniac on 2010-08-28
Confirmed. Ubuntu Maverick Meerkat 64 WORKS on an L505D. The Ubuntu Team still has some work to do, though. Happy with it overall.

---

### Post by Lykopis on 2010-09-03
Using Ubuntu 10.10 (full update as of today, Sept 3 2010) seems really stable and boots without any major errors. Looks like 10.10 will work just fine on these laptops.

Edit:
10.10 beta is out you can get it here:
[http://gb.releases.ubuntu.com/10.10/](http://gb.releases.ubuntu.com/10.10/)

You will probably want the Desktop CD.
I have not tried it so I make no promises.

---

### Post by jcer93705 on 2010-10-10
> **Lykopis said:**
> Using Ubuntu 10.10 (full update as of today, Sept 3 2010) seems really stable and boots without any major errors. Looks like 10.10 will work just fine on these laptops.

Edit:
10.10 beta is out you can get it here:
[http://gb.releases.ubuntu.com/10.10/](http://gb.releases.ubuntu.com/10.10/)

You will probably want the Desktop CD.
I have not tried it so I make no promises.

Do you have the same problem as me with ubuntu 10.10 rc? Mouse pad being too sensitive that it detect the palm from mm of distance?

---

### Post by Lykopis on 2010-10-18
> **jcer93705 said:**
> Do you have the same problem as me with ubuntu 10.10 rc? Mouse pad being too sensitive that it detect the palm from mm of distance?

Yes the touch pad is really sensitive even with 10.10 final.
I haven't tried to fix it yet though.

---

### Post by jcer93705 on 2010-10-18
> **Lykopis said:**
> Yes the touch pad is really sensitive even with 10.10 final.
I haven't tried to fix it yet though.

Be cool to disable that touch pad whenever we want it to be disable. I use a mouse with my laptop anyways.

---

### Post by Lykopis on 2010-10-19
> **jcer93705 said:**
> Be cool to disable that touch pad whenever we want it to be disable. I use a mouse with my laptop anyways.
The only way I found to disable the touch pad was through MS-Windows.
If you still have MS-Windows on the machine you can disable the touch pad 
using the (FN) keys, the settings will stick when you boot back into Ubuntu.
:rolleyes:

---

### Post by jcer93705 on 2010-10-19
> **Lykopis said:**
> The only way I found to disable the touch pad was through MS-Windows.
If you still have MS-Windows on the machine you can disable the touch pad 
using the (FN) keys, the settings will stick when you boot back into Ubuntu.
:rolleyes:

Hmmm really yea right are you serious? To bad if its true my window 7 is jacked up of a nasty trojan cant even go safe mode. LOL

---

### Post by Lykopis on 2010-10-21
> **jcer93705 said:**
> Hmmm really yea right are you serious? To bad if its true my window 7 is jacked up of a nasty trojan cant even go safe mode. LOL
  Yeah, it's true.... But I don't have that option either.
I tossed MS-Windows also, as soon as 10.10 became final. I deleted MS-Windows 7, 
the recovery partition and that funky Windows 7 boot partition then reinstalled Ubuntu. 
MS-Windows 7 was supposed to be more secure :rolleyes:Yeah right it took 3 days from the
purchase date for someone to break into and comprise Windows 7 on this machine. 
Sorry, but my opinion of Windows 7 is not even printable.

---

### Post by jcer93705 on 2010-10-21
> **Lykopis said:**
> Yeah, it's true....
I tossed MS-Windows also, as soon as 10.10 became final. I deleted MS-Windows 7, 
the recovery partition and that funky Windows 7 boot partition then reinstalled Ubuntu. 
MS-Windows 7 was supposed to be more secure :rolleyes:Yeah right it took 3 days from the
purchase date for someone to break into and comprise Windows 7 on this machine. 
Sorry, but my opinion of Windows 7 is not even printable.

I don't think ubuntu 10.10 can match window 7. Window 7 is secured just have to setup up the system so you just run on limited account and gaming is awesome on it. Don't get me wrong i love ubuntu but it just cant keep up with mainstream os. My problem is if i can get quake 3 1.30 going in in linux then I will dump window 7 totally and run window xp in virtual machine. Serously window 7 is blowing everything away face it. But in smartphone android is whooping some ***. Linux isn't mature yet. 
Games should run without a problem in linux. All the games i put in ubuntu most of them have no sound or have sound but very laggy. I have a quake 3 pointrelease 1.30.run does not execute and says i have a Error in check sums 577480866 3671794242
but when i run the same file in redhat 9 in virtual machine it runs. Damnit11 Window 7 is the best os that microsoft ever done. Everything from dos to now application run in window 7, linux just i love linux but not ready for tranfering from window to linux. I'm frustrated right now. 

Sorry guys.

---

### Post by Lykopis on 2010-10-21
Somewhere I saw a port for Q3 to Linux, (I Think it was under Mandriva).
But I don't game so it really doesn't interest me. 
You might look at the ID Software site & find it.
As for Linux VS Windows, the Virus issues alone are enough to stop me.
Linux's security model  (Poorly copied by Vista & Win 7) is far superior to any version of Windows.

---

### Post by jcer93705 on 2010-10-21
> **Lykopis said:**
> Somewhere I saw a port for Q3 to Linux, (I Think it was under Mandriva).
But I don't game so it really doesn't interest me. 
You might look at the ID Software site & find it.


No, my file isn't missed up it just that ubuntu have a fit with quake 3 (1.30 version) patch, but yea i can download the latiest and install it easy. But that patch i want work with redhat but doesn't work with ubuntu i'm going to try fedora latiest one see if it execute it. But latiest quake 3 patch does work with ubuntu and the first patch for quake 3. My server is in 1.30 and 1.30 is the version i like not much servers but theres still people and my server is kindof popular, if i go to the version that does work on my l505d i'm fk because i will loose all the client that play on the server. Also quake 3 sound doesn't work in ubuntu. Wine hq should put alot more balls in their product because that is what we need. Everything from linux and open source has so much bugs that i'm encounter these past weeks.

---

### Post by jcer93705 on 2010-10-21
> **Lykopis said:**
> Somewhere I saw a port for Q3 to Linux, (I Think it was under Mandriva).
But I don't game so it really doesn't interest me. 
You might look at the ID Software site & find it.
As for Linux VS Windows, the Virus issues alone are enough to stop me.
Linux's security model  (Poorly copied by Vista & Win 7) is far superior to any version of Windows.

Well the thing is all the virus, trojan and spywares and other nasty thing is target to window since its a popular os. Also theres a reason why its so popular right? Just like android phones its more popular now then iphone 4. Why? Simply better. But i just hate that window work better then anything else thats why i want linux!! Show them all that linux work out of box with everything. But thats not the case that i experience with.

---

### Post by Lykopis on 2010-10-21
> **jcer93705 said:**
> No, my file isn't missed up it just that ubuntu have a fit with quake 3 (1.30 version) patch, but yea i can download the latiest and install it easy. But that patch i want work with redhat but doesn't work with ubuntu i'm going to try fedora latiest one see if it execute it. But latiest quake 3 patch does work with ubuntu and the first patch for quake 3. My server is in 1.30 and 1.30 is the version i like not much servers but theres still people and my server is kindof popular, if i go to the version that does work on my l505d i'm fk because i will loose all the client that play on the server. Also quake 3 sound doesn't work in ubuntu. Wine hq should put alot more balls in their product because that is what we need. Everything from linux and open source has so much bugs that i'm encounter these past weeks.
No what I mean is a Quake 3 main file that runs under Linux without Wine I.E. a Linux executable file, it might be in the Ubuntu synaptic. Otherwise look at 
[http://www.idsoftware.com/games/quake/quake3-arena/index.php?game_section=demo](http://www.idsoftware.com/games/quake/quake3-arena/index.php?game_section=demo)
You will find the Linux demo there. Use your *.pak files from your full windows version, it should work. As I said I don't game any more so I can't promise you.
I don't know what "bugs" you might refer to, as Ubuntu 10.10 runs Quite well on my machine. I can watch YouTube files, play CD's and with the Mediubuntu repository, DVD's work fine in Totem. I have compiz running and full 3D effects, the only time I get a crash is if I  do something that's stupid.

---

### Post by Lykopis on 2010-10-21
> **jcer93705 said:**
> Well the thing is all the virus, trojan and spywares and other nasty thing is target to window since its a popular os. Also theres a reason why its so popular right? Just like android phones its more popular now then iphone 4. Why? Simply better. But i just hate that window work better then anything else thats why i want linux!! Show them all that linux work out of box with everything. But thats not the case that i experience with.
The reason it's so popular is called monopoly-- MS-Windows comes on almost every PC sold, and Microsoft wants it that way. Check out this Novell web page:
[http://support.novell.com/techcenter/articles/nc2005_02c.html](http://support.novell.com/techcenter/articles/nc2005_02c.html)
Most "People" just use MS-Windows because it's already there. Some don't even know there is an alternative that's available to them. I have used Linux for over 6 years and still don't know all there is to know. Then how can one just try it for a few days and get a real feel for any distro? Not going to happen my friend. In that 6 years I never had a Linux system compromised or broken into, & nothing that even comes close to a virus. As I said before MS-Windows was  compromised 3 days after I purchased this Laptop. Windows FireWall Failed it's just that simple. Most Internet servers are running some *nix platform and not MS-Windows, Why? Because Unix / Linux & BSD are far more secure. As for out of the box experience with Linux. I can tell you a Toshiba A505 or L505 is not a good starter PC. Try a common desktop PC instead, Say a Dell or IBM (now called Lenovo).
However if you choose MS-Windows over Linux that's your choice, just as I choose to use Linux, so if you are happy with it cool then :guitar:

---

### Post by jcer93705 on 2010-10-21
> **Lykopis said:**
> No what I mean is a Quake 3 main file that runs under Linux without Wine I.E. a Linux executable file, it might be in the Ubuntu synaptic. Otherwise look at 
[http://www.idsoftware.com/games/quake/quake3-arena/index.php?game_section=demo](http://www.idsoftware.com/games/quake/quake3-arena/index.php?game_section=demo)
You will find the Linux demo there. Use your *.pak files from your full windows version, it should work. As I said I don't game any more so I can't promise you.
I don't know what "bugs" you might refer to, as Ubuntu 10.10 runs Quite well on my machine. I can watch YouTube files, play CD's and with the Mediubuntu repository, DVD's work fine in Totem. I have compiz running and full 3D effects, the only time I get a crash is if I  do something that's stupid.

Well i've been coping couple iso to a back up drive few min ago and frozed my laptop with cap luck led blinking. Some how virtual machine when i run it i ran fedora iso and i click on install in fedora live and doesn't do anything, many games sound isn't working, alot of compatibility issues. You are a person that does basic stuff like watch movies, listen mp3 and run compiz. But if you get to gaming, i don't game much but still addicted to some games. Wine is terrible app to run window app. I installed quake 3 there and damn mouse would get stuck on one side and just crazy.  Linux is great for multimedia though. Do you have toshiba l505d gs6000? Can you do copy and paste without crashing????? There this one media center that comes with sabayon linux and i tried going by installing it in ubuntu without sucess.

---

### Post by Lykopis on 2010-10-21
> **jcer93705 said:**
> Well i've been coping couple iso to a back up drive few min ago and frozed my laptop with cap luck led blinking. Some how virtual machine when i run it i ran fedora iso and i click on install in fedora live and doesn't do anything, many games sound isn't working, alot of compatibility issues. You are a person that does basic stuff like watch movies, listen mp3 and run compiz. But if you get to gaming, i don't game much but still addicted to some games. Wine is terrible app to run window app. I installed quake 3 there and damn mouse would get stuck on one side and just crazy.  Linux is great for multimedia though. Do you have toshiba l505d gs6000? Can you do copy and paste without crashing????? There this one media center that comes with sabayon linux and i tried going by installing it in ubuntu without sucess.
The problem with "All" Toshiba A505 and L505's is the INSYDE Bios, that thing is so buggy it should be tossed. I can copy & paste just fine. However I don't use virtual machine, I found performance under it to be totally unacceptable. As to the Sabayon Media Center  I think you are referring to XBMC, it's really just X-box Media Center.
 You can find it here:
[http://xbmc.org/](http://xbmc.org/) 
I never tried to install it though.
As to Compiz, Well it's not "Basic stuff", it's not enabled or installed by default. and it will slow down a PC if the video card is not up to it & there are some PC's it won't run on at all. Wine really isn't all that good for MS-Windows games. It will run some Windows Apps, But not all. I did use Photoshop with it for a while though.
My advice to people is "If you are a gamer use an X-Box or a MS-Windows PC."

PS: 
For Linux to work properly on an A505 or a L505 or any PC Using the INSYDE bios you need a distro  that uses Kernel 2.6.35.* or better
And you still might have to use the -- [FONT=monospace]acpi=[/FONT]copy_dsdt -- Kernel command for it to boot up.
At this time Sabayon and Ubuntu are about all that's stable on that Kernel. Fedora won't use that Kernel till Fedora 14 -- still in beta.
OpenSuse will use it in 11.4 -- still in milestone... Others I just don't know about.

---

### Post by wildcard_seven on 2010-11-19
I just want to say that I feel I share a bond with all who have went through this ordeal, which for most, began in that fateful holiday season upon the cusp of 2010. 

I waited for a proper Linux installation, unsatisfied with the hack-ish fixes attempted in the early going. Today, a dream has come to fruition. In truth, I had been using virtualbox through windows to satisfy the work I'd rather do on a linux machine, but I got burnt for the last time with malware....while running as a regular user, with antivirus/spyware installed, etc...

Came back to this thread, saw the boon had been achieved.

[IMG]http://bullylug.org/linux-penguin.jpg[/IMG]

[IMG]http://images.whatport80.com/images/thumb/c/cf/Trollface.jpg/400px-Trollface.jpg[/IMG]

---

### Post by Lykopis on 2010-11-21
Glad you are happy with Ubuntu. 
I know there are some that still have problems and it's not perfect yet on all 505 machines, 
I believe the next Linux Kernel will be much better on these Machines .
I did discover that if you use Kubuntu rather than Ubuntu you can disable 
the Touch-Pad in KDE's system settings for easier typing. 
At this time it's not possible in Ubuntu's Gnome desktop. 
I haven't tried  Kubuntu out very well though so there could be other problems.
So if you are up to the experimenting that could prove to be a good set up for some of us.

---

### Post by mchype on 2011-06-05
hey there guys! 

so i haven't spent the time to go through this entire thread, and for that, I am very sorry. But my goal here is to try to help out some others if they are still having issues with booting their toshiba laptops past the "kernel_thread_helper" on live CD or the actual installation.

This can be fixed by following this tutorial: [http://community.linuxmint.com/tutorial/view/420]("http://community.linuxmint.com/tutorial/view/420")

I wrote it, because I had only found the fix for My laptop in one place, and it took me over a month to find 1 line of code. 

I apologize if it is too hard to understand. I do hope that everyone will benefit from the tutorial! 

Hope all is well!

---

### Post by vishaluc on 2012-02-13
Hi, I'v got the Toshiba L750 model. Could anyone help me with a step by step procedure to install ubuntu(any version). Never faced any problem while installing it on my desktop, but apparently toshiba doesn't support op systems apart from windows! i tried installing it, but while booting it doesn't show any option other than win7. Also the "help boot from CD" option  doesn't work.

---

