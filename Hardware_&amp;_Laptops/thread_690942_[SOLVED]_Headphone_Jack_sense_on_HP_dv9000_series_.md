---
title: "[SOLVED] Headphone Jack sense on HP dv9000 series laptops"
date: 2008-02-08
forum: Hardware &amp; Laptops
---

### Post by cdtech on 2008-02-08
**[SIZE="5"][COLOR="DarkRed"]Howto: Headphone Jack sense on HP dv9000 series laptops[/COLOR][/SIZE]**
[B]
My setup :: [/B]

HP DV9608nr laptop
Gutsy 7.10
kernel: 2.6.22-14-generic 86_64 bit
[COLOR="Red"]Codec = **Conexant** CX20549 (Venice)[/COLOR]

[B]These procedures are a compilation of many different sites. The steps are made up of trial and error from others and my self's personal experiences. Although these procedures work for some, they may not work for others. I've tried to make this as fail safe as possible by saving a backup of the old drivers  to your home directory and explaining the procedures for re installation (if that situation arises). If you follow these procedures exactly as they are laid out you could have a working headphone sense switch in just a matter of minutes.
[/B]
For a fully functional ALSA installation, you will need the driver, the libs and the utilities. ALSA has it's own devices in /dev/snd, for example /dev/snd/pcmC0D1 is Card 0, Device 1.** Loading the ALSA devices is explained in section 4)**.
[B]
As always, any suggestions are totally welcome. Please don't hesitate to send me a private message if you need one on one help with these procedures.
[/B]
[COLOR="Blue"][SIZE="2"]**Good Luck.....**[/SIZE][/COLOR]

**[SIZE="4"]1) Preparing the installation ::[/SIZE]**

**Uninstall these packages:**
```
sudo apt-get remove --purge alsa-base alsa-tools
```

**And Install these packages:**
```
sudo apt-get install linux-headers-`uname -r` build-essential libncurses5-dev libncursesw5-dev ncurses-term alsa-tools-gui gettext po-debconf debhelper quilt alsa-base libc6-dev
```

**[SIZE="3"][COLOR="Red"]!!! be sure not to uninstall alsa-utils as it will uninstall your gdm too !!![/COLOR][/SIZE]**

**Back-up your current configuration:**

```
tar -zcvf ~/original-drivers.tgz /lib/modules/`uname -r`/kernel/sound
```

This will tar and save the current alsa drivers into your home directory. If all fails you will be able to convert back to your originals (see steps below for replacing original drivers).

**Make a directory for the alsa packages:**
(I chose to call the directory according to the alsa version)

```
sudo mkdir /usr/src/alsa-15rc
cd /usr/src/alsa-15rc
```

**Get alsa packages:**

```
wget ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.15rc3.tar.bz2
wget ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.15rc3.tar.bz2
wget ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.15rc1.tar.bz2
wget ftp://ftp.alsa-project.org/pub/firmware/alsa-firmware-1.0.15rc1.tar.bz2

```
**Unpack archives:**

```
tar xvf alsa-driver-1.0.15rc3.tar.bz2
tar xvf alsa-lib-1.0.15rc3.tar.bz2
tar xvf alsa-utils-1.0.15rc1.tar.bz2
tar xvf alsa-firmware-1.0.15rc1.tar.bz2
```

**you wont need the tar's afterwards so just remove them if you want:**

```
sudo rm *.bz2
```
[B][SIZE="4"]
2) Finding the Subsystem ID ::[/SIZE][/B]

To find your Subsystem Id - on the command line type:

```
cat /proc/asound/card0/codec#0
```

The results will show:

```
**Codec: Conexant CX20549 (Venice)** ## this is the conexant codec for the file to edit later
Address: 0
Vendor Id: 0x14f15045
**Subsystem Id: 0x103c30cf**  ## this is the id your looking for
Revision Id: 0x100100
Default PCM:
    rates [0x140]: 48000 96000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
**(I've shortened the complete output for space)**
```


**[SIZE="4"]3) Editing the conexant patch ::[/SIZE]**

**Stop alsa:**
    On a command line type:

```
sudo /etc/init.d/alsa-utils stop
```

and edit the conexant patch:

```
sudo gedit /usr/src/alsa-15rc/alsa-driver-1.0.15rc3/alsa-kernel/pci/hda/patch_conexant.c
```

Find the line that looks like this and add this line with your own Subsytem ID and your model as I did here, leaving the cxt5045_laptop intact :: 
**[COLOR="Blue"]SND_PCI_QUIRK(0x103c, 0x30cf, "HP DV9608nr", CXT5045_LAPTOP),[/COLOR]**

**[SIZE="4"]4) Configure alsa with the intel and conexant flags ::[/SIZE]**

**Install driver:**

```
cd alsa-driver-1.0.15rc3
./configure --with-cards=hda-intel --with-card-options=hda-codec-conexant
sudo make
sudo make install
```
**The ALSA drivers have their own devices, you make them using:**
(same directory your in now)
```
sudo ./snddevices
```

**Install alsa-lib:**

```
cd ../alsa-lib-1.0.15rc3
./configure
sudo make
sudo make install
```

**Install alsa-utils:**

```
cd ../alsa-utils-1.0.15rc1
./configure
sudo make 
sudo make install
```

**Install alsa-firmware:**
```

cd ../alsa-firmware-1.0.15rc1
./configure
sudo make 
sudo make install
```

**[SIZE="4"]5) Insert the modules into the kernel ::[/SIZE]**

```
sudo modprobe snd-hda-intel ; modprobe snd-pcm-oss ; modprobe snd-mixer-oss ; modprobe snd-seq-oss

```

**[SIZE="4"]6) Edit the alsa-base file ::[/SIZE]**

```
sudo gedit /etc/modprobe.d/alsa-base
```
Add to the last line, or if you have an "options snd-hda-intel" on the last line just add a model flag after it, such as I did:
```
options snd-hda-intel model=laptop
```

**Reboot....**

**[SIZE="3"][COLOR="DarkRed"]For those of you who have problems with these procedures can replace your original drivers by following this procedure ::[/COLOR][/SIZE]**

**[SIZE="4"]7) Replacing original drivers ::[/SIZE]**

```
sudo cp ~/original-drivers.tgz /original-drivers.tgz
**change to the root directory**
cd /

```
change to user root:
```
sudo -s
```
And untar using this command:
```
gunzip < original-drivers.tgz | tar --overwrite -xvf -
```

This will replace the drivers to their original state.

**Change log::**
02/08/08 - Re formated layout for clarity
02/08/08 - Added install modules into the kernel procedure.
02/08/08 - Edit alsa-base to include model=laptop.
02/09/08 - Added procedure for original driver replacement.
02/09/08 - Added sudo command to step 5 "insert the modules into the kernel".
02/10/08 - Replaced pico editor with the commonly used gedit.
02/10/08 - Removed the modconf procedure.
02/10/08 - Added the procedure to make the ALSA special device files in step 4.
02/12/08 - Edited the sudo gedit alsa location for the conexant patch.
03/04/08 - Thanks to Armenteros for pointing out #1 procedure. Reversed to make uninstall first then reinstall the alsa-base.

---

### Post by theorem_hunter on 2008-02-08
well on step 3:
i edited /usr/src/alsa-15rc/alsa-driver-1.0.15rc3/alsa-kernel/pci/hda/patch_conexant.c

i made my line look like this:
SND_PCI_QUIRK(0x103c, 0x30cf, "HP DV9607us", CXT5045_LAPTOP),

in step 5:
modconf gave an error, lsmod showed that snd-hda-intel was already in use

after rebooting... my sound was lower than it was before & i was still stuck with the 
headhone issue!

im going to try undo this... so i can have normal volume sound... but thank anyway

---

### Post by myddewji13 on 2008-02-08
ok...u mentioned backing up the drivers...can u pls post steps to undo the changes made in case it doesnt work for me...(my sound works now..just got a headphone issue...and last time i tried to fix stuff i ended up reinstalling the entire os..

---

### Post by cdtech on 2008-02-08
> **myddewji13 said:**
> ok...u mentioned backing up the drivers...can u pls post steps to undo the changes made in case it doesnt work for me...(my sound works now..just got a headphone issue...and last time i tried to fix stuff i ended up reinstalling the entire os..

Sorry to hear about your past experiences. Just untar the drivers in the original folder they were backed up from.

---

### Post by myddewji13 on 2008-02-09
could you pls post (or refer me) to the set of commands that will let me do that..?

---

### Post by cdtech on 2008-02-09
> **myddewji13 said:**
> could you pls post (or refer me) to the set of commands that will let me do that..?

Updated procedure to include driver replacement.

---

### Post by myddewji13 on 2008-02-09
sound stops working after i try to update...had to restore old drivers...everything works fine..except the headphone/speaker not muting issue...

---

### Post by Jake90 on 2008-02-09
Hey, I am new to linux so this may seem obvious to some people but I'll post it anyway. A couple of steps didn't work for me, then I tried putting sudo in front and it worked fine. I also just needed the first 5 steps and a reboot  to get everything working. Thanks a lot Cdtech

---

### Post by cdtech on 2008-02-10
> **myddewji13 said:**
> sound stops working after i try to update...had to restore old drivers...everything works fine..except the headphone/speaker not muting issue...

What laptop are you using, I would like to see you get this matter resolved.

What steps did you perform to test the outcome? Did you check your alsamixer to be sure nothing was muted?
During the alsa package install it does state to check your mixer, just need to be sure.

Thanks

---

### Post by myddewji13 on 2008-02-10
I keep getting an error on this step:

```
sudo /etc/init.d/alsasound stop
```

---

### Post by cdtech on 2008-02-10
> **myddewji13 said:**
> I keep getting an error on this step:

```
sudo /etc/init.d/alsasound stop
```

If you could post the error, maybe I can help. If you type on a command line:
```
ls /etc/init.d
```
see if you have a program named **alsasound** in that directory.
You could also try:
```
sudo /etc/init.d/alsa-utils stop
```
I've had an install rename my alsasound to alsasound.new, it took me awhile to find that.

---

### Post by myddewji13 on 2008-02-10
results for the command:

```
ls /etc/init.d
```

are
```
acpid              hostname.sh                      rcS
acpi-support       hotkey-setup                     readahead
alsa-utils         hwclockfirst.sh                  readahead-desktop
anacron            hwclock.sh                       README
apmd               keyboard-setup                   reboot
apparmor           killprocs                        rmnologin
apport             klogd                            rsync
atd                laptop-mode                      screen
avahi-daemon       libpam-foreground                sendsigs
bluetooth          linux-restricted-modules-common  single
bootclean          loopback                         skeleton
bootlogd           makedev                          stop-bootlogd
bootmisc.sh        module-init-tools                stop-bootlogd-single
brltty             mountall-bootclean.sh            stop-readahead
checkfs.sh         mountall.sh                      sysklogd
checkroot.sh       mountdevsubfs.sh                 udev
consolekit         mountkernfs.sh                   udev-finish
console-screen.sh  mountnfs-bootclean.sh            umountfs
console-setup      mountoverflowtmp                 umountnfs.sh
cron               mtab.sh                          umountroot
cupsys             networking                       urandom
dbus               nvidia-kernel                    usplash
dhcdbd             pcmciautils                      vbesave
dns-clean          powernowd                        waitnfs.sh
gdm                powernowd.early                  wpa-ifupdown
glibc.sh           pppd-dns                         x11-common
hal                procps.sh                        xserver-xorg-input-wacom
halt               rc
hdparm             rc.local

```

---

### Post by cdtech on 2008-02-10
Just use ```
sudo alsa-utils stop
``` in that step.

---

### Post by myddewji13 on 2008-02-10
that command does not work either ... it says :

```
myd@myd-laptop:~$ sudo alsa-utils stop
sudo: alsa-utils: command not found
myd@myd-laptop:~$ sudo stop alsa-utils
stop: Unknown job: alsa-utils
myd@myd-laptop:~$ 

```

---

### Post by cdtech on 2008-02-10
> **myddewji13 said:**
> that command does not work either ... it says :

```
myd@myd-laptop:~$ sudo alsa-utils stop
sudo: alsa-utils: command not found
myd@myd-laptop:~$ sudo stop alsa-utils
stop: Unknown job: alsa-utils
myd@myd-laptop:~$ 

```

I'm sorry for the type-O should be :
```
sudo /etc/init.d/alsa-utils stop
```
That should work for you.

---

### Post by myddewji13 on 2008-02-10
ok that worked...but the next step doesnt... :( ... i feel like an idiot

---

### Post by cdtech on 2008-02-10
> **myddewji13 said:**
> ok that worked...but the next step doesnt... :( ... i feel like an idiot

No need to feel that way, we'll get it worked out.

The next step is:
```
sudo pico /usr/src/alsa-15rc/alsa-kernel/pci/hda/patch_conexant.c
```
You could also use:
```
sudo gedit /usr/src/alsa-15rc/alsa-kernel/pci/hda/patch_conexant.c
```
If you followed the procedure you should have a directory named alsa-15rc in /usr/src:
```
ls /usr/src
```

---

### Post by myddewji13 on 2008-02-10
when i type in:

```
ls /usr/src
```

i get:
```
alsa-15rc
alsa-driver.tar.bz2
alsa-modules-2.6.22-14-generic_1.0.14-1ubuntu2+2.6.22-14.51_i386.deb
linux-headers-2.6.22-14
linux-headers-2.6.22-14-generic
linux-OLDVERSION.1202601597
modules

```

did i do something wrong?

---

### Post by cdtech on 2008-02-10
> **myddewji13 said:**
> when i type in:
```
ls /usr/src
```
did i do something wrong?

Try typing in a terminal:
```
sudo gedit /usr/src/alsa-15rc/alsa-kernel/pci/hda/patch_conexant.c
```
Or just copy and paste
What do you get?

---

### Post by myddewji13 on 2008-02-10
empty document that 'does not exist'

---

### Post by cdtech on 2008-02-10
> **myddewji13 said:**
> empty document that 'does not exist'

You didn't complete "1)Preparing the installation". You should go back to the "Make a directory for the alsa packages:" and do the cd /usr/src/alsa-15rc. Once you are in that directory go to "Unpack archives:" (be sure you are in that directory). Then you can do the "3) Editing the conexant patch ::".

You didn't Unpack archives and thats why you do not have that file.

Give that a try.

---

### Post by myddewji13 on 2008-02-10
i unpacked again (after downloading)...same thing :(...what am i doin wrong?

---

### Post by cdtech on 2008-02-10
> **myddewji13 said:**
> i unpacked again (after downloading)...same thing :(...what am i doin wrong?

type:
```
ls /usr/src/alsa-15rc
```
and show me what you have

---

### Post by myddewji13 on 2008-02-10
ok...nvm....i manually navigated to the file..and i got this...:

static struct snd_pci_quirk cxt5045_cfg_tbl[] = {
	SND_PCI_QUIRK(0x103c, 0x30b7, "HP DV6000Z", CXT5045_LAPTOP),
	SND_PCI_QUIRK(0x103c, 0x30bb, "HP DV8000", CXT5045_LAPTOP),
	SND_PCI_QUIRK(0x103c, 0x30b2, "HP DV Series", CXT5045_LAPTOP),
	SND_PCI_QUIRK(0x103c, 0x30b5, "HP DV2120", CXT5045_LAPTOP),
	SND_PCI_QUIRK(0x103c, 0x30cd, "HP DV Series", CXT5045_LAPTOP),
	SND_PCI_QUIRK(0x103c, 0x30d9, "HP Spartan", CXT5045_LAPTOP),
	SND_PCI_QUIRK(0x1734, 0x10ad, "Fujitsu Si1520", CXT5045_FUJITSU),
	SND_PCI_QUIRK(0x1734, 0x10cb, "Fujitsu Si3515", CXT5045_LAPTOP),
	SND_PCI_QUIRK(0x8086, 0x2111, "Conexant Reference board", CXT5045_LAPTOP),

do i delete all the lines except the one pertaining to my model or what?

---

### Post by cdtech on 2008-02-10
> **myddewji13 said:**
> ok...nvm....i manually navigated to the file..and i got this...:

static struct snd_pci_quirk cxt5045_cfg_tbl[] = {
	SND_PCI_QUIRK(0x103c, 0x30b7, "HP DV6000Z", CXT5045_LAPTOP),
	SND_PCI_QUIRK(0x103c, 0x30bb, "HP DV8000", CXT5045_LAPTOP),
	SND_PCI_QUIRK(0x103c, 0x30b2, "HP DV Series", CXT5045_LAPTOP),
	SND_PCI_QUIRK(0x103c, 0x30b5, "HP DV2120", CXT5045_LAPTOP),
	SND_PCI_QUIRK(0x103c, 0x30cd, "HP DV Series", CXT5045_LAPTOP),
	SND_PCI_QUIRK(0x103c, 0x30d9, "HP Spartan", CXT5045_LAPTOP),
	SND_PCI_QUIRK(0x1734, 0x10ad, "Fujitsu Si1520", CXT5045_FUJITSU),
	SND_PCI_QUIRK(0x1734, 0x10cb, "Fujitsu Si3515", CXT5045_LAPTOP),
	SND_PCI_QUIRK(0x8086, 0x2111, "Conexant Reference board", CXT5045_LAPTOP),

do i delete all the lines except the one pertaining to my model or what?

No, just add a line with your information
If your subsys id is the same as mine then you could just copy and paste the line I got.

---

### Post by myddewji13 on 2008-02-10
this line already has my info...:

SND_PCI_QUIRK(0x103c, 0x30cd, "HP DV Series", CXT5045_LAPTOP),

do i just keep going and complete the rest of the steps?

---

### Post by cdtech on 2008-02-10
> **myddewji13 said:**
> this line already has my info...:

SND_PCI_QUIRK(0x103c, 0x30cd, "HP DV Series", CXT5045_LAPTOP),

do i just keep going and complete the rest of the steps?
be sure its 103c and 30cd and not 30cf

Yes but be sure that you are in the proper directory:
```
cd /usr/src/alsa-15rc

```
then start at 4) Configure alsa with the intel and conexant flags ::

---

### Post by myddewji13 on 2008-02-10
ok things goin well till i hit this step:
sudo pico /etc/modprobe.d/alsa-base
 
cant find this file---so i went to look for it manually...it aint there...where did i screw up?

---

### Post by cdtech on 2008-02-10
> **myddewji13 said:**
> ok things goin well till i hit this step:
sudo pico /etc/modprobe.d/alsa-base
 
cant find this file---so i went to look for it manually...it aint there...where did i screw up?

so you did every step in section 4
what do you get here:
```
ls /etc/modprobe.d
```

---

### Post by myddewji13 on 2008-02-10
this is what i get:

```
aliases                blacklist-oss       ipw3945      nvidia-kernel-nkc
arch                   blacklist-scanner   isapnp       options
arch-aliases           blacklist-watchdog  libpisock9   thinkpad_acpi.modprobe
blacklist              bluez               lrm-video    toshiba_acpi.modprobe
blacklist-framebuffer  fuse                ndiswrapper
```

..so what should i do?>

---

### Post by myddewji13 on 2008-02-10
PS.
if i try to do step 4 again i get a no such file or directory error...does this mean i did something wrong?

---

### Post by cdtech on 2008-02-10
> **myddewji13 said:**
> this is what i get:

Reboot.........

---

### Post by myddewji13 on 2008-02-10
rebooted...no change...and no sound...no what? (PS thanks for stickin with me...i know im bein a pain in the ***)

---

### Post by cdtech on 2008-02-10
> **myddewji13 said:**
> rebooted...no change...and no sound...no what? (PS thanks for stickin with me...i know im bein a pain in the ***)
type:
```
alsamixer
```
make sure nothing is muted

---

### Post by myddewji13 on 2008-02-10
when i type alsamixer i get:
alsamixer: function snd_ctl_open failed for default: No such device

---

### Post by cdtech on 2008-02-10
> **myddewji13 said:**
> when i type alsamixer i get:
alsamixer: function snd_ctl_open failed for default: No such device
I'm thinking that section 4 was not properly done.

---

### Post by myddewji13 on 2008-02-10
should i start all over?

---

### Post by cdtech on 2008-02-10
> **myddewji13 said:**
> should i start all over?

It wont hurt anything to do so. The worst that could happen is that you end up with a working system.

Be sure you follow every step. All the steps are copy and paste, and don't skip anything.

---

### Post by myddewji13 on 2008-02-10
ARRRGH!!!

ok...all is goin well...until step 5...everytime i try to run it i get the following message:
FATAL: Error inserting snd_hda_intel (/lib/modules/2.6.22-14-generic/ubuntu/media/snd-hda-intel/snd-hda-intel.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_mixer_oss (/lib/modules/2.6.22-14-generic/kernel/sound/acore/oss/snd-mixer-oss.ko): Operation not permitted
FATAL: Error inserting snd_pcm_oss (/lib/modules/2.6.22-14-generic/kernel/sound/acore/oss/snd-pcm-oss.ko): Operation not permitted
FATAL: Error inserting snd_mixer_oss (/lib/modules/2.6.22-14-generic/kernel/sound/acore/oss/snd-mixer-oss.ko): Operation not permitted
WARNING: Error inserting snd_seq_device (/lib/modules/2.6.22-14-generic/kernel/sound/acore/seq/snd-seq-device.ko): Operation not permitted
WARNING: Error inserting snd_seq (/lib/modules/2.6.22-14-generic/kernel/sound/acore/seq/snd-seq.ko): Operation not permitted
WARNING: Error inserting snd_seq_midi_event (/lib/modules/2.6.22-14-generic/kernel/sound/acore/seq/snd-seq-midi-event.ko): Operation not permitted
FATAL: Error inserting snd_seq_oss (/lib/modules/2.6.22-14-generic/kernel/sound/acore/seq/oss/snd-seq-oss.ko): Operation not permitted



---

### Post by cdtech on 2008-02-10
> **myddewji13 said:**
> ARRRGH!!!

ok...all is goin well...until step 5...everytime i try to run it i get the following message:
FATAL: Error inserting snd_hda_intel (/lib/modules/2.6.22-14-generic/ubuntu/media/snd-hda-intel/snd-hda-intel.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_mixer_oss (/lib/modules/2.6.22-14-generic/kernel/sound/acore/oss/snd-mixer-oss.ko): Operation not permitted
FATAL: Error inserting snd_pcm_oss (/lib/modules/2.6.22-14-generic/kernel/sound/acore/oss/snd-pcm-oss.ko): Operation not permitted
FATAL: Error inserting snd_mixer_oss (/lib/modules/2.6.22-14-generic/kernel/sound/acore/oss/snd-mixer-oss.ko): Operation not permitted
WARNING: Error inserting snd_seq_device (/lib/modules/2.6.22-14-generic/kernel/sound/acore/seq/snd-seq-device.ko): Operation not permitted
WARNING: Error inserting snd_seq (/lib/modules/2.6.22-14-generic/kernel/sound/acore/seq/snd-seq.ko): Operation not permitted
WARNING: Error inserting snd_seq_midi_event (/lib/modules/2.6.22-14-generic/kernel/sound/acore/seq/snd-seq-midi-event.ko): Operation not permitted
FATAL: Error inserting snd_seq_oss (/lib/modules/2.6.22-14-generic/kernel/sound/acore/seq/oss/snd-seq-oss.ko): Operation not permitted

Did you copy and paste the command?
Maybe you should go root by typing sudo -s and try installing the modules again. Just redo step 5 without the sudo (if you do sudo -s).

---

### Post by myddewji13 on 2008-02-10
ok..done...but once i reboot and try to access alsamixer i get this error :

alsamixer: function snd_ctl_open failed for default: No such device

---

### Post by cdtech on 2008-02-10
> **myddewji13 said:**
> ok..done...but once i reboot and try to access alsamixer i get this error :

alsamixer: function snd_ctl_open failed for default: No such device

try starting the alsasound script :
```
sudo /etc/init.d/alsasound start
```
then run:
```
alsamixer
```

Also try running:
```
sudo alsaconf
```
Added the procedure in step 4 to correct this problem.
The ALSA drivers have their own devices, which need to be made using the ./snddevices. (see procedure #4)

---

### Post by cdtech on 2008-02-10
I found that this might help as well:
```
cd /usr/src/alsa-15rc/alsa-driver-1.0.15rc3
sudo ./snddevices
```

---

### Post by myddewji13 on 2008-02-10
ok...since the forums were down for a couple of hours i sorta started experimenting...anyways...i cant boot ubuntu anymore ... so im gonna do a fresh install...get my wireless configured then try these bsteps...if it doesnt work then ill go back to the old drivers and live with it...maybe my probs will fix themselves automatically in april :D ... 

PS...thanks alot for your help

---

### Post by myddewji13 on 2008-02-10
ok...since the forums were down for a couple of hours i sorta started experimenting...anyways...i cant boot ubuntu anymore ... so im gonna do a fresh install...get my wireless configured then try these steps...if it doesnt work then ill go back to the old drivers and live with it...maybe my probs will fix themselves automatically in april :D ... 

PS...thanks alot for your help

---

### Post by ahorriblemess on 2008-02-15
I have a dv6704nr, I tried this method and I lost my sound completely. I tried to restore my settings and that didn't work either. I ended up reinstalling Gutsy and just leaving it alone. Even if I could cut out speaker sound completely and only have headphone sound, that would be better than speakers+headphones or just speakers.

---

### Post by cdtech on 2008-02-15
> **ahorriblemess said:**
> I have a dv6704nr, I tried this method and I lost my sound completely. I tried to restore my settings and that didn't work either. I ended up reinstalling Gutsy and just leaving it alone. Even if I could cut out speaker sound completely and only have headphone sound, that would be better than speakers+headphones or just speakers.

I'm sure you unmuted the volumes through alsamixer?
Just thought I'd ask, alsamixer is muted by default.

---

### Post by ahorriblemess on 2008-02-15
Yeah I had the volume up on alsamixer, and if I tried to right click my sound icon, I would get an error message about the driver. 

I've done this one, and the instructions for the dv6636nr, the person who posted that said something about the newer models (x700) having Atheros cards. Mine is a 6704.... maybe that's why.

---

### Post by lbe on 2008-02-22
Worked on HP Pavilion 6615eo. Thanks alot!

---

### Post by Armenteros on 2008-03-03
Hello cdtech,

I'm trying to get this to work on a HP DV2710us, which I believe has similar specs to yours:
Chipset : nVidia nForce 560
Processor : AMD Turion 64 X2 Mobile TL-60 @ 2000 MHz
Video Card : Nvidia Corp GeForce 7150M
Audio: nVidia MCP67 High Definition Audio

I ran into the same issue as a previous user (myddewji13) had.  The "alsa-base" file is not present on my system (at least not on /etc/modprobe.d); therefore, I cannot complete step #6. I was looking at your instructions and I noticed a discrepancy that is probably causing grief to a lot of people attempting this solution including myself. The discrepancy is that you are instructing us to install the alsa-base package in step #1 (second to last package in the command) and then you are instructing us to remove it in step #2. So if you follow step #2 as indicated, there will be no alsa-base file to edit later on.

So should we re-install the alsa-base package from the repositories or do we need to get a new alsa-base package from somewhere else? I'm going to try re-installing the alsa-base package and will post the results later on.

---

### Post by cdtech on 2008-03-04
> **Armenteros said:**
> Hello cdtech,

I'm trying to get this to work on a HP DV2710us, which I believe has similar specs to yours:
Chipset : nVidia nForce 560
Processor : AMD Turion 64 X2 Mobile TL-60 @ 2000 MHz
Video Card : Nvidia Corp GeForce 7150M
Audio: nVidia MCP67 High Definition Audio

I ran into the same issue as a previous user (myddewji13) had.  The "alsa-base" file is not present on my system (at least not on /etc/modprobe.d); therefore, I cannot complete step #6. I was looking at your instructions and I noticed a discrepancy that is probably causing grief to a lot of people attempting this solution including myself. The discrepancy is that you are instructing us to install the alsa-base package in step #1 (second to last package in the command) and then you are instructing us to remove it in step #2. So if you follow step #2 as indicated, there will be no alsa-base file to edit later on.

So should we re-install the alsa-base package from the repositories or do we need to get a new alsa-base package from somewhere else? I'm going to try re-installing the alsa-base package and will post the results later on.

Thank you Armenteros. I changed the procedure to remove first then reinstall. I could see where that would cause some problems.

Thanks........

---

### Post by Armenteros on 2008-03-04
> **cdtech said:**
> Thank you Armenteros. I changed the procedure to remove first then reinstall. I could see where that would cause some problems.

Thanks........

Well, last night I re-installed the "alsa-base" package by running the command in step #1 (before step #6). The good news is that I was able to get sound back. The not so good news is that I Headphone Jack sense is still not working.

This evening I will try the setup again from scratch and will post results. 

cdtech - One thing I noticed that differs from your configuration is that mine instead of having "Codec = Conexant CX20549 (Venice)" has "Codec = Conexant 5051". Do you think that could be making the difference or it should be irrelevant?

Thanks for your help!

Edit :

I was doing some more research and found out that support for the "Conexant 5051" codec  was added on the alsa-driver v1.0.16rc2 ([http://www.alsa-project.org/main/index.php/Changes_v1.0.16rc1_v1.0.16rc2](http://www.alsa-project.org/main/index.php/Changes_v1.0.16rc1_v1.0.16rc2)),  which has been supersed by the final version  of 1.0.16. So I will try upgrading all the drivers to the latest version and see how it goes.

---

### Post by mauro_ita on 2008-03-06
M'I the onli one who got errors compiling the drivers?
I mean, when I use make under the driver directory I receive this errors msgs:

maurolnx@maurolnx-laptop:/usr/src/alsa-15rc/alsa-driver-1.0.15rc3$ sudo make
if [ ! -d include/sound -a ! -L include/sound ]; then \
          ln -sf ../alsa-kernel/include include/sound ; \
        fi
cp -puvf include/version.h include/sound/version.h
`include/version.h' -> `include/sound/version.h'
make dep
make[1]: Entering directory `/usr/src/alsa-15rc/alsa-driver-1.0.15rc3'
make[2]: Entering directory `/usr/src/alsa-15rc/alsa-driver-1.0.15rc3/acore'
copying file alsa-kernel/core/info.c
/usr/src/alsa-15rc/alsa-driver-1.0.15rc3/utils/patch-alsa: 24: patch: not found
make[2]: *** [info.c] Error 1
make[2]: Leaving directory `/usr/src/alsa-15rc/alsa-driver-1.0.15rc3/acore'
make[1]: *** [dep] Error 1
make[1]: Leaving directory `/usr/src/alsa-15rc/alsa-driver-1.0.15rc3'
make: *** [include/sndversions.h] Error 2

does someone have an idea about what should I do?

Moreover, is not mentioned but the ncurses_dev library has to be installed to compile go ahead with alsa.

thanks for your helps

mauro

---

### Post by Armenteros on 2008-03-07
I was able to compile 1.0.15rc3 drivers but that didn&#8217;t do anything for me. I also tried to compile the 1.0.16 drivers from alsa project, but that didn&#8217;t work, either.

So last night I decided to upgrade to Hardy Heron Alpha 6 (hot off the press :cool:) and all the audio components now work out of the box. In my limited testing, I haven&#8217;t found any major issues. So if you can&#8217;t live without audio, give Alpha 6 a try!.

---

### Post by myddewji13 on 2008-03-07
Hey...i have the same problem....and the same chip....so are you saying that this is fixed in hardy heron?

---

### Post by Armenteros on 2008-03-07
> **myddewji13 said:**
> Hey...i have the same problem....and the same chip....so are you saying that this is fixed in hardy heron?

For me, audio in Hardy HeronAlpha 6  is working very well at this point.  I believe that what  helped me is that my configuration requires the Conexant 5051 codec, which is now supported with alsa 1.0.16. So try to find out what codec you need (*aplay -l *should tell you) and do a search for that codec in [http://www.alsa-project.org/](http://www.alsa-project.org/) .

---

### Post by myddewji13 on 2008-03-07
been there done that....i have the 1.016 edition of alsa (or 1.6 w/e)... anyway...got sound...just cant use the headphones b/c the speaker doesnt mute...to date...i've tried everything and nothing has worked..pretty much gave up on ubuntu due to this but if the next release fixes it im back!!!

---

### Post by DigitalRedneck on 2008-03-19
Great guide, unfortunately, it doesn't seem to do much for my dv6745us with Conexant ID 5051.  I tried versions 15rc3 and 16, and would have tried upgrading to hardy heron, but I am having some annoying python gtk error (ImportError: /usr/lib/libcairo.so.2:) which i suppose if for the best since I would just end up with more bugs to fix.

So I'm taking another look at getting this method working and I was hoping you could answer a question or two.

Under the SND_PCI_QUIRK section, how does the model section work? Is that just a identification string it uses to tell us what quirk its working with, or is it a string it uses to identify the laptop to apply the fix.  If the later, how do I make sure my laptop's model number is the same as it says on the box.

And to the fella who has hardy heron running, is it using alsa 16 or a newer build?

---

### Post by myddewji13 on 2008-03-22
Hardy fixes it!!!! WOOOT ... yay!! ... oh yea..it killed my internet though.. so my workaround ended up being a clean install of gutsy with ndiswrapper then an upgrade... everything works... configs gonna take awhile though (srry this is sorta off topic)

PS... have a conexant 5051

---

### Post by michaelcole on 2008-07-16
Ubuntu 8 on a HP Pavillion dv9000.  It originally had Ubuntu 7 and I upgraded through the update manager.

I didn't have to do any of these steps.  Looks like this got fixed in the updates.

what I did was:

$ alsamixer

and turn up the volume on the front headphones

$ sudo alsaconf

and accept the defaults

use this command to restart alsa if it gives you problems:

$ sudo /etc/init.d/alsa-utils restart

Also check System->Preferences->Sound and make sure that everything says alsa   (Default Mixer tracks -> HDA Intel (alsa mixer)

Good Luck!

---

