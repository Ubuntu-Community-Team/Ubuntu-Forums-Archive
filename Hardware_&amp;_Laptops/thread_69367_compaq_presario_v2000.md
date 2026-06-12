---
title: "compaq presario v2000"
date: 2005-09-26
forum: Hardware &amp; Laptops
---

### Post by Coffeegeek on 2005-09-26
I have a spanking new compaq presario v2000 and for some reason, hoary refuses to run.  i tried the hoary liveCD and i tried installing kubuntu 5.10.  both give me the same error - loading up perfectly until i log in, then crashing before displaying the desktop.

mepis loaded fine, and it uses xfree86, so it might be a xorg driver issue [my guess]

any suggestions?  i'm at my wits end, and theres no way i'm putting XP back on.

---

### Post by beck24 on 2005-09-26
I'm having the exact same problem with 5.04, and 5.10, ubuntu and kubuntu on a compaq presario V2305CA

All the specs are here:
[http://h10025.www1.hp.com/ewfrf/wc/document?dlc=en&lc=en&product=503485&#9001;=en&cc=us&docname=c00392760]("http://h10025.www1.hp.com/ewfrf/wc/document?dlc=en&lc=en&product=503485&lang=en&cc=us&docname=c00392760")

It installs fine, then at the login screen it freezes the second you try to login.  It's unresponsive to anything and I have to pull the power to restart.  I'm using a dual boot with winXP (needed for my minidisk) but I would like to be using ubuntu for most applications.

Please help, I have a feeling the same fix will work for both laptop models.
Thanx.

---

### Post by Coffeegeek on 2005-09-26
I share your frustration, beck24.

what did you try?
i thought it might have been the video driver so i tweaked that a little [tried changing it to other things] i guessed that the login screen and the main system used different resolutions.  no luck there.

thats about where i gave up. i can't find a good reason for it to be crashing.

---

### Post by beck24 on 2005-09-26
Well I haven't really tried anything yet.  I'm a pseudo-n00b to linux, I've been running SUSE on my desktop for almost a year now but it never had any problems that couldn't be taken care of graphically through the YAST package manager.  I used the command line to launch programs and install a few things that YAST wouldn't, but other than that I don't know enough to begin changing configurations.
I started with SUSE on the laptop but it wouldn't give me the right resolution (1280x768), so I downloaded the ATI drivers for the videocard and it seemed to work, but next time I restarted the xserver was broken.
I have a friend who's a comp-sci researcher at the university and he told me to try ubuntu, after reading about it I want it, but it just won't cooperate.  If noone can help me sooner I know he's coming over on Friday and I'll get him to take a look at it, he's pretty linux literate.
Hopefully someone here can help us out sooner.  Until then I'm stuck with winXP, which isn't horrible, just not my preference.

---

### Post by Coffeegeek on 2005-09-27
the windows XP that came preinstalled with my laptop was unbearably slow.  i felt like i was back on the old 666mhz compuer.

if your friend fixes you up before we get help here, could you post what he did?

ubuntu has been nothing but a delight for me on my desktop. its fast, fun, easy to use.  and generally, you get support :-D

the big thing that improves it over SUSE in my opinion is the package management - no more spending hours playing with RPMS and screwing up your system by intalling the wrong one.

---

### Post by pongster on 2005-09-27
Hi! Noob here, but have been doing some tinkering with my Compaq V2013.  5.10 Breezy Preview installs fine... detects my hardware properly except the following:
1. Driver support for the Texas Instruments 6-in-1 Card Reader
2. Haven't tried out the Firewire and S-Video
3. USB works without a hitch
4. WiFi works perfectly (it detects my intel 2200 PRO Wireless Card)
5. Am still finding a way to get my Intel AC97 Modem to work (looking for the right linux-headers as the ones that come out from my googling all need a lower version kernel than what 5.10 installs)
6. Video Card resolution is detected properly (limited to 1024x768 and 1280x768... not complaining)

Maybe (just maybe) try reinstalling 5.10 cleanly (separate/dedicated partition for it)

During the boot process, it stops and indicates a bad format in line 12 of my /etc/fstab.... then takes about 20 seconds before giving me my login screen!  

I also can't dual boot into XP!  when i try, it says my hal.dll is corrupt!  after some googling, the problem is the bootloader or MBR (me thinks) so I run XP in recovery mode (insert the installation CD and press R) and use FIXBOOT to get me back into XP. and I'm back to Windows!  But the hitch is it destroys my /home directory in Ubuntu and I can't enter Ubuntu (in all modes, recovery, failsafe, etc.) so I decide to repair my Ubuntu (since i'm loving my new Linux!) and the XP hal.dll is back!  Any suggestions to overcome the following:
1. the bad format in line 12 of /etc/fstab
2. dual booting into XP (although, since i'm completely dumping XP this weekend, i just need to know how to solve the problem, in case I need to bring XP back... which is a longshot but what the heck right?)

---

### Post by beck24 on 2005-09-27
[FONT=verdana, arial, helvetica][SIZE=2]Good news, I'm posting this from Ubuntu Breezy right now!!

I saw my comp-sci friend today and he fixed it in seconds, here's what to do:

*****************************************************************
1. Boot into recovery mode.  It will get you to a command line.

2. Type: sudo nano /etc/X11/xorg.conf

3. Find the section titled: Section "Device"

4. As the last entry under "Device" add the line: Option     "NoAccel"

5. Ctrl-O to save

6. Ctrl-X to exit

7. Reboot in normal mode

8. Rejoice that your mouse will work and Gnome will load and that once again, everything is good in the world!
******************************************************************

I hope this works for you too Coffeegeek[/SIZE][/FONT]

---

### Post by Coffeegeek on 2005-09-28
Beck24 - you rock, man!

 loaded up perfectly. =)
i see you connected to the internet though.  none of my network drivers seem to have been detected [not wireless, nor wired]

i think ndiswrapper is supposed to fix it *scratches head*

anyway, thanks so much =) :-) :-) :-)

---

### Post by beck24 on 2005-09-28
Don't thank me, I didn't do it.  All I did was post the solution  :D

It automatically detected my network devices, but not wireless, my big problem now is multimedia...

every time I try to play an audio or video file using xmms, mplayer, or whatever the default player is, it restarts the xserver and makes me login again.
Oh well, one problem at a time right?
This is the first distro that automagically set the right resolution at 1280x768.

Anyway, glad I could help Coffeegeek!

---

### Post by Coffeegeek on 2005-10-01
You deserve the thanks.  you didn't have to help me out by posting the answer :-)

the multimedia thing is really strange.  is that all multimedia, or just one movie?

if its just one, it could be a codec issue.

---

### Post by JuanC on 2005-10-01
Thanks!.

It works for me also.

This would be fixed in the Breezy Badger Final version?

---

### Post by Coffeegeek on 2005-10-02
JuanC -

  I tried the latest beta and it had the same problem still.
i don't know how to bring it to the attention to the developers.

---

### Post by JuanC on 2005-10-02
[QUOTE=Coffeegeek]JuanC -
I tried the latest beta and it had the same problem still.
i don't know how to bring it to the attention to the developers.[/QUOTE]

I think posting this thread in [Breezy Badger Development Release](http://ubuntuforums.org/forumdisplay.php?f=70) would bring attention to developers.

This is anoying bug , because it seems that Ubuntu/Kubuntu don't work in this laptop.

I hope it would be fixed in Final version of Breezy Badger.

---

### Post by vtec on 2005-10-02
Does anyone know if any driver are around, or are being worked on for the media reader???

---

### Post by Coffeegeek on 2005-10-03
media reader?  -puzzled-
whats your issue?

soooo tired

---

### Post by JuanC on 2005-10-03
[QUOTE=Coffeegeek]media reader?[/QUOTE]

media reader , i think it is the 6in1 card media reader , that also don't work.

In my case , the volume buttons (+ , - , mute) also don't work.

---

### Post by vtec on 2005-10-03
[QUOTE=JuanC]media reader , i think it is the 6in1 card media reader , that also don't work.
In my case , the volume buttons (+ , - , mute) also don't work.[/QUOTE]


Yup that is the one. That is the only thing i have found not to work so far.

---

### Post by Coffeegeek on 2005-10-03
I don't see a media reader in mine.. must be an extra, or very well hidden.

about the volume keys - i didn't play around with it yet [the network thing is bumming me out too much]

i googled this up though:

--> Easy Access Keys 
If you're running GNOME, you can use acme to activate many of the special function keys (the FN-F? keys) and the volume control buttons. The upside is it's pretty easy to configure; the downsides are (1) it's apparently not in GNOME 6.2, instead being merged into the Keyboard Shortcuts control panel, and (2) it doesn't let you associate your own actions with the keys. This isn't a big deal for the volume keys (they work nicely), but for things like the Sleep key it is (acme hard codes this to execute either apm or xset dpms force off). Since I'm using ACPI this doesn't do much. My solution was to add my own apm program, which is simply a script which runs the hibernate script for suspend-to-disk. It's a kludge, but it works.

If you want to be able to program your own actions, there is a package called LinEAK which adds support for Internet keyboards and other cute buttons. It mentions running xev to catch events from special keys. Just to see what it did, I installed it and its default plug-ins, then added keycode definitions for the various hotkeys. The default plug-ins have three macros (EAK_MUTE, EAK_VOLDOWN and EAK_VOLUP) which control /dev/sound/mixer. Like acme, LinEAK uses X11 events so it will only work when you're running X11 (i.e., you can't start the daemon until the X11 server is already running).

tell me if you had any success with this or other methods.

---

### Post by vtec on 2005-10-04
Are you talking about the keys that share a spot with the F1 F2.... ect keys? I have a few of mine set with the tool that comes with gnome. I have one to lock the screen and one to put it to sleep. My volumn keys worked at install i think.

---

### Post by JuanC on 2005-10-04
Not the F1 F2 ... , i mean the volume buttons , that are separate of the keyboard , i have 3 buttons for the volume , + volume , - volume and mute.

---

### Post by vtec on 2005-10-04
[QUOTE=JuanC]Not the F1 F2 ... , i mean the volume buttons , that are separate of the keyboard , i have 3 buttons for the volume , + volume , - volume and mute.[/QUOTE]


Yeah i have them working on mine. I can't remeber if they worked after the install or if i configured them with some tool in gnome. When i get home tonite i'll take a look at there configuration.

---

### Post by JuanC on 2005-10-09
I try Breezy Release Candidate :
[http://www.kubuntu.org/announcements/breezy-release-candidate.php](http://www.kubuntu.org/announcements/breezy-release-candidate.php)

And i get the annoying error that KDE no starts , is there any member of the develop team that read this thread?

Is there any way to inform the develop team about this bug?

---

### Post by woodb on 2005-10-15
Does suspending work at all for you guys?  The breezy live cd I am using doesn't suspend properly (just like hoary) - it suspends, but immediately reboots on resume.

swsusp2 works in fedora, but I didn't have great luck with swsusp2 in hoary

---

### Post by mjukr on 2005-10-17
For all those with Presario v2000s, I've added my model to the LaptopTesting wiki:

[https://wiki.ubuntu.com/LaptopTestingTeam/CompaqPresarioV2000](https://wiki.ubuntu.com/LaptopTestingTeam/CompaqPresarioV2000)

Note that this is the Celeron model w/ Broadcom wireless. I'm pleased to report that everything works well in Hoary--even SLEEP! I can even use the Fn+F5 sleep key to activate it, or simply close the lid. The only thing that required extra work outside the default install was to configure ndiswrapper for wireless, since Broadcom chipsets are not well supported under Linux. I did have to uncomment the sleep line in /etc/acpi-support, but that was pretty trivial.

The volume up/down/mute function keys also work fine without any tweaking. Hopefully this is helpful for anyone considering a purchase! I'll fill in more of the details as I have time.

If you have any questions about my model's configuration, let me know and maybe I can assist if you're having issues with Breezy.

---

### Post by woodb on 2005-10-17
I took the plunge and installed Breezy this weekend..  pretty much everything worked out of the box on my laptop (2335 Intel wireless model).  Here is what does work (which did't in Hoary):

1)  Video Card:  In Hoary it detected a vesa card, with Breezy it uses the proper i810 card.  In fedora I had to use DRI snapshot drivers for it to work, it is excellent to see this work out of the box.
2)  Wireless card:  worked perfect out of the box (didn't even have to DL firmware or kernel modules).  Excellent! :)
3)  Volume buttons (!!!):  mute/up/down all work
4)  Suspend (to memory):  Didn't seem to work by default, I added "echo mem > /sys/power/state" to the /etc/acpi/lid.sh script and it seemed to work - however my  fourth consecutive suspend failed.  I am going to have to test and tweak this a little.   Also, the wireless button is not lit on resume, but the card appears to work fine.  

I have not played with suspend to disk yet, I am guessing I need to add something like "resume:/dev/hda" or something to my grub.conf?

Great progress on Breezy.  I am loving it so far.

---

### Post by mjukr on 2005-10-18
[QUOTE=woodb]
I have not played with suspend to disk yet, I am guessing I need to add something like "resume:/dev/hda" or something to my grub.conf?[/QUOTE]

Well, in my case I didn't have to modify anything for suspend-to-disk to work. It was suspend-to-RAM that I had to tweak. If you choose System->Logout->Hibernate, it will hopefully just work. 

Maybe I was just lucky :razz:

---

### Post by neko18 on 2005-12-29
[SIZE="1"]-Moderator, please delete this message. Sorry.-[/SIZE]

---

