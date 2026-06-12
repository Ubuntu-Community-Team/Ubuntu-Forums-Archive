---
title: "Why can't I stop swapping?!?!"
date: 2015-05-22
forum: Hardware
---

### Post by holysword on 2015-05-22
I'm in a slow machine with only 4GB memory, and I am clearly swapping all the time. htop reveals that the task eating the most memory is the webbrowser (chromium), with 12~18% of the memory, with the second place going to something with 3 or 4% memory usage. Am I mistaken or Ubuntu 14.04 LTS has tmpfs enabled by default?  If so, I'd assume that the memory is being shared with TMPFS, which would then easily fill 50% of the memory in one strike (just the cache of the browser could eat that fairly quickly). 

```
sacrispada@localhost ~ cat /etc/mtab/dev/sda6 / ext4 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
none /sys/fs/cgroup tmpfs rw 0 0
none /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
udev /dev devtmpfs rw,mode=0755 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
tmpfs /run tmpfs rw,noexec,nosuid,size=10%,mode=0755 0 0
none /run/lock tmpfs rw,noexec,nosuid,nodev,size=5242880 0 0
none /run/shm tmpfs rw,nosuid,nodev 0 0
none /run/user tmpfs rw,noexec,nosuid,nodev,size=104857600,mode=0755 0 0
none /sys/fs/pstore pstore rw 0 0
systemd /sys/fs/cgroup/systemd cgroup rw,noexec,nosuid,nodev,none,name=systemd 0 0

```

mtab seems to suggest that only 10% of my memory is reserved for that purpose, but it doesn't "feel" like so! Maybe I could disable TMPFS overall, to see if it changes? services --status-all doesn't seem to show anything tmpfs-related, but then again I'm not really a specialist in non-OpenRC builds.
```
 [ + ]  acpid
 [ - ]  anacron
 [ - ]  apparmor
 [ ? ]  apport
 [ + ]  avahi-daemon
 [ + ]  bluetooth
 [ - ]  brltty
 [ ? ]  console-setup
 [ + ]  cron
 [ ? ]  cryptdisks
 [ ? ]  cryptdisks-early
 [ + ]  cups
 [ + ]  cups-browsed
 [ - ]  dbus
 [ ? ]  dns-clean
 [ + ]  friendly-recovery
 [ - ]  grub-common
 [ ? ]  irqbalance
 [ + ]  kerneloops
 [ ? ]  killprocs
 [ ? ]  kmod
 [ ? ]  lightdm
 [ ? ]  networking
 [ + ]  ntp
 [ ? ]  ondemand
 [ ? ]  openafs-client
 [ ? ]  pppd-dns
 [ - ]  procps
 [ - ]  pulseaudio
 [ ? ]  rc.local
 [ + ]  resolvconf
 [ - ]  rsync
 [ + ]  rsyslog
 [ + ]  saned
 [ ? ]  sendsigs
 [ ? ]  speech-dispatcher
 [ - ]  sudo
 [ - ]  udev
 [ ? ]  umountfs
 [ ? ]  umountnfs.sh
 [ ? ]  umountroot
 [ - ]  unattended-upgrades
 [ - ]  urandom
 [ - ]  x11-common

```

Any suggestion?

---

### Post by kerry_s on 2015-05-22
install zram-config & reboot

it makes swap in ram

---

### Post by holysword on 2015-05-22
I guess I didn't explain myself properly. I have little RAM, so I want to use less RAM, not more.
I'd like to disable TMPFS exactly for that purpose, to have less RAM usage.

---

### Post by dino99 on 2015-05-22
yes 4 gb is enough and swapping should be only random and little.
maybe you open many tabs with chromium, which can be a reason. But you should also glance at the 'swappiness' settings, maybe you need to adjust them
[http://askubuntu.com/questions/103915/how-do-i-configure-swappiness](http://askubuntu.com/questions/103915/how-do-i-configure-swappiness)

---

### Post by holysword on 2015-05-22
I have no much choice concerning the amount of tabs I keep open... I basically have to keep several open. 18 right now. Hard to explain, but it is part of my work.
My complaint is not that the swap is being used, is that my memory is being OVERUSED. Chromium is taking 20% of the memory, but the remaining 80% could not possible be consumed by other processes which are taking pretty much nothing. If 60% of my memory would be in use I'd understand, but its ALWAYS at least 90%. This smells to me like tmpfs work. Swappiness or not swappiness, I would run out of memory anyway.

---

### Post by grahammechanical on 2015-05-22
I agree about Chromium being a memory hog and some websites use more memory than others. I have also noticed that in Ubuntu total memory also includes memory set aside in cache. As more applications are opened cache memory gets smaller. An OS will claim as much memory as is available. After all, that is what the memory is there for. 

Oh, by the way, zram does not convert swap into memory. It uses a form of memory compression to avoid swapping to disk. Although, as has already been stated, with 4GB RAM you should not need to swap.

[http://en.wikipedia.org/wiki/Zram](http://en.wikipedia.org/wiki/Zram)

Regards.

---

### Post by dino99 on 2015-05-22
18 tabs opened at once :p
i think you does not needs more explanations ;)
Look at the chromium settings, and try to find settings you can turn off, and/or add like adblock

---

### Post by holysword on 2015-05-22
Guys, I would REALLY like to thank you all for the suggestions, but that's not what I've been asking for.

I think we all agree that 4GB should be enough, and I should not be swapping ALL THE TIME. I'm not streaming videos or audio, I am just reading forums, documentations, reference guides of MPI, FORTRAN, dicionaries - plain text almost always, some few images. I do have adblock in draconian mode on. There is no justification for 4GB of memory being used constantly. My old laptop had 4GB memory and no TMPFS, and I've never had a problem with it. It did not have zram or anything like that. It was just a plain installation of Gentoo Linux.

I cannot comprehend how Ubuntu allows all of my memory to be consumed in such a mysterious way. "Change your habits" is not an answer. I can sum up 35% of memory use, with all the applications open, where are the other 65% being spent?!?! Its not about my habits, it is the system managing my resources in a way that doesn't fit my needs. I would guess that this is TMPFS's fault, if Ubuntu has TMPFS enabled by default (for those who don't know what TMPFS is, please Google it quickly, its quite simple, really). Can anyone comment on how to see if it is enabled and how to disable it in Ubuntu? If not, can someone suggest me a way to *****find out who is eating those 65% of my memory resources*****?

---

### Post by kerry_s on 2015-05-22
> **kerry_s said:**
> install zram-config & reboot

it makes swap in ram

my bag, i was on my ipod & cooking at the time, so i kind of just stopped mid sentence. ):P
anyways read the link " grahammechanical " provided, it will help make better use of your ram.

i use it on my netbook which only has 2gb, mine hasn't used actual swap yet since install.
chromium/chrome has had memory issues for some time now, there are bug reports on the issue you can google.
i myself have started using firefox more for when i need to use a lot of tabs or for media consumption, youtube addict. ;)

---

### Post by holysword on 2015-05-22
> **kerry_s said:**
> my bag, i was on my ipod & cooking at the time, so i kind of just stopped mid sentence. ):P
anyways read the link " grahammechanical " provided, it will help make better use of your ram.

i use it on my netbook which only has 2gb, mine hasn't used actual swap yet since install.
chromium/chrome has had memory issues for some time now, there are bug reports on the issue you can google.
i myself have started using firefox more for when i need to use a lot of tabs or for media consumption, youtube addict. ;)
Is zram going to help me figure out where the other 65% of my memory resources are being spent?

---

### Post by kerry_s on 2015-05-22
> **holysword said:**
> Is zram going to help me figure out where the other 65% of my memory resources are being spent?

it's more than likely cache, if nothing needs the ram & you have lots of ram available it will use it. did the same thing when i had a 4gb ram laptop, it's nothing to be worry about it's a os speed trick to make apps feel faster.

unless your getting the gray dim screen, which it does when busy, just go on about your business & let the os do it's job allocating available resources. 

what are you going to do with unused ram anyways ? such a waste just sitting there all empty.  ;)

---

### Post by v3.xx on 2015-05-22
Could we see the output of:
```
free -m
```

---

### Post by holysword on 2015-05-26
> **kerry_s said:**
> it's more than likely cache, if nothing needs the ram & you have lots of ram available it will use it. did the same thing when i had a 4gb ram laptop, it's nothing to be worry about it's a os speed trick to make apps feel faster.

unless your getting the gray dim screen, which it does when busy, just go on about your business & let the os do it's job allocating available resources. 

what are you going to do with unused ram anyways ? such a waste just sitting there all empty. ;)
It is not cache. It is not buffers. It is used memory. I use htop rather than top, and it clearly shows how much is allocated, how much is for cache and how much for buffers.
Also, I can't let the OS do "its job", because it is doing a bad job. Sometimes I have to wait 5s to wait the OS change the focus of an application (i.e. paginating things back and forth from the swap). Imagine coding like that.

> **v3.xx said:**
> Could we see the output of:
```
free -m
```
I will as soon as the memory fills in again.

---

### Post by kerry_s on 2015-05-26
are you leaving app's open for long periods of time ? 
memory usually doesn't get released till the app closes, at least that's how it works for me.
i know some people who just never close apps, cause they don't like waiting for startup. lol

if your coding & only have 4gb ram, you should have gone with a lighter system to make the most of resources. standard ubuntu unity is what 600mb->800mb just startup, just opening chrome is like 250mb, add in a few tabs, they tend to be 100mb->130mb depending on content. i'm sure you get what i mean.


i'm using ubuntu-mate, my startup is like 250mb, i'd have to open every app i have on my launcher + at least 20 tabs in chrome just to reach 1 gig of use, with no apps open it usually hangs around 300mb.

---

### Post by holysword on 2015-05-27
> **v3.xx said:**
> Could we see the output of:
```
free -m
```
Here you go:
```
[ holysword@localhost ] [~] $ free -m             total       used       free     shared    buffers     cached
Mem:          3832       3346        485        271         27        525
-/+ buffers/cache:       2793       1039
Swap:         3975       1002       2973
[ holysword@localhost ] [~] $ 
```


> **kerry_s said:**
> if your coding & only have 4gb ram, you should have gone with a lighter system to make the most of resources. 
I am actually using an unusual combo of E18 with plasma toolbars which goes to 240MiB~ memory use togheter, but thanks for the suggestion.


Still you are failing to see the problem. I am ***telling you***: Ctrl+C and CTRL+V the memory use from top, sum the thing up. It sum to 41%. Yet the memory use was 95% with half of my swap full. I am not asking how to use less resources, thank you very much. I am asking WHAT is using these extra unreported resources, how to find out, and how to disable it.

---

### Post by kerry_s on 2015-05-27
i understand.

if there is a app with a memory leak it's going to be hard to fine, they tend to not show on monitors.
basically it's a matter of trial, you just rule eack item out 1 at a time.
for example:
reboot the pc so nothings running but the desktop, note the ram level, don't open any apps, just let it set there. if the ram doesn't climb for no reason you know it's not the desktop enviroment.
next open 1 of your most used apps, again note ram level, if it don't climb, it's probably okay.
etc...

good luck to ya

---

### Post by v3.xx on 2015-05-27
> -/+ buffers/cache:  free = [COLOR=#ff0000]1039[/COLOR]
So you have a gig of ram available, but swap is kicking in.

Have you tried to set swappiness?  I run mine with a setting of zero.
[https://help.ubuntu.com/community/SwapFaq#What_is_swappiness_and_how_do_I_change_it.3F](https://help.ubuntu.com/community/SwapFaq#What_is_swappiness_and_how_do_I_change_it.3F)

You could ( as a experiment) turn swap off and run like that for a while.
[http://manpages.ubuntu.com/manpages/trusty/man8/swapon.8.html](http://manpages.ubuntu.com/manpages/trusty/man8/swapon.8.html)

Are there leftover running processes?  As pointed out, Chrome will do this.
Easy way to check is just use the 'System Monitor'.
> I am actually using an unusual combo of E18 with plasma toolbars
I am not a user of plasma and only have played with Enlightenment, but got to say that that sounds like a awesome pair :)

---

### Post by holysword on 2015-05-29
> **v3.xx said:**
> So you have a gig of ram available, but swap is kicking in.

Have you tried to set swappiness?  I run mine with a setting of zero.
[https://help.ubuntu.com/community/SwapFaq#What_is_swappiness_and_how_do_I_change_it.3F](https://help.ubuntu.com/community/SwapFaq#What_is_swappiness_and_how_do_I_change_it.3F)

You could ( as a experiment) turn swap off and run like that for a while.
[http://manpages.ubuntu.com/manpages/trusty/man8/swapon.8.html](http://manpages.ubuntu.com/manpages/trusty/man8/swapon.8.html)

Are there leftover running processes?  As pointed out, Chrome will do this.
Easy way to check is just use the 'System Monitor'.
It helped but still there is something consuming my memory when it shouldn't. I am getting close to simply uninstalling Ubuntu and using another distro. This is stressful. Does Ubuntu use TMPFS or not in the end?

> **v3.xx said:**
> I am not a user of plasma and only have played with Enlightenment, but got to say that that sounds like a awesome pair :)
Its hard to beat the convenience of KIO and fish protocol (which apparently is supported only by Konqueror and KIO for some reason...) when working on remote files. Once you see it, you can't live with gedit anymore. Or I cannot at least xP

---

### Post by v3.xx on 2015-05-29
> TMPFS, which would then easily fill 50% of the memory
My understanding is by default tmpfs (shm) is alocated 50% of system ram.

There is also a small possibility this could be graphic related.  What kind of graphics and driver are you running?

Are you going to try running with swap off?  Should be doable with 4G.

Have you tried looking through the system logs for errors?
> I am getting close to simply uninstalling Ubuntu and using another distro
Are you by chance thinking Bodhi?

---

### Post by holysword on 2015-06-01
> **v3.xx said:**
> My understanding is by default tmpfs (shm) is alocated 50% of system ram.

There is also a small possibility this could be graphic related.  What kind of graphics and driver are you running?

Are you going to try running with swap off?  Should be doable with 4G.

Have you tried looking through the system logs for errors?

Are you by chance thinking Bodhi?
I don't think the swap is the problem. The problem is that... there is... something... consuming my resources...
(Don't say "chromium", please, we have already been through all of that).

I am trying to blame the TMPFS since I started this topic, since it does take 50% by default to "speed up" and I know well that doesn't match very nicely when you're doing anything which is very memory hungry.

So the question is (again), if Ubuntu uses TMPFS by default, how to disable it?

---

### Post by Elfy on 2015-06-01
[https://wiki.archlinux.org/index.php/Tmpfs](https://wiki.archlinux.org/index.php/Tmpfs)

Have a look there.

---

### Post by kerry_s on 2015-06-01
just do "df -h" in terminal to see where tmpfs is being used.

here's mine so you have something to compare it to.

```

Filesystem      Size  Used Avail Use% Mounted on
udev            972M     0  972M   0% /dev
tmpfs           197M  5.4M  192M   3% /run
/dev/sda1       110G  4.7G  100G   5% /
tmpfs           983M   12M  971M   2% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           983M     0  983M   0% /sys/fs/cgroup
tmpfs           197M   48K  197M   1% /run/user/1000

```

---

### Post by holysword on 2015-06-01
> **Elfy said:**
> [https://wiki.archlinux.org/index.php/Tmpfs](https://wiki.archlinux.org/index.php/Tmpfs)

Have a look there.
I don't think Ubuntu uses systemd already ;)

---

### Post by holysword on 2015-06-01
> **kerry_s said:**
> just do "df -h" in terminal to see where tmpfs is being used.

here's mine so you have something to compare it to.

```

Filesystem      Size  Used Avail Use% Mounted on
udev            972M     0  972M   0% /dev
tmpfs           197M  5.4M  192M   3% /run
/dev/sda1       110G  4.7G  100G   5% /
tmpfs           983M   12M  971M   2% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           983M     0  983M   0% /sys/fs/cgroup
tmpfs           197M   48K  197M   1% /run/user/1000

```

I will when it gets filled again, I just rebooted.
What would be a "Filesystem: none" ? My /run/lock, shm, user and /syst/fs/cgroup are all mounted as "none", and only /run as TMPFS.

---

### Post by kerry_s on 2015-06-01
"none" means there's no physical disk partition.

---

### Post by Yellow Pasque on 2015-06-01
This whole thing about disabling tmpfs doesn't make any sense to me. Maybe you should just try removing stuff you don't need. Do you really need brltty? Do you print? (if not, get rid of cups) Do you scan? (if not, get rid of saned) Do you need speech-dispatcher? Etc. etc. etc.
Here's my Debian sid system with xfce, firefox, audacious running:

```
# df -h
Filesystem      Size  Used Avail Use% Mounted on
udev             10M     0   10M   0% /dev
tmpfs           779M  696K  779M   1% /run
/dev/sda1        52G   15G   35G  30% /
tmpfs           2.0G     0  2.0G   0% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           2.0G     0  2.0G   0% /sys/fs/cgroup
tmpfs           2.0G   92K  2.0G   1% /tmp
/dev/sda3       404G  283G  100G  74% /media/something
tmpfs           390M  4.0K  390M   1% /run/user/1000

# free -m
             total       used       free     shared    buffers     cached
Mem:          3893       2209       1684         13         94       1442
-/+ buffers/cache:        672       3221
Swap:         3814          0       3814
```

---

### Post by kerry_s on 2015-06-01
i don't think he should go that far.

it's got to be something he installed, not standard to the base os. 
i suspect chromium/chrome extensions, i tried chromium, it's screwy you can't even enable hardware accel.
so i grabbed chrome, with chrome the hardware accel fix works fine. but it is gobbling up some memory still. i can see in the task manager the extensions are using the most & i only have 2, ublock & flash control.

---

### Post by Elfy on 2015-06-03
> **holysword said:**
> I don't think Ubuntu uses systemd already ;)

oops - sorry, been using the unreleased version of *buntu for so long I forget others might be a version or 3 behind :D

---

### Post by holysword on 2015-06-17
> **kerry_s said:**
> it's got to be something he installed, not standard to the base os. 
i suspect chromium/chrome extensions, i tried chromium, it's screwy you can't even enable hardware accel.
so i grabbed chrome, with chrome the hardware accel fix works fine. but it is gobbling up some memory still. i can see in the task manager the extensions are using the most & i only have 2, ublock & flash control.

Okay, I owned someone the output of "free" once my computer starts lagging, I will still be owning that.
Problem is, I switched to Firefox to see if I could blame chrome as you guys are saying.

It turns out that no. Firefox seems more stable at first, but then when it crashes, it crashes harder. Chromium normally gives trouble with several pages open, but Firefox screws up with just some few, as long as one of them is "heavy" (e.g. if Google Drive or GMail are open, I can only have max 5 tabs, even if the other tabs are just plain text). This is very random though, sometimes it runs okay for a longer time. But when fills up the memory, I cannot even use a terminal. Trying to change to TTY may take about 5min to give me access to a laggy command line. I just get tired and do a hard reboot instead. That's not healthy.

I'm not sure if you guys can keep on trying to blame the browser (I bear no love for chrome or firefox, but I don't think its their fault). I will uninstall altogheter the flash plugin (even though chrome has its own and firefox had it "always ask" to enable) and see if anything changes, but I am unconvinced that the problem is the software.

---

### Post by holysword on 2015-12-17
Many years have gone.

I still haven't figured out how to disable TMPFS. There are 2347895023498256093487523 explanations on how to do that with systemd  but I can't find any for upstart.

My computer keeps on freezing and swapping all the time. I have tried using Firefox or Chromium.

So tell me guys, should I just give up Ubuntu, is that what will solve my problem?

---

### Post by oldfred on 2015-12-17
How much swap use does free show?
```
fred@trusy-ar:~$ free
             total       used       free     shared    buffers     cached
Mem:       8118288    1335480    6782808       9136      78784     527308
-/+ buffers/cache:     729388    7388900
Swap:      1952764          0    1952764
```

But RAM use is normal. Since most users reuse applications regularly, RAM is cached with what you ran. Only when RAM is full and you load a newer app, then some is released for that app.

       Linux ate my RAM! -  memory use cache
[http://www.linuxatemyram.com/](http://www.linuxatemyram.com/)

---

