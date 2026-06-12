---
title: "USB 3.0 adapter card reads &amp; writes; but WILL not boot...."
date: 2015-01-05
forum: Hardware
---

### Post by Mike_Walsh on 2015-01-05
Evening, everybody.

I decided over Xmas that it was time to modernise my Compaq desktop, and bring her into the 21st century.....properly!

Accordingly, I've fitted a USB 3.0 adapter card, which fits in one of my spare PCIe slots, and hooks up to the PSU via a Molex extension.

The Compaq runs an Athlon 64 3200+ @2 GHz, a WD 160 GB Caviar 'Black', has 3 GB of RAM, and is using the integrated graphics (ATI Radeon Xpress200); I don't do anything that needs fancy graphics, and these work well.

I have an external Seagate 'Expansion' USB HDD, and I also use a 7-port USB hub, with its own power supply. In addition to Ubuntu on the main hard drive, I also run Lubuntu on the Seagate, and I have a couple of flash drive installs (Lubuntu 32-bit, and Puppy Linux 'Tahrpup' 6.0.)

Now; the USB 3.0 adapter card is definitely recognised by the kernel, and is certainly working, because I can read from, and write to, the Seagate and various flash drives in the normal way. The curious thing is, however, that if I want to run any of my USB installs, the system then turns round and either says 'No system installed'.....or simply won't even recognise any thing plugged into the USB 3.0 ports!

Anybody come across this 'issue' before? I've never heard of GRUB not working through a USB 3.0 port before. If I re-plug things back into the USB 2.0 ports, it all works as it did previously.

This adapter card, like most things, was developed to use with Windows.....and the documentation strongly suggests that you visit the manufacturer's website, and download a driver to make it work properly. But of course, what good is a Windows 'driver' in Linux? Or would this work like a graphics driver, since it's plugged into a PCIe slot? I confess, I'm a little bit out of my depth here... 

It's obviously using some of the PCIe bus's 'data lines', but only a few; it's designed to work from a x1 slot, but I'm using my x16 slot, as it's the only one I have on here.....and it's not used, anyway. It only has about 12 contacts each side, instead of the hundreds that a graphics card has.

COULD this be anything to do with being plugged into, and running via, the PCIe 'lanes'? I can't figure out why things read & write as normal through the USB 3.0 ports.....but refuse to boot! :-k

Any advice, ideas or suggestions would be appreciated, as always.


Regards,

Mike.

---

### Post by weatherman2 on 2015-01-05
Not a surprise.  The BIOS may not be able to boot from an external USB card.  I think there is something specific (USB boot support) built into the BIOS that wouldn't extend to an external card.  If there is an option to enable "boot other device" in your BIOS setup you might try that.

---

### Post by Mike_Walsh on 2015-01-05
Thanks for the reply.

I WASN'T aware of that, I'll confess. I may have been mucking about with these things for 30-odd years, but have rarely, if ever, had any reason to go into the BIOS and play around with the settings.

So how is it that I can boot from flashdrive, when plugged into the powered USB hub? That presents NO problems.

Regards,

Mike.

---

### Post by weatherman2 on 2015-01-05
You mean, if you plug the hub into the USB 3.0 port you can boot from USB devices plugged into that hub?

If you mean the hub is plugged into a USB 2.0 port, then booting that way would make sense.  The BIOS still has the ability to see the boot device that way.  But it can't see it when connected to a USB 3.0 card.

The USB 3.0 card itself would need its own ability to be able to boot devices built into its own firmware.  As I said earlier, the ability to boot from motherboard USB ports is built into the motherboard BIOS.

---

### Post by Mike_Walsh on 2015-01-05
Ah, okay; I'm with you , now.

So I can use the USB 3.0 ports for data transfer in the normal way.....but just not for booting? Hmm.

Stupid question, perhaps, but what gives any specific device the abilty to boot, as opposed to any other device? This is what I'm trying to 'get my head round'! What, specifically, makes a device 'bootable'?

Or is that NOT something one can give a straight-forward answer to...? (!) :lol:

In my humble opinion, you're NEVER too old to learn....and I learn something new nearly every day..!


Regards,

Mike.

---

### Post by weatherman2 on 2015-01-05
Mike, I don't know the details of how a BIOS works with the hardware to be able to boot various devices.  I understand it enough to get a feel for what kinds of devices are likely to work and not.  I'm sure you can find more details with some creative web searches.

But in general, as I understand it, the BIOS will only boot specific devices it knows enough about.  However, some PCI and PCI-E cards also have the ability - in their own firmware/BIOS - to be able to boot themselves as well.  The BIOS can hand off control of booting to hardware in an add-on card (and the BIOS may have the "boot other devices" option for that - depends on the BIOS), but then the card's firmware or BIOS has to know how to take it from there.  I've used some SATA add-on cards for example that I could not boot from because the BIOS did not have the ability to hand off; in other motherboards, it could boot.

Is there a USB 3.0 card out there that also has the ability to boot?  Maybe.  I'm totally not surprised that many of them do not.

There may be a hack you could try whereby you could have a small flash drive connected to a USB 2.0 port directly on your motherboard that only does Grub - then that could hand off to a flash drive connected on your USB 3.0 card.  But then Grub would need to have a driver for the USB 3.0 card as well, and I'm not sure how doable THAT is...

---

### Post by Mike_Walsh on 2015-01-06
Okey-doke; that's a fair explanation!

I'll mark this as solved. Cheers!

Regards,

Mike.

---

