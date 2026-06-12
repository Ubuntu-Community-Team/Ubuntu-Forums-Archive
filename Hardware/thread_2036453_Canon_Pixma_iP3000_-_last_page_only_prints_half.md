---
title: "Canon Pixma iP3000 - last page only prints half"
date: 2012-08-01
forum: Hardware
---

### Post by beoram on 2012-08-01
I'm using a Canon Pixma iP3000 printer. I've used this printer for several years with Linux with no real problems. Right now I'm running under Bodhi Linux 2.0 (which has an Ubuntu 12.04 base) and I'm having a very strange problem: 

Whatever I print, the last page only prints the first half. But all of the pages before the last page print fine.

I've tried turning the printer on and off, and initiating the nozzle cleaning, and rebooting the computer, reinstalling the driver, etc.  But nothing seems to help.

Any ideas?

---

### Post by aikishugyo on 2012-08-02
> **beoram said:**
> I'm using a Canon Pixma iP3000 printer. /../ Right now I'm running under Bodhi Linux 2.0 (which has an Ubuntu 12.04 base) and I'm having a very strange problem: 

Whatever I print, the last page only prints the first half. But all of the pages before the last page print fine.

I've tried turning the printer on and off, and initiating the nozzle cleaning, and rebooting the computer, reinstalling the driver, etc./../

Hi, what driver do you use? If it is the gutenprint driver, then
[LIST=1]
[*]What is the gutenprint version?
[*]What resolution are you using?
[*]If resolution is "Automatic" or "Default", then try the various plain media modes in order and let me know if all exhibit the same error.
[/LIST]

Regards,
Gernot Hassenpflug

---

### Post by beoram on 2012-08-02
> **aikishugyo said:**
> Hi, what driver do you use? If it is the gutenprint driver, then
[LIST=1]
[*]What is the gutenprint version?
[*]What resolution are you using?
[*]If resolution is "Automatic" or "Default", then try the various plain media modes in order and let me know if all exhibit the same error.
[/LIST]

Regards,
Gernot Hassenpflug

1. gutenprint version: 5.2.8~pre1-0ubuntu2.1
2./3. I've printed on Automatic and 300x300, and it exhibits the same behavior.

Additional note: I had change the ink cartridge and was in the midst of printing something out when the system froze. The page it had been printing only half printed and I had to reboot the system. I am wondering if it could be something internal to the printer's data which got messed up. I've tried doing the "reset" described [here]("http://www.techrepublic.com/forum/questions/101-250249/printer-prints-only-half-pages-canon-ip3000"), but that didn't seem to help.

---

### Post by headscratcher on 2012-08-02
Hi ,

Im having the same issue with a Canon ip5200 since this morning when there was an update to CUPS 1.5.3.

Did you get the update through Software Updater as well, if so this would point to an issue with CUPS (again!!)

Someone else has the problem here [http://ubuntuforums.org/showthread.php?t=2036618](http://ubuntuforums.org/showthread.php?t=2036618)

Does anyone know when CUPS 1.6.0 will be available through updater??

---

### Post by jo@tux on 2012-08-02
Today I made &#8203;&#8203;an update after doing that I can find the same problem.
As an workaround I first disabled the updates (precise-updates and precise-backports)in the repositories.
Then I completely uninstalled cups 1.5.3 and installed the original version 1.5.2-9 again. If i do not disabled the updates i can not install the old version of cups. 
Then I have the version 1.5.2-9ubuntu1 locked until further notice. Now does my Printer IP4950 print full pages again.

---

### Post by beoram on 2012-08-02
Ah, so it is actually a CUPS problem? 

I'll try downgrading. (Or else upgrading to 1.6.0?)

---

### Post by beoram on 2012-08-02
Unfortunately when I tried to downgrade to CUPS 1.5.2-9 I get the following error:

```
Setting up cups (1.5.2-9ubuntu1) ...
ln: accessing `/usr/lib/cups/backend-available/ipp14': No such file or directory
dpkg: error processing cups (--configure):
 subprocess installed post-installation script returned error exit status 1

```

---

### Post by aikishugyo on 2012-08-03
As the gutenprint Canon backend maintainer, and not owning any of the printers usually, I'm always trying to get debugging information on Debian or Ubuntu forums.
Thanks for confirming you use 5.2.8pre-1. You can use 5.2.9 now too (skip 5.2.8 ), this is a packaging bugfix release after 5.2.8 came out a short time ago.
As for the issue, it really does appear to be CUPS, and not gutenprint :-(
But still, see if you get the same behaviour for the other resolutions: for plain media there are maybe 3 or 4.

Regards,
Gernot Hassenpflug

---

### Post by headscratcher on 2012-08-03
[aikishugyo]("http://ubuntuforums.org/member.php?u=167122") - Just to check whether updating to Gutenprint 5.2.9 makes any difference to the problem please could you let us know how to (easily) upgrade in Ubuntu to this newer version - has it been packaged yet?

I never had problems in 11.10 with CUPS 1.5.0 -  to help OP and myself does anyone know how to downgrade CUPS successfully to this and other versions.

many thanks!

---

### Post by beoram on 2012-08-03
I did a forcible "downgrade by downloaded .deb" installation of cups_1.5.0-16_i386 after purging the old cups package (I then had to reinstall gutenprint and bodhi-printing packages). It seems to be printing again normally again! 

So that's good, though I'm rather annoyed with CUPS for having wasted so much of my time.

---

### Post by headscratcher on 2012-08-04
Hi Beoram,

Great to hear you got the problem sorted.

Please could you let me know where you found the deb you installed for CUPS  1.5.0 and , if you can, go through the steps you took to get it working. I would be most grateful!

When I tried something similar I ended up breaking the package installer in Ubuntu and it took a great deal of sweat to get it functioning again. I think this was caused by a number of broken dependencies.

many thanks

---

### Post by kauboy on 2012-08-04
> **beoram said:**
> I did a forcible "downgrade by downloaded .deb" installation of cups_1.5.0-16_i386 after purging the old cups package (I then had to reinstall gutenprint and bodhi-printing packages). It seems to be printing again normally again! 

So that's good, though I'm rather annoyed with CUPS for having wasted so much of my time.

Beoram, I (rather stupidly) made the same mistake of trying to downgrade to 
1.5.2-9 despite having read your comment and have ended up with a broken CUPS that will neither uninstall nor upgrade. How exactly did you fix this? It would help me (and a lot of others) avoid wasting all the time that you did fixing yours.

**EDIT**: Here is how I fixed mine. Marked cups for complete removal, which also marked a few other packages for uninstallation. Noted down those packages which got uninstalled. Reinstalled cups (albeit the buggy 1.5.3 version) along with the other packages that got uninstalled. Seems to have worked, so far.

**EDIT2**: Except that my printer has been unregistered from the system (probably because complete removal purges configuration files too) but thats a minor issue.

---

### Post by headscratcher on 2012-08-04
Just reported this as a bug.

[https://bugs.launchpad.net/ubuntu/+source/cups/+bug/1033064](https://bugs.launchpad.net/ubuntu/+source/cups/+bug/1033064)

Really fed up spent a whole day trying to fix this. Downgraded to CUPS 1.5.0 but couldn't print from LibreOffice, printed from other apps OK though.

Help!

---

### Post by ubnewbie2 on 2012-08-06
> **headscratcher said:**
> Hi Beoram,

Great to hear you got the problem sorted.

Please could you let me know where you found the deb you installed for CUPS  1.5.0 and , if you can, go through the steps you took to get it working. I would be most grateful!

When I tried something similar I ended up breaking the package installer in Ubuntu and it took a great deal of sweat to get it functioning again. I think this was caused by a number of broken dependencies.

many thanks

Yes please, I also want to downgrade until they fix this problem.

---

### Post by ubnewbie2 on 2012-08-06
> **beoram said:**
> Unfortunately when I tried to downgrade to CUPS 1.5.2-9 I get the following error:

```
Setting up cups (1.5.2-9ubuntu1) ...
ln: accessing `/usr/lib/cups/backend-available/ipp14': No such file or directory
dpkg: error processing cups (--configure):
 subprocess installed post-installation script returned error exit status 1

```

Same here, so I'm stuck without printing.

---

### Post by headscratcher on 2012-08-06
ubnewbie2 - as a temporary solution I have installed Lubuntu 11.10 (which has CUPS 1.5.0) as a guest in Virtualbox and am running my printer from that..

Not ideal but at least it prints.

I had managed to downgrade to CUPS 1.5.0 (the last properly working version)  but then had problems printing from LibreOffice, (only this app, everything else was fine) the jobs were sent and visible in the print queue but were empty i.e. showing as 0k. Not sure whether this was a problem with the Gutenprint driver version.

Hopefully a proper fix is going to be released soon. I know that the bug has been triaged and is marked as critical - fingers crossed.

---

### Post by ubnewbie2 on 2012-08-06
> **headscratcher said:**
> ubnewbie2 - as a temporary solution I have installed Lubuntu 11.10 (which has CUPS 1.5.0) as a guest in Virtualbox and am running my printer from that..

Not ideal but at least it prints.

I had managed to downgrade to CUPS 1.5.0 (the last properly working version)  but then had problems printing from LibreOffice, (only this app, everything else was fine) the jobs were sent and visible in the print queue but were empty i.e. showing as 0k. Not sure whether this was a problem with the Gutenprint driver version.

Hopefully a proper fix is going to be released soon. I know that the bug has been triaged and is marked as critical - fingers crossed.

Nice idea - running a virtual machine for printing. Thanks. 

and yes, I hope the fix comes soon.

---

### Post by headscratcher on 2012-08-06
Good news !!!!

There has been some really quick work done by Till Kamppeter the Ubuntu printing maintainer and he has released a fix for testing - 1.5.3-0ubuntu3~ppa1

It's here (near the bottom of page) with instructions on how to install it...

[https://bugs.launchpad.net/ubuntu/+source/cups/+bug/1032456](https://bugs.launchpad.net/ubuntu/+source/cups/+bug/1032456)

Just tried it on my Canon iP5200 on Precise and it works!

Do bear in mind that this is a test fix - and do feedback any issues to Till at the above location.

Thank you Till! What a star! :)

---

### Post by frenchian on 2012-08-06
> **headscratcher said:**
> Good news !!!!

There has been some really quick work done by Till Kamppeter the Ubuntu printing maintainer and he has released a fix for testing - 1.5.3-0ubuntu3~ppa1

It's here (near the bottom of page) with instructions on how to install it...

[https://bugs.launchpad.net/ubuntu/+source/cups/+bug/1032456](https://bugs.launchpad.net/ubuntu/+source/cups/+bug/1032456)

Just tried it on my Canon iP5200 on Precise and it works!

Do bear in mind that this is a test fix - and do feedback any issues to Till at the above location.

Thank you Till! What a star! :)

#Till, just loaded the fix from your PPA. **Very** happy to say it works (on my MP270)!

#headscratcher, thanks for all the time you've spent on this. I suspect it speeded the solution for the rest of us....

Cheers

---

### Post by ubnewbie2 on 2012-08-06
I am on ubuntu 12.04. Even though I added Till's ppa, I still only see version 1.5.3. of cups.

Edit:  sorry either I tried to early or I missed it - but I have the update now, and it WORKS!  :)  Thanks.

---

### Post by beoram on 2012-08-07
Apologies for the late reply.

I haven't tried the new ppa (Till) as I'm wary of breaking what seems for the moment to be fixed.

My method for downgrading: 
1) completely remove CUPS in Synaptic. (Make sure to note down what else gets removed with it, so that I can reinstall those packages).
2) download CUPS 1.50 from here: [http://launchpadlibrarian.net/91425458/cups_1.5.0-16_i386.deb](http://launchpadlibrarian.net/91425458/cups_1.5.0-16_i386.deb)
3) manually install the above .deb
4) pin CUPS to version 1.50 in Synaptic (and in apt-get if you use the commandline, see [https://help.ubuntu.com/community/PinningHowto](https://help.ubuntu.com/community/PinningHowto) on pinning and [http://ubuntuforums.org/showthread.php?t=1941320](http://ubuntuforums.org/showthread.php?t=1941320) on removing pinning for apt-get)
5) reinstall any other packages that got removed when completely removing CUPS.

---

### Post by mikasam on 2012-08-07
Have the same printer issue with Canon MP270. Really very annoying.

---

