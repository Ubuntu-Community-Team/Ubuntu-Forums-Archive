---
title: "ACPI PROBLEM on Compaq armada 1700 and nosound"
date: 2004-10-24
forum: Hardware &amp; Laptops
---

### Post by tsubasa on 2004-10-24
HEllo i have install ubuntu 4.10 on my laptop compaq armada 1700 ( pentium 2 266Mhz and 196 Ram ).

And I stay on the logon screen for feuw hours I have no problem but if i log on and I start to use Gnome after 30 - 45 minute, it switch into console mode and write ' Critical temperature reached 96 °C shutting down", but my laptop is'nt warm at all : /, and I must reboot for reuse again ubuntu.

I have uninstall ACPI but always same behavior.

My second problem is my sound card, an es1688 ISA built in, befor i have a Suse 9.1 ( got sound directly from install) and a red hat ( got sound with sndconfig), but in ubuntu they are no alsaconf ( for try to activate sound blaster mode )and no sndconfig ????

How i can configure my soundcard and stop this fake alert on my laptop temperature ?

Thanks.

  :-k

---

### Post by Rnd227 on 2004-11-26
I have the same sound problem; the only difference is that my former Mandrake(s) did not give sound either. A tip would be appreciated...

---

### Post by WayneLeutwyler on 2005-01-04
To fix these problems.

To fix sound edit the /etc/modules file and add snd-es1688.

To fix the acpi problem edit /boot/grub/menu.lst find this line: kernel /boot/vmlinuz-2.6.8.1-3-386 root=/dev/hda1 ro quiet splash

Now add acpi=off right after splash. 

reboot your system so both change can tke effect. Once rebooted run alsamixer to set your sound levels.

I have an Armada 1700 did a clean install last night. System was up for about 35 minutes and then it rebooted. added the acpi=off and the system stayed up all night long. 

Hope this helps.

-wayne

---

### Post by Urian on 2005-02-01
[QUOTE=WayneLeutwyler]To fix these problems.

To fix sound edit the /etc/modules file and add snd-es1688.

To fix the acpi problem edit /boot/grub/menu.lst find this line: kernel /boot/vmlinuz-2.6.8.1-3-386 root=/dev/hda1 ro quiet splash

Now add acpi=off right after splash. 

reboot your system so both change can tke effect. Once rebooted run alsamixer to set your sound levels.

I have an Armada 1700 did a clean install last night. System was up for about 35 minutes and then it rebooted. added the acpi=off and the system stayed up all night long. 

Hope this helps.

-wayne[/QUOTE]
 Thanx, both settings worked out fine!

---

### Post by Ubluedog on 2007-03-15
i tried the acpi=off option , it ran longer but still shut down. so i went in from a hardware perspective and wired the fan to 5 volts which i found at a surface-mount capacitor between the dc dc converter pcb and the keyboard on the main pcb, look for the silver can cap, then look to the left an inch , there is a dark grey plastic flat mounted cap, 33uF 16 volt, its got switched 5 volts on it.
so far its lasted a few hours, but is dumping heat out the back bigtime.
will see how it goes and post back later
cheers from the bush

---

### Post by Ubluedog on 2007-03-16
The modification is reliable, I have tested it for a day in hot conditions and its worked well , no shutdown, no need for external blower. there is some fan noise as you can imagine, but its worth it to have ubuntu operational on a reliable basis.
if anyone wants pictures of where to apply the modification i can supply some
cheers

---

### Post by sudo_nym on 2007-04-18
> **WayneLeutwyler said:**
> To fix these problems.

To fix sound edit the /etc/modules file and add snd-es1688.

[...] 

Hope this helps.

-wayne

Thanks, I know this is old news, but it did help.  :-)  Yes, another Compaq Armada 1700.

Haven't had any trouble with the cooling fan [in fact, Xubuntu 6.10 is the only distro I've tried that managed to keep its cool `out of the box'], but now it's got sound too!  Until the other night, all it could manage was a direct-from-ACPI error beep.  Informative, when something goes wrong, but not very musical.

Now to fire up the FTP daemon, start the FTP client on my old Mac, and upload some audio...  [Local transfers only, by the way.  Just want to make sure you, and the RIAA, know that.]


Thanks again,

Patrick.

---

### Post by xinilux on 2007-05-09
I have run Debian on a Compaq Armada 1700 for almost two years with custom-patched 2.6.[78] kernels which take care of the no-fan/over-heating problem. This webpage explains how:

[www.linux-on-laptops.com/hosted/armada-1700-debian/](www.linux-on-laptops.com/hosted/armada-1700-debian/)

Note that the patch mentioned in the webpage can be applied to the 2.6.7 kernel using 'patch', but to apply the patch to the 2.6.8 kernel requires manually editing the kernel files and inserting the new code.

HTH

xinilux

---

