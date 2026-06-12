---
title: "Dell Latitude LS Laptop (x86) problems"
date: 2004-11-08
forum: Hardware &amp; Laptops
---

### Post by twiz on 2004-11-08
Fresh install of Ubuntu.

It auto partitioned everything, installed, my hostname was default - ubuntu.
After it installed and wanted to download new packages it was able to connect ot the internet right away and download updates.
After I rebooted and tried using it, the interface was down. I tried to add it, in System Configuration -> Networking.
It added my on board ethernet (which is what I want and have used before during install).
It only had ipv6 when I typed ifconfig (while I needed ipv4). I disabled it in /etc/modules.d/aliases (from what I read on the forums), and rebooted.

Here are the issues:
1- On system startup it saying loading the kernel and then "Starting Ubuntu..." 
After that message, it takes about a minute to a minute and a half for it to actually start going through the startup procedure.. why?
2- It fails to load the hotplug modules
3- My internet connection is not working during my regular startup, but works during the install phase?
My dmesg's last message is: "eth0: no IPv6 routers present"
and few lines before it says: "IPv6 over IPv4 tunneling driver"

Also the ipv6 module is still loading :(
$ grep ipv6 /etc/modprobe.d/aliases
# alias net-pf-10 ipv6

I ran modules-update and modules-update.modutils too & rebooted since.

Need help! :(

---

### Post by greenwom on 2005-08-20
I have the same laptop, the eth0 problem is kind of wierd.  Sometimes I have to:

ifdown eth0
ifup eth0

that fixes it.  

My problems with the LS are 1resolution is 600X800, do you have that problem?
                                             2 ndiswrapper isn't working.

---

### Post by Elling on 2005-10-29
FWIW, I installed 5.04 without problems on a Dell LS400.

Also, the LCD on the LS series (not L) is set to 800x600 -- it won't do anything else (windows or otherwise).

-peace-

---

