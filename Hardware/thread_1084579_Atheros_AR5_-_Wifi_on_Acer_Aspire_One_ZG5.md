---
title: "Atheros AR5 - Wifi on Acer Aspire One ZG5"
date: 2009-03-02
forum: Hardware
---

### Post by funkyali on 2009-03-02
Hi,

I just bought a Acer Aspire One ZG5. I installed ubuntu 8.10 and installed all the updates via a wired connection. I tried to fix the wireless problem by following this tutorial [https://help.ubuntu.com/community/AspireOne#Install](https://help.ubuntu.com/community/AspireOne#Install). but it is still not connection.

I had no problems getting the latest madwifi file. I then untar the file did the make and make install and then I did the last modprobe it does not say anything

If I do ifconfig I do not see my wifi there. I do see the item when I go to the Hardward drivers menu it does display it there.

Any thing else I coudl try?

Thanks in advance.

---

### Post by 5BallJuggler on 2009-03-02
what does the output of lspci give you?

if you see 

```

03:00.0 Ethernet controller: **Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)**
``` 

then the following method will work,

[http://ubuntuforums.org/showthread.php?t=1054629](http://ubuntuforums.org/showthread.php?t=1054629)

of course if the card is different, the above may still work

---

### Post by funkyali on 2009-03-02
Thanks, I shoudl have tried the old reboot option as I restarted the machine and it then picked up the wireless adaptor and network and is now happyly connected thanks for your post.

---

### Post by LuciusMare on 2009-09-19
So i will ask here,i didnt get to connect to my wifi with Ubuntu netbook remix (9.04),and more things didnt work,so i switched to "regular" 9.04.There,my wifi worked well,i hit the switch...nothing happened.Restart,and as said,couldnt connect,scan,nothing.So i hit it again,put on the floor and waited,and it worked.I am using it pretty much out of the box,so no madwifi,but the led doesnt work either.

---

### Post by LuciusMare on 2009-09-19
So i will ask here,i didnt get to connect to my wifi with Ubuntu netbook remix (9.04),and more things didnt work,so i switched to &quot;regular&quot; 9.04.There,my wifi worked well,i hit the switch...nothing happened.Restart,and as said,couldnt connect,scan,nothing.So i hit it again,put on the floor and waited,and it worked.I am using it pretty much out of the box,so no madwifi,but the led doesnt work either. edit: oops,wrong thread,sorry edit2:God,double post,sorry.

---

