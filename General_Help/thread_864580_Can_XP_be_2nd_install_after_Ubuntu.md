---
title: "Can XP be 2nd install after Ubuntu?"
date: 2008-07-19
forum: General Help
---

### Post by rsnow on 2008-07-19
After trying all day to find a way to get rid of Vista from my wife's HP Pavilion so I could install another OS, I would like to know if anyone can tell me:

a) Would installing Ubuntu give me the option to completely wipe Vista from the hard drive?

b) If so, could I then create a partition to install XP as a dual boot?

---

### Post by YaroMan86 on 2008-07-19
Yes, you can install Windows XP after Ubuntu. You just need to repair your GRUB MBR. Windows likes to overwrite anything non-windows in that MBR so you need to be careful.

Read this: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by brunolabs on 2008-07-19
a) Yes. You can delete/format the Vista partition.

b) If you install XP after Ubuntu it will mess up GRUB. So if you want to dual boot it's better to install XP first.

---

### Post by rsnow on 2008-07-19
What do you recommend for the best way to delete/format the Vistat partition so that I can install XP first?

---

### Post by lisati on 2008-07-19
> **rsnow said:**
> What do you recommend for the best way to delete/format the Vistat partition so that I can install XP first?
The first thing to do is make sure you have a bcakup of any important data on your Vista partition - including knowing the whereabouts of Vista installation and/or recovery disks, should the need arise to go back to Vista. Also make sure you are able to recover any other important data you might have on other partitions.

After that, it can sometimes be easier to install XP first (perhaps over the top of Vista, if that's what you want) and then Ubuntu. As has already been mentioned, Windows has a tendency to mess with anything non-Windows.

---

### Post by HermanAB on 2008-07-19
Dual boot is so 20th century...
;)

Unless you wish to play games on XP, I suggest that you install Ubuntu only, then install Virtualbox or VMware and install XP as a virtual machine in that.  The advantage is that you can then run Linux and Windows applications simultaneously.

Cheers,

Herman

---

### Post by rsnow on 2008-07-19
I have tried several times to install over Vista. Vista won't let me. It tells me to run chkdsk and then tells me I am denied from running chkdsk because I am not high enough on the totem pole (even though I am logged in as the administrator).

I have read of others having this same problem with HP machines, so I'm beginning to think there is some hanky panky involved trying to keep people from uninstalling Vista. On another forum I read where KillDisk was used to erase the hard drive but they still kept getting the same error message at the same place when they tried to install XP.

---

### Post by rsnow on 2008-07-19
I like the idea of linux and then using virtualbox or vm but I'm not sure my wife will go along plus I'm not sure I'm savvy enough yet to do the virtualbox or vm thing. A while back I tried to use Wine but couldn't figure it out.

I don't mind messing with things on my machine but I would rather not have the wife fussing at me all the time about hers.

---

