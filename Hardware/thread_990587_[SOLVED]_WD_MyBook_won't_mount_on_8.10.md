---
title: "[SOLVED] WD MyBook won't mount on 8.10"
date: 2008-11-22
forum: Hardware
---

### Post by TriplePlay2425 on 2008-11-22
Hey, I just installed Ubuntu last night (just decided to try it out for no particular reason  :D ) and I've been trying to get most of it set up.  Just now I plugged in my Western Digital 500GB USB external hard drive.  When I choose it under 'Places', it responds with an error message saying:
> Error
Unable to mount 500.1 GB Media
DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

When I first got it I formatted it to NTFS (never thinking I might use Linux).  I have nearly 300GB of data on it (and nowhere else to back it up), so I can't format it to FAT32.

I'm new to all distros of Linux, so if you think there's any chance of me not understanding something, I probably won't  :p


A bit off-topic:  I'm running an HP dv6000 laptop which has a Broadcom wireless device, which I've heard that the Broadcom devices aren't very Linux-friendly.  I want to know if I should post a new thread in this section (Hardware & Laptops) or if I should post that in the Networking & Wireless section.  Or better yet, if someone happens to know how to do that for me real quick here.
To be quite honest, it may not work anyways.  A few days ago it randomly stopped working for Vista (I am dual booting Ubuntu with Vista [for now at least]).  However, it shows the orange light to signify that it is off, but when it works properly the light should turn blue when I turn the switch on to enable it, but it stopped working for some reason.  I don't know if it's a hardware problem or if something went wrong.  It happened after my laptop bluescreened after resuming from hibernation (which seems to be kind of flaky on my laptop for some reason).

---

### Post by cprofitt on 2008-11-22
just curious...

Did you 'safely remove' it from XP/Vista? If not that will cause issues.

Have you tried reformatting it via gparted?

---

### Post by cariboo on 2008-11-22
What is the output of dmesg when you plug the device in? To check, open a Applications-->Accessories-->Termianl and type:

```
tail -n 10 /var/log/dmesg
```

This will print out the last 10 lines of dmesg, and will give you an indication of what the problem is. Paste the output in your next post.

Jim

---

### Post by TriplePlay2425 on 2008-11-23
> **PrivateVoid said:**
> just curious...

Did you 'safely remove' it from XP/Vista? If not that will cause issues.

Have you tried reformatting it via gparted?

Well, when I choose the "safely remove" option in XP/Vista, it always says that the device is busy, when it is most definitely not.  I cut access from the internet, close all bittorrent programs, close the Windows Sidebar, close all open applications, go into task manager and close any unnecessary tasks, and then try to safely remove it and it still says that it cannot stop the device because it is busy.  So before I unplug it, I hold the button on the front for about 5 seconds to turn the device off.  Then I unplug it.

And no, reformatting is not an option.  I have almost 300GB of data on there and nowhere else to back it up while it formats.  Technically I could put it on a bunch of DVDs, but that would take forever and be a large stack of DVDs.  If that was the only way I would rather just have to reboot into Vista to access it.


> **cariboo907 said:**
> What is the output of dmesg when you plug the device in? To check, open a Applications-->Accessories-->Termianl and type:

```
tail -n 10 /var/log/dmesg
```

This will print out the last 10 lines of dmesg, and will give you an indication of what the problem is. Paste the output in your next post.

Jim

Here you go:
```
[   17.179324] HDA Intel 0000:00:10.1: setting latency timer to 64
[   17.241278] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input11
[   17.276503] usbcore: registered new interface driver snd-usb-audio
[   18.539706] lp: driver loaded but no devices found
[   18.707422] Adding 602396k swap on /dev/sda6.  Priority:-1 extents:1 across:602396k
[   19.288768] EXT3 FS on sda5, internal journal
[   20.442670] type=1505 audit(1227409998.124:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4672
[   20.663948] type=1505 audit(1227409998.344:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4677
[   20.664190] type=1505 audit(1227409998.344:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4677
[   20.849527] ip_tables: (C) 2000-2006 Netfilter Core Team
```

---

### Post by cariboo on 2008-11-23
Was that output from right after you plugged the drive in? If so then your drive isn't being detected at all. Is there any way you can remove the drive from the enclosure and connect directly in a computer? I realize that you have a laptop, but if you can find a desktop to connect it to, then you can determine whether it is the hard drive or the enclosure.

Jim

---

### Post by TriplePlay2425 on 2008-11-23
> **cariboo907 said:**
> Was that output from right after you plugged the drive in? If so then your drive isn't being detected at all. Is there any way you can remove the drive from the enclosure and connect directly in a computer? I realize that you have a laptop, but if you can find a desktop to connect it to, then you can determine whether it is the hard drive or the enclosure.

Jim

No, that output was right after I tried to mount it and got the error.

but no worries, I actually got it to work!  I used:
sudo mount -t ntfs-3g /dev/sdb1 /media/hd-ntfs -o force

It took a lot of searching, but I found that and it worked.  Supposedly it is indeed a bug with not doing the "Safely remove hardware" action when removing it in Windows.

I appreciate your help though  :)

---

