---
title: "[Hardy] network disabled (in network manager) when resuming"
date: 2008-06-15
forum: Hardware
---

### Post by rrwo on 2008-06-15
When my laptop (a ThinkPad R61i) resumes from suspend, Network Manager often does not work, claiming that the network is disabled. When I right-click on it, "Enable networking" is unchecked, and "Enable wireless" is missing.  Clicking on Enable networking usually has no effect, and I need to restart my  machine to use the network.

Note that I often get messages that there were problems with suspend or resume, and am also having poblems with USB devices when I resume. (I'm told there's a connection with Network Manager and USB problems, from looking at some bug reports for the latter.)

Can anyone suggest a way to fix this? It's getting frustrating enough that I'm considering switching to another distribution.

---

### Post by Odrodzona-Sarmacja on 2008-06-15
if your /home is on other partition already,
... then just in synaptic manager save all markings into /home/yourdir/markings84.txt. reboot with livecd and reinstall xubuntu 8.4. (fix fstab to automount your stuff, check sudo swapon -s and fix swap partition too if not installed correctly). then load your markings84.txt in synaptic. The problem should be gone.

---

### Post by prshah on 2008-06-15
> **rrwo said:**
> When my laptop (a ThinkPad R61i) resumes from suspend, Network Manager often does not work, claiming that the network is disabled. 

Can anyone suggest a way to fix this? It's getting frustrating enough that I'm considering switching to another distribution.

Can you open a terminal (Applications-Accessories-Terminal), then give the following commands and post the output here. ```

cat /usr/lib/pm-utils/sleep.d/10NetworkManager
ls -l /usr/lib/pm-utils/sleep.d/10NetworkManager

```

---

### Post by prshah on 2008-06-15
> **Odrodzona-Sarmacja said:**
>  (fix fstab to automount your staff, 

:lolflag: I think this is for some other thread; I _like_ the idea of automounting my staff (I'm talking about my office, not... perverts!)

---

### Post by Odrodzona-Sarmacja on 2008-06-15
> **prshah said:**
> :lolflag: I Think This Is For Some Other Thread; I _like_ The Idea Of Automounting My Staff (i'm Talking About My Office, Not... Perverts!)

Lol

---

### Post by rrwo on 2008-06-16
Reinstall? That's a pretty drastic solution. I might as well install a different distro too...

---

### Post by Odrodzona-Sarmacja on 2008-06-16
Well, I be ehem, but i tried emulate this bug... I turned off networking just after reboot to check if i get any freezes in nvidia and xorg with turned off networking without need for rebooting. I found no freezes, but to my suprise after 1 hour, when I tried to reconnect with roaming mode network manager back to internet, it just kept on searching for connection without getting me any connection. I tried the ifup/ifdown, but so long the networking manager works on roaming mode there is issue that I can't reconnect to internet with ifup/ifdown.

Also the only errors I get when booting up xubuntu are network menager warnings.

Also on my xubuntu's the freezes of nvidia and xorg almost vanish when it is not connected to internet.

Also when I get freezes the only errors I get in syslog are kernel messages about networking warnings and network renewing ip (and of course the nvidia-glx-new error one, as opensource do freeze too, but leaves no error message in syslog at all about it).

So I am backing down. I don't think reinstalling xubuntu 8.04, 7.10 or 7.04 will help fix this issue. This is something that just is in these oses. I think this became almost a feature of xubuntu. I just wish it didn't keep on freezing my computer.

---

### Post by prshah on 2008-06-16
> **rrwo said:**
> Reinstall? That's a pretty drastic solution. I might as well install a different distro too...

Errr.. reply to post #3?

If you've decided on a reinstall anyway... then you can ignore this.

---

### Post by rrwo on 2008-06-16
The file exists, is owned by root, and has 755 perms. Nothing unusual.

What should I be looking for in that script? It looks like it's doing the right thing, and it's run according to /var/log/pm-suspend.log

---

### Post by sdennie on 2008-06-16
What wireless card do you have and what is the output of:

```

cat /etc/udev/rules.d/70-persistent-net.rules 

```

---

### Post by transalpler on 2008-06-29
I am having the same Problems with my Notebook here: I upgraded from Gutsy to 8.04 - everything was OK - since the last kernel update I have no more network after resumeing either from suspend or hibernation.
Its an Acer Aspire 3610 - Intel Celeron with intel graphics onboard. 

```

 wolfgang@Transalplers:~$ cat /usr/lib/pm-utils/sleep.d/10NetworkManager
#!/bin/bash

. /usr/lib/pm-utils/functions

suspend_nm() {
    # Tell NetworkManager to shut down networking
    dbus-send --system                         \
        --dest=org.freedesktop.NetworkManager  \
        /org/freedesktop/NetworkManager        \
        org.freedesktop.NetworkManager.sleep
}

resume_nm() {
    # Wake up NetworkManager and make it do a new connection
    dbus-send --system                        \
        --dest=org.freedesktop.NetworkManager \
        /org/freedesktop/NetworkManager       \
        org.freedesktop.NetworkManager.wake
}

case "$1" in
	hibernate|suspend)
		suspend_nm
		;;
	thaw|resume)
		resume_nm
		;;
	*)
		;;
esac

exit $?
wolfgang@Transalplers:~$ 

```

```

wolfgang@Transalplers:~$ ls -l /usr/lib/pm-utils/sleep.d/10NetworkManager 
-rwxr-xr-x 1 root root 675 2008-06-03 12:31 /usr/lib/pm-utils/sleep.d/10NetworkManager
wolfgang@Transalplers:~$ 

```
```

wolfgang@Transalplers:~$ cat /etc/udev/rules.d/70-persistent-net.rules 
# This file was automatically generated by the /lib/udev/write_net_rules
# program, probably run by the persistent-net-generator.rules rules file.
#
# You can modify it, as long as you keep each rule on a single line.

# PCI device 0x14e4:0x4318 (bcm43xx)
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:14:a4:81:73:59", ATTR{type}=="1", NAME="eth0"

# PCI device 0x10ec:0x8139 (8139too)
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:0a:e4:f2:8d:e8", ATTR{type}=="1", NAME="eth1"
wolfgang@Transalplers:~$ 

```

Reinstall ist not a pretty option for me...

---

### Post by prshah on 2008-06-29
> **transalpler said:**
> I am having the same Problems with my Notebook here: I upgraded from Gutsy to 8.04 - everything was OK - 


What are the hardware addresses (MAC) for your network adapters? This will tell: ```
ifconfig | grep -i hwaddr
``` Can you post the output here?

---

### Post by transalpler on 2008-06-29
00:14:a4:81:73:59 is the Wlan Card

00:0a:e4:f2:8d:e8 is Ethernet Card

Just checked that under windows becaus it is not nice to reboot all the time after a break..

When there is no network - I only get an entry for loopback in ifconfig

---

### Post by prshah on 2008-06-30
> **transalpler said:**
> 00:14:a4:81:73:59 is the Wlan Card
00:0a:e4:f2:8d:e8 is Ethernet Card

Fine now, post results of these commands- note that the first one _will_ cut off network access, and the second one _should_ restore it. Basically we are simulating a suspend and thaw to check if the error is at script level or somewhere else.
```

/usr/lib/pm-utils/sleep.d/10NetworkManager suspend

```

now wait 10 seconds and check your network manager icon; it should show overlaid with a small red cross indicated deactivated. Don't click anything there.

If it shows as disabled (small red cross in corner) then networking is being suspended fine. Now let's try a thaw:```

/usr/lib/pm-utils/sleep.d/10NetworkManager thaw
``` Again, wait 10~15 seconds, your connection _should_ be restored back as normal.

If it is not back as normal, then the error lies in this script. ```
dmesg | tail
``` will give more information about this.

If it is back as normal, then the error lies outside this script. Can you hibernate/suspend and restore successfully (except for the network issue)? In that case, perform a hibernate/suspend and then restore and post the contents of ```
sudo /etc/init.d/networking restart
cat /var/log/pm-suspend.log
``` The first command should enable networking again, if it doesn't please copy/paste error messages and logfile to some text file, save it, restart and then post that text file.

---

### Post by transalpler on 2008-06-30
I'm now in the office with no access to my notebook. 
After resuming (with no network) i am not able to reactivate it with sudo /etc/init.d/network restart
I only get something like: "unknown device eth1 ignored" or so...
maybe thats a hint?

---

### Post by prshah on 2008-06-30
> **transalpler said:**
> I'm now in the office with no access to my notebook. 
After resuming (with no network) i am not able to reactivate it with sudo /etc/init.d/network restart
I only get something like: "unknown device eth1 ignored" or so...
maybe thats a hint?

OK, please check the previous post suggestions when you get access to your laptop,

The "unknown device" message _may_ indicate that the modules are not being loaded after resume. Here's how to check: When you have a working network connection, give the command ```
lsmod > before
```

The suspend, wait a few seconds, restore, and give the commands ```
lsmod > after
diff before after
```

and post the results of the "diff" command as mentioned above.

Dont forget to try the commands in the previous post as well!

---

### Post by Odrodzona-Sarmacja on 2008-06-30
> **transalpler said:**
> I'm now in the office with no access to my notebook. 
After resuming (with no network) i am not able to reactivate it with sudo /etc/init.d/network restart
I only get something like: "unknown device eth1 ignored" or so...
maybe thats a hint?

Network-Manager is not fun. It freezes your computer at times. It malfunctions like you just noticed and it is doing something nasty thing to hard drive too, as images of hard drives taken from Ububtu with installed network-manager are like 3 Gb bigger (and network-manager package doesn't even look like 3Gb big program).

Just put in your /etc/network/interfaces
"
auto eth0
iface eth0 inet dhcp
"
then use "sudo ifdown eth0" to shut it down manually and "sudo ifup eth0" to restart it manually. Internet should work now without much problems despite network-manager malfunctioning.

Good luck!

---

### Post by transalpler on 2008-06-30
here we go - i hope i've tested all your advice:
```

wolfgang@Transalplers:~$ # now all OK after fresh reboot
wolfgang@Transalplers:~$ lsmod > before
wolfgang@Transalplers:~$ /usr/lib/pm-utils/sleep.d/10NetworkManager suspend
wolfgang@Transalplers:~$ /usr/lib/pm-utils/sleep.d/10NetworkManager thaw
wolfgang@Transalplers:~$ # network is back and OK
wolfgang@Transalplers:~$ # back after suspend - now no network
wolfgang@Transalplers:~$ sudo /etc/init.d/networking restart
[sudo] password for wolfgang: 
 * Reconfiguring network interfaces...                                                      Ignoring unknown interface eth1=eth1.
                                                                                     [ OK ]
wolfgang@Transalplers:~$ cat /var/lo
local/ lock/  log/   
wolfgang@Transalplers:~$ cat /var/log/pm-suspend.log 
Mon Jun 30 18:57:47 CEST 2008: running suspend hooks.
===== Mon Jun 30 18:57:48 CEST 2008: running hook: /usr/lib/pm-utils/sleep.d/00clear =====
===== Mon Jun 30 18:57:48 CEST 2008: running hook: /usr/lib/pm-utils/sleep.d/05led =====
===== Mon Jun 30 18:57:48 CEST 2008: running hook: /usr/lib/pm-utils/sleep.d/10NetworkManager =====
===== Mon Jun 30 18:57:48 CEST 2008: running hook: /usr/lib/pm-utils/sleep.d/20video =====
kernel.acpi_video_flags = 3
===== Mon Jun 30 18:57:48 CEST 2008: running hook: /usr/lib/pm-utils/sleep.d/49bluetooth =====
===== Mon Jun 30 18:57:48 CEST 2008: running hook: /usr/lib/pm-utils/sleep.d/50modules =====
===== Mon Jun 30 18:57:48 CEST 2008: running hook: /usr/lib/pm-utils/sleep.d/90clock =====
===== Mon Jun 30 18:57:49 CEST 2008: running hook: /usr/lib/pm-utils/sleep.d/94cpufreq =====
===== Mon Jun 30 18:57:49 CEST 2008: running hook: /usr/lib/pm-utils/sleep.d/95led =====
===== Mon Jun 30 18:57:49 CEST 2008: running hook: /usr/lib/pm-utils/sleep.d/99video =====
Mon Jun 30 18:57:49 CEST 2008: done running suspend hooks.
Mon Jun 30 18:57:58 CEST 2008: running resume hooks.
===== Mon Jun 30 18:57:58 CEST 2008: running hook: /usr/lib/pm-utils/sleep.d/99video =====
===== Mon Jun 30 18:57:58 CEST 2008: running hook: /usr/lib/pm-utils/sleep.d/95led =====
===== Mon Jun 30 18:57:58 CEST 2008: running hook: /usr/lib/pm-utils/sleep.d/94cpufreq =====
===== Mon Jun 30 18:57:58 CEST 2008: running hook: /usr/lib/pm-utils/sleep.d/90clock =====
===== Mon Jun 30 18:57:58 CEST 2008: running hook: /usr/lib/pm-utils/sleep.d/50modules =====
 * Reconfiguring network interfaces...
Ignoring unknown interface eth1=eth1.
   ...done.
===== Mon Jun 30 18:57:58 CEST 2008: running hook: /usr/lib/pm-utils/sleep.d/49bluetooth =====
===== Mon Jun 30 18:57:58 CEST 2008: running hook: /usr/lib/pm-utils/sleep.d/20video =====
===== Mon Jun 30 18:57:58 CEST 2008: running hook: /usr/lib/pm-utils/sleep.d/10NetworkManager =====
===== Mon Jun 30 18:57:58 CEST 2008: running hook: /usr/lib/pm-utils/sleep.d/05led =====
===== Mon Jun 30 18:57:58 CEST 2008: running hook: /usr/lib/pm-utils/sleep.d/00clear =====
Mon Jun 30 18:57:58 CEST 2008: done running resume hooks.
wolfgang@Transalplers:~$ lsmod > after
wolfgang@Transalplers:~$ diff before after
2c2,8
< af_packet              23812  2 
---
> b43                   144420  0 
> ssb                    34308  1 b43
> mac80211              165652  1 b43
> cfg80211               15112  1 mac80211
> input_polldev           5896  1 b43
> 8139too                27520  0 
> af_packet              23812  0 
38,41c44
< b43                   144420  0 
< rfkill                  8592  3 rfkill_input,b43
< mac80211              165652  1 b43
< cfg80211               15112  1 mac80211
---
> rfkill                  8592  2 b43,rfkill_input
44d46
< input_polldev           5896  1 b43
56c58
< evdev                  13056  7 
---
> evdev                  13056  6 
88d89
< 8139too                27520  0 
92d92
< ssb                    34308  1 b43
wolfgang@Transalplers:~$ 
```

---

### Post by prshah on 2008-06-30
> **transalpler said:**
> here we go - 
```

wolfgang@Transalplers:~$ lsmod > after
wolfgang@Transalplers:~$ diff before after


```

Apparently I'm not as good at understanding diffs as I thought I was; can you just post both "before" and "after" files?

---

### Post by transalpler on 2008-06-30
here we go:
I had to rename the files to .txt to be accepted by the forum

---

### Post by prshah on 2008-06-30
> **transalpler said:**
> 
```

wolfgang@Transalplers:~$ lsmod > before

[color=blue]===== Mon Jun 30 18:57:58 CEST 2008: running hook: /usr/lib/pm-utils/sleep.d/50modules =====
 * Reconfiguring network interfaces...
Ignoring unknown interface eth1=eth1.
   ...done.
[/color]
wolfgang@Transalplers:~$ lsmod > after
wolfgang@Transalplers:~$ diff before after
wolfgang@Transalplers:~$ 
```

> **transalpler said:**
> here we go:
I had to rename the files to .txt to be accepted by the forum

Ok there's absolutely no difference in the before and after lsmod, so all modules are being loaded successfully.

I notice that the network resume error first occurs in 50modules; the file itself seems to be alright except that the function suspend_modules() returns a value but resume_modules() does not; don't know if that is a problem or not. Maybe some more research...

In the meantime, output of ```
cat /etc/network/interfaces
``` please?

---

### Post by transalpler on 2008-06-30
Here we have /etc/network/interfaces
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback


# The primary network interface
auto eth1
# iface eth1 inet dhcp

```

---

### Post by prshah on 2008-07-01
> **transalpler said:**
> Here we have /etc/network/interfaces
```

# iface eth1 inet dhcp

```

AFAIK, the last line, which is commented out, is _essential_. It describes to the operating system how eth1 is to be handed; inet means it uses TCP/IP. Unless you have commented it out for a specific purpose, your should remove the "#", save it, restart the system, and then try a suspend/restore.

I regret that there is no cut-n-dried solution to your problem and so much experimenting is being done.

---

### Post by transalpler on 2008-07-01
well the # is not from me...
If it is essential - why does it work with normal reboot? 
I'll give it a try in the evening...

---

### Post by transalpler on 2008-07-01
Well without the # a resume after standby works - after some seconds the network gets up...

Will watch this for some time and repost if something still unusal...

---

### Post by atrus on 2008-08-20
If you're using network-manager, it's normal to have no uncommented interfaces in /etc/network/interfaces, as it's supposed to deal with them automatically.

I do occasionally have a problem where NetworkManager freezes on resume, in which case I have to:
[LIST=1]
[*]$ sudo killall NetworkManager
[*]$ sudo /etc/dbus-1/event.d/25NetworkManager restart
[/LIST]

---

### Post by ethanay on 2008-09-11
> **atrus said:**
> If you're using network-manager, it's normal to have no uncommented interfaces in /etc/network/interfaces, as it's supposed to deal with them automatically.

I do occasionally have a problem where NetworkManager freezes on resume, in which case I have to:
[LIST=1]
[*]$ sudo killall NetworkManager
[*]$ sudo /etc/dbus-1/event.d/25NetworkManager restart
[/LIST]

Same symptoms as original poster in Ubuntu [gnome] Hardy w/latest, and the above commands fix it.  It took about 30-45 seconds for network manager to restart -- so keep the terminal open long enough for it to complete the command.  Is this reported as a bug yet?

---

### Post by Denny Johnson on 2008-10-07
Thanks prshah, same problem as others, your post 23 works for me.
Will repost if it turns out to not be a solution.

---

### Post by cryolithic on 2008-10-16
I noticed with my machine on hardy that sometimes a simple kill wouldn't terminate the process and I'd need to kill -9 it, then restart.

get the process id
sudo ps aux | grep NetworkManager 
root     18651  0.1  0.0  30832  2828 ?        Ssl  12:58   0:00 NetworkManager

sudo kill -9 18651

sudo NetworkManager

---

### Post by rrwo on 2009-03-10
Ok, I've narrowed the problem down: if I resume my computer in a different power state, then the network doesn't work. That is, if I suspend my computer while plgged into AC, and resume in battery.

---

