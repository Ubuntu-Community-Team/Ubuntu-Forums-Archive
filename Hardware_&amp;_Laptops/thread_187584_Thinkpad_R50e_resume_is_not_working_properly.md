---
title: "Thinkpad R50e: resume is not working properly"
date: 2006-06-03
forum: Hardware &amp; Laptops
---

### Post by splitsch on 2006-06-03
Hello everyone!
I have a problem with my tihnkpad: resume is not working properly after a sleep.
Here is my sleep.sh script:
```
#!/bin/bash

/bin/sync

/sbin/rmmod uhci-hcd
/sbin/rmmod ehci-hcd

/usr/bin/chvt 1

cat /proc/bus/pci/00/02.0 > /var/cache/video.config

echo -n mem > /sys/power/state

cat /var/cache/video.config > /proc/bus/pci/00/02.0

rm -rf /var/cache/video.config

/usr/bin/chvt 7

/sbin/modprobe uhci-hcd
/sbin/modprobe ehci-hcd
```
With this one, it works 3/5 times, but randomly wake up strangly:
here are some printscreen:
[http://img159.imageshack.us/img159/8617/capture20bd.png](http://img159.imageshack.us/img159/8617/capture20bd.png)
[http://img214.imageshack.us/img214/5361/capture38xy.png](http://img214.imageshack.us/img214/5361/capture38xy.png)

I tried another script, found here:
[http://www.thinkwiki.org/wiki/Installing_Ubuntu_on_a_ThinkPad_R50e#Standby.2C_Sleep_and_Hibernation](http://www.thinkwiki.org/wiki/Installing_Ubuntu_on_a_ThinkPad_R50e#Standby.2C_Sleep_and_Hibernation)
```
# change to console 1
  FGCONSOLE=`fgconsole`
  chvt 6

  # safe video state
  cat /proc/bus/pci/00/02.0 > /tmp/video_state

  # sync filesystem
  sync

  # sync hardware clock with system time
  hwclock --systohc

  # go to sleep
  echo -n 3 > /proc/acpi/sleep

  # waking up
  # restore system clock
  hwclock --hctosys

  # restore video state
  cat /tmp/video_state > /proc/bus/pci/00/02.0

  # change back to X
  chvt $FGCONSOLE

  # clean up behind us
  rm /tmp/video_state
```

I have to say that I did everything proposed in the french forum and here:
[https://launchpad.net/distros/ubuntu/+source/acpi-support/+bug/40621](https://launchpad.net/distros/ubuntu/+source/acpi-support/+bug/40621)

I use Klaptop-sleep-trigger, or even when closing the lid or trigger manually the sleep.sh script: it works, but not all the time !
I tried kpowersave: not working at all! even hibernate does'nt work!

Do you have any clue, or track I could follow to make it work?
Could you explain me what those script do, so I could try to make them better.

Thank you!

Splitsch

ps: My english sucks, but I'm Belgian: French-speaker :)

---

### Post by lzap on 2006-06-04
Turn off DRI.

---

### Post by l.tambiah on 2006-06-04
Don't know if you have fixed it yet, but just to let you know I also have an IBM Thinkpad R50e and I used the code from the Thinkpad wiki as you did, and it worked  great. 

I still am not able to get hibernate to work as of yet though, but only a minor issue in my regard.

I added the hibernate issue to bugzilla you can see:- [bug47508]("https://launchpad.net/distros/ubuntu/+bug/47508")

No doubt someone will come up with a fix soon ;-)... 

Regards

L. Tambiah

---

### Post by splitsch on 2006-06-05
Hello, Could copy-paste your sleep.sh.
Mine is so modified! But it works fine, now, but I'd like to give it a try again!

Thanks!

---

### Post by lzap on 2006-06-05
Please paste, AFAIK on ThinkPad you should not have framebuffer support compiled in the kernel. Resume doesnt work then. IMHO you cant get it working by using the default Ubuntu kernel...

So what kernel do you use?

---

### Post by lzap on 2006-06-05
Would be nice to have something at [https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsIBM](https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsIBM)

---

### Post by l.tambiah on 2006-06-05
[quote=splitsch]Hello, Could copy-paste your sleep.sh.
Mine is so modified! But it works fine, now, but I'd like to give it a try again!

Thanks![/quote] 
Sure...The sleep.sh code is below:-

```


#!/bin/bash

# change to console 1
FGCONSOLE=`fgconsole`
chvt 6


 # safe video state
cat /proc/bus/pci/00/02.0 > /tmp/video_state


 # sync filesystem
sync


 # sync hardware clock with system time
hwclock --systohc


 # go to sleep
echo -n 3 > /proc/acpi/sleep


 # waking up
# restore system clock
hwclock --hctosys


 # restore video state
cat /tmp/video_state > /proc/bus/pci/00/02.0


 # change back to X
chvt $FGCONSOLE


 # clean up behind us
rm /tmp/video_state


``` 

Hope this helps...

---

### Post by splitsch on 2006-06-05
Hello!
I add VBE parameter in Xorg.cong, under the "device" sectoin:
```

Section "Device"
	Identifier	"Intel Corporation 82852/855GM Integrated Graphics Device"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	Option   "VBERestore"  "true"
EndSection

```
And both sleep.sh script works

> #!/bin/bash

/bin/sync

/sbin/rmmod uhci-hcd
/sbin/rmmod ehci-hcd

/usr/bin/chvt 1

cat /proc/bus/pci/00/02.0 > /var/cache/video.config

echo -n mem > /sys/power/state

cat /var/cache/video.config > /proc/bus/pci/00/02.0

rm -rf /var/cache/video.config

/usr/bin/chvt 7

/sbin/modprobe uhci-hcd
/sbin/modprobe ehci-hcd

and 

> 
# change to console 1
  FGCONSOLE=`fgconsole`
  chvt 6

  # safe video state
  cat /proc/bus/pci/00/02.0 > /tmp/video_state

  # sync filesystem
  sync

  # sync hardware clock with system time
  hwclock --systohc

  # go to sleep
  echo -n 3 > /proc/acpi/sleep

  # waking up
  # restore system clock
  hwclock --hctosys

  # restore video state
  cat /tmp/video_state > /proc/bus/pci/00/02.0

  # change back to X
  chvt $FGCONSOLE

  # clean up behind us
  rm /tmp/video_state

I'm using klaptop, not kpowersave and the lib powersave !
I prefer Kpowersave (more cumoisation!) but sleeping doesn't work, since it doesn't use sleep.sh at all!
I must say that the power drain is terrible!
Even when it sleeps, it use a lot (a lot!!) of power...

As we say it in french: "ça fait avancer le chmilblick" ;)...
We'll get things working properly, somedays, I'm sure!
If someone can get kpowersave working (ith sleep) properly on a tp R50e, that would be great !

Bye Bye!

---

### Post by splitsch on 2006-06-05
I must add, concerning your hibernate problem that my hibernante.sh script is like this:

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
echo -n "disk" >/sys/power/state

$LAPTOP_MODE stop

. /etc/acpi/resume.sh

```
I have no problem with it. I use Kubuntu dapper, fresh install on a tp r50e
If it can helps...

---

### Post by l.tambiah on 2006-06-06
Strange I have the same code (which is the default) and I mine does not work. Linux.com have an article today to provide a better insight.[URL="http://enterprise.linux.com/enterprise/06/05/24/1716222.shtml?tid=121&tid=23"]

How to suspend or hibernate a laptop on linux[/URL]

---

