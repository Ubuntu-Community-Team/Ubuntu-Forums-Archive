---
title: "Linux/Ubuntu Newbie network probs SMB support not running"
date: 2004-12-01
forum: Hardware &amp; Laptops
---

### Post by Anne Marshall on 2004-12-01
I installed Ubuntu on my laptop -it's a really good fast system EXCEPT having done a full install of Ubuntu when I try to log on to my Windows 2000 server I get the message:

                 SMB support is not running 
                 You don't have SMB support installed
                  Please install SMB suppport on the system to enable file  
                 sharing in Windows Networks.

Is SMB on the Ubuntu disk - if so how do I install it?

The NIC card or whatever is working and there seems to be traffic as far as the router.  

I'm  a Linux newbie so I don't know how to get this sorted myself.

---

### Post by lockenkeyster on 2004-12-02
You can use apt-get to install samba,

open a terminal and do both of these:

sudo apt-get install samba
sudo apt-get install smbfs

---

