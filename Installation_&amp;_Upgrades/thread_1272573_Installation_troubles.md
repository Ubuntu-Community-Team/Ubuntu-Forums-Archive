---
title: "Installation troubles"
date: 2009-09-22
forum: Installation &amp; Upgrades
---

### Post by jfmanamtr on 2009-09-22
I am not sure if this is the right forum for this, but it seems to be the closest fit. I am having troubles with my system after a fresh install. 
 
The issue is that I downloaded a copy of Ubuntu Server x64 9.04 from one of the mirrors. When I burn it to the disk, Brasero returns errors (saying that some files might be corrupt). I verified that the checksum for the CD & the chechsum for the ISO are the same. I have done a reinstall on my server (I messed upsomething & crashed it). After the reinstall, I can reboot the system & log in, but nothing works. I run DNS on it, but the DNS doesn't work. If I do a dig or an NS lookup, it says that no servers are available. Also, the network connection doesn't seem to work. PCs on my network can't ping the server by IP & the server can't ping other computers. I am not quite sure what is going on here & need a little direction. So any ideas?
 
~John

---

### Post by scragar on 2009-09-22
```
ifconfig
```
If your connection isn't listed try:
```
sudo ifconfig eth0 up
sudo dhcpcd eth0
```

---

### Post by jfmanamtr on 2009-09-22
That is the weird thing. The network adapter shows as up. I can ping the IP I set the adapter up with, but nothing else. The interface is up as far as I can tell. I can use ifdown eth0 to turn it off  & then ifup eth0 to turn it back on. But it can't talk to the outside world & nothing can talk to it.
 
~John

---

### Post by jfmanamtr on 2009-09-23
Ok. So, I have tried a few things. I tried using 8.04 to do the install thinking it may have been software related issue. The system still does the same thing after a fresh install of Ubuntu Server, the PC boots, but the DNS & network don't seem to work. I can't ping anything other than the static IP I assign to the NIC in the PC. If I try to do a dig, it comes back with a timeout & that there are no DNS servers available.
 
I also had a spare hard drive & tried an install on this drive using 9.04. The install went off without any errors. When I rebooted the PC, it came up to Boot Disk Failed. So I went in through a rescue disk. When the install finished, it looks like it didn't set the partion as active & didn't install GRUB. I fixed that using fdisk & reinstalling grub. I am still unable to communicate to anything other than the static IP that I set the PC to.
 
So, I am kinda stumped. The computer was working fine until I borked the OS (I was playing with Clonezilla). After I did that fresh install, this is what has been going on. So, any help or ideas would be greatly appreciated. Thanks!
 
~John

---

### Post by rreese6 on 2009-09-23
I always enjoy this kind of problem.

First, did you ever get the iso to burn without errors?
If not, you are not ready too install. the corrupted programs may very well be the ones that deal with the network

Let's assume you now have a good burn and an error free installation.
you open a terminal and type in "dmesg". you read through all of that and notice no problems...ok now you are ready to diagnose the IP issue.
 
Now lets look at the configuration of your network. if you have a router and it is set up for DHCp then you can run "dhclient" after you confirm that you have an IP Device (ifconfig).
after chclient do another ifconfig and see that it has received the ip address. if it has ping out to make sure you have connectivity.

Now once that is completed, you most likely want to set up a static IP
for you server. this can be done a couple of ways. you can just have the router always assign the same IP according to MAC address (easiest way). or you can do all the assignments manually through ifconfig, such as IP addr, Broadcast, netmask, gateway(GW) etc.
once you have set that up, you must take the network service down and bring it up.
Commands ifdown and ifup only control the interface (say eth0) not the network as a service.
once that is completed, you should be able to ping out again.
once that is finished set up your servers you want for your network.
Many people forget to "Bounce" the network service. (turn off and then on). 
Hopefully I explained that enough as when I am setting up servers, it seems intuitive to me and the methods I use change depending on server response. But that is the basic way I do it.
If you want to set up a DNS Server, then you need to understand that your local routing should know be set to know the difference between local access and public access. you would need to set it up to reroute all "look-up-failures" to an external DNS.  
This is starting to get too long and I don't want this to turn into a server network setup tutorial.

Let me know how things work out or if I have made errors in some fashion.

---

### Post by jfmanamtr on 2009-09-23
>  
First, did you ever get the iso to burn without errors?
If not, you are not ready too install. the corrupted programs may very well be the ones that deal with the network

 
I haven't been able to burn the ISO on my desktop without any errors. I burned a copy of 8.04 here at work without any errors & took it home where it is doing exactly the same thing. 
 
>  
Let's assume you now have a good burn and an error free installation.
you open a terminal and type in "dmesg". you read through all of that and notice no problems...ok now you are ready to diagnose the IP issue.

 
I have read through dmesg & see nothing unusual. It has a warning about the APCI timer, but that was there before hand & it worked.
 
>  
Now lets look at the configuration of your network. if you have a router and it is set up for DHCp then you can run "dhclient" after you confirm that you have an IP Device (ifconfig).
after chclient do another ifconfig and see that it has received the ip address. if it has ping out to make sure you have connectivity.

Now once that is completed, you most likely want to set up a static IP
for you server. this can be done a couple of ways. you can just have the router always assign the same IP according to MAC address (easiest way). or you can do all the assignments manually through ifconfig, such as IP addr, Broadcast, netmask, gateway(GW) etc.
once you have set that up, you must take the network service down and bring it up.
Commands ifdown and ifup only control the interface (say eth0) not the network as a service.
once that is completed, you should be able to ping out again.
once that is finished set up your servers you want for your network.
Many people forget to "Bounce" the network service. (turn off and then on). 
Hopefully I explained that enough as when I am setting up servers, it seems intuitive to me and the methods I use change depending on server response. But that is the basic way I do it.

 
I have a router, but at the moment the DHCP server on the router is turned off because I use the server I am setting up to do DHCP. I have the server setup as a Static IP address. I guess I could turn on the DHCP on the router & set the server to do DHCP to see if the computer will pull an IP from the router. I will give that a try & let you know what happens.
 
~John

---

### Post by jfmanamtr on 2009-09-23
I went home on my lunch break & I turned the DHCP server back on on my router. After I did this I set my desktop back to DHCP & it pulled an IP address from the router. I did a fresh install of Ubuntu Server 9.04. During the install when it tries to configure the network using DHCP, it says that the autoconfiguration failed because I either have no DHCP server setup or the server is running slowly. So, it looks like this maybe a hardware issue.I am going to try a few other things once I get off work & will update y'all as I can. Thanks for the idea!
 
~John

---

