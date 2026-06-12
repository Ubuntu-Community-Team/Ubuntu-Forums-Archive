---
title: "Can't Mount Hard Disk Drive To Ubuntu Laptop"
date: 2018-07-25
forum: Hardware
---

### Post by John_Patrick_Mason on 2018-07-25
A few weeks ago, my Lubuntu desktop failed to boot properly, so I removed the internal hard disk drive, bought a USB 3.0 2.5'' SATA hard drive adapter, and plugged it into my Ubuntu laptop to see if I could retrieve any data from the hard drive. Unfortunately, the drive wasn't mounted automatically, so I removed the cable, typed:

```
sudo tail -f /var/log/syslog
```

reconnected the cable, and waited for the results. The problem now is that the results don't show any listed partitions on the drive. The only thing it shows is the name of the drive "sdb". Here is a snippet of the results:

```
Attached scsi generic sg2 type 0
[sdb] Attached SCSI removable disk
```

I don't know how sensitive the results are, so I didn't post everything. In the unposted results, it shows the manufacturer, model, and serial number of the hard drive, so it is detecting something.

To be clear, I don't know what caused my desktop to fail. It could a motherboard failure or it could by a hard drive failure. The computer is so old that it's not even worth buying the necessary parts to swap them out.

I tried typing:

```
sudo mkdir /mnt/Lubuntu
sudo mount /dev/sdb /mnt/Lubuntu
```

to no avail.

Also, I don't know if it matters, but when I installed Lubuntu on the hard drive, I created three separate partitions: the swap partition, the root (/) partition, and the /home partition. I also opted to encrypt the **home** folder with a password.

---

### Post by oldfred on 2018-07-25
You do not mount drives, but mount partitions.
And abnormal shutdown often causes corruption, but drives do fail. That is why we have backups.
And if data encrypted it is more difficult to impossible to recover, or back up is your only recourse.

First see if testdisk shows partitions. If you have pass phrase you will need that to mount /home. And you may have to add drivers so live installer sees encrypted partition.

       [http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

If you can recover partitions:
       
 Includes chroot:
[https://help.ubuntu.com/community/EncryptedPrivateDirectory/#Live_CD_method_of_opening_a_encrypted_home_directory](https://help.ubuntu.com/community/EncryptedPrivateDirectory/#Live_CD_method_of_opening_a_encrypted_home_directory)

---

### Post by John_Patrick_Mason on 2018-07-26
For the record, I do perform backups regularly. But even if you perform backups regularly, there is still that time between backups that you can be vulnerable. I really hope it's just a hard drive failure, since I'd like to replace the hard drive with the other spare hard drive I have lying around, and reboot the system.

Does the testdisk utility work with ext3/ext4 filesystems? The examples listed are for NTFS filesystems. Also, where would I go about finding those drivers?

---

### Post by oldfred on 2018-07-26
Any drivers you may need are in Ubuntu repository.
Note that 18.04 does not do /home encryption anymore.

Testdisk works for all partitions.
I think only #12 is for NTFS. All the other details apply to all. 
You do have to initially select correctly on whether partitioning is MBR(msdos) or gpt(GUID).

---

### Post by John_Patrick_Mason on 2018-07-26
OK, I'm having a problem. I installed TestDisk, connected the external hard drive to the laptop, ran:

```
sudo testdisk
```

into the terminal, created a log file, but then when it comes time to selecting the appropriate hard drive, the external hard drive is nowhere to be found. Here is a list of the drives that are detected, though:

```

Disk /dev/sda
Disk /dev/mapper/cryptswap1
Disk /dev/dm-0

```
  
Is it possible the 2.5'' SATA hard drive adapter that I bought, that came with one USB type-A connector, somehow isn't supplying enough power to the external hard drive for my laptop to see it?

---

### Post by oldfred on 2018-07-26
Low power could be an issue.

Does this before & then after plugging in external drive show it?
lsusb

---

### Post by John_Patrick_Mason on 2018-07-27
[QUOTE=oldfred]Does this before & then after plugging in external drive show it?
lsusb[/QUOTE]

Yes.

This line wasn't present when the drive wasn't connected:

```
ASMedia Technology Inc. ASM1051E SATA 6Gb/s bridge, ASM1053E SATA 6Gb/s bridge, ASM1153 SATA 3Gb/s bridge
```

I also just noticed that there are two LED lights on the adapter. The one facing the SATA port for power is flashing red, while the other one, facing the SATA data port, is off.

EDIT: I just read the instructions that came with the adapter. It says, "The hard drive adapter requires no external power supply, as it is capable of receiving enough power from the USB Bus to which it is connected". A hard drive failure, perhaps?

---

### Post by oldfred on 2018-07-27
The adapter instructions may be for SSD or newer HDD that need less power.
If older drive it may need more power.
I would plug drive into system SATA port and run testdisk from live installer on drive.

---

### Post by John_Patrick_Mason on 2018-07-27
If I understand correctly, you want me to open up my laptop, connect the external hard drive to the system, and run TestDisk while it's on?

---

### Post by oldfred on 2018-07-27
If a laptop, then it is difficult to connect it directly to system.

The SSD adapter I have is just a cable with some smarts. But it shows connected even when SSD is unplugged as cable still has lights on. Just no activity.

---

### Post by John_Patrick_Mason on 2018-07-27
[QUOTE=oldfred]The SSD adapter I have is just a cable with some smarts. But it shows  connected even when SSD is unplugged as cable still has lights on. Just  no activity.[/QUOTE]

You're right. One of the LED lights on the cable is still flashing red, even when the hard drive isn't connected to the cable. But I'm not sure if I understand, what is it that you would like me to do? What do you mean when you said I should plug the drive into the system SATA port and run testdisk from the live installer? What is the system SATA port? Where is it located?

---

### Post by oldfred on 2018-07-27
Laptops usually use SATA, unless very old. And users can replace drives by opening the bottom of laptop. But I was suggesting that more if you had a desktop where you have multiple SATA ports and a bit easier to access.

Should be same connection as on your adapter. 
Scroll down about 1/3 of the link.
[https://en.wikipedia.org/wiki/Serial_ATA](https://en.wikipedia.org/wiki/Serial_ATA)

Other alternatives are: 
Do you have a friend with a desktop? 
Or buy an adapter that has separate power & signal connectors where you can plug power into wall.

---

### Post by John_Patrick_Mason on 2018-07-27
[QUOTE=oldfred]Laptops usually use SATA, unless very old. And users can replace drives  by opening the bottom of laptop. But I was suggesting that more if you  had a desktop where you have multiple SATA ports and a bit easier to  access.

Should be same connection as on your adapter. 
Scroll down about 1/3 of the link.
[https://en.wikipedia.org/wiki/Serial_ATA](https://en.wikipedia.org/wiki/Serial_ATA)[/QUOTE]

Oh, I know what SATA ports are, I just didn't know what you meant when you said I could just plug the hard drive into the "system" SATA port, given that the only computer that I have now that's functional, is the laptop. As far as plugging the external hard drive into one of my friends' desktop, right now that's not an option. I guess, I think, that means I'm going to have to buy another SATA adapter. Does [this]("https://www.amazon.com/AGPtek-Drive-Adapter-Converter-External/dp/B00BIE996S/ref=sr_1_3?ie=UTF8&qid=1532742218&sr=8-3&keywords=SATA+USB+adapter+with+power") adapter look like the right one?

---

### Post by oldfred on 2018-07-27
That looks ok, but it is USB2, I would suggest USB3.
We have seen others with issues with USB adapters. Some do not work with larger drives, some do not support gpt, some just have issues like you are having. 
And it seems to be a shot in the dark. Mine works, but it is USB3 only, no separate power supply. But I am using it with a SSD, so less power required.

I found on my old system using USB3 flash drive on USB2 ports was still a bit faster. And USB3 being newer, may then be newer design that works better. Laptops also have less USB power, so my desktop and USB3 may work where a laptop may not.

---

### Post by John_Patrick_Mason on 2018-07-28
What about [this]("https://www.amazon.com/dp/B075WY92BW/ref=twister_B07F2B2MG5?_encoding=UTF8&th=1") one? I should mention that the laptop I'm using is directly connected to the power supply, due to a dead battery. Could that be the reason why the USB SATA adapter that I have now isn't working?

---

### Post by oldfred on 2018-07-29
If you want more than one drive, that one does look good spec wise. Again it seems to be a shot in the dark. I would keep receipt or make sure you can return, if it does not.

But if laptop battery does not work, that also could be an issue.
Does laptop have USB3 ports? As that gives more power out.

[https://www.google.com/search?source=hp&ei=_eddW6nbHqvVjwSUyqCoDA&q=usb+port+power+output&oq=usb+port+power&gs_l=psy-ab.1.1.0l10.1141.4851.0.8389.15.14.0.0.0.0.156.1103.13j1.14.0..2..0...1.1.64.psy-ab..1.14.1097.0..35i39k1j0i131k1j0i67k1j0i20i264k1j0i131i67k1j0i131i20i264k1.0.cRz5OiV3ZU4](https://www.google.com/search?source=hp&ei=_eddW6nbHqvVjwSUyqCoDA&q=usb+port+power+output&oq=usb+port+power&gs_l=psy-ab.1.1.0l10.1141.4851.0.8389.15.14.0.0.0.0.156.1103.13j1.14.0..2..0...1.1.64.psy-ab..1.14.1097.0..35i39k1j0i131k1j0i67k1j0i20i264k1j0i131i67k1j0i131i20i264k1.0.cRz5OiV3ZU4)
      >  In the USB 1.0 and 2.0 specs, a standard downstream port is capable of delivering up to 500mA (0.5A); with USB 3.0, it moves up to 900mA (0.9A). The charging downstream and dedicated charging ports provide up to 1,500mA (1.5A) 



---

### Post by John_Patrick_Mason on 2018-07-29
[QUOTE=oldfred]Does laptop have USB3 ports?[/QUOTE]

Yes.

I'm not going to sweat it. If the new SATA USB adapter doesn't work, I'll just drill a couple of holes into the hard drive, just to make sure. I've already made backups anyway; at worst, I'll just lose a few weeks worth of data. The adapter is scheduled to be delivered on Wednesday, I'll let you know, then, if I'm successful.

---

### Post by John_Patrick_Mason on 2018-08-02
Looks like the new adapter isn't working. I can hear the hard drive spinning, unlike with the other adapter, but the hard drive isn't being detected, either in /media, or when I do:

```
tail -f /var/log/syslog
```

Could it be a hard drive failure?

---

### Post by oldfred on 2018-08-02
At this point it may be hard drive failure.
Only other way is to connect to a SATA port and see what Smart Status is, if drive is even seen. 
I do not think you can get smart status on USB drive.

---

### Post by John_Patrick_Mason on 2018-08-03
I'm building a new computer, but I'm waiting for prices to come down. I think I will save the hard drive, until then, to see if it works. Thanks for all the help. I'll leave this thread open until I get my computer up and running.

---

### Post by oldfred on 2018-08-03
the system I built a couple of years ago is now more expensive. Partly due to older parts probably not available, but some just up a lot.
         oldfred's new SFF system with skylake i5-6500 and 16.04
[http://ubuntuforums.org/showthread.php?t=2315007&p=13449024#post13449024](http://ubuntuforums.org/showthread.php?t=2315007&p=13449024#post13449024)
[http://pcpartpicker.com/p/8QKkCJ](http://pcpartpicker.com/p/8QKkCJ)

---

