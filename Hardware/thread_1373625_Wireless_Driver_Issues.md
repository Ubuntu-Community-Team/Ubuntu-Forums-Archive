---
title: "Wireless Driver Issues"
date: 2010-01-05
forum: Hardware
---

### Post by nstaros on 2010-01-05
I've tried to find a problem like mine but it seems most people's are similar but not the same and their solutions don't work for me. So if the answer to this has been posted, forgive me.

I have an HP Mini 110-1134CL running Ubuntu Netbook Remix Koala 9.10. I keep getting the same problem everyone else has with installing this driver, but when the solutions are posted, they're too thick with jargon that I can't quite understand what they're telling me to do.

I've tried probably a dozen different ways to install the driver for the built in Wi-Fi card to no avail.

I'm not 100% new to Linux... but 99%. :confused:

Anyway I've tried running the broadcom driver that came with the LiveCD and it didn't seem to work... It said it finished installing, and I rebooted, then nothing.

I also tried some Linux .tar.gz from Broadcom's website and that didn't work. 



If anyone knows how to solve this, could you please give me a step-by-step? I realize it's a pain in the ***, but I'm new to this distro, and for the most part, linux in general.

Thanks in advance! :)

---

### Post by gordintoronto on 2010-01-06
People who can't give you a step-by-step CAN help you with the jargon.

Perhaps if you said, "I did such and such, and expected XXXX but instead YYYY happened," many people could help you.

If you've tried a dozen ways, your system may be fubared, and the best thing is to start over.

By the way, for wireless issues the computer itself is not important, it's the wireless adapter.  lspci will identify it.

---

### Post by nstaros on 2010-01-06
Thanks

What's lspci?

---

### Post by nstaros on 2010-01-06
Okay, I figured out lspci. According to it I have the BCM4312. I googled that and came upon [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

Now I extracted that and ran the makefile... and I don't think it did anything... Now I'm stuck.

---

### Post by nstaros on 2010-01-06
Okay one last update before I head to bed for the night...

I followed the instructions at [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx) and now the hardware manager says the b43 driver is running but I still can't search/connect networks...

(I did a fresh OS install to wipe all the previous changes before I did this)

Any ideas?

---

### Post by gordintoronto on 2010-01-06
Can you do this?

Right-click the network manager icon, select "edit connections," open the wireless tab, click on "add."  You will need to enter your router's ID, the type of encryption and the router's password.

---

