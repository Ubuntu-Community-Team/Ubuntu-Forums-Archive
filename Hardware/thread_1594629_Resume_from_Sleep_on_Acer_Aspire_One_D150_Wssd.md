---
title: "Resume from Sleep on Acer Aspire One D150 W/ssd"
date: 2010-10-12
forum: Hardware
---

### Post by myddewji13 on 2010-10-12
Hi guys, 

I have an acer aspire one d150 netbook which has been upgraded to 2gb ram and a 64gb ssd. My current setup dualboots between Meerkat and Windows 7. My biggest problems is that I cannot resume from suspend in Ubuntu. 

Suspend generally works (although slowly sometimes). However, whenever resuming I am presented with a black screen and a mouse cursor. The cursor moves but I cannot do anything on this screen.

Switching to a virtual console (Ctrl+Alt+F1) brings up a text based login prompt. When trying to login using my username I get the following errror:

```
[   169.694953] end_request: I/O error, dev sda, sector (117267280)
```

Pressing the power button results in a similar error specifying a different sector. 

I once tried to suspend using 'sudo pm-suspend'. I actually managed to resume from this and got back to my desktop. However, trying to invoke 'sudo pm-suspend' again resulted in an error stating the drive was read only, after which my entire session crashed spectacularly. 

After looking around on google etc. it seems that the ext4 partition is not mounted correctly during resume? If this is true how do I fix this? If this isn't true what's wrong and how do I fix it?

---

### Post by myddewji13 on 2010-10-14
bump?

---

### Post by Dustyco.net on 2010-10-25
I'm having this same problem with my Kingston SNV425-S2/64GB in my old Compaq 6510b laptop running 10.10.

---

### Post by Hirs on 2011-01-27
Hi,

I'm having the same problem, I have an asus ul30a laptop, I recently changed the disk by a SSD disk, since then I can't resume from suspend, getting i/o errors on "/" 

Any update on this?

---

### Post by Brian96 on 2011-01-27
This seems to be a very wide problem, but, surprisingly, I cannot find a satisfactory answer.

---

### Post by NoUse on 2011-07-31
I'm seeing the same issue on a fresh 11.04 Natty install on my Dell Mini 1012 with a 64GB SSD drive installed.

---

### Post by Goribuntu on 2011-10-18
Hi, 

Could you all please go to  launchpad  and mark bug 819096   as affecting  you. Please add  the machine/SSD info, so we can exclude specific  hardware issues. The  more people are affected by it, the more attention  it gets from  developers :  [https://bugs.launchpad.net/ubuntu/+s...ux/+bug/819096]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/819096")

---

