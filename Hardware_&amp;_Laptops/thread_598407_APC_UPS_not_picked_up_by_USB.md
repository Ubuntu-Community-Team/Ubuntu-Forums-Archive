---
title: "APC UPS not picked up by USB"
date: 2007-10-31
forum: Hardware &amp; Laptops
---

### Post by Tyr_7BE on 2007-10-31
...in fact, nothing seems to be picked up by USB.  But USB still works.  Let me explain.

I bought an APC UPS the other day, and tried to plug in the USB cable today.  I was going to follow the instructions at [http://marius.scurtescu.com/2007/01/16/ubuntu_edgy_and_the_apc_es_550_ups](http://marius.scurtescu.com/2007/01/16/ubuntu_edgy_and_the_apc_es_550_ups) .  But when I went to issue a 'cat /proc/bus/usb/devices', it told me there was no such file.  In fact, when I issue a 'ls /proc/bus/usb', it comes up blank.

I know USB is working, as I have two external drives hooked up to a USB 2.0 PCMCIA adapter, and they both work like champs.  But I tried hooking up the UPS to both the built in USB port on the back of the laptop, and the PCMCIA adapter.  In both cases, /proc/bus/usb was empty, no 'devices' file.  Not even anything for my two external hard drives.

 Has the mechanism by which you see your USB devices changed?  When I issue a 'ls -l /sys/bus/usb/drivers' I get what I expect, basically everything that was shown on that page I linked to.  But the device itself doesn't appear to be picked up, and there is no /dev/hiddev0 device.

Ideas?  I'm using an old Compaq Armada M500.

---

### Post by Tyr_7BE on 2007-10-31
*bump*

EDIT: FYI, I just plugged the UPS into my Apple iBook, and OS X detected that there was a UPS just fine.  the little UPS icon appeared next to my battery icon.  So it seems the UPS is good and so are all the cables.  This looks to be an Ubuntu problem.

EDIT EDIT:

conor@jade:~$ lsusb
Bus 004 Device 003: ID 067b:3507 Prolific Technology, Inc. PL3507 ATAPI6 Bridge 
Bus 004 Device 002: ID 0402:5621 ALi Corp. USB 2.0 Storage Device
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 051d:0002 American Power Conversion Back-UPS Pro 500/1000/1500
Bus 001 Device 001: ID 0000:0000  


There it is.  But still, /proc/bus/usb is totally empty.

---

### Post by Tanker Bob on 2007-10-31
Gutsy USB mounting has serious issues. There are a number of threads about this in this forum. The most detailed is [here](http://ubuntuforums.org/showthread.php?p=3680098). That thread just covers removable storage media. There are others about other devices.

---

### Post by Tyr_7BE on 2007-10-31
Thanks.  I tried downgrading HAL to Feisty, but still no go.  I'll keep searching.

Is this going to be addressed with an updated HAL?  I'd hate to think that they're just going to leave it like this.

---

### Post by Tanker Bob on 2007-10-31
I haven't filed a formal bug report on launchpad yet. I will do so when I get a chance this week. I looked there to see if anyone had reported it as of last weekend, but no one had at that time. The kernel team probably doesn't read the forums, so a bug report is the only way to get it fixed. I do believe that they will try to fix it when reported.

---

### Post by Tyr_7BE on 2007-10-31
Good on ya for filing a bug.  Always appreciated.

I managed to make things sort of work with the following (ripped from [http://forums.virtualbox.org/viewtopic.php?t=2385&view=next&sid=de5c67b938115f5283daa0494284e251](http://forums.virtualbox.org/viewtopic.php?t=2385&view=next&sid=de5c67b938115f5283daa0494284e251) )

```

You need to edit an init script:
Code:
sudo gedit /etc/init.d/mountdevsubfs.sh

Then look for the following:
Code:
    #
    # Magic to make /proc/bus/usb work
    #
    #mkdir -p /dev/bus/usb/.usbfs
    #domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
    #ln -s .usbfs/devices /dev/bus/usb/devices
    #mount --rbind /dev/bus/usb /proc/bus/usb

Remove the #'s from the last four lines so it looks like this :
Code:
    #
    # Magic to make /proc/bus/usb work
    #
    mkdir -p /dev/bus/usb/.usbfs
    domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
    ln -s .usbfs/devices /dev/bus/usb/devices
    mount --rbind /dev/bus/usb /proc/bus/usb

And finally:
/etc/init.d/mountdevsubfs.sh start 
```

That site is definitely worth a read, lots of good stuff in that thread.

So I now have /proc/bus/usb/devices all populated and things are looking good.  I checked, and there's a /dev/usb/hiddev0 device, which is a pretty good sign.  But when I follow the same configuration linked off of the blog above, I get this when I try to start apcupsd:

conor@jade:~$ sudo /etc/init.d/apcupsd restart
/etc/default/apcupsd: 4: UPSCABLE: not found

UPSCABLE is set to 'usb', DEVICE is left blank (though i've tried setting it to /dev/usb/hiddev0 with no luck)

Still working on it.  Not there yet.

---

