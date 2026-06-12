---
title: "High wa% on Dell Inspiron 8200"
date: 2006-06-04
forum: Hardware &amp; Laptops
---

### Post by odix on 2006-06-04
Hi there
I've noticed a high io wait load with dapper on my Inspiron, this wasn't with breezy, KDE seems to start faster from the livecd as from the harddisk now, strange. My IBM T22 (P3/900, Inspiron P4/1800), also with dapper (kubuntu) starts nearly twice as fast into the desktop.

It's really strange, it looks like something is throttling the IO system down, may the IO scheduler ???

thanks in advance
odi

---

### Post by odix on 2006-06-05
As the system is currently in an nearly unusable state and I think, I'm not the only one with such hardware, I've create ab problem report ([#48499]("https://launchpad.net/distros/ubuntu/+bug/48499"))

regards

---

### Post by odix on 2006-06-05
did anybody know where the "essential drivers" are loaded, is this configurable ?
there will be a lot of modules be inserted, which are useless, maybe there is the problem.

---

### Post by odix on 2006-06-05
Additional Information:

The load factor is really high (between 0.3 and 0.7), for that case that the system does nearly nothing (writing this few words)

regards

---

### Post by heldal on 2006-06-06
[QUOTE=odix]did anybody know where the "essential drivers" are loaded, is this configurable ?
there will be a lot of modules be inserted, which are useless, maybe there is the problem.[/QUOTE]

"Essential drivers", i.e. the drivers needed to bring the system into a state where it is able to mount the root filesystem from your harddrive, are located in a ramdisk image. Check the boot config (/boot/grub/menu.lst) to find which file (<somename>.initrd) is used.  The image is created with "mkinitramfs". See man-pages and other documentation for the initramfs-tools package for further info.

Btw, I've got the same model computer and see the same performance-degredation after a breezy2dapper upgrade. So far I've tried different i/o-schedulers and checked the drivers. No improvement yet.

---

### Post by heldal on 2006-06-06
Can anybody attach and post a Nvidia-module (nvidia.ko) version 1.0-8762 for the latest i686 breezy kernel (2.6.12-10-686) here. I'd like to check the performance of the dapper desktop using the breezy-kernel left-over after the upgrade. The old kernel boots ok, but its nvidia-module is an old version that is rejected by the Xorg-server driver-module in Dapper. I don't feel like re-establishing a complete breezy dev-platform to compile the driver if somebody who had installed 1.0-8762 manually in the past can post a binary ;)

---

### Post by heldal on 2006-06-06
HAL (harware abstraction layer) seems to be the culprit (in fact the same as previously observed with magicdev). The primary disk and the cdrom are on the same IDE channel on the Inspiron 8200. HAL seems to be polling the cdrom for status change (disk inserted etc) every 2 sec or so. Each poll blocks the channel for more than 1 sec causing massive I/O problems. Just killing the "hald" process seems to bring performance back to normal. It does however cause problems for the desktop which relies on it. 

Still looking for alternative solutions ...

------

PS! I have tried the following alternative kernels to eliminate a possible problem with the default dapper kernel, but they don't eliminate the disk problem:
* Breezy kernel (2.6.12) 
* Plain kernel.org version (2.6.16.20)

---

### Post by odix on 2006-06-06
Hm, this sounds feasible, I give a try, and also digging in hald documentation

regards odix

---

### Post by odix on 2006-06-06
yes!, it's fully reproducable, killing hald brings you performance back, will update problem report

regards

---

### Post by odix on 2006-06-07
is there a possibility to disable cdrom polling via policies ?

---

### Post by heldal on 2006-06-07
Try to disable media-checks on hdb (if that's the CD on your machine) as follows:

1. Create a file /etc/hal/fdi/policy/cdrom.fdi with the following content:

```
<?xml version="1.0" encoding="UTF-8"?> <!-- -*- SGML -*- -->

<deviceinfo version="0.2">

  <device>
    <match key="block.device" string="/dev/hdb">
      <merge key="storage.media_check_enabled" type="bool">false</merge>
    </match>
  </device>

</deviceinfo>
```

2. Restart HAL with "/etc/init.d/dbus restart" (or reboot)


----

It is also possible to make changes from the commandline with hal-set-property, but those are lost when hald is restarted. First browse the output from "lshal" to find the UDI for the cdrom device. On my laptop this results in the following command (one line):

hal-set-property --udi /org/freedesktop/Hal/devices/storage_model_HL_DT_STCD_RW/
DVD_ROM_GCC_4240N --key storage.media_check_enabled --bool false

---

### Post by odix on 2006-06-07
Hi,
thank you, I've tried this today, without success, after restarting dbus all seems to be ok, but hotplging doesn't work, after reboot of machine i've checked the correct settings with lshal, but the behaviour is the same, the only difference is that the wa% is lower, but not the load factor, the system took ages to boot into the desktop, or start applications

regards

---

### Post by odix on 2006-06-09
Hi,
will there be any response from the developers/maintainers ?
I've disabled polling of both the cdrom and the harddisk (partitions) in the policy,

```

<deviceinfo version="0.2">
  <device> <!-- the dvd/cdrw drive -->
    <match key="storage.bus" string="ide">
      <match key="block.device" string="/dev/hdb">
        <merge key="storage.media_check_enabled" type="bool">false</merge>
        <merge key="storage.automount_enabled_hint" type="bool">false</merge>
      </match>
    </match>
  </device>

  <device> <!-- the harddisk -->
    <match key="storage.bus" string="ide">
      <match key="block.device" string="/dev/hda">
        <merge key="storage.media_check_enabled" type="bool">false</merge>
        <merge key="storage.automount_enabled_hint" type="bool">false</merge>
        <merge key="storage.no_partitions_hint" type="bool">true</merge>
      </match>
    </match>
  </device>
</deviceinfo>

```

 the performance is now better but even lightyears away from that if hald (dbus) service is stopped

regards

odiX

---

### Post by odix on 2006-06-19
Hi,
is there any reaction from the maintainers of hald ? Sorry but currently I'm a little bit angry about no reaction.

@heldal
do you have any workarround or solution

regards

---

### Post by heldal on 2006-06-19
[QUOTE=odix]
@heldal
do you have any workarround or solution
[/QUOTE]

Wish I did. The i8200 I used had 2 hdd's mirrored. Linux balances read requests between the drives in such a configuration so performance-degredation wasn't too bad. 

A potential hardware-workaround with one drive is to get hold of an empty drive-container for the front media bay and put your disk there. That drive becomes master on the 2nd IDE channel. The CDROM is then a slave alone on the 1st channel with no master so I don't know if that'll work.

Maybe some dell-guru has suggestions for changes to the i8k internal wiring to get the optical drive off the IDE channel used by the primary HDD.

Also note that this also is the cause of many reports of problems with optical-drives. IDE performance-problems makes it impossible to burn CDs or DVDs on many computers. A permanent solution has to involve either changes to the behavior of 'hald' or changes to the kernel's ide driver to avoid device-blocking or simply block repeated open() requests to the same device which seem to cause the problem. The question os how much attention this problem will get with modern systems moving to SATA and thus not affected.

//Per

---

### Post by odix on 2006-06-21
As I'm using the cdrom/dvd drive not very often, I've disabled the drive via appending a kernel parameter (hdb=none) in grub (/boot/grub/menu.lst),

note: this should only be a temporary solution for me ;-)

 regards odix

---

### Post by heldal on 2006-08-24
In the HAL-developers archive I found the attached diff that was made late 2005 to remove some laptops from a device blacklist. It looks similar to what's been discussed before, except it would apply to /usr/share/hal/fdi/preprobe/10osvendor/10-ide-drives.fdi. It may be that the content of files in /use/share/hal is handled differently from the /etc-files. Just guessing, I'm no hal-maintainer. The file also contain reference to a hdd which afik doesn't exist on the 8200 but shouldn't hurt.

Either use the patch-command to reverse the diff, or manualy edit the file (/usr/share/hal/fdi/preprobe/10osvendor/10-ide-drives.fdi) to add lines removed by the diff (starting with '-')


//per

---

### Post by icantdothatdave on 2006-09-05
Thank you so much! I have been banging my head against the wall ](*,)  for over two months now trying to get my Dell Latitude C840 to work right. I frequently use the CD drive, so disabling it was a poor option. I couldn't get the patch command to work correctly, but I just manually edited the file and added the missing lines. I was so frustrated with this that I was even led to try other distributions (SUSE and Fedora) :(  but hated them and came back in spite of the hald problem. Now I can run my beloved Ubuntu again without extreme slowdown or a disabled CD drive. You guys are awesome! :-D

---

### Post by blink on 2007-02-12
It seems this bug is back (and with a vengeance). The above soln (to effectively reblacklist polling of the drive) seems to not work anymore. I see hald-addon-storage continue to probe the cdrom every 2 seconds regardless of the settings.

 Here is the output of lshal (with the options above applied):

```

udi = '/org/freedesktop/Hal/devices/storage_model_HL_DT_STCD_RW/DVD_ROM_GCC_4240N'
  info.addons = {'hald-addon-storage'} (string list)
  storage.policy.desired_mount_point = 'cdrecorder'  (string)
  storage.policy.mount_filesystem = 'auto'  (string)
  storage.policy.should_mount = true  (bool)
  block.storage_device = '/org/freedesktop/Hal/devices/storage_model_HL_DT_STCD_RW/DVD_ROM_GCC_4240N'  (string)
  info.udi = '/org/freedesktop/Hal/devices/storage_model_HL_DT_STCD_RW/DVD_ROM_GCC_4240N'  (string)
  storage.cdrom.write_speed = 4234  (0x108a)  (int)
  storage.cdrom.read_speed = 4234  (0x108a)  (int)
  storage.cdrom.support_media_changed = true  (bool)
  storage.cdrom.hddvdrw = false  (bool)
  storage.cdrom.hddvdr = false  (bool)
  storage.cdrom.hddvd = false  (bool)
  storage.cdrom.bdre = false  (bool)
  storage.cdrom.bdr = false  (bool)
  storage.cdrom.bd = false  (bool)
  storage.cdrom.dvdplusrdl = false  (bool)
  storage.cdrom.dvdplusrw = false  (bool)
  storage.cdrom.dvdplusr = false  (bool)
  storage.cdrom.dvdram = false  (bool)
  storage.cdrom.dvdrw = false  (bool)
  storage.cdrom.dvdr = false  (bool)
  storage.cdrom.dvd = true  (bool)
  storage.cdrom.cdrw = true  (bool)
  storage.cdrom.cdr = true  (bool)
  storage.requires_eject = true  (bool)
  storage.hotpluggable = false  (bool)
  info.capabilities = {'storage', 'block', 'storage.cdrom'} (string list)
  info.category = 'storage'  (string)
  info.product = 'HL-DT-STCD-RW/DVD-ROM GCC-4240N'  (string)
  storage.removable = true  (bool)
  storage.physical_device = '/org/freedesktop/Hal/devices/pci_8086_248a_ide_0_1'  (string)
  storage.firmware_version = 'D110'  (string)
  storage.vendor = ''  (string)
  storage.model = 'HL-DT-STCD-RW/DVD-ROM GCC-4240N'  (string)
  storage.drive_type = 'cdrom'  (string)
  storage.automount_enabled_hint = false  (bool)
  storage.media_check_enabled = false  (bool)
  storage.no_partitions_hint = false  (bool)
  storage.bus = 'ide'  (string)
  block.is_volume = false  (bool)
  block.minor = 64  (0x40)  (int)
  block.major = 3  (0x3)  (int)
  block.device = '/dev/hdb'  (string)
  linux.hotplug_type = 3  (0x3)  (int)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_248a_ide_0_1'  (string)
  linux.sysfs_path_device = '/sys/block/hdb'  (string)
  linux.sysfs_path = '/sys/block/hdb'  (string)

```

The work-around right now is to kill hald-addon-storage. It stops the ide performance devastation. Of course, you will lose automounting and such.

This bug has been found many times and supposedly fixed many times. For references, redhat bugzilla has a good diagnosis and soln for it (back in 2005).

[https://bugzilla.redhat.com/bugzilla/show_bug.cgi?id=138148](https://bugzilla.redhat.com/bugzilla/show_bug.cgi?id=138148)

This bug was recently reopened (Nov 2005) in the redhat bugzilla list:

[https://bugzilla.redhat.com/bugzilla/show_bug.cgi?id=213995](https://bugzilla.redhat.com/bugzilla/show_bug.cgi?id=213995)

It seems clear that recent changes to hal have reintroduced the polling problem. To help with the background and history:

The Dell Inspiron 8200 (and other dell models) have the hard drive and cdrom/dvdrom share the ide bus. The polling of the cdrom blocks access to the hard drive and demolishes its performance.

The cdrom was blacklisted by hal back in 2004 to avoid polling, but the blacklist entry was removed ~ october 2005:

[http://lists.freedesktop.org/archives/hal/2005-October/003619.html](http://lists.freedesktop.org/archives/hal/2005-October/003619.html)

As someone said it now worked without the patch.

On the 1st redhat bugzilla entry, someone proposed a different mechanism to poll the cdrom drive status. It works without ANY performance hit to the hard drive. Unfortunately, hal does not use this method.

If someone knows the right hal maintainer, they should let them know. [http://www.freedesktop.org](http://www.freedesktop.org) (the home of hal) has been down for at least yesterday and today so I can only browse their website through google's cache.

There seems to be some arguments whether it's a hal bug or a kernel bug. But from the poor user's perspective the practical answer is "who cares! just fix it!". I think it would be easy for hal to offer a workaround (polling the cdrom in the redhat bugzilla proposed manner). If someone can track it down and confirm it's a kernel bug then more power to you.

hth!

---

### Post by heldal on 2007-05-02
> **blink said:**
> It seems this bug is back (and with a vengeance). The above soln (to effectively reblacklist polling of the drive) seems to not work anymore. I see hald-addon-storage continue to probe the cdrom every 2 seconds regardless of the settings.


Even after patching /usr/share/hal/fdi/preprobe/10osvendor/10-ide-drives.fdi?

Changes to policy-files in /etc makes no difference, but reversing the patch as described above still works on an inspiron 8200 that I maintain. That is with ubuntu 6.10 with all patches as of 5/1/07. It remains to see what happens when it's upgraded to 7.04 (feisty).

---

### Post by anco on 2007-06-04
Hello,

What a bummer... I just tried to install ubuntu 7.04 on Dell inspiron 8200 and yes same hd bug for me. Rest well recognised, but so slow. Inserting a cd does not help too much seems to me.

Hdparm test gives without cd only 1mb/s
with cd it gives around 7mb/s

But nowhere near 25mb/s

It is slower than other laptops with weaker specs...

What can I do on ubuntu Feisty to go around this problem?

---

### Post by joeybutterface on 2007-10-20
Getting this on my inspiron 9300 now. System is virtually unusable. Sometimes I do wonder if Linux is worth the effort.

---

