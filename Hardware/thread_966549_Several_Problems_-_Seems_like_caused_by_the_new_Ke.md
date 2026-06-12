---
title: "Several Problems - Seems like caused by the new Kernel"
date: 2008-11-01
forum: Hardware
---

### Post by Shrooms on 2008-11-01
Hello,

I hope this is the best fitting Sub-Forum for my problems because they are somehow difficult to keep in one category.

Since I updated Ubuntu via Update Manager before 2 days to the newest distribution release 8.10 32-Bit, Intrepid Ibex (before I had 8.04 32-Bit) I experience the following problems:

[LIST]
[*]Seems like Ubuntu can't control the CPU cooler anymore, because it runs always with the maximum RPM
[*]My Notebook needs several minutes after the shutdown-bootscreen disappeared to completely shut down when I run Ubuntu. Sometimes Messages like "acpid disconnected" appear.
[*]Applications run very slowly (Takes several Seconds to open a Window, I can see how it is built up), like the System has to handle something really heavy (like rendering something with Blender), but CPU and Memory Usage are as always
[/LIST]

That only appears when I boot with the new Kernel 2.6.27-7-generic, not if I boot with 2.6.24-16-generic.

I also downloaded yesterday the new CD Images of Kubuntu (64-Bit) and Xubuntu (64-Bit). I tested the live CD of Kubuntu, and it was also so damn slow (I know, the system has to read everything from the optical drive, but even that used to be much faster) opening windows and interaction with the user interface, but the cursor moved smoothly.

I hope you know something or that I am at least not alone with that problems. If there's no solution (even a new installation won't work) my Ubuntu must be the Atlantis of my Computer. Forever lost. :(

---

### Post by otetiani on 2008-11-03
I have the same slow shutdown with an acpid error but none of the other issues.  It takes about 2 minutes to shutdown.  All apps work well though and I play Oblivion via Crossover Games (works great).
Just switched to this laptop since I got sick of waiting for ATI to come out with an open driver for Radeon Mobility HD 2600
I am using an Asus V2S with an NVIDIA graphics card.  First time I've run Ubuntu on it, though I've used Ubuntu exclusively for 2.5 years now.

For now looking for solution, but can live with it for now.

---

### Post by Shrooms on 2008-11-06
Seems like the problem has been fixed (Google showed me in the following days, that we were not the only ones with these problems), a solution would be the boot parameter "noapic" (or "apic=off", first one should work better). Or they fixed the bug in the Kernel (I read that it is one in the Kernel, I am not sure) with the A... Programm... Input Controller.

---

### Post by ibomb on 2008-11-06
Ok, i have the same problem after kernel update, now where exactly do i have to put this 'noapic' word , i am a beginner of linux

---

### Post by otetiani on 2008-11-06
Looks likes the newest updates fixed the hanging shutdown issue on my laptop.  Didn't have time to look at what was in the updates from yesterday.

---

### Post by theDaveTheRave on 2008-11-08
HI all

I've got exactly the same isues on my acer laptop, after using Hardy that seemed to absolutely fly along with no problems (until I attempted to install virtual box that was!) I booted into "recovery", updated to Intrepid and thought everything was cool.

All my files were intact (I love a separate partition for /home makes life so easy!).

but now my little laptop is like and old windows 98 pc, (or the original version of Vista that was installed). Windows take an age to load up, and switching to different vitual desktops (I currently use 6) is really slow!

I've run a TOP and the memory usage is really high 

There is the screenshot of TOP from the terminal at the bottom of my post.

What worries me is that the memory usage is saying 
Mem:    504704k total,   496520k used,

I never remember it being so high in Hardy?

And when I sort the TOP output (as in the attached image) It seems that there isn't that much stuff using memory? Is it possible to collect just the memory details for ALL the processes? as I am certain that there is something wrong in how intrepid is utilising this particular resource.

In fact something I have just noticed:

I'm including 2 more images: each are a screenshot of TOP sorted for memory usage (as it the first file)
rootTOP - contains a TOP showing just root processes.
uidTOP - this is the TOP for my processes.

Now each screenshot show 34 rows of processes (a total of 68) which means that there are 50 processes that are missing (by a process of mathematical deduction from the number of "Tasks" being displayed.

So a quick glance (and it is very quick!) suggest that I am using about 70% CPU and that the ROOT is using about 10%, but a quick bit of math says that I am running at 98% memory usage?

I realise that there are 50 odd proceeses left to be found... but when I change the sort order (from highest uses first to lowest usage first) the processes don't seem to be using as much memory as the above calcluation (98%) would suggest!

and I never remember seeing this much memory being used when I used hardy?

In case you are wondering why I am going on about memory, if you have a look at the CPU usage it is minimal (1.2 to 3.5 %) most of the time.

What else concerns me is how slow the system now is at refreshing web pages, and navigation from one site to the next? Normally I would say this was a "web" issue, but I can't fathom why it would therefore become slower when I have more windows open.... unless it is somehow related to the screen refresh?

I'm going to try this "noapic" thing.. if I can find instructions! and then I'll post the results here.

David

EDIT:

OK I've been playing, and I forgot to add the extra screen shots!

Well this is what I have found out... I seem to have a limit on the number of open windows? Particularly if I open a subwindow of a system (eg, a preferences window, opening a "send new email" window in evolution or the "history" in Firefox) on opening this window the TOP will suddenly show a huge jump to 98.9% CPU usage for that particular running programme.

This seems to be the same when opening or closing the extra window!

I don't know if the ACPI line is going to help or not, but I'm definately going to try it our for a couple of days!

So here goes, I'll report what I did with instructions when I can, As I'm due to lose my internet whilst I'm away off site (and away from this pc) for the next couple of weeks.... but I may be able to add something if I'm lucky!


David

---

### Post by theDaveTheRave on 2008-11-08
so this is for everyone, but in particular for ibomb... information and instructions for changing the kernel boot parameters....

so this is what I have found... I'm by no means a "guru" but I've learnt lots from this little foray into the wild world of the GRUB boot loader/

so some quick research

Linux boot prompt:

[http://www.faqs.org/docs/Linux-HOWTO/BootPrompt-HOWTO.html]("http://www.faqs.org/docs/Linux-HOWTO/BootPrompt-HOWTO.html")

from this I found

the file linux/Documentation/kernel-parameters.txt. This file contains a brief listing of all the boot time arguments that you can provide,

but I did a quick search with
> 
locate kernel


and got a HUGE return, so I greped for either txt or doc files and got these
> 
davem@Dartagnon:~/Documents/ProgramHelp$ locate kernel |grep txt
/usr/share/doc/libfuse2/kernel.txt.gz
davem@Dartagnon:~/Documents/ProgramHelp$ locate kernel |grep doc
/lib/modules/2.6.24-19-generic/kernel/drivers/acpi/dock.ko
/lib/modules/2.6.24-19-generic/kernel/drivers/mtd/devices/doc2000.ko
/lib/modules/2.6.24-19-generic/kernel/drivers/mtd/devices/doc2001.ko
/lib/modules/2.6.24-19-generic/kernel/drivers/mtd/devices/doc2001plus.ko
/lib/modules/2.6.24-19-generic/kernel/drivers/mtd/devices/docecc.ko
/lib/modules/2.6.24-19-generic/kernel/drivers/mtd/devices/docprobe.ko
/lib/modules/2.6.24-19-generic/kernel/drivers/mtd/maps/scx200_docflash.ko
/lib/modules/2.6.27-7-generic/kernel/drivers/acpi/dock.ko
/lib/modules/2.6.27-7-generic/kernel/drivers/mtd/devices/doc2000.ko
/lib/modules/2.6.27-7-generic/kernel/drivers/mtd/devices/doc2001.ko
/lib/modules/2.6.27-7-generic/kernel/drivers/mtd/devices/doc2001plus.ko
/lib/modules/2.6.27-7-generic/kernel/drivers/mtd/devices/docecc.ko
/lib/modules/2.6.27-7-generic/kernel/drivers/mtd/devices/docprobe.ko
/lib/modules/2.6.27-7-generic/kernel/drivers/mtd/maps/scx200_docflash.ko
/usr/share/doc/nvidia-kernel-common
/usr/share/doc/libfuse2/kernel.txt.gz
/usr/share/doc/nvidia-kernel-common/changelog.gz
/usr/share/doc/nvidia-kernel-common/copyright
/usr/share/doc/python-launchpad-bugs/examples/kernel-buglist.py.gz
/usr/src/linux-headers-2.6.27-7/scripts/kernel-doc
/usr/src/linux-headers-2.6.27-7-generic/scripts/kernel-doc
davem@Dartagnon:~/Documents/ProgramHelp$ 


so now I now where this stuff lives on my system..... :guitar:

but no kernel-parameters.txt file  :confused: so a little more reading and I found this


to show your boot prompt commands try the <cat /proc/cmdline>, here is mine with the resulting output

> 
davem@Dartagnon:~/Documents/ProgramHelp$ cat /proc/cmdline 
root=UUID=a9556109-43eb-4fc4-9f51-26a06933b366 ro quiet splash 
davem@Dartagnon:~/Documents/ProgramHelp$


I will need this later on to "prove" to myself that my editing of config files has worked... basically I will do it again in the edit after I've rebooted..... read on and you will understand....

Further down on this web page there are details of the noapic argument, apparently send a <cat /proc/interrupts> to a terminal will tell you interesting stuff! her is mine!
> 
davem@Dartagnon:~/Documents/ProgramHelp$ cat /proc/interrupts
           CPU0       
  0:     402802   IO-APIC-edge      timer
  1:      11746   IO-APIC-edge      i8042
  8:        101   IO-APIC-edge      rtc0
  9:        280   IO-APIC-fasteoi   acpi
 12:     333024   IO-APIC-edge      i8042
 14:     106154   IO-APIC-edge      ata_piix
 15:      23373   IO-APIC-edge      ata_piix
 16:          1   IO-APIC-fasteoi   uhci_hcd:usb4, i915@pci:0000:00:02.0
 18:     482236   IO-APIC-fasteoi   uhci_hcd:usb3, wifi0
 19:      29754   IO-APIC-fasteoi   uhci_hcd:usb2
 20:          1   IO-APIC-fasteoi   tifm_7xx1, yenta
 22:       1751   IO-APIC-fasteoi   HDA Intel
 23:       6404   IO-APIC-fasteoi   uhci_hcd:usb1, ehci_hcd:usb5
220:          1   PCI-MSI-edge      eth0
NMI:          0   Non-maskable interrupts
LOC:     192895   Local timer interrupts
RES:          0   Rescheduling interrupts
CAL:          0   function call interrupts
TLB:          0   TLB shootdowns
SPU:          0   Spurious interrupts
ERR:          0
MIS:          0
davem@Dartagnon:~/Documents/ProgramHelp$ 


as this is all related to the APIC I did a quick search on Google for APIC interupts, and now I've got a lot of stuff to read for the weekend!

So now I've got a better understanding of what the APIC thing is and does, so now the question is how do I access my boot time parameters?

Well I realise that I am using GRUB (aka the GRand Unified Bootloader). so I did a quick <locate grub> and got a lot of results.

I found a readme, and this said to look into the info file... so now <info grub> has given me that.

reading this told me that....
> 
 --config-file=FILE
              specify stage2 config_file [default=/boot/grub/menu.lst]

so ever onwards I did the folowing....

> 

more /boot/grub/menu.lst

## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-7-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=a9556109-43eb-4fc4-9f51
-26a06933b366 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet



the above is only  shortened version of the file.... Obviously the line that starts <kernel> is the important one for booting.

There are further stanzas in the file that hold information for booting into other kernels, or for the mem test or the rescue system.

At the top of the file there is the line

default = 0

This is the first line that isn't commented out with the # character. It determines the "default" option for booting into... in my instance this is the first one that occurs after the < ## ## End Default Options ## > (obviously the stanzas are "zero indexed"!)

so I've decided to edit my file

So as not to damage my installs I've made a few changes.....

First there is a timeout before the "default" system is booted... it occurs after the < default = 0 > option. I've changed mine to give myself plenty of time if I've killed my system... also it will easily tell me if the changes have occured.

So I've changed
> 
timeout		3

so as it now reads
> 
timeout		8


so now to the "fun" part, and breaking your system... or hopefully not!

I've copied the first stanza, that reads as the one pasted in above... but it now reads
> 
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=a9556109-43eb-4fc4-9f51
-26a06933b366 ro quiet splash apic=off 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet


so hopefully that should solve my booting issues..... so I'm about to reboot and see what happens...

Back soon

Dave

Edit.

so first attempt wasn't a success, I tried the <noapic> option and there was no re-boot!
so I changed to <apic=off>, for a second boot up failure! so on investigation I decided that a "space" was required after the option and before the next line... so I changed to <apic=off > and I was OK to boot... success... or so I thought!

I've tried my normal lots of programs being open on mutliple desktops, and it still goes slow once I get to about 4 or 5 windows? but I don't understand why this should be?

I'm now begining to think it is something to do with the window manager?.... investigations to continue....


Edit 2...

OK so now I'm begining to think it may be a "firefox" problem? as the issue of re-drawing multiple windows only exists in the instances of using the preferences or history windows in Firefox.... so now I have to ask "HOW wierd is that"

what have the guys at mozilla changed?

Appart from the fact that boot times are still amazingly slow... and shutdown doesn't function properly (screen remains powered up like it has only gone to a "hibernate")

---

### Post by theDaveTheRave on 2008-11-09
Hi again all

So I've been doing some more investigations, and a bit of playing around

I decided to open firefox from a terminal, a suggestion made in this thread [http://ubuntuforums.org/showthread.php?t=908707&highlight=Firfox+problems]("http://ubuntuforums.org/showthread.php?t=908707&highlight=Firfox+problems") to see if any error message came up when I used firefox...

So this is what I do...

Open firefox, open a <history> window, then click on the one of the headings (in my instance the date heading), to sort by date... Unsurprisingly the CPU usage jumps to around 20%, but only for a little while. then I try it again, but this time the sort doesn't happen and the CPU jumps to 90% or more!When I jump between virtual desktops everything seems to work OK but slowly (not a surprise if I'm using upward of 90% on just a firefox task!) But when I jump back to the desktop with Firefox on it I have a broken half formed windows everywhere! Blurring of windows and all sorts?

Last night I tried a tiling window manager, in case is was a window manager problem, but this made no difference to the situation?

After a little while I get this error mesage in a window

> 
"Library" is not responding.

You may choose to wait a short while for it to continue or force the application to quit entirely.


I'm going to have a search of the forums and see if I can find anything on this problem, else I may open a new thread

So my question is now what?

Edit:

So I've had enough trouble here, I'm re-installing Hardy! Easy solution really, appart from needing to apt get everything again!

Dave

---

