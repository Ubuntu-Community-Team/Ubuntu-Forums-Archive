---
title: "samba hangs during file transfer"
date: 2004-12-29
forum: General Help
---

### Post by spb on 2004-12-29
I've got a ubuntu gnu/linux machine, a winxp machine, and a Mac.  

The ubuntu gnu/linux machine is serving and the other two are clients.  

Everything seems to work -- I connect and give my password.  I can see the partition and I can transfer small files.  

When I try to transfer large files (about 2MB or larger) the connection is lost.  

At first I thought that this was a problem on my WinXP machine, but today I connected the smb partitions on my Mac and had the same problem.  

Below is a portion of my log.smbd file.  I think that this shows my Mac connecting and the disconnecting 2 minutes later.  I can also include my smb.conf file although it doesn't contain anything more complicated than what is included in the beginner samba pages.  I also have a tcpdump from both the windows machine and mac although I can't make heads or tails of this

Thanks for any help you can give,
sb

[2004/12/29 13:55:07, 1] smbd/service.c:make_connection_snum(648)
  vesper (192.168.2.5) connect to service user initially as user nobody (uid=65534, gid=65534) (pid 17210)
[2004/12/29 14:00:16, 0] lib/util_sock.c:write_socket_data(430)
  write_socket_data: write failure. Error = Broken pipe
[2004/12/29 14:00:16, 0] lib/util_sock.c:write_socket(455)
  write_socket: Error writing 45 bytes to socket 23: ERRNO = Broken pipe
[2004/12/29 14:00:16, 0] lib/util_sock.c:send_smb(647)
  Error writing 45 bytes to client. -1. (Broken pipe)
[2004/12/29 14:00:16, 1] smbd/service.c:close_cnum(837)
  vesper (192.168.2.5) closed connection to service user
[2004/12/29 14:02:16, 0] lib/util_sock.c:write_socket_data(430)
  write_socket_data: write failure. Error = Connection reset by peer
[2004/12/29 14:02:16, 0] lib/util_sock.c:write_socket(455)
  write_socket: Error writing 168 bytes to socket 23: ERRNO = Connection reset by peer
[2004/12/29 14:02:16, 0] lib/util_sock.c:send_smb(647)
  Error writing 168 bytes to client. -1. (Connection reset by peer)
[2004/12/29 14:02:16, 1] smbd/service.c:close_cnum(837)
  vesper (192.168.2.5) closed connection to service scott
[2004/12/29 14:22:56, 1] smbd/service.c:close_cnum(837)
  pernod (192.168.2.3) closed connection to service scott
[2004/12/29 14:30:29, 1] smbd/service.c:make_connection_snum(648)
  vesper (192.168.2.5) connect to service user initially as user nobody (uid=65534, gid=65534) (pid 20032)
[2004/12/29 14:31:19, 1] smbd/service.c:close_cnum(837)
  vesper (192.168.2.5) closed connection to service user

---

### Post by spb on 2004-12-29
Here's one more hint... 

I can seem to be able to pull as much data as I want from the server to the clients, but I can't transfer data from the clients to the server without crashing.

There must be something stupid in my settings that I don't see!  

Here is my smb.conf file.  

[global]
  workgroup = HOME
  printcap name = cups
  printing = cups
  security = user
  username map = /etc/samba/smbusers
  encrypt passwords = true
  dns proxy = no
#  name resolve order = host wins bcast
  socket options = TCP_NODELAY

[homes]
   comment = Home Directories
   browseable = yes
   writable = yes
   create mask = 0700
   directory mask = 0700

---

### Post by spb on 2004-12-31
So it appears that I can ping from the Mac to the Linux box faster than I can ping from the linux box to the Mac.  So I began to think that maybe the NIC is bad on the linux machine.  If I run ifconfig eth0 I find:

eth0      Link encap:Ethernet  HWaddr 00:C0:F0:6D:3F:C8
          inet addr:192.168.2.2  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::2c0:f0ff:fe6d:3fc8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:979631 errors:3 dropped:131071 overruns:0 frame:0
          TX packets:1029966 errors:4 dropped:0 overruns:0 carrier:5
          collisions:0 txqueuelen:1000
          RX bytes:175912499 (167.7 MiB)  TX bytes:348046143 (331.9 MiB)
          Interrupt:5 Base address:0xd000

The question that I have is: Is it normal for 3-4 errors in the RX/TX packets?  What do other people get when the run "ifconfig eth0"?

---

