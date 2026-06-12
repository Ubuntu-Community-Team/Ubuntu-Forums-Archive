---
title: "Where is s2ram (suspend-to-ram) ?"
date: 2006-06-11
forum: Hardware &amp; Laptops
---

### Post by el_Salmon on 2006-06-11
I'm looking for "s2ram" utility, to suspend to ram my Dell Inspiron 4150 laptop but I haven't found it yet. I've read [[wiki] KubuntuPowersave]("https://wiki.ubuntu.com/KubuntuPowersave") and [OpenSuse : S2RAM]("http://en.opensuse.org/S2ram") and I think "s2ram" comes with "powersaved" or "suspend" packages but it's not clear.

---

### Post by jetpeach on 2006-07-05
I am also looking for this, all the KubuntuPowersave wiki says is "s2ram Kubuntu packages:      This program is supported by powersave and should fix suspend/resume on several machines. see: s2ram-project-page" but then on the s2ram page it has no info about installing or downloading, it says "2ram is part of the suspend project hosted on sourceforge and a package for SUSE 10.1 is available." so I go to the suspend page and find messages like "In orded to try µswsusp you must run a recent -mm kernel or mainline 2.6.17-rc1."  So it looks like we won't get suspend on our laptops in dapper? :(

---

### Post by returntoreality on 2006-07-11
the project suspend includes some tools, one of them is s2ram, which doesn't need a .17 kenrel or a -mm-patch. Suspend and resume, 2 other tools in this project need such a kernel but you can just compile s2ram without building resume or suspend. (after unpacking simply "make s2ram" in the extracted directory)

---

### Post by hizaguchi on 2006-07-25
I can suspend my 4150 using apm (not acpi though) by using "ctrl+alt+F6" to get away from X and then "Fn+Esc" to suspend.  When you wake it back up though, you have to hit "Fn+z" to refresh the bios or the fan will never stop spinning.  Probably not exactly what you're looking for, but it works.

---

### Post by pjotre on 2007-03-19
Hi!

I'm also having a problem with s2ram on my HP nx6310.

I tried it on Opensuse10.2 and it worked perfectly with s2ram -f (my notebook is not in the whitelist, so I had to force s2ram). Since I don't really like Suse that much (can't get clear fonts in Gnome/KDE) I switched back to Kubuntu and installed kpowersave. I also donwloaded suspend which contains s2ram ([http://sourceforge.net/project/showfiles.php?group_id=45483](http://sourceforge.net/project/showfiles.php?group_id=45483)) and installed it. 

When I tried to run s2ram -f it perfectly put the notebook into standby, but I couldn't resume (screen stayed black). 

I don't understand why it works in Suse but won't work in Kubuntu...

Do I have to deinstall guidance-power-manager? I only disabled it in KDE. Also, I only tried it with the live-cd, could this make a difference too?

Any ideas?

---

### Post by glenndavy on 2007-03-19
hey there el-salmon

sounds fishy to me

dpkg -S s2ram  tells me that its in the package uswsup

i.e.

apt-get install uswsup

... see how it goes, i think thats how dpkg -S is supposed to work

glenn

---

### Post by pjotre on 2007-03-20
where can I get uswsup? It's not in my repositories...

---

### Post by glenndavy on 2007-03-20
apparently its in universe... have you enabled universe and multiverse in your repositories (and if not do you need a hand doing so?)

which version are you running... edgy or fiesty? - when I get a chance i'll check that what im saying applies to edgy also

---

### Post by glenndavy on 2007-03-20
hey there - apparently that doesnt apply to edgy... sorry for the bum lead.- anyone else know how to install s2ram on edgy?

---

### Post by pjotre on 2007-03-23
Hi!

I found uswsusp here: [http://packages.ubuntu.com/edgy/utils/uswsusp](http://packages.ubuntu.com/edgy/utils/uswsusp)

But it doesn't contain s2ram. So I installed suspend ([http://sourceforge.net/project/showfiles.php?group_id=45483](http://sourceforge.net/project/showfiles.php?group_id=45483)) and kpowersave and I was finally able to use sudo s2ram -f which works fine on Opensuse for my notebook. It put my computer into sleep, but I wasn't able to resume. This is kinda strange I think, since I thought it'd work the same on any distribution. 

So now I'm stuck with Opensuse :( 

I hope (K)Ubuntu will properly implement s2ram soon!

If you find out anything, let me know.

---

### Post by glenndavy on 2007-03-23
hi - yes you're right - like i said above, doesnt have s2ram in ediy... im running fiesty, which has s2ram in the uwswup, if i understand dpkg -S correctly

suspending and hibernating are delicate, confusing and frustrating area i!?!

I found same thing. (ie cant resume from a seemingly successful suspend) .. but on fiesty using /usr/share/doc/uswsusp/README.s2ram-whitelist, i found some things to try. These are expanded on at [http://opensuse.org/s2ram](http://opensuse.org/s2ram) - i think you'll find something there to solve your prob

---

### Post by pjotre on 2007-04-04
Now I'm also running Feisty. Everything works pretty well, even suspend2ram worked out of the box - but only for like six or seven times. After that, I received an error-message in Gnome and since then it won't work anymore (keyboard won't wake up).

So I tried uwsusp and it works too!!!

But only if I use s2ram -f
But it works perfectly, even networks comes back.

Now my problem is this: How can I tell Gnome that it should use s2ram -f? I don't want to run it from the console everytime.... 

Any ideas?

I'd be glad...

BTW: Feisty is really nice! I'm glad I got rid of Opensuse, trust me!

---

### Post by glenndavy on 2007-04-04
> 
Now my problem is this: How can I tell Gnome that it should use s2ram -f? I don't want to run it from the console everytime....


yeah - dunno sorry - im trying to do the same thing from kubuntu. Im still confused about this, will post something here if i make any progress.

> BTW: Feisty is really nice! I'm glad I got rid of Opensuse, trust me!

yeah 'tis nice... though a mate just bought over his work laptop with opensuse on it - wanted a hand re ATI fglrx... gota say i'm coveting sax2 and also the default menu facility in their kde desktop.

---

### Post by pjotre on 2007-04-04
I didn't like suse's kde menu. I also had a hard time to make fonts look ok (they never looked good though - especially within this menu).

Anyways, I read this blog: [http://blog.paulbetts.org/index.php/2007/02/11/fixing-software-suspend-hibernate-with-uswsusp-in-ubuntu-feisty-and-edgy/](http://blog.paulbetts.org/index.php/2007/02/11/fixing-software-suspend-hibernate-with-uswsusp-in-ubuntu-feisty-and-edgy/)

and asked Robin Battey for help. This is what he wrote back:

> Actually, since I posted that comment, I've learned a bit more about the 
acpi scripts on feisty.  You don't have to divert pmi, and you can have 
pmi call s2disk itself.  All the magic is in the /etc/acpi/ directory, 
which contains all of the scripts that run when acpi events occur.  All of 
them you should consider modifying, anyway.

It's better to let pmi handle things, I've found, because the acpi scripts 
in /etc/acpi do things like unloading your network drivers, spinning down 
your disks, re-checking power status when you resume, and the like.  
Simply running "s2disk" (or "s2ram") doesn't do any of this, which can 
lead to some strange behavior on resume.

To directly answer your question, remove the dpkg-divert (run "dpkg-divert 
--remove /usr/sbin/pmi") and edit the /etc/acpi/hibernate.sh and 
/etc/acpi/sleep.sh scripts.  In hibernate.sh, you'll have to change how 
s2disk is called, because the s2disk command changed its commandline 
options since the acpi script was written.  In sleep.sh, you'll have to 
change the line echoing to /sys/power/state to call s2ram instead.

I've attached patch files you can apply to your acpi directory, assuming 
you haven't modified any files in there already.  The patch changes the 
two script to use uswsusp if it is installed, and to use the old method if 
it's not.  Don't forget to remove the dpkg-divert, or these scripts won't 
get called in the first place.

Cheers!
-robin

I tried to do this, and it kinda worked, but it didn't really solve my problem. He also attached a script to his mail, I can send it to you if you want, just send me your email-address (PM).

Maybe together we can figure things out!

---

### Post by glenndavy on 2007-04-04
hey there - I checked that blog, robin batteys reply and the acpi approach you mentioned - not getting anywhere.

on top of that i also get "suspend: could not open the resume device" when I s2disk

funny thing is I can run sleep.sh, and works fine, but cant get that script to fire in resoponse to say shutting lid, or requestion 'suspend' fromthe powermanager interface.

tried powersave instead of default pmi, no better
looks like its back to s2ram, or /etc/acpi/sleep.sh manually for me

thx for the info

---

### Post by kilou on 2007-05-01
What are the modification the need to be applied to sleep.sh and hibernate.sh to point these to s2ram -f and s2disk (uswsusp)?

---

### Post by schmolch on 2007-05-01
I know how to tell Gnome to use s2ram and/or s2disk.

I will tell you how to do it if somebody tells me why my networkmanager fails after resuming from s2ram.
It tries connecting but never succeeds.
If i run dhclient eth1 it works, but only until the networkmanager tries again and resets it. Sometimes it even says its connected but it isn't (the led is off or blinking).

---

### Post by kilou on 2007-05-02
Schmolch, I know how to make network manager work after resume/hibernate and I will tell you how to do it if you tell me how to modify the sleep.sh and hibernate.sh scripts to run with s2ram and s2disk LOL

No seriously here is what I found for your problem. I'm not sure this will solve it but just try (taken from [https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager))

Suspend support

At this point your connection won't survive suspend or hibernate. You have to create two files for that:

    *

      /etc/acpi/suspend.d/07-network-manager.sh

#!/bin/sh
/etc/dbus-1/event.d/25NetworkManager stop

    *

      /etc/acpi/resume.d/63-network-manager.sh

#!/bin/sh
/etc/dbus-1/event.d/25NetworkManager start

---

### Post by zanfur on 2007-05-02
Hi!  I am the aforementioned Robin Battey.

Here's a breakdown of how things work in Feisty:

When an acpi event occurs, it calls the scripts from the "hal" package, which are located in /usr/lib/hal/scripts.  These are mainly just permission-checking frontends for the scripts in the /usr/lib/hal/scripts/linux directory (or some other subdirectory if you're running something other than linux, but I assume you're running ubuntu if you're reading this thread).  These scripts are (somewhat) standardized, in /usr/lib, under package management, and in general I advise you to just leave them well enough alone.  It's good to know the starting place, though, so you can follow through what happens.

The script in question here, /usr/lib/hal/scripts/linux/hal-system-power-hibernate-linux, basically just goes down a list of power management software until it finds one, then runs that.  The first one it checks for is /usr/bin/powersave (in the powersaved package), and the second it checks for is /usr/sbin/pmi (in the powermanagement-interface package).  The powermanagement-interface package is installed by default, and powersaved is not, so that's the one it uses, by default.  It calls it as "/usr/sbin/pmi action hibernate".  (The hal-system-power-suspend-linux is similar, and calls pmi as "/usr/sbin/pmi action suspend".)

The /usr/sbin/pmi file is actually a bash script, so you can take a look at it and see what it does.  To save you the trouble, I'll tell you that it sources the config in /etc/default/acpi-support, loads the device functions from /usr/share/acpi-support/device-funcs, and runs "/etc/acpi/hibernate.sh force" (or "/etc/acpi/sleep.sh" if it was told to suspend).

If you take a look at the hibernate script, it goes through the scripts in /etc/acpi/hibernate.d, doing things like locking your screen, spinning your disks down, and a number of other things that make hibernating nice.  It then tries to hibernate, *first* trying s2disk, but using the standard kernel hibernate if s2disk isn't installed.  Unfortunately, there's an error in the script.  Here's what that section looks like:

 if [ -x /sbin/s2disk ]; then
     DEVICE="/dev/disk/by-uuid/`awk -F= '{print $3}' </etc/initramfs-tools/conf.d/resume`"
    if [ -f /etc/usplash.conf ]; then
        . /etc/usplash.conf
        /sbin/s2disk -x "$xres" -y "$yres" $DEVICE
    else
        /sbin/s2disk $DEVICE
    fi
 else
     echo -n "disk" >/sys/power/state
 fi

There are two problems with this.  First, s2disk no longer accepts -x or -y arguments, making this fail if you have usplash installed, and hence making hibernate fail in general (it doesn't fall back to other methods).  Second, the device string is completely unnecessary (it's just the UUID of your swap partition), and upgrades to the kernel change your swap partitions UUID.  (This is a bug, but it happens. If you ever find that your swap partition stops mounting, this is almost surely why.)  Not good news for people who want to use s2disk.

However, now that we're in /etc, we're in config-file land, which means changes won't get automatically overwritten by package management.  This is where I recommend you make your changes.  Get rid of the junk above and replace it with this:

 if [ -x /sbin/s2disk ]; then
    /sbin/s2disk
 else
     echo -n "disk" >/sys/power/state
 fi

That will make everything work with s2disk, through gnome's power manager, kde's power manager, kpowersave, klaptop, etc. Assuming you have s2disk installed, that is (the "uswsusp" package).  If you want to use s2ram (or s2both) for sleep mode as well, you'll have to edit the /etc/acpi/sleep.sh script, changing the following line to whatever you want to use instead:

 echo -n $ACPI_SLEEP_MODE >/sys/power/state

You probably will want to change it to this (change s2ram to s2both if you'd rather):

 if [ -x /sbin/s2ram ]; then
    /sbin/s2ram
 else
     echo -n $ACPI_SLEEP_MODE >/sys/power/state
 fi


Hope this clears things up for people.  Enjoy!

---

### Post by kilou on 2007-05-03
Thanks a lot Robin!! Everything works perfectly now and I can finally suspend and hibernate properly. Even Network manager restart correctl on resume!! GREAT!

Thanks so much

---

### Post by drobvice on 2007-05-04
I get a gray bar in the middle of the screen (when the ubuntu usplash appears) when I resume form hibernate.  Is this normal?

---

### Post by kilou on 2007-05-04
Yes this is normal. You could get a splash screen I think by installing splashy and splashy-themes packages but I cannot resume with them enabled.

---

### Post by nischg on 2007-05-07
I followed Robin's instructions and now both, sleep and hibernate work great on my Dell Inspiron e1505 / 6400.

Thanks a lot for all your research. It's going to make my Ubuntu-life easier.

---

### Post by nischg on 2007-05-15
So far I've noticed only one problem: after resuming one of my Core Duo's cores (CPU 1) is working at full load. I cant change the governor via gnome-applet, it's stuck on "ondemand" governor.

Any clues?

---

### Post by krugman on 2007-05-22
Hi guys!

I have also used the tip provided here, and now hibernate works on my laptop. However, it seems that after that, the power manager does not see when I am running on battery. Indeed, I have been running on batteries for 10 minutes, and it still says that I am at 99% of battery.

Anyone has the same problem???

---

### Post by H.E. Pennypacker on 2007-06-02
> **zanfur said:**
> 
However, now that we're in /etc, we're in config-file land, which means changes won't get automatically overwritten by package management.  This is where I recommend you make your changes.  Get rid of the junk above and replace it with this:

 if [ -x /sbin/s2disk ]; then
    /sbin/s2disk
 else
     echo -n "disk" >/sys/power/state
 fi

That will make everything work with s2disk, through gnome's power manager, kde's power manager, kpowersave, klaptop, etc. Assuming you have s2disk installed, that is (the "uswsusp" package).  If you want to use s2ram (or s2both) for sleep mode as well, you'll have to edit the /etc/acpi/sleep.sh script, changing the following line to whatever you want to use instead:

 echo -n $ACPI_SLEEP_MODE >/sys/power/state

You probably will want to change it to this (change s2ram to s2both if you'd rather):

 if [ -x /sbin/s2ram ]; then
    /sbin/s2ram
 else
     echo -n $ACPI_SLEEP_MODE >/sys/power/state
 fi


Hope this clears things up for people.  Enjoy!

I hate to be a pain, but this post is not exactly clear about what configuration file we are editing in the first place.  You said to replace our text with the text you have given us, but which file are we doing this in?  I have the same problem with the second part of your post.  What files are 

Also, where do I get s2disk from?  I can't find it in Synaptic, and a Google search doesn't provide a download.  s2ram is available via Google, but it looks like it is primarily available to SUSE users, and not us.

---

### Post by kilou on 2007-06-03
s2disk and s2ram are part of the uswsusp package. The two files you need to modify are /etc/acpi/hibernate.sh and /etc/acpi/sleep.sh. For simplification just do the following (if you're using GNOME):

*** install uswsusp package if not already installed ***

1) sudo gedit /etc/acpi/hibernate.sh
2) Delete everything and copy/paste the folowing, then save:

```
#!/bin/bash

. /etc/default/acpi-support
. /usr/share/acpi-support/power-funcs
. /usr/share/acpi-support/policy-funcs

if [ x$ACPI_HIBERNATE != xtrue ] && [ x$1 != xforce ]; then
  exit;
fi

# Unset video posting - it's not needed for suspend to disk
unset POST_VIDEO
unset USE_DPMS

. /etc/acpi/prepare.sh

#if [ x$LOCK_SCREEN = xtrue ]; then
#    for x in /tmp/.X11-unix/*; do
#	displaynum=`echo $x | sed s#/tmp/.X11-unix/X##`
#	getXuser;
#	if [ x"$XAUTHORITY" != x"" ]; then
#	    export DISPLAY=":$displaynum"
#	    . /usr/share/acpi-support/screenblank
#	fi
#    done
#fi

echo -n $HIBERNATE_MODE >/sys/power/disk

if [ -x /sbin/s2disk ]; then
/sbin/s2disk
else
echo -n "disk" >/sys/power/state
fi

$LAPTOP_MODE stop

. /etc/acpi/resume.sh
```

3) sudo gedit /etc/acpi/sleep.sh
4) Delete everything and copy/paste the following, then save

```
#!/bin/bash

. /etc/default/acpi-support
. /usr/share/acpi-support/power-funcs
. /usr/share/acpi-support/device-funcs
. /usr/share/acpi-support/policy-funcs

DeviceConfig;

if [ x$ACPI_SLEEP != xtrue ] && [ x$1 != xforce ]; then
  exit;
fi

# If gnome-power-manager or klaptopdaemon are running, let them handle policy
if [ x$1 != xforce ] && [ x$1 != xsleep ] && [ `CheckPolicy` = 0 ]; then
    exit;
fi

if [ x$LOCK_SCREEN = xtrue ]; then
    if pidof xscreensaver > /dev/null; then 
	for x in /tmp/.X11-unix/*; do
	    displaynum=`echo $x | sed s#/tmp/.X11-unix/X##`
	    getXuser;
	    if [ x"$XAUTHORITY" != x"" ]; then	    
		export DISPLAY=":$displaynum"
		. /usr/share/acpi-support/screenblank
	    fi
	done
    fi
fi

# Generic preparation code
. /etc/acpi/prepare.sh

if [ x$DISABLE_DMA = xtrue ] && [ -b /dev/hda ]; then
  hdparm -d 0 /dev/hda
fi

if [ -x /sbin/s2ram ]; then
/sbin/s2ram -f
else
echo -n $ACPI_SLEEP_MODE >/sys/power/state
fi

if [ x$RESET_DRIVE = xtrue ] && [ -b /dev/hda ]; then
    hdparm -w /dev/hda
    hdparm -C /dev/hda
    hdparm -C /dev/hda
    hdparm -C /dev/hda
    hdparm -d 1 /dev/hda
fi

if [ x$DISABLE_DMA = xtrue ] && [ -b /dev/hda ]; then
  hdparm -d 1 /dev/hda
fi

# Generic wakeup code
. /etc/acpi/resume.sh
```

5) enjoy!

---

### Post by H.E. Pennypacker on 2007-06-03
kilou, I really appreciate your post, but it is still not working for me.  uswsusp is installed, and I replaced the two files with what you have given me.  No luck at all.  It is especially frustrating because things were perfectly fine on Edgy.

---

### Post by kilou on 2007-06-04
> **H.E. Pennypacker said:**
> kilou, I really appreciate your post, but it is still not working for me.  uswsusp is installed, and I replaced the two files with what you have given me.  No luck at all.  It is especially frustrating because things were perfectly fine on Edgy.

Please explain what happens when you hibernate/suspend and what is the problem?

---

### Post by H.E. Pennypacker on 2007-06-04
> **kilou said:**
> Please explain what happens when you hibernate/suspend and what is the problem?

When I click on System > Quit, and select Suspend or Hibernate, the laptop never suspends or hibernates.  The screen goes dark, plays the screen saver, and if I move the mouse, it shows the password dialog.  It is as if I locked the screen, instead of having selected suspend or hibernate.

When I come back, Gnome starts acting up.  The desktop is not as responsive (clicking on something will produce a result a moment after the click) and my wireless is entirely gone (it disappears, even from an iwconfig result - iwconfig doesn't show eth1).

Logging out, and logging back in does not help.  Actually, I can log out, but logging back in is very troublesome.  The screen freezes for a while, shows a windowless gray area on the left side, and after quite a while, shows an error saying Gnome Settings Daemon died or something.  Wireless won't come back without restarting.  

I have also tried killing the X server (CTRL-ALT-BACKSPACE), but it doesn't help.

---

### Post by kilou on 2007-06-04
The wifi gone after resume can be cured this way:

You have to create two files for that:

* /etc/acpi/suspend.d/07-network-manager.sh

#!/bin/sh
/etc/dbus-1/event.d/25NetworkManager stop

* /etc/acpi/resume.d/63-network-manager.sh

#!/bin/sh
/etc/dbus-1/event.d/25NetworkManager start


Did you use the pmi divertion as proposed on the beginning of this thread? If you do you need to disable it.

---

### Post by H.E. Pennypacker on 2007-06-05
kilou, again, no luck.  Your wireless instructions didn't work for me either.  I don't know if I was supposed to have made those config files executables, but it's not working.  

I don't know what PMI is, but I am sure I didn't do anything PMI related.  

Looks like I am screwed, huh?  It sucks.

---

### Post by zanfur on 2007-06-06
Pennypacker:

It sounds like the acpi subsystem went through all the preparation to suspend (ran everything in /etc/acpi/suspend.d), but then the suspend itself failed for some reason.  You can get more information on why that is by invoking s2disk directly from the command prompt ("sudo s2disk").  If it says something like "can't find device", this means you have uswsusp configuration problems (look at /etc/uswsusp.conf), or that your swap isn't mounted (easiest way to check this is to run "top" and look at the "Swap:" field -- if it's zero, you have no swap).

When running s2disk manually fails without giving you an error message, you can find out more about what happened by running "dmesg".

Cheers!
-robin

---

### Post by ym4546 on 2007-06-13
I have a question for Robert (or anyone else),

I am running Kubuntu Feisty on a Dell Dimension 8200 desktop. Here's what happens when I suspend or hibernate:

1. i press the appropriate button from the kde menu, and either the suspend or the hibernation happens without a problem.

2. when i attempt to resume, i get a blank screen (the screen's on, but its blank). My USB keyboard is unresponsive, I ahve no mouse cursor or blinking cursor either.

Will (or might) the fix you mentioned (in post #19) deal with this? If there is a chance that it will fix it, can i reverse the steps just by replacing the original file?

Sorry to be a pain but I'm relatively inexperienced with this stuff, and I just want to make sure that if i screw anything up, I can reverse it.

Thanks for you time and expertise.

---

### Post by ym4546 on 2007-06-13
UPDATE: I was feeling risky, and tried that method, but it didn't work. However, I could replace the original copies of hibernate.sh and sleep.sh without problems.

I also tried a regular sudo s2disk, and I got the same result as before.

Could it be a bios problem? (i'm kind of scared of flashing an updated bios...)

---

### Post by jetpeach on 2007-06-14
ym4546, i'm not an expert, but i've had suspend problems for a long time one my laptop (presario 2100). i have not yet found a solution and am told it is because the ACPI functionality of some computers are not implemented properly - i guess they work on windows because they were implemented and tested solely on windows, but they do not meet the standard so fail with the implementation used by open-source...

i'm not sure if this is all true, and regardless, i should greatly appreciate if they got this functionality working on as many laptops/computers as possible.  i am still hoping to find a solutions, but to answer your question about the bios: no, i wouldn't expect flashing the bios to help (i would doubt they changed much/if any of the ACPI functionality in the bios in any revisions released), however technically the "problem" is with the bios, since it doesn't suppor the standard ACPI implementation...but this doesn't help us, so i will continue to look for and hope for a fix that will get s2ram working on my laptop.

---

### Post by andnobodyslept on 2007-06-18
So I've been looking over this thread (and the blog page) for the last day, I think I have tried all the tricks, editing the suspend.sh and hibernate.sh files, creating the network manager files, and yet still nothing seems to work. If I suspend using the gnome icon (quit, suspend) I get a bunch of error messages, mainly errno: 19. If I use the terminal and go with s2ram -f everything seems to work, or at least comes back to life, but I have the network manager problems, and it seems as though X can't find anything, example: I hit the firefox icon and it comes back saying that it can't find the file to implement firefox, same with the terminal, and slowly all the icons switch to white boxes with a red X. 

Maybe someone can think of an idea?

Thanks.

---

### Post by ehula on 2007-06-22
Firstly, thanks to Robin for his suggestions.

I am able to successfully suspend using "sudo s2ram" and hibernate using "sudo s2disk". I then followed Robin's instructions as follows:

**_/etc/acpi/hibernate.sh_**

changed:
>  if [ -x /sbin/s2disk ]; then
     DEVICE="/dev/disk/by-uuid/`awk -F= '{print $3}' </etc/initramfs-tools/conf.d/resume`"
    if [ -f /etc/usplash.conf ]; then
        . /etc/usplash.conf
        /sbin/s2disk -x "$xres" -y "$yres" $DEVICE
    else
        /sbin/s2disk $DEVICE
    fi
 else
     echo -n "disk" >/sys/power/state
 fi

to:
>  if [ -x /sbin/s2disk ]; then
    /sbin/s2disk
 else
     echo -n "disk" >/sys/power/state
 fi

**_/etc/acpi/sleep.sh_**

changed:
>  echo -n $ACPI_SLEEP_MODE >/sys/power/state


to:
>  if [ -x /sbin/s2ram ]; then
    /sbin/s2ram
 else
     echo -n $ACPI_SLEEP_MODE >/sys/power/state
 fi

I am now able to hibernate using Fn-F12 on my Thinkpad and by using the hibernate button Gnome Power Manager, but I am not able to suspend using either Fn-F4 or the suspend button or running "sudo /etc/acpi/sleep.sh" manually, but I still can suspend by "sudo s2ram".

Can anyone help me out?

---

### Post by madc on 2007-08-04
> **zanfur said:**
> Hi!  I am the aforementioned Robin Battey.

Here's a breakdown of how things work in Feisty:

  Get rid of the junk above and replace it with this:

 if [ -x /sbin/s2disk ]; then
    /sbin/s2disk
 else
     echo -n "disk" >/sys/power/state
 fi

That will make everything work with s2disk, through gnome's power manager, kde's power manager, kpowersave, klaptop, etc. Assuming you have s2disk installed, that is (the "uswsusp" package). 

Hope this clears things up for people.  Enjoy!


excellent, finally i have "hibernate" that works... thanks a lot!

---

### Post by owhno on 2007-08-23
> **ehula said:**
> Firstly, thanks to Robin for his suggestions.

I am able to successfully suspend using "sudo s2ram" and hibernate using "sudo s2disk". I then followed Robin's instructions as follows:

**_/etc/acpi/hibernate.sh_**

changed:


to:


**_/etc/acpi/sleep.sh_**

changed:


to:


I am now able to hibernate using Fn-F12 on my Thinkpad and by using the hibernate button Gnome Power Manager, but I am not able to suspend using either Fn-F4 or the suspend button or running "sudo /etc/acpi/sleep.sh" manually, but I still can suspend by "sudo s2ram".

Can anyone help me out?

Well if you run sleep.sh nothing happend.. so i wonderd what exit function made this call.
And now that i have commented it everything works like a charm:

```

# If gnome-power-manager or klaptopdaemon are running, let them handle policy
#if [ x$1 != xforce ] && [ x$1 != xsleep ] && [ `CheckPolicy` = 0 ]; then
#    exit;
#fi
```

---

