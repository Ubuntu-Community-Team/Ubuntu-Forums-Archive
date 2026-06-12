---
title: "Brother Scanner not recognized in 16.04"
date: 2017-01-24
forum: Hardware
---

### Post by mollie4168 on 2017-01-24
Hello,

I made some progress using this thread: [https://ubuntuforums.org/showthread.php?t=2321613](https://ubuntuforums.org/showthread.php?t=2321613), but I'm still not able to connect my Brother DCP-7065DN scanner.  It's been connected in the past, and then I started having issues about a year and a half ago.  I couldn't get it fixed through the forums or Brother and gave up by using my husband's Windows computer to connect to it.  It would be great to connect directly from my computer again.

[HTML]ii  brother-udev-rule-type1                              1.0.2                                         all          Brother udev rule type 1
ii  brscan-skey                                          0.2.4-1                                       amd64        Brother Linux scanner S-KEY tool
ii  brscan4:i386                                         0.4.4-1                                       i386         Brother Scanner Driver
ii  cupswrapperdcp7065dn:i386                            2.0.4-2                                       i386         Brother DCP7065DN CUPS wrapper driver
ii  dcp7065dnlpr:i386                                    2.1.0-1                                       i386         Brother DCP-7065DN LPR driver
ii  printer-driver-brlaser                               3-5~ubuntu1                                   amd64        printer driver for (some) Brother laser printers
ii  printer-driver-ptouch                                1.4-1                                         amd64        printer driver Brother P-touch label printers
[/HTML]

I've done the following:
I installed **[FONT=courier new]brother-udev-rule-type1-1.0.0-1.all.deb[/FONT]**

 I edited **/lib/udev/rules.d/40-libsane.rules** by adding      Code:
     # Brother scanners
ATTRS{idVendor}=="04f9", ENV{libsane_matched}="yes" 
before the line "# The following rule will disable". 

And I've copied /usr/lib/x86_64-linux-gnu/sane to /usr/lib/sane

My libusb-0.1-4 is up to date.  

Any ideas of what I'm missing?  ](*,)

Thanks.

---

### Post by DuckHook on 2017-01-25
Please post output of:```
ls -laF /usr | grep lib
``````
ls -laF /usr/lib | egrep 'sane|64'
```

---

### Post by SeijiSensei on 2017-01-25
Did you use the Driver Install Tool for your device from Brother's web site?  That seems to work flawlessly in setting up Brother printers and scanners.

---

### Post by DuckHook on 2017-01-25
> **SeijiSensei said:**
> Did you use the Driver Install Tool for your device from Brother's web site?  That seems to work flawlessly in setting up Brother printers and scanners.I can attest from personal experience that this tool does not work for some models of Brother MFCs. It installs the printer driver properly but leaves scanning nonfunctional.

The steps detailed in OP's link are necessary to get some models of MFC to scan. It still requires user to register the Brother ID in …libsane.rules and to create the symlink to /usr/lib/sane, hence my request for OP's output.

---

### Post by mollie4168 on 2017-01-25
Yes.  I've used the driver tool in the past, and it worked without issue.  It's been more recently that the scanner stopped working.  I've tried reinstalling everything, but it still isn't working.

[HTML]tracy@tracy:~$ ls -laF /usr | grep lib
drwxr-xr-x 175 root root 28672 Jan 24 18:58 lib/
drwxr-xr-x   3 root root  4096 Nov 17 22:18 lib32/
tracy@tracy:~$ ls -laF /usr/lib | egrep 'sane|64'
-rw-r--r--   1 root root  136440 Jul 13  2016 libecryptfs.so.1.0.0
-rw-r--r--   1 root root   39640 Jun 30  2016 libgimpthumb-2.0.so.0.800.16
-rw-r--r--   1 root root  137264 Jun 30  2016 libgimpui-2.0.so.0.800.16
drwxr-xr-x   2 root root   16384 Jan 24 20:16 sane/
drwxr-xr-x 127 root root  110592 Jan 24 18:03 x86_64-linux-gnu/

[/HTML]

---

### Post by DuckHook on 2017-01-26
Do you use 32-bit or 64-bit Ubuntu? Please do:```
uname -a
```
Is this a fresh install, or has it been network upgraded from a series of prior versions? /usr/lib32 should no longer be present unless you install some deprecated architecture libraries.

You stated that you:> copied /usr/lib/x86_64-linux-gnu/sane to /usr/lib/sane
It is important to not just copy, but to copy the right drivers. The actual details are in the following Brother website: [http://support.brother.com/g/s/id/linux/en/faq_scn.html?c=us_ot&lang=en&comple=on&redirect=on#f00101](http://support.brother.com/g/s/id/linux/en/faq_scn.html?c=us_ot&lang=en&comple=on&redirect=on#f00101)
Therefore:

[LIST=1]
[*]First, you must determine your Brother scanner driver version: whether brscan/2/3/4
[*]Then, locate where the Driver Install Tool put them by first:```
sudo updatedb
```
[*]Then if, for example, your scanner uses brscan4:```
locate libsane-brother4
```
[*]Then you must copy *all* of the drivers in the link above that are appropriate to your version of brscan into /usr/lib as per the link instructions.
[*]
[/LIST]
For good measure, to ensure there are no typos, please also post output of:```
ls -laF /lib/udev/rules.d
``````
cat /lib/udev/rules.d/40-libsane.rules | grep -iA2 brother
```

---

### Post by mollie4168 on 2017-01-26
> **DuckHook said:**
> Do you use 32-bit or 64-bit Ubuntu? Please do:```
uname -a
```

[HTML]
uname -a
Linux tracy 4.4.0-59-generic #80-Ubuntu SMP Fri Jan 6 17:47:47 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux[/HTML]

> 
Is this a fresh install, or has it been network upgraded from a series of prior versions? /usr/lib32 should no longer be present unless you install some deprecated architecture libraries.

It was a network upgrade.

> You stated that you:
It is important to not just copy, but to copy the right drivers. The actual details are in the following Brother website: [http://support.brother.com/g/s/id/linux/en/faq_scn.html?c=us_ot&lang=en&comple=on&redirect=on#f00101](http://support.brother.com/g/s/id/linux/en/faq_scn.html?c=us_ot&lang=en&comple=on&redirect=on#f00101)
Therefore:

[LIST=1]
[*]First, you must determine your Brother scanner driver version: whether brscan/2/3/4 
[/LIST]

I've been under the impression that I have brscan4 based on the information from the output in my first post.


> 

[LIST=1]
[*]Then, locate where the Driver Install Tool put them by first:```
sudo updatedb
``` 
[/LIST]

I get no response from this. 


> 
[LIST=1]
[*]Then if, for example, your scanner uses brscan4:```
locate libsane-brother4
``` 
[/LIST]

```

tracy@tracy:~$ locate libsane-brother4
/usr/lib/sane/libsane-brother4.so
/usr/lib/sane/libsane-brother4.so.1
/usr/lib/sane/libsane-brother4.so.1.0.7
/usr/lib/x86_64-linux-gnu/sane/libsane-brother4.so
/usr/lib/x86_64-linux-gnu/sane/libsane-brother4.so.1
/usr/lib/x86_64-linux-gnu/sane/libsane-brother4.so.1.0.7



```> 
[LIST=1]
[*]Then you must copy *all* of the drivers in the link above that are appropriate to your version of brscan into /usr/lib as per the link instructions. 
[/LIST]

When I attempt to copy from terminal based on the instructions, I get the following:  

```
cp /usr/lib64/sane/libsane-brother4.so.1.0.7 /usr/lib/sane
cp: cannot stat '/usr/lib64/sane/libsane-brother4.so.1.0.7': No such file or directory
```

This was why I modified the code for x86_64-linux-gnu as noted in the locate code above.  Is that where I went wrong?



> For good measure, to ensure there are no typos, please also post output of:```
ls -laF /lib/udev/rules.d
``````
cat /lib/udev/rules.d/40-libsane.rules | grep -iA2 brother
```

```
ls -laF /lib/udev/rules.d
total 772
drwxr-xr-x 2 root root  12288 Jan 24 19:20 ./
drwxr-xr-x 4 root root   4096 Jan 24 18:04 ../
-rw-r--r-- 1 root root    552 Jan  4  2016 39-usbmuxd.rules
-rw-r--r-- 1 root root     69 Nov 18  2014 40-crda.rules
-rw-r--r-- 1 root root  96705 Jan 24 19:20 40-libsane.rules
-rw-r--r-- 1 root root    998 Oct  8  2014 40-usb-media-players.rules
-rw-r--r-- 1 root root  35692 Nov  2  2015 40-usb_modeswitch.rules
-rw-r--r-- 1 root root    613 Jan 18 16:04 40-vm-hotadd.rules
-rw-r--r-- 1 root root    165 Mar 31  2016 50-apport.rules
-rw-r--r-- 1 root root    113 Mar  1  2016 50-bluetooth-hci-auto-poweron.rules
-rw-r--r-- 1 root root    210 Jan 12 08:08 50-firmware.rules
-rw-r--r-- 1 root root   3310 Jan 18 16:03 50-udev-default.rules
-rw-r--r-- 1 root root   5675 Oct 26  2015 55-Argyll.rules
-rw-r--r-- 1 root root   6497 Apr 16  2016 55-dm.rules
-rw-r--r-- 1 root root    921 Mar 29  2016 56-hpmud.rules
-rw-r--r-- 1 root root   2446 Apr 16  2016 56-lvm.rules
-rw-r--r-- 1 root root    606 Jan 18 16:03 60-block.rules
-rw-r--r-- 1 root root    910 Jan 18 16:03 60-cdrom_id.rules
-rw-r--r-- 1 root root    153 Jan 18 16:03 60-drm.rules
-rw-r--r-- 1 root root    738 Jan 18 16:03 60-evdev.rules
-rw-r--r-- 1 root root    583 May  5  2015 60-gnupg2.rules
-rw-r--r-- 1 root root   3368 Dec 22  2015 60-gnupg.rules
-rw-r--r-- 1 root root    329 Jan  8  2016 60-inputattach.rules
-rw-r--r-- 1 root root   6107 Dec 10  2015 60-libgphoto2-6.rules
-rw-r--r-- 1 root root    201 May 24  2016 60-openobex.rules
-rw-r--r-- 1 root root    912 Jun 29  2012 60-pcmcia.rules
-rw-r--r-- 1 root root    616 Jan 18 16:03 60-persistent-alsa.rules
-rw-r--r-- 1 root root   2464 Jan 18 16:03 60-persistent-input.rules
-rw-r--r-- 1 root root   1495 Apr 16  2016 60-persistent-storage-dm.rules
-rw-r--r-- 1 root root   5766 Jan 18 16:03 60-persistent-storage.rules
-rw-r--r-- 1 root root   1420 Jan 18 16:03 60-persistent-storage-tape.rules
-rw-r--r-- 1 root root    769 Jan 18 16:03 60-persistent-v4l.rules
-rw-r--r-- 1 root root   1190 Jan 18 16:03 60-serial.rules
-rw-r--r-- 1 root root    472 Aug 19 23:54 60-xdiagnose.rules
-rw-r--r-- 1 root root    328 Jan 24  2016 61-gnome-bluetooth-rfkill.rules
-rw-r--r-- 1 root root    456 Jan 18 16:04 61-persistent-storage-android.rules
-rw-r--r-- 1 root root    418 Jan 18 16:03 64-btrfs.rules
-rw-r--r-- 1 root root    257 Nov  2 17:12 64-xorg-xkb.rules
-rwxr-xr-x 1 root root    157 Jan  3 11:14 66-snapd-autoimport.rules*
-rw-r--r-- 1 root root    606 Mar  3  2016 66-xorg-synaptics-quirks.rules
-rw-r--r-- 1 root root   5219 Nov  6  2015 69-cd-sensors.rules
-rw-r--r-- 1 root root 165557 Jan 26  2016 69-libmtp.rules
-rw-r--r-- 1 root root   4250 Apr 16  2016 69-lvm-metad.rules
-rw-r--r-- 1 root root   1142 Mar  3  2016 69-wacom.rules
-rw-r--r-- 1 root root    170 Mar  3  2016 69-xorg-vmmouse.rules
-rw-r--r-- 1 root root    231 Jan 13 04:30 70-debian-uaccess.rules
-rw-r--r-- 1 root root    734 Jan 18 16:03 70-mouse.rules
-rw-r--r-- 1 root root    942 Jan 18 16:03 70-power-switch.rules
-rw-r--r-- 1 root root    462 Mar  7  2016 70-printers.rules
-rw-r--r-- 1 root root   2591 Jan 18 16:03 70-uaccess.rules
-rw-r--r-- 1 root root    461 Jan 18 16:04 71-power-switch-proliant.rules
-rw-r--r-- 1 root root   2710 Jan 18 16:04 71-seat.rules
-rw-r--r-- 1 root root    429 Aug 25 03:57 71-u-d-c-gpu-detection.rules
-rw-r--r-- 1 root root    596 Jan 18 16:04 73-seat-late.rules
-rw-r--r-- 1 root root    746 Jan 13 04:30 73-special-net-names.rules
-rw-r--r-- 1 root root    608 Jan 12 08:08 73-usb-net-by-mac.rules
-rw-r--r-- 1 root root    452 Jan 18 16:03 75-net-description.rules
-rw-r--r-- 1 root root    174 Jan 18 16:03 75-probe_mtd.rules
-rw-r--r-- 1 root root    484 Nov  4  2015 77-mm-cinterion-port-types.rules
-rw-r--r-- 1 root root   6910 Nov  4  2015 77-mm-ericsson-mbm.rules
-rw-r--r-- 1 root root   1734 Nov  4  2015 77-mm-huawei-net-port-types.rules
-rw-r--r-- 1 root root  13187 Nov  4  2015 77-mm-longcheer-port-types.rules
-rw-r--r-- 1 root root   2479 Nov  4  2015 77-mm-mtk-port-types.rules
-rw-r--r-- 1 root root   2024 Nov  4  2015 77-mm-nokia-port-types.rules
-rw-r--r-- 1 root root    383 Nov  4  2015 77-mm-pcmcia-device-blacklist.rules
-rw-r--r-- 1 root root    514 Nov  4  2015 77-mm-platform-serial-whitelist.rules
-rw-r--r-- 1 root root   3155 Nov  4  2015 77-mm-qdl-device-blacklist.rules
-rw-r--r-- 1 root root   1840 Nov  4  2015 77-mm-simtech-port-types.rules
-rw-r--r-- 1 root root   2929 Nov  4  2015 77-mm-telit-port-types.rules
-rw-r--r-- 1 root root   6705 Nov  4  2015 77-mm-usb-device-blacklist.rules
-rw-r--r-- 1 root root   2452 Nov  4  2015 77-mm-usb-serial-adapters-greylist.rules
-rw-r--r-- 1 root root   3666 Nov  4  2015 77-mm-x22x-port-types.rules
-rw-r--r-- 1 root root  14421 Nov  4  2015 77-mm-zte-port-types.rules
-rw-r--r-- 1 root root    965 Jan 18 16:04 78-graphics-card.rules
-rw-r--r-- 1 root root   4505 Jan 18 16:03 78-sound-card.rules
-rw-r--r-- 1 root root   1375 Jan 12 08:08 80-debian-compat.rules
-rw-r--r-- 1 root root    618 Jan 18 16:03 80-drivers.rules
-rw-r--r-- 1 root root    190 Nov 30 11:15 80-ifupdown.rules
-rw-r--r-- 1 root root    796 Nov  4  2015 80-mm-candidate.rules
-rw-r--r-- 1 root root    292 Jan 18 16:03 80-net-setup-link.rules
-rw-r--r-- 1 root root    146 Jan  3 11:14 80-snappy-assign.rules
-rw-r--r-- 1 root root   8179 Apr  1  2016 80-udisks2.rules
-rw-r--r-- 1 root root    523 Sep 27 10:09 84-nm-drivers.rules
-rw-r--r-- 1 root root  10560 Apr 28  2016 85-brltty.rules
-rw-r--r-- 1 root root     82 Mar 17  2016 85-hdparm.rules
-rw-r--r-- 1 root root    396 Apr  4  2016 85-keyboard-configuration.rules
-rw-r--r-- 1 root root   1682 Sep 27 10:09 85-nm-unmanaged.rules
-rw-r--r-- 1 root root    221 Nov 18  2014 85-regulatory.rules
-rw-r--r-- 1 root root    489 Apr 14  2016 90-alsa-restore.rules
-rw-r--r-- 1 root root   1632 Aug 17 08:18 90-fwupd-devices.rules
-rw-r--r-- 1 root root   1850 Apr 13  2016 90-libgpod.rules
-rw-r--r-- 1 root root   6640 Jan  5 18:31 90-pulseaudio.rules
-rw-r--r-- 1 root root    847 Nov  6  2015 95-cd-devices.rules
-rw-r--r-- 1 root root   1972 Nov 10 04:48 95-kpartx.rules
-rw-r--r-- 1 root root   2496 Jun 15  2016 95-upower-csr.rules
-rw-r--r-- 1 root root   8109 Jun 15  2016 95-upower-hid.rules
-rw-r--r-- 1 root root    354 Jun 15  2016 95-upower-wup.rules
-rw-r--r-- 1 root root    372 Feb 18  2014 97-dmraid.rules
-rw-r--r-- 1 root root   1518 Mar  1  2016 97-hid2hci.rules
-rw-r--r-- 1 root root   3866 Jan 18 16:04 99-systemd.rules
tracy@tracy:~$ cat /lib/udev/rules.d/40-libsane.rules | grep -iA2 brother
# If your scanner is supported by some external backend (brother, epkowa,
# hpaio, etc) please ask the author of the backend to provide proper
# device detection support for your OS
--
# Brother scanners
ATTRS{idVendor}=="04f9", ENV{libsane_matched}="yes"
LABEL="libsane_rules_end"


```

---

### Post by DuckHook on 2017-01-27
> **mollie4168 said:**
> This was why I modified the code for x86_64-linux-gnu as noted in the locate code above.  Is that where I went wrong?
No, I don't believe so. I think the newer install tool puts the drivers into the directory that you used, so it was a good guess. In any case, you have no /usr/lib64 directory, so the *cp* command was bound to fail.

I am rather intrigued by this: [https://ubuntuforums.org/showthread.php?t=2321613&p=13477477#post13477477](https://ubuntuforums.org/showthread.php?t=2321613&p=13477477#post13477477)
You might notice that this forum member has a working scanner, but two of his drivers are merely symlinks. They are really all the same driver, which is presumably the latest version. Are yours symlinks too?```
ls -laF /usr/lib/sane
``````
ls -laF /usr/lib/x86_64-linux-gnu/sane
```
You also mentioned that scanner stopped working about a year-and-a-half ago. I know it's a while back, but was this after an upgrade or update? Is your scanner on a static IP address?

Try turning on debug mode and then scan using command line as per this post: [https://ubuntuforums.org/showthread.php?t=2321613&p=13480927#post13480927](https://ubuntuforums.org/showthread.php?t=2321613&p=13480927#post13480927)

Pls post output back to this thread.

---

### Post by mollie4168 on 2017-01-27
My response was too long, so Part 1...

   > Are yours symlinks too?

```
ls -laF /usr/lib/sane
total 27704
drwxr-xr-x   2 root root   16384 Jan 24 20:16 ./
drwxr-xr-x 173 root root   28672 Jan 26 19:37 ../
-rw-r--r--   1 root root    8980 Jan 24 19:46 examples.desktop
-rw-r--r--   1 root root   13470 Jan 24 19:46 file.log
-rw-r--r--   1 root root 8095991 Jan 24 19:46 Firefox_wallpaper.png
-rw-r--r--   1 root root  238842 Jan 24 19:46 libgcrypt11_1.5.3-2ubuntu4.2_amd64.deb
-rw-r--r--   1 root root  237534 Jan 24 19:46 libgcrypt11_1.5.3-2ubuntu4.2_i386.deb
-rw-r--r--   1 root root     985 Jan 24 20:16 libsane-abaton.la
-rw-r--r--   1 root root   55520 Jan 24 20:16 libsane-abaton.so.1
-rw-r--r--   1 root root   55520 Jan 24 20:16 libsane-abaton.so.1.0.25
-rw-r--r--   1 root root    1006 Jan 24 20:16 libsane-agfafocus.la
-rw-r--r--   1 root root   67808 Jan 24 20:16 libsane-agfafocus.so.1
-rw-r--r--   1 root root   67808 Jan 24 20:16 libsane-agfafocus.so.1.0.25
-rw-r--r--   1 root root     978 Jan 24 20:16 libsane-apple.la
-rw-r--r--   1 root root   67848 Jan 24 20:16 libsane-apple.so.1
-rw-r--r--   1 root root   67848 Jan 24 20:16 libsane-apple.so.1.0.25
-rw-r--r--   1 root root    1041 Jan 24 20:16 libsane-artec_eplus48u.la
-rw-r--r--   1 root root  100440 Jan 24 20:16 libsane-artec_eplus48u.so.1
-rw-r--r--   1 root root  100440 Jan 24 20:16 libsane-artec_eplus48u.so.1.0.25
-rw-r--r--   1 root root     978 Jan 24 20:16 libsane-artec.la
-rw-r--r--   1 root root   84192 Jan 24 20:16 libsane-artec.so.1
-rw-r--r--   1 root root   84192 Jan 24 20:16 libsane-artec.so.1.0.25
-rw-r--r--   1 root root     971 Jan 24 20:16 libsane-as6e.la
-rw-r--r--   1 root root   30632 Jan 24 20:16 libsane-as6e.so.1
-rw-r--r--   1 root root   30632 Jan 24 20:16 libsane-as6e.so.1.0.25
-rw-r--r--   1 root root     992 Jan 24 20:16 libsane-avision.la
-rw-r--r--   1 root root  185072 Jan 24 20:16 libsane-avision.so.1
-rw-r--r--   1 root root  185072 Jan 24 20:16 libsane-avision.so.1.0.25
-rw-r--r--   1 root root     957 Jan 24 20:16 libsane-bh.la
-rw-r--r--   1 root root   89016 Jan 24 20:16 libsane-bh.so.1
-rw-r--r--   1 root root   89016 Jan 24 20:16 libsane-bh.so.1.0.25
lrwxrwxrwx   1 root root      35 Jun  6  2016 libsane-brother4.so -> /usr/lib/sane/libsane-brother4.so.1*
lrwxrwxrwx   1 root root      39 Jun  6  2016 libsane-brother4.so.1 -> /usr/lib/sane/libsane-brother4.so.1.0.7*
-rwxr-xr-x   1 root root  129696 Jun  6  2016 libsane-brother4.so.1.0.7*
-rw-r--r--   1 root root    1006 Jan 24 20:16 libsane-canon630u.la
-rw-r--r--   1 root root   72336 Jan 24 20:16 libsane-canon630u.so.1
-rw-r--r--   1 root root   72336 Jan 24 20:16 libsane-canon630u.so.1.0.25
-rw-r--r--   1 root root     999 Jan 24 20:16 libsane-canon_dr.la
-rw-r--r--   1 root root  162016 Jan 24 20:16 libsane-canon_dr.so.1
-rw-r--r--   1 root root  162016 Jan 24 20:16 libsane-canon_dr.so.1.0.25
-rw-r--r--   1 root root     978 Jan 24 20:16 libsane-canon.la
-rw-r--r--   1 root root     999 Jan 24 20:16 libsane-canon_pp.la
-rw-r--r--   1 root root   59448 Jan 24 20:16 libsane-canon_pp.so.1
-rw-r--r--   1 root root   59448 Jan 24 20:16 libsane-canon_pp.so.1.0.25
-rw-r--r--   1 root root   96504 Jan 24 20:16 libsane-canon.so.1
-rw-r--r--   1 root root   96504 Jan 24 20:16 libsane-canon.so.1.0.25
-rw-r--r--   1 root root     999 Jan 24 20:16 libsane-cardscan.la
-rw-r--r--   1 root root   63336 Jan 24 20:16 libsane-cardscan.so.1
-rw-r--r--   1 root root   63336 Jan 24 20:16 libsane-cardscan.so.1.0.25
-rw-r--r--   1 root root    1006 Jan 24 20:16 libsane-coolscan2.la
-rw-r--r--   1 root root  100576 Jan 24 20:16 libsane-coolscan2.so.1
-rw-r--r--   1 root root  100576 Jan 24 20:16 libsane-coolscan2.so.1.0.25
-rw-r--r--   1 root root    1006 Jan 24 20:16 libsane-coolscan3.la
-rw-r--r--   1 root root  104672 Jan 24 20:16 libsane-coolscan3.so.1
-rw-r--r--   1 root root  104672 Jan 24 20:16 libsane-coolscan3.so.1.0.25
-rw-r--r--   1 root root     999 Jan 24 20:16 libsane-coolscan.la
-rw-r--r--   1 root root  117448 Jan 24 20:16 libsane-coolscan.so.1
-rw-r--r--   1 root root  117448 Jan 24 20:16 libsane-coolscan.so.1.0.25
-rw-r--r--   1 root root     978 Jan 24 20:16 libsane-dc210.la
-rw-r--r--   1 root root   35416 Jan 24 20:16 libsane-dc210.so.1
-rw-r--r--   1 root root   35416 Jan 24 20:16 libsane-dc210.so.1.0.25
-rw-r--r--   1 root root     978 Jan 24 20:16 libsane-dc240.la
-rw-r--r--   1 root root   43720 Jan 24 20:16 libsane-dc240.so.1
-rw-r--r--   1 root root   43720 Jan 24 20:16 libsane-dc240.so.1.0.25
-rw-r--r--   1 root root     971 Jan 24 20:16 libsane-dc25.la
-rw-r--r--   1 root root   43808 Jan 24 20:16 libsane-dc25.so.1
-rw-r--r--   1 root root   43808 Jan 24 20:16 libsane-dc25.so.1.0.25
-rw-r--r--   1 root root    1034 Jan 24 20:16 libsane-dell1600n_net.la
-rw-r--r--   1 root root   38832 Jan 24 20:16 libsane-dell1600n_net.so.1
-rw-r--r--   1 root root   38832 Jan 24 20:16 libsane-dell1600n_net.so.1.0.25
-rw-r--r--   1 root root     964 Jan 24 20:16 libsane-dmc.la
-rw-r--r--   1 root root   55632 Jan 24 20:16 libsane-dmc.so.1
-rw-r--r--   1 root root   55632 Jan 24 20:16 libsane-dmc.so.1.0.25
-rw-r--r--   1 root root     992 Jan 24 20:16 libsane-epjitsu.la
-rw-r--r--   1 root root  106024 Jan 24 20:16 libsane-epjitsu.so.1
-rw-r--r--   1 root root  106024 Jan 24 20:16 libsane-epjitsu.so.1.0.25
-rw-r--r--   1 root root     985 Jan 24 20:16 libsane-epson2.la
-rw-r--r--   1 root root  188480 Jan 24 20:16 libsane-epson2.so.1
-rw-r--r--   1 root root  188480 Jan 24 20:16 libsane-epson2.so.1.0.25
-rw-r--r--   1 root root     992 Jan 24 20:16 libsane-epsonds.la
-rw-r--r--   1 root root  108904 Jan 24 20:16 libsane-epsonds.so.1
-rw-r--r--   1 root root  108904 Jan 24 20:16 libsane-epsonds.so.1.0.25
-rw-r--r--   1 root root     978 Jan 24 20:16 libsane-epson.la
-rw-r--r--   1 root root  131024 Jan 24 20:16 libsane-epson.so.1
-rw-r--r--   1 root root  131024 Jan 24 20:16 libsane-epson.so.1.0.25
-rw-r--r--   1 root root     992 Jan 24 20:16 libsane-fujitsu.la
-rw-r--r--   1 root root  198880 Jan 24 20:16 libsane-fujitsu.so.1
-rw-r--r--   1 root root  198880 Jan 24 20:16 libsane-fujitsu.so.1.0.25
-rw-r--r--   1 root root     992 Jan 24 20:16 libsane-genesys.la
-rw-r--r--   1 root root  540000 Jan 24 20:16 libsane-genesys.so.1
-rw-r--r--   1 root root  540000 Jan 24 20:16 libsane-genesys.so.1.0.25
-rw-r--r--   1 root root   55744 Jan 24 20:16 libsane-geniusvp2.so.1
-rw-r--r--   1 root root   55744 Jan 24 20:16 libsane-geniusvp2.so.1.0.22
-rw-r--r--   1 root root     992 Jan 24 20:16 libsane-gphoto2.la
-rw-r--r--   1 root root   43584 Jan 24 20:16 libsane-gphoto2.so.1
-rw-r--r--   1 root root   43584 Jan 24 20:16 libsane-gphoto2.so.1.0.25
-rw-r--r--   1 root root     985 Jan 24 20:16 libsane-gt68xx.la
-rw-r--r--   1 root root  166168 Jan 24 20:16 libsane-gt68xx.so.1
-rw-r--r--   1 root root  166168 Jan 24 20:16 libsane-gt68xx.so.1.0.25
-rw-r--r--   1 root root     985 Jan 24 20:16 libsane-hp3500.la
-rw-r--r--   1 root root   80064 Jan 24 20:16 libsane-hp3500.so.1
-rw-r--r--   1 root root   80064 Jan 24 20:16 libsane-hp3500.so.1.0.25
-rw-r--r--   1 root root     985 Jan 24 20:16 libsane-hp3900.la
-rw-r--r--   1 root root  427880 Jan 24 20:16 libsane-hp3900.so.1
-rw-r--r--   1 root root  427880 Jan 24 20:16 libsane-hp3900.so.1.0.25
-rw-r--r--   1 root root     985 Jan 24 20:16 libsane-hp4200.la
-rw-r--r--   1 root root   71784 Jan 24 20:16 libsane-hp4200.so.1
-rw-r--r--   1 root root   71784 Jan 24 20:16 libsane-hp4200.so.1.0.25
-rw-r--r--   1 root root     985 Jan 24 20:16 libsane-hp5400.la
-rw-r--r--   1 root root   67448 Jan 24 20:16 libsane-hp5400.so.1
-rw-r--r--   1 root root   67448 Jan 24 20:16 libsane-hp5400.so.1.0.25
-rw-r--r--   1 root root     985 Jan 24 20:16 libsane-hp5590.la
-rw-r--r--   1 root root   83968 Jan 24 20:16 libsane-hp5590.so.1
-rw-r--r--   1 root root   83968 Jan 24 20:16 libsane-hp5590.so.1.0.25
-rw-r--r--   1 root root  165800 Jan 24 20:16 libsane-hpaio.so.1
-rw-r--r--   1 root root  165800 Jan 24 20:16 libsane-hpaio.so.1.0.0
-rw-r--r--   1 root root     957 Jan 24 20:16 libsane-hp.la
-rw-r--r--   1 root root    1006 Jan 24 20:16 libsane-hpljm1005.la
-rw-r--r--   1 root root   59424 Jan 24 20:16 libsane-hpljm1005.so.1
-rw-r--r--   1 root root   59424 Jan 24 20:16 libsane-hpljm1005.so.1.0.25
-rw-r--r--   1 root root     985 Jan 24 20:16 libsane-hpsj5s.la
-rw-r--r--   1 root root   34952 Jan 24 20:16 libsane-hpsj5s.so.1
-rw-r--r--   1 root root   34952 Jan 24 20:16 libsane-hpsj5s.so.1.0.25
-rw-r--r--   1 root root  192248 Jan 24 20:16 libsane-hp.so.1
-rw-r--r--   1 root root  192248 Jan 24 20:16 libsane-hp.so.1.0.25
-rw-r--r--   1 root root     971 Jan 24 20:16 libsane-hs2p.la
-rw-r--r--   1 root root  115488 Jan 24 20:16 libsane-hs2p.so.1
-rw-r--r--   1 root root  115488 Jan 24 20:16 libsane-hs2p.so.1.0.25
-rw-r--r--   1 root root     964 Jan 24 20:16 libsane-ibm.la
-rw-r--r--   1 root root   59624 Jan 24 20:16 libsane-ibm.so.1
-rw-r--r--   1 root root   59624 Jan 24 20:16 libsane-ibm.so.1.0.25
-rw-r--r--   1 root root     999 Jan 24 20:16 libsane-kodakaio.la
-rw-r--r--   1 root root  120896 Jan 24 20:16 libsane-kodakaio.so.1
-rw-r--r--   1 root root  120896 Jan 24 20:16 libsane-kodakaio.so.1.0.25
-rw-r--r--   1 root root     978 Jan 24 20:16 libsane-kodak.la
-rw-r--r--   1 root root   71904 Jan 24 20:16 libsane-kodak.so.1
-rw-r--r--   1 root root   71904 Jan 24 20:16 libsane-kodak.so.1.0.25
-rw-r--r--   1 root root     992 Jan 24 20:16 libsane-kvs1025.la
-rw-r--r--   1 root root  109128 Jan 24 20:16 libsane-kvs1025.so.1
-rw-r--r--   1 root root  109128 Jan 24 20:16 libsane-kvs1025.so.1.0.25
-rw-r--r--   1 root root     992 Jan 24 20:16 libsane-kvs20xx.la
-rw-r--r--   1 root root   88736 Jan 24 20:16 libsane-kvs20xx.so.1
-rw-r--r--   1 root root   88736 Jan 24 20:16 libsane-kvs20xx.so.1.0.25
-rw-r--r--   1 root root     992 Jan 24 20:16 libsane-kvs40xx.la
-rw-r--r--   1 root root  101600 Jan 24 20:16 libsane-kvs40xx.so.1
-rw-r--r--   1 root root  101600 Jan 24 20:16 libsane-kvs40xx.so.1.0.25
-rw-r--r--   1 root root     964 Jan 24 20:16 libsane-leo.la
-rw-r--r--   1 root root   63840 Jan 24 20:16 libsane-leo.so.1
-rw-r--r--   1 root root   63840 Jan 24 20:16 libsane-leo.so.1.0.25
-rw-r--r--   1 root root     992 Jan 24 20:16 libsane-lexmark.la
-rw-r--r--   1 root root  100992 Jan 24 20:16 libsane-lexmark.so.1
-rw-r--r--   1 root root  100992 Jan 24 20:16 libsane-lexmark.so.1.0.25
-rw-r--r--   1 root root   72264 Jan 24 20:16 libsane-ls5000.so.1
-rw-r--r--   1 root root   72264 Jan 24 20:16 libsane-ls5000.so.1.0.22
-rw-r--r--   1 root root     985 Jan 24 20:16 libsane-ma1509.la
-rw-r--r--   1 root root   71672 Jan 24 20:16 libsane-ma1509.so.1
-rw-r--r--   1 root root   71672 Jan 24 20:16 libsane-ma1509.so.1.0.25
-rw-r--r--   1 root root    1006 Jan 24 20:16 libsane-magicolor.la
-rw-r--r--   1 root root  100952 Jan 24 20:16 libsane-magicolor.so.1
-rw-r--r--   1 root root  100952 Jan 24 20:16 libsane-magicolor.so.1.0.25
-rw-r--r--   1 root root    1013 Jan 24 20:16 libsane-matsushita.la
-rw-r--r--   1 root root   68240 Jan 24 20:16 libsane-matsushita.so.1
-rw-r--r--   1 root root   68240 Jan 24 20:16 libsane-matsushita.so.1.0.25
-rw-r--r--   1 root root    1006 Jan 24 20:16 libsane-microtek2.la
-rw-r--r--   1 root root  137440 Jan 24 20:16 libsane-microtek2.so.1
-rw-r--r--   1 root root  137440 Jan 24 20:16 libsane-microtek2.so.1.0.25
-rw-r--r--   1 root root     999 Jan 24 20:16 libsane-microtek.la
-rw-r--r--   1 root root   96704 Jan 24 20:16 libsane-microtek.so.1
-rw-r--r--   1 root root   96704 Jan 24 20:16 libsane-microtek.so.1.0.25
-rw-r--r--   1 root root     985 Jan 24 20:16 libsane-mustek.la
-rw-r--r--   1 root root    1006 Jan 24 20:16 libsane-mustek_pp.la
-rw-r--r--   1 root root  104920 Jan 24 20:16 libsane-mustek_pp.so.1
-rw-r--r--   1 root root  104920 Jan 24 20:16 libsane-mustek_pp.so.1.0.25
-rw-r--r--   1 root root  162664 Jan 24 20:16 libsane-mustek.so.1
-rw-r--r--   1 root root  162664 Jan 24 20:16 libsane-mustek.so.1.0.25
-rw-r--r--   1 root root    1020 Jan 24 20:16 libsane-mustek_usb2.la
-rw-r--r--   1 root root  161960 Jan 24 20:16 libsane-mustek_usb2.so.1
-rw-r--r--   1 root root  161960 Jan 24 20:16 libsane-mustek_usb2.so.1.0.25
-rw-r--r--   1 root root    1013 Jan 24 20:16 libsane-mustek_usb.la
-rw-r--r--   1 root root  170096 Jan 24 20:16 libsane-mustek_usb.so.1
-rw-r--r--   1 root root  170096 Jan 24 20:16 libsane-mustek_usb.so.1.0.25
-rw-r--r--   1 root root     964 Jan 24 20:16 libsane-nec.la
-rw-r--r--   1 root root   72056 Jan 24 20:16 libsane-nec.so.1
-rw-r--r--   1 root root   72056 Jan 24 20:16 libsane-nec.so.1.0.25
-rw-r--r--   1 root root     964 Jan 24 20:16 libsane-net.la
-rw-r--r--   1 root root   63328 Jan 24 20:16 libsane-net.so.1
-rw-r--r--   1 root root   63328 Jan 24 20:16 libsane-net.so.1.0.25
-rw-r--r--   1 root root     978 Jan 24 20:16 libsane-niash.la
-rw-r--r--   1 root root   72032 Jan 24 20:16 libsane-niash.so.1
-rw-r--r--   1 root root   72032 Jan 24 20:16 libsane-niash.so.1.0.25
-rw-r--r--   1 root root     957 Jan 24 20:16 libsane-p5.la
-rw-r--r--   1 root root   51264 Jan 24 20:16 libsane-p5.so.1
-rw-r--r--   1 root root   51264 Jan 24 20:16 libsane-p5.so.1.0.25
-rw-r--r--   1 root root     964 Jan 24 20:16 libsane-pie.la
-rw-r--r--   1 root root   84240 Jan 24 20:16 libsane-pie.so.1
-rw-r--r--   1 root root   84240 Jan 24 20:16 libsane-pie.so.1.0.25
-rw-r--r--   1 root root     978 Jan 24 20:16 libsane-pixma.la
-rw-r--r--   1 root root  190472 Jan 24 20:16 libsane-pixma.so.1
-rw-r--r--   1 root root  190472 Jan 24 20:16 libsane-pixma.so.1.0.25
-rw-r--r--   1 root root     992 Jan 24 20:16 libsane-plustek.la
-rw-r--r--   1 root root    1013 Jan 24 20:16 libsane-plustek_pp.la
-rw-r--r--   1 root root  186520 Jan 24 20:16 libsane-plustek_pp.so.1
-rw-r--r--   1 root root  186520 Jan 24 20:16 libsane-plustek_pp.so.1.0.25
-rw-r--r--   1 root root  231456 Jan 24 20:16 libsane-plustek.so.1
-rw-r--r--   1 root root  231456 Jan 24 20:16 libsane-plustek.so.1.0.25
-rw-r--r--   1 root root     964 Jan 24 20:16 libsane-pnm.la
-rw-r--r--   1 root root   40456 Jan 24 20:16 libsane-pnm.so.1
-rw-r--r--   1 root root   40456 Jan 24 20:16 libsane-pnm.so.1.0.25
-rw-r--r--   1 root root     971 Jan 24 20:16 libsane-qcam.la
-rw-r--r--   1 root root   51216 Jan 24 20:16 libsane-qcam.so.1
-rw-r--r--   1 root root   51216 Jan 24 20:16 libsane-qcam.so.1.0.25
-rw-r--r--   1 root root     978 Jan 24 20:16 libsane-ricoh.la
-rw-r--r--   1 root root   55528 Jan 24 20:16 libsane-ricoh.so.1
-rw-r--r--   1 root root   55528 Jan 24 20:16 libsane-ricoh.so.1.0.25
-rw-r--r--   1 root root     992 Jan 24 20:16 libsane-rts8891.la
-rw-r--r--   1 root root  158208 Jan 24 20:16 libsane-rts8891.so.1
-rw-r--r--   1 root root  158208 Jan 24 20:16 libsane-rts8891.so.1.0.25
-rw-r--r--   1 root root     978 Jan 24 20:16 libsane-s9036.la
-rw-r--r--   1 root root   55536 Jan 24 20:16 libsane-s9036.so.1
-rw-r--r--   1 root root   55536 Jan 24 20:16 libsane-s9036.so.1.0.25
-rw-r--r--   1 root root     992 Jan 24 20:16 libsane-sceptre.la
-rw-r--r--   1 root root   63712 Jan 24 20:16 libsane-sceptre.so.1
-rw-r--r--   1 root root   63712 Jan 24 20:16 libsane-sceptre.so.1.0.25
-rw-r--r--   1 root root     978 Jan 24 20:16 libsane-sharp.la
-rw-r--r--   1 root root   84496 Jan 24 20:16 libsane-sharp.so.1
-rw-r--r--   1 root root   84496 Jan 24 20:16 libsane-sharp.so.1.0.25
-rw-r--r--   1 root root     985 Jan 24 20:16 libsane-sm3600.la
-rw-r--r--   1 root root   72176 Jan 24 20:16 libsane-sm3600.so.1
-rw-r--r--   1 root root   72176 Jan 24 20:16 libsane-sm3600.so.1.0.25
-rw-r--r--   1 root root     985 Jan 24 20:16 libsane-sm3840.la
-rw-r--r--   1 root root   92080 Jan 24 20:16 libsane-sm3840.so.1
-rw-r--r--   1 root root   92080 Jan 24 20:16 libsane-sm3840.so.1.0.25
-rw-r--r--   1 root root     999 Jan 24 20:16 libsane-snapscan.la
-rw-r--r--   1 root root  213248 Jan 24 20:16 libsane-snapscan.so.1
-rw-r--r--   1 root root  213248 Jan 24 20:16 libsane-snapscan.so.1.0.25
-rw-r--r--   1 root root     978 Jan 24 20:16 libsane-sp15c.la
-rw-r--r--   1 root root   68040 Jan 24 20:16 libsane-sp15c.so.1
-rw-r--r--   1 root root   68040 Jan 24 20:16 libsane-sp15c.so.1.0.25
-rw-r--r--   1 root root     978 Jan 24 20:16 libsane-st400.la
-rw-r--r--   1 root root   55872 Jan 24 20:16 libsane-st400.so.1
-rw-r--r--   1 root root   55872 Jan 24 20:16 libsane-st400.so.1.0.25
-rw-r--r--   1 root root     985 Jan 24 20:16 libsane-stv680.la
-rw-r--r--   1 root root   75752 Jan 24 20:16 libsane-stv680.so.1
-rw-r--r--   1 root root   75752 Jan 24 20:16 libsane-stv680.so.1.0.25
-rw-r--r--   1 root root     999 Jan 24 20:16 libsane-tamarack.la
-rw-r--r--   1 root root   59616 Jan 24 20:16 libsane-tamarack.so.1
-rw-r--r--   1 root root   59616 Jan 24 20:16 libsane-tamarack.so.1.0.25
-rw-r--r--   1 root root     978 Jan 24 20:16 libsane-teco1.la
-rw-r--r--   1 root root   63872 Jan 24 20:16 libsane-teco1.so.1
-rw-r--r--   1 root root   63872 Jan 24 20:16 libsane-teco1.so.1.0.25
-rw-r--r--   1 root root     978 Jan 24 20:16 libsane-teco2.la
-rw-r--r--   1 root root   72064 Jan 24 20:16 libsane-teco2.so.1
-rw-r--r--   1 root root   72064 Jan 24 20:16 libsane-teco2.so.1.0.25
-rw-r--r--   1 root root     978 Jan 24 20:16 libsane-teco3.la
-rw-r--r--   1 root root   63872 Jan 24 20:16 libsane-teco3.so.1
-rw-r--r--   1 root root   63872 Jan 24 20:16 libsane-teco3.so.1.0.25
-rw-r--r--   1 root root     971 Jan 24 20:16 libsane-test.la
-rw-r--r--   1 root root   72688 Jan 24 20:16 libsane-test.so.1
-rw-r--r--   1 root root   72688 Jan 24 20:16 libsane-test.so.1.0.25
-rw-r--r--   1 root root     964 Jan 24 20:16 libsane-u12.la
-rw-r--r--   1 root root  122512 Jan 24 20:16 libsane-u12.so.1
-rw-r--r--   1 root root  122512 Jan 24 20:16 libsane-u12.so.1.0.25
-rw-r--r--   1 root root    1006 Jan 24 20:16 libsane-umax1220u.la
-rw-r--r--   1 root root   92688 Jan 24 20:16 libsane-umax1220u.so.1
-rw-r--r--   1 root root   92688 Jan 24 20:16 libsane-umax1220u.so.1.0.25
-rw-r--r--   1 root root     971 Jan 24 20:16 libsane-umax.la
-rw-r--r--   1 root root     992 Jan 24 20:16 libsane-umax_pp.la
-rw-r--r--   1 root root  211976 Jan 24 20:16 libsane-umax_pp.so.1
-rw-r--r--   1 root root  211976 Jan 24 20:16 libsane-umax_pp.so.1.0.25
-rw-r--r--   1 root root  179808 Jan 24 20:16 libsane-umax.so.1
-rw-r--r--   1 root root  179808 Jan 24 20:16 libsane-umax.so.1.0.25
-rw-r--r--   1 root root    1006 Jan 24 20:16 libsane-xerox_mfp.la
-rw-r--r--   1 root root   71720 Jan 24 20:16 libsane-xerox_mfp.so.1
-rw-r--r--   1 root root   71720 Jan 24 20:16 libsane-xerox_mfp.so.1.0.25
-rwxr-xr-x   1 root root     606 Jan 24 19:46 manifest.xml*
-rw-r--r--   1 root root     117 Jan 24 19:46 myclamz~
-rw-r--r--   1 root root     117 Jan 24 19:46 myclamz.sh~
-rw-------   1 root root       1 Jan 24 19:46 nano.save
-rw-------   1 root root      74 Jan 24 19:46 sudo.save
-rw-r--r--   1 root root    6430 Jan 24 19:46 wireless-info.tar.gz
-rw-r--r--   1 root root   31753 Jan 24 19:46 wireless-info.txt
-rwxr-xr-x   1 root root   13362 Jan 24 19:46 wireless_script*
```

```
ls -laF /usr/lib/x86_64-linux-gnu/sane 
total 9848
drwxr-xr-x   2 root root  40960 Aug  1 20:53 ./
drwxr-xr-x 127 root root 110592 Jan 26 19:07 ../
-rw-r--r--   1 root root    985 Sep 18  2015 libsane-abaton.la
lrwxrwxrwx   1 root root     24 Sep 18  2015 libsane-abaton.so.1 -> libsane-abaton.so.1.0.25
-rw-r--r--   1 root root  55520 Sep 18  2015 libsane-abaton.so.1.0.25
-rw-r--r--   1 root root   1006 Sep 18  2015 libsane-agfafocus.la
lrwxrwxrwx   1 root root     27 Sep 18  2015 libsane-agfafocus.so.1 -> libsane-agfafocus.so.1.0.25
-rw-r--r--   1 root root  67808 Sep 18  2015 libsane-agfafocus.so.1.0.25
-rw-r--r--   1 root root    978 Sep 18  2015 libsane-apple.la
lrwxrwxrwx   1 root root     23 Sep 18  2015 libsane-apple.so.1 -> libsane-apple.so.1.0.25
-rw-r--r--   1 root root  67848 Sep 18  2015 libsane-apple.so.1.0.25
-rw-r--r--   1 root root   1041 Sep 18  2015 libsane-artec_eplus48u.la
lrwxrwxrwx   1 root root     32 Sep 18  2015 libsane-artec_eplus48u.so.1 -> libsane-artec_eplus48u.so.1.0.25
-rw-r--r--   1 root root 100440 Sep 18  2015 libsane-artec_eplus48u.so.1.0.25
-rw-r--r--   1 root root    978 Sep 18  2015 libsane-artec.la
lrwxrwxrwx   1 root root     23 Sep 18  2015 libsane-artec.so.1 -> libsane-artec.so.1.0.25
-rw-r--r--   1 root root  84192 Sep 18  2015 libsane-artec.so.1.0.25
-rw-r--r--   1 root root    971 Sep 18  2015 libsane-as6e.la
lrwxrwxrwx   1 root root     22 Sep 18  2015 libsane-as6e.so.1 -> libsane-as6e.so.1.0.25
-rw-r--r--   1 root root  30632 Sep 18  2015 libsane-as6e.so.1.0.25
-rw-r--r--   1 root root    992 Sep 18  2015 libsane-avision.la
lrwxrwxrwx   1 root root     25 Sep 18  2015 libsane-avision.so.1 -> libsane-avision.so.1.0.25
-rw-r--r--   1 root root 185072 Sep 18  2015 libsane-avision.so.1.0.25
-rw-r--r--   1 root root    957 Sep 18  2015 libsane-bh.la
lrwxrwxrwx   1 root root     20 Sep 18  2015 libsane-bh.so.1 -> libsane-bh.so.1.0.25
-rw-r--r--   1 root root  89016 Sep 18  2015 libsane-bh.so.1.0.25
lrwxrwxrwx   1 root root     41 Jan  3  2015 libsane-brother4.so -> /usr/lib64/sane/libsane-brother4.so.1.0.7
lrwxrwxrwx   1 root root     41 Jan  3  2015 libsane-brother4.so.1 -> /usr/lib64/sane/libsane-brother4.so.1.0.7
lrwxrwxrwx   1 root root     41 Jan  3  2015 libsane-brother4.so.1.0.7 -> /usr/lib64/sane/libsane-brother4.so.1.0.7
-rw-r--r--   1 root root   1006 Sep 18  2015 libsane-canon630u.la
lrwxrwxrwx   1 root root     27 Sep 18  2015 libsane-canon630u.so.1 -> libsane-canon630u.so.1.0.25
-rw-r--r--   1 root root  72336 Sep 18  2015 libsane-canon630u.so.1.0.25
-rw-r--r--   1 root root    999 Sep 18  2015 libsane-canon_dr.la
lrwxrwxrwx   1 root root     26 Sep 18  2015 libsane-canon_dr.so.1 -> libsane-canon_dr.so.1.0.25
-rw-r--r--   1 root root 162016 Sep 18  2015 libsane-canon_dr.so.1.0.25
-rw-r--r--   1 root root    978 Sep 18  2015 libsane-canon.la
-rw-r--r--   1 root root    999 Sep 18  2015 libsane-canon_pp.la
lrwxrwxrwx   1 root root     26 Sep 18  2015 libsane-canon_pp.so.1 -> libsane-canon_pp.so.1.0.25
-rw-r--r--   1 root root  59448 Sep 18  2015 libsane-canon_pp.so.1.0.25
lrwxrwxrwx   1 root root     23 Sep 18  2015 libsane-canon.so.1 -> libsane-canon.so.1.0.25
-rw-r--r--   1 root root  96504 Sep 18  2015 libsane-canon.so.1.0.25
-rw-r--r--   1 root root    999 Sep 18  2015 libsane-cardscan.la
lrwxrwxrwx   1 root root     26 Sep 18  2015 libsane-cardscan.so.1 -> libsane-cardscan.so.1.0.25
-rw-r--r--   1 root root  63336 Sep 18  2015 libsane-cardscan.so.1.0.25
-rw-r--r--   1 root root   1006 Sep 18  2015 libsane-coolscan2.la
lrwxrwxrwx   1 root root     27 Sep 18  2015 libsane-coolscan2.so.1 -> libsane-coolscan2.so.1.0.25
-rw-r--r--   1 root root 100576 Sep 18  2015 libsane-coolscan2.so.1.0.25
-rw-r--r--   1 root root   1006 Sep 18  2015 libsane-coolscan3.la
lrwxrwxrwx   1 root root     27 Sep 18  2015 libsane-coolscan3.so.1 -> libsane-coolscan3.so.1.0.25
-rw-r--r--   1 root root 104672 Sep 18  2015 libsane-coolscan3.so.1.0.25
-rw-r--r--   1 root root    999 Sep 18  2015 libsane-coolscan.la
lrwxrwxrwx   1 root root     26 Sep 18  2015 libsane-coolscan.so.1 -> libsane-coolscan.so.1.0.25
-rw-r--r--   1 root root 117448 Sep 18  2015 libsane-coolscan.so.1.0.25
-rw-r--r--   1 root root    978 Sep 18  2015 libsane-dc210.la
lrwxrwxrwx   1 root root     23 Sep 18  2015 libsane-dc210.so.1 -> libsane-dc210.so.1.0.25
-rw-r--r--   1 root root  35416 Sep 18  2015 libsane-dc210.so.1.0.25
-rw-r--r--   1 root root    978 Sep 18  2015 libsane-dc240.la
lrwxrwxrwx   1 root root     23 Sep 18  2015 libsane-dc240.so.1 -> libsane-dc240.so.1.0.25
-rw-r--r--   1 root root  43720 Sep 18  2015 libsane-dc240.so.1.0.25
-rw-r--r--   1 root root    971 Sep 18  2015 libsane-dc25.la
lrwxrwxrwx   1 root root     22 Sep 18  2015 libsane-dc25.so.1 -> libsane-dc25.so.1.0.25
-rw-r--r--   1 root root  43808 Sep 18  2015 libsane-dc25.so.1.0.25
-rw-r--r--   1 root root   1034 Sep 18  2015 libsane-dell1600n_net.la
lrwxrwxrwx   1 root root     31 Sep 18  2015 libsane-dell1600n_net.so.1 -> libsane-dell1600n_net.so.1.0.25
-rw-r--r--   1 root root  38832 Sep 18  2015 libsane-dell1600n_net.so.1.0.25
-rw-r--r--   1 root root    964 Sep 18  2015 libsane-dmc.la
lrwxrwxrwx   1 root root     21 Sep 18  2015 libsane-dmc.so.1 -> libsane-dmc.so.1.0.25
-rw-r--r--   1 root root  55632 Sep 18  2015 libsane-dmc.so.1.0.25
-rw-r--r--   1 root root    992 Sep 18  2015 libsane-epjitsu.la
lrwxrwxrwx   1 root root     25 Sep 18  2015 libsane-epjitsu.so.1 -> libsane-epjitsu.so.1.0.25
-rw-r--r--   1 root root 106024 Sep 18  2015 libsane-epjitsu.so.1.0.25
-rw-r--r--   1 root root    985 Sep 18  2015 libsane-epson2.la
lrwxrwxrwx   1 root root     24 Sep 18  2015 libsane-epson2.so.1 -> libsane-epson2.so.1.0.25
-rw-r--r--   1 root root 188480 Sep 18  2015 libsane-epson2.so.1.0.25
-rw-r--r--   1 root root    992 Sep 18  2015 libsane-epsonds.la
lrwxrwxrwx   1 root root     25 Sep 18  2015 libsane-epsonds.so.1 -> libsane-epsonds.so.1.0.25
-rw-r--r--   1 root root 108904 Sep 18  2015 libsane-epsonds.so.1.0.25
-rw-r--r--   1 root root    978 Sep 18  2015 libsane-epson.la
lrwxrwxrwx   1 root root     23 Sep 18  2015 libsane-epson.so.1 -> libsane-epson.so.1.0.25
-rw-r--r--   1 root root 131024 Sep 18  2015 libsane-epson.so.1.0.25
-rw-r--r--   1 root root    992 Sep 18  2015 libsane-fujitsu.la
lrwxrwxrwx   1 root root     25 Sep 18  2015 libsane-fujitsu.so.1 -> libsane-fujitsu.so.1.0.25
-rw-r--r--   1 root root 198880 Sep 18  2015 libsane-fujitsu.so.1.0.25
-rw-r--r--   1 root root    992 Sep 18  2015 libsane-genesys.la
lrwxrwxrwx   1 root root     25 Sep 18  2015 libsane-genesys.so.1 -> libsane-genesys.so.1.0.25
-rw-r--r--   1 root root 540000 Sep 18  2015 libsane-genesys.so.1.0.25
lrwxrwxrwx   1 root root     27 Jan 29  2014 libsane-geniusvp2.so.1 -> libsane-geniusvp2.so.1.0.22
-rw-r--r--   1 root root  55744 Jan 29  2014 libsane-geniusvp2.so.1.0.22
-rw-r--r--   1 root root    992 Sep 18  2015 libsane-gphoto2.la
lrwxrwxrwx   1 root root     25 Sep 18  2015 libsane-gphoto2.so.1 -> libsane-gphoto2.so.1.0.25
-rw-r--r--   1 root root  43584 Sep 18  2015 libsane-gphoto2.so.1.0.25
-rw-r--r--   1 root root    985 Sep 18  2015 libsane-gt68xx.la
lrwxrwxrwx   1 root root     24 Sep 18  2015 libsane-gt68xx.so.1 -> libsane-gt68xx.so.1.0.25
-rw-r--r--   1 root root 166168 Sep 18  2015 libsane-gt68xx.so.1.0.25
-rw-r--r--   1 root root    985 Sep 18  2015 libsane-hp3500.la
lrwxrwxrwx   1 root root     24 Sep 18  2015 libsane-hp3500.so.1 -> libsane-hp3500.so.1.0.25
-rw-r--r--   1 root root  80064 Sep 18  2015 libsane-hp3500.so.1.0.25
-rw-r--r--   1 root root    985 Sep 18  2015 libsane-hp3900.la
lrwxrwxrwx   1 root root     24 Sep 18  2015 libsane-hp3900.so.1 -> libsane-hp3900.so.1.0.25
-rw-r--r--   1 root root 427880 Sep 18  2015 libsane-hp3900.so.1.0.25
-rw-r--r--   1 root root    985 Sep 18  2015 libsane-hp4200.la
lrwxrwxrwx   1 root root     24 Sep 18  2015 libsane-hp4200.so.1 -> libsane-hp4200.so.1.0.25
-rw-r--r--   1 root root  71784 Sep 18  2015 libsane-hp4200.so.1.0.25
-rw-r--r--   1 root root    985 Sep 18  2015 libsane-hp5400.la
lrwxrwxrwx   1 root root     24 Sep 18  2015 libsane-hp5400.so.1 -> libsane-hp5400.so.1.0.25
-rw-r--r--   1 root root  67448 Sep 18  2015 libsane-hp5400.so.1.0.25
-rw-r--r--   1 root root    985 Sep 18  2015 libsane-hp5590.la
lrwxrwxrwx   1 root root     24 Sep 18  2015 libsane-hp5590.so.1 -> libsane-hp5590.so.1.0.25
-rw-r--r--   1 root root  83968 Sep 18  2015 libsane-hp5590.so.1.0.25
lrwxrwxrwx   1 root root     22 Mar 29  2016 libsane-hpaio.so.1 -> libsane-hpaio.so.1.0.0
-rw-r--r--   1 root root 165800 Mar 29  2016 libsane-hpaio.so.1.0.0
-rw-r--r--   1 root root    957 Sep 18  2015 libsane-hp.la
-rw-r--r--   1 root root   1006 Sep 18  2015 libsane-hpljm1005.la
lrwxrwxrwx   1 root root     27 Sep 18  2015 libsane-hpljm1005.so.1 -> libsane-hpljm1005.so.1.0.25
-rw-r--r--   1 root root  59424 Sep 18  2015 libsane-hpljm1005.so.1.0.25
-rw-r--r--   1 root root    985 Sep 18  2015 libsane-hpsj5s.la
lrwxrwxrwx   1 root root     24 Sep 18  2015 libsane-hpsj5s.so.1 -> libsane-hpsj5s.so.1.0.25
-rw-r--r--   1 root root  34952 Sep 18  2015 libsane-hpsj5s.so.1.0.25
lrwxrwxrwx   1 root root     20 Sep 18  2015 libsane-hp.so.1 -> libsane-hp.so.1.0.25
-rw-r--r--   1 root root 192248 Sep 18  2015 libsane-hp.so.1.0.25
-rw-r--r--   1 root root    971 Sep 18  2015 libsane-hs2p.la
lrwxrwxrwx   1 root root     22 Sep 18  2015 libsane-hs2p.so.1 -> libsane-hs2p.so.1.0.25
-rw-r--r--   1 root root 115488 Sep 18  2015 libsane-hs2p.so.1.0.25
-rw-r--r--   1 root root    964 Sep 18  2015 libsane-ibm.la
lrwxrwxrwx   1 root root     21 Sep 18  2015 libsane-ibm.so.1 -> libsane-ibm.so.1.0.25
-rw-r--r--   1 root root  59624 Sep 18  2015 libsane-ibm.so.1.0.25
-rw-r--r--   1 root root    999 Sep 18  2015 libsane-kodakaio.la
lrwxrwxrwx   1 root root     26 Sep 18  2015 libsane-kodakaio.so.1 -> libsane-kodakaio.so.1.0.25
-rw-r--r--   1 root root 120896 Sep 18  2015 libsane-kodakaio.so.1.0.25
-rw-r--r--   1 root root    978 Sep 18  2015 libsane-kodak.la
lrwxrwxrwx   1 root root     23 Sep 18  2015 libsane-kodak.so.1 -> libsane-kodak.so.1.0.25
-rw-r--r--   1 root root  71904 Sep 18  2015 libsane-kodak.so.1.0.25
-rw-r--r--   1 root root    992 Sep 18  2015 libsane-kvs1025.la
lrwxrwxrwx   1 root root     25 Sep 18  2015 libsane-kvs1025.so.1 -> libsane-kvs1025.so.1.0.25
-rw-r--r--   1 root root 109128 Sep 18  2015 libsane-kvs1025.so.1.0.25
-rw-r--r--   1 root root    992 Sep 18  2015 libsane-kvs20xx.la
lrwxrwxrwx   1 root root     25 Sep 18  2015 libsane-kvs20xx.so.1 -> libsane-kvs20xx.so.1.0.25
-rw-r--r--   1 root root  88736 Sep 18  2015 libsane-kvs20xx.so.1.0.25
-rw-r--r--   1 root root    992 Sep 18  2015 libsane-kvs40xx.la
lrwxrwxrwx   1 root root     25 Sep 18  2015 libsane-kvs40xx.so.1 -> libsane-kvs40xx.so.1.0.25
-rw-r--r--   1 root root 101600 Sep 18  2015 libsane-kvs40xx.so.1.0.25
-rw-r--r--   1 root root    964 Sep 18  2015 libsane-leo.la
lrwxrwxrwx   1 root root     21 Sep 18  2015 libsane-leo.so.1 -> libsane-leo.so.1.0.25
-rw-r--r--   1 root root  63840 Sep 18  2015 libsane-leo.so.1.0.25
-rw-r--r--   1 root root    992 Sep 18  2015 libsane-lexmark.la
lrwxrwxrwx   1 root root     25 Sep 18  2015 libsane-lexmark.so.1 -> libsane-lexmark.so.1.0.25
-rw-r--r--   1 root root 100992 Sep 18  2015 libsane-lexmark.so.1.0.25
lrwxrwxrwx   1 root root     24 Jan 29  2014 libsane-ls5000.so.1 -> libsane-ls5000.so.1.0.22
-rw-r--r--   1 root root  72264 Jan 29  2014 libsane-ls5000.so.1.0.22
-rw-r--r--   1 root root    985 Sep 18  2015 libsane-ma1509.la
lrwxrwxrwx   1 root root     24 Sep 18  2015 libsane-ma1509.so.1 -> libsane-ma1509.so.1.0.25
-rw-r--r--   1 root root  71672 Sep 18  2015 libsane-ma1509.so.1.0.25
-rw-r--r--   1 root root   1006 Sep 18  2015 libsane-magicolor.la
lrwxrwxrwx   1 root root     27 Sep 18  2015 libsane-magicolor.so.1 -> libsane-magicolor.so.1.0.25
-rw-r--r--   1 root root 100952 Sep 18  2015 libsane-magicolor.so.1.0.25
-rw-r--r--   1 root root   1013 Sep 18  2015 libsane-matsushita.la
lrwxrwxrwx   1 root root     28 Sep 18  2015 libsane-matsushita.so.1 -> libsane-matsushita.so.1.0.25
-rw-r--r--   1 root root  68240 Sep 18  2015 libsane-matsushita.so.1.0.25
-rw-r--r--   1 root root   1006 Sep 18  2015 libsane-microtek2.la
lrwxrwxrwx   1 root root     27 Sep 18  2015 libsane-microtek2.so.1 -> libsane-microtek2.so.1.0.25
-rw-r--r--   1 root root 137440 Sep 18  2015 libsane-microtek2.so.1.0.25
-rw-r--r--   1 root root    999 Sep 18  2015 libsane-microtek.la
lrwxrwxrwx   1 root root     26 Sep 18  2015 libsane-microtek.so.1 -> libsane-microtek.so.1.0.25
-rw-r--r--   1 root root  96704 Sep 18  2015 libsane-microtek.so.1.0.25
-rw-r--r--   1 root root    985 Sep 18  2015 libsane-mustek.la
-rw-r--r--   1 root root   1006 Sep 18  2015 libsane-mustek_pp.la
lrwxrwxrwx   1 root root     27 Sep 18  2015 libsane-mustek_pp.so.1 -> libsane-mustek_pp.so.1.0.25
-rw-r--r--   1 root root 104920 Sep 18  2015 libsane-mustek_pp.so.1.0.25
lrwxrwxrwx   1 root root     24 Sep 18  2015 libsane-mustek.so.1 -> libsane-mustek.so.1.0.25
-rw-r--r--   1 root root 162664 Sep 18  2015 libsane-mustek.so.1.0.25
-rw-r--r--   1 root root   1020 Sep 18  2015 libsane-mustek_usb2.la
lrwxrwxrwx   1 root root     29 Sep 18  2015 libsane-mustek_usb2.so.1 -> libsane-mustek_usb2.so.1.0.25
-rw-r--r--   1 root root 161960 Sep 18  2015 libsane-mustek_usb2.so.1.0.25
-rw-r--r--   1 root root   1013 Sep 18  2015 libsane-mustek_usb.la
lrwxrwxrwx   1 root root     28 Sep 18  2015 libsane-mustek_usb.so.1 -> libsane-mustek_usb.so.1.0.25
-rw-r--r--   1 root root 170096 Sep 18  2015 libsane-mustek_usb.so.1.0.25
-rw-r--r--   1 root root    964 Sep 18  2015 libsane-nec.la
lrwxrwxrwx   1 root root     21 Sep 18  2015 libsane-nec.so.1 -> libsane-nec.so.1.0.25
-rw-r--r--   1 root root  72056 Sep 18  2015 libsane-nec.so.1.0.25
-rw-r--r--   1 root root    964 Sep 18  2015 libsane-net.la
lrwxrwxrwx   1 root root     21 Sep 18  2015 libsane-net.so.1 -> libsane-net.so.1.0.25
-rw-r--r--   1 root root  63328 Sep 18  2015 libsane-net.so.1.0.25
-rw-r--r--   1 root root    978 Sep 18  2015 libsane-niash.la
lrwxrwxrwx   1 root root     23 Sep 18  2015 libsane-niash.so.1 -> libsane-niash.so.1.0.25
-rw-r--r--   1 root root  72032 Sep 18  2015 libsane-niash.so.1.0.25
-rw-r--r--   1 root root    957 Sep 18  2015 libsane-p5.la
lrwxrwxrwx   1 root root     20 Sep 18  2015 libsane-p5.so.1 -> libsane-p5.so.1.0.25
-rw-r--r--   1 root root  51264 Sep 18  2015 libsane-p5.so.1.0.25
-rw-r--r--   1 root root    964 Sep 18  2015 libsane-pie.la
lrwxrwxrwx   1 root root     21 Sep 18  2015 libsane-pie.so.1 -> libsane-pie.so.1.0.25
-rw-r--r--   1 root root  84240 Sep 18  2015 libsane-pie.so.1.0.25
-rw-r--r--   1 root root    978 Sep 18  2015 libsane-pixma.la
lrwxrwxrwx   1 root root     23 Sep 18  2015 libsane-pixma.so.1 -> libsane-pixma.so.1.0.25
-rw-r--r--   1 root root 190472 Sep 18  2015 libsane-pixma.so.1.0.25
-rw-r--r--   1 root root    992 Sep 18  2015 libsane-plustek.la
-rw-r--r--   1 root root   1013 Sep 18  2015 libsane-plustek_pp.la
lrwxrwxrwx   1 root root     28 Sep 18  2015 libsane-plustek_pp.so.1 -> libsane-plustek_pp.so.1.0.25
-rw-r--r--   1 root root 186520 Sep 18  2015 libsane-plustek_pp.so.1.0.25
lrwxrwxrwx   1 root root     25 Sep 18  2015 libsane-plustek.so.1 -> libsane-plustek.so.1.0.25
-rw-r--r--   1 root root 231456 Sep 18  2015 libsane-plustek.so.1.0.25
-rw-r--r--   1 root root    964 Sep 18  2015 libsane-pnm.la
lrwxrwxrwx   1 root root     21 Sep 18  2015 libsane-pnm.so.1 -> libsane-pnm.so.1.0.25
-rw-r--r--   1 root root  40456 Sep 18  2015 libsane-pnm.so.1.0.25
-rw-r--r--   1 root root    971 Sep 18  2015 libsane-qcam.la
lrwxrwxrwx   1 root root     22 Sep 18  2015 libsane-qcam.so.1 -> libsane-qcam.so.1.0.25
-rw-r--r--   1 root root  51216 Sep 18  2015 libsane-qcam.so.1.0.25
-rw-r--r--   1 root root    978 Sep 18  2015 libsane-ricoh.la
lrwxrwxrwx   1 root root     23 Sep 18  2015 libsane-ricoh.so.1 -> libsane-ricoh.so.1.0.25
-rw-r--r--   1 root root  55528 Sep 18  2015 libsane-ricoh.so.1.0.25
-rw-r--r--   1 root root    992 Sep 18  2015 libsane-rts8891.la
lrwxrwxrwx   1 root root     25 Sep 18  2015 libsane-rts8891.so.1 -> libsane-rts8891.so.1.0.25
-rw-r--r--   1 root root 158208 Sep 18  2015 libsane-rts8891.so.1.0.25
-rw-r--r--   1 root root    978 Sep 18  2015 libsane-s9036.la
lrwxrwxrwx   1 root root     23 Sep 18  2015 libsane-s9036.so.1 -> libsane-s9036.so.1.0.25
-rw-r--r--   1 root root  55536 Sep 18  2015 libsane-s9036.so.1.0.25
-rw-r--r--   1 root root    992 Sep 18  2015 libsane-sceptre.la
lrwxrwxrwx   1 root root     25 Sep 18  2015 libsane-sceptre.so.1 -> libsane-sceptre.so.1.0.25
-rw-r--r--   1 root root  63712 Sep 18  2015 libsane-sceptre.so.1.0.25
-rw-r--r--   1 root root    978 Sep 18  2015 libsane-sharp.la
lrwxrwxrwx   1 root root     23 Sep 18  2015 libsane-sharp.so.1 -> libsane-sharp.so.1.0.25
-rw-r--r--   1 root root  84496 Sep 18  2015 libsane-sharp.so.1.0.25
-rw-r--r--   1 root root    985 Sep 18  2015 libsane-sm3600.la
lrwxrwxrwx   1 root root     24 Sep 18  2015 libsane-sm3600.so.1 -> libsane-sm3600.so.1.0.25
-rw-r--r--   1 root root  72176 Sep 18  2015 libsane-sm3600.so.1.0.25
-rw-r--r--   1 root root    985 Sep 18  2015 libsane-sm3840.la
lrwxrwxrwx   1 root root     24 Sep 18  2015 libsane-sm3840.so.1 -> libsane-sm3840.so.1.0.25
-rw-r--r--   1 root root  92080 Sep 18  2015 libsane-sm3840.so.1.0.25
-rw-r--r--   1 root root    999 Sep 18  2015 libsane-snapscan.la
lrwxrwxrwx   1 root root     26 Sep 18  2015 libsane-snapscan.so.1 -> libsane-snapscan.so.1.0.25
-rw-r--r--   1 root root 213248 Sep 18  2015 libsane-snapscan.so.1.0.25
-rw-r--r--   1 root root    978 Sep 18  2015 libsane-sp15c.la
lrwxrwxrwx   1 root root     23 Sep 18  2015 libsane-sp15c.so.1 -> libsane-sp15c.so.1.0.25
-rw-r--r--   1 root root  68040 Sep 18  2015 libsane-sp15c.so.1.0.25
-rw-r--r--   1 root root    978 Sep 18  2015 libsane-st400.la
lrwxrwxrwx   1 root root     23 Sep 18  2015 libsane-st400.so.1 -> libsane-st400.so.1.0.25
-rw-r--r--   1 root root  55872 Sep 18  2015 libsane-st400.so.1.0.25
-rw-r--r--   1 root root    985 Sep 18  2015 libsane-stv680.la
lrwxrwxrwx   1 root root     24 Sep 18  2015 libsane-stv680.so.1 -> libsane-stv680.so.1.0.25
-rw-r--r--   1 root root  75752 Sep 18  2015 libsane-stv680.so.1.0.25
-rw-r--r--   1 root root    999 Sep 18  2015 libsane-tamarack.la
lrwxrwxrwx   1 root root     26 Sep 18  2015 libsane-tamarack.so.1 -> libsane-tamarack.so.1.0.25
-rw-r--r--   1 root root  59616 Sep 18  2015 libsane-tamarack.so.1.0.25
-rw-r--r--   1 root root    978 Sep 18  2015 libsane-teco1.la
lrwxrwxrwx   1 root root     23 Sep 18  2015 libsane-teco1.so.1 -> libsane-teco1.so.1.0.25
-rw-r--r--   1 root root  63872 Sep 18  2015 libsane-teco1.so.1.0.25
-rw-r--r--   1 root root    978 Sep 18  2015 libsane-teco2.la
lrwxrwxrwx   1 root root     23 Sep 18  2015 libsane-teco2.so.1 -> libsane-teco2.so.1.0.25
-rw-r--r--   1 root root  72064 Sep 18  2015 libsane-teco2.so.1.0.25
-rw-r--r--   1 root root    978 Sep 18  2015 libsane-teco3.la
lrwxrwxrwx   1 root root     23 Sep 18  2015 libsane-teco3.so.1 -> libsane-teco3.so.1.0.25
-rw-r--r--   1 root root  63872 Sep 18  2015 libsane-teco3.so.1.0.25
-rw-r--r--   1 root root    971 Sep 18  2015 libsane-test.la
lrwxrwxrwx   1 root root     22 Sep 18  2015 libsane-test.so.1 -> libsane-test.so.1.0.25
-rw-r--r--   1 root root  72688 Sep 18  2015 libsane-test.so.1.0.25
-rw-r--r--   1 root root    964 Sep 18  2015 libsane-u12.la
lrwxrwxrwx   1 root root     21 Sep 18  2015 libsane-u12.so.1 -> libsane-u12.so.1.0.25
-rw-r--r--   1 root root 122512 Sep 18  2015 libsane-u12.so.1.0.25
-rw-r--r--   1 root root   1006 Sep 18  2015 libsane-umax1220u.la
lrwxrwxrwx   1 root root     27 Sep 18  2015 libsane-umax1220u.so.1 -> libsane-umax1220u.so.1.0.25
-rw-r--r--   1 root root  92688 Sep 18  2015 libsane-umax1220u.so.1.0.25
-rw-r--r--   1 root root    971 Sep 18  2015 libsane-umax.la
-rw-r--r--   1 root root    992 Sep 18  2015 libsane-umax_pp.la
lrwxrwxrwx   1 root root     25 Sep 18  2015 libsane-umax_pp.so.1 -> libsane-umax_pp.so.1.0.25
-rw-r--r--   1 root root 211976 Sep 18  2015 libsane-umax_pp.so.1.0.25
lrwxrwxrwx   1 root root     22 Sep 18  2015 libsane-umax.so.1 -> libsane-umax.so.1.0.25
-rw-r--r--   1 root root 179808 Sep 18  2015 libsane-umax.so.1.0.25
-rw-r--r--   1 root root   1006 Sep 18  2015 libsane-xerox_mfp.la
lrwxrwxrwx   1 root root     27 Sep 18  2015 libsane-xerox_mfp.so.1 -> libsane-xerox_mfp.so.1.0.25
-rw-r--r--   1 root root  71720 Sep 18  2015 libsane-xerox_mfp.so.1.0.25
```

> You also mentioned that scanner stopped working about a year-and-a-half ago. I know it's a while back, but was this after an upgrade or update? Is your scanner on a static IP address?


I'm pretty sure it stopped working after an upgrade. I'll go back and look at what I might have posted on the forum at that time. (Found it--https://ubuntuforums.org/showthread.php?t=2291470) I do not know whether it has a static address. Is it possible to have a non-static address when it connects via USB and not a network?

---

### Post by mollie4168 on 2017-01-27
Part 2...

   
> 
Try turning on debug mode and then scan using command line as per this post: [https://ubuntuforums.org/showthread....7#post13480927]("https://ubuntuforums.org/showthread.php?t=2321613&p=13480927#post13480927")

Plugged in and connected via USB:

```
tracy@tracy:~$ export SANE_DEBUG_DLL=128
tracy@tracy:~$ scanimage -L
[sanei_debug] Setting debug level of dll to 128.
[dll] sane_init: SANE dll backend version 1.0.13 from sane-backends 1.0.25git
[dll] sane_init/read_dlld: attempting to open directory `./dll.d'
[dll] sane_init/read_dlld: attempting to open directory `/etc/sane.d/dll.d'
[dll] sane_init/read_dlld: using config directory `/etc/sane.d/dll.d'
[dll] sane_init/read_dlld: considering /etc/sane.d/dll.d/hplip
[dll] sane_init/read_config: reading dll.d/hplip
[dll] add_backend: adding backend `hpaio'
[dll] sane_init/read_dlld: considering /etc/sane.d/dll.d/libsane-extras
[dll] sane_init/read_config: reading dll.d/libsane-extras
[dll] add_backend: adding backend `ls5000'
[dll] sane_init/read_dlld: done.
[dll] sane_init/read_config: reading dll.conf
[dll] add_backend: adding backend `net'
[dll] add_backend: adding backend `abaton'
[dll] add_backend: adding backend `agfafocus'
[dll] add_backend: adding backend `apple'
[dll] add_backend: adding backend `avision'
[dll] add_backend: adding backend `artec'
[dll] add_backend: adding backend `artec_eplus48u'
[dll] add_backend: adding backend `as6e'
[dll] add_backend: adding backend `bh'
[dll] add_backend: adding backend `canon'
[dll] add_backend: adding backend `canon630u'
[dll] add_backend: adding backend `canon_dr'
[dll] add_backend: adding backend `cardscan'
[dll] add_backend: adding backend `coolscan'
[dll] add_backend: adding backend `coolscan3'
[dll] add_backend: adding backend `dell1600n_net'
[dll] add_backend: adding backend `dmc'
[dll] add_backend: adding backend `epjitsu'
[dll] add_backend: adding backend `epson2'
[dll] add_backend: adding backend `epsonds'
[dll] add_backend: adding backend `fujitsu'
[dll] add_backend: adding backend `genesys'
[dll] add_backend: adding backend `gt68xx'
[dll] add_backend: adding backend `hp'
[dll] add_backend: adding backend `hp3900'
[dll] add_backend: adding backend `hpsj5s'
[dll] add_backend: adding backend `hp3500'
[dll] add_backend: adding backend `hp4200'
[dll] add_backend: adding backend `hp5400'
[dll] add_backend: adding backend `hp5590'
[dll] add_backend: adding backend `hpljm1005'
[dll] add_backend: adding backend `hs2p'
[dll] add_backend: adding backend `ibm'
[dll] add_backend: adding backend `kodak'
[dll] add_backend: adding backend `kodakaio'
[dll] add_backend: adding backend `kvs1025'
[dll] add_backend: adding backend `kvs20xx'
[dll] add_backend: adding backend `leo'
[dll] add_backend: adding backend `lexmark'
[dll] add_backend: adding backend `ma1509'
[dll] add_backend: adding backend `magicolor'
[dll] add_backend: adding backend `matsushita'
[dll] add_backend: adding backend `microtek'
[dll] add_backend: adding backend `microtek2'
[dll] add_backend: adding backend `mustek'
[dll] add_backend: adding backend `mustek_usb'
[dll] add_backend: adding backend `mustek_usb2'
[dll] add_backend: adding backend `nec'
[dll] add_backend: adding backend `niash'
[dll] add_backend: adding backend `pie'
[dll] add_backend: adding backend `pixma'
[dll] add_backend: adding backend `plustek'
[dll] add_backend: adding backend `qcam'
[dll] add_backend: adding backend `ricoh'
[dll] add_backend: adding backend `rts8891'
[dll] add_backend: adding backend `s9036'
[dll] add_backend: adding backend `sceptre'
[dll] add_backend: adding backend `sharp'
[dll] add_backend: adding backend `sm3600'
[dll] add_backend: adding backend `sm3840'
[dll] add_backend: adding backend `snapscan'
[dll] add_backend: adding backend `sp15c'
[dll] add_backend: adding backend `tamarack'
[dll] add_backend: adding backend `teco1'
[dll] add_backend: adding backend `teco2'
[dll] add_backend: adding backend `teco3'
[dll] add_backend: adding backend `u12'
[dll] add_backend: adding backend `umax'
[dll] add_backend: adding backend `umax1220u'
[dll] add_backend: adding backend `v4l'
[dll] add_backend: adding backend `xerox_mfp'
[dll] add_backend: adding backend `brother4'
[dll] sane_get_devices
[dll] load: searching backend `brother4' in `/usr/lib/x86_64-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/x86_64-linux-gnu/sane/libsane-brother4.so.1'
[dll] load: couldn't open `/usr/lib/x86_64-linux-gnu/sane/libsane-brother4.so.1' (No such file or directory)
[dll] load: trying to load `/usr/lib/sane/libsane-brother4.so.1'
[dll] load: dlopen()ing `/usr/lib/sane/libsane-brother4.so.1'
[dll] load: dlopen() failed (/usr/lib/sane/libsane-brother4.so.1: wrong ELF class: ELFCLASS32)
[dll] load: searching backend `xerox_mfp' in `/usr/lib/x86_64-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/x86_64-linux-gnu/sane/libsane-xerox_mfp.so.1'
[dll] load: dlopen()ing `/usr/lib/x86_64-linux-gnu/sane/libsane-xerox_mfp.so.1'
[dll] init: initializing backend `xerox_mfp'
[dll] init: backend `xerox_mfp' is version 1.0.13
[dll] load: searching backend `v4l' in `/usr/lib/x86_64-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/x86_64-linux-gnu/sane/libsane-v4l.so.1'
[dll] load: couldn't open `/usr/lib/x86_64-linux-gnu/sane/libsane-v4l.so.1' (No such file or directory)
[dll] load: trying to load `/usr/lib/sane/libsane-v4l.so.1'
[dll] load: couldn't open `/usr/lib/sane/libsane-v4l.so.1' (No such file or directory)
[dll] load: couldn't find backend `v4l' (No such file or directory)
[dll] load: searching backend `umax1220u' in `/usr/lib/x86_64-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/x86_64-linux-gnu/sane/libsane-umax1220u.so.1'
[dll] load: dlopen()ing `/usr/lib/x86_64-linux-gnu/sane/libsane-umax1220u.so.1'
[dll] init: initializing backend `umax1220u'
[dll] init: backend `umax1220u' is version 1.0.2
[dll] load: searching backend `umax' in `/usr/lib/x86_64-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/x86_64-linux-gnu/sane/libsane-umax.so.1'
[dll] load: dlopen()ing `/usr/lib/x86_64-linux-gnu/sane/libsane-umax.so.1'
[dll] init: initializing backend `umax'
[dll] init: backend `umax' is version 1.0.45
[dll] load: searching backend `u12' in `/usr/lib/x86_64-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/x86_64-linux-gnu/sane/libsane-u12.so.1'
[dll] load: dlopen()ing `/usr/lib/x86_64-linux-gnu/sane/libsane-u12.so.1'
[dll] init: initializing backend `u12'
[dll] init: backend `u12' is version 1.0.0
[dll] load: searching backend `teco3' in `/usr/lib/x86_64-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/x86_64-linux-gnu/sane/libsane-teco3.so.1'
[dll] load: dlopen()ing `/usr/lib/x86_64-linux-gnu/sane/libsane-teco3.so.1'
[dll] init: initializing backend `teco3'
[dll] init: backend `teco3' is version 1.0.1
[dll] load: searching backend `teco2' in `/usr/lib/x86_64-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/x86_64-linux-gnu/sane/libsane-teco2.so.1'
[dll] load: dlopen()ing `/usr/lib/x86_64-linux-gnu/sane/libsane-teco2.so.1'
[dll] init: initializing backend `teco2'
[dll] init: backend `teco2' is version 1.0.10
[dll] load: searching backend `teco1' in `/usr/lib/x86_64-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/x86_64-linux-gnu/sane/libsane-teco1.so.1'
[dll] load: dlopen()ing `/usr/lib/x86_64-linux-gnu/sane/libsane-teco1.so.1'
[dll] init: initializing backend `teco1'
[dll] init: backend `teco1' is version 1.0.10
[dll] load: searching backend `tamarack' in `/usr/lib/x86_64-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/x86_64-linux-gnu/sane/libsane-tamarack.so.1'
[dll] load: dlopen()ing `/usr/lib/x86_64-linux-gnu/sane/libsane-tamarack.so.1'
[dll] init: initializing backend `tamarack'
[dll] init: backend `tamarack' is version 1.0.0
[dll] load: searching backend `sp15c' in `/usr/lib/x86_64-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/x86_64-linux-gnu/sane/libsane-sp15c.so.1'
[dll] load: dlopen()ing `/usr/lib/x86_64-linux-gnu/sane/libsane-sp15c.so.1'
[dll] init: initializing backend `sp15c'
[dll] init: backend `sp15c' is version 1.0.0
[dll] load: searching backend `snapscan' in `/usr/lib/x86_64-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/x86_64-linux-gnu/sane/libsane-snapscan.so.1'
[dll] load: dlopen()ing `/usr/lib/x86_64-linux-gnu/sane/libsane-snapscan.so.1'
[dll] init: initializing backend `snapscan'
[dll] init: backend `snapscan' is version 1.4.53
[dll] load: searching backend `sm3840' in `/usr/lib/x86_64-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/x86_64-linux-gnu/sane/libsane-sm3840.so.1'
[dll] load: dlopen()ing `/usr/lib/x86_64-linux-gnu/sane/libsane-sm3840.so.1'
[dll] init: initializing backend `sm3840'
[dll] init: backend `sm3840' is version 1.0.0
[dll] load: searching backend `sm3600' in `/usr/lib/x86_64-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/x86_64-linux-gnu/sane/libsane-sm3600.so.1'
[dll] load: dlopen()ing `/usr/lib/x86_64-linux-gnu/sane/libsane-sm3600.so.1'
[dll] init: initializing backend `sm3600'
[dll] init: backend `sm3600' is version 1.0.6
[dll] load: searching backend `sharp' in `/usr/lib/x86_64-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/x86_64-linux-gnu/sane/libsane-sharp.so.1'
[dll] load: dlopen()ing `/usr/lib/x86_64-linux-gnu/sane/libsane-sharp.so.1'
[dll] init: initializing backend `sharp'
[dll] init: backend `sharp' is version 1.0.0
[dll] load: searching backend `sceptre' in `/usr/lib/x86_64-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/x86_64-linux-gnu/sane/libsane-sceptre.so.1'
[dll] load: dlopen()ing `/usr/lib/x86_64-linux-gnu/sane/libsane-sceptre.so.1'
[dll] init: initializing backend `sceptre'
[dll] init: backend `sceptre' is version 1.0.10
[dll] load: searching backend `s9036' in `/usr/lib/x86_64-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/x86_64-linux-gnu/sane/libsane-s9036.so.1'
[dll] load: dlopen()ing `/usr/lib/x86_64-linux-gnu/sane/libsane-s9036.so.1'
[dll] init: initializing backend `s9036'
[dll] init: backend `s9036' is version 1.0.0
[dll] load: searching backend `rts8891' in `/usr/lib/x86_64-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/x86_64-linux-gnu/sane/libsane-rts8891.so.1'
[dll] load: dlopen()ing `/usr/lib/x86_64-linux-gnu/sane/libsane-rts8891.so.1'
[dll] init: initializing backend `rts8891'
[dll] init: backend `rts8891' is version 1.0.2401
[dll] load: searching backend `ricoh' in `/usr/lib/x86_64-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/x86_64-linux-gnu/sane/libsane-ricoh.so.1'
[dll] load: dlopen()ing `/usr/lib/x86_64-linux-gnu/sane/libsane-ricoh.so.1'
[dll] init: initializing backend `ricoh'
[dll] init: backend `ricoh' is version 1.0.0
[dll] load: searching backend `qcam' in `/usr/lib/x86_64-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/x86_64-linux-gnu/sane/libsane-qcam.so.1'
[dll] load: dlopen()ing `/usr/lib/x86_64-linux-gnu/sane/libsane-qcam.so.1'
[dll] init: initializing backend `qcam'
[dll] init: backend `qcam' is version 1.0.0
[dll] load: searching backend `plustek' in `/usr/lib/x86_64-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/x86_64-linux-gnu/sane/libsane-plustek.so.1'
[dll] load: dlopen()ing `/usr/lib/x86_64-linux-gnu/sane/libsane-plustek.so.1'
[dll] init: initializing backend `plustek'
[dll] init: backend `plustek' is version 1.0.0
[dll] load: searching backend `pixma' in `/usr/lib/x86_64-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/x86_64-linux-gnu/sane/libsane-pixma.so.1'
[dll] load: dlopen()ing `/usr/lib/x86_64-linux-gnu/sane/libsane-pixma.so.1'
[dll] init: initializing backend `pixma'
[dll] init: backend `pixma' is version 1.0.17
[dll] load: searching backend `pie' in `/usr/lib/x86_64-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/x86_64-linux-gnu/sane/libsane-pie.so.1'
[dll] load: dlopen()ing `/usr/lib/x86_64-linux-gnu/sane/libsane-pie.so.1'
[dll] init: initializing backend `pie'
[dll] init: backend `pie' is version 1.0.9
[dll] load: searching backend `niash' in `/usr/lib/x86_64-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/x86_64-linux-gnu/sane/libsane-niash.so.1'
[dll] load: dlopen()ing `/usr/lib/x86_64-linux-gnu/sane/libsane-niash.so.1'
[dll] init: initializing backend `niash'
[dll] init: backend `niash' is version 1.0.1
[dll] load: searching backend `nec' in `/usr/lib/x86_64-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/x86_64-linux-gnu/sane/libsane-nec.so.1'
[dll] load: dlopen()ing `/usr/lib/x86_64-linux-gnu/sane/libsane-nec.so.1'
[dll] init: initializing backend `nec'
[dll] init: backend `nec' is version 1.0.0
[dll] load: searching backend `mustek_usb2' in `/usr/lib/x86_64-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/x86_64-linux-gnu/sane/libsane-mustek_usb2.so.1'
[dll] load: dlopen()ing `/usr/lib/x86_64-linux-gnu/sane/libsane-mustek_usb2.so.1'
[dll] init: initializing backend `mustek_usb2'
[dll] init: backend `mustek_usb2' is version 1.0.10
[dll] load: searching backend `mustek_usb' in `/usr/lib/x86_64-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/x86_64-linux-gnu/sane/libsane-mustek_usb.so.1'
[dll] load: dlopen()ing `/usr/lib/x86_64-linux-gnu/sane/libsane-mustek_usb.so.1'
[dll] init: initializing backend `mustek_usb'
[dll] init: backend `mustek_usb' is version 1.0.18
[dll] load: searching backend `mustek' in `/usr/lib/x86_64-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/x86_64-linux-gnu/sane/libsane-mustek.so.1'
[dll] load: dlopen()ing `/usr/lib/x86_64-linux-gnu/sane/libsane-mustek.so.1'
[dll] init: initializing backend `mustek'
[dll] init: backend `mustek' is version 1.0.138
[dll] load: searching backend `microtek2' in `/usr/lib/x86_64-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/x86_64-linux-gnu/sane/libsane-microtek2.so.1'
[dll] load: dlopen()ing `/usr/lib/x86_64-linux-gnu/sane/libsane-microtek2.so.1'
[dll] init: initializing backend `microtek2'
[dll] init: backend `microtek2' is version 1.0.0
[dll] load: searching backend `microtek' in `/usr/lib/x86_64-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/x86_64-linux-gnu/sane/libsane-microtek.so.1'
[dll] load: dlopen()ing `/usr/lib/x86_64-linux-gnu/sane/libsane-microtek.so.1'
[dll] init: initializing backend `microtek'
[dll] init: backend `microtek' is version 1.0.0
[dll] load: searching backend `matsushita' in `/usr/lib/x86_64-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/x86_64-linux-gnu/sane/libsane-matsushita.so.1'
[dll] load: dlopen()ing `/usr/lib/x86_64-linux-gnu/sane/libsane-matsushita.so.1'
[dll] init: initializing backend `matsushita'
[dll] init: backend `matsushita' is version 1.0.7
[dll] load: searching backend `magicolor' in `/usr/lib/x86_64-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/x86_64-linux-gnu/sane/libsane-magicolor.so.1'
[dll] load: dlopen()ing `/usr/lib/x86_64-linux-gnu/sane/libsane-magicolor.so.1'
[dll] init: initializing backend `magicolor'
[dll] init: backend `magicolor' is version 1.0.1
[dll] load: searching backend `ma1509' in `/usr/lib/x86_64-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/x86_64-linux-gnu/sane/libsane-ma1509.so.1'
[dll] load: dlopen()ing `/usr/lib/x86_64-linux-gnu/sane/libsane-ma1509.so.1'
[dll] init: initializing backend `ma1509'
[dll] init: backend `ma1509' is version 1.0.3
[dll] load: searching backend `lexmark' in `/usr/lib/x86_64-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/x86_64-linux-gnu/sane/libsane-lexmark.so.1'
[dll] load: dlopen()ing `/usr/lib/x86_64-linux-gnu/sane/libsane-lexmark.so.1'
[dll] init: initializing backend `lexmark'
[dll] init: backend `lexmark' is version 1.0.32
[dll] load: searching backend `leo' in `/usr/lib/x86_64-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/x86_64-linux-gnu/sane/libsane-leo.so.1'
[dll] load: dlopen()ing `/usr/lib/x86_64-linux-gnu/sane/libsane-leo.so.1'
[dll] init: initializing backend `leo'
[dll] init: backend `leo' is version 1.0.11
[dll] load: searching backend `kvs20xx' in `/usr/lib/x86_64-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/x86_64-linux-gnu/sane/libsane-kvs20xx.so.1'
[dll] load: dlopen()ing `/usr/lib/x86_64-linux-gnu/sane/libsane-kvs20xx.so.1'
[dll] init: initializing backend `kvs20xx'
[dll] init: backend `kvs20xx' is version 1.0.2
[dll] load: searching backend `kvs1025' in `/usr/lib/x86_64-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/x86_64-linux-gnu/sane/libsane-kvs1025.so.1'
[dll] load: dlopen()ing `/usr/lib/x86_64-linux-gnu/sane/libsane-kvs1025.so.1'
[dll] init: initializing backend `kvs1025'
[dll] init: backend `kvs1025' is version 1.0.5
[dll] load: searching backend `kodakaio' in `/usr/lib/x86_64-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/x86_64-linux-gnu/sane/libsane-kodakaio.so.1'
[dll] load: dlopen()ing `/usr/lib/x86_64-linux-gnu/sane/libsane-kodakaio.so.1'
[dll] init: initializing backend `kodakaio'
[dll] init: backend `kodakaio' is version 1.0.2
[dll] load: searching backend `kodak' in `/usr/lib/x86_64-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/x86_64-linux-gnu/sane/libsane-kodak.so.1'
[dll] load: dlopen()ing `/usr/lib/x86_64-linux-gnu/sane/libsane-kodak.so.1'
[dll] init: initializing backend `kodak'
[dll] init: backend `kodak' is version 1.0.7
[dll] load: searching backend `ibm' in `/usr/lib/x86_64-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/x86_64-linux-gnu/sane/libsane-ibm.so.1'
[dll] load: dlopen()ing `/usr/lib/x86_64-linux-gnu/sane/libsane-ibm.so.1'
[dll] init: initializing backend `ibm'
[dll] init: backend `ibm' is version 1.0.0
[dll] load: searching backend `hs2p' in `/usr/lib/x86_64-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/x86_64-linux-gnu/sane/libsane-hs2p.so.1'
[dll] load: dlopen()ing `/usr/lib/x86_64-linux-gnu/sane/libsane-hs2p.so.1'
[dll] init: initializing backend `hs2p'
[dll] init: backend `hs2p' is version 1.0.0
[dll] load: searching backend `hpljm1005' in `/usr/lib/x86_64-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/x86_64-linux-gnu/sane/libsane-hpljm1005.so.1'
[dll] load: dlopen()ing `/usr/lib/x86_64-linux-gnu/sane/libsane-hpljm1005.so.1'
[dll] init: initializing backend `hpljm1005'
[dll] init: backend `hpljm1005' is version 1.0.1
[dll] load: searching backend `hp5590' in `/usr/lib/x86_64-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/x86_64-linux-gnu/sane/libsane-hp5590.so.1'
[dll] load: dlopen()ing `/usr/lib/x86_64-linux-gnu/sane/libsane-hp5590.so.1'
[dll] init: initializing backend `hp5590'
[dll] init: backend `hp5590' is version 1.0.7
[dll] load: searching backend `hp5400' in `/usr/lib/x86_64-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/x86_64-linux-gnu/sane/libsane-hp5400.so.1'
[dll] load: dlopen()ing `/usr/lib/x86_64-linux-gnu/sane/libsane-hp5400.so.1'
[dll] init: initializing backend `hp5400'
[dll] init: backend `hp5400' is version 1.0.3
[dll] load: searching backend `hp4200' in `/usr/lib/x86_64-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/x86_64-linux-gnu/sane/libsane-hp4200.so.1'
[dll] load: dlopen()ing `/usr/lib/x86_64-linux-gnu/sane/libsane-hp4200.so.1'
[dll] init: initializing backend `hp4200'
[dll] init: backend `hp4200' is version 1.0.0
[dll] load: searching backend `hp3500' in `/usr/lib/x86_64-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/x86_64-linux-gnu/sane/libsane-hp3500.so.1'
[dll] load: dlopen()ing `/usr/lib/x86_64-linux-gnu/sane/libsane-hp3500.so.1'
[dll] init: initializing backend `hp3500'
[dll] init: backend `hp3500' is version 1.0.0
[dll] load: searching backend `hpsj5s' in `/usr/lib/x86_64-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/x86_64-linux-gnu/sane/libsane-hpsj5s.so.1'
[dll] load: dlopen()ing `/usr/lib/x86_64-linux-gnu/sane/libsane-hpsj5s.so.1'
[dll] init: initializing backend `hpsj5s'
[dll] init: backend `hpsj5s' is version 1.0.3
[dll] load: searching backend `hp3900' in `/usr/lib/x86_64-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/x86_64-linux-gnu/sane/libsane-hp3900.so.1'
[dll] load: dlopen()ing `/usr/lib/x86_64-linux-gnu/sane/libsane-hp3900.so.1'
[dll] init: initializing backend `hp3900'
[dll] init: backend `hp3900' is version 1.0.0
[dll] load: searching backend `hp' in `/usr/lib/x86_64-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/x86_64-linux-gnu/sane/libsane-hp.so.1'
[dll] load: dlopen()ing `/usr/lib/x86_64-linux-gnu/sane/libsane-hp.so.1'
[dll] init: initializing backend `hp'
[dll] init: backend `hp' is version 1.0.8
[dll] load: searching backend `gt68xx' in `/usr/lib/x86_64-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/x86_64-linux-gnu/sane/libsane-gt68xx.so.1'
[dll] load: dlopen()ing `/usr/lib/x86_64-linux-gnu/sane/libsane-gt68xx.so.1'
[dll] init: initializing backend `gt68xx'
[dll] init: backend `gt68xx' is version 1.0.84
[dll] load: searching backend `genesys' in `/usr/lib/x86_64-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/x86_64-linux-gnu/sane/libsane-genesys.so.1'
[dll] load: dlopen()ing `/usr/lib/x86_64-linux-gnu/sane/libsane-genesys.so.1'
[dll] init: initializing backend `genesys'
[dll] init: backend `genesys' is version 1.0.2506
[dll] load: searching backend `fujitsu' in `/usr/lib/x86_64-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/x86_64-linux-gnu/sane/libsane-fujitsu.so.1'
[dll] load: dlopen()ing `/usr/lib/x86_64-linux-gnu/sane/libsane-fujitsu.so.1'
[dll] init: initializing backend `fujitsu'
[dll] init: backend `fujitsu' is version 1.0.126
[dll] load: searching backend `epsonds' in `/usr/lib/x86_64-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/x86_64-linux-gnu/sane/libsane-epsonds.so.1'
[dll] load: dlopen()ing `/usr/lib/x86_64-linux-gnu/sane/libsane-epsonds.so.1'
[dll] init: initializing backend `epsonds'
[dll] init: backend `epsonds' is version 1.0.35
[dll] load: searching backend `epson2' in `/usr/lib/x86_64-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/x86_64-linux-gnu/sane/libsane-epson2.so.1'
[dll] load: dlopen()ing `/usr/lib/x86_64-linux-gnu/sane/libsane-epson2.so.1'
[dll] init: initializing backend `epson2'
[dll] init: backend `epson2' is version 1.0.124
[dll] load: searching backend `epjitsu' in `/usr/lib/x86_64-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/x86_64-linux-gnu/sane/libsane-epjitsu.so.1'
[dll] load: dlopen()ing `/usr/lib/x86_64-linux-gnu/sane/libsane-epjitsu.so.1'
[dll] init: initializing backend `epjitsu'
[dll] init: backend `epjitsu' is version 1.0.28
[dll] load: searching backend `dmc' in `/usr/lib/x86_64-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/x86_64-linux-gnu/sane/libsane-dmc.so.1'
[dll] load: dlopen()ing `/usr/lib/x86_64-linux-gnu/sane/libsane-dmc.so.1'
[dll] init: initializing backend `dmc'
[dll] init: backend `dmc' is version 1.0.0
[dll] load: searching backend `dell1600n_net' in `/usr/lib/x86_64-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/x86_64-linux-gnu/sane/libsane-dell1600n_net.so.1'
[dll] load: dlopen()ing `/usr/lib/x86_64-linux-gnu/sane/libsane-dell1600n_net.so.1'
[dll] init: initializing backend `dell1600n_net'
[dll] init: backend `dell1600n_net' is version 1.0.0
[dll] load: searching backend `coolscan3' in `/usr/lib/x86_64-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/x86_64-linux-gnu/sane/libsane-coolscan3.so.1'
[dll] load: dlopen()ing `/usr/lib/x86_64-linux-gnu/sane/libsane-coolscan3.so.1'
[dll] init: initializing backend `coolscan3'
[dll] init: backend `coolscan3' is version 1.0.0
[dll] load: searching backend `coolscan' in `/usr/lib/x86_64-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/x86_64-linux-gnu/sane/libsane-coolscan.so.1'
[dll] load: dlopen()ing `/usr/lib/x86_64-linux-gnu/sane/libsane-coolscan.so.1'
[dll] init: initializing backend `coolscan'
[dll] init: backend `coolscan' is version 1.0.0
[dll] load: searching backend `cardscan' in `/usr/lib/x86_64-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/x86_64-linux-gnu/sane/libsane-cardscan.so.1'
[dll] load: dlopen()ing `/usr/lib/x86_64-linux-gnu/sane/libsane-cardscan.so.1'
[dll] init: initializing backend `cardscan'
[dll] init: backend `cardscan' is version 1.0.2
[dll] load: searching backend `canon_dr' in `/usr/lib/x86_64-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/x86_64-linux-gnu/sane/libsane-canon_dr.so.1'
[dll] load: dlopen()ing `/usr/lib/x86_64-linux-gnu/sane/libsane-canon_dr.so.1'
[dll] init: initializing backend `canon_dr'
[dll] init: backend `canon_dr' is version 1.0.49
[dll] load: searching backend `canon630u' in `/usr/lib/x86_64-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/x86_64-linux-gnu/sane/libsane-canon630u.so.1'
[dll] load: dlopen()ing `/usr/lib/x86_64-linux-gnu/sane/libsane-canon630u.so.1'
[dll] init: initializing backend `canon630u'
[dll] init: backend `canon630u' is version 1.0.1
[dll] load: searching backend `canon' in `/usr/lib/x86_64-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/x86_64-linux-gnu/sane/libsane-canon.so.1'
[dll] load: dlopen()ing `/usr/lib/x86_64-linux-gnu/sane/libsane-canon.so.1'
[dll] init: initializing backend `canon'
[dll] init: backend `canon' is version 1.0.0
[dll] load: searching backend `bh' in `/usr/lib/x86_64-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/x86_64-linux-gnu/sane/libsane-bh.so.1'
[dll] load: dlopen()ing `/usr/lib/x86_64-linux-gnu/sane/libsane-bh.so.1'
[dll] init: initializing backend `bh'
[dll] init: backend `bh' is version 1.0.4
[dll] load: searching backend `as6e' in `/usr/lib/x86_64-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/x86_64-linux-gnu/sane/libsane-as6e.so.1'
[dll] load: dlopen()ing `/usr/lib/x86_64-linux-gnu/sane/libsane-as6e.so.1'
[dll] init: initializing backend `as6e'
[dll] load: searching backend `artec_eplus48u' in `/usr/lib/x86_64-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/x86_64-linux-gnu/sane/libsane-artec_eplus48u.so.1'
[dll] load: dlopen()ing `/usr/lib/x86_64-linux-gnu/sane/libsane-artec_eplus48u.so.1'
[dll] init: initializing backend `artec_eplus48u'
[dll] init: backend `artec_eplus48u' is version 1.0.0
[dll] load: searching backend `artec' in `/usr/lib/x86_64-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/x86_64-linux-gnu/sane/libsane-artec.so.1'
[dll] load: dlopen()ing `/usr/lib/x86_64-linux-gnu/sane/libsane-artec.so.1'
[dll] init: initializing backend `artec'
[dll] init: backend `artec' is version 1.0.0
[dll] load: searching backend `avision' in `/usr/lib/x86_64-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/x86_64-linux-gnu/sane/libsane-avision.so.1'
[dll] load: dlopen()ing `/usr/lib/x86_64-linux-gnu/sane/libsane-avision.so.1'
[dll] init: initializing backend `avision'
[dll] init: backend `avision' is version 1.0.297
[dll] load: searching backend `apple' in `/usr/lib/x86_64-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/x86_64-linux-gnu/sane/libsane-apple.so.1'
[dll] load: dlopen()ing `/usr/lib/x86_64-linux-gnu/sane/libsane-apple.so.1'
[dll] init: initializing backend `apple'
[dll] init: backend `apple' is version 1.0.0
[dll] load: searching backend `agfafocus' in `/usr/lib/x86_64-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/x86_64-linux-gnu/sane/libsane-agfafocus.so.1'
[dll] load: dlopen()ing `/usr/lib/x86_64-linux-gnu/sane/libsane-agfafocus.so.1'
[dll] init: initializing backend `agfafocus'
[dll] init: backend `agfafocus' is version 1.0.0
[dll] load: searching backend `abaton' in `/usr/lib/x86_64-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/x86_64-linux-gnu/sane/libsane-abaton.so.1'
[dll] load: dlopen()ing `/usr/lib/x86_64-linux-gnu/sane/libsane-abaton.so.1'
[dll] init: initializing backend `abaton'
[dll] init: backend `abaton' is version 1.0.0
[dll] load: searching backend `net' in `/usr/lib/x86_64-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/x86_64-linux-gnu/sane/libsane-net.so.1'
[dll] load: dlopen()ing `/usr/lib/x86_64-linux-gnu/sane/libsane-net.so.1'
[dll] init: initializing backend `net'
[dll] init: backend `net' is version 1.0.25
[dll] load: searching backend `ls5000' in `/usr/lib/x86_64-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/x86_64-linux-gnu/sane/libsane-ls5000.so.1'
[dll] load: dlopen()ing `/usr/lib/x86_64-linux-gnu/sane/libsane-ls5000.so.1'
[dll] init: initializing backend `ls5000'
[dll] init: backend `ls5000' is version 1.0.0
[dll] load: searching backend `hpaio' in `/usr/lib/x86_64-linux-gnu/sane:/usr/lib/sane'
[dll] load: trying to load `/usr/lib/x86_64-linux-gnu/sane/libsane-hpaio.so.1'
[dll] load: dlopen()ing `/usr/lib/x86_64-linux-gnu/sane/libsane-hpaio.so.1'
[dll] init: initializing backend `hpaio'
[dll] init: backend `hpaio' is version 1.0.0
[dll] sane_get_devices: found 0 devices

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).
[dll] sane_exit: exiting
[dll] sane_exit: calling backend `xerox_mfp's exit function
[dll] sane_exit: calling backend `umax1220u's exit function
[dll] sane_exit: calling backend `umax's exit function
[dll] sane_exit: calling backend `u12's exit function
[dll] sane_exit: calling backend `teco3's exit function
[dll] sane_exit: calling backend `teco2's exit function
[dll] sane_exit: calling backend `teco1's exit function
[dll] sane_exit: calling backend `tamarack's exit function
[dll] sane_exit: calling backend `sp15c's exit function
[dll] sane_exit: calling backend `snapscan's exit function
[dll] sane_exit: calling backend `sm3840's exit function
[dll] sane_exit: calling backend `sm3600's exit function
[dll] sane_exit: calling backend `sharp's exit function
[dll] sane_exit: calling backend `sceptre's exit function
[dll] sane_exit: calling backend `s9036's exit function
[dll] sane_exit: calling backend `rts8891's exit function
[dll] sane_exit: calling backend `ricoh's exit function
[dll] sane_exit: calling backend `qcam's exit function
[dll] sane_exit: calling backend `plustek's exit function
[dll] sane_exit: calling backend `pixma's exit function
[dll] sane_exit: calling backend `pie's exit function
[dll] sane_exit: calling backend `niash's exit function
[dll] sane_exit: calling backend `nec's exit function
[dll] sane_exit: calling backend `mustek_usb2's exit function
[dll] sane_exit: calling backend `mustek_usb's exit function
[dll] sane_exit: calling backend `mustek's exit function
[dll] sane_exit: calling backend `microtek2's exit function
[dll] sane_exit: calling backend `microtek's exit function
[dll] sane_exit: calling backend `matsushita's exit function
[dll] sane_exit: calling backend `magicolor's exit function
[dll] sane_exit: calling backend `ma1509's exit function
[dll] sane_exit: calling backend `lexmark's exit function
[dll] sane_exit: calling backend `leo's exit function
[dll] sane_exit: calling backend `kvs20xx's exit function
[dll] sane_exit: calling backend `kvs1025's exit function
[dll] sane_exit: calling backend `kodakaio's exit function
[dll] sane_exit: calling backend `kodak's exit function
[dll] sane_exit: calling backend `ibm's exit function
[dll] sane_exit: calling backend `hs2p's exit function
[dll] sane_exit: calling backend `hpljm1005's exit function
[dll] sane_exit: calling backend `hp5590's exit function
[dll] sane_exit: calling backend `hp5400's exit function
[dll] sane_exit: calling backend `hp4200's exit function
[dll] sane_exit: calling backend `hp3500's exit function
[dll] sane_exit: calling backend `hpsj5s's exit function
[dll] sane_exit: calling backend `hp3900's exit function
[dll] sane_exit: calling backend `hp's exit function
[dll] sane_exit: calling backend `gt68xx's exit function
[dll] sane_exit: calling backend `genesys's exit function
[dll] sane_exit: calling backend `fujitsu's exit function
[dll] sane_exit: calling backend `epsonds's exit function
[dll] sane_exit: calling backend `epson2's exit function
[dll] sane_exit: calling backend `epjitsu's exit function
[dll] sane_exit: calling backend `dmc's exit function
[dll] sane_exit: calling backend `dell1600n_net's exit function
[dll] sane_exit: calling backend `coolscan3's exit function
[dll] sane_exit: calling backend `coolscan's exit function
[dll] sane_exit: calling backend `cardscan's exit function
[dll] sane_exit: calling backend `canon_dr's exit function
[dll] sane_exit: calling backend `canon630u's exit function
[dll] sane_exit: calling backend `canon's exit function
[dll] sane_exit: calling backend `bh's exit function
[dll] sane_exit: calling backend `artec_eplus48u's exit function
[dll] sane_exit: calling backend `artec's exit function
[dll] sane_exit: calling backend `avision's exit function
[dll] sane_exit: calling backend `apple's exit function
[dll] sane_exit: calling backend `agfafocus's exit function
[dll] sane_exit: calling backend `abaton's exit function
[dll] sane_exit: calling backend `net's exit function
[dll] sane_exit: calling backend `ls5000's exit function
[dll] sane_exit: calling backend `hpaio's exit function
[dll] sane_exit: finished


```

---

### Post by DuckHook on 2017-01-27
Here are some of the problems. Parsing only for the relevant content:
```
ls -laF /usr/lib/x86_64-linux-gnu/sane
…
lrwxrwxrwx   1 root root     41 Jan  3  2015 libsane-brother4.so -> /usr/lib64/sane/libsane-brother4.so.1.0.7
lrwxrwxrwx   1 root root     41 Jan  3  2015 libsane-brother4.so.1 -> /usr/lib64/sane/libsane-brother4.so.1.0.7
lrwxrwxrwx   1 root root     41 Jan  3  2015 libsane-brother4.so.1.0.7 -> /usr/lib64/sane/libsane-brother4.so.1.0.7
```
Note that this is a neverending loop of symlinks that end up referring back to a symlink and not an actual driver. The result is:
```
$ export SANE_DEBUG_DLL=128
$ scanimage -L
…
[dll] load: trying to load `/usr/lib/x86_64-linux-gnu/sane/libsane-brother4.so.1'
[dll] load: couldn't open `/usr/lib/x86_64-linux-gnu/sane/libsane-brother4.so.1' (No such file or directory)
…
```
You also show:
```
…
[dll] load: dlopen()ing `/usr/lib/sane/libsane-brother4.so.1'
[dll] load: dlopen() failed (/usr/lib/sane/libsane-brother4.so.1: wrong ELF class: ELFCLASS32)
…
```…which indicates that you probably downloaded 32-bit drivers for your 64-bit OS.

Finally:
```
…
[dll] load: trying to load `/usr/lib/x86_64-linux-gnu/sane/libsane-v4l.so.1'
[dll] load: couldn't open `/usr/lib/x86_64-linux-gnu/sane/libsane-v4l.so.1' (No such file or directory)
[dll] load: trying to load `/usr/lib/sane/libsane-v4l.so.1'
[dll] load: couldn't open `/usr/lib/sane/libsane-v4l.so.1' (No such file or directory)
…
```…indicates that you are missing further scanning libraries.

I assume that you tinkered extensively on your own before asking for help here and this led to the current oddball configurations. If you can remember the exact steps you took, it would be helpful to confirm. However, in the end, it won't change what must be done.

Solutions:

Your symlinks must ultimately link to a real driver. To do so, you will have to remove the last symlink in the chain and either copy or link to a real driver. Since the *libsane-brother4.so.1.0.7* in */usr/lib/sane* is at least a real file (not being privy to your past actions, we have no way of knowing whether it is the original or not), *very carefully* do the following (probably best to copy and paste the following code rather than risk typos):
```
sudo rm /usr/lib/x86_64-linux-gnu/sane/libsane-brother4.so.1.0.7
```
This removes the broken link. Then, to link to (hopefully) the right file:```
sudo ln -s /usr/lib/sane/libsane-brother4.so.1.0.7 /usr/lib/x86_64-linux-gnu/sane/libsane-brother4.so.1.0.7
```You must check afterwards to make sure that the links are all good (i.e. point to a real file). They should show up in that blue colour indicating a good linkage. Broken links show as red (I believe).

I should alert you to the fact that what follows is just an educated guess, but to fix the other errors, I believe that you must install the libsane 32-bit libraries:
```
sudo apt install libsane:i386
```After installation, you will likely have to reboot.

Although the following is not part of your original problem, I hope you won't mind me making a few general observations:

While others have had great success with the Brother Install Tool and Brother products in general, that has not been my experience. Consequently, I don't own any Brother products anymore and all of the above has been mainly from vague recollection. I have found that HP products work best with Linux, mainly due to the incredible efforts of the HPLIP community. I'm not shilling for HP. Indeed, I have no vested interest in them. I've just found their printers to be the most trouble-free for the Linux ecosystem. Perhaps a consideration when you are buying your next multifunction machine.

While Xenial is pretty good at supporting 32-bit drivers where needed, it isn't a good idea to continue using them (unless, of course, you are running a 32-bit OS). You end up running into issues like this one. If Brother has 64-bit drivers for this machine, you are far better off using them rather than relying on libsane:i386, which is really a bit of a kludge. If Brother *does not have* 64-bit Linux drivers for your printer, then all the more reason to avoid Brother printers in the future.

Let us know how the above goes.

---

### Post by mollie4168 on 2017-02-01
Sorry, I was away/otherwise occupied for a few days, but I'm getting back to this now.

Before I get too far along, I had no output from your first two commands.  Should the second command at least have shown me a list, so I could see whether the links popped up in red or blue?  My apologies if this is a dumb question, but I didn't want to continue and make matters any worse.  I really appreciate your help and patience with this. 

This is what happened in terminal:
```
tracy@tracy:~$ sudo rm /usr/lib/x86_64-linux-gnu/sane/libsane-brother4.so.1.0.7
[sudo] password for tracy: 
tracy@tracy:~$ sudo ln -s /usr/lib/sane/libsane-brother4.so.1.0.7 /usr/lib/x86_64-linux-gnu/sane/libsane-brother4.so.1.0.7
tracy@tracy:~$ 


```

Thank you for the advice about HP devices.  I appreciate it, and will certainly keep that in mind next time.  I did a bit of research before I got my Brother multifunction and found some Linux support for them, but clearly not enough support or research happened!  The drivers seemed to be fine until my upgrade to 15.04.  Their technical support has been pretty dismal in even caring about this issue.

---

### Post by DuckHook on 2017-02-01
Greetings mollie4168

Like many commands in Linux, these will just execute in sullen silence. You won't have any idea if the link is good until you:```
ls -laF /usr/lib/x86_64-linux-gnu/sane/libsane-brother4.so.1.0.7
```
This is why I said:> You must check afterwards to make sure that the links are all good (i.e. point to a real file). They should show up in that blue colour indicating a good linkage. Broken links show as red (I believe).

---

### Post by mollie4168 on 2017-02-02
Here's what I got:

```
tracy@tracy:~$ ls -laF /usr/lib/x86_64-linux-gnu/sane/libsane-brother4.so.1.0.7
lrwxrwxrwx 1 root root 39 Feb  1 20:28 [COLOR=#00ffff]/usr/lib/x86_64-linux-gnu/sane/libsane-brother4.so.1.0.7[/COLOR] -> [COLOR=#00ff00]/usr/lib/sane/libsane-brother4.so.1.0.7*[/COLOR]
tracy@tracy:~$ 
tracy@tracy:~$ 
tracy@tracy:~$ sudo apt install libsane:i386
[sudo] password for tracy: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libsane:i386 is already the newest version (1.0.25+git20150528-1ubuntu2).
The following packages were automatically installed and are no longer required:
  linux-headers-4.4.0-31 linux-headers-4.4.0-31-generic linux-headers-4.4.0-34
  linux-headers-4.4.0-34-generic linux-headers-4.4.0-36
  linux-headers-4.4.0-36-generic linux-headers-4.4.0-38
  linux-headers-4.4.0-38-generic linux-headers-4.4.0-42
  linux-headers-4.4.0-42-generic linux-headers-4.4.0-45
  linux-headers-4.4.0-45-generic linux-headers-4.4.0-47
  linux-headers-4.4.0-47-generic linux-image-4.2.0-42-generic
  linux-image-4.4.0-31-generic linux-image-4.4.0-34-generic
  linux-image-4.4.0-36-generic linux-image-4.4.0-38-generic
  linux-image-4.4.0-42-generic linux-image-4.4.0-45-generic
  linux-image-4.4.0-47-generic linux-image-extra-4.2.0-42-generic
  linux-image-extra-4.4.0-31-generic linux-image-extra-4.4.0-34-generic
  linux-image-extra-4.4.0-36-generic linux-image-extra-4.4.0-38-generic
  linux-image-extra-4.4.0-42-generic linux-image-extra-4.4.0-45-generic
  linux-image-extra-4.4.0-47-generic
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 39 not upgraded.


```

I've done this or something like it in the past, and I get thrown off since it says nothing was installed.  How does it look to you?

Per  [http://askubuntu.com/questions/17299/what-do-the-different-colors-mean-in-the-terminal](http://askubuntu.com/questions/17299/what-do-the-different-colors-mean-in-the-terminal),  sky blue means a linked file and green means something executable or a  datafile.  So that part seemed to work fine.

---

### Post by DuckHook on 2017-02-02
> **mollie4168 said:**
> I've done this or something like it in the past, and I get thrown off since it says nothing was installed.  How does it look to you?```
libsane:i386 is already the newest version (1.0.25+git20150528-1ubuntu2).
```It is already installed. Hmmm&#8230;
> sky blue means a linked file and green means something executable or a  datafile.  So that part seemed to work fine.Yes indeed.

Will have to take some time, research, and do some hard thinking why you get those other errors.

---

### Post by DuckHook on 2017-02-03
The error:```
[dll] load: trying to load `/usr/lib/sane/libsane-v4l.so.1'
[dll] load: couldn't open `/usr/lib/sane/libsane-v4l.so.1' (No such file or directory)
```&#8230;is unlikely to be part of your current problem. This is a driver for old video input like the AV stream from a Hauppage TV Card. It was part of the libsane package up to Trusty (14.04) but disappeared in Xenial. Its own man page states that it was alpha software and full of bugs: [http://manpages.ubuntu.com/manpages/precise/man5/sane-v4l.5.html](http://manpages.ubuntu.com/manpages/precise/man5/sane-v4l.5.html)
I suspect that the Ubuntu package maintainers quietly deprecated it, and it no longer shows up in newer versions. I don't feel that it has anything to do with your current problem.

On the other hand:```
&#8230;
[dll] load: dlopen()ing `/usr/lib/sane/libsane-brother4.so.1'
[dll] load: dlopen() failed (/usr/lib/sane/libsane-brother4.so.1: wrong ELF class: ELFCLASS32)
&#8230;
```&#8230;is troubling. It means that your OS is refusing to translate the 32-bit driver functions into your native 64-bit OS environment. Since Brother only publishes a 32-bit driver for your scanner, this translation must take place. There is no native 64-bit driver for your scanner.

[LIST=1]
[*]Did you try installing the Brother driver using their Driver Install Tool?
[*]Did you download that tool directly from the Brother site? [http://support.brother.com/g/b/downloadlist.aspx?c=us&lang=en&prod=dcp7065dn_all&os=128](http://support.brother.com/g/b/downloadlist.aspx?c=us&lang=en&prod=dcp7065dn_all&os=128)
[*]Did you follow the instructions during installation and pick the right choices? You might specify what choices you picked.
[/LIST]
I'm at a disadvantage with this machine. I have nothing with which to experiment on or to try reproducing the problem.

Sorry, but running out of ideas.

**EDIT**

Just playing a hunch, but please post output of:```
apt-cache policy libc6
```

---

### Post by mollie4168 on 2017-02-03
[I][URL="http://support.brother.com/g/b/downloadend.aspx?c=us&lang=en&prod=dcp7065dn_all&os=128&dlid=dlf006654_000&flang=4&type3=600"]

[/URL][/I]> 
[LIST=1]
[*]Did you try installing the Brother driver using their Driver Install Tool?
[*]Did you download that tool directly from the Brother site? [http://support.brother.com/g/b/downl...5dn_all&os=128]("http://support.brother.com/g/b/downloadlist.aspx?c=us&lang=en&prod=dcp7065dn_all&os=128")
[*]Did you follow the instructions during installation and pick the right choices? You might specify what choices you picked.
[/LIST]
[I][URL="http://support.brother.com/g/b/downloadend.aspx?c=us&lang=en&prod=dcp7065dn_all&os=128&dlid=dlf006654_000&flang=4&type3=600"]
[/URL][/I]

1. Yes.
2. Yes.  Other than suggestions in Ubuntu forums (I don't remember anyone suggesting outside drivers), I've only used the Brother site to download drivers.
3. What's happened in the past is a blur, but I've recently used the links for the latest printer driver, the 32-bit scanner driver, and the scanner setting file.  I have followed the instructions to the best of my abilities which I know isn't saying much.  Like I said, I was able to successfully follow the directions and get everything working in the past, but after the scanner stopped working, and I was trying different things, it all became a jumble.  

```
tracy@tracy:~$ apt-cache policy libc6
libc6:
  Installed: 2.23-0ubuntu5
  Candidate: 2.23-0ubuntu5
  Version table:
 *** 2.23-0ubuntu5 500
        500 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages
        100 /var/lib/dpkg/status
     2.23-0ubuntu3 500
        500 http://us.archive.ubuntu.com/ubuntu xenial/main amd64 Packages


```

Again, I do really appreciate your working on this.  If it's not possible to fix, at least I know it's a more complex issue and not just my lack of knowledge--although that probably contributed to it.

---

### Post by DuckHook on 2017-02-03
Sorry, mollie4168. I'm all out of ideas for now. That hunch didn't pan out. You do have multiarch installed and it should have worked with your 32-bit driver.
> **mollie4168 said:**
> …If it's not possible to fix, at least I know it's a more complex issue and not just my lack of knowledge--although that probably contributed to it.Now, please don't you go there. Lack of knowledge is a relative state (we are all lacking knowledge compared to someone more experienced) and you've done especially well getting as far as you have. As I said at the outset: I've found Brother printers to be a pain. That's why I don't use them. And without any Brother equipment to work on, I'm advising you with one hand tied behind my back. But that's all the more reason why your mind should be at ease. This is not an "easy" problem.

At this point, what I would suggest is to please be patient, keep this thread unsolved, and perhaps a more knowledgeable member will jump in.

Most problems are fixable. It's just a matter of how much blood, toil and tears need to be shed to get there.

---

### Post by mollie4168 on 2017-02-06
Thank you very much for your efforts and advice DuckHook!

---

### Post by him610 on 2017-02-07
FWIW

While reading the different replies on this issue, I found one of my own prior entries from another thread referenced so I decided to see if I experienced the same problems as the OP.

The answer was yes and no; however, I should explain... My Brother MFC7360 network scanner has been set up for months. I just don't use it very often. I have two different computers (desktop and laptop) of comparable age. Both have LTS 1604 installed, main difference desktop was upgraded from LTS 1404+ while the laptop had 1604 installed from scratch to a clean disk.

On the desktop, the scanner software could not even detect the scanner. On the laptop, the scanner software not only detected the scanner, but was also able to scan no problem.

I don't know if this will shed any light on the OP's issue, but I hope it helps.

---

### Post by mollie4168 on 2017-02-07
I'm open to trying a clean install. Unless some other ideas about it come up, I'll give it a try this weekend.

---

### Post by mollie4168 on 2017-02-11
Did a fresh install of 16.04.  The printer is working--see below (I'm not sure what it means that it couldn't resolve me as a host...). Looking for some guidance before I mess around with the scanner again.  Trying not to mess this up.

I have a 64-bit computer.  This is not news, but Brother only has a scanner driver [for 32-bit machines]("http://support.brother.com/g/b/downloadlist.aspx?c=us&lang=en&prod=dcp7065dn_all&os=128").  In the interest of trying to make the scanner that I have work, what do you recommend?  Should I just do the 64-option to scan from the device instead of my computer?  With that option, should scans still show up on my computer? 


```
tracy@tracy:~/Downloads$ sudo su
sudo: unable to resolve host tracy
root@tracy:/home/tracy/Downloads# bash linux-brprinter-installer-2.1.1-1 DCP-7065DN
You are going to install following packages.
   dcp7065dnlpr-2.1.0-1.i386.deb
   cupswrapperDCP7065DN-2.0.4-2.i386.deb
   brscan4-0.4.4-1.amd64.deb
   brscan-skey-0.2.4-1.amd64.deb
OK? [y/N] ->n

root@tracy:/home/tracy/Downloads# bash linux-brprinter-installer-2.1.1-1 DCP-7065DN
You are going to install following packages.
   dcp7065dnlpr-2.1.0-1.i386.deb
   cupswrapperDCP7065DN-2.0.4-2.i386.deb
   brscan4-0.4.4-1.amd64.deb
   brscan-skey-0.2.4-1.amd64.deb
OK? [y/N] ->y


=========================================
Brother License Agreement

=========================================
Do you agree? [Y/n] ->y

wget -T 10 -nd --no-cache http://www.brother.com/pub/bsc/linux/packages/dcp7065dnlpr-2.1.0-1.i386.deb
--2017-02-11 11:54:55--  http://www.brother.com/pub/bsc/linux/packages/dcp7065dnlpr-2.1.0-1.i386.deb
Resolving www.brother.com (www.brother.com)... 23.215.104.153, 23.50.52.75
Connecting to www.brother.com (www.brother.com)|23.215.104.153|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 35008 (34K) [text/plain]
Saving to: ‘dcp7065dnlpr-2.1.0-1.i386.deb’

dcp7065dnlpr-2.1.0- 100%[===================>]  34.19K  --.-KB/s    in 0.01s   

2017-02-11 11:54:55 (3.02 MB/s) - ‘dcp7065dnlpr-2.1.0-1.i386.deb’ saved [35008/35008]


=========================================
GPL License Agreement

=========================================

Do you agree? [Y/n] ->y

wget -T 10 -nd --no-cache http://www.brother.com/pub/bsc/linux/packages/cupswrapperDCP7065DN-2.0.4-2.i386.deb
--2017-02-11 11:54:57--  http://www.brother.com/pub/bsc/linux/packages/cupswrapperDCP7065DN-2.0.4-2.i386.deb
Resolving www.brother.com (www.brother.com)... 23.209.190.57, 23.209.190.41
Connecting to www.brother.com (www.brother.com)|23.209.190.57|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 13318 (13K) [text/plain]
Saving to: ‘cupswrapperDCP7065DN-2.0.4-2.i386.deb’

cupswrapperDCP7065D 100%[===================>]  13.01K  --.-KB/s    in 0.001s  

2017-02-11 11:54:58 (9.81 MB/s) - ‘cupswrapperDCP7065DN-2.0.4-2.i386.deb’ saved [13318/13318]

Hit:1 http://us.archive.ubuntu.com/ubuntu xenial InRelease
Get:2 http://us.archive.ubuntu.com/ubuntu xenial-updates InRelease [102 kB]    
Get:3 http://security.ubuntu.com/ubuntu xenial-security InRelease [102 kB]     
Get:4 http://us.archive.ubuntu.com/ubuntu xenial-backports InRelease [102 kB]  
Get:5 http://security.ubuntu.com/ubuntu xenial-security/main amd64 DEP-11 Metadata [68.2 kB]
Get:6 http://security.ubuntu.com/ubuntu xenial-security/main DEP-11 64x64 Icons [43.0 kB]
Get:7 http://security.ubuntu.com/ubuntu xenial-security/universe amd64 DEP-11 Metadata [32.1 kB]
Get:8 http://security.ubuntu.com/ubuntu xenial-security/universe DEP-11 64x64 Icons [37.0 kB]
Fetched 487 kB in 1s (484 kB/s)                                  
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package ia32-libs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  lib32ncurses5 lib32z1

E: Package 'ia32-libs' has no installation candidate
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  lib32gcc1 libc6-i386
The following NEW packages will be installed:
  lib32gcc1 lib32stdc++6 libc6-i386
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 2,779 kB of archives.
After this operation, 12.5 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libc6-i386 amd64 2.23-0ubuntu5 [2,329 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu xenial/main amd64 lib32gcc1 amd64 1:6.0.1-0ubuntu1 [46.6 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 lib32stdc++6 amd64 5.4.0-6ubuntu1~16.04.4 [404 kB]
Fetched 2,779 kB in 0s (5,149 kB/s)   
Selecting previously unselected package libc6-i386.
(Reading database ... 206533 files and directories currently installed.)
Preparing to unpack .../libc6-i386_2.23-0ubuntu5_amd64.deb ...
Unpacking libc6-i386 (2.23-0ubuntu5) ...
Selecting previously unselected package lib32gcc1.
Preparing to unpack .../lib32gcc1_1%3a6.0.1-0ubuntu1_amd64.deb ...
Unpacking lib32gcc1 (1:6.0.1-0ubuntu1) ...
Selecting previously unselected package lib32stdc++6.
Preparing to unpack .../lib32stdc++6_5.4.0-6ubuntu1~16.04.4_amd64.deb ...
Unpacking lib32stdc++6 (5.4.0-6ubuntu1~16.04.4) ...
Processing triggers for libc-bin (2.23-0ubuntu5) ...
Setting up libc6-i386 (2.23-0ubuntu5) ...
Setting up lib32gcc1 (1:6.0.1-0ubuntu1) ...
Setting up lib32stdc++6 (5.4.0-6ubuntu1~16.04.4) ...
Processing triggers for libc-bin (2.23-0ubuntu5) ...
dpkg -x dcp7065dnlpr-2.1.0-1.i386.deb /
dpkg -x cupswrapperDCP7065DN-2.0.4-2.i386.deb /
dpkg-deb: building package 'dcp7065dnlpr' in 'dcp7065dnlpr-2.1.0-1a.i386.deb'.
dpkg -b ./brother_driver_packdir dcp7065dnlpr-2.1.0-1a.i386.deb
dpkg-deb: building package 'cupswrapperdcp7065dn' in 'cupswrapperDCP7065DN-2.0.4-2a.i386.deb'.
dpkg -b ./brother_driver_packdir cupswrapperDCP7065DN-2.0.4-2a.i386.deb
dpkg -i --force-all dcp7065dnlpr-2.1.0-1a.i386.deb
Selecting previously unselected package dcp7065dnlpr:i386.
(Reading database ... 206846 files and directories currently installed.)
Preparing to unpack dcp7065dnlpr-2.1.0-1a.i386.deb ...
Unpacking dcp7065dnlpr:i386 (2.1.0-1) ...
Setting up dcp7065dnlpr:i386 (2.1.0-1) ...
dpkg -i --force-all cupswrapperDCP7065DN-2.0.4-2a.i386.deb
Selecting previously unselected package cupswrapperdcp7065dn:i386.
(Reading database ... 206863 files and directories currently installed.)
Preparing to unpack cupswrapperDCP7065DN-2.0.4-2a.i386.deb ...
Unpacking cupswrapperdcp7065dn:i386 (2.0.4-2) ...
Setting up cupswrapperdcp7065dn:i386 (2.0.4-2) ...
Restarting cups (via systemctl): cups.service.
#
Will you specify the Device URI? [Y/n] ->n

Test Print? [y/N] ->y

wait 5s.
lpr -P DCP7065DN /usr/share/cups/data/testprint
You are going to install following packages.
   brscan4-0.4.4-1.amd64.deb

=========================================
Brother License Agreement

=========================================
Do you agree? [Y/n] ->y

wget -T 10 -nd --no-cache http://www.brother.com/pub/bsc/linux/packages/brscan4-0.4.4-1.amd64.deb
--2017-02-11 11:56:49--  http://www.brother.com/pub/bsc/linux/packages/brscan4-0.4.4-1.amd64.deb
Resolving www.brother.com (www.brother.com)... 23.215.104.153, 23.50.52.75
Connecting to www.brother.com (www.brother.com)|23.215.104.153|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 73860 (72K) [text/plain]
Saving to: ‘brscan4-0.4.4-1.amd64.deb’

brscan4-0.4.4-1.amd 100%[===================>]  72.13K  --.-KB/s    in 0.02s   

2017-02-11 11:56:49 (4.26 MB/s) - ‘brscan4-0.4.4-1.amd64.deb’ saved [73860/73860]

dpkg -i --force-all brscan4-0.4.4-1.amd64.deb
Selecting previously unselected package brscan4.
(Reading database ... 206866 files and directories currently installed.)
Preparing to unpack brscan4-0.4.4-1.amd64.deb ...
Unpacking brscan4 (0.4.4-1) ...
Setting up brscan4 (0.4.4-1) ...
This software is based in part on the work of the Independent JPEG Group.
You are going to install following packages.
   brscan-skey-0.2.4-1.amd64.deb

=========================================
Brother License Agreement

=========================================
Do you agree? [Y/n] ->y

wget -T 10 -nd --no-cache http://www.brother.com/pub/bsc/linux/packages/brscan-skey-0.2.4-1.amd64.deb
--2017-02-11 11:56:51--  http://www.brother.com/pub/bsc/linux/packages/brscan-skey-0.2.4-1.amd64.deb
Resolving www.brother.com (www.brother.com)... 23.215.104.153, 23.50.52.75
Connecting to www.brother.com (www.brother.com)|23.215.104.153|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 50852 (50K) [text/plain]
Saving to: ‘brscan-skey-0.2.4-1.amd64.deb’

brscan-skey-0.2.4-1 100%[===================>]  49.66K  --.-KB/s    in 0.02s   

2017-02-11 11:56:51 (2.90 MB/s) - ‘brscan-skey-0.2.4-1.amd64.deb’ saved [50852/50852]

dpkg -i --force-all brscan-skey-0.2.4-1.amd64.deb
Selecting previously unselected package brscan-skey.
(Reading database ... 206908 files and directories currently installed.)
Preparing to unpack brscan-skey-0.2.4-1.amd64.deb ...
Unpacking brscan-skey (0.2.4-1) ...
Setting up brscan-skey (0.2.4-1) ...
root@tracy:/home/tracy/Downloads# exit


```

---

### Post by DuckHook on 2017-02-11
Hello mollie4168

Not sure how much help I can be. As stated previously, it's been a while since I've messed around with Brother stuff.

[list=1]
[*]The output from your install says that you've already installed the scanner driver. Does it now scan?
[*]Did you do a:```
sudo apt update
```before installing the Brother drivers?
[*]Your driver install shows an error:```
…
Package ia32-libs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  lib32ncurses5 lib32z
…
```This message was not generated by the driver installation tool. It was generated by your own OS when the driver installation tool tried to download a pkg that doesn't exist. My suspicion is that your version of the scanning driver relies on this pkg and fails because it's not there.

ia32-libs was a hack to get 32-bit apps to run on a 64-bit OS. It was eliminated from the repos a number of versions ago once native multiarch support was built into Ubuntu to run 32-bit apps. Unfortunately, your driver seems to be written for a much earlier time, relying on a hack that no longer exists.
[*]I'm not knowledgeable enough to tell you how to work around this limitation in the Brother driver. I don't know whether it can or cannot be done.
[*]But I *am* reasonably sure that installing the 32-bit version of Ubuntu would be more suitable for this driver because it would then be running in its native architecture and would not require the hack. Seems a shame to go to a 32-bit OS just for the sake of a driver though. However, only you can decide if its worth yet another reinstall.
[/list]
> **mollie4168 said:**
> …In the interest of trying to make the scanner that I have work, what do you recommend?  Should I just do the 64-option to scan from the device instead of my computer?  With that option, should scans still show up on my computer?I don't understand what you mean by these questions. To my knowledge, there is no "64-bit option to scan from the device". Or am I missing something?

---

### Post by mollie4168 on 2017-02-11
1. Simple scan cannot find the scanner.
2. I did an update through system settings-->details before installing the driver.  I didn't go to details looking to do an update, but the option was there and hopefully acts the same as sudo apt update.  Sudo apt update currently says everything's up to date.
3. Thank you for catching this error and the background information on it.  That's good to know for context.
4. That's fine.  You've been really helpful in a lot of other ways.
5. I'll wait and see if any one else has more information. I'm not inclined to do a whole new install again for one driver, yet I suppose if I were to do it, this would be the time since I still haven't redone all my settings, programs, etc on this install.  I'll think about it.

---

### Post by DuckHook on 2017-02-11
> **mollie4168 said:**
> …I'm not inclined to do a whole new install again for one driver, yet I suppose if I were to do it, this would be the time since I still haven't redone all my settings, programs, etc on this install.+1

I'm not even 100% sure it will solve your problem. :-s

Here's a thought: you might try installing Ubuntu 32-bit onto a separate USB stick. You boot from the stick, install the driver onto the OS on the USB stick and see if it works. That way, you don't touch your current install and it gives you the freedom to experiment. If it works, at least you will know that your effort won't be expended running down yet another dead end.

---

### Post by mollie4168 on 2017-02-12
> 

Here's a thought: you might try installing Ubuntu 32-bit onto a separate  USB stick. You boot from the stick, install the driver onto the OS on  the USB stick and see if it works.

That's a really good idea, and I intend to try it.  However, (and this is going way off topic from my scanner), I can't format my USB disk to a) save the 32-bit OS or b) save work files that I scanned to my husband's computer to bring them to my computer so I can finish my work.  ](*,)

When I attempt to format the Ubuntu partition through disks (using the overwrite existing data and FAT options), I get this error: This partition cannot be modified because it contains a partition table; please reinitialize layout of the whole device. (udisks-error-quark, 11)

Everything seems to be pointing toward GParted, so I tried to install Gparted from the software center.  It installs and then immediately the "Install" button shows up next to it again.  It's on my launcher, but when I try to launch it, it asks for my password and then nothing.  See terminal output below.

I attempted to see if I could save the files I need on the free disk space partition, but the Windows computer asked me to format the disk.  It looks like perhaps the 2.2 MB disk was formatted but not the other.  Still no work files.  (I know I could email them or try other options and I may have to, but I'm attempting to limit the number of places they are to protect confidentiality.  Which is also why I've been trying to get the scanner to work directly to my computer again. The work stuff is more venting than anything--I'll figure it out--but it's just added frustration for something that in theory, shouldn't be so difficult!)

Let me know if I should start a new thread.  For now: here's what I was up to prior to trying the USB on the Window's computer:
```
tracy@tracy:~$ lsblk
NAME           MAJ:MIN RM   SIZE RO TYPE  MOUNTPOINT
sda              8:0    0 465.8G  0 disk  
&#9500;&#9472;sda1           8:1    0     1M  0 part  
&#9500;&#9472;sda2           8:2    0 461.8G  0 part  /
&#9492;&#9472;sda3           8:3    0     4G  0 part  
  &#9492;&#9472;cryptswap1 252:0    0     4G  0 crypt [SWAP]
sdb              8:16   1  14.9G  0 disk  
&#9500;&#9472;sdb1           8:17   1   1.4G  0 part  
&#9492;&#9472;sdb2           8:18   1   2.3M  0 part  
sr0             11:0    1  1024M  0 rom   
tracy@tracy:~$ sudo unmount sdb1
sudo: unable to resolve host tracy
[sudo] password for tracy: 
sudo: unmount: command not found
tracy@tracy:~$ sudo umount sdb1
sudo: unable to resolve host tracy
umount: sdb1: mountpoint not found
tracy@tracy:~$ sudo apt-get install gparted
sudo: unable to resolve host pc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  libgtkmm-2.4-1v5 libparted-fs-resize0
Suggested packages:
  xfsprogs reiserfsprogs reiser4progs jfsutils kpartx dmraid gpart
  libparted-dev
The following NEW packages will be installed:
  gparted libgtkmm-2.4-1v5 libparted-fs-resize0
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 1,129 kB of archives.
After this operation, 6,973 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://us.archive.ubuntu.com/ubuntu xenial/main amd64 libgtkmm-2.4-1v5 amd64 1:2.24.4-2 [671 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu xenial/main amd64 libparted-fs-resize0 amd64 3.2-15 [46.4 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu xenial/main amd64 gparted amd64 0.25.0-1 [411 kB]
Fetched 1,129 kB in 0s (2,745 kB/s)
Selecting previously unselected package libgtkmm-2.4-1v5:amd64.
(Reading database ... 206914 files and directories currently installed.)
Preparing to unpack .../libgtkmm-2.4-1v5_1%3a2.24.4-2_amd64.deb ...
Unpacking libgtkmm-2.4-1v5:amd64 (1:2.24.4-2) ...
Selecting previously unselected package libparted-fs-resize0:amd64.
Preparing to unpack .../libparted-fs-resize0_3.2-15_amd64.deb ...
Unpacking libparted-fs-resize0:amd64 (3.2-15) ...
Selecting previously unselected package gparted.
Preparing to unpack .../gparted_0.25.0-1_amd64.deb ...
Unpacking gparted (0.25.0-1) ...
Processing triggers for libc-bin (2.23-0ubuntu5) ...
Processing triggers for bamfdaemon (0.5.3~bzr0+16.04.20160824-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for gnome-menus (3.13.3-6ubuntu3.1) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu5) ...
Processing triggers for mime-support (3.59ubuntu1) ...
Processing triggers for hicolor-icon-theme (0.15-0ubuntu1) ...
Processing triggers for man-db (2.7.5-1) ...
Setting up libgtkmm-2.4-1v5:amd64 (1:2.24.4-2) ...
Setting up libparted-fs-resize0:amd64 (3.2-15) ...
Setting up gparted (0.25.0-1) ...
Processing triggers for libc-bin (2.23-0ubuntu5) ...
tracy@tracy:~$ gksu gparted
The program 'gksu' is currently not installed. You can install it by typing:
sudo apt install gksu
tracy@tracy:~$ sudo apt install gksu
sudo: unable to resolve host pc
[sudo] password for tracy: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  libgksu2-0
The following NEW packages will be installed:
  gksu libgksu2-0
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 123 kB of archives.
After this operation, 877 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://us.archive.ubuntu.com/ubuntu xenial/universe amd64 libgksu2-0 amd64 2.0.13~pre1-6ubuntu8 [71.8 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu xenial/universe amd64 gksu amd64 2.0.2-9ubuntu1 [51.5 kB]
Fetched 123 kB in 0s (596 kB/s)
Selecting previously unselected package libgksu2-0.
(Reading database ... 207035 files and directories currently installed.)
Preparing to unpack .../libgksu2-0_2.0.13~pre1-6ubuntu8_amd64.deb ...
Unpacking libgksu2-0 (2.0.13~pre1-6ubuntu8) ...
Selecting previously unselected package gksu.
Preparing to unpack .../gksu_2.0.2-9ubuntu1_amd64.deb ...
Unpacking gksu (2.0.2-9ubuntu1) ...
Processing triggers for libc-bin (2.23-0ubuntu5) ...
Processing triggers for gconf2 (3.2.6-3ubuntu6) ...
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for bamfdaemon (0.5.3~bzr0+16.04.20160824-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for gnome-menus (3.13.3-6ubuntu3.1) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu5) ...
Processing triggers for mime-support (3.59ubuntu1) ...
Setting up libgksu2-0 (2.0.13~pre1-6ubuntu8) ...
update-alternatives: using /usr/share/libgksu/debian/gconf-defaults.libgksu-sudo to provide /usr/share/gconf/defaults/10_libgksu (libgksu-gconf-defaults) in auto mode
Processing triggers for gconf2 (3.2.6-3ubuntu6) ...
Setting up gksu (2.0.2-9ubuntu1) ...
Processing triggers for libc-bin (2.23-0ubuntu5) ...
tracy@tracy:~$ gksu gparted

(gksu:7213): GConf-CRITICAL **: gconf_value_free: assertion 'value != NULL' failed

(gpartedbin:7304): Gtk-WARNING **: cannot open display: :0
tracy@tracy:~$ lsblk
NAME   MAJ:MIN RM   SIZE RO TYPE  MOUNTPOINT
sda      8:0    0 465.8G  0 disk  
&#9500;&#9472;sda1   8:1    0     1M  0 part  
&#9500;&#9472;sda2   8:2    0 461.8G  0 part  /
&#9492;&#9472;sda3   8:3    0     4G  0 part  
  &#9492;&#9472;cryptswap1
       252:0    0     4G  0 crypt [SWAP]
sdb      8:16   1  14.9G  0 disk  
&#9500;&#9472;sdb1   8:17   1   1.4G  0 part  /media/tracy/Ubuntu 16.04.1 LTS amd64
&#9492;&#9472;sdb2   8:18   1   2.3M  0 part  /mnt/usb-Lexar_USB_Flash_Drive_AANIYRGFG7NI74H
sr0     11:0    1  1024M  0 rom  


```

The last lsblk is current--it doesn't look like anything changed post-Windows "formatting."  Now 2 USB sticks show up in the launcher on my computer.  One for Ubuntu 16.04 with the install files and one with 2.4MB free space.


Update:
I thought I was getting somewhere using [this site]("http://www.wikihow.com/Format-a-USB-Flash-Drive-in-Ubuntu"), but no luck.

```

tracy@tracy:~$ sudo umount /dev/sdb1
sudo: unable to resolve host pc
[sudo] password for tracy: 
tracy@tracy:~$ sudo dd if=/dev/zero of=/dev/sdb bs=4k && sync
sudo: unable to resolve host pc
dd: error writing '/dev/sdb': No space left on device
3910657+0 records in
3910656+0 records out
16018046976 bytes (16 GB, 15 GiB) copied, 911.965 s, 17.6 MB/s
tracy@tracy:~$ lsblk
NAME   MAJ:MIN RM   SIZE RO TYPE  MOUNTPOINT
sda      8:0    0 465.8G  0 disk  
&#9500;&#9472;sda1   8:1    0     1M  0 part  
&#9500;&#9472;sda2   8:2    0 461.8G  0 part  /
&#9492;&#9472;sda3   8:3    0     4G  0 part  
  &#9492;&#9472;cryptswap1
       252:0    0     4G  0 crypt [SWAP]
sdb      8:16   1  14.9G  0 disk  
&#9500;&#9472;sdb1   8:17   1   1.4G  0 part  
&#9492;&#9472;sdb2   8:18   1   2.3M  0 part  /mnt/usb-Lexar_USB_Flash_Drive_AANIYRGFG7NI74H
sr0     11:0    1  1024M  0 rom   
tracy@tracy:~$ sudo dd if=/dev/zero of=/dev/sdb1 bs=4k && sync
sudo: unable to resolve host pc
[sudo] password for tracy: 
dd: error writing '/dev/sdb1': No space left on device
369461+0 records in
369460+0 records out
1513308160 bytes (1.5 GB, 1.4 GiB) copied, 100.91 s, 15.0 MB/s
```

---

### Post by DuckHook on 2017-02-12
Your experiences just keep getting odder and more surreal.

Your system shows a possible mismatch between the two locations where your hostname is recorded. This is the likely reason why gparted won't launch. Did you change any system settings from their defaults after your fresh install? In any case, please do the following:```
cat /etc/hosts
``````
cat /etc/hostname
```Your output should look similar to mine, but where "Xubuntu-min" is replaced with "tracy":```
duckhook@Xubuntu-min:~$  cat /etc/hosts
127.0.0.1	localhost
127.0.1.1	**[COLOR="#FF0000"]Xubuntu-min[/COLOR]**

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
``````
duckhook@Xubuntu-min:~$  cat /etc/hostname
**[COLOR="#FF0000"]Xubuntu-min[/COLOR]**
```I've artificially highlighted the names for emphasis, but your output won't be in red. The two names should be absolutely identical, down to case and punctuation. In my case, it is *Xubuntu-min*. In your case, it should be *tracy*. If this in not the case, then you will need to change one or the other to be identical with its erstwhile twin:```
sudo nano /etc/hostname
```Sudo will complain when you invoke nano because it is trying to resolve to two different hosts for now, but will accept your password anyways. Once you change your hostname to be identical to the one in /etc/hosts, *you must reboot* for changes to take effect. Thereafter, you should be able to use sudo without the error message popping up, and you should also be able to use gparted.

Let's wait to go to next steps until after you solve this one.

---

### Post by mollie4168 on 2017-02-12
This screw up was all me.  I clearly did not understand the impact of changing the name.  When I was setting up the OS, I couldn't remember where "tracy-gazelle-professional" showed up in practice.  I went with it at the time, but it's certainly not my preference to use it.  I was changing it through the System Settings--> Details screen.

I went through once and changed it back to gazelle.  Just modified it again to match case.  Off to restart.  I'll try GParted when I come back.

```
tracy@tracy-gazelle-professional:~$ cat /etc/hosts
127.0.0.1    localhost
127.0.1.1    tracy-Gazelle-Professional

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
tracy@tracy-gazelle-professional:~$ cat /etc/hostname
tracy-gazelle-professional
tracy@tracy-gazelle-professional:~$ sudo nano /etc/hostname
[sudo] password for tracy: 
tracy@tracy-gazelle-professional:~$ cat /etc/hosts
127.0.0.1    localhost
127.0.1.1    tracy-Gazelle-Professional

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
tracy@tracy-gazelle-professional:~$ cat /etc/hostname
tracy-Gazelle-Professional




```

---

### Post by mollie4168 on 2017-02-12
Success!  I'm in GParted.  Thank you.  I can find directions from here.

---

### Post by DuckHook on 2017-02-12
Because I run a lot of VMs and do so by cloning from an existing master image, I must change hostnames all the time. There is nothing wrong with you doing so as long as you make sure to do the identical change in both locations.

---

### Post by mollie4168 on 2017-02-12
I formatted the USB and tried 32-bit Xerus.  Installed the printer, and with the basic instructions on the Brother site for the scanner driver, the scanner did not work.  There's plenty of tinkering that could be had, but that was enough for me after all this.  I'm really glad I tried it.

For now, I'll continue using my husband's computer to scan things and move them to mine.  It's an inconvenience but not the end of the world.  However, I'm going to look into whether it'd be worth it to sell the Brother device and if so, I'd get an HP.  

Again, many thanks for your assistance DuckHook!   You've been wonderful, and I've learned a lot!

---

### Post by DuckHook on 2017-02-12
It's a shame we couldn't get it working, but you've been level-headed, even-tempered and shown the patience of a saint. You deserve a better result. Too bad we cannot just mark this thread "solved".

Good Luck and Happy Ubuntu-ing!

---

### Post by pdc on 2017-02-12
one can install ubuntu on usb; the core install remains; but anything else is forgotten after the power is turned off; one can make a usb stick "persistent" where it acts more like a hard drive, and one can save changes: that is my understanding

________

to install any Brother Scanner, one does need to change the permissions, so a standard user can access the scanner: in recent ubuntu versions, it involves downloading a very small deb file that make changes to [COLOR="#008000"]40-libsane.rules[/COLOR] that lives within [COLOR="#2F4F4F"]/etc/udev/rules.d[/COLOR]

one gets the file from here [http://support.brother.com/g/s/id/linux/en/instruction_scn1c.html?c=us_ot&lang=en&redirect=on#u13.04](http://support.brother.com/g/s/id/linux/en/instruction_scn1c.html?c=us_ot&lang=en&redirect=on#u13.04) .............. the file is called brother-udev-rule-type1-1.0.0-1.all.deb

I don't know if you did that Mollie: I made the comment on the first line (about persistent); thinking that if you were to try the file I mention above, you would need to do the whole brother driver install again as your first lot of downloads would not have been persistent .............

_________________________

I confess there any many nuances to this thread; and much mention of 32bit;

what I wonder about is that if I go here; 

[http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://www.brother.com/pub/bsc/linux/dlf/brscan4-0.4.2-1.amd64.deb&lang=English_lpr](http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://www.brother.com/pub/bsc/linux/dlf/brscan4-0.4.2-1.amd64.deb&lang=English_lpr)

and look for brscan4 (which I understand your DCP-7065DN is ....) that I can click to download what Brother call a [COLOR="#0000FF"]64bit debian package for brscan4[/COLOR]: I see the name of the package is [COLOR="#0000FF"]brscan4-0.4.2-1.amd64.deb[/COLOR] and that makes me think it is for 64bit machines 

and I guess I am thinking maybe that is the package one should try first of all to get the scanner working; 'cos I wasn't sure you had downloaded and installed that file/package

---

### Post by mollie4168 on 2017-02-20
Thanks PDC. It's going to take me a week or two to get back to working on the scanner and try this, but I'll post what happens when I do.

---

### Post by DAB4970 on 2017-05-04
My Brother is MFC-J615W (wireless).  I had to run brsaneconfig3 to get my 16.04/64bit to recognize my scanner.  Steps 5-1 and 5-2 on the linked web page.

[http://support.brother.com/g/s/id/linux/en/instruction_scn1b.html?c=us_ot&lang=en&prod=mfcj615w_all&redirect=on](http://support.brother.com/g/s/id/linux/en/instruction_scn1b.html?c=us_ot&lang=en&prod=mfcj615w_all&redirect=on)

---

### Post by Hamburgian on 2017-09-28
There is quite a simple way to deal with all this...I've spent about a day going through **every** fix on these pages - nothing worked. Rather than going for a fresh install, quite an extreme fix IMO, just uninstall everything to do with sane, I used synaptic to do this, then reinstall and use the Brother Printer install tool [http://support.brother.com/g/b/downloadend.aspx?c=au&lang=en&prod=mfc9330cdw_us_eu_as&os=128&dlid=dlf006893_000&flang=4&type3=625]("http://support.brother.com/g/b/downloadend.aspx?c=au&lang=en&prod=mfc9330cdw_us_eu_as&os=128&dlid=dlf006893_000&flang=4&type3=625")...everyhting done and dusted inside 20 mins!!!

---

### Post by mollie4168 on 2017-10-04
Can you explain which commands/programs you used?  I want to make sure I do it right and don't inadvertently uninstall things that I shouldn't.  The software center only comes up with SimpleScan when I search for sane, but I assume I should be removing more than that.  Thanks!  It would be great if this works!

---

