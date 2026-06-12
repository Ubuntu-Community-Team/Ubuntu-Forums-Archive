---
title: "Firestarter and sharing to LAN computers"
date: 2005-11-28
forum: General Help
---

### Post by padamson on 2005-11-28
HI,

I am running Firestarter on ubuntu. The other computers that connect to the samba shares are running windows xp. 

The LAN is managed by a router, each computer gets an ip off the router.

I have added each ip address that will be using the shares to the "allow connections from host" policy also, I have added an "allow service" of samba for each ip address needed.

I still cannot connect to the shares on ubuntu from any of the lan computers, I can only connect to the shares if the firewall is turned off.

Am I setting the firewall up correctly???

Thanks

---

### Post by tonysathre on 2005-12-01
Server Message Block (SMB) is the protocol used for file and print sharing it runs on TCP 139 and UDP 445 allowing access to these ports should do the trick, also check your event tab in firestarter to see if there are any errors.

---

### Post by padamson on 2005-12-15
Hi,

I have opened those ports for the ip's on my lan. Still, when I try to connect to shares on the ubuntu machine, I get no response.

Any other ideas? I checked the event log and it doesn't look like there is anything unusual in them.

Thanks,

Paul

---

### Post by cstudent on 2005-12-15
I set my firestarter to allow from 192.168.1.1/255.255.255.0 

Your network ip may be slightly different, but this accepts connection from any computer on my LAN. I'm not a network expert, but I think it could also be entered as 192.168.1.1/24. Maybe someone who knows could educate us.

---

### Post by padamson on 2005-12-18
Hi,

thanks for the help guys, I can connect to the samba share from the windows machine on the network. The only problem now is that I can only connect using the ip address, when the firewall is turned off, i can use the computer name or the ip address.

thanks

---

### Post by chusome on 2006-03-13
I've seen this problem over and over on the forum and have yet to find an answer, if anyone knows PLEASE save us from our ignorance!!!!!!

---

### Post by AndyCooll on 2006-03-27
If you are running a LAN and Firestarter, on the pc with the shares you need to add a rule to Firestarter tab "Policy->Inbound Traffic Policy":

```
192.168.0.0/24
```

That will give permissions to all your other pc's to access the pc with the shares. If you are running Samba, additionally you need to a further rule allowing the Samba service

:cool:

---

### Post by prawn on 2006-06-03
[QUOTE=chusome]I've seen this problem over and over on the forum and have yet to find an answer, if anyone knows PLEASE save us from our ignorance!!!!!![/QUOTE]Maybe you've worked this out by now, but the trick is to  go to Edit > Preferences > Advanced Options and ensure "Block broadcasts from external network"  is unchecked. Not sure why name look-up requests are considered "external network" when they are on the LAN, but it certainly sorted out this problem for me.

---

### Post by Sam Lars on 2006-06-29
Thanks... I put in
```
192.168.0.0/24
```
And it works.  Great!  But it's always nice to know why it works, just in case I want to change it, or need to change it.  What does that 0/24 mean?

---

### Post by cyberdyne on 2006-06-29
Im brand new to Ubuntu and Linux so apologies early on for my ignorance.

Is Firestarter available for Ubuntu 6.06? If not, is there an alternative please?
Thank you.

---

### Post by cyberdyne on 2006-06-30
[QUOTE=cyberdyne]Im brand new to Ubuntu and Linux so apologies early on for my ignorance.

Is Firestarter available for Ubuntu 6.06? If not, is there an alternative please?
Thank you.[/QUOTE]

:( 
no problem, installed it anyway.

---

### Post by imiksu on 2006-07-04
[QUOTE=prawn]Maybe you've worked this out by now, but the trick is to  go to Edit > Preferences > Advanced Options and ensure "Block broadcasts from external network"  is unchecked. Not sure why name look-up requests are considered "external network" when they are on the LAN, but it certainly sorted out this problem for me.[/QUOTE]

Thank you. This one helps... Now it's working, is it possible to fix that? I mean, 192.168.*.* should be internal network?

---

### Post by speckman on 2006-10-23
i have a net connection on wlan0, and am sharing it with eth1 with another comp running ubuntu.  i couldnt figure out why firestarter wasn't working (it'll say "failed to start the firewall.  an unknown error occured.  Please check your network device settings and make sure you internet connection is active.), until i realized it WAS working anyway and then realized dns wasn't setup on my other computer.

so maybe someone in the future will try that!  :)
(in networking, DNS tab, add 192.168.1.1)

---

