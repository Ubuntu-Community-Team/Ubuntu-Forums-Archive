---
title: "atheros wifi card almost working"
date: 2005-12-06
forum: General Help
---

### Post by luibh on 2005-12-06
Just did a new install of ubuntu 5.10. I have a 3com 3CRPAG175 wifi card which has an atheros chip set. I set up the wireless network through the network settings in the admin menu. Set up my ethernet that way as well. My wireless router shows up, so I know ubuntu knows what it is and knows how to use it. Put in my WEP key. But once activated, I cannot access the internet through the wifi network. When I am plugged into the router, I can see that the router gives the card an ip address. The router log ```
Time                    Message                 Note
Dec/05/2005 22:02:45    DHCP lease IP           00-0E-6A-D7-2B-91
                        192.168.0.150 to linux

Dec/05/2005 22:02:37    Wireless PC connected   00-0E-6A-D7-2B-91
```
So I know the router sees it and gives it the correct ip address. Any ideas as to why I cannot access the internet through the wireless network? Any suggestions would be great. This is my last hurdle before the system is setup the way I want it. For now, atleast.

---

### Post by luibh on 2005-12-15
Installed GTKWifi 1.09 to see if that would fix anything, but no. It can see my router and I can add it to my prefered networks. GTKWifi even asked for the WEP key. When it tries to connect I can watch the icon in the taskbar, it will briefly get a signal (only 30-40% strength) and then will loose it. The DHCP will then fail. I really don't know why its doing this.

---

### Post by luibh on 2005-12-15
So, my wifi card works perfectly fine! At school. At my university, there is no encryption. Could my WEP key be the problem? I have entered both plain text and hexadecimal versions of the key, and vice versa. Any suggestions now?

---

### Post by wylfing on 2005-12-15
Seems like a safe bet that it's the way you're entering the key. Go into your router's setup and take a very close look at its WEP keys. Are there multiple keys? Are they hex or decimal? Note: you shouldn't be "converting" the keys or anything -- type them *exactly* as they are!

Also under System > Administration > Networking make sure that your wi-fi card is activated, and make sure it is selected as your default gateway device.

---

### Post by kingsidy on 2005-12-15
i installed ubuntu on a friend's laptop, and as i remember the wireless worked out of the box. It was an atheros card. So like wylfing said, it is prolly just the way you are putting the key in.

---

### Post by luibh on 2005-12-15
You both are probably right. As far as I know, I was entering the key the same way as my router, but then again, I've been known to make simple mistakes like that. I will double check it and see this evening.

---

### Post by luibh on 2005-12-15
WIRELESS IS UP AND RUNNING!!! So, my problem was that my WEP key wasn't set up correctly. On the router, the WEP is set to hex and I enter a key. On my laptop, the key has to be set to ASCII and entered the same way. Thanks for the suggestions.

---

