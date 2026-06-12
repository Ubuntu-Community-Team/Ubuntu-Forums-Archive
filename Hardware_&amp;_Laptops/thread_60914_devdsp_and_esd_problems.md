---
title: "/dev/dsp and esd problems"
date: 2005-08-29
forum: Hardware &amp; Laptops
---

### Post by artooro on 2005-08-29
I just installed Ubuntu 5.0.4 on a Dell Latitude CPi laptop.

And as you know the sound does not work.

If I open "Recording Level Monitor":

Error (vumeter)
"Cannot connect to sound daemon.
Please run 'esd' at a command prompt."

So when I do that from root:
# esd
/dev/dsp: No such file or directory

And Sound Recorder produces:
"Device "/dev/dsp" does not exist."


I do have a sound card and it works in Windows XP but I have no idea of what kind it is. The main purpose of this laptop is to record audio   ](*,) 

I cannot connect to the internet in order to upgrade/install packages. (No netword card)
It would be great if I could get this working. If not I plan on testing Fedora Core before moving back to Windows as a last resort.

---

### Post by artooro on 2005-08-30
OK, 

I have some more information now.

It's a Dell Latitude CPi D266XT
and the sound card is a Crystal 4237B.

Output from lspci is:
0000:00:03:0 CardBus bridge: Texas Instruments PCI1131 (rev 01)
0000:00:03:1 CardBus bridge: Texas Instruments PCI1131 (rev 01)
0000:00:07:0 Bridge: Intel Corp. 82371AB/EB/MB P11X4 ISA (rev 01)
0000:00:07:1 IDE interface: Intel Corp. 82371AB/EB/MB P11X4 IDE (rev 01)
0000:00:07:2 USB Controller: Intel Corp. 82371AB/EB/MB P11X4 USB (rev 01)
0000:00:07:3 Bridge: Intel Corp. 82371AB/EB/MB P11X4 ACPI (rev 01)

But I'm not sure which one is for audio. Maybe for some reason it's not on there.

Any help please???

---

### Post by artooro on 2005-09-01
[QUOTE=artooro]OK, 

I have some more information now.

It's a Dell Latitude CPi D266XT
and the sound card is a Crystal 4237B.

Output from lspci is:
0000:00:03:0 CardBus bridge: Texas Instruments PCI1131 (rev 01)
0000:00:03:1 CardBus bridge: Texas Instruments PCI1131 (rev 01)
0000:00:07:0 Bridge: Intel Corp. 82371AB/EB/MB P11X4 ISA (rev 01)
0000:00:07:1 IDE interface: Intel Corp. 82371AB/EB/MB P11X4 IDE (rev 01)
0000:00:07:2 USB Controller: Intel Corp. 82371AB/EB/MB P11X4 USB (rev 01)
0000:00:07:3 Bridge: Intel Corp. 82371AB/EB/MB P11X4 ACPI (rev 01)

But I'm not sure which one is for audio. Maybe for some reason it's not on there.

Any help please???[/QUOTE]
 Would alsaconf help? If so how can I get it?

---

