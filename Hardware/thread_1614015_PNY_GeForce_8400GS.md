---
title: "PNY GeForce 8400GS"
date: 2010-11-05
forum: Hardware
---

### Post by taelmx on 2010-11-05
Ok, I've found another post about this, but it was way over my head, and I may even have a totally different set of problems. I recently tried getting my onBoard graphics to work at a better resolution, but ended up opting for swapping a graphics card of another computer. It's a PNY GeForce 8400GS. So the first thing I do is put it in and hook it up. Nothing happens when I boot, so I switch back over to onBoard, and then get to my desktop. I then go to "additional drivers" and install the 2nd one on the list that says (recommended). I'm then told I should restart, so I do...

Now it's booting up to a CLI, and I'm not sure what to do. Also, if I switch the BIOS setting to using the PCI rather than the onBaord graphics, it doesn't seem to want to boot up at all, and the fan makes a sort of "chugging" sound...like it's trying to load something really fast, then slows down really quick, and repeats this seemingly indefinitely...Any advice?

Oh, also, I'm trying to get this to work on an HP Pavillion a810e

---

### Post by coffeecat on 2010-11-05
> **taelmx said:**
> It's a PNY GeForce 8400GS.

What graphics chipset is the onboard video? If it's not nvidia, you will have installed the wrong driver for the 8400GS.

> **taelmx said:**
> so I switch back over to onBoard,

Do you mean in the BIOS, or did you just swap the VGA cable over?

> **taelmx said:**
> Also, if I switch the BIOS setting to using the PCI rather than the  onBaord graphics, it doesn't seem to want to boot up at all, and the fan  makes a sort of "chugging" sound

Do you mean PCI or PCIe? Most,  but not all, BIOSs automatically enable a PCIe/AGP video card if  detected and disable the onboard one. What was happening in your BIOS?

Which fan? The PNY card?

---

### Post by taelmx on 2010-11-05
What graphics chipset is the onboard video? If it's not nvidia, you will have installed the wrong driver for the 8400GS.

**I posted a while ago about the onBoard, and the conclusion was to not use it...it was kinda bad...and also not supported by ubuntu or the manufacturer as well as it should have been.**



Do you mean in the BIOS, or did you just swap the VGA cable over?

[B]I'm not sure what it was before, but I actually have to remove the PCI card in order for it to boot up if it's set to PCI in the BIOS. I'm more worried about getting the PCI card to work than the onBoard since I've already gone through that once. If you want to know..the onboard graphics for an HP Pavillion a810e is a VIA KM400A chip
[/B]
Do you mean PCI or PCIe? Most,  but not all, BIOSs automatically enable a PCIe/AGP video card if  detected and disable the onboard one. What was happening in your BIOS?

**In the BIOS, if I have it on PCI, it won't boot the computer, much less the display. When  I have it set to PCI in the BIOS with the card in, the fan(CPU fan I think) also does that sound that sounds like a CD drive loading something, then 1 second later it stops and retries...Would you say it's a hardware problem if it's not getting past the BIOS? I know the card is good, it works just fine on the other computer...**

---

### Post by coffeecat on 2010-11-05
I have difficulty following you.

You say your onboard graphics is a VIA. Boot into the machine with the onboard graphics enabled, go to Additional drivers and post what it says about which driver is enabled. **Exactly** what it says. We need to know what it is.

You keep saying 'PCI'. Are you sure it is PCI and not PCIe? 

Was the 8400GS card working in the computer you took it out of?

---

### Post by taelmx on 2010-11-05
Sorry if I'm a bit unclear, here we go:

OnBoard Graphics: VIA KM400A (No Linux Driver, pretty sure, but can boot up at 800x600, but that's about all)

AGP: An AGP slot is available, however, there is no card I have for it, other than one that is worse than the onBoard and doesn't work either.

PCI(not PCI-E): PNY Geforce 8400GS DDR2 512MB PCI (This is the one I'm trying to install)

So once I gave up on the driver for the OnBoard VIA KM400A, I put the Geforce in (PCI), and then booted up(BIOS still had onBoard as default of course), and went to Additional Drivers. It listed 2 available drivers, and I installed the recommended one, however, now when I boot up(with onBoard as default in the BIOS and the monitor plugged into the onBoard), all I get is a CLI, and I'm really not sure what did this...should I just reinstall Ubuntu?

---

### Post by coffeecat on 2010-11-05
> **taelmx said:**
> So once I gave up on the driver for the OnBoard VIA KM400A, I put the Geforce in (PCI), and then booted up(BIOS still had onBoard as default of course), and went to Additional Drivers. It listed 2 available drivers, and I installed the recommended one, however, now when I boot up(with onBoard as default in the BIOS and the monitor plugged into the onBoard), all I get is a CLI, and I'm really not sure what did this...should I just reinstall Ubuntu?

OK, I think I understand better what's going on. Your mistake, I think, was to install the card but leave the BIOS still set to the onboard and, I guess, the VGA cable attached to the onboard. (?) Or was the VGA cable attached to the PCI card? Whatever, it seems likely that Additional Drivers installed the nvidia driver and I'm not surprised you get a CLI with the onboard set in the BIOS and the VGA cable attached to the onboard. With the proprietary driver, you force the loading of it and a VIA graphics chipset cannot run from a nvidia driver. With the open-source driver, the boot sequence probes and detects hardware and the appropriate open-source drivers are loaded into memory when needed.

First question: have you tried setting the BIOS to the PCI card, attaching the VGA monitor cable to the PCI card and booting up? That really ought to work.

If not you need to uninstall the nvidia driver and start over - you shouldn't need to reinstall Ubuntu. If you want to try this, select recovery mode from the grub menu. You will get some scrolling text and then another menu. Select 'drop to root console' with or without networking. You will get a # prompt. Be very careful. You now have full root powers and a simple typo has the potential to break your system. Run this command:

```
apt-get purge nvidia*
```You now need to remove the xorg.conf file by running this:

```
mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```Make sure you get case correct. If you get an error you have typed it wrong. That's CAPITAL-X, eleven. Now...

```
shutdown -h now
```... and let the machine shutdown.

Now install the PCI card and attach the monitor cable to the **PCI card**. Start the computer, go into the BIOS and make sure the PCI card is enabled, **not the onboard**. Boot into Ubuntu. Do you have a usable GUI? Good. Can you get a better resolution? Good.

That should be enough. You'll only need the proprietary driver from Additional Drivers if you want 3d accleration for games or for compiz special effects. The open-source driver for your nvidia card will have been autoloaded by the system for you and is more capable than the VIA graphics driver.

---

