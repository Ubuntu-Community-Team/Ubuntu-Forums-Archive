---
title: "Feisty on a Thinkpad A30 - tips and a couple of issues"
date: 2007-06-21
forum: Hardware &amp; Laptops
---

### Post by tessuraea on 2007-06-21
I'm a not-quite-total newb.  I ran Dapper on my T22, but never played with the command line much.  There's a lot of quite basic stuff I don't know how to do, but I'm learning.  Now I have an A30, which is running Ubuntu Feisty and doing it quite well.  It can handle Beryl no problem, which I found surprising.  

A few things for other A30 users:

To install Beryl, I just used synaptic.  There are a dozen install guides for thinkpads; I didn't use any of them.  The default drivers worked just fine.  :)

Many, many people will tell you, when your power control settings aren't working, to disable ACPI and enable APM.  I don't think it's a good idea--the A30 uses ACPI just fine, and disabling it will make fan control difficult (see below).  It's important to add "acpi = force" to your kernel boot commands, though.  Otherwise linux assumes such an old laptop can't use ACPI.  This will allow your fn+whatever keys to work and make suspend mostly work.

ibm_acpi is your friend, and is included in the latest kernel.  Don't spend an hour trying to figure out how to get it.  :)

My fan never turned on--this is a known conflict.  I used [thinkwiki's fan control script ]("http://http://www.thinkwiki.org/wiki/ACPI_fan_control_script")and figured out how to get it into the startup sequence.  It's working, as far as I can tell.  The fan's on, at least.  I was getting worried. 

The on-board wireless works perfectly.  :)

Issues I haven't solved (and that I could really use some help with):

1.  When I soft reboot, the machine seems to shut down properly but then does not restart.  There's some hard drive activity but the monitor stays blank.  I have to hold down the button to power down and then turn it back on.  Not a huge problem, just trying to figure it out.

2.  No network support after I suspend/resume successfully.  I can re-enable it by telling network manager to look for my network manually.  EDIT:  I uncommented most of the things in /etc/network/interfaces (everything but lo was commented out) and now if I'm willing to wait about a minute after resuming network manager eventually catches on.

3.  Suspend-to-ram should work from the fn+f3 key combo, the menu, and the lid close.  fn+f3 works; the gnome menu works.  The lid close does not; the laptop appears to suspend properly (blinking sleep light, then steady) but does not resume when the lid is raised.  At that point, nothing can wake it up and I have to hold down the power button to reset.  EDIT:  I just got this behavior with a command-line suspend, and then tried again with the lid and had it resume perfectly.  So I guess it just doesn't always resume?  It looks like it's going to; the screen turns back on, but blank.

4.  Suspend-to-disk is a hit-or-miss sort of thing.  It hibernates, it just doesn't always resume.  I'm less concerned about this; I like the feature, but if I have to pick one, I'm more interested in sleep mode.

I would really like to be able to close the lid and have the thing go to sleep, then wake up when I open it again.  :)

I ran /etc/acpi/sleep.sh force and got this output (successful suspend/resume except the network missing):
> ifdown: interface eth0 not configured
ifdown: interface eth1 not configured
 * Shutting down ALSA...                                                 [ OK ] 
Function not supported
Function not supported
Ignoring unknown interface eth0=eth0.
Ignoring unknown interface eth1=eth1.
 * Setting up ALSA...                                                    [ OK ] 
grep: /proc/acpi/fan/*/state: No such file or directory
FATAL: Module acpi_sbs not found.
FATAL: Module acpi_sbs not found.


I don't know why it's having trouble with eth0 and eth1, and that grep: /proc... call is looking in the wrong place for my fan controls, I think?

I don't know why the lid suspend is different, either.  I really do want to learn this stuff, so any help that includes explanations of where to find the relevant files and how it all fits together would be very welcome!  I've done a lot of searching online without much luck.

Thank you!

---

### Post by mfichifichi on 2007-06-21
I've been leaving the lid open on mine for months (a latitude), after finally getting it to suspend on closing the lid it turns out that after a while it can't be woke back up and you have to long hold the pwr button down.  I seem to remember it all working with Dapper, but not Feisty. I added the 'acpi=force' just now and rebooted, but haven't had time to test if it makes the suspend work right. Not holding my breath since you're still getting that. One problem might be that I followed a tweak of some config files about relinking a sleep script to a suspend one or vice versa and now I can't remember what it was like initially... I changed some other stuff too, edited a config file and this was all months ago. :o
The Beryl window fx are nice and seem to work with the i830 chip but I'm not getting a cube or anything (I think I would have to have a mouse plugged up for that anyway), I've been wondering if it is because I'm not really running the GLX xserver and if if it would work ok with this chip if I were. Hoping to look into that tonight if I don't get distracted. I'd like to see what the glx is all about, there's a 3d java engine I have to get installed and I'd like to at least know how in case I have problems, that I might switch the server and find the one that works best. This laptop might not be capable enough: there's a 3d modeling program I want to try for building one of those reprap.org 3d plastic printers that I'll hopefully get to try out maybe by next month. :D

---

### Post by mfichifichi on 2007-06-21
With the wireless problem... I had this with mine and managed to fix it: [http://ubuntuforums.org/showthread.php?t=428817](http://ubuntuforums.org/showthread.php?t=428817)
it seems to have worked for somebody else too.

---

### Post by tessuraea on 2007-06-21
Thanks, mfichifichi.  I made the change suggested in that thread:  edited /etc/acpi/resume.d/62-ifup.sh, changed:

for x in $INTERFACES; do
ifup $x &
done

to:
ifdown -a;ifup -a

At this point, it's not waking up from sleep mode very often, but when it does it's got a network connection, at least.  

I just did the manual sleep thing again:  /etc/acpi/sleep.sh force.  Now it's giving me a whole lot of output, most of which doesn't look good.  I wish I understood the suspend/restore process better, which scripts are used and how Ubuntu goes about turning devices off and back on.  I feel like I could sort this stuff out if I did...  but there's such an amazing amount of information, and I'm not having a lot of luck finding an explanation I can understand *and* learn from.  

Here's what I got this time, when I told the laptop to sleep:
```
RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.eth0.pid with pid 5364
removed stale PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:d0:59:83:ac:42
Sending on   LPF/eth0/00:d0:59:83:ac:42
Sending on   Socket/fallback
There is already a pid file /var/run/dhclient.eth1.pid with pid 5600
removed stale PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:20:e0:89:d0:19
Sending on   LPF/eth1/00:20:e0:89:d0:19
Sending on   Socket/fallback
DHCPRELEASE on eth1 to 192.168.3.120 port 67
ifdown: interface eth0:avah not configured
SIOCSIFFLAGS: Cannot assign requested address
 * Shutting down ALSA...                                                 [ OK ] 
Function not supported
Function not supported
There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:d0:59:83:ac:42
Sending on   LPF/eth0/00:d0:59:83:ac:42
Sending on   Socket/fallback
There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:20:e0:89:d0:19
Sending on   LPF/eth1/00:20:e0:89:d0:19
Sending on   Socket/fallback
DHCPRELEASE on eth1 to 192.168.3.120 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:d0:59:83:ac:42
Sending on   LPF/eth0/00:d0:59:83:ac:42
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
RTNETLINK answers: File exists
run-parts: /etc/network/if-up.d/avahi-autoipd exited with return code 2
wlan0: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.
 * Setting up ALSA...                                                    [ OK ] 
grep: /proc/acpi/fan/*/state: No such file or directory
FATAL: Module acpi_sbs not found.
FATAL: Module acpi_sbs not found.

```

---

