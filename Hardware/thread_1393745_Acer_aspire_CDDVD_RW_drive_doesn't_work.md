---
title: "Acer aspire CD/DVD RW drive doesn't work"
date: 2010-01-29
forum: Hardware
---

### Post by Jabrouwer on 2010-01-29
Firstly, I am an linux noob.

My Acer aspire 5810TZ-4274 CD/DVD RW drive refuses to run any CD or DVD I put in.  The drive spins the cd for a few seconds, then stops and won't run the disk.

---

### Post by quixote on 2010-01-30
Just guessing, but it sounds to me like that's a bad drive.  Did the machine come with Windows?  If it's still on the system, can you boot into it, and does it see the CD?  If yes, then it's not the drive, but if no, then it's definitely the drive.  If this is a new computer, have the drive replaced while it's still under warranty!

---

### Post by Jabrouwer on 2010-01-31
It works in windows.  If the cd is in when I boot, Linux will read the cd and it will work fine.

---

### Post by quixote on 2010-01-31
Oh, okay, if a liveCD works then it's a totally different problem.  It's not even that there's something incompatible between your cd-dvd drive and ubuntu.  Just something awry with the setup.  Not that that makes it any easier... :(.

First, let's see if the drive is mounted, but just not showing up on the desktop for some reason.  Put a CD in the drive and wait for it to finish trundling.  Open a terminal (Accessories > Terminal) and at the command prompt type "mount -l" ("l" as in list, and without no quotes).

Near the bottom should be a line that looks something like this: > /dev/sr0 on /media/cdrom0 type iso9660 (ro,nosuid,nodev,utf8,user=you) Look for a line that says "cdrom" somewhere.  If there is none, it's not being mounted.  If it's there, copy it into your answer, and we'll see if that gives us something to work with.

---

### Post by TheWhiteDemon on 2010-01-31
I'm guessing you don't have the right codecs installed to play a CD or DVD. Install non-free codecs.

---

### Post by Jabrouwer on 2010-01-31
It has nothing to do with a liveCD, if there is a cd in the drive when I turn on my computer, linux (installed on my laptop) can read and wrote whatever is in the drive, but even if I eject the cd, it thinks the cd is still there.

Without a cd showing up, I get this from "mount -l"

/dev/sda5 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/home/jacob/.Private on /home/jacob type ecryptfs (ecryptfs_sig=f21521d282e02c85,ecryptfs_fnek_sig=6b88e6b3e96bf2c1,ecryptfs_cipher=aes,ecryptfs_key_bytes=16)

With a cd that shows up, I get:

/dev/sda5 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/home/jacob/.Private on /home/jacob type ecryptfs (ecryptfs_sig=f21521d282e02c85,ecryptfs_fnek_sig=6b88e6b3e96bf2c1,ecryptfs_cipher=aes,ecryptfs_key_bytes=16)
gvfs-fuse-daemon on /home/jacob/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=jacob)

I'm pretty certain they both say the same thing, and either way I don't see cdrom anywhere.

---

### Post by quixote on 2010-01-31
Yes, it sure looks like the CD isn't being mounted at all.  What does happen is that gvfs-fuse daemon becomes active, which is also weird.  It should be active all the time, I believe.  It's got no business thinking it's a cd-rom, or whatever it's doing!  Hopefully, somebody who knows what that means will come and tell us!

Meanwhile, try mounting a cd manually.  Put in a CD that you know works elsewhere.  Then type the following at the command prompt ```
sudo mount /media/cdrom0/
``` (that's cdrom-zero).  If there's a desktop icon and you can see the cd's files, great.  Then we just have to figure out why it's not doing it automatically.  If nothing visible happens, see whether there's anything new when you do "mount -l".  Also, open nautilus (file manager) and see whether you can see the CD files under the /media folder within the cdrom0 subfolder.

Remember, before pushing the button to eject the cd it needs to be unmounted: "sudo umount /media/cdrom0/"

---

