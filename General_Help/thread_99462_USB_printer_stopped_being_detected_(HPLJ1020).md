---
title: "USB printer stopped being detected (HPLJ1020)"
date: 2005-12-05
forum: General Help
---

### Post by earth_walker on 2005-12-05
(Originally was my response to [http://www.ubuntuforums.org/showthread.php?t=78272&page=3](http://www.ubuntuforums.org/showthread.php?t=78272&page=3), 
reworked  and reposted in the right forum)

Please help. I must have put 20 hours into false starts and bad advice getting my HP LJ1020 printer to work (mostly) using the foo2zjs-patched driver. I really should have left well enough alone, but since 2 people had no problems at all, I thought it would be safe to upgrade to the latest foo2zjs drivers. 

After following the directions in the Install file, the gnome printing panel stopped detecting my printer. No errors were given during the install.

So I tried to apply the udev patch given at [http://support.ideainformatica.com/hplj1020/](http://support.ideainformatica.com/hplj1020/) to the new foo2zjs driver, with no luck.

After playing around and having no luck with the new foo2zjs drivers, I tried to reinstall the older patched udev foo2zjs drivers again using Johnp_g's post above, to recreate my working printer setup.

However, the gnome printing panel still doesn't detect my printer! I've tried everything - rebooting, restarting udev, restarting cupsys, restarting the printer, reinstalling in different directories.

For various commands I get as follows:
$ cat /proc/sys/kernel/hotplug
/sbin/udevsend
and
$ sudo cat /usr/share/foo2zjs/firmware/sihp1020.dl > /dev/usb/lp0
bash: /dev/usb/lp0: Permission denied
and finally
$ sudo usb_printerid /dev/usb/lp0
Error: Input/output error: GET_DEVICE_ID on '/dev/usb/lp0'

So my guess is the printer is not being recognised. It is on. It has been turned off and on many times.

I have no clue where to go from here - up til now the problem has been with the printer giving errors, but it has always been detected at least.

Which components control this behaviour, and how do I restart/reinstall them?
Is there some way to check what's going on in udev? Has one of the installation scripts messed things up?
Is there a way to turn on 'hotplug' so that it may detect the usb printer instead?

Should I:
reinstall udev?
reinstall some other version of foo2zjs?
uninstall everything printer-related and start again? How would I go about that?

Help! Please!

---

### Post by installer on 2005-12-05
The post by Johnp_g in this thread got me going. :) 
_[http://www.ubuntuforums.org/showthread.php?t=78272&highlight=laserjet+1020](http://www.ubuntuforums.org/showthread.php?t=78272&highlight=laserjet+1020)_

---

### Post by earth_walker on 2005-12-05
[QUOTE=installer]The post by Johnp_g in this thread got me going. :) 
_[http://www.ubuntuforums.org/showthread.php?t=78272&highlight=laserjet+1020](http://www.ubuntuforums.org/showthread.php?t=78272&highlight=laserjet+1020)_[/QUOTE]

Yes, that's how I originally got it going, but it is not working for me a second time, and I cannot figure out what is different now.

---

### Post by earth_walker on 2005-12-05
Ok - let's say I want to bring my ubuntu back to before I made these multiple attempts to install printer drivers. What packages would I have to reinstall to do this?

How about erasing every file/directory that has "foo2zjs" in it, and then reinstalling ubuntu-base and ubuntu-desktop?

---

### Post by earth_walker on 2005-12-29
Simply using the latest (Dec 28 ) driver from [http://foo2zjs.rkkda.com/](http://foo2zjs.rkkda.com/) fixed everything, including letter-size printing. 

Since the udev setup from the older driver version was detecting the printer fine, I did not "make install-hotplug" at this install. Otherwise I followed the instructions in the INSTALL file.

Thanks to everyone for your suggestions.

---

