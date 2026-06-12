---
title: "problem ejecting flash drive"
date: 2014-07-31
forum: Hardware
---

### Post by VitasLoWang on 2014-07-31
Hello, I seem to have either found a bug or missing feature in Ubuntu, or my new 64GB flash drive with NTFS started to misbehave.
I have copied about 400MB of photos onto it using my ubuntu 14.04 with unity. I clicked the eject icon in nautilus (the little horizontal line with a triangle above). It disappeared - so I thought it is ok, done, written and safe to be removed. I pulled the drive out and got an error! From some reason there is no easy way in Ubuntu to do fsck (I would expect it to be in drive properties as it is in windows), so I did a checkdisk in windows. It fixed some errors. Then I did the same - copied some photos from my linux machine onto the drive, clicked the eject icon, and watched syslog...no messages appeared in like 30 seconds. So I pulled the drive out and immediatelly got a lot of I/O errors in syslog! WTH is this behavior?

Jul 31 14:17:34 T420-vitas udisksd[3285]: Cleaning up mount point /media/vitas/vitas_flash (device 8:32 is not mounted)
***here I pulled the drive out***
Jul 31 14:18:02 T420-vitas kernel: [17732.235841] usb 1-1.2: USB disconnect, device number 8    
Jul 31 14:18:02 T420-vitas kernel: [17732.242640] sd 10:0:0:0: [sdc] Unhandled error code
Jul 31 14:18:02 T420-vitas kernel: [17732.242644] sd 10:0:0:0: [sdc]  
Jul 31 14:18:02 T420-vitas kernel: [17732.242646] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
Jul 31 14:18:02 T420-vitas kernel: [17732.242647] sd 10:0:0:0: [sdc] CDB: 
Jul 31 14:18:02 T420-vitas kernel: [17732.242648] Write(10): 2a 00 03 7c 3a 00 00 00 f0 00
Jul 31 14:18:02 T420-vitas kernel: [17732.242653] blk_update_request: 42 callbacks suppressed
Jul 31 14:18:02 T420-vitas kernel: [17732.242655] end_request: I/O error, dev sdc, sector 58472960
Jul 31 14:18:02 T420-vitas kernel: [17732.242657] quiet_error: 42 callbacks suppressed
Jul 31 14:18:02 T420-vitas kernel: [17732.242658] Buffer I/O error on device sdc, logical block 7309120
Jul 31 14:18:02 T420-vitas kernel: [17732.242659] lost page write due to I/O error on sdc
Jul 31 14:18:02 T420-vitas kernel: [17732.242662] Buffer I/O error on device sdc, logical block 7309121
Jul 31 14:18:02 T420-vitas kernel: [17732.242663] lost page write due to I/O error on sdc
Jul 31 14:18:02 T420-vitas kernel: [17732.242664] Buffer I/O error on device sdc, logical block 7309122
Jul 31 14:18:02 T420-vitas kernel: [17732.242665] lost page write due to I/O error on sdc
Jul 31 14:18:02 T420-vitas kernel: [17732.242666] Buffer I/O error on device sdc, logical block 7309123
Jul 31 14:18:02 T420-vitas kernel: [17732.242667] lost page write due to I/O error on sdc
Jul 31 14:18:02 T420-vitas kernel: [17732.242668] Buffer I/O error on device sdc, logical block 7309124
Jul 31 14:18:02 T420-vitas kernel: [17732.242669] lost page write due to I/O error on sdc
Jul 31 14:18:02 T420-vitas kernel: [17732.242670] Buffer I/O error on device sdc, logical block 7309125
Jul 31 14:18:02 T420-vitas kernel: [17732.242671] lost page write due to I/O error on sdc
Jul 31 14:18:02 T420-vitas kernel: [17732.242672] Buffer I/O error on device sdc, logical block 7309126
Jul 31 14:18:02 T420-vitas kernel: [17732.242673] lost page write due to I/O error on sdc
Jul 31 14:18:02 T420-vitas kernel: [17732.242674] Buffer I/O error on device sdc, logical block 7309127
Jul 31 14:18:02 T420-vitas kernel: [17732.242675] lost page write due to I/O error on sdc
Jul 31 14:18:02 T420-vitas kernel: [17732.242676] Buffer I/O error on device sdc, logical block 7309128
Jul 31 14:18:02 T420-vitas kernel: [17732.242676] lost page write due to I/O error on sdc
Jul 31 14:18:02 T420-vitas kernel: [17732.242678] Buffer I/O error on device sdc, logical block 7309129
Jul 31 14:18:02 T420-vitas kernel: [17732.242678] lost page write due to I/O error on sdc
Jul 31 14:18:02 T420-vitas kernel: [17732.244669] sd 10:0:0:0: [sdc] Unhandled error code
Jul 31 14:18:02 T420-vitas kernel: [17732.244672] sd 10:0:0:0: [sdc]  
Jul 31 14:18:02 T420-vitas kernel: [17732.244673] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
Jul 31 14:18:02 T420-vitas kernel: [17732.244674] sd 10:0:0:0: [sdc] CDB: 
Jul 31 14:18:02 T420-vitas kernel: [17732.244675] Write(10): 2a 00 03 7c 3a f0 00 00 f0 00
Jul 31 14:18:02 T420-vitas kernel: [17732.244680] end_request: I/O error, dev sdc, sector 58473200
Jul 31 14:18:02 T420-vitas ntfs-3g[17538]: Unmounting /dev/sdc (vitas_flash)
Jul 31 14:18:02 T420-vitas udisksd[3285]: Unmounted /dev/sdc on behalf of uid 1000

Can somebody tell me why is there no hourglass cursor or something which would tell me that there is something still happening with the drive and I should not eject it?? I expected that the drive is ready to be ejected when this eject icon disappeares, but apparently this is not the case. And no there never was some tray notification that drive is now safe to be removed. I guess it is a problem of unity, because I think there was a clear message that drive is safe to be removed when I used Cinnamon. Why is it so hard to make it clear for the user when I can eject my flash drive?? I guess it is up to unity devs to answer this :roll: But once again I think - golden microsoft and their GUI :(

---

### Post by VitasLoWang on 2014-07-31
I just tested a different flash drive. When I clicked the eject icon this happened
Jul 31 15:07:32 T420-vitas udisksd[3285]: Cleaning up mount point /media/vitas/346C-16DB (device 8:33 is not mounted)
Jul 31 15:07:33 T420-vitas udisksd[3285]: Unmounted /dev/sdc1 on behalf of uid 1000

So there was a one second pause after I clicked and it probably wrote the cache and this message "Unmounted" means drive is safe to be removed. Why are there no notifications in Unity which would announce this to user? Is this normal?

---

### Post by grahammechanical on 2014-07-31
In Ubuntu when we put in a USB memory stick an icon will appear in the Launcher and File manager will show it in its lists of devices. When we right click the launcher icon or the label in file manager we will get two options - Eject which will unmount but allow for us to remount the USB memory stick again for future access, and Safely Remove which will remove the icon from the Launcher and its listing from File Manager. Now we can safely remove the USB memory stick from the USB port. The disappearance of the icon is the notification that it is safe to remove the USB memory stick.

When I select Eject when right clicking the launcher icon I do get a notification at the top right of the screen - "The drive has been successfully ejected."

Regards.

---

### Post by VitasLoWang on 2014-07-31
Hello, are you citing this from somewhere? What version of Ubuntu and Unity do you use that you have this extra option in nautilus when you right click on the device? I have only "eject" in the context menu. Do you have the small line and triangle icon next to a device icons? What happens if you click that? Unfortunatelly I cannot make a screenshot, because 14.04 apparently broke print screen key function :-\
vitas@T420-vitas:~$ unity --version
unity 7.2.1

Run this command please and tell me your Unity version

---

### Post by VitasLoWang on 2014-08-01
So I guess this is a wrong forum to post such advanced questions :-\

---

### Post by Mike_Walsh on 2014-08-01
Hi there.

It would appear that you are equating the Windows "safe to remove" function with a similar one in Ubuntu!

In all my years of using flash drives under Windows XP, I never once used that function. I simply made sure that write caching was disabled when initially setting up a USB...and thereafter simply unplugged the drive when I wanted to remove it.

I do precisely the same in Ubuntu.....and have yet to suffer ANY loss of data.

And as for being the wrong forum to post such an "advanced" question.....I beg to differ. The sum total of knowledge possessed by the members of this forum is WAY beyond anything any single individual could be expected to know; which is as it should be. 

Graham is a veritable fount of knowledge when it comes to Linux & Ubuntu; I've always found his advice to be eminently sensible , IF you take the time to read his posts through from start to finish.

ANYTHING you want to know about Linux in general, and Ubuntu in particular, simply post your query on here.....someone, sooner or later, WILL come up with a suggestion that will DEFINITELY help.

But please do NOT come on here and start "slagging off" the forum members for not answering you. That is NOT the way to obtain help; and in any case, people tend to view, and reply to, posts which are of interest to them, and where they think they may be able to help. The members of the Ubuntu forums are an extremely friendly, helpful bunch of very knowledgeable individuals...and politeness never hurt anyone. Such an attitude will, I feel, be given the consideration it deserves..!

In any case; why on EARTH are you using NTFS in Ubuntu.....or are you dual booting with Windows?

Ubuntu may LOOK similar in many ways to Windows; but it is, most decidedly, NOT Windows.

Regards,

Mike.

---

### Post by VitasLoWang on 2014-08-02
> **Mike_Walsh said:**
> Hi there.

It would appear that you are equating the Windows "safe to remove" function with a similar one in Ubuntu!

I am sorry I just want to know how it works. [COLOR=#000000]grahammechanical said he has "safely remove" there but this is something I have never seen, so I simply ask how did this function get there, but nobody seems to know :-][/COLOR]
> **Mike_Walsh said:**
> 
In all my years of using flash drives under Windows XP, I never once used that function....
Interesting. That is right this can work, but I think you would have to set this option for every flash drive individualy right? I am not sure if there is a global settings. And there is also another problem with this approach - considerably lower performance especially when using usb hard drives and not just flash drives. But anyway, I don't know how to disable cached write in Ubuntu - care to share your knowledge about this please?
> **Mike_Walsh said:**
> 
And as for being the wrong forum to post such an "advanced" question.....I beg to differ. The sum total of knowledge possessed by the members of this forum is WAY beyond ...
I really appreciate your effort, but don't you think it would be much simpler if you just answered me at least some of the things I asked? ;)
> **Mike_Walsh said:**
> 
In any case; why on EARTH are you using NTFS in Ubuntu.....or are you dual booting with Windows?

Man you may be surprised but I frequently use my flash drives to move data between not only linux computers ;) And yes I do have dual boot Ubuntu/windows on my work computer and I use several other computers with various windows versions on them. But I think it kind of defeats the purpose of a flash drive if you don't ever put it to some other pc then yours :D Ext4 is not natively supported in Windows so NTFS is more practical in this case.

---

### Post by Mike_Walsh on 2014-08-02
Hello, Vitas.

Sorry if I appeared to be 'sounding off' at you; but there are a fair number of Windows users on these forums who appear to be under the impression that they can DEMAND answers, and have every right to do so. They don't always seem to realise that almost the entire Linux community are enthusiastic volunteers; it's not like Microsoft where, having paid for the O/S, you tend to feel you have a right to backup and support!

Anyway; to the flashdrives. I myself am fairly new to Linux, although I can date my interest in, and usage of, computers, back to the days of the Commodore 64 and the original Sinclair ZX80. I have myself used flashdrives for data transfer between machines for many years (this was before the days of Bluetooth, and, latterly, the "cloud".)

Actually, as far as I am aware, every USB removable storage device (if flash memory-based) is always set-up at the factory with write-caching disabled by default. If you wish to enable it, you must voluntarily make the effort to do so. I don't think write-caching is reckoned to be particularly effective in flash memory (something to do with the wear-levelling algorithms they use? I could be wrong on this point...)

IF, however, your removable storage device is a hard drive (as with my own Seagate external Expansion drive), then write caching is ENABLED by default, as hard drives always work more efficiently with the feature working. It cuts down on the number of read/write operations, which in its turn, obviously, extends the life of the drive...

Upon investigation, I, like yourself, appear NOT to have the 'safely remove' option when clicking the triangle to the right of the drive listing. However, if you select the drive, right-click, and select 'Unmount', that will perform the same job. Unmounted volumes in Linux are always safe to remove and/or otherwise play around with, without the fear of data loss.

It could be that Graham has the option because he is currently one of the testers of the development release (that is to say, 'Utopic Unicorn'), which will be generally released in October. It may well be an option that IS available when the new version is released.

I guess we will have to wait and see.

Regards,

Mike.

BTW, at present 3 of my flashdrives are occupied by different versions of Puppy Linux; so these don't get used for data transfer. They are all plugged into a hub, and I merely select whichever one I want upon boot..!

---

### Post by Mike_Walsh on 2014-08-02
Hello again, Vitas.

If it's of any interest to you, these links may explain things a little bit:-

[http://arstechnica.com/civis/viewtopic.php?t=301957](http://arstechnica.com/civis/viewtopic.php?t=301957)

[http://www.mydigitallife.info/speed-up-and-optimize-usb-drive-speed-performance-by-enabling-write-caching/](http://www.mydigitallife.info/speed-up-and-optimize-usb-drive-speed-performance-by-enabling-write-caching/)

Hope that helps.


Regards,

Mike.

---

### Post by VitasLoWang on 2014-08-04
Thank you for some relevant info finally :) But I do not have "unmount" option when right clicking on a flash drive. There is only eject, which I believe is the same thing as clicking the little triangle... which in my case does not do any visible notification when and if done :-\
 From my experience the write caching or some sort of it must be enabled in windows 7, because it happened frequently to me that files written to a flash drive were missing if not safely removed... Regarding utopic unicorn - that is possible, but why I guess Graham is too busy to confirm that.
Will check those links. BTW ntfs formatted flash drive can be sped up also by disabling timestamp updating...
[http://technet.microsoft.com/en-us/library/cc785435.aspx](http://technet.microsoft.com/en-us/library/cc785435.aspx)
I am not sure if it is a system wide settings or drive related though...

---

