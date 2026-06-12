---
title: "Hardy Heron Printing Problems"
date: 2008-05-16
forum: Hardware
---

### Post by ljpenton on 2008-05-16
Upgraded from Ubuntu Feisty to Hardy Heron, and am now having issues printing via my wireless print server.

Printing to my HP Color Laser Jet 2605dn, via the DPR-1260 print server in Feisty worked flawlessly when setup as a lpd device. Since the upgrade to Hardy Heron all print jobs are taking a very long time (15+ minutes) to complete.

I've deleted and re-added the printer as a lpd device, and even tried ipp and HP JetDirect with no difference.

It's not practical to direct attach the printer to the laptop as it's shared between multiple devices. Does anyone have any idea as to what I need to do to CUPS to speed things up?

---

### Post by Mega_slayer on 2008-05-16
I'm having a similar problem with a HP Laserjet 8100 that is available on a network. It worked fine with Feisty but now it is not working.

---

### Post by ljpenton on 2008-05-17
Managed to fix my problem. Here's what I did:

1. Took a look at my TCP connectivity by doing a ping to the print server, and found that 33% of all packets were being lost.
2. A bit of Google research on TCP performance configurations, and I managed to determine that TCP is not configured quite right.
3. Made the following changes to /etc/sysctl.conf

    $ sudo vi /etc/sysctl.conf

      # increase TCP max buffer size to 4 Mb
      net.core.rmem_max = 4194304
      net.core.wmem_max = 4194304
      # increase Linux autotuning TCP buffer limits
      net.ipv4.tcp_rmem = 4096 87380 4194304
      net.ipv4.tcp_wmem = 4096 65536 4194304
      #congestion control for wireless
      net.ipv4.tcp_congestion_control=veno

4. Loaded the new sysctl.conf file

   $ sudo sysctl -p

5. Did a ping to the print server, no packets being dropped now.

6. This cleared things up; however, I reconfigured the printer to use the HP JetDirect protocol anyway (it's an HP printer).

---

### Post by tondunn on 2008-07-03
Since upgrading to Hardy my network attached printer has stopped working.  I have an HP Laserjet 2300 which has a jetdirect card.  Restarting the printer allows me to print for a short while, but it then seems to timeout and I get a connection error message even though I can ping the IP address of the printer OK.  I've tried installing the HPLIP drivers, however it has made no difference.

---

### Post by ftabor on 2008-08-13
> **ljpenton said:**
> Managed to fix my problem. Here's what I did:

1. Took a look at my TCP connectivity by doing a ping to the print server, and found that 33% of all packets were being lost.
2. A bit of Google research on TCP performance configurations, and I managed to determine that TCP is not configured quite right.
3. Made the following changes to /etc/sysctl.conf

    $ sudo vi /etc/sysctl.conf

      # increase TCP max buffer size to 4 Mb
      net.core.rmem_max = 4194304
      net.core.wmem_max = 4194304
      # increase Linux autotuning TCP buffer limits
      net.ipv4.tcp_rmem = 4096 87380 4194304
      net.ipv4.tcp_wmem = 4096 65536 4194304
      #congestion control for wireless
      net.ipv4.tcp_congestion_control=veno

4. Loaded the new sysctl.conf file

   $ sudo sysctl -p

5. Did a ping to the print server, no packets being dropped now.

6. This cleared things up; however, I reconfigured the printer to use the HP JetDirect protocol anyway (it's an HP printer).


What did you use for the Device URI?  I have a  DPR1260, but I cna't seem to get it to work.

---

