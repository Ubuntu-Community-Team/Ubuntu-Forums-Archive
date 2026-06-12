---
title: "[SOLVED] No sound - Realtek ALC262 (ICH8 Family) - snd-hda-intel"
date: 2007-09-30
forum: Hardware &amp; Laptops
---

### Post by brad103 on 2007-09-30
All righty. I have a Toshiba Tecra P5 laptop, running Xubuntu Feisty. Got most things functional now, but I have absolutely no sound (neither built-in speakers nor headphones).

I've tried:
Installing the latest ALSA drivers as detailed [here]("http://ubuntuforums.org/showthread.php?t=535841").

Running alsamixer and unmuting all available channels

Installing gnome-alsamixer and confirming the same

Editing /etc/modprobe.d/alsa-base like [here]("http://ubuntuforums.org/showthread.php?t=314383") or /etc/modprobe.d/snd-hda-intel like [here]("http://ubuntuforums.org/showthread.php?t=539006") with the values from /usr/share/doc/alsa-base/driver/ALSA-Configuration.txt.gz for ALC262 as again suggested [here]("http://ubuntuforums.org/showthread.php?t=314383").

lsmod, lspci and alsa-base are all attached.

Thanks a lot

---

### Post by brad103 on 2007-10-01
Bump. Any ideas out there?

---

### Post by aldeby on 2007-10-02
I read you should have already tried the whole procedure, however I just try it this way in case you missed something: 

```
# apt-get update && apt-get install mercurial build-essential libncurses5 automake autoconf

$ hg clone http://hg.alsa-project.org/alsa-driver alsa-driver
$ hg clone http://hg.alsa-project.org/alsa-kernel alsa-kernel

$ cd alsa-driver
$ ./hgcompile

# make install-modules
# alsaconf

some advice to add in /etc/modprobe.d/alsa-base 
this line "options snd-hda-intel" 

#mv /lib/modules/2.6.22-11-generic/ubuntu/media/snd-hda-intel/snd-hda-intel.ko /tmp
#depmod -a

reboot

```

---

### Post by brad103 on 2007-10-05
Thanks for the help, it is good to have it all in one place.

I tried what you suggested, see below (my comments in blue):

> **aldeby said:**
> I read you should have already tried the whole procedure, however I just try it this way in case you missed something: 

```
# apt-get update && apt-get install mercurial build-essential libncurses5 automake autoconf
[COLOR="Blue"]OK[/COLOR]

$ hg clone http://hg.alsa-project.org/alsa-driver alsa-driver
$ hg clone http://hg.alsa-project.org/alsa-kernel alsa-kernel
[COLOR="Blue"]OK[/COLOR]

$ cd alsa-driver
$ ./hgcompile
[COLOR="Blue"]OK[/COLOR]

# make install-modules
[COLOR="Blue"]OK[/COLOR]
# alsaconf
[COLOR="Blue"]OK - but when it supposedly makes the sound on completion, nothing is heard[/COLOR]

some advice to add in /etc/modprobe.d/alsa-base 
after this line "options snd-hda-intel" this text "laptop=toshiba"
[COLOR="Blue"]NOT OK - dmesg: unknown parameter 'laptop'[/COLOR]

#mv /lib/modules/2.6.22-11-generic/ubuntu/media/snd-hda-intel/snd-hda-intel.ko /tmp
[COLOR="Blue"]UH, GET RID OF THE MODULE?[/COLOR]
#depmod -a
[COLOR="Blue"]From linux.about.com:
Depmod creates a "Makefile"-like dependency file, based on the symbols it finds in the set of modules 
mentioned on the command line or from the directories specified in the configuration file.
This dependency file is later used by modprobe to automatically load the correct module or stack of modules.

So what would this achieve? When I tried this then the sound card device wasn't even visible on boot.[/COLOR]

reboot

```

Thanks again

---

### Post by aldeby on 2007-10-07
```
# alsaconf
[COLOR="SeaGreen"]you are right, it does not output any sound to me too, 
probably because although  drivers are installed the sound daemon is 
not running yet anyway this should not be a problem[/COLOR]

some advice to add in /etc/modprobe.d/alsa-base 
after this line "options snd-hda-intel" this text "laptop=toshiba"
[COLOR="SeaGreen"]yes you are right, laptop=toshiba is no longer
 required, it was my mistake not having took it off :)[/COLOR]

#mv /lib/modules/2.6.22-11-generic/ubuntu/media/snd-hda-intel/snd-hda-intel.ko /tmp
[COLOR="SeaGreen"]yes because the new driver does not overwrite the older one,
 the new driver is installed in  /lib/modules/2.6.22-12-generic/kernel/sound/pci/hda/
 while the one provided by ubuntu packages is in 
 /lib/modules/2.6.22-12-generic/ubuntu/media/snd-hda-intel so it happens that 
linux loads the ubuntu one and not the one we have installed.
You do not actually delete the module, but move it to /tmp folder,
 in case you want to revert the change you can still 
find it there for some time[/COLOR]

#depmod -a
[COLOR="SeaGreen"]
depmod -a (or depmod --all) is intended to check if
module dependencies are satisfied, it should not prompt
 you with an output if these are satisfied. 
Unfortunately I'm not very deep into this.

       Linux kernel modules can provide services (called "symbols") for  other
       modules  to  use (using EXPORT_SYMBOL in the code).  If a second module
       uses this symbol, that second module clearly depends on the first  mod&#8208;
       ule.  These dependencies can get quite complex.

       depmod  creates  a  list of module dependencies, by reading each module
       under /lib/modules/version and determining what symbols it exports, and
       what  symbols it needs. [/COLOR]

reboot

```

---

### Post by aldeby on 2007-10-07
it also seems with latest updates string 'option snd-hda-intel' is no longer recognised by alsa during the bootstrap, nontheless audio subsystem works without an issue.

---

### Post by brad103 on 2007-10-27
Thanks a lot for the help. I decided to dual boot with windows and couldn't get sound working there either. Sent laptop back to the supplier and it had a hardware fault! Back now all fixed and all is working well (except that headphone jack works in windows but is ignored in ubuntu, but that's for another thread).

Thanks :)

---

