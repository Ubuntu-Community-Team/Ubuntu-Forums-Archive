---
title: "Best laptops for Ubuntu?"
date: 2005-06-11
forum: Hardware &amp; Laptops
---

### Post by Chousuke on 2005-06-11
I'm going to buy a laptop, and I will not run Windows on it. Knowing the possible problems with Linux on laptops, my primary choice is an Apple 12" iBook on which I would run OS X. However, those things are pretty expensive. So, I'm here asking for recommendation for PC laptops which work near-flawlessly on Ubuntu as is. I did browse the wiki LaptopSurvey database, but It's categorised by maker/model, which makes finding a truly working laptop a pain.
Of a laptop I would require these qualities:

Affordability (preferably less than 1000 euros)
Good battery life (most PC laptops I've seen advertise 1.5 to 2 hours, while the iBook advertises 6 hours!)
screen/graphics working perfectly.
suspension (to ram/disk) working reliably and as good as possible
Ethernet and sound out of the box.
WLAN as good as possible. No wrapped windows drivers.
the graphics card  does not have to be powerful. (Maybe nvidia, since ATI's binary drivers are crappy. The open drivers for the newer cards are getting better though. Alternatively, an ATI supported by the old and stable OS drivers.)
USB
Lightweight. 15" screen tops, since anything over that is too big.
a DVD burner would be a huge plus

I _am_ willing to work to make it work, but the less work there is, the better. ;)

Recommendations are welcomed and greatly appreciated. Thanks in advance.

---

### Post by kiddyfurby on 2005-06-11
i m using a centrino notebook and preety much everything is working out of the box

a few minor problems are:
the 3d mode of intel 855 is quite slow in hoary (2d mode is fine)
suspend mode not working out of the box, not sure whether this can be fixed or not
1394 may not be working (i never use it)

Things working after hoary installation
wlan (old centrino use 2100, which is working well now, not sure abt 2200 used by new centrinos)
sound
display
touchpad
lan...


so i think a centrino notebook can't be too wrong for linux

---

### Post by sb73542 on 2005-06-11
I am extremely partial to IBM laptops because they are durable and well designed.  They have a huge user-base, so you can easily find cheap accessories, such as drive bay components, and they are also well supported by Linux.

---

### Post by phen on 2005-06-11
but ibm is way to expensive, if youre looking for a system around 1k euro.

there is a special ubuntu version for hp laptops. I am using it, and it works fine.

[http://ubuntuforums.org/showthread.php?t=35244](http://ubuntuforums.org/showthread.php?t=35244)

cheers,
kai

---

### Post by dpacket on 2005-06-11
I have a toshiba satellite L serie, everything works fine except the battery monitor, for the wireless just install ndiswrapper.  :-)

---

### Post by sb73542 on 2005-06-11
Yes, IBM's aren't cheap new.  But I have a used Thinkpad that I am very happy with, they can be obtained very cheap "off corporate lease" as resellers often call them, usually in very good condition.

---

### Post by luca_linux on 2005-06-11
I think the laptop surely has to be centrino-based and to have a nVidia graphic card: their linux driver is better than the ATI one (ATI proprietary driver (a.k.a. flrgx) has suspension issues.
Ethernet is not a problem.
As for wireless I can say that ipw2200's open drivers work just great and are getting better and better step by step.
I suggest IBM, since one of their goals is to make their laptops linux well supported.

---

### Post by TimL on 2005-06-11
I have an Acer Aspire 1520, which works pretty well with Ubuntu.

Sound & graphics (nVidia) work out of the box. The nVidia driver obviously improves the graphics performance, but it was a pain to set up the resolution under X. I had to search around for weeks to find a proper 'Modeline' setting to get the widescreen res set up properly.

Ethernet works too, I haven't got any wireless kit so I can't test the built-in wi-fi, but I cant' see any evidence of it being detected and set up as a device.

I have no idea how to get the built-in bluetooth working, but it isn't a priority for me.

I would recommend this laptop.

---

### Post by milosz on 2005-06-11
I have got hp compaq 9020 and everything works fine, except modem ;)
I recomende this laptop!

---

### Post by elsewhere on 2005-06-12
I'm partial to Dell.  Not only has my old Inspiron 8100 survived drops, beatings and spilled coffees, but it ran Kubuntu flawlessly "out of the box".  Everything just worked (tm), including suspend to RAM, without any tweaking.  Also ran FC3/FC4 nearly as well, although suspend to RAM was a lot more finicky under Fedora. 

My next notebook will be a Dell as well, although nVidia graphics will be a must on whatever I get.

Just my $0.02...

Cheers,
KV

---

### Post by nocturn on 2005-06-13
A very interesting thread.  I'm looking for a Laptop as well.
Any experiences with an Acer Aspire 1524 or an HP nx9105?

---

### Post by Seti on 2005-06-13
Girlfriend's laptop is Toshiba Satellite A10, EVERYTHING works out of the box.
wireless chipset is Prism, works very well.
Sound works.
About 1.5 hour battery-life.
P4 M series proc.
512 Mgb RAM.
very nice LCD screen.
Hibernate option works too!
Only thing that could make it a lot better would be an nVIDIA grfx card, oh well.

---

### Post by Poul on 2005-06-13
ubuntu is best distro out there for  laptops so you generally shouldn't have any problems with most of the stuff I'd go for sony or asus as i belive that laptop has to look proffesional but if i were you i suposse that i'd choose dell especially in us and uk as you can get great deals.

---

### Post by Arthemys on 2005-06-13
[QUOTE=Poul]ubuntu is best distro out there for  laptops so you generally shouldn't have any problems with most of the stuff I'd go for sony or asus as i belive that laptop has to look proffesional but if i were you i suposse that i'd choose dell especially in us and uk as you can get great deals.[/QUOTE]
 How can any of IBM's ThinkPads **not** look professional enough? ;)

---

### Post by xain on 2005-06-13
My IBM Thinkpad R32 runs just fine. What amazed me the most was when I inserted the DLINK PCMCIA Wireless card and it connected to the net right away ! At the moment I'm having hibernation issues I hope to solve soon, for it's a mayor functionality for any laptop user.

---

### Post by calt129 on 2005-06-22
I have recently bought a Samsung X20 (model V, somehow rare), with P4 Centrino, i915 chip, 1GB ram, 15" 1400x1050, DVD+-RW DL, 2.4kg, 6pin Firewire, etc. A dream machine :-) Most of the things such as WiFi, Hibernation, DVD-Writer worked out-of-box, and since this is my first contact with Ubuntu, I am really impressed with this relatively younger distro.

I had to tweak a few things though. i915 and 3D acceleration seem to be a problem for many ppl, but actually it's pretty easy to configure. With vesa drivers I got glxgears 600 something, with native i915 3d-enabled driver I got 1100 something, though I dont need much 3d power. some program called 915resolution makes it possible. More info on this (in german) [http://faq.pathfinderteam.org/index.php/Diskussion:Samsung_X20#3D_Beschleunigung_unter_Xorg](http://faq.pathfinderteam.org/index.php/Diskussion:Samsung_X20#3D_Beschleunigung_unter_Xorg)

Another small problem was that wlan gets deactivated after screensaver/hibernation. A 3-liner corrects it: rmmod ipw2200; modprobe ipw2200; /etc/init.d/networking restart.

Another problem with post-hibernation was the resolution gets resetted to vesa-resolution, but a small change in /etc/acpi/resume.sh corrected it.

The only things I've not tested yet are: pcmcia (shouldn't be a biggie), modem & cardreader. Except those, all is working very smoothly. All in all, I can wholeheartedly recommend it! In Germany, the price is ~1400 euro. I'll post a detailed insallation instruction on this; one in german is here: [http://udoburghardt.de/udo/laptop2/index.shtml](http://udoburghardt.de/udo/laptop2/index.shtml)

---

### Post by XDevHald on 2005-06-22
I would have to say Dell, but not because I work for them, only because they have the correct specs for it to run correctly. I would say anywhere from the Inspirion 600m to the XPS Gen 2 would be the best way to go.

---

### Post by thestonegroover on 2005-06-23
I run a dual boot laptop with XP and SuSE (which runs fine) and I have a 5G partition which I am regularly reloading with different distros. I have tried Ubuntu in my old Sony Vaio box and it worked fine. I have recently bought a new computer (dual boot  as mentioned) but no matter what I do I cannot get the X server to work under Ubuntu (I actually was trying to get Debian to work, and thought I would install Ubuntu so I could get a good look under the bonnet/hood, but X has not worked on that either). My box is a Dell Inspiron with the new Intel 915GM chipset (IPW2200,Dothan and 1G DDR2 400Mhz SDRAM), and while very good (especially for the money) I have a feeling that a lot of tweeking etc will be required before Ubuntu will work properly (no reflection on Ubuntu, I couldn't get Gentoo or Slackware to run X properly either).

For the money, nothing comes close to Dell in terms of quality (good chassis, excellent high-end components etc). I am very happy with mine.

Before getting this Dell, I would have said get a Sony (think Apple but with Intel and Windows), but I can't see how I could be happier with it now.

---

### Post by calt129 on 2005-06-24
As a side-note:

In a recent survey about notebook repairs, conducted by a respected german magazine (c't 2005/2) among its 1871 readers, IBM, Apple & Asus are the 3 topmost big brands regarding customer loyalty (for the next purchase), lowest defect rate and technically competent repairs. Sony, Gericom and Toshiba are on the bottom, where Sony especially "shines" through its bad customer service, inferior repairs and defect-proneness. HP/Compaq, Dell, Acer, Fujitsu/Siemens are somewhere in the middle. Brands which have smaller market shares in Germany, but not necessarily bad ones such as Panasonic, Samsung, Benq, JVC are apparently classified under the "others/misc" pie-slice :-)

c't has somehow a different reader-profile than plain home-users, there should be many business users, admins and alike among those readers.

Conclusion: If you wanna find better community support, stick to the bigger brands  as they're more common, e.g. according to the survey above: IBM or Asus. And don't buy notebooks with ATI chip since their Linux support has a baaad reputation. Speaking German helps as well, because the german Linux community is really huge and some laptop-installation guides are only available in German! (not that I'm a German ;-)

Just that you kow.


ps: I've used IBM, Maxdata, Acer, Dell and Samsung (P10) before; now I have my 2nd Samsung (X20). Until now, I was only happy with IBM & Samsung.

---

### Post by petard on 2005-06-24
I dug up an old Sony Vio PCG-XG500.  It has 512M Ram and a P3-700 Mhz CPU.  Ubuntu installed flawlessly.  I had the wireless running as soon as I plugged it in.  To get somewhat rewspectable performance I had to lay off the urge to install themes and other "eye-candy".  But for work related purposes, this thing is great.  I have OpenOffice, Remote Desktop, and Firefox.  Plus I can do nessus scans, and other network monitoring].  We're pretty much a RedHat and Window$ IT shop.  I couldn't get RedHat WS nor Fedora to load on this laptop.

I jumped on the Ubuntu bandwagon and I'm enjoying the ride....

---

### Post by palough on 2005-06-25
I have been a converted Xandros Business user and recently purchased the latest Xandros Business 3.0.  It is nowhere as nimble as Ubuntu and wireless LAN has been impossible to set up on my Clevo notebook, purchased only 2 weeks ago with all the latest gagets and hardware.  

Ubuntu installed EVERYTHING FIRST TIME except the wireless LAN (told me my Linksys wireless router was too slow to set up!) but first set up of it in the Control Panel and it runs like a Swiss Watch.  I am sold !.  So quick and easy.  

I can see why it came from nowhere to become the Number One Distro download. 

 Superb. Keep up the great work and to those who are worried about compatibility, I installed it on my daughters notebook, a cast off of mine, it installed flawlessly and again everything works.  Amazing.

By the way, Windows XP Professional can't determine all the hardware and I have to use the driver disc that came with the Computeter to install MOST of the hardware.  No such problems with Ubuntu. A 100% installation.

Now I will buy Crossover Office and I have the perfect system, the essential MS Apps like Visio, Photoshop CS will run flawlessly so, GOODBYE BILL GATES !

---

### Post by dizzie on 2005-06-27
I like threads like this....

Allow me to fill in :)

I own a Packard Bell laptop (R 6620) and everything works using Ubuntu v5.04 :D

Nothing is dodgy or needs tweaking with a out-of-the-box install, but customizing is a lifestyle, like ubuntu is :)

- Just my 5 cents....

Regards :D

---

### Post by nybble on 2005-06-28
[QUOTE=Chousuke]I'm going to buy a laptop, and I will not run Windows on it. Knowing the possible problems with Linux on laptops, my primary choice is an Apple 12" iBook on which I would run OS X. However, those things are pretty expensive. So, I'm here asking for recommendation for PC laptops which work near-flawlessly on Ubuntu as is. I did browse the wiki LaptopSurvey database, but It's categorised by maker/model, which makes finding a truly working laptop a pain.
Of a laptop I would require these qualities:

Affordability (preferably less than 1000 euros)
Good battery life (most PC laptops I've seen advertise 1.5 to 2 hours, while the iBook advertises 6 hours!)
screen/graphics working perfectly.
suspension (to ram/disk) working reliably and as good as possible
Ethernet and sound out of the box.
WLAN as good as possible. No wrapped windows drivers.
the graphics card  does not have to be powerful. (Maybe nvidia, since ATI's binary drivers are crappy. The open drivers for the newer cards are getting better though. Alternatively, an ATI supported by the old and stable OS drivers.)
USB
Lightweight. 15" screen tops, since anything over that is too big.
a DVD burner would be a huge plus

I _am_ willing to work to make it work, but the less work there is, the better. ;)

Recommendations are welcomed and greatly appreciated. Thanks in advance.[/QUOTE]
 i'm not sure about a real cheap one, but i'm using a Dell Inpsiron 9300 which is Centrino all the way, and you can get it on monthly financing, almost anywhere!....

**nybble**

---

### Post by zakili on 2005-06-28
i have Sony Vaio pcg-fr415s  ... all works fine on ubuntu 5.04, except modem ac97.

---

### Post by Ak37 on 2005-06-29
I use a Fujitsu 5010 subnotebook and Ubuntu runs great! Ethernet, Sound and external CD/DVD works out of the box. 3D support is a a little slow (I use xcompmgr to enable shaodwing, and it slows down Gnome), this isn't a gaming laptop anyway. Haven't tried the Modem/WiFi yet. 

The only major concern is the random lock-ups when accessing my External NTFS drive. :( That aside, Ubuntu is the best Linux distro I've ever tried!

---

### Post by atrus325 on 2005-06-29
In your price range, I had very good luck with [http://www.bestbuy.com/site/olspage.jsp?skuId=7024846&type=product&productCategoryId=cat01174&id=1099394652097](http://www.bestbuy.com/site/olspage.jsp?skuId=7024846&type=product&productCategoryId=cat01174&id=1099394652097)
before I decided to trade it in for a flashier compaq.  Everything Ubuntu ran out of the box, except the wireless card, which I got to work later.  I may have made a mistake in trading it in, even though all the specs on the compaq are better.

We'll see.

J.

---

### Post by gorkhal on 2005-06-30
I have a compaq presario 730 (got it on the cheap from ebay), only after buying did i fount out, numerous horror stories of this laptop and windows, and sadly they were all true. The lappy would freeze anytime, making for some very tense sessions of windows.

of course installed ubuntu (before which I obliterated windows), and its been running flawlessly, ubuntu set up everything correctly. No more crashes!!!

One gripe with Compaq P 730 though, the S3 graphics card is soo bad. 

Definitely get Dell though, if you got the $$$ to spare.

---

### Post by byen on 2005-06-30
well. i second petard. Bought a compaq presario 2100 US and using linux has been a pain. Most of the hardware included do not have easy support for linux. My Wifi broadcom card was a pain, my ATI radeon graphics card does nothing on linux and the monitor had to be tweaked to be recognized too. so... if compaq was on the list. Might wanna strike it out!
Some might differ but this is my experience.

---

### Post by nocturn on 2005-07-01
[QUOTE=byen]well. i second petard. Bought a compaq presario 2100 US and using linux has been a pain. Most of the hardware included do not have easy support for linux. My Wifi broadcom card was a pain, my ATI radeon graphics card does nothing on linux and the monitor had to be tweaked to be recognized too. so... if compaq was on the list. Might wanna strike it out!
Some might differ but this is my experience.[/QUOTE]

Compaq and HP sell the same machines.  Most of them have ATI cards and are a pain.

If you can manage to find one with Nvidia in it, it is highly likely it will work.

The same rule applies to all manufacturers.

---

### Post by uberlaff on 2005-07-10
[QUOTE=Chousuke]I'm going to buy a laptop, and I will not run Windows on it. Knowing the possible problems with Linux on laptops, my primary choice is an Apple 12" iBook on which I would run OS X. However, those things are pretty expensive. So, I'm here asking for recommendation for PC laptops which work near-flawlessly on Ubuntu as is. I did browse the wiki LaptopSurvey database, but It's categorised by maker/model, which makes finding a truly working laptop a pain.
Of a laptop I would require these qualities:

Affordability (preferably less than 1000 euros)
Good battery life (most PC laptops I've seen advertise 1.5 to 2 hours, while the iBook advertises 6 hours!)
screen/graphics working perfectly.
suspension (to ram/disk) working reliably and as good as possible
Ethernet and sound out of the box.
WLAN as good as possible. No wrapped windows drivers.
the graphics card  does not have to be powerful. (Maybe nvidia, since ATI's binary drivers are crappy. The open drivers for the newer cards are getting better though. Alternatively, an ATI supported by the old and stable OS drivers.)
USB
Lightweight. 15" screen tops, since anything over that is too big.
a DVD burner would be a huge plus

I _am_ willing to work to make it work, but the less work there is, the better. ;)

Recommendations are welcomed and greatly appreciated. Thanks in advance.[/QUOTE]
 Hey, just wanted to give you a heads up.  I have a Sony Vaio S260 and everything works right after install.  3D and all... here are some specs.  Because its not the newest S series, you can find awesome deals.  I got mine for $1150 US from the local circuit city.  Happy shopping!

13.3" wide screen
1.7ghz pentium M
512 ram
intel wireless
ATI Mobility 9200
60GB hard drive
4.2 lbs w/ battery

---

### Post by markdone on 2005-07-11
I am running Ubuntu on a Toshiba Sat. A35-S1592 and it works great.  No problems everthing worked out of the box (including wireless).  You should check the wireless compatibility [here.](https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards?highlight=%28wireless%29) 
If you are worried about battery life make sure that the processor you get is a mobile processor so that the processor frequency can be scaled to conserve power.  With my experience the more intel componets your laptop has the more likely it will work with linux.  I would also recommend that you get a Nvidia based card since the directions for the drivers are in the start-up guide[here.](http://ubuntuguide.org/#installnvidiadriver) 

Hope this helps,

Markd

---

### Post by MAMOHT on 2005-07-11
I have Fujitsu-Siemens Lifebook S7010 with xp installed on it. When I installed ubuntu on it, it had detecteall the hardware better than winXP :smile: (I had some wireless problems in win, but ubuntu solved them). So, I believe, ubuntu is more compatible and friendly, than win is for almost every type of notebook!

---

### Post by Chuckaluphagus on 2005-08-02
I just set up Ubuntu 5.04 on an Asus M3Np notebook.  Everything, and I do mean everything, works out of the box.  All hardware is detected, wireless network, ethernet and modem all work, video and sound are functional.  CPU throttling and ACPI are perfect.  I honestly couldn't ask for a better compatibiity.

The M3Np model is about a year old, but it's still a good working notebook, very well built and reliable.  Company webpage is here:

[http://www.asus.com/products4.aspx?l1=5&l2=25&l3=125&model=336&modelmenu=1](http://www.asus.com/products4.aspx?l1=5&l2=25&l3=125&model=336&modelmenu=1)

---

### Post by J2R on 2005-08-02
I have a Acer Aspire 1691WLMi, a most impressive laptop on which I have, alas, had to revert to Windows XP. 

Despite days of fiddling, I cannot get wireless networking (the internal Intel 2200BG) to work reliably with Ubuntu. I have tried various different versions of the IPW2200 native driver, as well as the ndiswrapper option, all without success (I often get a connection for a few minutes which then drops and cannot be reestablished without a reboot). I haven't got on to issues with hibernation, battery control, etc., yet, because the wi-fi has stopped me in my tracks.

It's a real shame - I'd much rather be using Ubuntu than the irritating XP. I've spent the last 18 months or so using Linux as my main desktop OS and I'm really missing it!

---

### Post by nocturn on 2005-08-02
[QUOTE=J2R]I have a Acer Aspire 1691WLMi, a most impressive laptop on which I have, alas, had to revert to Windows XP. 

Despite days of fiddling, I cannot get wireless networking (the internal Intel 2200BG) to work reliably with Ubuntu. I have tried various different versions of the IPW2200 native driver, as well as the ndiswrapper option, all without success (I often get a connection for a few minutes which then drops and cannot be reestablished without a reboot). I haven't got on to issues with hibernation, battery control, etc., yet, because the wi-fi has stopped me in my tracks.

It's a real shame - I'd much rather be using Ubuntu than the irritating XP. I've spent the last 18 months or so using Linux as my main desktop OS and I'm really missing it![/QUOTE]

I read somewhere that the driver for IPW2200 in Hoary is quite old and broken.
There are some tutorials on getting the newer one compiled (and copied over the older one, without compiling a new kernel).

Or, you could make an early switch to Breezy...

---

### Post by DanN on 2005-08-02
[Heres a link to one such tutorial](http://www.ubuntuforums.org/showpost.php?p=167782&postcount=46) , I actually just used it today on my nx6120 (I think its the Australian version of the nc6120, dunno though) and it fixed that issue right up for me, even got the wireless LED to work.  Ubuntu also works great on this model, I used the HP customised version and most things worked from install, had to set up the synaptics touchpad and fix wireless though.

---

### Post by luca_linux on 2005-08-02
Yes, and there's also this HowTo updated to the latest driver version: [http://www.ubuntuforums.org/showthread.php?t=26623](http://www.ubuntuforums.org/showthread.php?t=26623)

---

### Post by J2R on 2005-08-02
[QUOTE=luca_linux]Yes, and there's also this HowTo updated to the latest driver version: [http://www.ubuntuforums.org/showthread.php?t=26623](http://www.ubuntuforums.org/showthread.php?t=26623)[/QUOTE]

I'm afraid I followed this and still couldn't get wi-fi to work successfully. I tried driver versions 1.0.0, 1.0.4 and 1.0.6. As I mentioned, I could get things running for a few minutes and then the connection would drop. dmesg showed a 'firmware error, restarting' message but only a reboot would actually get it working again. (I did install the 2.3 version of the firmware).

---

### Post by shrimphead on 2005-08-02
I have installed Linux on about 4-5 different laptops in the last few months! and my latest aquisition, an IBM Thinkpad X21, with Hoary has been the nicest install I think I have ever done. as long as you remember to use apm and not acpi even the suspend functionality works flawlessly!

and for a P3 this system really flies!  :)

---

### Post by J2R on 2005-08-02
[QUOTE=shrimphead] as long as you remember to use apm and not acpi even the suspend functionality works flawlessly![/QUOTE]

How do you ensure that? And do you use Gnome/KDE, or have you gone for one of the much lighter weight window managers like XFCE?

---

### Post by SlackNerd on 2005-08-03
I have recently, due to budget constraints, picked up an [www.averatec.com](http://) 3250 from Walmart.  It was "only" $800.
They didn't have the one I wanted with the DVD burner but I"m sure that my experience will apply to that model also.

Literally, Ubuntu out of the box worked except for 2 things:

The Wireless network card.
The Touchpad.

A quick Google search and voila, here on the forums were the answers.

Next, I installed KDE (Kubuntu) because I'm partial to that flavor.  No worries there.  Next thing I know, I'm surfing the web and running my business from my favorite couch.

Hats off to the developers.  Home run for me.

---

### Post by eelozano on 2005-08-03
Dell Latitude  D600...works out the box with everything...not too terribly expensive either.

---

### Post by garner_nc on 2005-08-03
I have a Dell Inspiron 4100 which works well. Ubuntu found all hardware and configured properly.

---

### Post by Synner on 2005-08-03
I've installed it on one laptop, an HP Omnibook XE2.  Everything worked perfectly, except the resolution is stuck at 640.480.  I've been told modifiying the xorg.conf file would fix this.  Beyond that, though, not a single problem.

I also ran a live cd on a Dell Inspiron 2650 for a night.  everything, and I mean EVERYTHING worked flawlessly, and nearly twice as fast as Windows.  The Dell would be my first suggestion for a laptop, I'll probably have Windows removed by the end of the night.

---

### Post by neowhale on 2005-08-05
I'm using Toshiba A80 now. The problems I had were disable the hardware detection for pcmcia and need to install a patch to enable the network card.

---

### Post by vvlist on 2005-08-05
I have an IBM T40. Everything worked after the hoary install, even wireless worked fine. It's a centrino with an ATI graphics card. Hoary is the only linux dist. that 3D acceleration has worked on. It was $1600 two years ago, a little expensive, but definitely worth every penny.

---

### Post by bearbigears on 2005-08-06
i have a dell 8200 inspiron and ubuntu run very well on my laptop. even got the external volume controls to work. very pleased and microsoft free at last! free at last!

 \\:D/

---

### Post by johnmc on 2005-08-06
IBM - don't settle with anything less :D
(no i'm not an ibm salesperson ;-)

I got a T41 on which hoary is running just perfectly! Everything works out of the box - cudos to the developers!

---

### Post by poofyhairguy on 2005-08-06
Nothing beats HP:

[http://www.ubuntulinux.org/support/custom/hplaptops](http://www.ubuntulinux.org/support/custom/hplaptops)

For a few models the TRIED to make it so they would work with Ubuntu.

---

### Post by sneax on 2005-08-19
I have a Clevo M120W. Just technicaly I think this laptop is awesome, the screen is one of the best I ever seen (1280*800 on a 12.1' widescreen, small but so SHARP that you never notice it's so small!!!!). Hardware wise it's a Centrino, ram upto 512mb, intel integrated graphics (only downside), dvd writer possible, harddisk upto 80gig, intel wlan, lan, 2 usb, no firewire, infrared, no digital out but only headphones out and mic in.

That's it. Most of it can be customised. Clevo makes barebones and there are a lot of models out there who are actualy Clevo.

The 'lowest' series of Alienware (with the intel integrated graphics) is this laptop - a lot of others of Alienware are actualy Clevo too. Now on to the linux part: Ubuntu works flawless on my Promedion M120W, screen resolution recognised immidiately, plug and pluy usb works, dvd drive works, sound works, graphics work (though very slow glxgears rate, trying to fix it, having only 490fps), touchpad works and ACPI seems to work excellent too! (its cooling passivley most of the time)

I paid mine 1500EUR:
Centrino 1.7gighz
512MB
cd rw/dvd rom
win xp home (170EUR!)

I strongly advise going for the widescreen as it absolutely awesome, and very small - as big as an A4 paper though it performs very good and no problem to type!

---

### Post by TristanMike on 2005-08-19
Hi, I'm in Canada and want to get a laptop. But I've been told that if I buy a Dell off of their website, I won't be able to put Ubuntu on as my only OS. They said that Dell's are configured in such a way that you can only install the OS they want using their disks. 

How much validaty is there to this? Is it safe for me, a computer noob, to pick one up (keeping in mind it's nVidia and nVidia alone :) ). Or is there more involved than the Desktop setup?

Thanks in advance. T.M.

---

### Post by refdoc on 2005-09-08
I run 3 laptops under ubuntu

Oldest is a Packard Bell ipower 5542 (P4, 512MB, 40GB, DVD/CDRW, PCMCIA, 4xUSB, Firewire,InfraRed,svideo, cardreader, 64mb nvidea Intel537 modem, ethernet)

All but the infrared and the modem works now under ubuntu breezy absolutely fine. I am fiddling tonight more to get modem and irda working, maybe this is ok too. This laptop was expensive, is very heavy but is frequently available on ebay for currently  200-300 GBP second hand.

Next is a Dell Latitude 505 (Centrino, 512MB, 40Gb, DVD, 2xUSB, intel 3d mdem ethernet) I have not made much effort to get things going, am told that wireless shoudl be fine, but after a straight out of the box wartyintsallation without any fiddling  wireless and modem were the only two things not working.  In that spec it costed about 800 GBP

Finally an ibook G4 768MB DVD/CDRW, firewire, USB, modem, airport extreme. It runs as dual boot for MacOSX and Ubuntu hoary - out of the box everything but the modem and airport extreme worked fine. Sound required a little adjustement and is now crystal clear, sleep is fine. I understand some folks at gentoo got teh airport extreme to work, whiel the modem will probably not ever work.  Again, about 800 GBP

If I bought again a laptop it would be an ibook, dell or ibm. The Packard Bell was fine wrt Linux, but is simply too heavy.

Hope this helps

---

### Post by MetalMusicAddict on 2005-09-08
[QUOTE=poofyhairguy]Nothing beats HP:

[http://www.ubuntulinux.org/support/custom/hplaptops](http://www.ubuntulinux.org/support/custom/hplaptops)

For a few models they TRIED to make it so they would work with Ubuntu.[/QUOTE]
You would almost figure that they would use a different wireless chipset so their would be no hastle. :)

As for me I bought the cheap Dell Inspiron 2200. $580 US. Everything works great under Breezy (had video issue with Hoary) but the wireless which needs ndiswrapper. It actually runs REALLY nice. My 1st choice *was* a IBM though. :)

---

### Post by fenwik on 2005-09-08
[QUOTE=TristanMike]Hi, I'm in Canada and want to get a laptop. But I've been told that if I buy a Dell off of their website, I won't be able to put Ubuntu on as my only OS. They said that Dell's are configured in such a way that you can only install the OS they want using their disks. 

How much validaty is there to this? Is it safe for me, a computer noob, to pick one up (keeping in mind it's nVidia and nVidia alone :) ). Or is there more involved than the Desktop setup?

Thanks in advance. T.M.[/QUOTE]

Not valid at all

---

### Post by dbrine on 2005-09-16
I'm using a Toshiba S205. Works greats. P4 too I HIGHLY RECOMMEND

---

### Post by kamagurka on 2005-11-10
Everyone lauding Sony really needs to rethink. Vaios (as are most other Sony products) are overdesigned, badly assembled and overpriced pieces of crap wrapped in tinsel. Also, their service and general attitude towards customers is legendarily terrible.

---

### Post by bsbture on 2005-12-08
All right ,if you wanna buy IBM ThinkPad ,come to China !You can buy every thing without customs.smile

---

### Post by TimL on 2006-01-15
[QUOTE=TimL]I have an Acer Aspire 1520, which works pretty well with Ubuntu.

Sound & graphics (nVidia) work out of the box. The nVidia driver obviously improves the graphics performance, but it was a pain to set up the resolution under X. I had to search around for weeks to find a proper 'Modeline' setting to get the widescreen res set up properly.

Ethernet works too, I haven't got any wireless kit so I can't test the built-in wi-fi, but I cant' see any evidence of it being detected and set up as a device.

I have no idea how to get the built-in bluetooth working, but it isn't a priority for me.

I would recommend this laptop.[/QUOTE]


Just to add to this, in case anyone stumbles across this post, I have written up a how-to of setting up the widescreen display on an Acer Aspire 1522WLMi [on my site.]("http://tjl2.com/sysadmin/personal.html#nvidia")

---

### Post by Dave91 on 2006-01-15
im using a Compaq Armada m700;

It's about 5 years old (maybe even move, was given 2 of them by a friend)
Has Pentium 3 with 128mb of RAM - which runs like a dream with Ubuntu.

You can pick one of these up ebay for like 40 pound :D 

Or i will sell u a good enough condition one if u would like :D

Dave

---

