---
title: "How to get Vodafone Mobile Broadband TopUp And Go UK  dongle working?"
date: 2013-02-16
forum: Hardware
---

### Post by TheWizardTT on 2013-02-16
How to get Vodafone Mobile Broadband TopUp And Go (UK)  dongle working?

Dongle is  Vodafone K3570-Z

**Please see attached screenshot.**

Whatever connection info I enter it won't connect to them innernets.

I may have to uninstall Ubuntu (gasp!) if I can't get this sucker working. :)

---

### Post by foresthill on 2013-02-16
I think you're configuring it wrong. 

A few seconds after you plug it in, you should get an entry under the network icon on the top right taskbar that says "New CDMA Connection". When you click on that, you'll get a "Wizard" dialog box that asks you your country from a drop down menu, and then your provider from another drop down menu.

Is the device being detected as "New CDMA Device" at all? If not, you're in for real adventure, but I'm not saying it won't be possible to get the device working. With Linux, as we all know, pretty much anything is possible, given enough effort.

---

### Post by TheWizardTT on 2013-02-16
I think Ubuntu recognises it, alright.

When I click on it in the 'Connections' tab, it says "You are connected to the GSM Network ..." And then "Modem network, you are now offline" , presumably from Vodafone.

---

### Post by foresthill on 2013-02-16
I have to ask, Mr. Wizard, did you use the "Wizard" to configure the device? :D

Because that's all you should need to do, assuming your provider is listed in the drop down menu. It will set the correct number to dial, password, PPP settings and everything else for you "automagically". 

Any other adjustments you make will most likely only muck things up, unless you really know what you're doing, which I'm not assuming, but may be the case.

Or maybe I'm missing something here. It should be very easy to set up the device, but it looks to me as though you may be over-thinking it.

---

### Post by TheWizardTT on 2013-02-16
Yep, I used the wizard.

---

### Post by foresthill on 2013-02-16
Not sure I can help you beyond that then. Because all I do with my Virgin Mobile CDMA modem is plug it in, run the wizard, and after that, the modem automatically dials and connects and I'm online within 5-10 seconds.

The only thing I might suggest is to make sure you are using the latest version of Ubuntu, because each new version of the Linux kernel has fixes so that various hardware devices will work that didn't previously. For example, I have a Ralink wifi device on one of my notebooks that will only work with version 12.04 or later.

The only thing I can suggest would be to spend some time on Google and see if anyone else has figured out how to get your device to work, and also to try a few different Linux distros, and see if one of them will work. 

Sorry I can't be of more help than that. :(

BTW, why are you using a dongle with this device? I would think the USB modem would work by itself.

---

### Post by TheWizardTT on 2013-02-17
Sorry, yes, that's what it is. An external modem thingy.  I agree, it's odd. I've tried various connection username/password etc. variations.

---

### Post by foresthill on 2013-02-17
Any chance that the modem itself is broken? Does it work in Windows?

These things used to be a huge PITA to get working in versions 9.10 and earlier, but since then they are normally a breeze to get up and running. 

Are you saying the thing won't work if you plug it directly into a USB port? If so, I don't see why connecting it to a dongle would change the situation.

---

### Post by TheWizardTT on 2013-02-19
No, it works in Windows.  Forget I mentioned 'dongle'.   I insert it into my laptop. Ubuntu finds it Ok, but it won't sustain a connection to Vodafone. I might contact them.

---

