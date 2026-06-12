---
title: "gutsy on acer laptops"
date: 2007-10-18
forum: Hardware &amp; Laptops
---

### Post by dptxp on 2007-10-18
I am downloadiing Gutsy, shall be carrying out a fresh install on ACER 5101ANWLMi with 2 GHZ Turion, 512 DDR2 RAM, ATI Radeon Xpress 1100, Atheros AR5005G Wireless Network Adapter, Synaptics touchpad, ENE 5 in 1 cardreader.

Had not tried wireless in Feisty, ENE card reader did not work.

Any feedback on Gutsy on ACER ?

---

### Post by nukedathlonman on 2007-10-18
I have an Acer 5002WLMI and have been using Kubuntu on it since last November.  What happened in Novemebr is I was sick of fixing XP based systems, and haveing tried the Windows MEII (Vista) beta's, I knew I had to find a better OS.

I had a few issue's initaly out of the box with the kernel drivers, but was able to resolved the error messgaes in dmesg which took all of 2 days of research and tweeking - it's been rock solid since...  Well, I admit I just hit a minor issue whenl  I upgraded to Gusty after it went live last night.  I've got to find and fix a bug with the video adapter setup - the messages that get displayed between the spash screen and the login screen are being corrupted - I'll be investigating that later whenI get home.  I'm pretty sure it's just a minor video adapter setup problem, and will be easy to fix.

---

### Post by fadain on 2007-10-18
Just finished installing kubuntu on acer 5101 and it's a disaster. Can't hibernate/suspend anymore, volume buttons not working, screen flickers during booting, kopete crashes when logging into msn. The only thing good is that fonts look very very pretty.

---

### Post by wastedfluid on 2007-10-18
Hello friend.

Acer Aspire 5100.

The Kopete bug ^^ this guy ^^ is talking about, is a known bug, and awaiting a patch.

Volume buttons do not work - the volume goes from 0% - to 11%.   And back and fourth.  A fix for this is to go to Kmix, Settings, Global Shortcuts.. and change th shortcut for "Raise Volume" in there.. that works for me.


I've never been able to hibernate/suspend w/ my Acer..i've always had to use "uswsusp" w/ s2disk and s2ram --force to hibernate/suspend.  Unfortunately, that doesn't work anymore, either.

My screen flickers a lot during boot - but  who cares.  it boots.

You need to use ndiswrapper to get your wireless card to work properly (It works, just reports false signal usage)

but, other than that.. it's okay.

I'm waiting on patches for uswsusp, and Kopete.  Other than that - it's okay.

I want to go back to Fiesty, though.  Too late, now.. Fiesty was perfect.  All volume keys worked, s2disk worked, s2ram worked.. yuck.  Gutsy is a semi-disaster for me.

---

### Post by soupcatcher on 2007-10-19
Hi Guys,

I also have an acer 5101AWLMi and I have just installed Gutsy and the results have been far from disastrous but then again I haven't played with it much so far.  The installation went quite smoothly with no problems.  I must admit that I did experience the Suspend/Hibernate problem but now it seems to work again.  I couldn't bare to use Gusty after using the Suspend feature in Edgy and Fiesty.  Now I don't have a solution to the problem but an observation.  When the ATI accelerated graphics driver is not in use (System > Administration > Restricted Drivers), the Suspend feature seems to work on my Acer.  Please try this out to see if the same happens on your notebooks.

Also my card reader has never worked in either Edgy or Fiesty.  Noone as yet has written the drivers in linux for them.  But I could be wrong.

If you want a disaster, install Vista instead ;)

---

### Post by dptxp on 2007-10-19
I found this solution to long boot up time with black screen.
The boot time is short now, but I get some BIOS error after grub screen.
I have loaded the restricted ATI drivers.
[COLOR="Red"]The ENE card reader now works on 5101,[/COLOR] tested with MMC card after log in.


to disable, go to the terminal and type -

sudo gedit /boot/grub/menu.lst
...and enter your password

a big text file will open - you need to scroll right down to where it says ...


## ## End Default Options ##

title Ubuntu 7.10, kernel 2.6.22-14-generic
root (hd0,2)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=79b1afc9-1898-45b2-a4e4-c53dd8e67db7 ro quiet splash


...or similar. just change 'splash' to 'nosplash' and save. reboot and celebrate!
cheers
roger

---

### Post by dptxp on 2007-10-19
BTW, has anyone tried 64 bit on ACER5101 ?

---

### Post by AJB2K3 on 2007-10-19
Acer Aspire 3690

Everything but card reader and media keys working and i cant figure this out.
Does this work?
[http://advhertz.altervista.org/install-debian-gnulinux-on-acer-aspire-9113-wlmi/#SpecialKeys]("http://advhertz.altervista.org/install-debian-gnulinux-on-acer-aspire-9113-wlmi/#SpecialKeys")

---

### Post by dptxp on 2007-10-19
> **AJB2K3 said:**
> Acer Aspire 3690

Everything but card reader and media keys working and i cant figure this out.
Does this work?
[http://advhertz.altervista.org/install-debian-gnulinux-on-acer-aspire-9113-wlmi/#SpecialKeys]("http://advhertz.altervista.org/install-debian-gnulinux-on-acer-aspire-9113-wlmi/#SpecialKeys")

Debian packages should work in Ubuntu. No guarantee, but one can try.
What card reader do you have on your laptop ? Was it working in Feisty ?

---

### Post by cupacup on 2007-10-19
I have Acer 5002WLMI upgraded from feisty, everything works except hibernate and cpu scaling. I also noticed that DMA is disabled(dmesg) and bluetooth applet is missing.

---

### Post by fe99jlo on 2007-10-19
Aspire 3690

After Gutsy clean install, don't works the the cpu scaling, and a new problem:

Now i can't resume after suspend my computer. It worked fine on festy and edgy, but now the computer hang when i try resume after suspend.

I post a bug at [https://bugs.launchpad.net/ubuntu/+bug/154342]("https://bugs.launchpad.net/ubuntu/+bug/154342")  and i hope it could be useful.

Also, good news, now the ENE card reader works fine with SD cards, but i can't open my MS card. I haven't other type of card for test.

---

### Post by wastedfluid on 2007-10-19
Okay.

I have figured out how to fix hibernate for My Acer Laptop.

Disable the ATI Driver(In KDE, KDE->System Settings->Advanced->Restricted Drivers), for Gnome.. I have no idea.

After you disable the ATI Driver,

go to a terminal and:

sudo nano /etc/uswsusp.conf 

(If you do not have nano, sudo apt-get install nano - I'm pretty sure it comes on all installs)

It should look something like this:

```

# /etc/uswsusp.conf(8) -- Configuration file for s2disk/s2both
resume device = UUID=70554dbc-5ffc-4c5c-bd2e-258ad118db4f
splash = y
compress = y
early writeout = y
image size = 425876684
RSA key file = /etc/uswsusp.key
shutdown method = platform

```

You need to change the UUID= part, and replace it with your swap's /dev/ address.

To do this, just type 'sudo fdisk -l' - and you should find your swap in there.

```

wastedfluid@fluid:~$ sudo fdisk -l
[sudo] password for wastedfluid:

Disk /dev/hda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5ea4f703

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1305    10482381   83  Linux
/dev/hda2            1306       12030    86148562+  83  Linux
/dev/hda3           12031       12161     1052257+   5  Extended
**/dev/hda5           12031       12161     1052226   82  Linux swap / Solaris**
wastedfluid@fluid:~$     

```

Ok, so my swap is /dev/hda5.. now, go back to your 'sudo nano /etc/uswsusp.conf' - and comment out that long UUID= number, and add your /dev/hda5.. or YOUR swap.  Mine looks like this:

```

wastedfluid@fluid:~$ cat /etc/uswsusp.conf
# /etc/uswsusp.conf(8) -- Configuration file for s2disk/s2both
#resume device = UUID=70554dbc-5ffc-4c5c-bd2e-258ad118db4f
resume device = /dev/hda5
splash = y
compress = y
early writeout = y
image size = 425876684
RSA key file = /etc/uswsusp.key
shutdown method = platform
wastedfluid@fluid:~$                       

```

After you replace your resume device with your swap /dev/ address,

go to a terminal and type

'sudo dpkg-reconfigure uswsusp'

And it should re-configure everything.  Give it a go, and type sudo s2disk.  This should work for most Acer laptops...

---

### Post by mabdelaziz on 2007-10-19
Travelmate 6292

im very new to linux, everything is fine so far, but i have no sound :( the system acts like theres sound, and files play normally, but nothing is coming out of the speakers....

i read alot of posts and turns out i have a hda_intel card which has alot of issues with linux (tried all the major distros uptodate....NONE gave me sound!!!!)

any help greatly appreciated guys, i really wanna move away from windows
thnx in advance =)

---

### Post by mabdelaziz on 2007-10-20
guys sound works on travelmate 6292!!!!!!!!!!!!!!!!!!!!!!!!!!
i followed the instructions at 

[https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)

the instructions where really easy even for a complete noob like myself!!!! im so happy right now, i wont be going back to windows for a loooooooong time!!!

thank u ubuntu community, im in debt =)

---

### Post by ramadhian on 2007-10-20
My Laptop is Aspire 5051ANWXMi
- AMD Turion 64 MK36 2.0Ghz 
- ATI Radeon Express 1100
- Wireless Atheros Chipset

My Gutsy Installation result :
- Wireless Atheros Work Excellent with Restricted Driver
- ATI Restricted Driver can not be enabled
- Synaptic Touchpad work fine
- Bluetooth work and BlueTooth Applet fine
- MMC Reader work fine and Automatically call gThumb application to import photo & video
- WebCam still not working even kernel detected as Microdia Chipset (In WIndows XP it detected as OrbiCam)
  but someone already posted here about Microdia webcam / OrbiCam webcam.
  I already try the tips but still not work yet. 
- Boot Process take so much time, i have changed at GRUB option splash to nosplash
  and add option vga=791 and changing /etc/usplash.conf resolution to 1024x768
  but it still not make boot grub process a bit quicker
- Missing USplash after GDM Login
- Sometime I get frozen and wait for a few second to make my system giving a respon whenever I use mouse or toucpad to click somethin , it look like frozen and not giving a respon.
- If You wanna make a DualBoot "Ubuntu+Windows XP"
  need to add an entry manually at /boot/grub/menu.lst, not like in Feisty that can handle this so great.

I still digging for the grub boot time process

Any other Tips ?

---

### Post by dptxp on 2007-10-20
> **ramadhian said:**
> My Laptop is Aspire 5051ANWXMi
- AMD Turion 64 MK36 2.0Ghz 
- ATI Radeon Express 1100
- Wireless Atheros Chipset


- ATI Restricted Driver can not be enabled

Any other Tips ?

In my 5101, gutsy downloaded the ATI drivers and enabled them, were you connected to
the internet when you tried to enable ?

---

### Post by AJB2K3 on 2007-10-20
Opps I forgot to say i was still on 7.04

---

### Post by kosson on 2007-10-20
I've got an ACER 5101ANWLMi with 2 GHZ Turion with a Broadcom BCM 4318 (a major pain in the proverbial...) plus a PCMCIA wifi RaLink RT2561/RT61.

After Gutsy initial desaster I took another path installing with an alternative kubuntu cd and pick'n "Install a command-line system".
After take off I installed a freh kde based ubuntu:
apt-get install kubuntu-desktop kubuntu-artwork-usplash

Everything went fine, system booting normal with bootsplash with remarcable speed ! i was in a beautifull state of elation !

After this I remarked the following:
-even after enabling Broadcom wifi nothing hapened (taking a dmesg interogation showed there's something with dhcp leases - so a major pain in the proverbial, I'm sick with the fracki'n Broadcom winstrom)
- the biggest surprise came from RaLink, which I've boughted specialy to bypass Broadcom pain. So, both of the wifi show up in KNetworkManager, if I clisk to connet for one of them they go to a fatal 57 %. After some seconds reports failure cu connect. Interogation of log showed something with dhclient... frack'em up... my spine was burni'n and I felt that my stupid head is about to explode.
So, no wifi for the moment...
-test hybernation: no hybernation
-testing card reader I had a pleasant surprise as digiKam showed up.

Conclusion: if I'll pach wifi I would say that I'm a happy user... until then you know: spine... head... fra''''n

Thats it !

P.S. I'l tahe ndiswrapper way...

---

### Post by dptxp on 2007-10-20
Any of you getting bios error #81 with a few more error lines after GRUB ?
I get some sort of NETWORK error also when I shut down.
ACER5101, 2 MHZ Turion, luckily atheros WIFI, not tested wifi though

---

### Post by dptxp on 2007-10-20
sorry, duplicate post

---

### Post by ramadhian on 2007-10-21
ATI Driver work now , I download it from Synaptic Package Manager

Thanks..

---

### Post by ljbenjamin on 2007-10-21
Hi,

Just wanted to share my experience with the Acer Aspire 5024WLMI and Feisty --> Gutsy Kubuntu upgrade. Most things working properly.

CPU clocking - powernowd clocks to 800, 1200 and 1600Mhz

Sleep/suspend to RAM - Quite slow (10 - 15 seconds) but working

Hibername - Extremely slow (5-6 minutes for hibernate --> running again). Patience required as system appears frozen for about 3-4 minutes, white band across the screen, no keyboard response. Then shuts down. When you hit the power button, you need to use grub to "boot" Linux. This starts your previous session but takes 2-4 minutes depending on how much was written to disk i.e. what you were running in your session. Once the hibernate is over, the system thrashes the disk and CPU for another 5 minutes or so. All in all, hibernate isn't actually advantageous as the hibernate --> thaw --> usable system cycle takes so long...

Card reader - Working with SD cards but not Sony Memorystick.

Wireless - Working. I'm using acer_acpi 0.3 , ndiswrapper 1.48 (self compiled, not the ubuntu one).

A few things I've noticed about the wireless. My Acer provided wireless drivers worked on windows XP and ndiswrapper would install it and appear to be working as it should. However, knetworkmanager would always stall at 57% then dump me. I had to use the driver I've attached in "bcmdrivers.tar.gz ". I think these are originally HP's drivers but can't remember. Also, knetworkmanager now completely refuses to work with hidden SSID. In feisty,m it would allow you to connect with hidden ssid if you entered the details manually every time you wanted to connect (as it would forget them) but now, even this won't work I had to set my router to broadcast my ssid to be able to connect at all.

I've also attached ndiswrapper and acer_acpi versions that I'm using.

I also had to edit/create  /etc/modprobe.d/ndiswrapper to read "alias eth1 ndiswrapper"

and remember to:

make sure both modules are in "/etc/modules" so they start automatically. acer_acpi should come before ndiswrapper.
make sure that bcmxxx is blacklisted in /etc/modprobe.d/blackilist.

Let me know if this helps anyone.

/ljbenjamin

---

### Post by darrenn on 2007-10-21
acer 3680 everything seems to work fine except suspend and hibernate. Once I get it to work I will upgrade to gutsy.

---

### Post by ramadhian on 2007-10-21
acer_acpi work fine in Feisty ,..atheros wireless signal a bit better, but in Gutsy if I install module acer_acpi, my Atheros wireless can not work .. 

Atheros Wireless Signal in Gutsy much better without acer_acpi

is it acer_acpi really needed since wireless, bluetooth, MMC Reader work fine ?

but according to my test, applet panel for LCD Brightness level need acer_acpi to be loaded  to make it work ,,

--------------------------------------------------
Gutsy 7.40
Acer Aspire 5051ANWXMi
AMD Turion 64 Mobile Technology
14,1" WXGA Acer CrystalBrite LCD
ATI Radeon Xpress 1100
Atheros Wireless Chipset
Bluetooth 2.0 EDR
OrbiCam (Microdia Chipset)

---

### Post by teachop on 2007-10-21
Acer aspire 3100 - I am happy and grateful to the linux and gutsy devs.  The SD card reader works now, the Wifi works "out of the box", and Compiz works by addition of XGL.  The touchpad was very reasonable right out of the box - I did end up tweaking it just a bit in the conf file.

As has been well documented, the suspend/resume isn't working, which the reports say is due to the restricted driver I am using.

I have a problem with my ntfs partition that I have not figured out.  When I go to access it, it says "unable to mount the volume HDD".  But it was working at first so I need to dig into what happened there, since my music is on the ntfs.

All in all, so far, this is a great release for my Acer!

---

### Post by soupcatcher on 2007-10-21
> **dptxp said:**
> Any of you getting bios error #81 with a few more error lines after GRUB ?
I get some sort of NETWORK error also when I shut down.
ACER5101, 2 MHZ Turion, luckily atheros WIFI, not tested wifi though

I'm also getting bios error #81 when I start up.  What is it?

---

### Post by tarekeldeeb on 2007-10-22
Hello all ..

I have an Acer Aspire 5050/5051 with AMD64 .. installed Gutsy .. looks gr8 ..:popcorn:

my problem is with the 5in1 ENE card reader .. it does not work ..

is there any procedure to test/activate or maybe install some missing drivers ? :confused:

Thanks in advance,
Tarek

---

### Post by bobyy on 2007-10-22
HY
Acer 3150 ENE card reader work /volume keys ok/cpu-scalling ok/wirelles with Atheros set..ok/ATI drivervork with 1600 scorein (glxgears) / ewrithing out of box...

---

### Post by dptxp on 2007-10-22
> **tarekeldeeb said:**
> Hello all ..

I have an Acer Aspire 5050/5051 with AMD64 .. installed Gutsy .. looks gr8 ..:popcorn:

my problem is with the 5in1 ENE card reader .. it does not work ..

is there any procedure to test/activate or maybe install some missing drivers ? :confused:

Thanks in advance,
Tarek

It seems that 712 works, 710 does not (ENE Card Reader)

---

### Post by AJB2K3 on 2007-10-22
What setup do you use for getting the media keys working on the aspire?

---

### Post by dr_cerebro on 2007-10-22
Acer Aspire 5050-4872  Installed Ubuntu Gutsy Gibbon x86_64.

Blank screen at boot, which lasted 5 minutes to boot, I have to edit the grub to nosplash, and now, it boots in text mode and lasts 12 seconds to the login screen.

Wifi not working OTB, I had to install acer_acpi-0.8.2 and ndiswrapper (self-compiled), and download the 64 drivers for XP.  Sometimes it freezes when trying to connect (not often), but works perfect when connected.

Card reader works perfect.

Bluetooth not tested yet (I don't know how yet), I see the bluetooth icon, but I do not see the bluetooth antenna icon.  My cell phone does not detect another bluetooth device, but maybe I just doing something wrong in Ubuntu.

Audio muted by default, so I enabled surround, unmuted it and works perfect.

I had to install:

```
sudo aptitude install xserver-xgl
```

(I don't know what it does...I'm a newbie) in order to make Compiz Fusion work with my ATI card (ATI Radeon Express 1100)... and I love it !

Battery not recognized in any Linux distro.

---

### Post by VicAlpha on 2007-10-27
> **AJB2K3 said:**
> What setup do you use for getting the media keys working on the aspire?
I use keytouch

---

### Post by ramadhian on 2007-10-28
my Acer 5050 work fine with WiFi, Card Reader, Bluetooth,
except the Brightness Level Applet .

How do I make Brightness Level applet work without installing "acer_acpi" ?

---

### Post by Koziasty on 2007-10-28
my Acer 5022 wlmi works perfectly, although there were some troubles using ndiswrapper to install the wireless, because my router got confused if i used the linux driver. my laptop REQUIRES acer_acpi for the wireless to work.

i can use only some of the function buttons, but all the main ones (brightness, sound, block touchpad, tunr the screen off, num pad) work.
Hibernation and suspend work sometimes. 
There is strange flickering when watching videos and using fglrx (i dont have a need for fglrx, so i use ati driver instead - problems gone).

no other problems, it runs quicker and smoother under gutsy though i do get an odd halt. It is much quieter, too. 

Hope this helps anybody

---

### Post by thellawel on 2007-10-28
Acer Aspire 5100

Fresh install of Gutsy (AMD 64). Almost everything works except:

No splash screen (and ? long boot time) - managed to get it to work on shut down by changing the settings in  /etc/usplash.conf for my screen resolution (xres=1280 yres=800) but unable to get it to work on boot - changing grub settings doesn't appear to do anything

ENE Card reader - works for most SD cards (except my 1gb one ?doesn't works for cards > 512mb) but not with Sony Memory Stick (unable to test with any other card types)

Had to install xserver-xgl  (sudo aptitude install xserver-xgl) to get desktop effects to work.

Otherwise a fab install, and much more faster/stable then vista!

---

### Post by AJB2K3 on 2007-10-28
> **VicAlpha said:**
> I use keytouch

Keytouch?

Mine ene wont acces MSDP via MS/MSDP adapter (nothing new there) Fujifilm XD's not working aether on my 3690

---

### Post by Seisen on 2007-10-28
I have an Acer 5630 and everything works fine, well I haven't tried using the camera or the card reader. I have to use the restricted driver manager for my wifi.

---

### Post by joao82 on 2007-10-28
Gutsy was problematic at first because of the slow boot, but it is easily solved.
Graphics card works ok with the default drivers.
No more of that volume bug coming out from just one speaker, but now the volume keys on the keyboard can't adjust the sound level because of the 0-11% bug. Still it has sound and you canl set it with kmix on the tray.
One strange thing was that after the first boot I couldn't launch any program from the start menu, it just hanged for a while and disapeared. But after a restart it was just fine.
The thing that really set up my mind to install Gutsy was the card reader. Now it can detect sd cards and I no longer need a usb cable to see photos from my camera.
Wireless is ok too, I had wireless access running the live CD and immediately after installing it. Battery and cpu throttle work fine as before.
Go for it, but first check the solutions for the slow boot. This one worked for me:
> **LeeAdkins said:**
> Does the black Ubuntu loading splash screen work when you do that?

If not, here is another (slightly longer) fix that was posted elsewhere to fix it for reals. The problem with the slow boot is that the settings in Usplash can sometimes get messed up on install and hang up the boot. Removing some of the lines in menu.lst disables Usplash and fixes the problem. If you like the verbose boot up, then leave it. If you'd like the pretty Ubuntu boot up sequence, try this.

1) Put everything back in /boot/grub/menu.lst that you took out ( "ro quiet splash" in the kernel line and "quiet" at the end)

2) At the very end of the kernel line after  "splash" , add "vga=791" This is the weird part for me, because I'm not exactly sure why the number is 791. Make sure this goes on the same line, though.

3) Save that file, close it, and open up /etc/usplash.conf

4) Change the screen resolution to the resolution you are actually using. Save it and close it.

5) Grub won't know anything about this until you rebuild the boot, so do the following commands.

uname -r
This lists your current kernel version.

sudo update-initramfs -u -k *<insert results from uname -r here>*

This rebuilds the image that Grub uses to start the system.

Voila, you have fixed the boot speed issue and gotten the splash screen back. Reboot and enjoy the fruits of your labor. Your mileage may vary, but it worked for me on the first try and for quite a few other people throughout the forum.  This only works if Usplash is what was broken, which sounds right for all of you.  Also, you can always hit CTRL-F1 when the splash is running to get back to your verbose mode.

---

### Post by monstar on 2007-10-28
I have an Acer Aspire 5040

Turion 64 running Gusty 64bit clean install dual boot with WinXP

So far my video card works though I don't know if it does OpenGL/3d graphics..
My volume keys and brightness works out of the box however
Broadcom 4318 wireless adapter does not work, haven't been able to get it to work..

---

### Post by MarkMadsen on 2007-10-29
> **monstar said:**
> I have an Acer Aspire 5040

Broadcom 4318 wireless adapter does not work, haven't been able to get it to work..

On my Aspire 3680 running Gutsy, the bcm4318 only needed me to go to the restricted drivers manager, select the bcm3xx, and confirm that I wanted it to install the firmware.  Then it worked just fine.

---

### Post by darrenn on 2007-10-29
> On my Aspire 3680 running Gutsy, the bcm4318 only needed me to go to the restricted drivers manager, select the bcm3xx, and confirm that I wanted it to install the firmware. Then it worked just fine.

I have the same laptop as you. Suspend does not work for me at all. They say it's a bug in the latest kernel 2.6.22-14. Have you tried to use suspend by chance?

---

### Post by AJB2K3 on 2007-10-29
Still cant get my 3690 to detect the media keys.
AAAAAAAAAAAAAAAAAARRRRRRRRRRRRRRRRRRRGGGGGGGGGGGGGGG!!!!!!!!!!!!!!!!!!!!!!!!!

---

### Post by Zorael on 2007-10-29
Gutsy recognizes my media keys on my Acer Aspire 9815, but the volume buttons only go between 0% and 11%, with no noticable difference in volume.

Downgrading to Feisty kmilo and restarting fixed it, but now there is no visual feedback.

---

### Post by pljosephs on 2007-10-30
[FONT=Arial]Travelmate 4150 Infrared port and card reader not working

Can anyone tell me how to get the card reader and the infrared port working on the Acer Travelmate 4150?[/FONT]

---

### Post by monstar on 2007-10-30
I tried using the Restricted Drivers before, I had no luck with those..
I reinstalled several versions of the BCML5.inf drivers using ndiswrapper and had no luck with that.
I recently found some 64bit Windows BCML5 drivers and decided to try those but they don't work either.

--------
monstar@monstarL:~$ ndiswrapper -l
bcmwl5 : driver installed
        device (14E4:4318) present (alternate driver: bcm43xx)
--------

But I get nothing when I check for wireless networks and my light does not come on either.
I knwo that with Linux the light does not stay on like Windows, it flickers only with internet activity...but it never comes on and does not detect anything

---

### Post by choifyken on 2007-10-30
my AS4520G installed gusty,soundcard & wlan card didn't work.wlancard can work with ndiswrapper at Festy,but failed in Gusty,soundcard can be reconized by OS as Nvidia HDA268,but no soud output.

---

### Post by Zorael on 2007-10-30
Downgrading kmilo revived the volume control, at least. One restart later I had the visual feedback, and actually the new Gutsy OSD instead of the old one. Yay.

---

### Post by VicAlpha on 2007-10-30
My Acer 3003 Wlmi is working perfectly with Gusty. My multimedia keys didn't work so i've installed keytouch. I've downloaded my bcm4318 drivers from acer's website and it's working perfectly.

---

### Post by monstar on 2007-10-31
Finally got my wireless to work on the Acer Aspire 5040

What I did was follow the ACER_ACPI installation thread
[http://ubuntuforums.org/showthread.php?t=224350&highlight=acer+3020](http://ubuntuforums.org/showthread.php?t=224350&highlight=acer+3020)

BUT, since that post shows acer_acpi_0.3 which is OLD
You have to use the newer Acer_acpi which can be found on Page 8

[http://code.google.com/p/acer-acpi-deb/](http://code.google.com/p/acer-acpi-deb/)

I downloaded [http://acer-acpi-deb.googlecode.com/files/acer-acpi_0.9.1+2.6.22-14.46-mumbly5_amd64.deb](http://acer-acpi-deb.googlecode.com/files/acer-acpi_0.9.1+2.6.22-14.46-mumbly5_amd64.deb)
Because I am using Gusty 64 on my Turion 64..

My Wireless light turned on by itself and I am writing this via Wireless for the first time!

---

### Post by jointstereotype on 2007-10-31
I have an Acer Aspire 5100 laptop (see signature for full details), and everything seems to work well with Gutsy except for the ENE card reader, which reads / writes fine to the two 256mb SD cards I have, but which refuses to play nicely with my 2gb SD card.

Wireless wasn't supported out of the box; I got it to work using a Python script linked here in the forum (ndiswrapper). Sound and volume controls worked out of the box, though I noticed the volume sometimes mutes itself whenever clicking the "+" or "-" buttons in the GNOME volume control applet.

3D acceleration works using the default Ubuntu restricted driver. Desktop compositing effects also work nicely using the XGL server in conjunction with said drivers - however video playback is very poor with desktop effects enabled (video tearing / vertical sync issues due to the lack of direct rendering).

The included Acer Orbicam doesn't work. Haven't done much searching for a driver just yet...

Oh, and the FN combination keys for volume and screen brightness work just fine.

---

### Post by monstar on 2007-11-01
**Solution for Acer Aspire 5040 clean install of Gusty64**

Ok, So I screwd up my Ubuntu and had to reinstall so I put my knowledge to the test.

Here is EXACTLY what I did to get my Broadcom 4318 AirForce One installed on the Aspire 5040.

First of all you will need the newest Acer-Acpi which is 0.9.1
[LINK]http://acer-acpi-deb.googlecode.com/files/acer-acpi_0.9.1+2.6.22-14.46-mumbly5_amd64.deb

Keep that on your desktop.
 
Make sure you have the appropriate drivers, some people can use the restricted. For me I had to look for the AMD64 Wifi Drivers
[LINK]ftp://ftp.support.acer-euro.com/notebook/ferrari_4000/driver/winxp64bit/80211g.zip
-You need specifically the BCMWL564.sys file for AMD64.

Use ndiswrapper to install the drivers, do what you need to do. You may need Ndiswrapper-utils or Ndiswrapper-common

Unzip 80211g.zip onto the desktop, and name it something simple.

Go to that folder in the terminal and type

---
sudo ndiswrapper -i bcmwl5.inf
---

It will install itself, to make sure you have installed it correctly type

----
ndiswrapper -l
----


For me it displays
monstar@monstar-laptop:~$ ndiswrapper -l
bcmwl5 : driver installed
        device (14E4:4318) present (alternate driver: bcm43xx)


Then I wanted to make sure I had the correct firmware..

I followed the forum here
[LINK]http://ubuntuforums.org/showthread.php?t=405990

I used the Online 0.3.2, and when I extracted the folder the desktop, I opened Install.py

I chose only to install the BCM43xx Firmware (Disregard the comment abotu Ndiswrapper needing to be reinstalled.  Let it do its magic then close when its finished..



Remember the Acer_Acpi file we downloaded at the beginning.  Run that file, let it install and your wireless light -should- turn on.

I didn't quite do it in that order, but the final time thats how I did it and the light came on.  So I think that is the best order to go in.


REALLY REALLY REALLY hope this helps people.  About 2 weeks ago. Ubuntu 7.10 was released and I was a complete nub to the Linux world...I've been pushing and playing with this $#%^$&$ ...stuff and I finally got my wireless working twice in the same day (Twice because I screwed something up going through terminal by myself)

---

### Post by harleyquine on 2007-11-01
Awesome.. worked for me on Acer Aspire 3050. I must of tried at least 10 guides and this is the only one that worked, thanks so much have had a headache all day trying to get wireless to work on my laptop!

---

### Post by Haxor on 2007-11-04
Hey everyone,

I installed Gutsy on an Acer Aspire 5630-6288, it looks pretty good.
Webcam is not working, does anyone has succeded on having this orbicam working?
I can see there is a V4L driver loaded, apparently it has been recognized and is on the V4L list as working one, but not for me. I installed camorama but can't access /dev/video0.
MMC reader is not working.
Mail, Web, P, e, and the keys that control CD player not working either just the usual mute/vol up-dn

Anyone?

Warper

---

### Post by pjrodz on 2007-11-05
> **Haxor said:**
> Hey everyone,

I installed Gutsy on an Acer Aspire 5630-6288, it looks pretty good.
Webcam is not working, does anyone has succeded on having this orbicam working?
I can see there is a V4L driver loaded, apparently it has been recognized and is on the V4L list as working one, but not for me. I installed camorama but can't access /dev/video0.
MMC reader is not working.
Mail, Web, P, e, and the keys that control CD player not working either just the usual mute/vol up-dn

Anyone?

Warper

i also have an acer 5630 laptop and i'm planning to install gutsy. pls advice. thanks!

---

### Post by kvonb on 2007-11-05
_-_

---

### Post by Haxor on 2007-11-08
> **pjrodz said:**
> i also have an acer 5630 laptop and i'm planning to install gutsy. pls advice. thanks!

Hey pjrodz,

Installation went straightforward: wireless, audio, screen resolution, touchpad, hibernation, everything else (the Fn+keys) works fine. :KS
I found out that camorama does not support V4L2 that is why it does not work. Yesterday I found that aMSN did detected the webcam but I got no image. I got an error stating Tk had crashed, it was too late to see what was happening, but seems that sound recording is also an issue with aMSN, I'll check it today.

MMC reader still not working, nor the e, P, mail, www, CD buttons.

Has anyone had webcam working without just a black screen?

Haxor

---

### Post by kurotsuno on 2007-11-08
I have a acer 5052 and I'm planning on installing ubuntu on the second partition that came with the laptop. 

What kind of problems am I most likely to encounter ? I'm planning on dual booting keeping vista as certain hardware I use I know will not work on ubuntu. 

How do I go about dual booting :)

---

### Post by pjrodz on 2007-11-08
thanks for the heads up guys. will try to install gutsy over the weekend. plan to do a dual boot system with vista too. will tell you guys how it goes. :)

---

### Post by DonL on 2007-11-12
> **Haxor said:**
> Hey pjrodz,

Installation went straightforward: wireless, audio, screen resolution, touchpad, hibernation, everything else (the Fn+keys) works fine. :KS
I found out that camorama does not support V4L2 that is why it does not work. Yesterday I found that aMSN did detected the webcam but I got no image. I got an error stating Tk had crashed, it was too late to see what was happening, but seems that sound recording is also an issue with aMSN, I'll check it today.

MMC reader still not working, nor the e, P, mail, www, CD buttons.

Has anyone had webcam working without just a black screen?

Haxor
After loads of reading, I found that the KDE program "Kopete" will use the camera.
I don't personally have a use for it, but I hate having something that doesn't work.
Now on to the multicard reader for my XD card.......

---

### Post by Giggity on 2007-11-13
> **DonL said:**
> After loads of reading, I found that the KDE program "Kopete" will use the camera.
I don't personally have a use for it, but I hate having something that doesn't work.
Now on to the multicard reader for my XD card.......Thanks for the tip, Don.  I wouldn't have ever tried that if you hadn't mentioned it.  Now I wonder how I can get *other* programs to use the webcam on my 5630!

---

### Post by shahrc on 2007-11-17
I'm using aspire 3002NLCi and installed Gutsy 7.04. Everything else worked except wireless even with ndiswrapper installation. Using ndiswrapper in edgy was succesful though... Still searching for answers..

---

### Post by ezeze5000 on 2007-11-19
> **darrenn said:**
> I have the same laptop as you. Suspend does not work for me at all. They say it's a bug in the latest kernel 2.6.22-14. Have you tried to use suspend by chance?

My WIFI works great too!
I'm typing this to you on my Acer 3680 right now.
My sound doesn't work at all, it looks like I have 2 drivers loaded OSS and ALSA.
I'm not getting any errors, every thing seems to work correctly, I just have no sound.

Any ideas?

---

### Post by leap on 2007-11-19
Hi i have a acer aspire 5002wlmi and was wondering when you upgrade, do you have to redo the wireless. I'm new and it took a long time to get it up and running.

---

### Post by bran on 2007-11-24
no major complaints on Aspire 9400

ring switcher in compiz-fusion does not work  meh

---

### Post by empty89 on 2007-11-25
Everything work perfect for me in travelmate 4154LMI except for the graphic card problem. But manage to fixed it. maybe 1 complaint the card reader.

---

### Post by msrinath80 on 2008-02-28
> **wastedfluid said:**
> Okay.

I have figured out how to fix hibernate for My Acer Laptop.

Disable the ATI Driver(In KDE, KDE->System Settings->Advanced->Restricted Drivers), for Gnome.. I have no idea.

After you disable the ATI Driver,

go to a terminal and:

sudo nano /etc/uswsusp.conf 

(If you do not have nano, sudo apt-get install nano - I'm pretty sure it comes on all installs)

It should look something like this:

```

# /etc/uswsusp.conf(8) -- Configuration file for s2disk/s2both
resume device = UUID=70554dbc-5ffc-4c5c-bd2e-258ad118db4f
splash = y
compress = y
early writeout = y
image size = 425876684
RSA key file = /etc/uswsusp.key
shutdown method = platform

```

You need to change the UUID= part, and replace it with your swap's /dev/ address.

To do this, just type 'sudo fdisk -l' - and you should find your swap in there.

```

wastedfluid@fluid:~$ sudo fdisk -l
[sudo] password for wastedfluid:

Disk /dev/hda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5ea4f703

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1305    10482381   83  Linux
/dev/hda2            1306       12030    86148562+  83  Linux
/dev/hda3           12031       12161     1052257+   5  Extended
**/dev/hda5           12031       12161     1052226   82  Linux swap / Solaris**
wastedfluid@fluid:~$     

```

Ok, so my swap is /dev/hda5.. now, go back to your 'sudo nano /etc/uswsusp.conf' - and comment out that long UUID= number, and add your /dev/hda5.. or YOUR swap.  Mine looks like this:

```

wastedfluid@fluid:~$ cat /etc/uswsusp.conf
# /etc/uswsusp.conf(8) -- Configuration file for s2disk/s2both
#resume device = UUID=70554dbc-5ffc-4c5c-bd2e-258ad118db4f
resume device = /dev/hda5
splash = y
compress = y
early writeout = y
image size = 425876684
RSA key file = /etc/uswsusp.key
shutdown method = platform
wastedfluid@fluid:~$                       

```

After you replace your resume device with your swap /dev/ address,

go to a terminal and type

'sudo dpkg-reconfigure uswsusp'

And it should re-configure everything.  Give it a go, and type sudo s2disk.  This should work for most Acer laptops...


The above procedure helped me to "Hibernate" my Fujitsu Lifebook S7110. I use Gutsy Gibbon (32 bit). Thanks a lot!

---

