---
title: "netboot installation"
date: 2009-07-19
forum: Installation &amp; Upgrades
---

### Post by Angva on 2009-07-19
Hello all,

I would like to install Ubuntu onto my laptop via Network boot. If anyone experienced in this kind of thing can offer any advice I'd really appreciate it. Here's my siuation. I am following the guide found here: [https://help.ubuntu.com/community/Installation/Netboot](https://help.ubuntu.com/community/Installation/Netboot)

I am confused on a couple of points. First, the guide says "One old Celeron 400Mhz with non-bootable CD-ROM, (kanga, 172.31.0.242). This is the target for installation." How am I supposed to know what IP address I should be using for MY installation target? 

Also, this IP address is oddly not used elsewhere in the guide (a special note for the etherboot floppy method notwithstanding). I guess the author made a mistake, and the tftp file example has the wrong IP. Maybe instead of .240, he meant .242? (Otherwise we have another mystery - where did the .240 IP come from? :)) See below (from that page, under "Enable the tftpd server"):

  service tftp
  {
        disable                 = no
        socket_type             = dgram
        wait                    = yes
        user                    = root
        server                  = /usr/sbin/in.tftpd
        server_args             = -v -s /var/lib/tftpboot
        only_from   = **172.31.0.240**/28
        interface   = 172.31.0.252
  }

One final question I have is about the "DHCP Note" towards the bottom. I am using a Linksys router which I use as my DHCP server, so I'm pretty sure I need to edit dnsmasq.conf as described in this note. It is not clear to me what IP addresses I should be using for the first two lines. I understand the gateway IP is set in the third ("dhcp-option") line, but I'm not sure about the first two.

I appreciate any advice...The laptop is in a sorry state at the moment. :|

Thanks in advance,
A

---

