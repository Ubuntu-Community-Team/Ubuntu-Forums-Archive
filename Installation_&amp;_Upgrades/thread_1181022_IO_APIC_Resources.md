---
title: "IO APIC Resources?"
date: 2009-06-07
forum: Installation &amp; Upgrades
---

### Post by ohyou on 2009-06-07
Hey all,

So I am _extremely_ new at this (I basically have zero Linux experience)... and after hearing about the option to boot Ubuntu from a live cd, I figured I would give it a shot. After all, what have I got to lose? So I followed the instructions on the Ubuntu website and burned my very own 9.04 Jaunty Desktop CD. 

Fast forward to me booting from the CD and selecting the first option - Try without any changes to your system. From there it goes through a few basic things and then drops me to a very intimidating prompt (ubuntu@ubuntu$ or something like that...) ctrl+alt+f7 gives me nothing but a blank screen (I can still type in it) I noticed at the top of the screen it says IO APIC resources could not be allocated. Is this something easily fixable? Ive tried everything else I saw on the forums.. noapic, nolapic, acpi=off, safe graphics mode, sudo dpkg-reconfigure xserver-xorg, all that stuff, and in every combination you can think of...

This is on an averatec 3250H1 laptop. I have already checked the integrity of the disc - no errors.

So yeah. If anyone has any experience with this, or could offer any help or advice, that would be awesome. I have been trying to figure this out for a while, and would love to get this going on my system and perhaps eventually drop windows.

Thanks in advance!

---

### Post by oxf on 2009-06-07
> **ohyou said:**
> Hey all,

So I am _extremely_ new at this (I basically have zero Linux experience)... and after hearing about the option to boot Ubuntu from a live cd, I figured I would give it a shot. After all, what have I got to lose? So I followed the instructions on the Ubuntu website and burned my very own 9.04 Jaunty Desktop CD. 

Fast forward to me booting from the CD and selecting the first option - Try without any changes to your system. From there it goes through a few basic things and then drops me to a very intimidating prompt (ubuntu@ubuntu$ or something like that...) ctrl+alt+f7 gives me nothing but a blank screen (I can still type in it) I noticed at the top of the screen it says IO APIC resources could not be allocated. Is this something easily fixable? Ive tried everything else I saw on the forums.. noapic, nolapic, acpi=off, safe graphics mode, sudo dpkg-reconfigure xserver-xorg, all that stuff, and in every combination you can think of...

This is on an averatec 3250H1 laptop. I have already checked the integrity of the disc - no errors.

So yeah. If anyone has any experience with this, or could offer any help or advice, that would be awesome. I have been trying to figure this out for a while, and would love to get this going on my system and perhaps eventually drop windows.

Thanks in advance!

I cant answer your question as such but you might want to take a look at my current thread which may involve an IO-APIC issue
[http://ubuntuforums.org/showthread.php?t=1181067](http://ubuntuforums.org/showthread.php?t=1181067)
In particular the provided link in the second reply which does explain the MS BIOS bug issue
[http://www.linuxquestions.org/questions/linux-hardware-18/mp-bios-bug-8254-timer-not-connected-use-noapic-option-to-boot-591891/](http://www.linuxquestions.org/questions/linux-hardware-18/mp-bios-bug-8254-timer-not-connected-use-noapic-option-to-boot-591891/)
Good luck

---

### Post by ohyou on 2009-06-08
Hey, thanks for the link! I took a look at that and it seems as though we have different issues. I can't even boot from the live cd; it just drops me to the terminal. Also, I forgot to mention that I did try the wubi install after the live cd gave me issues... still nothing.  I am probably going to give the alternate install cd a chance, and if that doesnt work, I may try an older version and see what happens.

---

### Post by 00b00nt00 on 2009-06-09
Run the Live CD until you get to the initial welcome screen. Hit 'F6' and you should see a list of four options. One will be 'noapic'. Select this option and try running from the CD again.

---

### Post by ohyou on 2009-06-09
Tried that... unfortunately it gave me the same results. :(

---

### Post by 00b00nt00 on 2009-06-10
I did a web search on your laptop, and it seems to have a VIA Unichrome chipset. For what it's worth, I can't get Linux up and running on my VIA based laptop either. If you would like to run Ubuntu, avoid VIA chipsets.

Personally, I feel that Canonical should publish a list of hardware users have reported as causing serious problems. That would stop us from wasting our time trying to coax Ubuntu to work.

Then, Ubuntu is free, and only costs a little time, not money.

---

### Post by fredj on 2009-06-11
Ubuntu seems to have problems with all sorts of hardware, even
recent mainstream hardware. I have an Intel IP35 based system
with a Nvidia 7600GT video card. None of the live CDs will run
on this system i.e 8.04, 8.10 or 9.04. I can install 9.04 from
the alternate CD but this freezes after the login screen.

On the other hand Suse linux installs without any major problems
and the Fedora live CD runs without any problems. So whatever
Ubuntu are doing they are not doing it well. I suppose switching
to another distribution may be the only answer.

---

### Post by yldouright on 2009-06-11
00b00nt00
I get similar error codes on an Epox 8RDA+ with Jaunty;

[  2.570936 IO APIC resources could not be allocated.
create_floppy_devices[588]:specified group 'floppy' unknown

so it doesn't appear to be exclusive to laptops. I resolved the freezing error by raising the CPU core voltage 0.5 volts so in my case it appeared to have been hardware related. My 9.04 server install went smoothly after that hardware tweak. For others experiencing freezing during the install process:

1. check the media
2. check your power supply
3. check for devices using IRQ 9 and move them

I am having a problem with sudo apt-get install ubuntu-desktop. It tells me it can't resolve the US server. I see that my /etc/network/interface is configured properly but the hardware is not recognized. I am using the nForce2 integrated chipset LAN. Any hints? What should the LAN bios entry be on the MAC address? Does the server default to 192.168.1.1 for the network DNS. I'm using a router to serve domain names, is this a problem? Again, this was a hardware problem. I needed to enable the MAC address in the bios. Everything works now.

---

