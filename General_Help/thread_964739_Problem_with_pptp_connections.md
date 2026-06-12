---
title: "Problem with pptp connections"
date: 2008-10-31
forum: General Help
---

### Post by dhtj on 2008-10-31
Hi all!
Im using ubuntu 8.10 and its cooler than 8.04 :lolflag:
In 8.04 an now in 8.10 i have a problem with configuring pptp connections
in ubuntu i can see my friends in lan but i haven't vpn
my windows looks like that

[img]http://www.download.bg/upl/attachments/1.1076.JPG[/img]
[img]http://www.download.bg/upl/attachments/2.7331.JPG[/img]
[img]http://www.download.bg/upl/attachments/3.9711.JPG[/img]
[img]http://www.download.bg/upl/attachments/4.2446.JPG[/img]
[img]http://www.download.bg/upl/attachments/5.9688.JPG[/img]

at the noon i will post screens from ubuntu too

ps:sorry for my bad english
ps2: if you have a free time i will be very hapy when you answer with pictures (where to write the ip's/dns/... in ubuntu) 

thank you very mutch in advance

and again sorry for my bad english i hope you are undarstend me :(

---

### Post by dhtj on 2008-10-31
here im configuring ubuntu network

[img]http://www.download.bg/upl/attachments/5.5562.JPG[/img]
my local network

[img]http://www.download.bg/upl/attachments/3.7997.JPG[/img]
it's working 

[img]http://www.download.bg/upl/attachments/1.5350.JPG[/img]
here im configuring "netlink" 

[img]http://www.download.bg/upl/attachments/2.5665.JPG[/img]
here i dont know what to do with this ticks

[img]http://www.download.bg/upl/attachments/4.5070.JPG[/img]
and netlink isnt starts 

[img]http://www.download.bg/upl/attachments/vpn.9583.JPG[/img]
why i cant click "add"

---

### Post by john_navarro on 2008-10-31
You need to add the "network-manager-pptp" package. You can do this from the command prompt with:

```
sudo apt-get install network-manager-pptp
```

Adding this will allow you to add PPTP connections.

---

### Post by dhtj on 2008-11-01
> **john_navarro said:**
> You need to add the "network-manager-pptp" package. You can do this from the command prompt with:

```
sudo apt-get install network-manager-pptp
```

Adding this will allow you to add PPTP connections.

```
dhtj@dhtj:~$ sudo apt-get install network-manager-pptp 
[sudo] password for dhtj: 
&#1063;&#1077;&#1090;&#1077;&#1085;&#1077; &#1085;&#1072; &#1089;&#1087;&#1080;&#1089;&#1098;&#1094;&#1080;&#1090;&#1077; &#1089; &#1087;&#1072;&#1082;&#1077;&#1090;&#1080;... &#1043;&#1086;&#1090;&#1086;&#1074;&#1086; 
&#1048;&#1079;&#1075;&#1088;&#1072;&#1078;&#1076;&#1072;&#1085;&#1077; &#1085;&#1072; &#1076;&#1098;&#1088;&#1074;&#1086;&#1090;&#1086; &#1089;&#1098;&#1089; &#1079;&#1072;&#1074;&#1080;&#1089;&#1080;&#1084;&#1086;&#1089;&#1090;&#1080;       
&#1063;&#1077;&#1090;&#1077;&#1085;&#1077; &#1085;&#1072; &#1080;&#1085;&#1092;&#1086;&#1088;&#1084;&#1072;&#1094;&#1080;&#1103;&#1090;&#1072; &#1079;&#1072; &#1089;&#1098;&#1089;&#1090;&#1086;&#1103;&#1085;&#1080;&#1077;&#1090;&#1086;... &#1043;&#1086;&#1090;&#1086;&#1074;&#1086; 
&#1055;&#1072;&#1082;&#1077;&#1090;&#1098;&#1090; network-manager-pptp &#1085;&#1077; &#1077; &#1085;&#1072;&#1083;&#1080;&#1095;&#1077;&#1085;, &#1085;&#1086; &#1077; &#1074; &#1089;&#1087;&#1080;&#1089;&#1098;&#1082;&#1072; &#1089;&#1098;&#1089; &#1079;&#1072;&#1074;&#1080;&#1089;&#1080;&#1084;&#1086;&#1089;&#1090;&#1080; &#1085;&#1072; &#1076;&#1088;&#1091;&#1075; &#1087;&#1072;&#1082;&#1077;&#1090;. 
&#1058;&#1086;&#1074;&#1072; &#1084;&#1086;&#1078;&#1077; &#1076;&#1072; &#1086;&#1079;&#1085;&#1072;&#1095;&#1072;&#1074;&#1072;, &#1095;&#1077; &#1087;&#1072;&#1082;&#1077;&#1090;&#1072; &#1083;&#1080;&#1087;&#1089;&#1074;&#1072;, &#1086;&#1089;&#1090;&#1072;&#1088;&#1103;&#1083; &#1077;, &#1080;&#1083;&#1080; &#1077; &#1076;&#1086;&#1089;&#1090;&#1098;&#1087;&#1077;&#1085; 
&#1089;&#1072;&#1084;&#1086; &#1086;&#1090; &#1076;&#1088;&#1091;&#1075; &#1080;&#1079;&#1090;&#1086;&#1095;&#1085;&#1080;&#1082; 
&#1054;&#1073;&#1072;&#1095;&#1077; &#1089;&#1083;&#1077;&#1076;&#1085;&#1080;&#1090;&#1077; &#1087;&#1072;&#1082;&#1077;&#1090;&#1080; &#1075;&#1086; &#1079;&#1072;&#1084;&#1077;&#1089;&#1090;&#1074;&#1072;&#1090;: 
  network-manager 
E: &#1055;&#1072;&#1082;&#1077;&#1090;&#1098;&#1090; network-manager-pptp &#1085;&#1103;&#1084;&#1072; &#1082;&#1072;&#1085;&#1076;&#1080;&#1076;&#1072;&#1090; &#1079;&#1072; &#1080;&#1085;&#1089;&#1090;&#1072;&#1083;&#1080;&#1088;&#1072;&#1085;&#1077;
```

I know you dont undarstand this language but it means: This package is missing but network-manager-pptp is replaced by network-manager

---

### Post by dhtj on 2008-11-01
oh nooooo
[https://bugs.launchpad.net/ubuntu/intrepid/+source/network-manager-pptp/+bug/259168](https://bugs.launchpad.net/ubuntu/intrepid/+source/network-manager-pptp/+bug/259168)

---

### Post by dhtj on 2008-11-02
> **john_navarro said:**
> You need to add the "network-manager-pptp" package. You can do this from the command prompt with:

```
sudo apt-get install network-manager-pptp
```

Adding this will allow you to add PPTP connections.

now i download this pack from my win
and evrything is allright
thank you very mutch
you can lock the theme :popcorn:

---

