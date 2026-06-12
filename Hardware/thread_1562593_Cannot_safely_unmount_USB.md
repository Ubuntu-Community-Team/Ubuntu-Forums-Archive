---
title: "Cannot safely unmount USB"
date: 2010-08-27
forum: Hardware
---

### Post by kakyoism on 2010-08-27
On lucid,
I save music and video on USB drives and every now and then
after I close media player, I just can't unmount the drive.
The process just hangs forever.

This didn't happen on Hardy.

Any ideas??

---

### Post by kakyoism on 2010-08-27
tried to restart the system but it hangs because of the USB problem, as shown in the kern.log below 

```

Aug 27 20:52:08 kakyo-desktop kernel: [329912.777317] usb 2-5.2: reset high speed USB device using ehci_hcd and address 13
Aug 27 20:52:39 kakyo-desktop kernel: [329943.689043] ===>rt_ioctl_giwscan. 9(9) BSS returned, data->length = 1097
Aug 27 20:53:14 kakyo-desktop kernel: [329978.777272] usb 2-5.2: reset high speed USB device using ehci_hcd and address 13
Aug 27 20:53:39 kakyo-desktop kernel: [330003.689130] ===>rt_ioctl_giwscan. 10(10) BSS returned, data->length = 1231
Aug 27 20:54:39 kakyo-desktop kernel: [330063.689041] ===>rt_ioctl_giwscan. 11(11) BSS returned, data->length = 1334
Aug 27 20:55:39 kakyo-desktop kernel: [330123.686174] ===>rt_ioctl_giwscan. 10(10) BSS returned, data->length = 1233
Aug 27 20:55:50 kakyo-desktop kernel: [330134.757341] usb 2-5.2: reset high speed USB device using ehci_hcd and address 13
Aug 27 20:56:39 kakyo-desktop kernel: [330183.687430] ===>rt_ioctl_giwscan. 7(7) BSS returned, data->length = 893
Aug 27 20:57:39 kakyo-desktop kernel: [330243.689046] ===>rt_ioctl_giwscan. 9(9) BSS returned, data->length = 1097
Aug 27 20:58:39 kakyo-desktop kernel: [330303.688552] ===>rt_ioctl_giwscan. 8(8) BSS returned, data->length = 996
Aug 27 20:59:00 kakyo-desktop kernel: [330324.780627] usb 2-5.2: reset high speed USB device using ehci_hcd and address 13
Aug 27 20:59:39 kakyo-desktop kernel: [330363.688569] ===>rt_ioctl_giwscan. 9(9) BSS returned, data->length = 1130
Aug 27 21:00:39 kakyo-desktop kernel: [330423.689041] ===>rt_ioctl_giwscan. 8(8) BSS returned, data->length = 996
Aug 27 21:01:18 kakyo-desktop kernel: [330462.757266] usb 2-5.2: reset high speed USB device using ehci_hcd and address 13
Aug 27 21:01:39 kakyo-desktop kernel: [330483.689347] ===>rt_ioctl_giwscan. 9(9) BSS returned, data->length = 1099
Aug 27 21:02:39 kakyo-desktop kernel: [330543.688065] ===>rt_ioctl_giwscan. 8(8) BSS returned, data->length = 959
Aug 27 21:03:39 kakyo-desktop kernel: [330603.685298] ===>rt_ioctl_giwscan. 8(8) BSS returned, data->length = 996
Aug 27 21:04:39 kakyo-desktop kernel: [330663.686390] ===>rt_ioctl_giwscan. 8(8) BSS returned, data->length = 996
Aug 27 21:05:39 kakyo-desktop kernel: [330723.688537] ===>rt_ioctl_giwscan. 9(9) BSS returned, data->length = 1097
Aug 27 21:06:00 kakyo-desktop kernel: [330744.761336] usb 2-5.2: reset high speed USB device using ehci_hcd and address 13
Aug 27 21:06:26 kakyo-desktop kernel: [330770.776547] usb 2-5.2: reset high speed USB device using ehci_hcd and address 13

```


BTW: since I installed Lucid, the kern.log and dmesg are always spammed by the usb message, which leads me to the suspicion that something is fundamentally wrong with the USB driver.

---

### Post by Fir3chi3f on 2010-08-28
Have you tried this usb drive in another computer? different/same OS? What kind of usb drive are we dealing with?

---

### Post by kakyoism on 2010-08-28
Yes, i used it on Windows and Mac both work flawlessly.

---

### Post by kakyoism on 2010-08-28
It's just any USB key can have the problem.
I just checked with fuser or lsof, no processes are actually using the drive, but I just can't umount them....

The commands i used is

fuser /media/USB-DRIVE
lsof | grep "/media/USB-DRIVE"

---

### Post by kakyoism on 2010-09-04
bump.

I'm gonna have to bump this everyday because it happens to me everyday.

I found that if an application like terminal is using that mounted USB folder. The umount is going to hang forever. YES, this sounds right. But if now I close that app the umount is still gonna hang until I reboot!!! THIS is what makes absolutely no sense!!!

---

### Post by kakyoism on 2010-09-05
This also caused this problem
[http://ubuntuforums.org/showthread.php?p=9807912#post9807912]("http://ubuntuforums.org/showthread.php?p=9807912#post9807912")

---

### Post by kakyoism on 2010-09-05
bump

---

### Post by kakyoism on 2010-09-06
bump

---

### Post by hsoulen on 2010-09-06
Quick question... May sound silly but you never know.

What "media player" are you using? If you are using Rhythmbox, it stays running in the upper taskbar when you click the "x" you must select "quit" for it to close, could be it still has your USB key locked?

Failing that, I am still doing some research and FYI constant "bumping" will not help your case. We are all here to help and that is just annoying.

Cheers,

Hank

---

### Post by hsoulen on 2010-09-06
OK, just noticed you x-posted this to about 4 other forums which combined with the "bumps" is silly as when I try to google your issue the top 4 hits are your issue in other forums.

With the chastising over...

I am wondering if your issue may not be related to another symptom such as your audio or video devices not releasing the streams when you close your media application, this may sound silly but it is possible.

Can you try the following:


[LIST=1]
[*]Use your Windows or MAC computer (you mentioned both worked fine with this USB key) to write a simple text file to the USB device
[*]Mount the USB Key on the Linux machine and open the text file (cat it or VI or gedit...)
[*]Close the file then attempt to unmount the device
[/LIST]
Does this work or same symptom? I am just trying to see if maybe your audio/video files are the problem.

Cheers,

Hank

---

### Post by kakyoism on 2010-09-06
Yes, I did try my best to make sure all my media players be stopped and quit before I unmount. But the point is: If I made a mistake in doing so, or in other cases, I won't be able to unmount the drive AT ALL and it crashes my apt-get and fails a system reboot.... This makes careful unmounting such a burden to take. I've been doing it extremely carefully since the release of Lucid (not so much for the previous versions), but it's still quite error prone. I don't think it's fair to ask users to unmount or crash...

The cases that fail the unmount could be visiting the drive with terminal but the terminal is in another workspace when trying to umount the drive, etc. And mistakes like this easily happens. 

BTW, fuser command doens't always indicate what's using the mounted folder after the device is removed.

---

### Post by kakyoism on 2010-09-26
Still the same.
The only way to umount them is press the power button.
I don't think my machine would like that.

---

