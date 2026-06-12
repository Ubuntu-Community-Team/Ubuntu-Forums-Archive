---
title: "No Wireless"
date: 2012-09-02
forum: Hardware
---

### Post by tmcq on 2012-09-02
I've been through the many posts with this same problem and applied the recommended fixes but still no good:

Compaq Presario c500.  Installed Ubuntu 12.04 LTS - everything working except wireless.  

Info from terminal:

06:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)

I did the:

sudo apt-get install b43-fwcutter firmware-b43-installer

and rebooted, but still no wireless.  Also - the wireless button will not activate when I press it.  If I log off and start windows I can get it to work.  Eventually want to delete windows.  Please help.  I love everything else.  Can't wait to dump windows.

---

### Post by ooVoh9em on 2012-09-02
> **tmcq said:**
> I've been through the many posts with this same problem and applied the recommended fixes but still no good:

Compaq Presario c500.  Installed Ubuntu 12.04 LTS - everything working except wireless.  

Info from terminal:

06:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)

I did the:

sudo apt-get install b43-fwcutter firmware-b43-installer

and rebooted, but still no wireless.  Also - the wireless button will not activate when I press it.  If I log off and start windows I can get it to work.  Eventually want to delete windows.  Please help.  I love everything else.  Can't wait to dump windows.

I notice that you have installed the firmware packages for the wireless device. However, did you follow the instructions at the following link? [https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_Natty_11.04](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_Natty_11.04)

At the bottom it states:

> CAUTION: This pci.id is also claimed by the Broadcom STA driver provided by bcmwl-kernel-source. Installation blacklists b43 and ssb. The driver bcmwl-kernel-source driver wl doesn't work well and b43 and ssb are preferred. To remove the incorrect driver and blacklist... 

So, if that is your issue, it suggests the following:

```
sudo apt-get remove --purge bcmwl-kernel-source
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
```

it also suggests that on Ubuntu 11.10 (and likely 12.04) that the above commands might need be replaced by:


```
sudo apt-get remove --purge bcmwl-kernel-source
sudo rm /etc/modprobe.d/broadcom-sta-common.conf
```


I have also found a few threads regarding this device, and many people seem to have it working. For further reading, I would suggest:

[http://ubuntuforums.org/showthread.php?t=1905799](http://ubuntuforums.org/showthread.php?t=1905799)


I do not own this device myself, but hopefully the above information is enough to help you continue to troubleshoot your issue.

---

### Post by tmcq on 2012-09-02
I had done that command replacement...however just now after the third re-start it is now working.  Not sure what did it, but I'm there.  Thanks!

---

