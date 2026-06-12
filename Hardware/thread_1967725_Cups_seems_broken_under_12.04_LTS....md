---
title: "Cups seems broken under 12.04 LTS..."
date: 2012-04-28
forum: Hardware
---

### Post by Palmer Eldritch on 2012-04-28
[COLOR=black]Hello,[/COLOR]
 
[COLOR=black]I just installed Ubuntu 12.04 LTS for my venerable father, (87 years!) Cups unfortunately seems clearly broken on this OS release, and I was not able to setup functionally his Canon i-SENSYS mf4270 network printer. Meanwhile I've choose a Dell 3110cn also available on our network which works perfectly under this OS. (With 10.04 LTS Ubuntu version, Cups correctly handles this Canon printer...)[/COLOR]
 
[COLOR=black]Does anyone have a solution?[/COLOR]
 
[COLOR=black]Thank you![/COLOR]
 
[COLOR=black]Regards,[/COLOR]
[COLOR=black]Palmer.[/COLOR]
 
[COLOR=black]**PS:**[/COLOR]
 
[COLOR=black]I have not either unfortunately found a plugin for GKrellM for a Dell Vostro 410 for this OS vesion...[/COLOR]

---

### Post by grahammechanical on 2012-04-28
During the past five months I have seen any number of updates for CUPS come through in 12.04. A lot work has been done. Too much for it to be written off as broken, just like that.

Perhaps you need a driver. I have seen libraries for HP and Brother printers listed in Synaptic but nothing for Canon.

here is a link to their page.

[http://www.canon-europe.com/support/software/linux/]("http://www.canon-europe.com/support/software/linux/")

The last version of Ubuntu that Canon tested their Linux driver with was 7.04. Perhaps it is more accurate to say that Canon is broken in Linux.

Regards

P.S. Here is a link to a driver that might work:

[https://launchpad.net/~michael-gruz/+archive/canon]("https://launchpad.net/~michael-gruz/+archive/canon")

---

### Post by barri on 2012-04-28
for me, my Canon iP4600 stopped working reliably after the upgrade to 12.04. And I tried now for hours to get it to work....  without success.

12.04 recognizes the printer and installs a driver. Also I can print test-pages. But otherwise print-jobs just hang or never execute about 50% of the time.

Something seems totally broken here.

Does anyone know how to do a clean reinstall of CUPS?

---

### Post by Palmer Eldritch on 2012-04-28
Hello,
 
Thank you Grahammechanical for your response, but I am not exaggerating by saying Cups seems broken in Ubuntu 12.04 LTS as it is clearly the case, we have to call a spade a spade!
 
This does not seems specific to Ubuntu, but also affects other distributions of Linux, this is clearly the latest version of Cups which seems to be the cause.
 
On our home network we have two other PCs with ubuntu 10.04 LTS, and this network Canon printer works perfectly with the Cups driver from the Canon website.
 
As reported by Barri, the print test fails with the following error message: &#8220;Inactive - File &#8216;/ usr/lib/cups/filter/pstoufr2cpca&#8217; not available: No such file or directory"; I tried to add the file from an installation of Ubuntu 10.04 LTS, but it does not solve the problem&#8230;
 
In my opinion it is a very serious problem for an LTS release, Canon is not an exotic brand, there was a lot of Canon printers sold worldwide!
 
Regards
Palmer.

---

### Post by Palmer Eldritch on 2012-04-29
> **barri said:**
> for me, my Canon iP4600 stopped working reliably after the upgrade to 12.04. And I tried now for hours to get it to work.... without success.
 
12.04 recognizes the printer and installs a driver. Also I can print test-pages. But otherwise print-jobs just hang or never execute about 50% of the time.
 
Something seems totally broken here.
 
Does anyone know how to do a clean reinstall of CUPS?
Hello,
 
I didn&#8217;t even succeed to print a page test, but you ask the right question!
 
Regards,
Palmer.

---

### Post by Palmer Eldritch on 2012-04-29
Hello,
 
On the [North American Canon website]("http://www.usa.canon.com/cusa/support/office/imageclass_copiers/imageclass_mf4270/imageclass_mf4270#DriversAndSoftware") there is a newer version of the driver:
 
- [Canon UFR II Printer Driver for Linux Version 2.40]("https://docs.google.com/open?id=0B8uZlrsvNCkKRDM4eUZxeVNqQWs") (Direct link)
 
It seems to have been tested in Ubuntu version 11.04, maybe someone had installed this version?
 
I will also try to reinstall cups-client_1.5.2-9ubuntu1_i386.deb ...
 
This may be perhaps a solution?
 
Regards,
Palmer.

---

### Post by robertmarik on 2012-04-30
Hello all

I have also strong opinion that something is broken - printing to two printers (HP p2015d, WM20i) stopped to work after upgrade to 12.04. 

I have error messages cups-ipp-missing-printer-state-reasons and cups-ipp-missing-validate-jod. Perhaps relevant to [http://bugs.launchpad.net/ubuntu/+source/cups/+bug/945028](http://bugs.launchpad.net/ubuntu/+source/cups/+bug/945028)

Is it possible to downgrade cups to the Ubuntu version 10.10 ?

Thanks. 
Robert

---

### Post by merlinus on 2012-04-30
I have similar problems with 12.04, which did not exist with 11.10.  I set up my HP LaserJet 4 as a network printer.  It works fine from the machine to which it is connected, but no longer works over the network.

I use the ipp protocol, and sending a job gives an error message that the printer is busy.

---

### Post by Palmer Eldritch on 2012-04-30
> **merlinus said:**
> I have similar problems with 12.04, which did not exist with 11.10. I set up my HP LaserJet 4 as a network printer. It works fine from the machine to which it is connected, but no longer works over the network.
 
I use the ipp protocol, and sending a job gives an error message that the printer is busy.
Hello,
 
On a French forum a user said today he had a similar problem with version 11.10 of Ubuntu that was solved by an update after a few days without having to do anything else ...
 
Regards,
Palmer.

---

### Post by merlinus on 2012-04-30
Let's hope so!!!  And perhaps it will fix other issues as well.

---

### Post by NLinTKO on 2012-05-01
I am experiencing the same problem. Printing on my Canon iP3500 worked well with Ubuntu 11.10, but does not work anymore since upgrading to 12.04. The printer is recognized by Ubuntu and its status is properly indicated, but a test page cannot be printed and no print job appears in print. I have tried to reinstall the driver but this did not improve the situation.

---

### Post by Palmer Eldritch on 2012-05-01
> **merlinus said:**
> Let's hope so!!! And perhaps it will fix other issues as well.
Hello,
 
Good news!
 
After deleting the Canon printer, uninstalled its drivers, reinstalled completely Cups, installed the version 2.4 of printer drivers, reinstalled the Canon printer, **and performed a system update**, everything is OK!!!
 
My venerable father is so happy! :)
 
Regards,
Michail.

---

### Post by mcblades on 2012-05-01
I also am experiencing problems with cups 1.52x on ubuntu 12.04.

I have a konica-minolta 4750en which worked flawlessly on 11.04 & 11.10 under cups either as an ipp network device or via USB.

After attempting to upgrade my desktop to 12.04 from a usb drive I hosed the system and ended up reinstalling a fresh copy (thank the penguin for dejadup). I installed the printer and it's ppd file via the cups web interface and tried to print a test page.

cups discovers the printer and sends it a file which then kills the printer (hangs with the printer LCD flashing 'processing' and also hangs the printers web interface). So I reboot the printer and try again this time installing the printer from unity.  Alas, same problems.

The one laptop in my house which I have yet to "upgrade" to 12.04 (running ubuntu 11.10 and cups 1.5) however connects to the printer flawlessly and prints fine.

I am now trying to figure out how to redirect the output of cups to a file so I can compare the two printjobs. Maybe something will leap out.

Any help or advice gratefully received

---

### Post by pkilpo on 2012-05-03
I have a problem too with  printing in 12.04 Epson AcuLaser wont print
I followed the 11.10 instructions  downloaded driver source [http://www.avasys.jp/lx-bin2/linux_e/mfp/DL1.do](http://www.avasys.jp/lx-bin2/linux_e/mfp/DL1.do),
configured compiled and installed driver. All seems ok.

Even copied compiled stuff from /usr/local/bin to /usr/lib/cups/filters 

Ubuntu founds the printer and it *seems* that it prints test page, it shows on printed queue, but nothing really gets printed. It seems that it does not even send anything to printer because data light does not blink.

Printer itself is working fine when printing from Windows.

cups error_log shows that kind of warnings: 
W [03/May/2012:21:55:22 +0300] failed to CreateProfile: org.freedesktop.ColorManager.AlreadyExists:profile id 'EPSON_AL-CX11-RGB..' already exists.

I have tried to purge and reinstall cups too.

---

### Post by mcblades on 2012-05-04
There seems to be a bug in the postscript that ghostscript spits out vs that of pdftops used in cups 1.50 (on oneiric).

There is an ongoing discussion re the KM printer on the bugs forum at cups.org.

In the end I setup a virtualbox running 11.10, LAMP and cups and now print to that from my 12.04 systems.

Hopefully someone will sort this out before too long, it must be affecting a significant number of users.

---

### Post by ratcheer on 2012-05-04
Adding my voice to this, I am unable to print to a Canon MP620 from 12.04. I can print without problems in 11.10. I am having to keep 11.10 on my PC just for printing. :(

Tim

---

### Post by crf on 2012-05-05
I can't print now either, after upgrading to 12.04. 
I have two different drivers installed for my printer, a Samsung CLP 325-W, the foo2qpdl driver from [http://foo2zjs.rkkda.com/](http://foo2zjs.rkkda.com/) and the Samsung proprietary driver. Both used to work, but now nothing is printed.  

Using system-config-printer, neither driver gets the toner levels correct either. Ugly nonsense is printed there. Asking for toner levels also generates non-stop ip traffic between the computer and the printer. (I have to cancel that job using CUPS web interface.) 

I made a bug. Hasn't got must of a response yet. [https://bugs.launchpad.net/ubuntu/+source/cups/+bug/992982](https://bugs.launchpad.net/ubuntu/+source/cups/+bug/992982)

---

### Post by crf on 2012-05-05
Does anyone understand cups commands?
[http://localhost:631/help/spec-command.html](http://localhost:631/help/spec-command.html)

I'd like to use one to just send a reportlevels query.

---

### Post by svenakela on 2012-05-06
There's a bug report on Cups in Ubuntu 12.04. Multiple users have confirmed that Cups 1.5.2 doesn't work as expected while earlier releases of Ubuntu did. 

[https://bugs.launchpad.net/ubuntu/+source/cups/+bug/992982](https://bugs.launchpad.net/ubuntu/+source/cups/+bug/992982)

---

### Post by niplas on 2012-05-09
Also experiencing this bug

Seems related to ghostscript and/or the ps / pdf pre-filters of CUPS

---

### Post by duncanidaho391 on 2012-05-10
I'm experiencing this as well.... can't seem to get it to work at all, on 12.04, canon ip2600
Edit:
My canon ip2600 is working with 12.04 now, Instead of using the michael gruz repo, I followed the instructions here: [http://ubuntuforums.org/showpost.php?p=10580814&postcount=33](http://ubuntuforums.org/showpost.php?p=10580814&postcount=33)

(got the drivers from [http://support-asia.canon-asia.com/](http://support-asia.canon-asia.com/) )
And to make the dependencies pass, I changed libcupsys2 to libcups2 and libpopt0 to 1.16

And a final note, I REMOVED the printer from the cups config, then TURNED THE PRINTER off, and unplugged the USB cable BEFORE installing these packages. Then I turned the printer on WITHOUT the USB connected, WAITED for warmup to COMPLETE. Then connected the cable.

Dunno if all these particular steps are necessary, but this is exactly what worked for me with an up to date 12.04 after trying various fixes including completely hunting down and downgrading cups dependencies for hours.

---

### Post by dFlyer on 2012-05-11
I concur that cups in 12.04 is broken on my HP Photosmart 8250. What seems strange is that I can print with libreoffice and acroread. I can't print with AfterShot Pro, gimp, shotwell, and most other programs. Whats real strange is that Bibble5 prints about 50% of the time. So yes Cups in 12.04 is broken.

---

### Post by evaarties on 2012-05-11
> **ratcheer said:**
> Adding my voice to this, I am unable to print to a Canon MP620 from 12.04. I can print without problems in 11.10. I am having to keep 11.10 on my PC just for printing. :(

Tim

Here is a script which will install working drivers [http://rackerua.com/2011/05/mp-620-630-debian-based-univeral-installer/](http://rackerua.com/2011/05/mp-620-630-debian-based-univeral-installer/)

One problem I still have is printing multiple pages on one page. I can set it ie to two pages per page, but it's scaled as if I choose 4 pages per page. Anyone else having this problem in 12.04?

---

### Post by ratcheer on 2012-05-11
> **evaarties said:**
> Here is a script which will install working drivers [http://rackerua.com/2011/05/mp-620-630-debian-based-univeral-installer/](http://rackerua.com/2011/05/mp-620-630-debian-based-univeral-installer/)

One problem I still have is printing multiple pages on one page. I can set it ie to two pages per page, but it's scaled as if I choose 4 pages per page. Anyone else having this problem in 12.04?

Thank you, but I have already run that script several times. It worked on Oneiric, but not on Precise. For me, anyway.

Tim

---

### Post by evaarties on 2012-05-12
> **ratcheer said:**
> Thank you, but I have already run that script several times. It worked on Oneiric, but not on Precise. For me, anyway.

Tim

Have you also tried the latest version? Just 15 hours ago a new version was placed online which fixes problems with 12.04 64bit.

---

### Post by old_dog on 2012-05-12
I am having same sort of problem with an Canon IP4200 and 12.04, is there any news, rumour or response yet?

---

### Post by old_dog on 2012-05-12
I am having same sort of problem with an Canon IP4200 and 12.04
Is there any news, rumour or response yet?
Cheers
old_dog

---

### Post by old_dog on 2012-05-12
My apologies for posting twice.....
I am going to blame it on the high speed internet we have round here, in fact last year someone did an experiment with a carrier pidgeon and t'internet you know what the carrier pidgeon won!

---

### Post by The Cog on 2012-05-12
Another "Me too" post. 
In my case, networked HP laserjet 4050 worked in many previous versions of Ubuntu, in 12.04 it just prints an error message  (accessviolation and OFFENDING COMMAND if I remember rightly). Test page prints OK so I guess it might be a problem in the postscript generator.

---

### Post by pkilpo on 2012-05-12
I did this what was on launchpad:

[https://bugs.launchpad.net/ubuntu/+source/cups-filters/+bug/950713/comments/7](https://bugs.launchpad.net/ubuntu/+source/cups-filters/+bug/950713/comments/7)

(replacing that printer with AL-CX11.ppd)

/tmp/printout came up 0 length.

It seems that it does not render anything to ps when printing.
Intresting :p

EDIT:

Solved!
Debugging further on cmd inside pstoalcx11.sh found that libstdc++.so.5 was missing.
This was not written to any log, just found out when executing command on terminal.
"sudo apt-get install ia32-libs" installs a lot of libs including the missing one.

---

### Post by DMJ on 2012-05-20
Same type of issue with a Samsung SCX-4623f. It worked flawlessly in 11.04 and 11.10. I tried it from to different computers, one running 32 bit 12.04, and the other running 64 bit. I also have ia32-libs installed already. So that's not the cause. 

The behavior is sporadic. At first it would print the first copy, but not the others. Then it wouldn't print at all. I tried logging in and out, re-installing the driver. Unplugging, and reconnecting the printer. 

I connected it to a Win XP VM, and it printed without issues.

I think Canonical needs to rethink their release system. It's seems they're in a hurry to push the new releases out on time, rather than making sure they're working first. Of course it's my fault, really, for upgrading so soon after the release date. Foolish.

---

### Post by DMJ on 2012-05-20
Update. At least in my case, it's a Unity or Gnome issue. I logged into KDE and was able to print without any problems. 

Dangit. I was really starting to like this version of Unity too. I guess I'll go back to KDE for now, until I get this figured out.

Strange, though. Why would the DE effect printing? 

I'd thought it may be the fact that I have both DEs installed and it's a conflict. But I have the same problem on my laptop, which only has Unity installed.

---

### Post by nrundy on 2012-05-20
> **Palmer Eldritch said:**
> [COLOR=black]Hello,[/COLOR]
 
[COLOR=black]I just installed Ubuntu 12.04 LTS for my venerable father, (87 years!) Cups unfortunately seems clearly broken on this OS release, and I was not able to setup functionally his Canon i-SENSYS mf4270 network printer. Meanwhile I've choose a Dell 3110cn also available on our network which works perfectly under this OS. (With 10.04 LTS Ubuntu version, Cups correctly handles this Canon printer...)[/COLOR]
 
[COLOR=black]Does anyone have a solution?[/COLOR]
 

I don't know a solution, but I AGREE with you. 12.04 broke printing!

I have had zero problems with my printers using 10.04. But when I installed 12.04 I have not been able to get any of the printers to print.

---

### Post by robertmarik on 2012-05-21
> **DMJ said:**
> Update. At least in my case, it's a Unity or Gnome issue. I logged into KDE and was able to print without any problems. 

I tried lxde and the problem persists. The message "Print file was not accepted." is in the /var/log/cups/errors and in the printer properties I have cups-ipp-missing-printer-state-reasons and cups-ipp-missing-valiadate-jobs.

---

### Post by DMJ on 2012-05-21
> **robertmarik said:**
> I tried lxde and the problem persists. The message "Print file was not accepted." is in the /var/log/cups/errors and in the printer properties I have cups-ipp-missing-printer-state-reasons and cups-ipp-missing-valiadate-jobs.

It seems like there's more than one issue being described in this thread. What exactly is the behavior your getting in LXDE? LXDE is GTK+ based, so there are probably some common components with Unity. 

Has anyone tried Gnome Shell, to see if the problem exists there as well?

I'm going to check out launchpad. I'd bet there's a bug report. I'll take a look at the log files as well, when I get the time.

My guess is that there's some process in Unity that's keeping cups busy so it's not able to process print jobs.

---

### Post by jitro72 on 2012-05-21
I have the same problem with Toshiba e-studio 4520 in Gnome Shell and in Unity too. :(

---

### Post by DMJ on 2012-05-21
> **jitro72 said:**
> I have the same problem with Toshiba e-studio 4520 in Gnome Shell and in Unity too. :(

Has anyone else tried this in KDE. I'm interested to know if it works consistently there.

I checked out launchpad, and couldn't find any bug reports. Of course, I've never found the search there to work very well. 

Strange that this doesn't appear to be more widespread. It must work fine for a lot of people. It could be particular drivers, but the same driver works for me in KDE.

---

### Post by NLinTKO on 2012-05-22
Have you found these bug reports?
[https://bugs.launchpad.net/ubuntu/+source/cups/+bug/992468](https://bugs.launchpad.net/ubuntu/+source/cups/+bug/992468)
[https://bugs.launchpad.net/ubuntu/+source/cups/+bug/945028](https://bugs.launchpad.net/ubuntu/+source/cups/+bug/945028)
I think there are even more.

---

### Post by old_dog on 2012-05-22
A lot of people seem to be having a problem with 12.04 and in particular Canon printers. Can we expect a solution to be forthcoming? the reason I ask is that I have been sitting on my hands waiting. 
Do I start attempting some hare-brained scheme of my own that I know will end in disaster and a complete re-install.
Cheers old_dog

---

### Post by ratcheer on 2012-05-22
> **old_dog said:**
> 
Do I start attempting some hare-brained scheme of my own that I know will end in disaster and a complete re-install.


Don't do it! I did two complete reinstalls of Precise after trying various suggestions to solve this problem. I ended up kust keeping an Oneiric installation in order to be able to print.

My printer is a Canon MP-620. My travails are documented here, probably in more than one thread.

Tim

---

### Post by eyekone on 2012-05-22
Just wanted to mention that I seem to have the a similar problem with a Toshiba 3540 (Office MFP).

It prints the test page, but no the Ubuntu test page; a page with an error: "PS error: invalidaccess".
After updating to 12.04 it worked fine on PDF documents and pictures, but anything with text (documents or excel sheets, etc) would come up with the above error.
Now nothing works and I only are able to print a first time after reinstalling, afterwards the printer seems to be offline or out of paper, evenso this isn't the case.

I've tried removing cups, removing the printer driver, trying different drivers, updating cups (unsucessfully) to 1.5.3 and many combinations of them all.

This is our office printer and I require is all the time. My solution meanwhile is asking colleagues to print documents or to transfer the file on a spare windows laptop.

I'm not hoping to get any solutions from here, but just to mention my problem.



Jah bless!

---

### Post by DMJ on 2012-05-22
> **old_dog said:**
> A lot of people seem to be having a problem with 12.04 and in particular Canon printers. Can we expect a solution to be forthcoming? the reason I ask is that I have been sitting on my hands waiting. 
Do I start attempting some hare-brained scheme of my own that I know will end in disaster and a complete re-install.
Cheers old_dog

Just use a VM to print until it's resolved. Install Kubuntu or another KDE distro in VBox. Then spend the time you save by not re-installing learning the how CUPS works so you can troubleshoot :)

---

### Post by DMJ on 2012-05-22
> **NLinTKO said:**
> Have you found these bug reports?
[https://bugs.launchpad.net/ubuntu/+source/cups/+bug/992468](https://bugs.launchpad.net/ubuntu/+source/cups/+bug/992468)
[https://bugs.launchpad.net/ubuntu/+source/cups/+bug/945028](https://bugs.launchpad.net/ubuntu/+source/cups/+bug/945028)
I think there are even more.

It looks like those are for network printing. My problem is exists for USB attached as well. 

When I get some time, I'm going to dive under the hood, and figure this out, you'll see :)

Fortunately I have KDE installed as well, so I have lost much time because of it.

---

### Post by jitro72 on 2012-05-23
Hope CUPS 1.5.3 will resolve this situation. Does anybody know when it could be expected?

---

### Post by pt123 on 2012-05-24
I recently upgraded from 10.10 to 12.04,  where cups-pdf was working perfectly fine but now it's useless because of of a bug where it is converting all text to images than embedding them as text. All the text printed to PDF is bloody useless as it can't be copied it is like having paper.

The bug seems to reported here, as usual it has been marked as wishlist for 11.10.
[https://bugs.launchpad.net/ubuntu/+source/cups-pdf/+bug/820820](https://bugs.launchpad.net/ubuntu/+source/cups-pdf/+bug/820820)
It has to do with cups doing an unnecessary conversion in the middle.

I have also created another bug report for 12.04.
[https://bugs.launchpad.net/ubuntu/+source/cups-pdf/+bug/1003883](https://bugs.launchpad.net/ubuntu/+source/cups-pdf/+bug/1003883)

---

### Post by DrDee on 2012-05-24
I originally posted to this forum:
[http://ubuntuforums.org/showthread.php?t=1971177]("http://ubuntuforums.org/showthread.php?t=1971177")

Here is my modified repost:
I also have a system issue using my new install of** Kubuntu** 12.04 64 bit with my HP 4050TN, which is connected via parallel port. I can print from Libre Office, but not Thunderbird email or FireFox as it prints the email header and then only the first four lines. Then I get three vertical lines on the left and a new boxed error page that reports this:

HP LaserJet 4050 Series
2014.116 0
551662132

I also need this printer with my system and this seems to be a bug. I see some people don't see an issue with KDE, but I have had an issue for quite some time.  Can some one take action as this seems quite serious?

---

### Post by DMJ on 2012-05-25
> **DrDee said:**
> I originally posted to this forum:
[http://ubuntuforums.org/showthread.php?t=1971177]("http://ubuntuforums.org/showthread.php?t=1971177")

Here is my modified repost:
I also have a system issue using my new install of** Kubuntu** 12.04 64 bit with my HP 4050TN, which is connected via parallel port. I can print from Libre Office, but not Thunderbird email or FireFox as it prints the email header and then only the first four lines. Then I get three vertical lines on the left and a new boxed error page that reports this:

HP LaserJet 4050 Series
2014.116 0
551662132

I also need this printer with my system and this seems to be a bug. I see some people don't see an issue with KDE, but I have had an issue for quite some time.  Can some one take action as this seems quite serious?


I don't have any problems in KDE, but this appears to be a different bug from what I'm experiencing. I can't print from any application.

I haven't tried firefox or t-bird under kde though, because I never use them.

---

### Post by ratcheer on 2012-05-25
> **jitro72 said:**
> Hope CUPS 1.5.3 will resolve this situation. Does anybody know when it could be expected?

This may be slightly off topic, but I can report that I have gotten my Canon MP620 working in Siduction 12.1 (a derivative of Debian sid), which is using CUPS 1.5.3. It was not easy, because CUPS detected the printer, but not its address. So I followed some instructions in the CUPS doc to add the printer to my hosts file and add its MAC address and IP address to dhcpd.conf. Viola!

I find it mildly amusing that this offshoot of Debian testing running the very latest 3.4 Linux kernel allows me to use my printer while the "thoroughly tested" Ubuntu LTS does not.

Tim

---

### Post by ratcheer on 2012-05-25
CUPS 1.5.3 is now in proposed release status for Precise, as of about 14 hours ago.

[https://launchpad.net/ubuntu/+source/cups/1.5.3-0ubuntu1](https://launchpad.net/ubuntu/+source/cups/1.5.3-0ubuntu1)

Tim

---

### Post by ratcheer on 2012-05-25
I have managed to solve my 12.04 printing problems with things from two PPA's.

First, I found package cups-bjnp (which seems to stand for "bubble jet network printer") in Robbie Williamson's PPA. After installing it, I was able to setup and use my printer with a CUPS driver named "CUPS+Gutenprint v5.2.8-pre".

Then, I came across an answer on AskUbuntu that led me to take a closer look at Michael Gruz's PPA's. One of them had been recommended to me previously, but when I tried to install from it, apt-get failed. But today, I dug into his page and found that he has several PPA's, one of which is named "Canon printer driver daily". It has some drivers for Precise. So, I loaded that PPA and was able to find and install driver "Canon MP630 series Ver.3.00". The package name is "cnijfilter-mp630series". And it works, too.

So, I have been wrong about 12.04 and CUPS 1.5.2. They can be made to work, although certainly not "out of the box". 

Tim

---

### Post by robertmarik on 2012-05-26
The update from proposed did not solve my problem. This is my printers.conf file. Are the lines like "Reason cups-ipp-missing-printer-state-reasons" O.K.? This appears with red sign if I click Printers->propertises->ink/tonel level.

Robert


# Printer configuration file for CUPS v1.5.3
# Written by cupsd
# DO NOT EDIT THIS FILE WHEN CUPSD IS RUNNING
<Printer hp-p2015d>
UUID urn:uuid:bc5a0f77-b385-38d0-6bc4-67fabaf4bad3
Info HP LaserJet p2015d
Location knihovna
MakeModel HP LaserJet p2015d Series, hpcups 3.12.2
DeviceURI [http://195.178.75.62:1010/PS-0F00BD-U3](http://195.178.75.62:1010/PS-0F00BD-U3)
State Idle
StateTime 1338040776
Reason cups-ipp-conformance-failure-report
Reason cups-ipp-missing-printer-state-reasons
Reason cups-ipp-missing-validate-job
Type 36892
Accepting Yes
Shared No
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
OpPolicy default
ErrorPolicy retry-job
</Printer>
<DefaultPrinter Xerox-WorkCentre-M20>
UUID urn:uuid:301c0988-96a3-3530-4f1e-835167fc6188
Info Xerox WorkCentre M20
Location 
MakeModel Xerox WorkCentre M20 Foomatic/Postscript
DeviceURI ipp://195.178.75.62:1010/PS-0F00BD-P1
State Idle
StateTime 1338040779
Reason cups-ipp-conformance-failure-report
Reason cups-ipp-missing-printer-state-reasons
Reason cups-ipp-missing-validate-job
Type 8433684
Accepting Yes
Shared Yes
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
OpPolicy default
ErrorPolicy retry-job
</Printer>

---

### Post by DMJ on 2012-05-27
I haven't been able to find any bug reports on launchpad, so I posted one myself. 

[https://bugs.launchpad.net/ubuntu/+source/cups/+bug/1004977](https://bugs.launchpad.net/ubuntu/+source/cups/+bug/1004977)

---

### Post by Snoopy_5_1 on 2012-05-27
Hello ratcheer,

please can you explain in detail what you did?
For example what you exactly installed and what orders you used?

I just understand I solved the problem ;)

Sry but I am kind of a newbie but I need to print ;)

---

### Post by ratcheer on 2012-05-27
@Snoopy_5_1, two of the three things I did were specific for Canon printers.

First, I downloaded and installed package cups-bjnp from Launchpad. I do not know exactly what it does, but it did give me network detection of my Canon MP620 printer.

[https://launchpad.net/~robbiew/+archive/cups-bjnp]("https://launchpad.net/%7Erobbiew/+archive/cups-bjnp")

However, the detection did not seem to know the printer's IP address. So, I followed some instructions I found in the CUPS documentation:

> **Configuring the IP Address**

  When you first install a network printer or print server on your LAN,  you need to set the Internet Protocol ("IP") address. Most higher-end  "workgroup" printers allow you to set the address through the printer  control panel. However, if you have many printers you will want to  assign the addresses remotely - this makes administration a bit easier  and avoids assigning duplicate addresses accidentally.
  To setup your printer or print server for remote address assignment,  you'll need the Ethernet Media Access Control ("MAC") address, also  sometimes called a node address, and the IP address you want to use for  the device. The Ethernet MAC address can often be found on the printer  test page or bottom of the print server.

**Configuring the IP Address Using DHCP**

  The DHCP protocol is the usual way of setting the IP address of a printer on a managed network. Using the standard dhcpd(8) program supplied with UNIX you simply need to add a line to the /etc/dhcpd.conf file:

  host *hostname* 
{   hardware ethernet *mac-address*;   
fixed-address *ip-address*;
 }   

Make sure that the hostname you use is also listed in the /etc/hosts file or is registered with your DNS server.
Then, I added the printer in CUPS, selected the offered CUPS+Gutenprint driver, tested it, and it worked.

But, I did not really care for that Gutenprint driver. So, after a lot of digging, I found this PPA and added it:

[https://launchpad.net/~michael-gruz/+archive/canon-trunk]("https://launchpad.net/%7Emichael-gruz/+archive/canon-trunk")

Then, I installed the driver from that PPA for my printer, added the printer again, and selected that driver. I tested it, and it also worked. So now I have not one, but two instances of the same printer installed and working, each using a different driver.

I hope this helps you. Good luck,
Tim

---

### Post by Snoopy_5_1 on 2012-05-30
Hy Ratcheer thanks for you answer.
So I have an Canon printer ;) That is the good news *g*
But it is not an Network printer. Its attached via usb.
So do I need to install cups-bjnp?

So I think I will test the ppa you found for my printer?

---

### Post by ratcheer on 2012-05-30
> **Snoopy_5_1 said:**
> Hy Ratcheer thanks for you answer.
So I have an Canon printer ;) That is the good news *g*
But it is not an Network printer. Its attached via usb.
So do I need to install cups-bjnp?

So I think I will test the ppa you found for my printer?

I think you should not need the bjnp component for a USB-connected printer. I don't see why you would, anyway.

Tim

---

### Post by Snoopy_5_1 on 2012-05-30
So what driver I need do get my printer work?
This one?
[https://launchpad.net/~michael-gruz/+archive/canon-trunk]("https://launchpad.net/%7Emichael-gruz/+archive/canon-trunk")
Or maybe I just wait a litte bit untill they get it worked generel on ubuntu?

---

### Post by JohnAspinall on 2012-05-30
I've got a Pixma 610 that stopped working under Ubuntu 12.4.
It has worked in every previous release back to 9.10.

Looking in /var/log/cups/error_log I see this:
D [30/May/2012:19:45:42 -0400] [Job 386] MP610_series: error while loading shared libraries: libpopt.so.0: cannot open shared object file: No such file or directory

The failure symptoms are very similar to other ones mentioned on this thread: the job appears to spool correctly, but then nothing happens, and eventually the job is killed as "printer unresponsive".

I have force-loaded the libpopt0 package, that isn't the problem.  Instead, I suspect that part of the printer chain-of-filters is now looking for libpopt in the wrong place.

Is this driver install worth a try?

(It's a USB-connected printer, not network.)

And here's the culprit:

```
$ cd /usr/lib/cups/filter
$ ldd pstocanonij | grep popt
	libpopt.so.0 => not found

```
 but...
```
$ ls /lib/x86_64-linux-gnu/*popt*
/lib/x86_64-linux-gnu/libpopt.so.0  /lib/x86_64-linux-gnu/libpopt.so.0.0.0

```

 but...
pstocanonij is a 32-bit executable!  So, question now is: do I
(a) look for a 64-bit pstocanonij, or
(b) find a 32-bit libpopt?

---

### Post by ratcheer on 2012-05-30
> **Snoopy_5_1 said:**
> So what driver I need do get my printer work?
This one?
[https://launchpad.net/~michael-gruz/+archive/canon-trunk]("https://launchpad.net/%7Emichael-gruz/+archive/canon-trunk")
Or maybe I just wait a litte bit untill they get it worked generel on ubuntu?

I don't know, but I doubt that Ubuntu will ever carry a set of Canon printer drivers. At least not for the ones Canon does not support on Linux, which includes my MP620.

What printer do you have? What Ubuntu release? 32 or 64 bit?

Tim

---

### Post by jitro72 on 2012-05-31
Proposed now works! :)

---

### Post by crf on 2012-05-31
I can print now.
I had to delete and remake the printer, in system-config-printer and choose **AppSocket/JetDirect** for the connection. 

Normally the default is **ipp** connection. But my printer, apparently, has errors in its ipp implementation, which makes cups write **ipp-conformance-failure-report** and give up.

[https://bugs.launchpad.net/ubuntu/+source/cups/+bug/992982]("https://bugs.launchpad.net/ubuntu/+source/cups/+bug/992982")
[http://www.cups.org/str.php?L4079]("http://www.cups.org/str.php?L4079")

---

### Post by Snoopy_5_1 on 2012-06-05
> **ratcheer said:**
> I don't know, but I doubt that Ubuntu will ever carry a set of Canon printer drivers. At least not for the ones Canon does not support on Linux, which includes my MP620.

What printer do you have? What Ubuntu release? 32 or 64 bit?

Tim

Hy [ratcheer]("http://ubuntuforums.org/member.php?u=848769") and thanks again for you help.
I have an Canon i560x and an 64 bit ubuntu,

I also tried that delete and reinstall you printer think which does not worked ;)

---

### Post by NLinTKO on 2012-06-17
In case someone is still following this thread: today I was able to print again using my Canon PIXMA iP3500 printer. I read an article stating that Gutenprint 5.2.8 was released, having improved printing features for Canon printers. I installed this, selected the correct Canon printer driver that came with it, and was then able to print a test page, an email (so only normal text) and a map from a website. I was not able to do any of this since I had installed Ubuntu 12.04 LTS (64 bit version).

---

### Post by Mopar1973Man on 2012-06-17
Strange but true... Some how the upgrade got trigger on my machine and so I proceeded with the update to 12.04. I was worried that my Canon MF4150 would die since it was quite the project to get it working in 11.10. Well guess what made the update no problems and Cannon printer is still working fine.

---

### Post by Snoopy_5_1 on 2012-06-18
> **NLinTKO said:**
> In case someone is still following this thread: today I was able to print again using my Canon PIXMA iP3500 printer. I read an article stating that Gutenprint 5.2.8 was released, having improved printing features for Canon printers. I installed this, selected the correct Canon printer driver that came with it, and was then able to print a test page, an email (so only normal text) and a map from a website. I was not able to do any of this since I had installed Ubuntu 12.04 LTS (64 bit version).

One Question, how do you install Gutenprint 5.2.8!
Can you explain it to an newby step by step please ;)

---

### Post by ratcheer on 2012-06-19
> **Snoopy_5_1 said:**
> One Question, how do you install Gutenprint 5.2.8!
Can you explain it to an newby step by step please ;)

sudo apt-get install printer-driver-gutenprint

Tim

---

### Post by Snoopy_5_1 on 2012-06-19
it seams I allready have the new on:
driver and model: Canon i560 - CUPS+Gutenprint v5.2.8-pre1

Is it strange that Cups and Gutenprint is installed?
I really hope I can print again sometime ;)

---

### Post by shvman on 2012-06-25
I have a Canon s750 printer that was working fine on my laptop using 11.10 (32).  It uses the driver specified for the s800 (CUPS+gutenprint v5.2.7 Simplified) and works perfectly.    I installed 12.04 (x64) on my desktop and have not been able to get the same printer to work correctly using the Canon s750 driver (CUPS+gutenprint v5.2.8 pre1); however, the Canon s630 Foomatic/bj8XXYYZ.upp works most of the time.   Something has definitely changed from 11.10 to 12.04.  Hope there's a solution soon.

---

### Post by merlinus on 2012-07-02
Despite all the updates to 12.04, I still cannot print over my network using ipp:// (or from a vm running windows using [http://)](http://)), both with serveripaddress:631/printers/HP-LaserJet-4

This worked perfectly until 12.04.

Help greatly appreciated!!!

---

### Post by aikishugyo on 2012-07-06
I've read the entire theread wihtout seeing a single lines from CUPS logs anywhere. Very odd!
If something does not work in CUPS, the first thing to do should be to enable debugging in the log file and then see what is the result.
The reason is simple:
- either it is a problem with CUPS
- or it is a problem with gutenprint
- or the Canon driver

At least for the first two, this should be clear from the logs. As the maintainer of the Canon backend for the gutenprint project, I am very much interested in resolving bugs in the Canon backend, but this is impossible when the bugs are not clearly isolated.

Currently, I have some bugs proven for the pro series, and I am trying to collect useable information on possible bugs with other Canon devices.

Regards,
Gernot Hassenpflug

---

### Post by violinuxer on 2012-07-08
> **aikishugyo said:**
> I've read the entire theread wihtout seeing a single lines from CUPS logs anywhere. Very odd!

Just thought I would add my voice to the crowd...

I have a Canon iP4000. I just posted a thread [here]("http://ubuntuforums.org/showthread.php?t=2020637") about some issues i've been having. I seem to be having issues at the kernel level. If anyone is interested, I posted some errors I found in my cups log file

If anyone has been getting this in their syslogs, I would be interested to hear about it:

can't set config #1, error -110

This happens with my server and  desktop when connecting the printer. Both are running precise. Any ideas?

Details can be found in the above thread.

violinuxer

---

### Post by abdulcanbaz on 2012-07-11
My printer is Xerox Phaser 3140, it's connected to my USR9108 router and was working smoothly on http:// until this bloody 12.04! It's been months, I removed and re-installed almost everything regarding the printer, tried past versions and now there's an update error about the cups server due to some missing dependencies. I gave up...

---

### Post by HowardJZ on 2012-07-11
Linux Mint 13 Cinnamon Flavored here.

I had the same kinds of problems using LM13. There was a post on the LM13 forums that solved it for me. -- Since LM13 is based on U12.04 maybe the same solution will work here.

Sorry. I did not preserve a link to the LM forum post. My notes say:

> The menu system for configuring printers is not connected to the correct application.

At the command line say: system-config-printer

When the application comes up, the Help->About should say 1.3.8 if you your machine has all updates applied (on 11-Jul-2012).

Use the application to configure printers.


Hope this helps

---

### Post by rad_sci_guy on 2012-08-03
I have CUPS 1.5.3 installed on my Ubuntu 12.04 server and It's still broken on my system. I had a backup of my old 8.04 server and I booted into the backup.  I was able to print on CUPS 1.3.7.  The printer settings are identical for both versions so there's defintely still a problem with the new CUPS.

I'm using an HP laserjet 1020 attached with usb.

---

### Post by rickm1945 on 2012-08-03
Just to add my two cents worth if anyone is interested. I have a HP 6500 wireless that prints scans and I can even send faxes from my laptop via the wireless network. If I were using a CAnon printer and having all the problems I have been reading about in this thread I thin I would change printer brands. I'm not a big fan of HP by any means, there computers and laptops suck, but they do support Linux  with their printers. The HPLIP is a fantastic toolbox for use in Ubuntu and works fine no hassles. Hope this might give somebody an idea for hassle free printing.

---

### Post by kf7nnz on 2012-08-04
> **aikishugyo said:**
> I've read the entire theread wihtout seeing a single lines from CUPS logs anywhere. Very odd!
If something does not work in CUPS, the first thing to do should be to enable debugging in the log file and then see what is the result.
The reason is simple:
- either it is a problem with CUPS
- or it is a problem with gutenprint
- or the Canon driver

At least for the first two, this should be clear from the logs. As the maintainer of the Canon backend for the gutenprint project, I am very much interested in resolving bugs in the Canon backend, but this is impossible when the bugs are not clearly isolated.

Currently, I have some bugs proven for the pro series, and I am trying to collect useable information on possible bugs with other Canon devices.

Regards,
Gernot Hassenpflug

Hello Gernot,

I would be happy to post some log info if it will help, but how do I turn on debugging for CUPS?  Thanks!

Canon MF8050cn, network connected, 12.04 64-bit.

Ron

> **rickm1945 said:**
> Just to add my two cents worth if anyone is interested. I have a HP 6500 wireless that prints scans and I can even send faxes from my laptop via the wireless network. If I were using a CAnon printer and having all the problems I have been reading about in this thread I thin I would change printer brands. I'm not a big fan of HP by any means, there computers and laptops suck, but they do support Linux  with their printers. The HPLIP is a fantastic toolbox for use in Ubuntu and works fine no hassles. Hope this might give somebody an idea for hassle free printing.
Yeah, that's real helpful! FWIW, HP printers (at least the inkjet variety) suck as bad as their computers and laptops. And what do you suggest I do with my Canon color laser? Use it as a boat anchor?

---

### Post by ratcheer on 2012-08-05
@kf7nnz, on the main CUPS web interface page, just click the View Logs and select Error Log, or something like that (I am not at the PC where I use CUPS, right now). It will give you plenty of info that could be used for a bug report.

Also, is your printer direct connected or networked? If it is networked, you probably need package cups-bjnp, or something closely related to it. I had to get it from a Launchpad PPA.

Tim

---

### Post by kf7nnz on 2012-08-05
@ratcheer - How do I get to the main CUPS web interface page? I tried [http://localhost:631](http://localhost:631) but I don't see anything about logs on that page.

My printer is networked. I saw the suggestion you had posted earlier re: cups-bjnp. I tried adding that PPA but I got an error to the effect of "not found" (don't remember exactly as that was last night).

ETA: Just tried it again. I had misspelled "robbiew". The PPA added but when I tried "sudo apt-get install cups-bjnp" I get "E: Unable to locate package cups-bjnp"

I downloaded a Linux driver from Canon. It is in the RPM package format. I installed a package called alien to convert the RPMs to DEB format. Everything seems to go smoothly - Find network printer finds and correctly identifies the printer (Canon-MF8050), and find driver finds and correctly identifies the driver (Canon-MF8000-UFRII-LT). I am able to ping the printer and get a reply. But when I click Print Test Page, Printer State changes from "Idle" to "Idle - /usr/lib/cups/filter/pstoufr2cpca failed".

---

### Post by ratcheer on 2012-08-06
> **kf7nnz said:**
> @ratcheer - How do I get to the main CUPS web interface page? I tried [http://localhost:631](http://localhost:631) but I don't see anything about logs on that page.


Sorry, like I said, I was not at my PC that uses CUPS when I wrote that message.

From the page you referenced, click on the Administration tab. Then  in the upper right area of the screen, there should be a button labeled "View error log".

Tim

---

### Post by mikasam on 2012-08-06
There is a printing problem, since the latest updates in Ubuntu 12.04. My Canon Printer MP 270 and now since a few days it only prints incomplete pages (half of it). This also applies for testpage printing. Same of the updates do not work.
Printing was working now for me since Ubuntu 10.10 (always same printer).
Printer is OK works under Win 7.

---

### Post by Snoopy_5_1 on 2012-08-06
Since I still get some printing problems here is my erro log.
I hope that will help somehow
My problem is, as I posted before that the printer either wont print at all he started but than dont prin anythink (automatic resolution)
Or he just print the page very small wenn I selcted 300x300 dpi resolution

I am glad that we make some progress here

```

W [06/Aug/2012:17:41:10 +0200] failed to CreateProfile:  org.freedesktop.ColorManager.AlreadyExists:profile id 'Canon-i560-Gray..' already exists 
W [06/Aug/2012:17:41:10 +0200] failed to CreateProfile: org.freedesktop.ColorManager.AlreadyExists:profile id 'Canon-i560-RGB..' already exists 
W [06/Aug/2012:17:41:10 +0200] failed to CreateDevice: org.freedesktop.ColorManager.AlreadyExists:device id 'cups-Canon-i560' already exists 
W [06/Aug/2012:17:41:10 +0200] failed to CreateProfile: org.freedesktop.ColorManager.AlreadyExists:profile id 'Generic-PCL-Laser-Printer-Gray..' already exists 
W [06/Aug/2012:17:41:10 +0200] failed to CreateDevice: org.freedesktop.ColorManager.AlreadyExists:device id 'cups-Generic-PCL-Laser-Printer' already exists 
W [06/Aug/2012:17:41:10 +0200] failed to CreateProfile: org.freedesktop.ColorManager.AlreadyExists:profile id 'Generic-PCL-Laser-Printer-Gray..' already exists 
W [06/Aug/2012:17:41:10 +0200] failed to CreateDevice: org.freedesktop.ColorManager.AlreadyExists:device id 'cups-Generic-PCL-Laser-Printer' already exists 
W [06/Aug/2012:17:41:10 +0200] failed to CreateProfile: org.freedesktop.ColorManager.AlreadyExists:profile id 'PDF-Gray..' already exists 
W [06/Aug/2012:17:41:10 +0200] failed to CreateProfile: org.freedesktop.ColorManager.AlreadyExists:profile id 'PDF-RGB..' already exists 
W [06/Aug/2012:17:41:10 +0200] failed to CreateDevice: org.freedesktop.ColorManager.AlreadyExists:device id 'cups-PDF' already exists

```

---

### Post by kf7nnz on 2012-08-07
Okay I have copied the error log from a job that failed. I hope the person who was working on the Canon issue that asked to see a log reads this - I would like to be able to print! 

ETA: I also tried lpr -H 192.168.1.200:9100 /var/log/cups/error_log 
The result I get is lpr: Error - scheduler not responding. 

```

W [04/Aug/2012:18:03:09 -0700] failed to CreateProfile: org.freedesktop.ColorManager.AlreadyExists:profile id 'Canon-MF8000-UFRII-LT-Gray..' already exists
W [04/Aug/2012:18:03:09 -0700] failed to CreateProfile: org.freedesktop.ColorManager.AlreadyExists:profile id 'Canon-MF8000-UFRII-LT-RGB..' already exists
W [04/Aug/2012:18:03:09 -0700] failed to CreateDevice: org.freedesktop.ColorManager.AlreadyExists:device id 'cups-Canon-MF8000-UFRII-LT' already exists
W [04/Aug/2012:18:03:09 -0700] failed to CreateProfile: org.freedesktop.ColorManager.AlreadyExists:profile id 'Canon-MF8000-UFRII-LT-Gray..' already exists
W [04/Aug/2012:18:03:09 -0700] failed to CreateProfile: org.freedesktop.ColorManager.AlreadyExists:profile id 'Canon-MF8000-UFRII-LT-RGB..' already exists
W [04/Aug/2012:18:03:09 -0700] failed to CreateDevice: org.freedesktop.ColorManager.AlreadyExists:device id 'cups-Canon-MF8000-UFRII-LT' already exists
W [04/Aug/2012:18:03:09 -0700] failed to CreateProfile: org.freedesktop.ColorManager.AlreadyExists:profile id 'Canon-MF8000-UFRII-LT-Gray..' already exists
W [04/Aug/2012:18:03:09 -0700] failed to CreateProfile: org.freedesktop.ColorManager.AlreadyExists:profile id 'Canon-MF8000-UFRII-LT-RGB..' already exists
W [04/Aug/2012:18:03:09 -0700] failed to CreateDevice: org.freedesktop.ColorManager.AlreadyExists:device id 'cups-Canon-MF8000-UFRII-LT' already exists
E [04/Aug/2012:18:03:12 -0700] [Job 8] Job stopped due to filter errors; please consult the error_log file for details.
D [04/Aug/2012:18:03:12 -0700] [Job 8] The following messages were recorded from 18:03:12 to 18:03:12
D [04/Aug/2012:18:03:12 -0700] [Job 8] Adding start banner page "none".
D [04/Aug/2012:18:03:12 -0700] [Job 8] Adding end banner page "none".
D [04/Aug/2012:18:03:12 -0700] [Job 8] File of type application/vnd.cups-pdf-banner queued by "ron".
D [04/Aug/2012:18:03:12 -0700] [Job 8] hold_until=0
D [04/Aug/2012:18:03:12 -0700] [Job 8] Queued on "Canon-MF8000-UFRII-LT" by "ron".
D [04/Aug/2012:18:03:12 -0700] [Job 8] job-sheets=none,none
D [04/Aug/2012:18:03:12 -0700] [Job 8] argv[0]="Canon-MF8000-UFRII-LT"
D [04/Aug/2012:18:03:12 -0700] [Job 8] argv[1]="8"
D [04/Aug/2012:18:03:12 -0700] [Job 8] argv[2]="ron"
D [04/Aug/2012:18:03:12 -0700] [Job 8] argv[3]="Test Page"
D [04/Aug/2012:18:03:12 -0700] [Job 8] argv[4]="1"
D [04/Aug/2012:18:03:12 -0700] [Job 8] argv[5]="job-uuid=urn:uuid:f5f428f6-18b0-3f4a-4448-f55cf2f83d77 job-originating-host-name=localhost time-at-creation=1344128592 time-at-processing=1344128592"
D [04/Aug/2012:18:03:12 -0700] [Job 8] argv[6]="/var/spool/cups/d00008-001"
D [04/Aug/2012:18:03:12 -0700] [Job 8] envp[0]="CUPS_CACHEDIR=/var/cache/cups"
D [04/Aug/2012:18:03:12 -0700] [Job 8] envp[1]="CUPS_DATADIR=/usr/share/cups"
D [04/Aug/2012:18:03:12 -0700] [Job 8] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"
D [04/Aug/2012:18:03:12 -0700] [Job 8] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [04/Aug/2012:18:03:12 -0700] [Job 8] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"
D [04/Aug/2012:18:03:12 -0700] [Job 8] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"
D [04/Aug/2012:18:03:12 -0700] [Job 8] envp[6]="CUPS_SERVERROOT=/etc/cups"
D [04/Aug/2012:18:03:12 -0700] [Job 8] envp[7]="CUPS_STATEDIR=/var/run/cups"
D [04/Aug/2012:18:03:12 -0700] [Job 8] envp[8]="HOME=/var/spool/cups/tmp"
D [04/Aug/2012:18:03:12 -0700] [Job 8] envp[9]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [04/Aug/2012:18:03:12 -0700] [Job 8] envp[10]="SERVER_ADMIN=root@ubRMHI"
D [04/Aug/2012:18:03:12 -0700] [Job 8] envp[11]="SOFTWARE=CUPS/1.5.3"
D [04/Aug/2012:18:03:12 -0700] [Job 8] envp[12]="TMPDIR=/var/spool/cups/tmp"
D [04/Aug/2012:18:03:12 -0700] [Job 8] envp[13]="USER=root"
D [04/Aug/2012:18:03:12 -0700] [Job 8] envp[14]="CUPS_SERVER=/var/run/cups/cups.sock"
D [04/Aug/2012:18:03:12 -0700] [Job 8] envp[15]="CUPS_ENCRYPTION=IfRequested"
D [04/Aug/2012:18:03:12 -0700] [Job 8] envp[16]="IPP_PORT=631"
D [04/Aug/2012:18:03:12 -0700] [Job 8] envp[17]="CHARSET=utf-8"
D [04/Aug/2012:18:03:12 -0700] [Job 8] envp[18]="LANG=en_US.UTF-8"
D [04/Aug/2012:18:03:12 -0700] [Job 8] envp[19]="PPD=/etc/cups/ppd/Canon-MF8000-UFRII-LT.ppd"
D [04/Aug/2012:18:03:12 -0700] [Job 8] envp[20]="RIP_MAX_CACHE=128m"
D [04/Aug/2012:18:03:12 -0700] [Job 8] envp[21]="CONTENT_TYPE=application/vnd.cups-pdf-banner"
D [04/Aug/2012:18:03:12 -0700] [Job 8] envp[22]="DEVICE_URI=socket://192.168.1.200:9100"
D [04/Aug/2012:18:03:12 -0700] [Job 8] envp[23]="PRINTER_INFO=Canon MF8000 UFRII LT"
D [04/Aug/2012:18:03:12 -0700] [Job 8] envp[24]="PRINTER_LOCATION=192.168.1.200"
D [04/Aug/2012:18:03:12 -0700] [Job 8] envp[25]="PRINTER=Canon-MF8000-UFRII-LT"
D [04/Aug/2012:18:03:12 -0700] [Job 8] envp[26]="PRINTER_STATE_REASONS=none"
D [04/Aug/2012:18:03:12 -0700] [Job 8] envp[27]="CUPS_FILETYPE=document"
D [04/Aug/2012:18:03:12 -0700] [Job 8] envp[28]="FINAL_CONTENT_TYPE=printer/Canon-MF8000-UFRII-LT"
D [04/Aug/2012:18:03:12 -0700] [Job 8] envp[29]="AUTH_I****"
D [04/Aug/2012:18:03:12 -0700] [Job 8] Started filter /usr/lib/cups/filter/bannertopdf (PID 1851)
D [04/Aug/2012:18:03:12 -0700] [Job 8] Started filter /usr/lib/cups/filter/pdftopdf (PID 1852)
D [04/Aug/2012:18:03:12 -0700] [Job 8] Started filter /usr/lib/cups/filter/pdftops (PID 1853)
D [04/Aug/2012:18:03:12 -0700] [Job 8] Started filter /usr/lib/cups/filter/pstoufr2cpca (PID 1854)
D [04/Aug/2012:18:03:12 -0700] [Job 8] Started backend /usr/lib/cups/backend/socket (PID 1855)
D [04/Aug/2012:18:03:12 -0700] [Job 8] pdftops - copying to temp print file "/tmp/0073d50250571"
D [04/Aug/2012:18:03:12 -0700] [Job 8] STATE: +connecting-to-device
D [04/Aug/2012:18:03:12 -0700] [Job 8] Looking up "192.168.1.200"...
D [04/Aug/2012:18:03:12 -0700] [Job 8] hrDeviceDesc="Canon MF8050"
D [04/Aug/2012:18:03:12 -0700] [Job 8] prtGeneralCurrentLocalization type is 5, expected 2!
D [04/Aug/2012:18:03:12 -0700] [Job 8] backendWaitLoop(snmp_fd=5, addr=0x7faaee3669b8, side_cb=0x7faaec828180)
D [04/Aug/2012:18:03:12 -0700] [Job 8] Using image rendering resolution 300 dpi
D [04/Aug/2012:18:03:12 -0700] [Job 8] Started filter pdftops (PID 1856)
D [04/Aug/2012:18:03:12 -0700] [Job 8] Started filter pstops (PID 1857)
D [04/Aug/2012:18:03:12 -0700] [Job 8] Page = 612x792; 14,14 to 598,778
D [04/Aug/2012:18:03:12 -0700] [Job 8] slow_collate=0, slow_duplex=0, slow_order=0
D [04/Aug/2012:18:03:12 -0700] [Job 8] Before copy_comments - %!PS-Adobe-3.0
D [04/Aug/2012:18:03:12 -0700] [Job 8] %!PS-Adobe-3.0
D [04/Aug/2012:18:03:12 -0700] [Job 8] %Produced by poppler pdftops version: 0.18.4 (http://poppler.freedesktop.org)
D [04/Aug/2012:18:03:12 -0700] [Job 8] %%LanguageLevel: 2
D [04/Aug/2012:18:03:12 -0700] [Job 8] %%DocumentSuppliedResources: (atend)
D [04/Aug/2012:18:03:12 -0700] [Job 8] %%DocumentMedia: plain 612 792 0 () ()
D [04/Aug/2012:18:03:12 -0700] [Job 8] %%BoundingBox: 0 0 612 792
D [04/Aug/2012:18:03:12 -0700] [Job 8] %%Pages: 1
D [04/Aug/2012:18:03:12 -0700] [Job 8] %%EndComments
D [04/Aug/2012:18:03:12 -0700] [Job 8] Before copy_prolog - %%BeginDefaults
D [04/Aug/2012:18:03:12 -0700] [Job 8] Before copy_setup - %%BeginSetup
D [04/Aug/2012:18:03:12 -0700] [Job 8] Before page loop - %%Page: 1 1
D [04/Aug/2012:18:03:12 -0700] [Job 8] Copying page 1...
D [04/Aug/2012:18:03:12 -0700] [Job 8] pagew = 583.7, pagel = 763.7
D [04/Aug/2012:18:03:12 -0700] [Job 8] bboxx = 0, bboxy = 0, bboxw = 612, bboxl = 792
D [04/Aug/2012:18:03:12 -0700] [Job 8] PageLeft = 14.2, PageRight = 597.8
D [04/Aug/2012:18:03:12 -0700] [Job 8] PageTop = 777.8, PageBottom = 14.2
D [04/Aug/2012:18:03:12 -0700] [Job 8] PageWidth = 612.0, PageLength = 792.0
D [04/Aug/2012:18:03:12 -0700] [Job 8] Wrote 1 pages...
D [04/Aug/2012:18:03:12 -0700] [Job 8] PID 1856 (pdftops) exited with no errors.
D [04/Aug/2012:18:03:12 -0700] [Job 8] PID 1857 (pstops) exited with no errors.
D [04/Aug/2012:18:03:12 -0700] [Job 8] End of messages
D [04/Aug/2012:18:03:12 -0700] [Job 8] printer-state=3(idle)
D [04/Aug/2012:18:03:12 -0700] [Job 8] printer-state-message="/usr/lib/cups/filter/pstoufr2cpca failed"
D [04/Aug/2012:18:03:12 -0700] [Job 8] printer-state-reasons=none
```

---

### Post by aikishugyo on 2012-08-07
I'm just posting to note that this is not a Gutenprint issue, since the driver being used for the MF8000 is the Canon-supplied driver for their UFRII protocol.

Regards,
Gernot Hassenpflug
Gutenprint project Canon backend maintainer

---

### Post by kf7nnz on 2012-08-08
Thank you, Gernot. I do still have a gutenprint issue that you could perhaps help me with (see below).  

I am happy to report that I was able to print finally. I had installed the cups-bjnp backend.  I found a thread for people having the same issue with earlier 64-bit versions of Ubuntu. They solved the problem by uninstalling the Canon .deb packages created with the alien utility, then creating a symbolic link to /usr/lib from /usr/lib64 like so:

```
sudo ln -s /usr/lib /usr/lib64
```

Then reinstall the .deb packages. I am now able to print. However, the driver doesn't seem to be the one I had originally, for instance, it doesn't show that the printer has duplex printing capabilities. I was hoping to install a better driver, like the gutenprint driver, but I don't know how. Can anyone help? Thanks!

---

### Post by vexorian on 2012-08-08
I noticed that renaming a printer (which I need so that it has the same name as when there is a windows partition in here) causes a cups misconfiguration the next time you boot.

---

### Post by aikishugyo on 2012-08-09
> **kf7nnz said:**
> Thank you, Gernot. I do still have a gutenprint issue that you could perhaps help me with (see below).  
/../
However, the driver doesn't seem to be the one I had originally, for instance, it doesn't show that the printer has duplex printing capabilities. I was hoping to install a better driver, like the gutenprint driver, but I don't know how. Can anyone help? Thanks!

Hi, glad you could print at last.
I'm afraid gutenprint, which is a dedicated inkjet driver project with incidentally some non-inkjet drivers as well, does not have support for UFRII protocol. We're pretty in need of programmers for more well-known backends, like PCL support, and if someone would reverse engineer UFRII that would certainly be appreciated, but there is no-one able to do that in the project at this point.
If your printer has emulation for PCL, or ESC/P2 or PDF or PS, for example, then you could use another driver, such as ones from foomatic (or gutenprint for ESC/P2), perhaps not with all options available, but that is largely a function of the PPD file CUPS has access to (and whether the various CUPS filters correctly set up the options).

---

### Post by ray field on 2012-08-09
when 12.04 dropped I struggled to get my Canon MP530 working -- typically a job would start and then stop halfway through a page -- until I finally got it somehow a couple of months ago. now one of the updates has broken it. now, either a job will stop halfway through a page, or the printer fails to acknowledge a job at all (a step backward from before, when at least the LED would say "PRINTING" even when it wasn't).

the HP Laserjet 1300 which I have on a print server, is working fine.

I am anxious to get rid of this Canon which has always been a pita under Linux, however I still have a package of cartridges to get through.

---

### Post by tomasrey88 on 2012-08-11
I have no idea what you just said. So, all I have to do to install my Dell 3110cn printer in Ubuntu 12.04 is just type in, " sudo ln -s /usr/lib /usr/lib64 " at the Terminal? If not, then what other steps do I take? Please tell it to me in simple step-by-step fashion for the rest of us dummies. Thanks ;0)

> **kf7nnz said:**
> Thank you, Gernot. I do still have a gutenprint issue that you could perhaps help me with (see below).  

I am happy to report that I was able to print finally. I had installed the cups-bjnp backend.  I found a thread for people having the same issue with earlier 64-bit versions of Ubuntu. They solved the problem by uninstalling the Canon .deb packages created with the alien utility, then creating a symbolic link to /usr/lib from /usr/lib64 like so:

```
sudo ln -s /usr/lib /usr/lib64
```Then reinstall the .deb packages. I am now able to print. However, the driver doesn't seem to be the one I had originally, for instance, it doesn't show that the printer has duplex printing capabilities. I was hoping to install a better driver, like the gutenprint driver, but I don't know how. Can anyone help? Thanks!

---

### Post by kf7nnz on 2012-08-11
> **tomasrey88 said:**
> I have no idea what you just said. So, all I have to do to install my Dell 3110cn printer in Ubuntu 12.04 is just type in, " sudo ln -s /usr/lib /usr/lib64 " at the Terminal? If not, then what other steps do I take? Please tell it to me in simple step-by-step fashion for the rest of us dummies. Thanks ;0)

I'm afraid I can't tell you how to do it for your printer. The steps I was talking about worked for Canon printers in 64-bit versions of Ubuntu. Have you tried installing your Dell printer through the GUI yet? Click System Settings (on the Unity taskbar) | Printing | +Add button and follow the prompts. If that doesn't work then post back here and I will try to help you if I can.

---

### Post by parrjd2 on 2012-08-13
> **ray field said:**
> when 12.04 dropped I struggled to get my Canon MP530 working -- typically a job would start and then stop halfway through a page -- until I finally got it somehow a couple of months ago. now one of the updates has broken it. now, either a job will stop halfway through a page, or the printer fails to acknowledge a job at all (a step backward from before, when at least the LED would say "PRINTING" even when it wasn't).

the HP Laserjet 1300 which I have on a print server, is working fine.

I am anxious to get rid of this Canon which has always been a pita under Linux, however I still have a package of cartridges to get through.


Possible work-around (it worked for me)
 I also have a Canon MP530 -  after upgrading to 12.04 from 11.10 I noticed my print speed slowed down noticeably (almost 5 minutes for a 1 page b&w document)!

So I tried a few 'out of the box' tests to see if I could get back to reasonable print speeds with my Canon.

 1 - Installed Fuduntu 2012-3 onto another partition;  Hooray! that same 1 page doc now printed in less than 30 seconds under Fuduntu.

 2 - went back to Ubuntu 12.04 partition and then deleted it. Then I loaded Ubuntu 11.10 onto that partition (after formatting it to ext4). Under Unity (sigh..) I printed the same 1 page doc - Great! it now prints in less than 30 seconds (very acceptable for the MP530).

3 - Final test (I like Cinnamon over Unity); installed Cinnamon onto the 11.10 system.
Next I ran the same 1 page doc print test - Yes! still under 30 seconds.

Like others I feel there are some real issues in CUPS for non HP printers under 12.04.
Not sure if you want to go back to 11.10 but it appears (at least to me) to work a lot faster than the 12.04 CUPS.... (Your mileage may vary).

Cheers, J

---

### Post by ray field on 2012-08-13
> **parrjd2 said:**
> Possible work-around (it worked for me)
 I also have a Canon MP530 -  after upgrading to 12.04 from 11.10 I noticed my print speed slowed down noticeably (almost 5 minutes for a 1 page b&w document)!

So I tried a few 'out of the box' tests to see if I could get back to reasonable print speeds with my Canon.

 1 - Installed Fuduntu 2012-3 onto another partition;  Hooray! that same 1 page doc now printed in less than 30 seconds under Fuduntu.

 2 - went back to Ubuntu 12.04 partition and then deleted it. Then I loaded Ubuntu 11.10 onto that partition (after formatting it to ext4). Under Unity (sigh..) I printed the same 1 page doc - Great! it now prints in less than 30 seconds (very acceptable for the MP530).

3 - Final test (I like Cinnamon over Unity); installed Cinnamon onto the 11.10 system.
Next I ran the same 1 page doc print test - Yes! still under 30 seconds.

Like others I feel there are some real issues in CUPS for non HP printers under 12.04.
Not sure if you want to go back to 11.10 but it appears (at least to me) to work a lot faster than the 12.04 CUPS.... (Your mileage may vary).

Cheers, J

thanks, but that's a lot of "around"! I still have a Lucid install on one of my partitions, and though I had a lot of issues with this printer there as well -- I am never buying a Canon printer again -- the last time I booted it up it was working, so I do have that as an option. plus I like Unity!

---

### Post by Culito on 2012-09-06
Just to add...
Epson Stylus on USB didn't work after upgrade.  All I had to do was go go system settings > printers, delete the printer, and re-add it.  This seemed to search for new drivers and the printer worked normally after that.

---

### Post by BicyclerBoy on 2012-09-06
Canon seem to get a bad rap..but they provide open source drivers for linux & they work.
They may deserve it for the cost of ink cartridges but not for providing good drivers.

The current ppa for canon drivers:
[https://launchpad.net/~michael-gruz/+archive/canon-trunk](https://launchpad.net/~michael-gruz/+archive/canon-trunk)

---

### Post by abexman on 2012-09-12
Im having similar issues with my Canon mx320. Was working initially, but stopped. Similar 
failed to CreateProfile:  org.freedesktop.ColorManager.AlreadyExists:profile id errors.

---

### Post by salemboot on 2012-09-27
Somebody get Conanical to roll back the package :(

---

### Post by criatura on 2012-09-28
I have Ubuntu 12.04 x64 with a tm-t20 epson thermal printer, sometimes prints, but sometimes gives me this error at cups web interface:

tm-t20-212 	Unknown 	Withheld 	2k 	1 	 stopped 
"/usr/lib/cups/filter/pstopdf failed"

Or sometimes I see that the Job is complete at the job list, but the printer doesn't print nothing.

cups logs:

W [28/Sep/2012:14:35:43 -0300] failed to CreateDevice: org.freedesktop.         ColorManager.AlreadyExists:device id 'cups-tm-t20' already exists
W [28/Sep/2012:14:35:43 -0300] failed to CreateProfile: org.freedesktop.        ColorManager.AlreadyExists:profile id 'tm-t20-Gray..' already exists
W [28/Sep/2012:14:35:43 -0300] failed to CreateDevice: org.freedesktop.         ColorManager.AlreadyExists:device id 'cups-tm-t20' already exists

Sometimes it cut the paper, sometimes not. 

I installed the official drivers provided by Epson.

---

### Post by salemboot on 2012-09-30
Don't install any PPA for the drivers.

Click the Cog up in the right-hand corner and select Printers.

Turn on the printer and make sure it is connected.

When the Printers windows appears, click +Add and wait a few minutes.

Your printer should appear within the configuration wizard.  Mine did and its an Canon MX330.

Click the defaults and continue on.  Cups should identify your printer.  I saw a few other models in the list.

I was able to successfully print a test page afterwards.

---

### Post by aikishugyo on 2012-09-30
The printing system in recent linux versions, and MacOSX consistes of:
1) CUPS, which has some core backends and filters;
2) a batch of filters and backends that used to be in CUPS but are not maintained by Openprinting.org (like pstopdf);
3) printer drivers, like gutenprint, or the Canon drivers people download from the PPA.
4) PPD files, like those from gutenprint (for the printers supported in gutenprint), generic ones (for printers that handle PS, for example) or the Foomatic project.

CUPS shows the available PPDs, and the information displayed also shows which driver is used (e.g., generic PCL or PS, or gutenprint, etc.).

A lot of the errors reported are not actually in CUPS, but in the print filters that CUPS no longer maintains. So the debug output of CUPS should be set and consulted to ascertain what exactly the error is owing to.

---

### Post by ejoftheweb on 2012-10-02
I do not know if this is the same bug. 

I have a lexmark CD543 laser printer, it has been working fine under 10.04 but since upgrading to 12.04 it will only print one job.

First job of the day prints fine. 

Next job goes through the spooler and shows as "completed", with the right file size, but nothing happens at the printer. No error shows.

To print, first reboot. This is a pain, so I now find that restarting cups does it -  ```
sudo restart cups
``` 

But restarting cups for every job is hardly a decent solution.

---

### Post by JeremySchubert on 2012-10-03
had the same issue, printer would install but then would not print, giving the message "The printer is busy".  Found the following fix on  another website, it worked like a charm for me.

It worked the only other thing i had to do was change the protocol from  line printer daemon to HP Jetdirect - socket. Then i connected by the IP  address and worked.

---

### Post by dragonfly41 on 2012-10-12
My HP LaserJet 2100M - which previously worked reliably on ubuntu 10.10 - and windows in dual boot - is now not even seen by ubuntu 12.04.1 (installed via upgrades).

"no local printers found" in printers.

I also want to add Canon ip2600 as a second printer (not available today for testing). I've added this in case Canon ip2600 is also not found.

[https://launchpad.net/~michael-gruz/+archive/canon-trunk](https://launchpad.net/~michael-gruz/+archive/canon-trunk)

sudo add-apt-repository ppa:michael-gruz/canon-trunk

Printers are attached via USB port

Is there any workaround?

[Edit]

I installed HPLIP
HP Linux Imaging and Printing System (ver. 3.12.2)
Printer/Fax Setup Utility ver. 9.0


and this utility reports .
[COLOR=Red]
error: No devices found on bus: usb[/COLOR]

---

### Post by alaphonse on 2012-11-18
This just isn't supposed to be so effing hard. It's a testament to how much I hate Windows that I'm willing to put so much time trying to figure this out. Newbie - I'm not stupid, I'm not impatient and I'm not afraid to try things out but everyone here is speaking another language, it's immensely frustrating. I think it's ironic that something that purports to be Open Source can be so closed to the vast majority of computer users out there. I suppose that's the price we paid for allowing Microsoft and Apple to spoon feed us all these years. Apologies for the rant but it's been 3 weeks dicking around trying to get the most basic levels of functionality - wireless access to the web, print my documents, play my games, watch my movies.

Ubuntu 12.04 - Canon Pixma 4200 - finally got drivers to at least recognize printer and print a test page. Nothing else will print  it just hangs in Processing. I've tried most of the proposed fixes, at least the ones I understood, without luck. It appears that I might just have to dump the Canon and go to an HP printer. I'd do it in a heartbeat if I believed it would actually solve the problem but to say I'm a little gun shy would be a massive understatement. Help a brother out, all I want to do is print my documents they way I've always been able to.

---

### Post by BicyclerBoy on 2012-11-18
@ dragonfly

After adding the canon-trunk ppa..
sudo apt-get update
sudo apt-get install cnijfilter-ip2600series

Do you have synaptic package manager installed or are you using the software centre ?

---

### Post by ray field on 2012-11-18
> **alaphonse said:**
> This just isn't supposed to be so effing hard. It's a testament to how much I hate Windows that I'm willing to put so much time trying to figure this out. Newbie - I'm not stupid, I'm not impatient and I'm not afraid to try things out but everyone here is speaking another language, it's immensely frustrating. I think it's ironic that something that purports to be Open Source can be so closed to the vast majority of computer users out there. I suppose that's the price we paid for allowing Microsoft and Apple to spoon feed us all these years. Apologies for the rant but it's been 3 weeks dicking around trying to get the most basic levels of functionality - wireless access to the web, print my documents, play my games, watch my movies.

Ubuntu 12.04 - Canon Pixma 4200 - finally got drivers to at least recognize printer and print a test page. Nothing else will print  it just hangs in Processing. I've tried most of the proposed fixes, at least the ones I understood, without luck. It appears that I might just have to dump the Canon and go to an HP printer. I'd do it in a heartbeat if I believed it would actually solve the problem but to say I'm a little gun shy would be a massive understatement. Help a brother out, all I want to do is print my documents they way I've always been able to.

it isn't supposed to be that hard. but somehow, for some reason, Canon makes it a nightmare -- believe me, I've wasted hours trying to make my old MP530 work, and now it prints about one in five times. it's a cryin shame, because they make good printers.

I will never buy a Canon printer again. HP support is really good, for regular B&W printing I have a Deskjet1300 that has good Linux drivers. For color printing, I saved up to get a Brother MFC-J835DW and while it doesn't do everything I want it to do (print to hard 8x10 stock) it works very well and the Linux support is good -- an added bonus is ink is significantly cheaper than other inkjets. 

It can be frustrating to deal with manufacturers like Canon and NVidia in the Ubuntu world, but don't let them sour your experience.

---

### Post by BicyclerBoy on 2012-11-19
I have had 2 canon printers over some years worked well with ubuntu 10.04 up to 12.04..
I think the canon drivers are very good, much nicer interface than windows version.
One of the printers is model mp272.

Printer sharing over network with CUPS works well after you get a handle on the different printer "icons" & their meanings.

The HP driver (on my old HP DJ) works but is as slow as a pig in mud.

I've used nVidia in all my PCs except netbook, never had a problem that wasn't my own making.

---

### Post by zandman on 2012-11-23
Similar issue here: my HP OfficeJet suddenly refuses to print. It did for some time after the upgrade to 12.04 but since yesterday evening it's no longer printing.
So next step was remove printer and set it up again.
Removal was successful :) but set up was not](*,)
The printer is seen but if i then select it and click "add" the printer install window disappears after a while with no printer installed.

---

### Post by zandman on 2012-11-23
And then reinstalling it via the HPLIP toolbox does the trick, i can print again.
What is confusing is that the HPLIP fax utility is under the Applications->Office menu, while the HPLIP toolbox is under Applications->System Tools->Preferences (still using Gnome, not a great fan of Unity on my normal workstation)

---

### Post by bjchip on 2012-11-23
It doesn't SEEM broken, it IS broken and it has been broken for months now without any fix in sight.  

I am printing by shifting over to Windows...  and my Ubuntu which has worked well for me for most of the past decade, is almost useless.  

What is being done I have no idea, but this problem has to be corrected.  

I'll have to move to a different linux release, and SOON, because I can't use a system that can't even print to a damned network printer.   Concentrating on UNITY which I have given months to try to get used to, is a mistake IMHO, when an LTS release shows up the BASICS are the things that have to work, and there isn't much that is as basic as this.

---

### Post by silvagroup on 2012-12-06
Same problems here. But unlike zandman doing remove and add with HPLIP or expunging cups and reinatll does not do the trck, still screws up.
My desktop however has not experieced the same issues, even tough they are both Ubuntu. Desktop conyinued to work after upgrade to 12.04 and after upgrade to 12.10 (don't recommend 12.10 to much stuff broken!!!!) but rpinting still works. So something in upgrade process jacked up the system but what is the isssue. May need to do fresh install of some OS. Have windows several versions need to use them I suppose till then.

---

### Post by pbowler on 2013-01-01
I have a Canon iP4600 and have had problems getting it working under Ubuntu before - see[COLOR=Navy] [http://ubuntuforums.org/showthread.php?t=975747&highlight=ip4600&page=3](http://ubuntuforums.org/showthread.php?t=975747&highlight=ip4600&page=3)[/COLOR].  I upgraded to Ubuntu 12.04 today and, after a lot of problems :x and several hours hard work:eek:, my printer is now working\\:D/.  The key actions seem to have been:

[LIST=1]
[*]Download the driver from[COLOR=Blue] [COLOR=Navy]http://www.canon-europe.com/Support/Consumer_Products/products/printers/InkJet/PIXMA_iP_series/PIXMA_iP4600.aspx?DLtcmuri=tcm:13-738716&page=1&type=download[/COLOR][/COLOR]
[*]cd to the download directory and then enter:  [COLOR=Red]tar xf iP4600_debian_printer.tar[/COLOR]
[*]            Install libcupsys2:  [COLOR=Red]sudo apt-get install libcupsys2[/COLOR] and ignore the unresolved dependencies.  This didn't seem to do anything, but may have been necessary.
[*]Install the basic Canon filter:  [COLOR=Red]sudo dpkg -i --force-architecture cnijfilter-common_3.00-1_i386.deb[/COLOR] and ignore the unresolved dependencies.  After this step, the printer seemed to be working, but in a strange way.
[*]Install the iP4600 specific filter:  [COLOR=Red]sudo dpkg -i --force-architecture cnijfilter-ip4600series_3.00-1_i386.deb[/COLOR] and ignore the unresolved dependencies.
[*]Delete the printer using the Ubuntu Printer manager (from the menu attached to the button on the top right)
[*]Add the printer using the Ubuntu Printer manager.
[*]Check the printer options carefully and adjust as necessary.  Some were set to strange values, including the manual paper feed as the default !  (Accessed by right-clicking the printer icon and selecting properties).
[/LIST]
The following commands were also run at various times, but I don't think they were necessary (and hopefully haven't damaged anything :???:):
<ul>[COLOR=Red]sudo apt-get -f install[/COLOR]
                           [COLOR=Red]sudo apt-get install libpopt0[/COLOR]
Some commands were run with the file [COLOR=Purple]*multiarch*[/COLOR] in [COLOR=Purple]/etc/dpkg/dpkg.cfg.d[/COLOR] removed (see the release notes for Ubuntu 12.04 which indicate that this may be necessary to make aptitude work properly!

---

### Post by Gsyman on 2013-01-24
After doing an upgrade to 12.10 and trying to use my Windows network printer accessed via Samba, I just get the reply 'filter failed'.
The printer is a Lexmark X1150.
What's going on here, this printer has worked for years with previous versions, it really shouldn't be a problem?

---

### Post by 7seastraveller on 2013-02-04
Agree. Cups seesm broken on 12.04 LTS.
 
Upgraded from Ubuntu 10.04 LTS to Ubuntu 12.04 LTS a week ago, cannot print to HP color LasorJet 5550 since then. Was printing fine with Ubuntu 10.04!

I've seen all the big name printers are not working on this forum under CUPS on Ubuntu 12.04 and were all working fine under previous version. 
Canon, Lexmark, Brother, HP... you name it.
 
Ubuntu 12.04 LTS stable version should not be released with such a big issue!

---

### Post by jon_herr on 2013-02-21
CUPS is broken for me too...

My setup:

12.04LTS server (64 bit) with a Brother HL-2140 connected to it directly through a USB cable.

The server itself can print to the printer, and the printer is visible from the CUPS administration web page.   (localhost:631)

My other ubuntu boxes that are all 12.04LTS workstations can see the printer share through CUPS but when I issue a print job or test page I get the error message that the printer is "not responding".

I've googled and googled...  my only suspicion is that it's an apparmor problem - even though I have configured apparmor to just "complain" about CUPS problems.  

Whether apparmor is in "enforce" or "complain" mode for the the server doesn't seem to affect local printing from the server.  The server can always print - the client computers have never been able to print.

This all worked under 11.10 and earlier versions.  

In addition - I have a raspberry pi that is running debian with the same version of CUPS and everything works.  Local shares, remote shares, everything.  I'm about to punt and just use the PI for printing but I shouldn't have to...  

HELP!

---

### Post by jon_herr on 2013-02-22
Bump

---

### Post by jon_herr on 2013-02-23
Anyone?  

In summary:

(1) I can print locally from the server.
(2) I can find / install the printer from the clients (12.04LTS desktops)
(3) Attempts to print from the clients results in "Processing - The printer is not responding." messages.

Otherwise the printer shows as being "IDLE" after I clear the print queue.

---

### Post by catgate on 2013-02-24
Hello jon_herr,

You are not alone. I am running 12.04.2 LTS (in classic mode) and can not get my Epson DX 5050 to run. Using simplescan it will scan into the computer but it will not print. 
However I just plugged in my older Epson R200 and it just printed as though it had never been unplugged for four years or more.
There does seem to be what is known as "A noisey silence" about the matter. Even an enormous update of a couple of days ago included nothing that has made any difference.


HELP ):P

---

### Post by Snoopy_5_1 on 2013-03-02
Hello,

just postet about an year ago that my printer Canon i560 was not able to print.
However he hase gone over the edge now ;)
So I bought a new one Canon Pixma MG6250
Here are no problems with printing.
Cups works finde and the printer works also really good.
Installing was not difficult. Also via WiFi priniting is possible.

So I think maybe it dont work with old printers?

---

### Post by catgate on 2013-03-03
I have found out what my problem was. 
Even though 12.04 recognises the printer it is still necessary to tell the bloody stupid thing to use it by turning it on though *system settings*. 
Is this common or just my copy???

---

### Post by akgrant on 2013-03-09
I've had similar issues with CUPS under 12.04.  My Canon iP4200 which works fine under Ubuntu 11.10 or 12.10 fails to print grayscale under 12.04.

I've been able to work around the issue in two ways: install 5.0.1 driver from openprinting.org, or manually build and install libgutenprint.so.3.0.0 from gutenprint 5.2.8 (see [Bug #1151207 @ Launchpad]("https://bugs.launchpad.net/ubuntu/+source/gutenprint/+bug/1151207") for more details).

My impression is that the problem is that Ubuntu 12.04 is delivered with GutenPrint 5.2.8-pre1, earlier and later versions of GutenPrint appear to be more stable.

Is there a supported way to upgrade Ubuntu 12.04 from gutenprint 5.2.8-pre1 to 5.2.8 (or 5.2.9)?

Thanks,
Alistair

---

### Post by jon_herr on 2013-03-11
My symptoms are different...

I CAN print locally on the server through CUPS to my Brother printer as described.

I cannot print remotely either through CUPS or SAMBA. 

* CUPS jobs from remote clients are denied - yes they have legit accounts and passwords.
* Jobs from samba make it in to the samba inbox but never print.

Both of these methods worked in 10.04LTS

---

### Post by tstduke on 2013-04-30
I found this on another thread and it worked to fix my printer problem. 
From the terminal run "sudo system-config-printer" then select the correct driver for your printer. 
Here is the link to the other thread:
[http://ubuntuforums.org/showthread.php?t=1999536](http://ubuntuforums.org/showthread.php?t=1999536)

---

