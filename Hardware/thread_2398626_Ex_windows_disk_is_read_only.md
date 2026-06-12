---
title: "Ex windows disk is read only"
date: 2018-08-15
forum: Hardware
---

### Post by meknoy on 2018-08-15
After installing Ubuntu, I connected my "D"drive from my old Windows setup directly on the motherboard. 

I can access it from 'other locations', and all my data is readable but I can not writhe.

Can I make this drive connect atoumaticly with all reading and writing rights without deleting all my files. This drive might go back in a Windows machien later.

Thanks for the help

---

### Post by yancek on 2018-08-15
Your D drive from your old windows is undoubtedly a windows (ntfs) filesystem so first check to see if the software need to access a windows filesystem from Linux is installed with this command:

```
whereis ntfs-3g
```

If you get a positive response, then you need to understand that all Linux systems, includng Ubuntu are designed as MULTI-USER systems and the normal user rarely has rights to do more than read directories/files outside the user /home directory.  You need to change the owner and/or group for the directory in which this partition is shown, probably under /media/user (your actual user name here).  To understand root/administrator usage on Ubuntu which uses sudo, you can read the Ubuntu documentation at the page below.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by oldfred on 2018-08-15
Is your version of Windows 8 or 10?
Those use fast start up which is just hibernation.
And it sets the hibernation flag on all NTFS partitions. 
The Ubuntu NTFS driver will not auto mount hibernated NTFS to prevent damage. You can manually mount read only.

       Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[URL="http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html"]http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html
      [/URL]
 More explanation of NTFS driver & Windows hibernation
[http://askubuntu.com/questions/145902/unable-to-mount-windows-ntfs-filesystem-due-to-hibernation](http://askubuntu.com/questions/145902/unable-to-mount-windows-ntfs-filesystem-due-to-hibernation) 
    [URL="http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html"]
[/URL]

---

