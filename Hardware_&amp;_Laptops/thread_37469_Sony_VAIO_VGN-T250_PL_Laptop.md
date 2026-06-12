---
title: "Sony VAIO VGN-T250 P/L Laptop"
date: 2005-05-27
forum: Hardware &amp; Laptops
---

### Post by fastluck on 2005-05-27
I installed several distributions on my vaio, including Mandrake, Suse, and Debian Sarge.  All with mixed results.  Installing UBUNTU instantly resulted in a usable laptop!  Here are the details:

Video (at 1024x768) - but widescreen doesn't work, so there's a one-inch bar on both sides of the screen that is unusable.  **Solved**

Sound doesn't work. **solved**

Ethernet, modem, wireless, bluetooth - All detected and appear to work flawlessly!  UBUNTU was instantly able to access the internet and download patches.  In fact, while installing Ubuntu, my wireless switch was off.  The installer even informed me that I need to turn on the switch. I was impressed with how smoothly everything went.

Mousepad works just as well as it did under windows, in every way.

**Update:**  Video now works.  Solution is posted here: [http://ubuntuforums.org/journal.php?do=showjournal&j=108](http://ubuntuforums.org/journal.php?do=showjournal&j=108)

**Update:**  Sound now works.  Solution at end of thread. How-to will be put together within the next couple of days.

**Update** Bluetooth Mouse: [http://ubuntuforums.org/showthread.php?p=609310#post609310](http://ubuntuforums.org/showthread.php?p=609310#post609310).

Fastluck

P.S: Thanks Hannes_ Tread and LuvDemHeels for the help! I couldn't have done it without you.  (Well, maybe I could have, but then someone else would have had to show me the way.) :)

P.P.S:  If you want to have someone else do the work, there's a post later in this thread (here: [http://ubuntuforums.org/showthread.php?p=244794#post244794](http://ubuntuforums.org/showthread.php?p=244794#post244794)) with some info about EmperorLinux.

---

### Post by hannes_ on 2005-05-27
[http://www.ubuntulinux.org/wiki/HdaIntelSoundHowto](http://www.ubuntulinux.org/wiki/HdaIntelSoundHowto)

thats about the sound I guess..


and vga with nvidia drivers (dont know which one is in it) just add / override the following line in ur /etc/X11/xorg.conf (Monitor section)

Modeline         "1280x800" 80.58 1280 1344 1480 1680 800 801 804 827

thats for 1280x800

gl hf

---

### Post by fastluck on 2005-05-29
My xorg.conf only shows one supported resolution--the right one.  1280x768.  But 1024x768 is what I get.

---

### Post by luvdemheels on 2005-05-30
This link should help with your widescreen and sound.

[http://users.skynet.be/thomasvst/linux-on-laptop/](http://users.skynet.be/thomasvst/linux-on-laptop/)

---

### Post by fastluck on 2005-05-30
I still can't get alsa working.  See end of thread.

Once I got video working, I posted a blog here: [http://ubuntuforums.org/journal.php?do=showjournal&j=108](http://ubuntuforums.org/journal.php?do=showjournal&j=108).  

Sound is not working, and is **currently unsupported under Linux.** as far as I can tell.  So far, the how-tos I've been able to find are completely irrelevant to this computer, where sound is concerned. Also, there's no sound driver available on the Alsa hardware list. This link lists supported hardware from Analog Devices, Inc: [http://www.alsa-project.org/alsa-do..._Devices#matrix](http://www.alsa-project.org/alsa-do..._Devices#matrix)

This is the hardware on this machine, according to Windows XP (dmesg does NOT mention the sound hardware, and as far as I can tell, it is NOT detected).

Soundmax Integrated Digital Audio
Analog Devices, Inc.
PNP Device ID: "PCI\VEN_8086&DEV_24C5&SUBSYS_81C0104D&REV_03\3&61AAA01&0&FD"

I went to Analog's web page, and as is typical of people who manufacture hardware for Windows laptops, there's nothing there that would help someone who's not an electrical engineer.  My next step is Sony's site,  but I've been there many times over the past few weeks and don't expect to find anything.

So if anyone has help relevant to this notebook, please let me know!  I'm at my wits' end here and I don't want to boot to Windows to play MP3s.

Here's my dmesg output: [deleted]

---

### Post by fastluck on 2005-05-31
I went to Sony's site, and discovered that the Windows sound driver that works for the VGN-T250P/L (T250PL) also works for these vaio models:

VGN B100, B100B, B100P; VGN B150FP; VGN B250FP; VGN T130FP; VGN T140P;
VGN T150, T150P; VGN T160P; VGN T170P; VGN T240P; VGN T250, T250P;
VGN T260P, VGN T270P; VGN T340P; VGN T350, T350P; VGN T360, T360P; VGN T370P

Does anyone own one of these models that they successfully got sound working on?  If you do, please let me know how. **Update:  ** None of these machines are listed at the Linux On Laptops site or in any forum message here.

**Update:** Sound solution should work for all the Vaios listed here.  Let me know if you're successful with one of them.

---

### Post by fastluck on 2005-05-31
According to lspci, this is the sound hardware:

0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)

...so maybe I'll retry the intel how-to.  I'll keep you posted.

Fastluck

---

### Post by fastluck on 2005-05-31
I tried to make alsa-drivers.  But it requires the kernel source (or at least the headers).  Typing apt-get install kernel-headers doesn't work, but apt-get install kernel-source does.  Problem is, the version I'm running as reported  by dmesg is 2.6.10-5-386.  But the source version apt-get retrieves is 2.4.27.  Where can I get the source version that corresponds to the kernel version installed on my machine?  I know I can go to linuxkernel.org, but I'm sure their version of the source isn't the exact same thing as what I should be able to get from this site.

**Solution:**  Using synaptic, download kernel sources and headers for your version.  

Copy the correct Config-* file from your /boot directory to .config in your kernel source directory.

Here are the config files in my /boot directory:
```

root@roadrage:/usr/src # ls /boot | grep -i config
config-2.6.10-5-386
config-2.6.10-5-686
config-2.6.11-1-686

```
**Note:**  I had problems with kernel version 2.6.11-1-686 on this computer. The mouse responded extremely slow and I had kernel panics whenever I tried to shut down.  I recommend another kernel.  The default from the CD is 2.6.10-5-686, or at least that's the one I'm running now.  The only reason the other one's there is because I used synaptic to download the kernel images.  You don't need to do that to make this work.

Run 'make menuconfig' but don't choose anything.  Just exit and save.  
Run 'make', but don't run 'make install'.  

Then you'll be able to build the alsa projects.  

Go into /usr/src and create a symlink called 'linux' that points to the linux source directory.  In my case, the command was:

root@roadrage:/usr/src # ln -s linux-source-2.6.10 linux

Note that this command must be run as root.

For everything (including alsa-drivers), run .'/configure' then './make' from each directory. **Do not** pass any arguments to ./configure when building alsa-drivers!  Instead, let it build all of the drivers.  You'll waste a small amount of disk space, but it will detect your hardware correctly.  You can always free up the space later if you want to.

---

### Post by fastluck on 2005-05-31
It seems that to install the proper version of the source, you have to type:

apt-get install linux-source-2.6.10

...and not kernel-source as I had thought.  I tried that, and it's now installing.

**Update:** Using synaptic to install kernel source and headers for the proper version worked.  Then, make menuconfig and make need to be done before you can compile the alsa drivers.  (see later in thread)

---

### Post by fastluck on 2005-06-01
Using synaptic, I installed the linux kernel sources and headers.  In my case, it was 2.6.10.  Then I opened a terminal, typed

cd /usr/src

and typed

ln -s linux-source-2.6.10
cd alsa/alsa-driver*

./configure --with-cards=hda-intel

That worked, finally.
 **Update**--configure may work, but that's the wrong driver.  The configure line should be:

./configure

(No arguments) This causes all drivers to be created.  That worked for me.

I typed

make

That failed, because it couldn't find the .config file.  So I looked in boot for config files.  There were two:

config-2.6.10-5-386
config-2.6.10-5-686

I typed:

cp /boot/config-2.6.10-5-686 /usr/src/linux-source-2.6.10/.config

...went back into the alsa drivers directory (for me, that's /usr/src/alsa/alsa-driver-1.0.9rc4a

...and typed
make

That failed.  I got:

/bin/sh: scripts/basic/fixdep: No such file or directory.

**Update:**  Solution is to go into the linux source directory, and type:
make menuconfig

Then type:
make

As root, I entered

chown -R fastluck /usr/src/linux-source-2.6.10

...before compiling the kernel. Then I logged in as fastluck, to make sure I didn't inadvertently install the new kernel whilst building it.

---

### Post by fastluck on 2005-06-01
I think I'm talking to myself....but I'm going to keep posting messages--stay tuned.  When all is said and done, I'll have a how-to.

---

### Post by fastluck on 2005-06-01
A helpful user told me to compile my kernel.  So I went into /usr/src/linux* and typed:

make menuconfig

I exited the program, told it to save, then typed:

make

After that I was able to build alsa.  But the configure step for alsa-drivers is:

./configure

...with no arguments.  When I did it the other way it didn't detect my card.

After ./configure, 'make' and 'make install' should do the trick.

---

### Post by fastluck on 2005-06-01
Ran alsaconf.  Selected cards are intel8x0 and legacy.  So the card is probably intel8x0.  Selected that.

**Note:** If you want to, you can pass intel8x0 to the ./configure instruction (see above).  I didn't try that.  I just built everything.  But it may work.

Went into mixer and selected Advanced Linux Sound Architecture.  No sound yet, so I rebooted.

I'm convinced I have the right driver.  But **still no sound.**  Help!
**Note:** intel8x0 is the right driver.

**Solution:**  Keep reading!

---

### Post by fastluck on 2005-06-01
Once I did all that, I still had no sound.  

The mixer app, in KDE is on the panel at the bottom of the screen.  I right-clicked on it, and toggled all of the input and output items off and on.  **That did the trick!**  Of course, the mixer app disappeared from the panel for some reason, but my sound now works.  This is an idea I got from several people who were nice enough to post their success--that seems to be a common thread.  And the alsa documentation--it warns that everything is muted by default.

I'm going to put all this into a better how-to. But in the meantime, this thread contains all the answers to the problems I've encountered. I am still working on getting the USB hard drive to work, but I'll have that working soon as well. And let me know how things worked for you!  My email is fastluck [at] email [DOT] clom (remove the 'l' from 'clom').

And **rate this thread!**  I don't want anyone else ripping their hair out like I did.

Fastluck

---

### Post by Kornelius X on 2005-07-01
Hi there,

I've installed Ubuntu on my Vaio t 350, and everything, so far, is working well.   I was wondering if anyone has been able to get the function and/or volume buttons to work of the system?  

Thanks!

---

### Post by fastluck on 2005-07-02
[QUOTE=Kornelius X]Hi there,

I've installed Ubuntu on my Vaio t 350, and everything, so far, is working well.   I was wondering if anyone has been able to get the function and/or volume buttons to work of the system?  

Thanks![/QUOTE]
 I haven't, and it would be really useful.  I just haven't researched it yet.

Cheers

---

### Post by ranf on 2005-07-04
[QUOTE=Kornelius X]
I've installed Ubuntu on my Vaio t 350, and everything, so far, is working well.   I was wondering if anyone has been able to get the function and/or volume buttons to work of the system?  
[/QUOTE]

Does the T-Series have jogdial? If yes give sjog or rsjog a try.

---

### Post by Kornelius X on 2005-07-06
hi there,

No, the T series has no jog-dial...   It has all the standard function keys, a wifi switch, and a couple of volume buttons.   Still no luck getting them all to work.   

Thanks,

K

---

### Post by fastluck on 2005-07-07
EmperorLinux (a company who sells aftermarket laptops reconfigured for Linux), at [http://www.EmperorLinux.com](http://www.EmperorLinux.com), now supports this particular model.  I'm sure the quote I received from them is subject to change, but this shows what they're currently charging.

Here's the email I received from them, in case anyone wants to go that route. Their preference is UBUNTU, but of course you can choose just about any linux distro you want.

DISCLAIMER:  I am in no way associated with this company.  But originally this was the route I was going to take, I'm impressed with the communications I had with them and I strongly believe in what they do.



```
> ---------------  Automated:  --------------- Thank you for your 
> interest in an EmperorLinux Kiwi T250.
> Your new Linux system is in our database as indicated below.
>
> The status of your EmperorLinux laptop is: quoted.
> The status of your payment for it is: quote.
>
> System:
>     EmperorLinux: Kiwi T250:
>     Sony vgn-t250, 1200 MHz, 512 MB RAM,
>     60 GB drive, 10.6" 1280x768 LCD, DVD-RW, 10/100/wifiBG/56k,
>     Ubuntu Hoary / Windows (10G /win, 2G /data),
>     Kiwi T250 manual,
>     12 months Linux Technical Support                 0.00 x1
>     + os: Depot Install: Sony VAIO T250P/L          400.00 x1
>     Tax: 0.0%                                         0.00
>     Shipping: FedEx (Next Day):                      75.00
>     ----------------------------------------------------------
>     Total:                                          475.00
>
>
> Order Info:
>     Invoice #:     XXXXXXXXXXXXXXXX
>     Order Date:
>     Ship Date:      (estimated)
>     System Status: quoted
>
>
> Ship Address:
>    XXXXXXXXXXXX
>     ,
>     UNITED STATES
>
> Billing:
>     Amex:
>     quote
>
> Notes:
>     1. qt: 5-23, 7-06
>
> Terms:
> This quotation and any order stemming from it are governed by our 
> Terms and Conditions of Sale:
>   [http://www.EmperorLinux.com/policy/terms_conditions.php](http://www.EmperorLinux.com/policy/terms_conditions.php)
> Our Support, Warranty, and Return policies are also hereby referenced.
> Every attempt has been made to ensure accuracy in the description and 
> pricing of this system.  The pricing in this quote is valid for 10 
> days from the date of the email.  Prices are subject to change after 10 days.
>
> Enjoy your new EmperorLinux Kiwi T250!
>
>
>
> --
> -- Lincoln
>
> *------------------------------------------------------------------*
>
> |  Lincoln D. Durey, Ph.D.  |  Phone:    1-888-651-6686            |
> |   Electrical Engineer     |  in GA:    (770)-612-1205            |
> |     EmperorLinux, Inc.    |  Fax:      (770)-612-1210            |
> |     900 Circle 75 Pkwy.   |  web:      [www.EmperorLinux.com](www.EmperorLinux.com)      |
> |     Suite 1380            |  support:  [email]support@EmperorLinux.com[/email]  |
> |     Atlanta, GA 30339     |  email:    [email]lincoln@EmperorLinux.com[/email]  |
>
> *------------------------------------------------------------------*
```

---

### Post by ranf on 2005-07-07
[QUOTE=Kornelius X]No, the T series has no jog-dial...[/QUOTE]
Ahh, OK.
[QUOTE=Kornelius X]It has all the standard function keys, a wifi switch, and a couple of volume buttons.   Still no luck getting them all to work.   
[/QUOTE]
Run xev to see if X gets at them.

Maybe the ACPI daemon grabs them first. Try:
```
sudo tail -f /var/log/acpid
``` and then press the buttons. If you see some new lines you can start fiddling with acpi events (located in /etc/acpi/events).

---

### Post by romkey on 2005-07-28
[QUOTE=ranf]Ahh, OK.

Run xev to see if X gets at them.

Maybe the ACPI daemon grabs them first. Try:
```
sudo tail -f /var/log/acpid
``` and then press the buttons. If you see some new lines you can start fiddling with acpi events (located in /etc/acpi/events).[/QUOTE]
 I've been wrestling with my VGN-T350P.  Got video to work perfectly, as well as WiFi and on-board ethernet (haven't bothered w/bluetooth yet).  However, audio is fighting me.  I installed the latest Alsa driver 1.09b and ran Alsaconf -- it detects a sound card -- reported as an "Intel 82801DB/DBL/DBM (ICH4" (gets cut off at that point), but still get no sound...

Any ideas?  Anyone manage to get a T350 series audio working?

---

### Post by fastluck on 2005-07-28
Does the driver load?  Have you futzed-around with kmix to turn on sound?  For some reason, when you run alsaconf the driver is initially set to mute.

---

### Post by fastluck on 2005-08-08
I find that the touchpad is constantly getting in my way when I type, and repositioning the cursor to places I don't want it to.  But I need the touchpad when I don't have an external mouse connected.  So I wrote this Ruby script that toggles it (to get the Ruby interpreter, type apt-get install ruby. I've found that it's far more capable and usable than bash or csh).

This script checks to see whether the psmouse module is loaded.  If loaded, it unloads it.  If unloaded, it loads it. 

Here it is, for anyone who needs it:

```

#!/usr/bin/ruby
# Toggle mouse touchpad module
# Copyright 2005 by John Reynolds, Tijeras, NM., fastluck@email.com
# This source code may be used under the terms of the GPL.
#
# I originally wrote this code because of the annoying habit my
# Sony Vaio VGN-T150 laptop has of repositioning the mouse cursor
# whenever I hit the spacebar. When this script is run, it will 
# "toggle" the module's "loadedness" depending on whether or not
# it is already loaded.  Now I can hook up an external mouse and
# unhook the onboard one.
#

# MODPROBE method:
# Install or uninstall a module based on the number of matches
# found (number of matches should never be more than one).
def modprobe(nrmatches)
	modulename="psmouse"
	if (nrmatches > 0)
		puts "Uninstalling #{modulename}"
		`sudo modprobe -r #{modulename}`
	else
		puts "Installing #{modulename}"
		`sudo modprobe #{modulename}`
	end
end


# NUMSTRMATCHES method
# Iterate over the items in the array and return the number array
# elements that contain the value {valuetomatch}.
def numstrmatches(stringarray, valuetomatch)
	count=0
	for str in stringarray
		if (str =~ /#{valuetomatch}/)
			count = count + 1
		end
	end
	
	count
end

# Main program

# Get list of loaded modules.			
stringarray = [`cat /proc/modules`]

# Get number of strings that match 'psmouse'	
# NOTE:	If you're replacing this with something else,			
# it would be a good idea to make sure that this doesn't 
# return extra matches.  If it does, you may have to modify
# this code.
nm=numstrmatches(stringarray, 'psmouse')
			
#Uncomment the following for debugging		
#puts "Result from numstrmatches: #{nm}"

# Call the modprobe method--it will decide whether to
# load or unload.		
modprobe nm

```

---

### Post by Kornelius X on 2005-08-14
HI there, 

I tried running that code, and it gives me the following;
[Sat Aug 13 22:30:54 2005] 1 client rule loaded
[Sat Aug 13 22:37:50 2005] received event "button/lid LID0 00000080 00000001"
[Sat Aug 13 22:37:50 2005] notifying client 8202[1000:1000]
[Sat Aug 13 22:37:50 2005] client has disconnected
[Sat Aug 13 22:37:50 2005] executing action "/etc/acpi/lid.sh"
[Sat Aug 13 22:37:50 2005] BEGIN HANDLER MESSAGES
[Sun Aug 14 00:52:41 2005] starting up
[Sun Aug 14 00:52:42 2005] 21 rules loaded
[Sun Aug 14 00:55:27 2005] client connected from 8190[1000:1000]
[Sun Aug 14 00:55:27 2005] 1 client rule loaded

I then pressed all the function keys, and nothing happened....  

still no luck : (

---

### Post by fastluck on 2005-08-14
> **Kornelius X]HI there, 

I tried running that code, and it gives me the following said:**
>  1 client rule loaded
[Sat Aug 13 22:37:50 2005] received event "button/lid LID0 00000080 00000001"
[Sat Aug 13 22:37:50 2005] notifying client 8202[1000:1000]
[Sat Aug 13 22:37:50 2005] client has disconnected
[Sat Aug 13 22:37:50 2005] executing action "/etc/acpi/lid.sh"
[Sat Aug 13 22:37:50 2005] BEGIN HANDLER MESSAGES
[Sun Aug 14 00:52:41 2005] starting up
[Sun Aug 14 00:52:42 2005] 21 rules loaded
[Sun Aug 14 00:55:27 2005] client connected from 8190[1000:1000]
[Sun Aug 14 00:55:27 2005] 1 client rule loaded

I then pressed all the function keys, and nothing happened....  

still no luck : (
 Can you post the output from

cat /etc/proc/modules

Thanks

---

### Post by Kornelius X on 2005-08-20
Hi there,

I don't have a etc/proc   directory.  I do have a etc/modules however...  the contents of this;

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

ide-cd
ide-disk
ide-generic
lp
mousedev
psmouse
sbp2
sr_mod


any ideas? 

Thanks!

---

### Post by pavan on 2005-09-01
For those of you having sound issues, here is how I solved it:

Open alsamixer in the command prompt and go to the external amplifier (it is turned on by default) and turn it off... and bingo!! there is sound.  \\:D/ 

Pavan

PS: I have a vgn-t140p

---

### Post by drrjv on 2005-09-21
I got alsa to work on a T350 using Pavan's method of turning the external sound off.

BTW, I am using Breezy which has the .9 version of alsa

---

### Post by digitaldan on 2005-09-23
I have a few small issues with my vgn-t350p, maybe someone can help....

Suspend to ram, 

this is killing me.  The acpi scripts are working fine, unloading modules, video , ect...  But when the machine wakes up I get hda dma timeout errors which take up to 120 seconds to reset and cause the box to freeze.  I have had the scripts turning dma off, on, even sending resets  to the drive but nothing works.  I'm coming from a powerbook who's suspens to ram was phonominal.  (I'm using s3_bios option on boot).

Volume buttons

they send all send the same acpi/keycode number to xev/acpi.  So to linux they all look like the same key and cannot distinguish between them.  (mute is actually mouse 4)

GPRS

I don't expect this to work, but if anyone has figured out how to activate it .... when I had windows on it (not anymore :) )the GPRS modem looked like a regular com port that a modem script could communicate with, I'm guessing in linux its just a matter of toggling the hardware to turn it on (and turn the wifi off) and get a /dev/ttySX

---

### Post by waltrothfuss on 2005-11-17
The link to the journal page with directions for getting the video chip working correctly does not work.  Clicking on the link returns an error message, not found on server.  Any other way to find out what is in the directions?

This is the non-working link:

[http://ubuntuforums.org/journal.php?do=showjournal&j=108](http://ubuntuforums.org/journal.php?do=showjournal&j=108)

---

### Post by fastluck on 2005-11-17
[QUOTE=waltrothfuss]The link to the journal page with directions for getting the video chip working correctly does not work.  Clicking on the link returns an error message, not found on server.  Any other way to find out what is in the directions?

This is the non-working link:

[http://ubuntuforums.org/journal.php?do=showjournal&j=108](http://ubuntuforums.org/journal.php?do=showjournal&j=108)[/QUOTE]

Yeah--they shut down all the journal links for some reason.  Let me look at my laptop at home.  If you're using the latest UBUNTU it's a lot easier.

---

### Post by diomedes on 2006-01-13
I have a VGN-T370P.  

With the latest Fedora, sound worked out-of-the-box, and thanks to [markadavis.org/vgnt150.html](http://www.markadavis.org/vgnt150.html) I was able to get the widescreen display operating at its native 1280x768 using [855resolution](http://perso.wanadoo.fr/apoirier/) in a short script called from the bottom of /etc/rc.d/rc.sysinit:

```
855resolution 52 1280 768 > /dev/null
855resolution 43 1280 768 > /dev/null
```... and a monitor config that looks like this:

```
HorizSync    20 - 90
VertRefresh  50 - 100
DisplaySize 230 138
Modeline "1280x768" 80.14 1280 1344 1480 1680 768 769 772 795
```

I have only recently found Ubuntu and plan on installing it as soon as it this CD has downloaded.  

Tuxmobil.org has a [helpful page](http://tuxmobil.org/sony.html) for those of us running Linux on Sony notebooks.

---

### Post by Peacepunk on 2006-03-04
[QUOTE=fastluck]
**Update:**  Video now works.  Solution is posted here: [http://ubuntuforums.org/journal.php?do=showjournal&j=108](http://ubuntuforums.org/journal.php?do=showjournal&j=108)
[/quote]



Deadlink I'afraid...

---

### Post by parravan on 2006-04-11
[QUOTE=fastluck]I installed several distributions on my vaio, including Mandrake, Suse, and Debian Sarge.  All with mixed results.  Installing UBUNTU instantly resulted in a usable laptop!  Here are the details:

Video (at 1024x768) - but widescreen doesn't work, so there's a one-inch bar on both sides of the screen that is unusable.  **Solved**

Sound doesn't work. **solved**

Ethernet, modem, wireless, bluetooth - All detected and appear to work flawlessly!  UBUNTU was instantly able to access the internet and download patches.  In fact, while installing Ubuntu, my wireless switch was off.  The installer even informed me that I need to turn on the switch. I was impressed with how smoothly everything went.

Mousepad works just as well as it did under windows, in every way.

**Update:**  Video now works.  Solution is posted here: [http://ubuntuforums.org/journal.php?do=showjournal&j=108](http://ubuntuforums.org/journal.php?do=showjournal&j=108)

**Update:**  Sound now works.  Solution at end of thread. How-to will be put together within the next couple of days.

**Update** Bluetooth Mouse: [http://ubuntuforums.org/showthread.php?p=609310#post609310](http://ubuntuforums.org/showthread.php?p=609310#post609310).

Fastluck

P.S: Thanks Hannes_ Tread and LuvDemHeels for the help! I couldn't have done it without you.  (Well, maybe I could have, but then someone else would have had to show me the way.) :)

P.P.S:  If you want to have someone else do the work, there's a post later in this thread (here: [http://ubuntuforums.org/showthread.php?p=244794#post244794](http://ubuntuforums.org/showthread.php?p=244794#post244794)) with some info about EmperorLinux.[/QUOTE]

I'm a newbie with some previous unix experience and would like to install kubuntu on my T250.
It has the 5g hidden install partion and the 60g drive with 2 partitions with XPP on the first- data on the second.
What would you recommend?
I am thinking of repartitioning with partition magic to give me 10g partion.
Is this all I need?
Should it be below the 1024 cylynder?

I'm still searching for more definitive guidlines but thought I would see if you can give me a jump start with the initial installation for a dual boot sytem setup.
Any links you know of would be appreciated.

Thanks
 Joe

---

### Post by stargateQ on 2008-05-13
good evening my friend ,,,
i have the same problems with my sony laptop vgn-t170p
could you guide me ,so i can solve the problems too ?
thanks in advance 

ps. when i started the linux version ,,i though it would be difficult ,,,but this surpass my imagination !!!
thanks again 

> **fastluck said:**
> I installed several distributions on my vaio, including Mandrake, Suse, and Debian Sarge.  All with mixed results.  Installing UBUNTU instantly resulted in a usable laptop!  Here are the details:

Video (at 1024x768) - but widescreen doesn't work, so there's a one-inch bar on both sides of the screen that is unusable.  **Solved**

Sound doesn't work. **solved**

Ethernet, modem, wireless, bluetooth - All detected and appear to work flawlessly!  UBUNTU was instantly able to access the internet and download patches.  In fact, while installing Ubuntu, my wireless switch was off.  The installer even informed me that I need to turn on the switch. I was impressed with how smoothly everything went.

Mousepad works just as well as it did under windows, in every way.

**Update:**  Video now works.  Solution is posted here: [http://ubuntuforums.org/journal.php?do=showjournal&j=108](http://ubuntuforums.org/journal.php?do=showjournal&j=108)

**Update:**  Sound now works.  Solution at end of thread. How-to will be put together within the next couple of days.

**Update** Bluetooth Mouse: [http://ubuntuforums.org/showthread.php?p=609310#post609310](http://ubuntuforums.org/showthread.php?p=609310#post609310).

Fastluck

P.S: Thanks Hannes_ Tread and LuvDemHeels for the help! I couldn't have done it without you.  (Well, maybe I could have, but then someone else would have had to show me the way.) :)

P.P.S:  If you want to have someone else do the work, there's a post later in this thread (here: [http://ubuntuforums.org/showthread.php?p=244794#post244794](http://ubuntuforums.org/showthread.php?p=244794#post244794)) with some info about EmperorLinux.

---

