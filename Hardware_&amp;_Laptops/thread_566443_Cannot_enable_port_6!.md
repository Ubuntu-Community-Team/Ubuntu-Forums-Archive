---
title: "Cannot enable port 6!"
date: 2007-10-03
forum: Hardware &amp; Laptops
---

### Post by FarmerJo on 2007-10-03
Hi,

I was looking into a problem with my refresh rate and wanted to execute these three commands.

sudo /etc/init.d/ gdm stop
sudo pdkg-reconfigure xserver-org
sudo /etc/init.d/ gdm start

I started a terminal and executed the first. The system reverted to text mode as expected but I got the message.

[224.254647] hub 5-0:1.0: Cannot enable port 6. Maybe the hub cable is bad?

I typed in the second command and there was no feedback at all on its execution. The same with the third command. Eventually I pressed CTRL-ALT-DEL which stopped the system gracefully and I was able to restart again.

Is the above error the reason why I could not execute any commands? What does this error mean? 

I have two USB controllers, a USB 1 and a USB 2 but only one of then responds when a flash pen is plugged into a USB socket. Could this be part of the problem?

Regards
FarmerJo

---

