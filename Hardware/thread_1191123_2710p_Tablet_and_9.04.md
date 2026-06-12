---
title: "2710p Tablet and 9.04"
date: 2009-06-18
forum: Hardware
---

### Post by zoomy942 on 2009-06-18
First off, I have used ubuntu alot from series 7, through 8 and into 9.04.  I havent used it in a while though, and when i was using 8.10, there was a lot of manual setup for my tablet to get things working.  I got really good at it but havent used ubuntu in a few months.  

fast forward to today, and i have installed 9.04 and much to my surprise my vzw embedded card works as does my stylus.  i can click on the screen and it functions correctly.  Now, with 8.10, i used to have a custom script for the stylus right click to work, and all i am seeing now is this is configured through a HAL of some kind and with wacomcpl.  I'm not sure what the HAL is or how to set it up, and when i type wacomcpl in the terminal, i get the popup but nothing is listed, even though my pen works.  I think it's odd, but this 9.04 is a different animal than 8.10 on a tablet PC.  

so im just curious how to get my stylus right click working.  Also, if there are links for getting hibernate to work or standby to function when i close the lid (right now it does nothing) that would be cool too. 

It's amazing becasue with 9.04, i only have 2 things to do so all my functions work.  in 8.10, it was about 15 things.  Good job developers.

---

### Post by zoomy942 on 2009-06-18
As a side note, the stylus, when i am holding down the button, and click in Firefox for example, opens in a new tab.  So that tells me it's seeing the button, it just isnt mapped right.  but that doesnt change the no wacomcpl items listed in that popup menu.

---

### Post by zoomy942 on 2009-06-18
by the way, i missed ubuntu :)

---

### Post by Favux on 2009-06-18
Hi zoomy942,

If you go read Jaunty Users near the top here:  [http://ubuntuforums.org/showthread.php?t=1038949](http://ubuntuforums.org/showthread.php?t=1038949)  It should explain things to you.  Then follow the link in 1) to take you to gali98's Jaunty HOW TO.

---

### Post by zoomy942 on 2009-06-18
i notice in the gali howto, it says that if i have a serial tablet, this wont work.  Mine is a serial tablet.

---

### Post by Favux on 2009-06-18
Hi zoomy942,

My apologies, I thought you had a TX2500.  To see why wacomcpl doesn't work in a terminal enter:

xsetwacom list

It will be blank from what you're describing, then try:

xinput --list

Which will show you the names HAL is returning.  See Jaunty Users 3 or 3a.

---

### Post by zoomy942 on 2009-06-18
no sweat.  i didnt specify.  :)

here is what i got

```
zimmerman@zimmerman-laptop:~$ xsetwacom list
zimmerman@zimmerman-laptop:~$ xinput --list
"Virtual core pointer"	id=0	[XPointer]
	Num_buttons is 32
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 0
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 0
"Virtual core keyboard"	id=1	[XKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"AT Translated Set 2 keyboard"	id=2	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Wacom Serial Tablet PC Pen Tablet/Digitizer"	id=3	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
	Num_buttons is 32
	Num_axes is 6
	Mode is Absolute
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is 26312
		Resolution is 2540
	Axis 1 :
		Min_value is 0
		Max_value is 16520
		Resolution is 2540
	Axis 2 :
		Min_value is 0
		Max_value is 255
		Resolution is 1
	Axis 3 :
		Min_value is -64
		Max_value is 63
		Resolution is 1
	Axis 4 :
		Min_value is -64
		Max_value is 63
		Resolution is 1
	Axis 5 :
		Min_value is 0
		Max_value is 1023
		Resolution is 1
"Wacom Serial Tablet PC Pen Tablet/Digitizer eraser"	id=4	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
	Num_buttons is 32
	Num_axes is 6
	Mode is Absolute
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is 26312
		Resolution is 2540
	Axis 1 :
		Min_value is 0
		Max_value is 16520
		Resolution is 2540
	Axis 2 :
		Min_value is 0
		Max_value is 255
		Resolution is 1
	Axis 3 :
		Min_value is -64
		Max_value is 63
		Resolution is 1
	Axis 4 :
		Min_value is -64
		Max_value is 63
		Resolution is 1
	Axis 5 :
		Min_value is 0
		Max_value is 1023
		Resolution is 1
"Video Bus"	id=5	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Macintosh mouse button emulation"	id=6	[XExtensionPointer]
	Num_buttons is 32
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
"PS/2 Generic Mouse"	id=7	[XExtensionPointer]
	Num_buttons is 32
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
zimmerman@zimmerman-laptop:~$ 

```

---

### Post by Favux on 2009-06-19
Hi zoomy942,

OK, so:

stylus = "Wacom Serial Tablet PC Pen Tablet/Digitizer"
eraser = "Wacom Serial Tablet PC Pen Tablet/Digitizer eraser"

So you can substitute the new names in your rotation script and your old .xinitrc.  By renaming the stylus and eraser in the .xinitrc wacomcpl should work.  Or you could try rec's script and see if it works for you.  It should.  Then use Section 3 below Jaunty Users to get wacomcpl set up.

Interestingly someone tried "stylus" for stylus and it worked for him.  He didn't have an eraser so he wasn't able to try "eraser".

---

### Post by zoomy942 on 2009-06-19
> **Favux said:**
> Hi zoomy942,

OK, so:

stylus = "Wacom Serial Tablet PC Pen Tablet/Digitizer"
eraser = "Wacom Serial Tablet PC Pen Tablet/Digitizer eraser"

So you can substitute the new names in your rotation script and your old .xinitrc.  By renaming the stylus and eraser in the .xinitrc wacomcpl should work.  Or you could try rec's script and see if it works for you.  It should.  Then use Section 3 below Jaunty Users to get wacomcpl set up.

Interestingly someone tried "stylus" for stylus and it worked for him.  He didn't have an eraser so he wasn't able to try "eraser".

so i re-read this about 6 times and i kepy seeming like you jumped in mid-thought.  you say renaming things and such, but where /how can i get to that?  i know it's not in the xorg apparently.

---

### Post by Favux on 2009-06-19
Hi zoomy942,

I was referring back to the HOW TO I linked in post #4.  Some of the stuff applies to serial tablets too.  The .xinitrc is a hidden file that wacomcpl generates.  If you have your old one you should be able to rename the wacom input devices in it and wacomcpl would then work.  Or use rec's script as mentioned in Jaunty Users 3a) near the top.

---

### Post by zoomy942 on 2009-07-03
wow!  Thanks very much!  I ran through this this morning

[http://ubuntuforums.org/showthread.php?p=7068115#post7068115]("http://ubuntuforums.org/showthread.php?p=7068115#post7068115")

and its works great now.  nice!

now my next question will be how to enable the screen rotation.  i did this before in older ubuntu's with scripts and such, and the reason i am asking here is becasue i dont know if it's different (since setting up my stylus was so different).

---

### Post by Favux on 2009-07-03
Hi zoomy942,

Great!  Since you've installed wacom-names (rec's script) xsetwacom commands should now work.  Which means rotation scripts will work.  See the Rotation HOW TO here:  [http://ubuntuforums.org/showthread.php?p=6274392#post6274392](http://ubuntuforums.org/showthread.php?p=6274392#post6274392)  Method 1 or 3 should work.  If your video card lets you use Method 1 you can remove or comment out the touch lines in the script.

---

### Post by zoomy942 on 2009-07-04
is it normal that my right click that i config with the wacomcpl doesnt stay configed after i reboot?  i set it up and once i reboot its gone.

---

### Post by Favux on 2009-07-04
Hi zoomy942,

No that isn't normal.  Once you've set up the .xinitrc to run on startup in Startup Applications as in Section 3 here:  [http://ubuntuforums.org/showthread.php?t=1038949](http://ubuntuforums.org/showthread.php?t=1038949) it should apply.

So check the .xinitrc and make sure it's executable by right click and viewing properties.  Check that it's still in Startup applications.  Basically review the Section 3 steps.

---

### Post by zoomy942 on 2009-07-04
ha.  excellent.  i skipped step 3....lol:lolflag:

---

### Post by zoomy942 on 2009-07-10
So here is something for you.  im not sure if it is related, but maybe. 

Ever since i enabled all this, i get the problem where my tablet will boot up and at the login screen, the keyboard and eraserhead pointer will not respond.  the tablet stylus does and i reboot by touching that option on the screen, but before i ran through these steps that never ever ever happened.  

think its related?

---

### Post by Favux on 2009-07-11
Hi zoomy942,

I've never heard of anything like that.  Unless, I suppose, you try to setup an onscreen keyboard to log in.

In Section 3 above with wacomcpl did you do the part about checking that one file and commenting out the line if it wasn't already?

---

### Post by zoomy942 on 2009-09-22
her there Favux!  Thanks again for all you help thus far!
i ran into a snag and i was curios about your input.  I went to use the auto-magic rotation applet and i am confused.  First when i installed it, i got the error saying it couldnt find the hp_wmi, so i did a

```
zimmerman@Karmic-Tablet:~$ modprobe -l | grep hp-wmi
kernel/drivers/platform/x86/hp-wmi.ko
zimmerman@Karmic-Tablet:~$ ^C
zimmerman@Karmic-Tablet:~$ 

```

and saw that, then i saw you tell someone else to run

```
zimmerman@Karmic-Tablet:~$ gksudo gedit /etc/modules
```

so i did that, and now when i boot up, my applet sits in the loading state and never moves past it.  I posted a screenshot of it.  What do you think I should do next?

---

### Post by Favux on 2009-09-22
Hi zoomy942,

Well first a question.  Do you have auto-magic rotation in Windows?

Since hp-wmi requires wmi to work check to see if you have wmi.  Use the modprobe line grepping wmi first.  Then see if it's present in "lsmod".

---

### Post by zoomy942 on 2009-09-22
> **Favux said:**
> Hi zoomy942,

Well first a question.  Do you have auto-magic rotation in Windows?

Since hp-wmi requires wmi to work check to see if you have wmi.  Use the modprobe line grepping wmi first.  Then see if it's present in "lsmod".

yes sir.  in windows, i install the HP stuff and bam, rotate the screen, click her down and she rotates :).  this is the last thing in linux i have to configure then linux will do everything my windows would.

how do i do the grepping wmi?

---

### Post by Favux on 2009-09-22
Hi zoomy942,

Just like with hp-wmi:
```
modprobe -l | grep wmi
```

---

### Post by zoomy942 on 2009-09-22
and here you go good sir.

```
zimmerman@Karmic-Tablet:~$ modprobe -l | grep wmi
kernel/drivers/platform/x86/dell-wmi.ko
kernel/drivers/platform/x86/acer-wmi.ko
kernel/drivers/platform/x86/hp-wmi.ko
kernel/sound/core/snd-rawmidi.ko
zimmerman@Karmic-Tablet:~$ 

```

---

### Post by Favux on 2009-09-22
Hi zoomy942,

Sorry, that should have been:
```
modprobe -l | grep wmi.ko
```
It should be in /lib/modules/`uname -r`/extra/hp-wmi.ko where "uname -r" is your current kernel.  Or something close.  If it's there then check:
```
lsmod
```
If it's not in that output add it "wmi" (without the quotes) to "/etc/modules" above "hp-wmi" and reboot.

Of course this all depends on your bios supporting "wmi".

---

### Post by zoomy942 on 2009-09-22
here is what you mentioned below...

```
zimmerman@Karmic-Tablet:~$ modprobe -l | grep wmi.ko
kernel/drivers/platform/x86/dell-wmi.ko
kernel/drivers/platform/x86/acer-wmi.ko
kernel/drivers/platform/x86/hp-wmi.ko
zimmerman@Karmic-Tablet:~$ lsmod
Module                  Size  Used by
nls_iso8859_1           5280  0 
nls_cp437               6976  0 
vfat                   13184  0 
fat                    59832  1 vfat
usb_storage            65888  0 
binfmt_misc            10220  1 
ppdev                   8232  0 
vboxnetadp             94892  0 
vboxnetflt            102060  0 
vboxdrv              1710188  1 vboxnetflt
iptable_filter          3872  0 
ip_tables              21200  1 iptable_filter
x_tables               25832  1 ip_tables
snd_hda_codec_analog    79680  1 
sdhci_pci               8928  0 
sdhci                  20484  1 sdhci_pci
snd_hda_intel          31528  2 
snd_hda_codec          79776  2 snd_hda_codec_analog,snd_hda_intel
snd_pcm_oss            44704  0 
snd_mixer_oss          18976  1 snd_pcm_oss
snd_pcm                93160  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
arc4                    2144  2 
snd_seq_dummy           3460  0 
ecb                     3296  2 
snd_seq_oss            33440  0 
snd_seq_midi            8192  0 
snd_rawmidi            27360  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
iwlagn                123328  0 
snd_seq                60608  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
iwlcore               132320  1 iwlagn
mac80211              210136  2 iwlagn,iwlcore
snd_timer              26992  2 snd_pcm,snd_seq
snd_seq_device          8308  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    77096  15 snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
hp_wmi                  6896  0 
tpm_infineon           10044  0 
joydev                 13088  0 
soundcore               9088  1 snd
tpm                    18464  1 tpm_infineon
tpm_bios                7680  1 tpm
psmouse                57124  0 
serio_raw               6596  0 
hp_accel               12480  0 
lis3lv02d               9312  1 hp_accel
input_polldev           4720  1 lis3lv02d
led_class               5256  3 sdhci,iwlcore,hp_accel
lp                     11908  0 
parport                40528  2 ppdev,lp
snd_page_alloc         10928  2 snd_hda_intel,snd_pcm
cfg80211              109208  3 iwlagn,iwlcore,mac80211
uvcvideo               65260  0 
videodev               43360  1 uvcvideo
v4l1_compat            16804  2 uvcvideo,videodev
v4l2_compat_ioctl32    13344  1 videodev
ricoh_mmc               4480  0 
heci                   64676  0 
i915                  244456  3 
drm                   193856  3 i915
i2c_algo_bit            7076  1 i915
video                  23484  1 i915
e1000e                138704  0 
output                  3680  1 video
intel_agp              31856  1 
fbcon                  41248  71 
tileblit                3136  1 fbcon
font                    8832  1 fbcon
bitblit                 6688  1 fbcon
softcursor              2336  1 bitblit
zimmerman@Karmic-Tablet:~$ 

```

---

### Post by Favux on 2009-09-22
Hi zoomy942,

Alright, so it's not showing up in the modprobe.  Did you check the directory?

```
hp_wmi                  6896  0 
```
Is present presumably from adding it to the modules file.  Wmi should show up in lsmod if it was being loaded and look like:
```
wmi                    15808  1 hp_wmi
```

However I noticed:
```
hp_accel               12480  0 
```
So could it be that your tablet auto-rotates based on an accelerometer?  And not a swivel hinge switch?  Then this module seems dependent on it:
```
lis3lv02d               9312  1 hp_accel
```
And finally this module seems to depend on lis3lv02d:
```
input_polldev           4720  1 lis3lv02d
```
So maybe for your tablet pc the rotation signal is in/from input_polldev?

I'm not sure where to go.  Adding wmi to modules might bork your system.  Or if not it may not do anything.

---

### Post by zoomy942 on 2009-09-22
okay, here is a pic of that directory.  am i missing the extras folder?

and no sir, its just a swivle hinge like most other tablets. :)

---

### Post by Favux on 2009-09-22
Hi zoomy942,

I think you need to go into the kernel folder and then drivers one and finally the acpi folder.

---

### Post by zoomy942 on 2009-09-22
and there you have it

---

### Post by Favux on 2009-09-22
Hi zoomy942,

I guess you could do a Search for "wmi.ko".

I think it's suppose to be installed automatically with your kernel's "linux-image".  At least I think that's where it would be.  So is it not installing because your bios doesn't support it?

I suppose you could reinstall the "linux-image" using Synaptic Package Manager.  I don't think that would bork your system.  Just be very sure it's the same version as your kernel.
```
cat /proc/version_signature
```
The idea is that somehow wmi got left out of the previous "linux-image" install, even though it should have been included.

I'm just not sure it's worth trying because I'm not sure of the risk.  I think it's small to none as long as it's the correct version.

---

### Post by zoomy942 on 2009-09-22
well, let me ask you this - is the wmi part i saw in those HOW TO posts about installing your own something i should consider?  i skipped those steps.

---

### Post by Favux on 2009-09-22
Hi zoomy942,

No the wmi should be there.  That's for compiling hp-wmi in Intrepid which doesn't have it.

Let's look in Package search and see if we can find wmi:  [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

And by the way if you compiled a wacom.ko or other kernel driver/module reinstalling "linux-image" would knock it out.

---

### Post by Favux on 2009-09-22
Hmm.  It seems to be calling it wmi.h and then the results page links me through to:  [http://packages.ubuntu.com/jaunty/linux-headers-2.6.28-11-generic](http://packages.ubuntu.com/jaunty/linux-headers-2.6.28-11-generic)  So it may be in linux-headers?  Try searching your directories for wmi.h.  And look through Package search a bunch.  That doesn't seem right.

---

### Post by zoomy942 on 2009-09-22
here is the wmi section.

im running 9.10 by the way - not sure if that mattered

---

### Post by zoomy942 on 2009-09-22
> **Favux said:**
> Hmm.  It seems to be calling it wmi.h and then the results page links me through to:  [http://packages.ubuntu.com/jaunty/linux-headers-2.6.28-11-generic](http://packages.ubuntu.com/jaunty/linux-headers-2.6.28-11-generic)  So it may be in linux-headers?  Try searching your directories for wmi.h.  And look through Package search a bunch.  That doesn't seem right.

found it

---

### Post by Favux on 2009-09-22
Hi zoomy942,

OK, there it is.  At a wild guess does the name change from wmi.ko to wmi.h mean they took it from a kernel module in Intrepid and made it part of the kernel in Jaunty/Karmic?  Maybe that's why it isn't showing up in lsmod.  But if so it should still be active and supporting hp-wmi you'd think.

So I'm stuck.  I don't see why the applet doesn't work for you, other then the obvious that your bios doesn't support the wmi extensions.  I don't know how we'd figure that out.  See if the HP site has something on it?  Contact them?

---

### Post by zoomy942 on 2009-09-22
so it looks like it supports WMI

must be a name change from 9.04 to 9.10?

[http://74.125.155.132/search?q=cache:ZXkCp9am1ksJ:forums11.itrc.hp.com/service/forums/questionanswer.do%3FthreadId%3D1208628+2710p+wmi+bios&cd=3&hl=en&ct=clnk&gl=us&client=firefox-a]("http://74.125.155.132/search?q=cache:ZXkCp9am1ksJ:forums11.itrc.hp.com/service/forums/questionanswer.do%3FthreadId%3D1208628+2710p+wmi+bios&cd=3&hl=en&ct=clnk&gl=us&client=firefox-a")

more refernces to WMI here

[http://74.125.155.132/search?q=cache:YMQN1UFHTZAJ:dkukawka.blogspot.com/2008/08/how-to-activate-your-hp-umts-card.html+2710p+wmi+bios&cd=7&hl=en&ct=clnk&gl=us&client=firefox-a]("http://74.125.155.132/search?q=cache:YMQN1UFHTZAJ:dkukawka.blogspot.com/2008/08/how-to-activate-your-hp-umts-card.html+2710p+wmi+bios&cd=7&hl=en&ct=clnk&gl=us&client=firefox-a")

---

### Post by zoomy942 on 2009-09-22
something else i noticed...

on my tablet, i have little buttons on the screen edge for CRT+ALT+DEL, and that one works...  i have one for screen rotate as well...  could i find out what the command is when i press it and map it to a rotate script?

---

### Post by zoomy942 on 2009-09-22
what do you make of this?

[http://ubuntuforums.org/showpost.php?p=7191496&postcount=106]("http://ubuntuforums.org/showpost.php?p=7191496&postcount=106")

---

### Post by Favux on 2009-09-22
Hi zoomy942,

OK, from the links it does look like wmi/hp-wmi should work for your 2710p tablet pc.

So you should have the infrastructure set.

I think the problem may be with Karmic.  Another person just reported not seeing /sys/devices/platform/hp-wmi:
> Hi I'm also trying to run Karmic on my new Tx2. I notice that there is no /sys/devices/platform/hp-wmi folder but the hp-wmi module is install. Is it going to be update before the real release as the bug is filed as fixed in karmic. Am I missing something? Or, should I report a bug?
Both the script and applet look it that location for the "tablet" event to trigger the rotation.  So if that's right we need to find where the new location is.  And/or file a bug like he suggests.  Since Karmic has 2.6.31 you have the "patched" hp-wmi that returns "tablet" rather than "dock" for the event.  So right now it's a mystery.

Regarding the rotation bezel button did you look in step 5) or 6) in the Rotation HOW TO for how to use xev?

I'm not sure what you're asking about re MisterR2's post.

---

### Post by zoomy942 on 2009-09-22
> **Favux said:**
> Hi zoomy942,

OK, from the links it does look like wmi/hp-wmi should work for your 2710p tablet pc.

So you should have the infrastructure set.

I think the problem may be with Karmic.  Another person just reported not seeing /sys/devices/platform/hp-wmi:

Both the script and applet look it that location for the "tablet" event to trigger the rotation.  So if that's right we need to find where the new location is.  And/or file a bug like he suggests.  Since Karmic has 2.6.31 you have the "patched" hp-wmi that returns "tablet" rather than "dock" for the event.  So right now it's a mystery.

Regarding the rotation bezel button did you look in step 5) or 6) in the Rotation HOW TO for how to use xev?

I'm not sure what you're asking about re MisterR2's post.


understood on all counts.  so, how about tomorrow, i fire up 9.04 on a thumbdrive LIVECD and set all this up and see if it works?  think that would help explin more of the mystery?  next, as for that post about not having that folder, i hate it (screenshot attached).  

i feel like we are close, and karmic may have just changed the name a bit/location...

i'm 100% at your disposal to figure this out.

---

### Post by zoomy942 on 2009-09-22
and steps 5 and 6 where?  i have like 7 How To's open  LOL

---

### Post by Favux on 2009-09-22
Hi zoomy942,

Oops, sorry.  I meant the Rotation HOW TO:  [http://ubuntuforums.org/showthread.php?p=6274392](http://ubuntuforums.org/showthread.php?p=6274392)  under "let's get down to rotating".

---

### Post by zoomy942 on 2009-09-22
when i run xev, i get no reponse about my button, so i run that command to remove the hotkeys and readd them?  lol- it says no file found.  so thats not it.

ugh - i know i'm close.  it's gotta be something small i skipped.

---

### Post by Favux on 2009-09-22
Hi zoomy942,

Two out of our four bezel buttons don't work.  Red_Lion was working on it.  It looks like either the DSDT is buggy or more likely needs lines written in to support them.  I sum up what little I know in posts #273 and #274 here:  [http://ubuntuforums.org/showthread.php?t=996830&page=28](http://ubuntuforums.org/showthread.php?t=996830&page=28)

---

### Post by zoomy942 on 2009-09-22
> **Favux said:**
> Hi zoomy942,

Two out of our four bezel buttons don't work.  Red_Lion was working on it.  It looks like either the DSDT is buggy or more likely needs lines written in to support them.  I sum up what little I know in posts #273 and #274 here:  [http://ubuntuforums.org/showthread.php?t=996830&page=28](http://ubuntuforums.org/showthread.php?t=996830&page=28)

pfft!  what little you know!?  you have been a genius with helping me as far as I'm concerned.  :)

so, i will negate using my bezel button for now.  

from what i have read, there is a certain signal that my tablet uses to say ROTATE, and the guys that discovered this in the TX tablets had that signal figured out.  do you think maybe my signal is different?  i'm not sure because as of now, the applet sits at loading, like its looking for hp_wmi..  but then again, if it couldnt find it, it would error out.  It's not erroring out, it's just sitting at loading, as if it doesnt know what to do with it.  i bet you dollars to donuts if i loaded 9.04 it would all work fine.

---

### Post by Favux on 2009-09-23
Hi zoomy942,

Ayuthia was nice enough to test the applet out for us in Karmic just now.  It works for him.  Apparently hp-wmi isn't loading by default and the guy I quoted didn't know to add it to /etc/modules.  So that's not your problem.  Darn.

> do you think maybe my signal is different?
Maybe it is.  Maybe it would work in 9.04?  I just don't know.  And you could try the script and see what happens.  If you do want to mess around with the script remember to do the changes for the "patched" hp-wmi, which is what you have in Karmic.

---

### Post by Ayuthia on 2009-09-23
I think I am now caught up with your information about the hp-wmi and rotation.  The signal for the tablet mode should be in /sys/devices/platform/hp-wmi/tablet.  If you do:
```
cat /sys/devices/platform/hp-wmi/tablet
```when it is in normal mode, it should return 0.  If the lid is closed and in tablet mode, it should return 1.

Does your stylus have an eraser?  I think that there might be a bug with the app that will make it show "Loading..." if there is no eraser.  It has been a while since I looked at the code.  I recall having that problem, but the app still rotated.  Does the app allow your tablet to rotate the screen?

Another thing that might help is to run the application from the Terminal.  If you go to the application's directory in the Terminal and do the following:
```
./magic-rotation-0.2-4
```It should run the application and it should also display any issues that it encounters.

If you want to test out the swivel code, you can do the cat command at the top of this post when the lid is open.  You will need CellWriter to do it when it is closed (since you will not have access to the keyboard when the lid is closed).  If you don't use the Terminal that often you can do the first command with the lid open, then run cell writer, close the lid, and with cell writer press the up arrow key and then press the enter key.  The up arrow will retrieve the last command entered.

---

### Post by Favux on 2009-09-23
Hi zoomy942,

Thanks Ayuthia that should get us going!

And zoomy for eraser read touch.  If you can ever get to the applet icon, right click on it and go to Advanced Settings.  Just delete touch.

---

### Post by zoomy942 on 2009-09-23
Thanks for the help!!  Excellent progress.  I ran the cat command and posted the results in the screenshot.  it does in fact change from 0 to 1, so we know the signal is working.  also, i removed touch from the advanced settings and still it sits at looading.  and to answer your question, it doesnt rotate the screen yet.

i ran the applet from the terminal (as in the screenshot) and it worked fine, no errors.  it gave an error when Tough was still in the advanced settings, and once i removed it, it stopped giving the error.  

We are getting there!  :)

---

### Post by Favux on 2009-09-23
Hi zoomy942,

Definite progress!

Looking at your screen shot it sure seems like it should be rotating.  Everything seems to be in place.

In fact, since we now know wmi was present in the kernel all along, it should have started rotating as soon as you added hp-wmi to /etc/modules and rebooted.  Even with inotify picking up on the touch error I'd think.  If you also have wmi in /etc/modules you should remove it and reboot.

There were a lot of changes made to the Xorg Intel video drivers going from Jaunty to Karmic.  I don't know what method for rotation you were using in Jaunty.  Does it work in Karmic for you?

---

### Post by Ayuthia on 2009-09-23
I am not for sure what is happening here.  I have run into this a while back when I was testing, but I attributed it to me working on a different version of this app while I was testing this one.

Favux, it looks like state_change is not getting called or else it is stalling before it gets there.  My theories:
[LIST=1]
[*]state_chage is not getting called.  We could put a print statement at the beginning of the function and see if it gets in there.
[*]The read to the tablet file is not getting populated.  Once again we can place a print statement there to see what cur_state is storing in state_notifier.
[/LIST]

Your thoughts?

---

### Post by Favux on 2009-09-23
Hi zoomy942,

Say do you have CellWriter installed?

Meanwhile I'll take a look at Ayuthia's very good suggestions.

---

### Post by zoomy942 on 2009-09-23
> **Favux said:**
> Hi zoomy942,

Definite progress!

Looking at your screen shot it sure seems like it should be rotating.  Everything seems to be in place.

In fact, since we now know wmi was present in the kernel all along, it should have started rotating as soon as you added hp-wmi to /etc/modules and rebooted.  Even with inotify picking up on the touch error I'd think.  If you also have wmi in /etc/modules you should remove it and reboot.

There were a lot of changes made to the Xorg Intel video drivers going from Jaunty to Karmic.  I don't know what method for rotation you were using in Jaunty.  Does it work in Karmic for you?

hey there - I have cell writer installed yes sir.

as for the method i had before, i was a rotate.sh and normal.sh script that i manually ran.  i will go try them now.  Stand by.

---

### Post by zoomy942 on 2009-09-23
Okay, i tested this script.

```
#!/bin/bash
#script by Francisco Athens modified from Gentoo Wiki Intructions:
#http://gentoo-wiki.com/HARDWARE_HP_Compaq_2710p#Brightness_and_Rotation
#get current setting
testrot=`xrandr -q |grep LVDS | awk '{print $3}'`
#test if screen is rotated in protrait mode
if [ "$testrot" = "800x1280+0+0" ];then
#optional kill any old xvkbd instances so that
# fresh one can load in the correct place in the screen
#killall xvkbd
xrandr -o normal
xsetwacom set stylus rotate 0
xsetwacom set eraser rotate 0
else
#killall xvkbd
xrandr --output LVDS --rotate right
xsetwacom set stylus Rotate CW
xsetwacom set eraser Rotate CW
#optional: put xvkbd on the bottom of the screen
#xvkbd -always-on-top -geometry 800x150+0-0
fi
```

and ya know - it didnt rotate the screen, but the stylus directions were all wrong and going to wrong way.  so it responded, but the video didnt move, maybe it's like you had said about intel drivers being alot different in Karmic

---

### Post by zoomy942 on 2009-09-23
i was playing around with xrandr manually and check this out.

---

### Post by Favux on 2009-09-23
Hi zoomy942,

Oh boy...

Alright, the stylus going off seems to mean the xsetwacom commands worked, just not xrandr.  By the way in the script, I think 0 (for normal) is the old syntax, and it should be 'NONE' for the newer versions.  Although I think it's suppose to be backwards compatible I think I remember something about exceptions.  Whatever.

I can't read what's on the screen shot.  Or is that what you're showing?  The font gets garbled?

Assuming I'm not missing something important from the screen shot:

Anyway this could be a serious bug and headache for Intel video users in Karmic.

I don't remember seeing anything about this in the Karmic testing forum.  You could search there for an answer about rotation with Intel.  Hopefully it's not a bug, just some sort of configuration needed in xorg.conf or whatever.

If that doesn't go anywhere you might want to search launchpad and see if anyone has reported no rotation with Intel in Karmic.  If not you probably should file a bug report.  And start a thread in the Karmic forum.

Hopefully I'm over reacting.

Edit:  Oops!  You were showing me the screen rotated into tablet mode!  Ouch.

---

### Post by Ayuthia on 2009-09-23
I am always a few minutes behind.  I was thinking that you should just try xrandr -o right and it looks like you have done it and it appears that it worked.

Does the xsetwacom command work in getting the stylus in the right direction?

---

### Post by zoomy942 on 2009-09-23
> **Ayuthia said:**
> I am always a few minutes behind.  I was thinking that you should just try xrandr -o right and it looks like you have done it and it appears that it worked.

Does the xsetwacom command work in getting the stylus in the right direction?

hey there.

so i tried it with manually doing xsetwacom and xrandr and ya know what - it worked perfectly.  so now  now im wondering why the applet isnt seeing everything.

also, i noticed that the applet doesnt show the cell writer window when i flip the screen accroding to the settings. 

this is GREAT progress!  you guys rock!

---

### Post by Favux on 2009-09-23
Hi zoomy942,

Correct me if I'm misunderstanding you, but it isn't just the applet, is it?  You're able to manually rotate the screen and stylus in a terminal but your old rotate script doesn't work.  Is that right?  Have you tried a method 1 script in the Rotation HOW TO?:  [http://ubuntuforums.org/showthread.php?p=6274392](http://ubuntuforums.org/showthread.php?p=6274392)  Or Tom Jaeger's rotation daemon in method 3?

I guess I'd like to see a script working for you before we move on to the applet.  Preferably the Auto-magic Rotation script in method 4.

Do you see what I'm saying?

---

### Post by zoomy942 on 2009-09-24
i see exactly what you are saying.  you want to prove the functionality is there before messing around with the applet.  makes perfect sense.  thats why i'm so willing to work on this with any information you need - that applet is AWESOME.

okay, so method 1 works perfectly fine.  flips the screen and stylus.  BAM.

method 3 gave an error when i went to install it and i posted a screenie of the error.

---

### Post by Favux on 2009-09-24
Hi zoomy942,

Good, at least you have a working rotation script available.

I should have realized the Jaunty deb wouldn't work in Karmic.  Tom's a good guy, he'll probably update it soon.  Or we could ask.

Do you feel up to trying to see if you can get the auto-magic rotation script working first?

---

### Post by zoomy942 on 2009-09-24
> **Favux said:**
> Hi zoomy942,

Good, at least you have a working rotation script available.

I should have realized the Jaunty deb wouldn't work in Karmic.  Tom's a good guy, he'll probably update it soon.  Or we could ask.

Do you feel up to trying to see if you can get the auto-magic rotation script working first?

Of course!  I'm up for anything!  :)

---

### Post by Favux on 2009-09-24
Hi zoomy942,

You're probably working on the script.  I hope you've got it/will get it working.  In the meantime I thought I'd upload the "debugging" Magick for you.

Follow the same instructions and place it alongside 0.2-4.  That way you'll have the icons.  Remember to go into Properties and make it executable.  Quit Magick if you have it running.

Then open a terminal in the same directory like before and enter:
```
./debug_magick-rotation-0.2-4
```
You should see output in the terminal like this when you rotate to tablet and back:
```
~$ ./debug_magick-rotation-0.2-4
Use native hp_wmi event file
stfile output: <open file '/sys/devices/platform/hp-wmi/dock', mode 'r' at 0x2217030>
True
Change to normal state
False
Change to Tablet mode
True
Change to normal state
```
With the terminal in focus use ctrl + c to shut down Magick.  A backtrace that might be useful should appear.  Post the output.

If you see output like above then it's on to the next step.  Remove the comment on line 231 from in front of:
```
#				print 'cur_state output:', cur_state
```
Be sure to preserve the line's indentation.

Now when you restart Magick you should see current state which should be 0.  It will keep repeating at the polling interval.  So rotate to tablet fairly quickly, which should then change state to 1 for you, and then back to landscape.  Then hit ctrl + c to quit Magick.  If you take too long you'll fill up the terminal and loose the beginning of the output.  The output should be something like:
```
~$ ./debug_magick-rotation-0.2-4
Use native hp_wmi event file
stfile output: <open file '/sys/devices/platform/hp-wmi/dock', mode 'r' at 0x13fb030>
cur_state output: 0

True
Change to normal state
cur_state output: 0

cur_state output: 4

False
Change to Tablet mode
cur_state output: 4

cur_state output: 0

True
Change to normal state
cur_state output: 0

```
Of course I removed the extra current state lines.

My hope is this is just a glitch in Karmic and an update will come along any minute and fix it for you.

---

### Post by Ayuthia on 2009-09-24
I duplicated the error, I think.

zoom842, Do you have wacom-tools installed?

EDIT:
Actually, can you try running cellwriter then run the magick-rotation application?  I think that it is getting stuck on the first call to cellwriter.

---

### Post by Favux on 2009-09-24
Hi zoomy942 and Ayuthia,

Attached find a new "debug" Magick with Ayuthia's proposed fix.

Use:
```
./debug-2_magick-rotation-0.2-4
```
to start it.

---

### Post by zoomy942 on 2009-09-24
holy crap that worked!!

let me keep testing it before i start jumping up and down :)

PS - how did you do that?

---

### Post by zoomy942 on 2009-09-24
okay, here is an update.  i did a total of 10 screen flips, slowly to not make it mad, amd when i got back to normal and went to use my eraser head pointer (no trackpad on this tablet) and it wasnt responding.  turns out the keyboard wasnt responding either.  but, my stylus worked fine, so i rebooted and i had input back again.

does that make sense?  i wonder whats up - but the screen flipping workd great!  i love you guys!

---

### Post by zoomy942 on 2009-09-25
hmm  at reboot, im getting 2 cellwriters opening too.  im gonna investitage...

---

### Post by Favux on 2009-09-25
Hi zoomy942,

Totally cool!

So it looks like we can add the HP 2700's to the list.  Aside from the HP 2710p there's a 2720 something, right?  Any others?

Not sure why you lost eraser and keyboard.  Seen that, keyboard and bezel buttons stop working in tablet mode, with the TX2500's.  The fix for them was updating the bios.  So see if there's a bios update available.  Apparently something in the bios.  Maybe a buggy DSDT?

Keep testing.  Let me know.  Did you capture any of the output?

I feel a Magick 0.2-5 coming on.  And then maybe a merge with Ayuthia's code?

Don't understand a second CellWriter.  Magick shouldn't do that.

---

### Post by zoomy942 on 2009-09-25
> **Favux said:**
> Hi zoomy942,

Totally cool!

So it looks like we can add the HP 2700's to the list.  Aside from the HP 2710p there's a 2720 something, right?  Any others?

Not sure why you lost eraser and keyboard.  Seen that, keyboard and bezel buttons stop working in tablet mode, with the TX2500's.  The fix for them was updating the bios.  So see if there's a bios update available.  Apparently something in the bios.  Maybe a buggy DSDT?

Keep testing.  Let me know.  Did you capture any of the output?

I feel a Magick 0.2-5 coming on.  And then maybe a merge with Ayuthia's code?

Don't understand a second CellWriter.  Magick shouldn't do that.

the only other one is a 2730, which is the same as mine besides a cpu difference.  

thansk for the info about the tx2500's and the freeze problem.  i will hunt around for bios upgrades...LOL - then see if i can upgrade the bios with linux.

how would you like me to capture any outputs, i sure dont mind if it will help you out at all.  i think merging with his code is a good idea ftrom what you two discovered here.  i can help test if you'd like it.  you never said whay you did to make it work ;)

as for cellwriter...whats odd is it acts like its just the icon, not cell writer becasue when i go to right click it and chose about, its the about window for the notification area, not cell writer.  strange huh?

something as a side note, i have learnedusing Karmic - anytime there are init updates pushed out, my right click gets broken on my tablet.  LOL - gotta love alpha testing huh?

---

### Post by Favux on 2009-09-25
Hi zoomy942,

Is it the 2730p?

Do not try to upgrade bios with linux!!!  Much better to use windows.  It's doable but fraught with danger.  At least that's what I've read.

Aren't you running the debug version through the terminal?  It should be spitting out extra lines that I added to help debug it.  Oh well.

It turns out Ayuthia had already run into this bug and fixed it while adapting the Magick code for his TX2z/n-trig project.  So I added his fix.  Small change to one line (#181 when I changed it).

Not sure what's going on with CellWriter icon/notification area about.  Now that may be something from Magick.  Some sort of cross over from inotify?  I don't know.  There aren't two instances of CellWriter in your Startup Applications, is there?

Well you're the one who loaded an alpha.  Always an adventure.  :)

---

### Post by Ayuthia on 2009-09-25
> **Favux said:**
> Hi zoomy942,

Is it the 2730p?

Do not try to upgrade bios with linux!!!  Much better to use windows.  It's doable but fraught with danger.  At least that's what I've read.

Aren't you running the debug version through the terminal?  It should be spitting out extra lines that I added to help debug it.  Oh well.

It turns out Ayuthia had already run into this bug and fixed it while adapting the Magick code for his TX2z/n-trig project.  So I added his fix.  Small change to one line (#181 when I changed it).

Not sure what's going on with CellWriter icon/notification area about.  Now that may be something from Magick.  Some sort of cross over from inotify?  I don't know.  There aren't two instances of CellWriter in your Startup Applications, is there?

Well you're the one who loaded an alpha.  Always an adventure.  :)

The debug version does not come with the icons for the system tray so my spot is invisible there.  Could that be the problem that is making it look like there is more than one cellwriter?

EDIT: One other question:  zoomy942, do you use any boot parameters?  Can you check /var/log/dmesg.0 and see what it says after this happens?  dmesg.0 is the log for the previous session so if the keyboard crashed, it should show up around the end of that log.

---

### Post by Favux on 2009-09-25
Hi zoomy942 & Ayuthia,

I asked zoomy942 to place the debug version next to 0.2-4 so that the icons would be available.  Did you zoomy?

Funny thing happened on the way to 0.2-5.  I've been using "killall cairo-dock" before and "cairo-dock -o &" after the CellWriter calls to restart Cairo Dock so that it resizes correctly after rotation.  Needless to say this causes the hang again.

So I could either not use the fix and add " &" to the CellWriter lines near the beginning or put a warning in Advanced Settings.  I went with the warning.  But this is a change in practice, since I've been telling folks to use '&' when needed.  Any thoughts?

Ayuthia, trivial syntax question.  I found 'os.system(i + "&")' also works.  Although you'd think you would need the space as in 'os.system(i + " &")'.

---

### Post by Ayuthia on 2009-09-25
> **Favux said:**
> Hi zoomy942 & Ayuthia,

I asked zoomy942 to place the debug version next to 0.2-4 so that the icons would be available.  Did you zoomy?

Funny thing happened on the way to 0.2-5.  I've been using "killall cairo-dock" before and "cairo-dock -o &" after the CellWriter calls to restart Cairo Dock so that it resizes correctly after rotation.  Needless to say this causes the hang again.

So I could either not use the fix and add " &" to the CellWriter lines near the beginning or put a warning in Advanced Settings.  I went with the warning.  But this is a change in practice, since I've been telling folks to use '&' when needed.  Any thoughts?

Ayuthia, trivial syntax question.  I found 'os.system(i + "&")' also works.  Although you'd think you would need the space as in 'os.system(i + " &")'.

The space is not really needed.  It is just my habit to do so.  As for the & in the code, if there are problems with Cairo Dock and the &, I would leave it out of the code, and add the warning.  You might change the code to default cellwriter to have the & at the end so that it will work.  There is no easy way to trap this scenario because it is not an error.  It is just waiting for the application to finish.

I don't use Cairo Dock, but what does the -o do?

---

### Post by Favux on 2009-09-25
Hi Ayuthia,

Cairo Dock 2.x is now openGL so '-o' tells it to use openGL.  You can also start it with '-c' so it uses cairo if your video card doesn't support openGL.  It looks like both Intel and ATI will finally support openGL in Karmic.

> There is no easy way to trap this scenario because it is not an error. It is just waiting for the application to finish.
Right.  Good point.

---

### Post by zoomy942 on 2009-09-26
> **Favux said:**
> Hi zoomy942,

Is it the 2730p?

Do not try to upgrade bios with linux!!!  Much better to use windows.  It's doable but fraught with danger.  At least that's what I've read.

Aren't you running the debug version through the terminal?  It should be spitting out extra lines that I added to help debug it.  Oh well.

It turns out Ayuthia had already run into this bug and fixed it while adapting the Magick code for his TX2z/n-trig project.  So I added his fix.  Small change to one line (#181 when I changed it).

Not sure what's going on with CellWriter icon/notification area about.  Now that may be something from Magick.  Some sort of cross over from inotify?  I don't know.  There aren't two instances of CellWriter in your Startup Applications, is there?

Well you're the one who loaded an alpha.  Always an adventure.  :)

yup, its the 2730p.  i attched a screenshot of the terminal, and even after i pressed CRTL C to end it, hoping it shows the output you were looking for.  did it work okay?

and ignore those errors about the stylus.  i havent gone through and re-enabled it yet.  good ol' Alphas.  :)

---

### Post by zoomy942 on 2009-09-26
> **Ayuthia said:**
> The debug version does not come with the icons for the system tray so my spot is invisible there.  Could that be the problem that is making it look like there is more than one cellwriter?

EDIT: One other question:  zoomy942, do you use any boot parameters?  Can you check /var/log/dmesg.0 and see what it says after this happens?  dmesg.0 is the log for the previous session so if the keyboard crashed, it should show up around the end of that log.


i went to boot up today, and it only showed 1 cellwriter.  hmm - nothing like a random bug.

as far as boot parameters, since im not entirely sure what those are, i'm gonna go ahead and say i dont use any.  want me to still check out that log for you?

---

### Post by Favux on 2009-09-26
Hi zoomy942,

Nope, your screenshot  on post #66 is perfect and shows what's expected.  Somehow I completely spaced it.  Maybe cause I was waiting for the current state stuff?  I have no idea.

Anyway is Magick working well for you?  Any further, other problems?

Boot parameters would be stuff you've added to the kernel boot line like acpi=off or something.  Always a good idea to eyeball the log when an error happens.

---

### Post by zoomy942 on 2009-09-26
> **Favux said:**
> Hi zoomy942,

Nope, your screenshot  on post #66 is perfect and shows what's expected.  Somehow I completely spaced it.  Maybe cause I was waiting for the current state stuff?  I have no idea.

Anyway is Magick working well for you?  Any further, other problems?

Boot parameters would be stuff you've added to the kernel boot line like acpi=off or something.  Always a good idea to eyeball the log when an error happens.

so far it seems to be working great.  I'm looking around on the interwebz for info about other people noticing the occasional keyboard freeze when returning to laptop mode from tablet mode - but i havent looked alot since i was at work all day today.

as for the debug version i am using, is that okay to use for now? want me to test another version i saw you mention?  

other 2710p and 2730p users will be excited this works in linux now - thanks to you two's hard work.  

i will go look at that log spot, but now that you describe it, i am certain i havent changed anything.

---

### Post by Favux on 2009-09-26
Hi zoomy942,

Sure, it'll be OK for now.  I'll try and post 0.2-5 tomorrow and it would be great if you'd test it.

---

### Post by zoomy942 on 2009-09-26
> **Favux said:**
> Hi zoomy942,

Sure, it'll be OK for now.  I'll try and post 0.2-5 tomorrow and it would be great if you'd test it.

okay buddy.  i am all yours.  just tell me what you want me to test and post and i'll get it done for you.

thanks for letting me help

---

### Post by Ayuthia on 2009-09-26
> **zoomy942 said:**
> i went to boot up today, and it only showed 1 cellwriter.  hmm - nothing like a random bug.

as far as boot parameters, since im not entirely sure what those are, i'm gonna go ahead and say i dont use any.  want me to still check out that log for you?

The log might be helpful mainly to see why the keyboard stops working.  If you don't recall adding any boot paramaters, then you most likely haven't added any.

The next time the keyboard quits working, you can post the dmesg.0 log and we can look at it if it does not make any sense to you.  The log will also let us know if you are using any boot parameters.

The tx2 does need a boot parameter added to help the keyboard from quitting when it goes into suspend mode if I recall correctly.  That is why I was asking.

---

### Post by zoomy942 on 2009-09-26
> **Ayuthia said:**
> The log might be helpful mainly to see why the keyboard stops working.  If you don't recall adding any boot paramaters, then you most likely haven't added any.

The next time the keyboard quits working, you can post the dmesg.0 log and we can look at it if it does not make any sense to you.  The log will also let us know if you are using any boot parameters.

The tx2 does need a boot parameter added to help the keyboard from quitting when it goes into suspend mode if I recall correctly.  That is why I was asking.

excellent to know!  i will try it today!

---

### Post by Favux on 2009-09-26
Hi zoomy942,

Magick Rotation 0.2-5 is posted.  It's at post #291 here:  [http://ubuntuforums.org/showthread.php?t=996830&page=30](http://ubuntuforums.org/showthread.php?t=996830&page=30)

Please let me know how it works for you.

---

### Post by zoomy942 on 2009-09-26
okay, color my confused.  i havent changed anything since last nght besides the normal round of updates (the only big one being the 2.6.31-11 kernel update...

and now it will rotate to tablet fine (as shown in the screenshot) but when i rotate back to regular, nothing happens.  how about them apples.  i can manually use xrandr to switch it but the applet doesnt do it.

ugh - and it did like 24 hours ago.

---

### Post by Favux on 2009-09-26
Hi zoomy942,

Well that doesn't sound good.  Maybe I goofed somewhere.

Try right clicking on it and going into Advanced Settings.  Make sure everything is good and then Save.  And then reboot and see if it works.

If not quit it and check if the debug 0.2-4 works.

I guess kernel updates could possible mess up the video.

---

### Post by zoomy942 on 2009-09-26
i went back and tried the previous version that was working fine and it didnt work either.

---

### Post by zoomy942 on 2009-09-26
it's gotta be something small becasue it acts like it wants to work.

let me try that cat command thing...  stand by.

---

### Post by zoomy942 on 2009-09-26
looks like it still sees the signal.  

Intel video problem maybe?  i think there was an update to that too.

what can i do to help?

---

### Post by Favux on 2009-09-27
Hi zoomy942,

The signal is correct so wmi/hp-wmi is working.

A kernel and possible Intel video update occurs in Karmic today.

Debug Magick 0.2-4 no longer works.  So whatever is wrong isn't due to, or just due to, 0.2-5.

Are you able to manually rotate through a terminal?  Do the xsetwacom rotation commands work too?

---

### Post by zoomy942 on 2009-09-27
> **Favux said:**
> Hi zoomy942,

The signal is correct so wmi/hp-wmi is working.

A kernel and possible Intel video update occurs in Karmic today.

Debug Magick 0.2-4 no longer works.  So whatever is wrong isn't due to, or just due to, 0.2-5.

Are you able to manually rotate through a terminal?  Do the xsetwacom rotation commands work too?


Yes sir. Works great.

---

### Post by Favux on 2009-09-27
Ok, so manual works good.

Was there a python update in there by any chance?

---

### Post by zoomy942 on 2009-09-27
> **Favux said:**
> Ok, so manual works good.

Was there a python update in there by any chance?

That's a good question. When I see a list of updates, I genarlly scan for pulseaudio, intel, and kernels. Where can we find out what was updated?

---

### Post by Favux on 2009-09-27
Hi zoomy942,

I think I've seen a command in the Jaunty or Karmic developement forums for that.  Basically "dpkg something".  But I can't remember it.

Nothing clever is coming to me at this point.  We'll see if it does or if Ayuthia has an idea.

---

### Post by Favux on 2009-09-27
Hi zoomy942,

I just had a TX2z in Jaunty tell me Magick 0.2-5 worked for him.  (Either that or he was just very excited to download it.)

So let's test if Magick is able to update the 'state' to itself in Karmic:  0 or 1

Go to post #63 and using the debug 0.2-4 version follow the instructions for removing the comment in front of the cur_state line.  Run it in a terminal as described and see if it starts spitting out:
```
cur_state output: 0
```
lines.  Changing to:
```
cur_state output: 1
```
when rotated.

---

### Post by zoomy942 on 2009-09-27
so there is the problem.  it can change to one way, b ut it doesnt "feel" the change back to normal.

```
zimmerman@Karmic-Tablet:~$ ./debug-2_magick-rotation-0.2-4
Use patched hp_wmi event file
stfile output: <open file '/sys/devices/platform/hp-wmi/tablet', mode 'r' at 0x2717360>
cur_state output: 0

True
Change to normal state
cur_state output: 0

cur_state output: 0

cur_state output: 0

cur_state output: 0

cur_state output: 0

cur_state output: 0

cur_state output: 0

cur_state output: 0

cur_state output: 0

cur_state output: 0

cur_state output: 0

cur_state output: 0

cur_state output: 0

cur_state output: 0

cur_state output: 0

cur_state output: 0

cur_state output: 0

cur_state output: 0

cur_state output: 0

cur_state output: 0

cur_state output: 0

cur_state output: 0

cur_state output: 0

cur_state output: 0

cur_state output: 0

cur_state output: 1

False
Change to Tablet mode
cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

^Ccellwriter: Caught signal 2, cleaning up
Traceback (most recent call last):
  File "./debug-2_magick-rotation-0.2-4", line 517, in <module>
    gtk.main()
KeyboardInterrupt
zimmerman@Karmic-Tablet:~$ xrandr -o normal
zimmerman@Karmic-Tablet:~$ 


```

---

### Post by Favux on 2009-09-27
Hi zoomy942,

Thanks for doing that.  Magick's showing the state, both unrotated and rotated.  So why doesn't state change back to 0 when rotating back to landscape?

We'll need Ayuthia to look at it.

I think it's CellWriter again.  Either it doesn't work right yet in Karmic or the commands for show and hide have changed in Karmic:
```
cellwriter --show-window

cellwriter --hide-window
```
I think it's hanging after the show command.  So either something about that or the hide command going back to landscape.  We see CellWriter on your screenshot in tablet mode anyway, correct?  I could be way off of course.

If you haven't spent much time training it why don't you do a complete uninstall through Synaptic and reboot.  Then reinstall it and reboot.  Then cross your fingers and try to rotate after checking Advanced Settings and saving.

---

### Post by zoomy942 on 2009-09-27
> **Favux said:**
> Hi zoomy942,

Thanks for doing that.  Magick's showing the state, both unrotated and rotated.  So why doesn't state change back to 0 when rotating back to landscape?

We'll need Ayuthia to look at it.

I think it's CellWriter again.  Either it doesn't work right yet in Karmic or the commands for show and hide have changed in Karmic:
```
cellwriter --show-window

cellwriter --hide-window
```
I think it's hanging after the show command.  So either something about that or the hide command going back to landscape.  We see CellWriter on your screenshot in tablet mode anyway, correct?  I could be way off of course.

If you haven't spent much time training it why don't you do a complete uninstall through Synaptic and reboot.  Then reinstall it and reboot.  Then cross your fingers and try to rotate after checking Advanced Settings and saving.


I understand what you are saying. I will reinstall cellwriter first thing in the morning. I'm gonna go to sleep now - I have a 2 year old who will have me up bright and early at 7am mountain time. 

You rock buddy :)

---

### Post by Favux on 2009-09-27
Hi zoomy942,

The terrible twos, oh no!

Before reinstalling CellWriter see if this makes a difference.  I found an error in the Advanced Settings table that apparently has been there all along.  It behaves differently when you go to Setup and Advanced Settings anyway.  So something changed with the "correction".

You can remove the "-fix" in the name.

Let me know.  I have to crash too.

---

### Post by Ayuthia on 2009-09-27
> **zoomy942 said:**
> so there is the problem.  it can change to one way, b ut it doesnt "feel" the change back to normal.

```
zimmerman@Karmic-Tablet:~$ ./debug-2_magick-rotation-0.2-4
Use patched hp_wmi event file
stfile output: <open file '/sys/devices/platform/hp-wmi/tablet', mode 'r' at 0x2717360>
cur_state output: 0

True
Change to normal state
cur_state output: 0

cur_state output: 0

cur_state output: 0

cur_state output: 0

cur_state output: 0

cur_state output: 0

cur_state output: 0

cur_state output: 0

cur_state output: 0

cur_state output: 0

cur_state output: 0

cur_state output: 0

cur_state output: 0

cur_state output: 0

cur_state output: 0

cur_state output: 0

cur_state output: 0

cur_state output: 0

cur_state output: 0

cur_state output: 0

cur_state output: 0

cur_state output: 0

cur_state output: 0

cur_state output: 0

cur_state output: 0

cur_state output: 1

False
Change to Tablet mode
cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

cur_state output: 1

^Ccellwriter: Caught signal 2, cleaning up
Traceback (most recent call last):
  File "./debug-2_magick-rotation-0.2-4", line 517, in <module>
    gtk.main()
KeyboardInterrupt
zimmerman@Karmic-Tablet:~$ xrandr -o normal
zimmerman@Karmic-Tablet:~$ 


```

So, does the output keep showing 1 repeatedly or does it stop when the lid is back in the normal position?  I was able to test it out in Karmic and it ran over here. If the 1 stops repeating then it is getting stuck at the os.system command if it does not stop, then it is not reading the signal.

If you want to look at the install logs, you can go into /var/log/dpkg.log and see what was updated.  There was an intel driver change in the last one for me.  There was a python update around the 24th or earlier.

---

### Post by zoomy942 on 2009-09-27
> **Favux said:**
> Hi zoomy942,

The terrible twos, oh no!

Before reinstalling CellWriter see if this makes a difference.  I found an error in the Advanced Settings table that apparently has been there all along.  It behaves differently when you go to Setup and Advanced Settings anyway.  So something changed with the "correction".

You can remove the "-fix" in the name.

Let me know.  I have to crash too.


lol yeah - well, im up.  been up since 7:30.  she came to cuddle with wifey and i at 5.  love it.

i tried the fix file you gave me and it acts the same.  but i noticed something that might help - once i switch it to tablet mode, it will switch fine, then i CTRL C the applet and then use xrandr to return my screen to normal - this we all know.  however, when i re-enable the applet, it will auto switch back to tablet mode - like it's stuck in that mode according to the applet.  does that make sense?

---

### Post by zoomy942 on 2009-09-27
> **Ayuthia said:**
> So, does the output keep showing 1 repeatedly or does it stop when the lid is back in the normal position?  I was able to test it out in Karmic and it ran over here. If the 1 stops repeating then it is getting stuck at the os.system command if it does not stop, then it is not reading the signal.

If you want to look at the install logs, you can go into /var/log/dpkg.log and see what was updated.  There was an intel driver change in the last one for me.  There was a python update around the 24th or earlier.


there was a python update, you are right, but it's been working since then.  however, maybe that intel driver update is what broke the applet?

as for your question, when i rotate it back to normal, it does not stop showing the 1.  it just keeps going, and going and going and going....

---

### Post by Favux on 2009-09-27
Hi zoomy942,

Ok, we know Magick 0.2-5 works in Intrepid, Jaunty, and Karmic for Ayuthia.

Your bios seems to support wmi and hp-wmi.

Magick is reading the state as 0 in landscape and 1 when rotated (portrait).  It does not see a change back to 0 when you rotate back to landscape.

Because Karmic is alpha 6:

-A problem with hp-wmi?

-A problem with python?

-A problem with the Intel video not updating xrandr somehow?  That doesn't seem likely.  The state change is due to the swivel hinge.
> once i switch it to tablet mode, it will switch fine, then i CTRL C the applet and then use xrandr to return my screen to normal - this we all know. however, when i re-enable the applet, it will auto switch back to tablet mode - like it's stuck in that mode according to the applet. does that make sense?
But Magick doesn't store the state.

This makes me suspect your swivel hinge is "broken".  It seems to return 0 after a reboot, but once used it keeps returning 1 and not resetting to 0.  Either that or it is returning a different signal to indicate rotation back to normal?  Not 0 like a TX?

Try doing this command in a terminal:
```
cat /sys/devices/platform/hp-wmi/tablet
```
like Ayuthia showed you.  In landscape after a fresh boot, after rotation to portrait, and then after rotation back to landscape.  What we want to see is 0,1,0.  Not 0,1,1.  Or maybe 0,1,? would be something we could work with.  If it keeps returning 1 after rotating back to landscape (normal) try rebooting and see if it now returns 0 again.

Of course this could all be BS.  Let's see what Ayuthia thinks.

Also find attached the debug version of Magick 0.2-5

---

### Post by zoomy942 on 2009-09-27
okay so whats going on.  the debug version you just gave me works fine?!  haha - that makes no sense to a rookie like me.  I'm going to reboot a handful of times and keep trying it.

also, i attached 2 shots for the 1,0 stuff you werre asking.  the first one labeled "before reboot" is me starting in landscape, rotating the screen and showing it stick to 1.

the other pic is after a reboot displaying it go back to zero.

stand by.  im gonna try this debug thing over a reboot, or a handful of reboots.h

---

### Post by zoomy942 on 2009-09-27
okay - so now i am noticing that it works better when run from the terminal then on bootup. 

also, when i run it from terminal, in landscape, it will rotate to tablet mode and back ONCE.  then i go from landscape to tablet again and back and it will get stuck in tablet - UNLESS - i close and reopen the applet and rotate the screens.  

lol- dont think my hinge is broke, but i can install windows to see if i really have to :).

seems like after one time of changing the state, it doesnt want to after that.  maybe a permissions thing?

---

### Post by zoomy942 on 2009-09-27
did the round of updates in the screenshot and it works much much better now.  does that make sense?

---

### Post by Favux on 2009-09-27
Hi zoomy942,

You've been busy!

Well I'm glad it's working better after the updates.  I don't really see anything in there that should help though.

Here's the chain as I understand it:

swivel hinge switch > bios > wmi > hp-wmi > creates:  /sys/devices/platform/hp-wmi/tablet  with inotify/pynotify thrown in as a helper but not mandatory.

So you can see what I was thinking.  The bios isn't going to be affected and is unlikely to suddenly fail.  Wmi and hp-wmi both could have been affected by the kernel update.

The python update could affect the script directly and/or pynotify.  Python is transitioning to 3.0 so it's possible that a newer version is finding what is now considered a syntax error.  I think the transition version is 2.6 for 3.0 and 2.7 for 3.1, or something like that.  I guess you could check Synaptic for the version.

But I think you've ruled that out with the cat commands.  It isn't switching state.  So I don't think it's Magick.

So I was wondering if the sudden change was due to gunk in the swivel hinge.  You said things were working after the update for 0.2-4 and only went wonky the next day when you tried 0.2-5.  That seemed to eliminate wmi and hp-wmi.  So what happened overnight was my question?  I don't have a visual picture of the switch or any idea how it works.  But I figured maybe gunk or a weak spring.

But who knows.  It's getting better, that's what's important.  Either the update or repeated swiveling clearing gunk out?  I have no idea.

---

### Post by Ayuthia on 2009-09-27
> **zoomy942 said:**
> there was a python update, you are right, but it's been working since then.  however, maybe that intel driver update is what broke the applet?

as for your question, when i rotate it back to normal, it does not stop showing the 1.  it just keeps going, and going and going and going....

Sorry for the late reply.  Today was indoor waterpark day with the kids.

The 1 showing repeatedly is possibly showing that read is not getting updated.  I am still trying to figure that one out.  I have tested out that file before with using inotifywait.  That command sits and waits until a change occurs with the file being tested.  I have switched the lid to tablet mode and the command sat there waiting for the change.  However, the file was accessed and changed in value.  I have found better results using /dev/input/eventX instead.  The downside to using that file is that the /dev folders need admin privileges for read access.

I am not fully convinced that my thought above is the issue because it seems that other people using it are not having the same problem.  

I am going to try to find some time Monday to see if I can add some debugging code to the application along with a flag to trigger the debug mode.  This way we are able to use that application as is, but if we need to debug it, we can just call the application in debug mode to get all the extra information.

zoomy942, by any chance have you made any modifications to the options (such as have the application call an additional program before or after the lid is rotated)?

---

### Post by zoomy942 on 2009-09-27
> **Favux said:**
> Hi zoomy942,

You've been busy!

Well I'm glad it's working better after the updates.  I don't really see anything in there that should help though.

Here's the chain as I understand it:

swivel hinge switch > bios > wmi > hp-wmi > creates:  /sys/devices/platform/hp-wmi/tablet  with inotify/pynotify thrown in as a helper but not mandatory.

So you can see what I was thinking.  The bios isn't going to be affected and is unlikely to suddenly fail.  Wmi and hp-wmi both could have been affected by the kernel update.

The python update could affect the script directly and/or pynotify.  Python is transitioning to 3.0 so it's possible that a newer version is finding what is now considered a syntax error.  I think the transition version is 2.6 for 3.0 and 2.7 for 3.1, or something like that.  I guess you could check Synaptic for the version.

But I think you've ruled that out with the cat commands.  It isn't switching state.  So I don't think it's Magick.

So I was wondering if the sudden change was due to gunk in the swivel hinge.  You said things were working after the update for 0.2-4 and only went wonky the next day when you tried 0.2-5.  That seemed to eliminate wmi and hp-wmi.  So what happened overnight was my question?  I don't have a visual picture of the switch or any idea how it works.  But I figured maybe gunk or a weak spring.

But who knows.  It's getting better, that's what's important.  Either the update or repeated swiveling clearing gunk out?  I have no idea.

yeah - im a busy bee with fun stuff like this.  i agree that maybe gunk might have been in there, but im the cleanest guy i know (but my wife is borderline OCD about cleaning) so im not too sure about that.  weak spring quite possibly, but it seemed flawless before, no matter what state the screen was in.  I'm wondering if something in a python update might have helped?  I have since flipped my screen a zillion times, gone in and out of standby and everything works okay.

gotta love running an Alpha huh?  i have a feeling this wont be the last time it stops working - but theres no way im going back to windows :)

seriously - you are awesome for helping me so much with this.  totally amazing of you.

---

### Post by zoomy942 on 2009-09-27
> **Ayuthia said:**
> Sorry for the late reply.  Today was indoor waterpark day with the kids.

The 1 showing repeatedly is possibly showing that read is not getting updated.  I am still trying to figure that one out.  I have tested out that file before with using inotifywait.  That command sits and waits until a change occurs with the file being tested.  I have switched the lid to tablet mode and the command sat there waiting for the change.  However, the file was accessed and changed in value.  I have found better results using /dev/input/eventX instead.  The downside to using that file is that the /dev folders need admin privileges for read access.

I am not fully convinced that my thought above is the issue because it seems that other people using it are not having the same problem.  

I am going to try to find some time Monday to see if I can add some debugging code to the application along with a flag to trigger the debug mode.  This way we are able to use that application as is, but if we need to debug it, we can just call the application in debug mode to get all the extra information.

zoomy942, by any chance have you made any modifications to the options (such as have the application call an additional program before or after the lid is rotated)?

so i read your first paragraph, and you are saying you have seen the repeated 1 return right?  like i was?  

i wish i had another 2710p or a person with one to test this like I am to see if its a device thing for our tablets instead of an overall program issue.  

No sir to your question.  i havent touched a thing.

---

### Post by Ayuthia on 2009-09-28
> **zoomy942 said:**
> so i read your first paragraph, and you are saying you have seen the repeated 1 return right?  like i was?  

i wish i had another 2710p or a person with one to test this like I am to see if its a device thing for our tablets instead of an overall program issue.  

No sir to your question.  i havent touched a thing.

I have not seen the repeated 1 before, but I have seen instances where the system does not seem to know that there was an update to that file.

I will still try to create a debug option for this so that we can see what is happening behind the scenes for other future issues.  For now, it seems that things are working but the debug option will be more helpful for future issues or if this comes back up.

I wish I knew if that was an alpha issue or if it is an obscure bug in the application.  Maybe this is a sign telling me that I should spend more time in Karmic than goofing off in Gentoo....

---

### Post by zoomy942 on 2009-09-28
lol - nice - gentoo is a great distro.

so i did a round of updates today and it seems to be working.  i'm going to test it more when i get home tonight.

---

### Post by jmcnaught on 2009-10-20
Thank you for this thread, it really helped me get up and running on my 2710p.

I'm using Karmic, and the only thing I had to fix was the stylus and eraser renaming for wacomcpl/xsetwacom.  For this I wrote a custom .fdi file, which I've pasted below.

The .fdi file also maps the stylus button to mouse button 3 (right click).  That way I didn't have to touch .xinitrc to make the button remapping permanent.

I've only tested this file under Karmic.  It probably works in Jaunty too.  It might also work for other tablet pc's.   I'm putting it here because it seems like the best place, and it's for public domain so anyone can use it for anything.

For Karmic put the file here: /usr/share/hal/fdi/policy/20thirdparty/10-linuxwacom.fdi

See also: [https://help.ubuntu.com/community/Wacom.fdi](https://help.ubuntu.com/community/Wacom.fdi)


cheers,
Jeremy

[html]<?xml version="1.0" encoding="UTF-8"?> <!-- -*- SGML -*- -->

<deviceinfo version="0.2">
    <device>
        <match key="info.capabilities" contains="serial">
            <match key="@info.parent:pnp.id" contains="WACf004">
                <append key="info.capabilities" type="strlist">input</append>
                <merge key="input.x11_driver" type="string">wacom</merge>
                <merge key="input.x11_options.Type" type="string">stylus</merge>
                <merge key="input.x11_options.ForceDevice" type="string">ISDV4</merge>
                <merge key="input.x11_options.Button2" type="string">3</merge>             
                <merge key="input.device" type="copy_property">serial.device</merge>
                <merge key="info.product" type="string">stylus</merge>               
                <append key="info.callouts.add" type="strlist">hal-setup-wacom</append>
                <append key="wacom.types" type="strlist">eraser</append>
            </match>
        </match>
    </device>
    <device>
        <match key="input.x11_options.Type" contains="eraser">
            <merge key="info.product" type="string">eraser</merge>
        </match>
    </device>
</deviceinfo>
[/html]

---

### Post by Andruk Tatum on 2010-01-25
So, I'm trying to get my 2710 working with the swivel hinge on Karmic. What do I have to do to get it working?

I should also add: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/512490](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/512490)

---

### Post by Favux on 2010-01-25
Hi Andruk Tatum,

Two separate issues.

Which video chipset do you have?:
```
lspci | grep VGA
```

Go to Method 4 on this [HOW TO]("http://ubuntuforums.org/showpost.php?p=6274392&postcount=1") and follow the links.

---

### Post by Andruk Tatum on 2010-01-26
Intel GM965, and xrandr seems to work fine.

And I've attached the errors I've encountered compiling the hp_wmi on my machine; as referenced in "Auto-magic Rotation HOW TO" in Method 4 in your link.

What include file am I missing, or what am I doing wrong?

Thanks for the help.

---

### Post by Favux on 2010-01-26
Hi Andruk Tatum,

Sure.  You have the Karmic kernel so I assume you're in Karmic.  The hp-wmi module is already in Karmic so there is no need to compile it, and wmi is in the Karmic kernel.  Just check lsmod and make sure hp-wmi is auto-loading.  If not add it to the modules file in /etc.  Just read through the [mini-HOW TO]("http://ubuntuforums.org/showpost.php?p=7738673&postcount=225") again and you'll see where you're going wrong.

Re: the video/keyboard problems.  Do you have Compiz enabled?

---

### Post by Andruk Tatum on 2010-01-26
Ah, thanks, I guess I didn't read it close enough.  I'll try it again tonight.

And I do have Compiz enabled, does that matter?

---

### Post by Favux on 2010-01-26
> And I do have Compiz enabled, does that matter? 
It might.  Loosing the keyboard is something ATI users have reported for a long time with the proprietary fglrx/Catlyst driver and Compiz.  They have to either turn Compiz off prior to rotation or just not use it.  Try disabling it and see if that fixes things.  If that isn't it there are a couple other possibilities for the keyboard problem too.

---

### Post by Andruk Tatum on 2010-01-27
Thanks for all the help; I managed to get the switch working.

For the reference for others:
For my HP 2710p tablet running Karmic, I simply had to add "hp-wmi" (without the quotes) to my /etc/modules file.  Then the file /sys/devices/platform/hp-wmi/tablet is "0" when the tablet is open in laptop mode, and "1" when the tablet is in tablet mode.

---

### Post by Andruk Tatum on 2010-02-08
I seem to be having the exact same issue as zoomy942 regarding the swivel hinge.  I don't think it's gunked up, but it does respond a bit randomly to the swivel rotating.  I will try to run the debug version of Magick, but both C programs I have created to monitor the signal (one program using inotify and one that simply continuously opens the file, reads it, and closes it over and over) have come up with similar results.

Interestingly, the inotify program doesn't ever fire off events when I rotate the tablet; it only fires off events when I read the signal with cat to determine what state it's in.  Does anybody know what could be going wrong?  And does anybody have anything they'd like me to try?

---

