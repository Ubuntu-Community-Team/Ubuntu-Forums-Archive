---
title: "Rioch webcam now works but only in Kopote!?"
date: 2010-11-12
forum: Hardware
---

### Post by dillinga on 2010-11-12
Hi Guys,

Just switched over to Ubuntu last night in an effort to resolve my various hardware issues (gotta love Sony Vaios!).

I've managed to get the r5u87x user tools working and my camera is recognised on boot. At first I thought it was still broken though as both cheese and skype don't show any image when I test the cam.

However, after reading another post, someone mentioned they were able to get the cam working in Kopote.

I installed it and it works!! Can anyone help point me to why this might be happening and how I can get the cam to work in other apps?

I've checked lsof output from all 3 utils and see that kopote uses an additional lib but not sure if that means anything.

Thanks in advance,

Tony

Bus 001 Device 002: ID 05ca:1837 Ricoh Co., Ltd Visual Communication Camera VGP-VCC4 [R5U870]

testing/cheese_output:cheese  1774 dillinga  mem    REG      252,0    26404 1941605 /usr/lib/gstreamer-0.10/libgstvideorate.so
testing/cheese_output:cheese  1774 dillinga  mem    REG      252,0   104640 1941600 /usr/lib/gstreamer-0.10/libgstvideo4linux2.so
testing/cheese_output:cheese  1774 dillinga  mem    REG      252,0    47200 1941603 /usr/lib/gstreamer-0.10/libgstvideofilter.so
testing/cheese_output:cheese  1774 dillinga  mem    REG      252,0    30224  740358 /usr/lib/libgstvideo-0.10.so.0.21.0
testing/cheese_output:cheese  1774 dillinga  mem    REG      252,0    81076 1941606 /usr/lib/gstreamer-0.10/libgstvideoscale.so
testing/cheese_output:cheese  1774 dillinga  mem    CHR       81,0             7690 /dev/video0
testing/cheese_output:cheese  1774 dillinga   27u   CHR       81,0      0t0    7690 /dev/video0


testing/kopete_output:kopete  1883 dillinga  mem    REG      252,0   137028  741692 /usr/lib/libkopete_videodevice.so.4.5.0
testing/kopete_output:kopete  1883 dillinga  mem    CHR       81,0             7690 /dev/video0
testing/kopete_output:kopete  1883 dillinga   29u   CHR       81,0      0t0    7690 /dev/video0


testing/skype_output:skype   1828 dillinga  mem    CHR       81,0             7690 /dev/video0
testing/skype_output:skype   1828 dillinga   28u   CHR       81,0      0t0    7690 /dev/video0

---

### Post by Quackers on 2010-11-12
Welcome to UF :-)

I got mine working with this

[https://launchpad.net/~r5u87x-loader/+archive/ppa](https://launchpad.net/~r5u87x-loader/+archive/ppa)

---

### Post by dillinga on 2010-11-12
Thanks Quackers

I tried that also but it seems to have the same effect as the loader from the existing r5u87x tools. Cam still works fine in Kopete but no cigar in cheese/skype. Looks like there's a way to get Kopete to wrap around skype but I'd rather get it working natively..

Any more?

---

### Post by Quackers on 2010-11-13
No sorry. Once I found that and installed everything it worked, so I stopped looking :-)

---

### Post by dillinga on 2010-11-13
Man this is so annoying! I just got one-touch screen switching to work with nvidia-settings and I'm golden now except for that darn camera. Having to switch back to Windows just for Skype is not optimal in the least!

---

### Post by dillinga on 2010-11-13
I've just installed Ekiga and found that works as well. Having now done an strace on skype and Ekiga during a video test it seems that skype tries to open /dev/video0 (but the syscall doesn't complete). Ekiga on the other hand does the same but also does a load of work in /sys/class/video4linux ?

 grep vid /tmp/skype 
2013  open("/dev/video0", O_RDWR|O_NONBLOCK <unfinished ...>
2013  open("/dev/video0", O_RDWR|O_NONBLOCK <unfinished ...>

rep vid /tmp/ekiga 
2207  stat64("/sys/class/video4linux/", {st_mode=S_IFDIR|0755, st_size=0, ...}) = 0
2207  open("/sys/class/video4linux/", O_RDONLY|O_NONBLOCK|O_LARGEFILE|O_DIRECTORY|O_CLOEXEC) = 49
2207  lstat64("/sys/class/video4linux/video0", {st_mode=S_IFLNK|0777, st_size=0, ...}) = 0
2207  stat64("/sys/class/video4linux/video0", {st_mode=S_IFDIR|0755, st_size=0, ...}) = 0
2207  open("/sys/class/video4linux/", O_RDONLY|O_NONBLOCK|O_LARGEFILE|O_DIRECTORY|O_CLOEXEC) = 49
2207  lstat64("/sys/class/video4linux/video0", {st_mode=S_IFLNK|0777, st_size=0, ...}) = 0
2207  stat64("/sys/class/video4linux/video0", {st_mode=S_IFDIR|0755, st_size=0, ...}) = 0
2207  lstat64("/dev/nvidia0", {st_mode=S_IFCHR|0666, st_rdev=makedev(195, 0), ...}) = 0
2207  lstat64("/dev/nvidia0", {st_mode=S_IFCHR|0666, st_rdev=makedev(195, 0), ...}) = 0
2207  lstat64("/dev/nvidiactl", {st_mode=S_IFCHR|0666, st_rdev=makedev(195, 255), ...}) = 0
2207  lstat64("/dev/nvidiactl", {st_mode=S_IFCHR|0666, st_rdev=makedev(195, 255), ...}) = 0
2207  lstat64("/dev/v4l/by-path/pci-0000:00:1a.7-usb-0:2:1.0-video-index0", {st_mode=S_IFLNK|0777, st_size=12, ...}) = 0
2207  stat64("/dev/v4l/by-path/pci-0000:00:1a.7-usb-0:2:1.0-video-index0", {st_mode=S_IFCHR|0660, st_rdev=makedev(81, 0), ...}) = 0
2207  lstat64("/dev/v4l/by-id/usb-05ca_1837-video-index0", {st_mode=S_IFLNK|0777, st_size=12, ...}) = 0
2207  stat64("/dev/v4l/by-id/usb-05ca_1837-video-index0", {st_mode=S_IFCHR|0660, st_rdev=makedev(81, 0), ...}) = 0
2207  lstat64("/dev/video0", {st_mode=S_IFCHR|0660, st_rdev=makedev(81, 0), ...}) = 0
2207  lstat64("/dev/video0", {st_mode=S_IFCHR|0660, st_rdev=makedev(81, 0), ...}) = 0
2207  lstat64("/dev/.udev/tags/udev-acl/video4linux:video0", {st_mode=S_IFLNK|0777, st_size=68, ...}) = 0
2207  stat64("/dev/.udev/tags/udev-acl/video4linux:video0", 0xbfc3b5cc) = -1 ENOENT (No such file or directory)
2207  lstat64("/dev/.udev/links/v4l\\x2fby-path\\x2fpci-0000:00:1a.7-usb-0:2:1.0-video-index0", {st_mode=S_IFDIR|0755, st_size=60, ...}) = 0
2207  open("/dev/.udev/links/v4l\\x2fby-path\\x2fpci-0000:00:1a.7-usb-0:2:1.0-video-index0/", O_RDONLY|O_NONBLOCK|O_LARGEFILE|O_DIRECTORY|O_CLOEXEC) = 52
2207  lstat64("/dev/.udev/links/v4l\\x2fby-path\\x2fpci-0000:00:1a.7-usb-0:2:1.0-video-index0/c81:0", {st_mode=S_IFREG|0444, st_size=0, ...}) = 0
2207  lstat64("/dev/.udev/links/v4l\\x2fby-id\\x2fusb-05ca_1837-video-index0", {st_mode=S_IFDIR|0755, st_size=60, ...}) = 0
2207  open("/dev/.udev/links/v4l\\x2fby-id\\x2fusb-05ca_1837-video-index0/", O_RDONLY|O_NONBLOCK|O_LARGEFILE|O_DIRECTORY|O_CLOEXEC) = 52
2207  lstat64("/dev/.udev/links/v4l\\x2fby-id\\x2fusb-05ca_1837-video-index0/c81:0", {st_mode=S_IFREG|0444, st_size=0, ...}) = 0
2207  lstat64("/dev/.udev/db/video4linux:video0", {st_mode=S_IFREG|0644, st_size=527, ...}) = 0
2207  open("/dev/video0", O_RDONLY|O_NONBLOCK) = 49
2207  open("/dev/video0", O_RDONLY)     = 49
2207  stat64("/sys/class/video4linux/", {st_mode=S_IFDIR|0755, st_size=0, ...}) = 0
2207  open("/sys/class/video4linux/", O_RDONLY|O_NONBLOCK|O_LARGEFILE|O_DIRECTORY|O_CLOEXEC) = 49
2207  lstat64("/sys/class/video4linux/video0", {st_mode=S_IFLNK|0777, st_size=0, ...}) = 0
2207  stat64("/sys/class/video4linux/video0", {st_mode=S_IFDIR|0755, st_size=0, ...}) = 0
2207  open("/sys/class/video4linux/", O_RDONLY|O_NONBLOCK|O_LARGEFILE|O_DIRECTORY|O_CLOEXEC) = 49
2207  lstat64("/sys/class/video4linux/video0", {st_mode=S_IFLNK|0777, st_size=0, ...}) = 0
2207  stat64("/sys/class/video4linux/video0", {st_mode=S_IFDIR|0755, st_size=0, ...}) = 0
2207  lstat64("/dev/nvidia0", {st_mode=S_IFCHR|0666, st_rdev=makedev(195, 0), ...}) = 0
2207  lstat64("/dev/nvidia0", {st_mode=S_IFCHR|0666, st_rdev=makedev(195, 0), ...}) = 0
2207  lstat64("/dev/nvidiactl", {st_mode=S_IFCHR|0666, st_rdev=makedev(195, 255), ...}) = 0
2207  lstat64("/dev/nvidiactl", {st_mode=S_IFCHR|0666, st_rdev=makedev(195, 255), ...}) = 0
2207  lstat64("/dev/v4l/by-path/pci-0000:00:1a.7-usb-0:2:1.0-video-index0", {st_mode=S_IFLNK|0777, st_size=12, ...}) = 0
2207  stat64("/dev/v4l/by-path/pci-0000:00:1a.7-usb-0:2:1.0-video-index0", {st_mode=S_IFCHR|0660, st_rdev=makedev(81, 0), ...}) = 0
2207  lstat64("/dev/v4l/by-id/usb-05ca_1837-video-index0", {st_mode=S_IFLNK|0777, st_size=12, ...}) = 0
2207  stat64("/dev/v4l/by-id/usb-05ca_1837-video-index0", {st_mode=S_IFCHR|0660, st_rdev=makedev(81, 0), ...}) = 0
2207  lstat64("/dev/video0", {st_mode=S_IFCHR|0660, st_rdev=makedev(81, 0), ...}) = 0
2207  lstat64("/dev/video0", {st_mode=S_IFCHR|0660, st_rdev=makedev(81, 0), ...}) = 0
2207  lstat64("/dev/.udev/tags/udev-acl/video4linux:video0", {st_mode=S_IFLNK|0777, st_size=68, ...}) = 0
2207  stat64("/dev/.udev/tags/udev-acl/video4linux:video0", 0xbfc3b59c) = -1 ENOENT (No such file or directory)
2207  lstat64("/dev/.udev/links/v4l\\x2fby-path\\x2fpci-0000:00:1a.7-usb-0:2:1.0-video-index0", {st_mode=S_IFDIR|0755, st_size=60, ...}) = 0
2207  open("/dev/.udev/links/v4l\\x2fby-path\\x2fpci-0000:00:1a.7-usb-0:2:1.0-video-index0/", O_RDONLY|O_NONBLOCK|O_LARGEFILE|O_DIRECTORY|O_CLOEXEC) = 52
2207  lstat64("/dev/.udev/links/v4l\\x2fby-path\\x2fpci-0000:00:1a.7-usb-0:2:1.0-video-index0/c81:0", {st_mode=S_IFREG|0444, st_size=0, ...}) = 0
2207  lstat64("/dev/.udev/links/v4l\\x2fby-id\\x2fusb-05ca_1837-video-index0", {st_mode=S_IFDIR|0755, st_size=60, ...}) = 0
2207  open("/dev/.udev/links/v4l\\x2fby-id\\x2fusb-05ca_1837-video-index0/", O_RDONLY|O_NONBLOCK|O_LARGEFILE|O_DIRECTORY|O_CLOEXEC) = 52
2207  lstat64("/dev/.udev/links/v4l\\x2fby-id\\x2fusb-05ca_1837-video-index0/c81:0", {st_mode=S_IFREG|0444, st_size=0, ...}) = 0
2207  lstat64("/dev/.udev/db/video4linux:video0", {st_mode=S_IFREG|0644, st_size=527, ...}) = 0
2207  open("/dev/video0", O_RDONLY|O_NONBLOCK) = 49
2207  open("/dev/video0", O_RDONLY)     = 49
2207  open("/dev/video0", O_RDWR)       = 49
2207  open("/sys/class/video4linux/video0/dev", O_RDONLY) = 50
2207  open("/sys/class/video4linux/video0/device/modalias", O_RDONLY) = 50

---

