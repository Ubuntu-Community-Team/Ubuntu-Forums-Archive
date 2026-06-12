---
title: "ACPI: Subsystem revision 20050729"
date: 2006-01-29
forum: Installation &amp; Upgrades
---

### Post by stromb on 2006-01-29
Hello all,

I just recently purchased a new HP dv5000 laptop and want to install Ubuntu 5.10. When booting the AMD64 install disc, it gets past the initial Ubuntu "boot:"  screen (where I press enter) but then everything comes to a halt with the last message being:

*ACPI: Subsystem revision 20050729*

Another message a few line above it reads:

*ACPI: Looking for DSDT in initrd... not found!*

I have tried a number of different boot options to no avail. Here are my laptop specs:

- HP Pavilion dv5000z CTO Notebook
- AMD Turion(TM) 64 ML-34 (1.8GHz/1MB L2 Cache)
- 15.4" WXGA BrightView Widescreen (1280x800)
- 128MB ATI RADEON(R) XPRESS 200M w/Hypermemory(TM)
- 1.0GB DDR SDRAM (2x512MB)
- 60 GB 4200 RPM Hard Drive
- DVD/CD-RW Combo Drive
- 54g(TM) 802.11b/g WLAN w/ 125HSM/SpeedBooster(TM)

I didn't see it listed anywhere that this AMD64 installation disc works for Turion 64, but I figured the architecture would be similar enough. Is this the problem? If anyone could shed some light it would be much appreciated. Also, if any additional information is needed feel free to ask.

Thanks in advance!

---

### Post by per engberg on 2006-02-11
Hi,
I´ve got the same PC with exactly the same problem (with live CD). Tried the 32-bit version but that seems to give me problems with video mode (tried with vga=771, no luck). Hope someone has a better answer.
Per

---

### Post by meenfreem on 2006-02-13
hmz... I have exactly the same problem with exactly the same laptop... I've been searching for two days now but nothing. 

Tried some of the command lines I've found on the forums, but indeed, no luck yet.

Could it have anything to do with the BIOS the laptop is running? The laptop we have is the newest we could find basicly and it's running BIOS version PhoenixBIOS F.22, KBC version 49.25. Anybody who has any ideas... please let us know!

---

### Post by meenfreem on 2006-02-14
Guys, I got it to install :D

I typed this command: linux vga=771 noapic nolapic

and it went through the install without problems, that is, the install from the cd is done and its now just finishing the install from the packages (whatever they call it, but it doesn't need the cd anymore) and I don't think it'll crash on me now...

I might ofcourse still run into more problems when the install is complete, ie graphics.

---

### Post by per engberg on 2006-02-14
Great. I gave up on the 64-bit (thought it might be to ambitious for a beginner like me) and got the live version of the 32-bit running by using live-expert vga=771 and accept defaults except choosing VESA in stead of ATI for graphics. Now I'll have to test the 64-bit again with your switches.
Per

---

### Post by meenfreem on 2006-02-14
before you do that :D I think I installed the 32bit version too :D

---

### Post by per engberg on 2006-02-14
Thanks for the heads up :)

---

### Post by stromb on 2006-02-14
meenfreem is the man! I haven't yet had a chance to fully install Ubuntu, just did enough to see if it would get past the error message (which, of course, it did). Can I ask you where you found this boot option? Also, does anyone have any feedback on how well the hardware was detected on this laptop? I'm also curious to know if any of you guys got the internal wireless adapter working. I plan to do the install within the next few days and will post my results (successes, failures, etc.).

Thanks!

---

### Post by stromb on 2006-02-14
Okay, I lied. I couldn't wait. I began the install (with only 2 hours to spare) hoping it would be quick and painless. Unfortunately, despite the install going smoothly, X failed to start after the reboot. I now get this error:

**Failed to start the X server (your graphical interface). It is likely that it is not set up correctly....** <the rest omitted>

I only had time for a quick Google search and came up with very little. Many suggestions were to run:

*$ sudo dpkg-reconfigure xserver-xorg*

I tried this, but having little knowledge in the way of X configuration I had hardly a clue as to what options to choose. I chose mostly the defaults with a few alterations, but had no luck. I'll work on this later when I have more time and post whatever I find. Anyone else get this?

Thanks!

---

### Post by per engberg on 2006-02-15
Finally got it running with some help form my brother.  I also had to run 
$ sudo dpkg-reconfigure xserver-xorg
The main change to the defaults was to use VESA in stead of ATI for driver. It now loads but unfortunately not with the optimal resolution. Best i can get is 1024x756 or somthing like that, not 1200x800. From Ubuntu i then downloaded a driver from ATI's site, supposedly for notebooks with ATI, not the Xpress 200M explicitly. After running the install I tried to configure using 
sudo sh ./usr/X11R6/bin/aticonfig --initial
but there seemes to be a file missing, so no luck. I'll try to find some solution to this, otherwise everything seems to work OK. Haven't tested with wireless network yet though.

---

### Post by n0ah420 on 2006-02-15
I have the HP5035nr and everything is fine (for now).  I installed with:

```
linux vga=771 noapic nolapic
```

Then after install and dist-upgrade (as well as adding the K7 Kernel) I removed the vga=771 noapic nolapic from /boot/grub/menu.1st and it booted fine.  

To get the xserver to work you need to change the driver to ati (1280x800 works!) but you need to add the following option in your xorg.conf file (Under device listing):

```
"Option"             "NoAccel"            "true"
```

This should allow the xserver to work.  I have been using Ubuntu for two years now on 6 different machines.  This is a new laptop which appears to have some issues.  Most likely it will all work out.  I will be doing the ati drivers tonight, I am sure 3D works as well.  If you have any questions let me know.  

My last machine was an eMachines M6805, which if you know anything about, was also a big pain in the butt.

---

### Post by per engberg on 2006-02-16
Thanks, I'll try that tonight

---

### Post by meenfreem on 2006-02-16
I have been trying some things with the wireless network, and made some progress actually. Got it to recognize the wlan card, but since i mucked up my network settings, I can't connect to the internet yet. 

here's the thread that explans the wlan setup: [http://ubuntuforums.org/showthread.php?t=25683](http://ubuntuforums.org/showthread.php?t=25683)

I'll struggle with the ATI drivers later on...

---

### Post by n0ah420 on 2006-02-16
So last night I was able to get WiFi and 3D Acceleration to work on the dv5035nr.  Its a touchy beast but everything works.  I am getting a weird message that is continuously printed to the kernel log which is starting to anger me, but none the less it is all comming together.  Where there is a will there is a way I guess.  

Just an added not you should use the WiFi drivers fro hp.com.  I also used the newest ATI drivers and built the kernel module and .deb myself (there is a how-to floting around for an older driver which should work).  I updtaed the bios, but the changelog did not indicate any acpi revisions.  CPU scaling is working but the battery meter has no idea how much time is left.

---

### Post by per engberg on 2006-02-16
Great, nice to know that it's possible. Do you have a link to the how-to for the older driver? Building kernels and .deb's is all new to me, so I'll need all the help I can get.
Per

---

### Post by n0ah420 on 2006-02-16
I used the following howto (but with the newest ATI driver):

[http://www.ubuntuforums.org/showthread.php?t=75428&highlight=ati]("http://www.ubuntuforums.org/showthread.php?t=75428&highlight=ati")

---

### Post by per engberg on 2006-02-17
Thanks, will try that tonight.

---

### Post by meenfreem on 2006-02-17
i'm about to throw this heap out the window... neither the wifi nor the ati drivers will work! grrrr

---

### Post by n0ah420 on 2006-02-17
Can you tell me a little more about your problem?  Maybe I can help.  For the ati card you should remove all of the Synaptic FGLRX stuff first (make sure to do a complete removal so the configuration files are taken away).  The follow the How-To above but with a newly downloaded Driver from ATI.

As for the wireless, same thing.  Start from scratch, then reinstall ndiswrapper.  Grab the bcmwl5.inf and bcmwl5.sys files from the driver package on hp.com.  Then do:

```
sudo ndiswrapper -i bcmwl5.inf
sudo ndiswrapper -m
sudo ndiswrapper -hotplug
sudo modprobe ndiswrapper
```

Reboot and press the wireless button (make sure the light comes on after the module is loaded).  The setup your wireless connection in the Network Properties dialog.  To make it turn on at startup you may have to modify:

```
/etc/network/interfaces
```

Edit the line that says:

```
auto lo eth0
```

and add

```
auto lo eth0 wlan0 (you can also remove eth0 if you don't need it, ifup eth0 later on if you do)
```

In theory that should all be edited for you by the Network Properties dialog, but it doesn't hurt to take a look.  The wirelss configuration will also be stored later on in this file.

It may be somewhat of an issue to get things to work on this newer hardware but it is possible.  Wireless and 3D acceleration are always an issue but if you trudge through it, you just might learn something in the process.  Let me know if you need more info.

---

### Post by stromb on 2006-02-18
n0ah420 (or is it 4:20? :D),

I haven't even started with the video yet, but I'm currently having trouble with the WLAN card. I have the dv5000z (see OP for specs) and have also followed the instructions from both of these threads:

[http://ubuntuforums.org/showthread.php?t=25683]("http://ubuntuforums.org/showthread.php?t=25683")

[http://ubuntuforums.org/showthread.php?t=31926]("http://ubuntuforums.org/showthread.php?t=31926")

as well as your instructions you have just recently posted. No luck with any of them. What I have done thus far is this:

1.) Went to HP's site and downloaded [this]("http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?dlc=en&lc=en&os=228&product=425543&lang=en&cc=us&softwareitem=ob-17753-1") driver, opened the *.exe and found the bcmwl5.inf and bcmwl5.sys files in the extracted directory (C:\SWSetup\WLanAppInstall\Broadcom).

2.) Copied the bcmwl5.inf and bcmwl5.sys files to my Ubuntu laptop.

3.) Updated Ubuntu using Update Manager.

4.) Updated apt:

```
$ sudo apt-get update
```

5.) Installed the "build-essential" package (which I read was required to get ndiswrapper to work with this WLAN adapter). I did this using:

```
$ sudo apt-get install build-essential
```

6.) Installed latest Linux headers (not sure what this was for, but did it as instructed):

```
$ sudo apt-get install linux-headers-2.6.12-10
```

7.) Installed ndiswrapper and driver, etc. using:

```
$ sudo apt-get install ndiswrapper-utils
$ cd /the_dir_I_copied_the_wlan_drivers_into/
$ sudo ndiswrapper -i bcmwl5.inf
$ sudo ndiswrapper -l
Installed ndis drivers:
bcmwl5 driver present
$ sudo ndiswrapper -m
$ sudo ndiswrapper -hotplug
$ sudo modprobe ndiswrapper (which did not bring up the adapter)
```

I then rebooted just to see if that would do the trick, but it didn't. I even tried uninstalling everything above and starting over from scratch, but no luck.

Two things to note, however:

1.) The only thing I found related to "Synaptic FGLRX stuff" was fglrx-control, which was not installed by default so, of course, I couldn't remove it. Is there anything else I'm missing with this step?

2.) On step 3 of [this]("http://ubuntuforums.org/showthread.php?t=25683") thread it states that you must edit the *.conf file(s) in the /etc/ndiswrapper/bcmwl5/ directory. I didn't understand this step and, therefor, didn't follow it. Can you decipher this? Is this necessary, because I didn't see this as a required step on any other posted "how-to"? Also, I have more than one *.conf file in that directory and the step from the "how-to" seems to expect there to only be one.

I'll continue to work on this and post whatever I find...because after all...if there's a will, there's a way to get this damn WLAN card to work if it takes the next 20 releases of Ubuntu to do it!!! :D

Thanks in advance!

---

### Post by n0ah420 on 2006-02-18
So just quickly, if you never installed fglrx (the ATI drivers) from Synaptic then don't worry about it, just try the How-To.

For the wireless card.  It might be ready to go. Try:

```
sudo ifup wlan0
```

If it does not come up reply with the output of:

```
cat /etc/network/interfaces

ifconfig -a
```

Remember you can try and activate/setup the adapter through the network settings dialog as well.  It may be installed just not activated/on. try pressing the wireless button on your laptop then doing the ifup command.

---

### Post by stromb on 2006-02-18
n0ah420,

The interface doesn't exist yet apparently.

```
$ sudo ifup wlan0
Ignoring unknown interface wlan0=wlan0.
```

Here is what I have in /etc/network/interfaces:

```

$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

# The primary network interface
iface eth0 inet dhcp
```

I'm guessing I have to manually add the wlan0? I thought I had this done before I started over from scratch but I'll be damned if I can remember what I did to add it. In any event, I don't think I knew what to do after adding it. Any other suggestions?

Thanks!

---

### Post by stromb on 2006-02-19
n0ah420,

Thanks for the link to the ATI "how-to"! For anyone else who has yet to do this, it was **extremely** easy. You can download the latest driver from [here]("https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.22.5-i386.run"). Everything else you need to know is in the "how-to" n0ah420 posted. Works perfectly. BTW, has anyone gotten the WLAN card to work yet? That is the only thing I have yet to get working. I found it difficult to find information on how to add the wlan0 manually, and before messing anything up I thought I'd check here first.

Also, has anyone else noticed (at least for the HP dv5000z) that whenever the system is accessing the cd-rom drive, the mouse cursor completely goes haywire (clicking and jumping all over the place)?

Thanks!

---

### Post by n0ah420 on 2006-02-19
So I haven't noticed any issues when accessing the DVD. However if there is no disc in the driver weird error messages get posted to my log. Must be a driver thing.

As for the wlan0 I have been able to get it to work. The easiest way is to use gtkwifi (Search for ndiswrapper in Synaptic). The problem with this laptop is the stupid wi-fi button. After installing it reboot, then:

```
sudo ndiswrapper -hotplug (just in case)
sudo modprobe ndiswrapper
``` 
Then configure the adpater through the Admin-->Networking interface.  I then pressed the wi-fi button and:

```
sudo ifup wlan0
``` 
Now all is well. I have had issues with this broadcom chipset on nearly every machine I have ever had. Sometimes trial and error will help out. Its the wi-fi button that causes most issues. I have attached the drivers I used. Below is my /etc/network/interfaces file (wep key changed).

```
n0ah@dreamer:/media/storage/temp$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

# The primary network interface
iface eth0 inet dhcp

iface wlan0 inet dhcp
wireless-essid n0ah Productions
wireless-key f43222d9c9

auto wlan0

```

---

### Post by n0ah420 on 2006-02-19
--duplicate--

---

### Post by meenfreem on 2006-02-20
we got the wireless to work properly... turns out that in my case, the how-to worked fine (the ndiswrapper stuff) but our router used the wrong key! It was set to WPA or something and ubuntu doesn't support it! So everything was working fine, but it just couldn't connect to the router (a linksys wireless-g). So what we did was just go into the router set-up and check what type of 'key' it uses, and change it to WEP if necessary. From then on it should be easy setup. 

Today I'll go through the ATI setup.

---

### Post by meenfreem on 2006-02-20
seemed like I got everything to install properly now... eventhough the ATI setup decreased my resolution to 1024x768... had to manually give the 1280x800 option in the xorg.conf file. But when I did, everything is working fine...

Now to get the 6-in1 reader to work, but from what I understand, there's very little hope for that... at least till Dapper, which might support it.

---

### Post by stromb on 2006-02-20
meenfreem,

You have the dv5000z too right? Can you post what steps you took to install the WLAN? I've followed both how-to's step for step twice over and I still can't get the card detected when using *sudo modprobe ndiswrapper* (nothing in dmesg, no light, nothing). I posted everything I've done thus far on page 2 of this thread. I really don't see what I'm doing wrong.

Thank!

P.S. What is "gtkwifi"?

---

### Post by meenfreem on 2006-02-23
I have a dv5074EA to be precise...

I followed the ndiswrapper steps, and actually managed to install everything properly but I still had no internet... so I got all confused untill my colleague discovered that the router itself was using the wrong type of keycode (WPA or something, it should be WEP!). So I would suggest you check that first.

in network properties create a new location, and check whether the wlan0 is there or not... if it isn't, I wouldn't know what you did wrong :S sorry... if it is there, but no internet than it's most likely the router.

In the top bar on the desktop you also have a network icon right?! It's normally on lo ... try typing wlan0 instead of lo. For me it started showing that it showed the connection strength. Should be a clear give away whether its actually working or not... 

just some ideas, I'm a total n00b still when it comes to this.

---

### Post by n0ah420 on 2006-02-23
I just wanted to let everyone know that I installed dapper last night from Flight4 and all is well.  On top of that the wireless card is automatically detected and installed.  Much faster then breezy was.  I still had to give the noapic nolapic during install, but removing them afterwards does not cuase any issues.  dapper will be out in a month so unless you are a complete newbie and don't want to deal with a few updates/breakages I would suggest moving to dapper on  this laptop.

---

### Post by stromb on 2006-02-23
Yeah, I think I will just switch to Dapper. As far as the WLAN on my laptop goes, I'm very confident I did everything right and it just isn't able to bring that card up. But if anyone has any further suggestions I would be happy to give them a shot before reinstalling.

Thanks!

P.S. Once the official release of Dapper comes out will I have to reinstall or will the Update Manager and apt be sufficient enough to bring it completely up-to-date (meaning once I install the Alpha, will I have to reinstall the official release)?

---

### Post by n0ah420 on 2006-02-23
Once the release comes out you will automatically be up to date.  Thats the beauty of linux.  Since you will be updating on a regular basis (becuase its in dev right now), once the repos are turned final you will be right there with em so no reinstall in required.  I haven't been able to get fglrx working in dapper though.  Its the only thing pissing me off.  But thats what I get for buying an ati 'enriched' laptop.  Wish there were more nvidia laptops out there.  If anyone else is reading this and using an X200M card with dapper and getting:

```
DRI initialization failed!
```

in the /var/log/Xorg.0.log file, drop me a line and let me know if you fixed it.  I have have been able to do so.

---

### Post by stromb on 2006-02-23
Sounds good. I'll assume you haven't played with Xgl and compiz yet since you're having trouble with your video, right? Let me know if you do.

Thanks!

---

### Post by n0ah420 on 2006-02-23
I'm not even going to attempt Xgl until I can get DRI working in a reasonable fashion.

---

### Post by adesai on 2006-02-23
So, has anybody with this problem actually been able to install the 64-bit version? It seems like all the fixes here are for 32-bit.

---

### Post by n0ah420 on 2006-02-23
I am now just venting my general anger at this laptop and linux.  I have linux on 3o f 4 machines here at home.  My webserver runs linux, I use linux at work (though just for server activities - applications on windows), and I can get this freeking laptop to do what I want.  Here are the problem childs (I know this is nothing new):

1) Stupid Broadcom chipset

2) Ridiculous ATI direct rendering support

3) Head bashing ACPI though the bios

What do you have to do in 2006 to get linux on a new new laptop?  So yes everything works...but not as well as Windows does on this same machine.  In fact Windows is running circles around Linux for the first time in three years that I have been dual-booting.  Its a shame.  So i just had to vent...not giving up, just disapointed in my poor choice of hardware and the poor support for it in the current kernel.

---

### Post by n0ah420 on 2006-02-23
Adesai,

Save yourself the headache of 64-bit and install 32-bit for now.  You will most likely have the same issues plus all the other fun that comes along with 64-bit like codecs/wine/flash/etc. 

But don't let my negativity diseude you.

---

### Post by stromb on 2006-02-23
n0ah420,

I hear you. But I think you know as well as I do that Ubuntu is moving at an incredible pace and will be rivaling Microsoft in the desktop market in the very near future. While I'm going nuts myself over this WLAN card, I'd still choose Linux (well, FreeBSD before anything ;)) over Windows any day of the week, as I'm sure you would too. Let me know if you get any further with your laptop and I'll do the same...after all, it's the community that makes Open Source what Microsoft could never be...

Thanks! ;)

---

### Post by n0ah420 on 2006-02-24
stromb,

You're right, I'm not going to give up, it just bothers me.  I guess patience really is a virtue.  I'll let you know where I get with this hunk of plastic and silicon.

---

### Post by n0ah420 on 2006-04-06
So just wanted to update anyone having HP dv500 series issues.  I am currently triple booting my dv5025nr with dapper.  Wireless (ndiswrapper) and fglrx are working fine.  In fact I am pretty happy right now about its speed.  There is a new bios update from HP you should definitely install it.  Also to fix the error messages from the DVD writer check out this thread:

[http://ubuntuforums.org/showthread.php?p=883892#post883892]("http://ubuntuforums.org/showthread.php?p=883892#post883892")

---

### Post by stromb on 2006-04-09
n0ah420,

Very nice. I *was* waiting for April when Dapper was originally supposed to be released to do a final install of Ubuntu, but now I'm just going to sit back and wait until June. Besides, right now I have everything working like a champ with a FreeBSD/Gnome install (with the exception of wireless), so I'm really not too bothered with having to wait the extra few weeks. Once I set it all up though, I'll post any problems/successes I have for everyone else to view.

Thanks for the update!

P.S. What errors were you getting from the DVD writer? Was this when you were trying to burn?

---

### Post by n0ah420 on 2006-04-09
```
The failed "Read Cd/Dvd Capacity" packet command was
```

These errors are printed to the log (and screen in console mode) when there is no media in the drive.

See my previous post for the link to a fix.

---

