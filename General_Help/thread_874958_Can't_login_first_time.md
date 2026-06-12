---
title: "Can't login first time"
date: 2008-07-30
forum: General Help
---

### Post by emakarov on 2008-07-30
Hello,

When I try to log in immediately after boot, the result is similar to pressing Ctrl-Alt-Backspace: the screen goes black and I am thrown back to the login screen. The second time I log in without problems. I also log without problems if at the first login screen after boot, I press Ctrl-Alt-Backspace and then log in. So it seems that restarting X is what matters.

I posted this problem a couple of months ago but did not receive any replies. Is there at least a way to trace what is happening during the first login, and what operation causes the restart of X?

I have Hardy and Gnome.

Thank you,
Evgeny

---

### Post by cdtech on 2008-07-30
Is this a new install or have you had this running for awhile?

The start up scripts are located within the /etc/rcS.d and the shutdown scripts within the /etc/rc0.d directories. Since you have the issue at start up I would almost qaurantee the problem to be within the /etc/rcS.d directory.

It may be possible that one script (symbolic link to the script within /etc/init.d) is causing this erratic behavior. I would start by "sudo mv 'S40nameofscript'" to "K40nameofscript" (changing S to K) for the one you suspect, until you find the culprit.

* Kills K##scripts
* Starts S##scripts 

Hope this helps..........

---

### Post by prshah on 2008-07-30
> **emakarov said:**
> 
Is there at least a way to trace what is happening during the first login, and what operation causes the restart of X?



Sure; take a look at (and post here) your /var/log/Xorg.0.log" file. You should [b,g]zip it before posting.

---

### Post by emakarov on 2008-07-31
> **cdtech said:**
> Is this a new install or have you had this running for awhile?
I upgraded from 7.10 to 8.04 maybe three months ago, and for a while I did not have this problem.

> **cdtech said:**
> I would start by "sudo mv 'S40nameofscript'" to "K40nameofscript" (changing S to K) for the one you suspect, until you find the culprit.
All right... Do you know if I should rename them in ascending or descending order (w.r.t. the number after S)? I mean, which ones are less important? Are there modules that are essential for running the system?

---

### Post by emakarov on 2008-07-31
> **prshah said:**
> Sure; take a look at (and post here) your /var/log/Xorg.0.log" file. You should [b,g]zip it before posting.
Here it is. After the first unsuccessful login I pressed Ctrl-Alt-F1, logged in and copied this file to a different place (I don't know if this was necessary in order not to overwrite it after successful login).

Thanks,
Evgeny

---

### Post by prshah on 2008-07-31
> **emakarov said:**
> Here it is. 

From your log file:
> ```
(II) LoadModule: "type1"
(WW) Warning, couldn't open module type1
(II) UnloadModule: "type1"
(EE) Failed to load module "type1" (module does not exist, 0)

```

I don't have this module mentioned anywhere; is it possibly related to nvidia? Can you check your /etc/X11/xorg.conf for lines similar to ```
LoadModule "type1"
``` and comment them out?

I have a Type1 font entry, but not module load request in either my xorg.conf or my Xorg.0.log file.

---

### Post by pauper on 2008-07-31
Please, try:

```
sudo invoke-rc.d --query gdm start
```

Does it produce any error messages?

Run "dmesg" right after you boot next time and attach output to your post. And
let's see the following:

```
cat /etc/init.d/gdm
cat /etc/modules
runlevel
ls -l /etc/rc?.d

# where ? is your current runlevel, see "man runlevel"
```

Have you added anything to /etc/rcS.d/S??bootmisc.sh script?

Do you see the same behavior when you use Live CD?

> **cdtech said:**
> I would start by "sudo mv 'S40nameofscript'" to "K40nameofscript" 
changing S to K) for the one you suspect, until you find the culprit.

A point to ponder. From man page update-rc.d([noparse]8)[/noparse], line 18 through 21:

> As a rule of thumb, the sequence number of the stop link should 100 minus the
sequence number of the start link; this causes services to be stopped in the
opposite order to that in which they are started. Obviously, therefore, the
default stop sequence number should be 80. Defaulting to 20, as update-rc.d
does, is an old bug that cannot be fixed because of the risk of breaking
things.

Anyway, it's just plain stupid to go about disabling any init script by
guessing. Lots of scripts contain "BEGIN INIT INFO", where description of what
they do is provided; or refer to man pages, if any supplied. [i]Please, read it
before stopping anything.[/i] And never mess with /etc/{rc0.d,rc1.d,rc6.d}
directories.

```
less /usr/share/doc/sysv-rc/README.runlevels.gz
```

---

### Post by emakarov on 2008-08-01
Yes, there was a line
```
Load "type1"
``` in xorg.conf and I commented it out.

```
sudo invoke-rc.d --query gdm start
```
This does not print anything (after I login on second attempt).

I attach the output of dmesg: dmesg1.txt is done after Ctrl-Alt-F1 login after the failed login, and dmesg2.txt is done after the second GUI login.

/etc/init.d/gdm is also attached.

```
~/tmp/login> cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
sbp2
```

```
~/tmp/login> runlevel
N 2
```

```
~/tmp/login> ls -l /etc/rc2.d
total 4
-rw-r--r-- 1 root root 556 2008-04-19 01:05 README
lrwxrwxrwx 1 root root  19 2008-05-08 12:21 S01policykit -> ../init.d/policykit
lrwxrwxrwx 1 root root  17 2007-12-21 14:45 S05vbesave -> ../init.d/vbesave
lrwxrwxrwx 1 root root  15 2007-12-21 14:45 S10acpid -> ../init.d/acpid
lrwxrwxrwx 1 root root  25 2007-12-21 14:45 S10powernowd.early -> ../init.d/powernowd.early
lrwxrwxrwx 1 root root  18 2007-12-21 14:45 S10sysklogd -> ../init.d/sysklogd
lrwxrwxrwx 1 root root  34 2007-12-21 14:45 S10xserver-xorg-input-wacom -> ../init.d/xserver-xorg-input-wacom
lrwxrwxrwx 1 root root  15 2007-12-21 14:45 S11klogd -> ../init.d/klogd
lrwxrwxrwx 1 root root  14 2008-05-08 12:21 S12dbus -> ../init.d/dbus
lrwxrwxrwx 1 root root  17 2008-06-24 17:50 S16openvpn -> ../init.d/openvpn
lrwxrwxrwx 1 root root  22 2007-12-21 14:45 S18avahi-daemon -> ../init.d/avahi-daemon
lrwxrwxrwx 1 root root  16 2007-12-21 14:45 S19cupsys -> ../init.d/cupsys
lrwxrwxrwx 1 root root  14 2007-12-21 14:45 S20apmd -> ../init.d/apmd
lrwxrwxrwx 1 root root  16 2007-12-21 14:45 S20apport -> ../init.d/apport
lrwxrwxrwx 1 root root  17 2008-03-09 22:46 S20hddtemp -> ../init.d/hddtemp
lrwxrwxrwx 1 root root  22 2007-12-21 14:45 S20hotkey-setup -> ../init.d/hotkey-setup
lrwxrwxrwx 1 root root  17 2007-12-21 14:45 S20makedev -> ../init.d/makedev
lrwxrwxrwx 1 root root  23 2008-05-09 22:00 S20nvidia-kernel -> ../init.d/nvidia-kernel
lrwxrwxrwx 1 root root  19 2007-12-21 14:45 S20powernowd -> ../init.d/powernowd
lrwxrwxrwx 1 root root  15 2007-12-21 14:45 S20rsync -> ../init.d/rsync
lrwxrwxrwx 1 root root  23 2007-12-21 21:53 S20smartmontools -> ../init.d/smartmontools
lrwxrwxrwx 1 root root  16 2007-12-21 14:45 S24dhcdbd -> ../init.d/dhcdbd
lrwxrwxrwx 1 root root  13 2008-05-08 12:21 S24hal -> ../init.d/hal
lrwxrwxrwx 1 root root  19 2007-12-21 14:45 S25bluetooth -> ../init.d/bluetooth
lrwxrwxrwx 1 root root  20 2008-05-08 01:35 S25pulseaudio -> ../init.d/pulseaudio
lrwxrwxrwx 1 root root  13 2007-12-21 14:45 S30gdm -> ../init.d/gdm
lrwxrwxrwx 1 root root  13 2008-03-09 22:06 S50ntp -> ../init.d/ntp
lrwxrwxrwx 1 root root  17 2007-12-21 14:45 S89anacron -> ../init.d/anacron
lrwxrwxrwx 1 root root  13 2007-12-21 14:45 S89atd -> ../init.d/atd
lrwxrwxrwx 1 root root  14 2007-12-21 14:45 S89cron -> ../init.d/cron
lrwxrwxrwx 1 root root  17 2007-12-21 14:45 S98usplash -> ../init.d/usplash
lrwxrwxrwx 1 root root  22 2007-12-21 14:45 S99acpi-support -> ../init.d/acpi-support
lrwxrwxrwx 1 root root  21 2007-12-21 14:45 S99laptop-mode -> ../init.d/laptop-mode
lrwxrwxrwx 1 root root  18 2007-12-21 14:45 S99rc.local -> ../init.d/rc.local
lrwxrwxrwx 1 root root  19 2007-12-21 14:45 S99rmnologin -> ../init.d/rmnologin
lrwxrwxrwx 1 root root  24 2007-12-21 14:45 S99stop-readahead -> ../init.d/stop-readahead

```

I have not changed /etc/rcS.d/S80bootmisc.sh

I did add the hard drive spin fix file to /etc/acpi/start.d and other subdirectories in /etc/acpi, but removing it did not help.

```
~/tmp/login> cat 99-hdd-spin-fix.sh
#!/bin/sh
hdparm -B 254 /dev/sda
hdparm -S 0 /dev/sda
```

Finally, I removed
```
Driver         "nvidia"
```
from xorg.conf. I attach it as well. So far nothing solved the problem.

In the meanwhile, thanks for your advices!

Evgeny

---

### Post by pauper on 2008-08-02
I looked through your attachments and haven't found anything revealing yet.
Any changes done to /etc/rc.local?

[list][*]Next time you boot, after GRUB screen, press Alt-F1 or/and Alt-F8 to view
kernel messages. To stop text from scrolling use flow control calls (XON/XOFF):
press Ctrl-s to pause and Ctrl-q to renew (pressing Ctrl-s again might work as
well). Maybe it will spit out some error or warning regarding GDM.
[*]Disable GDM from auto start and load it manually.

```
runlevel
sudo mv /etc/rc2.d/S30gdm /etc/rc2.d/K70gdm
sudo shutdown -r 0
```

Let the system reboot... Press Enter to get to the prompt. Login.

Check for errors. Start X session.

```
sudo invoke-rc.d --query gdm start
sudo invoke-rc.d --force gdm start
```

Later, don't forget to change K70gdm back to S30gdm.
[*]Compare your /etc/rc{2,3,4,5}.d directories. If you find that positions or
status of entries differ, you may try changing default runlevel to 3, 4, or 5.

An example: change to runlevel 3. Make a backup copy of rc-default file.
Change appropriate lines. Overwrite. Reboot.

```
sudo cp /etc/event.d/rc-default{,.bak}
sed -e 's/telinit 2/telinit 3/g' /etc/event.d/rc-default > ~/rc-default
sudo mv ~/rc-default /etc/event.d
sudo shutdown -r 0
```[/list]

P.S. Consider doing a clean installation next time. In my experience any new
release upgrades sometimes tend to break things that used to work before.

---

