---
title: "IronKey Secure USB device"
date: 2008-08-09
forum: General Help
---

### Post by Ve6jhc on 2008-08-09
I searched the forums and found a few threads on the IronKey but none that I saw provided a working solution to my issue.
My 8 GB IK works great on Windows but I also need to access my secure files on Linux. When I use my IK in Ubuntu 8.04 it auto mounts the CD part of the IK. I can browse to the Linux folder and when I double click on the app I get this error message...

sh: cannot create /proc/scsi/device_info: Permission denied
unable to add IronKey entry to /proc/scsi/device_info
please try re-running as root
Hit return to exit

So I try from the Command Line. I see that IK is mounted as /media/IronKey. I navigate to that location and try sudo IronKey....bash error - unknown command.

I review what I have tried and I go back to the first error message about not being able to add the IronKey entry to the /proc/scsi/device_info....I check that the file and path is correct. There is nothing in the device_info file.....Does anybody have the correct info on what to add here or am I just barking up the wrong tree?

What methods have worked for you to be able to unlock the secure side of IK in Ubuntu 8.04?

---

### Post by Ve6jhc on 2008-08-11
A user on the Ironkey forums provided a method that I have confirmed as working....I thought I would post his tip here to complete the thread in case others had the same issue.

Basically the procedure is to right click on the CD icon on the desktop and browse to the Linux folder, Right click on on ironkey and select "Open with other application", and then go down to the bottom and use a custom command - enter "gksudo". You will be prompted for your Ironkey unlock password and Ubuntu will them automount the newly unlocked USB drive on your desktop.

---

### Post by tkh23 on 2009-08-14
Got the Following Error:
```

tkh@ubuntu:/media/cdrom/linux$ gksudo ./ironkey
Failed to contact the GConf daemon; exiting.
```

---

### Post by dcstar on 2009-08-14
> **tkh23 said:**
> Got the Following Error:
```

tkh@ubuntu:/media/cdrom/linux$ gksudo ./ironkey
Failed to contact the GConf daemon; exiting.
```

Because things that worked in old versions do not necessarily work in newer Ubuntu versions.

There is a known issue with root command shells and 9.04.

---

### Post by tkh23 on 2009-08-27
Thanks for your reply, now I know why it doesn't work. However, I'd prefer if you were able to propose a fix >.< Oh yeah, please?  :)

EDIT: Found a bunch of stuff on this topic here:
[https://bugs.launchpad.net/ubuntu/+source/gconf2/+bug/328575](https://bugs.launchpad.net/ubuntu/+source/gconf2/+bug/328575)
and managed to mount my ironkey using this workaround:
> [#7]("https://bugs.launchpad.net/ubuntu/+source/gconf2/+bug/328575/comments/7")                                   [endeneu]("https://bugs.launchpad.net/%7Edotsw")             wrote             on 2009-03-22:                                                                            I also have this bug.UbuntuJauty,all last updates
Temporary solution  $ gnome-terminal -e "sudo -i"

        


---

### Post by kyle2595 on 2009-09-16
There is helpful information on this post "http://ubuntuforums.org/showthread.php?t=1241340" I was using Ubuntu 9.04.

---

### Post by dakkar9999 on 2010-04-13
Brilliant!  The gksudo command worked for me as well!  I'm running Lucid Lynx 10.04.

Thanks

---

