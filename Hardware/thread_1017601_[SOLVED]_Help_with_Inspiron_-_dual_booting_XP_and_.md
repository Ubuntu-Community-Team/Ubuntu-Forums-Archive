---
title: "[SOLVED] Help with Inspiron - dual booting XP and Intrepid"
date: 2008-12-21
forum: Hardware
---

### Post by BigSilly on 2008-12-21
Is this even possible?

The missus bought an Ubuntu Gutsy Dell 1525 a while ago and has been really happy with it. Sadly, the demands of her (obviously technologically challenged) Open University course work mean that she has to have an XP install to access the course tools. She's miffed, and so am I, since it means leaving the comfort of an easy Linux install and back to the drudgery of a driver hunt for XP.

She only needs a tiny XP install, and I have spotted a 5Gb FAT32 partition that I was going to use for XP, leaving the rest for a fresh Intrepid install. Great! However...

From what I gather, I have to disable the Flash Cache Module in the BIOS, and also the AHCI setting has to be changed to ATI in order to successfully install XP. Once installed you cannot change these back (apparently). Thing is, how will that impact on my fresh Intrepid install? Will it still be as functional with these items disabled for XP? 

Any help much appreciated here. I'm fed up of Windows already, and I haven't even installed the thing yet! Thanks all.

---

### Post by Idefix82 on 2008-12-21
Seeing that you are so reluctant to install windows (which I can totally understand), can you not try to run the tools under Wine or in a virtual machine?

---

### Post by BigSilly on 2008-12-21
That's not a bad idea. I can't believe I didn't think of it! Will it still run OK after a kernel upgrade though? It's imperative that this thing is running without hitch.

Otherwise, are you saying I'm going to have issues with Ubuntu after disabling those BIOS objects?

---

### Post by BigSilly on 2008-12-22
In case this is useful for someone, I disabled those objects in the Dell's BIOS and successfully installed both Windows XP and Ubuntu Intrepid without a hitch. Particularly impressed with Intrepid - it installed in minutes and was fully compatible - wireless and all - without ANY extra intervention from me. All I had to do was download the programs we need from the repos and it was away.

My hat is doffed yet again to the quality of Ubuntu!

---

