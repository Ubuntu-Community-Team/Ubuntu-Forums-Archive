---
title: "Inspiron 1525 no wireless after resume from hibernate/suspend"
date: 2008-04-13
forum: Hardware &amp; Laptops
---

### Post by nibblebot on 2008-04-13
Hi all,
 I recently bought a Dell Inspiron 1525 and installed Ubuntu 7.10 on it. I had to downgrade the BIOS to rev A08 as per: [http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/Resume_from_Suspend_Broken_with_newer_BIOS](http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/Resume_from_Suspend_Broken_with_newer_BIOS)
to get suspend/hibernate to work at all. Now, I am trying to wireless to work after resuming from hibernate/suspend.

I would like to use the restricted driver from dell for my broadcom WLAN but it doesn't show up in the 'Restricted Driver Manager' dialog. Instead, I found a solution that uses ndiswrapper from: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

However, using the ndiswrapper for wireless, I can't reconnect to any network on resume. My WiFi light is on, so I think that means the driver is loaded, The gnome network manager applet says that I am connected to a network but no websites load. Anyone else have this problem? Any workarounds/solutions? How might I get the restricted broadcom driver to show up in the 'Restricted Driver Manager'?

Thanks in advance!
-j

---

