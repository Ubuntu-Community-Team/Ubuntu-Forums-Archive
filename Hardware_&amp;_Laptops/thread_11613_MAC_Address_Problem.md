---
title: "MAC Address Problem"
date: 2005-01-18
forum: Hardware &amp; Laptops
---

### Post by hitchhiker on 2005-01-18
My Spec -

ECS L7VTA Motherboard
AMD 2000+ CPU
1024 Mb RAM

The motherboard has a VIA chipset with onboard LAN, a VIA Rhine II.
This was fine in both Win XP and Ubuntu.

The problem started when I installed Windows manager and all it's components via Symantic although I didn't touch any network settings.

The problem -

My MAC address has somehow been changed to 00-00-00-00-00 and Ubuntu will no longer connect to the net or even speak to my router.
It will work in Win XP because my router cloned my original MAC address when I first installed it. 
In Win XP, the result of IPCONFIG /ALL is -

Windows IP Configuration

        Host Name . . . . . . . . . . . . : andrew
        Primary Dns Suffix  . . . . . . . :
        Node Type . . . . . . . . . . . . : Unknown
        IP Routing Enabled. . . . . . . . : No
        WINS Proxy Enabled. . . . . . . . : No

Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : VIA Rhine II Fast Ethernet Adapter
        Physical Address. . . . . . . . . : 00-00-00-00-00-00
        Dhcp Enabled. . . . . . . . . . . : No
        IP Address. . . . . . . . . . . . : 192.168.1.100
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 192.168.1.1
        DNS Servers . . . . . . . . . . . : 194.168.4.100
                                            194.168.8.100

In Ubuntu, ifconfig -a does not show the eth0 card although it is listed in /etc/network/interfaces.

Any ideas how I can get my original MAC address back?

Thanks,

HH.

---

### Post by hitchhiker on 2005-01-18
Ok, this problem had been plaguing me all morning whether I booted into Win XP or Ubuntu. Now it's working again and an ifconfig -a gives my real original MAC address.
I'm a bit stumped as to what the problem was and what fixed it.

I was playing around with some MAC address changing software in Win XP to fix the problem but that should only change it in software and then, because the program was a trial version, it wouldn't let me set the original address.

Anyway, I'm confused but it's working.

Still, any suggestions appreciated.

HH.

---

### Post by nocturn on 2005-01-18
[QUOTE=hitchhiker]Ok, this problem had been plaguing me all morning whether I booted into Win XP or Ubuntu. Now it's working again and an ifconfig -a gives my real original MAC address.
I'm a bit stumped as to what the problem was and what fixed it.

I was playing around with some MAC address changing software in Win XP to fix the problem but that should only change it in software and then, because the program was a trial version, it wouldn't let me set the original address.

Anyway, I'm confused but it's working.

Still, any suggestions appreciated.

HH.[/QUOTE]

I'm guessing: hardware glitch.

---

### Post by hitchhiker on 2005-01-18
The problems come back again now  :confused: 

Output from Win XP System Information -

IP Address	192.168.1.100
IP Subnet	255.255.255.0
Default IP Gateway	192.168.1.1
DHCP Enabled	No
DHCP Server	Not Available
DHCP Lease Expires	Not Available
DHCP Lease Obtained	Not Available
MAC Address	00:00:00:00:00:00
I/O Port	0x0000C800-0x0000C8FF
Memory Address	0xE8131000-0xE81310FF
IRQ Channel	IRQ 23


Help  :sad: 

HH.

---

### Post by jackmacokc on 2005-01-20
if you're getting a mac address of all zero's...then its definately a hardware problem..not a problem with win/ubuntu. thats what you get for relying on motherboard integrated crap  [-X

---

