---
title: "4Gb USB and Xubuntu"
date: 2009-05-27
forum: Installation &amp; Upgrades
---

### Post by Gudjon on 2009-05-27
Hello,

Wanting to run Xubuntu on a 4Gb USB-stick.
Following the steps from [pendrivelinux]("http://www.pendrivelinux.com/usb-xubuntu-904-persistent-install-windows/") , running according to the steps,
and  after running everything I do the following:
I copy the content from the file 3Gnb casper-rw loop file to 'r oot' directory of the USB-stick. This is working fine. I then upgrade, using the update manager.

Then I would like to install openJDK and Eclipse ( ver 3.2 ) on the Stick.
This works, but there seems to be some broken packages.
I am able at first to run a Java-program in Eclipse.
I am not able to store anything in my workspace.
Then I am not able to launch Eclipse ....
- is this linked to my upgrade.


A bit new to this, is my 4G drive already full ?
This is the output when running df -h

[INDENT]ubuntu@ubuntu:/$ df -h
Filesystem            Size  Used Avail Use% Mounted on
tmpfs                1003M  2.4M 1000M   1% /lib/modules/2.6.28-11-generic/volatile
tmpfs                1003M  2.4M 1000M   1% /lib/modules/2.6.28-11-generic/volatile
tmpfs                1003M     0 1003M   0% /lib/init/rw
varrun               1003M  104K 1003M   1% /var/run
varlock              1003M     0 1003M   0% /var/lock
udev                 1003M  144K 1002M   1% /dev
tmpfs                1003M  128K 1003M   1% /dev/shm
rootfs                3.0G  1.4G  1.5G  47% /
/dev/sdb              3.8G  3.4G  422M  90% /cdrom
/dev/loop0            593M  593M     0 100% /rofs
tmpfs                 3.0G  1.4G  1.5G  47% /tmp
tmpfs                1003M  2.4M 1000M   1% /lib/modules/2.6.28-11-generic/volatile
tmpfs                1003M  2.4M 1000M   1% /lib/modules/2.6.28-11-generic/volatile
tmpfs                1003M  2.4M 1000M   1% /lib/modules/2.6.28-11-generic/volatile
tmpfs                1003M  2.4M 1000M   1% /lib/modules/2.6.28-11-generic/volatile
[/INDENT]Considering space, what should I be looking for ?
is there space or is there no space for my applications.
 
my thoughts for this stick , and correct me if I am going down the wrong path,
is to install - later on - Eclipse with some plugins ( so that I have support for JSP/Servlets apps ) and MySQL - is there enough space here ?
Or could anyone provide me with a better approach ( using some other dist than Xubuntu ? ) so that I can fullfill the thoughts ...

Hope that anyone can give me some advice here.

Best regards, Gudjon

---

