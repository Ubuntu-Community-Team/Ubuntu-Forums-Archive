---
title: "USB Drive Ownership"
date: 2006-08-08
forum: Hardware &amp; Laptops
---

### Post by LadyDoor on 2006-08-08
Hello...

Does anybody know of a way in which to allow me to move files onto and off of (or create and/or delete files on) a USB stick without having to use sudo every time? I just ask because it's kind of annoying having to su or sudo anytime I want to use the thing. Here's the line from my fstab (I had the same problem before adding the line--having it in my fstab doesn't seem to cause it to automount, unfortunately--any thoughts on that?).

# /dev/sda1 is, I have determined, the right device.
# <file system> <mount point>  <type>  <options>       <dump>  <pass>
/dev/sda1       /media/thumb   auto    rw,user,noauto     0       0

And here's the relevant output from dmesg when I plug it in.

[17180620.196000] usb 3-2: new high speed USB device using ehci_hcd and address 4
[17180620.328000] scsi2 : SCSI emulation for USB Mass Storage devices
[17180620.328000] usb-storage: device found at 4
[17180620.328000] usb-storage: waiting for device to settle before scanning
[17180625.328000]   Vendor: Ut161     Model: USB2FlashStorage  Rev: 0.00
[17180625.328000]   Type:   Direct-Access                      ANSI SCSI revision: 02
[17180625.332000] SCSI device sda: 983808 512-byte hdwr sectors (504 MB)
[17180625.332000] sda: Write Protect is off
[17180625.332000] sda: Mode Sense: 00 00 00 00
[17180625.332000] sda: assuming drive cache: write through
[17180625.340000] SCSI device sda: 983808 512-byte hdwr sectors (504 MB)
[17180625.344000] sda: Write Protect is off
[17180625.344000] sda: Mode Sense: 00 00 00 00
[17180625.344000] sda: assuming drive cache: write through
[17180625.344000]  sda: sda1
[17180625.372000] sd 2:0:0:0: Attached scsi removable disk sda
[17180625.372000] sd 2:0:0:0: Attached scsi generic sg0 type 0
[17180625.384000] usb-storage: device scan complete

Any thoughts on this?

Thanks,
Door

---

### Post by jordilin on 2006-08-08
Ubuntu should detect it automatically, so it's not necessary having a line in fstab. Second, what filesystem format has your pendrive?

---

### Post by LadyDoor on 2006-08-08
Thanks for your reply. Uhhh...Ubuntu does not detect it automatically; I promise. I had to make a dir in /media for it and also had to do some googling as to where I could find the device so as to be able to mount it in the first place. I believe that the filesystem is FAT, since it is supposed to be designed to work on Windows, Mac, and Linux. The problem isn't a complete inability to write to the thing--it's that I have to be root. I'd like to find a way to write to it as my normal user account (it would also be nice if it would automount, but I'll take what I can get).

Any ideas?
--Door

---

### Post by LadyDoor on 2006-08-08
Oh, and I should probably mention that attempts to **chown** the dir the drive is mounted on only gives me an error that the operation's not permitted; the same goes for anything on the drive itself. Normally the folder the drive is mounted on is owned by my normal user; however, when I mount it, it becomes owned by root until I unmount the drive.

--Door

---

### Post by LadyDoor on 2006-08-09
Sorry to bump, but, well...*bump*

---

### Post by rippon on 2006-08-09
I am interested in the solution as well. If mine mounts at all, it is read-only unless I do:
sudo mount -o rw,remount /media/sdb1

But typing in the command gets old if you use it a lot, and it *should* autodect. Same thing with my camera as well.

Bump for a good thread!

---

### Post by LadyDoor on 2006-08-11
Hate to be rude, but *ka-bump*

---

### Post by LadyDoor on 2006-08-17
Any ideas? It just seems weird that there's no way to have a non-root-writable usb drive.

--Door

---

### Post by a133x on 2006-08-18
I have exactly the same problem as yours, cant write on it, dont have permission, aldo it would be great if we could login as root. THat would solve the problem. Anyone has a tip for us?

---

### Post by a133x on 2006-08-18
> **a133x said:**
> I have exactly the same problem as yours, cant write on it, dont have permission, aldo it would be great if we could login as root. THat would solve the problem. Anyone has a tip for us?

I have solved my problem but I am not sure if this will work for you. What I did was that I added to the /etc/fstab to the usb device line, I added to the option field "user" so it gave acces for me to mount it directly with the user rights. So you should try this. IF this still does not I can tell you something what to do, but this is totaly not recommended. You have to log in as root in gnome. Go to System > Administration > Login Screen  and under de security tab click on "alow system administrator login", BUT I repet, this is not advised to do because it will not be as secure.

---

### Post by LadyDoor on 2006-08-18
Thanks for your replies...if you'll recall from my first post, though, updating /etc/fstab did *not* solve the problem, even after reboot.

Also, sorry to contradict you, but there is no need to log in to GNOME as root. If I recall, there may be a way to start a terminal or file manager as root from your regular account (for the GNOME environment, for example, <alt>F2 -> gksudo nautilus -> <enter>). In addition, you can always **su** to root in a terminal:

To set the password for root:
```
$ sudo passwd root
```
After you enter your password for sudo, you will be met with the following prompt. Enter the new password (a SECURE one--this is root!) and then retype it when asked to.
```
Enter new UNIX password:
Retype new UNIX password:
```

Then, any time you are in a terminal(my preference--I don't much like file managers), you can type
```
$ su
```
and then enter root's password. You will be root on that terminal until you type
```
$ exit
```
or until you close it. But BE CAREFUL with this. I wanted to get around this because it's not a good idea to play around as root--so I didn't want to have to su all the time. Oh well. Thanks anyway.

--Door

---

### Post by LadyDoor on 2006-08-18
P.S.:  GNOME probably also has a way to add a shortcut to your desktop or to the GNOME bar to open a root file manager or term. I don't use it, though, so I'm not sure.

--Door

---

### Post by heffo_j on 2006-08-19
G'day,

I'm no super wiz on this but here is my solution:

My USB stick shows up on the screen. I right click on the icon as root and change the permissions. Bingo.

Here is my interesting problem. 

I lose the USB sick connection when I start up VMware Server to run my XP ( as VMware virtual machine). This is configured to see the USB stick and does so, but at the expense of losing the connection under Ubuntu. Solution is to reboot/hibernate and it is back. Alternatively, I "switch off" the USB stick in VMware and it preserves the USB connection under Ubuntu. Now work that one out??

Regards
John

---

### Post by LadyDoor on 2006-08-19
> I lose the USB sick connection when I start up VMware Server to run my XP ( as VMware virtual machine). This is configured to see the USB stick and does so, but at the expense of losing the connection under Ubuntu. Solution is to reboot/hibernate and it is back. Alternatively, I "switch off" the USB stick in VMware and it preserves the USB connection under Ubuntu. Now work that one out??

I don't know whether this will work, but you might try unmounting the USB stick in Ubuntu prior to trying to use it in VMWare.

--Door

P.S.:  How about a way to write the the thing as somebody *other* than root? Anybody???

---

### Post by moreinfo on 2006-08-20
I'm very new at this stuff and still am completely lost on what's being said.  I'm not sure if this is even the right thread but...

I recently bought an MP4 and put some music on, simply by copying and pasting it.

Anyway, I closed it then tried it out, it worked perfectly, so I decided to add some more.

But this time I went to add them and got the following message:

[SIZE="3"]Error while copying to "/media/usbdisk".
You do not have permissions to write to this folder.[/SIZE]

It shows up on my desktop everytime I plug it in.
What does "mount" mean?

So do you think if I try the:" sudo mount -o rw,remount /media/sdb1 " from rippon or the,

/etc/fstab from a133x

could that help?

And if I were to try it, what does it mean, how and where do I try it?  ...Yes I am so new... but at least I'm trying.

Thanks for your help in advance.

Oh yeah, and I tried to change the permissions but got the following:
[SIZE="3"] The permissions could not be changed
Couldn't change the permissions of "usbdisk" because it is on a read-only disk[/SIZE]
How can I change it back to obviously how it was before.

---

### Post by moreinfo on 2006-08-24
Anyone?

---

### Post by LadyDoor on 2006-08-24
> What does "mount" mean?

Here's the thing:  Windows considers every device to be a different "drive" (so you've got **drive c** with all the program files, **drive a** with a floppy disc, **drive d** with your cds, etc.). This means that every time you insert a device, Windows considers it to be a whole new filesystem--which is why you have **c:\\whatever\whatever** for a file on your computer, but **d:\\something\something** would be the location for a file on a CD.

Linux, on the other hand, considers everything to be part of the same filesystem--so **/** is the root of the filesystem (so you've got, say, **/home/username** instead of **c:\\My Documents** or whatever). This means that whenever you insert a CD, Linux has to "mount" it, or decide on a place in your filesystem to put those files. For example, in Ubuntu when you insert a CD, it is "mounted" on **/media/cdrom0**--insert a data CD and then open **/media/cdrom0** and you will see what I'm talking about. If you have any questions I would be glad to try to explain further.

> Error while copying to "/media/usbdisk".
You do not have permissions to write to this folder.

That is because you need to write to it as root, unfortunately. I believe that earlier in this thread there were explanations of how to go about doing that.

> So do you think if I try the

```
sudo mount -o rw,remount /media/sdb1
```

from rippon or the **/etc/fstab** from a133x, could that help? And if I were to try it, what does it mean, how and where do I try it?

It just might help. To use rippon's suggestion, you need to open up a terminal like so:  hit *alt+F2* (in GNOME), type *gnome-terminal*, and then hit *enter*.

Now, just copy and paste the command that rippon provided into the prompt and enter your password.*

As to the **/etc/fstab**...**fstab** is a file in the **/etc** folder (**/etc** is where system-wide configuration files are kept). So to edit that, you would need to fire up your favorite text editor as root and point it at that file--but make a backup first.

> Oh yeah, and I tried to change the permissions but got the following:

```
The permissions could not be changed
Couldn't change the permissions of "usbdisk" because it is on a read-only disk
```

How can I change it back to obviously how it was before.

That is *exactly* what this thread is trying to establish.

> Yes I am so new... but at least I'm trying.

Yes! There is nothing wrong with not automagically knowing all the answers. It's good to ask questions, because that's how you get answers--AND you seem to ask questions nicely, which is extra-good with sprinkles and chocolate on top 8) . I know that this stuff can be frustrating and confusing at first, but once you get everything up and running as you like it, it's a good operating system. Good luck, and just be persistent!

--Door

*BUT you need to substitute whatever the name of your folder is...it'll be **/media/something**

---

### Post by LadyDoor on 2006-08-24
Hee! I figured out how to fix *my* problem (or at least this one)!!!

Edit **/etc/fstab** so that it includes a line for your device like this one:

```
/media/thumb     auto    rw,user,noauto  0 0
```

DO include the "user" line.

Now, open up the **/etc/group** file and add yourself to the group **users**, like so (without the "before" and "after" lines):

```

(BEFORE)
users:x:100:

(AFTER (if you happen to be me))
users:x:100:door

```

So there you have it--usb media mounted as your user! Shiny.

--Door

---

### Post by wyth on 2006-08-24
Just checking, because you just added this answer and I just started reading this thread 10 minutes ago.

Was your USB mounting, but you were unable to save anything to it?  The problem I'm having is everything looks hunky-dory, and a file will show up on my USB drive if I copy it there while it's still plugged in, but if I remove the drive and plug it back in, no file is there.

---

### Post by LadyDoor on 2006-08-24
Wyth:  my problem was that you had to be root to save to the USB, and it's not good to do more things as root than you absolutely *have* to--so I was looking for a way to save files as my normal, day-to-day user. Sorry...I wish I could be of more help to you, but I have no idea what's causing your problem.

Good luck!
--Door

---

### Post by glennric on 2006-08-24
I don't know if this will help you or not.  I have a usb flash drive that is automatically detected when I insert it.  Furthermore, I am the owner of the files on it.  Not root.  I looked in the mtab and it has the line
```
/dev/sda1 /media/usbdisk vfat rw,nosuid,nodev,quiet,shortname=mixed,uid=1000,gid=1000,umask=077,iocharset=utf8 0 0
```

---

### Post by moreinfo on 2006-08-26
Hi again, 

Well I still have absolutely no idea, I tried the remount thing, but I think it's mounts everytime anyway, as it shows up on my desktop and I can access the files on it.

I still can't add files to it as I still have no "Permissions", I even tried as root but got exactly the same answer.

So I was wondering how to edit /esc/fstab

because I was trying to change permissions in as root and nothing would change.

Thanks again for any insight.

---

### Post by LadyDoor on 2006-08-26
First, back up your /etc/fstab. In a terminal:

```
sudo cp /etc/fstab /etc/fstab.bak
```

Then press <alt>f2, enter **gksudo gedit /etc/fstab**, and hit enter. Follow the directions earlier in this thread for what to do with it.

--Door

---

### Post by moreinfo on 2006-08-28
Well, you wouldn't read about it. 
It worked! I can now add files and folders.

But, the funny thing is (well not really) is that I added another folder to my usb and the original one I added has gone mad!

140608 items!!
I can't delete the original folder because it won't let me 'trash' it.
Each time I go into it I have to click "Stop".
it shows the files but then it starts multiplying them???

And I can't figure out how to get rid of it.
I want to try and delete it from within Terminal but have no idea how.

It's just weird, the highest I saw was over 3,000,000 items and over 390GB on a 1GB usb. Go Figure!

Again any help to delete would be appreciated
Thanks

---

### Post by LadyDoor on 2006-08-28
> I want to try and delete it from within Terminal but have no idea how.

Back up that other folder you wanted to keep, first.

```
$ cp /path/to/usb/and/then/to/good/folder /path/to/destination
```

Then, do this:  

```
$ cd /path/to/usb
```

Then, type **pwd** to make *absolutely sure* you're in the right dir.

Finally, do the following. BE VERY, VERY CAREFUL WITH "rm -rdf." 

MAKE SURE that you remember the "**./**"--especially the "**.**" .

```
$ rm -rdf ./*
```

It will take a while. And if you need to be root to write to your usb, do sudo before that command, but be EVEN MORE CAREFUL :-) .

The reason for the extra caution is that that will **remove** from the folder **.** (your working directory--the one you're in), **recursively,** **including directories** and **forcing the removal of all files without prompting you**, everything specifed after the **/**. And what's specified after the **/** is *****, meaning **any sequence of characters greater than or equal to 0 in length**.

Good luck!

--Door.

P.S.:  You might also check that directory you copied into it for viruses...

---

### Post by moreinfo on 2006-08-28
Thanks for that,

Although it didn't seem to remove it, I couldn't get right into the folder to delete it.

I only got to media/usbdisk

It would not recognise anything after that.

I tried again to delete (not in terminal) but got the following error.

Error "I/O error" while deleting "/media/usbd.../...

And what's a good virus scanner you could recommend. I do have firestarter.
I am so used to XP.

Thanks again.

---

### Post by manitoba98 on 2006-08-28
Have you tried the gid= and umask= mount options? setting gid to an appropriate group, and umask to 007 or similar, when mounting (using -o), or in the fstab (under the options column). That should cause it to mount with that group and umask.

---

### Post by moreinfo on 2006-08-30
Hi, I'll try anything to learn, just don't know what it means.

 manitoba98  	Have you tried the gid= and umask= mount options? setting gid to an appropriate group, and umask to 007 or similar, when mounting (using -o), or in the fstab (under the options column). That should cause it to mount with that group and umask.

So if you can continue to point me in the right direction, I'll go for it!

I'm so new you really have to spell it out.
Thanks again.

---

### Post by moreinfo on 2006-08-30
OK, LadyDoor, I got the following...

bash: /bin/rm: Argument list too long

Thanks for any info.

---

### Post by LadyDoor on 2006-08-30
My guess is it thinks there're too many files in there to remove all at once. I don't know what's making it go crazy, but it sounds like bad news :-( .

Good luck!
--Door

---

### Post by moreinfo on 2006-09-01
Too Many! Absolutely!

Over 140,000 with GigaByte coming out my ears. 

Something definitely is up. It's only 1GB, thanks for your help LadyDoor.

Looks like I'll keep searching.

---

### Post by GabrielWolff on 2006-09-01
Hey, I got a similar problem, but nothing in this thread could solve it.

All the files on my USB stick are read-only files, and I'm not the owner, so I can't change that (how come?)

my etc/fstab looks like this (after trying to change it according to this thread, which obviously didn't help):

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda	/media/MEMORYSTICK	vfat	rw,user,noauto,sync	0	0
```

What's wrong?

---

### Post by LadyDoor on 2006-09-01
Try adding yourself to the group "users." Back up a little bit to find out how, in one of my posts :-)

--Door

---

### Post by GabrielWolff on 2006-09-01
Hey door, thanks for you reply

Did that, did that. Here's how my **etc/group** looks:

```
root:x:0:
daemon:x:1:
bin:x:2:
sys:x:3:
adm:x:4:gabriel,barbara
tty:x:5:
disk:x:6:
lp:x:7:cupsys
mail:x:8:
news:x:9:
uucp:x:10:
man:x:12:
proxy:x:13:
kmem:x:15:
dialout:x:20:gabriel,cupsys,barbara
fax:x:21:gabriel,barbara
voice:x:22:
cdrom:x:24:hal,gabriel,barbara,haldaemon
floppy:x:25:hal,gabriel,barbara,haldaemon
tape:x:26:gabriel,barbara
sudo:x:27:
audio:x:29:gabriel,barbara
dip:x:30:gabriel,barbara
www-data:x:33:
backup:x:34:
operator:x:37:
list:x:38:
irc:x:39:
src:x:40:
gnats:x:41:
shadow:x:42:
utmp:x:43:
video:x:44:gabriel,barbara
sasl:x:45:
plugdev:x:46:hal,gabriel,barbara,haldaemon
staff:x:50:
games:x:60:
users:x:100:gabriel
nogroup:x:65534:
crontab:x:101:
ssh:x:102:
postfix:x:103:
postdrop:x:104:
syslog:x:105:
klog:x:106:
gabriel:x:1000:
lpadmin:x:107:gabriel,barbara
scanner:x:108:gabriel,barbara,cupsys
admin:x:109:gabriel,barbara
messagebus:x:110:
hal:x:111:
slocate:x:112:
saned:x:113:
gdm:x:114:
barbara:x:1001:
dhcp:x:115:
ssl-cert:x:116:
haldaemon:x:117:
```

As you suggested, I added myself to groups:x:100. Was empty before. Still, even after reboot (dunno if that was needed), it changed nothing. Any ideas why?

Gabriel

---

### Post by LadyDoor on 2006-09-01
Gabriel,

I'm sorry...I don't know why it didn't work--I only know what does or doesn't work for me, to be honest.

I wish you the best of luck in fixing this.

--Door

P.S.:  You might try doing sudo chown gabriel:gabriel * while in the directory of your usb stick.

P.P.S.:  For future reference, I'm told a reboot isn't necessary after modifying /etc/fstab or /etc/group.

---

### Post by rshel on 2006-09-07
WEll here is an interesting wrinkle ...

I have a USB thumb drive.  A few months ago, when I first became an apotle ofUbuntu, I had problems with writing to my usb thumb/flash drive because of ownership problems.  After exploring this and other threads, I found a sort-of solution.  Part of the problem was that any file created by apps such as OpenOffice had very restrictive permissions that prevented me from copying them to external drives (I think, it's been awhile).  Eventually I just made a launcher that recursively changed permissions in the directory where my work files are and that solved that. Not too elegant, but it worked and I didn't have time or knowlege for anything more involved.  

Anyway, to get to the point, suddenly one of my thumb drives stopped working.  My other three other usb thumb drives (I carry a lot of files around from machine to machine, which is why this is a crucial problem for me) still work fine. Just this one forgot who I am and refuses to allow me to write to it.

I tried Lady Door's suggestion of adding myself to users.  It worked.  Unfortunately, whenever I use Unison to sync my files, the usb thumb drive becomes read only again.  These problms with usb drives and easy write access are going to be a big reason why more people dont' use Ubuntu/linux.  It is just too much of a headache to find out suddenly you can't quickly and easily transfer your files when you need to.  That said ... for me, Ubuntu is too much fun to ever think of returning to Windows except for visits.

---

### Post by gostal on 2006-09-08
For what it's worth after this very looong :) thread here's a tiny fstab howto. With apropriate options in fstab you can control who's to own the device and what group it should belong to by setting the options uid and gid (user ID and group ID). These are the numbers that you find in /etc/passwd and /etc/group. In /etc/passwd the first number is uid and the second gid. In /etc/group there is only one and that's gid. If these options are not set then by default root is used for both.An easy way of finding uid and gid for a user logged in is to issue the following command in a terminal window:```
id
``` 

Read and write permissions are set by the option umask provided that the device is mounted with the options rw as opposed to ro which indicates that the divice will be read-only no matter what the umask says. The umask consists of three octal numbers that work exacly the opposite way compared  chmod. The numbers controlling permissions are:

read		4
write		2
execute		1

Using chmod you would set the permissions by adding whatever numbers you want so that read and execute would be 5 and write and execute would be 3 (I can't imagine why anyone would want to be able to write but not read but logically that's how it works:D ). For umask it's the other way around so that 5 would mean that read and execute are not allowed and a umask of 7 means that you can't do a thing.

Example fstab line for a FAT formatted device:

```
/dev/device /mnt/mountpoint vfat rw,user,uid=1000,iocharset=iso8859-1,umask=007 0 0
```


device=hdb3 - 3rd partion on hdb i.e. second IDE hard drive 
device=sda1 - 1st partion on a scsi drive or a usb storage medium.
vfat - filesystem type
user - allows users to mount and umount if they are members of group users which users are not by default
iocharset - option controlling char encoding and byte interpretation. By default iocharset=utf8 is normally used but this does not go well with FAT or at least that used to be the case.

The owner of the device has uid=1000 and since gid is not set the group will default to root (gid=0 normally). The umask setting 007 will grant full permissions(read,write,execute) to owner and group whereas world can do nothing. Note that the device will have to be mounted with read/write permissions (rw) for the umask setting to have any effect for owner and group.

The two zeros at the end of the line indicate that the filesystem should neither be checked nor dumped in the event of a system hangup.
 
USB storage media should normally automount if they can be correctly identified by the hal daemon. Making an fstab entry for the device means that it cannot automount. In Ubuntu the actual mounting is done by pmount if there is no fstab entry. Unfortunately pmount has many mount options hard coded that is you don't get much say. Ohter distros may do things differently by dynamically updating /etc/fstab for instance.

This tiny guide should enable you to set up /etc/fstab so that you can do what you want with the device.

Best wishes
Gösta

---

### Post by rshel on 2006-09-10
Thanks!  I will give it a try. This is why I love ubuntu and linux: people willing to share knowledge rather than horde it for profit.  If only there were an Ubuntu for everything else in the world ....


EDIT:  Tried your suggestion.  Basically worked as well as that given by Lady Door.  The usb thumb/flash drive mounts and is read/write able. However, whenever I run a profile in UNISON to try to sync my hard drive files with the usb flash drive files, the flash drive becomes read-only.  This occurs  after UNISON has compared the two drives and determined the differences between them.  So UNISON then refuses to write new files to the flash drive. The permissions of the flash drive still show rwx for user and group.  Very strange.  I'll post this on a UNISON thread as well.  

Thanks.

---

### Post by moreinfo on 2006-09-13
Well, I tried everything, and it seems that I must have a completely different sort of problem.

Anyway, I plugged my USb into a Windows XP machine and what would you know, "Virus, Detected", AVG found it and booted it. however this did not get rid of my 140000+ items.

However, now, I can use my USB storage with no problems.  It's just like having a ghost directory on there that I can see - Still can't get rid of it, but it's not taking any space, or being a problem, so for me, it's staying.

As for others, I still am only a newbie, and still have know idea about Linux, but will continue to have fun (or not!) learning.

---

### Post by threespacemen on 2006-11-28
> **gostal said:**
> USB storage media should normally automount if they can be correctly identified by the hal daemon. Making an fstab entry for the device means that it cannot automount.

If you want to be able to change the umask (ie, permissions) on devices and still have them automount when you plug them in, the file you need to look at is:

/usr/share/hal/fdi/policy/10osvendor/10-storage-policy.fdi

Search for your device name in this file (plug the device in, then type dmesg in a terminal window - should be listed under "Model", but ymmv...) - in my case it was an ipod. Section of the file looks something like this:

```
          <!-- Attempt mount point 'ipod' for iPod's -->
          <match key="@block.storage_device:portable_audio_player.type" string="ipod">
            <merge key="volume.policy.desired_mount_point" type="string">ipod</merge>
          </match>
```

I added the following line just after the "merge key" line:

<merge key="volume.policy.mount_option.umask" type="string">000</merge>

...so the whole thing looks like this:

```
          <!-- Attempt mount point 'ipod' for iPod's -->
          <match key="@block.storage_device:portable_audio_player.type" string="ipod">
            <merge key="volume.policy.desired_mount_point" type="string">ipod</merge>
            <merge key="volume.policy.mount_option.umask" type="string">000</merge>
          </match>
```

So now when I plug the ipod in, automount works without a problem, and mounts with full permissions. Of course, change your umask value to best reflect whatever permissions you want to have on the device.

(found the answer at [http://lists.freedesktop.org/archives/hal/2005-December/004120.html](http://lists.freedesktop.org/archives/hal/2005-December/004120.html) after a fair bit of digging...)

---

### Post by Phil Baxter Jr. on 2007-06-27
> **gostal said:**
> For what it's worth after this very looong :) thread here's a tiny fstab howto. With apropriate options in fstab you can control who's to own the device and what group it should belong to by setting the options uid and gid (user ID and group ID). These are the numbers that you find in /etc/passwd and /etc/group. In /etc/passwd the first number is uid and the second gid. In /etc/group there is only one and that's gid. If these options are not set then by default root is used for both.An easy way of finding uid and gid for a user logged in is to issue the following command in a terminal window:```
id
``` 

Read and write permissions are set by the option umask provided that the device is mounted with the options rw as opposed to ro which indicates that the divice will be read-only no matter what the umask says. The umask consists of three octal numbers that work exacly the opposite way compared  chmod. The numbers controlling permissions are:

read		4
write		2
execute		1

Using chmod you would set the permissions by adding whatever numbers you want so that read and execute would be 5 and write and execute would be 3 (I can't imagine why anyone would want to be able to write but not read but logically that's how it works:D ). For umask it's the other way around so that 5 would mean that read and execute are not allowed and a umask of 7 means that you can't do a thing.

Example fstab line for a FAT formatted device:

```
/dev/device /mnt/mountpoint vfat rw,user,uid=1000,iocharset=iso8859-1,umask=007 0 0
```


device=hdb3 - 3rd partion on hdb i.e. second IDE hard drive 
device=sda1 - 1st partion on a scsi drive or a usb storage medium.
vfat - filesystem type
user - allows users to mount and umount if they are members of group users which users are not by default
iocharset - option controlling char encoding and byte interpretation. By default iocharset=utf8 is normally used but this does not go well with FAT or at least that used to be the case.

The owner of the device has uid=1000 and since gid is not set the group will default to root (gid=0 normally). The umask setting 007 will grant full permissions(read,write,execute) to owner and group whereas world can do nothing. Note that the device will have to be mounted with read/write permissions (rw) for the umask setting to have any effect for owner and group.

The two zeros at the end of the line indicate that the filesystem should neither be checked nor dumped in the event of a system hangup.
 
USB storage media should normally automount if they can be correctly identified by the hal daemon. Making an fstab entry for the device means that it cannot automount. In Ubuntu the actual mounting is done by pmount if there is no fstab entry. Unfortunately pmount has many mount options hard coded that is you don't get much say. Ohter distros may do things differently by dynamically updating /etc/fstab for instance.

This tiny guide should enable you to set up /etc/fstab so that you can do what you want with the device.

Best wishes
Gösta
Ok, a newcommer to ubuntu here.  Running ubuntu 7.04 on IBM T22, now 27 June 07.  

Have not yet located alternate answers to the USB HDD Ownership for ubuntu 7.04.

How where would I find current information?  And how/where would I get enough mentoring to attempt modifying my recently installed ubuntu 7.04 operated in the external drive slot as a boot HDD removed from the internal HDD containing an OS known as XP-Pro I'd like to totally escape from.    Thanks,   Phil B

---

### Post by Fíona on 2007-07-15
I am also having problems trying to copy files to my usbdisk (stick). 

Some info:

/etc/fstab-
/dev/sda1       /media/usbdisk  auto    rw,user,noauto  0       0

/etc/mtab-
/dev/sda1 /media/usbdisk vfat rw,noexec,nosuid,nodev,user=fiona 0 0

fiona@newone:/media$ ls -la
drwxr-xr-x  4 fiona fiona 16384 1970-01-01 01:00 usbdisk
drwxr-xr-x  2 root  root   4096 2007-07-15 09:34 usbdisk-1

Why there are 2 entries for usbdisk, I don't know; something to do with pmount maybe?

Can anyone enlighten me as to how I can have "normal" access to my usbstick?

---

### Post by Gary.M on 2007-07-21
May I offer this experience?

[http://ubuntuforums.org/showthread.php?p=3059660#post3059660](http://ubuntuforums.org/showthread.php?p=3059660#post3059660)

I will post further as I try various USB drives I have with this

---

### Post by Fíona on 2007-07-24
Hi Gary, thanks for the tip. I've had a look at the thread suggesting installing ntfs-3g. I run into a problem installing the packages though, I cannot authenticate the packages in spite of using the following command:
wget  [http://flomertens.free.fr/ubuntu/givre_key.asc](http://flomertens.free.fr/ubuntu/givre_key.asc) -O- | sudo apt-key add -

and  am therefore reluctant to continue the installation.

I admit to not understanding this use of keys very well. 
Will anyone advise how this works?

---

### Post by whereareyoutakingme on 2007-07-24
this is quite strange, i tried the howto: posted just above and i was able to get my external HD working.  However, i was unable to figure out which one was actually my external HD (i.e. sda, sdb, sdb2, or sdc)...i just tried all of them until one seemed to work.  but when i noticed that it didn't matter which one i used in the new line i added to fstab (the one referenced in the howto above) ....the USB external HD still worked. and sure enough when i deleted the line completely, it still worked.  this leads me to believe that it was working all along, however i know for a fact that yesterday i had no permissions to write to the external HD because i tried it several times, with and without using sudo nautilus to copy/paste files.

so my question is this...
I am still trying to get my USB thumbdrive to mount, is it recognized in Computer but when i open it i get a message saying that this device can't be mounted, probably because there is no media in the drive.  How do I know which one of the sda, sdb, sdb1, or sdc points to my USB thumbdrive or my internal NTFS HD, because i am still trying to get both of them working with full read/write access?  ps. - the internal NTFS HD is a separate HD from the one on which Ubuntu is installed.

also...if i figure out which of the sda, sdb, sdb1 and sdc point to which drive, will that howto guide work for mounting both the thumbdrive and the internal HD?

---

### Post by Gary.M on 2007-07-24
> **Fíona said:**
> Hi Gary, thanks for the tip. I've had a look at the thread suggesting installing ntfs-3g. I run into a problem installing the packages though, I cannot authenticate the packages in spite of using the following command:
wget  [http://flomertens.free.fr/ubuntu/givre_key.asc](http://flomertens.free.fr/ubuntu/givre_key.asc) -O- | sudo apt-key add -

and  am therefore reluctant to continue the installation.

I admit to not understanding this use of keys very well. 
Will anyone advise how this works?

I just installed it using the aptitude package manager in system. Synaptic would do it too. Just located the ntfs-3g driver and chose install. Bingo. Done.

---

