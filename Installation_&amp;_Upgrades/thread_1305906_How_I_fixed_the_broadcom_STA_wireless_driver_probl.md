---
title: "How I fixed the broadcom STA wireless driver problem in 9.10"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by lexpenrose on 2009-10-30
Ok, there's about 1 million people with the same problem : Broadcom STA Wireless driver problems since 9.10 ( worked for everyone in 9.04 ) 
Here's how to "FIX" it , more like a triple bypass : 

First of all , set your router to use WEP 40 bit, because WPA is seriously bugged still with Ubuntu

- Just after installing Ubuntu 9.10, make sure you use a WIRED internet connection ( using your onboard NIC , not wireless obviously since it doesn't work ) 
- Issue a "sudo apt-get update" on the terminal to update all the drivers etc. 
- Then go to System -> Administration -> Hardware Drivers 
And select the Broadcom Wireless STA Driver and click Activate.

That's the only way I got this working , I'm sure there's 100 other ways but at least this is a guaranteed way for people to fix their problems ( provided they have access to wired internet )

---

### Post by pulakka on 2009-10-30
I went the same way, but i would like to be albe to connect to my accesspoint using WPA.

Did anyone find a solution for this?

---

### Post by linthusiast on 2009-10-30
I am now posting from Ubuntu 9.10 via my Wifi STA (lspci - "Broadcom 4306") using WPA and getting full speed. For the record this did not work for me out of the box in 9.10, unlike 9.04 where it just worked.

I followed the following tutorial: **[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)**

However connecting the machine to a wired network or having a 9.04 machine at hand was not an option for me so considering I am dual booting with Windows 7, I accessed the web and downloaded the necessary files (3 in all) using that. Then I had the 3 files need on my NTFS partition which I could then mount and access when I rebooted in to Ubuntu.

In the above tutorial they suggest you jump through hoops to get b43-fwcutter, but you can directly download it from here instead: **[http://bu3sch.de/b43/fwcutter/b43-fwcutter-011.tar.bz2](http://bu3sch.de/b43/fwcutter/b43-fwcutter-011.tar.bz2)**

Then extract and build it in Ubuntu using the following
tar xjf b43-fwcutter-011.tar.bz2
cd b43-fwcutter-011
make

With the above tutorial, once I got to the stage where I rebooted my machine it automatically connected to my Wireless Profile (which uses WPA) that I had previously configured.

Hope this helps ;)

---

### Post by bhishan on 2009-10-30
Isn't this a big problem for people who have access to wireless internet only?

---

### Post by x2wdtoyotax on 2009-10-30
YES! I have an HP Mini 1030nr that uses a Broadcom BCM4312 802.11b/g (rev 01) wireless card. I do not have the option of connecting via a wired connection due to the fact that netbooks do not usually have an ethernet jack due their small form factor.  I have had to download the packages manually on a seperate system and transfer them to the netbook via usb.  I am to the point of activating the driver and I get stuck.  I click activate... the machine goes through the motions without any errors and returns back to the same window, with the driver still not activated. I am quickly losing patience! Any suggestions? 

BTW here is my original posts... following the steps I have taken to get this far. 

[http://ubuntuforums.org/showthread.php?p=8197228#post8197228](http://ubuntuforums.org/showthread.php?p=8197228#post8197228)

Any help will be greatly appreciated!

---

### Post by Haythayt on 2009-10-31
Same problem here (Dell Inspiron 1525,). None of the many solutions (reinstalling bcmwl-kernel-source etc...) so far helped me. And still Jockey did not install the Broadcom STA driver. Seems the bug was known prior to the release and its fix did not help in my case, e.g.:

[https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/443185](https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/443185)

So I did lose my patience. ;)

And I downloaded the broadcom driver myself and "installed" them.

First download the drivers here:

[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

Then follow this instructions:

[http://www.broadcom.com/docs/linux_sta/README.txt](http://www.broadcom.com/docs/linux_sta/README.txt)

Afterwards I could connect to my wireless network. Unfortunately this was not the case anymore after rebooting. lsmod shows neither "wl" or "lib80211" anymore.
Does anybody know how to add these modules permanently? (Adding to /etc/modules? And where do I have to put the wl.ko file then? Somewhere in /lib/modules/2.6.../.?)
And how may this interfere with Ubuntu's Jockey if it by any chance works again? For after loading the modules manually Jockey still does not show the driver activated...)

Thanks for your help...

---

### Post by superticky on 2009-10-31
> **x2wdtoyotax said:**
> YES! I have an HP Mini 1030nr that uses a Broadcom BCM4312 802.11b/g (rev 01) wireless card. I do not have the option of connecting via a wired connection due to the fact that netbooks do not usually have an ethernet jack due their small form factor.  I have had to download the packages manually on a seperate system and transfer them to the netbook via usb.  I am to the point of activating the driver and I get stuck.  I click activate... the machine goes through the motions without any errors and returns back to the same window, with the driver still not activated. I am quickly losing patience! Any suggestions? 

BTW here is my original posts... following the steps I have taken to get this far. 

[http://ubuntuforums.org/showthread.php?p=8197228#post8197228](http://ubuntuforums.org/showthread.php?p=8197228#post8197228)

Any help will be greatly appreciated!


I have the same problem, I also have a  HP Mini 1030nr.

By the way, the HP Mini 1030nr  DO HAVE a wired NIC, its just hidden, under a plastic cover on one of the side corners, look carefully, need to remove the plastic cover.

---

### Post by Sly_tom_cat on 2009-11-02
> **Haythayt said:**
> Same problem here (Dell Inspiron 1525,). 
Does anybody know how to add these modules permanently? 


I've added wl.ko also in /lib/modules/<kernel version>/kernel/drivers/net/wireless/
and got the wl.ko loaded after reboot. But it didn't help me - still have this issue unsolved on my Compaq 7620s laptop

---

### Post by superticky on 2009-11-02
I have solved the issue for me.

Steps:

- load the ubuntu 9.10 live with pen drive.
- after ubuntu loaded completely, go to hardware drivers
- select STA proprietary (the second one on the list)
- activate and it will work.
- now install the ubuntu into hard drive.
- after ubuntu is installed, go to  hardware drivers
- only one will appear, which is the one we need.
- activate buy it wont work (its okey for now)
- now Go to pool/restricted/b/bcmwl on Ubuntu Live USB pen drive. Double click into the .deb file in there, and REINSTALL that package. 
- go now again to hardware drivers.
- Now you can activate Broadcom STA driver, most cases you will see its already activated.
- now Wifi should work.

it worked for me on a hp mini.

please note: i founded another bug, after you have internet, if you do update/upgrade all, the new version of firefox wont work, it will say "bus error".

Thanks.

---

### Post by stevenw66 on 2009-11-04
I have an HP 1000. I have manually installed the drivers from broadcom (4312 chipset) and have activated after much work. Rebooted, still no wireless access. Everything looks fine but cannot discover wireless network SSID. Tried to configure manually, still no luck. Device Manager shows the device and drivers loaded and active with no issues. Is there something I need to do to get network manager to search for available open infrastructure SSID's? I've tried many other wireless tools and none of them can detect any wireless network SSID's. This worked well in 9.04 so what happened.

If anybody expects Ubuntu to overtake windows they better figure out how not to regress each release relative to network access and video!

---

### Post by jordbrill on 2009-11-04
> **superticky said:**
> I have solved the issue for me.

Steps:

- load the ubuntu 9.10 live with pen drive.
- after ubuntu loaded completely, go to hardware drivers
- select STA proprietary (the second one on the list)
- activate and it will work.
- now install the ubuntu into hard drive.
- after ubuntu is installed, go to  hardware drivers
- only one will appear, which is the one we need.
- activate buy it wont work (its okey for now)
- now Go to pool/restricted/b/bcmwl on Ubuntu Live USB pen drive. Double click into the .deb file in there, and REINSTALL that package. 
- go now again to hardware drivers.
- Now you can activate Broadcom STA driver, most cases you will see its already activated.
- now Wifi should work.

it worked for me on a hp mini.

please note: i founded another bug, after you have internet, if you do update/upgrade all, the new version of firefox wont work, it will say "bus error".

Thanks.


THANK YOU SO MUCH! this fixed my issue completely on my HP Mini 110!!!!

I cannot thank you enough!!!

---

### Post by sroland81 on 2009-11-05
I have an HP 6735s Laptop and installed a fresh copy of Karmic and went to Hardware Drivers and activated STA driver... then when restarted the Wireless LED does not even change to blue (on), it stays red (off)... In Hardware Drivers nothing appears.... and i got no wireless... lspci shows no wireless device BCM4311 like it used to be in Jaunty... what can i do about it?

Thanks,

Santiago.-

---

### Post by eighto2 on 2009-11-12
> **lexpenrose said:**
> Ok, there's about 1 million people with the same problem : Broadcom STA Wireless driver problems since 9.10 ( worked for everyone in 9.04 ) 
Here's how to "FIX" it , more like a triple bypass : 

First of all , set your router to use WEP 40 bit, because WPA is seriously bugged still with Ubuntu

- Just after installing Ubuntu 9.10, make sure you use a WIRED internet connection ( using your onboard NIC , not wireless obviously since it doesn't work ) 
- Issue a "sudo apt-get update" on the terminal to update all the drivers etc. 
- Then go to System -> Administration -> Hardware Drivers 
And select the Broadcom Wireless STA Driver and click Activate.

That's the only way I got this working , I'm sure there's 100 other ways but at least this is a guaranteed way for people to fix their problems ( provided they have access to wired internet )

Amazing, I've been going nuts over this for days. This is HUGE! Thanks

---

### Post by Rifester on 2009-11-12
I don't know if this will help anybody, but my broadcom 4311 card worked fine in the BETA version of 9.10.    I cannot get it to function at all in the released version.    I have clean installed the beta version and am now upgrading to the current release and my wireless is working.    Something must have gotten messed up between beta and release for those of us who have to use the STA wireless driver.

---

### Post by profgeek on 2009-11-13
I downloaded ubuntu unr 9.10, running it on a lenovo ideapad s10 (the first model).  I downloaded it fine, noticed the wireless problem, followed instructions and managed to install the bcmkernel from the USB pool.

Now the wireless driver shows up as a propriety driver in "Hardware Connections," but simply refuses to activate, no matter what I do.  I type in my password to authenticate, it begins trying to activate, closes the window, and leaves me back at the authentication screen.

I've tried reinstalling and rebooting like 10 times, used a wired connection to get updates, etc.

Nothing.

This is my first linux experience, and may well be my last.  If wireless doesn't work, what's the ******* point? Might as well use windows.

---

### Post by efflandt on 2009-11-13
Bootable Ubuntu 9.10 live/install on USB stick (booted on Dell Inspiron 6400 w/4311) does have the STA driver, but not activated.  When activated, it said I needed to reboot, (actually had to shutdown, and cold boot).  Driver then said activated, but not in use.

I found wl.ko under /lib/modules/2.6.31-14-generic/updates/dkms/
Not sure if necessary, but I did **sudo depmod -a** (may be necessary if manually copying wl.ko to a system).
**sudo modprobe -v wl**
Then previously configured, but not working wireless, suddenly started working.
But it did not auto load on reboot. and had to do sudo modprobe wl again.

Note that ifconfig showed that MAC as eth2 (no wlan0), so I not sure if searching for wireless networks works or not (I could not find that).  I was at a hotel and had booted to WinXP first, so had already configured Network Connections, Wireless in Ubuntu to the specific SSID.

I probably should put this somewhere in the USB stick's init scripts, if I figure out how to not auto login ubuntu user, but for now I just added this to ubuntu's ~/.profile to auto load the module (if not already loaded) if the USB stick boots on a PC with that Broadcom device:

```
# load Broadcom wireless module if Dell laptop
if lspci | grep -q BCM4311; then
        lsmod | grep -qw wl - || sudo modprobe wl
fi
```So now the bootable USB stick auto loads wl module if that device is present.

---

### Post by CaKiwi on 2009-11-14
Post #1 worked for my Linksys WPC54GS wireless adapter (Broadcom BCM4318 chip set)

---

### Post by wandalalakers on 2009-11-14
ProfGeek, I sent you a PM.

---

### Post by DanH42 on 2009-11-15
Using Netbook Remix 9.10 on an HP mini 1000, when I open Hardware Drivers, the list is empty ("No proprietary drivers are in use on this system"). Also, wired Ethernet doesn't work. Any clues?

EDIT: I used a USB network card to get the update, now everything works great. Thanks;)

---

### Post by pmenefee on 2009-11-16
Unfortunately my solution was to go back to 9.04.  It works.
I have a desktop out in my workshop, and no way to connect except via wireless from my home network.  After I upgraded to 9.10, I spent quite a bit of time trying to get a connection established, only to read on this forum that it just wasn't going to happen.  I pulled out the 9.04 CD and installed.  Wireless works just fine and I'm connected again.

This is a big deal for me and I really can't believe that a new version of Ubuntu would be released that just didn't connect.  Come on guys, I know nothing is perfect, but surely wireless connectivity would be high on the list of things to double check before you release a new version.  I bet we lost a lot of users with this one.

---

### Post by jlrivitti on 2009-11-16
I was having problem with my Dell Latitude and I solved it removing ndiswrapper (and b43 that I've added before) from /etc/modules. So, Broadcom 802.11 Linux STA wireless driver worked ok (System >> Administration >> Hardware Drivers).

---

### Post by marstodd on 2009-11-26
Hello!
First post, new install on nice middle age compaq laptop
Trying to get wireless working.
I have Hardware Drivers Broadcom B43 Wireless driver green.
(after working on some install info)
What specifically needs to be set up?
(other than name and password) will it detect networks in range?
how and where?
We use WPA2 (or WPA) here at home is this OK?
Do I have to keep unplugging Ethernet cable to test if my wireless will work?
Thanks for what I have so far!
Todd.

---

### Post by marstodd on 2009-11-26
Wow it works!
Now if that install whatever I did, could be put into some kind of script so that a dumb user could do it!!!! fantastic. broadcomm BCM4318 rev 2. 
Man the laptop I thought was a goner has a new life!

---

### Post by h1kz0r on 2009-11-26
The only thing that works is go back to 9.04 or whatever other distro that doesn't brake ur stuff after the upgrade.
Unfortunately I tried all the different methods online including this one and still the wireless doesn't work on my hp mini.
The wl is loaded fine, the STA Driver says active and in use and the wireless led is on.
iwlist gives me an error... failed to read scan data, invalid argument when i do scan or scanning.
I see this issue resolved in many places, but this is complete bs imo and all those ppl have it working on 9.04 not 9.10 and the rest of us just downgraded.
this issue is still unresolved, just like all the other "solved" threads about this.
lsmod shows wl is loaded and all the other checks confirms "it's working" while in fact it's not.

---

### Post by mt1234 on 2009-11-29
It appears that an Ubuntu 9.10 64-bit installation by default has the "Connect to wireless and ethernet networks" setting unchecked in the User Privileges for the Administrators group and Users group (possibly others). 

Go to System > Administration > Users and Groups. Click on Properties and then go to the User Privileges tab. Check the box next to "Connect to wireless and ethernet networks". Then click OK. 

Then go back to System > Administration > Hardware Drivers. Make sure the Broadcom STA wireless driver is activated. You may need to restart the computer after it is activated. Once restarted, make sure that any switch or button on your laptop or desktop for turning on the wireless radio is turned on. 

This worked for me! I hope this helps! :D

---

### Post by mebinte on 2009-12-20
is there anyway to get this working on live usb mode? i see the drivers in restricted drivers adn install them. after reboot, i have to install them again :confused:. i am running ubuntu live usb in persistent mode. How can i get it to work?

---

### Post by efflandt on 2009-12-20
See my answer #16 on 2nd page for more details.  With persistent usb iso, after you activate the hardware driver for STA and reboot, hardware drivers should show it as active, but not used.  Try **sudo modprobe -v wl** (last character is small L).

BTW, after I enabled STA on regular 64-bit 9.10 installed on WD Passport USB drive (temporarily connected by wireless bridge), wl and related modules loaded automatically on boot.  But Broadcom wireless on that Dell is weak compared with anything else, so I just deactivated that and use Linksys WUSB54GSC instead (which is stronger and supported by default).  I don't need the Broadcom driver anyway if that USB drive is booted on my desktop or Toshiba laptop (supported built-in wireless).

---

### Post by mebinte on 2009-12-22
> **efflandt said:**
> See my answer #16 on 2nd page for more details.  With persistent usb iso, after you activate the hardware driver for STA and reboot, hardware drivers should show it as active, but not used.  Try **sudo modprobe -v wl** (last character is small L).

BTW, after I enabled STA on regular 64-bit 9.10 installed on WD Passport USB drive (temporarily connected by wireless bridge), wl and related modules loaded automatically on boot.  But Broadcom wireless on that Dell is weak compared with anything else, so I just deactivated that and use Linksys WUSB54GSC instead (which is stronger and supported by default).  I don't need the Broadcom driver anyway if that USB drive is booted on my desktop or Toshiba laptop (supported built-in wireless).

i use unebootin to create usb iso with ubuntu iso. does that give me a  persistent usb iso?

---

### Post by jeremygrieshop on 2010-01-30
In case anyone else runs into this, I got wireless working on my mini v10 under ubuntu 9.10 by the following:

  1. Insert your USB drive back in.
  2. Install dkms_2.1.0.1-0ubuntu1_all.deb from the drive
  3. Install patch_2.5.9-5_i386.deb from your drive

  * critical, you must install "patch", because bcmwl will need it to patch the driver source and build updated drivers.  It's not a .deb dependency, which is why I failed to see this in the first place.

  4. Install bcmwl-kernel-source_5.10.91.9+bdcom-0ubuntu4_i386.deb
  5. Reboot
  6. Activate hardware driver from System->Administration->Hardware Drivers

Voila!

---

### Post by 64bitguy on 2010-01-31
> **mt1234 said:**
> It appears that an Ubuntu 9.10 64-bit installation by default has the "Connect to wireless and ethernet networks" setting unchecked in the User Privileges for the Administrators group and Users group (possibly others). 

Go to System > Administration > Users and Groups. Click on Properties and then go to the User Privileges tab. Check the box next to "Connect to wireless and ethernet networks". Then click OK. 

Then go back to System > Administration > Hardware Drivers. Make sure the Broadcom STA wireless driver is activated. You may need to restart the computer after it is activated. Once restarted, make sure that any switch or button on your laptop or desktop for turning on the wireless radio is turned on. 

This worked for me! I hope this helps! :D

[SIZE=3][COLOR=Red]**Bingo**[/COLOR][/SIZE][COLOR=Red]...[/COLOR] Wow, talk about painless!  (Fix applies to 32bit Versions of Karmic too).  No patching, downloading, terminal processes... this is the short and sweet version.

One minor thing to note, in step 1, on the **System > Administration > Users and Groups** screen, you'll need to click on the keys symbol (next to where it says, "**Click to make changes**" ) ***[COLOR=Red]BEFORE[/COLOR]*** you can continue on with the instructions and alter (enable) your user privileges for Wireless and Ethernet network settings.

Other than that, this reply was perfect in that it will allow you (in the second section **System > Administration > Hardware Drivers**) to automatically detect and install the correct Broadcom drivers (and Fax/Modem drivers too!) versus going with one of the many previously (and elsewhere) described manual installation routes that have you installing Drivers at your own risk.  There are other ways that work, true enough; but so far for me this way works every time **AUTOMATICALLY** with a variety of Broadcom Wireless and hardware/software modem adapters and works the FIRST TIME.  One reboot and you're off to the races. 

Thanks!

---

### Post by hmntsk on 2010-02-15
.

---

### Post by RocketRay on 2010-03-16
The fix in the first post worked for me, though on the first reboot the wireless device wasn't listed in Network Connections.  Hardware Devices said it was activated but "not used".  So I rebooted with the wired connection and it came back.  I disconnected the wired ethernet and on the next reboot the wireless connection worked automatically.  Should be good from here on out.

I've got an Acer Aspire 5517 laptop BTW.

---

### Post by GOR4N on 2010-03-28
> **Haythayt said:**
> Same problem here (Dell Inspiron 1525,). None of the many solutions (reinstalling bcmwl-kernel-source etc...) so far helped me. And still Jockey did not install the Broadcom STA driver. Seems the bug was known prior to the release and its fix did not help in my case, e.g.:

[https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/443185](https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/443185)

So I did lose my patience. ;)

And I downloaded the broadcom driver myself and "installed" them.

First download the drivers here:

[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

Then follow this instructions:

[http://www.broadcom.com/docs/linux_sta/README.txt](http://www.broadcom.com/docs/linux_sta/README.txt)

Afterwards I could connect to my wireless network. Unfortunately this was not the case anymore after rebooting. lsmod shows neither "wl" or "lib80211" anymore.
Does anybody know how to add these modules permanently? (Adding to /etc/modules? And where do I have to put the wl.ko file then? Somewhere in /lib/modules/2.6.../.?)
And how may this interfere with Ubuntu's Jockey if it by any chance works again? For after loading the modules manually Jockey still does not show the driver activated...)

Thanks for your help...

I have hpMini110 with Ubuntu 9.10 Netbook Remix and the same problem :)
I used [Broadcom drivers v5.60]("http://www.broadcom.com/support/802.11/linux_sta.php") and [README.txt]("ttp://www.broadcom.com/docs/linux_sta/README.txt") instructions to make WiFi and Bluetooth working but could not boot wifi at system boot ... same problem again :)

But this is the way that I used (with help of many users from this forum) to have working hpMini110 with Ubuntu 9.10 Netbook Remix :P

first to make WiFi work when system boots start TERMINAL and type:
[B]
gksudo gedit /etc/rc.local [/B]*(**this will allow you to edit rc.local **file *[I]that runs command as root)

[/I]add commands

[B] rmmod ssb
rmmod b43[/B]
[B]rmmod wl
modprobe lib80211
insmod /lib/modules/2.6.31-20-generic/kernel/drivers/net/wireless/wl.ko
[/B]*(I don't need rmmod b43 because it is blacklisted, and rmmod wl because it is not loaded ... check your case and delete commands if you don't need them)*

 at the end you should have **exit 0 **command
*(also if you have that command that looks like **modeprobe wl** you can remove that because there is typing mistake in README.txt file it should be **modprobe wl **but it is working without this)*

save your **rc.local **file quit **gedit** application and reboot your system
you should now have WiFi loaded with your system and Bluetooth also

Next problem that I had was **Unlock keyring** popup window that needs password to let application **NetworkManager **to work and to connect to desired wireless network

I solved that problem by starting **Accessories>Password and Encryption keys** 
Then I right-clicked **Passwords:default** and selected Change password
I enterd the old-one and left new ones empty
Not very safe but it works

---

### Post by philidox on 2010-04-20
> **lexpenrose said:**
> Ok, there's about 1 million people with the same problem : Broadcom STA Wireless driver problems since 9.10 ( worked for everyone in 9.04 ) 
Here's how to "FIX" it , more like a triple bypass : 

First of all , set your router to use WEP 40 bit, because WPA is seriously bugged still with Ubuntu

- Just after installing Ubuntu 9.10, make sure you use a WIRED internet connection ( using your onboard NIC , not wireless obviously since it doesn't work ) 
- Issue a "sudo apt-get update" on the terminal to update all the drivers etc. 
- Then go to System -> Administration -> Hardware Drivers 
And select the Broadcom Wireless STA Driver and click Activate.

That's the only way I got this working , I'm sure there's 100 other ways but at least this is a guaranteed way for people to fix their problems ( provided they have access to wired internet )

Thanks brotha that was dead on!

---

### Post by Jeyaprakash on 2010-05-04
> **superticky said:**
> I have solved the issue for me.

Steps:

- load the ubuntu 9.10 live with pen drive.
- after ubuntu loaded completely, go to hardware drivers
- select STA proprietary (the second one on the list)
- activate and it will work.
- now install the ubuntu into hard drive.
- after ubuntu is installed, go to  hardware drivers
- only one will appear, which is the one we need.
- activate buy it wont work (its okey for now)
- now Go to pool/restricted/b/bcmwl on Ubuntu Live USB pen drive. Double click into the .deb file in there, and REINSTALL that package. 
- go now again to hardware drivers.
- Now you can activate Broadcom STA driver, most cases you will see its already activated.
- now Wifi should work.

it worked for me on a hp mini.

please note: i founded another bug, after you have internet, if you do update/upgrade all, the new version of firefox wont work, it will say "bus error".

Thanks.

This helped me to setup my wifi in my compaq C555. Instead of USB drive, I opened the same location in the Ubuntu CD. Just went through the folders as in windows and it worked fine. Thanks for the post.

---

### Post by burcs on 2011-03-10
> **superticky said:**
> I have solved the issue for me.

Steps:

- load the ubuntu 9.10 live with pen drive.
- after ubuntu loaded completely, go to hardware drivers
- select STA proprietary (the second one on the list)
- activate and it will work.
- now install the ubuntu into hard drive.
- after ubuntu is installed, go to  hardware drivers
- only one will appear, which is the one we need.
- activate buy it wont work (its okey for now)
- now Go to pool/restricted/b/bcmwl on Ubuntu Live USB pen drive. Double click into the .deb file in there, and REINSTALL that package. 
- go now again to hardware drivers.
- Now you can activate Broadcom STA driver, most cases you will see its already activated.
- now Wifi should work.

it worked for me on a hp mini.

please note: i founded another bug, after you have internet, if you do update/upgrade all, the new version of firefox wont work, it will say "bus error".

Thanks.

This worked for me in 10.04, too. Installing the driver via the hardware drivers menu, Synaptic, or apt-get never would make it work. Had managed to connect a few times but it would always say "no internet access". This was on 10.10 Netbook edition and I finally gave up and uninstalled it, then decided to give 10.04 a shot.

Still a little buggy, as the panel icon has a red exclamation mark and doesn't show the signal strength, but at least it's connected and working.

[img]http://i.imgur.com/XZME4.png[/img]

Thanks.

---

