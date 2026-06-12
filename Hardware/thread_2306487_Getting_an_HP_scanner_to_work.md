---
title: "Getting an HP scanner to work"
date: 2015-12-15
forum: Hardware
---

### Post by sideburns on 2015-12-15
My sister is currently running Xubuntu 14.10 and has an HP4500 model G510g printer.  It prints just fine, but can't scan.  We've installed hplip and tried xsane.  It acts like it's scanning but never shows a preview or asks where to save the image.  I've searched the archives, but the most recent post mentioning this model is from mid-2013.  I'm posting the question instead of her because I'm the one who understands how to do whatever's needed.  Any suggestions or possible fixes will be greatly appreciated.

---

### Post by Bucky Ball on 2015-12-16
Suggest you upgrade to a supported release. That could be your issue, particularly if the printer/scanner is a newer model. 14.10 is no longer supported (as of mid-2015). 

Did you download the correct driver for it and choose it when you added the printer in 'Printers'?

Be aware that any advice you get here may not be applicable to an obsolete release. Hopefully something with help. 

(Final note: That machine no longer gets updates or, more importantly, security updates. If online it will become vulnerable.)

---

### Post by sideburns on 2015-12-16
The printer has worked Just Fine as a printer ever since it was installed, but she's only recently needed to scan and didn't realize that it wasn't set up.  My guess is that we picked the right drivers.  As I don't use Ubuntu, I didn't know that her installation was out-of-date, and we'll be upgrading it when time allows.  However, if we can get the scanner running now, that's one less thing to worry about later.

---

### Post by Bucky Ball on 2015-12-16
Check which version of HPLip you have installed. The version required for this printer, according to[ this webpage]("http://hplipopensource.com/hplip-web/models/officejet/officejet_4500_g510g-m.html"), is: 

> Minimum HPLIP version	3.10.2

Also, check the driver you have installed by going to 'Printers> Properties' of the printer.

---

### Post by Geoffrey_Arndt on 2015-12-16
This printer (including scan) should be fully supported in Linux . . . I would second Bucky's recommendation to upgrade, and then reinstall driver is the normal "add printer" dialogue.   (this often will utilize the pre-installed modules ).     The most reliable way to scan that I've found in Ubuntu and other Linux distros is by using the "Simple Scan" program (after doing the drivers update).

Also, have you checked out HP's website for Cloud Print support?   Might be worth a looky-see.

---

### Post by sideburns on 2015-12-16
You did read, didn't you, that she just installed the most recent version of hplip, and that it prints Just Fine?  Assuming that she doesn't have the time right now for a proper upgrade, what other pertinent suggestions do you have?

---

### Post by Geoffrey_Arndt on 2015-12-16
How about losing the "attitude" . . . You wrote "My guess is that we picked the right drivers".

So, what was the result of using "Simple Scan" . . ?

---

### Post by sideburns on 2015-12-16
I'll drop the attitude if and when you start reading my posts before responding and stop repeating previous suggestions.  As far as Simple Scan goes, I'm not at her computer, and don't know why she hasn't checked this thread or responded on her own.  As my .sig says, I don't use Ubuntu.  I have, however, been a Fedora user since FC 6, and started with Linux back in about '98.

---

### Post by Softa on 2015-12-16
Hi, Sister here,
I installed  HPLIP version 3.10.2.  As to the printer, its been installed and working for a couple of years with no problem.
When I first got the printer, not only did it print and copy, but I was also able to scan.  After several upgrades, it no longer
scans.  Yes, I know that I have an outdated version, and will be upgrading soon, but I need the scanner to work ASAP.

After installing the drivers, I tried to scan something.  It went through all the motions, but there is nothing to be seen.

Your help would be appreciated, and remember, I am not tech savvy, so keep it simple, please.

---

### Post by QIII on 2015-12-16
If the need to scan has only come about recently, we don't know how long this has been the case.  If several release updates have occured, it is entirely possible that some dependencies may not be fulfilled or any number of similar conditions could be at play.

In any case I will repeat what has been said above:  there is a great likelyhood that any advice given will not work on an unsupported release.  However, you are free to wait on advice from one of the *volunteers* on the Forums

Now, if anyone has an issue with that and would like to cop an attitude, I urge caution.

---

### Post by Geoffrey_Arndt on 2015-12-16
> **Softa said:**
> Hi, Sister here,
I installed  HPLIP version 3.10.2.  As to the printer, its been installed and working for a couple of years with no problem.
When I first got the printer, not only did it print and copy, but I was also able to scan.  After several upgrades, it no longer
scans.  Yes, I know that I have an outdated version, and will be upgrading soon, but I need the scanner to work ASAP.

After installing the drivers, I tried to scan something.  It went through all the motions, but there is nothing to be seen.

Your help would be appreciated, and remember, I am not tech savvy, so keep it simple, please.

The 3.10 series drivers are 2010 vintage.   Almost as ancient as my Unix background (PDP 1011 user since 1978, Unix Dev. since 1980).

So:

1).   Try uninstalling (purging) those drivers via the Synaptic front-end package manager (complete uninstall) and
2).   Install the current version 3.15.11. 
3).    Check and see if you do have the Simple Scan program already installed - if not, it's worked great for me (I used to have this exact printer, and all functions worked perfect including scan).

Good luck - - I think you'll get plenty of good help on this forum.

---

### Post by sideburns on 2015-12-16
Please notice that when the printer was first installed, there was no difficulty scanning; now there is.  Before accusing me of an "attitude," I'd appreciate it if you'd at least try to address that issue rather than just pointing a finger at the fact that 14.10 is now unsupported.

---

### Post by sideburns on 2015-12-16
Thank you, Geffrey_Arndt for your constructive suggestions.  We will follow them as soon as time permits, and report back on how they worked.  This is exactly the type of help I was looking for and that I gave to callers during the 7.5 years I spent doing senior-level tech support for an ISP, and that I give on the various Fedora-specific forums I infest.  Yes, it's important to remind people that their software's outdated, but once is enough; if they don't want to, or can't (I got stuck, recently, well behind the curve for Fedora because of hardware issues on my desktop, now fixed.) repeatedly telling them to upgrade is somewhat less than useful.

---

### Post by Geoffrey_Arndt on 2015-12-16
Frankly, my opinion of the HP 4500 AIO is not very high.   

Wouldn't surprise me to learn of a hardware issue also (as my paper feeder was very unreliable).    On the other hand, the _HP Envy 120_ is an outstanding quality printer - - that you might get a great price reduction on via eBay or similar.    The best low-cost printers I've used (consumer grade) are the Epson Work Force series, and certain Brother models.

Are the repos still available for Ubu 14.10?   That can pose problems with installing any later version deb.   If that deb won't install - - are you prepared to build the drivers from source?   That's why the recommendation re upgrade to Wily (in fact you'd likely be better off upgrading to Xenial 16.04 LTS beta, as it would be a seamless upgrade (rolling release model) to the stable release in April).

---

### Post by Bucky Ball on 2015-12-16
The latest version of HPLip is 3.13.3 in the 14.04 LTS. I don't think you could run the latest version on your machine if you could install it. 

That is the HPlip in the 14.04 repositories. The latest version is probably newer than that. Rather than install the latest version, you have probably installed the newest version for your OS, which is obsolete, like the OS. :)

Oh, but that's been said.

* So what happened when you tried to install them?

---

### Post by sideburns on 2015-12-16
Up until recently, Geoffrey_Audt, the printer worked Just Fine, and it still works fine as a printer and copier; it's just stopped working as a scanner.  (We can rule out hardware difficulties in the printer, btw, because it copies without problems.)

Bucky Ball, when we installed (not just tried, installed) the latest drivers, the printer continued to work as a printer and copier, and continued to fail to scan.  To be very, very specific, the situation as described in my original post is what we have *after* installing the newest available drivers.  Also, why are you talking about what's in the 14.04 repo when we're working with 14.10?  Is there a reason to think that the drivers for the older version are the more recent one?

---

### Post by lisati on 2015-12-16
> **sideburns said:**
>   Also, why are you talking about what's in the 14.04 repo when we're working with 14.10?  Is there a reason to think that the drivers for the older version are the more recent one?

14.10 is past its "use by date" which can increase the difficulty in fixing problems because its repos will be offline.

---

### Post by Geoffrey_Arndt on 2015-12-16
Other possibilities:

a).   Setup a Live Knoppix dvd - - has all the printer software installed including simple scan, OR

b).  Use CLI/Terminal:   [https://paulbradley.org/scanning-linux-command-terminal/](https://paulbradley.org/scanning-linux-command-terminal/)  



PS:   Lisati:   14.04 is still supported & repos fully available, but not 14.10 as you say.

---

### Post by sideburns on 2015-12-16
Thank you, Lisati, I just needed to make sure I wasn't missing something.

Using a CLI is a good way to find out if the scanner works, and we'll keep it in mind, although I hope we can get a GUI working.

---

### Post by lisati on 2015-12-16
> **Geoffrey_Arndt said:**
> PS:   Lisati:   14.04 is still supported & repos fully available, but not 14.10 as you say.
I noticed after posting that maybe I'd made a mistake. Sorry about that, I've edited my post and sent myself to the corner wearing a dunce's cap. :(

---

### Post by Geoffrey_Arndt on 2015-12-17
OK, probably my last post on this thread _pending further "results/feedback"_ from the OP Bro/Sis . . . 

Below is basic CLI command for standard document scan.   Change name of jpg file according to your choice:

This worked on my HP 120 Envy multi-function printer.   It outputs the file (scanned-document.jpg) to your file manager - whereupon you can then display/modify and send it to your printer.   Quality was excellent, and took about 10 seconds to do.    Worth a shot in my view.   Do not need sudo.

*scanimage -p --mode Color --resolution 300 --jpeg-quality 0  > scanned-document.jpg*

---

