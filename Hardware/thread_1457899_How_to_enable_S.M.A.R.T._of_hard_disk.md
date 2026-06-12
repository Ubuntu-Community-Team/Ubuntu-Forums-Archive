---
title: "How to enable S.M.A.R.T. of hard disk?"
date: 2010-04-19
forum: Hardware
---

### Post by chaopoch on 2010-04-19
I just bought a WD Caviar Green 1.5 TB SATA (WD15EARS) hard disk to be the second disk for data storage, but when I try to detect its temperature, I got the following output:

$ sudo hddtemp /dev/sdb
/dev/sdb: WDC WD15EARS-00Z5B1: [COLOR="Red"]S.M.A.R.T. not available[/COLOR]

How can I enable the S.M.A.R.T. of hard disk? thanks.


PS: The hard disk is in an USB external case.

---

### Post by khelben1979 on 2010-04-19
Try with ksensors or xsensors. They are using [lm_sensors]("http://en.wikipedia.org/wiki/Lm_sensors") to get the the temperature.

You can search for them in [Synaptic Package Manager]("http://en.wikipedia.org/wiki/Synaptic_package_manager") or use the **apt-get install** command to install them.

---

### Post by cascade9 on 2010-04-19
SMART can normally be turned on (or off) in the BIOS settings.

---

### Post by chaopoch on 2010-04-19
Thanks for reply, and sorry for that I forgot to mention the hard disk is an USB external hard disk.

---

### Post by chaopoch on 2010-04-20
I try to run command [COLOR="Red"]sudo smartctl --smart=on /dev/sdb[/COLOR] to enable SMART of the USB external hard disk, but it says

"[COLOR="SeaGreen"]unable to fetch IEC (SMART) mode page [unsupported field in scsi command]
A mandatory SMART command failed: exiting.[/COLOR]"

any comment? thanks.

---

### Post by Morbius1 on 2010-04-20
SMART has been disabled because it does dumb things to SSD's:

[https://edge.launchpad.net/ubuntu/+s...s/007-2ubuntu6]("https://edge.launchpad.net/ubuntu/+source/devicekit-disks/007-2ubuntu6")
 > devicekit-disks (007-2ubuntu6) karmic-proposed; urgency=low

  * Add 11-disable-smart-probing.patch: Disable ATA SMART probing on ATA
    disks. It causes hardware damage to a lot of SSD disks. This is a
    workaround, until a real fix in libatasmart is found. (LP: [#445852]("https://edge.launchpad.net/bugs/445852"))
 -- Martin Pitt <email address hidden>   Thu, 25 Mar 2010 18:47:35 +0100                      

---

### Post by chaopoch on 2010-04-20
> **Morbius1 said:**
> SMART has been disabled because it does dumb things to SSD's:

[https://edge.launchpad.net/ubuntu/+s...s/007-2ubuntu6]("https://edge.launchpad.net/ubuntu/+source/devicekit-disks/007-2ubuntu6")

WD Caviar Green 1.5 TB SATA (WD15EARS) hard disk is NOT a SSD.

---

### Post by Morbius1 on 2010-04-20
>                                                  devicekit-disks (007-2ubuntu6) karmic-proposed; urgency=low

  * Add 11-disable-smart-probing.patch: **[COLOR=Blue]Disable ATA SMART probing on ATA[/COLOR]** 
    **[COLOR=Blue]disks[/COLOR]**. It causes hardware damage to a lot of SSD disks. This is a
    workaround, until a real fix in **[COLOR=Blue]libatasmart[/COLOR]** is found. (LP: [#445852]("https://edge.launchpad.net/bugs/445852"))
 -- Martin Pitt <email address hidden>   Thu, 25 Mar 2010 18:47:35 +010That's why it was disabled.

---

### Post by proxess on 2010-04-20
Whatever the hard-disk, if connected through USB, S.M.A.R.T doesn't work. I have a Seagate Barracuda 7200.12 1TB and it's the same situation.

---

### Post by fusky on 2010-11-27
ive recently been trying to check my hard disks as well,all hard disk none are ssd.i know they all have smart since they were advertised as having it.but i noticed all the ones plugged in with usb say smart not available even though it should be ,is there  a way i can make it see it or is there another program that can smart through usb.i was trying to use the ubuntu disk utility.

---

### Post by Morbius1 on 2010-11-28
As far as I know SMART is still disabled because it does damage to SSD disks.

---

