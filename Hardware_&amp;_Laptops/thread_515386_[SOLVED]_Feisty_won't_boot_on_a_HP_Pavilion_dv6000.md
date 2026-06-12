---
title: "[SOLVED] Feisty won't boot on a HP Pavilion dv6000 (AMD Turion 64x2) after fresh inst"
date: 2007-08-01
forum: Hardware &amp; Laptops
---

### Post by odiseo77 on 2007-08-01
Hi people, my friend brought me her HP Pavilion dv6000 because she wanted to install linux in it, so I decided to install Ubuntu Feisty 64 bits (it's an AMD Turion 64x2). I picked up a Ubuntu Feisty alternate cd for 64 bits and did the installation as usual (no problems during installation, it was perfectly clean). The problem is, when I try to boot ubuntu after the installation, it hangs at the beggining of the bootup process. So I reset the machine and started on recovery mode, and the first time it got hung up at the following stage "setting up console font and keymap"... I reset the laptop again and the next time it got hung up at the message that says "loading hardware drivers". So I reinstalled Feisty again and managed to start in recovery mode, so I ran 'apt-get update && apt-get upgrade' in order to install the newest kernel and it got frozen when downloading openoffice; then I reset the machine again, ran the same commands, and when it had fetched all the packages, got frozen on the "working" message that appears right when apt-get is going start installing the packages. Now it won't boot, no matter what I do (had reset it like 3 times and it always gets stuck at "loading hardware drivers").

So, what could be wrong here, and how to solve it? (I had never dealt with laptops so I'm desperately crashing my head against the wall ). The only solution I see is to put the latest Feisty's kernel for amd64 in my USB key, chroot her installation from a live-cd (if I manage to make it work) and install it; do you think this could solve the issue?


P.S.: Sorry to bother you guys with this, but I need urgent help since my friend returns to the US next saturday, so I'm running out of time :-s

EDIT: Oh, and one issue I noticed during the first installation was that the first time it named the ethernet device as eth0 and the wireless device as eth1 and the second time I installed it, it named the ethernet device as eth1 and the wireless one as eth0 :confused:

---

### Post by odiseo77 on 2007-08-02
Solved (kind of): I reinstalled Feisty (32 bits) with the 'noapic' boot option and now it's working *almost* perfect including kernel upgrades, and such (the only thing I've noticed is that when I'm booting, I get the "BIOS BUG #81" message and sometimes I get weird messages at the console).

---

### Post by ZX3Junglist on 2007-08-02
Good to hear that you've got that figured out a bit.

I also have just picked up a DV6000 series pavilion, and I'm having some trouble myself. It seems that the 2.6.16 kernel that Ubuntu 7.04 is using has trouble sorting APIC/SMP on these HP laptops.

Fiesty will only boot 32 bits with noapic, and then I get problems with linux disabling IRQs (this is a handling function of APIC) which causes my USB and wireless to not work.

The [solution?!] is to boot with noapic nosmp, which irons out the IRQ disabling, but only loads one processor..

From my initial research, it looks like 2.6.22 might hold some hope for me.. I've never built e kernel before but I may give it a go.

anyone had any luck with the settings? I find tons of users with problems, but no real solutions. :-/

[digress]
This is my first venture with Vista, and I goddamned hate it. I thought it would be a nice step up from XP, but they really broke the workflow. I can't seem to do a damn thing in it, and always feel 'lost.'
[/digress]

---

### Post by odiseo77 on 2007-08-02
Hi, yesterday when I was digging on google for this laptop and the error message when trying to boot any distro ("BIOS BUG #81"...) I read somewhere that the solution was to upgrade the BIOS' firmware, so I went to HP's website, looked for the firmware, booted vista and installed it, but the problem remained, so I had to reinstall Feisty with the 'noapic' option. After that, I noticed that every kernel upgrade has this option by default (and it kind of works... at least the system doesn't freeze upon boot and I don't get weird sound issues). As for the usb and wireless, the usb devices are working fine (I plugged in an USB key and a usb mouse and they worked like a charm); as for the wireless card, I'm not sure since I directly connected the laptop to the router (could test it when I get home).

Oh, and the weird messages I get on the terminal are related to IRQ, but other than that, the system seems to be running fine.

Greetings.

---

### Post by manishk on 2007-08-09
Hi, my friend bought a HP dv6000 recently...the dv6502 variant ([http://www.mxinfosys.com/hp/hplaptop.htm](http://www.mxinfosys.com/hp/hplaptop.htm))

He wants to install Feisty on it, but the Live CD runs only in the 'Safe Graphics Mode', in which he gets a 600x800 screen (which is pretty irritating on a widescreen). The restricted drivers manager says that there are no restricted drivers needed for it.

Will it work if I install in this safe graphics mode??

Any solutions??

---

### Post by odiseo77 on 2007-08-09
Hi, I didn't use the live-cd but the alternate cd which install everything in text mode (don't worry, it's easy :) ). When you see the first screen, press F6, then then, edit the line of the boot parameters and add 'noapic' (without the quotes) at the end of it; that's the way I workaround this issue on my friend's machine.

Greetings.

---

### Post by splintercellguy on 2007-08-09
> **manishk said:**
> Hi, my friend bought a HP dv6000 recently...the dv6502 variant ([http://www.mxinfosys.com/hp/hplaptop.htm](http://www.mxinfosys.com/hp/hplaptop.htm))

He wants to install Feisty on it, but the Live CD runs only in the 'Safe Graphics Mode', in which he gets a 600x800 screen (which is pretty irritating on a widescreen). The restricted drivers manager says that there are no restricted drivers needed for it.

Will it work if I install in this safe graphics mode??

Any solutions??

Please create a new thread to avoid confusion. You can definitely install, but after installation, you will have to go into Recovery Mode and run:

sudo dpkg-reconfigure -phigh xserver-xorg

then reboot.

---

### Post by manishk on 2007-08-16
Thanks for your help, and I'm really sorry for posting in the wrong thread.

---

