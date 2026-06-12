---
title: "Problem: USB Drive, mount, permissions, Apache"
date: 2009-12-20
forum: Hardware
---

### Post by tconrad on 2009-12-20
Hi,

I have Ubuntu 9.10 on an Acer Aspire One (to play and learn Linux).   I installed an Apache 2 web server
and that works fine.  However, I want to be able to see files on an external USB drive.

The USB drive mounts easily and correctly at bootup or by pluging it in.  However, the mount permissions have read/execute off for group/other by default and this prevents the web server from seeing the files.

I've found several discussions on the web related to this (although generally a year old!) and the suggestion is to create a mount in the /etc/fstab file which includes a umask to allow others to see the mount.

I try this but get an error about the fuseblk access.   It recommends doing a chmod 4755 on the ntfs-3g.  Well, that didn't work.  I ge tanother error saying that the suid is wrong when it tries to mount.  (I verified that the chmod was performed and it set some sticky bit).

Questions:

[INDENT]1) is this the best way to approach this?   I'm a single user on my laptop.  Is there an easier way - example, just get the automount to use the right umask?

2) ok, if I need to actually mess with fstab file, then ideas on settings?
[/INDENT]
If I ask the system what the auto mount used (which works), I get this:

/dev/sdb1 on /media/FreeAgent Drive type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)

I've tried including those various options in fstab, with no success.   I have the UUID (and it does get the mount command to see my request via fstab).  I created the mount point in /media as well.

The main error I get when I'm close is: 
[INDENT]*Unable to mount FreeAgent Drive.  Error mounting:  mount exited with exit code 1: helper failed with:*
*Unprivileged user can not mount NTFS block devices using the external FUSE*
*library. Either mount the volume as root, or rebuild NTFS-3G with integrated*
*FUSE support and make it setuid root. Please see more information at*
*[http://ntfs-3g.org/support.html#unprivileged](http://ntfs-3g.org/support.html#unprivileged)*
[/INDENT]
Must I rebuild the NTFS-3G?   If that's the trick - how does one do it?  The link above says to do the chmod which didn't work.  That wasn't "rebuilding" either.

Ideas?

Thanks,
Tim

---

### Post by tconrad on 2009-12-20
This link has relevant information, but again it refers to how to rebuild ntfs-3g, but nowhere explains how a novice actually goes about doing that to remedy the problem.

[https://bugs.launchpad.net/ubuntu/+source/ntfs-3g/+bug/205081](https://bugs.launchpad.net/ubuntu/+source/ntfs-3g/+bug/205081)

Tim

---

### Post by tconrad on 2009-12-20
Part 3...

It looks like I sort of have this fixed!!  (it works, but I get error messages).  I can even see files remotely via apache http connection!

Let me explain the things that I did.  I don't know how many are necessary.  I have a kludge of things from the internet.   The message "*rebuild NTFS-3G with integrated" *shows up in Google 1200 times, but there are no step by step fixes - amazing.  This seems to plague a lot of Linux users, old and new alike.

For those who stumble here, some notes.

You will need to hack a source file and install manually.  If you're spiled with the Synaptic installer like me, time to get out of the comfort zone.   For some reason, they didn't put this in as runtime option for average people to get their drives working with "user" access.

Do *not* get the latest version of ntsf-3g or you'll be left trying to figure out dependencies that Synaptic took care of for you (there are some missing header files with latest download).  Instead, look at the Synaptic window and see what version you already have installed.   Search for that and download it.  (it went to my $HOME/Downloads).

My ntfs-3g came from here:[https://launchpad.net/ubuntu/karmic/+source/ntfs-3g/1:2009.4.4-1ubuntu1Notes](https://launchpad.net/ubuntu/karmic/+source/ntfs-3g/1:2009.4.4-1ubuntu1Notes) on installing things manually:
   [http://www.faqs.org/docs/Linux-HOWTO/Software-Building-HOWTO.html](http://www.faqs.org/docs/Linux-HOWTO/Software-Building-HOWTO.html)


# create local scratch area
mkdir src
cd src
mv MYPATH/*gz .

# uncompress ntfs* files in here
gunzip -c ntfs* | tar xvf -
rm -f ntf*gz

# go to the ntfs area and be ready for editing
cd ntfs*

# do fixes
Edit the src/ntfs-3g.c file at the beginning of the main() function.   Comment out these
lines (edit to insert the /*  ** */ to look exactly as below).  (I found this on the web)


/* #ifndef FUSE_INTERNAL
* if ((getuid() != geteuid()) || (getgid() != getegid())) {
* fprintf(stderr, "%s", setuid_msg);
* return NTFS_VOLUME_INSECURE;
* }
* #endif
*/

# then run 3-step install
# want integrated fuse support

./configure --with-fuse=internal
make
sudo make installNote that the fuse=internal seems to be the default for a Linux install, but I'm not sure what's up with that.  The instructions on the web refer to using "integrated" mode, but that's not shown in any file in the directory.  Also, people on the web talk about *not* using external mode.  Well, it seems you need to pick one, so I said internal.   This is potentially a second difference from when this was installed with defaults by ubuntu.

Lastly, I uncommented the line with user_allow_other in /etc/fuse.conf.   Use

sudo vi /etc/fuse.conf

(or your favorite editor instead of vi).  Remove the # sign.   Some places on the net suggest this isn't needed (or used?).    I did it since it seemed to help.

Click on restart to reboot and hopefully things come back.   If not, you can always redo a clean install with none of these changes and redo the sudo make install again.

My last /etc/fstab has this:

UUID=425846E65846XXX /media/FreeAgentDrive ntfs user,umask=0022 0 0

and I manually created the directory /media/FreeAgentDrive with mkdir.


************* STATUS

While everything works now when I plug in the USB drive, but I get errors:

[INDENT]*Error mounting: mount exited with exit code 1: helper failed with:*
*Error opening '/dev/sdb1': Permission denied*
*Failed to mount '/dev/sdb1': Permission denied*
*Please check '/dev/sdb1' and the ntfs-3g binary permissions,*
*and the mounting user ID. More explanation is provided at*
*[http://ntfs-3g.org/support.html#unprivileged](http://ntfs-3g.org/support.html#unprivileged)*
[/INDENT]
Still, I can a desktop icon, and the file manager for the drive pops up.   I check and I can browse
the files and they have rwxr-xr-x permissions (the whole goal of this!).  As I mentioned, the web access also works perfectly.

This is the mount output...

/dev/sdb1 on /media/FreeAgentDrive type fuseblk (rw,noexec,nosuid,nodev,allow_other,default_permissions,blksize=4096)

I'd still like to get rid of the errors.  Ideas?  I'm sort of content to wait for a new (working) version of ntfs-3g to be released for ubuntu and hopefully an announcement that no weird stuff is needed.

-Tim

---

### Post by JFire on 2010-01-02
I think there may be a better solution:
[https://bugs.launchpad.net/ubuntu/+source/devicekit-disks/+bug/482501](https://bugs.launchpad.net/ubuntu/+source/devicekit-disks/+bug/482501)
 
Reply #13 at the above link instructs us how to rebuild the devicekit-disks package which is the HAL replacement in Karmic, with the appropriate permissions patch and install it.
Just follow the instructions from reply #13, or if you prefer download the already patched/rebuild .deb file and install it from here:
[http://seletkovic.net/code/devkit-disks/devicekit-disks_007-2ubuntu4custom1_i386.deb](http://seletkovic.net/code/devkit-disks/devicekit-disks_007-2ubuntu4custom1_i386.deb)

~ G

---

### Post by tconrad on 2010-01-27
Thanks JFire!

OK, my original setup got messed up.  An update came along (and frankly, I just take most of the updates that come along) and of course, today, I can't access my external drive at all.

I took your advice and did this:

[http://seletkovic.net/code/devkit-di...stom1_i386.deb]("http://seletkovic.net/code/devkit-disks/devicekit-disks_007-2ubuntu4custom1_i386.deb")

Since I had problems getting the new directions on that threat to work (for example, the second step didn't work and I don't have an AMD64).

Question:  Assume I'm a Linux dummy.   Is there any housekeeping that dummies need to do to

a) stop the old junk from reinstalling
b) make sure that we continue to get updates for the packages that work

Frankly, this is irritating.  If there was a way to disassociate my PC from the Linux developers that insist on defaulting my local USB drive from being accessible, I'd really like to do that.   We should at least have a straightforward way to set defaults or otherwise control at runtime the permissions for when we access external drives instead of errors and messages to go to the web for the latest threads on how to circumvent the new security.   The above link should just become the new default until the others get their act together.

Thanks much for the help!   If not for that link, I'd be back to square 1 today...

Thanks,
Tim

---

### Post by sufehmi on 2011-02-05
> **JFire said:**
> I think there may be a better solution:
[https://bugs.launchpad.net/ubuntu/+source/devicekit-disks/+bug/482501](https://bugs.launchpad.net/ubuntu/+source/devicekit-disks/+bug/482501)
 
Reply #13 at the above link instructs us how to rebuild the devicekit-disks package which is the HAL replacement in Karmic, with the appropriate permissions patch and install it.
Just follow the instructions from reply #13, or if you prefer download the already patched/rebuild .deb file and install it from here:
[http://seletkovic.net/code/devkit-disks/devicekit-disks_007-2ubuntu4custom1_i386.deb](http://seletkovic.net/code/devkit-disks/devicekit-disks_007-2ubuntu4custom1_i386.deb)

~ G

Hey JFire, nice one - after googling around, it seems that your suggestion above is the only feasible one.

Unfortunately, two years later - and this regression bug STILL existed :

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/453605/comments/9](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/453605/comments/9)

And the work around above no longer works :

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/453605/comments/10](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/453605/comments/10)

Also the deb package mentioned above is no longer available - I suppose it's good though, since it may no longer compatible with the latest version of Ubuntu.

So - any ideas / hints on how to resolve this problem now ?



Thanks !
Harry

---

### Post by JFire on 2011-02-05
Hi

I've re-built the package as per the instructions in Reply #13 at ([https://bugs.launchpad.net/ubuntu/+source/devicekit-disks/+bug/482501](https://bugs.launchpad.net/ubuntu/+source/devicekit-disks/+bug/482501)) and made it available again.

I haven't tested the new package, but I don't see why it wouldn't work. You can find the appropriate deb files here:
[http://seletkovic.net/code/devkit-disks/devicekit-disks_007-2ubuntu7custom1_i386.deb](http://seletkovic.net/code/devkit-disks/devicekit-disks_007-2ubuntu7custom1_i386.deb)
[http://seletkovic.net/code/devkit-disks/devicekit-disks-doc_007-2ubuntu7custom1_all.deb](http://seletkovic.net/code/devkit-disks/devicekit-disks-doc_007-2ubuntu7custom1_all.deb)

Please let us know if this solution is still relevant and works for you - if it's no longer relevant I'll delete it.

Thanks

~G

---

### Post by sufehmi on 2011-02-09
> **JFire said:**
> Hi

I've re-built the package as per the instructions in Reply #13 at ([https://bugs.launchpad.net/ubuntu/+source/devicekit-disks/+bug/482501](https://bugs.launchpad.net/ubuntu/+source/devicekit-disks/+bug/482501)) and made it available again.

I haven't tested the new package, but I don't see why it wouldn't work. You can find the appropriate deb files here:
[http://seletkovic.net/code/devkit-disks/devicekit-disks_007-2ubuntu7custom1_i386.deb](http://seletkovic.net/code/devkit-disks/devicekit-disks_007-2ubuntu7custom1_i386.deb)
[http://seletkovic.net/code/devkit-disks/devicekit-disks-doc_007-2ubuntu7custom1_all.deb](http://seletkovic.net/code/devkit-disks/devicekit-disks-doc_007-2ubuntu7custom1_all.deb)

Wow, excellent ! :D ok here goes :

First it conflicted with dmsetup, no problem = ```
sudo apt-get remove dmsetup
``` -- clear !

Then I installed it again, but got a different error :

```
$sudo dpkg -i devicekit-disks_007-2ubuntu7custom1_i386.deb 
(Reading database ... 218134 files and directories currently installed.)
Preparing to replace devicekit-disks 007-2ubuntu7custom1 (using devicekit-disks_007-2ubuntu7custom1_i386.deb) ...
Unpacking replacement devicekit-disks ...
dpkg: dependency problems prevent configuration of devicekit-disks:
 devicekit-disks depends on libparted1.8-12 (>= 1.8.8.git.2009.06.03-1ubuntu5); however:
  Package libparted1.8-12 is not installed.
dpkg: error processing devicekit-disks (--install):
 dependency problems - leaving unconfigured
Processing triggers for man-db ...
Errors were encountered while processing:
 devicekit-disks

$
```

I did sudo apt-get update, no joy. So I looked around my repository server's directory. I looked in all branches - main,universe,multiverse; but can't find this libparted1.8-12*.deb file at all.

So currently I'm stumped there.

Any hints / ideas ?


Thanks!
Harry

---

### Post by pkeffect on 2011-06-04
As  this is my first post bare with me...

So I installed apache2, mysql and php5 (Ubuntu 11.04 - gnome classic). All works well after a bit of configuring. Then I try setting a symlink to a storage directory on my external 2TB usb drive. No go... 

I then found this thread along with few others around the web with the same issues. Apache and persmission issues keeping apache or any user from having read or write access to the external. You can't chown or chmod it with any positive outcome. This is because the external drive is automounted by hal with some really crap perms. I was getting fed up.

On my last straw I tried this. I made a shell script to remount the drive the way I wanted it mounted.

```

sudo umount /dev/sdb1
sleep 1
sudo mount -o umask=0000 /dev/sdb1 /media/External-2TB

```Seems changing the umask to 0000 (root) was the winning work. I have to run this script every time I reboot which isn't too much of a hassle. Reboot and look at a dir or page via your browser on your externeal and you'll get those damn permission problems you can't do anything about. Remount your drive with new umask and try to access again and you will be good to go.

This might not been everything I had done to fix the problem. I guess i will have to wait till someone else tests this out. BTW, my external is formatted with NTFS and this made 0 difference.

Hope this helps some of you.


-pkeffect

---

### Post by jcmtnez on 2012-08-05
Thanks to pkeffect. Your solution worked perfectly for me. Good thing this was your first post. 

Here it is a bit more elaborated for those not too familiar with shell scripting.

Note: My USB drive was mounting automatically as Bkup. Change Bkup to match the name of your USB drive.

I created a text file and I named it **mount-usb.sh**. I added to this file the code below. On the header of this code it is described how to use it:

```

#!/bin/bash    
# This script is for mounting the external USB drive so that Apache can
# see it as described at: http://ubuntuforums.org/showthread.php?t=1360075
# Before running for the first time you must make this file executable
# as follows:
#  $ chmod a+x mount-usb.sh
#  $ chmod 700 mount-usb.sh
# After that you can run this script like this:
#  $ ./mount-usb.sh
# You must run this script every time you start the system and attach
# the drive.

sudo umount /dev/sdb1
sleep 1
sudo mount -o umask=0000 /dev/sdb1 /media/Bkup

```Note: The first time I ran this it gave me an error like:

```

fuse: failed to access mountpoint /media/Bkup: No such file or directory

```I created a new folder called Bkup under /media and I ran the script again.

It worked like a charm!

---

