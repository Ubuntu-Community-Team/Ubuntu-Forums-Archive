---
title: "abit as8 motherboard and ieee1394"
date: 2005-09-25
forum: Hardware &amp; Laptops
---

### Post by lompolo on 2005-09-25
Firewire integrated to motereboard isn't working with Mini DV camcorder. If I have camcorder turned on dmesg gives configrom errors. I have tested with hoary installed and breezy live and knoppix. My friend got it working with his computer with breezy live with different motherboard. 

I think problem is motherboard [abit as8]. Any ideas?? Can't go to abit (USA) forums.

---

### Post by mlomker on 2005-09-25
Do you have the latest system BIOS?  Have you searched Google using the dmesg error?  It'd help if you posted that.

---

### Post by lompolo on 2005-09-27
dmesg gives :
ieee1394: Error parsing configrom for node 0-00:1023
ieee1394: Error parsing configrom for node 0-01:1023
ieee1394: The root node is not cycle master capable; selecting a new root node and resetting...
and so on.

I havn't found nothing intresting with google.
I think bios updating might help. Abit bios updates are .exe files. I have no windows.

---

### Post by mlomker on 2005-09-27
> I think bios updating might help. Abit bios updates are .exe files. I have no windows.

Well, I can't help you with that one but the BIOS update is worth a try.  Most BIOS updates come as boot floppy images.  You run the file and then it creates a boot disk for you.

---

### Post by lompolo on 2005-09-27
I downloaded bios update file. Then i ran it with wine. It created folder with 5 files. awd flash.exe and AS8_18.bin are important files I guess. Next thing is how I could create bios update floppy using these files.

Thanks for helping

---

### Post by mlomker on 2005-09-27
Yeah, they probably want you to create a Win9x boot floppy and copy those files to it.  You then run the executable after booting up.

---

### Post by lompolo on 2005-09-28
Bios update didn't help.

---

### Post by mlomker on 2005-09-28
There are alot of posts with that dmesg error on Google.  [Take a look]("http://www.google.com/search?q=%22ieee1394%3A+Error+parsing+configrom+for+node") through them.  I don't use firewire, so I don't have any specific advice.

---

### Post by lompolo on 2005-11-15
Because integrated soundcard (microphone plug) wasn't working in as8, changed motherboard (free with shops guarantee) and got firewire card (pci). Now firewire works.

Thanks.

---

