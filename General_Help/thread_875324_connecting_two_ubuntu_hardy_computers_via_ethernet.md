---
title: "connecting two ubuntu hardy computers via ethernet"
date: 2008-07-30
forum: General Help
---

### Post by Glich on 2008-07-30
Hello, I have two Ubuntu Hardy laptops one with openssh-server installed in addition to the default. I have configured under Systems->Administration->Network, under wired connection the static IP of both computers to something reasonable: 192.168.0.100 and 192.168.0.101

and both with the subnetmask of 255.255.255.0

When the Ethernet crossover cable is connected there is no indication of any connection being made and when I try the ping command I get:

ping 192.168.0.101
connect: Network is unreachable

How can I connect both machines to each other? My ultimate goal would be to have ssh access to one machine from the other.

Thanks.

---

### Post by Iowan on 2008-07-30
That should have worked...  post your **/etc/network/interfaces** file(s).  I'd be curious if there's an "auto eth0" line, or if the configuration(s) are there.

After connecting the cable, you might try restarting networking on both machines.

---

### Post by editrix on 2008-07-31
Another thing you can try is: **sudo ifconfig eth0 up** before you ping them. I have the same setup, but I use a dialup modem to connect to the internet. Don't ask me how I figured this out, but to get the ethernet card to work I have to do that, then when I want to get on the internet I do: **sudo ifconfig eth0 down** so the computer knows to use the modem.

BTW, I just ftp my files from one box to the other, rather than ssh.

---

### Post by Glich on 2008-07-31
Thanks for the responses! It works now.

Iowan: No I don't have "auto eth0" in that file. Thanks.

editrix: Thanks for the advice. I can send files and commands over ssh so I think it's better than ftp, though I haven't used ftp :)

Thanks :D

---

