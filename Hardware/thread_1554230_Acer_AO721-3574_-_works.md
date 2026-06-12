---
title: "Acer AO721-3574 - works?"
date: 2010-08-16
forum: Hardware
---

### Post by OldGaf on 2010-08-16
I am thinking of buying an Acer AO721-3574.

I have to send away for it and want to make sure that everything will work with 10.04 before I commit.

I have Googled it but have not found results for this model and k/ubuntu.

Concerns would be Video, wireless, sound and webcam support.

[Acer AO721-3574]("http://us.acer.com/acer/productv.do?LanguageISOCtxParam=en&kcond61e.c2att101=82466&sp=page16e&ctx2.c2att1=25&link=ln438e&CountryISOCtxParam=US&ctx1g.c2att92=843&ctx1.att21k=1&CRC=83346820#wrAjaxHistory=9")

---

### Post by OldGaf on 2010-08-22
My main concern would be:

Integrated ATI Radeon™ HD 4225 (384MB dedicated memory)

Hope I can get HW acceleration working....

---

### Post by Brian Holmes on 2010-08-29
I bought an Acer AO721-3574 with the ATI card and the AMD Athlon II Neo K125 processor. Despite many tries I was UNABLE to install 32-bit Ubuntu 10.04 on it (using the thumb drive method I use on my other machines). The install appeared to be successful, but on restart it would make three login sounds and hang at the login screen. 

Strangely enough, I WAS able to install Ubuntu Netbook Remix on it, so I think this must be a pretty minor problem. UNR is great on the little Acer so I'd say, go with it!

To get the wireless and ethernet connections going I downloaded the Alternate install disk on another computer, and since the AO721 has no disc drive I mounted the iso image using some mount scripts that I found (but I now realize it's probably easier to just use the already installed Archive Mounter). You can then install the wireless driver by using the Hardware Drivers panel in the Administration menu. You have to go looking for the Atheros AR851 ethernet driver on the net, then install it with the commands given in post # 6 in this thread (note you have to install the build-essential packets from Synaptic first):

[http://ubuntuforums.org/showthread.php?t=1476231](http://ubuntuforums.org/showthread.php?t=1476231)

There are two remaining problems though. First, neither sleep or hibernate works - a real inconvenience. Second, the wireless has to be enabled each time you boot up, so that slows things down considerably. Any advice on fixing these two problems would be greatly appreciated!

---

### Post by OldGaf on 2010-08-29
> **Brian Holmes said:**
> I bought an Acer AO721-3574 with the ATI card and the AMD Athlon II Neo K125 processor. Despite many tries I was UNABLE to install 32-bit Ubuntu 10.04 on it (using the thumb drive method I use on my other machines). The install appeared to be successful, but on restart it would make three login sounds and hang at the login screen. 

Strangely enough, I WAS able to install Ubuntu Netbook Remix on it, so I think this must be a pretty minor problem. UNR is great on the little Acer so I'd say, go with it!

To get the wireless and ethernet connections going I downloaded the Alternate install disk on another computer, and since the AO721 has no disc drive I mounted the iso image using some mount scripts that I found (but I now realize it's probably easier to just use the already installed Archive Mounter). You can then install the wireless driver by using the Hardware Drivers panel in the Administration menu. You have to go looking for the Atheros AR851 ethernet driver on the net, then install it with the commands given in post # 6 in this thread (note you have to install the build-essential packets from Synaptic first):

[http://ubuntuforums.org/showthread.php?t=1476231](http://ubuntuforums.org/showthread.php?t=1476231)

There are two remaining problems though. First, neither sleep or hibernate works - a real inconvenience. Second, the wireless has to be enabled each time you boot up, so that slows things down considerably. Any advice on fixing these two problems would be greatly appreciated!

wow.... this is a bit worrisome!
I am still waiting for mine to arrive.... should be any day now.
I have a small usb CD/DVD burner and will use it to try to install Kubuntu 10.04 64 bit.

How about H/W Acceleration? Was there a driver available?

---

### Post by Brian Holmes on 2010-08-30
Well, the proprietary FGLRX graphics driver for the ATI card can be activated when you go to Hardware Drivers in the Administration menu. As it says in the panel: "This driver is required to fully utilise the 3D potential of some ATI graphics cards, as well as provide 2D acceleration of newer cards." All the video applications I've tried work perfectly. Compiz produced some visual freakout on the desktop, but I don't think that has anything to do with the graphics card.

Though I'm not into games and don't push the limits of my computers, I do find the AO721 to be a very nice little machine, excellent screen and keyboard, extremely light and portable while also a great improvement over the classic 10-inch netboks that are so small and cramped. But the Athlon processor is new and apparently some of its details are not integrated into the Ubuntu core. I am really hoping for a fix on the sleep/hibernation issue...

---

### Post by Brian Holmes on 2010-08-31
Just to continue with the details: I got the speaker jack and mic working by upgrading ALSA according to this post:

[http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04](http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04)

However, no luck with Skype yet.... or that damn suspend!

---

### Post by Romus on 2010-09-07
Hi everybody.
I have Acer ao721 with Debian testing on. Everything work, but  touchpad scrolling not work. Have anybody the same problem? 
P.S. Skype works well, try to install linux-image-2.6.35.
P.P.S Sorry for my English.

---

### Post by OldGaf on 2010-09-08
> **Brian Holmes said:**
> I bought an Acer AO721-3574 with the ATI card and the AMD Athlon II Neo K125 processor. Despite many tries I was UNABLE to install 32-bit Ubuntu 10.04 on it (using the thumb drive method I use on my other machines). The install appeared to be successful, but on restart it would make three login sounds and hang at the login screen. 

Strangely enough, I WAS able to install Ubuntu Netbook Remix on it, so I think this must be a pretty minor problem. UNR is great on the little Acer so I'd say, go with it!

To get the wireless and ethernet connections going I downloaded the Alternate install disk on another computer, and since the AO721 has no disc drive I mounted the iso image using some mount scripts that I found (but I now realize it's probably easier to just use the already installed Archive Mounter). You can then install the wireless driver by using the Hardware Drivers panel in the Administration menu. You have to go looking for the Atheros AR851 ethernet driver on the net, then install it with the commands given in post # 6 in this thread (note you have to install the build-essential packets from Synaptic first):

[http://ubuntuforums.org/showthread.php?t=1476231](http://ubuntuforums.org/showthread.php?t=1476231)

There are two remaining problems though. First, neither sleep or hibernate works - a real inconvenience. Second, the wireless has to be enabled each time you boot up, so that slows things down considerably. Any advice on fixing these two problems would be greatly appreciated!

Unable to install wireless.... I have an alt install cd mounted via usb dvd. No drivers found :(

---

### Post by OldGaf on 2010-09-08
Well.... try as I might I was unable to get either network adapter running under kubuntu (32 or 64 bit).

I am running OpenSuse 11.3 (64 bit) and got both going.
Ethernet worked out of the box and I was able to get wireless going using the package manager.

I also have ATI H/W acceleration working and the desktop effects working.

all seems fine, but I am missing my Debian based Linux :(

I will probably try again in a few days.... unless I get used to this distro.

---

### Post by OldGaf on 2010-09-08
> **Romus said:**
> Hi everybody.
I have Acer ao721 with Debian testing on. Everything work, but  touchpad scrolling not work. Have anybody the same problem? 
P.S. Skype works well, try to install linux-image-2.6.35.
P.P.S Sorry for my English.

BTW.... touch pad is working fine under OpenSuse 11.3
I could not tap to select at first but then found it was disabled under touchpad configuration.... which by the way has ALOT of nice setting in it.

---

### Post by 9000cc on 2010-09-09
> **OldGaf said:**
> Well.... try as I might I was unable to get either  network adapter running under kubuntu (32 or 64 bit).

I have Ubuntu 10.04.1 amd64 running on my AO721. With wireless drivers, alsa updated and ATI hardware acceleration.

To  install I used the desktop image on a usb key/stick.. the livecd has  the Broadcom wireless drivers under restricted hardware drivers (System  > Administration > Hardware Drivers) once activated I was on my  wifi easily. I needed internet access to get an encrypted lvm2 up and  running on the hard disk before starting the installer.

Once the  installer finished I chose "Continue Testing" and then chroot into the  new install to add lvm2 and cryptsetup. At this point I also installed  the b43-fwcutter package to download the restricted firmware blobs etc.  so that the fresh install would have wireless access on first boot. I  still haven't tackled getting the ethernet working but it's not an  urgent concern for me.

If anyone wants my complete install instructions I'll post them if requested. In the mean time here are some notes:

-  I (accidentally) used the x86 desktop image to install the first time  around.. I got all the way through the install and then upon first boot  the keyboard/trackpad stopped functioning at the login prompt. Whether  this can be solved by setting the account to automatically login, I'm  not sure.. I didn't spend much time on that once I realised I had picked  up the wrong usb key.

- The amd64 desktop image works well..  provided I made sure to hit "H" to access the boot options menu.. select  the language, then press F6 to choose boot options, select "nomodeset"  and then hit escape to exit the options menu.. finally select "Try  Ubuntu.." to boot up.

- If you want to avoid having to chroot  etc.. you could use a usb network adapter temporarily to install the  restricted Broadcom drivers but for some that may not be an option. The  point is the drivers are available, and can be installed using only the  desktop livecd, but there are easier ways if you have access to them.


General thoughts:

-  I really like the hardware.. performance wise, battery life, screen  resolution and size all put it ahead of all the other Eee PCs, NC10s, HP  Minis I've had recently. But this is my first Acer and I'm not sure the  build quality is quite on the same level as some of the others.

- I love the textured lid on mine and the fact shiny plastic has been relegated to just the screen bezel.

- For fellow Canucks, I got mine at Costco as they have a good price on it (until the 12th of September) they are $399 plus tax.

-  Luckily I got mine at Costco as the first one I bought had an issue  with the HD such that the initial Windows boot/install couldn't complete  and the restore partition wouldn't wipe the main partition until after  it had booted once. Obviously no restore media was included so this was a  bit of a Catch-22.

- I configured the one I am typing this on  now with a 200GB partition for Windows (truecrypt system encrypted with  all my data/music/films) and a 20GB luks/lvm2 ubuntu install. Machine  worked flawlessly for 5 hours of my flight to London. Then the hard disk  died 2 hours before landing. Disk is totally dead.. pulled it out of  the machine (thanks to large bottom access panel) and tried it in a USB  enclosure. Not sure if it's a heat issue as the bottom of the laptop  gets quite warm or just a random bad drive out of a batch. Anyway.. put  in a temporary disk and dedicated the whole thing to Ubuntu as I don't  have restore media for Windows while on the road. Will return this AO721  when I finish my trip.. I'll probably get another one though..

---

### Post by OldGaf on 2010-09-09
9000cc --> very nice description.

So... had I used a live CD I would have had WiFi.... damn.... I always use the Alt install disks as I find it faster.

Now.... do I keep Suse.... with everything working, or do I go back and try Kubuntu.....

Can you tell me how well your touchpad works?
I seem to have many more options with this netbook under Suse like "Disable while typing".

I know under kubuntu 10.04 (32 bit) I had to fiddle with other netbooks (3 Acers and an HP Mini) and then they were still not 100%.

---

### Post by OldGaf on 2010-09-10
Wow.... installed Kubuntu 10.04.1 64 bit.

Mounted the live CD and located the restricted drivers folder containing the bcmwl deb, but was unable to install it due to "unable to install 'libc6-dev'"

I also booted to the live cd and installed the driver from the "Hardware Drivers" menu.

It did install the driver but I was unable to activate the wireless (no option) and the light did not come on. 

Sigh..... should have stayed on Suse..

BTW.... I do not have the extra and nice to have touchpad options under Kubuntu that Suse had.

---

### Post by OldGaf on 2010-09-10
I guess it is not suprising that I am having better luck with SUSE's KDE..... 

"KDE Desktop innovations
SUSE has been a leading contributor to the KDE project for many years, and now SUSE sponsors more developers to work directly within KDE than any other distribution. Hence, SUSE’s contributions in this area have been very wide-ranging, and affecting many parts of KDE such as kdelibs and KDEBase, Kontact, and kdenetwork. Other notable projects include:

KNetworkManager – a front-end to NetworkManager. 
Kickoff – a new K menu for KDE Plasma Desktop. "

If only it had the same amount of packages available...

---

### Post by OldGaf on 2010-09-10
Back on SUSE.... everything working again ):P

---

### Post by BLaZuRE on 2010-09-11
So, for all of you with a working copy of linux on AO721, how did you do it?

I've tried Ubuntu x86 and x64, both failed.  I either got it to hang, doing that intro Ubuntu sound over and over or got a black screen of doom, saying something about something not being reserved properly (memory?).

I tried with 10.04 with Ubuntu full install & net install.  Also with Fedora and Debian.  Though, I haven't tried netbook remix ....  Does 10.04.1 offer support for AO721?

P.S. For some reason, I get a balloon in Windows when coming out of sleep/hibernation(/lock?) saying port 5 of my USB devices could not be restarted.  Anyone having similar issues?  Which device could this be ... -_- (internal)

Edit: Oh, and I've tried USB install & CD install =(

---

### Post by OldGaf on 2010-09-11
> **BLaZuRE said:**
> So, for all of you with a working copy of linux on AO721, how did you do it?

I've tried Ubuntu x86 and x64, both failed.  I either got it to hang, doing that intro Ubuntu sound over and over or got a black screen of doom, saying something about something not being reserved properly (memory?).

I tried with 10.04 with Ubuntu full install & net install.  Also with Fedora and Debian.  Though, I haven't tried netbook remix ....  Does 10.04.1 offer support for AO721?

P.S. For some reason, I get a balloon in Windows when coming out of sleep/hibernation(/lock?) saying port 5 of my USB devices could not be restarted.  Anyone having similar issues?  Which device could this be ... -_- (internal)

Edit: Oh, and I've tried USB install & CD install =(

It was 10.04.1 that I was trying..... both 32 and 64bit.... no joy on the network drivers.

Grab openSUSE 11.3 live cd. Everything is working 4 me and I am already getting used to it.

If you really want to stick with ubuntu.... maybe give 10.10 a shot.

For me it is not worth putting that much effort into it as this is just my netbook.... I will keep Kubuntu on my main PC.

Once you get it working (under any linux distro) you will LOVE this netbook..... I have had an eeepc and an HP mini, and there are 3 other Acers in the house, but this it the best one I have used by far.

---

### Post by OldGaf on 2010-09-12
OK.... I am trying Kubuntu 10.10

Both nics are working fine.
However, now I have no sound and no H/W acceleration.

---

### Post by Romus on 2010-09-13
I will try to tell, how I installed Ubuntu10.04 on Acer AO721.
I put both &#1093;86 and &#1093;64, all worked well. I did a boot drive with the help unetbootin from Debian. The notebook has normally booted from it (before there was a case that wasn't loaded, the reason and hasn't clarified).
1. To make Ethernet it is necessary to install AR81Family-Linux.
2. To make wifi it is necessary to install compat-wireless.
3. To make a sound(headphones and microphone). I has found very good script here [http://ubuntuforums.org/showthread.php?p=6589810#post6589810](http://ubuntuforums.org/showthread.php?p=6589810#post6589810)
4. Is better to install 35th kernel from additional repos.
I hope that to somebody has helped.
P.S. Sorry for my English.

---

### Post by OldGaf on 2010-09-18
Well........ finally got 10.04.1 installed.

Kubuntu live would not work.... wifi was detected but would not connect.
Ubuntu live however DID work... go figure!

Booted to ubuntu live, installed wifi through Jockey and installed to the HD.

Rebooted and installed KDE4.... after tweaking a bit I have it how I like it. Just have to remove gnome and I will be left with Kubuntu.

So... why the hell did the Kubuntu live not work when the Ubuntu did... is all the same under the covers.... just diff window managers....

---

### Post by OldGaf on 2010-09-18
> **OldGaf said:**
> Well........ finally got 10.04.1 installed.

Kubuntu live would not work.... wifi was detected but would not connect.
Ubuntu live however DID work... go figure!

Booted to ubuntu live, installed wifi through Jockey and installed to the HD.

Rebooted and installed KDE4.... after tweaking a bit I have it how I like it. Just have to remove gnome and I will be left with Kubuntu.

So... why the hell did the Kubuntu live not work when the Ubuntu did... is all the same under the covers.... just diff window managers....



Actually.... everything but mic is working....

---

### Post by Romus on 2010-09-20
Ubuntu 10.4.1:
Touchpad not work, Ethernet not work, nothing changed.

---

### Post by Romus on 2010-09-20
Somebody tell me, please. Touchpad scrolling working just in OpenSuse?

---

### Post by OldGaf on 2010-09-20
> **Romus said:**
> Somebody tell me, please. Touchpad scrolling working just in OpenSuse?

I had to do nothing for the touchpad in any of my attempts to install Ubuntu / Kubuntu except turn on tapping in the touchpad settings. Have you checked the settings?

The only thing that OpenSUSE has over K/Ubuntu is extra settings like "deactivate touchpad while typing".

Also, how did you install the OS.... from a live CD ?

---

### Post by Romus on 2010-09-21
tapping works out of the box. Scrolling not working. I installed ubuntu  every time from usb stick. First time i installed ubuntu 10.04 x86 from usb stick without any problems, but Ethernet, wifi, touchpad scrolling not worked. Ethernet and wifi are working well now, but nether ubuntu nor debian touchpad scrolling not worked. Now i have debian squeeze on Acer, everything work perfectly, but scrolling not working and i tried to install gsynaptics, and change xorg.conf. Anyway synaptics touchpad recognized like PS/2 mouse and using driver mice.

P.S. I've changed kde on gnome, because after installing new version of ati-driver i can't turn on composition, when i tried to do systemsettings - desktop kde crashed. This is a kde-bug. It was not the basic reason why I have passed to gnome.   
P.S. Sorry for my very bad English :)

---

### Post by OldGaf on 2010-09-22
> **Romus said:**
> tapping works out of the box. Scrolling not working. I installed ubuntu  every time from usb stick. First time i installed ubuntu 10.04 x86 from usb stick without any problems, but Ethernet, wifi, touchpad scrolling not worked. Ethernet and wifi are working well now, but nether ubuntu nor debian touchpad scrolling not worked. Now i have debian squeeze on Acer, everything work perfectly, but scrolling not working and i tried to install gsynaptics, and change xorg.conf. Anyway synaptics touchpad recognized like PS/2 mouse and using driver mice.

P.S. I've changed kde on gnome, because after installing new version of ati-driver i can't turn on composition, when i tried to do systemsettings - desktop kde crashed. This is a kde-bug. It was not the basic reason why I have passed to gnome.   
P.S. Sorry for my very bad English :)

wow.... not sure what is going on there.... is it 10.04.01?

Edit:
Sorry... I see it is....

This is very odd... have you checked the touch pad settings?

---

### Post by Brian Holmes on 2010-09-27
Has anyone got suspend working on the AO721?

I have everything working on my Netbook Remix 10.04 EXCEPT suspend. I tried installing 10.10 Beta on a separate partition, it is an easier install because the ethernet works out of the box and you get the wifi driver directly from the additional drivers menu. However, suspend still does not work. The computer appears to go to sleep, the screen goes dark and I get a flashing orange light, but then it won't wake up.

I would be very curious to know whether suspend works for anyone else, and especially, how you got it working.

thanks! BH

---

### Post by stillaway on 2010-10-02
Same result here -- everything is working except suspend.

I have tried 10.04, 10.10 and am currently using Debian experimental with 2.6.35.  I will try 2.6.36 shortly when it is out of RC, but I am suspecting it is a BIOS issue and we are going to have to wait for a BIOS update from Acer.


If anyone finds out anything else, or comes up with a method to fix this I would love to hear it.

- Steven

---

### Post by sbraz on 2010-12-25
i have ubuntu 10.04 running right here.

1. i had lockups problems at boot after installing too, solved adding "nomodeset" to kernel options. after that i've downloaded the last fglrx from amd.com and everything went fine after a bit of trouble: it appears that kernels version 2.6.36+ breaks fglrx. 2.6.35-22-generic works fine.
also, installing 10.10 "fixes" this problem.

2. mic problems are solved by removing pulseaudio and installing esound. to regain keyboard volume controls i mapped these commands to the appropriate keys:
amixer -c 0 sset Master,0 toggle
amixer -c 0 sset Master,0 2+
amixer -c 0 sset Master,0 2-
installing gnome-alsamixer helps too :)

3. i had problems with the wired card, fixed by apt-getting kernel 2.6.35-22-generic. wireless have been swapped with an atheros chip but i remember it worked out of the box.

4. i'm still trying to solve some troubles with that alps touchpad... i'll do that later. :) 

5. cpu seems to run hotter than it should, i saw 70°C while recompiling a kernel... and it's winter. turns out that many acer laptops have troubles with fan control.

6. i am testing for hibernate (i don't like suspend, it's disabled in kernel), rebooting now...

---

### Post by sbraz on 2010-12-25
hibernate WORKS! to do that, you'll have to recompile a kernel of your choice and disable ACER_WMI as suggested on some guides.

make menuconfig
device drivers -> X86 Platform Specific Device Drivers -> < >   Acer WMI Laptop Extras

as i said before i'm using a customized 2.6.35.10 kernel.

**[SIZE="5"] edit [COLOR="Red"]i am totally wrong, see my next post[/COLOR][/SIZE]**

---

### Post by sbraz on 2010-12-28
after two days, i think i've compiled at least 30 kernels to trace the hibernate/resume problems on my 721:

1. hit the hibernate button, display turns off, no data is written on disk, system hung, forced poweroff fixes the problem, on reboot networking is disabled:
turns out that APIC is not working well on this machine, disabling it makes it successfully dump ram data on a swap partition provided there's enough space to do that (i have a 2GB swap partition).
resuming works with "radeon" driver, for fglrx read below. 
```
sudo menuconfig
Processor type and features  --->
[ ] Local APIC support on uniprocessors
```
networking is disabled because there are some scripts which among other things disables networking _before_ issuing the actual ACPI suspend, and does the opposite after a _successful_ resuming of the system kernel.

2. wifi off on resume, requiring three "wifi on, wifi off" cycles of Fn+F3 button:
solved by disabling ACER_WMI module.
```
make menuconfig
device drivers ->
[*] X86 Platform Specific Device Drivers  --->
< > Acer WMI Laptop Extras
```


fglrx WON'T RESUME, xorg.log says this: 
```
(WW) Falling back to old probe method for fglrx
(II) Loading PCS database from /etc/ati/amdpcsdb
(--) Chipset Supported AMD Graphics Processor (0x9712) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:17:0) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:18:0) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:18:2) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:0) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:2) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:0) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:1) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:2) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:3) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:4) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:22:0) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:22:2) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@1:5:1) found

........

(EE) fglrx(0): ACPI: DRM connection failed

........

(WW) fglrx(0): board is an unknown third party board, chipset is supported
(EE) fglrx(0): ACPI: DRM connection failed
(WW) fglrx(0): Hasn't establisted DRM connection

........

(WW) fglrx(0): No DRM connection for driver fglrx.

........

(EE) fglrx(0): atiddxDriScreenInit failed, GPS not been initialized. 
(WW) fglrx(0): ***********************************************************
(WW) fglrx(0): * DRI initialization failed                               *
(WW) fglrx(0): * kernel module (fglrx.ko) may be missing or incompatible *
(WW) fglrx(0): * 2D and 3D acceleration disabled                         *
(WW) fglrx(0): ***********************************************************
(II) fglrx(0): FBADPhys: 0xc2900000 FBMappedSize: 0x10000000
(II) fglrx(0): Reserved 0x02900000 bytes of sideport memory for power saving
(EE) fglrx(0): Failed to map FB memory
(II) fglrx(0): === [xdl_x750_atiddxScreenInit] === end

Fatal server error:
AddScreen/ScreenInit failed for driver 0
```



i'll begin testing if there's a working driver version in three... two... one... i'm going to bed! :D

---

### Post by sbraz on 2010-12-28
freeze after install: [https://bugs.launchpad.net/ubuntu/+bug/661637](https://bugs.launchpad.net/ubuntu/+bug/661637)

suspend/resume [https://bugs.launchpad.net/ubuntu/+bug/642091](https://bugs.launchpad.net/ubuntu/+bug/642091)

---

### Post by Brian Holmes on 2011-01-02
Thanks Sbraz!

I finally solved my suspend problem by following your link to the bug page, and then following another link I found there:

[http://www.theplatform.info/user/mateibota/view/linux-suspend-hibernate-fix](http://www.theplatform.info/user/mateibota/view/linux-suspend-hibernate-fix)

What this does is disable ACPI and enable APM in its place. Works perfectly for me. Instructions below.

Now, after using Ubuntu for five or six years I am not longer afraid of the terminal but I am not a programmer and I have not been able to implement your instructions for disabling the acer_wmi function that kills the wifi when the computer suspends. Could you give the full set of commands to do that? It would be most appreciated.

thanks again, Brian

*****

Fixing suspend on Acer AO721-3547, courtesy of "ThePlatform.info":

STEP 1:  Modify the parameters of the GRUB configuration file.

sudo nano /boot/grub/grub.cfg

STEP 2: Look for the line with the information about your kernel.

STEP 3: After "quiet splash" add the following parameters.

    * noacpi apm=on noapic
    * press CTRL + O to save

STEP 4: Install cpufreqd to maintain CPU power saving and scaling capabilities.

sudo apt-get install cpufreqd

STEP 5: Reboot your machine and test SUSPEND and HIBERNATE

---

### Post by sbraz on 2011-01-03
> **Brian Holmes said:**
> Thanks Sbraz!

I finally solved my suspend problem by following your link to the bug page, and then following another link I found there:

[http://www.theplatform.info/user/mateibota/view/linux-suspend-hibernate-fix](http://www.theplatform.info/user/mateibota/view/linux-suspend-hibernate-fix)

What this does is disable ACPI and enable APM in its place. Works perfectly for me. Instructions below.

i think i've already tried the "noacpi" with no success :( but i'll try again using your instructions. :)

are you successfully suspending/resuming using **fglrx**? so far that's the only remaining problem on my 721, no matter what driver version i use it keeps blackscreening when starting X.

> I have not been able to implement your instructions for disabling the acer_wmi function that kills the wifi when the computer suspends. Could you give the full set of commands to do that? It would be most appreciated.

if you are running a stock kernel from the repository, the output of "sudo lsmod |grep acer" should show you an "acer_wmi" module. in my case it doesn't because i've compiled a kernel from source without that module.

to disable/remove/prevent from loading a module:

1. compile a kernel without that module. (my instructions from my previous post are for this method)

or 

2. sudo nano /etc/modprobe.d/blacklist.conf
add a line somewhere with "blacklist acer_wmi" without quotes.

---

### Post by sbraz on 2011-01-03
it appears that i refused to understand what i read about disabling ACPI, as i've just tried hibernate/thaw and it works. just like that.
:popcorn:

thanks Brian Holmes for pointing me into the right direction. :KS

---

### Post by Brian Holmes on 2011-01-10
Well, this is great, the main problem of suspend/resume has been solved!

Occasionally I do get freezes on suspend, but only occasionally.

I did try blacklisting acer_wmi as indicated, and it did keep my wireless powered up on resume, but other connection problems appeared and so I went back to the previous configuration. All I have to do is push Fn/F3 on resume and everything works fine.

best of luck to all 721 users!

Brian

---

### Post by sbraz on 2011-01-10
actually i forgot about this thread.

the hibernate/thaw operation worked just ONE time, maybe luck or maybe it loaded the "radeon" instead of "fglrx" driver after rebuilding my kernel who knows.. :(
at the very end, after extensively testing the opensource radeon driver, i've decided to use acpi instead of apm, fglrx 10.12 and sacrifice S1 S3 and S4 functions (disabled via kernel compiling).

what happens to you with acer_wmi blacklisted is strange thanks for the report: are you sure it stays unloaded after resuming your system? you can check this typing "lsmod |grep -i wmi". if it's still therek, something else has to be done to make it stay out of the system, in my opinion kernel rebuild is often a good option. :)

---

### Post by OldGaf on 2011-03-18
Sometimes the bottom of the the screen is "non responsive".

An easy way to test it is to open Firefox and go to facebook. Now switch Firefox to full screen. Now try to click on the "chat" tab on the bottom right.

Anyone else getting this?




[IMG]http://www.oldgaf.com/pics/nial-446472.png[/IMG]

---

### Post by sbraz on 2011-03-19
i can't test this as i don't have FB anymore. :) 

_have you tried the newest ati fglrx drivers?_ atm it's 11.2.

i'm using a custom 2.6.37.4 kernel based on the latest official ubuntu kernel configuration with the "nohpet" kernel option and everything works (including suspend, hibernation, resume and thaw) exept touchpad's scrolling.
**please note** that at least the last two kernels available from repository works fine too, even if it's not "optimized" for this specific hardware.

kernel 2.6.38 gave me some troubles with proprietary ati drivers... can't figure out why yet. :)

---

### Post by OldGaf on 2011-03-19
[QUOTE=sbraz;10576089]i can't test this as i don't have FB anymore. :) 

_have you tried the newest ati fglrx drivers?_ atm it's 11.2.

well.... I managed to blow up the video.... man it is tiring fighting with video in linux.....

Oh well... I did install opensuse 11.4 on another partion and the issue is gone.... tho the wifi will not work :(

Will continue the fight with the Kubuntu partion tomorrow.

---

### Post by sbraz on 2011-03-21
> **OldGaf said:**
> well.... I managed to blow up the video.... man it is tiring fighting with video in linux.....

i understand, i've fixed things since i got this lovely laptop! :D

anyway, if you are stuck in text mode as i was months ago, try running this script from superuser (i've copied this from a script i've used when i was trying to fix this damn ati driver... i was rebooting like 1000 times/day lol):

```
/usr/share/ati/fglrx-uninstall.sh  # (if it exists)
apt-get remove -y --purge fglrx*
apt-get remove -y --purge xserver-xorg-video-ati xserver-xorg-video-radeon
apt-get install -y xserver-xorg-video-ati
apt-get install -y --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
dpkg-reconfigure xserver-xorg
```

okay, you now should be able to boot and start the X server.

now to install fglrx, open a terminal and type "sudo -i" to get superuser privileges:
"cd /*wherever you have downloaded the ati .run file*/"
"./ati-driver-installer-11-2-x86.x86_64.run --buildpkg Ubuntu/maverick" [COLOR="Red"]_OR_[/COLOR] "--buildpkg Ubuntu/lucid" ... depends on your distro. :)
"dpkg -i *.deb"

if there are no obvious errors the drivers are installed.

i don't know if it's optional or not but another command would be 
"aticonfig --initial". i run this in the past, i don't know if it's necessary.

please note that you CAN select the single user runlevel called "recovery" in grub2 when booting to gain root access in case of hard-crashes caused by the video driver.

i hope this helps. :)

---

### Post by OldGaf on 2011-03-21
> **sbraz said:**
> i understand, i've fixed things since i got this lovely laptop! :D

anyway, if you are stuck in text mode as i was months ago, try running this script from superuser (i've copied this from a script i've used when i was trying to fix this damn ati driver... i was rebooting like 1000 times/day lol):

```
/usr/share/ati/fglrx-uninstall.sh  # (if it exists)
apt-get remove -y --purge fglrx*
apt-get remove -y --purge xserver-xorg-video-ati xserver-xorg-video-radeon
apt-get install -y xserver-xorg-video-ati
apt-get install -y --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
dpkg-reconfigure xserver-xorg
```

okay, you now should be able to boot and start the X server.

now to install fglrx, open a terminal and type "sudo -i" to get superuser privileges:
"cd /*wherever you have downloaded the ati .run file*/"
"./ati-driver-installer-11-2-x86.x86_64.run --buildpkg Ubuntu/maverick" [COLOR="Red"]_OR_[/COLOR] "--buildpkg Ubuntu/lucid" ... depends on your distro. :)
"dpkg -i *.deb"

if there are no obvious errors the drivers are installed.

i don't know if it's optional or not but another command would be 
"aticonfig --initial". i run this in the past, i don't know if it's necessary.

please note that you CAN select the single user runlevel called "recovery" in grub2 when booting to gain root access in case of hard-crashes caused by the video driver.

i hope this helps. :)

Wow... thanks for the help!
I did not read this until after I had installed 10.10 .... which is working VERY well so far... I did not have to do anything "extra" and everything is working.....

Still have the same issue with the bottom of the screen when running some applications in full screen mode tho (did not have the issue with opensuse).

I will just live with it for now. This nice little netbook has become my main computer.

---

### Post by OldGaf on 2011-03-22
Actually had two little tweaks... one was the KDM screen was nasty if I logged out, the other was Dolphin would show the home folder as empty until I did a refresh.

Both fixes:

[http://ubuntuforums.org/showthread.php?t=1205382](http://ubuntuforums.org/showthread.php?t=1205382)

[http://ubuntuforums.org/showthread.php?t=1702106](http://ubuntuforums.org/showthread.php?t=1702106)

---

