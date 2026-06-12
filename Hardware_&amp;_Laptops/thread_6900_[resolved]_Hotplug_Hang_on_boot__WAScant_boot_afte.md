---
title: "[resolved] Hotplug Hang on boot  WAS:cant boot after install(hotplug hang)"
date: 2004-12-02
forum: Hardware &amp; Laptops
---

### Post by paul.hendrick on 2004-12-02
Hi, i've posted this over in the laptop forum too, but this is probably the best place for this problem.

ok, i installed ubuntu,but on the first reboot i get this error when hotplug starts:
modprobe FATAL: Error installing hw_random (lib/modules/2.6.8.1-3-386/kernel/drivers/char/hw_random)
input/output error

then nothing, complete hang there, and doesnt continue after waiting.
i've looked around and saw i can add hw_random to the hotplug blacklist, but i cant even get to a login prompt.

any ideas?

---

### Post by paul.hendrick on 2004-12-02
ok, i had an idea to add hw_random to the blacklist, i used the ubuntu live cd and mounted the root partition from there, then edited the file. now, the hotplug service just hangs, with no output at all.

still stuck on this one. any ideas?

---

### Post by jdong on 2004-12-02
Hmm, very strange. Can you give us more information about your hardware?

This is definitely a hardware issue -- something that we'd want to get to the Ubuntu Developers.

---

### Post by paul.hendrick on 2004-12-02
my laptop is the second to last one on this page:
[http://www.acernotebooks.co.uk/asp/product.asp?recorprod=1&product=200&cat=79&ph=&keywords=&recor=&SearchFor=&PT_ID=](http://www.acernotebooks.co.uk/asp/product.asp?recorprod=1&product=200&cat=79&ph=&keywords=&recor=&SearchFor=&PT_ID=)

all the specs are there, so i dont know any more info about it.

---

### Post by tjwhaynes on 2004-12-02
I hate being a "me too" but here goes...

Me too!  :mrgreen: 

That aside, I have an AMD64 box running Warty plus one Debian64 lilo package (GRUB hangs on boot - see my other posts) booting the 2.6.8.1-3-amd-generic vmlinuz via LILO. 

The last thing on the screen is 
 * Starting hotplug subsystem

The keyboard is still operational, the screen blanker kicks in if  I leave the machine alone and I can use the Alt-SysRq-"r s u e i" combo to get out of the hang and terminate the init before giving the three finger salute (Ctrl-Alt-Delete) to reboot.

If I disable ACPI in the bios, I get error messages about  pciehp and shpchp: Operation not permitted. 

Changing the boot parameters doesn't seem to help ... I'll keep hacking. 

Cheers,
Toby Haynes

---

### Post by tjwhaynes on 2004-12-02
Actually, try this if you are stuck staring at that Starting hotplug message. Press

Alt-SysRq-e

(SysRq is also known as "Print Screen").

This kills off all processes at the current level. In my case it allows the runlevel 2 processing to begin and so I'm currently typing away on my laptop while everything installs off CD.

My current postmortem examination shows that the snd-au8830 has OOops'd the kernel. I shall try and disable this module once I work out where Ubuntu keeps its alsa module configuration lists. Failing that I shall remove the card. You may find that you have a module that has also failed to initialize and that has blocked the normal startup.

Hope this helps.

Cheers,

---

### Post by paul.hendrick on 2004-12-03
anyone have info on this at all? i'm at work, so haven't been playing with it today but i really want to get ubuntu running on this system, but i've got no idea where to go from here.

any clues from ubuntu devs?

thanks for reading.

---

### Post by paul.hendrick on 2004-12-03
ok, alt+sysrq+e kills the hotplus service, and ubuntu is running, kindof. no matter what driver i choose(vga, ati, radeon) i cant get X up at all!
my graphics card is an ATI mobility radeon x600. i'm tearing my hair out at this point :( a shame, cos i really enjoy ubuntu pon my desktop system...

---

### Post by tjwhaynes on 2004-12-03
I did fix my problem. Here's how I diagnosed it and how I fixed it.

The hang in hotplug was caused by a kernel module being loaded by hotplug crashing. You can find out which one by typing 

*dmesg*

and looking up from the bottom of the list until you see the ooops report or other error. In my case it was the alsa module snd-au8830 - this is needed for the Aureal Vortex 2 soundcard I dropped into my machine in the hope that it might work. 

To stop this module being loaded, I added this module name to the alsa blacklist. You can find the list of blacklisted modules by looking in

*cd /etc/hotplug/blacklist.d*
*ls*

On my Ubuntu install, there is only one file: alsa-base. Edit this file and add a line for the module that is causing the problem. e.g.

*snd-au8830*

Now reboot and cross your fingers.

The reason X won't initialise in this case is that once a module has Ooops'd, no further kernel modules can be initialized and hence, X can't start.

Hope this helps,

Toby Haynes

---

### Post by tacubuntuforums on 2004-12-04
I just wanted to ask if all this helps only boot problems after logging.
...Well this can be undertood in two ways:
1. that you can only use it past logging step
2. that only gives info about problems after logging.
Since I know less than nothing, both answers wll be welcome.
Thanx

---

### Post by paul.hendrick on 2004-12-06
i've managed to get ubuntu (kind of) installed, but i'm still geting the hotplug hang.
I've looked through the dmesg output, and there's no kernel panic/oops messages at all, so i'm still nonthewiser about what is causing it. i tried fedora core 3 on this laptop yesterday and it installed and runs fine, however i'd prefer to run ubuntu.
are there any other things i should look for next time i install warty?

getting despirate now :S
paul.

---

### Post by paul.hendrick on 2004-12-12
Hi again,
after giving up on getting ubuntu to run I installed fedora on the laptop and it works fine out of the box. but i REALLY want ubuntu on it :(
i'm still stuck at the hotplug hang though. there's no error output in the dmesg log, and the system doesn't seem to actually freeze at hotplug(there's still keyboard input going onto the screen).

is there anything else i can try?

---

### Post by jdong on 2004-12-12
Hoary has new hotplug. Does it work?

---

### Post by paul.hendrick on 2004-12-12
I'm downloading todays hoary iso, so I'll post the outcome sometime tomorrow. It might be down to the hotplug module in the kernel, so has hoary got a different kernel from warty?

---

### Post by paul.hendrick on 2004-12-13
After a week of trying to get wary installed on my laptop, i've finally done it. with a lot of arsing around though.
I had to install ubuntu, then before the reboot(while the remaining packages are being copied to the hard drive), i had to open a separate terminal and move the hotplug init script out out the init.d directory to stop it being executed when ubuntu reboots.
then reboot and let the rest of the system install. 
THEN i had to install a new kernel(2.6.9 from kernel.org), and get my network card working.
After that, I still couldnt get X to start, so I installed xorg from hoary.
thats it. phew.

the ubuntu hoary cd i made had the same problem with hanging on the hotplug process, so gave that a miss.

---

### Post by fuckit756 on 2004-12-15
Hi everyone,
I have the same laptop (acer 1802wsmi) and the same problem with hotplug. I can finish the install with Ctrl+C when hotplug crash, but after the install process my usb/firewire devices don't work. And my network card is not recognized.  I can run X with the vesa driver, but I can't upgrade my system to try to solve the problem. I tryed to install Hoary last night, and although the kernel is 2.6.9, i got the problem.  I really want to install ubuntu. Does the developpers are aware of that problem ?
Thanks.

---

### Post by paul.hendrick on 2004-12-16
I've experienced it again on another acer laptop. this time i tried something A LOT less tricky and just booted the installer with:
```

linux acpi=off nosmp

```

and the system runs fine. must be a kernel related bug in warty AND hoary. how do you report this to a dev?

---

### Post by fuckit756 on 2005-01-07
Hi, thanks for your reply. 
The installation process succeeds with the boot command : 
# linux acpi=off

During the install process, the network is correctly configured (DHCP). But once the install has finished, my network doesn't work. It can't be "active". When I try to activate it, he's deactivated after one second. Have you a clue about this issue ?

I think it's a ubuntu kernel issue, because i've tried other distros (fedora, mandrake) and i've not these problems.
I've tried to install Debian sarge last night (with the last net-install CD), and the system can't boot after the first restart. I've kernel issues with USB.

---

### Post by vrode on 2006-02-05
What's interesting, when I boot into the system via recovery mode, hitting esc on the grub menu,

I noticed the cursor sitting on the following message,

snd-hda-intel: can't be laoded
missing kernel or user driver snd-hda-intel
shpchp: already loaded
uhci-hcd: already loaded
uhci-hcd: already loaded
uhci-hcd: already loaded
uhci-hcd: already loaded
<3>hw_random: RNG not detected
hw_random: can't be loaded
missing kernel or user mode driver hw_random

When I hit alt+sysrq+e it drops me into command prompt,

dmesg shows [snd_hda_intel] being listed across, alsa_card_azx_init?

What I can add to /etc/hotplug/blacklist so that it bypasses the message?


please advice.

regards,
/virendra

---

