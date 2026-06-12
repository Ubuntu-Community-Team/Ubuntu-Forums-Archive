---
title: "Ubuntu do not load and do not install anymore after restart"
date: 2011-02-22
forum: Hardware
---

### Post by goun on 2011-02-22
Hello,

I turned on my laptop and I got the message "Checking Battery State..." before my Ubuntu 10.10 load. I wait for a long time but the message never dissapear so I restarted the laptop in the hard way. Then I got a list of options as you can see in "init.JPG".

- If I choose the first option (Ubuntu, with Linux 2.6.35-25-generic) then Ubuntu never load but instead I get what you can see in "generic.JPG"

-If I choose the second option (Ubuntu, with Linux 2.6.35-25-generic (recovery mode)) then Ubuntu still never load and I get the messages as in "generic (recovery mode).JPG"

After all, I decided to reinstall Ubuntu 10.10. I boot the system with the ubuntu live cd and then:

-If I select just to Try Ubuntu from CD then they load and run normal. The problem is that when I try to open my internal hard drive (Places->117 GB FileSystem) then either I get a bug report that the "process "ubiquity" terminated unexpectedly" or an Error message that "a job is pending on /dev/sda1"

-If I select to install Ubuntu then the installation is stuck on the first step and then Ubuntu are never installed!

Do you know what it might happen? Do you think that my internal hard drive is damaged?

Thank you in advance!

---

### Post by goun on 2011-02-23
I also tried to run fsck for all my /dev/sda without success as you can see in Screenshot.png.
Is there any other recommendation?

---

### Post by ph3ar on 2011-02-23
Hello, 

I think that by default Ubuntu livecd mounts all disks and partitions by default. From your post it seems that has already mounted your HD (/dev/sda$).

1. Check with this command for any mounted partition(s) from the HD (/dev/sda$ as you mentioned in your post):
```
mount |grep /dev/sda
```

2. The command should return something like this:
```
/dev/sda.. on /media/... type ext4
```

If it exists such a line then it means that you HD is mounted, prior to anything backup your data just to be sure.

Run the output of the following commands, to check if there is any error report to the kernel ring buffer.
```
dmesg |grep sda
```

Try to unmount the mounted filesystems in order to scan the HD for errors.
```
sudo umount /dev/sda*
*: Find out which is the partition name by the output of 2nd command. 
```

Try to check the partition(s) for errors and send the output.

Finally you can install the [smartmontools]("https://help.ubuntu.com/community/Smartmontools"), a package to control and monitor storage systems using the Self-Monitoring, Analysis and
 Reporting Technology System (S.M.A.R.T.) built into the HD.

---

### Post by goun on 2011-02-24
I use fdisk with parameter "r" in order to delete all of my partitions. Only then I was able to install Ubuntu 10.10 again.

---

### Post by ph3ar on 2011-02-25
> **goun said:**
> I use fdisk with parameter "r" in order to delete all of my partitions. Only then I was able to install Ubuntu 10.10 again.

Hi, nice that you solve your problem. :)

You mention the parameter "r" but such an option doesn't delete all partitions in fdisk. 
This parameter is used to return back to the main menu while you are in the extra functionality (parameter "x") menu of the fdisk interactive menu.

Did you mean to say the parameter "d" ?

---

### Post by goun on 2011-02-25
You are right, I meant "d"! :)

---

