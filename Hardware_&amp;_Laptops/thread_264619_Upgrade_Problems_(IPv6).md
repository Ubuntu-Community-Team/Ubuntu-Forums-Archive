---
title: "Upgrade Problems (IPv6)"
date: 2006-09-24
forum: Hardware &amp; Laptops
---

### Post by bobterri on 2006-09-24
Well, I made the plunge.  I am a pastor of a church and decided to wipe XP off my hardrive and install 6.06.  Everything was going great, then....

I upgraded all suggested packages back on Sept. 19??? including the new kernel 2.6.15-27-386.

After this I couldn't connect through my wireless, ethernet or dial-up services.  I learned that by disabling IPv6 in Firefox about:config I could again get on the internet.  

However, I can no longer use Evolution for my Email and I downloaded and tried Thunderbird and the same problem.  Is there some way to disable IPv6 in these Email clients?  I tried disabling IPv6 system-wide through creating the /etc/modprobe.d/bad_list file (I forget now the exact contents of the file) and that didn't help.

Can anyone help?

---

### Post by Melcar on 2006-09-25
For the wireless:
How did you get it working in the first place?  Did you have to install drivers or was it "plug and play"? If you had to install drivers by way of ndiswrapper or some other method, you may have to reinstall then after you upgraded your kernel.

---

### Post by xyz on 2006-09-25
Here's a little info that might help you:
In a terminal, type:
```
sudo gedit /etc/modprobe.d/bad_list/
```
This creates bad_list in /etc/modprobe.d
Copy/Paste  **alias net-pf-10 off**  into it
Save and reboot.
Now copy/paste  **ip a | grep inet6**  into your terminal.
It should returm nothing.

Type  about:config  to check for Firefox
In filter, copy/paste  **network.dns.disableIPv6** into Filter and set it to "true"  by double clicking on it.
[Wireless]("http://www.ubuntuforums.org/forumdisplay.php?f=139")

---

### Post by bobterri on 2006-09-25
Melcar,

I have the ipw2200 drivers.  It worked right after initially installing Dapper.  It worked wonderfully until the last upgrade.

xyz,

I've tried these things.  It doesn't matter.  Thanks, though.

---

### Post by bobterri on 2006-09-25
Wow, it wasn't the updates after all, unless somehow they affected my Actiontec dsl modem.  I updated the firmware on the modem and now IPv6 protocol works again.  Weird, huh?

---

### Post by Melcar on 2006-09-25
> **bobterri said:**
> Wow, it wasn't the updates after all, unless somehow they affected my Actiontec dsl modem.  I updated the firmware on the modem and now IPv6 protocol works again.  Weird, huh?

Well you did upgrade your kernel which probably screwed around with your device firmwares registared in Ubuntu.  Everytime you do a critical update (like kernel changes) be prepared for this kinds of problems.  Basicaly everything that is kernel dependant needs to be reinstalled after a kernel update (like video drivers and sometimes wireless devices).  Glad you could fix your problem.

---

### Post by bobterri on 2006-09-26
I have been using this modem for a little over a year and have updated kernels about six times in three different distros (Mandriva, Xandros, Mepis and now Ubuntu).  I have updated Ubuntu's kernel twice.  This is the first time this has happened.  

Is there some info you could refer me to that would explain what you're talking about?

Thanks!

---

### Post by bobterri on 2006-09-26
Oops!  I mean four distros.

---

