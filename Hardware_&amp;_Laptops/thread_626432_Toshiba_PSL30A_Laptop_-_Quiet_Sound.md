---
title: "Toshiba PSL30A Laptop - Quiet Sound"
date: 2007-11-29
forum: Hardware &amp; Laptops
---

### Post by ClenchedTeeth on 2007-11-29
***************************************************************************************

                                                PLEASE READ

My current state of affairs, thanks to an AMAZING amount of help from 
danwood76, is that I can install a patched version of alsa and get the sound to 
work at 100% volume, but alsa mixer won't run and the fn keyboard shortcuts 
don't work (ie mute, volume up/down).
***************************************************************************************

I know this has been asked before quite a bit, I've read through a LOT of other threads and had no luck at all.
Laptop is a Toshiba PSL30A (aka L30) running gutsy (all packages up to date). I have tried things like reinstalling alsa, messing around with /etc/modprobe.d/alsa-base, and I am as sure as I can be that all of the volume controls are turned up. 
When I first installed, there was no sound at all, but I got it working by following the instructions here:
    [https://answers.launchpad.net/ubuntu/+question/15839](https://answers.launchpad.net/ubuntu/+question/15839)
Sound card is as follows:
    lspci | grep -i audio
    00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)
If any more info is needed just let me know.

---

### Post by ClenchedTeeth on 2007-12-02
Bump
Please help - anyone?

---

### Post by ClenchedTeeth on 2007-12-09
Bump again. Please? Is anyone out there?
As much as I hate to say it, going back to Windows is looking pretty tempting.

---

### Post by danwood76 on 2007-12-11
If your audio device is the same as mine, its an ALC861VD.

I have an L30-10V, when I was trying to get sound working I had to recompile the alsa driver with a modification in the patch_realtek.c to allow the hardware ID of my laptops sound to be recognised as the ALC861VD.

I also had to compile with the option set to asus-laptop, which you may try instead of toshiba in the alsa-base file.

Before I did this I had no headphone audio and sound out of only my left speaker, this is because the chips that control the sound can be setup or wired in many different ways depending on the desired output and the alsa drivers need to be told which way they are wired up.

If you want to try recompiling the drivers with the patched file I will find the link to the original place I found it.

regards,
Danny

---

### Post by ClenchedTeeth on 2007-12-11
Hey thanks for your reply, that sounds very promising.

> **danwood76 said:**
> If your audio device is the same as mine, its an ALC861VD.

My lspci returns a different result than ALC861VD - how can I check that they are in fact the same or different?

> **danwood76 said:**
> 
If you want to try recompiling the drivers with the patched file I will find the link to the original place I found it.

That sounds awesome, very keen to give that a go. A link would be great.

---

### Post by danwood76 on 2007-12-12
> **ClenchedTeeth said:**
> 
My lspci returns a different result than ALC861VD - how can I check that they are in fact the same or different?
.

my lspci returns the same as yours.
To check I think it says in the hardware profiler the exact sound card.

I couldnt find the original link, but if your card is an ALC861 or the VD type I will write a quick guide for you when I get a free minute.

regards,
Danny

---

### Post by ClenchedTeeth on 2007-12-12
> **danwood76 said:**
> my lspci returns the same as yours.
To check I think it says in the hardware profiler the exact sound card.


Yep, you're right. System menu > Preferences > Hardware Information shows devices 
[INDENT]"ALC861 Analog ALSA Capture Device"
"HDA ATI SB ALSA Control Device"
"HDA ATI SB ALSA hardware specific Device"
"ALC861 Analog ALSA Playback Device"
"ALC861 Analog ALSA OSS Control Device"
"ALC861 Analog ALSA PCM Device"
"ALC861 Analog ALSA PCM Device"[/INDENT]
(Note the final one is listed twice)

> **danwood76 said:**
> 
I couldnt find the original link, but if your card is an ALC861 or the VD type I will write a quick guide for you when I get a free minute.

regards,
Danny

Awesome, if you could that would be great, but I will try to have a hunt around myself and see if I can do it.
Thanks again for the help!

---

### Post by seawright on 2007-12-12
While you are waiting you might like to check whether your sound device is supported by OSS.
See:
[http://ubuntuforums.org/showpost.php?p=3768914](http://ubuntuforums.org/showpost.php?p=3768914)

---

### Post by ClenchedTeeth on 2007-12-12
> **seawright said:**
> While you are waiting you might like to check whether your sound device is supported by OSS.
See:
[http://ubuntuforums.org/showpost.php?p=3768914](http://ubuntuforums.org/showpost.php?p=3768914)

Yes, my sound device is listed as being compatible ('ATI High Definition Audio (SB450)', on [http://manuals.opensound.com/devlists/Linux.html](http://manuals.opensound.com/devlists/Linux.html))
Did you just want me to check that compatibility, or should I follow all of the instructions listed on that post?

---

### Post by seawright on 2007-12-12
Provided none of the sound applications you use are Alsa only (the latest version of Skype springs to mind) you should be ok to follow the instructions. I would leave the mixer icon in the panel though as there is a fix to get it working.
See:
[http://www.4front-tech.com/forum/viewtopic.php?t=2357]("http://www.4front-tech.com/forum/viewtopic.php?t=2357")

---

### Post by ClenchedTeeth on 2007-12-12
I tried those instructions, all seemed to go well but it didn't fix the sound, and I lost my desktop wallpaper and icons. There was also a message saying something along the lines of not being able to start an applet, and asking if I should delete it from the configuration. I foolishly clicked 'delete' without writing down the message, so I can't give the exact text that was in the dialogue box.
The desktop went black initially (see attached screenshot), but after a while my wallpaper came back (but still no icons). No menu appears when I right-click on the desktop. Other programs still work, and run as usual. It doesn't help if I disable desktop effects. Restarting doesn't help either.
I'll start having a google-hunt to see if there is a fix for this new problem.
:confused:
Edit: NB, wallpaper comes back when I open up the appearance control panel.

---

### Post by seawright on 2007-12-12
Check if package libesd-alsa0 is installed. If it is then install libesd0 which will replace it and should fix your desktop problems after logging out and back in again.

Don't try removing libesd-alsa0 as it will break dependencies for a lot of other packages, installing libesd0 will remove libesd-alsa0 cleanly without effecting anything else.

If the desktop is not restored properly or you get errors when trying to add missing icons to the panel goto /tmp/ and remove any files and directories with your username in the filename, then log out and back in again.

It's late here so I'm off to bed now but I'll check back tomorrow.

---

### Post by ClenchedTeeth on 2008-02-05
Ok, sorry for the LONG hiatus, I basically gave up on linux for a while there since my attempt at fixing this left ubuntu practically useless. I now have the time to fix this, and I don't desperately need my laptop for work at the moment.
My last attempt was flawed because I tried multiple fixes on top of each other. So,  I have completely reinstalled from scratch, and left the system untouched. The OS partition has been backed up via dd, so I can quickly restore it to a clean state.
So, who can advise me on how to get my sound working?

---

### Post by danwood76 on 2008-02-06
can you post the result of
```

lspci -nn -v | grep 'Audio'

```

I would like to see the hardware IDs for your sound card.
Then I will write you a guide on recompiling the alsa drivers if you want.

regards,
Danny

---

### Post by ClenchedTeeth on 2008-02-07
That would be fantastic. Here is the output:
00:14.2 Audio device [0403]: ATI Technologies Inc SB450 HDA Audio [1002:437b] (rev 01)
Thank you so much!

---

### Post by danwood76 on 2008-02-07
I think you have the exact same soundcard as I have on my laptop.
Could you check the hardware IDs for me?

Go System -> Preferences -> Hardware Information
then scroll down the left hand list and select 'SB450 HDA Audio'
then click advanced on the right.

Scroll to the bottom of that list and tell me what the values of,
pci.subsys_product_id
pci.subsys_vendor_id

mine are:
```

pci.subsys_product_id int 65329 (0xff31)
pci.subsys_vendor_id int 4473 (0x1179)

```

with this info I can patch the drivers source for you to make it a little easier.

regards,
Danny

---

### Post by ClenchedTeeth on 2008-02-07
Here's that info:
```
pci.subsys_product_id   int   65329 (0xff31)
pci.subsys_vendor_id   int   4473 (0x1179)
```
If you don't mind, I would prefer to see how to patch the drivers myself (if it's not too hard, and you don't mind showing me), rather than just getting the patched versions off you. That way I will learn something from this, and hopefully become less of a noob!

---

### Post by danwood76 on 2008-02-07
It is quite simple to do.

First of all download the alsa-driver source code from the alsa project site.
Untar it somewhere useful, It helps if you put all stuff you compile in the same place so its easy to find.
For example I put all my source code in ~/build

Then locate the file we need to patch, im using the 1.0.15 driver version but the method is the same no matter which version you use.
```

alsa-driver-1.0.15/alsa-kernel/pci/hda/patch_realtek.c
```
Open that file with gedit (or which ever text editor you choose) and search for this string:
```

snd_pci_quirk alc861vd
```
This next section displays all the hardware IDs associated with that sound card and which options to load.
We need to add our vendor ID and product ID to this, in a string that looks like:
```

	SND_PCI_QUIRK(x1179, 0xff31, "Toshiba L30", ALC861_ASUS_LAPTOP),

```
I use the asus option in that line because it worked best for me, the toshiba gave me odd results which didnt work properly.
So we end up with that entire section looking like this:
```

static struct snd_pci_quirk alc861vd_cfg_tbl[] = {
	SND_PCI_QUIRK(0x1043, 0x12e2, "Asus z35m", ALC660VD_3ST),
	SND_PCI_QUIRK(0x1043, 0x1339, "Asus G1", ALC660VD_3ST),
	SND_PCI_QUIRK(0x1043, 0x81e7, "ASUS", ALC660VD_3ST_DIG),
	SND_PCI_QUIRK(0x10de, 0x03f0, "Realtek ALC660 demo", ALC660VD_3ST),
	SND_PCI_QUIRK(0x1019, 0xa88d, "Realtek ALC660 demo", ALC660VD_3ST),

	/*SND_PCI_QUIRK(0x1179, 0xff00, "DALLAS", ALC861VD_DALLAS),*/ /*lenovo*/
	SND_PCI_QUIRK(0x1179, 0xff01, "DALLAS", ALC861VD_DALLAS),
	SND_PCI_QUIRK(0x17aa, 0x3802, "Lenovo 3000 C200", ALC861VD_LENOVO),
	SND_PCI_QUIRK(0x17aa, 0x2066, "Lenovo", ALC861VD_LENOVO),
	SND_PCI_QUIRK(0x1179, 0xff00, "Toshiba A135", ALC861VD_LENOVO),
	SND_PCI_QUIRK(0x1179, 0xff03, "Toshiba P205", ALC861VD_LENOVO),
	SND_PCI_QUIRK(0x1565, 0x820d, "Biostar NF61S SE", ALC861VD_6ST_DIG),
	SND_PCI_QUIRK(0x1849, 0x0862, "ASRock K8NF6G-VSTA", ALC861VD_6ST_DIG),
	SND_PCI_QUIRK(0x103c, 0x30bf, "HP TX1000", ALC861VD_HP),

	SND_PCI_QUIRK(x1179, 0xff31, "Toshiba L30", ALC861_ASUS_LAPTOP),
	{}
};

```

save that file and the patching is done.
told you it was simple.

On with the compiling:

Make sure we have the stuff needed to compile:
```
sudo apt-get install build-essential linux-headers-$(uname -r)
```

Then change to the alsa-driver-1.0.15 folder in terminal and type
```
./configure --with-cards=hda-intel
```
That will set up the compile options for us and tells it to just compile the intel driver, if any errors come up in there then stop and post the errors (or try to solve them yourself)

Then:
```
make clean
```
this isnt really necessary as it cleans old compile files but do it anyway for completness.
then on  with the actual build:
```

make
sudo make install

```

The last two are seperate commands, the first makes the drivers and the second installs them.
you then need to reboot and cross your fingers it works ok :)

I just tried to build it on my laptop and found that when I first ran make it exited with errors, running that command again straight after and compiled perfectly.

If you get any errors post them up here in full.

regards,
Danny

-- edit --

Just to add, your volumes might all be muted when you restart, this is normal and you should just be able to turn them up with the gnome sound mixer.

---

### Post by ClenchedTeeth on 2008-02-07
That's fantastic, I'll try that as soon as I get home. (Proxy issues here at office - don't ask.) Will get back to you. Thanks for writing that guide, it looks easy to do.

---

### Post by ClenchedTeeth on 2008-02-07
Ok, I'm getting somewhere with the proxy now, shouldn't the lines:
```
SND_PCI_QUIRK(x1179, 0xff31, "Toshiba L30", ALC861_ASUS_LAPTOP),
```
have '0x1179' instead of 'x1179'? All the other lines in that group of code do. I'll assume so for the time being.

---

### Post by ClenchedTeeth on 2008-02-07
After a bit of confusion, I realised I had forgotten to run the configure.in script. After that, things started to compile.
I rebooted and haven't been able to get anything working. Going to system > preferences > sound, I have set all of the playback devices for various things to use the ALSA device, but then when I press the 'test' button, I get the following popup error message:
"audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=chat: Could not open resource for writing."
Also, I used to be able to push fn + esc to mute and unmute, and fn + up/down to change the volume. (Not that I could ever hear any sound, just that the little scree notifications would pop up corresponding to the buttons that I had pressed.) Now, the sound just stays on zero when I push these keys. 
I hope that made sense. Any ideas?

---

### Post by danwood76 on 2008-02-08
> **ClenchedTeeth said:**
> Ok, I'm getting somewhere with the proxy now, shouldn't the lines:
```
SND_PCI_QUIRK(x1179, 0xff31, "Toshiba L30", ALC861_ASUS_LAPTOP),
```
have '0x1179' instead of 'x1179'? All the other lines in that group of code do. I'll assume so for the time being.

Yeah sorry, made a typo there!

Also I forgot to say you do also need to install these packages too:
They are key to getting sound working, sorry I missed them out the guide.
They include things like the alsa-mixer and the sound library's, which are obviously needed.
You need to download the same version of these as you have the driver for.

alsa-lib
alsa-utils
alsa-oss

follow the same compile method

```

cd alsa-lib-xxx
./configure
make
make install

```
etc.
This is the standard build format for most apps in linux.

you may also need to modprobe these modules after to get the modules inserted and running.

```

modprobe snd-hda-intel
modprobe snd-pcm-oss
modprobe snd-mixer-oss
modprobe snd-seq-oss

```

if sound still doesnt work there is a config file where you can specify more oprions.
/etc/modprobe.d/alsa-base
although on my laptop with the exact same sound card I havent specified any additional options there.

good luck,
Danny

---

### Post by ClenchedTeeth on 2008-02-08
Ok, so I downloaded the sourcefor the following:
alsa-lib
alsa-utils
alsa-oss
and followed the same compile method as instructed. alsa-lib seemed to go fine, but the other two both had the same error when running the configure.in script:
configure: error: Sufficiently new version of libasound not found.
If you like I can give you the enrtire output from the script. BTW, I tried an apt-get install libasound but there didn't seem to be a matching package. Nb: alsa-oss was version 1.0.15 while the others were version 1.0.16. These were all from the alsa download page.
Edit: Right before the error, the config script checks for libasound headers version >=1.0.15  (claims they are not present) But running 'apt-get install libasound2' says I already have the latest version.

---

### Post by danwood76 on 2008-02-09
libasound is the alsa-lib package I think.

did the sudo make install pop up any errors when installing this package?

regards,
Danny

---

### Post by ClenchedTeeth on 2008-02-09
> **danwood76 said:**
> libasound is the alsa-lib package I think.

did the sudo make install pop up any errors when installing this package?

regards,
Danny

No, no obvious errors. I can dump the output to a text file for you if you like?

---

### Post by danwood76 on 2008-02-09
yes if you can.
that might help folve this issue.

regards,
Danny

---

### Post by ClenchedTeeth on 2008-02-09
Scratch that. I tried again with alsa-lib, then rebooted, OSS now seemed to compile and install fine, but the alsa-utils configure script now has the error:
configure: error: this packages requires a curses library

---

### Post by danwood76 on 2008-02-09
another thing you could try is installing the older version of the driver/libs.
they will work with the standard gutsy libsound2, although you will need to re apply the patch.

[alsa-driver-1.0.15]("ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.15.tar.bz2")
[alsa-lib-1.0.15]("ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.15.tar.bz2")
[alsa-utils-1.0.15]("ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.15.tar.bz2")

that was the original version I had patched on my laptop, it might give you better results.

---

### Post by danwood76 on 2008-02-09
> **ClenchedTeeth said:**
> Scratch that. I tried again with alsa-lib, then rebooted, OSS now seemed to compile and install fine, but the alsa-utils configure script now has the error:
configure: error: this packages requires a curses library

ah, you need to install libncurses5-dev.

```

sudo apt-get install libncurses5-dev
```

regards,
Danny

---

### Post by ClenchedTeeth on 2008-02-09
Ok, current stat of affairs is that I am able to compile/install alsa-driver, alsa-lib, alsa-oss. When I try to run sudo make on alsa-utils, I get the following error:
```
mv: cannot stat `t-ja.gmo': No such file or directory
make[2]: *** [ja.gmo] Error 1
make[2]: Leaving directory `/home/rory/build/alsa/alsa-utils-1.0.16/alsaconf/po'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/rory/build/alsa/alsa-utils-1.0.16/alsaconf'
make: *** [all-recursive] Error 1
```
When I run the configure script, I get no errors.

---

### Post by danwood76 on 2008-02-09
I just had a quick look in my build directory and I have a file called ja.gmo (not t-ja.gmo)

delete the alsa-utils-1.0.16 directory and re untar it again, run ./configure then make and see if it fails.
it might be that something generated a bad config file thats not being overwritten so its looking for the wrong filename when compiling.

if it does fail again could you post the full output of ./compile and the make please.

---

### Post by ClenchedTeeth on 2008-02-09
> **danwood76 said:**
> delete the alsa-utils-1.0.16 directory and re untar it again, run ./configure then make and see if it fails.

Already tried that, no luck. (I presume that there is enough error checking in the zip file that I don't need to try downloading it again?) Here is the output of the config script:

```
rory@frink:~/build/alsa/alsa-utils-1.0.16$ sudo ./configure 
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether NLS is requested... yes
checking for msgfmt... no
checking for gmsgfmt... :
checking for xgettext... no
checking for msgmerge... no
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for shared library run path origin... done
checking for CFPreferencesCopyAppValue... no
checking for CFLocaleCopyCurrent... no
checking for GNU gettext in libc... yes
checking whether to use NLS... yes
checking where the gettext function comes from... libc
checking for cross-compiler... gcc
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for a BSD-compatible install... /usr/bin/install -c
checking whether ln -s works... yes
checking for ALSA CFLAGS... 
checking for ALSA LDFLAGS...  -lasound -lm -ldl -lpthread
checking for libasound headers version >= 1.0.15... found.
checking for snd_ctl_open in -lasound... yes
checking for snd_tlv_get_dB_range... yes
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for initscr in -lncurses... yes
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking whether time.h and sys/time.h may both be included... yes
checking whether gcc needs -traditional... no
checking for special C compiler options needed for large files... no
checking for _FILE_OFFSET_BITS value needed for large files... 64
checking for _LARGE_FILES value needed for large files... no
configure: creating ./config.status
config.status: creating Makefile
config.status: creating alsactl/Makefile
config.status: creating alsamixer/Makefile
config.status: creating amidi/Makefile
config.status: creating amixer/Makefile
config.status: creating m4/Makefile
config.status: creating po/Makefile.in
config.status: creating alsaconf/alsaconf
config.status: creating alsaconf/Makefile
config.status: creating alsaconf/po/Makefile
config.status: WARNING:  alsaconf/po/Makefile.in seems to ignore the --datarootdir setting
config.status: creating aplay/Makefile
config.status: creating include/Makefile
config.status: creating iecset/Makefile
config.status: creating utils/Makefile
config.status: creating utils/alsa-utils.spec
config.status: creating seq/Makefile
config.status: creating seq/aconnect/Makefile
config.status: creating seq/aplaymidi/Makefile
config.status: creating seq/aseqdump/Makefile
config.status: creating seq/aseqnet/Makefile
config.status: creating speaker-test/Makefile
config.status: creating speaker-test/samples/Makefile
config.status: creating include/aconfig.h
config.status: include/aconfig.h is unchanged
config.status: executing po-directories commands
config.status: creating po/POTFILES
config.status: creating po/Makefile
config.status: executing depfiles commands
```

And here is the output of the make command:

```
rory@frink:~/build/alsa/alsa-utils-1.0.16$ sudo make
Making all in include
make[1]: Entering directory `/home/rory/build/alsa/alsa-utils-1.0.16/include'
make  all-am
make[2]: Entering directory `/home/rory/build/alsa/alsa-utils-1.0.16/include'
make[2]: Leaving directory `/home/rory/build/alsa/alsa-utils-1.0.16/include'
make[1]: Leaving directory `/home/rory/build/alsa/alsa-utils-1.0.16/include'
Making all in alsactl
make[1]: Entering directory `/home/rory/build/alsa/alsa-utils-1.0.16/alsactl'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/rory/build/alsa/alsa-utils-1.0.16/alsactl'
Making all in alsaconf
make[1]: Entering directory `/home/rory/build/alsa/alsa-utils-1.0.16/alsaconf'
Making all in po
make[2]: Entering directory `/home/rory/build/alsa/alsa-utils-1.0.16/alsaconf/po'
mv: cannot stat `t-ja.gmo': No such file or directory
make[2]: *** [ja.gmo] Error 1
make[2]: Leaving directory `/home/rory/build/alsa/alsa-utils-1.0.16/alsaconf/po'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/rory/build/alsa/alsa-utils-1.0.16/alsaconf'
make: *** [all-recursive] Error 1
```

---

### Post by danwood76 on 2008-02-10
I compared your configure output with mine and you are missing a few packages that I have.
I think its the gettext package that will be causing the problems.

```

sudo apt-get install gawk gettext
```

Although I think gettext is installed by default tho I cant be 100% sure.
If it is installed then its not finding it for some reason.

I had a look through the makefile for that particular directory (/home/rory/build/alsa/alsa-utils-1.0.16/alsaconf/p) and it uses the gettext api a lot so this will definatly cause you problems.

regards,
Danny

---

### Post by ClenchedTeeth on 2008-02-10
That worked well, thanks. The drivers are now all compiled and installed. Next step was to do the modprobes as you suggested. The last three worked fine but the first one (snd-hda-intel) returned this error:
```
FATAL: Error inserting snd_hda_intel (/lib/modules/2.6.22-14-generic/ubuntu/media/snd-hda-intel/snd-hda-intel.ko): Unknown symbol in module, or unknown parameter (see dmesg)
```
I'm going to try restarting now and see what happens...

---

### Post by ClenchedTeeth on 2008-02-10
No luck after restarting. The appropriate part of dmesg reads:
```
[  236.820000] snd_hda_intel: disagrees about version of symbol snd_ctl_add
[  236.820000] snd_hda_intel: Unknown symbol snd_ctl_add
[  236.820000] snd_hda_intel: disagrees about version of symbol snd_pcm_new
[  236.820000] snd_hda_intel: Unknown symbol snd_pcm_new
[  236.820000] snd_hda_intel: disagrees about version of symbol snd_pcm_limit_hw_rates
[  236.820000] snd_hda_intel: Unknown symbol snd_pcm_limit_hw_rates
[  236.820000] snd_hda_intel: disagrees about version of symbol snd_card_register
[  236.820000] snd_hda_intel: Unknown symbol snd_card_register
[  236.820000] snd_hda_intel: disagrees about version of symbol snd_card_free
[  236.820000] snd_hda_intel: Unknown symbol snd_card_free
[  236.820000] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_preallocate_pages_for_all
[  236.820000] snd_hda_intel: Unknown symbol snd_pcm_lib_preallocate_pages_for_all
[  236.820000] snd_hda_intel: disagrees about version of symbol snd_card_proc_new
[  236.820000] snd_hda_intel: Unknown symbol snd_card_proc_new
[  236.820000] snd_hda_intel: disagrees about version of symbol snd_ctl_find_id
[  236.820000] snd_hda_intel: Unknown symbol snd_ctl_find_id
[  236.820000] snd_hda_intel: disagrees about version of symbol snd_ctl_new1
[  236.820000] snd_hda_intel: Unknown symbol snd_ctl_new1
[  236.820000] snd_hda_intel: disagrees about version of symbol snd_component_add
[  236.820000] snd_hda_intel: Unknown symbol snd_component_add
[  236.820000] snd_hda_intel: disagrees about version of symbol snd_card_new
[  236.820000] snd_hda_intel: Unknown symbol snd_card_new
[  236.820000] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_malloc_pages
[  236.820000] snd_hda_intel: Unknown symbol snd_pcm_lib_malloc_pages
[  236.820000] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_ioctl
[  236.820000] snd_hda_intel: Unknown symbol snd_pcm_lib_ioctl
[  236.820000] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_free_pages
[  236.820000] snd_hda_intel: Unknown symbol snd_pcm_lib_free_pages
[  236.820000] snd_hda_intel: Unknown symbol snd_ctl_elem_read
[  236.824000] snd_hda_intel: Unknown symbol snd_ctl_elem_write
[  236.824000] snd_hda_intel: disagrees about version of symbol snd_pcm_set_ops
[  236.824000] snd_hda_intel: Unknown symbol snd_pcm_set_ops
[  236.824000] snd_hda_intel: disagrees about version of symbol snd_pcm_hw_constraint_list
[  236.824000] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_list
[  236.824000] snd_hda_intel: disagrees about version of symbol snd_device_new
[  236.824000] snd_hda_intel: Unknown symbol snd_device_new
[  236.824000] snd_hda_intel: disagrees about version of symbol snd_pcm_suspend_all
[  236.824000] snd_hda_intel: Unknown symbol snd_pcm_suspend_all
[  236.824000] snd_hda_intel: disagrees about version of symbol snd_card_disconnect
[  236.824000] snd_hda_intel: Unknown symbol snd_card_disconnect
[  236.824000] snd_hda_intel: disagrees about version of symbol snd_pcm_hw_constraint_integer
[  236.824000] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_integer
[  236.824000] snd_hda_intel: disagrees about version of symbol snd_pcm_period_elapsed
[  236.824000] snd_hda_intel: Unknown symbol snd_pcm_period_elapsed
[  236.824000] snd_hda_intel: disagrees about version of symbol snd_pcm_hw_constraint_step
[  236.824000] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_step
```

---

### Post by danwood76 on 2008-02-10
Try recompiling the alsa-driver again.
it sounds as if its getting confused between versions, or the driver didnt compile/install correctly.

try this configure line this time.
```

sudo ./configure --with-cards=hda-intel --with-oss=yes
make
sudo make install
sudo modprobe snd-hda-intel

```

if modprobe works correctly it will give no output.
give it a restart if you get this result.

---

### Post by ClenchedTeeth on 2008-02-10
Ok everything is compiled/installed/modprobed now, but after restarting the sound doesn't work. I think I have all the volumes turned up and all the right settings (see screen cap).
When I use the hotkey combinations, they only seem to do anything when the HDA ATI SB device is selected ('device' under the section 'default mixer tracks'), when I use the alc861 device the volume won't change at all.
Clicking the test buttons no longer gives me an error (but no sound either).

---

### Post by danwood76 on 2008-02-11
Having a look at your attatchment I can see one problem.
Your OSS mixer is different to mine, yours is for the ALC861 not the -VD variant.
Im wondering if maybe you patched the file in the wrong place, or something else is going on.

Do you mind posting your patch_realtek.c as an attatchment for me to have a quick look at?
Just want to double check its patched in the correct section.

Here is my sound prefs panel for you to compare with.

regards,
Danny

---

### Post by danwood76 on 2008-02-11
I just recompiled mine with version 1.0.16 and you can clearly see in the alsa-mixer my card is detected as a ALC861-VD whereas yours is just an ALC861.

Attached is my alsa mixer page.

---

### Post by ClenchedTeeth on 2008-02-11
Here is that file. I notice that a file with the same name also exists at ./pci/hda/patch_realtek.c as well as at ./alsa-kernel/pci/hda/patch_realtek.c. There's also the fact that almost all of the other lines in the section of code that I patched have the 'vd' option. Do you think either of these things are significant?

```
static struct snd_pci_quirk alc861vd_cfg_tbl[] = {
	SND_PCI_QUIRK(0x1019, 0xa88d, "Realtek ALC660 demo", ALC660VD_3ST),
	SND_PCI_QUIRK(0x103c, 0x30bf, "HP TX1000", ALC861VD_HP),
	SND_PCI_QUIRK(0x1043, 0x12e2, "Asus z35m", ALC660VD_3ST),
	SND_PCI_QUIRK(0x1043, 0x1339, "Asus G1", ALC660VD_3ST),
	SND_PCI_QUIRK(0x1043, 0x81e7, "ASUS", ALC660VD_3ST_DIG),
	SND_PCI_QUIRK(0x10de, 0x03f0, "Realtek ALC660 demo", ALC660VD_3ST),
	SND_PCI_QUIRK(0x1179, 0xff00, "Toshiba A135", ALC861VD_LENOVO),
	/*SND_PCI_QUIRK(0x1179, 0xff00, "DALLAS", ALC861VD_DALLAS),*/ /*lenovo*/
	SND_PCI_QUIRK(0x1179, 0xff01, "DALLAS", ALC861VD_DALLAS),
	SND_PCI_QUIRK(0x1179, 0xff03, "Toshiba P205", ALC861VD_LENOVO),
	SND_PCI_QUIRK(0x1565, 0x820d, "Biostar NF61S SE", ALC861VD_6ST_DIG),
	SND_PCI_QUIRK(0x17aa, 0x2066, "Lenovo", ALC861VD_LENOVO),
	SND_PCI_QUIRK(0x17aa, 0x3802, "Lenovo 3000 C200", ALC861VD_LENOVO),
	SND_PCI_QUIRK(0x1849, 0x0862, "ASRock K8NF6G-VSTA", ALC861VD_6ST_DIG),
	SND_PCI_QUIRK(0x1179, 0xff31, "Toshiba L30", ALC861_ASUS_LAPTOP),
	{}
};
```

---

### Post by danwood76 on 2008-02-11
I just looked at the first page and I think ive been a bit stupid here.
sorry for this.

Your card is the ALC861 not the -VD type. so I think the patch should go in the alc861 section.

Im thinking this might be why they dont include these hardware IDs in either section, as either would break the other.
I just tried placing the patch in the ALC861 section and I broke my laptop sound so I think its worth a try, as placing it back in the -VD section fixed it again.

the section looks like this:
```

static struct snd_pci_quirk alc861_cfg_tbl[] = {
	SND_PCI_QUIRK(0x1043, 0x1205, "ASUS W7J", ALC861_3ST),
	SND_PCI_QUIRK(0x1043, 0x1335, "ASUS F2/3", ALC861_ASUS_LAPTOP),
	SND_PCI_QUIRK(0x1043, 0x1338, "ASUS F2/3", ALC861_ASUS_LAPTOP),
	SND_PCI_QUIRK(0x1043, 0x1393, "ASUS", ALC861_ASUS),
	SND_PCI_QUIRK(0x1043, 0x13d7, "ASUS A9rp", ALC861_ASUS_LAPTOP),
	SND_PCI_QUIRK(0x1043, 0x81cb, "ASUS P1-AH2", ALC861_3ST_DIG),
	SND_PCI_QUIRK(0x1179, 0xff00, "Toshiba", ALC861_TOSHIBA),
	/* FIXME: the entry below breaks Toshiba A100 (model=auto works!)
	 *        Any other models that need this preset?
	 */
	/* SND_PCI_QUIRK(0x1179, 0xff10, "Toshiba", ALC861_TOSHIBA), */
	SND_PCI_QUIRK(0x1462, 0x7254, "HP dx2200 (MSI MS-7254)", ALC861_3ST),
	SND_PCI_QUIRK(0x1462, 0x7297, "HP dx2250 (MSI MS-7297)", ALC861_3ST),
	SND_PCI_QUIRK(0x1584, 0x2b01, "Uniwill X40AIx", ALC861_UNIWILL_M31),
	SND_PCI_QUIRK(0x1584, 0x9072, "Uniwill m31", ALC861_UNIWILL_M31),
	SND_PCI_QUIRK(0x1584, 0x9075, "Airis Praxis N1212", ALC861_ASUS_LAPTOP),
	/* FIXME: the below seems conflict */
	/* SND_PCI_QUIRK(0x1584, 0x9075, "Uniwill", ALC861_UNIWILL_M31), */
	SND_PCI_QUIRK(0x1849, 0x0660, "Asrock 939SLI32", ALC660_3ST),
	SND_PCI_QUIRK(0x8086, 0xd600, "Intel", ALC861_3ST),
	{}
};

```
and after patching like this:
```

static struct snd_pci_quirk alc861_cfg_tbl[] = {
	SND_PCI_QUIRK(0x1043, 0x1205, "ASUS W7J", ALC861_3ST),
	SND_PCI_QUIRK(0x1043, 0x1335, "ASUS F2/3", ALC861_ASUS_LAPTOP),
	SND_PCI_QUIRK(0x1043, 0x1338, "ASUS F2/3", ALC861_ASUS_LAPTOP),
	SND_PCI_QUIRK(0x1043, 0x1393, "ASUS", ALC861_ASUS),
	SND_PCI_QUIRK(0x1043, 0x13d7, "ASUS A9rp", ALC861_ASUS_LAPTOP),
	SND_PCI_QUIRK(0x1043, 0x81cb, "ASUS P1-AH2", ALC861_3ST_DIG),
	SND_PCI_QUIRK(0x1179, 0xff00, "Toshiba", ALC861_TOSHIBA),
	/* FIXME: the entry below breaks Toshiba A100 (model=auto works!)
	 *        Any other models that need this preset?
	 */
	/* SND_PCI_QUIRK(0x1179, 0xff10, "Toshiba", ALC861_TOSHIBA), */
	SND_PCI_QUIRK(0x1462, 0x7254, "HP dx2200 (MSI MS-7254)", ALC861_3ST),
	SND_PCI_QUIRK(0x1462, 0x7297, "HP dx2250 (MSI MS-7297)", ALC861_3ST),
	SND_PCI_QUIRK(0x1584, 0x2b01, "Uniwill X40AIx", ALC861_UNIWILL_M31),
	SND_PCI_QUIRK(0x1584, 0x9072, "Uniwill m31", ALC861_UNIWILL_M31),
	SND_PCI_QUIRK(0x1584, 0x9075, "Airis Praxis N1212", ALC861_ASUS_LAPTOP),
	/* FIXME: the below seems conflict */
	/* SND_PCI_QUIRK(0x1584, 0x9075, "Uniwill", ALC861_UNIWILL_M31), */
	SND_PCI_QUIRK(0x1849, 0x0660, "Asrock 939SLI32", ALC660_3ST),
	SND_PCI_QUIRK(0x8086, 0xd600, "Intel", ALC861_3ST),

	SND_PCI_QUIRK(0x1179, 0xff31, "Toshiba L30", ALC861_ASUS_LAPTOP),
	{}
};

```

you obviously need to do:
```

./configure --with-cards=hda-intel
make clean
make
sudo make install
and reboot

```

Again sorry for my ignorance, seems a bit silly that toshiba made 2 different sound cards with the exact same hardware IDs.

-- edit --

added make clean to delete the already built files

---

### Post by ClenchedTeeth on 2008-02-11
All seems to compile fun but the modprobe returns the error:

```
rory@frink:~/build/alsa/alsa-driver-1.0.16$ sudo modprobe snd-hda-intelFATAL: Error inserting snd_hda_intel (/lib/modules/2.6.22-14-generic/ubuntu/media/snd-hda-intel/snd-hda-intel.ko): Unknown symbol in module, or unknown parameter (see dmesg)
```

dmesg gives:
```
[  810.752000] snd_hda_intel: disagrees about version of symbol snd_ctl_add

[  810.752000] snd_hda_intel: Unknown symbol snd_ctl_add

[  810.752000] snd_hda_intel: disagrees about version of symbol snd_pcm_new

[  810.752000] snd_hda_intel: Unknown symbol snd_pcm_new

[  810.756000] snd_hda_intel: disagrees about version of symbol snd_pcm_limit_hw_rates

[  810.756000] snd_hda_intel: Unknown symbol snd_pcm_limit_hw_rates

[  810.756000] snd_hda_intel: disagrees about version of symbol snd_card_register

[  810.756000] snd_hda_intel: Unknown symbol snd_card_register

[  810.756000] snd_hda_intel: disagrees about version of symbol snd_card_free

[  810.756000] snd_hda_intel: Unknown symbol snd_card_free

[  810.756000] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_preallocate_pages_for_all

[  810.756000] snd_hda_intel: Unknown symbol snd_pcm_lib_preallocate_pages_for_all

[  810.756000] snd_hda_intel: disagrees about version of symbol snd_card_proc_new

[  810.756000] snd_hda_intel: Unknown symbol snd_card_proc_new

[  810.756000] snd_hda_intel: disagrees about version of symbol snd_ctl_find_id

[  810.756000] snd_hda_intel: Unknown symbol snd_ctl_find_id

[  810.756000] snd_hda_intel: disagrees about version of symbol snd_ctl_new1

[  810.756000] snd_hda_intel: Unknown symbol snd_ctl_new1

[  810.756000] snd_hda_intel: disagrees about version of symbol snd_component_add

[  810.756000] snd_hda_intel: Unknown symbol snd_component_add

[  810.756000] snd_hda_intel: disagrees about version of symbol snd_card_new

[  810.756000] snd_hda_intel: Unknown symbol snd_card_new

[  810.756000] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_malloc_pages

[  810.756000] snd_hda_intel: Unknown symbol snd_pcm_lib_malloc_pages

[  810.756000] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_ioctl

[  810.756000] snd_hda_intel: Unknown symbol snd_pcm_lib_ioctl

[  810.756000] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_free_pages

[  810.756000] snd_hda_intel: Unknown symbol snd_pcm_lib_free_pages

[  810.756000] snd_hda_intel: Unknown symbol snd_ctl_elem_read

[  810.756000] snd_hda_intel: Unknown symbol snd_ctl_elem_write

[  810.756000] snd_hda_intel: disagrees about version of symbol snd_pcm_set_ops

[  810.756000] snd_hda_intel: Unknown symbol snd_pcm_set_ops

[  810.756000] snd_hda_intel: disagrees about version of symbol snd_pcm_hw_constraint_list

[  810.756000] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_list

[  810.756000] snd_hda_intel: disagrees about version of symbol snd_device_new

[  810.756000] snd_hda_intel: Unknown symbol snd_device_new

[  810.756000] snd_hda_intel: disagrees about version of symbol snd_pcm_suspend_all

[  810.756000] snd_hda_intel: Unknown symbol snd_pcm_suspend_all

[  810.756000] snd_hda_intel: disagrees about version of symbol snd_card_disconnect

[  810.756000] snd_hda_intel: Unknown symbol snd_card_disconnect

[  810.756000] snd_hda_intel: disagrees about version of symbol snd_pcm_hw_constraint_integer

[  810.756000] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_integer

[  810.756000] snd_hda_intel: disagrees about version of symbol snd_pcm_period_elapsed

[  810.756000] snd_hda_intel: Unknown symbol snd_pcm_period_elapsed

[  810.756000] snd_hda_intel: disagrees about version of symbol snd_pcm_hw_constraint_step

[  810.756000] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_step
```

Do I still need to use the --with-oss=yes option? At some stage soon I'm going to consolidate all of the instructions into a single posting just so that we're on the same page.

---

### Post by danwood76 on 2008-02-11
> **ClenchedTeeth said:**
> 
Do I still need to use the --with-oss=yes option? At some stage soon I'm going to consolidate all of the instructions into a single posting just so that we're on the same page.

No need, I dont think it does anything to tell you the truth as you already install oss separately.

try running
```

make clean
./configure --with-cards=hda-intel
make
sudo make install

```

I had a similar error when I recompiled last time which was solved with a make clean and a re compile.
If it works its definitely worth consolidating and printing out or saving somewhere handy, I have a folder on my PC with guides and so on.

---

### Post by ClenchedTeeth on 2008-02-11
Instructions so far:

Install the required packages:
```
sudo apt-get install build-essential linux-headers-$(uname -r) libncurses5-dev gawk gettext
```

Download the alsa-driver source code from the [alsa project site]("http://www.alsa-project.org/main/index.php/Download").
Untar it (tar -xjf <filename)>somewhere useful, It helps if you put all stuff you compile in the same place so its easy to find.
For example I put all my source code in ~/build

Then locate the file we need to patch, im using the 1.0.15 driver version but the method is the same no matter which version you use.
```
alsa-driver-1.0.15/alsa-kernel/pci/hda/patch_realtek.c
```

Open it up with gedit and find this section:
```
static struct snd_pci_quirk alc861_cfg_tbl[] = {
	SND_PCI_QUIRK(0x1043, 0x1205, "ASUS W7J", ALC861_3ST),
	SND_PCI_QUIRK(0x1043, 0x1335, "ASUS F2/3", ALC861_ASUS_LAPTOP),
	SND_PCI_QUIRK(0x1043, 0x1338, "ASUS F2/3", ALC861_ASUS_LAPTOP),
	SND_PCI_QUIRK(0x1043, 0x1393, "ASUS", ALC861_ASUS),
	SND_PCI_QUIRK(0x1043, 0x13d7, "ASUS A9rp", ALC861_ASUS_LAPTOP),
	SND_PCI_QUIRK(0x1043, 0x81cb, "ASUS P1-AH2", ALC861_3ST_DIG),
	SND_PCI_QUIRK(0x1179, 0xff00, "Toshiba", ALC861_TOSHIBA),
	/* FIXME: the entry below breaks Toshiba A100 (model=auto works!)
	 *        Any other models that need this preset?
	 */
	/* SND_PCI_QUIRK(0x1179, 0xff10, "Toshiba", ALC861_TOSHIBA), */
	SND_PCI_QUIRK(0x1462, 0x7254, "HP dx2200 (MSI MS-7254)", ALC861_3ST),
	SND_PCI_QUIRK(0x1462, 0x7297, "HP dx2250 (MSI MS-7297)", ALC861_3ST),
	SND_PCI_QUIRK(0x1584, 0x2b01, "Uniwill X40AIx", ALC861_UNIWILL_M31),
	SND_PCI_QUIRK(0x1584, 0x9072, "Uniwill m31", ALC861_UNIWILL_M31),
	SND_PCI_QUIRK(0x1584, 0x9075, "Airis Praxis N1212", ALC861_ASUS_LAPTOP),
	/* FIXME: the below seems conflict */
	/* SND_PCI_QUIRK(0x1584, 0x9075, "Uniwill", ALC861_UNIWILL_M31), */
	SND_PCI_QUIRK(0x1849, 0x0660, "Asrock 939SLI32", ALC660_3ST),
	SND_PCI_QUIRK(0x8086, 0xd600, "Intel", ALC861_3ST),
	{}
};
```
Add the line:
```
SND_PCI_QUIRK(0x1179, 0xff31, "Toshiba L30", ALC861_ASUS_LAPTOP),
```
So it now looks like this:
```
static struct snd_pci_quirk alc861_cfg_tbl[] = {
	SND_PCI_QUIRK(0x1043, 0x1205, "ASUS W7J", ALC861_3ST),
	SND_PCI_QUIRK(0x1043, 0x1335, "ASUS F2/3", ALC861_ASUS_LAPTOP),
	SND_PCI_QUIRK(0x1043, 0x1338, "ASUS F2/3", ALC861_ASUS_LAPTOP),
	SND_PCI_QUIRK(0x1043, 0x1393, "ASUS", ALC861_ASUS),
	SND_PCI_QUIRK(0x1043, 0x13d7, "ASUS A9rp", ALC861_ASUS_LAPTOP),
	SND_PCI_QUIRK(0x1043, 0x81cb, "ASUS P1-AH2", ALC861_3ST_DIG),
	SND_PCI_QUIRK(0x1179, 0xff00, "Toshiba", ALC861_TOSHIBA),
	/* FIXME: the entry below breaks Toshiba A100 (model=auto works!)
	 *        Any other models that need this preset?
	 */
	/* SND_PCI_QUIRK(0x1179, 0xff10, "Toshiba", ALC861_TOSHIBA), */
	SND_PCI_QUIRK(0x1462, 0x7254, "HP dx2200 (MSI MS-7254)", ALC861_3ST),
	SND_PCI_QUIRK(0x1462, 0x7297, "HP dx2250 (MSI MS-7297)", ALC861_3ST),
	SND_PCI_QUIRK(0x1584, 0x2b01, "Uniwill X40AIx", ALC861_UNIWILL_M31),
	SND_PCI_QUIRK(0x1584, 0x9072, "Uniwill m31", ALC861_UNIWILL_M31),
	SND_PCI_QUIRK(0x1584, 0x9075, "Airis Praxis N1212", ALC861_ASUS_LAPTOP),
	/* FIXME: the below seems conflict */
	/* SND_PCI_QUIRK(0x1584, 0x9075, "Uniwill", ALC861_UNIWILL_M31), */
	SND_PCI_QUIRK(0x1849, 0x0660, "Asrock 939SLI32", ALC660_3ST),
	SND_PCI_QUIRK(0x8086, 0xd600, "Intel", ALC861_3ST),

	SND_PCI_QUIRK(0x1179, 0xff31, "Toshiba L30", ALC861_ASUS_LAPTOP),
	{}
};
```

Save and close the file.

Run this:
```
./configure --with-cards=hda-intel
make
sudo make install

```

Download the same version of these as you have the driver for.

alsa-lib
alsa-utils
alsa-oss

follow the same compile method:
```
cd alsa-lib-xxx
./configure
make
sudo make install
```

Run the following modprobe commands:
```
sudo modprobe snd-hda-intel
sudo modprobe snd-pcm-oss
sudo modprobe snd-mixer-oss
sudo modprobe snd-seq-oss
```

Reboot.

Run alsamixer from the command line to turn the volume up on the channels.

Profit.

---

### Post by danwood76 on 2008-02-11
[QUOTE=ClenchedTeeth]
Profit.[/QUOTE]

Have you got it working now then?

---

### Post by ClenchedTeeth on 2008-02-11
Still getting the same error when I try to modprobe:
```
FATAL: Error inserting snd_hda_intel (/lib/modules/2.6.22-14-generic/ubuntu/media/snd-hda-intel/snd-hda-intel.ko): Unknown symbol in module, or unknown parameter (see dmesg)


```
Do I need to restart before I do the modprobe?

---

### Post by ClenchedTeeth on 2008-02-11
> **danwood76 said:**
> Have you got it working now then?
Nope, just trying to exercise the power of positive thinking!

---

### Post by danwood76 on 2008-02-11
yeah try rebooting.
if you get the error again recompile it, im not really sure I may have rebooted in the middle aswell.

---

### Post by ClenchedTeeth on 2008-02-11
Have rebooted and recompiled with no change. Does it matter if I do oss, utils and lib before/after the driver?

---

### Post by danwood76 on 2008-02-11
you shouldnt need to recompile the oss, utils, libs. just the driver.
sorry I should have said that earlier.

once you have the oss, utils, libs installed reboot and try and recompile just the driver and do it afresh so delete the driver dir re untar it and repatch etc.

I can only think that something else has got corrupted whilst its compiling.

---

### Post by wrgarrett on 2008-02-11
Guys, I hope I'm not hijacking this thread, I apologize if I am. I'm trying to learn but I have no experience at all with this. I have the exact same setup, Toshiba Audio device [0403]: ATI Technologies Inc SB450 HDA Audio [1002:437b] (rev 01) and no sound. Would there be any way you could post a working patch for me?

---

### Post by ClenchedTeeth on 2008-02-11
> **danwood76 said:**
> you shouldnt need to recompile the oss, utils, libs. just the driver.
sorry I should have said that earlier.

No worries, just thought it might have made a difference.
A recompile from scratch gives me the exact same error when I try to modprobe.
What do you think about the VD vs non-VD issue? Because it seemed to get closer to working when we patched the VD section. (Ie drivers/devices showed up in the sound control panel, test buttons didn't give error messages, volume hotkeys functioned properly...).
Do you think that I might actually have the VD model, but it is showing up incorrectly as the non-VD model for some reason?

---

### Post by ClenchedTeeth on 2008-02-11
> **wrgarrett said:**
> Guys, I hope I'm not hijacking this thread, I apologize if I am. I'm trying to learn but I have no experience at all with this. I have the exact same setup, Toshiba Audio device [0403]: ATI Technologies Inc SB450 HDA Audio [1002:437b] (rev 01) and no sound. Would there be any way you could post a working patch for me?
Absolutely, once we can get it working! I will post the full set of steps in one go once it's sorted out.
And all thanks/kudos goes to danwood76 for working this out, I'm just doing what he suggests.

---

### Post by danwood76 on 2008-02-12
> **ClenchedTeeth said:**
> No worries, just thought it might have made a difference.
A recompile from scratch gives me the exact same error when I try to modprobe.
What do you think about the VD vs non-VD issue? Because it seemed to get closer to working when we patched the VD section. (Ie drivers/devices showed up in the sound control panel, test buttons didn't give error messages, volume hotkeys functioned properly...).
Do you think that I might actually have the VD model, but it is showing up incorrectly as the non-VD model for some reason?

you had the same problem back in post #34 and im wondering if the --with-oss=yes option fixed that for you.

the -VD version is a different card, and as I said earlier I tried to recompile forcing my card to be the non VD type and it broke my sound.
try re doing the compile with the --with-oss=yes option and see if it helps.

```

sudo ./configure --with-cards=hda-intel --with-oss=yes
make clean
make
sudo make install
sudo modprobe snd-hda-intel

```

---

### Post by ClenchedTeeth on 2008-02-12
Using the --with-oss=yes option makes no difference, modprobe still fails. Even on a completely fresh build (ie starting from scratch, repatching and building).

---

### Post by danwood76 on 2008-02-12
Ive just looked into this a bit deeper and it seems that you may have some corrupted module files for some reason, possibly a failed make install has messed things up.

you can manually remove the module, although it is a little tricky and im not 100% sure really if it will work.
Im gonna try it on my laptop and post you up quick how to if I succeed in deleting and reinstalling the module.

It might be easier if you are able to re install ubuntu completely and start with a fresh OS and apply the patch from complete scratch. Though if you have done a lot of program installs and customising it may not be worth it.

---

### Post by ClenchedTeeth on 2008-02-12
I will do a full reinstall now. The main drawback is the 200+MB of updates that have been downloaded, but I can live with that. Will get back to you when reinstall is completed. Fingers crossed!

---

### Post by danwood76 on 2008-02-12
When you do get back to a working clean OS.
Build and install them in this order, dont bother doing the modprobe after any of them, once you have installed them all just reboot.

alsa-driver (patched) -> alsa-libs -> alsa-utils -> alsa-oss

thats the way ive always done it, and I think the alsa site spicifies this order too.

oh and dont forget before you build you will need to install the odd dependencies:
```

sudo apt-get install libncurses5-dev gawk gettext

```

good luck!

---

### Post by ClenchedTeeth on 2008-02-12
alsa-lib required the make command to be run with sudo (hopefully that doesn't indicate an error?), otherwise the installation/compiling went flawlessly. I rebooted and opened the sound preferences control panel, but no devices are listed. Should I try modprobing?
BTW I updated my list of combined instructions above to include the sudo make as well as the installation of the dependencies that I needed.

---

### Post by ClenchedTeeth on 2008-02-12
Modprobing snd-hda-intel still fails with the same old error.

---

### Post by danwood76 on 2008-02-12
the make shouldnt require sudo.
yeah do a modprobe of each module like before and reboot, then try alsamixer

---

### Post by danwood76 on 2008-02-12
> **ClenchedTeeth said:**
> Modprobing snd-hda-intel still fails with the same old error.

Try installing the driver by compiling everything.
so just do a ./configure with nothing after it:

```

make clean
./configure
make
sudo make install

```

and also recompile the alsa-libs

I think the modprobe error is because of the alsa-libs module not installing properly.

---

### Post by ClenchedTeeth on 2008-02-12
> **danwood76 said:**
> the make shouldnt require sudo.

Note that I also used 'sudo make' instead of 'make' for the oss, and that I am always using sudo for the ./configure script.

Ok I have compiled alsa-driver without the option for the compile script, and restarted. When I try to make alsa-lib without sudo it still gives an error:
```
rory@frink:~/build/alsa/alsa-lib-1.0.16$ make

Making all in doc

make[1]: Entering directory `/home/rory/build/alsa/alsa-lib-1.0.16/doc'

Making all in pictures

make[2]: Entering directory `/home/rory/build/alsa/alsa-lib-1.0.16/doc/pictures'

make[2]: Nothing to be done for `all'.

make[2]: Leaving directory `/home/rory/build/alsa/alsa-lib-1.0.16/doc/pictures'

make[2]: Entering directory `/home/rory/build/alsa/alsa-lib-1.0.16/doc'

make[2]: Nothing to be done for `all-am'.

make[2]: Leaving directory `/home/rory/build/alsa/alsa-lib-1.0.16/doc'

make[1]: Leaving directory `/home/rory/build/alsa/alsa-lib-1.0.16/doc'

Making all in include

make[1]: Entering directory `/home/rory/build/alsa/alsa-lib-1.0.16/include'

make  all-recursive

make[2]: Entering directory `/home/rory/build/alsa/alsa-lib-1.0.16/include'

Making all in sound

make[3]: Entering directory `/home/rory/build/alsa/alsa-lib-1.0.16/include/sound'

make[3]: Nothing to be done for `all'.

make[3]: Leaving directory `/home/rory/build/alsa/alsa-lib-1.0.16/include/sound'

make[3]: Entering directory `/home/rory/build/alsa/alsa-lib-1.0.16/include'

make[3]: Leaving directory `/home/rory/build/alsa/alsa-lib-1.0.16/include'

make[2]: Leaving directory `/home/rory/build/alsa/alsa-lib-1.0.16/include'

make[1]: Leaving directory `/home/rory/build/alsa/alsa-lib-1.0.16/include'

Making all in src

make[1]: Entering directory `/home/rory/build/alsa/alsa-lib-1.0.16/src'

Making all in control

make[2]: Entering directory `/home/rory/build/alsa/alsa-lib-1.0.16/src/control'

if /bin/bash ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT cards.lo -MD -MP -MF ".deps/cards.Tpo" -c -o cards.lo cards.c; \

        then mv -f ".deps/cards.Tpo" ".deps/cards.Plo"; else rm -f ".deps/cards.Tpo"; exit 1; fi

mkdir .libs

 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT cards.lo -MD -MP -MF .deps/cards.Tpo -c cards.c  -fPIC -DPIC -o .libs/cards.o

cards.c:200: fatal error: opening dependency file .deps/cards.Tpo: Permission denied

compilation terminated.

make[2]: *** [cards.lo] Error 1

make[2]: Leaving directory `/home/rory/build/alsa/alsa-lib-1.0.16/src/control'

make[1]: *** [all-recursive] Error 1

make[1]: Leaving directory `/home/rory/build/alsa/alsa-lib-1.0.16/src'

make: *** [all-recursive] Error 1


```

---

### Post by danwood76 on 2008-02-13
if you use sudo for the configure script this is why you need to sudo the make.
The configure script creates makefiles among other things thatif made in sudo will not allow normal user writing.

---

### Post by ClenchedTeeth on 2008-02-13
> **danwood76 said:**
> if you use sudo for the configure script this is why you need to sudo the make.
The configure script creates makefiles among other things thatif made in sudo will not allow normal user writing.

Oh ok. After running it as sudo once, it then requires sudo to run it again. I had incorrectly assumed that this means it always needs sudo.

All the same, it still fails the modprobe. Can you think of some way to independently confirm that my card is/isn't the VD model? That seems the most promising thing to me, since it worked better when we assumed that it was the VD model.

You said earlier that "Your OSS mixer is different to mine, yours is for the ALC861 not the -VD variant." Do you think that I do in fact have a VD model, but something else apart from the driver, (ie OSS, or maybe something else) is incorrectly configured and needs to be patched?

---

### Post by danwood76 on 2008-02-13
I believe yours is the plain ALC861 model, they are very similar in spec but have slightly different register addressing. I think the name it gets is actually retrieved from the sound card itself as with mine patched to be an ALC861 it still says -VD.

Im not sure whats breaking your snd-hda-intel module, you could try compiling a completely unpatched version and see if it installs (it should install fine otherwise you may have some other error)
Then when you have it installed you can recompile just the driver to see if the patching has any effect.

Back a few days ago (back to post 35) you had the same problem.
was there anything else you did to correct this issue?

---

### Post by ClenchedTeeth on 2008-02-13
The only thing I think I did was restart. I've restarted heaps and had no luck. I will try another fresh attempt (full OS reinstall and driver recompile) and see what happens.

---

### Post by danwood76 on 2008-02-13
I just did some looking through the alsa site and they have some slightly different compile directions to mine:
[http://alsa.opensrc.org/index.php/Quick_Install](http://alsa.opensrc.org/index.php/Quick_Install) (section  3. Compiling and installing)

Theres some quite good troubleshooting things in the faw relating to this error (I should have looked here earlier)

Tip 2 from here might help:
[http://alsa.opensrc.org/index.php/Unresolved_Symbols](http://alsa.opensrc.org/index.php/Unresolved_Symbols)

It says to make sure you remove all alsa modules before you compile, tho I dont think I ever did this it may help you.

---

### Post by ClenchedTeeth on 2008-02-13
Ok I'm confused about what I should be trying. Should I try your instructions without patching or should I have a go at the instructions you linked to (Quick install - Compiling and Installing)?

---

### Post by ClenchedTeeth on 2008-02-13
> **danwood76 said:**
>  you could try compiling a completely unpatched version and see if it installs (it should install fine otherwise you may have some other error)
Then when you have it installed you can recompile just the driver to see if the patching has any effect.
I have installed a completely unpatched version, with no options specified for the configuration script. This installed without any errors but the sound doesn't work. Screenshot shows sound prefs window at this point.
I then patched the driver and reinstalled it, using the --with-cards=hda-intel option on the configure script. This made no noticable difference, which I find strange because I would have expected it to put me back in the situation I was in back at post #37. At that stage I had two sound devices to choose from, but here I can only choose Realtek ALC861 (OSS mixer). I find it hard to believe that this difference is caused by installing the driver normally then going back and installing the patched version.

This is all using the ./configure, make, sudo make install instructions that you have given me, ignoring (for now, I will try them later) the different make instructions that were suggested in the link you gave me.

---

### Post by ClenchedTeeth on 2008-02-13
Since I was suspicious about what was going on in my last post, I did a fresh install and followed my instructions from post #44 above. Everything still seemed to be going as per usual but when I rebooted I heard the music that ubuntu makes when it starts up. When I open up the Sound Preferences control panel the test buttons now work. (See screenshot below).
The sound is stuck on 100% volume and it's really loud, but it appears to work. Just for reference, a listing of the commands I used is below (slightly edited). I don't know what I did differently but I'm really happy.
The only thing that needs to be done now is to get the volume controls working. The fn keyboard shortcuts have no effect and when I try to run alsamixer from the command line I still get the error:

```
alsamixer: function snd_mixer_load failed: No such file or directory


``` 

History of commands used to get it working (I also enabled some repositories under system>admin>software sources)
EDIT: THIS SET OF COMMANDS IS SUPERCEDED BY THE SET IN POST #73 BELOW
```
    1  export http_proxy="http://username:password@proxy:3128"

    2  sudo apt-get update

    4  sudo apt-get install synergy

    6  sudo apt-get install build-essential linux-headers-$(uname -r) libncurses5-dev gawk gettext

    7  cd build/alsa/

   11  tar -xjf alsa-driver-1.0.16.tar.bz2 

   13  tar -xjf alsa-utils-1.0.16.tar.bz2 

   14  tar -xjf alsa-oss-1.0.15.tar.bz2 

   15  tar -xjf alsa-lib-1.0.16.tar.bz2 

   16  cd alsa-driver-1.0.16/

   17  cp ../patch_realtek.c_PATCHED ./alsa-kernel/pci/hda/patch_realtek.c 

   18  ./configure --with-cards=hda-intel

   19  make

   20  sudo make install

   21  cd ..

   22  cd alsa-lib-1.0.16/

   23  ./configure

   24  make

   25  sudo make install

   26  cd ..

   27  cd alsa-utils-1.0.16/

   28  ./configure

   29  make

   30  sudo make install

   31  cd ..

   32  cd alsa-oss-1.0.15/

   33  ls

   34  ./configure

   35  make

   36  sudo make install

   37  sudo modprobe snd-hda-intel

   38  sudo modprobe snd-pcm-oss

   39  sudo modprobe snd-mixer-oss

   40  sudo modprobe snd-seq-oss

   41  sudo reboot
```

---

### Post by danwood76 on 2008-02-14
Ah, finally some progress.
This is good.

Try re installing the alsa-utils, this contains the mixer apps and so on which might explain your errors.
Or we have another issue, but hearing the ubuntu welcome music for the first time is satisfying :)

---

### Post by ClenchedTeeth on 2008-02-14
I did a disk image of the working installation and then went back and did a full reinstall from scratch to make sure I could reproduce the result. It turns out that once I have finished compiling and installing the drivers, I need to reboot WITHOUT modprobing. Upon starting up again I get the sound working but no volume control. So between lines 36 and 37 I must have restarted with the mouse rather than using the command prompt. So, the following set of commands definitely works (this is for my own reference rather than your information I guess):

```

    3  export http_proxy="http://username:password@proxy:3128"

    4  sudo apt-get update

    5  sudo apt-get install synergy

    6  nohup synergyc host &

    7  sudo apt-get install build-essential linux-headers-$(uname -r) libncurses5-dev gawk gettext


    8  cd build/alsa/

    9  tar -xjf alsa-driver-1.0.16.tar.bz2 

   10  tar -xjf alsa-utils-1.0.16.tar.bz2 

   11  tar -xjf alsa-oss-1.0.15.tar.bz2 

   12  tar -xjf alsa-lib-1.0.16.tar.bz2 


   13  ls

   14  cd alsa-driver-1.0.16/

   15  cp ../patch_realtek.c_PATCHED ./alsa-kernel/pci/hda/patch_realtek.c


   16  ./configure --with-cards=hda-intel

   17  make

   18  sudo make install


   19  cd ../alsa-lib-1.0.16/

   20  ./configure

   21  make

   22  sudo make install


   23  cd ../alsa-utils-1.0.16/

   24  ./configure

   25  make

   26  sudo make install


   27  cd ../alsa-oss-1.0.15/

   28  ./configure

   29  make

   30  sudo make install


   31  sudo reboot

   32  history


```
At this stage the sound works but there is no volume control. Note that I haven't modprobed anything yet. Recompiling the alsa-utils with the following commands and rebooting made no change as far as I can see. Sounds still works, but is stuck on 100% and the keyboard shortcuts don't work.

```
cd build/alsa/alsa-utils-1.0.16/

make clean

./configure

make

sudo make install

sudo reboot


```

---

### Post by danwood76 on 2008-02-15
I think it may be an issue with the ALC861_ASUS_LAPTOP option.
This can give funny results.

This is a dump of the list of options for the ALC861:
```

	ALC861_3ST,
	ALC660_3ST,
	ALC861_3ST_DIG,
	ALC861_6ST_DIG,
	ALC861_UNIWILL_M31,
	ALC861_TOSHIBA,
	ALC861_ASUS,
	ALC861_ASUS_LAPTOP,
	ALC861_AUTO,
	ALC861_MODEL_LAST,

```

I dumped that from the patch_realtek.c file.
You could try the ALC861_TOSHIBA option, and obviously work your way through the list if you like.
The toshiba option (looking at the source code) uses a different mixer but the same sound options, so may give you control over it hopefully.

So for example:
```

	SND_PCI_QUIRK(0x1179, 0xff31, "Toshiba L30", ALC861_TOSHIBA),

```
Would be your patch line.

You only need to recompile the alsa-driver but you do need to reboot each time as it is a kernel module.

---

### Post by ClenchedTeeth on 2008-02-15
Here's what I've tried so far, and some of them have given me equivalent results to ALC861_ASUS_LAPTOP, but none of them have allowed me to change the  volume, run alsamixer etc. so far.

Have tried all of these:
```
	/*SND_PCI_QUIRK(0x1179, 0xff31, "Toshiba L30", ALC861_ASUS_LAPTOP),*/
	/*SND_PCI_QUIRK(0x1179, 0xff31, "Toshiba L30", ALC861_TOSHIBA),*/
	/*SND_PCI_QUIRK(0x1179, 0xff31, "Toshiba L30", ALC861_3ST),*/
	/*SND_PCI_QUIRK(0x1179, 0xff31, "Toshiba L30", ALC861_AUTO),*/
	/*SND_PCI_QUIRK(0x1179, 0xff31, "Toshiba L30", ALC861_MODEL_LAST),*/
	/*SND_PCI_QUIRK(0x1179, 0xff31, "Toshiba L30", ALC861_ASUS),*/
	SND_PCI_QUIRK(0x1179, 0xff31, "Toshiba L30", ALC861_UNIWILL_M31),
```

These ones have worked (ie they give me sound, but no volume adjustments etc:
```
	/*SND_PCI_QUIRK(0x1179, 0xff31, "Toshiba L30", ALC861_ASUS_LAPTOP),*/
	/*SND_PCI_QUIRK(0x1179, 0xff31, "Toshiba L30", ALC861_ASUS),*/
	SND_PCI_QUIRK(0x1179, 0xff31, "Toshiba L30", ALC861_UNIWILL_M31),
```

So far it's been slow going, I'll keep trying with the rest.

---

### Post by ClenchedTeeth on 2008-02-15
Have tried them all now, and the only ones that worked were ALC861_UNIWILL_M31, ALC861_ASUS and ALC861_ASUS_LAPTOP. None of them got the volume controls, keyboard shortcuts, alsamixer etc working. I did notice that some of them showed different options (mic, line in, cd etc) in the bottom panel of the sound preferences control panel.

---

### Post by danwood76 on 2008-02-16
If you run alsamixer do any of the volume controls in that change the volume?
The alsamixer will show all the volume controls available, I would try this with the ALC861_ASUS_LAPTOP option as I think this is the correct choice.

The GNOME mixer hides the options it thinks are unused, so if any of the alsalmixer controls works as a volume control you can always enable that option in the gnome mixer and set that to be the adjusted volume with the shortcut keys.

-- edit --

I was just looking through the bug reports on the alsa-project site relating to this card and one guy reports the same behaviour as you have and that the PCM option in alsa mixer works for changing the volume.
It should be quite a simple task to select that for the GNOME mixer to use.

---

### Post by ClenchedTeeth on 2008-02-16
> **danwood76 said:**
> If you run alsamixer do any of the volume controls in that change the volume?
The alsamixer will show all the volume controls available, I would try this with the ALC861_ASUS_LAPTOP option as I think this is the correct choice.


In every case alsamixer returns the error:
```
alsamixer: function snd_mixer_load failed: No such file or directory
```
when I try to run it. The only time I have had it working is when I was patching the VD section (IIRC).

---

### Post by danwood76 on 2008-02-16
Could you post the output of:
```

lsmod | grep snd

```

I have tested patching my drivers in different places making it load different sound cards.
I cant seem to make it break the mixer, so Im confused.
It might be that the mixer module isnt loading.

also:
```

dmesg | grep hda

```

will show us if there are errors loading the modules.

Hopefully it will turn something up we can go on.

regards,
Danny

---

### Post by ClenchedTeeth on 2008-02-16
Minor improvement: I ran alsaconf and now my keyboard shortcuts seem to work better: the keys I press now show up with corresponding visuals on the screen, but they still have no effect on the actual sound level. Alsamixer still refuses to run.

The outputs you asked for are as follows:
```
rory@frink:~$ lsmod | grep snd

snd_hda_intel         341912  1 

snd_pcm_oss            42784  0 

snd_mixer_oss          18048  2 snd_pcm_oss

snd_pcm                78596  2 snd_hda_intel,snd_pcm_oss

snd_page_alloc         11656  2 snd_hda_intel,snd_pcm

snd_hwdep              10628  1 snd_hda_intel

snd_seq_oss            35456  0 

snd_seq_midi_event      8704  1 snd_seq_oss

snd_seq                54224  4 snd_seq_oss,snd_seq_midi_event

snd_timer              24964  2 snd_pcm,snd_seq

snd_seq_device          9740  2 snd_seq_oss,snd_seq

snd                    56740  9 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_oss,snd_seq,snd_timer,snd_seq_device

soundcore               8800  2 snd


```

```
rory@frink:~$ dmesg | grep hda

[   32.256000] hda-intel: Invalid position buffer, using LPIB read method instead.


```

---

### Post by ClenchedTeeth on 2008-02-24
Hey, sorry to bump this thread, but did that info give you any ideas about what I should do?

---

### Post by danwood76 on 2008-02-24
Sorry I forgot to reply to your other post.

You have exactly the same sound modules loaded as me and the dmesg error is similar to the dmesg error on mine.
I think its more of a warning that an error.

Otherwise im pretty stumpted.
I still think that maybe the alsa utils is broken in some way.

If you re patch the patch_realtek.c in the original way (ALC861VD) does the mixer then run? If not then there is probably an issue with the alsa-utils or alsa-lib install.

regards,
Danny

---

### Post by ClenchedTeeth on 2008-02-24
> **danwood76 said:**
> Sorry I forgot to reply to your other post.

No worries! 
Patching in the original/ALC861VD way doesn't get alsamixer going. I'm at a loss trying to figure out how I got to the point I was at in post #37. Will try imaging a fresh install back on and see if I can get any further. I'll keep an eye on the output created by compiling utils and lib, maybe there's an error in there that I missed.

---

### Post by ClenchedTeeth on 2008-02-24
Trying the original/ALC861VD patch on a fresh install makes no difference. alsamixer still refuses to run. Looking back on what I was doing, I was still modprobing at that stage. Running these four modprobe commands doesn't seem to make a difference either.

---

### Post by danwood76 on 2008-02-25
Does alsamixer load before you compile the drivers.
With the default sound drivers? (fresh install)

If it does you could try patching and compiling version 1.0.14 of the alsa driver (Gutsys default version) which I think you can grab from the repositories.

So on a clean install:
```

sudo apt-get install alsa-source

```
This will download the alsa-driver source package that is compatible with the default installed alsa version.
When downloaded it is located /usr/src/alsa-driver.tar.bz2

Then follow the patching and install method using just the driver section.
Note that you will have to patch the file again and not re use your patch_realtek.c from the later version as it wont be compatible.

This should, if you were able to load the alsa mixer from default, get you to working sound plus the mixer.

Good luck,
Danny

---

### Post by ClenchedTeeth on 2008-02-25
Hi, don't have laptop with me at the moment, but I will try that tomorrow. So I should only do the alsa-driver bit? How do I prevent it from trying to update alsa to the latest version in the future?

---

### Post by apienk01 on 2008-02-25
Hi, sorry to interrupt, but I've had a similar problem. After compiling new ALSA I couldn't modprobe snd-hda-intel (unrecognized symbol). I tracked down the cause to a file version conflict. It turns out that ALSA installer (make install) places its modules in a different dir than Gutsy packages. So when you 'make install', you end up with two snd-hda-intel.ko's, one version 1.0.14 (Gutsy) and the other 1.0.16 (in my case). The solution is to deinstall 1.0.14 Gutsy ALSA packages (libasound2, alsa-base, alsa-oss, alsa-utils), then manually remove the old module before 'sudo make install'. The old one can be identified by creation date.

```
sudo updatedb
locate snd-hda-intel.ko
```

Hope it helps.

---

### Post by danwood76 on 2008-02-25
> **ClenchedTeeth said:**
> Hi, don't have laptop with me at the moment, but I will try that tomorrow. So I should only do the alsa-driver bit? How do I prevent it from trying to update alsa to the latest version in the future?

Yes just recompile the driver section, that is all you will get with the alsa-source package anyway.

About stopping it from updating, I think you can tell it to force a version in synaptic which will stop it from trying to update.

---

### Post by ClenchedTeeth on 2008-02-25
> **danwood76 said:**
> Does alsamixer load before you compile the drivers.
With the default sound drivers? (fresh install)

Oops, I forgot to check. Will try to remember next time I go back to a fresh install. (Edit: yes, alsamixer does run on a fresh install. Sound preferences shows two cards "HDA ATI SB (Alsa mixer)", and "Realtek ALC861 (OSS Mixer)".)
However, after doing the alsa-source install, the sound didn't work and alsamixer didn't work. No devices show in the Sound Preferences window.

> **apienk01 said:**
> Hi, sorry to interrupt, but I've had a similar problem. After compiling new ALSA I couldn't modprobe snd-hda-intel (unrecognized symbol). I tracked down the cause to a file version conflict. It turns out that ALSA installer (make install) places its modules in a different dir than Gutsy packages. So when you 'make install', you end up with two snd-hda-intel.ko's, one version 1.0.14 (Gutsy) and the other 1.0.16 (in my case). The solution is to deinstall 1.0.14 Gutsy ALSA packages (libasound2, alsa-base, alsa-oss, alsa-utils), then manually remove the old module before 'sudo make install'. The old one can be identified by creation date.

```
sudo updatedb
locate snd-hda-intel.ko
```

Hope it helps.

Thanks for this suggestion, will try this next...

---

### Post by ClenchedTeeth on 2008-02-25
> **apienk01 said:**
> Hi, sorry to interrupt, but I've had a similar problem. After compiling new ALSA I couldn't modprobe snd-hda-intel (unrecognized symbol). I tracked down the cause to a file version conflict. It turns out that ALSA installer (make install) places its modules in a different dir than Gutsy packages. So when you 'make install', you end up with two snd-hda-intel.ko's, one version 1.0.14 (Gutsy) and the other 1.0.16 (in my case). The solution is to deinstall 1.0.14 Gutsy ALSA packages (libasound2, alsa-base, alsa-oss, alsa-utils), then manually remove the old module before 'sudo make install'. The old one can be identified by creation date.

```
sudo updatedb
locate snd-hda-intel.ko
```

Hope it helps.
Just trying this now, I have run the command:
```
sudo apt-get remove libasound2 alsa-base alsa-oss alsa-utils


```
which actually removed a huge number of components, probably because they all involve sound in some way. It leaves a LOT of things not working - is there something I'm doing wrong?

---

### Post by danwood76 on 2008-02-27
it will break a lot of packages if you remove alsa.
I have never removed alsa before or after installing the latest drivers.

You can remove the modules manually, by deleting them from the modules.dep file (this wont actually remove the modules just makes it think theyre not there)

To do this enter the following command:
```

sudo gedit /lib/modules/$(uname -r)/modules.dep

```

then search for the module name you wish to remove, for example snd-hda-intel.ko
I find it at:
```

84. **/lib/modules/2.6.23.11-15.12.07/kernel/sound/pci/hda/snd-hda-intel.ko:** /lib/modules/2.6.23.11-15.12.07/kernel/sound/acore/snd-pcm.ko /lib/modules/2.6.23.11-15.12.07/kernel/sound/acore/snd-timer.ko /lib/modules/2.6.23.11-15.12.07/kernel/sound/acore/snd-page-alloc.ko /lib/modules/2.6.23.11-15.12.07/kernel/sound/acore/snd-hwdep.ko /lib/modules/2.6.23.11-15.12.07/kernel/sound/acore/snd.ko /lib/modules/2.6.23.11-15.12.07/kernel/sound/soundcore.ko

```
Note that this is my desktop and im running kernel v2.6.23-11, it is also good to enable line numbers so you actually delete only that line and nothing else after it.
I can simply delete the line above and save to remove that module, there are quite a few sound modules, they all start with snd- luckily so you could search through the list just doing snd-.
Only delete the module names that begin with snd-, so in the above example the actual module is snd-hda-intel as that is what appears first. (ive made it bold to point this out)

I did do this on my laptop a few weeks ago to test it out, I removed all the sound modules and actually deleted them too (their locations can be found from this modules.dep file)
Then I reinstalled the sound drivers and it was working again.

Removing stuff using synaptic will remove all stuff that depends on it so its best not to remove core modules using synaptic.

---

### Post by ClenchedTeeth on 2008-02-27
I'm a little confused - do I need to:
- remove all lines which mention 'snd-'?
- remove all lines which mention 'snd-hda-intel'?
- remove all entries containing 'snd-' (and leave the rest of the line intact?
- remove all entries containing 'snd-hda-intel' (and leave the rest of the line intact?
Sorry, I think it's the second option but I am not sure.

---

### Post by danwood76 on 2008-02-27
First I would backup the modules.dep that way you can restore it if you completely mess it up.
Then I would remove each line with snd- in it, save the file and reboot.

It should then give you errors about missing sound modules so then recompile the driver then the libs then the utils and the oss.

---

### Post by ClenchedTeeth on 2008-02-27
I had no success with this. Removed all of the appropriate lines from the text file, rebooted, compiled and installed alsa, rebooted again and have no sound. Alsamixer won't run.
I might try the other method now, of just removing ubuntu's default .ko file as per apienk01's suggestion.

---

### Post by ClenchedTeeth on 2008-03-02
I removed that file before compiling/installing alsa, but it didn't seem to make any noticable change.

---

### Post by stedevil on 2008-03-06
I've posted in this thread how to get all sound working on my 
Toshiba Equium L30-149 (PSL35E-002002N5) with the ATI SB450 (ACL861VD) soundchip

I don't know which L30 exactly you have, but it might be worth a shot :)
[http://ubuntuforums.org/showthread.php?p=4462175#post4462175](http://ubuntuforums.org/showthread.php?p=4462175#post4462175)

---

### Post by ClenchedTeeth on 2008-03-07
> **stedevil said:**
> I've posted in this thread how to get all sound working on my 
Toshiba Equium L30-149 (PSL35E-002002N5) with the ATI SB450 (ACL861VD) soundchip

I don't know which L30 exactly you have, but it might be worth a shot :)
[http://ubuntuforums.org/showthread.php?p=4462175#post4462175](http://ubuntuforums.org/showthread.php?p=4462175#post4462175)

Thanks - just having a go at this now...

---

### Post by ClenchedTeeth on 2008-03-07
That didn't work. I started with a fresh install, made the changes you outlined in that post,and rebooted.

If you are interested, the output of lspci -vvnn is:
```
00:14.2 Audio device [0403]: ATI Technologies Inc SB450 HDA Audio [1002:437b] (rev 01)

        Subsystem: Toshiba America Info Systems Unknown device [1179:ff31]

        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-

        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=slow >TAbort- <TAbort- <MAbort- >SERR- <PERR-

        Latency: 64, Cache Line Size: 32 bytes

        Interrupt: pin ? routed to IRQ 19

        Region 0: Memory at c0000000 (64-bit, non-prefetchable) [size=16K]

        Capabilities: [50] Power Management version 2

                Flags: PMEClk- DSI- D1- D2- AuxCurrent=55mA PME(D0+,D1-,D2-,D3hot+,D3cold+)

                Status: D0 PME-Enable- DSel=0 DScale=0 PME-

        Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-

                Address: 0000000000000000  Data: 0000


```

So it looks almost identical to yours. Note that mine doesn't seem to be a VD model, according to the sound control panel from when we got the sound (but not volume etc) working.

---

### Post by stedevil on 2008-03-08
> **ClenchedTeeth said:**
> That didn't work. I started with a fresh install, made the changes you outlined in that post,and rebooted.

If you are interested, the output of lspci -vvnn is:
00:14.2 Audio device [0403]: ATI Technologies Inc SB450 HDA Audio [1002:437b] (rev 01)
Subsystem: Toshiba America Info Systems Unknown device [1179:ff31]


That looks EXACTLY like the stuff I have. Very surprised to hear it's not working.

Just a quick confirmation on that you did everything
* Installed ALSA 1.0.16

* Added /etc/modprobe.d/alsa-base
options snd-hda-intel model=dallas
(and removed any other sound options you had there)

* Reboot

If you did those things and it still doesnt work, go to this webpage and download the alsa-info.sh script
[http://www.alsa-project.org/main/index.php/Help_To_Debug](http://www.alsa-project.org/main/index.php/Help_To_Debug)
Run it and paste the link here so we can try to find out what's broken.

---

### Post by LuisGMarine on 2008-03-08
run this command:

```
gksu gedit /etc/modprobe.d/alsa-base
```


change the last line so it reads:

```
options snd-hda-intel model=toshiba
```

if you don't have a line that looks like that, then just add it to the file.  Save and reboot and try sound, it * SHOULD * be louder.  if not follow these steps in this guide,

[http://ubuntuforums.org/showthread.php?t=715301](http://ubuntuforums.org/showthread.php?t=715301)

---

### Post by ClenchedTeeth on 2008-03-08
Sorry, you're probably not up with the current state of affairs - I can get the sound working, but I can't get any of the mixers going. If I compile and install the patched version of alsa, I get the sound working but at ridiculously loud volumes. Alsamixer will not run, and none of the fn keyboard shortcuts work. (mute/volume up/volume down).
Fair enough, the 100 posts in this thread are a pretty boring read! I will edit my first post so that newcomers will know where I am at.

Dont have my laptop with me at the moment, will update you when I do. However, I do know that I didn't delete the other option lines in that file...

---

### Post by stedevil on 2008-03-09
> **LuisGMarine said:**
> 
```
options snd-hda-intel model=toshiba
```


I know for a fact that model=toshiba is completely screwed up on hardware with lspci -vvnn
...
00:14.2 Audio device [0403]: ATI Technologies Inc SB450 HDA Audio [1002:437b] (rev 01)
Subsystem: Toshiba America Info Systems Unknown device [1179:ff31]
...

[color=orange]Edit: I'm actually partially wrong about this. Driver is chosen by CODEC ID and then Subsystem ID. So in this case my computer is ALC861VD - [1179:ff31] while ClenchedTeeth's is  ALC861 - [1179:ff31], so NOT the same even though SB450 HDA Audio [1002:437b] would fool you into believing otherwise.[/color]

BTW, what lspci -vvnn output do your hardware have? Is it even working with the same codec? 


> **ClenchedTeeth said:**
> I can get the sound working, but I can't get any of the mixers going. If I compile and install the patched version of alsa, I get the sound working but at ridiculously loud volumes. Alsamixer will not run, and none of the fn keyboard shortcuts work. (mute/volume up/volume down).


Hold on, are you adding your own custom patches to alsa 1.0.16? DONT! The vanilla 1.0.16 works out of the box with model=dallas

I have the patch that will be in 1.0.17, but the only difference to vanilla .16 is that names have been corrected and MIC boost channels added. All sound mixing works as it should with .16 model=dallas

And oh, do run the alsa-info.sh script from [1] just so we verify that you dont have conflicting driverversions or something screwing things up for you.  

This is how it looks for me btw [http://pastebin.ca/930516](http://pastebin.ca/930516)

[1] [http://www.alsa-project.org/main/index.php/Help_To_Debug](http://www.alsa-project.org/main/index.php/Help_To_Debug)

---

### Post by ClenchedTeeth on 2008-03-09
I just tried again, here's what I did:

Starting with a fresh install, installed the required packages needed to compile alsa.
Unzipped alsa.
Went into the driver, libs, utils, oss folders (in that order) and ran the commands "./configure", "make", "sudo make install" in each one. (Note that I usually do "--with-cards=hda-intel" with the driver's ./configure command, but you said do a plain install so I left it out. I'm a little unsure if this was right or not.)
Changed my /etc/modprobe.d/alsa-base file to look like this:
```

# autoloader aliases

install sound-slot-0 /sbin/modprobe snd-card-0

install sound-slot-1 /sbin/modprobe snd-card-1

install sound-slot-2 /sbin/modprobe snd-card-2

install sound-slot-3 /sbin/modprobe snd-card-3

install sound-slot-4 /sbin/modprobe snd-card-4

install sound-slot-5 /sbin/modprobe snd-card-5

install sound-slot-6 /sbin/modprobe snd-card-6

install sound-slot-7 /sbin/modprobe snd-card-7



# Cause optional modules to be loaded above generic modules

install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe --quiet snd-ioctl32 ; : ; }

install snd-pcm /sbin/modprobe --ignore-install snd-pcm && { /sbin/modprobe --quiet snd-pcm-oss ; : ; }

install snd-mixer /sbin/modprobe --ignore-install snd-mixer && { /sbin/modprobe --quiet snd-mixer-oss ; : ; }

install snd-seq /sbin/modprobe --ignore-install snd-seq && { /sbin/modprobe --quiet snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }

install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi && { /sbin/modprobe --quiet snd-seq-midi ; : ; }

# Cause optional modules to be loaded above sound card driver modules

install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }

install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }



# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)

install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }



# Load snd-seq for devices that don't have hardware midi;

#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for

#   non-Creative Labs PCI hardware

install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }

# Prevent abnormal drivers from grabbing index 0

# options snd-hda-intel model=dallasoptions snd-bt87x index=-2

# options cx88-alsa index=-2

# options saa7134-alsa index=-2

# options snd-atiixp-modem index=-2

# options snd-intel8x0m index=-2

# options snd-via82xx-modem index=-2

# options snd-usb-audio index=-2

# options snd-usb-usx2y index=-2

# options snd-usb-caiaq index=-2

# Ubuntu #62691, enable MPU for snd-cmipci

# options snd-cmipci mpu_port=0x330 fm_port=0x388



# Added by me:
options snd-hda-intel model=dallas

```

Rebooted and I get no sound. Alsamixer doesn't run and the keyboard shortcuts don't run.

Should I have used the option "--with-cards=hda-intel"?

---

### Post by ClenchedTeeth on 2008-03-09
Oh, and for the alsa-info.sh script, do you want me to run it after a fresh ubuntu install, after alsa installed and sound working at 100% volume, or after doing the dallas option that you described? Or does it not matter?
One thing I will say straight away, is that my card identifies itself differently:
```
!!HDA-Intel Codec information
!!---------------------------
--startcollapse--
Codec: Realtek ALC861
```
While yours reads:
```
  88. HDA-Intel Codec information
  89. ---------------------------
  90. (click to collapse section)
   1.  
   2. Codec: Realtek ALC861-VD
```
As danwood76 has already said, while my card has the same identifiers, it identifies itself as the non VD model for some reason.

---

### Post by stedevil on 2008-03-09
> **ClenchedTeeth said:**
> 
 (Note that I usually do "--with-cards=hda-intel" with the driver's ./configure command, but you said do a plain install so I left it out. I'm a little unsure if this was right or not.)


This doesnt matter in this case. That option just tells the computer to only compile the HDA-INTEL driver, saving some compilation time.

> 
# Added by me:
options snd-hda-intel model=dallas


That seems like you did everything just as you should, but that your soundchip identifies itself as a NON VD is really weird. Only thing I can think of is that you might need a BIOS update for your laptop. Do you have the latest?

But before that, run the script and post the link, just in case we can find something weird in there. And run it with 1.0.16 installed and model=dallas

---

### Post by ClenchedTeeth on 2008-03-09
There you go:
[http://pastebin.ca/935942](http://pastebin.ca/935942)
From memory I have the latest bios but it's a very good idea so I will check just in case.

---

### Post by stedevil on 2008-03-09
OK, I immediately spot 1 thing (that I should have already seen). You have commented out all the default options that are there to BLOCK weird drivers being loaded in ways that can break things. When I said "(and removed any other sound options you had there)" I meant the lines you might have added yourself previously. So put those default ones in again how they where and reboot. If it's still not working, run the script again.

I'll keep looking meanwhile.

---

### Post by ClenchedTeeth on 2008-03-09
Turns out the bios was not updated. After updating it and running the script, it still identifies itself as the non VD variant.

---

### Post by stedevil on 2008-03-09
> **ClenchedTeeth said:**
> Turns out the bios was not updated. After updating it and running the script, it still identifies itself as the non VD variant.

Is that with our without putting back the default/bugfix soundoptions?

---

### Post by ClenchedTeeth on 2008-03-09
> **stedevil said:**
> OK, I immediately spot 1 thing (that I should have already seen). You have commented out all the default options that are there to BLOCK weird drivers being loaded in ways that can break things. When I said "(and removed any other sound options you had there)" I meant the lines you might have added yourself previously. So put those default ones in again how they where and reboot. If it's still not working, run the script again.


Oops, ok the default lines are back in there. I rebooted and still have no luck. There is now no audio device showing in the sound control panel.
Running the script again gives this: [http://pastebin.ca/935992](http://pastebin.ca/935992) Doesn't look like there are any sound cards being detected now...

---

### Post by stedevil on 2008-03-09
You have a small typo/cut'n'paste error in there from 1 point or another

snd-hda-intel: model=dallasoptions snd-bt87x index=-2

should be

snd-bt87x: index=-2


so remove the "options snd-hda-intel: model=dallas" from the front of that line

---

### Post by ClenchedTeeth on 2008-03-09
Sorry about that. I've fixed that and rebooted. (I didn't put in the colons you showed since the rest of the lines in that file didn't have them - they're put in by the script.)
I've commented out the dallas line, so the lines now look like this
```
# options snd-hda-intel model=dallas
options snd-bt87x index=-2
```
Script results: [http://pastebin.ca/936008](http://pastebin.ca/936008)

---

### Post by stedevil on 2008-03-09
Ok, at least we got the settings sorted, but it really puzzles me that you have the same subsystem ID for another hardware. I'm starting to think that maybe Toshiba has screwed up royally because I've spotted another Toshiba model reporting the same Subsystem ID

[Here](helllabs.org/codecgraph/#Conexant%20CX20551%20(Waikiki))

I'll ask the alsa HDA-Intel coder I've been in direct contact with to make both my Desktop and Laptop work in case he can shed some light on this matter and perhaps provide a solution. 

Meanwhile, perhaps you can post the full model name/number of your laptop? Mine is
Toshiba Equium L30-149 (PSL35E-002002N5)
Maybe it might help someone sort out what is going on here.


Additionally, any extra info you can provide about your system could potentially be very helpful for the hda-intel coders to help you fix this problem. 

So go to [http://helllabs.org/codecgraph/](http://helllabs.org/codecgraph/) and download, unpack and run it.
Probably you will also have to install graphviz first (it's in the ubuntu repositories so use synaptic or whatever tool you prefer).

To generate the other requested files, just do
sudo lspci -vvnn > lspci
and
cat /proc/asound/card0/codec#0 > codec#0

(if you happen to have also codec#1 etc, do the same for them for good measure)

Then send all the files and svg to [email]ehabkost@raisama.net[/email] so they can add your data to the page.

---

### Post by ClenchedTeeth on 2008-03-09
Getting in touch with the HDA-Intel coder sounds great.
The box the laptop came in, and the sticker on the bottom of the laptop itself both say:
Model name: Satellite L30
Part no.: PSL30A-00100E
Which I can find at the australian toshiba website (toshiba.com.au). I didn't buy the laptop new, but the guy I bought it from is in New Zealand (and so am I). It seems to be very rare, possibly something that was only sold in australasia?
I'll get that other info sorted out soon, would you like a copy of that stuff on this thread too?

---

### Post by stedevil on 2008-03-09
Well, I guess posting it here as well could never hurt.

Regarding "special/rare" modell, apparently that is how Toshiba (and possibly others as well) do. They have different model names for (very) similar products on different markets. Eg my laptop couldnt be found unless one went though the Swedish "portal" at Toshiba. If you have a direct link to the webpage with the specs to your exact model, then post that link too. :)

---

### Post by ClenchedTeeth on 2008-03-09
Info on the laptop can't be directly linked, you need to go to [www.toshiba.com.au](www.toshiba.com.au), click on "Mobile Computing", click on "Support" in the grey bar on the left, the click on "Drivers, BIOS, Utilities" in the download centre, then select notebooks > satellite > L30-(PSL30A).> GO. Hope that made sense!
The files are attached...

---

### Post by stedevil on 2008-03-09
> **ClenchedTeeth said:**
> Info on the laptop can't be directly linked,  Hope that made sense!


[This page](http://www.isd.toshiba.com.au/71/live.dll/topic/content/driver_search_list.jsp?BV_SessionID=%40%40%40%401972638649.1205119899%40%40%40%40&BV_EngineID=ccceadedggdggfkcefecekfdffhdfgi.0&theAction=true&CATOID=-15058&MODE=NPRO&ProductMenu_0=Notebooks&ProductMenu_1=Satellite&ProductMenu_2=1153629&x=19&y=7) you mean? ;)

---

### Post by ClenchedTeeth on 2008-03-09
> **ClenchedTeeth said:**
> Info on the laptop can't be directly linked, you need to go to [www.toshiba.com.au](www.toshiba.com.au), click on "Mobile Computing", click on "Support" in the grey bar on the left, the click on "Drivers, BIOS, Utilities" in the download centre, then select notebooks > satellite > L30-(PSL30A).> GO. Hope that made sense!
The files are attached...

When I try that link, it just tells me that my session has timed out. It relies on cookies or some other such magic. I almost fell for that too :D, (opening the frame in a new window and grabbing the link) but I checked it on the desktop I have here and it didn't work. It looks like this though:

---

### Post by stedevil on 2008-03-10
Yeah, you're right. It amazes me how much effort some companies put into making their webpages as inaccessible as possible... :P

---

### Post by stedevil on 2008-03-10
Ok, got some explanations today that I though I should share with you. :)

> Toshiba tends to use teh same subsystem ID even though they are using different codecs.  It's not unheard of.  The driver is supposed to first look at the codec ID, then look at the pci subsystem ID and match the system to one in the table.

> 
[The ALC861] codec is very different from the 861VD. ALC861 is for versions A, B, and C for this codec.  The ALC861VD is the "Version D", and has added capabilities and is probably a newer manufacturing process. ...it's the codec ID/Subsystem ID combo that uniquely defines the audio system.  Some manufactures don't even make it that easy.


He further goes on to say that the code for your system is yet incomplete. Time permitting, he will have a look at it this week. So for now you are stuck with broken sound, but hopefully it will look brighter in the nearby future :)

He also sais that meanwhile you likely will need/want
option snd_hda_intel model=toshiba
in /etc/modprobe.d/alsa-base

(of course, once the chip is properly identified, hopefully in Alsa 1.0.17, autodetection should take care of it)

---

### Post by GrueMaster on 2008-03-10
Yea, I said that. 

Hello.  I'm Tobin Davis, Alsa HDA driver contributor and Linux junkie.  I was looking over the information on your system from earlier posts, and based on the driver configuration for that codec, it looks like it is very incomplete.  Could you try a different model, just to see if you get the correct settings?  For example, try "model=6stack-dig", and then run "speaker-test -c 8 -t wav -Dplug:surround7.1" to see what channels drive the speakers and headphones.  Also, with this model, try recording from the microphones.  The goal is to isolate the channels that are actually wired up (this sound chip is a 4 stereo channel out, single stereo channel in codec (overkill for most laptops).

Drop me an email once you have tested this configuration, and I can start shooting you patches to try.  Send to my userID <AT> gmail.com.

Tobin

---

### Post by ClenchedTeeth on 2008-03-10
Just emailing Tobin now...

---

### Post by ClenchedTeeth on 2008-03-10
Just handed out some "thanks" medals to danwood76, GrueMaster and stedevil - I really can't thank you guys enough for helping me with this, I honestly expected my call for help to be lost in the vacuum of the internet and never replied to. You guys are awesome!

---

