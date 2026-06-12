---
title: "Linux support for TomTom Home"
date: 2008-09-19
forum: General Help
---

### Post by isprins on 2008-09-19
I contacted tomtom because i feel that it is somewhat weird that tomtoms's GPS/navigation runs Linux, but the only software that exists are for mac or window$. It is called Tomtom Home.

(translated from Norwegian)

Customer (XXXXXXX)   09/17/2008 03:05 PM
I am not complaining, or bashing. However I would respectfully request you please begin Linux support for TomTom Home. I can't seem to run it in Wine, or in windows emulators. I understand TomTom's themselves are Linux based. Myself, I run Ubuntu Linux. With the dissatisfaction of Vista, XP becoming obsolete, and the price of either of them being inhibitive(and ridiculous); Linux is gaining popularity as a mainstream operating system. Ubuntu Linux especially since it is free, and has excellent support via web based forums. Once again, would you please consider creating a Linux distribution of TomTom home. If you need any help or advice please feel free to contact the thousands of programmers at 
[http://ubuntuforums.org/index.php](http://ubuntuforums.org/index.php)

Their answer:
Dear costumer
 
Thanks for getting in touch with us
 
TomTom gets more and more inquiry's if  there will be made a TomTom HOME version for Linux soon.  It is not currently planned, but they are open to it if enough users wants a Linux version.
 
TomTom HOME runs under wine, but it cannot detect the device.
What kind of emulators have you tried?
 
Please encourage more Linux users to notify us that a TomTom HOME version should be made. My colleges here at TomTom relays the inquiry's to me and i will relay them to the management and try to convince them that it is not good  costumer support to ignore Linux users because more and more are switching to Linux.

With regards,
Tomtom User support.


My answer:
 

I have tried Wine, and it does not detect the device.
I am told that it works good with VirtualBox running XP, but whats the point of running Linux then.

---------

I have posted this at:
[http://kubuntuforums.net/forums/index.php?topic=3097595.0](http://kubuntuforums.net/forums/index.php?topic=3097595.0)
and news.. 

alt.os.linux.ubuntu
alt.satellite.gps
alt.satellite.gps.tomtom
alt.comp.linux
alt.os.linux.ubuntu

---

### Post by bwhite82 on 2008-09-21
I too find it outrageous that a device that runs Linux does not provide an application that interfaces with the device on Linux. I'm no developer (and as such I could be wrong), but it couldn't be too hard to port this to Linux given the following:

(From [http://adblockplus.org/blog/tomtom-home-and-add-ons](http://adblockplus.org/blog/tomtom-home-and-add-ons))

> As some might know, I am a developer in the team behind TomTom HOME, an application that allows users to manage their TomTom navigator devices (e.g. installing new content on them, sharing it with other users or doing backups).

**TomTom HOME is based on XULRunner, it runs basically on the same code as Firefox.** This has many advantages for us, amongst others — support for add-ons comes with the platform, almost for free...

Additionally, when I explore the installation folder of the application in Vista, I can see a whole lot of .jar files. Java runs natively in Linux...

---

### Post by -Zeus- on 2008-09-21
I have a TomTom and I will send in a support request myself.

---

### Post by mdbarton on 2008-10-02
I've also submitted a support request along the same sort of lines (081002-001384)
> I am not complaining, or bashing. However I would respectfully request you please begin Linux support for TomTom Home.  At the moment I have to boot Windows XP to run TomTom Home (but that doesn't work either! see 081002-000852).  I have tried TomTom Home under Wine but it does not detect the device.

I understand TomTom's themselves are Linux based. Myself, I run Ubuntu Linux. With the dissatisfaction of Vista, XP becoming obsolete, and the price of either of them being inhibitive(and ridiculous); Linux is gaining popularity as a mainstream operating system.  There are many new 'netbook' devices coming to the market that run Linux, not Windows, out of the box.  

Would you please consider creating a Linux distribution of TomTom home. If you need any help or advice please feel free to contact the thousands of programmers at [http://ubuntuforums.org/showthread.php?t=924794](http://ubuntuforums.org/showthread.php?t=924794)

(TomTom Home on Windows XP does not seem to see me device either!)

Hope this helps, and I encourage others with TomTom accounts to submit similar support requests.

---

### Post by mdbarton on 2008-10-03
and got this as an answer:
> Thank you for contacting TomTom Customer Support.

We would like to thank you for your feedback regarding TomTOm Home compatability.

At TomTom we take all customer comments, feedback and suggestions seriously and therefore we have passed your comments on to our 2nd Line team, Product Management and Marketing Team.


With Best Regards,

The TomTom Customer Support Team

Which is better than an all out no!

---

### Post by fluffman86 on 2008-10-04
I requested a Linux version from TomTom USA back in May.  They didn't sound nearly as hopeful as TomTom Norway, but they did seem somewhat interested.

I'm hopeful that they'll do something soon.  I pointed them to picasa as a great example of free (as in beer, not speech) software that was designed for linux but works well under wine.  I don't even care that much about the HOME software...I would just like to download the updated maps in a file and unzip them to my GO which shows up as a removable device.

What bothers me about it is that when I bought my TomTom online I checked out the TomTom website to find which one I wanted before purchasing on eBay.  *NOWHERE* was anything listed about needing software to upgrade the TomTom.  I assumed it would either pick up a cell signal (like the Kindle?) or plug up to the computer and extract new maps, or possibly even be web-based,which would all be platform independent.

It would really be trivial for them to just upgrade the Home software to detect the device as a hard drive instead of some other crap...especially since (as I said) Ubuntu already recognizes it as a removable device.  

:(

---

### Post by taladan on 2008-10-05
Ya know, I've got a TomTom and I've never even tried to hook it up to my linux box...just assumed that it was probably unsupported.  I think (if I can remember to tomorrow) I'll put in a support request for it.  Can't hurt, might help.

Thanks for the heads up on this.

Tal

---

### Post by laemt on 2008-11-24
I tried to use wine for tomtom home and got an error...

fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\windows\\temp\\nsp627.tmp\\UAC.dll") not found

How do I fix this?

---

### Post by laemt on 2008-11-24
Ok i put MSVCR80 in the system32 file. now getting.

fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"

Any ideas?

---

### Post by paintbalforjesus on 2008-12-11
I also sent a message to tomtom asking them to support linux, maybe we can get them to support it and not worry about trying wine, since that apparently doesn't work.

As far as your error laemt I don't know how to fix that, but it appears from others posts that even if you do get it fixed and get tomtom home running in wine you still won't be able to connect it to your device, so it will be quite useless.

---

### Post by pedja_portugalac on 2008-12-17
I also own TomTom GO930 and would like to make it work with Linux. As far as I know it's not possible to make it work under Wine properly but there is another way maybe we could do it. Making your PC pretending that it is a GPRS capable telephone connected over bluetooth. 

There is howto, little outdated and for rpm (fedora) but still we can have an idea about the way. I'll try to find out about that soon and if you also want to check that this is the link to the page:

[http://www.fenrus.org/tomtom/](http://www.fenrus.org/tomtom/)

I found, this morning, that the bluez, bluetooth application that come from the box in Ubuntu 8.10, is the one TomTom use to connect to devices. At least models: Tom Tom GO300, GO500, GO700, RIDER, ONE, ONE (EDR version), and I presume that my GO930 also use it but as it is brand new model they forget to mention it. This is a good news in our research and I wish you, guys, also get there to help us find solution. I feel that this will be small job of configuration to make the pc pretend that it is a GPRS capable telephone. Here is official page of bluez:

[http://www.bluez.org/qualification/](http://www.bluez.org/qualification/)

My question for TomTom support service
> I found you are using bluez as bluetooth connection application. I am Linux Ubuntu user and bluez come in Ubuntu from the box. I am wondering if we could make our PC pretend that it is a GPRS capable telephone and update our TomTom device that way? Any idea, please let us know? 

---

### Post by YMS_1975 on 2008-12-22
I got sick and tired of this issue. I just started a new thread  about what I've decided to do about it.

[Check it out.]("http://ubuntuforums.org/showthread.php?t=1018673")

Or, if you don't want to read that thread, just jump to the good stuff [HERE]("http://www.PetitionOnline.com/tomlinux/").

**Please spread the word. If you come across any Ubuntu or TomTom/GPS websites, please post the link above. I believe if the demand is visible, TomTom will come around.**  :)

---

### Post by bazzer on 2008-12-29
**Tomtom do not support Linux**. I contacted their tech support and was told to use a compatible computer. However, there are no specifications on the box and there is no reason for me to assume they don't cater for Linux, so I'm pretty annoyed by this. 

The tech support droid told me that my comments would be passed to "second line", but I responded and told him I consider this to be rude, and that I would like to be reimbursed for the difference between **my** experience of the product and that of a Windows or Mac user. We will indeed see what happens next. Nothing, I bet.

Note - Tomtom HOME will not work in WINE, as WINE can't do the do with USB.

---

### Post by prakashkashyap on 2009-05-10
It is utter lack of respect for the customers that tom tom is not willing to release software for the linux user. I condemn it. I will advice my friends not to buy tom tom.

---

### Post by cdurst on 2009-06-01
> **prakashkashyap said:**
> It is utter lack of respect for the customers that tom tom is not willing to release software for the linux user. I condemn it. I will advice my friends not to buy tom tom.
Chill out.  Tom Tom is not en enormous company, and you'd probably be surprised at how few developers they have.

(Disclaimer: I have no connection or inside knowledge about the company, but I've worked for enough small companies to know how their resources are usually allocated.)

Naturally they're going to support the most popular platforms first.  They actually seem like a fairly open company (compared to Garmin), and they've definitely shown willingness to consider a Linux port.  But when it comes to limited development resources and priorities, which do you think ranks higher: fixing important bugs in the Windows/Mac software, adding new features to help sell the product, or supporting a niche platform for which there MAY be workarounds* anyway?

That said, hopefully linux-based netbooks might help push the numbers in our favor.

In the meantime, sign the petition.

Charles

 * - Note that for them a reasonable workaround is: borrow someone else's PC.  What percentage of Linux users do you think would be unable to use that solution?  10%?  20%?   Of the 1-2% linux desktop portion of the market?  Of course, I would be in that group, but I can't imagine that it would be a hugely significant portion of their overall market.

P.S. 1saleaday.com is selling refurbished TomTom's at 70% off today only.
(I'm not connected with them either, except as a customer.)

---

### Post by ruehara on 2009-06-10
I have a Tomtom XL 30 and have been having similar problems. Even though Ubuntu/Wine/VirtualBox won't recognise the GPS as a USB device, Ubuntu will recognise it as a mountable external drive. Once mounted, the whole directory structure and contents are browseable.

I pointed this out to Tomtom and suggested that if things like maps, map corrections and GPS fixes could be made available as downloadable files then it wouldn't be a hard job at all to copy them into the relevant directories on the Tomtom.

Their reply was to "get more people to write to us. The more requests we have for Home for Linux, the more likely we are to develop it".

So there's the answer. Get writing in.

---

### Post by cdurst on 2009-06-12
OK, well my Refurbished TomTom ONE 3rd Edition arrived from 1saleaday.com yesterday.

I think I've almost managed to get the HOME software running under Wine on Kubuntu 8.04 (hardy heron).  Here's what I've done so far:

* When I plugged it into the USB port and told it to connect to the computer, it auto-mounted on /media/INTERNAL.

* Having previously installed the winehq verison of wine (which seems to be broken), I did a "complete removal" uninstall and re-installed from Hardy Updates.  The only reason I mention this is because when I then went into the Wine part of "systemsettings" (under the Advanced tab), it saw /media/INTERNAL and mapped it to the D: drive.  If I hadn't gone into systemsettings/Wine with a clean installation, I'm guessing I'd have had to add /media/INTERNAL manually.

* Download the current version of winetricks:

   wget [http://www.kegel.com/wine/winetricks](http://www.kegel.com/wine/winetricks)

put it somewhere in your path, and do a "chmod +x winetricks" to make it executable.  (More information on winetricks can be found on [this page]("http://wiki.winehq.org/winetricks")).

* Run winetricks as your regular user (not root) to install some support libraries:

   winetricks dotnet20 vcrun2005sp1 ie6

That will download and install several freely-available software packages from Microsoft and may take a while.  If it looks like it has hung at some stage, give it at least 5-10 minutes before you attempt to kill it.  Occasionally you should see Windows-like dialogs popping up asking you to approve licenses and such.  (Legal Disclaimer: make sure you meet the Legal requirements of each license before accepting it.)  Approve everything and let it install in the default ways.

* Then "cd /media/INTERNAL" and launch "wine InstallTomTomHOME.exe".  Answer the usual questions and it should install fine.  Then it will attempt to run, and it seems to work.  When I did this, I hadn't installed ie6 yet, and it popped up a dialog asking me which app to run for "https:".  I'm assuming that having IE installed should help with that.

* Once you have it installed, you should be able to run it by doing:

   cd ~/.wine/drive_c/Program\ Files/TomTom\ HOME\ 2/
   wine TomTomHOME.exe

Anyway, you end up with a nice dialog with big buttons for updating your TomTom or purchasing maps and stuff.  At that point, I wimped out.  I don't really want the "update" to fail in the middle, at least not without a backup...  I'm making a backup now, then I'll try again and see what happens.

Update: OK, well I guess it really doesn't work.  The problem is that it doesn't detect the TomTom device.  I'll try again tomorrow.  If anyone has a suggestion, I'd love to hear it.

Update 2: OK, I guess the problem is that Wine doesn't really support USB ... yet.  Though [http://wiki.winehq.org/USB]("http://wiki.winehq.org/USB") seems to indicate that it might be possible if you're willing to build your own Wine from the latest bleeding-edge source.  It looks like if TomTom wanted to put out a Linux version, they could get about 90% of the way there by using winelib and just implementing a Linux-native version of their USB interface.

OK, so now I know why Wine won't work.  What's the problem with using VirtualBox?

---

### Post by altonbr on 2009-06-17
What e-mail address should I be sending complaints to?

I just purchased a TomTom GPS device for my father as I (wrongly) assumed it would work with Linux due to them using the Linux kernel and releasing modified versions of their software to the FOSS community.

I'm pretty darn ticked off they don't support Linux either, especially because no one in my family own's a Mac or Windows.

---

### Post by cdurst on 2009-06-17
> What e-mail address should I be sending complaints to?

I just used their usual support question system to ask them (nicely) how I can run TomTom HOME on Linux.

The response I got back (minus the marketing fluff), said:
> Due to software issues, our TomTom Home program is not compatible with Linux. We do not have any software available for it at this time. We apologize for any frustration this may cause. We currently have software available for:

Windows (latest service packs recommended):

-2000

-XP

-Vista

Mac:
-OS X 10.3.9 or higher

We apologize for any inconvenience or frustration this may have caused you.

Anyway, since then I have found out that it is possible to do it if you are willing to run Windows XP inside the non-free (but zero cost) version of VirtualBox and then share the Linux TomTom USB device into the virtualized system.  It worked for me on Jaunty (9.04) with the latest version of VirtualBox (2.2.4) with my TomTom ONE 3rd Edition.

It was able to update the software and maps on the TomTom, and everything seems to work fine, so far.

Charles

---

### Post by BB88 on 2009-11-19
Sorry for bumping an old post, but I thought I would share my current experience.

I am running Ubuntu 9.10 on an Acer 5536 Laptop. Running Wine 1.01, and installed TomTom HOME 1.5.106.

My TomTom Device was detected on Ubuntu as a removable device and it gave it a nice TomTom icon on the desktop. It was mounted as /media/TOMTOM.

I configured the drives wine saw when I plugged in the USB Cable and it detected the TomTom as a removable drive. I then fired up TomTom HOME and changed the device to point to /media/TOMTOM and it connected fine, with updates and installation.

Hope this helps!

---

### Post by wharp on 2009-12-02
BB88: Have you tried with the newest version? I think it's 1.6. I get an error when trying to install.

wes@pendragon:~/Downloads$ wine TomTomHOME2winlatest.exe 
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\windows\\temp\\nst165.tmp\\UAC.dll") not found

---

### Post by wharp on 2009-12-02
Ok, I took care of that issue with winetricks. TomTom Home is installed and runs fine, but doesn't see my gps. I have a TomTom 325-SE. Ubuntu (Karmic) sees it and mounts it to /media/INTERNAL (not sure why this mount point). Anybody have any ideas on what I need to do to get wine/TomTom Home to see the gps unit?

BB88: What gps do you have?

---

### Post by daller on 2009-12-19
I have a Tomtom XL IQ Routes, and I'm running Kubuntu 9.10

I can install Tomtom HOME 2.7.3.1894 from the device:

Install wine and cabextract:
```
sudo aptitude install wine cabextract
```

Get winetricks: ([http://wiki.winehq.org/winetricks](http://wiki.winehq.org/winetricks))
```
wget http://www.kegel.com/wine/winetricks
```

Install needed stuff for Tomtom HOME to work:
```
sh winetricks corefonts vcrun6 vcrun2005
```

Just in case it should help anything, have /media/TOMTOM point at /media/INTERNAL:
```
sudo ln -s /media/INTERNAL /media/TOMTOM
```

Start the installation of Tomtom HOME:
```
wine /media/INTERNAL/InstallTomTomHOME.exe
```
(or right-click the installer, and choose to open with wine)

I can now open Tomtom HOME from the start menu.
But the application doesn't detect my GPS.

Wine is configured with D: pointing at /media/INTERNAL
I have installed Total Commander 7.50a just to check that wine has set up the drives correctly - and I can browse the GPS just fine from there.

Any ideas why TOMtom HOME is not picking up the device?

---

### Post by wreinders on 2009-12-28
Same problem with me.
TomTom HOME installed succesfully, but after connection of my TomTom XL IQ Routes the program doesn't see any connected device.
The device seems to be properly mounted as /media/INTERNAL/ (identified as the wine D: drive).

---

### Post by maspin on 2009-12-28
I work with TomTom. There aren't really any approved solutions for TomTom Home. But, if you contact Customer Support, and very nicely inform the people you speak with that you would like them to pass your message that you would like Linux support, it will eventually make an impact.

In the mean time, there are a few workarounds

Applications can be manually installed from .cab files. Not all application versions are readily available for all devices. If you do need to update your application though, contact Customer Support, they will ask for your application version, and can usually send you the appropriate .cab files (and instructions) to install them on your device.

If you have safety camera files, you can go to [www.tomtom.com/plus/mypois.php](www.tomtom.com/plus/mypois.php). Here you can manually download .zip files of your safety camera files, and install them on your device (if you have paid for them, they will work on your linked device).

Some voice files you can probably find online with enough searching,and copy in to your 'voices' folder, or 'LoquendoTTS' if you have Text-to-Speech though 3rd party additions can be buggy sometimes, especially if there is a large amount of them.

Maps, however, can only be downloaded from TomTom Home.

If anyone comes up with a good (somewhat easy) solution, let me know!

---

### Post by jedistorm on 2010-01-10
I Sent them an email as well.

---

### Post by nisbeam on 2010-01-30
Same here, TomTom Home runs fine under Wine but although the device is recognised as E: /media/INTERNAL Home does not detect it.

Anyone know if there is any sort of retry anywhere in Home? or does it try to re-connect somehow.

Thanks.

---

### Post by cdurst on 2010-02-01
I think the main problem with running TomTom Home under Wine, is that it really wants to talk to the TomTom directly over USB and the current standard Wine releases do not have USB support built-in.

There are, however, some source code patches that purport to add USB support using libusb.  You'll find them here: [http://wiki.winehq.org/USB]("http://wiki.winehq.org/USB").

Personally, I have given up on the Wine approach for now since I was able to get it working using WinXP in a VirtualBox, but I'd love to hear if it works with the Wine USB patches.

---

### Post by abou ali on 2010-02-18
If ppl, like me, who don't own a Sat Nav yet, but considering to have one that has support for a Linux (ubuntu) version of the Desktop Kit, where should I send an email?

I think my case would be considered even more favourably from TomTom, as they didn't get my money yet.. and to be honest, if some other maker provide a Linux kit, I'll go for the other brand... so they have advantage in providing support for Linux quickly.

---

### Post by maspin on 2010-02-19
To contact support, [www.tomtom.com/368](www.tomtom.com/368).
There are steps to submit a case on the website.

---

### Post by emarkay on 2010-02-22
My GF has one (I can read maps, thank you) and find it horrid that there is no possibility of even a kludge to get this thing working in Ubuntu!

It's an XL 325SE, and I just sent an email to them to suggest thad since "many users are finding Microsoft's security and licensing issues untolerable, Ubuntu Linux with the various Windows emulators has provided near 90% coverage of all Win apps."

---

### Post by jumplinuxforum on 2010-03-19
Please affiliate at this group: [http://www.facebook.com/group.php?v=wall&gid=107059599320763](http://www.facebook.com/group.php?v=wall&gid=107059599320763) :) thanks!

FB should be the right way for solving this!:popcorn:

---

### Post by emarkay on 2010-03-20
> **jumplinuxforum said:**
> Please affiliate at this group: [http://www.facebook.com/group.php?v=wall&gid=107059599320763](http://www.facebook.com/group.php?v=wall&gid=107059599320763) :) thanks!

FB should be the right way for solving this!:popcorn:


Facebook is for teenagers, poseurs and the easily amused ("Ooh ooh, look at me and comment on what I just did!") Please don't encourage the migration from real open communication to this self-inflated one-way medium.  

And yes I had a FB page for a few months; I abandoned it. (For example, how can you equally have everyone at the same level of awareness and interest without offending or boring - that's why some of us are only "casual friends.")

---

### Post by Zill on 2010-03-20
> **abou ali said:**
> If ppl, like me, who don't own a Sat Nav yet, but considering to have one that has support for a Linux (ubuntu) version of the Desktop Kit, where should I send an email?

I think my case would be considered even more favourably from TomTom, as they didn't get my money yet.. and to be honest, if some other maker provide a Linux kit, I'll go for the other brand... so they have advantage in providing support for Linux quickly.
I actually *do* own a Garmin SatNav but, despite repeated requests, Garmin apparently have no interest in providing any support at all for Linux users.

This means that I am unable to update the Garmin map data - I have been "Linux only" for years now and have no access to a Windows system.

Garmin and TomTom etc please take note that when I do replace my SatNav it will be with one that has Linux support!

---

### Post by kc8hr on 2010-03-24
> **Zill said:**
> <snip>
Garmin and TomTom etc please take note that when I do replace my SatNav it will be with one that has Linux support!
Please let us know when you _do_ find a GPS device manufacturer that supports Linux!

---

### Post by DeLiK on 2010-05-17
I own a TT 930, and I've contacted the TT support in both ways.
One as a user that already owns a TT, the other (with a newly registered user) as user converted to Linux who is willing to buy a TT 930.

Let's see to who will they answer first, and what will be the answers.

:popcorn:

---

### Post by danellisuk on 2010-11-11
This is the response I received from TomTom support:-

> 
Dear Daniel,

The reference number for your query is XXXXXX-XXXXXX.

Thank you for taking the time to contact TomTom Customer Support. My name is Sophia and we are always happy to help.

Please provide me an opportunity to assist you.

Let me assure you that I will serve my best to resolve this query.

I truly understand your concern regarding operating TomTom device on Linux.

At TomTom we do try to provide the best qualitative TomTom services and TomTom products to our valued customer.

But unfortunately we do not yet have any TomTom Home application which can be installed on Linux (Ubuntu).

It may be the case in the future we will have TomTom Home for Linux operating system.

Please view our website regularly for updates.

You can also register to receive our Email Newsletter by logging onto your account via the website and click on Support -> My Profile and then tick the options for 'Newsletter categories'.

The maps that we currently have available can be found by clicking on the link below:-
[http://www.tomtom.com/products/maps/](http://www.tomtom.com/products/maps/)

We have passed your query on to our product management team as we like to have customer feedback and are very much concerned to know our customers interested in.

You have also stated that you do not want to work on Windows; however we have TomTom Home application currently available for Windows and MAC operating system.

Please bear with us.

We require your patience and support on this.

As you are our valued customer, we always believe in serving you with best and quality TomTom services.

Thank you for your valuable time and for giving me an opportunity to assist you.

With Kind Regards

Sophia
The TomTom Customer Care Team


---

### Post by Zill on 2010-11-11
> **danellisuk said:**
> This is the response I received from TomTom support:-
Quote:

...You have also stated that you do not want to work on Windows; however we have TomTom Home application currently available for Windows and MAC operating system.

Sophia
The TomTom Customer Care Team 

Thanks for the update danellisuk.  It's good to know that TomTom think all we have to do is buy a Mac... ](*,)

---

### Post by C4RL0 on 2012-07-23
Hello. Sorry for digging out this old stuff but I thought the topic is as up-to-date as it was during its creation.
I just bought a TomTom VIA 135 and guess what... couldn't mount it with my Linux (Mandriva 2010).
Google led me to this thread, so I signed the petition and wrote the above suggested email to the TomTom support.
As a german proverb says: "Hope is the last to die".

---

### Post by bazzer on 2012-07-23
Don't apologise, Tomtom should be the ones apologising. Instead they're being shown up for the leeches they are. Take GPL for their own profit and give nothing back.

---

