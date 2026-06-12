---
title: "Maxtor One Touch III Firewire external hard drive set up"
date: 2008-07-18
forum: Hardware
---

### Post by jukingeo on 2008-07-18
Hello all,

I am right now exploring what is working and not working with Ubuntu on my system.  One of the things that I have connected is a Maxtor One Touch III firewire external hard drive.

When turned on, I get an "unclean drive-cannot mount" error message and it suggests that I run "mount -t /dev/sdc1/media/New Volume -o Force" from the Terminal.

Not knowing what this would do, I didn't do anything.  This drive has critical data on it from what I saved from Windows.  I ABSOLUTELY don't want to do anything in this drive that will corrupt it.

At first I thought I may have a communication problem with the firewire port and I was told to run this command in Terminal:

geo@geo-desktop:~$ tail -f /var/log/messages

This is the result:

Jul 18 11:00:52 geo-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.interface_mtu
Jul 18 11:20:26 geo-desktop -- MARK --
Jul 18 11:40:26 geo-desktop -- MARK --
Jul 18 12:00:26 geo-desktop -- MARK --
Jul 18 12:20:26 geo-desktop -- MARK --
Jul 18 12:40:26 geo-desktop -- MARK --
Jul 18 13:00:26 geo-desktop -- MARK --
Jul 18 13:20:26 geo-desktop -- MARK --
Jul 18 13:40:26 geo-desktop -- MARK --
Jul 18 14:00:26 geo-desktop -- MARK --

The terminal stopped here and then I turned on the Maxtor firewire drive and this was the next result:

Jul 18 14:01:55 geo-desktop kernel: [10931.502572] scsi4 : SBP-2 IEEE-1394
Jul 18 14:01:56 geo-desktop kernel: [10932.502842] ieee1394: sbp2: Logged into SBP-2 device
Jul 18 14:01:56 geo-desktop kernel: [10932.503139] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
Jul 18 14:01:56 geo-desktop kernel: [10932.503507] scsi 4:0:0:0: Direct-Access     Maxtor   OneTouch III     035f PQ: 0 ANSI: 4
Jul 18 14:01:56 geo-desktop kernel: [10932.506596] sd 4:0:0:0: [sdc] 625142448 512-byte hardware sectors (320073 MB)
Jul 18 14:01:56 geo-desktop kernel: [10932.506934] sd 4:0:0:0: [sdc] Write Protect is off
Jul 18 14:01:56 geo-desktop kernel: [10932.507981] sd 4:0:0:0: [sdc] 625142448 512-byte hardware sectors (320073 MB)
Jul 18 14:01:56 geo-desktop kernel: [10932.508201] sd 4:0:0:0: [sdc] Write Protect is off
Jul 18 14:01:56 geo-desktop kernel: [10932.508511]  sdc: sdc1
Jul 18 14:01:56 geo-desktop kernel: [10932.530681] sd 4:0:0:0: [sdc] Attached SCSI disk
Jul 18 14:01:56 geo-desktop kernel: [10932.530734] sd 4:0:0:0: Attached scsi generic sg4 type 0


So from this output it does seem like Ubuntu is noticing something.  So the next step is that I would like to know if this drive will work in Ubuntu and if I can read/write to it.

There are no other devices hooked up to the firewire port (but I do have intentions on purchasing a firewire audio device in the future).

My system is a Dell Dimension 4600 with a 2.8ghz processor 1.5gig ram, one 80gig IDE 7200 rpm drive and one 500gig SATA 7200rpm drive.

My system is currently on a dual boot Windows XP (currently obliterated from a mistake in drive formating last night (which is why I need to access the Maxtor drive in Ubuntu) and Ubuntu Hardy (8.04).

As I said above, there was a mistake I made in partition selection in gparted and ended up ruining my Windows partition.  However, I am still able to boot into Ubuntu (which is on a different drive).  The Maxtor One Touch III is only used for storage of important data only and there are no executables and no operating systems on that drive.

Any assistance would be appreciated.

Thank You,

Geo

---

### Post by phidia on 2008-07-18
> Jul 18 14:01:56 geo-desktop kernel: [10932.508511] sdc: sdc1


That's your drive as the linux system reports it. What filesystem do you have on that drive?
Anyway you can have a go at mounting it by creating a mountpoint (in a terminal) "sudo mkdir /mnt/myextdrive" 
(select any meaningful name you want there after "mnt/")
To mount the drive using terminal "sudo mount /dev/sdc1 /mnt/myextdrive"
If that doesn't work it will give some error messages anyway, and you can post those here.

---

### Post by jukingeo on 2008-07-18
> **phidia said:**
> That's your drive as the linux system reports it. What filesystem do you have on that drive?
Anyway you can have a go at mounting it by creating a mountpoint (in a terminal) "sudo mkdir /mnt/myextdrive" 
(select any meaningful name you want there after "mnt/")
To mount the drive using terminal "sudo mount /dev/sdc1 /mnt/myextdrive"
If that doesn't work it will give some error messages anyway, and you can post those here.


I did as you said, but for some reason it didn't appear to work.

Here is my terminal information.  I ran the "tail" command again afterwards and strangely the information seems to be different.

geo@geo-desktop:~$ sudo mkdir /mnt/myextdrive
[sudo] password for geo: 
geo@geo-desktop:~$ sudo mount /dev/sdc1 /mnt/myextdrive
mount: special device /dev/sdc1 does not exist
geo@geo-desktop:~$ tail -f /var/log/messages
Jul 18 17:59:29 geo-desktop kernel: [   72.354282] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
Jul 18 17:59:29 geo-desktop kernel: [   72.354302] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
Jul 18 17:59:29 geo-desktop kernel: [   72.354335] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
Jul 18 17:59:29 geo-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Jul 18 17:59:31 geo-desktop kernel: [   74.660897] NET: Registered protocol family 17
Jul 18 17:59:32 geo-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.host_name
Jul 18 17:59:32 geo-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.domain_name
Jul 18 17:59:32 geo-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Jul 18 17:59:32 geo-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Jul 18 17:59:32 geo-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.interface_mtu

I don't see anything there that shows the drive.

You know something though...I heard sometimes you do have to wait a while before firewire devices kick in.  But I never had that problem with windows.

Any idea what to do now?

Thanx,

Geo

---

### Post by phidia on 2008-07-18
Running dmesg with tail as in: "dmesg | tail" just provides you with the last lines of dmesg-instead of the whole output.

Can you expound on this: > I did as you said, but for some reason it didn't appear to work.

That isn't specific enough to know what happened. When you typed/entered sudo mount /dev/sdc1 /mnt/whatever_mountpoint_you_created 
you must have gotten some output.

---

### Post by jukingeo on 2008-07-19
> **phidia said:**
> Running dmesg with tail as in: "dmesg | tail" just provides you with the last lines of dmesg-instead of the whole output.

Can you expound on this: 
That isn't specific enough to know what happened. When you typed/entered sudo mount /dev/sdc1 /mnt/whatever_mountpoint_you_created 
you must have gotten some output.

Ok, that did something:

Here is what I got this time:

geo@geo-desktop:~$ dmesg | tail -f /var/log/messages
Jul 18 23:50:21 geo-desktop kernel: [   73.781078] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
Jul 18 23:50:21 geo-desktop kernel: [   73.781113] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
Jul 18 23:50:23 geo-desktop kernel: [   76.029571] NET: Registered protocol family 17
Jul 18 23:50:28 geo-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.host_name
Jul 18 23:50:28 geo-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.domain_name
Jul 18 23:50:28 geo-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Jul 18 23:50:28 geo-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Jul 18 23:50:28 geo-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.interface_mtu
Jul 19 00:09:59 geo-desktop -- MARK --
Jul 19 00:29:59 geo-desktop -- MARK --
Jul 19 00:49:56 geo-desktop kernel: [ 3641.707069] scsi4 : SBP-2 IEEE-1394
Jul 19 00:49:57 geo-desktop kernel: [ 3642.706663] ieee1394: sbp2: Logged into SBP-2 device
Jul 19 00:49:57 geo-desktop kernel: [ 3642.706976] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
Jul 19 00:49:57 geo-desktop kernel: [ 3642.707463] scsi 4:0:0:0: Direct-Access     Maxtor   OneTouch III     035f PQ: 0 ANSI: 4
Jul 19 00:49:57 geo-desktop kernel: [ 3642.710302] sd 4:0:0:0: [sdc] 625142448 512-byte hardware sectors (320073 MB)
Jul 19 00:49:57 geo-desktop kernel: [ 3642.710638] sd 4:0:0:0: [sdc] Write Protect is off
Jul 19 00:49:57 geo-desktop kernel: [ 3642.711697] sd 4:0:0:0: [sdc] 625142448 512-byte hardware sectors (320073 MB)
Jul 19 00:49:57 geo-desktop kernel: [ 3642.712091] sd 4:0:0:0: [sdc] Write Protect is off
Jul 19 00:49:57 geo-desktop kernel: [ 3642.712456]  sdc: sdc1
Jul 19 00:49:57 geo-desktop kernel: [ 3642.733079] sd 4:0:0:0: [sdc] Attached SCSI disk
Jul 19 00:49:57 geo-desktop kernel: [ 3642.733136] sd 4:0:0:0: Attached scsi generic sg4 type 0

geo@geo-desktop:~$ sudo mount /dev/sdc1 /mnt/myextdrive
[sudo] password for geo: 
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sdc1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sdc1 /mnt/myextdrive -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sdc1 /mnt/myextdrive ntfs-3g force 0 0
geo@geo-desktop:~$ 


I got a similar error message pop-up that in so many words told me to do the same thing.  At this point I can only do choice two, but the words "your own responsibility" are throwing me and I certainly don't want to invoke a command that may corrupt the data on this drive.

Geo

---

### Post by jukingeo on 2008-07-20
Hello Phidia,

Please come back when you have the chance.  I would like to continue with our progress.

Thanx,

Geo

---

