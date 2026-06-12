---
title: "ACPI on a Inspiron 8600 with Hoary"
date: 2005-03-27
forum: Hardware &amp; Laptops
---

### Post by blawson327 on 2005-03-27
I found out my problem with the my laptop not resuming from standby is due to the nvidia drivers. I can use the nv drivers and it works fine as far as suspending goes, but 2 new problems are introduced:

1) My screen will no longer blank completely with the nv drivers

2) the nv drivers seem extremely slow,  <300fps in glxgears, nvidia drivers gave ~3000fps


Has anyone had any luck with the Nvidia drivers and suspending? I tried both ways of installing them, with synaptic, and building my own from nvidia's page, both yeild the same results with suspend not working.


I really would appreciate any help with this problem. Thanks in advance

Ben

---

### Post by subzero on 2005-03-27
Hi,

I'd just like to tell, that I'm also looking for a solution to this problem. I'm also on an Inspiron 8600, however, mine is with an ATI-card.

CP from my /var/log/acpid is:
[Mon Mar 28 03:01:03 2005] starting up
[Mon Mar 28 03:01:04 2005] 21 rules loaded
[Mon Mar 28 03:01:13 2005] received event "battery BAT0 00000080 00000001"
[Mon Mar 28 03:01:13 2005] executing action "/etc/acpi/power.sh"
[Mon Mar 28 03:01:13 2005] BEGIN HANDLER MESSAGES
[Mon Mar 28 03:01:13 2005] END HANDLER MESSAGES
[Mon Mar 28 03:01:13 2005] action exited with status 0
[Mon Mar 28 03:01:13 2005] completed event "battery BAT0 00000080 00000001"
[Mon Mar 28 03:01:48 2005] client connected from 8181[1000:1000]
[Mon Mar 28 03:01:48 2005] 1 client rule loaded

My /etc/acpi/powerbtn.sh script is like this:
```
#!/bin/sh
# /etc/acpi/powerbtn.sh
# suspend to ram and come back

#save the console
CONSOLE=`fgconsole`
chvt 12
VBESTATE=`tempfile`
/usr/sbin/vbestate save >$VBESTATE;

# lock the powerbutton, so pressing it once starts the suspend,
# and pressing it again to come back doesn't start this script all
# over again.
LOCK_FILE=/var/lock/powerbtn.lock

get_lock () {
        dotlockfile -p -l -r 0 $LOCK_FILE
        [ $? -ne 0 ] && return 1
        return 0
}

release_lock () {
        [ $$ -eq `cat $LOCK_FILE` ] || exit 1
        dotlockfile -u $LOCK_FILE
}

trap "" 2 3 15
get_lock || exit 1

#stop the acpi daemon ... gross, but it's the easiest way
/etc/init.d/acpid stop >/dev/null 2>&1

# shut the backlight off
dpms off

#take down the network and unload the usb moduels
ifdown eth0
modprobe -r ehci_hcd
modprobe -r usbhid
modprobe -r uhci_hcd
modprobe -r ohci1394

# suspend to ram
echo "mem" > /sys/power/state

#reload the display module, mine is the intel i830
modprobe fglrx

# use that video post program and restore the state of the adapter
/usr/sbin/vm86_video_post
/usr/sbin/vbestate restore <$VBESTATE
rm $VBESTATE

# reload the usb modules, network, set the time
# and turn the backlight back on
modprobe ehci_hcd
modprobe usbhid
modprobe uhci_hcd
modprobe usbhid
modprobe uhci_hcd
modprobe ohci1394
ifup eth0
hwclock --hctosys
/usr/sbin/dpms on

# go back to the console
chvt $CONSOLE;
#chvt 12;
#chvt $CONSOLE;

# Other half of the hideous hack
/etc/init.d/acpid start >/dev/null 2>&1

# done
release_lock
```

---

### Post by blawson327 on 2005-03-28
I have noticed 2 things. My APCID log is the same whether I do a clean reboot or a Suspend/Forced reboot, so that appears to not be a problem. 
A more important thing I noticed is that if X is NOT running and I run the suspend script, it will resume perfectly. 

If anyone would like to see any other logs I have let me know, as I do not have a clue as to what I am looking for in any of them. 

SubZero: see if yours will resume from console only, as mine does

---

### Post by Polymira on 2005-03-29
I too have an inspiron 8600 (with ati), and from the hours of research and 10's of distro's i've tried ... i have come to the conclusion that suspend / hibernate don't work ... some have gotten them too .. if you would like to see [http://www.linux-laptop.net/](http://www.linux-laptop.net/)

---

### Post by subzero on 2005-03-29
Hi,

I've managed to get my suspend-to-ram working. It seems that the fglrx driver from ATI is what causes the trouble. Now my problem is, that I cannot get DRI enabled with the MESA driver.

---

### Post by blawson327 on 2005-03-31
well going on subzero's fix, I uninstalled the nvidia drivers and changed them back to the nv drivers. This allows suspend work correctly. Although this introduced 3 new problems:

1) with the nv drivers the screen will no longer blank out totally when the lid is closed

2) on resume from suspend I can no longer "tap" my touchpad for clicking abilities. I read that you can unload the USB modules and that should fix it, but I am unsure how to do that. I may need to recompile the kernel with USB support in modules if they are not already? And I havent been able to recompile the kernels, I have never done it before so I am probably doing it wrong, or dont have something installed that needs to be


3) A problem with the nv drivers is that the colors dont blend as nice, the default ubuntu background screen has noticeable lines where the color goes from dark to light of the same color, kind of like its at a low color depth. can this be increased if this is the problem? Also the performance is terrible with the nv drivers

---

