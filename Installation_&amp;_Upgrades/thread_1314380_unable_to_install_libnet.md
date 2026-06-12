---
title: "unable to install libnet"
date: 2009-11-04
forum: Installation &amp; Upgrades
---

### Post by piyush.neo on 2009-11-04
i am using ubuntu 9.04
i downloaded libnet1.0 and gave following command
**piyush@black-hat:~/libnet-1.0$ ./configure**[I]
loading cache ./config.cache
Begining autoconfiguration process for libnet-1.0...
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking build system type... i686-pc-linux-gnu
checking for gcc... (cached) gcc
checking whether the C compiler (gcc  ) works... yes
checking whether the C compiler (gcc  ) is a cross-compiler... no
checking whether we are using GNU C... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for working const... (cached) yes
checking for a BSD compatible install... (cached) /usr/bin/install -c
checking whether make sets ${MAKE}... (cached) yes
checking for ranlib... (cached) ranlib
checking for ar... (cached) ar
checking for ln... (cached) ln
checking for strerror... (cached) yes
checking for pcap_open_live in -lpcap... (cached) no
checking low-level packet interface type... found SOCK_PACKET
checking how to run the C preprocessor... (cached) gcc -E
checking for net/ethernet.h... (cached) yes
checking for libnet_build_ip in -lnet... (cached) no
checking machine endianess... lil
checking if unaligned accesses fail... (cached) no
checking for sys/sockio.h... (cached) no
creating ./config.status
creating Makefile
creating test/Makefile
creating test/TCP/Makefile
creating test/Ethernet/Makefile
creating test/UDP/Makefile
creating test/ICMP/Makefile
creating test/Random/Makefile
creating test/OSPF/Makefile
creating util/Makefile
creating util/Get-mac/Makefile
creating example/Makefile
creating libnet-config
creating include/config.h
include/config.h is unchanged
[/I][B]
piyush@black-hat:~/libnet-1.0$ make
[/B][I]ar -cr lib/libnet.a src/libnet_resolve.o src/libnet_socket.o src/libnet_checksum.o src/libnet_prand.o src/libnet_version.o src/libnet_write_ip.o src/libnet_insert_ipo.o src/libnet_insert_tcpo.o src/libnet_error.o src/libnet_link_sockpacket.o src/libnet_packet_mem.o src/libnet_build_ip.o src/libnet_build_tcp.o src/libnet_build_udp.o src/libnet_build_arp.o src/libnet_build_ethernet.o src/libnet_build_icmp.o src/libnet_build_igmp.o src/libnet_build_dns.o src/libnet_build_snmp.o src/libnet_build_rip.o src/libnet_build_ospf.o src/libnet_asn1.o src/libnet_hex_dump.o src/libnet_if_addr.o src/libnet_port_list.o 
ranlib lib/libnet.a[/I]



[B]but still not getting libnet.h in /urs/include/libnet.h
am i missing something????.....
[/B]

---

### Post by cariboo on 2009-11-04
Is there a reason why you can't use the version in the repositories?

---

### Post by piyush.neo on 2009-11-04
thanks...i was not knowing that....
i installed libnet1 version1.1.2.1-4
but still when i am compiling a c program, its giving 
[B]error: libnet.h: No such file or directory

[COLOR=Red]which libnet version should i install to install libenet.h????

[/COLOR][/B]

---

### Post by dimhead on 2010-12-24
try sudo apt-get install libnet1-dev then check /usr/include | grep libnet
it should be there

---

### Post by piyush.neo on 2011-01-02
Sorry for late reply
> 
try sudo apt-get install libnet1-dev then check /usr/include | grep libnet
it should be there 	

yeah right file is there but still application using it was showing the file was missing....my PATH doesn't have /usr/include...may be thats why...!!!!
But then how my C programs run....:confused: .Anyway thanks for reply . At this point i don't remember the application for which i was using it.

---

