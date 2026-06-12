---
title: "Toshiba L775D-S7305 (AMD A6 3400m) suspend problem"
date: 2012-03-02
forum: Hardware
---

### Post by bbrg548 on 2012-03-02
I am having the same issue described in [this thread]("http://ubuntuforums.org/showthread.php?t=1814914"), however, the OP's solution there does not work for me. I'm starting a new thread because the original is marked "solved" and there hasn't been any activity since November (despite bumping it).

I am running a (very) slightly different system (-S7305 instead of a -S7222, and 11.10 instead of 11.04).
The problem is:
> Suspend to ram freezes the machine in a weird way - it is seems that it does enter suspend with backlight going off, but then it immediately wakes up and freezes dead requiring holding power button to power it off. The weird part is that after that it powers on to blank screen - BIOS is dead as well, the only way out of it is to disconnect battery.

The OP's solution was:
> Create a file /etc/pm/config.d/modules with the following line:
SUSPEND_MODULES="rtl8192ce r8169 uvcvideo"

Create a file /etc/pm/sleep.d/77_fix_wakeup with the following contents:
echo GLAN > /proc/acpi/wakeup
echo LID > /proc/acpi/wakeup

This two changes seem to be directly relevant. I also disabled grub graphical terminal and removed "quiet splash" from kernel command line. Not sure that would affect suspend. I just like it more trying to read all those fast scrolling messages during boot than to stare at animated dots.

This fixed suspend to RAM for him, but not for me. Anyone have any idea where to start?

---

### Post by bbrg548 on 2012-04-05
Fixed! Solution found [here]("https://wiki.archlinux.org/index.php/Toshiba_Satellite_L775D_S7340").

Step 1: Create a file at /etc/pm/sleep.d/20_custom-ehci_hcd, with the following code: 
```
#!/bin/sh
#inspired by http://art.ubuntuforums.org/showpost.php?p=9744970&postcount=19
#...and http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug    
# tidied by tqzzaa :)

VERSION=1.1
DEV_LIST=/tmp/usb-dev-list
DRIVERS_DIR=/sys/bus/pci/drivers
DRIVERS="ehci xhci" # ehci_hcd, xhci_hcd
HEX="[[:xdigit:]]"
MAX_BIND_ATTEMPTS=2
BIND_WAIT=0.1

unbindDev() {
  echo -n > $DEV_LIST 2>/dev/null
  for driver in $DRIVERS; do
    DDIR=$DRIVERS_DIR/${driver}_hcd
    for dev in `ls $DDIR 2>/dev/null | egrep "^$HEX+:$HEX+:$HEX"`; do
      echo -n "$dev" > $DDIR/unbind
      echo "$driver $dev" >> $DEV_LIST
    done
  done
}

bindDev() {
  if [ -s $DEV_LIST ]; then
    while read driver dev; do
      DDIR=$DRIVERS_DIR/${driver}_hcd
      while [ $((MAX_BIND_ATTEMPTS)) -gt 0 ]; do
          echo -n "$dev" > $DDIR/bind
          if [ ! -L "$DDIR/$dev" ]; then
            sleep $BIND_WAIT
          else
            break
          fi
          MAX_BIND_ATTEMPTS=$((MAX_BIND_ATTEMPTS-1))
      done  
    done < $DEV_LIST
  fi
  rm $DEV_LIST 2>/dev/null
}

case "$1" in
  hibernate|suspend) unbindDev;;
  resume|thaw)       bindDev;;
esac
```
Step 2: Make this file executable with this command:
```
sudo chmod 755 /etc/pm/sleep.d/20_custom-ehci_hcd
```
Step 3: Enjoy. The screen still flickers, but the laptop goes into proper sleep.

You'll also need to do the keyboard/touchpad fix provided at the same site. That seems to also fix the automatic reboot on power off bug. Otherwise, you'll run into the problem of the computer restarting after you put it to sleep and the keyboard not working so that you can't put enter your password and the only solution is to reboot and lose your session.

---

### Post by hotweiss on 2012-06-14
Sadly this fix doesn't work with the Canadian equivalent - the L745D.

---

### Post by zonyx on 2012-07-19
This seems to have fixed these issues on the L775D-S7226 as well.  Thanks for posting.  It's nice to finally be able to use this laptop like a laptop.  :)

---

