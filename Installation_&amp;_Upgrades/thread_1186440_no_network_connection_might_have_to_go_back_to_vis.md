---
title: "no network connection might have to go back to vista?"
date: 2009-06-13
forum: Installation &amp; Upgrades
---

### Post by geordiejohn on 2009-06-13
hello i have just installed ubuntu 9.04 on my dell inspiron 1501 laptop and i cannot connect to the internet,i can see a msg saying no network connection and i do not know how to connect to my home network?
i have already tried installing pclinux/mint/suse as i want to get away from vista,but not one distro connects auto to my home network like vista does.
thank you.

---

### Post by Amilo1718 on 2009-06-13
you filled in all necessary details (SSID, encryption,...) ?

---

### Post by geordiejohn on 2009-06-13
yes i did that but no luck

---

### Post by Neckbeard Stallman on 2009-06-13
In order for a Linux machine to talk to a WIndows machine (assuming that is what your other computers on the network are) you need SAMBA. quickest and easiest way to get it is Add/Remove then go to youtube and watch a video on how to configure it. Thats what I did. Took a couple network power cycles before I get the IP addresses correct. (order that they booted up) but it finnaly worked

---

### Post by Mark Phelps on 2009-06-13
Is it a wired connection or wireless connection.  Wireless continues to be a challenge to get working.

If it's wireless, you may have to resort to using NDISWrapper. Search the networking forum on that and you will find a number of posts detailing the steps to be followed to install that and get it working.

If it's wired, I'm presuming you're connecting to a router.  If you're trying to connect to the internet through ICS on an MS Windows machine, that's going to be very difficult to get working.

---

### Post by cariboo on 2009-06-13
To help we need you to run a few troubleshooting steps. Could you open an Applications-->Accessories-->Terminal and type the following command.

```
sudo lshw -C network > network.txt
```

The above command will list all your network hardware details and pipe it to a text file. You can copy the text file to your Windows partition, then paste it in your next post.

BTW threating to go back to windows is not the Ubuntu way of doing things. :)

---

### Post by geordiejohn on 2010-09-20
i have installed Ubuntu 10.04 and all working fine,i am just waiting for 10.10 now.
thank you.

---

