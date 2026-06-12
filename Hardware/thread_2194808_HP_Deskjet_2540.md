---
title: "HP Deskjet 2540"
date: 2013-12-20
forum: Hardware
---

### Post by donnierlove on 2013-12-20
Trying to install an HP Deskjet 2540 All-in-One Series in Ubuntu 11.10.

I keep running into this "error 100". What can I do to get past it?

---

### Post by mörgæs on 2013-12-20
Hi, welcome to the fora.

HP's are usually easy to work with, but your version of Ubuntu is obsolete. Best is to begin with a fresh install of 13.10.

Post again when that's running.

---

### Post by donnierlove on 2013-12-21
I'd rather avoid that if I can. The newer versions are becoming progressively less suitable for me.

---

### Post by Bucky Ball on 2013-12-21
You don't need to go with a straight Ubuntu. Why not try Xubuntu or some other flavour? You will not get a lot of help with an unsupported release. 

I would suggest that upgrading to 13.10 is one option. 12.04 is supported for five years and pretty much rock solid. Either way, you might not get far sorting this on 11.10 (HP may not support that anymore in their drivers).

---

### Post by donnierlove on 2013-12-23
I was extremely unhappy with 11.10, and I don't want 12 or 13. I'd rather go back to 8 or 9, when it was a better operating system. But I didn't come here to discuss that. What is "error 100" and how do I make it go away?

---

### Post by Bucky Ball on 2013-12-23
> **Bucky Ball said:**
> You will not get a lot of help with an unsupported release. 



Simply because no-one's using it, and hasn't for months. But anyhow, as you want to stay with 11.10, if there is any hope of getting help you are going to need to give a lot more info. At what point you are getting this error and what you did and have done to try and remedy it would be a good start. 'I keep getting error 100' doesn't tell us much. 

Good luck. ;)

PS: Odd how 12 and 13 are unsatisfactory as they should be an improvement on 11. Same desktop environment. Curious as to what's so radically different, but as you say, off-topic and not for discussion here. :-k

If you are simply having troubles trying to install them or something is not working that did work in 11.10, you might contemplate starting a thread about that rather than attempting to fix a release that is getting more vulnerable as time goes on or moving backwards to releases that will be more vulnerable again.

---

### Post by Iowan on 2013-12-23
> **donnierlove said:**
> Trying to install an HP Deskjet 2540 All-in-One Series in Ubuntu 11.10.

I keep running into this "error 100". What can I do to get past it?

Have you checked HP's site:
[http://h10025.www1.hp.com/ewfrf/wc/product?product=5295967&lc=en&cc=us&dlc=en](http://h10025.www1.hp.com/ewfrf/wc/product?product=5295967&lc=en&cc=us&dlc=en)
I didn't check them all, but
[http://h30434.www3.hp.com/t5/forums/searchpage/tab/message?filter=labels%2Clocation&location=community%3Apsg&q=%22error+100%22](http://h30434.www3.hp.com/t5/forums/searchpage/tab/message?filter=labels%2Clocation&location=community%3Apsg&q=%22error+100%22)
suggests a communication problem (wireless?).

---

### Post by donnierlove on 2013-12-23
DEPENDENCY AND CONFLICT RESOLUTION
----------------------------------
Running 'sudo apt-get install --assume-yes python-dev'
Please wait, this may take several minutes...
error: Command failed. Re-try #1...
Running 'sudo apt-get install --assume-yes python-dev'
Please wait, this may take several minutes...
error: Command failed. Re-try #2...
Running 'sudo apt-get install --assume-yes python-dev'
Please wait, this may take several minutes...
error: Command failed. Re-try #3...
Running 'sudo apt-get install --assume-yes python-dev'
Please wait, this may take several minutes...
error: Package install command failed with error code 100
Would you like to retry installing the missing package(s) (y=yes*, n=no, q=quit) ? y
Running 'sudo apt-get install --assume-yes python-dev'
Please wait, this may take several minutes...
error: Package install command failed with error code 100
Would you like to retry installing the missing package(s) (y=yes*, n=no, q=quit) ? n
warning: Some HPLIP functionality might not function due to missing package(s).
Running 'sudo apt-get install --assume-yes libcups2-dev'
Please wait, this may take several minutes...
error: Command failed. Re-try #1...
Running 'sudo apt-get install --assume-yes libcups2-dev'
Please wait, this may take several minutes...
error: Command failed. Re-try #2...
Running 'sudo apt-get install --assume-yes libcups2-dev'
Please wait, this may take several minutes...
error: Command failed. Re-try #3...
Running 'sudo apt-get install --assume-yes libcups2-dev'
Please wait, this may take several minutes...
error: Package install command failed with error code 100
Would you like to retry installing the missing package(s) (y=yes*, n=no, q=quit) ?

On this page, [http://hplipopensource.com/hplip-web/install/install/index.html](http://hplipopensource.com/hplip-web/install/install/index.html), it's somewhere around step 8 or 9.

---

### Post by Bucky Ball on 2013-12-23
HP do not appear to provide a driver for this device, according to this:

[http://h10025.www1.hp.com/ewfrf/wc/softwareCategory?product=5295967&lc=en&cc=us&dlc=en&lang=en&cc=us](http://h10025.www1.hp.com/ewfrf/wc/softwareCategory?product=5295967&lc=en&cc=us&dlc=en&lang=en&cc=us)

Linux drivers from HP come in the form of HPLip. Not sure if you have that installed, but if not, unplug your printer, install HPLip from Synaptics or Software Centre then plug the printer in and switch it on. If it is supported, it should be picked up. You may need to reboot the machine after installing HPLip. 

No idea where this command comes from or why:

```
sudo apt-get install --assume-yes python-dev
```

You need to provide a link so we can see what you're attempting, but try these suggestions first as they may work anyhow.

Support didn't look good for that model, but read this and follow the instructions to update HPLip:

[http://www.liberiangeek.net/2013/08/hp-linux-imaging-and-printing-hplip-version-3-13-8-released-with-support-for-more-printers/](http://www.liberiangeek.net/2013/08/hp-linux-imaging-and-printing-hplip-version-3-13-8-released-with-support-for-more-printers/)

HPLip, as of August this year, apparently includes drivers for that printer.

Note: please use [code] tags for code. You can type them or 'Go Advanced', mark out code and click the # icon. Makes it easier to read. ;)

---

### Post by Donnie Love on 2013-12-23
> **Bucky Ball said:**
> ...unplug your printer, install HPLip from Synaptics or Software Centre then plug the printer in and switch it on...

I've had the printer plugged in the whole time. Is this where I'm going wrong?

---

### Post by Bucky Ball on 2013-12-23
donnierlove, go here and follow the instructions. Paste the two lines of code into a terminal one at a time. V simple. All HP printers rely on HPLip:

[http://www.liberiangeek.net/2013/08/...more-printers/](http://www.liberiangeek.net/2013/08/...more-printers/)

Your printer has only been supported by them since August so you need to update HPLip by following the instructions there. ;)

@Donnie Love: Start your own thread rather than crashing this one. It just confuses the issue. If you haven't got HPLip installed that's where you're going wrong. Thanks. ;)

... but wait, are you the same user with a name change??? Apologies if you are and the above instructions apply if that is the case.

* More detailed instructions for same update installation of HPLip:

[http://www.liberiangeek.net/2013/02/hp-linux-imaging-and-printer-hplip-version-3-13-2-releasedadds-support-for-more-printers/](http://www.liberiangeek.net/2013/02/hp-linux-imaging-and-printer-hplip-version-3-13-2-releasedadds-support-for-more-printers/)

This looks like where your error codes are coming from. Lets see if you get them with the updated HPLip.

---

### Post by Donnie Love on 2013-12-23
I tried installing it from the Software Center, but it tells me "Package dependencies cannot be resolved". By that I assume it means there's no hope for 11.10. I guess I'll just have to admit defeat an update to newer version, which I'm sure I'll regret. When I updated to 11, my machine was crippled for a week and never fully recovered. :0[

---

### Post by Donnie Love on 2013-12-23
> ... but wait, are you the same user with a name change??? Apologies if  you are and the above instructions apply if that is the case.

Yes, sorry for the confusion. Had problems accessing old account with new log-in.

---

### Post by Donnie Love on 2013-12-23
Yeah, it's not going to work. I give up. Thanks anyway.

---

### Post by Bucky Ball on 2013-12-23
Installing the new HPLip via the instructions on the link I supplied (NOT via Software Centre as that HPLip, even in 12.04, might be too old to support that printer), would definitely be missing dependencies in 11.10. 

You can do a straight upgrade to 12.04 LTS from 11.10 via the update manager (you should see a box up top telling you 'New LTS version 12.04 available' or something like it). This should keep settings as is, but these kind of upgrades can be problematic sometimes. ALWAYS backup before upgrading this, or any other way. ;)

Good luck with it and create a new post if you have problems.

---

### Post by mörgæs on 2013-12-23
> **Donnie Love said:**
> When I updated to 11, my machine was crippled for a week and never fully recovered.

Yes, an upgrade can wreck any system. That's why I started with recommending a fresh install of 13.10.

---

