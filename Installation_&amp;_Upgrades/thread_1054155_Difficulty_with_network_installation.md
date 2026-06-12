---
title: "Difficulty with network installation"
date: 2009-01-29
forum: Installation &amp; Upgrades
---

### Post by redmage123 on 2009-01-29
Hello all,

I'm having a bit of a vexing problem trying to install Ubuntu 8.10 over the network to a laptop.  I've set up my Ubuntu server (another laptop) to act
as the DHCP/TFTP/BOOTP server as well as an HTTP server.  

I'm able to get the pxelinux boot cycle working correctly.  It also downloads the preseed.cfg file correctly.  However, it fails when attempting to download /ubuntu/dists/intrepid/Release and /ubuntu/dists/intrepid/Release.gpg from my server (Running Kubuntu 8.10 with all appropriate .debs installed).  

The network is as simple as I can make it.  Basically, the server is connected to the booting client via a crossover cable.  No other 
devices exist.  The network isn't connected to any proxy servers or to the internet at all. 

Server's ip address - 192.9.200.1
Client's ip address - 192.9.200.2

There isn't anything wrong with the http server (I'm using Apache2.2), that i can find, since the client is able to download the preseed.cfg file via http, I've also stuck a separate laptop running Hardy Heron and done wgets.  Everything seem to work correctly.  I'm at a loss as to what to do next.  I can't tell what the exact problem is with the client, or even what the real failure is as there isn't a log file that I can check (unless there's a file that I don't know about).  I'm also attaching the relevant part of the preseed.cfg file.

### Mirror settings
# If you select ftp, the mirror/country string does not need to be set.
d-i mirror/protocol string http
d-i mirror/country string enter information manually
d-i mirror/http/hostname string 192.9.200.1
d-i mirror/http/directory string /ubuntu
d-i mirror/http/proxy string

# Suite to install.
#d-i mirror/suite string testing
# Suite to use for loading installer components (optional).
#d-i mirror/udeb/suite string testing
d-i mirror/suite string intrepid

Can anyone suggest what to try next?  I'm considering changing protocols to ftp or even NFS, but, the http is the simplest option and I'd really like it to work. 

Any help appreciated...

---

