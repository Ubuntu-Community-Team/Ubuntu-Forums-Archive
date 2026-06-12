---
title: "Error: unable to enumerate USB device on port 1"
date: 2009-06-24
forum: Hardware
---

### Post by AcidRain0 on 2009-06-24
Hi, I am having trouble with my WD my home external hdd. I have been using it on ubuntu for about a month, then all of a sudden it doesn't work anymore as soon as I plug it in. When I plug it in, the hdd turns on, and dmesg will say this over and over, sometimes for 10 mins straight... 

[  600.209066] usb 1-1: new high speed USB device using ehci_hcd and address 29
[  600.264462] hub 1-0:1.0: unable to enumerate USB device on port 1
[  600.453366] hub 1-0:1.0: unable to enumerate USB device on port 1
[  600.641350] hub 1-0:1.0: unable to enumerate USB device on port 1
[  600.828449] hub 1-0:1.0: unable to enumerate USB device on port 1
[  601.016974] hub 1-0:1.0: unable to enumerate USB device on port 1
[  601.277215] usb 3-1: new full speed USB device using uhci_hcd and address 2


but eventually it will work and detect the hdd. I have tried multiple cords, and all of my ports, nothing works. I have also reinstalled ubuntu, and it does it when loading from ubuntu cd. But I have loaded up gentoo a few times from cd, and it has not done it. Does anyone know what is wrong?

---

### Post by AcidRain0 on 2009-06-29
bump

---

### Post by muglikar on 2009-06-29
Hello brother,
                    I have turned to Linux hoping it will solve my problem that my hard drive which is receiving a msg regarding my USB Hard Disk "This device cannot start. (Code 10)"

I have chosen Ubuntu due to recoomendation by a frnd and his advocacy that Ubuntu has huge support and that he has not faced any prob whatsoever whne he used Ubuntu.

I think the problem is because I reinstallled XP sp2, which in turn I did because the HD was running well on my Dell Laptop but its not working on my Desktop...

Another prob is that scrolling on my desktop CRT monitor has suddenly become discrete after I reinstalled XP sp2...

I cant change my Monitor's refresh rate...Earlier I could change it from 60 Hz to 85Hz...

DO U THINK UBUNTU WILL SOLVE THESE PROBLEMS FOR ME?

---

### Post by d4rthpimp on 2009-06-30
@AcidRain0

I am having this problem too with my external USB 2.0 hard drives on a new Dell T300.

Dell product sheet for T300 claims all USB ports are 2.0, but only front ports are identified as 2.0 capable and the rear ports are identified as 1.1, which is untenable for any backup capabilities.

lsusb:
Bus 001 Device 004: ID 04b4:6560 Cypress Semiconductor Corp. CY7C65640 USB-2.0 "TetraHub"
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 413c:2005 Dell Computer Corp. RT7D50 Keyboard
Bus 004 Device 002: ID 413c:3010 Dell Computer Corp. Optical Wheel Mouse
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

I am running 9.10 and have tried slipping usb_storage into /etc/modules per a bug report I found on launchpad to no luck.

I was actually able to get this device mounted at one time by plugging and replugging it, over and over.  It's not a solution by any means.  I have also tried swapping cables and all, USB drive mounts fine on other platforms/machines.

dmesg snipit:
[   28.820491] usb 1-7.2: new high speed USB device using ehci_hcd and address 9
[   28.900113] usb 1-7.2: device descriptor read/64, error -71
[   29.090119] usb 1-7.2: device descriptor read/64, error -71
[   29.280115] usb 1-7.2: new high speed USB device using ehci_hcd and address 10
[   29.360115] usb 1-7.2: device descriptor read/64, error -71
[   29.550114] usb 1-7.2: device descriptor read/64, error -71
[   29.741368] usb 1-7.2: new high speed USB device using ehci_hcd and address 11
[   30.160031] usb 1-7.2: device not accepting address 11, error -71
[   30.240120] usb 1-7.2: new high speed USB device using ehci_hcd and address 12
[   30.660021] usb 1-7.2: device not accepting address 12, error -71
[   30.660128] hub 1-7:1.0: unable to enumerate USB device on port 2

---

### Post by davidcemin on 2009-08-19
Hi, 
Does anyone have already solved this bug?

---

### Post by nidelius on 2010-02-14
Anyone looked more into this I'm geeting the same error

---

### Post by IcarusR on 2010-02-14
Have you tried external power, or at least using second usb port for power ??

---

### Post by nidelius on 2010-02-14
I have indeed, although I'm beginning to suspect there is a hardware faliure involved. The harddrive doesn't work in windows XP or Windows 7 either.

---

### Post by Spooky257 on 2010-02-21
unable to enumerate USB device on port 1

is the same error I'm getting on my front usb ports and I know it's not a hardware issue since they worked fine earlier.  I have 2 partitions, one is running Ubuntu 9.04 and the other is running Mint 8.  Same problem on both sides.

---

### Post by insainb@ssist on 2010-03-01
I have the same problem.  Harddrive definitely works (tried it on my friend's laptop running Windows XP).  Tried different USB port, different USB cable all with the same problem.  I have ntfs-3g installed, my other NTFS formatted harddrive works fine.

# dmesg | tail
[ 4088.476361] hub 1-0:1.0: unable to enumerate USB device on port 3
[ 4088.664368] hub 1-0:1.0: unable to enumerate USB device on port 3
[ 4088.852362] hub 1-0:1.0: unable to enumerate USB device on port 3
[ 4089.040354] hub 1-0:1.0: unable to enumerate USB device on port 3

can't even try mounting it, doesn't show up in fdisk -l:confused:

Anyone find a solution?  If I find something that works I'll post it.

---

### Post by rahfin on 2010-03-13
Having a similiar problem. Usb devices like camera and printers work fine, but usb storage devices are not found.

I enabled usb-storage, ntfs-3g is installed.

I read about the usb2.0 being the problem and the workaround to disable ehci_hcd module but was unable to do that, rmmod or modprobe couldn't find it. It is clearly visible from in dmesg though.

A snippet of dmesg after plugging and unplugging two usb sticks. "Maybe the USB cable is bad?" message repeats when having the usb sticks on.
```

[11509.652094] usb 1-3: new high speed USB device using ehci_hcd and address 37
[11509.752144] hub 1-0:1.0: unable to enumerate USB device on port 3
[11874.204095] hub 1-0:1.0: Cannot enable port 3.  Maybe the USB cable is bad?
[11877.176432] hub 1-0:1.0: Cannot enable port 3.  Maybe the USB cable is bad?
[11880.144075] hub 1-0:1.0: Cannot enable port 3.  Maybe the USB cable is bad?
[11883.112089] hub 1-0:1.0: Cannot enable port 3.  Maybe the USB cable is bad?
[11883.224080] usb 1-7: new high speed USB device using ehci_hcd and address 42
[11883.328151] hub 1-0:1.0: unable to enumerate USB device on port 7
[11904.472097] hub 1-0:1.0: Cannot enable port 3.  Maybe the USB cable is bad?
[11907.440096] hub 1-0:1.0: Cannot enable port 3.  Maybe the USB cable is bad?
[11910.408093] hub 1-0:1.0: Cannot enable port 3.  Maybe the USB cable is bad?
[11913.376095] hub 1-0:1.0: Cannot enable port 3.  Maybe the USB cable is bad?
[11913.616090] usb 1-7: new high speed USB device using ehci_hcd and address 47
[11913.716121] hub 1-0:1.0: unable to enumerate USB device on port 7
[11927.340096] hub 1-0:1.0: Cannot enable port 3.  Maybe the USB cable is bad?
[11930.308096] hub 1-0:1.0: Cannot enable port 3.  Maybe the USB cable is bad?
[11933.276124] hub 1-0:1.0: Cannot enable port 3.  Maybe the USB cable is bad?
[11936.244118] hub 1-0:1.0: Cannot enable port 3.  Maybe the USB cable is bad?
[11939.212116] hub 1-0:1.0: Cannot enable port 7.  Maybe the USB cable is bad?
[11942.180123] hub 1-0:1.0: Cannot enable port 7.  Maybe the USB cable is bad?
[11945.148114] hub 1-0:1.0: Cannot enable port 7.  Maybe the USB cable is bad?
[11948.116096] hub 1-0:1.0: Cannot enable port 7.  Maybe the USB cable is bad?
[12802.472072] hub 1-0:1.0: Cannot enable port 3.  Maybe the USB cable is bad?
[12805.440124] hub 1-0:1.0: Cannot enable port 3.  Maybe the USB cable is bad?
[12808.432105] hub 1-0:1.0: Cannot enable port 3.  Maybe the USB cable is bad?
[12811.404432] hub 1-0:1.0: Cannot enable port 3.  Maybe the USB cable is bad?
[12814.380097] hub 1-0:1.0: Cannot enable port 7.  Maybe the USB cable is bad?
[12817.348106] hub 1-0:1.0: Cannot enable port 7.  Maybe the USB cable is bad?
[12820.316096] hub 1-0:1.0: Cannot enable port 7.  Maybe the USB cable is bad?
[12823.284092] hub 1-0:1.0: Cannot enable port 7.  Maybe the USB cable is bad?
[13440.844089] hub 1-0:1.0: Cannot enable port 3.  Maybe the USB cable is bad?
[13443.812089] hub 1-0:1.0: Cannot enable port 3.  Maybe the USB cable is bad?
[13446.780089] hub 1-0:1.0: Cannot enable port 3.  Maybe the USB cable is bad?
[13449.748087] hub 1-0:1.0: Cannot enable port 3.  Maybe the USB cable is bad?
[13452.716096] hub 1-0:1.0: Cannot enable port 7.  Maybe the USB cable is bad?
[13455.684119] hub 1-0:1.0: Cannot enable port 7.  Maybe the USB cable is bad?
[13458.652105] hub 1-0:1.0: Cannot enable port 7.  Maybe the USB cable is bad?
[13461.620106] hub 1-0:1.0: Cannot enable port 7.  Maybe the USB cable is bad?

```

---

### Post by 1serveyou on 2010-04-09
I'm getting the same error but mine is saying on port 2. It is a 2.5 laptop hard drive that I'm using an external enclosure, and I know it works because I just tried it on my latpop. The hard drive has my backup of a PS3, but I don't need that info if I have to reformat. Any help would greatly be appreciated.

---

### Post by TaimurK on 2010-07-09
I have problems with my USB to Serial cable Pl2303, Visual Communication Camera VGP-VCC4 R5U870 and USB HDD Enclosure ID 05e3:0702 Genesys Logic, Inc. USB 2.0 IDE Adapter on my Vaio Laptop FZ150E
:(

---

### Post by imnotjack on 2010-08-11
Hi All.
I have the same problem with all external drives... Including my phone through the usb cord. I know they get power due to the fact that my phone will charge when its plugged in, and most of the time there is a delay in recognizing the device if it will be recognized at all. On this same topic in another thread I saw that a recent kernel as of Ubuntu 9.04/.10 (I don't remember which) was the cause of the issue, and that using a former kernel fixed this problem. nobody knows exactly why this issue exists or how to fix it but that it is related to the newest series of kernels. I'm not sure how to downgrade my kernel though....
Hope this points someone in the right direction and if anyone finds an answer please do post here again. :) nice talking with ya'll. TTYL! :D
John

---

### Post by aircooledbusnut on 2010-08-30
Same problem. However it is my internal webcam on my sony laptop.

---

### Post by e_victor480 on 2010-08-31
I have this problem with a mouse on my Laptop. 

Im running Lucid Lynx 10.04
It started about a month ago with a mouse i have used for over a year. Then fried 2 mice*?? in the same day and they will not work on any computer. 

When it first happened my output screenlet threw an error reading "Port # over current" and external speakers and the led's flickered until i unplugged the mouse. 

Today I took the mouse apart to see if it was damaged visibly. Tried it one more time and it threw a new error code. 
"unable to enumerate usb device #"

This happens on all my usb ports with this mouse but my external speakers and my cooling pad both work error free. 
Not sure if my problem is related to others but the more info the better i say.

Greatly puzzled in Canada.

---

### Post by imnotjack on 2010-09-03
OK Everyone!!!!!
I have somewhat of a cumbersome fix.
In desperation I discovered something that is so simple it blew my mind!!!!!
you might want to print these instructions or copy them or something just make them accessible apart from this web page.

1-reboot your computer
2-login normally
3-switch to terminal mode " CRTL ALT F1 "
4-login ( user name, Password )
5-plug in device that gets the error messages 
6- type in the word " help "
(typing anything while the error messages are shooting up all over the place won't render the command invalid it just makes it hard for a human to read. the computer keeps track of all that is put in by the keyboard and will execute the broken command.It should then stop giving the errors and if it is a flash drive or usb hard drive then it should say something like "assuming drive cache write through" I've done this 3 times successfully. )
7-type in " sudo service gdm restart "
(this will log you out and perform a normal login)
Note:This cannot be done in a normal Terminal window. you must be in a terminal mode.

Anyway hope this helps others the way it helped me and/or show some blessed soul how to fix the darn thing for us. or teach us how to fix it for that matter... lol :)

John

---

### Post by Neva on 2010-10-08
Thank you imnotjack and John, the shutdown fix worked.

In my case, I could not see the printer listed on lsusb
 
 Error -71 was typical.

Tried various fixes, they didn't help:

A 3 minute shutdown first with the PSU not switched off. That didn't help.

Step 7 here - [http://hplipopensource.com/hplip-web/install/manual/distros/ubuntu.html](http://hplipopensource.com/hplip-web/install/manual/distros/ubuntu.html)
```
sudo usermod -a -G lp $USER
``` Hotfix here -  [http://www.novell.com/support/search.do?cmd=displayKC&docType=kc&externalId=7002864&sliceId=1&docTypeID=DT_TID_1_1](http://www.novell.com/support/search.do?cmd=displayKC&docType=kc&externalId=7002864&sliceId=1&docTypeID=DT_TID_1_1)
```
echo -1 > /sys/module/usbcore/parameters/autosuspend
```Then tried the fix to shut down the computer completely, turn off the power supply for 30mins.

That worked and lsusb shows the printer again.

---

### Post by gad241 on 2010-10-13
I too am seeing this problem with Ubuntu 9.04, 2.6.28-19-generic kernel. I tried the various "fixes" posted in this thread without results. I'm using a Belkin USB wireless adapter version 4. I have rebooted the machine many times and have shutdown the machine and then unplugged the power for 10-15 minutes. Powered back up with the same results. 

Somebody mention that there may not be enough power from usb port. With that thought I plugged the USB wifi into a powered usb hub. Same symptoms but with a new observation; The LED on the usb wifi stick was lit up but the port LED on the hub that the stick was plugged into was not. Odd. Anyway, I got sidetracked and then noticed the port LED on the hub was lit. I have see this this before (w/o the usb hub) that the the system finally recognized the USB wifi stick by randomly performing the "lsusb" command.

I have two other machines running Ubuntu 9.04 (one x64 version) that do not suffer from this issue.

I haven't tried an external hard drive to see if the problem shows up again.

---

### Post by gad241 on 2010-10-15
Just a follow up to my last post. I plugged in a USB external drive and it was correctly recognized and does not produce the error of the OP. I believe that it is a driver issue concerning my USB wireless stick.

---

### Post by jimboat on 2010-10-16
I've been having the same problem with a WD My passport hard drive, which I have resolved if it's of any help.
 
It's been a long running problem, with a former WD drive failing. The new one failed to mount, So this time I re-formatted to ext 4, and it initially worked (I use as a back up drive.) Then failed to mount the second time. 

Latest error from dmesg was:
48.050026] usb 6-1: new full speed USB device using uhci_hcd and address 6
[   48.470072] usb 6-1: device not accepting address 6, error -71
[   48.470081] hub 6-0:1.0: unable to enumerate USB device on port 1


I tried installing usbmount, and pmount, and then had permission problems with USB memory sticks with FAT32.

I finally removed usbmount and pmount which resolved the permission problems, but the wd would still not mount. Someone mentioned power earlier. I had a 2 into 1 usb lead left over from a vodem stick that works fine (on linux!) without it. Plug the two leads in first, then the drive into the end and bingo, drive appeared like magic on the desktop.

Thanks for the advice above, it helped to work through the problem!

---

### Post by mogli2 on 2010-12-19
Hi all,

I was receiving the same error message when trying to connect my new phone to my machine (connecting under windows didn't work either). On a different machine it worked without a problem, so I imagined it was a problem with my USB controller.

Turns out: For me a BIOS upgrade solved the problem! (My previous BIOS was from mid 2009 and was the 1.0 version from the manufacturer.)

Hope this helps others, too.

---

### Post by mgw2008 on 2011-01-02
> **imnotjack said:**
> OK Everyone!!!!!
I have somewhat of a cumbersome fix.
In desperation I discovered something that is so simple it blew my mind!!!!!
you might want to print these instructions or copy them or something just make them accessible apart from this web page.

1-reboot your computer
2-login normally
3-switch to terminal mode " CRTL ALT F1 "
4-login ( user name, Password )
5-plug in device that gets the error messages 
6- type in the word " help "
(typing anything while the error messages are shooting up all over the place won't render the command invalid it just makes it hard for a human to read. the computer keeps track of all that is put in by the keyboard and will execute the broken command.It should then stop giving the errors and if it is a flash drive or usb hard drive then it should say something like "assuming drive cache write through" I've done this 3 times successfully. )
7-type in " sudo service gdm restart "
(this will log you out and perform a normal login)
Note:This cannot be done in a normal Terminal window. you must be in a terminal mode.

Anyway hope this helps others the way it helped me and/or show some blessed soul how to fix the darn thing for us. or teach us how to fix it for that matter... lol :)

John

Gee... I've been searching for weeks now to fix my Kubuntu systems after migrating from 10.04 (everything works) to 10.10 (can't connect to USB HD anymore). Just replace the "gdm" with "kdm" in the restart command line.

Add'l remark: USB doesn't reconnect after suspend (ACPI S3).

Txs a ton

---

### Post by enid on 2011-03-07
Hi,

After some searches and solutions that didn't work for me , I found this: [http://www.absolutelytech.com/2010/04/18/solved-unable-to-enumerate-usb-device-disabling-ehci_hcd/ ]("http://www.absolutelytech.com/2010/04/18/solved-unable-to-enumerate-usb-device-disabling-ehci_hcd/")
and it worked for me.
Didn't find why the  load average kept staying over 1.5 but now it has  decreased below .5 because of the warnings on syslog disappearing.             

Regards

---

### Post by daelomin on 2011-03-23
It did not work for me at first in Ubuntu 10.10.

I found an esoteric solution : unplug the pc (in my case a laptop removed from the docking station), press & hold the power button for 20s (provoking a hard shutdown).

Restart it... plug it in... worked. Quite weird...

---

### Post by Sonja on 2011-06-26
enid's solution worked for me. Yay!

---

### Post by demiurg on 2011-07-16
enid's solution does not seem to work for me

---

### Post by demiurg on 2011-07-16
Well, looks like it did work for me eventually, but... what confused me is that I still got the "unable to enumerate" error message, but than it stopped and the disk started working.

However, I now get this error message from time to time which does not look good

 kernel: [  548.617143] sd 7:0:0:0: [sdc]  Sense Key : Recovered Error [current] [descriptor]
 kernel: [  548.617159] Descriptor sense data with sense descriptors (in hex):
 kernel: [  548.617164]         72 01 04 1d 00 00 00 0a 09 0c 00 00 00 00 00 07 
 kernel: [  548.617185]         00 00 
 kernel: [  548.617193] sd 7:0:0:0: [sdc]  ASC=0x4 ASCQ=0x1d
 kernel: [  579.036882] sd 7:0:0:0: [sdc]  Sense Key : Recovered Error [current] [descriptor]
 kernel: [  579.036898] Descriptor sense data with sense descriptors (in hex):
 kernel: [  579.036903]         72 01 04 1d 00 00 00 0e 09 0c 00 00 00 00 00 07 
 kernel: [  579.036924]         00 00 00 00 40 50 
 kernel: [  579.036936] sd 7:0:0:0: [sdc]  ASC=0x4 ASCQ=0x1d
 kernel: [  580.240915] sd 7:0:0:0: [sdc]  Sense Key : Recovered Error [current] [descriptor]
 kernel: [  580.240930] Descriptor sense data with sense descriptors (in hex):
 kernel: [  580.240935]         72 01 04 1d 00 00 00 0e 09 0c 00 00 00 00 00 00 
 kernel: [  580.240956]         00 4f 00 c2 00 50 
 kernel: [  580.240967] sd 7:0:0:0: [sdc]  ASC=0x4 ASCQ=0x1d
 kernel: [  643.699566] sd 7:0:0:0: [sdc] Unhandled error code
 kernel: [  643.699576] sd 7:0:0:0: [sdc]  Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK
 kernel: [  643.699585] sd 7:0:0:0: [sdc] CDB: Read(10): 28 00 00 01 37 5f 00 00 80 00
 kernel: [  643.699605] end_request: I/O error, dev sdc, sector 79711


Something's seriously ****** up with USB 3.0 in the recent kernel

---

### Post by rsbrux on 2011-09-18
I am having a similar problem with various linux distros,including various versions of clonezilla, RescueDisk, Fedora and in this case, Mythbuntu 11.04.  The problem is repeated, almost continuous, appearance of the error message &quot;unable to enumerate USB device on port 7&quot;, even after unplugging all external USB devices.  This prevents GUI display even in recovery mode.  Oddly enough, I was able to use the system normally until I had finished configuring the myth backend, at which time these symptoms. My system supports only USB 2.0, and there is no BIOS update available for it.  The problem appears to have been introduced (into the kernel?) some time ago, as some users report that the error messages only appeared after an update.  See [https://bugzilla.redhat.com/show_bug.cgi?id=511391](https://bugzilla.redhat.com/show_bug.cgi?id=511391) for some historical background.  The problem appears to be no longer present in Clonezilla live 1.2.8.46.  However, it is hard to be sure, because I only ever use Clonezilla briefly, and the problem only showed up in Mythbuntu after a couple of days.  I had high hopes of migrating my HTPC from Windoze to Linux, but these hopes are dashed, at least until this problem can be solved.     
     
  P.S. Further research turns up many reports of this error coming and going, going back to 2006.  Active bug reports are, for example, 666563 and 725108 in the Red Hat list (mentioned previously above) and [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/836816](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/836816).  This last is marked &quot;new&quot; and as affecting &quot;1 person&quot;, both of which indications are seriously misleading.  I am still waiting for my edit/post/write authorization for launchpad.  Meanwhile, I beg all others affected by this bug to add yourselves to it and to add appropriate links to other instances, so that it gets the appropriate level of attention.

---

