---
title: "Every time File got corrupted while copying to Memory Card/Phone"
date: 2015-01-05
forum: Hardware
---

### Post by amit17 on 2015-01-05
I am using Ubuntu 14.04 .From last two days I am facing a strange problem.Every time I copy a file from computer to phone(internal memory)/memory card via data cable,the destination file  got corrupted.Everything was working fine before two days and at this time copying works well in Windows as well .I am able to copy correctly via bluetooth only it's not working via USB cable.While copying file I am not getting error and file copying takes a very short time as compared to normal copy as before.I am using Sony Xperia M running on Android 4.3.
Please help me to resolve this issue.

---

### Post by sudodus on 2015-01-05
Welcome to the Ubuntu Forums :-)

It might be a problem that the copy is buffered, and not yet written to the mass storage device, in this case the memory card. If that is the case there are several methods to synchronize it.

1. Run ***sync*** in a terminal window, and wait for it to complete (return to the prompt).
```

sync
```


2. ***Unmount*** the mass storage device (which will run sync automatically before unmounting)


a. Press the ***eject button*** in the file browser, and wait for the button to disappear,  - the easy way, if it works :smile:


b. or unmount the mounted partition(s) in the device ***in a terminal window***

Identify the mass storage device and mounted partitions on it with the terminal command

```
df
```

and  unmount it

```
sudo umount /dev/sdxy
``` or

```
sudo umount /media/pathname-to-the-mass-storage-device
```

where x is the device letter and y is the partition number, for example **/dev/sdb1**

Check afterwards that it is no longer mounted.

```
df
```


3. Finally unplug it (the card or pendrive or external drive or phone) safely :-)

---

### Post by amit17 on 2015-01-06
Thanks for reply.
USB Cable is connected in Media Transfer Mode(MTP).I have also tried to change it to Mass Storage Mode(MSC) but it's not working.
Here is the output of df command in MTP mode .It's not listing phone/memory card

> a@a-HP-Pavilion-dv4-Notebook-PC:/$ df
Filesystem     1K-blocks     Used Available Use% Mounted on
/dev/sda7       17754448 14764468   2065052  88% /
none                   4        0         4   0% /sys/fs/cgroup
udev             1506864        4   1506860   1% /dev
tmpfs             303288     1296    301992   1% /run
none                5120        0      5120   0% /run/lock
none             1516440    24448   1491992   2% /run/shm
none              102400       44    102356   1% /run/user
/dev/sda1      113360012 20002640  93357372  18% /media/a/Windows 7
/dev/sda5       27503216   101124  27402092   1% /media/a/Ubuntu
/dev/sda4      103164924 29260040  73904884  29% /media/a/Windows 8
/dev/sda2       47284760 36921500  10363260  79% /media/a/Softwares
a@a-HP-Pavilion-dv4-Notebook-PC:/$

---

### Post by sudodus on 2015-01-06
Have you seen this tutorial? (I'm no expert on MTP, but the tutorial might help you)
[URL="http://ubuntuforums.org/showthread.php?t=2226702"]
Connect an Android device using MTP in Ubuntu 14.04 LTS[/URL]

---

### Post by amit17 on 2015-01-06
I tried that no change :(
I am trying to create a file in Memory Card ,I am getting this error.
> libmtp error:  Could not send object info.

---

### Post by sudodus on 2015-01-06
Is the file system read-only for Ubuntu when connected like that?

I hope someone with more experience will reply. What if you post a question in that tutorial thread about MTP?

---

