---
title: "Changing MAC address."
date: 2005-09-07
forum: Hardware &amp; Laptops
---

### Post by Plank117 on 2005-09-07
I've been trying to change the MAC address of my NIC with the following command:
$ ifconfig eth0 hw ether 00:01:02:03:04:08

However, whenever I run this, I receive the following message:
SIOCSIFHWADDR: Operation not permitted

Can anyone help me out with this? Should I run this before I connect to a network? Should I blame society? Help me out.

---

### Post by amohanty on 2005-09-07
The MAC address also known as the ethernet address is the hardware address for your specific NIC and is part of the hw config of your NIC. It uniquely identifies your NIC. It cannot be changed though it can be faked, but only for nefarious purposes :) and requires quite a bit of networking knowledge and access to raw sockets.

Why do you want to do this btw?

AM

---

### Post by Plank117 on 2005-09-07
My Dad blocked my MAC address from our home network as a challenge, he wants to see if I can get around it. I'm using a dial-up connection right now. I'm cheating by asking for help, but I how else will I learn? We do this sort of stuff a lot, so its not like you'll be getting him mad or anything.

---

### Post by lehel.kulcsar on 2005-09-07
[QUOTE=Plank117]I've been trying to change the MAC address of my NIC with the following command:
$ ifconfig eth0 hw ether 00:01:02:03:04:08

However, whenever I run this, I receive the following message:
SIOCSIFHWADDR: Operation not permitted

Can anyone help me out with this? Should I run this before I connect to a network? Should I blame society? Help me out.[/QUOTE]
 Try the following in the command line:
$ cd /etc/init.d/
$ ./network stop
$ ifconfig eth0 hw ether 00:01:02:03:04:08
$ ./network restart

However you will have to do this after each reboot !

---

### Post by heimo on 2005-09-07
I'll modify a bit what was suggested above (this is untested):
> Try the following in the command line:
$ sudo /etc/init.d/networking stop
$ sudo ifconfig eth0 hw ether 00:01:02:03:04:08
$ sudo /etc/init.d/networking start



EDIT: Hmm... not actually sure if bringing down and starting networking is neccessary. You can try without.

---

### Post by s_p_a_r_k_y on 2005-09-07
yea i don't think its necessary to take down the interface. the reason you got permission denied (I'm assuming) is because you didn't do it as root. a normal user may not change (fake) the mac address. I believe your command was right, just stick a sudo in front of it. If it works, then simply stick it at the end of your /etc/init.d/network script so its executed everytime you boot (if thats what you want)

---

### Post by Plank117 on 2005-09-07
Thanks! That worked perfectly! I did have to stop/start the network card, I had a feeling that's what I needed to do, becuase changing the address while it was running would really screw up packet routing. Would it be possible for me to write a shell script that does this? Don't give me any code, I'd rather write it myself so I can actually learn something.

---

### Post by adun on 2005-09-07
Nothing would be easier, the code is nearly complete... :)

---

### Post by Plank117 on 2005-09-07
I'd have to check "Linux: In a Nutshell" for writing shell scripts, since I've never written one before.

---

