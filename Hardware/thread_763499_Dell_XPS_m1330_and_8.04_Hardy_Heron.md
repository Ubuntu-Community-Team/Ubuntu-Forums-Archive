---
title: "Dell XPS m1330 and 8.04 Hardy Heron"
date: 2008-04-23
forum: Hardware
---

### Post by ethanay on 2008-04-23
UPDATE: Ok, as I promised (a while ago) I am posting my install/setup notes...ask if they don't make sense and I will try to explain (they make sense to me!)
------------------------------------------------
Ubuntu 8.04 Hardy Heron
install and setup notes

Install process:
Hardy does an excellent job of detecting hardware (at least on this laptop). The only big option here is partitioning, and I will pass on a recent recommendation and change that has worked well for me:  Create a / (root) partition as /dev/sda1.  You can safely make it any size from about 7gb - 12+gb (imo more than that seems excessive).  

The size depends on how many programs you will install and how much tmp file space you need:  If you install TONS of programs and need a lot of tmpfile space, then spring for the larger size.  I have (what I consider) a lot of extras installed right now, and am using about 4.9gb.

Copy /home/ethan to new setup; exclude unnecessary .hidden_folders
	unnecessary with install to / (root) partition only

--------------------
Add medibuntu repository (restricted extras)
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/medibuntu.list
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
--------------------
enable Dell Hardy respositories: [http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/Update_Dell_PPA_Entry](http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/Update_Dell_PPA_Entry)
	/etc/apt/sources.list
deb [http://ppa.launchpad.net/dell-team/ubuntu](http://ppa.launchpad.net/dell-team/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/dell-team/ubuntu](http://ppa.launchpad.net/dell-team/ubuntu) hardy main
----------------------------------------
enable backports, restricted repositories and updates
	install linux-backports-modules-X-generic, linux ubuntu modules (Dell)

bugs:	hard drive click after suspend?
	uvcvideo error
	intel wireless
see ugly_fix (posted below)

change keyboard shortcuts
	system > preferences > keyboard shortcuts
		media player: shift ctrl m
		calculator: shift ctrl c
		e-mail: shift ctrl e
		web browser: shift ctrl i
		search: shift ctrl s
		panel menu: shift ctrl super (windows key)
		run terminal: <super>t (edit manually in gconf-editor > apps > metacity)
		zoom in/out: ctrl alt +/-
		expo key:  says "ctrl alt"e but is really <super>e
		toggle maximization state:  shift alt b
		minimize: shift alt d
		move: shift alt m
		resize: shift alt r
		toggle all workspaces: shift alt a
		max vertically: shift alt v
		max horizontal: shift alt h
		hide all and focus desktop: ctrl alt h	
		

install backup scripts to /usr/local/bin
	backup_incremental /home/ethan /media/disk
A cousin gave me a set of simple backup scripts that utilize the power of rsync and hardlinks to make incremental backups to the location of your choice.  They can be run by cron, but I run it manually with a simple wrapper script, so all I type in the terminal is "backup."
-----------------
Uninstall unnecessary software
Clean/disable unnecessary boot services, session, modules
	I don't use accessibility, apmd, bluetooth, evolution, etc and don't need them running.
------------------
Install complete generic kernel:  restricted and backports
	I don't recommend installing the realtime kernel in addition, because 1) it requires specific performance tuning that conflicts with power-management and interface interactivity (once setup correctly).  It also broke hibernate for me while using the generic kernel, even after uninstalling.  If you need realtime performance, dual boot.  I recommend 64studio.

More Packages
firmware-addon-dell, firmware-tools > these let you update firmware, bios, etc
sensors-applet > enable acpi cputemp monitoring in the panel
hddtemp (no autoload), sysfsutils, sysinfo, powertop, FATsort [for pmp], checkinstall

lilypond, jedit, lilypondtool
	[http://lilypondtool.organum.hu/](http://lilypondtool.organum.hu/)
Musescore+fluid-soundfont-gm
	[http://www.pianosounds.com/freesoundfont.htm](http://www.pianosounds.com/freesoundfont.htm)
	make sure it uses hw:0 and not "default"

Wine, GNU Solfege, Gnome Office, Zim Desktop Wiki, cGmail, Stellarium, MusicBrainz Picard, Grsync, Gwget, APTonCD, Firestarter, Deluge, Audacity, Ubuntu Restricted Extras, GNUSound, Advanced Desktop Effects Settings (ccsm), Sound Converter, OpenOffice Suite, Mozilla Thunderbird, GNUCash, Gnome-do, xpad
	start GNU Solfege with the --no-sound flag, setup sound, exit, start normally

---------------------------
add AWN repository
[http://ubuntuforums.org/showthread.php?t=762363](http://ubuntuforums.org/showthread.php?t=762363)
echo 'deb [http://ppa.launchpad.net/reacocard-awn/ubuntu](http://ppa.launchpad.net/reacocard-awn/ubuntu) hardy main'  |  sudo tee -a /etc/apt/sources.list
echo 'deb-src [http://ppa.launchpad.net/reacocard-awn/ubuntu](http://ppa.launchpad.net/reacocard-awn/ubuntu) hardy main'  |  sudo tee -a /etc/apt/sources.list

Configure Avant Window Navigator
	ubuntu theme -- [http://thelinuxmovement.blogspot.com/2007/09/ubuntu-human-theme-for-awn.html](http://thelinuxmovement.blogspot.com/2007/09/ubuntu-human-theme-for-awn.html)
	rhythmbox plugin -- [http://wiki.awn-project.org/Plugins:Rhythmbox](http://wiki.awn-project.org/Plugins:Rhythmbox)
		unzip to /home/username/.gnome2/rhythmbox/plugins (2 files + 2 folders)
		enable within rhythmbox plugins

install gnome-do gnome-do-plugin-rhythmbox
	add gnome-do -q to startup sessions
	gconf-editor > apps > gnome-do shortcut: <super>d
[https://wiki.ubuntu.com/GnomeDo/Plugins](https://wiki.ubuntu.com/GnomeDo/Plugins)
	configure indexing locations and depth:  /home/ethan/.config/gnome-do/FileItemSource.config
/home: 1
/home/ethan: 3
/home/ethan/Desktop: 1
/home/ethan/Documents: -1 (infinite)
/usr/bin: 1
	install tracker-utils and add tracker search plugin

configure deluge
	automatic blocklist: [http://bluetack.gotalkaboutit.com/bluetack/level1.zip](http://bluetack.gotalkaboutit.com/bluetack/level1.zip)

Configure desktop appearance:
	top bar (from left to right) 
		launchers: xpad, gedit, gnome-do, file search
		applets: keyboard layout switcher, workspace switcher, trash, cpu temp monitor, system monitor (cpu, mem, net, hdd; 2 sec frequency), weather, volume control, sys tray, clock

terminal
	transparency, dark color schema for contrast (white on black)

gconf-editor
Power management settings
	actions -- hibernate and suspend
	dim screen = 12 [lowest setting]
	no lock screen on suspend/hibernate
metacity global key bindings
	<super>t launch terminal
nautilus
	check desktop icons visible

add startup items > system > preferences > sessions
Gnome-do
Avant-window-navigator

Set preferred applications (preferences): Thunderbird, Rhythmbox

install wineapps
	finale notepad (see e-memory)
	encore (see e-memory)
configure wine: windows xp, alsa sound driver
-------------------------------
disable apmd in system > administration > services -- suspend and hibernate OK!
----------------------
Keep powernowd [default is ondemand] OR...
uninstall powernowd
	I prefer to uninstall and use sysfsutils to automatically load cpufreq_ondemand.  If you don't use them, the other cpufreq options are

If uninstalling, use only ondemand/native powersave governor default:
unload cpufreq_conservative, cpufreq_powersave, cpufreq_userspace
	blacklist if necessary: add blacklist [module name] to /etc/modprobe.d/blacklist

install sysfsutils
	add to /etc/sysfs.conf
		devices/system/cpu/cpu0/cpufreq/scaling_governor = ondemand
check with cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
set on the fly with cpufreq-selector -g ondemand or performance
if ondemand is not enabled at startup, load
add to /etc/modules *if necessary
	acpi_cpufreq
	cpufreq_ondemand
	cpufreq_stats
	freq_table*
--------------------
for sysctl.conf if not default
min_power < /sys/class/scsi_host/host0/link_power_management_policy

change concurrency = none to "shell" in /etc/init.d/rc
---------------------------
to run 16-bit wine apps
	sudo sysctl -w vm.mmap_min_addr=0

to make permanent: edit /etc/sysctl.conf
and change the line that reads:
	vm.mmap_min_addr = 65536
		to
	vm.mmap_min_addr = 0
--------------------------
disable splash screens for debug/something interesting and informative to look at
/boot/grub/menu.lst -- remove "quiet" and "splash"
	## additional options to use with the default boot option, but not with the
	## alternatives
	## e.g. defoptions=vga=791 resume=/dev/hda5
	# defoptions=quiet splash
execute: sudo update-grub
--------------------
laptop automatic power management
[http://ubuntuforums.org/showthread.php?t=729644](http://ubuntuforums.org/showthread.php?t=729644)

[http://www.lesswatts.org/tips/](http://www.lesswatts.org/tips/)

/usr/lib/pm-utils/power.d/laptop-tools
	change dirty_writeback_centisecs to 1500 (was 30) and disk_idle_secs to 5 (was 2)
------------------------------
performance tuning
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)
	add vm.swappiness = 10 to /etc/sysctl.conf to reduce kernel tendency to use swap
this is trivial and probably unnecessary (i don't do it) -- Linux already does a good job managing swap (sooo much better than windows!)
----------------
to change root password (if necessary):
sudo passwd root
----------
If changing partitions after install:
	update /etc/fstab
	update /etc/initramfs-tools/conf.d/resume
run update-initramfs -u
-----------------------
UGLY_FIX
--------------------
persistent safe hdparm setting (254)
[https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695/comments/273](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695/comments/273)
copy 99-hdparm-fix.sh to /etc/pm/*.d/99-hdparm-fix.sh
see [http://ubuntuforums.org/showthread.php?t=772159](http://ubuntuforums.org/showthread.php?t=772159)
-------------------
uvcvideo on sleep
[https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.24/+bug/147757/comments/15](https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.24/+bug/147757/comments/15)
add "uvcvideo" to SUSPEND_MODULES in /usr/lib/pm-utils/defaults
--------------------
iwl3945 scanning issues
[http://www.intellinuxwireless.org/bugzilla/show_bug.cgi?id=1579#c15](http://www.intellinuxwireless.org/bugzilla/show_bug.cgi?id=1579#c15)
create /etc/modprobe.d/iwl3945 and add
 alias wlan0 iwl3945
 options iwl3945 disable_hw_scan=1
--------------------------
BEGIN OLD POST
------------------------------
> Hello all,

I'd like this to be a thread for any XPS M1330/1530 owners to discuss 8.04 Hardy Heron on their systems.  I'll kick things off :)

Intel Centrino Core2 Duo 1.5ghz
2 gb ram
DVD +/- RW
Intel integrated (X3100?) video
Intel 3945abg wireless networking

External hard drive for /home backup and file archiving

I was new to Ubuntu from Windows, and 7.10 Gutsy was my first installation, ditching Vista.  I haven't decided whether/when I will upgrade, because (thanks to the help of several other people) my 7.10 installation is finally very stable -- so much so that I'm beginning to take it for granted even though the first couple of months were shaky.  However, there are three big reasons for me to upgrade:
1) take full advantage of the Long Term Support (LTS)
2) potential increased hardware compatibility and battery life
3) a chance to finally undo, once and for all, the infamous [Dell Media "self-destruct" Direct button]("http://ubuntuforums.org/showthread.php?t=606345&page=2")

in #2 above, I that the following are fixed by default
a) get rid of the [excessive hard-drive wear and tear bug]("http://ubuntuforums.org/showpost.php?p=3675960")
b) suspend and hibernate work reliably out of the box [note: I said "reliably", not "completely bug-free" :) ]
c) the internal microphone finally works
d) less 3945 wireless woes (iwl3945 has been VERY buggy, so I'm still using ipw3945, which locks occasionally)

Here are a lot of the references I used to get 7.10 working OK -- hopefully they won't be necessary for 8.04!
[http://blog.higherthings.org/borghardt/article/3077.html](http://blog.higherthings.org/borghardt/article/3077.html)
[http://www.nervous.it/2007/11/linux-dell-xps-m1330/](http://www.nervous.it/2007/11/linux-dell-xps-m1330/)
[https://wiki.ubuntu.com/InstallingUbuntuOnADellXPSM1330](https://wiki.ubuntu.com/InstallingUbuntuOnADellXPSM1330)
[http://www.wains.be/index.php/2008/01/21/ubuntu-on-dell-xps-m1330/](http://www.wains.be/index.php/2008/01/21/ubuntu-on-dell-xps-m1330/)
[http://www.atlas95.com/blog/tag/xps-m1330/](http://www.atlas95.com/blog/tag/xps-m1330/)
[http://ubuntuforums.org/showthread.php?t=622378](http://ubuntuforums.org/showthread.php?t=622378)

cheers,
ethan

---

### Post by jespdj on 2008-04-23
I am already running 64-bit Ubuntu 8.04 RC on my M1530 and it works great. No big issues.

[http://jesperdj.pbwiki.com/Ubuntu-on-the-Dell-XPS-M1530](http://jesperdj.pbwiki.com/Ubuntu-on-the-Dell-XPS-M1530)

By the way, there is a [Dell Ubuntu Support](http://ubuntuforums.org/forumdisplay.php?f=342) forum here on ubuntuforums.org, your poll would have fit better there.

The Dell Media Direct button doesn't destruct anything on my M1530. When I press it to start the computer, it displays the Media Direct boot screen with GRUB overlaid on it in an ugly way, and it just proceeds to boot Ubuntu. Partitions or the MBR isn't destroyed.

> a) get rid of the excessive hard-drive wear and tear bug
Not fixed in 8.04, but it isn't an Ubuntu- or Linux-specific problem anyway. Just apply the "ugly fix" described in that post.

> b) suspend and hibernate work reliably out of the box [note: I said "reliably", not "completely bug-free"  ]
c) the internal microphone finally works
d) less 3945 wireless woes (iwl3945 has been VERY buggy, so I'm still using ipw3945, which locks occasionally)
Suspend and hibernate work normally and without any problems.
The internal microphone works, thanks to a new version of ALSA.
My M1530 has the 4965 and doesn't have any problems with connecting.

The only thing that I haven't yet working is the fingerprint reader.

---

### Post by atlas95 on 2008-04-23
All is working immediately, don't worry. It is the best computer I have never had with linux.

---

### Post by jespdj on 2008-04-23
I now also have the fingerprint reader working - I just forgot to install libpam-thinkfinger.

---

### Post by barbarian on 2008-04-23
*Not planning on it* because I'll plan to make fresh install:)

---

### Post by Kernel Sanders on 2008-04-23
I've had nothing but problems :(

My 3 issues are:

1) The wireless appears to work fine, but won't connect to ANY network.

2) I have the dedicated NVIDIA GeForce 128mb graphics card, and although Hardy says it's using the only compatible driver (the non-free one), in the admin menu it's ticked as enabled, but the next column shows a red light and "not enabled". 

3) I assume because of the above, this is why when I select the best desktop effects, it returns a "cannot enable" or similar message.

Gutted :(

---

### Post by thebigham on 2008-04-23
sigh..i got the m1330 and i updated, and tons of problems.

1. I can't even shut down without pressing the power button.

2. Suspend and hibernate never works.

3. The sound is really low even when its on max volume.

4. I can't even connect to the internet most of the time. When it's finally connected, i get 5mb and below out of a 10mb connect and the connection is very unstable, disconnects constantly. Three other computers with in my house with wireless connection works perfectly fine.Nightmares :(

---

### Post by ethanay on 2008-04-24
hey thebigham,

i'm curious:

1) what hardware do you have?
2) did you do a clean install, or did you do the upgrade?
3) are you using the 32-bit or 64-bit version?

As i understand it, the upgrade doesn't always work and can break several things.  if/when i do upgrade, i am planning on doing a clean install:

1) make a redundant backup of my /home folder
2) reboot and check and see if the "media direct" self-destruct thing is still there
3) zero the hard drive anyway just to be sure
4) do a fresh install of 8.04 from the live cd with separate /boot (12gb), /swap (4gb) and /home (rest) partitions.


ps i plan on using the 32-bit as i understand overall there are less software/hardware complications, less online support, and not much performance difference except for certain specific operations

---

### Post by ethanay on 2008-04-24
Hi Kernel Sanders,

What wireless card do you have?  which driver set are you using? (if intel: ipw, iwl, or ndiswrapper?) Did you try connecting to any networks manually via commandline?  were they a,b, or g networks?

ethan

---

### Post by Daelyn on 2008-04-24
> **Kernel Sanders said:**
> I've had nothing but problems :(

1) The wireless appears to work fine, but won't connect to ANY network.



Have a look at this thread if you use the iwlwifi driver :P
[http://ubuntuforums.org/showthread.php?t=764886](http://ubuntuforums.org/showthread.php?t=764886)

---

### Post by thebigham on 2008-04-24
> **thebigham said:**
> sigh..i got the m1330 and i updated, and tons of problems.

1. I can't even shut down without pressing the power button.

2. Suspend and hibernate never works.

3. The sound is really low even when its on max volume.

4. I can't even connect to the internet most of the time. When it's finally connected, i get 5mb and below out of a 10mb connect and the connection is very unstable, disconnects constantly. Three other computers with in my house with wireless connection works perfectly fine.Nightmares :(

Most of my problems are fixed after a fresh install of the final version of 8.04 :)

---

### Post by kklepack on 2008-04-25
I'm running 8.04 with wubi on 1530 and the only problem, I found is low sound from speakers on max volume. I'm new any advice?

---

### Post by ethanay on 2008-04-26
hey kklepack,

have you tried looking at the sound mixer settings?  it's probably different in hardy than in gutsy, so i'm not sure how much of a help i can be.  i know that hardy features pulseaudio, which allows you to set independent volume levels for each running program.  you might check that.

otherwise, in gutsy, you can type alsamixer in a terminal and check those volumes.  also, go to volume control (menu: system > preferences or menu: applications, sound & video).  you can also get it by right-clicking on the speaker icon on the gnome panel.  if you can't see it anywhere, you'll need to add it to the system tray (right click > add to panel) and/or display it in the menus: right click on the applications menu, click edit menus, and place a check bar by it.

it might all be different with pulse audio, though...but the basic principal is check the mixer volume levels and see if something is turned down (pcm, main, front speakers, etc).

---

### Post by ethanay on 2008-04-26
I just upgraded the bios from A07 to A09, and tried the 8.04 32-bit live cd.   I was very impressed with how polished Hardy seems to be -- absolutely no fuss with anything.

I chose the 32-bit because except for some media transcoding/encoding, pretty much everything I do is office-related+listening to music.  And I have only 2 gb of memory, so I don't really see any benefit to the 64-bit version for myself.

The only thing that seemed to go wrong was when I for some stupid reason (habit?) chose "suspend" rather than "restart" from the shutdown menu and it hung the system.  Duh.

The bios update seemed to improve battery life and I've read elsewhere it might have resolved the load/unload cycles issue.  We'll see.

If suspend/hibernate work reliably after install, then I'll be one very happy 8.04 LTS user.

I will post back after the install with the results.

ethan

---

### Post by GeoMX on 2008-04-28
I have updated using the network update option, I have two problems with Hardy:

- no sound in aMsn when other applications are using sound (rhytmbox)
- brightness control shortcut (Fn + UP/DOWN) does not work correctly, when you press once you move UP/DOWN several brightness levels, not just one.

Hope someone knows how to fix these, thanks in advance for your help.

---

### Post by ethanay on 2008-04-28
I haven't had a single issue with sound yet.

I will be posting several bugs/frustrations soon.  One of the minor ones is the brightness control shortcuts.  Are you running bios v.A09, by chance?  I've heard it's linked to that.

The one that's killing me is the hard disk head parking/load cycle count issue.  NONE of the fixes I've tried (and I've tried ALL of 'em...) work.  After resume from suspend it's always back to several clicks a minute until I manually execute a script or via CLI.

---

### Post by MrFreshy on 2008-04-28
so far so good for me...

the only issue that i am having, is that my volume is low even when maxed.
i have checked the alsamixer, and it shows max volume. i crank it up on youtube, etc, and can still barely hear anything if there is any other noise around me.

---

### Post by mailforbiz on 2008-04-28
I still have issues with 7.10 and am wondering if I should upgrade to 8.04 or should try to fix the issues in 7.10.

My major issues currently are :

Internal/External mic: tried out all the links that the original poster mentioned but no-can-do. Installing the backports did no good. I don't have EITHER INTERNAL OR EXTERNAL MIC working. Pretty frustrating as I want to use Ubuntu exclusively but need to use skype for work. Sound worked out of the box

Hibernate:
It seems to go into hibernation but on wakeup, the screen never wakes up though i hear the HD and the fans. I end up turning power off using the power button and rebooting
Suspend: Same as above

Dell travel mouse: Bluetooth works, front/back buttons and side scroll not working

Webcam: low priority but would be great if worked

Any pointers/suggestions? Thanks in advance!!

---

### Post by ethanay on 2008-04-29
Hi mailforbiz,

i never got the internal mic working in 7.10.  Dell might have a fix on its [wiki page]("http://linux.dell.com/wiki/index.php/Ubuntu_7.10").

For resume, try [this page]("http://blog.higherthings.org/borghardt/article/3077.html")

FWIW, resume from hibernate and suspend have been more reliable _by default_ in 8.04, but there are still plenty of other bugs (wireless, hard drive power management, cpu cores, etc) to contend with related to suspend/hibernate and resume.

---

### Post by DreamerMd on 2008-04-30
> **Kernel Sanders said:**
> I've had nothing but problems :(

Hi I also have a 1330 lap.. really happy how everything is going now

My 3 issues are:

1) The wireless appears to work fine, but won't connect to ANY network.

go to manual, chose whatever type of signal you have. I choosed WEP, got the key password and choosed DHCP... it works perfect now....



2) I have the dedicated NVIDIA GeForce 128mb graphics card, and although Hardy says it's using the only compatible driver (the non-free one), in the admin menu it's ticked as enabled, but the next column shows a red light and "not enabled". 


Go to administration...synaptic.... and look for nvidia drivers.. choose "new" and download it... not it works and can have allnice effects :)

3) I assume because of the above, this is why when I select the best desktop effects, it returns a "cannot enable" or similar message.

Gutted :(

good luck and let me know how it goes

---

### Post by GeoMX on 2008-05-01
Had not noticed the new policykit stuff until today (don't know why), and a new problem has arised.
I switch the wireless on, but the indicator led does not turn on, and I can't connect to any network, network-admin can't find any available connection, when shutting down I can see several error messages refering to network-manager :confused:.

[SOLVED]
Two things:
- [http://ubuntuforums.org/showthread.php?t=764886](http://ubuntuforums.org/showthread.php?t=764886)
- They changed the network id at work, I didn't know and didn't notice since the network-admin is not showing available networks (in properties, it used to show the id and the quality of the network, it is not doing so right now).

---

### Post by zorba_the_greek on 2008-05-06
[One problem only...]("http://ubuntuforums.org/showthread.php?t=783440"):(

---

### Post by ethanay on 2008-05-06
enable backports repository to upgrade the wireless drivers.

i have the same issues with iwl3945/network manager.  in order to get everything working after resume or bootup, i usually have to disable networking, re-enable, and force a scan via cli:

```
sudo iwlist wlan0 scan
```

then it will see available connections and do the rest, but won't do any more scanning after that.  also, sometimes when i resume from suspend/hibernate, network manager sees wireless as a wired connection, and will even connect fully as such (showing two computers rather than the wireless strength bars).  disabling/re-enabling networking is a temporary fix.

---

### Post by ethanay on 2008-05-16
update:  all my wireless woes have been fixed by disabling hardware scanning according to [comment 15]("http://www.intellinuxwireless.org/bugzilla/show_bug.cgi?id=1579#c15") of bug 1579 at [www.intellinuxwireless.org](www.intellinuxwireless.org)

create and edit by:
```
sudo gedit /etc/modprobe.d/iwl3945
```
add the following lines:
```
alias wlan0 iwl3945
options iwl3945 disable_hw_scan=1

```

save and close.  restart or modprobe or whatever (a hibernate/resume simply worked for me).

now network manager has full control over iwl3945, and will automatically scan and connect.  disable/enable networking is automatic scan and reconnect.  the hardware kill switch used to lock up the driver, forcing a modprobe.  now it works perfectly fine, and rescans and connects after the card is enabled again via the killswitch.
---------------
should this be a bug to report in ubuntu, i.e., a wrong default configuration parameter?  it seems that iwl3945 simply needs to be configured with hardware scanning disabled in order to play nice with network manager...?

---

### Post by panholt on 2008-07-05
> **GeoMX said:**
> I have updated using the network update option, I have two problems with Hardy:

- no sound in aMsn when other applications are using sound (rhytmbox)
- brightness control shortcut (Fn + UP/DOWN) does not work correctly, when you press once you move UP/DOWN several brightness levels, not just one.

Hope someone knows how to fix these, thanks in advance for your help.

The brightness issue can be fixed by adding 'blacklist video' to the end of /etc/modprobe.d/blacklist and then a reboot.

---

### Post by ethanay on 2008-07-16
blacklisting the video module causes video problems (disappearing graphics and graphical corruption) for me, so i'm waiting for a real fix

---

### Post by stash1071 on 2008-07-18
My laptop speakers didn't put out much volume until I went into volume settings and put both front speaker sliders up to max.

---

### Post by jbor7755 on 2008-08-26
Yeah, thats what I had to do first.  But the sound level doesn't scale properly with the volume control either.  You have to have well in excess of 60% to have decent volume, whilst in windows it scales much better and even 10% can be heard.

---

### Post by ethanay on 2008-09-22
have you tried with headphones?  i've found that volume scales with headphones well, but through the main speakers it has the scaling problem.  I don't much care about this since for the most part, when i listen seriously it is through headphones or an exterior sound system.  when i'm using the built-ins, i don't expect much :P

speaking of which, have people gotten the 2nd headphone jack to work?  i can't get any system sound out of it yet, but i hear the background "static" noise when i plug in, so i think it should work if i enable the right setting or something...

---

### Post by crazyniggy on 2008-09-30
hi can someone help me, i cont get in to the bios with my Bluetooth Keyboard, 
or setting up windows, im trying to setup windows because ive got a virus,,
and im doing all the right things to got in to the bios?
thanks

my lapto is a dell xps m2010

---

### Post by ethanay on 2008-10-02
hi crazy,

welcome to ubuntu forums.

if you have a new issue, especially with a different computer, you should post a new topic on these forums.  that way, more people will see it and you will be more likely to get a helpful response.

good luck!

---

### Post by peter_t on 2008-12-01
After upgrading my m1330n, I am unable to get the dvd writer to mount.  When I run lshw, I see the the entry below so I assume that the hardware is recognized:

/0/100/1f.1/0.0.0      /dev/cdrom  disk        DVD+-RW UJ-857G

Is the problem related to my fstab? Could someone post the proper entries for the m1330?  Thanks in advance.

---

### Post by ethanay on 2008-12-05
here's what my fstab has for my dvd writer:
```
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

hope that helps

---

### Post by peter_t on 2008-12-06
I still see the following error in my system log after making those changes to my fstab:

Dec  6 19:18:01 dell-desktop kernel: [35901.476000] sr0: CDROM (ioctl) error, command: Test Unit Ready 00 00 00 00 00 00
Dec  6 19:18:01 dell-desktop kernel: [35901.476000] sr: Sense Key : Hardware Error [current] 
Dec  6 19:18:01 dell-desktop kernel: [35901.476000] sr: Add. Sense: Tracking servo failure

Any additional suggestions? Thanks.

---

