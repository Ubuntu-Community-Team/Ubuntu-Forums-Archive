---
title: "Wireless problem with Linksys"
date: 2008-09-13
forum: Hardware
---

### Post by Yori on 2008-09-13
Hello world.

I recently installed Ubuntu Hardy Heron on my Toshiba Satellite.  Try as I might, I can't get it to connect to my Linksys wireless router [WRT54-something].  After a bit of research, I found similar problems with the same model router.  Then, after I tried the same thing, the router died (I couldn't access the configuration, and the software it came with didn't detect it), and I had to go through the hard reboot process to get the router working again.

I'm running the latest Ubuntu Hardy Heron (8.04?), and I got this from the Terminal:
```
yori@yori-laptop:~$ lspci -nn | grep -i atheros
02:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter [168c:001c] (rev 01)
```

I also installed Wine and tried the setup program that the Linksys router generates, but it stuck at "Extracting Files, this may take 1 minutnee."

Would anyone help me solve my problem?

---

### Post by phidia on 2008-09-13
From the Ubuntu wiki on wireless [here]("https://help.ubuntu.com/community/WifiDocs") there is a link for wireless router [issues]("https://help.ubuntu.com/community/WifiDocs/RouterIssues")
The linksys referenced there isn't the same model as yours but it might be worth trying the fix anyway.

---

### Post by dvlong on 2008-09-13
> **Yori said:**
> Hello world.

I recently installed Ubuntu Hardy Heron on my Toshiba Satellite.  Try as I might, I can't get it to connect to my Linksys wireless router [WRT54-something].  After a bit of research, I found similar problems with the same model router.  Then, after I tried the same thing, the router died (I couldn't access the configuration, and the software it came with didn't detect it), and I had to go through the hard reboot process to get the router working again.

I'm running the latest Ubuntu Hardy Heron (8.04?), and I got this from the Terminal:
```
yori@yori-laptop:~$ lspci -nn | grep -i atheros
02:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter [168c:001c] (rev 01)
```

I also installed Wine and tried the setup program that the Linksys router generates, but it stuck at "Extracting Files, this may take 1 minutnee."

Would anyone help me solve my problem?
Recently I've gone through about 2 weeks of trying to get my wireless to work using the same router.  Most of my efforts were focused on my wireless drivers.  In the end, I reset my router to factory defaults, and then made the minimal adjustments (i.e. changed the ip address of the router) so that it worked without conflict on my network.  This did the trick for me.

---

### Post by Yori on 2008-09-14
Well, I got it fixed.  I guess resetting the router did it, along with trying every different type of WEP security options it gave me.  Well, thanks for your help, everyone!  If I ever need more help, I'll be sure to come straight here.

---

