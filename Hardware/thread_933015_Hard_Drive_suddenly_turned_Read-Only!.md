---
title: "Hard Drive suddenly turned Read-Only!"
date: 2008-09-29
forum: Hardware
---

### Post by nikki on 2008-09-29
About a week ago I attempted to reinstalled Ubuntu. I hadn't used it in a few months and Hardy Heron had come out so I decided to try it out. In the past I have had no problems trying to install Ubuntu.

I ended up installing with the Hardy Heron liveCD, and after my installation had completed I rebooted. Upon reboot, nothing happened. It was as if grub was never installed. I attempted to boot the LiveCD again to see what I could do. I noticed it claimed my Ubuntu partitions had be written, but when trying to delete them and start over I was told by the installer it was unable to copy the files.

Since I was having difficulty with installing Ubuntu, I then gave Slackware a try to see if I could get it to write over these partitions. When I tried to run cfdisk on Slackware, I am given the message "Opened disk read-only - you have no permission to write".

I then attempted to go back to Windows XP, and tried booting up that disk and get a similar error.

I then tried using a gparted liveCD to try to write over it. It also claims that they are read only, and that it can't write over them.

Any ideas on how can I regain access to my hard drive?

---

### Post by nikki on 2008-10-08
Decided to give this a bump because I haven't gotten any responses and I'd really like to attempt to fix it rather than have to buy a new hard drive. I've actually started to consider trying to find a magnet and see what happens, but as an absolute last resort. Any suggestions would be appreciated.

---

### Post by Patb on 2008-10-08
Nikki, it is a bit of a stab in the dark but you might try using a [Gparted Live CD]("http://gparted.sourceforge.net/livecd.php") to delete the partitions on the drive and perhaps set up your new partitions using that before trying to reinstall Ubuntu. 

Cheers, Pat

---

### Post by jerome1232 on 2008-10-08
I would try that hard drive in another computer before naming it the culprit.


A month or so ago about an hour in my hard disk would act like everything had been deleted on it, and I couldn't write to it. On a reboot all data was still there.

After alot of troubleshooting and swaping out parts I figured out it was the motherboard. go figure.

---

### Post by nikki on 2008-10-09
I'll try to find another desktop to work with. I'm actually in college dorms right now so a lot of people don't have desktops. Another issue I had come to think of it, was that sound didn't work in LiveCDs (I have integrated sound and it had always worked before) so I guess it wouldn't be too far fetched to find that it really isn't the hard drive.

---

