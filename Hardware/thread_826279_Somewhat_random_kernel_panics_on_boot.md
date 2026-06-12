---
title: "Somewhat random kernel panics on boot"
date: 2008-06-11
forum: Hardware
---

### Post by jnnnnn on 2008-06-11
Hi all,

I have just purchased an M1330 from Dell, and it's been running Hardy fine until a few days ago (almost directly after the most recent kernel update).  Now, during most boots (9 in 10) it says "Kernel panic - not syncing: Fatal exception in interrupt".  This happens at different points during the boot - sometimes it makes it to the blank brown screen and then the mouse stops working and the power light flashes.  Recently it has been failing at about 6% of the automatic fsck.

For the one in 10 boots where it makes it to the desktop, everything is fine.

Thinking there was a disk problem, I booted up the ubuntu install CD and noticed the same lockup - does this mean it is a hardware issue?  On the second attempt the CD booted successfully and GParted reported no errors on the ext3 partition.

Presumably the fact that the CD failed to boot once indicates that it is not related to the recent kernel update.

I also tried repairing the X config (disabling nvidia-glx-new) but that didn't help.

I have no trouble running Vista Business on the same machine.

I've attached a screenshot of the panic.

Any ideas?

---

### Post by jnnnnn on 2008-06-13
Update:

the kernel options 
acpi=off
acpi=noirq
noapic
don't make any difference.

I have noticed that it always seems to freeze just as the fan gets louder.

Please help, I don't want to use Vista!

---

### Post by ByteJuggler on 2008-06-13
Very much sounds like a hardware issue I'm afraid...  I would send the laptop back to Dell to get it thoroughly stress tested.  It sounds like there might be some sort of heat related cpu issue going by what you say about the fan.

---

### Post by jnnnnn on 2008-06-23
New discovery! Turning the wireless switch off until it has finished booting (and is showing the desktop) causes the problem to occur much less frequently, and it only hangs occasionally when I turn the wireless switch on once the desktop has finished loading.  If it manages to connect (or start connecting) to a network then then risk of hanging has passed.  I think I can live with that.

From other forums it seems as though the previous driver (3***) was fairly unstable.

In case anyone's interested, my wireless driver stats:
iwl4965AGN intel wireless wifi link driver
version 2.6.24-19-generic SMP mod_unload 586

Thanks for your help.

---

### Post by ukripper on 2008-06-23
> **jnnnnn said:**
> New discovery! Turning the wireless switch off until it has finished booting (and is showing the desktop) causes the problem to occur much less frequently, and it only hangs occasionally when I turn the wireless switch on once the desktop has finished loading.  If it manages to connect (or start connecting) to a network then then risk of hanging has passed.  I think I can live with that.

From other forums it seems as though the previous driver (3***) was fairly unstable.

In case anyone's interested, my wireless driver stats:
iwl4965AGN intel wireless wifi link driver
version 2.6.24-19-generic SMP mod_unload 586

Thanks for your help.

can you post outout of the follwoing, lets see which kernel you are using and maybe you can use previous kernel which was working fine:
```
uname -a
```

and do this as well so we know which driver you are using;
> lshw -C network

---

### Post by jnnnnn on 2008-06-25
$ uname -a
Linux jl 2.6.24-19-generic #1 SMP Wed Jun 4 16:35:01 UTC 2008 i686 GNU/Linux

$ sudo lshw -C network 
  *-network               
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wmaster0
       version: 61
       serial: 00:1f:3b:61:26:b3
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl4965 ip=192.168.1.3 latency=0 module=iwl4965 multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: NetLink BCM5906M Fast Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:1d:09:3c:0a:2f
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.86 latency=0 link=no module=tg3 multicast=yes port=twisted pair


To confirm, the laptop only hangs (presumably kernel panicking) if
 - the wireless switch is on during boot (occasionally makes it to desktop/wireless connection password prompt, and after that it's fine)
 - I turn the wireless switch on while the machine is idle (this only occasionally causes a problem, and it's never crashed more than 30 seconds after turning on the wireless switch - it's never crashed after I see the wireless password prompt box)

If I boot to a command prompt, with the wireless switch on there are regular error messages about microcode (and the laptop hangs after a wildly variable amount of time, between 3 seconds and several minutes); these messages stop if I turn the wireless switch off.

---

### Post by ukripper on 2008-06-25
> **jnnnnn said:**
> 

To confirm, the laptop only hangs (presumably kernel panicking) if
 - the wireless switch is on during boot (occasionally makes it to desktop/wireless connection password prompt, and after that it's fine)
 - I turn the wireless switch on while the machine is idle (this only occasionally causes a problem, and it's never crashed more than 30 seconds after turning on the wireless switch - it's never crashed after I see the wireless password prompt box)

If I boot to a command prompt, with the wireless switch on there are regular error messages about microcode (and the laptop hangs after a wildly variable amount of time, between 3 seconds and several minutes); these messages stop if I turn the wireless switch off.
Ok then perhaps we can apply this workaround it will blacklist your driver during boot and just at login screen will re-enable your wireless driver again which will by pass your kernel panick if it is caused by this driver.

Follwo the below instructions :

In terminal type:
```
sudo gedit /etc/modprobe.d/blacklist
```

add  this to the file at bottom - [COLOR="DarkGreen"]**blacklist iwl4965**[/COLOR]
save and exit.

Then open **rc.local **file as following, this will load driver after boot has finished and during login:



```
sudo gedit /etc/rc.local
```

add these two lines **before** [COLOR="Red"]exit 0[/COLOR] - 
[B][COLOR="DarkGreen"] modprobe iwl4965
 /etc/init.d/networking restart[/COLOR][/B]

save and reboot.

You are all done.

Lets go from there to isolate the problem area.

---

### Post by jnnnnn on 2008-06-25
I followed your instructions.

I tried several combinations:
- Booting with the driver enabled by rc.local: froze on second of five boots only (with password dialog on screen).
- Booting with driver enabled by default (not blacklisted): froze on second, 5th, 6th, 7th and 8th boots (of 8), often before the desktop finished loading.
- Booting with driver not enabled at all: no freezes (of 10 boots).

Enabling driver manually by typing second set of commands in to terminal: successful (I only tried this once, but waiting a 5 minutes with the password dialog on screen did not lead to a crash).

The wireless switch has the same effect on failure rates as does disabling the driver.

I noticed that if the keychain password prompt loads (because it wants the wireless network password), the machine sometimes freezes while it is on screen but never after the password is entered. 

So I would say the problem is definitely something to do with this driver... how can I work out exactly what is wrong?

---

### Post by ukripper on 2008-06-25
> **jnnnnn said:**
> I followed your instructions.

I tried several combinations:
- Booting with the driver enabled by rc.local: froze on second of five boots only (with password dialog on screen).
- Booting with driver enabled by default (not blacklisted): froze on second, 5th, 6th, 7th and 8th boots (of 8), often before the desktop finished loading.
- Booting with driver not enabled at all: no freezes (of 10 boots).

Enabling driver manually by typing second set of commands in to terminal: successful (I only tried this once, but waiting a 5 minutes with the password dialog on screen did not lead to a crash).

The wireless switch has the same effect on failure rates as does disabling the driver.

I noticed that if the keychain password prompt loads (because it wants the wireless network password), the machine sometimes freezes while it is on screen but never after the password is entered. 

So I would say the problem is definitely something to do with this driver... how can I work out exactly what is wrong?

check ```
gedit /var/log/messages
``` and look for (EE) are errors or (WW) are warnings.

If the  workaround from my previous post works for you then you can keep it where it is right now and you won't get any freeze up during boot

Try using nm-applet to connect which won't ask you for password I believe. If it does then perhaps we can find a way to disable that too.

---

### Post by jnnnnn on 2008-06-29
I have finally solved this issue to my satisfaction.

There seems to have been a problem with not waiting long enough between inserting the iwl4965 driver into the kernel and starting up the networking.

Looking through /var/log/messages, there are several messages about network devices (bluetooth and wireless card) not being ready.

I wrote a script that executes the commands described earlier,
> 
sudo modprobe iwl4965
sudo /etc/init.d/networking restart

and this script causes a crash every time.  However, typing it in manually hasn't caused any crashes.

For anyone else with this problem, I recommend you follow the steps given above to blacklist the iwl4965 module from loading on boot, _do not_ add it to the /etc/local.rc file, but create a script on your desktop that you can run:

#!/bin/sh
sudo modprobe iwl4965
sleep 10
sudo /etc/init.d/networking restart

It may also work to put a sleep delay in the local.rc; I haven't tried this.

---

### Post by ByteJuggler on 2008-06-29
I think you should file a bug report about this, crashing behaviour is buggy behaviour in one way or another.  At least you have a work-around in the meantime.  Go to [Launchpad]("https://bugs.launchpad.net/ubuntu") to file a bug report.  Please include as much information as possible about your hardware (as well as the output of "sudo lspci") in the report (and read up on how to make a proper report as well please.)

---

### Post by ukripper on 2008-06-30
> **ByteJuggler said:**
> I think you should file a bug report about this, crashing behaviour is buggy behaviour in one way or another.  At least you have a work-around in the meantime.  Go to [Launchpad]("https://bugs.launchpad.net/ubuntu") to file a bug report.  Please include as much information as possible about your hardware (as well as the output of "sudo lspci") in the report (and read up on how to make a proper report as well please.)

I fully agree. As devlopers need to know of such bugs. It would help them resolve further driver bugs relating to this.

---

### Post by jnnnnn on 2008-06-30
I will report this one to the kernel team... I'm just building up a proper set of debug info for them.  I also want to check that it hasn't been fixed upstream.

There are some similar bugs:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/212406](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/212406)
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/194091](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/194091)

Thanks heaps for your help, I would have had no idea without your suggestions.

---

### Post by jnnnnn on 2008-07-08
I have installed the intrepid alpha.  With that (the latest version?) the wireless simply won't connect at all (behaves as if there is never any network signal), which I suppose is an improvement over hardy's random crashing behaviour, but still unfortunately unusable.  Still no problems in vista so I guess I'll be using that until the intel wireless iwl4965 / iwlwifi drivers improve.

---

### Post by ukripper on 2008-07-08
> **jnnnnn said:**
> I have installed the intrepid alpha.  With that (the latest version?) the wireless simply won't connect at all (behaves as if there is never any network signal), which I suppose is an improvement over hardy's random crashing behaviour, but still unfortunately unusable.  Still no problems in vista so I guess I'll be using that until the intel wireless iwl4965 / iwlwifi drivers improve.

You may give Gutsy a go! Updates from package manager for gutsy are supported till April 2009. 

Or you can use this guide in the below link to manually make your drivers work in ibex
[http://ubuntuforums.org/showthread.php?t=493095](http://ubuntuforums.org/showthread.php?t=493095)

Well, i thought that workaround on hardy worked for you. Why are you not using that instead?

---

### Post by jnnnnn on 2008-07-08
> **ukripper said:**
> 
Well, i thought that workaround on hardy worked for you. Why are you not using that instead?

That workaround fixed the boot issue, but the driver also restarts (frequently hanging the machine) on resume from sleep, which I could not live with... I could probably modprobe -r the module on sleep and add it again manually on wake, but it got to be too much of a hassle.

Update: I just found [http://intellinuxwireless.org/?n=fw_error_report](http://intellinuxwireless.org/?n=fw_error_report) , which is a page describing how to debug the driver (including the "Microcode SW Error" that I was seeing occasionally) - I'll reinstall Hardy, get the latest driver from the above site, and submit a bug report to their bug tracker.

Thanks again for your help.

---

### Post by ukripper on 2008-07-08
> **jnnnnn said:**
> That workaround fixed the boot issue, but the driver also restarts (frequently hanging the machine) on resume from sleep, which I could not live with... I could probably modprobe -r the module on sleep and add it again manually on wake, but it got to be too much of a hassle.




you can use following workaround for that, i have created it for iwl3945.

First open file  /etc/default/acpi-support 
```
sudo gedit  /etc/default/acpi-support
```
look for > MODULES_WHITELIST=""
change to
> MODULES_WHITELIST="iwl4965"
save and exit.
Then create a script in /etc/acpi/resume.d
```
#!/bin/bash
#/etc/acpi/resume.d/99-restart-network-manager.sh

/etc/dbus-1/event.d/25NetworkManager restart
/etc/dbus-1/event.d/26NetworkManagerDispatcher restart
```

save and exit.
reboot

then see if your network is back without lockups.
hope it helps.

---

### Post by jnnnnn on 2008-07-08
I think I have properly solved this problem - all that was required was the latest version of the drivers.

On a fresh Hardy install, I installed all the default updates and rebooted three times.  Locked up every time.  I then used a wired network to install the latest (well, almost) version of the iwlwifi driver using the simple instructions at [http://linuxwireless.org/en/users/Download](http://linuxwireless.org/en/users/Download) .  I have now rebooted five times with no lockups so I will take that as the problem being fixed in the latest version of the drivers. 

I'm sorry for taking so long to figure this out; thanks for all your help.  Perhaps the linuxwireless website should be made easier to find? I was only googling for the error messages I was getting, it took me a while to figure out that (a) the wireless was at fault and (b) Hardy doesn't have the latest drivers and (c) it is fairly easy to update them manually.

Yay, my ubuntu works! :D  Thank goodness, I was getting really annoyed by all Vista's disk accessing when the machine is idle.

---

### Post by ukripper on 2008-07-08
Great it worked out for you! There were many options to sort this problem but you have done it one way which is great! That is what i like about GNU/linux ain't one way to go about!:)

---

