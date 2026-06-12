---
title: "Ubuntu drivers into Lubuntu"
date: 2012-11-19
forum: Hardware
---

### Post by saulofg on 2012-11-19
Hi, I have a Acer Netbook and its works with a bad performance with Windows. I installed Ubuntu 12 but it's works slow too, but I didn't have no hardware drivers problems, then I installed Lubuntu, but in this case my Wireless Network doesn't work. I didn't found Linux drivers in the web. Somone can help me?

---

### Post by |{urse on 2012-11-19
Please post the output of 
```
lspci | grep "Network"
```
This will help us determine what driver you need.

---

### Post by NikTh on 2012-11-19
Hi , 

Please open a terminal (CTRL+ALT+T) and execute bellow commands with order. (Active Internet connection required, eg: via Ethernet cable)

```
wget "http://ubuntuone.com/1kKCgeRTZHszxUdsSEekYz" -O ~/wirelessinfo
chmod +x wirelessinfo
sudo ./wirelessinfo
```The last command will produce a file named **netinfo.txt** inside your /home folder.
Click on "New Reply" and attach the file. [See here on how to attach a file]("http://i.stack.imgur.com/0E6qS.png") 

_Above is a script for debugging proposes. All your sensitive data are hidden for security reasons. _

Thanks

---

