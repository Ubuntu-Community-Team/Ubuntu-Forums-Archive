---
title: "Problems with DVD-R"
date: 2014-11-12
forum: Hardware
---

### Post by Jarrett_ on 2014-11-12
I'm new to Ubuntu and having some problems with my DVD r drive. It is a new install of 14.04.  I have two DVD rs , neither seems to want to recognize blank DVD -r.  One is an internal Sony, and the other is an external HP.  

Ran sudo lshw

both drives appear present and operating "

        *-cdrom
             description: DVD-RAM writer
             physical id: 0.0.0
             bus info: scsi@5:0.0.0
             logical name: /dev/sr1
             capabilities: audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: status=ready

             description: DVD writer
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/sr0
             capabilities: audio cd-r cd-rw dvd dvd-r
             configuration: status=nodisc

Neither shows up under devices in files.  When I try to burn an image it says no disks available.  Both drive mount DVDs fine and recognize CD -r.  Its the same drive and same DVDs that I used to burn the Ubuntu image so I know the disks and the drives are compatible.  I've read through several DVD theads and checked permissions on the /dev/ folders and the media folder where it should be mounting the drive.  Any ideas?

/dev/sr1/ shows ready I just can't access it.

---

