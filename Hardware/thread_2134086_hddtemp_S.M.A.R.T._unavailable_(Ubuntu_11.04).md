---
title: "hddtemp S.M.A.R.T. unavailable (Ubuntu 11.04)"
date: 2013-04-10
forum: Hardware
---

### Post by Flashgunn on 2013-04-10
Hi guys,
I'm running ubuntu 11.04 with hddtemp 0.3-beta15 on an old netbook. I have two external hard drives attached (USB), both from WD and both S.M.A.R.T. capable; when I try to get SMART infos with hddtemp:
```
sudo hddtemp /dev/sdc
/dev/sdc: WD Ext HDD 1021: S.M.A.R.T. not available
```
But if I use the Disk Utility GUI it works flawlessly (I can run self-test, read temps and info etc.). The problem is that I'd like to access those information via SSH (I'm using the netbook as a NAS): is there some way to either fix hddtemp or access the Disk Utility GUI via terminal?
Thank you for the help!

---

### Post by dabl on 2013-04-10
With everything connected and running as you intend to use it, let's see the output of

```
sudo blkid -c /dev/null -o list
```

---

### Post by ahallubuntu on 2013-04-10
~

---

### Post by Flashgunn on 2013-04-10
> **dabl said:**
> With everything connected and running as you intend to use it, let's see the output of

```
sudo blkid -c /dev/null -o list
```
```

device     fs_type label    mount point    UUID
-------------------------------------------------------------------------------
/dev/sda1  ext4             /              12697083-03a3-4d92-bb00-ab037c365b22
/dev/sda5  swap             <swap>         cdaadf3c-1c2e-4668-8014-561d2c9354fa
/dev/sdb1  ntfs    Franz    /media/Franz   0AF8BB3FF8BB2839
/dev/sdc1  ntfs    Elements /media/Elements FA8496FF8496BD97
/dev/sdd1  ntfs    BigHD    /media/BigHD   54E459D3E459B846
```
Sdc and sdd are the SMART capable hard drives I need to monitor


@ahallubuntu:
smartctl works fine out of the box (only need to enable -a and filter  things out with grep)! So it's even more strange that hddtemp isn't able  to access the SMART infos of my hard drives...maybe it need an update?  Still thank you both guys for the help!

---

### Post by dabl on 2013-04-11
If you look down in the replies on [**[color=green]this[/color]**](http://www.linuxjournal.com/magazine/monitoring-hard-disks-smart?page=0,3) page from 2007, you'll see a reference to the lack of SMART capability across a USB connection.  Apparently it is not a new phenomenon.  However, with those disks in their own external enclosures (i.e. away from the CPU and GPU and that heat), if you can provide reasonable ventilation they should not experience a thermal problem under normal use.

---

### Post by ahallubuntu on 2013-04-11
> **dabl said:**
> If you look down in the replies on [**[color=green]this[/color]**](http://www.linuxjournal.com/magazine/monitoring-hard-disks-smart?page=0,3) page from 2007, you'll see a reference to the lack of SMART capability across a USB connection.  Apparently it is not a new phenomenon.

As I noted above, it's quite possible in 2013 to access S.M.A.R.T. info over USB with smartctl - with many controllers, anyway.  I do it all the time.  Usually the -d sat and -T permissive options to smartctl are all that I need.  I'm also using a more recent version of smartmontools in 12.04 than was available in 11.04.

---

