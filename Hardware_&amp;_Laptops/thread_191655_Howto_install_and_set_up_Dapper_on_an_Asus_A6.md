---
title: "Howto install and set up Dapper on an Asus A6"
date: 2006-06-07
forum: Hardware &amp; Laptops
---

### Post by an.echte.trilingue on 2006-06-07
I bought an Asus A6VA recently and just finished installing Kubuntu Dapper on it.  This thread is intended to help others with this and similar laptops get everything working with issues that are specific to this hardware, but not to show people how to install/configure software not related to getting the computer itself working.  Please, if you have any questions or suggestions, please respond and let me know.  My job requires that I take extended trips rather frequently, but I will do my best to answer questions and update/edit the original post as I discover things or people post them.

There is a similar thread for Ubuntu 5.10 [here]("http://www.ubuntuforums.org/showthread.php?t=134300").

Since many Asus computers have a similar setup to this one, here is a quick list of what is under the hood so you know if this will apply to you:
[INDENT]ATI Radeon Mobility X700
Intel/Pro Wireless 2200 Gig
Intel Chipset on MoBo (I think)
Screen 1280x800 at 60 Hz
Intel Centrino[/INDENT]


_Dapper supports most everything out of the box_.  Follow this howto and you should pick up most everything else, too.


**Step 1:  Installation**

_First things first: _ If you are going to make this a dual boot system, I personally recommend that first back up your files, then do your partitioning from a liveCD that has qtparted (such as knoppix), then reinstall windows on the first hard drive.  This is however not really necessary; if you do not want to reinstall windows just see the [dual boot page in the wiki]("https://wiki.ubuntu.com/WindowsDualBootHowTo").  This is how I set up my hard drive:
[INDENT]HDA1:  15GB, NTFS (windows lives here)
HDA2:  10GB, EXT3 (ubuntu lives here)
HDA3:  1GB, SWAP (ubuntu's swap file)
HDA4:  45GB, FAT32 (to share files between the two OS's)[/INDENT]

Loading the CD:  I assume that you have already [downloaded kubuntu]("http://www.kubuntu.org/download.php"), [burned it to a CD]("https://wiki.ubuntu.com/BurningIsoHowto"), and [read the install wiki]("https://wiki.ubuntu.com/Installation") where it applies to you.  The next thing you need to do is boot from it.  Put the CD in the drive and reboot.  While the Asus screen is still up, either press the F2 key to select the boot device or ESC to edit the boot device order in the BIOS.  Of course, you want to boot from CD before the hard drive.  You will then get a GRUB menu asking you what to load.  **You want to load the safe graphics mode**, the regular one will leave you with a black screen.

_Install that baby!_ by simply clicking on the Install Icon on the desktop.  Answer the questions until you get to the part about partitioning.  Unless you do not want any other OS's on this computer, **do not **accept the default to wipe the drive; partition by hand.  If you did what I did, the partitioning is already done and you can skip to the step where you select mount points.  Mine looks like this:
[INDENT]/dev/hda1 mounts on /media/windows (do not format)
/dev/hda2 mounts on / (format it ext3)
/dev/hda3 is swap
/dev/hda4 mounts on /media/fileshare[/INDENT]
If you can you should connect to the internet before going on from here so that the installer can download updates and verify mirrors, but do not succumb to the the temptation to play with programs or surf the net while the installation is going on: you can do it but there is a good chance you will bugger your install (which only takes 10 min anyway).


**Step 2: Wireless**

At this juncture I should mention that new users need to read the wiki pages on [installing software]("https://wiki.ubuntu.com/InstallingSoftware") and [ adding repositories]("https://wiki.ubuntu.com/AddingRepositoriesHowto").  

Dapper detects the wireless card out of the box.  The only problem with the wireless that I have found so far is that there is no easy (aka GUI) way to connect to WPA encrypted networks.  Fix that with:

```
sudo aptitude install knetworkmanager
```

When you run this it will put an icon in your system tray that you can use to connect to pretty much any network.


**Step 3: Kernel**

You probably want the i686 kernel.
```
sudo aptitude install linux-686
```


**Step 4:  Video**

I am sure this is the step you have all been waiting for.  The good news is, it mostly works.  The bad news is that compositing is broken.  I don't know how to fix it without using the [GDM hack]("http://www.ubuntuforums.org/showthread.php?t=131253"), but that would require using GDM instead of KDM (someone please let me know if this is possible with KDM) and if you do that you will lose some important things in the KDE environment (like the ability to shut down from the kmenu).

_Drivers:_ are very easy.  First, make sure that you have the [ restricted repository]("https://wiki.ubuntu.com/AddingRepositoriesHowto") selected.  Then, simply:
```
sudo aptitude install linux-restricted-modules-686 
sudo aptitude install xorg-driver-fglrx
```

_xorg.conf_ is a bear to get set up on this computer.  So, I will just give you mine:

**[INDENT][ATTACH]10876[/ATTACH][/INDENT]**

To use this file, do this:
```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo cp /path/to/file/xorg.conf.txt /etc/X11/xorg.conf
```

Save  everything else you were working on, and then restart X with CTRL+ALT+BACKSPACE.

This will do the following things for you:  set the xorg driver to the fglrx one that you downloaded, set x's resolution to 1280x800@60, set your monitor resolution to that as well, and enables compositing (which is broken on this driver but it might work on the next update).

_Warning #1_ I have a German keyboard.  You probably want to edit the keyboard section to look like the one in your backup copy of xorg.conf before saving.

_Warning #2_ If for some reason this does not work for you and you get a blank screen, then hit CTRL+ALT+F2 to go to another console, login in, and type this:
```
sudo mv /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
sudo init 6
```
If you have a hard lockup and can't switch to a virtual terminal, reset the computer and boot into the recovery console and do the same thing.

_Tip:_  The default fonts look like crap on this screen.  [This post]("http://www.ubuntuforums.org/showthread.php?t=4456") (originally written for Warty way back in the day but still valid) shows you how to get really smooth looking fonts.


**Step 5:  Fix the boot**

I do not know if this was unique to me or if is is a hiccough with this computer, so I will post it anyway.  After installing kubuntu and booting for the first time, i found that the fsck hangs on the MBR, reporting that it does not match its backup.  The solution is this:
```
kdesu kate /etc/fstab
```
find this line:
```
/dev/hda1       /media/windows  ntfs    defaults,utf8,umask=007,gid=46 0       1
```
and change the last 1 to a zero.


**Step 6:  Multimedia and Application Shortcut Keys**(Thank you ltmon)

For most of the keys, [this page]("https://wiki.ubuntu.com/KDEMultimediaKeys") in the wiki details how to set them up.  To save others the tedium of using xev my .Xmodmap is here:[ATTACH]10889[/ATTACH].  Just rename it and put it where the wiki says to.

This is what the keys will show up as:
[INDENT]F13: Less than/ Greater than / pipe symbols (for some reason this button does not work on the german keyboard: you should certainly delete this if you are using another layout)
F14: Skip Back
F15: IM
F16: Skip Forward
F17: FN+F10 (mute)
F18: Play
F19: Stop
F20: FN+F11 (vol down)
F21: FN+F12 (vol up)
F22: Browser
F23: Email
[/INDENT]
Tip:  The DCOP line for increase volume is "dcop kmix Mixer0 increaseVolume 0" and decrease is "dcop kmix Mixer0 decreaseVolume 0"
Tip: The easiest way to change the multimedia button settings is to change the
shortcuts in the media player itself.  In Kaffeine, for example, go to Settings-- Configure Shortcuts.

Bear in mind that this is for the German keyboard and yours might be different.  Right now you have to repeat this process for every user.  I will look into making changes to the system default and edit this page then.


**Step 7:  Things I still have to look into:**

[INDENT]The function keys for bringing the Wifi up and down and turning the Touchpad on and off seem to work, but the scripts that they call do not.  The return an error: Can't access shared memory area. SHMConfig disabled?

The fonts still look horrible in some applications.

I have not tested the mic.

The infrared network thing does not seem to work.

Camera:  My particular example does not have one and [I have read that it creates issues]("http://www.ubuntuforums.org/showthread.php?t=73578").  If you get it working please let me know how so that I can post it here.

I have not tested it with a second monitor (I intend to edit this to show how to set up a dual head config if possible, but my other monitor is in storage and I will not be able to do this until August or so.  I would appreciate help here...)

I have not tested the S-video jack (I have no TV so if somebody else can look into this I would appreciate it very much)
[/INDENT]

**Step 8: What doesn't work:**

[INDENT]_Sleep/Hibernate:_ I have done everything I know how to.  I changed settings in grub.  I tried a million different things in xorg.  I compiled a new kernel with support for suspend2 (although I may have messed this up).  I can't get it to work.  Anybody have any ideas?[/INDENT]


Well, that is all I have for now.  I will edit this as I get my own system up.

---

### Post by ltmon on 2006-06-07
Good post.  I'm getting an M6VA (aka Z70VA in the US I think) tonight.  It has very similar hardware, so your setup will probably help.

Your volume,  multimedia and wifi keys will provide either an ACPI event or an X keycode.  Have a look at [https://wiki.ubuntu.com/KDEMultimediaKeys](https://wiki.ubuntu.com/KDEMultimediaKeys) (for x keycodes) or the scripts in /etc/acpi for ACPI events.

---

### Post by an.echte.trilingue on 2006-06-08
Thank you for the tip.  You saved me a lot of time.

---

### Post by ltmon on 2006-06-08
Well I didn't get my new laptop last night, the delivery is late :mad: so I can't confirm any of this or help as yet.

My previous scourings of blogs and forums have lead me to believe that suspend2 is the only current way of suspending the m6/z70/a6 and other newer Asus laptops with ATi cards.

I was going to follow the guide at [http://ubuntuforums.org/showthread.php?t=75443](http://ubuntuforums.org/showthread.php?t=75443) or this more detailed version at [http://wiki.suspend2.net/DistroAndHardwareSetup/Ubuntu_Breezy_Badger](http://wiki.suspend2.net/DistroAndHardwareSetup/Ubuntu_Breezy_Badger) (both for Breezy, but probably easily replicated for Dapper) to see if I could get it working.

L.

---

### Post by an.echte.trilingue on 2006-06-09
Yeah.  I really don't want to use suspend2.  As well as it may work, I would like people with no experience to be able to follow this guide and get their computer working as well under Kubuntu as the OEM Windows installation works, and rebuilding the kernel is probably not something that "anyone" will be willing to put up with.  Suspend and Hibernate are probably important enough to be show stoppers for some potential users.  I found some other options on google that I will try tonight.  

That being said, I built another kernel last night (haven't had time to try it yet), and if that works I will probably post another guide and link to it from this one for those who are willing to take the time.

At any rate, this is probably a temporary problem as kernel 2.6.18 will have suspend2 integrated into it.  I just wonder when it will make its way into Ubuntu... how fast is kernel development and will kernels with number differences that large be backported to Dapper? I have no idea what the conventions are here...

---

### Post by ltmon on 2006-06-11
[QUOTE=an.echte.trilingue]
At any rate, this is probably a temporary problem as kernel 2.6.18 will have suspend2 integrated into it.  I just wonder when it will make its way into Ubuntu... how fast is kernel development and will kernels with number differences that large be backported to Dapper? I have no idea what the conventions are here...[/QUOTE]

I very much doubt there will be an official update to 2.6.18, but it will probably be available as a backport through the ubuntu backports project ([http://backports.ubuntuforums.org](http://backports.ubuntuforums.org)) when it is uploaded to Dapper + 1 (Edgy Eft).

---

### Post by Cylence on 2006-06-18
Hi, thank you for your howto, you saved me a lot of time!

Your way of installing Ati drivers didn't work for me. I managed following the instructions in this post: [http://ubuntuforums.org/showthread.php?t=191944&highlight=ati+drivers+work+aticonfig]("http://ubuntuforums.org/showthread.php?t=191944&highlight=ati+drivers+work+aticonfig").

---

### Post by Cisto on 2006-06-21
Thanks for the xmodmap file, i was getting crazy in binding keys...

I also had to put in /etc/modprobe.d/alsa-base "options snd_hda_intel model=z71v posfix=1" to get headphone jack working.

In order to avoiding the stupid messege saying "lcd display changed: on/off" here and there I edited kmiload.desktop disabling kmilod autoload and load on demand.

Finally, i had to set the --terminate options for kdm logout because otherwise ati fglrx drivers crashed if I chase to halt the computer in kde menù.

---

### Post by Cylence on 2006-06-22
[QUOTE=Cisto]Thanks for the xmodmap file, i was getting crazy in binding keys...[/QUOTE]

Me too. Eventually this and other issues made me switch to Ubuntu (Gnome), where most multimedia keys are working out of the box. By default (Italian keyboard) they are mapped as follows:

Fn+F1 = nothing
Fn+F2 = nothing
Fn+F5 to F7 = screen brightness down/up/off
Fn+F8 = nothing
Fn+F10 to F12 = PCM volume mute/down/up *
Fn+Ins = Num Lock
Fn+Canc = Scroll Lock

* headphones volume after editing /etc/modprobe.d/alsa-base

Keys on top (left to right):

1 = lock screen
2 = mail reader
3 = browser
4 = nothing
5 = shutdown dialog

Keys which are mapped to "nothing" give no output in XEV. Audio DJ controls do, so I had no problems setting them up using System/Preferences/Keyboard Shortcuts.

[QUOTE=Cisto]I also had to put in /etc/modprobe.d/alsa-base "options snd_hda_intel model=z71v posfix=1" to get headphone jack working.[/QUOTE]

There's a typo which prevents the sound module from working. In /etc/modprobe.d/alsa-base you should write "options snd-hda-intel model=z71v position_fix=1", as Cisto himself explains in [this post]("http://www.ubuntuforums.org/showthread.php?t=201657").

[QUOTE=Cisto]In order to avoiding the stupid messege saying "lcd display changed: on/off" here and there I edited kmiload.desktop disabling kmilod autoload and load on demand.

Finally, i had to set the --terminate options for kdm logout because otherwise ati fglrx drivers crashed if I chase to halt the computer in kde menù.[/QUOTE]

I had no such problems in Gnome.

---

### Post by Cisto on 2006-06-23
[QUOTE=Cisto]Thanks for the xmodmap file, i was getting crazy in binding keys...

I also had to put in /etc/modprobe.d/alsa-base "options snd_hda_intel model=z71v posfix=1" to get headphone jack working.

In order to avoiding the stupid messege saying "lcd display changed: on/off" here and there I edited kmiload.desktop disabling kmilod autoload and load on demand.

Finally, i had to set the --terminate options for kdm logout because otherwise ati fglrx drivers crashed if I chase to halt the computer in kde menù.[/QUOTE]

Ok, I want tell you other 2 tips I've discovered:

I've found another way to avoid the stupid "lcd display changed :on/off" messege, allowing a full use of kded and kmilod. I understood that the messege appeared when the /proc/acpi/asus/lcd file was written or read by acpid. Setting that file to -rw completly solves the problem. To get this automatically done on boot, follow those simple steps:

[PHP]sudoedit /etc/rc.local[/PHP]

than put in the file

[PHP]/bin/chmod 222 /proc/acpi/asus/lcd
exit 0[/PHP]

Obviously, in /usr/share/services/kded/kmilod.desktop you have to have

[PHP]X-KDE-Kded-autoload=true
X-KDE-Kded-load-on-demand=true[/PHP]

I've found a way to get xmodmap autoload on KDE start. I have an italian keyboard, so my .Xmodmap file (created in my home directory) is configured in this way:

[PHP]keycode 200 = F13
keycode 241 = F14
keycode 143 = F15
keycode 163 = XF86AudioMute
keycode 209 = XF86AudioLowerVolume
keycode 136 = XF86AudioRaiseVolume[/PHP]

F14 and F15 are configured in the kcontrol to start the web browser and the email client. The audio controls are binded by XF86 signals (and yes, osd works!).

To have this xmodmap file directly autoloaded on KDE startup:

[PHP]vim .kde/env/xmodmap.sh[/PHP]

put in:

[PHP]#!/bin/bash (-)
xmodmap ~/.Xmodmap[/PHP]

Now we want xmodmap to autostart, so:

[PHP]vim .kde/Autostart/xmodmap.desktop[/PHP]

write in:

[PHP][Desktop Entry]
Comment=
Comment[it]=
Encoding=UTF-8
Exec=sh .kde/env/xmodmap.sh
GenericName=
GenericName[it]=
Icon=
MimeType=
Name=xmodmap
Name[it]=xmodmap
Path=
StartupNotify=false
Terminal=false
TerminalOptions=
Type=Application
X-DCOP-ServiceType=none
X-KDE-SubstituteUID=false
X-KDE-Username=
[/PHP]

On restart, xmodmap will auto-load your .Xmodmap file.

---

### Post by norman_h on 2006-08-12
I have an Asus M6R and it looks *very* similar to the A6.

I have managed to get suspend to disk, battery/ac monitor and most other [COLOR="Red"]acpi options working[/COLOR].  I haven't managed to get suspend to RAM working.  I haven't tested the multimedia side buttons yet as they are nothing but a pain when they are working (easy to bump and trigger something thats not wanted).

I needed to do a kernel recompile with a patch to the kernels [COLOR="Red"]drivers/acpi/ec.c[/COLOR] file.  I used the ubuntu repository kernel source (as it has some ubuntu specific already patches applied to it).  The ASUS bug is a known bug and is documented at [bugme.](http://bugme.osdl.org/show_bug.cgi?id=6111)  The patch will make its way into a full kernel release sooner or later.


```

 drivers/acpi/ec.c |   16 ++++++----------
 1 files changed, 6 insertions(+), 10 deletions(-)

diff --git a/drivers/acpi/ec.c b/drivers/acpi/ec.c
index f339bd4..de95a09 100644
--- a/drivers/acpi/ec.c
+++ b/drivers/acpi/ec.c
@@ -989,7 +989,6 @@ static int acpi_ec_poll_add(struct acpi_
 	int result = 0;
 	acpi_status status = AE_OK;
 	union acpi_ec *ec = NULL;
-	unsigned long uid;
 
 	ACPI_FUNCTION_TRACE("acpi_ec_add");
 
@@ -1012,10 +1011,9 @@ static int acpi_ec_poll_add(struct acpi_
 	acpi_evaluate_integer(ec->common.handle, "_GLK", NULL,
 			      &ec->common.global_lock);
 
-	/* If our UID matches the UID for the ECDT-enumerated EC,
-	   we now have the *real* EC info, so kill the makeshift one. */
-	acpi_evaluate_integer(ec->common.handle, "_UID", NULL, &uid);
-	if (ec_ecdt && ec_ecdt->common.uid == uid) {
+	/* XXX we doesn't test uids, because on some boxes ecdt uid = 0, see:
+	   http://bugzilla.kernel.org/show_bug.cgi?id=6111 */
+	if (ec_ecdt) {
 		acpi_remove_address_space_handler(ACPI_ROOT_OBJECT,
 						  ACPI_ADR_SPACE_EC,
 						  &acpi_ec_space_handler);
@@ -1059,7 +1057,6 @@ static int acpi_ec_intr_add(struct acpi_
 	int result = 0;
 	acpi_status status = AE_OK;
 	union acpi_ec *ec = NULL;
-	unsigned long uid;
 
 	ACPI_FUNCTION_TRACE("acpi_ec_add");
 
@@ -1085,10 +1082,9 @@ static int acpi_ec_intr_add(struct acpi_
 	acpi_evaluate_integer(ec->common.handle, "_GLK", NULL,
 			      &ec->common.global_lock);
 
-	/* If our UID matches the UID for the ECDT-enumerated EC,
-	   we now have the *real* EC info, so kill the makeshift one. */
-	acpi_evaluate_integer(ec->common.handle, "_UID", NULL, &uid);
-	if (ec_ecdt && ec_ecdt->common.uid == uid) {
+	/* XXX we doesn't test uids, because on some boxes ecdt uid = 0, see:
+	   http://bugzilla.kernel.org/show_bug.cgi?id=6111 */
+	if (ec_ecdt) {
 		acpi_remove_address_space_handler(ACPI_ROOT_OBJECT,
 						  ACPI_ADR_SPACE_EC,
 						  &acpi_ec_space_handler);


```

---

### Post by simogol on 2007-01-09
Hi everybody,
I tried to launch both ubuntu and kubuntu 6.10 in safe video mode on my a6va but screen looks dead. it actually shuts off. 
i can hear sounds and everything else seems to work, all but screen...

I also tried to boot using option vga=771, but nothing happened...

Any hint?

Ciao,
Simone.

---

### Post by ssm on 2007-01-09
> **norman_h said:**
> I have an Asus M6R and it looks *very* similar to the A6.

I have managed to get suspend to disk, battery/ac monitor and most other [COLOR="Red"]acpi options working[/COLOR].  I haven't managed to get suspend to RAM working.  I haven't tested the multimedia side buttons yet as they are nothing but a pain when they are working (easy to bump and trigger something thats not wanted).

I needed to do a kernel recompile with a patch to the kernels [COLOR="Red"]drivers/acpi/ec.c[/COLOR] file.  I used the ubuntu repository kernel source (as it has some ubuntu specific already patches applied to it).  The ASUS bug is a known bug and is documented at [bugme.](http://bugme.osdl.org/show_bug.cgi?id=6111)  The patch will make its way into a full kernel release sooner or later.
[www.unreadedpost.com](www.unreadedpost.com)

```

 drivers/acpi/ec.c |   16 ++++++----------
 1 files changed, 6 insertions(+), 10 deletions(-)

diff --git a/drivers/acpi/ec.c b/drivers/acpi/ec.c
index f339bd4..de95a09 100644
--- a/drivers/acpi/ec.c
+++ b/drivers/acpi/ec.c
@@ -989,7 +989,6 @@ static int acpi_ec_poll_add(struct acpi_
 	int result = 0;
 	acpi_status status = AE_OK;
 	union acpi_ec *ec = NULL;
-	unsigned long uid;
 
 	ACPI_FUNCTION_TRACE("acpi_ec_add");
 
@@ -1012,10 +1011,9 @@ static int acpi_ec_poll_add(struct acpi_
 	acpi_evaluate_integer(ec->common.handle, "_GLK", NULL,
 			      &ec->common.global_lock);
 
-	/* If our UID matches the UID for the ECDT-enumerated EC,
-	   we now have the *real* EC info, so kill the makeshift one. */
-	acpi_evaluate_integer(ec->common.handle, "_UID", NULL, &uid);
-	if (ec_ecdt && ec_ecdt->common.uid == uid) {
+	/* XXX we doesn't test uids, because on some boxes ecdt uid = 0, see:
+	   http://bugzilla.kernel.org/show_bug.cgi?id=6111 */
+	if (ec_ecdt) {
 		acpi_remove_address_space_handler(ACPI_ROOT_OBJECT,
 						  ACPI_ADR_SPACE_EC,
 						  &acpi_ec_space_handler);
@@ -1059,7 +1057,6 @@ static int acpi_ec_intr_add(struct acpi_
 	int result = 0;
 	acpi_status status = AE_OK;
 	union acpi_ec *ec = NULL;
-	unsigned long uid;
 
 	ACPI_FUNCTION_TRACE("acpi_ec_add");
 
@@ -1085,10 +1082,9 @@ static int acpi_ec_intr_add(struct acpi_
 	acpi_evaluate_integer(ec->common.handle, "_GLK", NULL,
 			      &ec->common.global_lock);
 
-	/* If our UID matches the UID for the ECDT-enumerated EC,
-	   we now have the *real* EC info, so kill the makeshift one. */
-	acpi_evaluate_integer(ec->common.handle, "_UID", NULL, &uid);
-	if (ec_ecdt && ec_ecdt->common.uid == uid) {
+	/* XXX we doesn't test uids, because on some boxes ecdt uid = 0, see:
+	   http://bugzilla.kernel.org/show_bug.cgi?id=6111 */
+	if (ec_ecdt) {
 		acpi_remove_address_space_handler(ACPI_ROOT_OBJECT,
 						  ACPI_ADR_SPACE_EC,
 						  &acpi_ec_space_handler);


```
[www.unreadedpost.com](www.unreadedpost.com) look I dont now.

---

### Post by metcalfe on 2008-01-12
just bumping the thread because adding "options snd_hda_intel model=z71v posfix=1"

in /etc/modprobe.d/alsa-base  just fixed my headphone problem. 
The headphone hardware switch used to work fine: when i plugged the headphones, the speakers stopped playing but i got no sound from the headphone jack. Now, everything is peachy :)


I am using ubuntu 7.10 gutsy on an ASUS A6VM - Q008H which is apparently a rare model xD


thanks, and i hope this helps someone :popcorn:

---

