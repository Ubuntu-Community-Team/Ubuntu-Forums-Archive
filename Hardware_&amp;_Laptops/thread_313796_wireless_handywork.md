---
title: "wireless handywork"
date: 2006-12-06
forum: Hardware &amp; Laptops
---

### Post by lfys on 2006-12-06
With some effort (look [here](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)) I managed to make work a wifi card with Broadcom chipset.

Manually I do:

```
sudo rmmod ndiswrapper
sudo modprobe bcm43xx
``` Then I have to wait a few seconds (!!!) until eth2 becomes available.

Then I do
```
sudo iwlist eth2 scan
```

to finally make a connection with the network. (Maybe something els will do too?)

I've put the commands above in a startup script and apparantly this fails to work, probably because eth2 isn't available yet when the iwlist is asked.
After startup I do see that eth2 is there and when I ask for the iwlist by means of the terminal the ,etwork connection is made.

Thus I stay busy. Does someone have a solution?

---

### Post by trubblemaker on 2006-12-07
Stop ndiswrapper from being loaded:
 ```
echo 'blacklist ndiswrapper' | sudo tee -a /etc/modprobe.d/blacklist
```

load bcm43xx at boot time.
```
echo 'bcm43xx' | sudo tee -a /etc/modules
```

hope this helps

---

### Post by trubblemaker on 2006-12-07
should also mention that this would enable you to use you

/etc/network/interfaces file to configure the interface for you.

if you need help doing that post back here

---

### Post by lfys on 2006-12-14
And so my work ends.
Thank you.

---

