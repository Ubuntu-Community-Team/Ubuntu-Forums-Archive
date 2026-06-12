---
title: "kubuntu 23.10 doesn't recognize external disk"
date: 2023-10-14
forum: Hardware
---

### Post by ksso on 2023-10-14
Hi
just installed kubuntu 23.10, it doesn't recognize an external disk through usb
however, kubuntu 23.04 still recognize it

see screenshot

---

### Post by Rubi1200 on 2023-10-14
What filesystem is being used on the external drive?

---

### Post by ksso on 2023-10-14
Is using ntfs because I need it to work with kubuntu and windows, but I created the partition table with kubuntu 23.04, and it has been  recognized and still is recognized on another laptop with kubuntu 23.04


Similar issues happened (with time, Kubuntu failed to recognize the disk (somehow showing this behavior when I use the disk in another operating system), but Windows still recognize it), but this time it's just the new release that doesn't recognize it.

---

### Post by yancek on 2023-10-15
There are a number of reasons for a problem like this, more so when using different operating systems, filesystems on different compters.

Have you attached the disk to a windows computer, removed it and attached it to 23.04, removed it and attached it to 23.10 with the same results?

Some reasons for this behavior is not properly/safely removing the attached usb, having the ntfs filesystem in a hibernated state and problems with the filesystem itself.  Based on the message in the image you posted, the first thing I would try would be to boot into windows with the disk attached and run chkdsk and see what the results are.  

You might make note of how/when/why this happens.  Does it always happen?  Does it happen only after removing from windows?  Does it happen when you attach it to windows, completely shut down the computer, the start and boot into the Ubuntu 23.10.  Having notes of exactly what happens when and how is going to help you to resolve the problem.  The error in your image has a very large number of possible causes.  Good luck.

---

### Post by ksso on 2023-12-08
> You might make note of how/when/why this happens.  

Does it always  happen?  
No, I just formatted the external disk with kubuntu 23.10, and it went well until I used it in windows, after that, it again doesn't recognize the  external drive

> Does it happen only after removing from windows?  
It seems so, and maybe not for all windows, I am not sure, because I can't try with each windows...

> Does it  happen when you attach it to windows, completely shut  down the computer,  the start and boot into the Ubuntu 23.10.  Having  notes of exactly what  happens when and how is going to help you to  resolve the problem.  The  error in your image has a very large number  of possible causes.  Good  luck.

I just plugged in Kubuntu after using windows, but the message appears and  doesn't allow the loading of the disk. In this case, the disk was  partitioned with kubuntu 23.10

thank you

---

### Post by ksso on 2023-12-09
More info.  With an initial partition of the external disk (ntfs) made with kubuntu 23.10, after using it in windows 10, when using it again in kubuntu23.10 it does not recognize it. However, when I make the initial partition (fast nfts) of the external disk with windows10, I can use it without problem between windows10 and kubuntu 23.10.

---

### Post by oldfred on 2023-12-09
Windows uses fast startup which sets hibernation flag.
Then Linux NTFS driver will not open read/write as if you force write, it is lost when Windows restores from hibernation.
Even if you turn off fast start up in Windows, an update may turn it back on.

Fast Start up off (always on hibernation), note that Windows turns this back on with updates, SHIFT + Shut down button
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[https://www.elevenforum.com/t/turn-on-or-off-fast-startup-in-windows-11.1212/](https://www.elevenforum.com/t/turn-on-or-off-fast-startup-in-windows-11.1212/)
[https://www.makeuseof.com/windows-11-turn-on-or-off-fast-startup/](https://www.makeuseof.com/windows-11-turn-on-or-off-fast-startup/)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)
[https://www.windowscentral.com/how-disable-windows-10-fast-startup](https://www.windowscentral.com/how-disable-windows-10-fast-startup)

---

### Post by ksso on 2023-12-09
Hello
Sorry, I did not check the term, I mean quick format, it is for an external disk, it is not dual boot.
Is just a checking box when you apply format to a external drive, (right click option, for w10)
thank you
[https://www.partitionwizard.com/disk-recovery/quick-format-vs-full-format.html](https://www.partitionwizard.com/disk-recovery/quick-format-vs-full-format.html)

---

### Post by yancek on 2023-12-10
If you are using a drive between systems (windows/Linux), you need to be aware as mentioned above, that some windows updates will turn on hibernation even if the user turned it off.  You also need to be aware that you as the user will neither be asked or notified that this will happen.  In some cases, Secure Boot will also be turned on and windows may set itself to first boot priority in the BIOS firmware (on EFI systems).

Formatting as ntfs with gparted usually works but, if you have a windows system available I would suggest that you always use it for operations like this.  If you don't have windows, why ntfs other than  perhaps to share with other users who use windows 
 
Hibernation on in dual boot systems isn't usually a problem, only when a user tries to write to an ntfs filesystem from Linux.

---

### Post by ksso on 2023-12-10
> Hibernation on in dual boot systems isn't usually a problem, only when a user tries to write to an ntfs filesystem from Linux.
This is not about dual boot, thank you

---

