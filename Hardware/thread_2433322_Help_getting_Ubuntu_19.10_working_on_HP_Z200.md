---
title: "Help getting Ubuntu 19.10 working on HP Z200"
date: 2019-12-17
forum: Hardware
---

### Post by ian5142 on 2019-12-17
I have a HP Z200 that I would like to run Ubuntu on. I have a SSD running Ubuntu 19.10. It floats from computer to computer at the moment. I have run it from both of my laptops and another desktop at different times. The HP Z200 refuses to boot from it. No GRUB, nothing. I can boot from a HDD with Windows 7 on it fine. 

There are no options to turn off UEFI boot and turn on Legacy boot in the BIOS. It has the latest BIOS update, v1.19.

Any other options getting this old PC to run the latest version of Ubuntu?

---

### Post by tea for one on 2019-12-18
How old is your HP Z200?

If it originally had Windows 7, then it is surprising that you cannot explore and alter the BIOS?

If you have a CD/DVD drive on this PC, then you could install via a DVD?

However, I'm pretty convinced that the BIOS options are available although probably hidden.

---

### Post by Autodave on 2019-12-18
+1 with tea for one: I have never seen a BIOS that didn't have those options.  They may be hard to find, but they are there.

---

### Post by oldfred on 2019-12-18
Is the external drive BIOS or UEFI boot?

If HP Z200 is older & BIOS only it should boot a BIOS system automatically, if you choose to boot the external drive.
But you may still have to turn on allow USB boot or full USB support.

My old BIOS system had many USB boot options. But to boot full install on flash drive, it was another hard drive boot option. See if you have a sub-menu for hard drive boot options.

---

### Post by tea for one on 2019-12-18
Another thought?

Is this an ex-corporate pc where the BIOS is password protected and the USB ports are disabled via a BIOS setting?

---

### Post by ian5142 on 2019-12-19
No, it is not a corporate PC that has a BIOS password. Yes, all of the USB ports are enabled.

Currently my Ubuntu internal HDD is corrupted. It won't boot in either of my two laptops. Error: fsck exited with status 8.

I know the drive is ext4. There is not much on there that I don't mind losing. It might be worth my while to just reformat and start over.

---

### Post by oldfred on 2019-12-19
If ext4 you can run a full fsck and see if that works.

       To see all the ext4 partitions
sudo parted -l
#From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p tries fixes where response not required, run both commands
sudo e2fsck -C0 -p -f -v /dev/sdb1
# -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

---

### Post by tea for one on 2019-12-20
> I have a SSD running Ubuntu 19.10. It floats from computer to computer at the moment. I have run it from both of my laptops and another desktop at different times. The HP Z200 refuses to boot from it

> I can boot from a HDD with Windows 7 on it fine. 

> Currently my Ubuntu internal HDD is corrupted. It won't boot in either of my two laptops. Error: fsck exited with status 8.

I'm a bit confused.

You have two laptops, one desktop and an old HP Z200?

Which machine originally contained the Ubuntu internal HDD?

Do you still have a boot problem with your *floating ssd*?

However, I have noticed that moving SSD and HDD drives from PC to PC (whether adding the drive internally or booting externally) has the potential to compromise the UEFI database.
When this happens, you can end up in a grub rescue screen with no easy way out.
If, as a last resort you power off the PC, you can cause corruption on an attached filesystem.

---

### Post by ian5142 on 2019-12-20
I have 2 laptops and the Z200. I believe the HDD was originally in one of the 2 laptops. That is the one I am trying to repair it in.

---

