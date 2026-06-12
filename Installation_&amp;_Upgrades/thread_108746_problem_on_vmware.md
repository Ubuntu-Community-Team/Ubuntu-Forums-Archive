---
title: "problem on vmware"
date: 2005-12-26
forum: Installation &amp; Upgrades
---

### Post by noeluylee on 2005-12-26
Hi, I installed vmware on my ubuntu, it worked fine at first and was able to play around with it a bit, in fact I was able to install debian on it. But today, I when I run the program, nothing happends. I restart my ubuntu by restarting my pc, and run the vmware again, still nothings happen. I dont know whats wrong. Any people incounter this problem before? 

Also, How to un-install this application? 

I am planning to uninstall it and install it again... but i dont know how to remove this application since it does not appear on the synaptics.

Does this problem using the jre on my ubuntu? coz I am currently having a problem on jre, my eclipse does not work as well.

Thanks a lot.

Regards,
Noel

---

### Post by loupy on 2005-12-26
I've have not run into that issue.  I was unable to install it under the default Ubuntu Kernel (even using gcc 3.4), so I built my own and it works now.

To uninstall vmware run the following command:

sudo /usr/bin/vmware-uninstall.pl

---

### Post by anil_robo on 2005-12-26
[quote=loupy]To uninstall vmware run the following command:
sudo /usr/bin/vmware-uninstall.pl[/quote] SHouldn't it be ```
sudo **perl** /usr/bin/vmware-uninstall.pl
```

---

### Post by noeluylee on 2005-12-26
I have gcc 4.0, just checked it on synaptics.

Okay I will try to uninstall it, and install, will see if this fix the problem. :)

thanks guys.

Noel

---

### Post by noeluylee on 2005-12-27
Hi, I was able to re-install the vmware, and was able to run it, but I encounter error upon running my virtual server... errors are:

--Version mismatch with vmmon module: expecting 137.0, got 116.0.
You have an incorrect version of the `vmmon' kernel module.
Try reinstalling VMware Workstation.

--Failed to initialize monitor device.

--Unable to change virtual machine power state: Cannot find a valid peer process to connect to

--Failed to reply to the dialog: Pipe: Read failed

what this problem again :( any suggestions?

Thanks

---

### Post by noeluylee on 2005-12-27
anybody knows any workaround to this problem ? - thanks

---

### Post by anil_robo on 2005-12-29
[quote=noeluylee]--Version mismatch with vmmon module: expecting 137.0, got 116.0.
You have an incorrect version of the `vmmon' kernel module.
Try reinstalling VMware Workstation.[/quote]

There was a thread about this in the forums, and people solved this problem too. I can't remember where exactly, but you can start with these links:
[http://www.ubuntuforums.org/showthread.php?t=84275](http://www.ubuntuforums.org/showthread.php?t=84275)
[http://www.ubuntuforums.org/showthread.php?t=107063](http://www.ubuntuforums.org/showthread.php?t=107063)
[http://www.ubuntuforums.org/showthread.php?t=107545](http://www.ubuntuforums.org/showthread.php?t=107545)
[http://www.ubuntuforums.org/showthread.php?t=84085](http://www.ubuntuforums.org/showthread.php?t=84085)

Please post here after you've solved the problem. Thanks! :)

---

