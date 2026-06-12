---
title: "Setup a modem PCMCIA xircom"
date: 2005-08-08
forum: Hardware &amp; Laptops
---

### Post by hsolis on 2005-08-08
\\:D/ Yes! I spent some time trying to set up my modem. I know this can be pretty simple for some of you but sometimes the solution is more simple than the sugestions arround. My modem was not recognize when I run the autodetect from the 
System -> Administration -> Networking. I always got:
Could not autodetect modem device
Then I spent hours looking in forums for drives, config... etc. etc... finally I ran in terminal as root:

# wvdialconf  /etc/wvdial.conf

It detect that my modem was on ttyS14 I put that number in the Networking window and it ran nicely!!!
Thanks to all the guy arround!
H

---

### Post by equability on 2007-03-21
> **hsolis said:**
> \\:D/ Yes! I spent some time trying to set up my modem. I know this can be pretty simple for some of you but sometimes the solution is more simple than the sugestions arround. My modem was not recognize when I run the autodetect from the 
System -> Administration -> Networking. I always got:
Could not autodetect modem device
Then I spent hours looking in forums for drives, config... etc. etc... finally I ran in terminal as root:

# wvdialconf  /etc/wvdial.conf

It detect that my modem was on ttyS14 I put that number in the Networking window and it ran nicely!!!
Thanks to all the guy arround!
H

Ciao "hsolis".

I spent some time trying to set up my modem, too.

I did, what you posted and.............. it works.

Great.

Thank your very much.

---

