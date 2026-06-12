---
title: "Successful installation of Ubuntu Edgy Eft on Samsung R20 T7200"
date: 2007-03-29
forum: Hardware &amp; Laptops
---

### Post by Nikos.Alexandris on 2007-03-29
**1.** Download ati driver **8.34.8**

([COLOR="Red"] *** Important ***[/COLOR] **I could not run gdm with the latest driver 8.35.5!** )

*Searching in ati's official webpage I bombed in to this... release notes for driver 8.34.8:*

[COLOR="Black"]The ATI Catalyst&#8482; Linux software suite is designed to support the following ATI Integrated products:

    * Radeon&#8482; Xpress 1250 IGP (both AMD and Intel)
    * Radeon&#8482; Xpress 200 series[/COLOR] 

 > Read here: [COLOR="Blue"]_[http://www2.ati.com/drivers/linux/linux_8.34.8.html](http://www2.ati.com/drivers/linux/linux_8.34.8.html)_[/COLOR]


**2.** Install edgy in text mode from edgy DVD

**3.** Boot in rescue mode

**4.** Install ati driver according to the unofficial ati linux driver wiki

[COLOR="Blue"]_[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)_[/COLOR]

**5.** Reboot and... have fun!


**[COLOR="Red"]* Problems I experienced till now:[/COLOR]**

[B]1. No 3D acceleration (!)

2. Fn+Esc forces the computer to sleep... but he never wakes up properly again !!!
[/B] - Although it worked once!!!



Also... [https://wiki.ubuntu.com/LaptopTestingTeam/SamsungR20?highlight=%28samsung%29](https://wiki.ubuntu.com/LaptopTestingTeam/SamsungR20?highlight=%28samsung%29)



Greetings,

Nikos.

---

### Post by jet2230 on 2007-04-10
thanks, i really wanted ubuntu on my r20 since the os it comes with (vista) is a load of crap. i hope this works.

---

### Post by jet2230 on 2007-04-11
yes it works.

i had to manually install the ati drivers, then ran the ati-config script.  Gnome works fine, but no full 3d accel from my ati gfx card. has any1 got this to work properly on samsung r20?

---

### Post by Nikos.Alexandris on 2007-04-12
Still haven't found any trick to get 3D with ATI 1250... :( 

We have to wait... !

---

### Post by jet2230 on 2007-04-17
> **Nikos.Alexandris said:**
> Still haven't found any trick to get 3D with ATI 1250... :( 

We have to wait... !

what do u mean? on my samsing r20 i can run openarena & beryl at same time. im sure openarena requires some sort of 3D stuff to work.

altho when i run glxgears i get:

Xlib:  extension "XFree86-DRI" missing on display ":1.0".

but will work fine when beryl is off

---

### Post by jet2230 on 2007-04-19
> **Nikos.Alexandris said:**
> Still haven't found any trick to get 3D with ATI 1250... :( 

We have to wait... !

how did u get the sleep function to work? mine just reboots on sleep mode

---

### Post by GlasWolf on 2007-04-23
I've just followed this procedure to install Feisty and ATI driver v8.36.5.  X loads at the correct resolution but I'm not sure I have 3D support.  Also there's no sound, despite it working in Edgy according to the testing page.

---

### Post by Nikos.Alexandris on 2007-04-24
I am sorry for being kind of late... About the sleep modus it just works some times and some times not... (in edgy)

---

### Post by Nikos.Alexandris on 2007-04-24
I also got this reply from HotFoot!

 Re: ATI 1250 under Feisty?
Hi Nikos,

Sorry for the late reply. I didn't get a notification of this message, so I only noticed it right now.

Installing the drivers for the Radeon 1250 IGP was as simple as going to the Restricted Drivers Manager and selecting to enable the drivers (Feisty). I did have to manually edit xorg.conf to get the proper resolution settings, but the 3D acceleration was a piece of cake.

HotFoot

Quote:
Originally Posted by Nikos.Alexandris
Hi!

I have a new Samsung laptop with ATI Xpress 1250 IGP card.

As I read you have the same chipset...

My question is if you could install feisty without installing manually any ati linux driver?

Please for a reply... ! I am thinking to upgrade to feisty but I am sceptical since the 7.04 beta live cd didn't let me boot... !!!

Thank you in advance,

Nikos.

---

### Post by GlasWolf on 2007-04-25
> **Nikos.Alexandris said:**
> Installing the drivers for the Radeon 1250 IGP was as simple as going to the Restricted Drivers Manager and selecting to enable the drivers (Feisty).
I did this, but 3D acceleration was still disabled.

> **Nikos.Alexandris said:**
> My question is if you could install feisty without installing manually any ati linux driver?
I'm pretty noob at all this, but I couldn't get X to load until I'd manually installed the 8.36.5 driver from text mode.

---

### Post by jet2230 on 2007-04-26
has any1 got dual screen to work with this ATI 1250? 

i have got it to work with  **aticonfig --dtop=horizontal --overlay-on=1 ** . This works fine, i can move applications to the next screen etc... but only in a normal gnome session.

has any1 got this to work with the beryl session? the best i can do is twin view on beryl, but would like to use it as a big desktop like in gnome session.

---

### Post by GlasWolf on 2007-04-26
Jet: seeing as you're the only person to have 3D acceleration, can you please detail the process you went through to set it up.  In other words, how did it vary from Nikos' original post?

---

### Post by GlasWolf on 2007-04-29
Finally managed to get this going.  It may have been as simple as running through the ATI installer GUI once I'd managed to get into X by running the text mode one.  Beryl still doesn't start, but at least I have something to work with...

---

### Post by GlasWolf on 2007-05-06
Looks like I'm talking to myself here.  Oh well, in case anyone else is reading I now have Beryl up and running by basically following the instructions [here]("http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL").  The only thing that doesn't work is viewing the cube itself (which crashes X), everything else is fine.  To really take advantage of Beryl you'll need to get your touchpad scrolling features running.  Although the pad works, it only does so as a regular mouse.  In fact, Feisty doesn't load the Synaptics driver even though it recognises it as one.  You just need to follow the instructions [here]("http://www.debuntu.org/2006/06/18/67-how-to-setting-up-touchpad-on-a-laptop-a-complete-guide") and you should be good to go.

The only remaining problem I have is a complete lack of sound.  There are plenty of posts all over about getting the Azalia SB300 working but I've yet to find a fix that works for me.  I've tried the updated modules available [here]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/103699"), but no joy.  The most hopeful method is [this one]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/106843"), but when I try to build the new modules at the end it doesn't create any files.  If someone can explain how to get the feisty-updates stuff mentioned in the last post in that thread then I'd be very grateful.

***Edit: working recompiled modules now uploaded - see [here]("http://ubuntuforums.org/showpost.php?p=2644090&postcount=22")***

---

### Post by fodder on 2007-05-08
I managed to get sound to work by following the instructions at
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/106843](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/106843)

There are a couple of steps not included in the last post of that thread. You need to install some packages to be able to build the modules. I installed the packages listed in the Master Kernel thread which seemed to do the job.

Instead of "make menuconfig" you have to run "make oldconfig && make prepare".

I got two script errors when compiling the modules, solved by copying the required scripts from /usr/src/linux-headers-2.6.20-15-generic.

Hope this helps.

Re graphics drivers: 3d acceleration works with the ati drivers but I found that they broke suspend and hibernate. For me these are more important so I went back to the open source drivers. If anyone knows how to fix power with the ati drivers, please let me know.

---

### Post by GlasWolf on 2007-05-09
Well you got me one step further on so thanks for that, but despite successfully compiling the new modules and copying them in I still have no sound.  Clicking on the speaker still results in the "No volume control GStreamer plugins and/or devices found" error.  However, having messed around with so many things to try and get it working may have broken it elsewhere.  I'm tempted to start from scratch now that I know how to get the rest of the hardware working.  The Vista triple-boot menu is the only thing I'm worried about!

I can also confirm that suspend and hibernate don't work for me either, but thankfully (for me) I don't really use them.

---

### Post by fodder on 2007-05-09
> **GlasWolf said:**
> Clicking on the speaker still results in the "No volume control GStreamer plugins and/or devices found" error.

Hmm I never saw this. Do you see volume controls if you run alsamixer in the console?

---

### Post by GlasWolf on 2007-05-09
Update - I reinstalled the whole thing from scratch, and got everything working fine, including sound.  But (and there had to be a but...) I've now lost my wireless access.  The real problem is it didn't come up immediately during the first install either, but seemed to suddenly start working.  It looks like the drivers are installed (in the restricted section, as they were last time) but I can't see any wireless networks.  Oh well, I'll work on that one tomorrow.

---

### Post by fodder on 2007-05-10
I know that feeling. I'm also on my second install. First time my wireless didnt work and then seemed to randomly start after a reboot. Second time it worked out of the box :confused:

---

### Post by GlasWolf on 2007-05-11
Oh well, at least I know I'm not going crazy.

---

### Post by GlasWolf on 2007-05-11
Yay, wireless is back!  I was trying all sorts of stuff to no avail, the last of which was entering manual settings as per [this]("http://ubuntuforums.org/showpost.php?p=2360813&postcount=18") post.  However, I'm sure what started it working was booting into Windows to make sure wireless still worked there.  I rebooted, went straight into Ubuntu, did a [FONT="Courier New"]sudo iwlist ath0 scan[/FONT] and 3 APs popped up straight away.

It's almost as if it's a power management thing, where Ubuntu can't see the card to configure it until it's been woken up by something else.

---

### Post by GlasWolf on 2007-05-12
I've uploaded my working sound modules [here]("http://www.glaswolf.net/ubuntu/r20_sound_modules.tar.bz2") in case they're of use to anyone.  Just unzip them using the archive manager and run [FONT="Courier New"]sudo cp snd-hda-*.ko /lib/modules/2.6.20-15-generic/kernel/sound/pci/hda/.[/FONT] from the directory where you put the files.

---

### Post by jet2230 on 2007-05-13
hi GlasWolf, thank you very much for sharing those sound module files - i needed them for my samsung r20 and your instructions worked like a charm.

i recently upgraded my distro from 6.10 edgy to 7.04 feisty.  everything wnt well except for the sound, wireless & beryl (all of which were working in 6.10 edgy)

i already got the wireles fixed, and ur files fixed my sound which is working fine now.

have u got any idea of how i could get my beryl fixed?  all the beryl stuff is still installed but now compiz is there as a option as well which it was not before. anyway neither beryl or compiz work under the beryl session. 

thanks again for them sound files.

---

### Post by jet2230 on 2007-05-13
erm, ive just been reading the other posts, sorry GlasWolf for not getting back to u quicker - i havn´t really checked out the ubuntu forums for quite a while. anyway if u need any files let me know, everything on my laptop is working fine.  i even got my xbox pad to work with ubuntu - its so cool.

DUEL SCREEN UPDATE
=====================

dual screen in beryl works fine - AS LONG AS BOTH RESOLUTIONS FOR BOTH SCREENS IS 1024x786 (or under).  i had this working perfect in 6.10 edgy, but since upgrading to 7.04 beryl does not work :( - i am working on a solution for this, if any1 can help pls let me know thanks.

---

### Post by GlasWolf on 2007-05-13
Did you use [this]("http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL") tutorial?  First thing is to make sure the ATI drivers are working - run fglrxinfo and see if it says ATI or mesa.  If it's still on the mesa driver, try re-running the ATI driver install from within X (see the ATI driver release notes for instructions).  Otherwise, go through the Beryl tutorial again carefully and see what happens.

---

### Post by jet2230 on 2007-05-13
ello, this is my fglrxinfo output:

za@bob:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon Xpress 1200 Series
OpenGL version string: 2.0.6334 (8.34.8)


im going thru that beryl guide u just gave, but i think i need to uninstall all my beryl stuff and reinstall it. but i dont know what to uninstall, so many files.

---

### Post by GlasWolf on 2007-05-13
There's a part of that tutorial about downgrading beryl-core by using a different repository, that may be all you need to uninstall.  Make sure you do all the stuff about creating a startxgl.sh file, and make sure you use the options menu to change the session to "Xgl" before you log in.  Also, I needed to use the tips about missing shutdown and restart buttons and themes not working, but Beryl was up and running by then.

---

### Post by jet2230 on 2007-05-16
well even after uninstalling all the beryl stuff and reinstalling it - i still have the same problem. been checking the other forums for answers on this, and so far this is the only solution i have come across:

LD_PRELOAD=/usr/lib/fglrx/libGL.so.1.2.xlibmesa beryl --replace &

i just might have to go back to 6.10 edgy i think the upgrade was a bad choice on my part.

---

### Post by GlasWolf on 2007-05-16
I've just noticed you're using ATI driver version 8.34, whereas I'm using the latest 8.36.5.  Might be worth upgrading before you go back to Edgy.  Alternatively, you could try a fresh reinstall of Feisty from scratch (with 8.36.5), as the linked tutorials in this thread have worked for myself and others.  Only wireless has proved to be a headscratcher, and seems to work if you can boot into Windows to "wake the card up" before going back to Ubuntu.

---

### Post by jet2230 on 2007-05-22
thanks for the advise GlasWolf, but even after upgrading to the new ati drivers 8.36.5 i still have the same issue with beryl.  

i was looking to reintsall 6.10, but looks like i&#314;l be reinstalling 7.10 . 7.10 got some nice features and the movies play better over the network, which they didn´t in edgy. just when i thought i had everything setup perfectly grr, hope this new install will be the last 1.

---

### Post by GlasWolf on 2007-05-22
Do you mean 7.04 or is there a beta of 7.10 out?  Anyway, as per the first post in the thread, install in text mode then manually install the 8.36.5 drivers to get X up and running.  From that point on you should be able to just go through the tutorials in this thread to get everything working.  Well, good luck!

---

### Post by jet2230 on 2007-05-29
ops, i ment 7.04 soz.

still have not got round to reinstalling it, i seem to be using ubuntu 7.04 more n more now even tho no beryl.
  
beryl working would be a nice touch, tho it is not mandatory for me.

---

### Post by jet2230 on 2007-05-29
just out of curiosity, how would i install 7.04 CD version in command line mode as there is no command line install option on the CD version?  

can´t seem to find the DVD version of 7.04.

---

### Post by GlasWolf on 2007-05-29
I think it's the "alternate desktop CD" you get from ticking the box at the bottom of the [download page]("http://www.ubuntu.com/getubuntu/download").

---

### Post by RickSeymour on 2007-05-31
What is the current hardware status of Feisty on this laptop? 
Bluetooth
card reader
acpi


[https://wiki.ubuntu.com/LaptopTestingTeam/SamsungR20](https://wiki.ubuntu.com/LaptopTestingTeam/SamsungR20)
needs updating

---

### Post by jet2230 on 2007-06-01
Bluetooth - does not come integrated with the r20 laptop, tho a bluetooth usb dongle should work fine
card reader - works 
acpi - sleep mode does not work (not on mine anyway)

---

### Post by fodder on 2007-06-01
Sleep and hibernate work but only with the open source drivers, not the ati drivers. (I havent tested the latest drivers released yesterday but I have no reason to think they would fix the problem - this is a long standing issue ati doesnt acknowledge)
3d acceleration works only with the ati drivers and not the open source drivers.
So pick which is more important for you.

On the plus side, the sound issues seem to have been fixed in the latest kernel update, so recompiling the drivers is no longer required.

---

### Post by GlasWolf on 2007-06-01
There is an updated BIOS for the R20 available [here]("http://www.samsungpc.com/products/r20/r20_bios.htm"), which seems to have fixed the sleep problem (in my case, at least).  Hibernate still jumps straight back out again though.  I haven't tested the latest ATI drivers either, but may do so over the weekend.

---

### Post by stchman on 2007-06-01
> **Nikos.Alexandris said:**
> **1.** Download ati driver **8.34.8**

([COLOR="Red"] *** Important ***[/COLOR] **I could not run gdm with the latest driver 8.35.5!** )

*Searching in ati's official webpage I bombed in to this... release notes for driver 8.34.8:*

[COLOR="Black"]The ATI Catalyst™ Linux software suite is designed to support the following ATI Integrated products:

    * Radeon™ Xpress 1250 IGP (both AMD and Intel)
    * Radeon™ Xpress 200 series[/COLOR] 

 > Read here: [COLOR="Blue"]_[http://www2.ati.com/drivers/linux/linux_8.34.8.html](http://www2.ati.com/drivers/linux/linux_8.34.8.html)_[/COLOR]


**2.** Install edgy in text mode from edgy DVD

**3.** Boot in rescue mode

**4.** Install ati driver according to the unofficial ati linux driver wiki

[COLOR="Blue"]_[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)_[/COLOR]

**5.** Reboot and... have fun!


**[COLOR="Red"]* Problems I experienced till now:[/COLOR]**

[B]1. No 3D acceleration (!)

2. Fn+Esc forces the computer to sleep... but he never wakes up properly again !!!
[/B] - Although it worked once!!!



Also... [https://wiki.ubuntu.com/LaptopTestingTeam/SamsungR20?highlight=%28samsung%29](https://wiki.ubuntu.com/LaptopTestingTeam/SamsungR20?highlight=%28samsung%29)



Greetings,

Nikos.

Install Feisty (clean install not upgraded) as it has restricted drivers for both ATI and Nvidia.

---

### Post by Nikos.Alexandris on 2007-06-04
WOW!

...some mailing action took place here!

I was (and am) very busy so no-time unfortunately to check upon this thread.

Anyway,

the latest driver (8.37.something for ati's 1250 IGP card) crashes and works, works and crashes.

I can log-in and this message "...session lasted less than 10 seconds..." comes up. I don't know what the problem is...

---

### Post by jet2230 on 2007-06-04
i got everything reinstalled, and beryl working too.  a fresh install of ubuntu-7.04-alternate-i386 did the job (manually installed the latest ati drivers before running GDM).

all hardware working except for sleep/hibernation functions (even after samsung  bios update thru vista) 

to get beryl working i used this guide [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Beryl_.28ATI.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Beryl_.28ATI.29)  - works flawlessly with the ATI x1250 IGP.  my current working version is beryl 0.2.0*

* i encounted problems when upgrading beryl 0.2.0 to 0.2.1, thats when my beryl effects stopped working (just last night). to resolve the issue i had to remove beryl 0.2.1 and install beryl 0.2.0 again.

im glad i did a fresh install of fiesty 7.04, 

ubuntu + beryl on r20 = the best operating system i have had the pleasure of using.

---

### Post by Nikos.Alexandris on 2007-06-04
Hello Jet2230!

Could you please describe the way you installed the ati driver?

Thank you in advance!

---

### Post by Nikos.Alexandris on 2007-06-04
FYI:

fsando in another thread wrote:

 Re: Install new ati driver and update kernel (What works for me)
Quote:
Originally Posted by Nikos.Alexandris View Post
And again... it doesn't work anymore!!! I didn't really touch anything.

GDM starts but crashes and brings me back again into the login screen...

What is up?
Hi Nikos - I'm sorry I don't know. But there may be more then one issue (there often are).

One: you may need to do the module update part (see above), or the kernel you use may not be supported - as an example: I use the 'low-latency' kernel that comes with feisty - I had to do the module update to use it. I would like to use the 'real-time' kernel instead, though. So I installed it and tried to boot into it, I don't recall the exact result except that I dropped it immediately - it either gave me an unreadable screen or a very slow performance.

There have been a lot of issues with the kernels in Feisty - you may be a victim of one of those issues.

You may need to update your bios (I had to with my old laptop).

Yet another issue is with Beryl: On the beryl site they explicitly advice against the version that comes with feisty and advice you to use rc3 from their site (repositories) instead.

Lastly you may have 'fiddled with the wrong things' - it may be easier to do a complete reinstall. I had to go through a few reinstall cycles myself before my system began to 'behave'. That has actually been the same experience I have had with every new version of windows (used it since 1994) - you do quite a few cycles before you begin to know the process. Good thing is that an Ubuntu install takes about an hour, a window install takes the better part of a week (drivers and software included)

---

### Post by GlasWolf on 2007-06-04
> **Nikos.Alexandris said:**
> Hello Jet2230!

Could you please describe the way you installed the ati driver?

Thank you in advance!
I'm sure jet will confirm whether he did the same, but I used the [instructions]("http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#Method_2:_Install_the_8.35.5_Driver_Manually") you linked to in your original post.  The first time I did this, 3D acceleration wasn't available (just as you reported) but it started working after running the driver install GUI from within X.  After I did a full reinstall, everything came up ok straight away.  This was probably due to something I messed up in my original installation attempt.  This is all with Feisty, btw.

---

### Post by Nikos.Alexandris on 2007-06-04
OK, that was it... I am reinstalling and I will report in case it is successful!!!

Thanx for the reply GlasWolf.

---

### Post by Nikos.Alexandris on 2007-06-05
OK. I cannot hold it: I re-installed feisty.

I installed ati 8.37 driver the manual way.

Yet...

nik@vertical:~$ fglrxinfo 
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)

and when I log-in I always get an error screen

[ATTACH]34383[/ATTACH]

and the text is:

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "nik"
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/vertical:/tmp/.ICE-unix/5413
Fontconfig error: "~/.fonts.conf", line 1: XML declaration not well-formed
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"
exec: 3: imwheel: not found
Warning: Only changing the first 7 of 9 buttons.
Initializing gnome-mount extension
Fontconfig error: "~/.fonts.conf", line 1: XML declaration not well-formed

(gnome-power-manager:5509): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.

(update-notifier:5497): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.

What is wrong with my system?

---

### Post by GlasWolf on 2007-06-05
I've never had anything like that, but I've only used the 8.36.5 driver.  Does the ATI driver appear in the restricted drivers section?  You could try re-running the gui driver setup in Gnome as per [ATI's instructions]("https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.37.6-inst.html").

---

### Post by jet2230 on 2007-06-05
> **Nikos.Alexandris said:**
> Hello Jet2230!

Could you please describe the way you installed the ati driver?

Thank you in advance!

sorry i didnt explain this in a bit more detail, but it did give me a few problems when i initially tried installing them.  1st problem i had was running the 'aticonfig --initial' script to setup the xorg.conf file, this gave me 'xorg version not detected' error, but did give me options to override so i did as instructed (used 1 of the examples on the screen output) - and job was done to log into GDM.

also after loging into GDM i updated everything which included the latest ubtunu kernel update 2.6.20-16-generic + the restricted packages which are vital for the wireless, ati drivers etc

had to manually edit the xorg.conf to include the proper syntactic touch pad drivers (the default drivers didnt have features like side scroll)

for beryl i know there are many guides for the ATI chipset, but the 1 i used was [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Beryl_.28ATI.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Beryl_.28ATI.29) that gives 2 methods of installing beryl + also shows you how to uninstall beryl if anything goes wrong. the 2nd method for me worked, look under ' Alternate method: Using closed source FGLRX drivers from ATI ' for full description - this will installed version 0.2.0 which works with my ati chipset, i dont know why the new 0.2.1 dosn't work.

i also used ati drivers version 8.36.5, but after reading the recent posts i realize there is a newer version 8.37.6, wondering weather or not to try these new drivers

---

### Post by Nikos.Alexandris on 2007-06-07
Right stchman... finally it works.

1. Clean install of Feisty 7.04 (the default kernel and then upgrade to 2.6.20-16-generic)

2. Install the restricted drivers... (no manual ati driver install)

P.S. I forgot to mention something important... Initially I installed 7.04 64-bit vesrion... So, this is why, I suppose, I could not get the ati 8.37 work properly.

---

### Post by garyng on 2007-06-12
I need some clarification :

Is it true that if I don't need 3D, I can use the open source driver that comes with x.org 7.3, for this notebook ?

I got very confusing information after lots of google search.

thanks for any help in advance.

---

### Post by jet2230 on 2007-06-13
garyng, what do u mean if u don't need 3D?

has any1 got kismet to work with the AR5006EG ATHEROS wireless chipset on the samsung r20?

in vmware when running xp i cant get no sound, any1 got fix for this? also can not install OSX 10.5 thru vmware server, does not let me boot off the ISO file.

also will it be possible to run [Asterisk]("http://www.asterisk.org/") on this laptop, since it has modem builtin (is that all the hardware needed for a complete IP PBX system?). would like to know if any1 has tried this.

---

### Post by garyng on 2007-06-13
I mean if I don't use any apps that use 3D, do I still need to use the fglrx driver or I can just use the radeon driver in xorg 7.3 ?

I just need a standard X desktop(no compiz or xgl etc. and no gaming).

I tried the vesa driver but it seems that it doesn't like the 1280x800 resolution.

I tried the radeon driver(from xorg) but it doesn't detect the device, yet some are saying I can use that if I don't need any 3D feature.

asterisk has nothing to do with modem. It is a purely VOIP based PBX. If you need interface with the analog world, you need a service provider for that. Some geeks tried the bluetooth -> cellphone route too but that is a hackery setup for fun.

---

### Post by jet2230 on 2007-06-13
which version of ubuntu r u using? ive tried edgy & currently got 7.04 fiesty. on both i have had to manually install the ati drivers, after that i have had no problem with he screen resolutions, GDM always starts in max res which is1280x800.

if u r using fiesty then its just a matter of upgrading the kernel and enabling the restricted drivers for the ati chipset.

---

### Post by garyng on 2007-06-13
I was not referring to the fglrx driver(ati/amd one) but see if I can do it without. Someone said it is not needed for 2d based usage. But the xorg doc implies their driver won't work. That is why I need the clarification.

---

### Post by fodder on 2007-06-15
You do need an fglrx driver since the xorg ati and radeon drivers dont recognise the card. You can either use the one from the ati site or you can download the "xorg-driver-fglrx" package from the restricted repositories (this may also be on the install cd, i'm not sure). 

What determines whether you have 3d acceleration or not is whether the fglrx kernel module is loaded. I think this is provided by the "linux-restricted-modules" packages.

---

### Post by jet2230 on 2007-06-15
i had fun with this, found out how to install max os on vmware thru ubuntu fiesty using this guide:

[http://wiki.osx86project.org/wiki/index.php/Vmware_how_to#Step_2_-_Download_OS_X_10.4.5_or_10.4.6_or_10.4.7_or_10.4.8_ISO](http://wiki.osx86project.org/wiki/index.php/Vmware_how_to#Step_2_-_Download_OS_X_10.4.5_or_10.4.6_or_10.4.7_or_10.4.8_ISO)

this laptop is powerful enough to handle windows xp, mac os + beryl running at the same time - all in smooth fluid motion, ubuntu is very impressive.

[ATTACH]35460[/ATTACH]

---

### Post by jet2230 on 2007-07-11
has anyone managed to solve the sleep/hibernate problem with fiesty?

---

### Post by Nikos.Alexandris on 2007-07-11
Unfortunately not ;-(

---

### Post by GlasWolf on 2007-07-12
> **jet2230 said:**
> has anyone managed to solve the sleep/hibernate problem with fiesty?

Sleep mode works for me using [this]("http://www.samsungpc.com/products/r20/r20_bios.htm") bios, but not hibernate.  There is an even newer bios [here]("http://www.samsung.com/uk/support/productsupport/download/Model_Select.aspx?type=Computer&typecode=11&subtype=Notebook&cmssubtypecode=1102&model=NP-R20&filetype=FM&language=") which may be worth testing.

---

### Post by fodder on 2007-07-12
> **jet2230 said:**
> has anyone managed to solve the sleep/hibernate problem with fiesty?

Hibernate works for me with the latest ati drivers (8.38.6)!
Sleep seemed to give problems with the wireless, similar to the 'power up' problems described above. Have not tested this extensively though.

---

### Post by jet2230 on 2007-07-17
> **GlasWolf said:**
> Sleep mode works for me using [this]("http://www.samsungpc.com/products/r20/r20_bios.htm") bios, but not hibernate.  There is an even newer bios [here]("http://www.samsung.com/uk/support/productsupport/download/Model_Select.aspx?type=Computer&typecode=11&subtype=Notebook&cmssubtypecode=1102&model=NP-R20&filetype=FM&language=") which may be worth testing.

just tried it with latest bios update, i had to restart into windows vista  to do so (i rarely use vista now thanks to ubunty) - but sadly the sleep/hibernation problem is not fixed.

i did not want to try fodder's recommendation because ati drivers are pathetic every time I have upgraded them some big disaster happens. but I need hibernation/sleep to work properly on this laptop (the battery life is not too good). some of you guys have it working somehow. gonna try these new ati drivers ( 8.38.6) now. i really hope they dont mess anything up with my current setup everything is running so sweet atm except hibernation/sleep.

---

### Post by jet2230 on 2007-07-18
them new ati drivers don't work either, i updated from ati-driver-installer-8.37.6-x86 to ati-driver-installer-8.38.6-x86 and still no hibernation fix - laptop powers down then wakes up straight away most times, sometimes it just dies and i have to keep the power button pressed for 5 seconds to kill the system (so annoying). 

do I have to fiddle about with the xorg.conf or something? because at the end of the ati drivers update it mentioned to run the 'aticonfig --initial...'  command to make xorg.conf - i updated the drivers while i was in a graphical environment(GDM) - everything is still working fine which is a relif, i also already have a xorg.conf so why make another.

hibernation works perfect in vista, so should also be perfect in ubuntu or even better. what is stopping ati from fixing this problem in their drivers, big cooperate bullies.

---

### Post by fodder on 2007-07-21
Not sure I what I can say except that it does work for me :( 

The problem will not be in the xorg.conf, that has nothing to do with power management. It will either be in the fglrx module or the acpi configuration file. When you upgraded did you compile a new fglrx module?

The problem before the latest update was the fglrx module. If it was loaded, I had 3d acceleration but no hibernate/sleep. If it was not, hibernate sleep worked but no 3d. So you choose one over the other or you buy a new (non-ati :mad:) laptop.

---

### Post by jet2230 on 2007-08-01
finally got sleep to work (not hibernation) - problem was this in xorg.conf file:

Section "ServerFlags"
#other options can go here
Option "BlankTime" "0"
Option "StandbyTime" "0"
Option "SuspendTime" "0"
Option "OffTime" "0"
EndSection

i just made them lines look like this (basically comment out the lines):

Section "ServerFlags"
#other options can go here
#Option "BlankTime" "0"
#Option "StandbyTime" "0"
#Option "SuspendTime" "0"
#Option "OffTime" "0"
EndSection

restarted and tried sleep, worked fine - BUT sometimes the wireless connection will not come back (stays dead) to resolve this i had to restart into vista then back into ubuntu (i had to do this everytime this happened)

now i have a total solution for this sleep/wireless problem.  I installed [wicd]("http://www.linux.com/feature/118224") (instructions here [http://www.linux.com/feature/118224](http://www.linux.com/feature/118224)) - while installing wicd, apt-get automatically removed network manager (my pervious network manager which was giving problems after sleep initiated). after this my wireless stays alive even after sleep.  WPA encryption even works with wicd flawlessly, which did not in network manager (gave me a hard time anyway). so any of u guys having prob with networking i suggest you try wicd.

---

### Post by Nikos.Alexandris on 2007-10-07
Hi!

Any news about the latest ati's drivers for the 1250 model?

Gheers,

Nikos.

---

### Post by jet2230 on 2007-10-14
dunno about the latest ati drivers, but i can't wait to try 7.10 gutsy release. i really want to test it out on the r20, anyone tried 7.10 yet on r20?

---

### Post by Nikos.Alexandris on 2007-10-15
I 've installed 7.10 under VirtualBox. Seems to work smooth... But I think I will wait to do "apt-get dist-upgrade" on the real machine!

Anybody else?

---

### Post by Mitochondria on 2007-10-20
Has anybody got 7.10 to work from the live CD on samsung r20?

---

### Post by Nikos.Alexandris on 2007-10-20
It didn't work for me!

---

### Post by Loki-Master on 2007-10-21
it doesn't work for me for the moment too... 
Maybe must we wait the news ATI proprietary driver.

---

### Post by Nikos.Alexandris on 2007-10-25
I have posted in other threads that ATI's new driver (8.42.something) work for my 1250 graphic card on the Samsung R20 laptop monitor. I even have Compiz running without crashing.

Finally... !

---

### Post by Nikos.Alexandris on 2007-10-27
Are you guys still around?

Anybody interested for dual monitoring in Samsung R20?

---

### Post by Nikos.Alexandris on 2007-10-27
[https://groups.google.com/group/x1250/](https://groups.google.com/group/x1250/) for ATI 1250 owners!

---

