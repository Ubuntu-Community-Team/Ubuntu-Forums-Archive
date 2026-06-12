---
title: "What are these errors? pci_enable_pcie_error_reporting and NVRM: RmInitAdapter"
date: 2010-04-25
forum: Hardware
---

### Post by davidpbrown on 2010-04-25
I'm struggling with a Dell Inspiron 530 running Karmic that's showing odd but consistent graphics problems.

The BIOS splash screen looks fine but then the, usually white, small Ubuntu logo is then shown with yellow vertical lines and the text that looks malformed, during and after boot.


I'm slightly confused where the problem lies as Ubuntu is playing up now.. it doesn't want to shutdown and loops through recovery instead.

Even booting from an Ubuntu CD isn't working. That falls into a completely messed up screen I can't even read.


Errors in /var/log/messages that suggest fail are

e1000e 0000:00:19.0: pci_enable_pcie_error_reporting failed 0xfffffffb

NVRM: RmInitAdapter failed! (0x26:0xffffffff:1096)
NVRM: rm_init_adapter(0) failed
NVRM: RmInitAdapter failed! (0x26:0xffffffff:1096)
NVRM: rm_init_adapter(0) failed
NVRM: RmInitAdapter failed! (0x26:0xffffffff:1096)
NVRM: rm_init_adapter(0) failed
NVRM: RmInitAdapter failed! (0x26:0xffffffff:1096)
NVRM: rm_init_adapter(0) failed

I can upload the rest of it if that's useful.

What are those errors suggesting?


I tried updating the BIOS, via Dell, but no useful update was found. I've not reset to default values just yet as I'm thinking this might be more directly a graphics card issue.


This started when I played a graphics intensive game which stalled and flickered in a way I couldn't get out of and had to do a hard boot.

I then had problems which I thought was a [Nvida driver issue]("http://ubuntuforums.org/showpost.php?p=9074349&postcount=3") but that resolved itself after I'd tried running nvidia-xconfig as root. The bottom of that post shows the form of vertical line corrupted logo at boot. I guess the corrupted text that follows might be just a very basic font style, in the case the graphics card isn't available.

This second time, same game; I don't know if it's just a problem that's got worse..


If it is a graphics card that's failed, I think this is an on board card.. would installing a new graphics card as add in get around the broken element?

---

### Post by quixote on 2010-04-26
I was going to say that sounds like graphics driver issues, but you've been through all that already.

If it was failing hardware, you should have some kind of problems in other OSes.  If your system dual boots Windows, try getting into Windows and see how things look.

If it is hardware, then I'm not sure adding a card will solve the problem.  I think you may be looking at a motherboard replacement. :(  Anybody else out there know for sure?

---

### Post by davidpbrown on 2010-04-28
It's a single boot to Ubuntu and worked well for a long while but I think I've stressed it playing Urban Terror!

I've just found code
```
lspci -nn | grep VGA
```
reveals a graphics card.. nVidia GeForce 8300 GS

Searching on that though I'm not finding similar errors.

If I could be confident it was the card, I might just replace it. How to distinguish between motherboard and graphics card when it's a graphics/desktop problem. I'm still getting into the terminal ok but for the fragmented font type. Every time is exactly the same so it's not a variable problem I'd have expected from a hardware break.

---

