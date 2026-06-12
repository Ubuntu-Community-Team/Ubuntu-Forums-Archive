---
title: "HP Mini 5102 - Qualcomm Gobi2000 WWAN and GPS under 9.10 or 10.04"
date: 2010-04-17
forum: Hardware
---

### Post by ronzo on 2010-04-17
I am owner of a HP Mini 5102 with an integrated WWAN/GPS-Chip from Qualcomm (Gobi 2000). 

Has anyone here managed to get this working?

I found some hints on [http://www.madox.net/blog/projects/hp-probook-5310m-ubuntu-reference/](http://www.madox.net/blog/projects/hp-probook-5310m-ubuntu-reference/) but it seems my device id (03f0:231d) does not match with the ones listed in the patched qcserial.c ...

Here are the steps I did:

1) After adding my device id to qcserial, building and installing it, /dev/ttyUSB0 shows up.
2) With gobi_loader 0.4 (which is needed for gobi2000 and can be obtained here: [http://www.codon.org.uk/~mjg59/gobi_loader/](http://www.codon.org.uk/~mjg59/gobi_loader/) ) I could sucessfully load the firmware into the device.

Network manager does not show the Qualcomm device even though it (hp 2400un) is listed as a supported device on [http://live.gnome.org/NetworkManager/MobileBroadband](http://live.gnome.org/NetworkManager/MobileBroadband) - but maybe not in version 0.7.996 (ubuntu karmic uses).

I am pretty sure to be able to establish a WWAN connection using wvdial... we'll see.

I found this on the network manager site:
> I have a driver, but NetworkManager doesn't find my device

NetworkManager probes modems automatically to determine their capabilities. NetworkManager 0.7.x only probes known mobile broadband drivers to avoid interfering with non-3G serial devices. That does *not* include the generic usbserial driver, because it most often drives non-3G devices. To probe modems that are driven by usbserial with NetworkManager 0.7.x, edit the /lib/udev/rules.d/77-nm-probe-modem-capabilities.rules file and change the line:

DRIVERS=="option|sierra|hso|cdc_acm|qcserial|moto-modem", GOTO="probe"

to

DRIVERS=="option|sierra|hso|cdc_acm|qcserial|moto-modem|usbserial_generic", GOTO="probe"

and replug your modem. NetworkManager should then see it. If that still does not allow NetworkManager to find your modem, your modem may not yet be supported. Please file a bug and report the 'lsusb' output and other details of your device. 

In karmic there is no 77-nm-probe-modem-capabilities.rules file. Where can I add the usbserial_generic driver?

---

### Post by n00b2ubuntu on 2010-06-09
Same computer, same problem. Did you ever find a solution?

thanks,

Alex

---

### Post by alexlist on 2010-10-06
First the good news:

I used the Ubuntu 10.10 RC (assuming there won't be a lot of changes until Sunday).

My hardware is slightly different (using a Lenovo ThinkPad x201, type 3626-A14), but I also use the gobi2000 that is available as an option for this laptop.

However, qcserial as delivered with 10.10 and the kernel linux-image-2.6.35-22-generic (x86_64) now support the Gobi 2000, and gobi-loader 0.7 is available as an Ubuntu package!

Of course, one still has to download the binary firmware for the Gobi 2000, which is only available for Windows :(

I downloaded the Windows firmware from Lenovo:

[http://www-307.ibm.com/pc/support/site.wss/MIGR-70656.html](http://www-307.ibm.com/pc/support/site.wss/MIGR-70656.html)

This page has a section "Networking: Wireless WAN", and a subsection "ThinkPad Wireless WAN (UNDP)              - Qualcomm Gobi2000". There I found 

[http://www-307.ibm.com/pc/support/site.wss/document.do?lndocid=MIGR-72938](http://www-307.ibm.com/pc/support/site.wss/document.do?lndocid=MIGR-72938)

and finally a link to the firmware:

[http://download.lenovo.com/ibmdl/pub/pc/pccbbs/mobiles/7xwc44ww.exe](http://download.lenovo.com/ibmdl/pub/pc/pccbbs/mobiles/7xwc44ww.exe)

I managed to extract this using Wine, just by calling
```

wine 7xwc44ww.exe
```This will create C:\DRIVERS\WWANQL, which is available from Linux under 
~/.wine/drive_c/DRIVERS/WWANQL.

There, you will find a file 

~/.wine/drive_c/DRIVERS/WWANQL/Driver/GobiInstaller.msi

I didn't manage to extract this msi file on Linux in a meaningful way. cabextract will just produce files with unusable names, and msiexec under Wine doesn't seem to be capable to extract it. So, I went to a Windows machine to extract GobiInstaller.msi, like this:

```
 msiexec /a GobiInstaller.msi TARGETDIR=C:\TEMP
```This will create a "network install" version of the installer, which means all the necessary files are - finally - unpacked to C:\TEMP\gobi2000

I re-packaged everything to copy it back to Ubuntu, and named the file 7xwc44ww.zip 

Now the tricky part - I didn't know which of the many firmware versions to use:

```
alex@thinkpad:~/Downloads$ unzip -l 7xwc44ww.zip 
Archive:  7xwc44ww.zip
  Length      Date    Time    Name
---------  ---------- -----   ----
        0  2010-10-05 22:03   gobi2000/
        0  2010-10-05 22:03   gobi2000/Data Folder/
        0  2010-04-26 09:34   gobi2000/Data Folder/Options2kLenovo.txt
  2138624  2010-10-05 22:03   gobi2000/GobiInstaller.msi
        0  2010-10-05 22:03   gobi2000/Images/
        0  2010-10-05 22:03   gobi2000/Images/Lenovo/
        0  2010-10-05 22:03   gobi2000/Images/Lenovo/0/
      120  2010-04-26 07:58   gobi2000/Images/Lenovo/05c69205.did
     9284  2009-10-16 05:36   gobi2000/Images/Lenovo/0/UQCN.mbn
        0  2010-10-05 22:03   gobi2000/Images/Lenovo/1/
        0  2010-10-05 22:03   gobi2000/Images/Lenovo/12/
 11259956  2009-10-26 16:50   gobi2000/Images/Lenovo/12/amss.mbn
  3186732  2009-10-26 16:48   gobi2000/Images/Lenovo/12/apps.mbn
    12836  2009-10-16 10:14   gobi2000/Images/Lenovo/12/UQCN.mbn
  6582324  2009-04-13 12:49   gobi2000/Images/Lenovo/1/amss.mbn
  3022892  2009-04-13 12:48   gobi2000/Images/Lenovo/1/apps.mbn
    17136  2009-11-06 18:20   gobi2000/Images/Lenovo/1/UQCN.mbn
        0  2010-10-05 22:03   gobi2000/Images/Lenovo/2/
     9896  2009-10-19 21:37   gobi2000/Images/Lenovo/2/UQCN.mbn
        0  2010-10-05 22:03   gobi2000/Images/Lenovo/3/
  6639668  2009-05-26 11:55   gobi2000/Images/Lenovo/3/amss.mbn
  3506220  2009-05-26 11:54   gobi2000/Images/Lenovo/3/apps.mbn
    57252  2009-11-17 15:13   gobi2000/Images/Lenovo/3/UQCN.mbn
        0  2010-10-05 22:03   gobi2000/Images/Lenovo/4/
     9284  2009-10-16 15:53   gobi2000/Images/Lenovo/4/UQCN.mbn
        0  2010-10-05 22:03   gobi2000/Images/Lenovo/6/
    10524  2009-12-03 11:06   gobi2000/Images/Lenovo/6/UQCN.mbn
        0  2010-10-05 22:03   gobi2000/Images/Lenovo/7/
     9284  2009-10-15 20:51   gobi2000/Images/Lenovo/7/UQCN.mbn
        0  2010-10-05 22:03   gobi2000/Images/Lenovo/8/
     9284  2009-10-15 22:52   gobi2000/Images/Lenovo/8/UQCN.mbn
        0  2010-10-05 22:03   gobi2000/Images/Lenovo/9/
     9284  2009-10-16 12:39   gobi2000/Images/Lenovo/9/UQCN.mbn
        0  2010-10-05 22:03   gobi2000/Images/Lenovo/UMTS/
 11096116  2009-04-08 07:53   gobi2000/Images/Lenovo/UMTS/amss.mbn
  3104812  2009-04-08 07:52   gobi2000/Images/Lenovo/UMTS/apps.mbn
        0  2010-10-05 22:03   gobi2000/Module Retargetable Folder/
        0  2010-10-05 22:03   gobi2000/Module Retargetable Folder/amd64/
   519232  2010-04-26 07:58   gobi2000/Module Retargetable Folder/amd64/DIFxAPI.dll
   324344  2010-04-26 08:01   gobi2000/Module Retargetable Folder/amd64/DriverInstaller64.exe
     7595  2010-04-26 07:58   gobi2000/Module Retargetable Folder/amd64/qcfilterlno2k.cat
     2520  2010-04-26 09:33   gobi2000/Module Retargetable Folder/amd64/qcfilterlno2k.inf
     6400  2010-04-26 07:58   gobi2000/Module Retargetable Folder/amd64/qcfilterlno2k.sys
     7955  2010-04-26 09:33   gobi2000/Module Retargetable Folder/amd64/qcmdmlno2k.inf
     3874  2010-04-26 09:33   gobi2000/Module Retargetable Folder/amd64/qcnetlno2k.inf
     3594  2010-04-26 09:33   gobi2000/Module Retargetable Folder/amd64/qcserlno2k.inf
     7626  2010-04-26 07:58   gobi2000/Module Retargetable Folder/amd64/qcusbnetlno2k.cat
   138240  2010-04-26 07:58   gobi2000/Module Retargetable Folder/amd64/qcusbnetlno2k.sys
     8705  2010-04-26 07:58   gobi2000/Module Retargetable Folder/amd64/qcusbserlno2k.cat
   121600  2010-04-26 07:58   gobi2000/Module Retargetable Folder/amd64/qcusbserlno2k.sys
        0  2010-10-05 22:03   gobi2000/Module Retargetable Folder/win7/
        0  2010-10-05 22:03   gobi2000/Module Retargetable Folder/win7/amd64/
   717048  2010-04-26 07:58   gobi2000/Module Retargetable Folder/win7/amd64/PDSHelperlno.dll
     8404  2010-04-26 07:58   gobi2000/Module Retargetable Folder/win7/amd64/qclocationsensorlno.cat
    91384  2010-04-26 07:58   gobi2000/Module Retargetable Folder/win7/amd64/QCLocationSensorlno.dll
     4443  2010-04-26 07:58   gobi2000/Module Retargetable Folder/win7/amd64/QCLocationSensorlno.inf
     4197  2010-04-26 09:33   gobi2000/Module Retargetable Folder/win7/amd64/qcnetlno2k.inf
     7524  2010-04-26 07:58   gobi2000/Module Retargetable Folder/win7/amd64/qcusbnetlno2k.cat
   243712  2010-04-26 07:58   gobi2000/Module Retargetable Folder/win7/amd64/qcusbnetlno2k.sys
  2152176  2010-04-26 07:58   gobi2000/Module Retargetable Folder/win7/amd64/WUDFUpdate_01009.dll
        0  2010-10-05 22:03   gobi2000/Module Retargetable Folder/win7/x86/
   554232  2010-04-26 07:58   gobi2000/Module Retargetable Folder/win7/x86/PDSHelperlno.dll
     8404  2010-04-26 07:58   gobi2000/Module Retargetable Folder/win7/x86/qclocationsensorlno.cat
    68344  2010-04-26 07:58   gobi2000/Module Retargetable Folder/win7/x86/QCLocationSensorlno.dll
     4443  2010-04-26 07:58   gobi2000/Module Retargetable Folder/win7/x86/QCLocationSensorlno.inf
     4197  2010-04-26 09:33   gobi2000/Module Retargetable Folder/win7/x86/qcnetlno2k.inf
     7524  2010-04-26 07:58   gobi2000/Module Retargetable Folder/win7/x86/qcusbnetlno2k.cat
   209408  2010-04-26 07:58   gobi2000/Module Retargetable Folder/win7/x86/qcusbnetlno2k.sys
  1837296  2010-04-26 07:58   gobi2000/Module Retargetable Folder/win7/x86/WUDFUpdate_01009.dll
        0  2010-10-05 22:03   gobi2000/Module Retargetable Folder/x86/
   323648  2010-04-26 07:58   gobi2000/Module Retargetable Folder/x86/DIFxAPI.dll
     7571  2010-04-26 07:58   gobi2000/Module Retargetable Folder/x86/qcfilterlno2k.cat
     2520  2010-04-26 09:33   gobi2000/Module Retargetable Folder/x86/qcfilterlno2k.inf
     5248  2010-04-26 07:58   gobi2000/Module Retargetable Folder/x86/qcfilterlno2k.sys
     7955  2010-04-26 09:33   gobi2000/Module Retargetable Folder/x86/qcmdmlno2k.inf
     3874  2010-04-26 09:33   gobi2000/Module Retargetable Folder/x86/qcnetlno2k.inf
     3594  2010-04-26 09:33   gobi2000/Module Retargetable Folder/x86/qcserlno2k.inf
     7602  2010-04-26 07:58   gobi2000/Module Retargetable Folder/x86/qcusbnetlno2k.cat
   117248  2010-04-26 07:58   gobi2000/Module Retargetable Folder/x86/qcusbnetlno2k.sys
     8669  2010-04-26 07:58   gobi2000/Module Retargetable Folder/x86/qcusbserlno2k.cat
   106880  2010-04-26 07:58   gobi2000/Module Retargetable Folder/x86/qcusbserlno2k.sys
        0  2010-10-05 22:03   gobi2000/QDLService2k/
   331512  2010-04-26 09:31   gobi2000/QDLService2k/QDLService2kLenovo.exe
---------                     -------
 58692270                     83 files

```According to the description by

[http://www.codon.org.uk/~mjg59/gobi_loader/]("http://www.codon.org.uk/%7Emjg59/gobi_loader/")

you need three files for 3G cards:

I chose these two:

```
 11096116  2009-04-08 07:53   gobi2000/Images/Lenovo/UMTS/amss.mbn
  3104812  2009-04-08 07:52   gobi2000/Images/Lenovo/UMTS/apps.mbn
```and this one:

```
    10524  2009-12-03 11:06   gobi2000/Images/Lenovo/6/UQCN.mbn
```and put them to /lib/firmware/gobi.

Be patient, we're almost there...

After rebooting, I see the following:

```
alex@thinkpad:~/Downloads$ lsusb
Bus 002 Device 003: ID 05c6:9205 Qualcomm, Inc. 

alex@thinkpad:~/Downloads$ dmesg |grep -i qcs
[   19.150575] qcserial 2-1.4:1.2: Qualcomm USB modem converter detected
[   19.150774] usbcore: registered new interface driver qcserial
```So far so good...

I can now go to Network Manager and create a "Mobile Broadband" connection. This even allows me to select the Gobi 2000, my mobile operator (Swisscom, Switzerland) and voilà, I can see "Swisscom Default 1" under "Mobile broadband" in Network manager.

That's how far we got...

1.) have qcserial detect and recognize the card
2.) have gobi_loader load the firmware
3.) have ttyUSB0 created

If I try to connect, I get the following error: "GSM network disconnected".

/var/log/daemon.log shows the following:

```
Oct  6 12:25:31 thinkpad NetworkManager[1140]: <info> Activation (ttyUSB0) starting connection 'Swisscom Default 1'
Oct  6 12:25:31 thinkpad NetworkManager[1140]: <info> (ttyUSB0): device state change: 3 -> 4 (reason 0)
Oct  6 12:25:31 thinkpad NetworkManager[1140]: <info> Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) scheduled...
Oct  6 12:25:31 thinkpad NetworkManager[1140]: <info> Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) started...
Oct  6 12:25:31 thinkpad NetworkManager[1140]: <info> (ttyUSB0): device state change: 4 -> 6 (reason 0)
Oct  6 12:25:31 thinkpad NetworkManager[1140]: <info> Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) complete.
Oct  6 12:25:31 thinkpad NetworkManager[1140]: <info> Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) scheduled...
Oct  6 12:25:31 thinkpad NetworkManager[1140]: <info> Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) started...
Oct  6 12:25:31 thinkpad NetworkManager[1140]: <info> (ttyUSB0): device state change: 6 -> 4 (reason 0)
Oct  6 12:25:31 thinkpad NetworkManager[1140]: <info> Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) complete.
Oct  6 12:25:31 thinkpad modem-manager: (ttyUSB0) opening serial device...
Oct  6 12:25:31 thinkpad modem-manager: Modem /org/freedesktop/ModemManager/Modems/0: state changed (disabled -> enabling)
Oct  6 12:25:31 thinkpad modem-manager: Got failure code 100: Unknown error
Oct  6 12:25:31 thinkpad modem-manager: last message repeated 2 times
Oct  6 12:25:31 thinkpad modem-manager: Modem /org/freedesktop/ModemManager/Modems/0: state changed (enabling -> disabled)
Oct  6 12:25:31 thinkpad modem-manager: (ttyUSB0) closing serial device...
Oct  6 12:25:31 thinkpad NetworkManager[1140]: <warn> GSM modem enable failed: (32) Failed to find a usable modem character set
Oct  6 12:25:31 thinkpad NetworkManager[1140]: <info> (ttyUSB0): device state change: 4 -> 9 (reason 28)
Oct  6 12:25:31 thinkpad NetworkManager[1140]: <info> Marking connection 'Swisscom Default 1' invalid.
Oct  6 12:25:31 thinkpad NetworkManager[1140]: <warn> Activation (ttyUSB0) failed.
Oct  6 12:25:31 thinkpad NetworkManager[1140]: <info> (ttyUSB0): device state change: 9 -> 3 (reason 0)
Oct  6 12:25:31 thinkpad NetworkManager[1140]: <info> (ttyUSB0): deactivating device (reason: 0).
Oct  6 12:25:31 thinkpad NetworkManager[1140]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.

```When looking for this error message on [Google]("http://www.google.com/search?client=ubuntu&channel=fs&q=GSM+modem+enable+failed%3A+%2832%29+Failed+to+find+a+usable+modem+character+set&ie=utf-8&oe=utf-8"), I found that this is work in progress:

[http://osdir.com/ml/networkmanager-list/2010-09/msg00054.html](http://osdir.com/ml/networkmanager-list/2010-09/msg00054.html)

I will try to provide as much debug info as possible to the developers, but this definitely means we're almost there, without the need of a lot of manual recompiling and other interventions that are beyond the capabilities of the average user...

Thanks to all the people who've been posting their experiences, to Matthew Garrett for gobi_loader and the folks working on NetworkManager/ModemManager!

Alex

PS: Don't bother to edit /lib/udev/rules.d/77-nm-probe-modem-capabilities.rules as described above if you're using Ubuntu 10.10, as the above is only valid for NetworkManager up to 0.7. Ubuntu 10.10 uses NetworkManager 0.8.1, and GSM (and other) modems are now managed using ModemManager.

---

### Post by alexlist on 2010-10-11
OK,

after inserting the SIM card the right way, it actually *works*.

**Folks, gobi2000 works with Ubuntu 10.10!**

---

### Post by codeice on 2010-10-14
Great news! I have the same setup i.e. HP Mini 5102 - Qualcomm Gobi2000 WWAN, mobile broadband and would really like to ditch the Win 7 system that it came with.:smile:

I am not a progammer, and do not relish attempting the earlier configuration instructions on your post.

I have 10.10 on a disk ready to go - are you saying that 10.10 will do it for me with little config work on my side?

Thanks

---

### Post by alexlist on 2010-10-17
> **codeice said:**
> 
I am not a progammer, and do not relish attempting the earlier configuration instructions on your post.

I have 10.10 on a disk ready to go - are you saying that 10.10 will do it for me with little config work on my side?


I am not a programmer either. The problem is that the card needs firmware, and that the firmware is only available within a Windows installer package.

So if you follow my instructions step-by-step, in particular regarding unpacking the GobiInstaller.msi, and then copy the firmware files found to /lib/firmware/gobi, all you have to do is install gobi-loader in 10.10 and you're set.

I'm seeing some minor issues still, like that it keeps asking me for the SIM PIN every time it connects, but that's a minor glitch compared to having a non-working card...

Alex

---

### Post by codeice on 2010-10-17
OK, will get a pot of coffee going and give it a run, will also post my result. Many thanks. Pete

---

### Post by Lemo85 on 2010-10-24
> **codeice said:**
> OK, will get a pot of coffee going and give it a run, will also post my result. Many thanks. Pete

How did you go with this on the HP 5102, did you get the Modem working?

I'm thinking of giving it a shot tomorrow.

---

### Post by codeice on 2010-10-26
No not yet. Have got the Win 7 driver etc, and hoping to get some quiet time at the weekend.

---

### Post by alexlist on 2010-12-07
Bad, but actually good news:

I accidentally killed my Ubuntu installation and reinstalled with 10.10 x86_64.

The steps above with gobi_loader *are* still required, but I just followed my own instructions and have mobile broadband working again...

---

### Post by js_ on 2011-08-11
Hello,

I have a HP Mini 5102 too, with the said WWAN adapter, and I want to get it working with Ubuntu (the netbook edition). Now, I'm new to Ubuntu and I don't understand much of the conversation in this thread; but I'm willing to make an effort to learn.

So here's my question: does there exist some good tutorial the reading of which should suffice to make the above conversation intelligible to me? Thanks in advance.

JS

---

