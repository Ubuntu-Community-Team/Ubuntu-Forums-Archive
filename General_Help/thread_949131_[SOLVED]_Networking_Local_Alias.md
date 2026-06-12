---
title: "[SOLVED] Networking Local Alias"
date: 2008-10-15
forum: General Help
---

### Post by Knuffle on 2008-10-15
I have successfully set up network of Unix based computers and want to be able to refer to them by name, such as "UbuntuLaptop1". I remember in my last network I set up some sort of local alias so I could say something like export WIILOAD=tcp:wii instead of WIILOAD=tcp:192.168.0.103. I can't remember how I did that. Can anyone help? Thanks.

---

### Post by penguinpi.com on 2008-10-16
You should look into setting up a DNS server for your network.

But if you don't want to do that (and what I think you are referring to) is add the entries in your /etc/hosts file.

open /etc/hosts with you favorite text editor. After the 127.0. part dd something like this:



192.168.0.103       wii.yourdomain.com    wii
192.168.0.1         router.yourdomain.com  router


you should now be able to access machines via the hostname you have set for them.

---

### Post by shawnrgr on 2008-10-16
If your changing your hostname (192.168.1.3 myhostname) make sure you change both /etc/hosts and /etc/hostname

---

### Post by jerome1232 on 2008-10-16
How big is your LAN? DNS server might be the best solution (I only have 4 computers and I set up a DNS server because it was easier than maintaining 4 seperate hosts files)

---

