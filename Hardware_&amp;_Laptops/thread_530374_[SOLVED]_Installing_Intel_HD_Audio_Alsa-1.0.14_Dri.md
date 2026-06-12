---
title: "[SOLVED] Installing Intel HD Audio Alsa-1.0.14 Drivers."
date: 2007-08-20
forum: Hardware &amp; Laptops
---

### Post by linux23dragon on 2007-08-20
**[SIZE=5]_Debugging Intel HDA Audio (for the Intel HDA Sound cards)_[/SIZE]**

**UPDATE 28-11-07** :- [I]The Reason I've marked this thread solved is because most of the time you can get the sound card working by playing around with the Sound driver
                                 setup.  But I don't think its going to get much better untill Ubuntu uses Alsa-1.0.15 (or better).   Most of the solutions can be found in the Wiki
                                 links (provided in this post) or by installing  linux-backports-modules-*.   But some of you may need to play around with system software (esound,
                                 libasound and mixer settings), or system configuration  ( /etc/modprobe.d/alsa-base).  Search for the Notebook or desktop of choice to find the solution that best
                                 suites you, and the WiKi information should help too.[/I]

**UPDATE: 27-11-07** :- I've marked this thread SOLVED.  



The Intel HDA  drivers are not working correctly for lots of people.   So I've made this list of other peoples ideas (that worked using Gusty), for your reference to try out.
If you have already compiled or tinkered with the kernel (or Alsa drivers) then use the Synaptic PM to reinstall the kernel and reboot, to be on the safe side.
Now try only one of these hints, at a time:

[list]Check your volume control levels.   Also remember that you may need to add more sound devices in your  Volume Control Preferences.
[/list]

[list]If you don't have any sound output or you can't seem to get any device driver information (using the "cat /proc/asound/cards" command) .  Remove ~/.asoundrc
and ~/.asoundrc.asoundconf.  Logout and log back in.  And make sure your sound card is not muted. 
[/list]

[LIST]Install Ubuntu kernel back ports (linux-backports-modules-* ). Then reboot. ```
sudo apt-get install linux-backports-modules-generic
```
[/LIST]

[LIST]If the sound already works, but you want more input/outputs to work.  Try to use different model options listed in the [_*[COLOR="Blue"]Alsa wiki[/COLOR]*_]("http://alsa.opensrc.org/index.php/Hda#cooliris").   
[/LIST]

[LIST]If you have a Dell Notebook or Desktop system, then this [*_[COLOR="Blue"]Dell WiKi support[/COLOR]_*]("http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Issues/Audio_not_working_properly") (even if it is support for Ubuntu-7.04) might be worth a try.  Other users that don't
have a Dell system might have some luck with this fix as well.  If that solution it did not work out for you, then revert the changes (that had been instructed in the Dell Wiki page). 
[/LIST]

[LIST]See [*[COLOR="Blue"]Gutsy_Intel_HD_Audio_Controller[/COLOR]*]("https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller") howto, for even more methods for your hardware setup.
[/LIST]
If all of the above hints fail, then continue on.  Its just a matter of playing around, so post your findings if you have the Alsa system working (or not) for others to see.
[COLOR="Brown"]If you have your sound card working.  Please use the *'Ubuntu Device database'* tool found in the *"Device Manager"* (System -> Preferences -> Hardware Information), to
help the Ubuntu developers fix the issue.[/COLOR]


**_Final Configuration_**

Install a new Udev rules file (helps to create the audio device nodes and run the restore script)

[INDENT]```

sudo -i
```[/INDENT]
[INDENT]```

touch /etc/asound.state
```[/INDENT]
[INDENT]```

alsactl store
```[/INDENT]
[INDENT]```

cat > /etc/udev/rules.d/40-alsa.rules << "EOF"
# /etc/udev/rules.d/40-alsa.rules

# When a sound device is detected, restore the volume settings
KERNEL=="controlC[0-9]*", ACTION=="add", RUN+="/usr/sbin/alsactl restore %n"
EOF
```[/INDENT]
[INDENT]```

chmod -v 644 /etc/udev/rules.d/40-alsa.rules
```[/INDENT]



Run the command "speaker-test" in a terminal to test the sound, even after rebooting.
Use Ctrl + c to exit the test.


If you find that you have no sound or if Alsa no longer detects your sound card .  Then you will need to reinstall all the kernel $(uname -r) modules, linux-sound base
and alsa-base.  The system should then be restored.


CHANGELOG:
19-10-07  Added Gusty support and more notes on the Alsa driver
20-10-07  Added Ubuntu WiKi information and removed alsa-utils from the Uninstall section (An old 7.04 idea)
20-10-07  Added a second driver install method that is more disruptive than the original method.
20-10-07  Added [http://ubuntuforums.org/showpost.php?p=3475485&postcount=235](http://ubuntuforums.org/showpost.php?p=3475485&postcount=235).  Thanks goes to [Gunner_Sr]("http://ubuntuforums.org/member.php?u=401905")
21-10-07  This hint should now be easer to follow
21-10-07  Added a Dell support link, and changed the model=dell-laptop to model-ref.  Added a install path in Alsa driver method 2.
21-10-07  Added more hints.  Thanks goes to [dawdler]("http://ubuntuforums.org/member.php?u=169945")
21-10-07  Added  the Ubuntu Device database tool information.  Thanks goes to [kyfho23]("http://ubuntuforums.org/member.php?u=82191") for the info.
22-10-07  Fixed the 'conflicting driver' command to include "sudo"
22-10-07  Removed Alsa system installation instructions.

---

### Post by linux4africa on 2007-08-21
I had to force install a few of the packages with:

dpkg --force-overwrite --install

alsa-base is still an older version. I'll reboot and see what happens. (Samsung R70 laptop).

---

### Post by linux23dragon on 2007-08-25
UPDATE: More testing support has been included

---

### Post by linux23dragon on 2007-08-29
UPDATE:

Lots of hints and added kernel changes "2.6.20-16-lowlatency"

---

### Post by linux23dragon on 2007-10-18
UPDATE : Alsa-1.0.15 is now out and has lots of bug fixes and improvements with the Intel HDA sound card Drivers.

I think the microphone issues are fixed too :)

---

### Post by Swarms on 2007-10-18
Oi mate, now sitting with a Gutsy laptop, with a ICH8 family card. When will you update your guide for Gutsy? 

Thanks a lot for your work so far!

---

### Post by linux23dragon on 2007-10-18
> **Swarms said:**
> Oi mate, now sitting with a Gutsy laptop, with a ICH8 family card. When will you update your guide for Gutsy? 

Thanks a lot for your work so far!

Later on today.  I'm in the process of installing Gusty now :)

---

### Post by amvella on 2007-10-18
waiting for gutsy tutorial... cant figure out how to install this sound driver

---

### Post by freetonik on 2007-10-18
> **amvella said:**
> waiting for gutsy tutorial... cant figure out how to install this sound driver

me too...
my sound works good, but mic - doesn't :(

---

### Post by DRAGONPOWER on 2007-10-19
hello, im on gusty running 64-bit on a laptop hp dv9000/9500.

ive tries just about every method to get audio working but it just doesn't.

there's a button panel in front of the keyboard with these laptops and the volume button is always orange, when i press the button a volume overlay appears in my screen, and the volume up and down ones work. Problem is the button just stays orange instead of changinc colour to blue when volume is supposedly working.

help is needed and very much appreciated solving this issue.

---

### Post by linux23dragon on 2007-10-19
Gusty support is here :-)

Please test this out and report how this works for you.

---

### Post by Swarms on 2007-10-19
On the last copy paste command I get this output
bear@bear-laptop:~$ sudo gedit /etc/modprobe.d/alsa-base
bear@bear-laptop:~$ sudo update-modules
bear@bear-laptop:~$ sudo -i &&
> touch /etc/asound.state &&
> alsactl store &&
> cat > /etc/udev/rules.d/40-alsa.rules << "EOF"
> # /etc/udev/rules.d/40-alsa.rules
> 
> # When a sound device is detected, restore the volume settings
> KERNEL=="controlC[0-9]*", ACTION=="add", RUN+="/usr/sbin/alsactl restore %n"
> EOF
root@bear-laptop:~# chmod -v 644 /etc/udev/rules.d/40-alsa.rules
chmod: cannot access `/etc/udev/rules.d/40-alsa.rules': No such file or directory
failed to change mode of `/etc/udev/rules.d/40-alsa.rules' to 4040 (--Sr-----)
root@bear-laptop:~#

---

### Post by linux23dragon on 2007-10-19
> **Swarms said:**
> On the last copy paste command I get this output
bear@bear-laptop:~$ sudo gedit /etc/modprobe.d/alsa-base
bear@bear-laptop:~$ sudo update-modules
bear@bear-laptop:~$ sudo -i &&
> touch /etc/asound.state &&
> alsactl store &&
> cat > /etc/udev/rules.d/40-alsa.rules << "EOF"
> # /etc/udev/rules.d/40-alsa.rules
> 
> # When a sound device is detected, restore the volume settings
> KERNEL=="controlC[0-9]*", ACTION=="add", RUN+="/usr/sbin/alsactl restore %n"
> EOF
root@bear-laptop:~# chmod -v 644 /etc/udev/rules.d/40-alsa.rules
chmod: cannot access `/etc/udev/rules.d/40-alsa.rules': No such file or directory
failed to change mode of `/etc/udev/rules.d/40-alsa.rules' to 4040 (--Sr-----)
root@bear-laptop:~#

Thanks for the report.

Try it set by step like this 

```

sudo -i
```
```

touch /etc/asound.state
```
```

alsactl store
```
```

cat > /etc/udev/rules.d/40-alsa.rules << "EOF"
# /etc/udev/rules.d/40-alsa.rules

# When a sound device is detected, restore the volume settings
KERNEL=="controlC[0-9]*", ACTION=="add", RUN+="/usr/sbin/alsactl restore %n"
EOF
```
```

chmod -v 644 /etc/udev/rules.d/40-alsa.rules
```

EDIT: It looks like I need to to use "sudo" for the last "chmod" command ;-)
EDIT2: I've just added this to the first post (I had tested them out too)

---

### Post by Swarms on 2007-10-19
Thanks a lot mate, an easy way to install these HDA soundcards is a thing we all want. ;)

Ran a full reinstall of Gutsy, trying it again now.

---

### Post by Swarms on 2007-10-19
Btw. I can't uninstall alsa-utils without Synaptic requiring me to uninstall gdm, fast user switch applet, ubuntu desktop and ubuntu minimal, what to do?

---

### Post by linux23dragon on 2007-10-19
> **Swarms said:**
> Btw. I can't uninstall alsa-utils without Synaptic requiring me to uninstall gdm, fast user switch applet, ubuntu desktop and ubuntu minimal, what to do?

Thanks for that report.  Keep the alsa-utils.  It should not effect the system.

I'll update my post now.

---

### Post by Swarms on 2007-10-19
Ok I kept it, did all what the guide said, and rebooted the system. Now the system boots with errors saying it's not able to launch the Gnome Settings Manager.

I know you got fixes, but will try to boot with some other models specified in the modprobe part.

---

### Post by linux23dragon on 2007-10-19
> **Swarms said:**
> Ok I kept it, did all what the guide said, and rebooted the system. Now the system boots with errors saying it's not able to launch the Gnome Settings Manager.

I know you got fixes, but will try to boot with some other models specified in the modprobe part.

You should not have the errors at all, but we can fix the issues.

Can you please check to see if you have* libgnome-window-settings1* (using Synaptic package manager) installed?


By the way, we can reinstall the default Gusty Alsa software without the need to reinstall Ubuntu.  That too should fix the new errors.  Perhaps we just need to install only the Alsa driver?

What system are you using? A Dell Notebook?


EDIT:

You can remove the new alsa-1.0.15 software by using Synaptic package manager.  And then reinstall the default Alsa sound system.

By default gusty only installs:

libasound2
libao2
linux-sound-base
alsa-utils
alsa-base

And to recover the kernel-driver, you only need to reinstall the kernel itself.

---

### Post by Swarms on 2007-10-19
It was becasue I read on that wiki page that an easy fix would be not to specify any model at all, so tried it and got all the errors, then I tried to add model=laptop and I got no errors except it can't find the soundcard anymore. Tried with the 2 jack model one too without any luck.

And its a Zepto Laptop [www.zepto.com](www.zepto.com)

And yeah I can recover easily, but more interested in fixing it. ;)

---

### Post by amvella on 2007-10-19
> **DRAGONPOWER said:**
> hello, im on gusty running 64-bit on a laptop hp dv9000/9500.

ive tries just about every method to get audio working but it just doesn't.

there's a button panel in front of the keyboard with these laptops and the volume button is always orange, when i press the button a volume overlay appears in my screen, and the volume up and down ones work. Problem is the button just stays orange instead of changinc colour to blue when volume is supposedly working.

help is needed and very much appreciated solving this issue.

i have hp dv9500t my buttons are blue..just being blue doesnt mean that its working... I have it blue and the sound is not working.

---

### Post by amvella on 2007-10-19
hey i got these error message while installing alsa-lib

```

grep: /var/tmp/ikqnZUJJbbQlTgXSaZHSR/newfile: No such file or directory

Copying files to the temporary directory...OK

Striping ELF binaries and libraries...OK

Compressing man pages...OK

Building file list...OK

Building Debian package...OK

Installing Debian package... FAILED!

*** Failed to install the package

Do you want to see the log file?  [y]: 

```

this is the log file

```

(Reading database ... 102403 files and directories currently installed.)
Unpacking alsa-lib (from .../alsa-lib_1.0.15-1_i386.deb) ...
dpkg: error processing /home/appu/alsa-lib-1.0.15/alsa-lib_1.0.15-1_i386.deb (--install):
 trying to overwrite `/usr/share/alsa/cards/ES1968.conf', which is also in package libasound2
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /home/appu/alsa-lib-1.0.15/alsa-lib_1.0.15-1_i386.deb
/var/tmp/ikqnZUJJbbQlTgXSaZHSR/dpkginstall.log (END) 

```

After continuing on with all the rest of the install.. and rebooting.. i got no sound.. my detected sound cards are not detected anymore..
What should i do now? Help Pls...

---

### Post by linux23dragon on 2007-10-19
I've updated to post to include a second driver install method that might be more disruptive to the kernel, but may have a better chance of working for some people.

---

### Post by linux23dragon on 2007-10-19
> **amvella said:**
> hey i got these error message while installing alsa-lib

```

grep: /var/tmp/ikqnZUJJbbQlTgXSaZHSR/newfile: No such file or directory

Copying files to the temporary directory...OK

Striping ELF binaries and libraries...OK

Compressing man pages...OK

Building file list...OK

Building Debian package...OK

Installing Debian package... FAILED!

*** Failed to install the package

Do you want to see the log file?  [y]: 

```


Did you give the package a name, like:  alsa-lib-1.0.15 while using the checkinstall command?

---

### Post by amvella on 2007-10-19
k i tried installing it it again..

So i copied and pasted the first set of code 
```

wget ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.15.tar.bz2 &&
tar xf alsa-driver-1.0.15.tar.bz2 &&
cd alsa-driver-1.0.15 &&
./configure \
--with-cards=hda-intel &&
make &&
sudo install -v -m644 pci/hda/snd-hda-intel.ko  /lib/modules/$(uname -r)/ubuntu/media/snd-hda-intel/ &&
cd ../ &&
sudo rm -rf alsa-driver-1.0.15 &&
sudo depmod -ae &&
sudo modprobe snd-hda-intel ; modprobe snd-pcm-oss ; modprobe snd-mixer-oss ; modprobe snd-seq-oss

```

and this is what i got after 

```

ALSA modules were successfully compiled.

`pci/hda/snd-hda-intel.ko' -> `/lib/modules/2.6.22-14-rt/ubuntu/media/snd-hda-intel/snd-hda-intel.ko'
FATAL: Error inserting snd_hda_intel (/lib/modules/2.6.22-14-rt/ubuntu/media/snd-hda-intel/snd-hda-intel.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_mixer_oss (/lib/modules/2.6.22-14-rt/kernel/sound/core/oss/snd-mixer-oss.ko): Operation not permitted
FATAL: Error inserting snd_pcm_oss (/lib/modules/2.6.22-14-rt/kernel/sound/core/oss/snd-pcm-oss.ko): Operation not permitted
FATAL: Error inserting snd_mixer_oss (/lib/modules/2.6.22-14-rt/kernel/sound/core/oss/snd-mixer-oss.ko): Operation not permitted
WARNING: Error inserting snd_seq_device (/lib/modules/2.6.22-14-rt/kernel/sound/core/seq/snd-seq-device.ko): Operation not permitted
WARNING: Error inserting snd_seq (/lib/modules/2.6.22-14-rt/kernel/sound/core/seq/snd-seq.ko): Operation not permitted
WARNING: Error inserting snd_seq_midi_event (/lib/modules/2.6.22-14-rt/kernel/sound/core/seq/snd-seq-midi-event.ko): Operation not permitted
FATAL: Error inserting snd_seq_oss (/lib/modules/2.6.22-14-rt/kernel/sound/core/seq/oss/snd-seq-oss.ko): Operation not permitted

```

What am i doing here? man this is very hard.. nothing is going right for me :(

---

### Post by linux23dragon on 2007-10-19
> **amvella said:**
> k i tried installing it it again..

So i copied and pasted the first set of code 
```

wget ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.15.tar.bz2 &&
tar xf alsa-driver-1.0.15.tar.bz2 &&
cd alsa-driver-1.0.15 &&
./configure \
--with-cards=hda-intel &&
make &&
sudo install -v -m644 pci/hda/snd-hda-intel.ko  /lib/modules/$(uname -r)/ubuntu/media/snd-hda-intel/ &&
cd ../ &&
sudo rm -rf alsa-driver-1.0.15 &&
sudo depmod -ae &&
sudo modprobe snd-hda-intel ; modprobe snd-pcm-oss ; modprobe snd-mixer-oss ; modprobe snd-seq-oss

```

and this is what i got after 

```

ALSA modules were successfully compiled.

`pci/hda/snd-hda-intel.ko' -> `/lib/modules/2.6.22-14-rt/ubuntu/media/snd-hda-intel/snd-hda-intel.ko'
FATAL: Error inserting snd_hda_intel (/lib/modules/2.6.22-14-rt/ubuntu/media/snd-hda-intel/snd-hda-intel.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_mixer_oss (/lib/modules/2.6.22-14-rt/kernel/sound/core/oss/snd-mixer-oss.ko): Operation not permitted
FATAL: Error inserting snd_pcm_oss (/lib/modules/2.6.22-14-rt/kernel/sound/core/oss/snd-pcm-oss.ko): Operation not permitted
FATAL: Error inserting snd_mixer_oss (/lib/modules/2.6.22-14-rt/kernel/sound/core/oss/snd-mixer-oss.ko): Operation not permitted
WARNING: Error inserting snd_seq_device (/lib/modules/2.6.22-14-rt/kernel/sound/core/seq/snd-seq-device.ko): Operation not permitted
WARNING: Error inserting snd_seq (/lib/modules/2.6.22-14-rt/kernel/sound/core/seq/snd-seq.ko): Operation not permitted
WARNING: Error inserting snd_seq_midi_event (/lib/modules/2.6.22-14-rt/kernel/sound/core/seq/snd-seq-midi-event.ko): Operation not permitted
FATAL: Error inserting snd_seq_oss (/lib/modules/2.6.22-14-rt/kernel/sound/core/seq/oss/snd-seq-oss.ko): Operation not permitted

```

What am i doing here? man this is very hard.. nothing is going right for me :(

Try to install the Alsa driver with method 2. 

Oh did you try to use "dpkg --force-overwrite --install" with Alsa-lib ?  Because I don't think we can uninstall "libasound2" with out uninstalling other softaware you need.

---

### Post by linux23dragon on 2007-10-19
> **amvella said:**
> k i tried installing it it again..

So i copied and pasted the first set of code 
```

wget ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.15.tar.bz2 &&
tar xf alsa-driver-1.0.15.tar.bz2 &&
cd alsa-driver-1.0.15 &&
./configure \
--with-cards=hda-intel &&
make &&
sudo install -v -m644 pci/hda/snd-hda-intel.ko  /lib/modules/$(uname -r)/ubuntu/media/snd-hda-intel/ &&
cd ../ &&
sudo rm -rf alsa-driver-1.0.15 &&
sudo depmod -ae &&
sudo modprobe snd-hda-intel ; modprobe snd-pcm-oss ; modprobe snd-mixer-oss ; modprobe snd-seq-oss

```

and this is what i got after 

```

ALSA modules were successfully compiled.

`pci/hda/snd-hda-intel.ko' -> `/lib/modules/2.6.22-14-rt/ubuntu/media/snd-hda-intel/snd-hda-intel.ko'
FATAL: Error inserting snd_hda_intel (/lib/modules/2.6.22-14-rt/ubuntu/media/snd-hda-intel/snd-hda-intel.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_mixer_oss (/lib/modules/2.6.22-14-rt/kernel/sound/core/oss/snd-mixer-oss.ko): Operation not permitted
FATAL: Error inserting snd_pcm_oss (/lib/modules/2.6.22-14-rt/kernel/sound/core/oss/snd-pcm-oss.ko): Operation not permitted
FATAL: Error inserting snd_mixer_oss (/lib/modules/2.6.22-14-rt/kernel/sound/core/oss/snd-mixer-oss.ko): Operation not permitted
WARNING: Error inserting snd_seq_device (/lib/modules/2.6.22-14-rt/kernel/sound/core/seq/snd-seq-device.ko): Operation not permitted
WARNING: Error inserting snd_seq (/lib/modules/2.6.22-14-rt/kernel/sound/core/seq/snd-seq.ko): Operation not permitted
WARNING: Error inserting snd_seq_midi_event (/lib/modules/2.6.22-14-rt/kernel/sound/core/seq/snd-seq-midi-event.ko): Operation not permitted
FATAL: Error inserting snd_seq_oss (/lib/modules/2.6.22-14-rt/kernel/sound/core/seq/oss/snd-seq-oss.ko): Operation not permitted

```

What am i doing here? man this is very hard.. nothing is going right for me :(

You are not doing anything wrong :-)

EDIT: The 1st Post has been updated.  I've fixed some of the issues by removing some of the modules loaded  by the command line.  Thanks for the report.  Keep them reports coming people :)

Try to install the Alsa driver with method 2. 

Oh did you try to use "dpkg --force-overwrite --install" with Alsa-lib ?  Because I don't think we can uninstall "libasound2" with out uninstalling other software you need.

---

### Post by amvella on 2007-10-19
man i quit.. its not working.. very fresturating..anyhow... thanks for all the help u guys..gutsy stable is not that great.. gutsy RC was working much better for me... even after i compiled all the alsa-driver, alsa-lib, and alsa-utls sound worked in RC... but not in gutsy...

---

### Post by amvella on 2007-10-19
ok this is what i did...

i reinstalled ubunty gutsy gibbon RC...

```
sudo apt-get install build-essential ncurses-dev gettext
```

downloaded the linux headers

```
sudo apt-get install linux-headers-`uname -r`
```

download the latest alsa drivers, alsa lib, and alsa utls

```
cd /usr/src/[code]

make a dir

[code]sudo mkdir alsa
```

copy all the downloaded tar files to this folder 
After done copying run these commands

```
sudo tar xf alsa-driver-1.0.15.tar.bz2 
sudo tar xf alsa-lib-1.0.15.tar.bz2 
sudo tar xf alsa-utils-1.0.15.tar.bz2 

```

then 

```

cd alsa-driver-1.0.15/
sudo ./configure
sudo make
sudo make install

```

after this is done cd into the library folder

repeat the same compiling commands

```

sudo ./configure
sudo make
sudo make install

```

change directory to utls

then repeat the codes

```

sudo ./configure
sudo make
sudo make install

```

then copy paste this code in

```
sudo depmod -a
```

then reboot

```
sudo reboot
```

This worked for me.. hopefully this works for anyone with hp dv9500t laptop

---

### Post by linux23dragon on 2007-10-19
> **amvella said:**
> ok this is what i did...

i reinstalled ubunty gutsy gibbon RC...

--cut--

download the latest alsa drivers, alsa lib, and alsa utls

---cut---

copy all the downloaded tar files to this folder 
After done copying run these commands

--cut--

This worked for me.. hopefully this works for anyone with hp dv9500t laptop

Hi amvella

If that worked for you, then the instructions (from the first post) should of worked for you in Gusty too(since they are nearly the same instructions).  That is very strange :-k 


Can you please post the out put after running these commands (from you new Gusty RC installation)?:-
```

cat /proc/asound/cards
```

```

dmesg
```

```

gcc -v
```

---

### Post by linux23dragon on 2007-10-19
Added more information and hints that may help some people depending on the system used.


Just to note.  I've never seen such issues with the Linux kernel before.  And it is (some how) to do with the kernel configuration setup in Ubuntu-7.10.  I know  we shouldn't have that many issues if you had the original kernel 2.6.22 from [www.kernel.org](www.kernel.org)

Well thats my two cents on the issue.

---

### Post by DMCrimson on 2007-10-19
After using installation methods both 1 and 2, I have received the same error message at the end of both:

WARNING: Error inserting snd_hwdep (/lib/modules/2.6.22-14-generic/kernel/sound/acore/snd-hwdep.ko): Unknown symbol in module, or unknown parameter (see dmesg)

What does this mean?

EDIT;  Hey, the sound works!  Thanks for the guide man, I've been crazy about this problem for the past two days.

---

### Post by amvella on 2007-10-20
> **linux23dragon said:**
> Hi amvella

If that worked for you, then the instructions (from the first post) should of worked for you in Gusty too(since they are nearly the same instructions).  That is very strange :-k 


Can you please post the out put after running these commands (from you new Gusty RC installation)?:-
```

cat /proc/asound/cards
```

```

dmesg
```

```

gcc -v
```

sorry dude the sond topped working again.. i don no y.. i think its the updates i installed from the automatic updates that messed it up.. now i don no wat to do.. should i recompile it again and see if it works.. i will let you know after a recompile.. aite.. 
thanks alot for getting back to my post..

---

### Post by Gunner_Sr on 2007-10-20
None of this worked for me. The easiest that I followed and it worked was the following.

[http://ubuntuforums.org/showpost.php?p=3475485&postcount=235](http://ubuntuforums.org/showpost.php?p=3475485&postcount=235)

-cg

---

### Post by linux23dragon on 2007-10-20
> **amvella said:**
> sorry dude the sond topped working again.. i don no y.. i think its the updates i installed from the automatic updates that messed it up.. now i don no wat to do.. should i recompile it again and see if it works.. i will let you know after a recompile.. aite.. 
thanks alot for getting back to my post..


You will only need to recompile the Alsa-driver.

---

### Post by amvella on 2007-10-20
dude it started working agiain after i recompiled the driver, lib and utls

now i will give u the outputs for the commands you gave me.. 

```

~$ cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf8400000 irq 23

``` 

```

:~$ dmesg
[    0.000000] Linux version 2.6.22-14-generic (buildd@palmer) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Sun Oct 14 23:05:12 GMT 2007 (Ubuntu 2.6.22-14.46-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000ce000 - 00000000000d0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007fed0000 (usable)
[    0.000000]  BIOS-e820: 000000007fed0000 - 000000007fedf000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007fedf000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] 1150MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f82e0
[    0.000000] Entering add_active_range(0, 0, 523984) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   523984
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   523984
[    0.000000] On node 0 totalpages: 523984
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2301 pages used for memmap
[    0.000000]   HighMem zone: 292307 pages, LIFO batch:31
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP signature @ 0xC00F8240 checksum 0
[    0.000000] ACPI: RSDP 000F8240, 0024 (r2 HP    )
[    0.000000] ACPI: XSDT 7FED229A, 0084 (r1 HPQOEM SLIC-MPC  6040000  LTP        0)
[    0.000000] ACPI: FACP 7FEDBC04, 00F4 (r3 HP     30CC      6040000 ALAN        1)
[    0.000000] ACPI: DSDT 7FED3638, 8558 (r1 HP     30CB      6040000 INTL 20060707)
[    0.000000] ACPI: FACS 7FEDEFC0, 0040
[    0.000000] ACPI: APIC 7FEDBCF8, 0068 (r1 HP     30CB      6040000 LOHR       5A)
[    0.000000] ACPI: HPET 7FEDBD60, 0038 (r1 HP     30CB      6040000 LOHR       5A)
[    0.000000] ACPI: MCFG 7FEDBD98, 003C (r1 HP     30CB      6040000 LOHR       5A)
[    0.000000] ACPI: TMOR 7FEDBDD4, 0026 (r1 HP     30CC      6040000 PTL         3)
[    0.000000] ACPI: APIC 7FEDBDFA, 0068 (r1 HP     30CB      6040000  LTP        0)
[    0.000000] ACPI: BOOT 7FEDBE62, 0028 (r1 HP     30CB      6040000  LTP        1)
[    0.000000] ACPI: SLIC 7FEDBE8A, 0176 (r1 HPQOEM SLIC-MPC  6040000  LTP        1)
[    0.000000] ACPI: SSDT 7FED335B, 02DD (r1 HP     30CB         1000 INTL 20060707)
[    0.000000] ACPI: SSDT 7FED28AA, 025F (r1  HP    30CB         3000 INTL 20060707)
[    0.000000] ACPI: SSDT 7FED2804, 00A6 (r1  HP    30CB         3000 INTL 20060707)
[    0.000000] ACPI: SSDT 7FED231E, 04E6 (r1  HP     30CB        3000 INTL 20060707)
[    0.000000] ACPI: BIOS bug: multiple APIC/MADT found, using 0
[    0.000000] ACPI: If "acpi_apic_instance=2" works better, notify linux-acpi@vger.kernel.org
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:15 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1 6:15 APIC version 20
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:60000000)
[    0.000000] Built 1 zonelists.  Total pages: 519891
[    0.000000] Kernel command line: root=UUID=dfa926fd-87a3-4ffb-ac7e-66df06259a0a ro quiet splash
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1995.432 MHz processor.
[   15.836881] Console: colour VGA+ 80x25
[   15.837148] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   15.837403] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   15.909313] Memory: 2066468k/2095936k available (2015k kernel code, 28172k reserved, 916k data, 364k init, 1178432k highmem)
[   15.909320] virtual kernel memory layout:
[   15.909321]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   15.909322]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   15.909323]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   15.909324]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   15.909325]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   15.909325]       .data : 0xc02f7d26 - 0xc03dce84   ( 916 kB)
[   15.909326]       .text : 0xc0100000 - 0xc02f7d26   (2015 kB)
[   15.909329] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   15.909359] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   15.909483] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   15.909487] hpet0: 3 64-bit timers, 14318180 Hz
[   15.990470] Calibrating delay using timer specific routine.. 3994.51 BogoMIPS (lpj=7989025)
[   15.990492] Security Framework v1.0.0 initialized
[   15.990497] SELinux:  Disabled at boot.
[   15.990507] Mount-cache hash table entries: 512
[   15.990613] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e3bd 00000000 00000001
[   15.990619] monitor/mwait feature present.
[   15.990621] using mwait in idle threads.
[   15.990624] CPU: L1 I cache: 32K, L1 D cache: 32K
[   15.990626] CPU: L2 cache: 2048K
[   15.990628] CPU: Physical Processor ID: 0
[   15.990630] CPU: Processor Core ID: 0
[   15.990631] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e3bd 00000000 00000001
[   15.990639] Compat vDSO mapped to ffffe000.
[   15.990649] Checking 'hlt' instruction... OK.
[   16.006552] SMP alternatives: switching to UP code
[   16.006901] Early unpacking initramfs... done
[   16.257363] ACPI: Core revision 20070126
[   16.257406] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   16.262679] CPU0: Intel(R) Core(TM)2 Duo CPU     T7250  @ 2.00GHz stepping 0d
[   16.262692] SMP alternatives: switching to SMP code
[   16.262763] Booting processor 1/1 eip 3000
[   16.272951] Initializing CPU#1
[   16.350306] Calibrating delay using timer specific routine.. 3990.68 BogoMIPS (lpj=7981368)
[   16.350311] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e3bd 00000000 00000001
[   16.350315] monitor/mwait feature present.
[   16.350317] CPU: L1 I cache: 32K, L1 D cache: 32K
[   16.350319] CPU: L2 cache: 2048K
[   16.350321] CPU: Physical Processor ID: 0
[   16.350322] CPU: Processor Core ID: 1
[   16.350323] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e3bd 00000000 00000001
[   16.350790] CPU1: Intel(R) Core(TM)2 Duo CPU     T7250  @ 2.00GHz stepping 0d
[   16.350810] Total of 2 processors activated (7985.19 BogoMIPS).
[   16.350978] ENABLING IO-APIC IRQs
[   16.351166] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   16.498317] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   16.518324] Brought up 2 CPUs
[   16.653084] migration_cost=85
[   16.653193] Booting paravirtualized kernel on bare hardware
[   16.653267] Time:  0:47:36  Date: 09/20/107
[   16.653283] NET: Registered protocol family 16
[   16.653350] EISA bus registered
[   16.653354] ACPI: bus type pci registered
[   16.653655] PCI: PCI BIOS revision 3.00 entry at 0xfde31, last bus=7
[   16.653657] PCI: Using configuration type 1
[   16.653658] Setting up standard PCI resources
[   16.655474] ACPI: EC: Look up EC in DSDT
[   16.656434] ACPI: EC: GPE=0x17, ports=0x66, 0x62
[   16.657527] ACPI: System BIOS is requesting _OSI(Linux)
[   16.657529] ACPI: Please test with "acpi_osi=!Linux"
[   16.657530] Please send dmidecode to linux-acpi@vger.kernel.org
[   16.658469] ACPI: Interpreter enabled
[   16.658472] ACPI: (supports S0 S3 S4 S5)
[   16.658487] ACPI: Using IOAPIC for interrupt routing
[   16.664783] ACPI: EC: GPE=0x17, ports=0x66, 0x62
[   16.664832] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   16.664844] PCI: Probing PCI hardware (bus 00)
[   16.667005] PCI: Transparent bridge - 0000:00:1e.0
[   16.667086] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   16.667343] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEGP._PRT]
[   16.667462] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[   16.667576] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[   16.667687] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP06._PRT]
[   16.667811] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[   16.676615] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 *5 6 7 10 12 14 15)
[   16.676708] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[   16.676800] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 *7 10 12 14 15)
[   16.676890] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[   16.676981] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[   16.677071] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[   16.677161] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[   16.677251] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[   16.677369] Linux Plug and Play Support v0.97 (c) Adam Belay
[   16.677377] pnp: PnP ACPI init
[   16.677385] ACPI: bus type pnp registered
[   16.679548] pnp: PnP ACPI: found 11 devices
[   16.679550] ACPI: ACPI bus type pnp unregistered
[   16.679553] PnPBIOS: Disabled by ACPI PNP
[   16.679589] PCI: Using ACPI for IRQ routing
[   16.679591] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   16.770065] NET: Registered protocol family 8
[   16.770066] NET: Registered protocol family 20
[   16.770120] pnp: 00:01: iomem range 0xfed1c000-0xfed1ffff could not be reserved
[   16.770123] Time: tsc clocksource has been installed.
[   16.770130] Switched to high resolution mode on CPU 0
[   16.770134] pnp: 00:01: iomem range 0xfed14000-0xfed17fff could not be reserved
[   16.770137] pnp: 00:01: iomem range 0xfed18000-0xfed18fff could not be reserved
[   16.770139] pnp: 00:01: iomem range 0xfed19000-0xfed19fff could not be reserved
[   16.770145] pnp: 00:04: iomem range 0xfed00000-0xfed003ff could not be reserved
[   16.770152] pnp: 00:07: ioport range 0x6a0-0x6af has been reserved
[   16.770154] pnp: 00:07: ioport range 0x6b0-0x6ff has been reserved
[   16.770207] Switched to high resolution mode on CPU 1
[   16.800400] PCI: Failed to allocate mem resource #6:20000@e0000000 for 0000:01:00.0
[   16.800472] PCI: Bridge: 0000:00:01.0
[   16.800474]   IO window: 2000-2fff
[   16.800478]   MEM window: c4000000-c6ffffff
[   16.800481]   PREFETCH window: d0000000-dfffffff
[   16.800484] PCI: Bridge: 0000:00:1c.0
[   16.800487]   IO window: 4000-7fff
[   16.800493]   MEM window: f4000000-f7ffffff
[   16.800497]   PREFETCH window: f0000000-f3ffffff
[   16.800503] PCI: Bridge: 0000:00:1c.1
[   16.800506]   IO window: 8000-bfff
[   16.800511]   MEM window: bc000000-bfffffff
[   16.800516]   PREFETCH window: c8000000-cbffffff
[   16.800523] PCI: Bridge: 0000:00:1c.5
[   16.800525]   IO window: c000-cfff
[   16.800531]   MEM window: f8000000-f80fffff
[   16.800536]   PREFETCH window: 88000000-880fffff
[   16.800542] PCI: Bridge: 0000:00:1e.0
[   16.800543]   IO window: disabled.
[   16.800549]   MEM window: f8100000-f81fffff
[   16.800554]   PREFETCH window: disabled.
[   16.800568] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[   16.800573] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   16.800595] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 17
[   16.800601] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   16.800622] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 16 (level, low) -> IRQ 16
[   16.800627] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   16.800650] ACPI: PCI Interrupt 0000:00:1c.5[B] -> GSI 16 (level, low) -> IRQ 16
[   16.800655] PCI: Setting latency timer of device 0000:00:1c.5 to 64
[   16.800670] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   16.800679] NET: Registered protocol family 2
[   16.846076] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   16.846126] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
[   16.846724] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   16.846931] TCP: Hash tables configured (established 131072 bind 65536)
[   16.846933] TCP reno registered
[   16.862183] checking if image is initramfs... it is
[   17.403947] Freeing initrd memory: 7049k freed
[   17.404041] Simple Boot Flag at 0x35 set to 0x1
[   17.404443] audit: initializing netlink socket (disabled)
[   17.404457] audit(1192841256.236:1): initialized
[   17.404539] highmem bounce pool size: 64 pages
[   17.406094] VFS: Disk quotas dquot_6.5.1
[   17.406134] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   17.406210] io scheduler noop registered
[   17.406211] io scheduler anticipatory registered
[   17.406213] io scheduler deadline registered
[   17.406224] io scheduler cfq registered (default)
[   17.406351] Boot video device is 0000:01:00.0
[   17.406424] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   17.406458] assign_interrupt_mode Found MSI capability
[   17.406461] Allocate Port Service[0000:00:01.0:pcie00]
[   17.406489] Allocate Port Service[0000:00:01.0:pcie02]
[   17.406558] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   17.406617] assign_interrupt_mode Found MSI capability
[   17.406619] Allocate Port Service[0000:00:1c.0:pcie00]
[   17.406644] Allocate Port Service[0000:00:1c.0:pcie02]
[   17.406738] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   17.406797] assign_interrupt_mode Found MSI capability
[   17.406799] Allocate Port Service[0000:00:1c.1:pcie00]
[   17.406824] Allocate Port Service[0000:00:1c.1:pcie02]
[   17.406918] PCI: Setting latency timer of device 0000:00:1c.5 to 64
[   17.406977] assign_interrupt_mode Found MSI capability
[   17.406979] Allocate Port Service[0000:00:1c.5:pcie00]
[   17.407003] Allocate Port Service[0000:00:1c.5:pcie02]
[   17.407150] isapnp: Scanning for PnP cards...
[   17.761210] isapnp: No Plug & Play device found
[   17.777525] Real Time Clock Driver v1.12ac
[   17.777738] hpet_resources: 0xfed00000 is busy
[   17.777761] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   17.778652] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   17.778750] input: Macintosh mouse button emulation as /class/input/input0
[   17.778811] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   17.819853] serio: i8042 KBD port at 0x60,0x64 irq 1
[   17.819857] serio: i8042 AUX port at 0x60,0x64 irq 12
[   17.819975] mice: PS/2 mouse device common for all mice
[   17.821993] EISA: Probing bus 0 at eisa.0
[   17.822000] Cannot allocate resource for EISA slot 1
[   17.822003] Cannot allocate resource for EISA slot 2
[   17.822009] Cannot allocate resource for EISA slot 4
[   17.822011] Cannot allocate resource for EISA slot 5
[   17.822013] Cannot allocate resource for EISA slot 6
[   17.822014] Cannot allocate resource for EISA slot 7
[   17.822016] Cannot allocate resource for EISA slot 8
[   17.822018] EISA: Detected 0 cards.
[   17.822086] TCP cubic registered
[   17.822099] NET: Registered protocol family 1
[   17.822117] Using IPI No-Shortcut mode
[   17.822261]   Magic number: 11:758:759
[   17.822512] Freeing unused kernel memory: 364k freed
[   17.856997] input: AT Translated Set 2 keyboard as /class/input/input1
[   18.990422] AppArmor: AppArmor initialized<5>audit(1192841257.736:2):  type=1505 info="AppArmor initialized" pid=1261
[   19.015517] fuse init (API version 7.8)
[   19.024583] Failure registering capabilities with primary security module.
[   19.061553] ACPI: SSDT 7FED3019, 027A (r1  HP    30CB         3000 INTL 20060707)
[   19.061751] ACPI: SSDT 7FED2B09, 048B (r1  HP    30CB         3001 INTL 20060707)
[   19.062210] Monitor-Mwait will be used to enter C-1 state
[   19.062212] Monitor-Mwait will be used to enter C-2 state
[   19.062214] Monitor-Mwait will be used to enter C-3 state
[   19.062219] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   19.062223] ACPI: Processor [CPU0] (supports 8 throttling states)
[   19.062418] ACPI: SSDT 7FED3293, 00C8 (r1  HP    30CB         3000 INTL 20060707)
[   19.062598] ACPI: SSDT 7FED2F94, 0085 (r1  HP    30CB         3000 INTL 20060707)
[   19.085207] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[   19.085212] ACPI: Processor [CPU1] (supports 8 throttling states)
[    3.052000] Marking TSC unstable due to: possible TSC halt in C2.
[    3.052000] ACPI Exception (thermal-0311): AE_BAD_DATA, No critical threshold [20070126]
[    3.056000] Time: hpet clocksource has been installed.
[    3.400000] usbcore: registered new interface driver usbfs
[    3.400000] usbcore: registered new interface driver hub
[    3.400000] usbcore: registered new device driver usb
[    3.400000] USB Universal Host Controller Interface driver v3.0
[    3.400000] ACPI: PCI Interrupt 0000:00:1a.0[A] -> GSI 16 (level, low) -> IRQ 16
[    3.400000] PCI: Setting latency timer of device 0000:00:1a.0 to 64
[    3.400000] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    3.400000] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    3.400000] uhci_hcd 0000:00:1a.0: irq 16, io base 0x00001800
[    3.400000] usb usb1: configuration #1 chosen from 1 choice
[    3.400000] hub 1-0:1.0: USB hub found
[    3.400000] hub 1-0:1.0: 2 ports detected
[    3.440000] SCSI subsystem initialized
[    3.444000] libata version 2.21 loaded.
[    3.504000] ACPI: PCI Interrupt 0000:00:1a.1[B] -> GSI 21 (level, low) -> IRQ 18
[    3.504000] PCI: Setting latency timer of device 0000:00:1a.1 to 64
[    3.504000] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    3.504000] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
[    3.504000] uhci_hcd 0000:00:1a.1: irq 18, io base 0x00001820
[    3.504000] usb usb2: configuration #1 chosen from 1 choice
[    3.504000] hub 2-0:1.0: USB hub found
[    3.504000] hub 2-0:1.0: 2 ports detected
[    3.628000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 19
[    3.628000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[    3.628000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    3.628000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 3
[    3.628000] uhci_hcd 0000:00:1d.0: irq 19, io base 0x00001840
[    3.628000] usb usb3: configuration #1 chosen from 1 choice
[    3.628000] hub 3-0:1.0: USB hub found
[    3.628000] hub 3-0:1.0: 2 ports detected
[    3.732000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 20
[    3.732000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[    3.732000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    3.732000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 4
[    3.732000] uhci_hcd 0000:00:1d.1: irq 20, io base 0x00001860
[    3.732000] usb usb4: configuration #1 chosen from 1 choice
[    3.732000] hub 4-0:1.0: USB hub found
[    3.732000] hub 4-0:1.0: 2 ports detected
[    3.836000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 21
[    3.836000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[    3.836000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    3.836000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 5
[    3.836000] uhci_hcd 0000:00:1d.2: irq 21, io base 0x00001880
[    3.836000] usb usb5: configuration #1 chosen from 1 choice
[    3.836000] hub 5-0:1.0: USB hub found
[    3.836000] hub 5-0:1.0: 2 ports detected
[    3.940000] ACPI: PCI Interrupt 0000:00:1a.7[C] -> GSI 18 (level, low) -> IRQ 21
[    3.940000] PCI: Setting latency timer of device 0000:00:1a.7 to 64
[    3.940000] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    3.940000] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 6
[    3.940000] ehci_hcd 0000:00:1a.7: debug port 1
[    3.940000] PCI: cache line size of 32 is not supported by device 0000:00:1a.7
[    3.940000] ehci_hcd 0000:00:1a.7: irq 21, io mem 0xf8404800
[    3.944000] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.944000] usb usb6: configuration #1 chosen from 1 choice
[    3.944000] hub 6-0:1.0: USB hub found
[    3.944000] hub 6-0:1.0: 4 ports detected
[    4.000000] Clocksource tsc unstable (delta = -377003145 ns)
[    4.048000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 19
[    4.048000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    4.048000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    4.048000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 7
[    4.048000] ehci_hcd 0000:00:1d.7: debug port 1
[    4.048000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[    4.048000] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xf8404c00
[    4.052000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    4.052000] usb usb7: configuration #1 chosen from 1 choice
[    4.052000] hub 7-0:1.0: USB hub found
[    4.052000] hub 7-0:1.0: 6 ports detected
[    4.156000] r8169 Gigabit Ethernet driver 2.2LK loaded
[    4.156000] ACPI: PCI Interrupt 0000:06:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[    4.156000] PCI: Setting latency timer of device 0000:06:00.0 to 64
[    4.156000] eth0: RTL8168b/8111b at 0xf887a000, 00:1b:24:ab:53:62, XID 38000000 IRQ 17
[    4.156000] ACPI: PCI Interrupt 0000:07:09.0[A] -> GSI 20 (level, low) -> IRQ 22
[    4.212000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[22]  MMIO=[f8100000-f81007ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    4.216000] ahci 0000:00:1f.2: version 2.2
[    4.216000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 20
[    5.092000] usb 7-4: new high speed USB device using ehci_hcd and address 3
[    5.220000] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 3 Gbps 0x7 impl SATA mode
[    5.220000] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo pio slum part 
[    5.220000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[    5.220000] scsi0 : ahci
[    5.220000] scsi1 : ahci
[    5.220000] scsi2 : ahci
[    5.220000] ata1: SATA max UDMA/133 cmd 0xf887c100 ctl 0x00000000 bmdma 0x00000000 irq 20
[    5.220000] ata2: SATA max UDMA/133 cmd 0xf887c180 ctl 0x00000000 bmdma 0x00000000 irq 20
[    5.220000] ata3: SATA max UDMA/133 cmd 0xf887c200 ctl 0x00000000 bmdma 0x00000000 irq 20
[    5.232000] usb 7-4: configuration #1 chosen from 1 choice
[    5.476000] usb 2-2: new full speed USB device using uhci_hcd and address 2
[    5.488000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00241b008cec6300]
[    5.652000] usb 2-2: configuration #1 chosen from 1 choice
[    5.656000] hub 2-2:1.0: USB hub found
[    5.660000] hub 2-2:1.0: 3 ports detected
[    5.744000] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    5.744000] ata1.00: ATA-7: ST9160821AS, 3.BHE, max UDMA/100
[    5.744000] ata1.00: 312581808 sectors, multi 16: LBA48 
[    5.744000] ata1.00: configured for UDMA/100
[    6.012000] usb 4-1: new full speed USB device using uhci_hcd and address 2
[    6.068000] ata2: SATA link down (SStatus 0 SControl 300)
[    6.176000] usb 4-1: configuration #1 chosen from 1 choice
[    6.384000] ata3: SATA link down (SStatus 0 SControl 300)
[    6.384000] scsi 0:0:0:0: Direct-Access     ATA      ST9160821AS      3.BH PQ: 0 ANSI: 5
[    6.384000] ata_piix 0000:00:1f.1: version 2.11
[    6.384000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 19 (level, low) -> IRQ 20
[    6.384000] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[    6.384000] scsi3 : ata_piix
[    6.384000] scsi4 : ata_piix
[    6.384000] ata4: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x000118a0 irq 14
[    6.384000] ata5: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x000118a8 irq 15
[    6.384000] usb 2-2.3: new full speed USB device using uhci_hcd and address 3
[    6.388000] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[    6.388000] sd 0:0:0:0: [sda] Write Protect is off
[    6.388000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    6.388000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.388000] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[    6.388000] sd 0:0:0:0: [sda] Write Protect is off
[    6.388000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    6.388000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.388000]  sda: sda1 sda2 sda3 sda4
[    6.428000] sd 0:0:0:0: [sda] Attached SCSI disk
[    6.432000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    6.540000] usb 2-2.3: configuration #1 chosen from 1 choice
[    6.548000] usbcore: registered new interface driver hiddev
[    6.560000] input: Microsoft Microsoft&#65533; Wireless Notebook Presenter Mouse 8000 as /class/input/input2
[    6.560000] input: USB HID v1.11 Mouse [Microsoft Microsoft&#65533; Wireless Notebook Presenter Mouse 8000] on usb-0000:00:1a.1-2.3
[    6.560000] usbcore: registered new interface driver usbhid
[    6.560000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[    6.728000] ata4.00: ATAPI: Slimtype DVD A  DS8A1H, WH66, max MWDMA2
[    6.836000] Attempting manual resume
[    6.836000] swsusp: Resume From Partition 8:2
[    6.836000] PM: Checking swsusp image.
[    6.836000] PM: Resume from disk failed.
[    6.876000] kjournald starting.  Commit interval 5 seconds
[    6.876000] EXT3-fs: mounted filesystem with ordered data mode.
[    6.932000] ata4.00: configured for MWDMA2
[    7.100000] scsi 3:0:0:0: CD-ROM            Slimtype DVD A  DS8A1H    WH66 PQ: 0 ANSI: 5
[    7.100000] scsi 3:0:0:0: Attached scsi generic sg1 type 5
[   13.584000] Linux agpgart interface v0.102 (c) Dave Jones
[   13.720000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   13.724000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   13.968000] sdhci: Secure Digital Host Controller Interface driver
[   13.968000] sdhci: Copyright(c) Pierre Ossman
[   13.968000] sdhci: SDHCI controller found at 0000:07:09.1 [1180:0822] (rev 22)
[   13.968000] ACPI: PCI Interrupt 0000:07:09.1[B] -> GSI 21 (level, low) -> IRQ 18
[   13.968000] mmc0: SDHCI at 0xf8100800 irq 18 DMA
[   14.416000] nvidia: module license 'NVIDIA' taints kernel.
[   14.420000] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[   14.420000] Uniform CD-ROM driver Revision: 3.20
[   14.420000] sr 3:0:0:0: Attached scsi CD-ROM sr0
[   14.668000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   14.668000] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   14.668000] NVRM: loading NVIDIA UNIX x86 Kernel Module  100.14.19  Wed Sep 12 14:12:24 PDT 2007
[   14.736000] iwl4965: Intel(R) Wireless WiFi Link 4965AGN driver for Linux, 1.1.0
[   14.736000] iwl4965: Copyright(c) 2003-2007 Intel Corporation
[   14.736000] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   14.736000] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   14.736000] iwl4965: Detected Intel Wireless WiFi Link 4965AGN
[   14.744000] Linux video capture interface: v2.00
[   15.004000] uvcvideo: Found UVC 1.00 device HP Webcam (064e:a101)
[   15.004000] usbcore: registered new interface driver uvcvideo
[   15.004000] USB Video Class driver (v0.1.0)
[   15.072000] iwl4965: Tunable channels: 11 802.11bg, 13 802.11a channels
[   15.072000] wmaster0: Selected rate control algorithm 'iwl-4965-rs'
[   15.368000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 23
[   15.368000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   15.608000] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x1a0b1, caps: 0xa04713/0x200000
[   15.716000] input: SynPS/2 Synaptics TouchPad as /class/input/input3
[   16.032000] lp: driver loaded but no devices found
[   16.092000] Adding 2016148k swap on /dev/sda2.  Priority:-1 extents:1 across:2016148k
[   16.508000] EXT3 FS on sda4, internal journal
[   18.036000] ACPI: Battery Slot [BAT0] (battery present)
[   18.044000] input: Power Button (FF) as /class/input/input4
[   18.044000] ACPI: Power Button (FF) [PWRF]
[   18.044000] input: Power Button (CM) as /class/input/input5
[   18.044000] ACPI: Power Button (CM) [PWRB]
[   18.044000] input: Sleep Button (CM) as /class/input/input6
[   18.044000] ACPI: Sleep Button (CM) [SLPB]
[   18.044000] input: Lid Switch as /class/input/input7
[   18.044000] ACPI: Lid Switch [LID]
[   18.116000] No dock devices found.
[   18.220000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   18.220000] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   18.304000] ACPI: AC Adapter [ACAD] (off-line)
[   19.308000] ppdev: user-space parallel port driver
[   19.520000] audit(1192859274.165:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=5201 profile="/usr/sbin/cupsd"
[   19.572000] apm: BIOS not found.
[   19.604000] r8169: eth0: link down
[   19.880000] Failure registering capabilities with primary security module.
[   20.104000] Bluetooth: Core ver 2.11
[   20.104000] NET: Registered protocol family 31
[   20.104000] Bluetooth: HCI device and connection manager initialized
[   20.104000] Bluetooth: HCI socket layer initialized
[   20.128000] Bluetooth: L2CAP ver 2.8
[   20.128000] Bluetooth: L2CAP socket layer initialized
[   20.232000] Bluetooth: RFCOMM socket layer initialized
[   20.232000] Bluetooth: RFCOMM TTY layer initialized
[   20.232000] Bluetooth: RFCOMM ver 1.8
[   51.420000] NET: Registered protocol family 17
[   53.160000] wlan0: Initial auth_alg=0
[   53.160000] wlan0: authenticate with AP 00:18:4d:4b:91:80
[   53.164000] wlan0: RX authentication from 00:18:4d:4b:91:80 (alg=0 transaction=2 status=0)
[   53.164000] wlan0: authenticated
[   53.164000] wlan0: associate with AP 00:18:4d:4b:91:80
[   53.164000] wlan0: RX AssocResp from 00:18:4d:4b:91:80 (capab=0x411 status=0 aid=2)
[   53.164000] wlan0: associated
[   59.712000] NET: Registered protocol family 10
[   59.712000] lo: Disabled Privacy Extensions
[   59.712000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   70.352000] wlan0: no IPv6 routers present

```

```

:~$ gcc -v
Using built-in specs.
Target: i486-linux-gnu
Configured with: ../src/configure -v --enable-languages=c,c++,fortran,objc,obj-c++,treelang --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --with-gxx-include-dir=/usr/include/c++/4.1.3 --program-suffix=-4.1 --enable-__cxa_atexit --enable-clocale=gnu --enable-libstdcxx-debug --enable-mpfr --enable-checking=release i486-linux-gnu
Thread model: posix
gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)

```

So what does it mean? i have to recompile the sound driver every time it stops working? like an update is done.. i have to recompile the whole audio driver? isnt there a fix to this? 

My next question is so if the Release Candidate can work with alsa why not the stable release? am surprised....

---

### Post by linux23dragon on 2007-10-20
> **amvella said:**
> dude it started working agiain after i recompiled the driver, lib and utls

now i will give u the outputs for the commands you gave me.. 

```

~$ cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf8400000 irq 23

``` 

So what does it mean? i have to recompile the sound driver every time it stops working? like an update is done.. i have to recompile the whole audio driver? isnt there a fix to this? 

My next question is so if the Release Candidate can work with alsa why not the stable release? am surprised....

That is a good question.  I was hoping that the output you sent will tale a story.

Was the update just a single package (daylight saving or something)?  Or a combination of packages?

Normally you only need to recompile if the kernel was updated or upgraded.  So it would be a surprise (to me) if we would need to recompile Alsa system with any updates.

---

### Post by linux23dragon on 2007-10-20
> **Gunner_Sr said:**
> None of this worked for me. The easiest that I followed and it worked was the following.

[http://ubuntuforums.org/showpost.php?p=3475485&postcount=235](http://ubuntuforums.org/showpost.php?p=3475485&postcount=235)

-cg

Thanks for the report.  I'll add this link to the collection :-)

---

### Post by linux23dragon on 2007-10-20
I have rewritten the howto so it is easer to follow.

Enjoy :-)

---

### Post by ilkkal on 2007-10-20
I'm getting this lots of this kind of error in dmesg:
[   17.508000] snd_hda_intel: disagrees about version of symbol snd_ctl_add
[   17.508000] snd_hda_intel: Unknown symbol snd_ctl_add
[   17.508000] snd_hda_intel: disagrees about version of symbol snd_pcm_new
[   17.508000] snd_hda_intel: Unknown symbol snd_pcm_new
[   17.508000] snd_hda_intel: disagrees about version of symbol snd_pcm_limit_hw_rates
[   17.508000] snd_hda_intel: Unknown symbol snd_pcm_limit_hw_rates
[   17.508000] snd_hda_intel: disagrees about version of symbol snd_card_register
[   17.508000] snd_hda_intel: Unknown symbol snd_card_register
[   17.508000] snd_hda_intel: disagrees about version of symbol snd_card_free
[   17.508000] snd_hda_intel: Unknown symbol snd_card_free
[   17.508000] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_preallocate_pages_for_all

Any idea?

---

### Post by linux23dragon on 2007-10-20
> **ilkkal said:**
> I'm getting this lots of this kind of error in dmesg:
[   17.508000] snd_hda_intel: disagrees about version of symbol snd_ctl_add
[   17.508000] snd_hda_intel: Unknown symbol snd_ctl_add
[   17.508000] snd_hda_intel: disagrees about version of symbol snd_pcm_new
[   17.508000] snd_hda_intel: Unknown symbol snd_pcm_new
[   17.508000] snd_hda_intel: disagrees about version of symbol snd_pcm_limit_hw_rates
[   17.508000] snd_hda_intel: Unknown symbol snd_pcm_limit_hw_rates
[   17.508000] snd_hda_intel: disagrees about version of symbol snd_card_register
[   17.508000] snd_hda_intel: Unknown symbol snd_card_register
[   17.508000] snd_hda_intel: disagrees about version of symbol snd_card_free
[   17.508000] snd_hda_intel: Unknown symbol snd_card_free
[   17.508000] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_preallocate_pages_for_all

Any idea?

Did you install Alsa libs as well, or just the kernel driver?

---

### Post by ilkkal on 2007-10-20
> **linux23dragon said:**
> Did you install Alsa libs as well, or just the kernel driver?

I installed all of them. (all of the files in the guide)

---

### Post by linux23dragon on 2007-10-20
> **ilkkal said:**
> I installed all of them. (all of the files in the guide)

It is a possible side effect you will have with the Ubuntu kernel, as it is not a standard build.   

Did you use kernel driver method 1 or 2.  Does the sound work?

Edit:- I might put a 3rd method that will compile and replace the whole Alsa-driver system.  I've done that before in Ubuntu-7.10, without success.  Infact the alsa system would not work at all (until I reinstalled the kernel itself).
Hopefully Gusty might be a different story.

---

### Post by ilkkal on 2007-10-20
> **linux23dragon said:**
> It is a possible side effect you will have with the Ubuntu kernel, as it is not a standard build.   

Did you use kernel driver method 1 or 2.  Does the sound work?

Edit:- I might put a 3rd method that will compile and replace the whole Alsa-driver system.  I've done that before in Ubuntu-7.10, without success.  Infact the alsa system would not work at all (until I reinstalled the kernel itself).
Hopefully Gusty might be a different story.

I did the method 2. No, it doesn't work. Well, you could add the third way so I can test what happens :)

---

### Post by linux23dragon on 2007-10-20
> **ilkkal said:**
> I did the method 2. No, it doesn't work. Well, you could add the third way so I can test what happens :)

Done :)  May the good gods be with you :-)

---

### Post by ilkkal on 2007-10-20
I think there were no Gods with me. I get no errors to dmesg, but there is still no sound... weird don't you think? Should I reinstall the libs etc. after completely replacing the old alsa-driver with method 3?

---

### Post by ewel on 2007-10-20
I have hp dv6599, tried almost every method from this forum to run sound and it's still not working :(

```

...
ALSA modules were successfully compiled.

`pci/hda/snd-hda-intel.ko' -> `/lib/modules/2.6.22-14-generic/ubuntu/media/snd-hda-intel/snd-hda-intel.ko'
FATAL: Error inserting snd_hda_intel (/lib/modules/2.6.22-14-generic/updates/sound/pci/hda/snd-hda-intel.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```

dmesg:
```

[33161.288000] snd_hda_intel: disagrees about version of symbol snd_dma_free_pages
[33161.288000] snd_hda_intel: Unknown symbol snd_dma_free_pages
[33161.288000] snd_hda_intel: disagrees about version of symbol snd_dma_alloc_pages
[33161.288000] snd_hda_intel: Unknown symbol snd_dma_alloc_pages

```

---

### Post by dawdler on 2007-10-20
Hi,

I have a dell inspiron 1420 that uses the Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02).

Here is my "cat /proc/asound/cards":
```
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfe9fc000 irq 20

```

I am having the "no sound" issue with Gutsy similar to everyone else who has been following this thread.  Here is what I have done thus far:

I tried updating the alsa module using the module-assistant [method]("http://ubuntuforums.org/showthread.php?t=569082&page=2")...Still no sound.

I removed the alsa package using apt-get and rebooted...Still no sound.

I downloaded and installed the ALSA driver 1.0.15rc3 from source under method 2...Still no sound

I have tried to tweak the /etc/alsa-base config file:
```
option snd_hda_intel model=dell-laptop
```
No sound so I tried...
```
option snd_hda_intel model=laptop
```
Still no sound.

There are no error messages in my log files regarding the snd-hda-intel driver.  And the snd-hda-intel driver is loading (verified using lsmod).  However, I did notice that the loaded driver's size is about 300KB (printed by lsmod).  The newly compiled driver is 2MB while the original snd-hda-intel driver is about 336KB.  Could it be possible that the kernel is still using the old driver?  Is there a way to verify this?

Help!  Having no audio sux...

---

### Post by dawdler on 2007-10-20
Update:
I firmly believe that the kernel is using the older "snd-hda-intel.ko" module on my machine even after installation of the 1.0.15 driver from source.  There exists a copy of the older module in "/lib/modules/2.6.22-14-generic/updates/sound/pci/hda" which the kernel loads.

I went ahead and replaced the older module in that directory with a copy of the newer one.  Rebooted.  The "snd-hda-intel.ko" failed to load.

/var/log/messages showed:

```

Oct 20 17:34:06 dell kernel: [   15.100000] snd_hda_intel: Unknown symbol snd_verbose_printk
Oct 20 17:34:06 dell kernel: [   15.100000] snd_hda_intel: disagrees about version of symbol snd_dma_free_pages
Oct 20 17:34:06 dell kernel: [   15.100000] snd_hda_intel: Unknown symbol snd_dma_free_pages
Oct 20 17:34:06 dell kernel: [   15.100000] snd_hda_intel: disagrees about version of symbol snd_dma_alloc_pages
Oct 20 17:34:06 dell kernel: [   15.100000] snd_hda_intel: Unknown symbol snd_dma_alloc_pages

```

What now?

---

### Post by Jimlas53 on 2007-10-20
I have also been struggling with the alsa driver issue - Toshiba A135 notebook.  As I worked through the different threads regarding building and installing the alsa drivers, I tried modprobe snd-hda-intel, and it complained about not finding the module.  It appears that most of the time the build process puts the snd-hda-intel.ko driver file in another directory, not the one Ubuntu is using.  I found an old module in /lib/modules/2.6.22-14-generic/ubuntu/media/snd-hda-intel
This thread has gotten me going with sound (so far) but it looks like something is a little goofy with the targets the modprobe is using??

---

### Post by Jimlas53 on 2007-10-20
[QUOTE=dawdler;3585828]Update:
I firmly believe that the kernel is using the older "snd-hda-intel.ko" module on my machine even after installation of the 1.0.15 driver from source.  There exists a copy of the older module in "/lib/modules/2.6.22-14-generic/updates/sound/pci/hda" which the kernel loads.

I went ahead and replaced the older module in that directory with a copy of the newer one.  Rebooted.  The "snd-hda-intel.ko" failed to load.
--snip




Yes, this is part of it, although one module depends on the other, that is the module in /lib/modules/2.6.22-14-generic/updates/sound/pci/hda is also needed and loaded, and it is not the same as the one in /lib/modules/2.6.22-14-generic/ubuntu/media/snd-hda-intel.  This one is 1.9Mb.


Hope this helps!

---

### Post by linux23dragon on 2007-10-20
> **Jimlas53 said:**
> I have also been struggling with the alsa driver issue - Toshiba A135 notebook.  As I worked through the different threads regarding building and installing the alsa drivers, I tried modprobe snd-hda-intel, and it complained about not finding the module.  It appears that most of the time the build process puts the snd-hda-intel.ko driver file in another directory, not the one Ubuntu is using.  I found an old module in /lib/modules/2.6.22-14-generic/ubuntu/media/snd-hda-intel
This thread has gotten me going with sound (so far) but it looks like something is a little goofy with the targets the modprobe is using??

Thanks for the report.

Yea, that is the problem with distribution modified (3rd party fixed) kernels.  It just makes things worse for us, if the system does not work (like the Intel HDA Alsa drivers)  correctly.   

Did you use driver install method 1, 2 or 3?

Install method 1 and 3 puts the snd-hda-intel.ko in /lib/modules/2.6.22-14-generic/ubuntu/media/snd-hda-intel.

So you used build method 2?

---

### Post by linux23dragon on 2007-10-20
I've changed the options "snd-hda-intel model=del-laptop" to "snd-hda-intel model=ref"

It is understood that the "ref" model option should allow any sound card to work.  But might not have all the full functionality.  In short, I think its a better test option.

I've also changed Driver install method 2 so the "snd-hda-intel.ko" driver, will be installed at  /lib/modules/$(uname -r)/ubuntu/media/snd-hda-intel/


Now I have also been thinking about the codec itself (snd-hda-codec.ko).  It is normally in the same location as the  "snd-hda-intel.ko" driver (/lib/modules/$(uname -r)/kernel/sound/pci/hda/)

Also, the codec itself can be upgraded.  I'll look more into that too.

Any thoughts?

---

### Post by Jimlas53 on 2007-10-20
Heh, I've been doing so much in the last several days, it all blurs!
I think I used the first method, #1, although I could be wrong.  I did verify that the module is now in the /ubuntu... directory, and it is the one I built tonight.

So... Excellent job, my friend!  

This is the kind of thing that drive people right away from linux.  I wish the ubuntu folks had just waited a couple more weeks until these kinds of issues could get resolved before releasing.  Lots of potential linux fanatics are returning to their "real" OS as a result of this release cycle.

Now if I can just get the headphones and speakers separated...  Using the -auto option doesn't help.  I'll have to try the different stack options, I guess.

---

### Post by dawdler on 2007-10-20
There are three copies of the snd-hda-intel module in my "/lib/2.6.22-14-generic/" directory:
```

./kernel/sound/snd-hda-intel.ko
./updates/sound/pci/hda/snd-hda-intel.ko
./ubuntu/media/snd-hda-intel/snd-hda-intel.ko

```

The installation of the latest ALSA driver from source drops in the following new modules:
```

./lib/modules/2.6.22-14-generic/
./lib/modules/2.6.22-14-generic/kernel/
./lib/modules/2.6.22-14-generic/kernel/sound/
./lib/modules/2.6.22-14-generic/kernel/sound/snd-hda-intel.ko
./lib/modules/2.6.22-14-generic/kernel/sound/snd-hwdep.ko
./lib/modules/2.6.22-14-generic/kernel/sound/snd.ko
./lib/modules/2.6.22-14-generic/kernel/sound/snd-mixer-oss.ko
./lib/modules/2.6.22-14-generic/kernel/sound/snd-page-alloc.ko
./lib/modules/2.6.22-14-generic/kernel/sound/snd-pcm.ko
./lib/modules/2.6.22-14-generic/kernel/sound/snd-pcm-oss.ko
./lib/modules/2.6.22-14-generic/kernel/sound/snd-rtctimer.ko
./lib/modules/2.6.22-14-generic/kernel/sound/snd-seq-device.ko
./lib/modules/2.6.22-14-generic/kernel/sound/snd-seq.ko
./lib/modules/2.6.22-14-generic/kernel/sound/snd-seq-midi-event.ko
./lib/modules/2.6.22-14-generic/kernel/sound/snd-seq-oss.ko
./lib/modules/2.6.22-14-generic/kernel/sound/snd-timer.ko

```

As you can see, the install does not touch "./updates/sound/pci/hda/snd-hda-intel.ko"
& "./ubuntu/media/snd-hda-intel/snd-hda-intel.ko".  I replaced the "./ubuntu/media/snd-hda-intel/snd-hda-intel.ko" with the same one in "./lib/modules/2.6.22-14-generic/kernel/sound/snd-hda-intel.ko".  It did not solve my issue, but the snd-hda-intel module loaded.

When I replaced the "./updates/sound/pci/hda/snd-hda-intel.ko", with the latest module, the snd-hda-intel module failed to load with errors.

Studying my modules.dep file, I see that all the sound module dependencies are directed to the drivers in "./updates/sound/" rather than "./kernel/sound/".  How do I get my modules.dep to look into the "./kernel/sound/" directory for the sound drivers?

I think the using the module-assistant program did this to me...

---

### Post by loopeando on 2007-10-20
Anyone tried this with a Lenovo 3000 N100?

Beacuse I've installed Gutsy and the audio jack sense doesn't work.

Is this a possible solution?

Thx in advance!

---

### Post by linux23dragon on 2007-10-21
Hi dawdler

> **dawdler said:**
> There are three copies of the snd-hda-intel module in my "/lib/2.6.22-14-generic/" directory:
```

./kernel/sound/snd-hda-intel.ko
./updates/sound/pci/hda/snd-hda-intel.ko
./ubuntu/media/snd-hda-intel/snd-hda-intel.ko

```

Can you remove/uninstall linux-backports-modules-* ?  That should remove "/updates/sound/pci/hda/snd-hda-intel.ko" 

Try one of the following:-

[list]The "/kernel/sound/snd-hda-intel.ko", is the result of the Alsa driver "make install" command.

Try to move "/kernel/sound/snd-hda-intel.ko" somewhere out side of the kernel modules   .  You might need to use the "sudo depmod -ae" afterwards.  

You can move "snd-hda-intel.ko"  back to "/kernel/sound/snd-hda-intel.ko" to recover.[/list]



[list]The "/ubuntu/media/snd-hda-intel/snd-hda-intel.ko" is the default location  of "snd-hda-intel.ko".  This is because the developers have tried to fix it.  So I had installed the new (1.0.15) "snd-hda-intel.ko" in that location as well.   

Try moving "/ubuntu/media/snd-hda-intel/snd-hda-intel.ko" 
(followed by "depmod -ae) out of the kernel, just to see if the system will work without it.

You can move "snd-hda-intel.ko"  back to  "/ubuntu/media/snd-hda-intel/snd-hda-intel.ko" to recover[/list]




> **dawdler said:**
> 
Studying my modules.dep file, I see that all the sound module dependencies are directed to the drivers in "./updates/sound/" rather than "./kernel/sound/".  How do I get my modules.dep to look into the "./kernel/sound/" directory for the sound drivers?

I think the using the module-assistant program did this to me...

May be,  See what happens if you uninstall linux-backports-modules-*


Edit: Ive updated the first post in regards to uninstalling the linux-backports-modules-*, and the Alsa WiKi for people that already has sound working

---

### Post by linux23dragon on 2007-10-21
> **loopeando said:**
> Anyone tried this with a Lenovo 3000 N100?

Beacuse I've installed Gutsy and the audio jack sense doesn't work.

Is this a possible solution?

Thx in advance!


If the sound works, try to use [ the Alsa wiki]("http://alsa.opensrc.org/index.php/Hda#cooliris") first.

---

### Post by dawdler on 2007-10-21
linux23dragon,

I am pretty sure that running module-assistant for alsa installed the alsa drivers into the "/lib/modules/2.6.22-14-generic/updates".  Not knowing how to remove these modules using module-assistant, I manually deleted the entire directory.  I also deleted all the "/lib/modules/2.6.22-14-generic/module.*" files.  Depmod and rebooted.  No sound and snd-hda-intel module (v1.0.15rc3) failed to load.

> Try moving "/ubuntu/media/snd-hda-intel/snd-hda-intel.ko" 
(followed by "depmod -ae) out of the kernel, just to see if the system will work without it.

I then uninstalled the 1.0.15rc3 drivers and I also deleted the module in the "./ubuntu/media/snd-hda-intel/" directory.  I built the 1.0.15 drivers from source and installed.  No sound but the drivers loaded w/o error and it was definitely the 1.0.15 driver.  The other module in /ubuntu/media does nothing...

I then uninstalled the 1.0.15 driver and rebuilt the drivers using the "--with-card-options=all" in addition to the "--with-cards=hda-intel" option.  Installed, rebooted...still no sound and again the drivers loaded w/o error.

I am running out of things to try...

As a note, I performed depmod whenever I made changes.  Oh, I also uninstalled the backports thing and no change.  I will try uninstalling and running with absolutely no alsa drivers and see what happens.

Do you know why there are recommendations to use 1.0.15rc3 for some ppl even though 1.0.15 is a recent final release?

---

### Post by ewel on 2007-10-21
copying snd-hda-intel.ko

from 

```
/lib/modules/2.6.22-14-generic/ubuntu/media/snd-hda-intel
```

to

```
/lib/modules/2.6.22-14-generic/kernel/sound
```

and then 

```
sudo modprobe snd-hda-intel
```


and then I tried tu turn on sound and...
works for me! thanks for advices :-]

---

### Post by linux23dragon on 2007-10-21
> **dawdler said:**
> 

I am running out of things to try...

As a note, I performed depmod whenever I made changes.  Oh, I also uninstalled the backports thing and no change.  I will try uninstalling and running with absolutely no alsa drivers and see what happens.

Do you know why there are recommendations to use 1.0.15rc3 for some ppl even though 1.0.15 is a recent final release?

Thanks for the report dawdler.


It's been known that some Alsa driver releases can change the device functionality of the HDA sound cards.  One release candidate will allow you to have the microphone working correctly, while another Alsa release won't.

The default Alsa drivers in a given linux kernel can also be a release candidate too.  Like in linux-2.6.20:

```

core2@core2-desktop:~$ cat  /proc/asound/version 
Advanced Linux Sound Architecture Driver Version 1.0.14rc1 (Tue Jan 09 09:56:17 2007 UTC).
```


Try removing   ~/.asoundrc and ~/.asoundrc.asoundconf.  Logout and log back in.

You might need to reinstall the Linux kernel (Using Synaptic PM), before you try out a different Alsa driver installation method. 

Hope this helps

---

### Post by linux23dragon on 2007-10-21
Thanks for all of the reports guys.  I've added some more notes and fixes based on information thats been provided.

Remember, not everyone has the same system or Intel HDA sound cards.  So the results do very.

Keep those reports coming :-)

---

### Post by dawdler on 2007-10-21
I finally got my sound to work!:)

I am using the 1.0.15 alsa build from source on my dell 1420.  I tweaked different things so I am not too sure what exactly "fixed" it, but I think mucking around with the alsamixer did it.  I think the sound was fixed too low or something...grrr

Lessons learned:
1.  Make sure the alsa module being loaded is the correct version.  Check using the ```
cat /proc/asound/version
``` command.  Fix it if its not correct and make sure the driver loads along with other snd drivers.
2.  After reboot, check to see if /dev/snd exists.  If it doesn't, follow the help in the "INSTALL" file that comes with the source.
3.  If you execute ```
cat /proc/asound/cards
``` and it correctly prints, then drivers are ok.  Mess around with the alsamixer and hope that you get sound.

If this didn't help, check out the [alsa troubleshooting wiki]("http://alsa.opensrc.org/TroubleShooting") as well as this thread for any additional insight.

Linux is a love,hate relationship...

Thanks all and good night!

---

### Post by linux23dragon on 2007-10-21
> **dawdler said:**
> I finally got my sound to work!:)

I am using the 1.0.15 alsa build from source on my dell 1420.  I tweaked different things so I am not too sure what exactly "fixed" it, but I think mucking around with the alsamixer did it.  I think the sound was fixed too low or something...grrr

Lessons learned:
1.  Make sure the alsa module being loaded is the correct version.  Check using the ```
cat /proc/asound/version
``` command.  Fix it if its not correct and make sure the driver loads along with other snd drivers.
2.  After reboot, check to see if /dev/snd exists.  If it doesn't, follow the help in the "INSTALL" file that comes with the source.
3.  If you execute ```
cat /proc/asound/cards
``` and it correctly prints, then drivers are ok.  Mess around with the alsamixer and hope that you get sound.

If this didn't help, check out the [alsa troubleshooting wiki]("http://alsa.opensrc.org/TroubleShooting") as well as this thread for any additional insight.

Linux is a love,hate relationship...

Thanks all and good night!

Good work dawdler :-)

Thanks for the report.  I've updated the post in regards to your findings.

---

### Post by kyfho23 on 2007-10-21
My lack of sound was fixed by using the Gutsy Intel HD Audio Controller link in the first paragraph of the original post ([https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)). 
 I installed the Linux-backports-modules-generic through Synaptic/Adept.
 Scroll down to Workarounds, use Method A (WARNING: 3rd step took a few minutes to finish on a Core2Duo 2.4 GHz machine), and reboot.

I'm using the HDA-Intel sound card built into a DQ965 motherboard - onboard audio, in other words.

My rig is a customized Systemax, built around the above mobo.

IF YOU DO GET YOUR SOUND SYSTEM WORKING, YOU MIGHT WANT TO LET THE MAINTAINERS KNOW USING THE UBUNTU/KUBUNTU/XUBUNTU DEVICE DATABASE (it's in my kubuntu menu/system.) This seems to be a pretty widespread bug, and all the data they can get will help them. 

Good Luck.


(and linux23dragon: ALL HAIL ERIS!!!!! she certainly seems to be in charge here)

---

### Post by linux23dragon on 2007-10-21
> **kyfho23 said:**
> 
IF YOU DO GET YOUR SOUND SYSTEM WORKING, YOU MIGHT WANT TO LET THE MAINTAINERS KNOW USING THE UBUNTU/KUBUNTU/XUBUNTU DEVICE DATABASE (it's in my kubuntu menu/system.) This seems to be a pretty widespread bug, and all the data they can get will help them. 

Good Luck.


(and linux23dragon: ALL HAIL ERIS!!!!! she certainly seems to be in charge here)
Hi kyfho23

Thanks for the report.  I'll add that important information in the first post.

Excellent work :-)

---

### Post by loopeando on 2007-10-21
> **linux23dragon said:**
> If the sound works, try to use [ the Alsa wiki]("http://alsa.opensrc.org/index.php/Hda#cooliris") first.

Tried it and got nothing.

Sound works but the jack sense doesn't.

It worked with Feisty's default kernel (2.6.20-15), then it was broken with Feisty's kernel update (2.6.20-15) and it remaings broken with Gutsy.

Any advice?

---

### Post by linux23dragon on 2007-10-21
> **loopeando said:**
> Tried it and got nothing.

Sound works but the jack sense doesn't.

It worked with Feisty's default kernel (2.6.20-15), then it was broken with Feisty's kernel update (2.6.20-15) and it remaings broken with Gutsy.

Any advice?

Hi loopeando

OK,  try to upgrading the driver itself.  Remember to reinstall the kernel if you don't have the desired results (unless you like the sound you hair :-))and post a bug report.

Good luck

---

### Post by Jimlas53 on 2007-10-21
linux23dragon, has anyone gotten the headphone/speaker muting issue resolved?  This also seems to be common across a number of the Intel-based audio systems.
Does this go back to some of your earlier comments regarding the unique kernel configurations being done at the distro level?
I think the devs have their hands very full in the next couple of weeks!

-Doug

---

### Post by linux23dragon on 2007-10-21
> **Jimlas53 said:**
> linux23dragon, has anyone gotten the headphone/speaker muting issue resolved?  This also seems to be common across a number of the Intel-based audio systems.
Does this go back to some of your earlier comments regarding the unique kernel configurations being done at the distro level?
I think the devs have their hands very full in the next couple of weeks!

-Doug

I've been seeing mixed reports about the headphones issues.  Some people say it works with Alsa-driver-1.0.15rc3 or Alsa-driver-1.0.15rc1. And other users (with differnt models) still have issues.  But I have had no current feed back with the new Alsa-driver-1.0.15.


It could be due to the fact that we need more configuration setups in ~/.asoundrc or in /etc/modules.conf.

At the momment, its hard to say if that this is the fault of the driver, or our configurations.  Its hard to use the [*_[COLOR="Blue"]Alsa Matrix WiKi[/COLOR]_*]("http://www.alsa-project.org/main/index.php/Matrix:Vendor-Intel"), since some of the models are not listed yet.
EDIT: Keep in mind that the "/etc/udev/rules.d/40-alsa.rules" file, should take care of things (in regards to the Alsa driver configuration).  But if you find other methods then please post them for all to see.



If anyone would like to play around with the configurations, or knows how they got their external  microphone to work is welcome to post their solutions (with the model used).

---

### Post by linux23dragon on 2007-10-22
Removed Alsa driver installation.

---

### Post by crazyforpurple on 2007-10-24
hello linux 23 dragon, 

i want to thank you so very much for your posting here and the amount of time you ahve dedicated to helping others get their sound working.... i am so very greateful as i have tried numerous things to get it working on my laptop and then jim sent me the link to your post and it worked!!!!

so heres what i did for my TOSHIBA SATELLITE A135-S7404: 
(hoping that this will give hope to others who have this latop!)

1.       after installing ubuntu gutsy i had no sound and no sound cards were detected. 
2.       when i tried the command "cat /proc/asound/cards" it would just say no soundcards installed
3.        i couldnt even find these files....
          "Remove ~/.asoundrc and ~/.asoundrc.asoundconf."

           let alone remove them! so i went on to the next step:

4.        i then went onto your next step:
           "Install Ubuntu kernel back ports (linux-backports-modules-* ). You may need to run the above command (Possible conflicting driver issue). Then reboot."

to do this i did the following:

go to system, administration, synaptic package manager, 
type in your password
in synaptic package manager, go to settings, repositories

under the "ubuntu software" tab I checked on each entry under "downloadable from the internet" and unchecked the cd/dvd option. 

then under the "updates" tab I checked everything including the gutsy backports. 
close the repositories box and then click reload in the synaptic package manager. 

5.      I don't think its necessary at this time but I restarted my laptop for good measure at this point. 

6.      I then went back into the synaptic package manager and ran a search for backports

7.      I also went to applications, accessories, terminal and ran the following command
uname -r to find the details of my kernal.

it came back with 2.6.22-14-generic

8.     In the synaptic package manager I had many options from my search and I wasnt sure which one I should use... I narrowed it down to 

linux-backports-modules (which in the info said "Generic Linux backported drivers.")
and 
linux-backports-modules-gene-2.6.22.14.21 (which in the info said "Backported drivers for generic kernel image")

I'm not quite sure why, but I clicked on the latter on and marked it for install. I then clicked "apply" and once it was all done I restarted the laptop and on restart I had sound!!!!!! :)


This may not be worth noting but when I use the term "restart" I actually shut down and then start up the laptop as using the "restart" option on mine means that it hangs before the log in screen. 

Thanks again and I hope this helps someone else xxx

I am now off to configure my wireless connection and am praying that it doesn't affect the sound :???:

love lucy xxxxxxxxxxxxxxxxxxxxxxx

---

### Post by linux23dragon on 2007-10-25
> **crazyforpurple said:**
> 

4.        i then went onto your next step:
           "Install Ubuntu kernel back ports (linux-backports-modules-* ). You may need to run the above command (Possible conflicting driver issue). Then reboot."

love lucy xxxxxxxxxxxxxxxxxxxxxxx

Thanks Lucy, for that report.

I've updated the post to fix that (Possible conflicting driver issue) statement, that I forgot to remove earlier.

---

### Post by lightningstormz on 2007-10-25
Realtek has ALSA drivers specifically designed for the Intel HD Audio. Go to this link [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=24&Level=4&Conn=3&DownTypeID=3#2]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=24&Level=4&Conn=3&DownTypeID=3#2")

There is a readme document inside that tells you how to configure it. You will also need kernel sources and some other packages to compile it. It works very well with my HP dv9500t.

---

### Post by loopeando on 2007-10-25
> **lightningstormz said:**
> Realtek has ALSA drivers specifically designed for the Intel HD Audio. Go to this link [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=24&Level=4&Conn=3&DownTypeID=3#2]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=24&Level=4&Conn=3&DownTypeID=3#2")

There is a readme document inside that tells you how to configure it. You will also need kernel sources and some other packages to compile it. It works very well with my HP dv9500t.

I'll try this on my Lenovo 3000 N100.

Thx!

EDIT: Damn. My codec is not Realtek, it's from Analog Devices.

---

### Post by fung on 2007-11-26
Did 4 weeks of no updates mean everyone somehow fixed it? I'm still in the dark here so if anyone has anymore to add, that would be great to my friends and I here at this thread [http://ubuntuforums.org/showthread.php?p=3838160](http://ubuntuforums.org/showthread.php?p=3838160) thanks

---

### Post by linux23dragon on 2007-11-28
> **fung said:**
> Did 4 weeks of no updates mean everyone somehow fixed it? I'm still in the dark here so if anyone has anymore to add, that would be great to my friends and I here at this thread [http://ubuntuforums.org/showthread.php?p=3838160](http://ubuntuforums.org/showthread.php?p=3838160) thanks

I've put an update to explain why I think this thread is solved.  Not to mention that it is asking a bit much for a end user to start going under the hood of a operating system that he/she has never used before.  Also, most people (like myself) have found that you no longer can compile Alsa-1.0.15 into the current Ubuntu-7.10 kernel (like you used too with Ubuntu-7.04) without having some sort of driver issues.

That could be just me not using "modules assistant", or something.  But some people still had issues if they did use "modules assistant".  I suspect that it is to do with Ubuntu support reasons (which is a good thing), but thats just me guessing.  



I've looked at your [*_**[COLOR="Blue"]thread[/COLOR]**_*]("http://ubuntuforums.org/showthread.php?p=3838160") and it appears that you were able to get sound to work (at some stage), on the same day.

---

### Post by steinkaare on 2007-11-28
I'm trying to use method H. It says i have to download the latest alsa driver. Well i'm trying, the first step works fine, but when it comes to installing and compiling the lates driver i'm lost. [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto) I'm using this guide. when using this command: 
sudo mkdir -p /usr/src/alsa
cd /usr/src/alsa
sudo cp ~/downloads/alsa* .
sudo tar xjf alsa-driver*.bz2
sudo tar xjf alsa-lib*.tar.bz2
sudo tar xjf alsa-utils*.tar.bz2

this happens.

kai@kai-laptop:/usr/src/alsa$ sudo tar xjf alsa-lib*.tar.bz2
tar: alsa-lib*.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
kai@kai-laptop:/usr/src/alsa$ sudo tar xjf alsa-utils*.tar.bz2
tar: alsa-utils*.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
kai@kai-laptop:/usr/src/alsa$
kai@kai-laptop:/usr/src/alsa$     *
bash: *: command not found
kai@kai-laptop:/usr/src/alsa$

Someone please tell me what im doing wrong!

---

### Post by linux23dragon on 2007-11-28
> **steinkaare said:**
> I'm trying to use method H. It says i have to download the latest alsa driver. Well i'm trying, the first step works fine, but when it comes to installing and compiling the lates driver i'm lost. [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto) I'm using this guide. when using this command: 
sudo mkdir -p /usr/src/alsa
cd /usr/src/alsa
sudo cp ~/downloads/alsa* .
sudo tar xjf alsa-driver*.bz2
sudo tar xjf alsa-lib*.tar.bz2
sudo tar xjf alsa-utils*.tar.bz2

this happens.

kai@kai-laptop:/usr/src/alsa$ sudo tar xjf alsa-lib*.tar.bz2
tar: alsa-lib*.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
kai@kai-laptop:/usr/src/alsa$ sudo tar xjf alsa-utils*.tar.bz2
tar: alsa-utils*.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
kai@kai-laptop:/usr/src/alsa$
kai@kai-laptop:/usr/src/alsa$     *
bash: *: command not found
kai@kai-laptop:/usr/src/alsa$

Someone please tell me what im doing wrong!


Try doing this : -

```

cd /usr/src/alsa &&
sudo cp ~/downloads/alsa* /usr/src/alsa/ &&
sudo tar xjf alsa-driver*.bz2 &&
sudo tar xjf alsa-lib*.tar.bz2 &&
sudo tar xjf alsa-utils*.tar.bz2
```

---

### Post by fung on 2007-11-28
> **linux23dragon said:**
> I've put an update to explain why I think this thread is solved.  Not to mention that it is asking a bit much for a end user to start going under the hood of a operating system that he/she has never used before.  Also, most people (like myself) have found that you no longer can compile Alsa-1.0.15 into the current Ubuntu-7.10 kernel (like you used too with Ubuntu-7.04) without having some sort of driver issues.

That could be just me not using "modules assistant", or something.  But some people still had issues if they did use "modules assistant".  I suspect that it is to do with Ubuntu support reasons (which is a good thing), but thats just me guessing.  



I've looked at your [*_**[COLOR="Blue"]thread[/COLOR]**_*]("http://ubuntuforums.org/showthread.php?p=3838160") and it appears that you were able to get sound to work (at some stage), on the same day.

What did you mean you no longer can compile Alsa 1.0.15 into the current kernel? I think I've done it and haven't run into any problems.. And yes I did end up getting sound but the headphones don't work :( maybe that's the driver issue you were talking about?

---

### Post by linux23dragon on 2007-11-28
> **fung said:**
> What did you mean you no longer can compile Alsa 1.0.15 into the current kernel? I think I've done it and haven't run into any problems.. And yes I did end up getting sound but the headphones don't work :( maybe that's the driver issue you were talking about?

The problems are a mixed bag, depending on the sytem setup used.  You might see lots of Alsa driver messages in the kernel log.

---

### Post by steinkaare on 2007-11-30
> **linux23dragon said:**
> Try doing this : -

```

cd /usr/src/alsa &&
sudo cp ~/downloads/alsa* /usr/src/alsa/ &&
sudo tar xjf alsa-driver*.bz2 &&
sudo tar xjf alsa-lib*.tar.bz2 &&
sudo tar xjf alsa-utils*.tar.bz2
```

this is what i get 
cp: cannot stat `/home/kai/downloads/alsa*': No such file or directory
kai@kai-laptop:/usr/src/alsa$
im such a noob

---

### Post by linux23dragon on 2007-11-30
> **steinkaare said:**
> this is what i get 
cp: cannot stat `/home/kai/downloads/alsa*': No such file or directory
kai@kai-laptop:/usr/src/alsa$
im such a noob

Hi steinkaare

Do you know were the Alsa software was saved too?  The commands I have given assumes that the Alsa software was saved in the /home/kai/downloads folder.

---

### Post by airjaw on 2007-11-30
Ok so sound works.. thanks for the fix.  I don't know if anyone else has asked this question  but I didn't feel like going through 9 pages of this thread to find it.

Usually the volume settings have options for a lot of different options:

Master , Headphone, PCM, Line-in, CD, Microphone, PC speaker.

How come there is only one option on my laptop (Inspiron 1520), "Volume"
Is there any way to get the other options?

Also, the volume is not synced with XMMS.  I have not tried with other music programs.
What this means is that when you change the volume in xmms, the volume is unaffected.
'

---

### Post by linux23dragon on 2007-11-30
> **airjaw said:**
> Ok so sound works.. thanks for the fix.  I don't know if anyone else has asked this question  but I didn't feel like going through 9 pages of this thread to find it.

Usually the volume settings have options for a lot of different options:

Master , Headphone, PCM, Line-in, CD, Microphone, PC speaker.

How come there is only one option on my laptop (Inspiron 1520), "Volume"
Is there any way to get the other options?

Also, the volume is not synced with XMMS.  I have not tried with other music programs.
What this means is that when you change the volume in xmms, the volume is unaffected.
'

Hi airjaw

Open the Volume Control and o to Edit->Preferences.  Select what you need, then your good to go.
You can also change the sound device driver in Volume Control (File->Change Device) to see even more sound device options.


Edit : - This might not be needed, but it won't hurt ether.

Add more Alsa functionality by installing more Alsa driver tools : -
  
```
sudo apt-get install alsa-base alsa-tools alsa-oss alsa-utils alsa-firmware-loaders
```

Reboot

This may not even be needed anymore but you can see if you can get more sound card functionality by adding a model name.

Edit the /etc/modprobe.d/alsa-base file : -
```
sudo gedit /etc/modprobe.d/alsa-base
```

And add this line : -
```
options snd-hda-intel model=dell-laptop
```

Reboot.

If adding a sound card model to /etc/modprobe.d/alsa-base did nothing for you, then you may remove (or just leave) the model info from  /etc/modprobe.d/alsa-base.

---

### Post by josethemute on 2007-12-08
I don't know if this has been posted yet, but this was my solution to this problem:

Basically, I wanted alsa 1.0.15 instead of 1.0.14, so I built the 1.0.15 module from source.  I downloaded the source from the following site: 
[http://www.alsa-project.org/main/index.php/Download](http://www.alsa-project.org/main/index.php/Download)

I needed the driver file, the library file, and the utilities file.  I then followed this guide on the ubuntu website:
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

This may have already been posted, but I didn't see anything about it in the first post, so I hope this helps someone.

---

### Post by zyg0t3 on 2007-12-15
> **Gunner_Sr said:**
> None of this worked for me. The easiest that I followed and it worked was the following.

[http://ubuntuforums.org/showpost.php?p=3475485&postcount=235](http://ubuntuforums.org/showpost.php?p=3475485&postcount=235)

-cg

I agree with this statement. If you've updated your kernel you should check out that link.

or do this.

> 

NOTE: Change the kernel version as necessary.

There are two copies of the snd_hda_intel,ko file lurking in /lib/modules:
Code:

/lib/modules/2.6.22-14-generic/ubuntu/media/snd-hda-intel/snd-hda-intel.ko
/lib/modules/2.6.22-14-generic/kernel/sound/pci/hda/snd-hda-intel.ko

To solve this problem, run these commands in the a terminal under "su" privileges
Code:

rm /lib/modules/2.6.22-14-generic/ubuntu/media/snd-hda-intel/snd-hda-intel.ko
ln -s /lib/modules/2.6.22-14-generic/kernel/sound/pci/hda/snd-hda-intel.ko /lib/modules/2.6.22-14-generic/ubuntu/media/snd-hda-intel/snd-hda-intel.ko

gedit /etc/modules

Add these lines to the bottom:
Code:

snd-hwdep
snd-hda-intel

Restart, and it should be working.

A HUGE thanks to benguin, who framed the solution for the kernel update bug.



---

### Post by wrgarrett on 2008-02-11
> **crazyforpurple said:**
> hello linux 23 dragon, 

i 

Thank you so very much! I have tried everything. My sound worked with 6.04 but quit on 7.10 (I skipped 7.04). Followed your instructions to the letter, rebooted and I have sound!

You rock!

---

### Post by Ebbonified on 2008-03-09
Thanks! It worked!

---

