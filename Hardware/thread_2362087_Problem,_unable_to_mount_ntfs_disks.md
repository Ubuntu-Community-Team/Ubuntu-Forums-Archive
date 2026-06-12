---
title: "Problem, unable to mount ntfs disks"
date: 2017-05-24
forum: Hardware
---

### Post by Vic_Paine on 2017-05-24
I'm unable to mount the Win 10 disks in my PC when in Ubuntu, Win 10 and 7 run with no problems.  Error message below.  Do I need to do something in Win or Uuntu to sort this problem?  Check disk reports no errors.
```
Error mounting /dev/sdb3 at /media/vic/Data: Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000" "/dev/sdb3" "/media/vic/Data"' exited with non-zero exit status 14: The disk contains an unclean file system (0, 0).
Metadata kept in Windows cache, refused to mount.
Failed to mount '/dev/sdb3': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.
```
Win is always shut down correctly, although I've noticed there is always a memory error when shutting down on all 3 Win 10 PC's that I use at various times.

---

### Post by sp40140 on 2017-05-24
New versions of windows don't actually shutdown. They go in deep sleep mode. I think there are settings to make windows do proper shutdown. 
A word of caution. It is not good idea to mount the windows boot drive. It's very risky. You will potentially break that install.
If you have data you want to access, then create a new partition for data only.

---

### Post by Vic_Paine on 2017-05-24
Thank you your reply, since I lost all my data about 12 years ago during a windows "event" I have always kept data on a completely different drive.  Looks as though I need to do some research with windows shutdown.

---

### Post by yancek on 2017-05-24
Windows 8 & 10 use hibernation/fastboot by default.  If you want to access a "data" partition on windows from Ubuntu or any Linux, you need to have hibernation/fastboot turned off.  The methods vary, there is a way in windows and should be in the BIOS also.  Don't do anything to system files on windows from Ubuntu or Linux, only data.

---

### Post by Chanath on 2017-05-24
> **Vic_Paine said:**
> I'm unable to mount the Win 10 disks in my PC when in Ubuntu, Win 10 and 7 run with no problems.  Error message below.  Do I need to do something in Win or Uuntu to sort this problem?  Check disk reports no errors.
```
Error mounting /dev/sdb3 at /media/vic/Data: Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000" "/dev/sdb3" "/media/vic/Data"' exited with non-zero exit status 14: The disk contains an unclean file system (0, 0).
Metadata kept in Windows cache, refused to mount.
Failed to mount '/dev/sdb3': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.
```
Win is always shut down correctly, although I've noticed there is always a memory error when shutting down on all 3 Win 10 PC's that I use at various times.

Have look here; [https://www.howtogeek.com/262325/why-is-windows-hibernating-instead-of-fully-shutting-down/](https://www.howtogeek.com/262325/why-is-windows-hibernating-instead-of-fully-shutting-down/)
That'd stop Windows from going to sleep.

---

### Post by Vic_Paine on 2017-05-25
> **Chanath said:**
> Have look here; [https://www.howtogeek.com/262325/why-is-windows-hibernating-instead-of-fully-shutting-down/](https://www.howtogeek.com/262325/why-is-windows-hibernating-instead-of-fully-shutting-down/)
That'd stop Windows from going to sleep.

Looked at that, already done it but rechecked. Definitely correct but still can't access data disk. Somewhat annoying because I've become used to accessing my files from either OS but can only access from windows now.  Some things are easier in win whilst others are easier in Linux (for me anyway) but I have to copy a file to a USB in Win to access it from Linux on the same PC, crazy.

---

### Post by sp40140 on 2017-05-25
Either Windows or some application running in windows is locking that drive/partition. Boot into windows and just before shutting down, eject / safely remove the drive. And boot into linux and try it.

---

### Post by kagashe on 2017-05-25
Shutdown Windows using following command
```
Shutdown /s /t 0
```

You can type the command in Run box.

Kamalakar

---

### Post by Vic_Paine on 2017-05-25
> **kagashe said:**
> Shutdown Windows using following command
```
Shutdown /s /t 0
```

You can type the command in Run box.

Kamalakar

Well done that works, thank you.
Takes twice as long to load but I can live with that to make things work as they should.

---

### Post by kagashe on 2017-05-25
I had discovered this when I installed Ubuntu in dual boot with Windows 8.1 on my Laptop. You can read about it on my [blog]("https://kagashe.blogspot.in/2014/12/installation-of-ubuntu-14041-in-dual.html").

Kamalakar

---

