---
title: "nVidia Mixer (nvmixer)"
date: 2005-03-26
forum: Hardware &amp; Laptops
---

### Post by Dracontopes on 2005-03-26
[font=Verdana]Problem: nVidia Mixer (nvmixer) does not remember the settings I gave it. After a reboot all settings are gone. :neutral:

nVidia has a solution for this particular problem, which is this:

```


 If you wish to have nvmixer audio settings automatically restored each time the nvsound driver loads, add the following lines to the configuration file for 2.4 kernels:

post-install nvsound sleep 1; /usr/bin/nvmix-reg -f /etc/nvmixrc -L >/dev/null 2>&1 ||:
pre-remove nvsound /usr/bin/nvmix-reg -f /etc/nvmixrc -S >/dev/null 2>&1 ||:

 For 2.6 kernels:

install nvsound /sbin/modprobe --ignore-install nvsound ; sleep 1; /usr/bin/nvmix-reg -f /etc/nvmixrc -L >/dev/null 2>&1 || :
remove nvsound { /usr/bin/nvmix-reg -f /etc/nvmixrc -S >/dev/null 2>&1 || : ; }; /sbin/modprobe -r --ignore-remove nvsound

 For both 2.4 and 2.6 kernels, you should also edit /etc/rc.d/init.d/halt, or /etc/init.d/halt.local on SuSE distributions:

if grep -q "\(nvsound\)" /proc/modules && [ -x /usr/bin/nvmix-reg ]; then
/usr/bin/nvmix-reg -f /etc/nvmixrc -S >/dev/null 2>&1 
fi  For *Red Hat Enterprise Linux 4* and *Fedora Core 3*, add the following line in /etc/rc.local:

/usr/bin/nvmix-reg -f /etc/nvmixrc -L >/dev/null 2>&1 

```

But, because I'm a linux/Ubuntu n00b, I don't exactly know where to put the lines... 

I created a file in /etc/modutils which has these lines:
```

[/font][font=Verdana]install nvsound /sbin/modprobe --ignore-install nvsound ; sleep 1; /usr/bin/nvmix-reg -f /etc/nvmixrc -L >/dev/null 2>&1 || :
remove nvsound { /usr/bin/nvmix-reg -f /etc/nvmixrc -S >/dev/null 2>&1 || : ; }; /sbin/modprobe -r --ignore-remove nvsound

```

Then: update-modules
When looking at modules.conf (created/updated by update-modules) I can see the lines from the file are in here.

Unfortunately this has 0% effect -> nvmixer is not 'remembering' settings :(

Might there be an extra file which has to be edited, like in Redhat/Fedora and SuSE?
[/font]

---

### Post by Dracontopes on 2005-03-29
C'mon, there must be more people who use the nForce 2 soundcard and this driver... :cry:

---

### Post by MrGrumpy on 2005-03-29
Well there is but we all seem to ahve our own little problems and its getting annoying :( Mine is that i get no sound in games  :confused: 

Ali


BTW thanks for the hint on nvmixer i did not know that i could get that up :)

---

### Post by ploum on 2005-03-29
Dracontopes ; nobody use the nforce proprietary driver. It's really a piece of crap and the ALSA one is much more better (and free).

---

### Post by Dracontopes on 2005-03-29
[QUOTE=ploum]Dracontopes ; nobody use the nforce proprietary driver. It's really a piece of crap and the ALSA one is much more better (and free).[/QUOTE]
 Tat may be so, but that driver doens't support my 4.1 analog speakers

---

### Post by Redemption042 on 2005-12-13
Furthermore, the alsa driver doesn't support the soundstorm chipset nor does the alsa driver support the hw mixing the soundcard is capable of.

---

### Post by Dearhell on 2006-01-21
I have exactly the same problem, after reboot all settings are gone, so I must run nvmixer again each time in order to use my 4.1 speakers, and not only 2.1

---

### Post by CiberAmigo on 2006-01-28
Same problem here. Allthough I manage to load nvsound, I still have problem unloading other snd modules that is interfere with nvsound

Cencerly CiberAmigo

---

### Post by CiberAmigo on 2006-01-28
basically I did what the releasenote told me (/usr/share/doc/nforce/ReleaseNotes.html)

Open the modules file:
```

sudo gedit /etc/modules
```

Insert the following text beneath every thing:
```

install nvsound /sbin/modprobe --ignore-install nvsound ; sleep 1; /usr/bin/nvmix-reg -f /etc/nvmixrc -L >/dev/null 2>&1 || :
 remove nvsound { /usr/bin/nvmix-reg -f /etc/nvmixrc -S >/dev/null 2>&1 || : ; }; /sbin/modprobe -r --ignore-remove nvsound
```

Open /etc/init.d/halt:
```

sudo gedit /etc/init.d/halt
```

Insert the following text after the last "fi" and before the line thats starts with "halt":
```

# Recommended by Nvidia inserted by user:jan
if grep -q "\(nvsound\)" /proc/modules && [ -x /usr/bin/nvmix-reg ]; then
 /usr/bin/nvmix-reg -f /etc/nvmixrc -S >/dev/null 2>&1 
 fi
```

Mine halt-file look like this:
```

 PATH=/sbin:/bin:/usr/sbin:/usr/bin

# Get the default from /etc/default/halt.
[ -f /etc/default/halt ] && . /etc/default/halt

if [ "$INIT_HALT" = "" ]
then
	case "$HALT" in
		[Pp]*)
			INIT_HALT=POWEROFF
			;;
		[Hh]*)
			INIT_HALT=HALT
			;;
		*)
			INIT_HALT=POWEROFF
			;;
	esac
fi

# See if we need to cut the power.
if [ "$INIT_HALT" = "POWEROFF" ] && [ -x /etc/init.d/ups-monitor ]
then
	/etc/init.d/ups-monitor poweroff
fi

# Don't shut down drives if we're using RAID.
hddown="-h"
if grep -qs '^md.*active' /proc/mdstat
then
	hddown=""
fi

# If INIT_HALT=HALT don't poweroff.
poweroff="-p"
if [ "$INIT_HALT" = "HALT" ]
then
	poweroff=""
fi

# Recommended by Nvidia inserted by user:jan
if grep -q "\(nvsound\)" /proc/modules && [ -x /usr/bin/nvmix-reg ]; then
 /usr/bin/nvmix-reg -f /etc/nvmixrc -S >/dev/null 2>&1 
 fi

halt -d -f -i $poweroff $hddown

: exit 0
```

Remember to "blacklist all other snd modules in /etc/hotplug/blacklist:
```

sudo gedit /etc/hotplug/blacklist
```

Insert folliowing text into the buttom of the file:
```

# snd_intel8x0 replaced with nvsound
snd_intel8x0
```

Now restart Your machine.

I hope it will work on Your machine as it does on my machine. :D 

Cencerly 
CiberAmigo

---

### Post by double0seven on 2006-04-02
i followd you howto step by step, but it doesnt work. any ideas what could be wrong? when i reboot my machine it gives an error bout alsactl_state, it says that it cant find a soundcard, perhabs these two things belong together?

---

