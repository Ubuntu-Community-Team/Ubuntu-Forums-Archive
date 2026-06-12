---
title: "GUI Hard Drive Sector Test under 18.04 ???"
date: 2018-09-13
forum: Hardware
---

### Post by rebeltaz on 2018-09-13
Is there not a GUI linux equivalent to ms' scandisk? I guess e2fsck is the command line equivalent? I know how to use that, but I'd really like a GUI version.

---

### Post by deadflowr on 2018-09-14
Look in Disks.
In Disks highlight the drive in the left panel, then highlight the partition in the main window, then click on the double cog/sprocket thing underneath the main window and it'll list options including check file system, which is the equivalent to e2fsck.

Other options to scan disks sectors would be under the SMART settings, which are up top right in the hamburger icon.

---

### Post by rebeltaz on 2018-09-14
I did check Disks earlier. For some reason, the two drives connected via USB do not show SMART options although the two connected internally do. When I click the gear icon (I don't know when we all regressed back to hieroglyphics) there is no option on any drive/partition for "Check File System". I get:

* Format Partition
* Edit Partition
* Edit Filesystem [edits drive label] 
*[COLOR="#A9A9A9"] Change Passphrase [greyed out][/COLOR]
* Edit Mount Options
*[COLOR="#A9A9A9"] Edit Encryption Options [greyed out][/COLOR]
* Create Partition Image
* Restore Partition Image
* Benchmark Partition

---

