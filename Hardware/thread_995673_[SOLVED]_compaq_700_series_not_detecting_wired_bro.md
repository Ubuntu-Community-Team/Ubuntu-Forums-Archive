---
title: "[SOLVED] compaq 700 series not detecting wired broadband connection"
date: 2008-11-28
forum: Hardware
---

### Post by avinash389 on 2008-11-28
hiii every one 

i've laoded my compaq 700 series laptop with ubuntu 
its not detecting my  broadband net connection 
which is working with my XP loaded desktop 

please kindly help me 
i'm new to ubuntu

---

### Post by prshah on 2008-11-28
> **avinash389 said:**
> 
i've laoded my compaq 700 series laptop with ubuntu 
its not detecting my  broadband net connection 
which is working with my XP loaded desktop 


From Windows XP, open a "Command Prompt" and give the following command```
ipconfig /all
``` Post back the output. This information will tell us what settings to use to set it up in Ubuntu.

Normally, a wired connection should work right out of the box, without any extra effort required.

In Windows XP, do you use a dial-up type connection (PPPoE)? Or do you just plug in the modem/router and surf without the need to connect/disconnect?

---

### Post by avinash389 on 2008-11-28
windows ip configuration
host name.........................:g-d3e3659b8b3a4
primary dns suffix ...............:
node type.........................:hybrid
IP routing enabled................: no 
WINS proxy enabled................:no

ethernet adaptor local aera connection :

    connection-specific DNS Suffix.:
    descreption....................:intel<R> pro/100 VE Network connection
physical address...................:00-14-85-97-F3-95
Dhcp Enabled.......................:yes
Auto configuration Enabled.........:yes
IP address.........................:123.245.192.138
subnetmask.........................:255.264.240.0
default gateway....................:123.234.192.1
DHCP server........................:124.125.5.141
                                    124.125.5.140
                                    220.445.236.85
                                    220.445.236.84

---

### Post by avinash389 on 2008-11-28
thank you for ur reply 
the above is the out put from 
ipconfig/all

and i dont use any dailup type connection 
all ive to do is go to my internet service provider web page and log in there and i can access net

---

### Post by prshah on 2008-11-28
> **avinash389 said:**
> 
all ive to do is go to my internet service provider web page and log in there and i can access net

So I assume you are using "cable" Internet (Eg, Hathway, Sify or so).

Looking at the output from Windows, your Internet should work automatically.. have you tried it? (By opening the Firefox browser to your ISP's login page?)

If that doesn't work, try this: Open a Terminal (Applications-Accessories-Terminal) and give the command ```
sudo dhclient eth0
``` If you get a line saying "No DHCP leases received" then it has failed; proceed to the next step. Otherwise, try your browser again, try to connect to the ISP's login page. If it still doesn't work, try the next step.

If none of the above work, try this: Right click the network manager icon (towards upper right, in the upper panel) and choose "Edit Connections". In the tab "Wired" look for an entry such as "Auto eth0". 

If this entry exists, click on it, then click on "Edit". 
Give it a name, and make sure both checkboxes "Connect automatically" and "System setting" are enabled.
Click on the tab "IPv4 settings" and choose "Manual" for "Method".
Click on "Add" next to the "Addresses" box, and enter your IP address as 123.245.192.138, your netmask as 255.264.240.0, and your gateway as 123.234.192.1. For DNS servers, enter ```
220.445.236.85,220.445.236.84
```

Click "OK" to save all the information, then "Close". From the terminal, restart networking```
sudo /etc/init.d/networking restart
``` and check if you can reach your ISP's login page.

Post back if you run into difficulties at any point, or if you still cannot connect.

---

### Post by avinash389 on 2008-11-28
> **prshah said:**
> So I assume you are using "cable" Internet (Eg, Hathway, Sify or so).

Looking at the output from Windows, your Internet should work automatically.. have you tried it? (By opening the Firefox browser to your ISP's login page?)

If that doesn't work, try this: Open a Terminal (Applications-Accessories-Terminal) and give the command ```
sudo dhclient eth0
``` If you get a line saying "No DHCP leases received" then it has failed; proceed to the next step. Otherwise, try your browser again, try to connect to the ISP's login page. If it still doesn't work, try the next step.

If none of the above work, try this: Right click the network manager icon (towards upper right, in the upper panel) and choose "Edit Connections". In the tab "Wired" look for an entry such as "Auto eth0". 

If this entry exists, click on it, then click on "Edit". 
Give it a name, and make sure both checkboxes "Connect automatically" and "System setting" are enabled.
Click on the tab "IPv4 settings" and choose "Manual" for "Method".
Click on "Add" next to the "Addresses" box, and enter your IP address as 123.245.192.138, your netmask as 255.264.240.0, and your gateway as 123.234.192.1. For DNS servers, enter ```
220.445.236.85,220.445.236.84
```

Click "OK" to save all the information, then "Close". From the terminal, restart networking```
sudo /etc/init.d/networking restart
``` and check if you can reach your ISP's login page.

Post back if you run into difficulties at any point, or if you still cannot connect.
thank you for your reply prshah, 
the command  

   sudo dhclient eth0
gives ,
NO DHCPOFFERS reciveg
no working details in persistent database - sleeping


so ive tried for the next suggestion
on right clicking the network manager i dint find any thing like edit connections but when i left clicked i had mannual configuration 
so when i clicked it opened network settings 

so please suggest me what to do ....i'm using ubuntu 8.04

---

### Post by avinash389 on 2008-11-28
actually i used net in my laptop ....
but i had a problem with my net.....both my desktop (with XP) n laptop with (ubuntu 8.04) dint detect network connection
it showed network cable unplugged even though cable is plugged in
so as directed by my internet srevice provider i changed my LAN settings into duplex mode its
now its working with XP loaded desktop but not with my laptop
is there some thing i can do with my laptop like in my desktop

---

### Post by prshah on 2008-11-28
> **avinash389 said:**
> 
it showed network cable unplugged even though cable is plugged in
so as directed by my internet srevice provider i changed my LAN settings into duplex mode 

Fist, check the link with ```
sudo mii-tool eth0
``` If it does not show a (auto-negotiated) link you can force it to a particular state with any one of these```
#for 100mpbs full duplex
sudo mii-tool -f 100baseTx-FD eth0
#for 100mpbs half duplex
sudo mii-tool -f 100baseTx-HD eth0
#for 10mpbs full duplex
sudo mii-tool -f 10baseT-FD eth0
#for 10mpbs half duplex
sudo mii-tool -f 10baseT-HD eth0
```

do _NOT_ use these commands if the first mii-tool commands reports a proper auto-negotiated link.

---

### Post by avinash389 on 2008-11-29
thank you prshah
for your reply that solves my problem

---

