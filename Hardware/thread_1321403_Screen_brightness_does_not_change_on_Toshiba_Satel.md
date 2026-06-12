---
title: "Screen brightness does not change on Toshiba Satellite in Karmic"
date: 2009-11-10
forum: Hardware
---

### Post by eOgas on 2009-11-10
I've just purchased a new Satellite T135 and installed a fresh copy of Karmic Koala on it.  Pretty much everything works great right out of the box.  I had to use ndiswrapper for wireless, but it wasn't a huge hassle.  Unfortunately, there seems to be a hardware issue with the brightness changing.

The brightness is controlled using a combination of Fn and F keys.  The strange thing is that Karmic actually responds to the key presses, and changes the brightness value.  But this is not reflected in the actual brightness of the screen.  I have tried brightness applet by itself as well to no avail.  Also, the screen does not automatically dim when it is taken off of AC power.  It almost appears to be 'stuck' on full brightness at all times.

It isn't a huge issue, but I can get 9 hrs of battery life in Windows 7, and only about 6.5 in Karmic, and I suspect that this issue is the largest factor.  Any help would be appreciated.

---

### Post by eOgas on 2009-11-10
bump

---

### Post by phrizek on 2009-11-10
I'm having the exact same problem with a new laptop as well. It is a different make/model than yours so I am wondering if this is a widespread problem in 9.10. I've searched the forums and other have reported similar issues. I wonder if there is a bug report on this...

---

### Post by X1R1 on 2009-11-11
same thing here, on an Acer 5810TZ, on 9.04 I was able to just type this in a terminal:

```
xrandr --output LVDS --set BACKLIGHT_CONTROL native
```

And I can control the brightness perfectly. But now on karmic if I execute that command I get:

```
X Error of failed request:  BadRROutput (invalid Output parameter)
  Major opcode of failed request:  149 (RANDR)
  Minor opcode of failed request:  15 (RRGetOutputProperty)
  Serial number of failed request:  30
  Current serial number in output stream:  30

```

Any help would be appreciated :popcorn:

---

### Post by eOgas on 2009-11-11
X1R1, I just tried your xrandr command and I get the exact same error.  As this is a new laptop, I've only run Karmic on it, but from the sounds of it, this is a Karmic specific problem.

I'm doing a little research into what could be going on with xrandr.

---

### Post by eOgas on 2009-11-11
Okay, I've now got brightness controls working perfectly.  I used the fix discussed in this post: [http://ubuntuforums.org/showthread.php?t=121742](http://ubuntuforums.org/showthread.php?t=121742)

Basically, all you do is edit /etc/default/grub  You add 'nomodeset acpi_backlight=vendor' to the GRUB_CMDLINE_LINUX_DEFAULT line.

Everything works as expected, except for some reason the lowest brightness setting turns the screen off completely.  I don't know whether or not this is a feature or a bug.  Either way, I'm satisfied with this fix.  I hope it works for you guys too.

---

### Post by stz184 on 2009-11-13
> **eOgas said:**
> Okay, I've now got brightness controls working perfectly.  I used the fix discussed in this post: [http://ubuntuforums.org/showthread.php?t=121742](http://ubuntuforums.org/showthread.php?t=121742)

Basically, all you do is edit /etc/default/grub  You add 'nomodeset acpi_backlight=vendor' to the GRUB_CMDLINE_LINUX_DEFAULT line.

Everything works as expected, except for some reason the lowest brightness setting turns the screen off completely.  I don't know whether or not this is a feature or a bug.  Either way, I'm satisfied with this fix.  I hope it works for you guys too.

I am using Ubuntu 9.10 (upgraded from 9.04) and I haven't such file /etc/default/grub. Please help!

---

### Post by InaBanina on 2009-11-17
The fix mentioned above worked for me. I'm new to Ubuntu so it's a relief to be able to find help online. Thank you!

---

### Post by slakkie on 2009-11-17
> **stz184 said:**
> I am using Ubuntu 9.10 (upgraded from 9.04) and I haven't such file /etc/default/grub. Please help!


You should edit the following section:

```

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

```

to

```

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash nomodeset acpi_backlight=vendor

```

And run grub-update as root:

```

sudo grub-update

```

That should fix it.

---

### Post by nomnex on 2009-11-23
> **slakkie said:**
> You should edit the following section:

How does he edit a file he does not have? no /etc/default/grub in my system either:

```
user@pc:/etc/default$ ls
acpid         cacerts        kernel-helper-rc                 samba
acpi-support  console-setup  klogd                            saned
alsa          cron           linux-restricted-modules-common  ssh
apmd          cups           locale                           syslogd
apport        dbus           ntp                              tmpfs
avahi-daemon  ddclient       ntpdate                          ufw
bluetooth     devpts         pulseaudio                       useradd
bootlogd      hal            rcS                              virtualbox-ose
brltty        halt           rsync

```

EDIT: the file path seems related to Grub2, which is not installed during the update (see: [https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2))

---

### Post by rahulpatilb on 2009-11-23
I had the same problem on my Acer 4736 laptop having GM45 chipset, 4500MHD. I tried out adding 'nomodeset acpi_backlight=vendor' to the GRUB_CMDLINE_LINUX_DEFAULT line. After rebooting the brightness keys started to work, though the keys were revered. Unfortunately the brightness resets after subsequent reboots and some times stops working.

Anyone has any idea what could be the problem? Thanks in advance

---

### Post by im2061 on 2009-12-18
Go to System > Preference > Power Management
Under "Display", "Set display brightness to:", choose the brightness you prefer.

---

### Post by apstanto on 2010-01-08
I am also using Ubuntu 9.10 (upgraded from 9.04) and do not have the file /etc/default/grub.  I want to do "xrandr --output LVDS --set BACKLIGHT_CONTROL native".  Any suggestions?

---

### Post by Cabs21 on 2010-01-11
I had this same issue with 9.04 and when I upgraded to 9.10 it still didnt work.  I was ecstatic that the problem seemed to fix itself when I went from 32-bit to 64-bit 9.10 with a fresh install I could adjust the brightness with the Fn+F8/F9 key combos.  However after I updated my software the problem resurfaced and I can no longer see any results from me changing the brightness in power management or or the Fn key combos.

---

### Post by Vignesh S on 2010-01-12
OMG!! I was having the same problem on my Toshiba Satellite T110 (which is pretty much the same thing is that T135) and after I applied your fix, IT WORKS!!! :-D I seriously owe you one :-D

---

### Post by chellrose on 2010-01-31
> **eOgas said:**
> Okay, I've now got brightness controls working perfectly.  I used the fix discussed in this post: [http://ubuntuforums.org/showthread.php?t=121742](http://ubuntuforums.org/showthread.php?t=121742)

Basically, all you do is edit /etc/default/grub  You add 'nomodeset acpi_backlight=vendor' to the GRUB_CMDLINE_LINUX_DEFAULT line.

Everything works as expected, except for some reason the lowest brightness setting turns the screen off completely.  I don't know whether or not this is a feature or a bug.  Either way, I'm satisfied with this fix.  I hope it works for you guys too.

That fix works in GNOME... I can set brightness with the brightness applet or with the Fn keys.  Unfortunately, KDE3 (which I use much more often) seems to be ignoring that fix.  The link in eOgas' post takes me to a completely unrelated thread about an incorrect Ubuntu installation.  Does anyone have a suggestion for getting brightness to work in KDE?

Thanks. :)

---

### Post by Viaxl on 2010-02-03
THANKS DUDE! You saved my ***!
even this didn't work at first. I'm using Grub2.  I append that line to the GRUB_CMDLINE_LINUX_DEFAULT there was no effect.

then after a lot of reading I figured out the update-grub doesn't work to me at all. it just doesn't change the \boot\grub\grub.cfg (I found this problem because I can't update Kernel too. changing in menu.lst has no effect either)

so i edit the grub.cfg... ignoring "DO NOT EDIT THIS FILE", append "nomodeset acpi_backlight=vendor" , so the entry changes to:
```
menuentry &#8220;Ubuntu, Linux 2.6.31-14-generic&#8221; {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,1)
    search &#8211;no-floppy &#8211;fs-uuid &#8211;set c6a96e39-7f93-4663-b35f-8df4d30b0764
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=c6a96e39-7f93-4663-b35f-8df4d30b0764 ro quiet splash [COLOR=Red]nomodeset acpi_backlight=vendor[/COLOR]
    initrd    /boot/initrd.img-2.6.31-14-generic
}
```reboot, it works! both in gnome and KDE!
you saved my eyes too~
hope this could help someone, even though i'm not sure what i am doing. i'm such a newbie to linux, maybe someone could explain to me why? is it a bug?

---

### Post by Ganda1f on 2010-02-09
[FONT=Arial]I am running Ubuntu 9.04 on Acer laptop, and I had to edit[/FONT] [FONT=Courier New]/boot/grub/menu.lst[/FONT] and do the changes specified by slakkie.

Once those changes are done you need to run  the command ```
sudo update-grub
``` and reboot to get the brightness working properly. Just that the keys are reversed. I don't think that is a major problem.

---

### Post by peepingtom on 2010-02-09
o  edit: sry, bad advice :D

---

### Post by Cauda_Draconis on 2010-03-26
It's not working on my Toshiba Satellite A100, either. Changing display brightness never has. I tried eOgas' grub fix, but all that did was get the computer to recognize that it can't change the brightness (the tooltip on the brightness applet in the panel says "Cannot get laptop panel brightness").

---

### Post by filipejps on 2010-04-09
Same problem here after changing /etc/default/grub:

"Cannot get laptop panel brightness"

I've a Toshiba Satellite T130

---

### Post by squee on 2010-04-29
> **filipejps said:**
> Same problem here after changing /etc/default/grub:

"Cannot get laptop panel brightness"

I've a Toshiba Satellite T130


I have to bump this, sorry.

Same problem even with the newest updates. Also running a Toshiba t130.

---

### Post by Ganda1f on 2010-05-03
I upgraded from jaunty to karmic on Acer 4736, and the brightness control no longer works! The fix that was working on jaunty is also not working. I have tried other options mentioned here too, (except installing 64-bit ubuntu) and still brightness control does not work....

---

### Post by squee on 2010-06-22
BUMP

MODS this is still not solved for 10.04

Should a new thread be created or this one just edited?

---

### Post by jabbermacy on 2010-07-08
I don't even HAVE my T135 yet but I'm going to bump this anyway! The screen brightness issue unsolved means I can't use Linux on this laptop! BIG BUMMER.  Any new information on the problem or fixes??:(

---

### Post by larmoe01 on 2010-10-22
Applying "nomodeset acpi_backlight=vendor" to grub, will crash Xorg, since the most recent version of Xorg doesn’t support this string. 
For the T130 I found this workaround, witch will dim the screen brightness and extend the battery time. This workaround will not allow you to adjust the brightness with the fn keys. 

You can manually adjust the brightness with setpci:
```
sudo setpci -s 00:02.0 F4.B=#
```
were # is a value from 0 - 99. 

This can be used in ACPI events to control the brightness according to the state of the AC adapter. 
```
sudo touch /etc/acpi/brightness.sh
sudo chmod 755 /etc/acpi/brightness.sh
sudo nano -w /etc/acpi/brightness.sh 
```
Copy paste the lines below to brightness.sh:
```
#!/bin/sh

if [ "`sed -e "s/.[^ ]* *//" /proc/acpi/ac_adapter/ACAD/state`" = "on-line" ]
        then
                logger "ACPI: AC adapter is on-line, brightness up..."
                sudo setpci -s 00:02.0 F4.B=99

        else
                logger "ACPI: AC adapter is off-line, brightness down..."
                sudo setpci -s 00:02.0 F4.B=40

fi

```
Now we have to edit the events to trigger brightness.sh. As root type
```
echo action=/etc/acpi/brightness.sh >> /etc/acpi/events/battery
echo action=/etc/acpi/brightness.sh >> /etc/acpi/events/ac
restart acpid
```
This will dim the brightness when laptop goes on battery, an brighten the screen when the AC adapter is connected. 

Reference: [http://www.gentoo-wiki.info/ACPI/Configuration]("http://www.gentoo-wiki.info/ACPI/Configuration")

---

### Post by cnu1 on 2010-10-26
> **slakkie said:**
> You should edit the following section:

```

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

```to

```

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash nomodeset acpi_backlight=vendor

```And run grub-update as root:

```

sudo grub-update

```That should fix it.

Firstly a big thanks, it worked for me.  Just for others who may still be having the problem. The key word is "nomodeset"


[LIST=1]
[*]my default_grub line looks like this:  [COLOR=#000099][FONT=Arial]_GRUB_CMDLINE_LINUX_DEFAULT="quiet acpi_osi=Linux nomodeset acpi_backlight=vendor splash"_[/FONT][/COLOR]
[*]Then I ran "sudo update-grub" and "sudo update-grub2"
[*]Finally restart.  For me I was able to see the slidebar in the power management preferences
[/LIST]

---

### Post by Naguz on 2010-11-22
Nomodeset isn't an option for many, since any half-recent intel graphics driver requires it. (I'm guessing you have one without intel graphics unless the intel drivers weren't updated with Jaunty - In which case they are very old.)

I'm getting kind of dired of the manual setcpi thingy, Different location needs different backlight.

---

### Post by Pataforce8 on 2010-12-28
Hey all
I'm having the same problem, unfortunately using the nomodeset fix crashes my xserver and the setpci fix does not change the brightness for me. Any help?

---

### Post by deibhaid on 2011-01-19
Hey guys, 

I took some of the previous bits of advice that I found around and I made scripts that I bound to the fn+brightnessup and fn+brightnessdown keys.  I used the Compizconfig settings manager's commands section to bind each script to the brightness keys.

I am sure the bash scripts aren't perfect and could be easily modified to be more efficient, bit this works great for my purposes.  Note: for this to work, one must run setpci with root permissions.  chmod 4755 works, but of course it creates quite a potential security hole.  perhaps adding the program to the sudoers list with your username would be acceptable.

**************************************************
brightness_up.sh
**************************************************
#!/bin/sh
test -f /tmp/brightness || echo 99 > /tmp/brightness
brightness=$((`cat /tmp/brightness`+5))
if [ $brightness -gt 99 ] ; then
  brightness=99;
fi
echo $brightness > /tmp/brightness
export brightness
setpci -s 00:02.0 F4.B=`cat /tmp/brightness`



**************************************************
brightness_down.sh
**************************************************
#!/bin/sh
test -f /tmp/brightness || echo 6 > /tmp/brightness
brightness=$((`cat /tmp/brightness`-5))
if [ $brightness -lt 0 ] ; then
  brightness=0;
fi
echo $brightness > /tmp/brightness
export brightness
setpci -s 00:02.0 F4.B=`cat /tmp/brightness`

---

### Post by deibhaid on 2011-03-07
**************************************************
brightness_up.sh
**************************************************
#!/bin/sh
test -f /tmp/dim || echo ff > /tmp/dim
brightness=$((`cat /tmp/dim`))
if [ $(grep -c ff /tmp/dim) -eq 1 ] ; then
                setpci -s 00:02.0 F4.B=ff;exit;
        elif [ $brightness -gt 99 ] ; then
                brightness=ff;
                else brightness=$((`cat /tmp/dim`+5));
fi
export brightness
if [ $brightness -eq 100 ] ; then
        brightness=ff;
fi
echo $brightness > /tmp/dim
setpci -s 00:02.0 F4.B=`cat /tmp/dim`

**************************************************
brightness_down.sh
**************************************************
#!/bin/sh
test -f /tmp/dim || echo 6 > /tmp/dim
brightness=$((`cat /tmp/dim`-5))
if [ $(grep -c ff /tmp/dim) -eq 1 ] ; then
        brightness=95;
        elif [ $brightness -lt 0 ] ; then
        brightness=0;

fi
echo $brightness > /tmp/dim
export brightness
setpci -s 00:02.0 F4.B=`cat /tmp/dim`

---

### Post by deibhaid on 2011-03-07
It looks like a rather ugly script, so if someone has suggestions or modifications, feel free to add them!

---

### Post by squee on 2011-04-13
running 11.04b and by default this still isnt resolved. I'd prefer not to use a script like before. The function button works fine as always, and the notification comes up indicating that the screen is brighter or dimmer but it doesnt change.

Any ideas? (also can a mod unmark this a solved - it is not.)

---

### Post by wgarciamachmar on 2011-09-13
Same problem here. Did the script. Nothing changes, though the indicator shows up and hot keys are working.

---

### Post by squee on 2011-10-08
Months later I have found a partial solution. 

The below tutorial changes the brightness depending on the state of the AC charger. It works perfectly for me (though I modified the script so the AC brightness was at max FF rather than 99 value)
[http://forums.linuxmint.com/viewtopic.php?f=42&t=63446](http://forums.linuxmint.com/viewtopic.php?f=42&t=63446)
[http://ubuntuforums.org/showpost.php?p=10011340&postcount=26](http://ubuntuforums.org/showpost.php?p=10011340&postcount=26)

also for manual changing outside of the above script, one can use


```
sudo setpci -s 00:02.0 F4.B=FF 
```   Where FF can be replaced with any value from 00 (black) to FF max bright using hexadecimal notation.

Hope this helps!

---

### Post by RSA-2010 on 2011-11-06
I had tried getting this to work on a few occasions previously, even to the point of getting into the deeper innards here:

[https://wiki.ubuntu.com/Kernel/Debugging/Backlight](https://wiki.ubuntu.com/Kernel/Debugging/Backlight)

 . . . but all to no avail . . . I had simply gotten used to having a full-on backlight and the related crappier battery life, which was an everpresent reminder of things not being perfect.   

However, in Kubuntu 11.10 (upgraded from 11.04 and possibly from 10.10 further back) on a Toshiba Satellite T135-S1310, adding "nomodeset acpi_backlight=vendor" to the GRUB_CMDLINE_LINUX_DEFAULT line did not work (as expected, and as noted previously in the thread, nomodeset just freaked everything out), but removing nomodeset and just leaving the vendor part has at last worked perfectly.  The Fn keys work and it can all be changed in the software settings.

Specifically, my line looks like this:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor"

And my my, what an amazing change!   :D

I don't know of any other special events which might've occurred, so if others try this and have an issue please let me know.

---

### Post by ccurry21 on 2011-12-06
[RSA-2010]("http://ubuntuforums.org/member.php?u=1242721")'s solution does not work for me. After adding this line and rebooting, brightness hotkeys work as before until I suspend, but when awakening the machine the backlight remains completely dimmed.

---

### Post by zampes on 2011-12-19
Hi there,
I'm in the same fix right now, with a brand new Toshiba L755-s5242GR. Has anyone found anything that would allow one to dim the backlight? I'm going blind here. I've tried all the fixes mentioned here and nothing works; I've tried some other things myself, but still, no fix.

---

### Post by RSA-2010 on 2012-05-05
As it happens, I developed an issue where the laptop wouldn't go to sleep.   The backlight=vendor thing is the cause.

Now in Kubuntu 12.04, removing the backlight line returns the unit to its old behavior (sleeps, but always has full brightness), so the problem is **not really solved**.   

Putting that line in produces brightness change capability, but if I have to walk away from the laptop with the lid open it will sit there like an idiot until the battery drains completely.

Closing the lid can produce the desired sleep *sometimes*, and of course manually ordering to sleep via the "Leave" widget or similar will work, but it will wake up and drain itself if the battery gets low (which is just stellar behavior when it's in a case, lemme tell ya).

So, basically, it's a compromise right now between being blind in a dark room or letting the laptop drain itself and lose work if I have to run fast and don't get a chance to close the lid and confirm it actually decided to sleep this time.

---

### Post by nomnex on 2012-05-05
> **RSA-2010 said:**
> 
So, basically, it's a compromise right now between being blind in a dark room or letting the laptop drain itself and lose work if I have to run fast and don't get a chance to close the lid and confirm it actually decided to sleep this time.

If you need the ACPI feature on your notebook, you should still be able to set a default brightness when you enter the BIOS setting. Try that: enter a TTY console, see if the keys work, or when you boot: enter the BIOS menu (usually ALT+F2) and try the keys.

---

### Post by RSA-2010 on 2012-05-06
Aha, let me issue a correction, now.   The problem is indeed resolved in 12.04.

I shall now uselessly provide the entire tale:

Basically, my 12.04 upgrade didn't work properly, failing out initially due to a download problem.   I restarted the upgrade later and it seemed to work mostly okay, but I did show a few errors (mostly things already being installed and configured, which I presumed was not anything to worry about).

But, I did still have an issue with a lot of widgets in my panel not being found, so I attempted to sudo apt-get install kdeplasma-addons, but that wouldn't work, so I had to do sudo apt-get -f install . . . which seemed to resolve the remaining flaws in 12.04, I thought.

It was under that state that I posted last, after having done some testing with the acpi_backlight=vendor setting.  But it didn't work, as noted, so I put it back to the way it was (with vendor, so I had brightness control).

Today, however, I was informed that I had 4 security updates and 941 program updates, which seemed rather odd to me given the presumably-successful upgrade.   So I attempted the updates but they failed three times (freezing in mid-update), requiring sudo dpkg --configure -a to clear it each time and start anew.

Now, finally, I believed 12.04's update to be complete.  I had a new Grub2 entry indicating a new kernel and all, which had been the same before.   But then I kept having a weird issue where my laptop would power itself off after like a minute sometimes (when not watching a video).   I could wake it up (so it was sleeping), but it was annoying, and seemed to indicate something was amiss.

Then it finally hit me . . . during the testing, I'd set it to go to sleep after a minute when on battery power.   It wasn't a new problem . . . the bloody thing finally was working!

:guitar:

So, apparently the new kernel with 12.04 provides some assistance in that regard, though for the record I am still using acpi_backlight=vendor.

If anyone is having issues still, please advise.  I'll monitor the thread and we can go over any settings.  I'm no expert, but it is working on mine, so there ya go.

---

### Post by chellrose on 2012-05-07
At least for the (presumably) minority of us who are using Trinity KDE, this is still an issue.  I'm running 10.10 Maverick, which is apparently the newest version of Trinity.  (Anyone else using 10.10 but one of the "standard" desktops like Unity or KDE4 having this issue?  Just curious whether it's a Trinity thing or a 10.10 thing.)

Anyhow, a question.  A brief glance at the old responses reveals that the acpi_backlight=vendor line is supposed to go in /etc/default/grub.  But IIRC, we don't edit /etc/default/grub directly under grub 2.  I may have missed something, but does anyone know how to do the equivalent in grub 2?

Thanks.

---

