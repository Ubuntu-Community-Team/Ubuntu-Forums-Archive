---
title: "Ubuntu 5.10 horrible issues (no sound no network) on my old IBM 600 e Thinkpad issues"
date: 2006-03-07
forum: Hardware &amp; Laptops
---

### Post by hasek on 2006-03-07
Dear Friends,

i got an old ibm thinkpad 600e and i wanted to install 5.10 ubuntu version and big surprise : i got 2 major issues and one minor issue :


-The sound card from the thinkpad is not recognised (it is a Cirrus logic 
CS4610/11 crystal clear audio accelarator) 

-The pcmcia Dlink DFE-690 TXD ethernet card is recognised with realtek module, but it is usless, the network interface take 3 minutes to bring up , and even it manages to get assigned a dhcp address after 15 minutes, the ping response to my home router is enormous 99 % loss 1 % success with ping timings close to 15 seconds !! the network interface was working well with windows XP :-(

-The graphic card seems not to be recognised (Neomagic corp NM2200 magic graph 256 av (rev20)), my graphical display is very slow as it were in framebuffer mode 

i tried to find out solutions to bring up ethernet up
with google, but the solutions proposed on internet is to desactivate acpi in grub, but i do not know how to do that, 

the other things is some linux experts do not advice to disable acpi as on most laptops, it may desactivate fans on laptop that might very dangerous..

Is there some of you that had the same issues on these ibm laptops ? how to get rid of them easily ?

thanks a lot for your help, cause like this the laptop is realy useless :-(

---

### Post by grumpymole on 2006-03-09
hasek,

See the info below about the sound:

===>

Known problem with the TP600E. The soundcard is incorrectly identified as CS462x.

There are plenty of web pages out there describing solutions to this. But here is the Reader's Digest version:

1. Blacklist the incorrect sound card in /etc/hotplug/blacklist. Add lines for

snd-cs46xx
cs46xx

as written above - with the xx's

2. Add the following lines into /etc/modprobe.d/alsa-base

alias char-major-116 snd
alias char-major-14 soundcore
alias snd-card-0 snd-cs4236
options snd-cs4236 isapnp=0 cport=0x538 port=0x530 sb_port=0x220 fm_port=0x388 irq=5 dma1=1 dma2=0
alias sound-slot-0 snd-card-0
alias sound-slot-1 snd-card-1

alias sound-service-0-0 snd-mixer-oss
alias sound-service-0-1 snd-seq-oss
alias sound-service-0-3 snd-pcm-oss
alias sound-service-0-8 snd-seq-oss
alias sound-service-0-12 snd-pcm-oss

alias /dev/mixer snd-mixer-oss
alias /dev/dsp snd-pcm-oss
alias /dev/midi snd-seq-oss

options snd cards_limit=1

NOTE: When copying and pasting the above, make sure that the line starting with 'options...' is one line ending with '...dma2=0'.

3. Add the line

snd-cs4236

to the file /etc/modules

Reboot.

Also important: During power up, if you press F2 (I think), you get into change the config. In this you need to make sure that the Fastboot option is *disabled*.

If you are still having no success: try adding 'acpi=off pnpbois=off' at the end of the kernel boot params. Press 'esc' during Grub countdown and select 'e' to edit the boot command and add these to the end. I need these to allow my Xircom PCMCIA ether card to work.

Regards

Warren

===>

To deactivate acpi, reboot and the first thing you will see is the Grub countdown (only about 3 seconds, I think).  Also, you will see a message to press 'Esc'.  Press 'Esc' and you will go to an application to edit the GRUB boot params.  

Select the kernel that boots, usually the first line in the list.  Press 'e' to edit.

Then scroll down (usually one line) to the line beginning with "kernel /boot/..." and press 'e' again.  You go straight to the right place to edit and add acpi=off pnpbios=off to the end of the line.  Press 'ESC' once you are done.

Then press 'b' to boot and the machine will boot with these parameters, but ONLY THIS TIME.  Next time you boot, it goes back to the original settings.  To make the changes permanent, you need to edit the file /boot/grub/menu.lst.

Regards

Warren

---

### Post by hasek on 2006-03-13
thanks a lot Warren it worked

---

