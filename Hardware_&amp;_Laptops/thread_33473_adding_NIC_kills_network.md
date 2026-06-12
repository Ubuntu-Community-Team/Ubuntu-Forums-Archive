---
title: "adding NIC kills network"
date: 2005-05-11
forum: Hardware &amp; Laptops
---

### Post by zerojunkie on 2005-05-11
Hey all, switched to Ubuntu about 3 months back and couldn't be happier. Except for tonight when I added a second NIC to my configuration. Doing so, kills both card's ability to access the network (statically assigned IP's). I can see them in ifconfig and configure them from the same program. However when I, for example, attempt to ping any hosts in the network of the either nic. I get a destination host unreachable. Removing the secondary NIC (eth1) fixes the problem...and it's doing it with both tulip and 8139too drivers/chipsets. Any clue what might cause something like that? Oh yeah, also adding to the complexity I can see the Rx counter increment when I ping the address of either interface from another workstation. However when tcpdump is run on that interface no traffic is seen. Iptables is not configured. And lspci -vv see's both and on different IRQ's...I'm at a loss guys, any help would be greatly appreciated. Thanks!

---

### Post by JonahRowley on 2005-05-11
Are these NICs connected to different networks?  If you insert your second NIC in a lower-numbered PCI slot, and especially if they're using the same driver, the new NIC will take eth0, pushing your old one to eth1.  Were you watching both interfaces with tcpdump, or were you watching the one you were expecting to see traffic on?  Try switching the cables around.  Don't laugh, I've done things like this before, and smacked myself in the forehead once I realized.

---

### Post by zerojunkie on 2005-05-11
[QUOTE=JonahRowley]Are these NICs connected to different networks?  If you insert your second NIC in a lower-numbered PCI slot, and especially if they're using the same driver, the new NIC will take eth0, pushing your old one to eth1.  Were you watching both interfaces with tcpdump, or were you watching the one you were expecting to see traffic on?  Try switching the cables around.  Don't laugh, I've done things like this before, and smacked myself in the forehead once I realized.[/QUOTE]


Best post evar!  

Moving the cards around worked. I moved what was eth0 up two slots and put eth1 where it used to be, and bam. Can't believe I didn't try that last night. ](*,)

Much thanks for the advice.

---

