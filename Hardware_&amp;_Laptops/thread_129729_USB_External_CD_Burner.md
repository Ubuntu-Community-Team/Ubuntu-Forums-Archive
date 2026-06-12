---
title: "USB External CD Burner"
date: 2006-02-14
forum: Hardware &amp; Laptops
---

### Post by aggiechemist on 2006-02-14
I have not been able to burn CDs wih my external USB CD burner.

The model of the burner is a Sony CRX120E, and the name that marketing gave it is "Spressa." This thing is pretty old, but worked fine until I moved the system over to Ubuntu.

The thing auto mounts OK, and I can read data and play CDs with it. The problem is when I try to actually burn with it.

I have tried Graveman, Gnomebaker, and a few others. It seems like the problem is independent of the software interface used. It will start in on the burn session, but as soon as is supposed to start burning, the thing just sort of hangs there and never gets anywhere.

The device does (usually) show up in the cdrecord -scanbus list. But right after a failed burn, the drive is no longer in the scanbus list.

I am pretty much stuck there. I have considered trying to add the drive into the fstab so that I can be sure that programs can always find it, but haven't had much luck at giving it the right name and parameters. This is just about the last thing that is imperfect for me in Ubuntu:???: , and I would love to see if fixed. Any suggestions?

---

### Post by aggiechemist on 2006-02-15
I have done a little more work, and this is what I can add to the last post.

When I put in a disk of data to just read, the system mounts the disk to the /dev/scd0 point mapped to mnt/cdrecorder. That is great.

When I run gnomebaker, it tries to burn with the drive in the location /dev/sg0.

Why are there two different device names? I don't know. I have tried putting both into fstab to see if that helps at all, and it is no good.

Also, I should not that gnomebaker gives lots of interesting errors. One says that it cannot find /mnt/cdrecorder, so I should add it to the fstab. That is why I tried that. It also has problems getting access to the drive, so I find that running it as a root process is neccesary. 

When I put it in the fstab, it never seems to mount anything propoerly. FOr instance, when I try to open the disk it just takes me to my home directory. I don't understand that at all.

Help?

---

### Post by aggiechemist on 2006-02-19
Maybe at least someone could give me some guidance on why the drive sometimes is referred to as scd0 and sometime as sg0, and the sometimes it is some sort of usbfs located at /proc/bus/usb instead of at /media/cdrecorder?

---

