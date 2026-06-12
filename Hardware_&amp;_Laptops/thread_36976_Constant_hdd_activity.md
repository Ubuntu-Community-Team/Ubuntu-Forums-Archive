---
title: "Constant hdd activity ?"
date: 2005-05-25
forum: Hardware &amp; Laptops
---

### Post by karl_kashofer on 2005-05-25
Hi !

Running Ubuntu 5.04 on a Powerbook Pismo with a 4 Gig Toshiba harddrive.

Problem is: The harddisk is constantly active. It seems very similar to the problem in this post: [http://www.ubuntuforums.org/showthread.php?t=5617](http://www.ubuntuforums.org/showthread.php?t=5617)

Every three or so seconds I get a scratching sound from the hdd.
I have had disks die on me before, so I know the sound a bad hdd makes, this one is different though. I have also replaced the disk with another 4Gb disk, and it does the same thing.
I tried to put the hd to sleep with "hdparm -y /dev/hda" which works nicely, the drive spins down and silence commences. However, after 3 seconds the disk powers up again and makes this awful noise again.
The noise does not happen if I wait at the Yaboot screen, so its definitely something in Ubuntu.
I have killed all userland processes including all the logging to no avail.
I tried the suggestion about acoustic management from the aforementioned thread, but apparently the drive does not support this as it just throws up an error.

This noise is not only annoying, it also prevents the hd from ever spinning down.
I have made a short recording of the sound, maybe this rings a bell with someone:
[http://www.kashofer.dyndns.org/weird_sound.ogg](http://www.kashofer.dyndns.org/weird_sound.ogg) (500kb)

The computer was idle at that time, just sitting there recording to RAM.

Its the loud sound in the foreground, the background noise is another computer.
Anyone having a similar experience ?
Ideas ?

Thanks,
Karl

---

### Post by ::DoGG:: on 2005-05-25
What is You filesystem on a hdd ? I had the same problem some time ago in debian on ext3 filesystem. turnsout that it was some daemon running in background causing hdd to journal . when in moved back to ext2 on fresh install everything went ok.

---

### Post by karl_kashofer on 2005-05-25
Hi !

I just mounted the drive as ext2 , but noise is still here.

Bugger.
Cheers,
Karl

---

### Post by ::DoGG:: on 2005-05-26
well in ext2 should be ok... anyawy, in my opinion something is running in background, that`s not a filesystem or hdd fault. Did You checked all the processes ? Probably one of them is responsible for some logs, is making check about couple seconds that`s why You got the noise.

---

### Post by mcarter on 2005-05-26
Try installing the laptop-mode packages if they're not installed, and edit the config file to enable laptop-mode even when on AC power.  It reconfigures everything to reduce disk writes.

---

### Post by karl_kashofer on 2005-06-03
Hi !

Just wanted to let you guys know that this actually worked !
After installing laptop-mode and laptop-mode-tools the hd is perfectly silent now when I type "laptop-mode start"

To get that working with pbbuttons you need to configure your AC setting to "powersave".

I also found that the spindown time is lost after a sleep cycle so i added a script to /etc/apm/events.d/resume.d All it does is "hdparm -S 4 /dev/hda"

So now the hd is silent all the time (as laptop-mode is started all the time) and spin down is controlled in the laptop-mode script and additionally set after sleep by my script.

Very happy now, 
Cheers,
Karl

---

### Post by Rxke on 2005-06-03
Could you post this script etc. with a bit of explanation for newbies?

I could probably figure it out myself after a lot of trial and error, but since, I've got to study, not tinker, and you've got a real working setup, I'm interested how you did it...

---

### Post by Tommy on 2005-07-10
[QUOTE=karl_kashofer]
After installing laptop-mode and laptop-mode-tools the hd is perfectly silent now when I type "laptop-mode start"

To get that working with pbbuttons you need to configure your AC setting to "powersave".

I also found that the spindown time is lost after a sleep cycle so i added a script to /etc/apm/events.d/resume.d All it does is "hdparm -S 4 /dev/hda"
[/QUOTE]

I've been trying to figure this out myself, but I discovered that you don't need to install the laptop-mode-tools to be able to issue the "laptop-mode start" command. In fact, from all my reading, pbbuttonsd and the other power management tools should be starting laptop-mode already, though on my machine it isn't starting. There must be a bug somewhere. (Maybe in my brain?) If I manually start laptop-mode the behavior is just as I expect.

I see some bugs reported against laptop-mode, including [https://bugzilla.ubuntu.com/show_bug.cgi?id=6111](https://bugzilla.ubuntu.com/show_bug.cgi?id=6111)  but this particular one doesn't sound like exactly the same thing. (Except the part about losing the hdparm settings, and the acknowledgement that someone is working to fix the scripts.) 

I believe the relevant scripts on Hoary PowerPC are in the /etc/power/ directory. There is also the /etc/default/laptop-mode file... but even though mine says ENABLE_LAPTOP_MODE="yes" it's not starting.

---

### Post by KrIaXPaTaLa on 2005-07-14
Apologise for my ignorance, but how can one tell if laptop-mode is enabled?

Regards,

Kriax, Portugal.

---

### Post by Tommy on 2005-07-14
[QUOTE=KrIaXPaTaLa]Apologise for my ignorance, but how can one tell if laptop-mode is enabled?[/QUOTE]

That is a very good question -- I have ASSUMED the mode has not started because my hard drive doesn't spin down, but after I issue the "laptop-mode start" command, the drive spins down, and maintains the characteristic low-power activity until I reboot. 

On the other hand, if I subsequently issue the "laptop-mode start" command, it gives the same message -- "Starting Laptop_mode." I don't know how to tell.

I'm digging through this site:
[http://www.xs4all.nl/~bsamwel/laptop_mode/](http://www.xs4all.nl/~bsamwel/laptop_mode/)

which mentions man pages, but apparently you don't get those until you install the laptop-mode-tools package (which isn't normally installed in Ubuntu, so I removed it to see if it was interfering with anything). 

Apparently Ubuntu uses some method OTHER than laptop-mode-tools to activate the features. If anyone finds some ubuntu-specific documentation it would be helpful. I'm not sure what scripts are SUPPOSED to activate it on an Ubuntu installation. When I get a few minutes today I may have a look at the laptop-mode start script (but it will take a bit more digging to find out what's supposed to CALL it).

---

### Post by KrIaXPaTaLa on 2005-07-14
It seems laptop-mode is starting by itself, on system startup. The reason I think this, is that, at shutdown, I get the message "stopping laptop-mode", whitout me starting it manualy during my work session. Still, I have no idea of how to confirm this. I should say that I get about 100 minutes worth of work with full battery on my Pentium M 1.6 (acer travelmate 4002). But I get at least 3 hours in windows :S

Regards,

Kriax, Portugal.

---

### Post by Tommy on 2005-07-14
[QUOTE=KrIaXPaTaLa]It seems laptop-mode is starting by itself, on system startup. The reason I think this, is that, at shutdown, I get the message "stopping laptop-mode", whitout me starting it manualy during my work session. Still, I have no idea of how to confirm this.[/QUOTE]

I have not noticed that message, but I am not usually looking at the messages as it shuts down. I'm almost positive there's no "laptop-mode start" message when mine is booting, and I just dug through /etc/init.d/ and /etc/rc0.d/ and /etc/rc2.d/ and /etc/rc6.d/ and I didn't see any scripts with "laptop" in the name.

So I wonder what script is calling it (or is supposed to be)? One way to figure it out would be to go to the virtual console and manually call all the scripts in rc0.d and watch to see.

Oh, what the heck... I'll do that now and report back. -- I just did  -- DON'T do it, or at least don't run the script "S20sendsigs stop" because that will kill off your bash session and your only choice is to hit the reset button.

Anyway, I can confirm that the laptop-mode message does NOT appear on this computer when it's starting up or shutting down. I'm running Hoary on a PowerBook G3 -- I gather yours is not PowerPC, so your startup and shutdown scripts could be different.

---

### Post by Tommy on 2005-07-14
I just opened a bug -- [http://bugzilla.ubuntu.com/show_bug.cgi?id=12701](http://bugzilla.ubuntu.com/show_bug.cgi?id=12701)

I entered it as a PowerPC bug but I presume others commenting here are running other platforms...

---

### Post by Bart Samwel on 2005-07-27
Hi there,

I'm the author of Laptop Mode Tools and the maintainer of the Debian package laptop-mode-tools. I've just found out about the existence of the Ubunto laptop-mode package and have done some research. Here's what I've found.

The Ubuntu laptop-mode package predates the laptop-mode-tools package, and it is based on the script that laptop mode tools forked off of about a year ago. This old script was maintained mostly by me in the kernel documentation, and I forked and abandoned it a year ago because of the patching hassle (every change had to go through Linus) and the installation hassle (it was a script embedded in the documentation). I've checked the laptop-mode package, and it seems to be mostly a verbatim packaging of that script, except for the addition of /etc/default/laptop-mode support.

I guess you'd currently be better off running laptop-mode-tools instead, as it represents a year's worth of improvements and bugfixes, and has an actual config file, manpages, and an online FAQ. Whatever you do, you want to install either laptop-mode-tools or laptop-mode, but not both, because they will probably interfere with eachother. I'm talking to the maintainer of the laptop-mode package to resolve this confusing mess.

(If you have any further questions, mail me, because I won't be following the discussion.)

--Bart

---

### Post by polzin on 2005-12-14
[QUOTE=Bart Samwel]Whatever you do, you want to install either laptop-mode-tools or laptop-mode, but not both, because they will probably interfere with eachother. 
[/QUOTE]

Stupid question:
Here I get a problem, because ubuntu-desktop depends an acpi-support and this on  laptop-mode. If I try "apt-get remove laptop-mode" it says that I am about to deinstall ubuntu-desktop.  Any suggestion?

Tobias

---

### Post by Tommy on 2005-12-14
[QUOTE=polzin]Stupid question:
Here I get a problem, because ubuntu-desktop depends an acpi-support and this on  laptop-mode. If I try "apt-get remove laptop-mode" it says that I am about to deinstall ubuntu-desktop.[/QUOTE]

It's not a stupid question... You should be able to remove ubuntu-desktop with no problems, though if the package manager offers to remove tons of other things along with it, you should decline. 

ubuntu-desktop is a "meta" package that has lots of dependencies, and its main purpose is to make upgrades easier. If you need to remove it in this sort of circumstance, you'll just want to remember to re-enable it before doing a major upgrade.

(If you open Synaptic and select ubuntu-desktop, you'll its description that says pretty much the same thing. Starting in Breezy you also see other meta packages such as kubuntu-desktop, edubuntu-desktop, and xubuntu-desktop. They all serve similar functions for various ubuntu-derived collections.)

---

### Post by Tommy on 2005-12-14
[QUOTE=polzin]ubuntu-desktop depends an acpi-support and this on  laptop-mode...[/QUOTE]

I just looked on my system and don't see that dependency, but I'm using PowerPC and it doesn't even have acpi-support... so I did not have to remove ubuntu-desktop.

It's possible you will run into some other dependency problem. I believe from the command line you can "force" apt to override the stated depencencies, but you do risk having a "broken" dependency. (Probably not critical here, but potentially a problem.)

If you can't make the change to those two or three packages without causing all sorts of other things to happen, write back again....

---

### Post by pelle.k on 2006-01-15
[http://www.ubuntuforums.org/showthread.php?p=660011](http://www.ubuntuforums.org/showthread.php?p=660011)

---

### Post by padre999 on 2006-09-10
I have the same problem since a while. A "sudo laptop-mode start" as pelle.k described did the trick. Although I don't consider this as being a fix for this problem.

I saw that there is a bugreport on this issue:

[https://launchpad.net/distros/ubuntu/+bug/17878](https://launchpad.net/distros/ubuntu/+bug/17878)

Are there still people experiencing the same (the last post is quite old) or am I the only one now?

---

### Post by padre999 on 2006-09-18
I discovered that if I disable the kernel logging and the system logging services there is less data written to the hdd every 5 seconds. Instead of up to 100kB blocks written/read they are only about 50kb. Also I added the noatime option in fstab.

This results in the hdd running quiet at least, I don't hear the access anymore. But there IS still something accessing the disk every 5 seconds as I can see on the system monitor which is not the case on a freshly installed system.

See attached screenshot of system monitor.

---

