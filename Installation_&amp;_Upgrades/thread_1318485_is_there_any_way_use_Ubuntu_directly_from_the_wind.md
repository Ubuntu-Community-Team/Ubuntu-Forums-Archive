---
title: "is there any way use Ubuntu directly from the windows and boot on thumbdrive  ?"
date: 2009-11-07
forum: Installation &amp; Upgrades
---

### Post by rdrnnr on 2009-11-07
I need  ubuntu on a bootable thumbdrive and also i need  it on windows as a portable application.I know there is ways to do both separated but is there any way to do both together ?

---

### Post by efflandt on 2009-11-07
Not sure what you mean by use it from USB and Windows, but you can have Ubuntu run from Windows using wubi, or you can access Windows files if you boot a system from a USB flash drive.  For example from a 4 G USB stick with CD image, 1.1 G additional linux file system, and 2 G vfat free:

```
efflandt@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
aufs                  1.1G  431M  612M  42% /
udev                  502M  272K  501M   1% /dev
/dev/sdb1             3.8G  1.8G  2.0G  48% /cdrom
/dev/loop0            668M  668M     0 100% /rofs
none                  502M  160K  501M   1% /dev/shm
tmpfs                 502M   80K  502M   1% /tmp
none                  502M   92K  502M   1% /var/run
none                  502M     0  502M   0% /var/lock
none                  502M     0  502M   0% /lib/init/rw
/dev/sda2             120G   58G   63G  48% /media/HP_PAVILION

 efflandt@ubuntu:~$ ls /media/HP_PAVILION
2ac4ed9ed1a878bd25b115      Garmin           ntldr
5c3375e9c3b10876a95dc5f59d  Gigex Downloads  NVIDIA
additdiag.txt               gsak             OOsetup
ATI Demos                   hiberfil.sys     pagefile.sys
Auth.prof                   hp               Program Files
AUTOEXEC.BAT                IBJts            Python22
bios.txt                    Intel            RECYCLER
BOOT.BAK                    IO.SYS           SWSoftrem800b8_nf
boot.ini                    lexmark          sysprep
CBOETool                    LGSInst.Log      system.sav
Cla-CAV                     metrics.xml      System Volume Information
CONFIG.SYS                  mRouterDebug     Temp
Documents and Settings      MSDOS.SYS        WINDOWS
Documents.gdb               My Maps          WUTemp
DVDPATH.TXT                 NTDETECT.COM
```

---

### Post by rdrnnr on 2009-11-07
@efflandt thnx for reply .
I want to run my ubuntu on my windows as a portable application and i also want to use same usb as a bootable Ubuntu thumbdrive.

---

### Post by rdrnnr on 2009-11-07
??

---

### Post by efflandt on 2009-11-08
Wubi can run Ubuntu from Windows, see
[http://www.ubuntu.com/GetUbuntu/downloadmirrors#wubi](http://www.ubuntu.com/GetUbuntu/downloadmirrors#wubi)

And once you get into Unbuntu, there is System, Administration, USB Startup Disk Creator that can configure an install CD image to boot from USB.  Or you could install Ubuntu on the USB device with an install CD.

---

