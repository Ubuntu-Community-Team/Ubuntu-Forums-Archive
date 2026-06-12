---
title: "Dapper + nat problem"
date: 2006-05-31
forum: Hardware &amp; Laptops
---

### Post by abyssbbs on 2006-05-31
Hello guys,

     I'm facing a nat problem with ubuntu dapper server (last updates) . The pc is p3-450 /64mb/3com 10/100 6gb hdd(500mb swap). This pc i want to use it as
a internet server for my home lan(the classics dns,dhcp for my lan and nat server. The internet iface (ppp0) is a dsl modem bridged to eth0 .  i'm trying to enable nat with the following script after ppp0 is up
--
modprobe ipt_MASQUERADE # If this fails, try continuing anyway
iptables -F; iptables -t nat -F; iptables -t mangle -F
iptables -t nat -A POSTROUTING -o ppp0 -j MASQUERADE
echo 1 > /proc/sys/net/ipv4/ip_forward
--

from the other pc's of my lan i can ping internet addresses , which mean that my dns forwards succesfully the requests to my provider,  but i can use anything else from internet (e.x. www or upgrading my system)
if i flush the rules of the script i cant ping anything outside my lan which i thing is right...

bellow is the grep of lsmod which shows that the necessery modules for internet sharing is loaded.. 
----

Module                  Size  Used by
ip_nat_irc              2688  0
ip_nat_ftp              3328  0
ip_conntrack_irc        6768  1 ip_nat_irc
ip_conntrack_ftp        7792  1 ip_nat_ftp
ipt_TCPMSS              4608  0
ipt_tcpmss              2432  0
ipt_state               2048  2
ipt_MASQUERADE          3456  1
ipt_LOG                 6912  0
iptable_mangle          2944  0
iptable_filter          3072  1
iptable_nat             7812  1
ip_nat                 19628  4 ip_nat_irc,ip_nat_ftp,ipt_MASQUERADE,iptable_nat
ip_tables              22400  8 ipt_TCPMSS,ipt_tcpmss,ipt_state,ipt_MASQUERADE,ipt_LOG,iptable_mangle,iptable_filter,iptable_n
at
ip_conntrack           51500  8 ip_nat_irc,ip_nat_ftp,ip_conntrack_irc,ip_conntrack_ftp,ipt_state,ipt_MASQUERADE,iptable_nat,i
p_nat
nfnetlink               6552  2 ip_nat,ip_conntrack
pppoe                  14400  0
pppox                   3720  1 pppoe
ipv6                  265600  14
af_packet              22920  2
ppp_generic            30100  2 pppoe,pppox
slhc                    7424  1 ppp_generic
dm_mod                 58936  1
md_mod                 72532  0
lp                     11844  0
floppy                 62148  0
parport_pc             35780  1
parport                36296  2 lp,parport_pc
psmouse                36228  0
pcspkr                  2180  0
rtc                    13492  0
serio_raw               7300  0
sis5595                15368  0
3c59x                  45608  0
mii                     5888  1 3c59x
shpchp                 45632  0
pci_hotplug            29236  1 shpchp
i2c_isa                 4992  1 sis5595
i2c_sis5595             7684  0
i2c_sis630              7948  0
i2c_core               21904  4 sis5595,i2c_isa,i2c_sis5595,i2c_sis630
sis_agp                 8708  1
agpgart                34888  1 sis_agp
evdev                   9856  0
ext3                  135688  1
jbd                    58772  1 ext3
ide_generic             1536  0
ohci_hcd               21892  0
usbcore               129668  2 ohci_hcd
ide_cd                 33028  0
cdrom                  38560  1 ide_cd
ide_disk               17664  3
sis5513                17032  1
generic                 5124  0
processor              23360  0
fbcon                  42784  0
tileblit                2816  1 fbcon
font                    8320  1 fbcon
bitblit                 6272  1 fbcon
softcursor              2304  1 bitblit
capability              5000  0
commoncap               7296  1 capability
------

i tryed the ipmasq modules with the same results...
i  also tryed different kernels such us 686 or server  same results
the strange is that sometimes...is just work
same configuration  in a different pc but with ubuntu breezy is works perfectly...

pls can u help me.. i want to try it more before i return to breezy...

thanks a lot 

p.s.
   Pls Tell the development Team to change the way that installing/defining new locale's, is just awfull , old breezy's way is just rocks in this point...

---

### Post by abyssbbs on 2006-05-31
any one pls..? just a tip...?

---

### Post by steve.horsley on 2006-05-31
I could be totally wrong, but I suspect you can't do NAT if you're bridging. The fact that your NAT rule is being added to the POSTROUTING chain might support this. If I'm right, you will have to re-number your LAN, disable bridging and enable IP forwarding instead.

---

### Post by abyssbbs on 2006-06-01
hm... you make me confused a bit...:) my knowledge in ubuntu is not so deep...
i have a router modem that i set it to bridge..  and then from the ubuntu box with pppoe i made the connection... after that a ppp0 iface appears.
the guide that i used is from tldp.org.. and and specifically nat for dial up systems (the only i found with ppp iface and some eth iface for internal lan...)

i dont know how to do it....

p.s. .. i install firestarter and gnome and suddenly it works.. but this is not the solution i want.. this machine strictly must be in text mode...:D

p.s.2 thanks for your answer:D

---

### Post by steve.horsley on 2006-06-01
OK, If it works when you install firestarter, then I'm talking rubbish. Sorry.

You could try looking for your firestsarter script (I'm sure it must generate one) and looking in there for differences to your hand configuration.

---

### Post by abyssbbs on 2006-06-02
i finally find the solution in one other  topic/post..( [http://ubuntuforums.org/showpost.php?p=1079468&postcount=5](http://ubuntuforums.org/showpost.php?p=1079468&postcount=5) ) although that i had enabled the ip forward/proc/sys/net/ipv4/ip_forward (1)  i had also to change the /etc/sysctl.conf (uncoment the ipforward line) and now works with ipmasq and this change of the sysctl 


thanks everyone

---

