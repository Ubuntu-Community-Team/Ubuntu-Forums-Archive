---
title: "Wireless connection &amp; samba"
date: 2008-12-28
forum: Hardware
---

### Post by DazEllerington on 2008-12-28
Hi All,

I'm running Ubuntu EEE 8.04.1 on my Asus EEE PC 900 and am very happy with its performance and tools.

My wireless tool is mm-applet 0.6.6. Does anyone know how to make it launch a command after it connects to a wireless network. So:

If it connects to "homehub" I want it to launch mount -t smbfs //server1/share /blah -o user=me,pass=secret

but if it connects to "workwireless" I want it to launch mount -t smbfs //ntserver/myhome /blahwork -o user=windowslogon,pass=secret

?

And also, the opposite when it disconnects unsung umount - but this one isn't paramount.

Thanks in advance

Daz.

---

### Post by MeURi on 2008-12-28
Well, you can do these things using Wicd (an alternative network manager available from the repos), if I remember properly, but that's not what you asked for.

I actually don't know if NetworkManager offers this possibility.

---

### Post by Rohan Kapoor on 2008-12-28
Not possible with the default network manager.

---

### Post by DazEllerington on 2008-12-30
Hi,

I'm not getting on well with wicd. Connects OK at startup but any manual reconnects after it sits on "obtaining IP address" for ages and then freezes the whole system (power off needed).

The part for launching scripts is exactly what I need though.

Anyone know another way?

Thanks for your help.

Daz.

---

### Post by Rohan Kapoor on 2008-12-30
> **DazEllerington said:**
> Hi,

I'm not getting on well with wicd. Connects OK at startup but any manual reconnects after it sits on "obtaining IP address" for ages and then freezes the whole system (power off needed).

The part for launching scripts is exactly what I need though.

Anyone know another way?

Thanks for your help.

Daz.
Well... wicd is highly unstable on my machine though. But the scripts are not present in any other network manager.

All I can say is that you could connect and then run the scripts off of your desktop. I know that's not automatic but that's probably the best solution.

---

### Post by DazEllerington on 2008-12-30
This is fine for now but I'm going to modify nm-applet-0.7.0 to do some (very) basic script launching. Seems a challenge just to get it to compile as-is though ;) 

If anyone is interested or has any info before I start, please let me know.

Thanks.

Daz.

---

### Post by Rohan Kapoor on 2008-12-30
I would be interested in the final project, keep me updated please!

---

