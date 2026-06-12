---
title: "Unable to connect net"
date: 2005-12-01
forum: General Help
---

### Post by rajendrabujji on 2005-12-01
I'm new to Ubuntu. I installed Ubuntu in My system.
But I'm unable to change the screen resolution.
I'm unable to connect to trhe internet also.what should i do?

---

### Post by manicka on 2005-12-01
[QUOTE=rajendrabujji]I'm new to Ubuntu. I installed Ubuntu in My system.
But I'm unable to change the screen resolution.[/QUOTE

System --> Preferences --> Screen Resolution

[QUOTE=rajendrabujji]
I'm unable to connect to trhe internet also.what should i do?[/QUOTE]

You may need to enter your connection settings manually rather than using dhcp

System --> Administration --> Networking

---

### Post by akiro.yamamoto on 2005-12-01
Details plese...
For the screen resolution did you try to click on :
System >> Preferences >> Screen Resolution
And change it from there..

---

### Post by akiro.yamamoto on 2005-12-01
If that won't work or can't you may have to edit your xorg.conf file to enable  
higher resolutions...
Of course you can try to use :
sudo dexconf to reconfigure your xorg.conf file automatically

---

### Post by xmastree on 2005-12-01
Search these forums for [resolution]("http://www.ubuntuforums.org/search.php?searchid=2748334").
You'll probably find that you need to manually add your screen refresh rates to xorg.conf

As for the net connection, what kind of connection is it? dial-up? LAN? Wireless? We'll need more info to help you there.

---

### Post by akiro.yamamoto on 2005-12-01
Are you using dial up or a broadband connection?

---

### Post by rajendrabujji on 2005-12-01
I tried to change the screen resolution from System->preferences->resolution but no use. Default values r fixed ur and  not allowing any changes.

   My system is in a LAN of Satyam computer services Limited.I need help to connect to net

---

### Post by xmastree on 2005-12-01
What's the resolution stuck at?
If you're using a LAN, does it have a DHCP server or do you need to manually set the ip address etc?
System > Administration > Networking is where you set that up. If you're not sure you should speak to the network administrator to find out what you need.

---

