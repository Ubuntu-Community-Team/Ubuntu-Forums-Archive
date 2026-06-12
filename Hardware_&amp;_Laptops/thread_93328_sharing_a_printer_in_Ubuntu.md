---
title: "sharing a printer in Ubuntu"
date: 2005-11-21
forum: Hardware &amp; Laptops
---

### Post by UbuntUser4389 on 2005-11-21
I have 2 computers connected through a router/hub. Both are running Ubuntu 5.10. I would like to share a printer between the two. Right now I am trying to use CUPS. But so far no luck. The printer is attached to my IBM Netvista computer (host name = ibm1600). I would like to print from my Dell 8400 (host name = ubuntu (it was the default!)). 

Now, I already added the printer to Ubuntu locally on ibm1600, and it works just fine. I go to add a printer on ubuntu and I tell it to use CUPS. In the spot where you have to type in the URI, i put "http://ibm1600:631/ipp/".  I tried to print a test page and this is what it said, "Printing: Unable to lookup host 'ibm1600' - Unknown host" in the printer properties. 

I am not sure what I am doing wrong. Please help!!

Thanks A TON!

---

### Post by sabitha on 2005-11-22
try to add your /etc/cups/client.conf on your server printer
change the line :
 #ServerName your_server_name or IP

than change the printer > global setting > detect LAN printers

hope this help

---

### Post by Buffalo Soldier on 2005-11-22
Assumptions:[list]
[*] Your server's IP (IBM Netvista's): 192.168.1.2
[*] Your client's IP (Dell 8400): 192.168.1.3
[/list]

1. Modify cupsd.conf file on your server: **sudo gedit /etc/cups/cupsd.conf**

FROM```
#Port 80
#Port 443
#Port 631
#
Listen 127.0.0.1:631
```TO```
#Port 80
#Port 443
**Port 631**
#
**#Listen 127.0.0.1:631**
```


FROM```
#BrowseAddress x.y.z.255
#BrowseAddress x.y.255.255
#BrowseAddress x.255.255.255
#BrowseAddress 255.255.255.255
BrowseAddress @LOCAL
#BrowseAddress @IF(name)
```TO```
#BrowseAddress x.y.z.255
#BrowseAddress x.y.255.255
#BrowseAddress x.255.255.255
#BrowseAddress 255.255.255.255
**#BrowseAddress @LOCAL**
**BrowseAddress 192.168.1.255**
```


FROM```
<Location />
Order Deny,Allow
Deny From All
Allow From 127.0.0.1
</Location>
```TO```
<Location />
Order Deny,Allow
Deny From All
Allow From 127.0.0.1
**Allow From 192.168.1.[color=red]3[/color]**
</Location>
```


FROM```
<Location /admin>
#
# You definitely will want to limit access to the administration functions.
# The default configuration requires a local connection from a user who
# is a member of the system group to do any admin tasks.  You can change
# the group name using the SystemGroup directive.
#

AuthType Basic
AuthClass System
## Restrict access to local domain
Order Deny,Allow
Deny From All
Allow From 127.0.0.1

#Encryption Required
</Location>
```TO```
<Location /admin>
#
# You definitely will want to limit access to the administration functions.
# The default configuration requires a local connection from a user who
# is a member of the system group to do any admin tasks. You can change
# the group name using the SystemGroup directive.
#

AuthType Basic
AuthClass System
## Restrict access to local domain
Order Deny,Allow
Deny From All
Allow From 127.0.0.1
**Allow From 192.168.1.[color=red]3[/color]**

#Encryption Required
</Location>
```

2. Modify clients.conf file on your client: **sudo gedit /etc/cups/client.conf**

FROM```
#ServerName myhost.domain.com
```TO```
#ServerName myhost.domain.com
**ServerName 192.168.1.[color=red]2[/color]**
```

3. Restarts cups on server and client side: **sudo /etc/init.d/cupsys restart**

4. Check status on server and client side: **lpstat -t**

---

### Post by arphe_el on 2005-11-22
i try to save client.conf in gedit 

but there is an error "Could not save the file "/root/etc/cups/client.conf" "

what do you think is the problem? i'm using the root access

---

### Post by arphe_el on 2005-11-22
sorry for the stupid question about saving client.conf does not work i forgot to type sudo before that.

anyway i have a second question i already set-up the client.conf as you suggested since i have the same problem with ubuntu user439 and also set-up the cupsd.conf my question is how can i create an access to print to server on the assumption that computer A with ip address 192.168.1.101 (server) and computer B with ip address 192.168.1.102 (client) in which i want the computer B to print to computer A

Please be patient since i'm a newbie to this but i found ubuntu linux much friendlier than other distro.

Thank you and GODspeed

---

### Post by Buffalo Soldier on 2005-11-24
substitute:[list]
[*] 192.168.1.[color=red]2[/color] with 192.168.1.[color=red]101[/color]
[*] 192.168.1.[color=red]3[/color] with 192.168.1.[color=red]102[/color]
[/list]

---

### Post by arphe_el on 2005-11-24
Dear Buffalo Soldier,

Thank you very much it works for me I also documented the details of it from downloading the printer driver, installing, configuring cupsd.conf & client.conf, also to mount it to gui.

Thank you it's a great info that helps us newbies. GODspeed!

---

### Post by robertc on 2005-11-29
Buffalo Soldier,

Truly brilliant!!!  Thanks

Robertc

---

