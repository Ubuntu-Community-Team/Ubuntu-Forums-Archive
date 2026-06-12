---
title: "[SOLVED] Users in Lynksys WRT54G"
date: 2008-02-15
forum: Hardware &amp; Laptops
---

### Post by BobLand on 2008-02-15
My router works fine.  I began snooping around as Admin and found 2 users listed:
toshiba-user and Joseph-PC

I don't know if these are some kind of default user or they are on the wormy side and should be deleted.  

Thanks,
bobland

---

### Post by wieman01 on 2008-02-15
Are these user accounts or client PCs? If you are on wireless what sort of encryption do you use?

---

### Post by BobLand on 2008-02-15
Wireless and VPN are disabled.  The list is under DHCP Attive IP Table.

Besides the 2 known computers, me and my wife's, I have the following users under client host name:

PC11417150195 - 192.168.1.105
toshiba-user - 192.168.1.100       
tosihiba-user - 192.168.1.104
Joseph-PC - 192.168.1.103

Since the toshiba-use has the same address as the router I will assume it IS the router.  Perhaps, the other user is the wireless?  As far as the other two, I don't know.

I have a cable modem but nothing else connected to the router. I'm reluctant to delete them as I don't know if that will cause a problem with the router.

bobland

---

### Post by wieman01 on 2008-02-15
Very strange... wireless and Ethernet should both have the same IP address i.e. the router's address.

What do Toshiba and Linksys have in common I ask myself. Are you sure wireless is turned off?

---

### Post by BobLand on 2008-02-15
Every place that had a button to disable is clicked.  I checked this a few times.  There is no wireless enabled on this router.

---

### Post by 77midget on 2008-02-15
do any of these IPs ping?

---

### Post by amadeus266 on 2008-02-15
I have the same router. I think it keeps the name of any computers that have connected until the DHCP Lease expires. The different IP address are probably due to one of the PCs IP being changed. If you delete them, they will be recreated next time the PC connects.

---

### Post by Nicu Alecu on 2008-02-16
> **amadeus266 said:**
> I have the same router. I think it keeps the name of any computers that have connected until the DHCP Lease expires. The different IP address are probably due to one of the PCs IP being changed. If you delete them, they will be recreated next time the PC connects.

That is correct, if it's what you see under "Status / Local network / DHCP clients status". DHCP being ON by default, it creates a table of systems that, during time of use, have requested an automatically assigned IP addres. It clears up in time, but you can also clear it yourself,  but keep in mind that removing a DHCP client from the table means that the specific system that you are removing from the list will have to request another IP address after that. This is important only if you remove your own computer, of course ... :)

Anyways, since wireless is off and there's no other cable LAN connection, those system names you are seeing in the DHCP client list are completely irrelevant from the security point of view.

---

### Post by BobLand on 2008-02-16
Nicu,
That was the main part of the question I needed answering.

Thanks,
bobland

---

