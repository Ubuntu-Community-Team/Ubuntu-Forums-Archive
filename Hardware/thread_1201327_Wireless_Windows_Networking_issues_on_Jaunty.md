---
title: "Wireless Windows Networking issues on Jaunty"
date: 2009-07-01
forum: Hardware
---

### Post by denbeigh2000 on 2009-07-01
Hello,

I am running a HP Pavilion dv6 laptop, clean install of Jaunty.

When I open the "Network" window, I can enter workgroup, but I can only see the local host (me)

If I try to manually connect (smb://server/share), it will deliver:
"Error: Failed to mount Windows share
Please select another viewer and try again."

Can anybody help me with this?

---

### Post by jmaupas on 2009-07-03
I got the same problem.
Adding wlan0 (the wireless interface) in smb.conf solved this issue.

Application->Accessories->terminal

sudo nano /etc/samba/smb.conf
change 
; interfaces = 127.0.0.0/8 eth0
by
interfaces = wlan0 127.0.0.0/8 eth0

sudo /etc/init.d/samba restart

Maybe there is now a GUI to samba but I'm an old cmdline guy...

---

### Post by denbeigh2000 on 2009-10-20
Thanks! :D

All works perfectly now. (Y)

---

