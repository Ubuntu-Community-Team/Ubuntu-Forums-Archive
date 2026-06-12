---
title: "Canon MF4350d - Printer Scanner setup"
date: 2010-03-11
forum: Hardware
---

### Post by ridgeland on 2010-03-11
May 21, 2012 - - - Update for Ubuntu 12.04 LTS

When I installed Ubuntu 12.04 the system found the printer and installed a driver that does not work.  It's not hard to get it working though.

First you need the drivers from Canon's site.  The download zipped file has both the 32 bit and 64 bit drivers.  Note the steps below are for one specific version of the download.  Hopefully Canon has updated it and you will be getting a newer version and need to edit the commands.

The Canon support site is
[http://www.usa.canon.com/cusa/support](http://www.usa.canon.com/cusa/support)
The drivers for the MF4350d are at
[http://www.usa.canon.com/cusa/suppor...ersAndSoftware](http://www.usa.canon.com/cusa/suppor...ersAndSoftware)

Download the file to a known location like /home/user/Downloads

# # # First is a how-to for 64-bit systems ONLY # # #

Before doing this I had already installed Adobe's Acrobat Reader (acroread) which installed libc6-i386 ia32-libs lib32z1.  If you have not installed Reader then run this:
sudo apt-get install libc6-i386 ia32-libs lib32z1
(mjpollard post #88 and Footer post #93)
The 64 bit files are in RPM not DEB so you need alien to convert them
sudo apt-get install alien

For a 64 bit install I followed the work of bjtuna (post #80).  I put custom installs in /opt so I edited bjtuna's steps for my preferences.  The ln command was a major breakthrough, thanks bjtuna.

sudo -i
cp /home/user/Downloads/Linux_UFRII_PrinterDriver_V240_us_EN.tar.gz /opt/
cd /opt
tar xzvf Linux_UFRII_PrinterDriver_V240_us_EN.tar.gz
cd Linux_UFRII_PrinterDriver_V240_us_EN/64-bit_Driver/RPM
ln -s /usr/lib /usr/lib64
alien -k -c cndrvcups-common-2.40-2.x86_64.rpm
alien -k -c cndrvcups-ufr2-us-2.40-2.x86_64.rpm
dpkg -i cndrvcups-common_2.40-2_amd64.deb
dpkg -i cndrvcups-ufr2-us_2.40-2_amd64.deb

Now jump to the common steps &#8211; skip the 32-bit stuff

# # # Now the 32-bit version &#8211; it's easier # # #

I did not test this.  My last install was 32-bit but Ubuntu 11.04
Get the driver and extract as above

sudo -i
cp /home/user/Downloads/Linux_UFRII_PrinterDriver_V240_us_EN.tar.gz /opt/
cd /opt
tar xzvf Linux_UFRII_PrinterDriver_V240_us_EN.tar.gz
cd Linux_UFRII_PrinterDriver_V240_us_EN/32-bit_Driver/Debian
dpkg -i cndrvcups-common_2.40-2_i386.deb
dpkg -i cndrvcups-ufr2-us_2.40-2_i386.deb

# # # Common Steps # # #

Ubuntu 12.04 had already found the printer and installed a non-functioning driver for it.  So the first step is to delete the printer that is installed.  Next add a printer.  Side bar: I'm using Gnome Classic (no effects).  Printer maintenance menus there are incomplete.  I had to log in using Ubuntu (Unity) to have printer maintenance functions.  Add the printer and you are given several options for a driver.  The correct one was the fourth, the one with UFRII LT.  Sharing the printer was a pain.  It was so easy in 9.04, now it's CUPS.

For scanning I didn't install anything else.  I didn't test scanning until after the printer was installed and scanning worked fine.  I don't use the fax function so I don't know if it works.

The following is the original post of March 11, 2010 &#8211; Not so useful except to understand what the posts that follow are talking about.

# # # Original Post # # #

Out of the box the Canon MF4350d doesn't work with Linux (except as a copier).  So here is how I got it to work.  I don't use or care about the FAX machine feature so I am ignoring that.  This is an Image Class printer.  The user guide says MF4380dn MF4370dn and MF4350d 

Printer:
Canon has a site to download the driver [HERE]("http://support-asia.canon-asia.com/P/search?category=Multifunctional+Printers&series=ImageCLASS&model=imageCLASS+MF4380dn%2FMF4370dn%2FMF4350d%2FMF4320d&menu=download&filter=0")
There I downloaded:
Linux Printer Driver (UFR II) Ver.2.00E --- 2010-02-17
Unpack it and find a pair of Drivers.  In the Documents/ReadME you will find Ubuntu 9.04 32bit has been tested.  The only 64bit systems are Fedora and RedHat.  I could not get Ubuntu 9.04 64 bit to work, even with the rpm's for 64 bit.  Anyway I just installed a 32 bit version of Ubuntu 9.04 and that worked fine.
Before installing the debs (32 bit versions in download) you need to verify you have libcups2-dev.  Get it with Synaptics.  After libcups2-dev is installed just install the two debs.
cndrvcups-common_2.00-2_i386.deb
cndrvcups-ufr2-uk_2.00-2_i386.deb
Now connect the printer - Search for it if things don't start popping up.  It will want to install two print drivers.  One is fax the other is a printer.  Install using the recommended driver.  Send a test sheet (I don't like the test page because it consumes way to much toner).  If the first one works cancel the install of the second (fax).  
Pretty straight forward for a 32 bit installation.  

Scanner:
The sane version from synaptics will not work.  You have to get an unreleased version.
I followed a Linux-Mint post [HERE]("http://forums.linuxmint.com/viewtopic.php?f=51&t=28486") Here are my steps...
Synaptics - get libusb-dev --- without it no error messages will be generated but the scanner will never work.
Get the unreleased version of sane from debian.org [HERE]("http://git.debian.org/?p=sane/sane-backends.git")
Download the "Master" from the first line of the list.
My download was 4.7 MB called:
sane-backends-9b6a7af44269710d24576391c9b79e096b55aafb.tar.gz
as root extract the tar-ball in /opt
In a terminal 
```
$ sudo su
# cd /opt/sane-backends
# ./configure --prefix=/usr --sysconfdir=/etc --localstatedir=/var
# make
# make install
# cd /etc/udev/rules.d/
# gedit 40-scanner-permissions.rules
```
In gedit paste the following three lines:

> # usb scanner
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", MODE:="0666"
SUBSYSTEM=="usb_device",MODE:="0666"

Save it.   Check that it's in the correct folder /etc/udev/rules.d/ (I did this wrong once).

Reboot to have the new rules take effect.

Start XSane and it should default to it or offer it in a list.

I bought one for my mother and one for my wife while they were on sale ($130 with trade-in).

---

### Post by acankat on 2010-05-16
I've been looking for this solution last 6 months; you saved my life ! Thanks for the info.

---

### Post by johenkel on 2010-06-17
Did you mean libcups2-dev ? ( with an 'S' )
:confused:
Could not find a libcup2-dev.

johenkel

---

### Post by johenkel on 2010-06-18
I got it ! I got it ! 

WOW - THANKS !!

Works awesome - and even better since I used a discarded printer out of our surplus that was going into the trash, because its "eating" the paper. 
There was just that little paper holder clip from the discard tray inside the paper loader. Its only a few month old. Great !

Now, I don't need to fiddle with the Canon imageCLASS MF5550 that I just could not get to work under linux.

Thanks again !

What a way to end the work week .... Yey !!!!

johenkel

---

### Post by edgeconsults on 2010-07-24
This worked great for me too.  Just can't get it to print.

I can even get the ADF to work great.

Thanks a lot.

---

### Post by edgeconsults on 2010-07-24
Has anyone been able to get the printing function going on 64-bit ubuntu?  i'm running 9.04 and i was able to get scanning and the adf to work but i cannot print.  i even tried alien -k -c "nameof64bitrpms"  i downloaded the canon 2.10 driver for linux.

---

### Post by pdc on 2010-07-25
I've just posted on this or a similar thread! 

64bit systems look in /usr/lib64

canon is a default 32 bit install so puts stuff in /usr/lib

have a look in the filter directory

> /usr/lib/cups/filter/

see if there are any canon files there;

? copy them to the 

> /usr/lib64/cups/filter/ directory?

---

### Post by ridgeland on 2010-10-22
Update - installed U10.10 on our Gateway 4024 Laptop (32 bit CPU).  
Still 
[http://support-asia.canon-asia.com/contents/ASIA/EN/0100270807.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100270807.html)
for the drivers, a download at the bottom of a long, long page.
Now a version 2.10 is available.  Downloaded it. Extracted it.
Still the 32 bit has both deb and rpm, the 64 bit has only rpm.
Right clicked on 
cndrvcups-common_2.10-1_i386.deb
and selected 
"Open with Ubuntu Software Center"
Could not install, missing package cupsys.
UbuntuForums for the answer? Yes
[http://ubuntuforums.org/showthread.php?t=1592487](http://ubuntuforums.org/showthread.php?t=1592487)
leads to 
[https://help.ubuntu.com/community/CanonCaptDrv190](https://help.ubuntu.com/community/CanonCaptDrv190)
leads to
[http://security.ubuntu.com/ubuntu/pool/universe/c/cups](http://security.ubuntu.com/ubuntu/pool/universe/c/cups)
Look for the newest cupsys. I got:
cupsys_1.4.3-1ubuntu1.2_all.deb
download the deb
right click on it and select "Ubuntu Software Center"
Cupsys [Install] --- OK
Now back to 2.10 and try installing again in sequence: common then ufr2.
cndrvcups-common_2.10 --- OK
cndrvcups-ufr2-uk_2.10 --- OK
Now I power cycled both the printer and PC (not necessary? ).
Then the usual Menu -> System -> Printing and [Add]
Found two as expected.  The first plain name was FAX.  The second was the good one.
Tested with a short gedit line.  OK.

Scanner worked without needing any downloads.  SimpleScan is the default in U10.10, it worked. I used Synaptics to get Xsane, which also worked.

We don't use the fax so I didn't bother with it.

---

### Post by asn_knight on 2010-10-29
@ridgeland Thanks a lot for the thread!! :) Printer and Scanner working fine! :)

But Two-sided printing is not shown in the options...any idea how to do that??

Thanks.

---

### Post by ridgeland on 2010-10-29
Sorry,
No idea.  We haven't tried two sided.  If you solve it please post the solution here.
Thanks.

---

### Post by tonycm1 on 2010-12-24
Followed instructions and had it installed in no time on my laptop. Using Lucid 10.04 32bit installed with WUBI. Both Scanner and Printer work flawlessly when connected to USB! I'm not sure if I can get it to work using wireless...

The Ubuntu community never seizes to amaze me.... one of the big reasons I've slowly been able to ween myself off windows :)

---

### Post by nooblot on 2011-01-07
> **johenkel said:**
> I got it ! I got it ! 

WOW - THANKS !!



how about answering your own question eh ?

---

### Post by ridgeland on 2011-01-07
Thanks johenkel for pointing out my typo way back then. 
libcups2-dev NOT libcup2-dev
My apologies to everyone since for not correcting it sooner, it's corrected now.

---

### Post by nooblot on 2011-01-08
^ [IMG]http://www.acurazine.com/forums/images/smilies/thumbsup.gif[/IMG]

---

### Post by Jeffrywith1e on 2011-06-08
I can't seem to get MF4350d installed for 11.04. Is this solution for Ubuntu before 11.04? Doesn't seem to work for Natty. 

I get as far as printing the test page, but when trying that nothing happens. Nothing. Just says job # submitted.

---

### Post by Jeffrywith1e on 2011-06-12
I still cannot get this to work for me. I noticed that when you download from here the canon site, you are downloading version 2.20 instead of 2.0. Could that be making the difference?

---

### Post by thaegen on 2011-06-14
Found [this post](http://ubuntuforums.org/showpost.php?p=10745713&postcount=5), worked for me running 11.04 8-)

Didn't have to use the last step, but I'm printing over the network.  After aliening the RPMs and dpkg'ing the debs, the drivers popped up in my printer driver list.

---

### Post by fusion71 on 2011-08-03
Finally got this to work in 11.04 X64.  Had to install alien (to convert x64 rpms to debs), libc6-i386 and ia32-libs using Synaptic.

After installing the created debs (cndrvcups-common_2.20-1_amd64.deb,  cndrvcups-ufr2-uk_2.20-1_amd64.deb) with GDebi Package Manager,

I started the CUPS web interface [http://localhost:631/admin/](http://localhost:631/admin/) and added the printer by following the prompts-
NB There might be several choices. I chose Canon MF4320-4350 (UFRII LT) on connection cnusb:/dev/usblp0, not the fax option.
:D

---

### Post by scu-ba-de-buntu on 2011-08-11
I want to have your tuxbabies.

Followed what you said. Now I don't need to reboot for scanning.

---

### Post by spesheled1 on 2011-10-02
Thanks for this post. Printing and scanning now working perfectly in Easy Peasy 1.6 on my EeePC 900!

---

### Post by Footer on 2011-10-28
Sorry to bump an old thread but ... I had my MF4350d working perfectly using this method under 11.04.  Upgraded to 11.10 this week and now it's broke.  :-(

This is the error:

"File "/usr/lib/cups/filter/pstoufr2cpca" not available: Too many levels of symbolic links"

Any ideas???

Thanks!

Edit:  Uninstalled and reinstalled CUPS.  Then installed the drivers.  Bad link is now good!  Unfortunately, I still get this error:

```

/usr/lib/cups/filter/pstoufr2cpca failed

```

Any ideas?

---

### Post by Footer on 2011-10-29
Well folks, the solution was to go back to 11.04.  Just for grins, I did a fresh install of 11.10, same problem.  A link was created again to the file pstoufr2cpca.  This is NOT correct.  When I still couldn't print in 11.10, I reverted back to 11.04 (fresh install), installed the drivers and sure enough, pstoufr2cpca is actually a FILE not a LINK!  And printing works again!

It was a painful process to come to this conclusion but hopefully I will save some other's pain.  I did save the file separately in hopes that if I upgrade to 11.10 again, I can replace the link with the actual file after installing the drivers.

If anyone else has this problem or suggestions for a better solution, please post a reply to this thread!

:)

---

### Post by DaneM on 2012-01-26
I know this is an old thread, but it seems to be one the few on the topic I'm struggling with (according to Google, etc.).

I'm trying to get my Canon Imageclass MF8380Cdw color laser multifunction device to print.  I've installed the Linux UFR II package, as above, after installing the various packages suggested above, and the driver seems to install, but when I go to print, it says the job finished, and does nothing.

I'm using Linux Mint 12 (based on Ubuntu 11.10) 64-bit.  I've used alien to convert the 64-bit RPMs to .deb files, and they seem to install properly.

I tried copying the files from /usr/lib into /usr/lib64, as well as removing symlinks and replacing them with the real files, as suggested, but this has not helped.

I've tried connecting via WiFi network, and USB cable, and though CUPS finds the printer without any searching on my part, in both cases (it just lists it automatically for me to click on), and even suggests the UFR II driver, it doesn't work--but the logs in /var/log/cups don't indicate any problems at all.

I'm stumped!  I can't afford to buy another printer, and I'd love to see this thing working on my Linux installation (at least the printing aspect of it).  I'd greatly appreciate any help you can provide.

Thanks!

--Dane

---

### Post by Footer on 2012-01-26
Hi Dane,

I'm running Kubuntu 11.10 64bit and as I mentioned in my previous post, my ImageCLASS 4350d worked fine under 11.04 but broke under 11.10.  What I finally did to get it working was this:
```

sudo apt-get install libc6-i386 ia32-libs lib32z1

```
There's a reported bug here:

[https://answers.launchpad.net/ubuntu/+source/cups/+question/79913](https://answers.launchpad.net/ubuntu/+source/cups/+question/79913)

Then it worked!  Holy cow!!!  I was shocked!  So it seems like in addition to the UFR drivers under 11.10, you need some 32bit files as well.  Give it a shot and let us know if it works.

:)

---

### Post by DaneM on 2012-01-26
Thanks for the reply, Footer.

I ran the command you specified, but as it turns out, all those things were already installed, so no joy.  :-(

I did, however, just find this in /var/log/cups/error_log, which I somehow hadn't noticed before:

```

W [26/Jan/2012:13:40:25 -0800] [CGI] Missing Product in /usr/share/cups/model/CNCUPSIRADV4051ZK.ppd!
W [26/Jan/2012:13:40:31 -0800] failed to AddProfile: org.freedesktop.ColorManager.Failed:profile object path '/org/freedesktop/ColorManager/profiles/Canon_MF8380Cdw_Gray__' has already been added
W [26/Jan/2012:13:40:31 -0800] failed to AddProfile: org.freedesktop.ColorManager.Failed:profile object path '/org/freedesktop/ColorManager/profiles/Canon_MF8380Cdw_RGB__' has already been added
W [26/Jan/2012:13:40:31 -0800] failed to AddProfile: org.freedesktop.ColorManager.Failed:profile object path '/org/freedesktop/ColorManager/profiles/Canon_MF8380Cdw_Gray__' has already been added
W [26/Jan/2012:13:40:31 -0800] failed to AddProfile: org.freedesktop.ColorManager.Failed:profile object path '/org/freedesktop/ColorManager/profiles/Canon_MF8380Cdw_RGB__' has already been added
W [26/Jan/2012:13:40:53 -0800] failed to AddProfile: org.freedesktop.ColorManager.Failed:profile object path '/org/freedesktop/ColorManager/profiles/Canon_MF8380Cdw_Gray__' has already been added
W [26/Jan/2012:13:40:53 -0800] failed to AddProfile: org.freedesktop.ColorManager.Failed:profile object path '/org/freedesktop/ColorManager/profiles/Canon_MF8380Cdw_RGB__' has already been added
W [26/Jan/2012:13:40:53 -0800] failed to AddProfile: org.freedesktop.ColorManager.Failed:profile object path '/org/freedesktop/ColorManager/profiles/Canon_MF8380Cdw_Gray__' has already been added
W [26/Jan/2012:13:40:53 -0800] failed to AddProfile: org.freedesktop.ColorManager.Failed:profile object path '/org/freedesktop/ColorManager/profiles/Canon_MF8380Cdw_RGB__' has already been added

```

It should be noted that while working on this, I tried to install/uninstall the printer multiple times, but when I looked at this file the first time, it was empty.  Odd...  Anyway, these messages relate to my last attempt.

While I would like it if this driver used standard .ppd files (as mentioned in the error log), I don't think it does...correct?

Any other ideas?

Thanks!

--Dane

---

### Post by Footer on 2012-01-26
Bummer!  I feel your pain.  I almost feel like I got 'lucky' when I finally got my MF4350d to work under 11.10.  It was a struggle but it finally worked.

Don't give up!  Hopefully someone else will offer advice or you will eventually figure it out yourself.  Did you by chance have it working under a previous Linux Mint ... that may have been based on Ubuntu 11.04?

---

### Post by DaneM on 2012-01-26
Footer,

I just purchased the printer, so I haven't tried it in any other distro or version.  I was previously using Ubuntu 11.10, which I dumped yesterday, since I realized I couldn't cohabitate peacefully with Unity or Gnome 3.  :-D

I just tried installing the i386 libs on my 64-bit distro, but they need dependencies, like libglade2-0 and others, which can't be installed simultaneously in 32- and 64-bit versions.  *sigh*  Perhaps I can find some way to install the necessary .so files without having to use the package system, or messing anything else up.  Wish me luck... ;-)

Thanks again.

--Dane

---

### Post by Footer on 2012-01-26
Dane -- You should try Kubuntu 11.10!  Then do what I did and maybe your printer will work!  I've never been a Gnome fan so the whole Unity thing has never been a concern to me.

Good luck with whatever you decide.  I do hope you eventually get your printer to work ... And remember to post your results here!

:)

---

### Post by DaneM on 2012-01-27
Maybe I'll give Kubuntu another shot, sometime.

In any case, if/when I make it work, I'll post the solution here!

Have a good one.

--Dane

---

### Post by Footer on 2012-01-28
Well, here I am with an MF4350d that won't print again.  :(

I made the stupid mistake of trying out KDE 4.8 (was 4.7.4 under 11.10) and KDE 4.8 broke the living hell out of my system.  Non-responsive and unusable.  So I've basically just finished installing 11.10 from scratch, configuring everything again (I have /home on another partition so other than the OS, it's not bad).  Last thing to get working was the printer.

I've tried EVERYTHING including the 32bit files and guess what?  NO JOY!  So I really feel your pain now Dane!  I'm going to keep plugging away because I KNOW it works.  But something isn't quite right.  And I get no errors in [http://localhost/631](http://localhost/631) or /var/log/cups other than the ones you've seen Dane.

I guess we both need HELP now!

Thanks.

---

### Post by DaneM on 2012-01-28
Oh, no!

I'm sorry it broke for you!

I have an idea, though.  Did you just install KDE on an existing installation, or did you completely format/reinstall Ubuntu?  If you did the former, you can look at your package installation/removal history, and find out which libs, etc. were removed during the install!  That should provide a set of packages to try re-installing; when the printer works again, you know you found the right one!

I'm quite stumped right now, but given what you've said, I have confidence that you can get it working again, and tell me what I missed, when you do.  :-)

Thanks for keeping me "posted." ;)

--Dane

---

### Post by Footer on 2012-01-29
OK, here's where I'm at.

I fussed with trying to get the MF4350d to work after completely wiping the partition and starting from scratch with Kubuntu 11.10 (so no, the previous logs of package additions/deletions is not available).

I could not get it to work despite all the tricks in this thread and elsewhere.  And there never were any errors!

So, I wiped the partition again and went back to Kubuntu 11.04.  That's where I'm at right now.  It works perfectly.  I Installed the drivers and that was that.

So I'm back to trying to decide whether I should upgrade to 11.10 again and hopefully, after installing the 32bit files, it will work as before.  UGH!  I spent nearly all day yesterday to accomplish all of this.  You'd think I learned my lesson!  I really want to go back to 11.10.  It is so much faster then 11.04.  The performance is really noticeable.  I can't believe I struggled with 11.04 all those months.  And now I'm back to it again because of this stupid printer which I'm committed to make work (despite the thing only costing me about $100).  I really want to make it work and I really want to use 11.10!!!

Stay tuned!

:)

---

### Post by DaneM on 2012-01-29
Footer,

I can imagine how that could be quite a headache!

Might I suggest that you NOT install any 3rd-party repositories, then upgrade to the latest version of Ubuntu, via the Update Manager?  This should keep a log of what it changes in /var/log/apt.  As soon as the upgrade is finished, copy that whole directory, and all its subdirectories.  Then, use your favorite text editor (or "less <filename>" on the command line) to open the files, and post all the outpute here--one set of "code" tags per file.  (You may need to use zless, if some of the logs end in .gz.)

That *should* provide a list of what's changed, and *hopefully* point us in a good direction.  These logs may also be available in Synaptic, once you've finished the upgrade.

If you feel up to this, I look forward to seeing your result!

Also, if we can figure this out, we can post a solution/workaround/bugfix idea on the Launchpad bug tracker, so that others won't be so tormented by this!

Thanks.

--Dane

---

### Post by Footer on 2012-01-29
I am up to the challenge!   Not sure how soon I'll get to it but hopefully soon.  This is really bugging me and perhaps what you've suggested Dane will help us to fix this issue once and for all!

Thanks!  I'll report back very soon ...

:)

---

### Post by DaneM on 2012-01-30
Excellent.  :D

I'll stand by to try and help sift through whatever you come up with.

--Dane

---

### Post by Footer on 2012-02-04
Well, I've been running under Kubuntu 11.04 for a week now and it's almost driving me completely nuts (slow compared to 11.10).  So I might take the plunge this weekend and upgrade to 11.10 and watch my Canon MF4350d break.  But I will follow your tips Dane and post results here.  Hopefully we can see what changed and what broke it.

To be honest, printing to this printer under 11.04 is even a bit buggy.  Sometimes, I've had to run the scanner before it will print, from my 11.04 box or over the network.  The Printer Configuration under System Settings hasn't changed but there are times it just won't print.  I've found that sometimes a reboot helps, or a power cycle to the printer.

I seem to recall that when it was working under 11.10, it worked reliably.  So that gives me even more incentive to upgrade and get it working again!

Stay tuned!

:)

---

### Post by Footer on 2012-02-05
The upgrade from 11.04 to 11.10 is complete.  The printer did not work out of the shoot.  But this time, yet a third problem came up:

> 
Idle - "Printer not connected; will retry in 30 seconds..."


I found this as the "Status" under [http://localhost:631/printers](http://localhost:631/printers) (the CUPS browser interface).  I had not seen that one before.  I checked /usr/lib/cups/filter/pstoufr2cpca and in fact, it was a file (vs. a link) as it should be.  I then went to install the 32bit libraries:

> 
sudo apt-get install libc6-i386 ia32-libs lib32z1


But I installed them one at a time instead of all three at once.  I noted that lib32z1 was already installed, I guess by ia32-libs, so that one wasn't really needed.

Still no joy after the 32bit/i386 libs install, the status still showed as:

> 
Idle - "Printer not connected; will retry in 30 seconds..."


So I rebooted and guess what?  It worked!!!  I could print from my machine (the one the MF4350d is attached to) and also over the network from another machine on my network.

So I have no idea why the printer was not communicating with the machine at first, and I'm not 100% certain that the 32bit/i386 libraries made a difference or not but they were required the last time I went through this.

Dane -- I looked at and captured the files under /var/log/apt before and after the upgrade but they don't show much.  So I won't post their contents here unless you really think they will help us.  I did note during the install that I was asked if I wanted to:  "Keep /etc/cups/cupsd.conf" or replace it with the package maintainers copy (thereby losing all customizations).  I chose to Keep it.

And finally, I've attached a screenshot of the Package Changes that were reported for the upgrade.  It's only the numbers, I didn't take the time to note each individual package, but I'm sure that's buried in a log somewhere?  Pretty sure it's not captured in /var/log/apt though.

OK, not sure how much, if any of this helps.  This is my third time through this and I've basically had three different results.  I'm still not 100% confident the printer will continue working reliably, through logouts, reboots, etc.  I'll continue monitoring and report any anomolies here.  Scanning still works and always has through upgrades and even installing 11.10 from scratch.  It's just the darn printing!  I'm loving 11.10 though.  It's fast and smooth and pretty rock solid (except nepomuk, that's a mess!).

Thanks for reading!

:)

---

### Post by DaneM on 2012-02-05
Awesome!  I'm glad you got it working.  I wonder if my problems are having something to do with not rebooting after setting up the printer.  (One really shouldn't have to, but if it makes it work...)

Also, could you post the contents of your "/etc/cups/cupsd.conf" file?  I'd like to look at it, in case something is messed-up in mine.

I'll double-check to make sure those libs are installed on my own system; I think they are, but I'm not 100% certain (since I've tried so many things since I last messed with them).

Also, just to be clear: you're running Kubuntu, and not Ubuntu, right?  I doubt it matters, but I figure it's good to have all the variables sorted, inasmuch as I can do so.

Thanks for your help!  I'll get back to you within a few days to report any changes (good or bad) with the printing situation here.

--Dane

---

### Post by DaneM on 2012-02-06
One more question: did you install the 64-but UFR 2 driver, or did you somehow manage to install the 32-bit one?  I've been trying the 64-bit version, and I once tried installing the 32-bit one, but the 32-bit dependencies required would have uninstalled half my system (since they conflict with their 64-bit counterparts).

Also, if you installed the 64-bit one, can you provide the alien command you used to convert the RPM to a DEB?  I'm wondering if I've been doing it correctly.

I'm about to try again--this time, with a restart--but in case it fails, I'd like to know what to try next.  :-)

Thanks!

--Dane

Edit: I just had a brilliant idea!  Can you attach the file, "/etc/cups/ppd/<printer name>.ppd"?  Since it's working on your system, I can probably change the model/display name and then use it to install the printer, as if it were a driver file!  The UFRII driver would still be needed, but this would take care of the configuration end of it, for the most part, and help determine if the problem is a CUPS configuration issue--or perhaps make it work, outright!  If the forum won't let you attach the file (size, whatever), then you can open it in a text editor and copy/paste into a "code" box.  Thanks.

---

### Post by Footer on 2012-02-06
I installed the 64bit one.  These are the alien commands I used to convert the rpm to deb:

> 
sudo alien --to-deb --scripts cndrvcups-common-2.10-1.x86_64.rpm
sudo alien --to-deb --scripts cndrvcups-ufr2-uk-2.10-1.x86_64.rpm


The only 32bit files I installed are the ones I mentioned earlier.  I'm sure you don't want to install the 32bit driver!

I've attached the ppd file from my system.  Just remove the .txt extension!

Let me know how it goes!

:)

---

### Post by Footer on 2012-02-06
> **DaneM said:**
> 

Also, could you post the contents of your "/etc/cups/cupsd.conf" file?  I'd like to look at it, in case something is messed-up in mine.

Also, just to be clear: you're running Kubuntu, and not Ubuntu, right?  I doubt it matters, but I figure it's good to have all the variables sorted, inasmuch as I can do so.

--Dane

Yes!  I'm running Kubuntu 11.10!  And prior to that, Kubuntu 11.04.  The only way I've ever gotten this printer to work was doing an upgrade (11.04 --> 11.10).  I did try installing 11.10 from scratch but was unsuccessful at getting the printer to work.

Here's /etc/cups/cupsd.conf (FYI, this file is the one I did "Keep" on during the upgrade so it's the same as was on my system at 11.04):

```

LogLevel warn
MaxLogSize 0
SystemGroup lpadmin
# Allow remote access
Port 631
Listen /var/run/cups/cups.sock
# Share local printers on the local network.
Browsing On
BrowseOrder allow,deny
BrowseRemoteProtocols
BrowseAddress @LOCAL
BrowseLocalProtocols CUPS dnssd
DefaultAuthType Basic
<Location />
  # Allow shared printing...
  Order allow,deny
  Allow @LOCAL
</Location>
<Location /admin>
  Order allow,deny
</Location>
<Location /admin/conf>
  AuthType Default
  Require user @SYSTEM
  Order allow,deny
</Location>
<Policy default>
  <Limit Create-Job Print-Job Print-URI Validate-Job>
    Order deny,allow
  </Limit>
  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription
 Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-
Job CUPS-Move-Job CUPS-Get-Document>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>
  <Limit CUPS-Add-Modify-Printer CUPS-Delete-Printer CUPS-Add-Modify-Class CUPS-Delete-Class CUPS-Set-Default CUPS-Get
-Devices>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  </Limit>
  <Limit Pause-Printer Resume-Printer Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Rel
ease-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer Promote-Job Sc
hedule-Job-After CUPS-Accept-Jobs CUPS-Reject-Jobs>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  </Limit>
  <Limit Cancel-Job CUPS-Authenticate-Job>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>
  <Limit All>
    Order deny,allow
  </Limit>
</Policy>
<Policy authenticated>
  <Limit Create-Job Print-Job Print-URI Validate-Job>
    AuthType Default
    Order deny,allow
  </Limit>
  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription
 Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-
Job CUPS-Move-Job CUPS-Get-Document>
    AuthType Default
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>
  <Limit CUPS-Add-Modify-Printer CUPS-Delete-Printer CUPS-Add-Modify-Class CUPS-Delete-Class CUPS-Set-Default>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  </Limit>
  <Limit Pause-Printer Resume-Printer Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Rel
ease-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer Promote-Job Sc
hedule-Job-After CUPS-Accept-Jobs CUPS-Reject-Jobs>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  </Limit>
  <Limit Cancel-Job CUPS-Authenticate-Job>
    AuthType Default
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>
  <Limit All>
    Order deny,allow
  </Limit>
</Policy>

```

Good luck!

:)

---

### Post by DaneM on 2012-02-06
Thanks for getting back to me, Footer.

For the record (that is, for future viewers, as well as present), I'm posting what I just tried; I haven't yet tried using your cupsd.conf or .ppd file, or the rest you just posted.  That'll come next.

used these commands:
sudo apt-get install libc6-i386 ia32-libs lib32z1   #they were already installed
sudo alien cndrvcups-common-2.40-3.x86_64.rpm
sudo alien cndrvcups-ufr2-uk-2.40-3.x86_64.rpm
sudo dpkg -i *.deb

/usr/lib/cups/filter/pstoufr2cpca was missing; found it in /usr/lib64/cups/filter/; symlinked to "missing" location to no effect; copied it there to no effect.  Rebooted.

I'll post back soon!

---

### Post by DaneM on 2012-02-06
Well, it looks like my cupsd.conf is identical in every way that seems important, and our ppd files differ so much that they're probably not compatible with one another.  (There are plentiful references to feed type/location, duplex, color--black/white or color--etc. that will depend entirely on the physical properties of the respective devices.)

One thing I did notice, though, is that you're using version 2.10 of the driver, whereas I've been using version 2.40.  Where did you get that version?  Can you provide a link?  I'm wondering if the old version is somehow less buggy in the way that matters to my setup, or something.

Thanks.

--Dane

---

### Post by Footer on 2012-02-06
I'm actually using ver. 2.20.  I went to the website where I got them but the only version they have up now is 2.40.  I doubt the older version would solve your problem but maybe?

The .deb files are 1.1MB and 6.0MB.  The entire 2.20 driver package is 30MB!  What's the best way to get them to you?  Can't attach that large of files to the forum ...

EDIT:  Try this link:  [http://software.canon-europe.com/software/0040355.asp](http://software.canon-europe.com/software/0040355.asp)

---

### Post by DaneM on 2012-02-06
Progress...sort-of.

After downloading the file you linked to, I found that, unlike the current version, this older one has source code available!  Having spent some time in Gentoo and Slackware, I set out to compile it into native 64-bit binaries.  Here's what I ultimately had to do to make it compile:

```

1) sudo apt-get install autoconf automake libgtk2.0-dev libcups2-dev libxml2-dev libglade2-dev
2) tar -zxvf cndrvcups-common-2.20-1.tar.gz
3) cd cndrvcups-common-2.20
4) make gen
5) sudo make install
6) cd ..
7) tar -zxvf cndrvcups-lb-2.20-1.tar.gz
8) cd cndrvcups-lb-2.20
9) gedit (or vim, nano, or whatever you prefer for text editing) allgen.sh
10) where you see this:

[code]
./autogen.sh --prefix=${_prefix} --enable-static --disable-shared

```

change it to:

```

./autogen.sh --prefix=${_prefix} # --enable-static --disable-shared

```

(i.e. comment-out everything after "--prefix=${_prefix}", so it's disabled.)

11) gedit cngplp/autogen.sh
12) in the section that reads:

```

       automake - add-missing - gnu $ am_opt
       echo "Running autoconf ..."
       autoconf

```

add "autoreconf -ifv" on a new line, just below the above, so that it looks like this:

```

       automake - add-missing - gnu $ am_opt
       echo "Running autoconf ..."
       autoconf
       autoreconf -ifv

```

13) ./allgen.sh -deb
14) sudo make install
[/code]

I've since used checkinstall to turn the output of this process into a pair of bona-fide quick-and-dirty 64-bit .deb files.  (The dependencies and such are certainly not right, but they at least install properly.  I can deal with the rest later if need be.)

I found the bit about how to change those two files in some .diff files, posted at: 
[http://blog.kirie.net/linux/ubuntu/390.html](http://blog.kirie.net/linux/ubuntu/390.html)

It's in Japanese, so I used Google Translate to make it (mostly) readable.  After some deciphering, I was able to figure out just what was being changed.  Note that the site is dealing with a different Canon driver that just happens to suffer from (some of) the same code problems as the UFR2 driver.

That said, **my printer still won't print!**  I haven't yet tried a reboot, but I did restart CUPS with "sudo service cups restart", to no effect.  I'll reboot shortly and see if it suddenly starts working.  

*fingers crossed*

--Dane

---

### Post by Footer on 2012-02-06
ARGH!!!  How long did all that take you???  You are really committed to getting this printer to work!

I hope a reboot resolves it for you!  Good on you for being so persistent!  There seems to be absolutely no reason why we're having to jump through all these hoops to make this printer work under 11.10 (since it worked fine under 11.04!).

Keep me posted!  You're on a mission!

:)

---

### Post by venik212 on 2012-02-07
I have a Canon MF6530, and I am having the very same issues as you all are having. I had installed version 2.3 of the Canon driver under Lubuntu 64 bits. 
It is frustrating to discover that under XP the MF6530 simply worked immediately, while under (L)Ubuntu it is a real struggle.  I have the printer hooked up to the XP machine, and am trying to use it from the Lubuntu machine through Samba.  Lubuntu *sees* the printer just fine, but, like others b4 me, I am  getting the error: "/usr/lib/cups/filter/pstoufr2cpca failed".
All those 386 libraries had already been installed on my Lubuntu-64.

This (or a similar) struggle has been going on for a few years now, which is a VERY bad sign for Linux.

---

### Post by DaneM on 2012-02-12
Venik212, I feel your pain.  :-p

I've (for now, anyway) given up on trying to compile the 2.40 driver, since it's just so darned stubborn.  I don't know if the 2.20 driver has what you need, Venik212, but if it supports your model, I can at least show you how to compile it, probably (assuming the instructions above aren't sufficient).

As for my own struggle, I've even contacted Canon customer support since my last post, and got the typical answer:

"We're sorry, but we don't support Linux...blah, blah, blah..."

*Dane pulls his hair out*

I'm now trying a new tactic: installing from debs (converted from the RPMs via alien, as previously shown), and attempting to use my Windows 7 VirtualBox installation as a server--which I have share the printer and use CUPS to connect to that share.  Unfortunately, as brilliant a kludge is this is, it's not working at all: when I print a test page, I get on the jobs list, "User: witheld...State: stopped".  I know that both Windows (Vista onward) and Linux/Samba are temperamental about sharing and such, but I consider myself to be *fairly* good with Samba, and I don't yet know why this is not working.  VirtualBox is successfully sharing local folders with my host system (the system I want to print from), but for some reason, it's not printing.  :-(

```

For the record, my printer connection address is:
"smb://dane:mypassword@192.168.2.251/Canon_MF8380Cdw"
(i.e. smb://username:password@staticIPaddress/PrinterShareName).

```

Venik212, just to be clear: are you printing successfully by sharing from Windows XP to your (L)Ubuntu machine?  If so, please tell me any pointers you have!  If not, then it looks like we're in the same boat, and I'll do what I can to help you/us solve this problem.

Footer, thanks for your continued interest and willingness to help me with this problem.  It's my hope that we can solve this and then post the solution for all the world to see.  :-)

Thanks for posting, everyone.

--Dane

---

### Post by Footer on 2012-02-26
> **Footer said:**
> 
OK, not sure how much, if any of this helps.  This is my third time through this and I've basically had three different results.  I'm still not 100% confident the printer will continue working reliably, through logouts, reboots, etc.  I'll continue monitoring and report any anomolies here.  Scanning still works and always has through upgrades and even installing 11.10 from scratch.  It's just the darn printing!  I'm loving 11.10 though.  It's fast and smooth and pretty rock solid (except nepomuk, that's a mess!).

Thanks for reading!

:)

Two weeks post fiasco and I'm happy to report all is still working well.

Dane -- Did you get yours working yet?  How about any others following this thread?  What have been your experiences and would you care to share?

Thanks!

---

### Post by DaneM on 2012-02-26
Hi, Footer (and all).

Unfortunately, I've run into a "dead end."  I've even switched over to Mint's KDE version (largely because of the fractious nature of GTK development lately, but also to test printing), but have yet to see any success whatsoever.  No printing, no scanning, no computer-based faxing; nada.  :-(

For the time, I'm stumped.  If anybody has further suggestions on how to make this go, I'd be thrilled to hear them.  It's also probably worth noting at this point that your model may be genuinely better about Linux drivers than mine is (model: ImageClass MF8380Cdw).  *sigh*

I hope somebody is able to enlighten me about what to do next.

Thanks.

--Dane

---

### Post by ridgeland on 2012-02-26
Searching the Canon Asia site today I found:
[http://support-asia.canon-asia.com/P/search?category=Laser+Printers&series=ImageCLASS&model=imageCLASS+MF4350d&menu=Download&filter=0](http://support-asia.canon-asia.com/P/search?category=Laser+Printers&series=ImageCLASS&model=imageCLASS+MF4350d&menu=Download&filter=0)
There I found UFR II Printer Driver for Linux Version 2.40 which is this link:
[http://support-asia.canon-asia.com/contents/ASIA/EN/0100270810.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100270810.html)
version 2.40 was last updated: 27-Dec-2011
Unzipping I see they still have 32 bit *.deb and *.rpm but only *.rpm for 64 bit.

March 2012 will be two years for us using these printers (all Ubuntu).  We love 'em.
Our MF4350d is connected to my wife's laptop.  She bought a 64bit laptop in September 2011.  I installed Ubuntu 11.04 - 32bit OS and the printer is working fine with Canon's Version 2.20 on it.  Our home router gives me access to the printer and I use it to scan from my PC. 
The first MF4350d I bought was for my Mom.  Her PC is also 64 bit, using Ubuntu 9.04 32bit OS.  Mom's in her 80s and uses the printer more often as a copier than a printer.  Two years on the starter cartridge and she hasn't put a dent in it.

I use a 64 bit install, mostly.  I still boot to a 32 bit install to use LightScribe and LaCie.  When 12.04 is released I may switch to 32 bit too just for LightScribe and simplicity.  Ironically that will be the first Ubuntu release that does not recommend 32 bit over 64 bit.  Phoronix tests show 64 bit is 10% to 40% faster while executing some tests.  In our usage though 95% of the time the difference is 0% as the PC is waiting for a web page to load or for the user to type the next line or for the user to click on the next game piece.

I hope in April someone will post success with 12.04 64 bit.

---

### Post by DaneM on 2012-02-26
Thanks for the reply, ridgeland.

I've actually been trying to use the 2.40 version--UK, US, and other variants, included.  None of them seem to work (or at least, haven't, thus far).  They all come with 32-bit debs and rpms, but only a rpm for 64-bit.

I'm glad to hear your setup is working so well, though!  I'm beginning to think that despite the instructions on the Canon website to use this driver, it's simply doesn't have proper support for the MF8380Cdw.  :-p  If anyone manages to get this printer, or one of the 83xx series working, I'd be thrilled to find out just how it was done!  Perhaps I should start my own thread with that model number in the name...?

Anyway, have a good one.

--Dane

---

### Post by audeojude on 2012-02-27
sigh.. I have a MF4270 and this is the 4th time I have fought this battle in the last couple years since I purchased this printer. I have had to fix it multiple times as I have moved from ubuntu 9.0 - 11.10

Yesterday for other reasons I formated my computer and did a clean 11.10 install. This printer had been working on an upgrade to 11.10 now for almost 6 months. The alien to deb meathod had worked for me before but this time I hit the pstoufr2cpca filter error that everyone has been seeing. After hours of trying to fix it I finally caved in and just re-routed the print jobs through the 11.10 upgraded install on her workstation. Works perfectly when done like that. This will be the last canon printer I ever purchase though. I have been using it now for 2 or 3 years and it has been problematic with linux support since day one. If I wasn't an IT professional that works with linux, the printer wouldn't have worked at all for me. For a normal user that can't dip into the command line it would be pretty much unusable.

I sold a old samsung laser printer that had worked for years under windows, multiple flavours of linux etc... like a tank. It allways worked, setup easy and was cheap to keep in toner. I regret selling it like crazy. I wanted a laser all in one and got the canon for half price. Worst deal I have ever gotten. 

I recently picked up a samsung clp320 color laser printer. Guess what? It installs under windows, linux etc. with the greatest of ease.  For what it is worth I have never had driver issues with samsung printers under linux. HP's are mostly supported to though I am not a big fan of HP's. After this latest bout of troubleshooting I am done with Canon. It's just to much

---

### Post by Footer on 2012-03-11
Hey audeojude -- I think I could have written your response.  My experience has been almost exactly the same although I have not had my Canon as long as you.

Like you, I am an IT professional and work with Linux and you're right, this issue is not for the feint of heart!  It's been driving me crazy for awhile.

Mine seems to be working at the moment but it's probably temporary as Kubuntu gets upgraded or something else changes in the background.

Thanks for the tip of the cap to Samsung.  I'm in the market for a color laser soon and based on your response alone, I'll probably go that route.  I'm not a big fan of HP either which is why I went with Canon but with this driver issue, I can't throw my support to Canon especially for using with Linux.  Time to give the Samsung a try.

Thanks again!

---

### Post by DaneM on 2012-03-11
You know, that makes (at least) three of us who are IT/Linux professionals.  I suppose it's rather telling that the lot of us--with much help from the rest on this thread--have been unable to figure out this driver problem.  I rather like the printer/MFC, itself, and--like you--I bought it expressly because I became disillusioned with HP's post-early-1990s hardware; but man, I regret getting this device, due to its abysmal Linux driver support.  I hope you all have success with Samsung.  I seems like I'm stuck with this printer for the duration, due to cash flow problems...

--Dane

---

### Post by Footer on 2012-03-11
Where's the 'like' button?  Except for the cash flow problems of course!

:)

---

### Post by DaneM on 2012-03-11
Haha.  In the absence of such a button, I'll take a judicious nod of approval.  ;-)

---

### Post by audeojude on 2012-03-11
I purchased a Samsung CLP-325W color laser printer a month or two ago at tigerdirect for 69 dollars on sale. My 64bit ubuntu oneric installation saw it on the network and installed the drivers no muss no fuss. Works great. Though I have to say that the quality for pictures isn't as good as I had hoped. However for graphics etc it is absolutly brilliant. My old samsung was a ML-1430 if I remember correctly and it worked fine. Most distros back then didn't have drivers for it but samsung provided linux drivers that worked great. No worse than installing it under windows. The ML-1430 printer was the bomb for cost effective. toner cartridges were in teh 40 dollar range and I would get 3000+ pages out of a cartridge a lot of the time. This current color laser I don't have a good handle on yet for toner consumption. I got such a good deal on the printer that it will cost more than I paid to get a full set of cartridges.

Judgement is -- 
samsung easy to install and supported drivers in linux. 
Canon = nightmare even for the not faint of heart and knowledgeble user.

---

### Post by dmbortz on 2012-03-11
Hello everyone,

I've been lurking on this thread for a while now hoping someone would solve the problem.  Last week I decided that "surely I could fix this...my first linux install was 1996...I've even hacked a device driver or two in my day".

And, now I am admitting defeat.  I've spent (i.e., wasted) longer than I care to admit attacking this (unsuccessfully), but I thought I'd share what I've learned along the way.

* The setup:

Linux Mint 12 freshly installed on an i7 cpu machine.

ImageClass MF6530 all-in-one usb printer

Print server is a ASUS WL-520GU with dd-wrt (v24-sp2 build 17201 mini-usb-ftp) installed and usb printing enabled (socket://192.168.1.5:9100)

Printing works from my Ubuntu Natty laptop with the official Canon 2.20 64-bit driver installed (after an "alien -k --scripts" conversion to debs from the rpms).

* Attempts, failures, and discoveries:

1. Installation of converted Canon driver 2.20 and 2.40 64-bit rpms to debs has no issues.  As mentioned many times before in this thread, one can print using cups, but nothing comes out of the printer and no errors appear (even with "debug" instead of "warn" in /etc/cups/cupsd.conf) in the cups logs (except the annoying line that taunts you saying that "printing was successful").

2. Tried to compile from source.  Compile (./allgen.sh -deb) of cndrvcups-common-2.40 works and "make install"s fine.  Compile (./allgen.sh -deb) of cndrvcups-lb-2.40 errors out at this step:

make[3]: Entering directory `/home/dmbortz/install/mf6530drivers/Linux_UFRII_PrinterDriver_V240_us_EN/Sources/cndrvcups-lb-2.40/cpca/cnpklib'
/bin/bash ../libtool --tag=CC   --mode=link gcc -O2 -Wall -fPIC -D_UFR2_ -g -O2 -shared -version-info 1:0:0  -o libcnpkufr2.la -rpath /usr/lib cnpklib.lo cnpkopt.lo cnpkproc.lo -lbuftool 
libtool: link: can not build a shared library
libtool: link: See the libtool documentation for more information.
libtool: link: Fatal configuration error.

"cd"ing to the cndrvcups-lb-2.40/cpca/cnpklib directory and running:

libtool --tag=CC   --mode=link gcc -O2 -Wall -fPIC -D_UFR2_ -g -O2 -shared -version-info 1:0:0  -o libcnpkufr2.la -rpath /usr/lib cnpklib.lo cnpkopt.lo cnpkproc.lo -lbuftool 

works (not clear to me why this works...the libtool provided with the Canon driver is the same version as the one on my system).  "cd"ing up to the cndrvcups-lb-2.40 directory and running "./allgen -deb" again will finish compiling and then a "make install" works fine as well.

However, as before, print jobs report successful completion, without anything coming out of the printer.

3. I decided to get sneaky.  UFRII (Ultra Fast Rendering v2) is Canon's answer to PCL and thus one needs a pstoufr2cpca (postscript to UFR2) converter/filter.  In looking at the pstoufr2cpca.c file, there's several debugging commands, so I deleted the CPP "ifdef"s to see what would come out.  No dice.  The compiled pstoufr2cpca only creates a single logfile (/tmp/pstoufr2cpca.log).  I put the contents on pastebin at:

[http://pastebin.com/aFq5DBsf](http://pastebin.com/aFq5DBsf)

in case anyone sees anything useful. Fyi, the log in that file is repeated a few times (each time I tried to print something using this 'debugging' version of the filter).

And, despite there being mention of other debugging files, no other files are created.  Maybe if someone want to hunt down all the "ifdef"s someone could get the drive to create more info.  That someone will not be me.

4. I did #3 using the 2.20 driver and had the same result.

5. In googling this, there is a large number of people all over encountering similar issues...and not just on Canon printers.  Many users with different brand printers are encountering the "successful printing" without actual printing issue.  Our specific Canon problem has also been encountered forums in italian, slovenian, russian, and japanese and no one has any clue what's wrong or how to fix it. The only thing that might be useful to know is that this is occurring in many other distributions as well: archlinux, pclinuxos, gentoo, etc.  Someone in a gentoo forum:

[http://forums.gentoo.org/viewtopic-t-765593-start-0.html](http://forums.gentoo.org/viewtopic-t-765593-start-0.html)

seems to have had some success, but I don't know enough about gentoo to replicate it.

6. Yes, I've done cold and warm reboots and clean installs of cups and these drivers multiple times...nothing changes.

7. turboprint (non-free canon print filters) suffers from the same issue...and it makes no claims about supporting my printer...but reports that "printing was successful"!

8. Anyone know the difference between CARPS (Canon Advanced Raster Printing System) and UFRII-LT (Ultra Fast Rendering)? Aside from what you can find here:

[http://www.canon-europe.com/For_Home/Product_Finder/Fax/Laser/Features/Printer_Languages/](http://www.canon-europe.com/For_Home/Product_Finder/Fax/Laser/Features/Printer_Languages/)

and why one might consider choosing one driver vs. another?

9. Anyone know what "cnpkbidi" is?  The other commands the driver installs (cnjatool, cngplp, cnpkmoduleufr2) all do things I can figure out.  This one just returns:

ERROR: src = bidi_main.c, line = 524, err = 0¥n&#65533;&#65533;ERROR: src = bidi_main.c, line = 848, err = 0¥n

and there's no bidi_main.c in the Sources or on my system.

10. And speaking of the other commands, using cnjatool to turn on or off accounting doesn't change anything.

11. It would seem that cups shouldn't report that "printing was successful" when, in fact, it wasn't.  Anyone know of a good cups forum to mention this in?

12. Also, if this is just an issue which happens when users upgrade to oneiric (or lisa), anyone know of any substantial software version changes that could be the culprit?

13. Someone should nuke the "[SOLVED]" in the title of this thread.

best,
David

---

### Post by DaneM on 2012-03-11
Man, sorry to hear about the pain you've gone through, David.  Thanks, though for your very thorough list of what you've tried and what hasn't worked; I suspect that some day, somebody wiser than the lot of us might have an epiphany and fix this (and kindly deposit a pot of gold at the end of a rainbow, while he's at it...).

I absolutely agree that this thread isn't, in fact, "[SOLVED]", but I don't know how to remove it.  Perhaps the original poster (ridgeland) can be convinced to do so?  It would be much-appreciated.

On the topic of affordable printing, I searched long and hard to find a decent-sounding (based on reviews) -color- laser printer, with scan/copy/fax components and WiFi built-in.  I recall there being Samsung printers at a similar price point, but the reviews were (for whatever reason...) less favorable.  I really should have paid more attention to whether the printers worked on Linux, though.  (Note to self: write some scathing reviews.)  Hopefully, the prices of such printers will continue to decrease, and I'll be able to afford a new, Linux-friendly one within the current decade.  :-p

Thanks for all your help, everybody.  Here's wishing for that pot of gold.

---

### Post by audeojude on 2012-03-11
lol... this issue has ocurred been solved, ocrured again and again.. so many times .. in a month it will be solved... then it will happen again on the next distro upgrade etc...

I have personally fought and won this battle at least 3 times. This is the last time I will fight it.. next time I will buy a replacement printer and this one will find a home on craigs list, it isn't worth the time and effort to fight the same battle over and over again.

better to just avoid cannon printers.

---

### Post by Footer on 2012-03-15
Amen!  I've fought this battle at least 3 times as well.  It may very well be my last battle before I go to a Samsung printer.

If anyone finds a Samsung all-in-one (scanning/copying/printing and wireless would make me really happy) for a reasonable price, please post here.

:)

---

### Post by scu-ba-de-buntu on 2012-03-26
Just set it up properly on a virtual machine, and then never worry about it again

---

### Post by audeojude on 2012-03-26
You could do that but it is a aweful lot of work and resources just to get a printer working. It is well within the scope of my and several other of the posters on this thread but it is well outside the scope of the average computer user to set up a virtual system. Not to mention that it is better done on a server that isn't being rebooted etc..  What a pain to have to remember to start up a virtual server everytime you reboot your pc.. I do that currently to run my businesses accounting application and it gets old fairly quickly.

It comes down to you shouldn't have to use workarounds and crazy custom configurations to get something as basic as a printer to work. 

Scott

---

### Post by DaneM on 2012-03-26
As it so happens, I've set up a Windows 7 virtual machine, and when I really need to print something in Linux (or use some Windows-only program), I start it up.

This isn't, however, a good solution.  (1) VirtualBox is very picky about sharing your home folder; for whatever reason, it's nearly impossible (permissions and such...).  (2) If I'm using a program in Linux that I want to print from, then I have to install the program in Windows--which isn't always possible--then somehow get the VM to access the file, then print.

I've tried sharing the printer from the VM to my Linux host, and it doesn't work; I get the same problems as I got by trying to print directly from Linux.  ("Printing...done" but nothing is actually printed.)  The fact that I can't even print to an SMB shared printer with these crummy drivers is utterly unacceptable.

I appreciate the suggestion of trying a VM, but I'm sad to say it doesn't help much.

--Dane

---

### Post by audeojude on 2012-03-26
Dane,
I have a share directory on my linux box and a windows 7 virtualbox guest running on the system. I didn't even bother with the shared folder feature in virtual box. Just create a smb share of say a public directory in your users home directory. It's about as easy as right clicking on the folder and choosing sharing options :)

Then map that drive to a drive letter on the windows virtualbox guest. No muss no fuss.


Scott

---

### Post by DaneM on 2012-03-26
That's a good suggestion, Scott.  I'll probably do that in the future.

--Dane

---

### Post by sordna on 2012-03-28
I have an MF4150 which uses the same driver. It worked with 11.04, but broke with 11.10 and is still broken for me with 12.04, unfortunately.

---

### Post by dmbortz on 2012-03-30
Hello again everyone,

I really needed printing to work, so I solved the problem by wiping everything and then installing a 32 bit system.  Using the official Canon 32 bit debs means I can print again.

Anyway, we all knew that that would work, but I wanted to share that I also got remote scanning working.

If you are one of those people who does such things, then you might be interested in the following:

1. I have DD-WRT v24-sp2 mini-usb-ftp (SVN revision 17201) on an Asus WL-520GU/GC.  To get scanning to work, one needs to have extra space for some extra software.  I plugged a usb hub into the router (MF6530 plugged into the hub) and a usb stick plugged into the hub.  You'll also need to set up jffs on the usb stick (Seeing up jffs is really only for this hub, since it has an anemic amount of flash memory).

2. Follow directions here to set up the usb:
[http://www.dd-wrt.com/wiki/index.php/USB](http://www.dd-wrt.com/wiki/index.php/USB)

3. Make sure you have scanner.o from here:
[http://www.dd-wrt.com/phpBB2/viewtopic.php?t=43358](http://www.dd-wrt.com/phpBB2/viewtopic.php?t=43358)
and drop it in the appropriate 'modules' directory.

4. Follow the instructions in the first post here:

[http://www.dd-wrt.com/phpBB2/viewtopic.php?p=677441](http://www.dd-wrt.com/phpBB2/viewtopic.php?p=677441)

and in the last post.  The last one helps you to downgrade the libusb to the version that actually works.

Note that you can't use the package manager to do the downgrade as ipkg seems to have a broken -force-downgrade option...so you just have to copy over the libusb*.so.4.4.4 to /opt/lib/

5. Make sure you have added the router ip to /etc/sane.d/net.conf on your client machine

Scanning isn't fast, but it works!

best,
David

---

### Post by ridgeland on 2012-03-30
Thanks David (dmbortz) for sharing how you are scanning. There are lots of ways to do things.  
On our home LAN we use ssh on all the PCs, all running some release of Ubuntu.  From my PC I log on to the PC with the Canon scanner with ssh.  This opens a terminal window.  From there I run this script as sudo
```

#! /bin/sh
#
#	scan.sh
#
#	remote scan via command line
#

# require root password to continue
if [ ! $( id -u ) -eq 0 ]; then
	echo "scan.sh should be run as root"
	echo "Please enter root's password: "
	exec su -c "${0} ${CMDLN_ARGS}"
	exit ${?}
fi
echo; echo "Root permission was verified."; echo

echo "Scan will be at 300 dpi"
echo "Output will be saved as /tmp/scan.jpeg"
echo "Starting.  Wait for a message saying it has completed....."

scanimage --resolution 300 | pnmtojpeg -quality=90 > /tmp/scan.jpeg

echo "Scan has completed"; echo

```
The script uses scanimage and pnmtojpeg.  The script scans a full page size at 300 dpi and saves it as /tmp/scan.jpeg.  Since it's in /tmp next boot deletes it, next scan overwrites it.  I use places -> bookmark to connect to that PC with Nautilus (ssh server).  Then I copy /tmp/scan.jpeg to my PC and rename the file.
Now I can scan the next page.  I don't get a preview window or a method to set the scan size.  I use GIMP if I need to crop the image.  For my use that's very rare.  The hardest part is the walk from here to there to scan the next page or pick up my original. :)

---

### Post by audeojude on 2012-04-01
> **dmbortz said:**
> Hello again everyone,

I really needed printing to work, so I solved the problem by wiping everything and then installing a 32 bit system.  Using the official Canon 32 bit debs means I can print again.
David

I use so much ram on my desktop systems running virtual systems and dozens of windows in firefox that going back to 32 bit would hurt. I average 1.5 gigs memory usage just for the webbrowser. an average of another 4 gigs or better for virtual systems and then all the other stuff as well as the base OS.. I have 8 gigs total right now and when I upgrade will probably go to 32 to 64 gigs or ram so I can run the os off of a ram disk as well as all the virtual systems.

I admit I am not typical in usage and it is a bit over the top but it's how I work. If I go back to limited ram and speed I feel like taking a hammer to the computer after a while.
Scott

---

### Post by DaneM on 2012-04-14
Alright, so it would appear that the first step in making this printer work on Linux is to abandon trying to make it work on Ubuntu.  It's probably just as obtuse for any .deb distribution, but I haven't tested that.

Having gotten fed-up with the state of Ubuntu's GUI, I've been looking for another distro that would meet my needs for some time, now.  Linux Mint is *OK* but it's still just Ubuntu with some tweaks and additional software.  It can be made to work fairly well with KDE or MATE, but ultimately, it's been insufficient, and more to the point, it wouldn't *&$!*% print!

So, I started looking into RPM-based distros (which I'd previously sworn off).  I tried OpenSuse, but found that not only was it just as obtuse and hard to hand-configure as ever (that is, using anything other than YaST, which is essentially a GUI frontend to a bunch of ugly hacks), but the UFR2 RPMs wouldn't even install on it.  No OpenSuse.

Then, I tried Mageia.  Mageia is a completely free fork of Mandriva (formerly Mandrake), and since I'd used Mandrake before Ubuntu was around, I thought to give it a try.  Mandiva's always annoyed me a lot because of its built-in paywall for media codecs and more-or-less anything else useful; but Mageia is completely free, so that hitch is gone.  It's only in version 1, but it's a lot more polished than I expected, though the installation media selection for 64-bit is a bit odd.  Here's what I did to make my printer work:

1) Download the Mageia "open-source software only" DVD.  This DVD installs either 32-bit, or 64-bit, depending on your architecture, and it's the only way to get a 64-bit install, short of using the problematic network install CD.  (I tried the net install, and it went badly.)
2) Install Mageia by booting from the DVD; the process is very straight-forward.  I chose the "Custom" desktop option, and it works well for me.  I haven't tried their Gnome offering, but since I..."dislike"...Gnome 3, it's unimportant to me.  Ubuntu users should be aware that you'll need to input 2 passwords: 1 for your user, and 1 for root.  Mageia doesn't use sudo.
3) Run rpmdrake ("Install/Remove Software" in the KDE menu). Go to Options > Media Manager, and click "Add".  Select  "Full Set of Sources" and let it do its thing.  Then, also in the Media Manager, check whatever boxes you think are needed.  Be sure to enable non-free and tainted repos for media codecs, etc.  You can install that stuff later.
4) Search for and install "Task-Printing".  Also make sure that "Task-Printing-Canon" gets installed, to be on the safe side.  Scanning doesn't currently work, but there's also a package for that, should you feel inclined to fiddle.
5) Download the 2.40 (or latest) version of the UFR2 driver from Canon's web site.  Save it somewhere sensible.
6) Decompress/extract the UFR2 driver files and navigate to the 64-bit RPMs via the GUI file browser.  While you can install them via the command line, they'll probably give you crap about missing dependencies; the GUI installer will take care of that for you.  Double click on "cndrvcups-common-2.40-2.x86_64.rpm" and say "yes" to installing dependencies.  Then do the same for "cndrvcups-ufr2-us-2.40-2.x86_64.rpm" (or "cndrvcups-ufr2-uk-2.40-2.x86_64.rpm for the UK version").
7) Open a terminal (Konsole) and type:
```

su
<root password>
service cups restart
exit #this will log you out of root, for safety

```
8.) Now, you can go to the printer config tool by either typing, "system-config-printer" in a terminal, or KMenu > Tools > System Tools > Printing.  You may need to type your user or root password.
9) Select network printer (or USB if that's your connection type).  For network printer, you'll have to have set the printer's IP address to static (see the printer's manual).  Type that address into the "find network printer" box, and click the "find" button.  In my case, I instantly got it to see the printer's service and port.  You should make sure you're NOT in power saving mode when you do this.
10) Click "next" and continue on until it's given the printer a name, etc.  Done!

I printed a test page, and it came out quickly and properly with no tweaking at all needed.  I've since adjusted the settings to my liking (including duplex and toner saving), but that's just "icing on the cake."  If you want to use the scanner, you can try to get it working through "scannerdrake" or "system-config-printer", or via various sane-based CLI tools.  Good luck with that...  ;-)

On the upside, my model scans flawlessly to USB stick (plugged directly into the printer's USB port), so I just plug, press "scan", then re-plug the stick into my PC...*et voila!*

I hope this helps someone.  I know this isn't entirely appropriate for an *Ubuntu* forum, but since the problem seems unsolvable in Ubuntu, this is the best solution I could post for your benefit.

Note: I've thus far only installed Mageia in a VirtualBox (Win7 host), but since the printer is connected over network, and I'm using a "bridged adapter", I don't think it matters.  I'll be installing Mageia properly soon, and will report any problems I have with the printer that haven't come up on VirtualBox "hardware".  I don't expect there to be any.

Good luck to you all, and thanks for your commendable participation with attempting to solve this problem!

--Dane

P.S. Attached is a CUPS test printout, scanned via USB drive, in case anyone wants "proof" of my wild claims.  :-D  (Quality is reduced to comply with size limits for this forum.)

---

### Post by audeojude on 2012-04-16
I suppose that is one way of getting it to work :) replace the operating system. :)

I used to use mandrivia back when it was mandrake... dark ages of linux. I quit because of rpm hell. I have never gone back to a non deb/debian based os since then.

---

### Post by DaneM on 2012-04-16
audeojude,

I don't know if RPM hell has been fully solved, but I get the impression from fans I've known of the various RPM distros that it's much better than it used to be.  So far, I've not fully "dug into" Mageia, but it does show a lot of promise over the old Mandrake (which I preferred before I switched to Ubuntu around 2001).  Most of all, I consider it an option because it doesn't retain the crappy Mandriva/Mandrake paywall for useful software (that's free on other distros).

I'll post back if I run into significant problems.

---

### Post by Nath A on 2012-04-21
Thanks a lot . Finally got the scanner to work :)

---

### Post by DaneM on 2012-04-21
You did?!

What did you do to make the scanner work?  I've finally gotten printing online, but scanning has yet remained impossible for me.  

(Of course, we're using different models, but if it works for you, just maybe it'll work for me, right?)

Edit: I was able to scan to USB drive via the printer's build-in USB port.  Is this what you meant?  If I could get it to go from the scanner to my computer, though, that would be awesome.

---

### Post by DaneM on 2012-04-21
One more thing:

Since I promised a follow-up on Mageia, here it is.  I realize that this is an Ubuntu forum, so I hope I'm not out-of-line by promoting anther distro for the purpose of solving this problem.  Ubuntu is a good distro, so I'm not advocating a switch unless you feel like you have good enough reason to do so.

I've installed Mageia to my hard drive (with Win 7 on another drive; dual-boot), and so far, I've run into no problems of any note.  Learning which repositories ("media sources") have the stuff I want is taking a bit of time, and since it's such a new distro, the repos are lacking a few newer or less common things, like WINE 1.4/1.5 (currently there's only 1.3), and console game emulators.  Still, source code will get it all to me in a pinch.  (Notably, getting Mednafen to work required altering a symlink for the Nvidia drivers, but it was trivial enough once I figured it out.)

The printer is still working great, and since the device has a USB port built-in, I can scan well enough (and then "sneaker-net" the drive to my PC).

The distro, itself, has proven solid and reliable (so far), with all the features I care about.  "RPM Hell" appears to be a thing of the past, these days, since the advent and polishing of package management tools that are smart enough to detect endless circles of dependencies, versioning problems, etc.  I have yet to run into a serious problem with the RPMs, even after adding a bunch of repositories ("media sources") and installing/removing/upgrading a bunch of stuff.

As noted above, I'm still quite interested in getting scanning (directly to my PC, that is) to work; but if it doesn't, I won't have too much reason to complain, since I can accomplish what I need to, regardless.  Notably, the printer's drivers and Mageia's software for dealing with them (CUPS, KDE's utilities, and others) allow full access to such nice features as toner-saving, duplex, quality control, paper size/source, etc.  The driver tries to check "ink" (toner, actually) levels when connected via network, whereas when connected via USB, it realizes that that feature isn't supported, and says as much.

Installing the printer via USB is insanely easy (especially by contrast to the rest of this thread): you just plug in the cable, click "Add Printer" on the utility, and it'll find the printer, pick the UFR2 driver for you, and assign a pretty sensible name.  Voila!  Of course, you have to download and install the UFR2 driver manually, for either connection type (as instructed in my previous post), but that's very easy, as well.

All in all, I'm extremely happy with Mageia, and am even enjoying some nice features that Ubuntu lacked (such as MSec, which makes IPTables, anti-rootkit scanning, and other things quite easy for anyone).

Bottom line (as I see it): if you choose to switch for whatever reason (including to get the printer to work), you won't be disappointed.  It's really unfortunate that the UFR2 drivers hate Ubuntu (and most other distros), but at least there's a good alternative available.

Cheers, everyone!

--Dane

---

### Post by Nath A on 2012-04-22
> **DaneM said:**
> You did?!

What did you do to make the scanner work?  I've finally gotten printing online, but scanning has yet remained impossible for me.  

(Of course, we're using different models, but if it works for you, just maybe it'll work for me, right?)

Edit: I was able to scan to USB drive via the printer's build-in USB port.  Is this what you meant?  If I could get it to go from the scanner to my computer, though, that would be awesome.
Yeah it worked :) .Infact I am using a different model too (cannon mf4412)
Just follow the instructions on the first page.download sane [http://anonscm.debian.org/gitweb/?p=sane/sane-backends.git](http://anonscm.debian.org/gitweb/?p=sane/sane-backends.git)  (remember download master from the first line of the list.click on snapshot)..
Run nautilus as root create a folder 'sane-backends' in the /opt folder. 
Untar the downloaded file and copy the contents to /opt/sane-backends/ that you just created and just follow the instructions

Good Luck.

---

### Post by bjtuna on 2012-04-25
Oh, man. I just bought an imageCLASS D420 and I'm running Ubuntu 11.10 64bit. Reading this thread is like deja vu.  I don't know what I'm thinking but I'm about to take a stab at compiling these stupid bugged out Canon drivers. Will post here if I learn anything.

---

### Post by bjtuna on 2012-04-25
Okay, I figured it out, and my imageCLASS D420 is now printing in Ubuntu 11.10 64 bit.  The answer was here:
[http://ubuntuforums.org/showpost.php?p=11680367&postcount=36](http://ubuntuforums.org/showpost.php?p=11680367&postcount=36)

In short: using alien on the RPMs works fine *EXCEPT* that they try to write to /usr/lib64, which doesn't exist on our systems.  So if you symlink /usr/lib64 to /usr/lib and install the alien'd debs, you'll be good:

Start-to-finish:

Download the latest Linux drivers (v2.40 as of writing) on the USA Canon site.

```

sudo -i
tar xzvf Linux_UFRII_PrinterDriver_V240_us_EN.tar.gz
cd Linux_UFRII_PrinterDriver_V240_us_EN
cd 64-bit_Driver
cd RPM
ln -s /usr/lib /usr/lib64
alien -k -c cndrvcups-common-2.40-2.x86_64.rpm
alien -k -c cndrvcups-ufr2-us-2.40-2.x86_64.rpm
dpkg -i cndrvcups-common_2.40-2_amd64.deb
dpkg -i cndrvcups-ufr2-us_2.40-2_amd64.deb

```

Then install the printer with the Ubuntu GUI.  

Note:  I did a lot of crap before I finally got this to work, including compiling and installing the drivers from source and going down all the same roads as DaneM, which involved installing all kinds of dependency libs. So, I don't know for sure if this is going to work on its own for someone who hasn't done the same, but my guess is that it will.

Hopefully this helps.

-Brian

---

### Post by ridgeland on 2012-04-25
Thanks bjtuna!

The link to /usr/lib looks like a major breakthrough for those of us with 64 bit hardware.

The Canon support site is
[http://www.usa.canon.com/cusa/support](http://www.usa.canon.com/cusa/support)
The drivers for the MF4350d are at
[http://www.usa.canon.com/cusa/support/consumer/printers_multifunction/imageclass_series/imageclass_mf4350d#DriversAndSoftware](http://www.usa.canon.com/cusa/support/consumer/printers_multifunction/imageclass_series/imageclass_mf4350d#DriversAndSoftware)

Thanks for the "sudo -i".  I checked "man sudo" to see what it does. I had been using "sudo su".  "sudo -i" puts the user at /root rather than staying at /home/user.  Thanks.

This weekend I'll be downloading 12.04 and trying this.

---

### Post by dmbortz on 2012-04-25
Seriously?  That's all it took? I wasted a whole Saturday and I was one simlink away?  Time for some serious face-palming.

David

---

### Post by bjtuna on 2012-04-26
> **dmbortz said:**
> Seriously?  That's all it took? I wasted a whole Saturday and I was one simlink away?  Time for some serious face-palming.

#-o

Hah! Sorry

---

### Post by Footer on 2012-04-28
Has anyone been brave enough to upgrade to 12.04 yet?  Just curious if printing breaks and if so, does relinking fix???

Thanks!

---

### Post by bjtuna on 2012-04-28
> **Footer said:**
> Has anyone been brave enough to upgrade to 12.04 yet?  Just curious if printing breaks and if so, does relinking fix???

Thanks!

I upgraded to 12.04 and everything's still printing fine.

---

### Post by jscordia on 2012-04-28
> **bjtuna said:**
> 
In short: using alien on the RPMs works fine *EXCEPT* that they try to write to /usr/lib64, which doesn't exist on our systems.  So if you symlink /usr/lib64 to /usr/lib and install the alien'd debs, you'll be good:


Thanks a lot, creating this link before installing the debs allows to make work perfectly my MF4330d (on Kubuntu 12.04 64 bits, and with the version 2.40 of the Canon driver, I have not tried other configurations with this symlink technique).
Create the symlink, install the two .debs, add the printer for example in CUPS web interface, and print a test page, it should work immediately.

I have kept this symlink /usr/lib64 (this allows to remove the files put in /lib if I decide to remove the two debs installed above). This should not yield problems, because libraries are normally installed in /usr/lib on a 64-bits Ubuntu.

THANKS! :):)

---

### Post by gr8 on 2012-04-30
I tried creating the symbolic link and reinstalling the drivers and am getting the following error.

"Enable the 'Publish shared printers connected to this system' option in the server settings using the printing administration tool. To start this tool select System->Administration->Printing from the main menu."

I've already enabled the 'publish shared printers'. What should I do now?

---

### Post by mjpollard on 2012-05-01
> **bjtuna said:**
> 
Start-to-finish:

Download the latest Linux drivers (v2.40 as of writing) on the USA Canon site.

```

sudo -i
tar xzvf Linux_UFRII_PrinterDriver_V240_us_EN.tar.gz
cd Linux_UFRII_PrinterDriver_V240_us_EN
cd 64-bit_Driver
cd RPM
ln -s /usr/lib /usr/lib64
alien -k -c cndrvcups-common-2.40-2.x86_64.rpm
alien -k -c cndrvcups-ufr2-us-2.40-2.x86_64.rpm
dpkg -i cndrvcups-common_2.40-2_amd64.deb
dpkg -i cndrvcups-ufr2-us_2.40-2_amd64.deb

```

Then install the printer with the Ubuntu GUI.  

Note:  I did a lot of crap before I finally got this to work, including compiling and installing the drivers from source and going down all the same roads as DaneM, which involved installing all kinds of dependency libs. So, I don't know for sure if this is going to work on its own for someone who hasn't done the same, but my guess is that it will.

Hopefully this helps.

-Brian

To the above steps, I had to add

apt-get install ia32-libs

and I had to print to lpd://<ipaddress>/lp instead of http://<ipaddress>:9100

This on an MF8350cdn and a fresh install of 12.04 AMD64

It's good to be back on .DEB instead of .RPM

---

### Post by veleiro on 2012-05-03
I followed the steps in the post above, however my MF8350cdn (on the network) seems to not be added properly using Ubuntu GUI.  I had to type in the network IP to find anything, and it added it as a Canon-MF8300-UFRII-LT.  When I try to print to it, it says it's not connected.

---

### Post by mjpollard on 2012-05-05
> **veleiro said:**
> I followed the steps in the post above, however my MF8350cdn (on the network) seems to not be added properly using Ubuntu GUI.  I had to type in the network IP to find anything, and it added it as a Canon-MF8300-UFRII-LT.  When I try to print to it, it says it's not connected.

Mine registers as a 8300 series as well. My device URI reads as
```
lpd://192.168.0.51/lp
``` in the GUI.

---

### Post by Footer on 2012-05-05
Oh boy.  I upgraded to 12.04 this morning.  Guess what?  No joy printing.  :(

In the cups web browser status it says:

Idle - "src = libcanon_pdlwrapper.c, line = 512, err = 0¥nError Response:ReqNo=2, SeqNo=3,opvpErrorNo=-2"

This is yet ANOTHER error I have not seen before.  Scanning works fine.  I have the printer that is the subject of this thread, the MF4350d.

Dangit!  I'll try reinstalling the drivers I guess and post back.

**Update**:  After a couple more hours of messing around, it's working again.  It wasn't the smoothest of updates, for some reason, I don't think the update went completely through.  I had to run:  apt-get update and apt-get upgrade a few times, and after a few reboots, I finally got a status of "Idle" and it's now printing and scanning just fine again.  GOOD GRIEF!  It is now time to:  Step away from the keyboard.

:)

---

### Post by purdoom on 2012-05-06
I have 12.04 64 bit installed.  I followed the instructions to use alien to convert the RPM packages to deb packages, symlinked, and added the printer, and it claims it is working.  Only issue is nothing ever comes out of the printer.  Every test page I print claims 'processing' and 'sending to printer' then it leaves off at some status like:

Idle - src = libcanon_pdlwrapper.c, line = 514, err = 0¥nDEBUG: Wrote 1 pages...

And nothing is in the printer.  Per last person's advice, I did an apt-get update / upgrade and did a reboot as well, still no dice.

Does anyone know where I could get some more verbose debugging information as to what is going wrong here, or any additional tips?

---

### Post by Footer on 2012-05-06
I know you said you're running 64-bit, so am I.  However, I read in some other threads about this issue (my own issue included which was strikingly similar to yours), that you still need some 32-bit packages.

Check to make sure you have these:

```
sudo apt-get install libc6-i386 ia32-libs lib32z1
```

Reboot, turn printer off/on, yada yada yada.  Reboot again just to make sure.

Damn, I hope you get it fixed!

:)

---

### Post by paul2 on 2012-05-13
Thanks very much Footer! I was struggling with my Canon MF4370dn for few weeks since I have installed 64-bit Ubuntu (first 11.10, now 12.04). Just tried ia32-libs and now it at least prints. 

I would certainly have never guessed on my own that installing tons of 32-bit libraries would cure this misleading error:

'E [12/May/2012:19:36:03 -0400] [Job 31] src = libcanon_pdlwrapper.c, line = 514, err = 0\xc2\xa5nDEBUG: PID 2405 (gs) exited with no errors.',

-- but it did!

---

### Post by Footer on 2012-05-14
Crazy isn't it?  I discovered this awhile back via a lot of Google searching.  This and many other bizarre problems affect this particular printer family and ubuntu (and other distros?).  This thread has lots if details and history.

Glad you got it printing!

:)

---

### Post by ridgeland on 2012-05-21
I finally got my spouse's laptop set up for Ubuntu 12.04 64-bit and successfully installed the driver per bjtuna's steps.  I edited the original post to be a guide.  Please point out the errors!  Thanks.

---

### Post by DaneM on 2012-05-21
Very cool, BJTuna and ridgeland!  Thanks for posting this!

I'm currently running another distro, so I can't test/correct any steps for Ubuntu right now, but your suggestion about lib64 is probably a good one for those whose systems don't already have that directory.

I still mean to try and get the scanner working as per previous posts (although on my current distro); if/when I manage it, I'll report back any steps that seem like they'd work for Ubuntu.

Have a good one!

--Dane

---

### Post by es2burn on 2012-05-29
> **ridgeland said:**
> I finally got my spouse's laptop set up for Ubuntu 12.04 64-bit and successfully installed the driver per bjtuna's steps.  I edited the original post to be a guide.  Please point out the errors!  Thanks.

Thanks Ridgeland for the detailed updated instructions.

I followed your updated instructions, but ran into the same problem where my Canon printer (MF4570dn) showed functional, but nothing gets printed.

I had to install the 32-bit packages as footer suggested in order to make it to finally print.  Seems a bit slow when connecting to the network printer, but at least it prints now.

Haven't tested the scanning features yet.

Thanks again for the great help!

---

### Post by che_bizarro on 2012-07-09
Hi all,

I've had a fairly epic time getting Canon drivers to work on my 64-bit 12.04 LTS install but this morning I finally cracked it and hope that by sharing others will get the same joy...

Getting Canon drivers to work on 64-bit Ubuntu 12.04

Step 1. Download UFR drivers from Canon - [http://support-au.canon.com.au/contents/AU/EN/0100270808.html](http://support-au.canon.com.au/contents/AU/EN/0100270808.html)

Step 2. Convert the 64-bit RPM files to .deb using alien
      ```
sudo alien -s cndrvcups-common-2.40-1.x86_64.rpm
sudo alien -s cndrvcups-ufr2-uk-2.40-1.x86_64.rpm
```Step 3. Make Sym links in usr for lib64 -
        ```
sudo ln -s /usr/lib /usr/lib64
sudo ln -s /usr/local/lib /usr/local/lib64
```Step 4. Install .deb files
       ```
sudo dpkg -i cndrvcups-common_2.40-2_amd64.deb
sudo dpkg -i cndrvcups-ufr2-uk_2.40-2_amd64.deb
```Step 5. AppArmor denies the CUPS executables which the driver needs. Add to /etc/apparmor.d/local/usr.sbin.cupsd:
       ```
 /usr/lib64/cups/backend/cnusb Uxr,
 /usr/lib64/cups/filter/pstoufr2cpca Uxr,
```Don't forget the commas at the end of each line!

Step 6. Add the 32-bit libs that the driver seems to depend on:
        ```
sudo apt-get install ia32-libs
sudo apt-get install libjpeg62:i386
```Step 7. Restart CUPS
        ```
sudo service cups restart
```Step 8. Add your printer and everything should work just fine!

I hope this helps someone else!

---

### Post by DaneM on 2012-07-10
Che_bizarro,

Thanks for posting this!  I think I tried all those steps but the AppArmor one, and accordingly had no success on recent Ubuntu versions.  Very clever with that addition!  If/when I switch back to Ubuntu, I'll be sure to try that out.

Have a good one.

Edit: There should totally be a "reputation up" button (LinuxQuestions-style) for posts like that.

---

### Post by ervinshiznit on 2012-07-16
Hey guys.  I've tried all the steps suggested in this thread, but I still can't get my Canon MF4350d to print anything.  What's weird is that I'll print something, and it will saw processing in the print queue, and then disappear.

Do you guys have any suggestions?

---

### Post by DaneM on 2012-07-16
ervinshiznit,

Unfortunately, the behavior you're describing is a topic of much consternation throughout this thread.  Some people have managed to get around it, whether by a process such as che_bizarro describes, above, or by ultimately switching to another Linux distribution.  Sadly, I don't think I can provide further insight on this than I already have, but perhaps the insights of others on this thread--past and future will help you.

Good luck!

P.S. Is this the Ervin in Chico, CA?  :-)

---

### Post by ervinshiznit on 2012-07-16
So I found this piece of advice on a different forum for Linux Mint, and to my surprise it worked!

sudo cp /usr/lib64/libcanon* /usr/lib

I thought a symbolic link would be essentially doing what that copy command does, but hey if it works it works.

And nope, I'm not in CA

---

### Post by ervinshiznit on 2012-07-16
By the way what program should I use to scan?  I'm trying to get scanning to work now.

---

### Post by DaneM on 2012-07-16
Wow, I'm surprised that worked, since I tried something very similar, which didn't.  No complaints here, though.  ;-)

xscane is generally the "go-to" scanning program for Linux.  It's awkward and ugly, and you can possibly get better scanning functionality from GIMP or similar--but since xsane is closely related to the *nix scanner libraries, it's a good place to start.  Gnome and KDE have some related utilities that are basically reliant on xsane.  Let me know if you get scanning to work!  Solutions for this have been posted here, but I haven't had the energy to deal with it, given how much trouble it was to get printing to function.


The only Ervin I've met (and I assume your name isn't "shiznit..." ;-D ) happened to work with me at a computer shop here in CA, so I thought I'd ask.

Have a nice day.

---

### Post by ervinshiznit on 2012-07-16
Haha no my name isn't shiznit =P

Xsane initially gave me some device busy errors, but after restarting the printer and replugging the printer via usb, it works!  Thanks for the info on Xsane, and if I can be of any assistance with how I set up my printing and scanning functionality, I'm subscribed to email notifications on this thread.

Incidentally....I see no 2 pages on a side option in the driver.  This isn't just me right?

---

### Post by DaneM on 2012-07-17
Great!

I don't know if your model supports 2-sided printing; I'm using the MF8380CDW, and there's a driver option in the Gnome printing configuration tool for it.  Did you look under "job" and the other tabs?

---

### Post by ridgeland on 2012-07-17
Our MF4350D is connected to my wife's PC.  She uses double sided printing.  Recently she was complaining about how OOo or LibreOffice was flipping on the wrong edge.  Her work-around was to save it to pdf and print it from Adobe Reader.  The print project was a double sided 8 1/2 by 11 folded to be a four panel 8 1/2 by 5 1/2 bulletin.  Flipping the print on the short edge, not the long edge was the challenge.

---

### Post by DaneM on 2012-07-17
ridgeland,

There should be 2 ways to fix the double-sided printing without resorting to Adobe Reader.  


Method 1:

First, if you go to the printer setup tool and enter your printer's Properties, you'll see on the left (depending on which utility you're using--Gnome 3, Unity, Cinnamon, etc.) a tab/button called, "Printer Options."

Click that tab and look for "Duplex."  In its drop-down menu, choose either "ON (Long-edged Binding)" or "ON (Short-edged Binding)."  Set any other options you like (Toner Save, BindingEdge, etc.; there's also a "Word wrap" option under the "Job Options" tab) and click OK or Apply.

Ta-da! :-D

This should make these options "standard" for every print job unless you specify otherwise.


Method 2:

Since I no longer use a distro with OpenOffice instead of LibreOffice, I'll give instructions for the latter; hopefully they carry over.

When you go to print (File > Print...), go to the "Properties" button near the printer selection menu at the top.  Make sure your printer is highlighted first, of course.  There should be an option in one of the tabs for 2-sided or duplex.  That should offer you an option of how to print, but if "short edge" isn't an option, you might be able to choose "ignore" and use the defaults you selected using the first method, above.


I hope that helps.

--Dane

---

### Post by ridgeland on 2012-07-22
Thanks Dane,
That worked for flipping the page on the short edge.

---

### Post by DaneM on 2012-07-22
Excellent!  Thanks for the feedback.

---

### Post by erkserkserks on 2012-08-04
If it weren't for this thread, I would have never gotten my printer to work! In particular, I followed che_bizarro's steps and ervinshiznit's tip to get my MF4570dw working on Ubuntu 12.04 64-bit. The scanner still doesn't work, but that might be because the printer isn't supported by the SANE pixma backend yet.

---

### Post by DaneM on 2012-08-17
ervinshiznit,

Would you mind writing your instructions for how you got xsane working with your printer?  I've been working at it, and I think I've been doing it wrong.

Thanks.

--Dane

---

### Post by SylentBobNJ on 2012-08-23
> **ervinshiznit said:**
> So I found this piece of advice on a different forum for Linux Mint, and to my surprise it worked!

sudo cp /usr/lib64/libcanon* /usr/lib

I thought a symbolic link would be essentially doing what that copy command does, but hey if it works it works.





I followed all the steps here for my Canon imageClass MF5900 series multifunction to work in Ubuntu 12.04 64-bit.  

I had discovered after receiving the error:

```
there is a missing print filter for Canon MF5900 blah blah
```

that the filter executable called 'pstoufr2cpca' had not copied to the location CUPS was looking for it (/usr/lib/cups/filter) by checking the error logs in CUPS ([http://localhost:631](http://localhost:631)). I manually copied the file from the extracted RPM location of /usr/lib64/cups/filter to /usr/lib/cups/filter which satisfied the error but still nothing would print.  The job would "complete" but nothing would come out.

Then I saw the lovely yet absurd post above and copied the libcanon* files from one symlinked location to the other.  Viola, it prints.  I'll be scratching my head for a minute over this, but whatever, it works!  Thanks to all that shared their findings.

 -SB

---

### Post by daageep on 2012-08-25
thanks a lot! I got the printing and scanning functions to work. The scanning works perfectly with the Xsane package.

---

### Post by pravinbravi on 2012-09-10
You are awesome man. I have Ubuntu 12.04 AMD64, now the canon MF4350d printer works awesome. I would suggest the following tho:

```
sudo alien -k -c cndrvcups-common-*.rpm
sudo alien -k -c cndrvcups-ufr2-*.rpm
```note the -k -c options. That will give you the .deb files.

Thank you for the write up.


> **che_bizarro said:**
> Hi all,

I've had a fairly epic time getting Canon drivers to work on my 64-bit 12.04 LTS install but this morning I finally cracked it and hope that by sharing others will get the same joy...

Getting Canon drivers to work on 64-bit Ubuntu 12.04

Step 1. Download UFR drivers from Canon - [http://support-au.canon.com.au/contents/AU/EN/0100270808.html](http://support-au.canon.com.au/contents/AU/EN/0100270808.html)

Step 2. Convert the 64-bit RPM files to .deb using alien
      ```
sudo alien -s cndrvcups-common-2.40-1.x86_64.rpm
sudo alien -s cndrvcups-ufr2-uk-2.40-1.x86_64.rpm
```Step 3. Make Sym links in usr for lib64 -
        ```
sudo ln -s /usr/lib /usr/lib64
sudo ln -s /usr/local/lib /usr/local/lib64
```Step 4. Install .deb files
       ```
sudo dpkg -i cndrvcups-common_2.40-2_amd64.deb
sudo dpkg -i cndrvcups-ufr2-uk_2.40-2_amd64.deb
```Step 5. AppArmor denies the CUPS executables which the driver needs. Add to /etc/apparmor.d/local/usr.sbin.cupsd:
       ```
 /usr/lib64/cups/backend/cnusb Uxr,
 /usr/lib64/cups/filter/pstoufr2cpca Uxr,
```Don't forget the commas at the end of each line!

Step 6. Add the 32-bit libs that the driver seems to depend on:
        ```
sudo apt-get install ia32-libs
sudo apt-get install libjpeg62:i386
```Step 7. Restart CUPS
        ```
sudo service cups restart
```Step 8. Add your printer and everything should work just fine!

I hope this helps someone else!

---

### Post by Yetisaurus Akjas on 2012-09-20
On 10.04 (32-bit) I can confirm that the printer is functioning well with the cndrvcups-common 2.40-2 and cndrvcups-ufr2-us 2.40-2 downloaded from the US Canon site, but only after installing the libcups2-dev from aptitude. 
The DeviceURI is cnusb:/dev/usblp0 in the /etc/cups/printers.conf :p

---

### Post by haruska on 2012-09-26
I also can confirm this works on 12.04 with a MF4370dn over the network.

1. Symlink /usr/lib64 to /usr/lib
2. alien the 2 RPMs provided by canon
3. install the resulting debian packages
4. restart cups (optional?)
5. add printer via standard Printer GUI

The breakage from 11.04 => 12.04 was no longer using /usr/lib64 (but the aliened RPMs attempt to write there.)

---

### Post by theller on 2012-11-02
Thank you che_bizarro. You have brought me joy. Two weeks trying to get a  networked canon ir-adv 5051 to play nice with my 12.04 LTSP. Joy!!!

Step 6. Add the 32-bit libs that the driver seems to depend on:
        ```
sudo apt-get install ia32-libs
sudo apt-get install libjpeg62:i386
```Step 7. Restart CUPS
        
ia32-libs did not install anything but libjpeg62:i386 was the missing link.

---

### Post by Footer on 2012-11-04
Can anyone confirm if the MF4350d works after upgrading to 12.10?  It's been working perfectly under 12.04 but I've got the itch to upgrade.  :-)

I seriously don't want it to break and would love to hear if any other brave soul has moved on to 12.10 with continued success printing on your MF4350d.

Thanks!

---

### Post by omegamormegil on 2012-11-24
ridgeland,

Your May 21, 2012 - - - Update for Ubuntu 12.04 LTS instructions worked PERFECTLY for my Ubuntu 11.10 64-bit installation.  The only difference was I selected the driver for my printer:  Canon D400-450 (UFRII LT).  I am using a Cannon imageCLASS D420.  

I haven't tested scanning or faxing yet, but the test page is printing now.  Thanks!!!

---

### Post by Footer on 2012-11-25
> **omegamormegil said:**
> ridgeland,

Your May 21, 2012 - - - Update for Ubuntu 12.04 LTS instructions worked PERFECTLY for my Ubuntu 11.10 64-bit installation.

Did you mean 12.10?

Thanks!

---

### Post by rfboardengineer on 2012-12-07
I know this question is old, but I had a similar problem getting a MF4350d pritner to work on Ubuntu 12.10. I had to delete the symbolic link 
/usr/lib/cups/filter/pstoufr2cpca.

The filter I need was installed in 

/usr/lib64/cups/filter/pstoufr2cpca

By deleting the link in the /usr/lib/cups/filter folder and copying the actual file from the lib64, I was able to get printing again.

Of course this all has to be done in command line.

sudo -i

rm /usr/lib/cups/filter/pstoufr2cpca

cp /usr/lib64/cups/filter/pstoufr2cpca /usr/lib/cups/filter/

---

### Post by daghansa on 2013-01-19
I have had the same printing problem with  Canon MF 4370dn ( i-sensys mf4370dn) in linux mint. Linux Mint Nadia have installed a printer driver and that doesn't print the driver but capable of scan. I have deleted the printer from the printers and after that I have download the new driver from 
[http://support-asia.canon-asia.com/contents/ASIA/EN/0100270810.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100270810.html)

I extract the zip file and double clicked, installed the files cndrvcups-common_2.50-1_i386.deb and cndrvcups-ufr2-uk_2.50-1_i386.deb under 
 Linux_UFRII_PrinterDriver_V250_uk_EN/32-bit_Driver/debian/ directory. 

After I have added the printer MF4360-4390--UFRII-LT- from Printers. The fax was already added.  I have tested the printer and the scanner.  They have worked like a charm. Remember to select usb scan from the printer before scanning or else it gives a error and doesnt print also. Solve to that is remove the usb cable and plug it again

---

### Post by xtia on 2013-02-21
Thanks  **che_bizarro**, **pravinbravi.** After two days of trying, I finally get a   networked Canon IR-ADV C2030 to print well with my Ubuntu 12.04 AMD64 :)

---

### Post by RolfBly on 2013-03-28
I have a Canon MF4600 series, had the same problem installing it in 64-bit Ubuntu 12.04. 
Canon have driver version 2.6 available here: [http://software.canon-europe.com/products/0010462.asp](http://software.canon-europe.com/products/0010462.asp)
It comes with .deb files, so you don't need to convert. Their installation instruction is almost all you need to do. 
I then got this error: 

Idle - src = libcanon_pdlwrapper.c, line = 514, err = 0¥nDEBUG: Wrote 1 pages...

What fixed it in my case, is what Footer already said (and can be found [here]("https://answers.launchpad.net/ubuntu/+source/cups/+question/79913")): 

[SIZE=2][COLOR=#333333][FONT=Ubuntu]sudo apt-get install ia32-libs lib32z1[/FONT][/COLOR][/SIZE]

Strange that 32-bit libraries fixed a problem on 64-bit Ubuntu. Big libraries they are too. :roll:

---

### Post by pdc on 2013-03-28
so you went inside the directory I show in the thumbnail

.............[COLOR="#008000"]UFR [/COLOR]package...................[COLOR="#008000"]64bit drivers[/COLOR]..................[COLOR="#008000"]deb package[/COLOR] and installed these 64bit deb drivers............[COLOR="#EE82EE"]common.deb[/COLOR] first and then the [COLOR="#EE82EE"]ufr2_uk.deb[/COLOR] afterwards.........

and then needed the 32bit packages?...............just curious.................................

Canon do update packages and listen so I suspect one might be able to tell them of this issue

---

### Post by DaneM on 2013-03-28
Ooh, 2.60 drivers with debs...shiny!  Thanks for the heads up and workaround, RolfBly.  Are you sure this is the 64-bit driver?  Doesn't really surprise me that they need ia32 stuff (as do 64-bit Nvidia drivers), but just to be clear... :-)

Have a good one.

--Dane

---

### Post by SylentBobNJ on 2013-05-08
> **DaneM said:**
> Ooh, 2.60 drivers with debs...shiny!  Thanks for the heads up and workaround, RolfBly.  Are you sure this is the 64-bit driver?  Doesn't really surprise me that they need ia32 stuff (as do 64-bit Nvidia drivers), but just to be clear... :-)

Have a good one.

--Dane

I can confirm Canon has debs for their MF5950dw model. I just installed the 'common' followed by 'cups' debs and added the printer and it "just worked"!  There are 64-bit debs as well, just FYI, as that's what I'm using on 13.04 currently.

Thanks for the heads up!
 
-SB

---

### Post by DaneM on 2013-05-08
> **SylentBobNJ said:**
> I can confirm Canon has debs for their MF5950dw model. I just installed the 'common' followed by 'cups' debs and added the printer and it "just worked"!  There are 64-bit debs as well, just FYI, as that's what I'm using on 13.04 currently.

Thanks for the heads up!
 
-SB

Did you have to mess with AppArmor?

---

### Post by nooblot on 2013-05-11
So "**TONER LOW - PREPARE NEW TONER**" came on, I will replace when the tone starts to fade but:

1) Is the error indicator supposed to blink (red) _constantly_  ?

2) It won't print now, print status is "pending", so I had to switch to Windows virtual machine to print - Is this how it is with Linux ?

---

### Post by tcQBGCf on 2013-07-30
Thanks Footer. After installing the official v2.70 drivers my Canon MF 3010 still wasn't working. After installing these random packages, things work fine!

It's odd that Canon took the time to package their drivers as .deb packages but didn<t list these as dependencies.

---

### Post by Footer on 2013-09-15
I'm still running Kubuntu 12.04.  I've been ready to upgrade for awhile now but just haven't taken the time.  This printer thing is just one more thing that I'd rather not deal with.  Now that 13.10 will be out soon, I might just wait and take the plunge on that.  I'd be curious to know if after upgrading, your printer continues to work or if you have to mess around with the drivers again.  That's for anyone who's replied to this thread or is new to this thread.

Thanks!

---

### Post by fmn on 2014-05-24
Nothing useful to add here except to say a sincere thank you to OP ridgeland.....

Haven't played with Linux based systems in years so finding out how to get a Canon imageclass mf4350d up and running on Ubuntu 12.04 in this thread was pretty awesome :P

---

### Post by mahmoud_moosa2 on 2014-06-12
Dear ridgeland,

Just wanted to say Big thanks for your efforts.

After i followed your instructions, today i have successfully installed Canon image runner 2022 model in Ubuntu 12.04 32-bit.

I am so happy and Linux Ubuntu is the king.

Once again, thank you very much.

Mahmoud

---

