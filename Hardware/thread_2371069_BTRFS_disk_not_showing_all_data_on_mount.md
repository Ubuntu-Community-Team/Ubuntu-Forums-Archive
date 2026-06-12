---
title: "BTRFS disk not showing all data on mount"
date: 2017-09-10
forum: Hardware
---

### Post by hanoc on 2017-09-10
Hi,

I've got disk problems with a disk with the BTRFS format. I've found some threads about BTRFS and ubuntu but I was not able to mount the FS following any of them. Also that's only the first of my problems so…

The disk comes from a xbian media center (a linxu distro based on debian to run kodi on a raspberry) and it was formated by default with xbian which uses BTRFS.

I had some trouble with it and connected to an ubuntu machine. 

I have not been able to mount on ubuntu (more on that later) but now, when I connect it to the xbian machine it auto mounts but I don't see all my media. I see what it looks like a xbian install that's only 300MB of a 3TB disk

I can't understand how that data got there at some point trying to mount it on ubuntu I hit some auto repair and ubuntu wrote onto the disk for a very brief time then I plugged the disk to the xbian and fiddled with mounting it and stuff but at any point did I knowingly copy a full xbian installation there. 

I have no idea how BTRFS work and I know it's not as the EXT filesystems so maybe there is some explanation there but I can not make one out of it.

What it matters to me is that the disk had 1TB of information and at any point the disk was writing for that long nor I did (knowingly) format the device so my data should still be there but I don't know how to start to recover it.

I'm not sure where to go from here. 

Xbian does not see any problem with the disk nor it does show the data.

So I'll guess I'll try to mount it on ubuntu to see if there is any difference.

On that front I got this when I plug it on the ubuntu machine it says:

```
    Error mounting /dev/sdc1 at /media/miqueladell/storage: Command-line `mount -t "btrfs" -o "uhelper=udisks2,nodev,nosuid" "/dev/sdc1" "/media/miqueladell/storage"' exited with non-zero exit status 32: mount: wrong fs type, bad option, bad superblock on /dev/sdc1,
           missing codepage or helper program, or other error
    
           In some cases useful info is found in syslog - try
           dmesg | tail or so.

```


And finally dmesg says:
```

    [  625.323035] sd 7:0:0:0: Attached scsi generic sg2 type 0
    [  625.327169] sd 7:0:0:0: [sdc] Spinning up disk...
    [  626.332098] ........ready
    [  633.583796] sd 7:0:0:0: [sdc] 732558336 4096-byte logical blocks: (3.00 TB/2.73 TiB)
    [  633.585067] sd 7:0:0:0: [sdc] Write Protect is off
    [  633.585071] sd 7:0:0:0: [sdc] Mode Sense: 53 00 10 08
    [  633.586406] sd 7:0:0:0: [sdc] No Caching mode page found
    [  633.586409] sd 7:0:0:0: [sdc] Assuming drive cache: write through
    [  633.729453]  sdc: sdc1
    [  633.733935] sd 7:0:0:0: [sdc] Attached SCSI disk
    [  634.305739] BTRFS info (device sdc1): disk space caching is enabled
    [  634.305744] BTRFS: couldn't mount because of unsupported optional features (10).
    [  634.323706] BTRFS: open_ctree failed
```



In case anyone is interested the contents of the disk acording to xbian are as follows:
```

       .
    ./data
    ./data/@
    ./data/@/put_here_to_restore
    ./home
    ./home/@
    ./home/@/xbian
    ./home/@/xbian/.kodi
    ./home/@/xbian/.kodi/addons
    ./home/@/xbian/.kodi/addons/repository.superrepo.org.gotham.all
    ./home/@/xbian/.kodi/addons/repository.superrepo.org.gotham.all/LICENSE.txt
    ./home/@/xbian/.kodi/addons/repository.superrepo.org.gotham.all/addon.xml
    ./home/@/xbian/.kodi/addons/repository.superrepo.org.gotham.all/changelog.txt
    ./home/@/xbian/.kodi/addons/repository.superrepo.org.gotham.all/fanart.jpg
    ./home/@/xbian/.kodi/addons/repository.superrepo.org.gotham.all/icon.png
    ./home/@/xbian/.kodi/addons/packages
    ./home/@/xbian/.kodi/addons/packages/service.xbmc.versioncheck-0.3.19.zip
    ./home/@/xbian/.kodi/addons/packages/metadata.tvdb.com-1.8.4.zip
    ./home/@/xbian/.kodi/addons/packages/metadata.common.imdb.com-2.8.5.zip
    ./home/@/xbian/.kodi/addons/packages/service.subtitles.opensubtitles-5.0.14.zip
    …

```
and it goes on and on but it looks as if it is a copy of what my / was back then, for example see this two lists:
```

    &#10140;  ~ ls -1 /home/xbian
    run_on_reboot
    xbian-config-update.log
    xbian-initramfs-update.log
    xbian-update.log


    &#10140;  ~ ls -1 /media/storage/home/@/xbian
    run_on_reboot
    xbian-config-update.log
    xbian-initramfs-update.log
    &#10140;  ~
```


I know the question is anything but straightforward and that it involves Xbian which maybe is not such a widespread distro but I would greatly appreciate any hints on how to continue.

Additionally the xbian forums are down so I can't not ask there

---

