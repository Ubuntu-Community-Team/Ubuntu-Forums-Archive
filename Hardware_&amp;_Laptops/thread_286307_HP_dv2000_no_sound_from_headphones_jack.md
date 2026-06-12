---
title: "HP dv2000 no sound from headphones jack"
date: 2006-10-27
forum: Hardware &amp; Laptops
---

### Post by julioromano on 2006-10-27
Laptop: HP Pavillion dv2172ea
Sound Card: Intel HD Audio (Conexant chipset I think)

Sound system works without problems.

When I plug a pair of headphones in any of the 2 connectors the sound still comes out from the speakers and not from the headphones.

Of course in Windows XP the headphones jacks work properly.

Any suggestions?

Thanks
Bye
Marco

---

### Post by Paul14 on 2006-10-29
I have the same phenomenon on my Hp Pavillion DV9000. Any ideas?

---

### Post by maxdevis on 2006-10-30
same problem on my HP NC6000

---

### Post by maxdevis on 2006-10-30
i found this on this forum and it works for me:
but the front volume control doesn't work with the headphones

This is the default configuration if you are using Gnome (i.e.: Ubuntu). Here's a walkthrough:

* Go to "Application - Accessories - Alacarte Menu Editor";
* Select "Sound & Video" down the left side list;
* Check "Volume Control" in the right side pane;
* Click the "Close" button (bottom-right).

Then:

* Go to "Application - Sound & Video - Volume Control" (newly added from previous step);
* Select "Edit - Preferences" from the top menu bar;
* In the list, check "Headphone jack Sense" and "Close";

Now:

* Click on the "Switches" Tab;
* Check the "Headphone jack Sense" radio button (newly added from previous step).

There you go - you should now have a fully functional headphone jack. Unfortunately, I haven't found a way to sync the "Master" volume control of my laptop speakers with the headphone volume.

---

### Post by Paul14 on 2006-10-31
The thing is: I don't have the "Headphone jack Sense" in the prefs.

Any reason why?

Thanks

---

### Post by maxdevis on 2006-10-31
try this:

* Go to "Application - Sound & Video - Volume Control" (newly added from previous step);
* Select "Edit - Preferences" from the top menu bar;
* In the list, check "Headphone jack Sense" and "Close";
* Close program and restart the volume Control

---

### Post by Paul14 on 2006-11-03
That's my point, in the Edit - Preferences of the volume control I don't have the Headphone jack Sense. Thanks anyway :( don't know why.

---

### Post by m4dd0c on 2006-11-21
I got the same error on my dv6184ea, and no Headphone Jack Sense is present. Have this been reported as a bug?

---

### Post by trilliji on 2006-11-22
I have the same thing with an HP dv9000. I don't get a Headphone Jack Sense in the preferences either

---

### Post by Paul14 on 2006-11-24
So no one have found a solution to this problem?

---

### Post by Paulo79 on 2006-11-28
I've found many people with this problem. It seems the Intel HDA driver is still going through a lot of changes theses days. Some people reported that compiling the latest ALSA have solved their problems, but I haven't tried to do this with my dv9000.

Can anyone confirm success?

Best,

Paulo

---

### Post by Exclamation on 2006-11-28
Heres a bug report, please confirm it.
[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/66985](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/66985)

---

### Post by yebo29 on 2006-11-29
For those who still want the headphone jack sense option, try this:

in /etc/modprobe.d/alsa-base

add:

options snd-hda-intel model=z71v position_fix=1

then RESTART your machine. For some reason /etc/init.d/alsa-base restart
doesn't work.

Found this on another thread, thanks to **MHD** for this one.

---

### Post by yebo29 on 2006-11-29
OK, FYI, this didn't work for me.

But that doesn't mean it won't work for *YOU!*

---

### Post by Paulo79 on 2006-11-29
Please let us know which version of alsa each one of you have tried. Thanks!

---

### Post by Paulo79 on 2006-11-30
Ok, I finally decided to try to compile the latest alsa-drivers (only this) package for version 1.0.13. And it works now, both mic (mic jack and embeded mic) and headphones. :)

Followed this recipe found in
[http://www.ubuntuforums.org/showthread.php?t=272166&highlight=intel-hda](http://www.ubuntuforums.org/showthread.php?t=272166&highlight=intel-hda)

"How to fix:

1) You need the latest ALSA driver. Do this:

1. Get build-essential and linux-headers packages.
2. Get alsa-driver package from alsa-project.org
3. Unpack it.
4. Run "./configure --with-cards=hda-intel"
5. Run "sudo make"
6. Run "sudo make install"
7. Edit /etc/modules and add "snd-hda-intel"
8. Reboot."

It was that simple!! After that make sure your channels are not muted.

Thanks to Fraz for posting the solution...

Cheers!

Paulo

PS: I have a HP pavillion dv9000t (Intel Core 2 Duo), running Edgy (32-bit). Now I only need to get the embeded webcam and suspend/hibernate to work...

---

### Post by muximus on 2006-12-02
hey.. my problem is exactly the opposite.. i get perfect sound frm the headphones, but nothing from the onboard speakers.. dont wanna break it by compiling alsa and finding out that i have the same problem as u guys after.. i quite like my music on my speakers :)..i guess i will have to wai till the repos r updated

---

### Post by DougieFresh4U on 2006-12-02
My headphone and PCM switches work but no Master & Speaker sound (Intel) Have gone through all threads and no solution :mad: :mad: :mad: :mad:

---

### Post by yebo29 on 2007-01-04
Well, unfortunately I have tried to compile and install the newest version of alsa and I still don't have headphone capability (Darn!).
I perhaps messed it up though, because upon following the steps posted by Paulo79 (thanks for the post), I rebooted before editing /etc/modules, possibly screwing my entire install.

OOPS.

Oh well, atleast I still have sound through my speakers. I'll probably try again later...

FYI, I have a dv2000 Intel Centrino Duo.

---

### Post by MikaelHolber on 2007-02-11
I had the same problem. The latest alsa (1.0.14rc2) that was released after your post works for me. The levels in the output is a little low but it works.

---

### Post by GordSellar on 2007-03-09
> **yebo29 said:**
> For those who still want the headphone jack sense option, try this:

in /etc/modprobe.d/alsa-base

add:

options snd-hda-intel model=z71v position_fix=1

then RESTART your machine. For some reason /etc/init.d/alsa-base restart
doesn't work.

Found this on another thread, thanks to **MHD** for this one.

I did that and the expected result did not follow! Instead, the headphone jack worked as normal but all speaker output was killed!!!

Anyway, I think it's time try the new ALSA drivers...

---

### Post by nkassi on 2007-03-09
the instructions on this wiki page worked for me on a dv6000t:

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

Nic

---

### Post by mikewhatever on 2007-03-09
[https://help.ubuntu.com/community/HdaIntelSoundHowto?highlight=%28hda%29](https://help.ubuntu.com/community/HdaIntelSoundHowto?highlight=%28hda%29)

I think there is a 1.0.14rc2 available and 1.0.13 is a stable version. I hope it works for conexant chipset.
Here is another link [http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound](http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound)

---

### Post by stoopid1 on 2007-03-27
i have a dv2020 and i had to update my kenel because of problems with nvidia and the wlan drivers.  This caused my headphone and s/pdif jacks to work.  Here is where i found the instructions:
[http://ubuntuforums.org/showthread.php?t=334373](http://ubuntuforums.org/showthread.php?t=334373)

I admit, the process is a little more advanced, but ive been using linux for 5 days and ive had no problems with it. 

The only problem is that you have to manually select the output device, and the volume controls only work with the headphone output.  Im trying to find a solution for this.

---

### Post by airencracken on 2007-03-28
> **Paulo79 said:**
> Ok, I finally decided to try to compile the latest alsa-drivers (only this) package for version 1.0.13. And it works now, both mic (mic jack and embeded mic) and headphones. :)

Followed this recipe found in
[http://www.ubuntuforums.org/showthread.php?t=272166&highlight=intel-hda](http://www.ubuntuforums.org/showthread.php?t=272166&highlight=intel-hda)

"How to fix:

1) You need the latest ALSA driver. Do this:

1. Get build-essential and linux-headers packages.
2. Get alsa-driver package from alsa-project.org
3. Unpack it.
4. Run "./configure --with-cards=hda-intel"
5. Run "sudo make"
6. Run "sudo make install"
7. Edit /etc/modules and add "snd-hda-intel"
8. Reboot."

It was that simple!! After that make sure your channels are not muted.

Thanks to Fraz for posting the solution...

Cheers!

Paulo

PS: I have a HP pavillion dv9000t (Intel Core 2 Duo), running Edgy (32-bit). Now I only need to get the embeded webcam and suspend/hibernate to work...

Did this on my Toshiba l35 (thought it had the same sound card, not so sure now) and it borked my install won't boot now, fortunately the older kernel works. How should I go about fixing the other kernel?

---

### Post by ttolstead on 2007-04-03
I have also had this problem with my HP m7750n, in searching about I found out that my headphone jack had been turned off by default!

To fix this I opened a terminal and entered:

"alsamixer"

Which brings up a text based set of volume controls.   Across the bottom of the display there are several different words representing various devices.  You can move through the list using the left and right arrow keys.  Going all the way to the left highlights the word "HeadPhon".  Above this there is a box that will have either "MM" or "00".  "00" indicates the headphone jack is active, "MM" means it is muted.  The state of the box can be changed by typing M on the keyboard.  (Presumably for mute.)

This is what I found, and it fixed my problem with this.... :)  tat

---

### Post by eggdeng on 2007-04-03
Some HP laptops with Intel HDA audio require you to add the line
```
options snd-hda-intel model=hp
``` to /etc/modprobe.d/alsa-base. Reboot for changes to take effect.

---

### Post by lexarrow on 2007-05-26
maybe [this]("http://ubuntuforums.org/showthread.php?t=455147") can help

---

### Post by smurphy_it on 2007-09-18
**[SIZE="4"]May be possible to do all of this in X-Windows, but I usually do it this way so I know it works right every time the first time).[/SIZE]**

I have a HP DV2020 and always have that sound issue until I do a recompile.  My sound card is a nVidia MCP51 High Definition Audio [10de:026c] (rev a2).  It works a  little weird, but good enough for my liking.

Download the alsa-drivers package from the alsa website ([http://www.alsa-project.org/main/index.php/Main_Page](http://www.alsa-project.org/main/index.php/Main_Page)) and click the link on the right hand side to download the alsa-driver-1.014 package.  Extract it's contents to a folder.

Using a package manager download rcconf and g++
In a command line type "sudo rcconf" (uncheck kdm/gdm so x-windows don't load on bootup).
REBOOT

Login (X-windows shouldn't be running, that's fine)
type the following:
cd /etc/init.d
sudo ./alsa-utils stop

Next change into the folder you downloaded your alsa-driver package too (after extracting it's contents).
Then type the following:
./configure --with-cards=hda-intel
make
sudo make install

That should reconfigure your sound / headphones properly.
Next just type sudo rcconf and check kdm/gdm again so that it loads X-windows on bootup.
Reboot comptuer. (sudo shutdown -r now)

To make headphones work, plug them in (sound emits on both headphones and speakers) then mute sound, and unmute it... Sound will only emit from headphones then.  (If you boot lappy with headphones plugged in, I believe it will work without having to mute and unmute the sound).

Might be a little wonky, but it works.  Don't know if that affects microphone, as I don't use one.

---

### Post by humpmasterH on 2007-09-23
Hey, I had the same problem, I just installed the latest dev version of ALSA from their website, and it all worked.

I believe the version number for alsa-driver is 1.0.15rc2

---

