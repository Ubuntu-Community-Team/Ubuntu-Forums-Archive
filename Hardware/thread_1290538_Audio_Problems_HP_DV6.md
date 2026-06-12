---
title: "Audio Problems HP DV6"
date: 2009-10-13
forum: Hardware
---

### Post by sirsmilealot on 2009-10-13
Hello All,

I have an HP Pavilion DV6-1240ea laptop with an audio problem running Ubuntu 9.04. When using OpenSUSE this issue was remedied by adding the line:

```
options snd-hda-intel model=hp-m4 enable_msi=1
```

to

```
/etc/modprobe.d/sound
```

though I could not find this file in Ubuntu. Instead I entered it into

```
/etc/modprobe.d/alsa-base.conf
```

but still no joy. Any help would be greatly appreciated!

Kind Regards,

Paul Smith.

---

### Post by nzadLithium on 2009-10-13
```
options snd-hda-intel model=hp-m4 enable_msi=1
```

Did you try 
sudo rmmod snd-hda-intel
sudo modprobe snd-hda-intel model=hp-m4 enable_msi=1

If that works then its not checking your options at boot, if it doesn't then those options are not the solution to the problem in ubuntu/whatever version of alsa ubuntu is using.

---

### Post by sirsmilealot on 2009-10-14
Thanks for your reply. I've dropped those commands into terminal and this is what I get:

```
$ sudo rmmod snd-hda-intel
ERROR: Module snd_hda_intel is in use
$ sudo modprobe snd-hda-intel model=hp-m4 enable_msi=1
WARNING: All config files need .conf: /etc/modprobe.d/sound, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/oss-compat, it will be ignored in a future release.

```

---

### Post by sirsmilealot on 2009-10-14
I tried renaming those files with .conf and executed the command. I didn't get any feedback and there was no audio. This one has me stumped!

---

### Post by nzadLithium on 2009-10-15
do lsmod, find out whatever is using snd-hda-intel and rmmod those as well. Make a list so you can make sure they all start again once u start snd-hda-intel again.

---

### Post by Yellow Pasque on 2009-10-15
Have you tried model=hp-dv5 ?

---

### Post by sirsmilealot on 2009-10-17
> **Temüjin said:**
> Have you tried model=hp-dv5 ?

Thanks for your post. I have tried this but still nothing as of yet. Can you confirm where I ought to be adjusting the config files? I'm assuming

```
/etc/modprobe.d/alsa-base.conf
```

is correct though I am trying other locations too!

Cheers,

Paul.

---

### Post by nzadLithium on 2009-10-18
that should be correct. But as i was saying before try and load it manually first. Theres no point in playing round with config files until you actually know your options work. At the moment whenever you stick it in a config file theres too things that come into play, is it loading the config file, did you set the right options, (another possibility is did you actually put it in the file right but i think you've got that one :p), if you load the module manually first then you can tell without having the thing of is it not working coz it didnt load or is it not working coz i have the wrong options.

---

### Post by KeLa on 2009-10-19
I had the same problem with the same hardware and after updating alsa drivers to version 1.0.20 i get sound to work. 

Only problem i have at this time is that only internal speakers are working (none of the two headphone connectors are not working)

Can anybody help about the headphone issue?

---

### Post by KeLa on 2009-10-19
Solved the headphone problem and now audio is working ok.
Just needed to reinstall ubuntu 9.04 and install 1.0.21 version of alsa driver, lib and utils
as documented here: [http://monespaceperso.org/blog-en/2009/08/31/upgrade-alsa-1-0-21-on-ubuntu-jaunty-9-04/](http://monespaceperso.org/blog-en/2009/08/31/upgrade-alsa-1-0-21-on-ubuntu-jaunty-9-04/)
then added following lines to /etc/modprobe.d/alsa-base.conf

alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
options snd-hda-intel model=hp-m4

and after reboot sound works with internal speakers and headphones.

One backup plan i did is that i went and but Terratec Aureon Dual USB stick
and that has mic input + speaker/optical output and it works out of box.
This optical output is one thing i missed and needed on this laptop and now i have it also.

-KeLa-

---

### Post by mahboop on 2009-10-22
it works 100%
Advanced Linux Sound Architecture Driver Version 1.0.21.
Compiled on Oct 22 2009 for kernel 2.6.28-15-generic (SMP).
[COLOR="DarkRed"]**speakers and headphone**[/COLOR] are working FINE now on my hp pavilion dv6

Thanks

---

### Post by sirsmilealot on 2009-10-25
Apologies for the delay in replying chaps but as above, I managed to resolve this issue using the latest snapshot drivers. Now to solve the suspend/hibernate problems!

Cheers for your help!

Paul.

---

