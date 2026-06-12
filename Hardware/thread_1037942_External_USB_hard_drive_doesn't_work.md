---
title: "External USB hard drive doesn't work"
date: 2009-01-12
forum: Hardware
---

### Post by h2o4444 on 2009-01-12
Hello, 
 I've been trying to use my external hard drive in Ubuntu 8.10 and so far it has not worked. I can see the USB hard drive icon under computer:/// but when I try to open it, it says:

> UNABLE TO MOUNT EXTERNAL 60 GB
DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

 This hard drive was my old hard drive from a Toshiba Satellite 2455-S305. It is 60 GB and it is enclosed by a hotdrive case, which I bought separately to house the hard drive. The casing does not have an on/off button. It turns itself on when the USB is plugged into the computer, when the light is blue it means it's working properly, when the light is red it means it's not working properly (right now the light is red). Since I dual boot my HP Compaq tc4200 tablet laptop with Windows XP Pro Tablet Edition, I did not have this problem in windows.

 I tried to search for a solution to this problem on the web and at least one other person has the same problem, though with a different brand of hard drive. In one of the forums he/she was told to run "fdisk -l" in the terminal, so I did that too and this is what I get:

```
Disk /dev/sda: 60.0 GB, 60011642880 bytes
240 heads, 63 sectors/track, 7752 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x9d9818d7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7751    58597528+   7  HPFS/NTFS

Disk /dev/sdb: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd084d084

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        7296    58605088+   7  HPFS/NTFS
```

Can anybody help me? Thanks in advance.

---

### Post by madmax1735 on 2009-01-12
okey... since the drive u r tryin to load is an NTFS partition, u need to install something called ntfs-3g.

for this in terminal use command:

sudo apt-get install ntfs-3g

after this it will ask you for the sudo password. alternatively u could also install ntfs-3g using synaptic package manager.

after this you need to use another command in terminal:

sduo mount /dev/sdb1

alternatively you could also use ntfs tools under application>system tools>NTFS

if it gives u a weird error saying it cant mount "unclean shutdown" balh blah....... 2 option 

in terminal just issue comman:

ntfsfix /dev/sdb1 

and then the mount command....

i think that should do the trick.

---

### Post by h2o4444 on 2009-01-12
Hello madmax1735,
 Thank you for helping me. Before I did the 
"sudo apt-get install ntfs-3g" I actually saw that ntfs-3g was already installed in the Synaptic Package Manager. Since I'm kinda of new to Ubuntu so I did what you suggested anyways in the Terminal and I got:

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
ntfs-3g is already the newest version.
The following packages were automatically installed and are no longer required:
  libfreebob0 libwildmidi0 libdc1394-22 libsoundtouch1c2
  linux-headers-2.6.27-7 libjack0 linux-headers-2.6.27-7-generic libopenspc0
  podsleuth freepats gstreamer0.10-plugins-bad libcdaudio1 libgmyth0 libmms0
  libneon27-gnutls libiptcdata0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded

So from this I think you can tell that ntfs-3g is already installed. Then I did "sudo mount /dev/sdb1" and I got a message that read:

> mount: can't find /dev/sdb1 in /etc/fstab or /etc/mtab

By the way, there wasn't a NTFS program Under Applications > System Tools. Then I typed in "ntfsfix /dev/sdb1" and I got:

> The program 'ntfsfix' is currently not installed.  You can install it by typing:
sudo apt-get install ntfsprogs

Then I installed ntfsprogs then ran the "ntfsfix /dev/sdb1" again and I got:

> Failed to determine whether /dev/sbd1 is mounted: No such file or directory.
Mounting volume... Error opening partition device: No such file or directory.
Failed to startup volume: No such file or directory.
FAILED
Attempting to correct errors... Error opening partition device: No such file or directory.
FAILED
Failed to startup volume: No such file or directory.
Volume is corrupt. You should run chkdsk.

So I ran "chkdsk" on the command line and I got:

> bash: chkdsk: command not found

So I feel like I'm chasing a pigeon. Any ideas on what I should do next? I unplugged the USB drive and replugged it back in and got a different error message:
> 
UNABLE TO MOUNT EXTERNAL 60 GB
DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

Just to make sure I did the "sudo mount /dev/sdb1" command and I got the same error message in the Terminal, which is:
> 
mount: can't find /dev/sdb1 in /etc/fstab or /etc/mtab

PS: I installed ntfs-config from Synaptic Package Manager and a program called NTFS Configuration Tool appeared under Applications > System Tools. I opened it and check the box for "Enable write support for external device". But my external hard drive still doesn't work, with the same problem as before.

---

### Post by h2o4444 on 2009-01-13
OK, after some searching around I finally fixed the problem. Although I did it in Ubuntu I should have tried another, perhaps easier way, in Windows. And that is to first boot into Windows (my system is dual boot with XP and Ubuntu) and plug in the external USB hard drive, then unmount it by doing Safely Remove Hardware. Then go into Ubuntu and see if the problem is still there. I think what happens is that sometimes I just unplug the USB hard drive from Windows but system gets an error and thus Ubuntu thinks the drive is messed up. I have not tried this because I took the long way and did it in Ubuntu. If someone else has the same problem as me and solves it this way please let me know. I'm interested in finding out if my hypothesis is right or wrong.

Anyways, here's how I did it in Ubunto 8.10:

1) Install ntfs-3g and ntfsprogs (see previous post)
2) To find the drive I need to mount, I typed in "sudo fdisk -l" in the Terminal and got:

> Disk /dev/sda: 60.0 GB, 60011642880 bytes
240 heads, 63 sectors/track, 7752 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x9d9818d7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7751    58597528+   7  HPFS/NTFS

Disk /dev/sdb: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd084d084

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        7296    58605088+   7  HPFS/NTFS

3) I really don't know how to read this output but I think I needed to mount sdb1 because it didn't have as much info as sdb. Also I made sure that it is NTFS. Then I made a directory called sdb1 in /media by typing in "sudo mkdir /media/sdb1" in the Terminal
4) Then I typed "sudo mount -t ntfs-3g /dev/sdb1 /media/sdb1 -o defaults,unmask=0". This is a command that I found on some post. I think it means to mount the device called sdb1 in the /dev directory to the media directory that I just created in step 3. I don't know what "-o defaults,unmask=0" means. And my output was this:

> $LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sdb1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sdb1 /media/sdb1 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sdb1 /media/sdb1 ntfs-3g force 0 0

5) Note that I should have just done Choice 1, but I did Choice 2 because I wanted the challenge (I guess). Also I didn't know what relevant row the command is referring to in the /etc/fstab file. So after I typed in "sudo mount -t ntfs-3g /dev/sdb1 /media/sdb1 -o force" I got:

> $LogFile indicates unclean shutdown (0, 0)
WARNING: Forced mount, reset $LogFile.

6) At this point I'm beginning to have a good feeling about this, so I typed "sudo mount -t ntfs-3g /dev/sdb1 /media/sdb1 -o defaults,unmask=0" again thinking I had to mount it again because the system just reset itself. The message read:

> fuse: mount failed: Device or resource busy

7) This must mean the hard drive was mounted already, so I typed "ls /media/sdb1" and saw my folders in the hard drive. I saw the hard drive icon on the desktop as well.

---

### Post by h2o4444 on 2009-01-13
.

---

### Post by marty_ on 2009-01-22
I have just deleted vista and installed ubuntu  8.10 for the first time. so far it looks good and I am getting things going and glad to be free of MS.
I backed my documents up on a USB drive before installation with vista via NtfS file system, and now would like to access them.

I keep getting this message

$ ntfsfix /dev/sdb1 
Failed to determine whether /dev/sdb1 is mounted: No such file or directory.
Mounting volume... Error opening partition device: No such file or directory.
Failed to startup volume: No such file or directory.
FAILED
Attempting to correct errors... Error opening partition device: No such file or directory.
FAILED
Failed to startup volume: No such file or directory.
Volume is corrupt. You should run chkdsk.

Any advise please.  Marty

---

### Post by h2o4444 on 2009-01-23
Hello Marty,
 Read the previous posts to install ntfs-3g and ntfsprogs then follow the directions in #4. Ubuntu doesn't read and write NTFS file systems out of the box, must be a legal issue, so you have to install those two packages.

---

### Post by marty_ on 2009-01-24
Thanks,
 I did try all the things listed in the post and had no luck so I pulled the unit apart and and fitted the HD directly in my case.
 Mounted perfectly and all files are available to me.
I am very impressed with both ubuntu and this forum community and hope to learn a lot more here.

 Cheers and thanks.

---

