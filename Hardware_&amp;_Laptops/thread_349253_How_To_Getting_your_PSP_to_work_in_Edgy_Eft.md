---
title: "How To: Getting your PSP to work in Edgy Eft"
date: 2007-01-29
forum: Hardware &amp; Laptops
---

### Post by Dritzen on 2007-01-29
I set up my PSP this evening and it was pretty easy, so I thought I'd lay out the steps for everyone else.

I hear that some versions of the PSP firmware will automatically be detected in Ubuntu so if you plug in your psp and it works for you, then great.  If it doesn't work, read this guide.

For the record, I'm using the latest homebrew firmware, 3.03 OE-C Custom firmware.  Although I do not believe that your firmware version will really make a difference.  It's all the same filesystem in the long run.

Because you can flash any firmware version right now to a custom homebrew one, I imagine a lot of people will use this guide.

1) Plug in your PSP using USB

2) Turn on the PSP and put it into USB mode

3) Ubuntu will detect the PSP but probably won't automatically mount it.  If it doesn't, then keep following these steps.

4) Type dmesg in a console, the results will look like this:

```

[17372351.768000] usb 5-5: new high speed USB device using ehci_hcd and address 8
[17372351.900000] usb 5-5: configuration #1 chosen from 1 choice
[17372351.900000] scsi4 : SCSI emulation for USB Mass Storage devices
[17372351.900000] usb-storage: device found at 8
[17372351.900000] usb-storage: waiting for device to settle before scanning
[17372356.900000] usb-storage: device scan complete
[17372356.900000]   Vendor: Sony      Model: PSP               Rev: 1.00
[17372356.900000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17372356.904000] SCSI device sdb: 8005632 512-byte hdwr sectors (4099 MB)
[17372356.904000] sdb: Write Protect is off
[17372356.904000] sdb: Mode Sense: 00 6a 20 00
[17372356.904000] sdb: assuming drive cache: write through
[17372356.908000] SCSI device sdb: 8005632 512-byte hdwr sectors (4099 MB)
[17372356.908000] sdb: Write Protect is off
[17372356.908000] sdb: Mode Sense: 00 6a 20 00
[17372356.908000] sdb: assuming drive cache: write through
[17372356.908000]  sdb: sdb1
[17372356.912000] sd 4:0:0:0: Attached scsi removable disk sdb
[17372356.912000] sd 4:0:0:0: Attached scsi generic sg2 type 0

```

5) The line near the end shows the device name

In my example it is:
[17372356.908000]  sdb: sdb1

6) You will need to create an area to mount the psp, I suggest /media/psp .  Type this in a terminal:

```

sudo mkdir /media/psp

```

7) To mount the PSP, type this and replace /dev/sdb1 with your device from step 5:

```

sudo mount -t vfat -o shortname=win95,check=s /dev/sdb1 /media/psp

```

Congratulations, your PSP is mounted!  Unfortunately, only root can mount file systems, so if you want to mount the PSP as your regular user, continue to these optional steps.

Optional Steps:
8: We'll edit the fstab file

```

sudo nano /etc/fstab

```

9: Add this line to the bottom of the file, on its own line.  Of course, replace /dev/sdb1 with your PSP's device name.

```

/dev/sdb1  /media/psp  vfat  noauto,noatime,users,shortname=win95,check=s  0 0

```

Now you can mount your PSP without having to use sudo!  Just mount it as your regular user, no fancy mount command required:

```

mount /media/psp

```

Don't forget, after writing data to your PSP, type this line or else the data won't properly write to the PSP.  Wait for this to finish!  It took about 2 minutes to finish after I wrote 1 gig to my PSP.

```

umount /media/psp

```

That's all there is to it.

Additional links:
[QPSPManager]("http://sourceforge.net/projects/qpspmanager/")
[PSPVC - PSP Video Converter]("http://sourceforge.net/projects/pspvc/")

Places where I got my information:
[Linux + PSP Thread]("http://ubuntuforums.org/showthread.php?t=273578&highlight=psp")
[The Gentoo Wiki PSP Page]("http://gentoo-wiki.com/HOWTO_PSP")

A big thanks to the people who put out documentation on getting the PSP working in Linux and for taking the time to get it to work.

---

### Post by Fittersman on 2007-01-30
sweet man, great help, it works like a charm now and it took me about a minute to fix... lol

all i needed out of here though was the optional steps, my psp was automatically mounted and stuff but it was under the control of root so when i added the line in the fstab and it made it accessible to other users now it works for me :)

thanks :D

edit: ok a couple of problems here, when i try and copy some eboot.pbp off of the psp it locks the whole thing down and i cant do anything again... why is that?

also, is there any way to make the psp not automount?

---

### Post by zerosystem on 2007-01-31
> **Dritzen said:**
> Because you can flash any firmware version right now to a custom homebrew one, I imagine a lot of people will use this guide.

Mind telling us how? Specifically, I'd like to flash a vanilla 3.03 firmware with the 3.03 OE-C

---

### Post by Fittersman on 2007-01-31
i think he means downgrading to a lower version (v1.5) so that you can use homebrew on your psp, but he might mean what you think :D thats just what i got out of it...

plus if you search around, there are so many psp homebrew sites out there, i personally use qj.net or planetpsp.org (i think its .net and .org, but im not sure)

---

### Post by Dritzen on 2007-02-02
I'm not sure about getting it to not automount.  Usually the noauto line in /etc/fstab will do that but it sounds like Ubuntu is automounting it from somewhere else.

As far as downgrading the PSP, yes, that's what I was talking about.  All versions except 3.10 can be downgraded now but you will need an original copy of Grand Theft Auto: Liberty City Stories.  To find out if you have an original version of it, it will have the 2.0 updater on the UMD.

[Good info on the downgrader]("http://pspupdates.qj.net/Are-you-ready-for-homebrew-3-03-HEN-and-Downgrader-released-/pg/49/aid/80842")

Essentially you use a trick to downgrade the psp to version 1.50, then you can follow the steps to upgrade to the custom 3.03 OEC firmware from there.

The real key is having a copy of Grand Theft Auto: Liberty City Stories with the 2.0 firmware.  Now would be a good time to check out used copies at your local gamestore if you want to downgrade.

---

### Post by Fittersman on 2007-02-02
so what do you think about the problem that when i try and delete that file it returns to a read only disk (i think, or maybe it just acts like it, but it wont let me do anything again)?

---

### Post by Dritzen on 2007-02-03
Have you tried it as root?  Perhaps sudo rm filename will work for you.

I know that at one point, I wasn't able to remove files from my psp as a regular user.  After I wrote the guide, it was working fine but beforehand, I had to do it using sudo.

---

### Post by Fittersman on 2007-02-04
well it seems to work alright now, i formatted the memory stick before i upgraded to OE-C and now everthing works.

do you have 3.03OE-C? If not you should seriously think about getting it, it is so awsome, i think either booster or dark alex made it and its like v3.03 but it has all the benefits of a v1.5 and you can always downgrade back to v1.5 if you dont like it, its so awsome, it can do anything! :D

---

### Post by Dritzen on 2007-02-05
[New PSP 3.10 OE-A]("http://http://pspupdates.qj.net/3-10-OE-A-custom-firmware-out-and-about/pg/49/aid/81676")

These guys move fast.  I just upgraded to 3.03OE-C the other day and now 3.10 OE-A has been released.  I haven't updated to this myself yet so I can't say whether it has any bugs or not but it's out there.

---

### Post by Fittersman on 2007-02-05
yeah, i seen that, but i think im guna wait a bit cuz the OE-C is working fine for what i need, those guys are good though! :D

---

