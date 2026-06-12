---
title: "Suspend fix for Asus U36JC (k)ubuntu 12.04"
date: 2012-05-13
forum: Hardware
---

### Post by zynex on 2012-05-13
Found a working suspend fix for Asus U36JC;

```
#!/bin/sh
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
```sudo nano /etc/pm/sleep.d/20_custom-ehci_hcd

Paste the script above and save. Make it executable.

sudo chmod +x /etc/pm/sleep.d/20_custom-ehci_hcd

Suspend should now work :)

---

### Post by toolio on 2012-05-20
Fantastic! This works a treat on my Asus X73S. Thanks.

Edit: I found the original post here:

[http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug](http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug)

Lots of people commented saying it fixed the problem. My question as a new Ubuntu user:

How does a bug like this not get fixed in 12.04 when it has been happening for > 18 months and affects so many people???

---

### Post by zynex on 2012-05-24
I think the suspend/hibernate problem has to do with Asus? Seems like lots of Asus users have problem with this. Hope this fix is more permanent for future updates to :)

Anyone tried if hibernate works with this fix? Have no swap, so I can't test it :)

---

### Post by toolio on 2012-05-27
No swap here either!

---

### Post by Helios747 on 2012-05-29
Doesn't work for me. I have a 6.2 GB swap with an encrypted home directory. Suspend will work once, but then it will stop working again.

---

### Post by blistovmhz on 2012-10-06
OP works for K53e (all models afai can tell) on Mint13.  Didn't have this problem with SolusOS.
Not tested with encrypted disc yet.

Multiple suspends fine.  
Incidentally, this is exactly the same solution as I'd written for a bunch of the eeePC's. 
Anyone know wtf's up with Asus's EHCI that's different from everyone else?

---

### Post by zynex on 2012-10-21
Just tested this on Kubuntu 12.10 that I just installed, and it works there to.

---

