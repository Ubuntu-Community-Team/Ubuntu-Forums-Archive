---
title: "HP photosmart C6180 all in one issue"
date: 2011-09-20
forum: Hardware
---

### Post by MarkIam on 2011-09-20
I recently installed Ubuntu 11.04 for the first time. (First time Linux user) I have an HP photosmart C6180 that is network attached. I have the driver installed for the printer and that works fine. The scanner seems to be a problem though. I can't see the scanner over the network, as far as I can tell. 
 
Does any one have any information about network attached scanners and how they are located? 
 
Also, does anyone know if the driver for this device is also supposed to support the scanner?

---

### Post by Azdour on 2011-09-20
Hi,

How did you install the HP printer?  Did you open a terminal and run hp-setup?

According to the "HP Linux and Printing" website your scanner should work, see:

[http://hplipopensource.com/hplip-web/models/photosmart/photosmart_c6100_series.html](http://hplipopensource.com/hplip-web/models/photosmart/photosmart_c6100_series.html)

---

### Post by MarkIam on 2011-09-20
Thanks, I did not read deep enough into that site.  But then there is this solution listed...  The question is where do I put this information?  Is this command line entry or some other place?  
 
Solution: 
For network scanning, the "hp:/net/..." URI must be configured in the CUPS queue for auto-discovery by OpenOffice and xsane. You can manually specify the URI with xsane using the following format:
xsane <"hpaio" device uri>For example:
xsane hpaio:/net/PSC_750?ip=12.25.63.142*(Where the CUPS installed device URI is: hp:/net/PSC_750?ip=12.25.63.142, and the hp: was replaced with hpaio:)*

---

### Post by Azdour on 2011-09-21
Hi,

I'm guessing you open a terminal and type it there.

---

### Post by MarkIam on 2011-09-21
I am guessing you are not interested in really trying to help.  As noted previously, I am new to the linux environment.  That being said, if this is the wrong forum to ask novice questions at then where do I go?  Or should I just go back to Windows and take my chances?  If the Linux world wants to make inroads to the windows users then there must be a lot of grace given to the novice.  So sorry if my questions offend your mighty level of ability.  Is there anyone else on this forum that can answer questions or are you the only one out there?

---

### Post by Locke_99GS on 2011-09-21
I came in this thread because I use network attached (wireless) HP printers for printing and scanning on Linux. Then I read the thread:

> **MarkIam said:**
> I am guessing you are not interested in really trying to help.

Really?

The only one helping you, and you're going to be like that? Good luck getting assistance with that strategy. Maybe others will be less spiteful than I.

Sorry to trouble you, sir.

---

### Post by Porcini M. on 2011-09-22
I too could not run an HP photosmart scanner over the network. What I ended up doing is invoking xsane over ssh -X. So I'd have xsane up on my local screen, but actually running locally on the server connected to the scanner.

---

### Post by Azdour on 2011-09-22
Do you have xsane installed? On my computer I can find it under Applications | Graphics. When you run xsane it searches the network for scanners.

If it does not find it then I would suggest you go to Applications | Accessories | Terminal and type in:

```
xsane hpaio:/net/PSC_750?ip=12.25.63.142
```

Other than that I do not know what else to try.

I know how frustrating it is when you are trying to get things to work with computers in general. Yes, I did miss the fact you where a Linux beginner, but I am hoping that maybe the steps above may be of help. We are all volunteers here.

---

### Post by MarkIam on 2011-09-22
xsane hpaio:/net/PSC_750?ip=12.25.63.142  
 
In this string is the IP supposed to be the static IP of the printer?  
 
Does this need to be run only one time or is this something that needs to be done each time I want to scan or after each reboot?   
 
Yes, xsane is installed.  
 
Is there a decent book that covers how to use linux from the point of view of a windows admin.  Or should I just go look for a linux for dummies book?  
 
Or, more specifically, Ubuntu for dummies?  from what I have been reading the different flavors of linux out there are different enough to be a problem when talking about linux in general terms.  Is this accurate?  
 
Thanks for the help!

---

### Post by MarkIam on 2011-09-22
> **Locke_99GS said:**
> I came in this thread because I use network attached (wireless) HP printers for printing and scanning on Linux. Then I read the thread:
 
 
 
Really?
 
The only one helping you, and you're going to be like that? Good luck getting assistance with that strategy. Maybe others will be less spiteful than I.
 
Sorry to trouble you, sir.
 
Sorry also, but the comment previously made is a bit coarse.  "I'm guessing you open a terminal and type it there."  If I knew how to open a terminal then I would not have asked.  I am learning that though the OS is superior to windows, the plug and play is not.  This is and always will be a big roadblock to wide acceptance of linux unless clear and exact instructions are given with each command line entry and how it is speciffically formated for each instance.  thanks for your input.

---

### Post by Azdour on 2011-09-23
Hi,

Usually when you run xsane it should find the printer on the network, but I am guessing it is not. 

Yes, the last of this string "hpaio:/net/PSC_750?ip=12.25.63.142" is the IP of your printer. Run from the terminal I think it is telling xsane how and where to look for your printer.

I can see how my original reply may have seemed 'coarse' but that was never my intention.

I'm hoping that other people on this forum may be able to suggest some resources and books that may help you. You may even want to start a separate thread to ask.

---

### Post by dsdurkes on 2011-09-25
Linux and Windows/Mac differ in at least one important way. Windows and Macs have a refined, though limited, user interface enabling most people access to the installed functions and capabilities. Linux/Unix does rely on more knowledge and experience. Being able to navigate with the terminal is critical in order to get "inside" the system and configure things such as the C6180.

All that said, I have installed my C6180 as a wireless printer, which is great, but cannot for the life of me figure out how to install the wireless scanning capability. So, I punted and have the printer connected via USB but the great thing is that it remains a wireless printer for others to access. The Windows and Mac users can wirelessly scan as well. It's a kludge, I realize, but it works.

CUPS configuration is baffling me also so I'll be watching this thread for some clues on how to go about doing this.

---

