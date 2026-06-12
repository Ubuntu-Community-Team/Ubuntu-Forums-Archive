---
title: "Cannot detect my Seagate 1TB drive"
date: 2020-11-12
forum: Hardware
---

### Post by sofasurfer on 2020-11-12
My pc works. I bought a Seagate 1TB drive. The guy tested it ( watched him) and said it was 100% good. I brought it home and connected it in place of my old drive. I put a live cd in to install Ubuntu on the drive. Pc said that it can not detect the drive.
Help! any ideas what could be wrong? Does a 1TB drive require differant BIOS settings?

---

### Post by QIII on 2020-11-12
You should not need any special settings.

Did you check in your BIOS/EFI settings to see if the device is detected?

---

### Post by Yellow Pasque on 2020-11-12
Can you tell us what motherboard you have and what port it is connected to?

---

### Post by sofasurfer on 2020-11-12
I will answer you guys tomorrow but before I do I will need to know HOW to tell what port it is connected to.

---

### Post by Yellow Pasque on 2020-11-12
> **sofasurfer said:**
>  I will need to know HOW to tell what port it is connected to.

Open your case and look at it. Consult your mobo manual if necessary to determine the numbering of SATA ports (assuming this is a SATA drive). Or maybe it will tell you in the BIOS/EFI if it's detected there.

---

### Post by sofasurfer on 2020-11-12
Dell Inspiron 660.

Heres my manual [https://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=&cad=rja&uact=8&ved=2ahUKEwi6rbad9_3sAhXaQc0KHeLrD6UQFjAAegQIBhAC&url=https%3A%2F%2Fdownloads.dell.com%2Fmanuals%2Fall-products%2Fesuprt_desktop%2Fesuprt_inspiron_desktop%2Finspiron-660_owner%2527s%2520manual_en-us.pdf&usg=AOvVaw1kv-a_QJiHCc0qCtuA-JXF](https://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=&cad=rja&uact=8&ved=2ahUKEwi6rbad9_3sAhXaQc0KHeLrD6UQFjAAegQIBhAC&url=https%3A%2F%2Fdownloads.dell.com%2Fmanuals%2Fall-products%2Fesuprt_desktop%2Fesuprt_inspiron_desktop%2Finspiron-660_owner%2527s%2520manual_en-us.pdf&usg=AOvVaw1kv-a_QJiHCc0qCtuA-JXF)

Operating system drive (WD) is on sata 3.  Seagate 1TB drive is on sata 2.

With both drives connected pc starts fine 1TB drive is shown in "hardinfo".
Nothing in file system under "mnt".
Gparted shows WD drive as sbd but does not show anything for 1TB drive.
BIOS as startup shows boot mode set to legacy mode (whatever that is) and secure boot is "off".
1TB drive is listed.

On BIOS setup sata mode is set to AHCI. 
BIOS sata info shows 3 as disabled. Choice available for selection are usb floppy, internal WD (already used), usb storage, internal phillips (already used for DVD) and onboard NIC.

Starting pc with only 1tb drive connected and no operating system system show "hard drive failure. Strike F1 to continue". Strikeing F1 says reboot and select proper device.

Oh, oh!

---

### Post by DuckHook on 2020-11-12
Your BIOS is not showing your new drive. Therefore, there's no way for any OS to see it.

[list=1]
[*]Try enabling SATA 3 in BIOS. Your system could be mislabelling the drive, or it could be mistranslating (this happens when MOBO starts at 0 {zero} while BIOS reporting scheme starts at 1)
[*]Some HDDs have a jumper that sets them to "locked". Make sure all of yours are clear.
[*]It's still possible that the drive is defective. How did the vendor test it? What was the testing procedure?
[*]Try switching the SATA cable. Defective cables can sometimes be the problem.
[*]Try plugging the 1TB into the WD SATA slot. Sometimes, a bad connector is the problem.
[/list]
Chasing down HW problems is always a process of elimination. If you can think of other physical failure points, try to eliminate them too.

---

### Post by sofasurfer on 2020-11-12
I will try your suggestions. 
When the drive was tested he connected it to a pc with some kind of testing software install. this software supposedly tests the drive and checks speed and other stuff and determines life left in the drive.

---

### Post by QIII on 2020-11-12
There was once (years ago) a firmware issue with some Seagate drives that left the drive in a "busy" state - which required cutting and rigging a USB cable with a particular pin out, connecting those pins to the drive in a particular manner and then sending serial commands to the drive to reset it.  I had to do that once, and move all the data to a new drive.  I then used the old drive for target practice before hunting season that year.  The 7mm Remington Magnum round makes pretty little holes in hard drives on one side and big jagged holes on the back side.

I don't know how old the drive is, but you should be able to find the firmware version on the drive's label.  

Post that back here with the model number and I will see if I can find the info on whether the drive might be subject to that problem.

Check [this]("https://hackaday.com/2012/07/30/recovering-from-a-seagate-hdd-firmware-bug/") out.

---

### Post by mastablasta on 2020-11-13
so far i had two brand new and bad SATA cables (and i haven't connected that many disks in total). i suggest replacing that first as they are cheap to replace.

---

### Post by sofasurfer on 2020-11-13
I will get back to the cable issues tomorrow.
In the meantime, did you guys notice in my post #6 that the last line says I had a drive failure? Are you guys with me in hopeing that I may not be looking at a paperweight?

As for version number it is JC4A. And the drive is from 2015.

---

### Post by QIII on 2020-11-13
"Drive failure" in that message may mean any number of things.  A simple one would be if you only have one drive and it is unplugged (either power or data).

Your drive is too new and the firmware version is not the suspect one, so that is not the issue.

---

### Post by sofasurfer on 2020-11-13
I removed the good hard drive with the operating system and the good cable and installed the questionable 1TB drive. I got a black screen. I then put a Gparted DVD in the DVD drive. I got an error of "hard drive failure".

The small, 4 pin plug socket on the drive (which I think has to do with jumpers) has nothing connected to the pins.

---

### Post by QIII on 2020-11-13
Are you talking about the SATA power cable?

---

### Post by MartyBuntu on 2020-11-13
> **sofasurfer said:**
> I removed the good hard drive with the operating system and the good cable and installed the questionable 1TB drive. I got a black screen. I then put a Gparted DVD in the DVD drive. I got an error of "hard drive failure".

The small, 4 pin plug socket on the drive (which I think has to do with jumpers) has nothing connected to the pins.

Forget about jumpers on the SATA drive.

The drive is pooched. Run more diagnostics on it if you'd like....only you know the value of your own time.

---

### Post by sofasurfer on 2020-11-13
Theres like a 15 pin connector that takes a black plug and a 7 pin connector that takes the plug that plugs into the sata connectors on the MB. The plugs for both of these connections WERE attached to my good hard drive. I removed that drive and attached those plugs to the questionable drive.

---

### Post by rsteinmetz70112 on 2020-11-14
Did you buy a used drive? If you bought a new drive I can't see why someone would test it.

---

### Post by sofasurfer on 2020-11-14
Yes it was used. Whoops!

---

### Post by MartyBuntu on 2020-11-14
Get your money back. It's dead.

---

