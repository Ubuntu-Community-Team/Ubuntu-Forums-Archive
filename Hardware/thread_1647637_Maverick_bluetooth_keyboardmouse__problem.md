---
title: "Maverick bluetooth keyboard/mouse  problem"
date: 2010-12-17
forum: Hardware
---

### Post by sherbey on 2010-12-17
I have a small media centre pc running mythtv under lucid, and I use a bluetooth keyboard/trackpad with it with no issues; I'm in the process of setting up another such box with maverick and although I can get the keyboard to pair and work, when I reboot the pc I can't get the keyboard to connect. I have to delete the pairing and re-pair. This renders the wireless keyboard completely useless. A friend of mine has the same issue with similar hardware.
Clean install of 64 bit 10.10 ubuntu, logitech cordless mediaboard pro, generic bluetooth usb device.

How do I make the bluetooth connection persistent?

---

### Post by bric on 2010-12-18
I've installed Maverick on a new htpc for my parents and yes, same issue.  It's with the 32bit version (I think...hard to recall now, it was several weeks ago that I actually installed before getting the keyboard by mail).

Anyhow, same issue.  I pair in this manner:

Run through the wizard, type the pin on the bluetooth keyboard, happily read the success message, enter the pin again into a second pop up (dialogue) box with the WIRED keyboard because the bluetooth isn't actually working.  Then remove the keyboard, run the wizard again, type the pin with the bluetooth keyboard, read the success message, and it works!  This time without the second dialogue box.  Now I can use the bluetooth keyboard.

If I reboot (or leave it alone for a while --- 30+ min this time), then I have to restart the whole process.  Remove the keyboard, possibly reboot, then proceed as described above.

Once after rebooting I got the same 'second' popup asking for the pin again but I wasn't sure which pin (the first or the second) and I couldn't remember them anyway.  And I can't reliably summon that 'second' popup box after reboot so the point is moot (not worth trying to find out if one of the pins will work).

For reference, the 'second' dialog says, "Device 'Logitech Cordless MediaBoard Pro(TM)' wants to pair with this computer" and "Please enter the pin mentioned on device Logitech Cordless Mediaboard Pro (mac address here)".

Does this sound the same as for you? Or does it pair in a nicer fashion for you?

---

### Post by Raven2k360 on 2010-12-18
Seriously, WTH did they do with the kernel in the 10.xx releases???  Bluetooth worked perfectly in 9.10 for me, no muss no fuss...never had to set it up once...now I can't get it to work in any v10 release, or any current Fedora release (13+).

---

### Post by sherbey on 2010-12-19
I don't remember having to type the password in more than once (using the bluetooth keyboard). Once the connection is lost I can click on the gnome bluetooth widget, hit preferences and the keyboard is there (obviously using a wired mouse/kb), but it can't seem to be coaxed back to life without deleting it and running through the 'set up new device' mechanism. 
This is bordering on a showstopper; its not the first time ([http://ubuntuforums.org/showpost.php?p=10017614&postcount=8](http://ubuntuforums.org/showpost.php?p=10017614&postcount=8)) I've had working hardware on an older version of ubuntu borked by a newer version - though this time there seems to be no work-around I can find.

---

### Post by bric on 2010-12-20
You're lucky at least that you don't have to go through quite the same rigamarole to just make it connect in the first place (adding, removing, adding again just to get it working).  I'm mildly envious.

However, I agree, a near showstopper.

Once I have time to get round to my parents place (a fair possibility this Christmas season) I'm going to see if I can file a bug on Launchpad.  I'll post back here when I've done it.

---

### Post by icefest on 2010-12-20
I can confirm that I am getting the same message as bric Except I cannot get it to pair at all.  
Maverrick 10.10
 eeepc 1000HE 
Dell bluetooth keyboard.

---

### Post by bric on 2010-12-21
Hi icefest, I went through a couple bluetooth keyboards trying to get them to work on my parents' htpc (an apple and my own dell bluetooth from home).  Neither one worked for me.  I was able to pair the bluetooth mouse from dell but not the keyboard.  Got that second dialogue box popping up and wasn't successful after that... though I don't know if I repeatedly removed and tried again as I did with this logitech.

Anyhow, I know repeatedly removing/adding eventually gets this mediaboard pro paired and working.  It just doesn't stay connected.

Sigh.  Let us know if you get anywhere.

---

### Post by sherbey on 2010-12-30
This feature seems to be linked to a fresh install of maverick; I've got a Compaq 311c with built-in bluetooth that had lucid on it and has been upgraded to maverick; works fine with the logitech mediaboard pro - it connects, it works OK when you reboot the computer and when the screensaver kicks in. I've also got an eee 701, which has a fresh install of maverick on it; every time the screensaver kicks in you have to type the PIN in using the wired keyboard, followed by the PIN on the bluetooth keyboard otherwise it won't connect. Both of the above laptops are running 32bit standard gnome based ubuntu. 

I've tried searching for any configuration file that contains the bluetooth address of the mediaboard on the 311c without success, and bluez documentation is absolutely dire so no clues there as to where it keeps this information there. Checked the gnome keyring, not a sniff of anything bluetooth there either. Trawling through the installed files list for bluez listed in synaptic drew a blank too.

Something has changed in the bluez configuration between lucid and maverick. I can't find out what, and short of trawling the source code I'm not sure there is a way of finding out. I don't really want to hose the maverick install on my htpc, install lucid then upgrade to maverick just to fix this. 

I guess most people don't use bluetooth keyboards, and for them this isn't any sort of deal. However it used to work and it doesn't now, and it prevents a whole class of PC useage (HTPCs) from functioning, as well as making most bluetooth device use a complete pain. So its a MAJOR REGRESSION which fell through whatever testing was done on maverick prior to release. Hopefully this isn't the beginning of a 'so there's a bug, bite me' microsoftian attitude creeping in here :(

---

### Post by bric on 2010-12-30
That's interesting about the upgrade from Lucid being okay.  I'm tempted to go that route but, like yourself...
> I don't really want to hose the maverick install on my htpc, install lucid then upgrade to maverick just to fix this. 

In my case I installed ... bluez compat and (?) another bluez related package I can't recall at the moment (I made note somewhere).  And now the bluetooth can be kick started by doing a "sudo hidd --search" (on the wired keyboard).  An unsatisfactory workaround in almost all respects.

Hey, I wonder if I could dump that command into a cron job and have it repeat every 15 minutes or so.  Hmmmmm... have to try that next time I'm over at my parents place (with the htpc).

---

### Post by sripplinger on 2010-12-30
I have a Mediaboard Pro and brand spanken new installations of Meerkat on an MSI laptop (built in bluetooth) and on my HTPC (USB Bluetooth).  With my HTPC I am having the exact issue described by bric.  Pair, entering the code on the mediaboard and then 0000 on a wired keyboard.  Delete pairing and repair, only entering pin on mediaboard.  Keyboard then works, but only until it goes to sleep, is turned off, or the computer restarts.

I need to test this further on my laptop, but pairing worked much more easily.  Code only entered once on the mediaboard.  I got no request from the bluetooth keyboard to have its pin entered on the laptop keyboard (that's what the 0000 is).  I haven't tested whether the pairing is retained after reboot or turning the keyboard on and off.  Maybe I'll do that tomorrow.

But for now, my theory is that it may have something to do with the bluetooth hardware being used, rather than the installation (i.e. built-in bluetooth vs USB).  If anyone else comes up with something more, lemme know.  Also, if someone submits a bug report please post a link here so the rest of us can follow and contribute.

---

### Post by sherbey on 2010-12-31
The internal bluetooth device on my 311c is actually a USB device:-

mark@mark-laptop:~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 03f0:231d Hewlett-Packard 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0408:0ff1 Quanta Computer, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 0bda:0159 Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

3:2 is bluetooth, 2:2 is the internal webcam, 1:2 is the SD card reader. AFAIK most built-in devices like this on laptops are configured this way.

I don't know where or how the PIN is stored, but it feels a tad high level to be actually within the bluetooth hardware. That would require non-volatile storage and would imply that the pairing would move with the dongle, which I don't see any evidence for.

---

### Post by sripplinger on 2010-12-31
Well, I'm happily typing this out with my Mediaboard Pro on my laptop.  No issues connecting.  No issues staying connected after restart, etc.

@Sherbey:  Didn't mean to say that I thought the PIN would actually be stored in the bluetooth hardware.  But good point that even the internal bluetooth on laptops is a USB device.  Case is true for me, too.  Still, I think that there is likely a difference between what was put in my laptop and what I bought as a low-profile dongle.  This does not appear, however, to have anything to do with a fresh install of Maverick vs upgrading from Lucid.

Just for reference, here is what lsusb is reporting as my laptop vs external bluetooth devices:

Laptop - 
Bus 005 Device 003: ID 0db0:a97a Micro Star International Bluetooth EDR Device

External - 
Bus 006 Device 002: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)

---

### Post by sripplinger on 2010-12-31
Oh, and I just confirmed.  When I switch off my internal bluetooth on the lappy and use the dongle instead I get the same issues I did with the other computer.  So the issue does indeed appear to be with how the software bluetooth stack is playing with different bluetooth hardware.

Anyone know a good bluetooth dongle with a Micro Star chipset?

---

### Post by bric on 2010-12-31
My cron job idea didn't work... though perhaps there's something that could be done along those lines (but not with hidd --search).

I had thought of filing a bug report too but since the computer is at my folks' place it's made it a bit difficult.  Perhaps one of thse days if no one beats me to it.

---

### Post by sripplinger on 2010-12-31
Well, this certainly seems like a bug in the latest bluez package.  I may look into installing the Lucid bluez version and see if that helps.  If I get around to it I'll also submit a bug report. ;)

---

### Post by sripplinger on 2011-01-01
Just so that we are all comparing full notes here, what USB adapters are you all using?  Mine is a low-profile Iogear Class 2 (10 meters).

---

### Post by bric on 2011-01-01
Not sure the exact model but the bluetooth adapter I got was an IOGear class 1 device (100m) ... this was after I had trouble with another little adapter of some sort that I tried with an Apple bluetooth keyboard (and gave up on) and the dell bluetooth adapter/keyboard/mouse combo that I use on my own htpc.  With these 2 adapters I just failed completely to get them to pair/function with their respective keyboards (couldn't make them work by mixing matching either -- e.g., apple keyboard + dell adapter).  So I've had problems with maverick with various adapters/input devices.

At least I got the Mediaboard to connect, sort of.  Woohoo!

I'll look up the exact IOGear model when I'm back at my parents place.

---

### Post by sripplinger on 2011-01-01
Quick question.  I've been thinking about getting a Class 1 adapter, but I'm not sure if it is going to benefit me or not.  The Mediaboard Pro is just a Class 2 device, but will the Class 1 adapter give a better strength so that I could plug it in the back of my HPTC in my entertainment center?

Also, in the interest of finding some kind of solution to this issue, what do you all think would be the best way to go about installing the Lucid bluez package?  Would adding the Lucid repos cause problems with a Maverick install?  Should I just manually go and find all of the packages online?

---

### Post by bric on 2011-01-01
Regarding class 1: 

I went through a several RF keyboards (4) after failing with the apple and dell BT devices trying to find something with suitable htpc range.  So I was interested when I needed an adapter to try Logitech's mediaboard pro I was (naturally?) attracted to the advertised 100m range. Also, buying it from the computer shop it only cost $20 as compared to the $20 that I paid at the box store for class 2 adapter.

Along with same price and advertised (if unnecessary) range was that I read that battery life would conceivably be better with the stronger adapter signal.

Here, this was the adapter (an IOGear GBU321 - IOGEAR Enhanced Data Rate Bluetooth USB Adapter 100M Range)
[http://www.bestdirect.ca/products/220309/IOGEAR/GBU321/](http://www.bestdirect.ca/products/220309/IOGEAR/GBU321/)

As far as Lucid Bluez in Maverick .... ???
I don't have any idea really, though it doesn't sound like something I'd want to try myself.

---

### Post by sripplinger on 2011-01-01
Seeing as we are both using Iogear adapters, I'm guessing that all their stuff falls under those having issues with the latest bluez.  I'm thinking I may just go online to manually download and install the Lucid bluez package and all the required dependencies.  It's the dependencies that really make it a pain.

---

### Post by sherbey on 2011-01-01
I now have a bluetooth keyboard working under maverick, by robbing the bluetooth dongle off another machine. It attaches without fuss and is persistent after reboot (no PIN entry required to re-pair); its a very old MSI BToes. The other two dongles I have require PIN entry on reboot, and are truculent about pairing at all. I'm posting the lsusb very verbose reports for all three in case this throws any light on the subject.

The belkin adaptor is reported by lsusb as a broadcom  USB 2.0 hub, a keyboard, a broadcom corp (??) and finally a belkin bluetooth device:-
Bus 005 Device 012: ID 050d:0017 Belkin Components B8T017 Bluetooth+EDR 2.1
Bus 005 Device 011: ID 0a5c:4503 Broadcom Corp. 
Bus 005 Device 010: ID 0a5c:4502 Broadcom Corp. Keyboard (Boot Interface Subclass)
Bus 005 Device 009: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
 There are reports of this device working under 9.10 but not 10.10

Interestingly the BToes device reports the 'friendly name' that was in use on the original machine and not its new host (though nothing is listed as paired) so it must have some non-volatile storage on board.

---

### Post by sherbey on 2011-01-01
I've filed a bug report on launchpad (bug #[696378]("https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/696378"))

---

### Post by bric on 2011-01-01
heh heh ... so did I, just now.

:oops:

[https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/696393](https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/696393)

I've marked it as a duplicate but hopefully it helps anyway.  Mine was kind of a 2 part bug since I had issues connecting as well as issues staying connected.

---

### Post by bric on 2011-01-01
For those who didn't know, if a bug affects you:

1. Log into launchpad (create an account if necessary)
2. Near the top you will see something like:

[INDENT]This bug affects 2 people. Does this bug affect you? (and a little icon)[/INDENT]

3. Click on the little icon (looks a bit like a pencil) and you get a "yes this bug affects me / no this bug doesn't" popup.

I imagine that having more people affected by a bug gives it more weight.  We can probably use all the people possible voting on something like this since not everyone has a mediaboard pro.

---

### Post by Raven2k360 on 2011-01-04
> **sripplinger said:**
> Just so that we are all comparing full notes here, what USB adapters are you all using?  Mine is a low-profile Iogear Class 2 (10 meters).

I'm using the internal Dell BT mini-card, model 370 I believe as well as a Dell BT Travel Mouse.  I'm in Windows right now, and Device Manager says that Broadcom is the driver/chipset provider for the mini-card.  Worked fantastic in 9.04 and 9.10, but anything after that is a wash.

---

### Post by sherbey on 2011-01-05
Some further information :)

The bluetooth pairing data is located in /var/lib/bluetooth/nn:nn:nn:nn:nn:nn/ where nn: etc is the bluetooth address of your dongle or internal card. There is a file called linkkeys which contains the bluetooth address of paired devices followed by whitespace then the encrypted PIN; its owned by root and its permissions mean that it is only readable by root.

---

### Post by sripplinger on 2011-01-05
It seems like this bug is specific to adapters running with the Broadcomm Corp inside.  I just ordered an Azio (one of the new BTD211's, they look nice) which, from what I can tell, runs with the Cambridge Silicon Radio chipset.  I'll report on my success when I get it, hopefully this weekend.

---

### Post by sherbey on 2011-01-06
I've got a CSR dongle that won't connect well (0a12:0001); though it quite often reports a bluetooth ID of 00:00:00:00:00:00 (i.e. dead) so it may be a defective part. Its the risk you run when you buy a £2 part off amazon I guess...

---

### Post by sherbey on 2011-01-06
I've just found this website:-
 
[https://launchpad.net/~brian-rogers/+archive/ppa](https://launchpad.net/~brian-rogers/+archive/ppa)
 
there is a maverick .deb for bluez 4.84 that I shall try to install on my system, but it'll have to wait until the weekend. Anyone else feeling brave?

---

### Post by sripplinger on 2011-01-06
> **sherbey said:**
> I've just found this website:-
 
[https://launchpad.net/~brian-rogers/+archive/ppa](https://launchpad.net/~brian-rogers/+archive/ppa)
 
there is a maverick .deb for bluez 4.84 that I shall try to install on my system, but it'll have to wait until the weekend. Anyone else feeling brave?

I just tested this out and...  IT WORKS!  My Mediaboard Pro now connects normally and persists.  I tried turning off the keyboard and turning it back on as well as a system restart.  The only issue is that it may take the keyboard a few seconds to re-pair.  Great find sherbey!

This guy's repository does have some other stuff that I don't want or need.  After I installed his bluez package, and then upgraded my libbluetooth3, I just deactivated the repository so it didn't install pulseaudio libraries on my system.  I don't want it to screw with my Mythtv install.

---

### Post by bric on 2011-01-07
(regarding the install of bluez 4.84)

Wow, that sounds like good news ... I hope.

Does this mean that this is part of the alpha/pre-alpha stuff for 11-4 being backported to Maverick?  

Or is Maverick likely to see an update to bluez 4.84 through the official repositories? Is there a way to find out when/if?

I'll give it a try too (maybe this weekend?) and let you know if it works... is there any way to revert though if I end up worse off?

---

### Post by sripplinger on 2011-01-07
I'm sure you can just uninstall bluez (sudo apt-get purge bluez, then sudo apt-get autoremove).  After that remove or deactivate this guy's repository, update and reinstall bluez and gnome-bluetooth.

And I just got my Azio BTD211 today.  I tested it on my laptop which still has the native Maverick version of bluez (4.69?).  It works fine.  It just seems to be adapters that use the Broadcom Corp. hardware.  I still need to see if this new Class 1 adapter will give me any more luck connecting to it when I've got it plugged in the back of my HTPC and shoved into a compartment on my entertainment center.  Crossing my fingers!

---

### Post by sherbey on 2011-01-08
Just installed bluez-4.84 from the repository mentioned earlier; my mediaboard pro keyboard now successfully pairs (easily) with my computer and doesn't require any iritating PIN entry when it goes to sleep, the screensaver kicks in or the computer is rebooted. The dongle I am using is the broadcom based belkin  b8t017. I'll try out my CSR dongle later to test out stripplinger's thoughts on CSR hardware. Reee-sult!

---

### Post by sripplinger on 2011-01-08
Booyah!

---

### Post by bric on 2011-01-08
Yep, Booyah!!

Thank you Brian Rogers (and everyone else here for applying some brains to the problem).

The WAF is good at home with the htpc, now perhaps the one at my parents place will gain a reasonable ... PAF?

---

### Post by icefest on 2011-01-08
So how do I install bluez-4.84? (and get rid of the repo afterwards)

---

### Post by bric on 2011-01-09
> **icefest said:**
> So how do I install bluez-4.84? (and get rid of the repo afterwards)

1. Open a terminal (applications > accessories > terminal).

2. sudo add-apt-repository ppa:brian-rogers/ppa

3. sudo apt-get update

4. sudo apt-get bluez

5. Remove/disable the repository.  Possibly 
sudo remove-apt-repository brian-rogers/ppa
or just start the "Update Manager" from the administrative menu, then click the setup/options button on the dialog, then de-select the brian-rogers repos from the appropriate tab.

(and obviously don't install any other updates before removing the repository)

Please note that this is obviously not the official release and could possibly create other issues.  Though as was said above, probably (probably) you can remove bluez entirely and then install it again from the main repo if desired.

---

### Post by sripplinger on 2011-01-09
I actually was having some issues with the brian-rogers bluez and my new adapter.  I just did a sudo apt-get purge bluez followed by a sudo apt-get autoremove to get rid of that installation and all associated packages.  Then (with the brian-rogers repo disabled) I simply did sudo apt-get install gnome-bluetooth, which also installed the original bluez package again.

The newer bluez package did seem to work fine with the adapter I had issues with before, but the default bluez installation in Maverick seemed to work better for my Azio adapter.

---

### Post by abstraktion on 2011-01-09
> **bric said:**
> 1. Open a terminal (applications > accessories > terminal).

2. sudo add-apt-repository ppa:brian-rogers/ppa

3. sudo apt-get update

4. sudo apt-get bluez

5. Remove/disable the repository.  Possibly 
sudo remove-apt-repository brian-rogers/ppa
or just start the "Update Manager" from the administrative menu, then click the setup/options button on the dialog, then de-select the brian-rogers repos from the appropriate tab.

(and obviously don't install any other updates before removing the repository)

Please note that this is obviously not the official release and could possibly create other issues.  Though as was said above, probably (probably) you can remove bluez entirely and then install it again from the main repo if desired.

Thanks for the help...
Just a couple of corrections to help others...

4. sudo apt-get install bluez
5. Remove repository by... sudo rm /etc/apt/sources.list.d/brian-rogers-ppa-maverick.list

:)

---

### Post by bric on 2011-01-10
And there's another reason why you should never totally trust a person on the forums to give good advice.  However well intentioned, they tend to make typos or just give the wrong info from time to time.

Of course, this is the first time that I've ever made a mistake.
;)

---

### Post by marcb_ro on 2011-01-10
Just wanted to let you know that reverting to bluez 4.84-~0maverick from brian-rogers/ppa fixed my bluetooth issues on fresh install of ubuntu 10.10 x64.

I have a Cambridge Silicon Radio dongle (0A12:0001), and it just wouldn't work with the 4.89 bluez package. I would like to know how to freeze the package, so it doesn't get updated from the ubuntu main repo on *apt-get upgrade*.

By the way, shouldn't this thread be marked [SOLVED]?

Cheers!

---

### Post by sherbey on 2011-01-11
The default bluez in Maverick is 4.69, so you are updating bluez to 4.84 rather than reverting. There are other packages in the Brian Rogers PPA (pulseaudio I think) which you may or may not want to upgrade, so the simplest way to prevent an update to this would be to install the repository, update bluez ONLY then disable the repository. I'd suggest you use the Synaptic Package Manager unless you want to cut and paste command lines into a terminal window.
 
Sripplinger is having problems with 4.84 which is why I hadn't flagged it as [SOLVED]
 
My CSR dongle 0A12:0001 doesn't play with 4.84, but I think its actually defective. It doesn't work with 4.69 either :(

---

### Post by sripplinger on 2011-01-11
My 'issue' with 4.84 may have been with connectivity rather than software.  I haven't tested 4.84 again, though, as 4.69 has been working fine for me with my new adapter.

---

### Post by marcio123 on 2011-01-13
On right of [B]MediaBoard Prothere is a 'touchpad'. Does it work like touchpads in laptops ? 

Does it work on Ubuntu 10.10 ?
[/B]

---

### Post by bric on 2011-01-13
> **marcio123 said:**
> On right of [B]MediaBoard Prothere is a 'touchpad'. Does it work like touchpads in laptops ? 


Yes.

> **marcio123 said:**
> 
Does it work on Ubuntu 10.10 ?
[/B]

If you follow the directions in this thread (either with dongle or software updates), yes.

---

### Post by barbecuy on 2011-03-21
Just waned to let evrybody know that the brian rogers source for bluez fixed my problem
Had to install bluez following the command line, reconnect my keyboard one more time, reboot the computer.
I have a Dell Bt Travel mouse and an AZIO KB333BM (model designed/copied from the mac bluetooth keyboard). Mouse was working fine but got the annoying enter pin ley every time I start up my laptop, but not any more, this thread fixed the problem I tried to fix for a week
Thanks

---

### Post by DrDunkMcNally on 2011-03-21
You guys are the best, I know we're close to the next release but you've saved me a LOT of frustration!

Cheers!

---

### Post by GusPS on 2011-06-03
Hi. On the Brian PPA site there's only the 4.89 version.
Anyone has the 4.84 amd64?
Thanks!

---

### Post by GusPS on 2011-06-04
I'm testing 4.89, it's more stable than the one from then official repos, but I get tx timeout too.
I've also changed the power property from true to false.

---

### Post by bric on 2011-06-04
I've updated to Natty Narwhal (11.04) and things are working better than ever for me (I still had some occasional quirks needing reboots with the other fix).  So if you're feeling brave about upgrading (not without its own risks)...

Good luck.

---

