---
title: "SCSI scanner char device permissions: crw-rw----+"
date: 2010-10-02
forum: Hardware
---

### Post by DrJohn999 on 2010-10-02
Maybe this is an uninformed question, but I'm troubleshooting a scsi scanner installation. The scanner lands at /dev/sg6 with the following permissions;
```
# ls -lisa /dev/sg6
4833 0 crw-rw----+ 1 root root 21, 6 2010-10-02 16:45 /dev/sg6
#

```
Question is: what's the '+' sign at the end of the permissions? I've never seen this before and am wondering what is its significance? Can't find any documentation.

The scanner problem is (as root):
```
# scanimage -L
device `coolscan3:scsi:/dev/sg6' is a Nikon LS-2000 film scanner
# scanimage -d coolscan3:scsi:/dev/sg6 -T
scanimage: open of device coolscan3:scsi:/dev/sg6 failed: Invalid argument

```
i.e. looks like a general failure to communicate.

---

### Post by Belfry on 2010-10-10
According to the ArchLinux [wiki]("http://wiki.archlinux.org/index.php/ACL#Output_of_ls_command"), "+" indicates an ACL (access control list) is in effect for a file.  Several files get created with this designation, like /dev/sr0 and /dev/dri/card0, even without the ACL program installed; I guess so one can readily restrict access to things like the optical drive or 3d graphics once it is installed.

I don't think this is the source of your problem (because it would probably throw a permission error), but the group ownership of devices with "+" belong to groups like cdrom, video, or audio. Maybe your scanner needs some other group ownership besides root.  Try setting it to your user account to test: ```
sudo chown root:$USER /dev/sg6
```

---

