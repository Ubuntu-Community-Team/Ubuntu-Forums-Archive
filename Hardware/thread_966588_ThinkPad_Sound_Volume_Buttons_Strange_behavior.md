---
title: "ThinkPad Sound Volume Buttons: Strange behavior"
date: 2008-11-01
forum: Hardware
---

### Post by AnythingBut on 2008-11-01
There's a problem the way Ubuntu handles the sound volume buttons on ThinkPads.  This has been a problem in past releases and, sadly, still is a problem in Intrepid.  You can read an old thread about it here: [http://ubuntuforums.org/showthread.php?t=496180](http://ubuntuforums.org/showthread.php?t=496180) (I would have posted in that thread if it wasn't archived read-only).

Anyway, the problem is that the volume buttons change both a software sound volume (mixer) as well as the "hardware" volume in the ThinkPad.  This leads to annoying and confusing situations where the OSD reports a volume which doesn't correspond well to what comes out of the speakers.  It can be as far as the hardware being muted, while the OSD reports full volume.   I wrote a little patch of the gnome-settings-daemon packages to fix the problem.

To see if this problem (and my fix) applies to you, type in a terminal 

```
cat /proc/acpi/ibm/volume
```

This file reports the "hardware" volume.  If the volume reported each time you type the above changes as you push the volume buttons, then my patch should work.  If the file doesn't exist or if it doesn't change, then don't install my package.

You can install my package by adding

```
deb http://ppa.launchpad.net/4lorne/ubuntu intrepid main
```

as an apt source.  You can do this any number of ways, for example the Third-Party Software tab of System->Administration->Software Sources.  After adding the source, you should be asked to update your gnome-settings-daemon package.  After logging out and back in, pushing the buttons will report the hardware volume while not changing any software volume (I hope.  I've only tested it on my T60.  Let me know if it works for you.)

Here's some more info about the problem:
-The real solution is for an ALSA mixer driver to be written for the hardware volume.  This has been in the TODO list of the thinkpad-acpi kernel module maintainer for a long time.  My fix is just a stop-gap solution, but there doesn't seem to be much movement on this ALSA mixer.
-The Launchpad bug can be found here: [https://bugs.launchpad.net/ubuntu/+source/acpid/+bug/51537](https://bugs.launchpad.net/ubuntu/+source/acpid/+bug/51537)
-I submitted my patch to gnome but, after initially being accepted, it was taken out because the real solution is the ALSA mixer thing.  You can read about this here: [http://bugzilla.gnome.org/show_bug.cgi?id=524425](http://bugzilla.gnome.org/show_bug.cgi?id=524425)

Let me know if it works for you and if you find it useful.

Cheers.

---

### Post by djwheels on 2008-11-01
This worked for me on a Thinkpad X31.  I believe I also used your patch to fix this issue in Hardy Heron.

---

### Post by Whoopie on 2008-11-02
Hi,

thanks for your work. I always searched something like this.

Would it be possible to change the software mixer according to the hardware mixer state so that they are in sync?

Best regards,
Whoopie

---

### Post by AnythingBut on 2008-11-02
Hi Whoopie,

> **Whoopie said:**
> 
Would it be possible to change the software mixer according to the hardware mixer state so that they are in sync?


I suppose it's possible, but I don't think it would be ideal.  Technical issues aside (eg., the HW mixer has only 15 levels while the software has many more), changing them both in sync would make for really rapid volume changes since the two volume levels multiply together (so you'd get Volume^2).

I like keeping the software volume fixed most of the time and use the HW buttons to change the sound level.  That's my preference.

Cheers

---

### Post by iosonofabio on 2008-11-08
Hi!
I'm using a T60 on ArchLinux (i.e. not ubuntu!) with Gnome. I just installed this distribution a week ago. Before that I used ubuntu (intrepid too) and I noticed the problem of "too drastic volume change" in Gnome.

Now things are quite different. The volume buttons do work, i.e. they actually change the volume level, but the Gnome-OSD does not appear. I checked with xev, the volume buttons do not cause any xev-relevant event at all.

Many Arch users prefer installing tpb utility because it is desktop-manager-independent.

I looked at your patch quite closely, but since I am no advanced programmer it is not easy for me to write a similar one for myself. I'm not asking you to write one either.

Could you explain me how it could be possible to write a patch similar to yours?

Thanks, cheers

---

### Post by AnythingBut on 2008-11-08
Hey iosonofabio,

> **iosonofabio said:**
> 
I checked with xev, the volume buttons do not cause any xev-relevant event at all.

You need to get this fixed before any patch resembling mine will work.  My patch depends on X/Gnome to report volume button presses.  I'm not sure exactly how to fix this problem since I've never had this issue myself.

This the lack of x-events doesn't effect tpb because, if I recall correctly, tpb polls the hardware directly and constantly (which is one of the reasons I don't like to use it).

> **iosonofabio said:**
> 
Could you explain me how it could be possible to write a patch similar to yours?

Sure.  The general scheme of things is that my patch provides Gnome hooks that get called when the buttons set in gnome-keybinding-properties get pushed.  The hooks respond with the the hardware volume which is simply read from /proc/acpi/ibm/volme (it's a bit hacky).  Feel free to private message me about details.

---

### Post by oofnik on 2008-12-03
Works perfectly in Hardy, just replaced 'intrepid' with 'hardy' in the apt line. Thank you!!

---

### Post by rafe101 on 2009-01-07
Yeah, I just used the patch with Hardy.  Everything works perfectly now.  Thanks.

---

### Post by xepe on 2009-01-11
Thanks!!!

your patch has worked for my t41 in every ubuntu I'd had.

---

### Post by gudmund84 on 2009-01-20
Hello

I added the source, but it does not work. It worked under hardy, but not on intrepid.

cat /proc/acpi/ibm/volume shows the volume and the hardware buttons works fine and set to volume up/down/mute under gnome keyboard shortcuts. They do not change the software volume any more, but the OSD is not showing.

Any idea why I do not get the OSD?

---

### Post by AnythingBut on 2009-01-20
> **gudmund84 said:**
> Hello
Any idea why I do not get the OSD?

Double check you have the right package installed:
"aptitude show gnome-setting-daemon" should tell you version 2.24.0-0ubuntu4-4lorne3

Are your volume buttons producing ACPI events?
run "acpi_listen" in the terminal and make sure your buttons show up when you push them.

Are your ACPI events being handled?
Look in /etc/acpi/events for thinkpad-[volume-up,volume-down,mute] and check inside that they're mapped to the events you see in acpi_listen.  They should also have an action associated with each.

---

### Post by gudmund84 on 2009-01-21
Thanks for the answer.

The version is 2.24.0-0ubuntu4~4lorne3, but the buttons is not producing ACPI events.

I tried to re-bind the keys under keyboard shortcuts, but nothing happens. So it looks like Ubuntu does not have the keys installed. That might be why it does not produce ACPI events.

/etc/acpi/events$ cat thinkpad-volume-up 
# Volume Up
event=ibm/hotkey HKEY 00000080 00001015
action=/etc/acpi/volupbtn.sh
/etc/acpi/events$ cat thinkpad-volume-down 
# Volume Down
event=ibm/hotkey HKEY 00000080 00001016
action=/etc/acpi/voldownbtn.sh
/etc/acpi/events$ cat thinkpad-mute 
# Volume Always Mute
event=ibm/hotkey HKEY 00000080 00001017
action=/etc/acpi/always-mute.sh

Can it be that the keys are not recognized in Ubuntu/Gnome?

---

### Post by AnythingBut on 2009-01-21
> **gudmund84 said:**
> 
Can it be that the keys are not recognized in Ubuntu/Gnome?

The lack of ACPI events is what the problem is.  The ACPI events in turn generate the key presses (you can trace the path of the scripts in /etc/acpi to a acpi_fakekey call).

I think its the thinkpad_acpi kernel module that produces the ACPI events, which you obviously have installed since you can check /proc/acpi/ibm/*

Do you have a funky kernel installed or a really new thinkpad that isn't supported yet by the module?  Is /usr/sbin/acpid running?  Does your laptop produce any other ACPI events (other buttons, Lid, etc.)?

You can private message me instead of posting on the thread since it seems the problem is pretty unrelated to the thread topic, for the most part.

---

### Post by robber on 2009-06-24
OP, would you please update your patch for Jaunty Jackalope also?

---

### Post by AnythingBut on 2009-06-24
> **robber said:**
> OP, would you please update your patch for Jaunty Jackalope also?

Hi robber,

I'm glad I'm not the only one still bothered by this problem.  I haven't repatched gnome-settings-daemon for jaunty, but I have a patched kernel that provides an ALSA mixer for the hardware speakers.  You can find it in one of my PPAs.

```

deb http://ppa.launchpad.net/4lorne/thinkpadvol/ubuntu jaunty main 

```

It's not up to speed with the most recent Jaunty kernel at the moment, but I'll try to update it so soon.  It will still work fine though.  It's just an older Jaunty kernel.

Once you have the kernel installed and are booting with it, in System->Sound->Devices(tab) change the Default Mixer Track to Device: Speaker with the Playback mixer.  Then, if all goes well you should be set.

Some notes:
- The warning to not install this still holds if you don't have a laptop with this problem.  Don't install this patch unless you read my first post.  There is no code in the kernel to distinguish laptops with HW mixers from those that don't.
- The ALSA mixer has been made read only by default.  You can move all sorts of sliders around in volume control stuff, but it wont do squat.  These are bugs in the UI.  (Of course, the hardware buttons will always work.)  If you really want, you can make the mixer read-write with the module option alsavol_writable=1.  Though, funky things might happen since gnome-settings-daemon likes to try to change things.

Please let me know if it works and what you think.

---

### Post by robber on 2009-06-24
Thanks for the help AnythingBut. So I put the line in my source.list and get the pub key, then apt-get update. Now what do I do? Which package should I update and should I add something to grub? Sorry I'm not good at this (yet).

---

### Post by AnythingBut on 2009-06-24
> **robber said:**
> Thanks for the help AnythingBut. So I put the line in my source.list and get the pub key, then apt-get update. Now what do I do? Which package should I update and should I add something to grub? Sorry I'm not good at this (yet).

Hey robber,

That PPA now has an up-to-date version of the kernel that should replace the default Jaunty kernel (as long as you haven't done something funky with your system). ```
 sudo aptitude update && sudo aptitude safe-upgrade
``` should take care of it.  You can double check it's installed with ```
sudo aptitude show linux-image-2.6.28-13-generic
``` which should report version 2.6.28-13.45~lorne1.  All the grub stuff should be taken care of by the installer.

I hope that helps.

---

### Post by roy.nico on 2009-09-22
> **AnythingBut said:**
> Double check you have the right package installed:
"aptitude show gnome-setting-daemon" should tell you version 2.24.0-0ubuntu4-4lorne3

Are your volume buttons producing ACPI events?
run "acpi_listen" in the terminal and make sure your buttons show up when you push them.

Are your ACPI events being handled?
Look in /etc/acpi/events for thinkpad-[volume-up,volume-down,mute] and check inside that they're mapped to the events you see in acpi_listen.  They should also have an action associated with each.

Hello, 
I would be intersted by some solutions of your problems, which look similar to mine :
* I have a X61 Tablet, with jaunty 
* my volume/mute buttons do NOT produce acpi events, but other button do (esc, enter button on the tablet, or brightness...)
* in /etc/acpi/events i have no thinkpad-[volume-up,volume-down,mute]

On the other hand, i can make the button "work", by creating a keyboard shortcut in System/preferences/shortcuts :

Volume mute : XF86AudioMute
and so on...

But strangely enough, it doesn't act on the global volume, but on the Microphone volume/mute !!

Any idea ? 

Thanks, 

nicolas

---

### Post by AnythingBut on 2009-09-24
Hey nicolas,

I'm not sure what you mean by this:

> **roy.nico said:**
> 
But strangely enough, it doesn't act on the global volume, but on the Microphone volume/mute !!

Does the X61 have a full hardware mixer (does /proc/acpi/ibm/volume report changing volume levels)?  I know some ThinkPads only have Mute in hardware while volume is done completely in software.

As an aside, the PPA with my fix is a little out of date right now so it probably wont help.  I'll update it soon if it'd be handy for anyone.

---

### Post by roy.nico on 2009-09-25
Hej AnythingBut,


> **AnythingBut said:**
> 
I'm not sure what you mean by this:

I mean the following. If i press the "Mute" button, it does not mute the global sound, but it does mute the microphone. If i press the "Volume +" button, it increases the volume of the microphne, etc...

> **AnythingBut said:**
> 
Does the X61 have a full hardware mixer (does /proc/acpi/ibm/volume report changing volume levels)?

I have :
```

$$ more /proc/acpi/ibm/volume 

level:		7
mute:		off
commands:	up, down, mute
commands:	level <level> (<level> is 0-15)

```
And this file is neither modified by pressing the volume/mute buttons, nor by modifing the volume level in Gnome "volume Controler".

Thanks if you have any idea...

nicolas

---

### Post by AnythingBut on 2009-09-27
> **roy.nico said:**
> 
And this file is neither modified by pressing the volume/mute buttons, nor by modifing the volume level in Gnome "volume Controler".


I don't think your problem applies to this thread... but you might want to check you settings in the Sound Preferences.  Check which default mixer is selected.

---

### Post by egruber on 2009-10-29
I have a T40 and I just installed 9.10.  I've had Ubuntu for a few years now and the volume buttons on the laptop used to bring up a speaker graphic and a bar that moved left and right as I adjusted the volume.  Starting with one of the upgrades (maybe 9.04, I'm not sure), the graphic disappeared and button pushes do not change the volume on the bar at the top of the screen.  I still have sound, though. I'm not really familiar with terminal commands, but I can follow simple instructions. 

I did do the Hardware Test in the first post and the numbers did change as I hit the volume buttons. I added the Intrepid package to my Other Software, logged out and in, but it did not work so I removed it.  Probably because I am on 9.10 Any suggestions?  Thanks!

---

### Post by un234567 on 2010-02-24
Well, i have the same problem too. The volume OSD does not show up, and the volume keys do not work with xev. I checked /etc/acpi/events and i dont have anything like volume up, volume down or mute. But, the keys were controlling the volume in /proc/acpi/ibm/volume

level:		7
mute:		off
commands:	up, down, mute
commands:	level <level> (<level> is 0-15)

I appreciate any help

---

### Post by AnythingBut on 2010-02-24
> **un234567 said:**
> Well, i have the same problem too. The volume OSD does not show up, and the volume keys do not work with xev. I checked /etc/acpi/events and i dont have anything like volume up, volume down or mute. But, the keys were controlling the volume in /proc/acpi/ibm/volume


Sorry, I don't have any good solution for Karmic.  You should keep an eye on this [launchpad bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/357673").  There are some proposed solutions there, but nothing seems ready.

---

### Post by un234567 on 2010-02-26
sorry for double posting, delete this plz.

---

### Post by un234567 on 2010-02-26
Thanks for replying but I am using "jaunty" not karmic, it is written in my profile. Also, the OSD used to work before an upgrade from intrepid to jaunty. I have a Thinkpad Z61m laptop and I am running the OSS driver. Therefore I dont think this patch works for me. I am just trying to define the problem in order to search for a suitable solution as I am still a linux noob.

Note: I downgraded xserver to 1.52 and I downgraded gnome session + gnome power manager to 2.24 because I have an ATI x1400 card and I wanted to run the ATI proprietary driver. I donno if the downgrade is responsible for the problem.

---

