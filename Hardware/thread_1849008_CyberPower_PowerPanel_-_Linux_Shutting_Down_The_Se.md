---
title: "CyberPower PowerPanel - Linux Shutting Down The Second I Plug In UPS"
date: 2011-09-23
forum: Hardware
---

### Post by war59312 on 2011-09-23
Hi,

I am trying to get my CyberPower CP1500PFCLCD UPS working.

I am running Ubuntu Server 11.04 x64.

I installed PowerPanel from:

[http://www.cyberpowersystems.com/products/management-software/ppl.html?selectedTabId=resources&imageI=#tab-box](http://www.cyberpowersystems.com/products/management-software/ppl.html?selectedTabId=resources&imageI=#tab-box)

The second I hook up my UPS via the included USB cable Ubuntu says the battery is critical and Linux is now shutting down. :(

The screen goes black a few seconds later and the computer just freezes it seems. It does NOT shutdown. Still running. But now I have to hold in the power button it turn it off.

Now it takes about 10 seconds really after I plug in the computer for all the services to stop, so it seems. So I was able to run sudo pwrstat -status right for the shutdown and this is what I see:

> The UPS information shows as following:

    Properties:
        Model Name................... CP1500PFCLCD
        Firmware Number.............. CRCA102-3I1
        Rating Voltage............... 120 V
        Rating Power................. 900 Watt

    Current UPS status:
        State........................ Normal
        Power Supply by.............. Utility Power
        Utility Voltage.............. 120 V
        Output Voltage............... 120 V
        Battery Capacity............. 100 %
        Remaining Runtime............ 24 min.
        Load......................... 243 Watt(27 %)
        Line Interaction............. None
        Test Result.................. Unknown
        Last Power Event............. NoneAll of that information is correct and as yu can see the battery is just fine and fully charged.

So why is Ubuntu thinking the battery is critical and causing a screwed up shutdown?

For a temp work around I have ran: sudo pwrstat -lowbatt -shutdown off

That way at least it does NOT try to shutdown on me.

Also I am seeing this:

_[[IMG]http://img199.imageshack.us/img199/2606/upsx.th.png[/IMG]]("http://imageshack.us/photo/my-images/199/upsx.png/")_

I then ran this but sadly it makes no difference, and yes I rebooted after doing so:

> gconftool-2 --type bool --set /apps/gnome-power-manager/general/use_time_for_policy falseIf I run upower --dump, I get:
> Device: /org/freedesktop/UPower/devices/ups_hiddev0
  native-path:          /sys/devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.0/usb/hiddev0
  vendor:               CPS
  model:                CP1500PFCLCD
  serial:               CRCA102-3I1
  power supply:         yes
  updated:              Fri Sep 23 15:42:57 2011 (14 seconds ago)
  has history:          yes
  has statistics:       yes
  ups
    present:             yes
    state:               empty
    time to empty:       20.5 minutes
    percentage:          0%

Daemon:
  daemon-version:  0.9.9
  can-suspend:     yes
  can-hibernate    yes
  on-battery:      no
  on-low-battery:  no
  lid-is-closed:   no
  lid-is-present:  no
  is-docked:       noThanks for the help,

Will

---

### Post by war59312 on 2011-10-08
Bump!

Any ideas? Really would like to get this working.

---

### Post by war59312 on 2012-01-01
Well no ideas eh?

Dang their support sucks, as in, never replied.

---

### Post by nealmcb on 2012-02-02
I'm sorry I don't have a direct answer for you - I just ran across your thread while looking for help for my own question.

My experience has been that the best approach, especially for a bug like this, is to search the Ubuntu bug reporting tool - Launchpad.  The section for bugs on Gnome Power Manager is at

 [https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager)

If you don't see something there, the best way to get input and help from developers, is to file a bug report.  

 [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

Another option I find more polished and connected than the forums is AskUbuntu.  See e.g. the question I asked:

 [http://askubuntu.com/questions/100957/how-to-control-ups-via-nut-rather-than-gnome-power-manager](http://askubuntu.com/questions/100957/how-to-control-ups-via-nut-rather-than-gnome-power-manager)

Good luck!

---

### Post by DemocritusJr on 2012-04-29
I had the same issue as you. This occurred when I upgraded to Ubuntu 12.04. I think there is a conflict between powerpanel and gnome-power-manager. I uninstalled powerpanel. It appears that gnome-power-manager recognizes my cyberpower ups just fine on its own. If gnome-power-manager doesn't offer you enough options, I suggest you uninstall or disable it, and then reinstall powerpanel. Hope this helps!

---

### Post by dphurst on 2012-12-18
Normally you don't hook up the UPS while the machine is running.  If you hook up the UPS while the machine is shutdown, then boot, then install the software, that works out just fine.  I just used powerpanel on ubuntu 12.04 to manage the installed Cyberpower 1350AVR.  I do not have the gnome-powermanager installed either.

I used to admin SGI's.  They required the software to be installed prior to booting the system with the UPS hooked up.  A warning in APCC Powerchute software installation manual explained that the interpretation of the serial cable signal pattern by the UPS if the cable was connected while the machine was running was an automatic shutdown of the UPS.  So, I've always hooked the UPS up when the machines were powered down.

---

### Post by tgalati4 on 2012-12-19
Part of that automatic shutdown had to do with the special serial cables required for APC UPS's.  If you use a standard serial cable, you will get an instant shutdown.  If you use APC's expensive, proprietary cable, then it will work fine.  You can build a custom cable--there are plans on the web.

For the OP's UPS with a USB cable, it could be a USB hotplug issue, or it could be how the UPS framework is designed.  If you lose USB communication--shut down immediately, because you are unprotected without the UPS's ability to talk to the computer.  Plugging in the cable could cause such a disruption.  I would think that pulling the USB cable would be a test as well.

---

