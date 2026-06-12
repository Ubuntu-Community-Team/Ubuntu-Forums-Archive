---
title: "network manager is erasing my network mask field"
date: 2008-11-11
forum: General Help
---

### Post by hwttdz on 2008-11-11
I'm making a new connection, because I need to have a static ip on my local network.  Anyways I specify 255.255.255.0 for the network mask, and network manager applet changes it (to 24, which seems to work, but I feel it should not change it).  It changed my gateway a few times as well, but it seems to have stuck now.  Is this a reported problem, what could I be doing wrong.  

I am right clicking hitting edit connections.  Editing the new connection, going to ipv4 setting it to manual, adding something to the box there and inputting everything I want and clicking ok.  Then if I open it up again, my settings have changed.

---

### Post by fatphilthethird on 2008-11-12
Try editing /etc/network/interfaces

See here: 
[http://www.howtogeek.com/howto/ubuntu/change-ubuntu-server-from-dhcp-to-a-static-ip-address/](http://www.howtogeek.com/howto/ubuntu/change-ubuntu-server-from-dhcp-to-a-static-ip-address/)

Worked for me

Fat

---

