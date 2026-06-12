---
title: "Can't write or delete files"
date: 2010-01-29
forum: Hardware
---

### Post by savaan on 2010-01-29
I've been going smoothly along with my Ubuntu Karmic, but just out of the blue last night I was trying to copy a downloaded driver onto my flash drive. It wouldn't copy...wouldn't write to the drive. I tried to delete something from the flash drive and got this: 

Error stating file '/media/A8E1-329D/madwifi-0.9.4/ath': Input/output error

This happens whether I'm using a small 500mb thumb drive or my 250gig USB removeable drive. They won't allow a copy and paste...the paste feature is simply unavailable and in gray. The drive USED to get plugged in and named "500mb drive" or something like that, but now when I plug it in, its auto-named "A8E1-329D"...and won't allow deletions or pastes. It sounds like a problem with permissions, so I went there. In the permissions tab all it has is:
"The permissions of A8E1-329D could not be determined"

I have NO clue what I may have done...I haven't been poking around resetting everything because I'm still new :) Any help?

---

### Post by ajgreeny on 2010-01-29
with the drive attached run ```
ls -l
``` in terminal and report back here what you see.

---

### Post by savaan on 2010-01-29
OK..here's what I have:

total 48
drwxr-xr-x  2 techbot techbot 4096 2010-01-28 10:00 Desktop
drwxr-xr-x  7 techbot techbot 4096 2010-01-28 09:21 Documents
drwxr-xr-x  3 techbot techbot 4096 2010-01-29 08:55 Downloads
-rw-r--r--  1 techbot techbot  167 2010-01-20 15:50 examples.desktop
drwxr-xr-x  5 techbot techbot 4096 2010-01-22 16:59 kdenlive
drwxr-xr-x  4 techbot techbot 4096 2010-01-20 19:52 LimeWire
drwxr-xr-x 29 techbot techbot 4096 2010-01-23 13:11 Music
drwxr-xr-x  7 techbot techbot 4096 2010-01-28 10:00 Pictures
drwxr-xr-x  2 techbot techbot 4096 2010-01-20 15:57 Public
drwxr-xr-x  2 techbot techbot 4096 2010-01-20 15:57 Templates
drwxrwxr-x  2 techbot techbot 4096 2010-01-23 09:28 Ubuntu One
drwxr-xr-x  2 techbot techbot 4096 2010-01-23 15:31 Videos


Would you mind telling me what that command is? I'm still new, so everything you guys are telling me I make note of for future reference :)

---

### Post by BbUiDgZ on 2010-01-29
> **savaan said:**
> OK..here's what I have:

total 48
drwxr-xr-x  2 techbot techbot 4096 2010-01-28 10:00 Desktop
drwxr-xr-x  7 techbot techbot 4096 2010-01-28 09:21 Documents
drwxr-xr-x  3 techbot techbot 4096 2010-01-29 08:55 Downloads
-rw-r--r--  1 techbot techbot  167 2010-01-20 15:50 examples.desktop
drwxr-xr-x  5 techbot techbot 4096 2010-01-22 16:59 kdenlive
drwxr-xr-x  4 techbot techbot 4096 2010-01-20 19:52 LimeWire
drwxr-xr-x 29 techbot techbot 4096 2010-01-23 13:11 Music
drwxr-xr-x  7 techbot techbot 4096 2010-01-28 10:00 Pictures
drwxr-xr-x  2 techbot techbot 4096 2010-01-20 15:57 Public
drwxr-xr-x  2 techbot techbot 4096 2010-01-20 15:57 Templates
drwxrwxr-x  2 techbot techbot 4096 2010-01-23 09:28 Ubuntu One
drwxr-xr-x  2 techbot techbot 4096 2010-01-23 15:31 Videos


Would you mind telling me what that command is? I'm still new, so everything you guys are telling me I make note of for future reference :)

it lists everything on said directory and shows permissions and owner and group.

do it again (after drive is in)with this path
```
ls -l /media
```

edit: see [here](http://www.columbia.edu/acis/rad/unixcmds/ls.html) for info on the ls command

---

### Post by savaan on 2010-01-29
total 12
drwx------ 8 techbot techbot 4096 1969-12-31 18:00 A8E1-329D
lrwxrwxrwx 1 root    root       6 2010-01-20 15:18 cdrom -> cdrom0
drwxr-xr-x 2 root    root    4096 2010-01-20 15:18 cdrom0
drwxr-xr-x 2 root    root    4096 2010-01-23 08:59 data


I don't know how I would have lost permissions, thats not something that I've even messed with. I just plug and move items around on the drives

Again, just tried to delete something on the small flash drive and got this: 

Error stating file '/media/A8E1-329D/madwifi-0.9.4/ath': Input/output error




==========

As I'm sitting here trying to move data from my 250g removable, I got this ominous looking thing...

Error mounting: mount exited with exit code 13: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Failed to read $UpCase, unexpected length (-1 != 131072).
Failed to mount '/dev/sdb1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

---

### Post by ajgreeny on 2010-01-29
Whoops, sorry!

I forgot the /media in my first post.
The permissions listing for your usb drive
drwx------ 8 techbot techbot 4096 1969-12-31 18:00 A8E1-329D 
looks exactly the same as when my usb stick is attached
drwx------ 3 andrew root 81920 1970-01-01 01:00 Kingston512

Could it be the folders or partitions on the drive that are not correct in some way.
Try ```
ls -lR /media
``` with the drive attached.  This will give the permissions on all folders and files on the disk.

---

### Post by savaan on 2010-01-29
running that comman gave me the permissions for everything on that flash drive. i logged into root to try to change the  permissions per file, but I still get an error saying it cannot be changed. 
When I go to the desktop and right click to change permissions on the mounted flash drive itself, I get a message on the permissions tab that says permissions can't be determined.

Just out of curiosity, is there a way to set back to default on permissions? it appears that something got out of whack along the past few days

---

### Post by ajgreeny on 2010-01-29
Have a look at the manuals for chown and chmod which may help,though I suspect not.  I think it may be something to do with the filesystem on the drive, which is what fat32, ntfs, ext3?  If it's fat32 as many are, or even fat16, there should be no permissions on the files on the drive, as fat can not deal with such things, and only the mount point folder would have linux permissions set.

If all else fails, why not just copy the files to your linux file system, using "sudo cp - - -" if needed, and there you can reset any permissions that are incorrect.  You can then just reformat the usb drive to whatever system you want.

---

### Post by savaan on 2010-01-30
That's exactly my problem though. I can't write to or copy from the drive. Luckily, before all this started I copied everything to my system. I formatted that flash drive and now I'm able to work with it just fine. I think that solved the problem...whatever it was ;)

---

### Post by savaan on 2010-02-01
Nope...false alarm. I reformatted the card and it appeared just fine on my desktop. However, once I unplugged it, it won't mount automatically again.

---

### Post by chewearn on 2010-02-01
Did you right-click on the drive, then select "Unmount volume" before unplugging it?

---

### Post by savaan on 2010-02-01
I don't believe I did. I don't think I'd been doing that at all...it just auto-detected and would show up on my desktop. Should I be unmounting each time?

---

### Post by chewearn on 2010-02-01
> **savaan said:**
> I don't believe I did. I don't think I'd been doing that at all...it just auto-detected and would show up on my desktop. Should I be unmounting each time?

Yes, you should unmount every time before unplug.  It's same as in Windows, where you need to click "Safely remove".

---

### Post by savaan on 2010-02-01
Guess I thought it was like XP Pro...always just plugged and unplugged. How would I go about getting this drive to mount again? :(

---

### Post by chewearn on 2010-02-01
Even with WinXP, it good practice to click on "safely remove" before unplugging a USB storage, else you risk data loss or corruption.

---

To find out what's wrong, we need to see if there is any error message in the log.

First, plug in the drive.  Wait around 10 sec for the detection to complete.  Then run this command.
```
dmesg | tail -n 20
```The command will output the last 20 lines from the kernel.  It should tell us of error.  Copy/paste the output to this thread, enclosing it between [noparse]```
 
```[/noparse] tag.

---

### Post by savaan on 2010-02-01
Here's the output...

```
[163523.308056] usb 2-4: device descriptor read/64, error -62
[163523.572045] usb 2-4: new full speed USB device using ohci_hcd and address 9
[163523.752241] usb 2-4: device descriptor read/64, error -62
[163524.036051] usb 2-4: device descriptor read/64, error -62
[163524.316118] usb 2-4: new full speed USB device using ohci_hcd and address 10
[163524.728566] usb 2-4: device not accepting address 10, error -62
[163524.908046] usb 2-4: new full speed USB device using ohci_hcd and address 11
[163525.316081] usb 2-4: device not accepting address 11, error -62
[163525.316112] hub 2-0:1.0: unable to enumerate USB device on port 4
[173547.720011] usb 2-4: new full speed USB device using ohci_hcd and address 12
[173547.904012] usb 2-4: device descriptor read/64, error -62
[173548.188008] usb 2-4: device descriptor read/64, error -62
[173548.468009] usb 2-4: new full speed USB device using ohci_hcd and address 13
[173548.648008] usb 2-4: device descriptor read/64, error -62
[173548.932008] usb 2-4: device descriptor read/64, error -62
[173549.212009] usb 2-4: new full speed USB device using ohci_hcd and address 14
[173549.620007] usb 2-4: device not accepting address 14, error -62
[173549.796009] usb 2-4: new full speed USB device using ohci_hcd and address 15
[173550.204012] usb 2-4: device not accepting address 15, error -62
[173550.204019] hub 2-0:1.0: unable to enumerate USB device on port 4

```

Thanks for all the help. Sorry for so many questions in here, but I'm totally OFF Windows and trying to learn a new OS :)

---

### Post by chewearn on 2010-02-01
From the error message, the kernel is not even able to read the USB identifier.
It appears likely to be failing hardware.  Well, that's my suspicion.

A bit of troubleshooting is required to find the root cause.

1. Drive itself failing
If you have a second PC, try the drive on it; if it works this will eliminate the drive as the cause.

2. USB port failing
Try the drive on another USB port, both the one next to the suspected failing port (if any) and another port further apart.

In the first scenario, adjacent ports usually share the same USB controller.  In the second scenario, another USB port further away (e.g. USB in front vs USB at the back of a PC) has different USB controller.

Try another device, like a USB mouse on the same port.  Is it working?

3. Cabling?
Sometimes, the contacts on the cabling can be worn out.  Try another cable, if you can find one.

4. Self-powered vs Bus powered
Flash drive is bus powered.  Smaller 2.5" drive can be bus powered but sometimes, the PC USB power could dip when the drive spin up or down, and cause problem.  If the drive has external power, trying using it.

I have also encounter poor quality bus-powered USB hub, which draw too much power and causes problem.

---

### Post by savaan on 2010-02-01
Well now I feel dumb...I'm not computer illiterate by any means...I build my own boxes. I've had this drive for some time and know it works on my wifes comp, so I just assumed that Ubuntu wasn't mounting it properly... turns out its a bad USB port on my box :) Thanks for that suggestion! Seems I can see/read and write to it now. I'll make sure to unmount in the future!

---

