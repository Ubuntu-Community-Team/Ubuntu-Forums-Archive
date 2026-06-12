---
title: "Thin Client can't find nbi.img"
date: 2009-10-13
forum: Installation &amp; Upgrades
---

### Post by glj on 2009-10-13
Two days of trying to install Ubuntu 9.04 on a server that will serve thin clients via LTSP has left me totally frustrated. During the installation from the Ubuntu 9.04 Alternate CD, much to my surprise I was never prompted regarding installing LTSP. With much searching through various forums, documentation, etc. for help on the subject of LTSP I attempted to get the LTSP setup working after the initial Ubuntu installation. I thought I had it.

When I fired up one of the thin clients (which boot from floppy disks, by the way), much to my dismay the client showed a TFTP error. Even though it's getting all the right info from the dhcp server, it can't find the /ltsp/i386/nbi.img. I can certainly understand why! There is no i386 directory in /var/lib/tftpboot. Rather than i386, the directory is amd64. And in that directory, nbi.img does not exist. There's a pxelinux.0 file in there which along with nbi.img is mentioned in /etc/ltsp/dhcpd.conf.

Is the pxelinux.0 file used when the NIC has a boot rom and the nbi.img file used when booting from a floppy disk? The nbi.img file simply does not exist on the server hard drive! Where does that file come from? One would think that installing ltsp on the server would take care of generating needed files. And why is the directory called amd64 rather than i386? Is that because the server has two Xeon processors and is running SMP?

As you can tell, I am very confused by the LTSP environment and I haven't been able to find a clear, detailed tutorial on installing it on Ubuntu/Edubuntu 9.04. The main thing I need right now is the nbi.img file, I guess. Then hopefully, if I put nbi.img in the /var/lib/tftpboot/ltsp/amd64 directory and make sure that my dhcpd.conf file points to the amd64 director rather than to an i386 directory, the thin client will load nbi.img and be happy. Does that sound reasonable? Then where can I get the nbi.img file?

---

### Post by glj on 2009-10-14
I rebuilt the ltsp client environment. The following command to rebuild the ltsp client environment allows the client to find the nbi.img file.```
sudo ltsp-build-client --arch i386
```Unfortunately, after the client gets its IP address, etc., via DHCP and the server transmits the nbi.img file (actually the file linked to by nbi.img) to the client, the client hesitates for a few minutes and drops into the BusyBox shell. Above the shell prompt, I observed an error message that said Error: Connect: Connection refused. That error message was followed by problems with mounting and so on. So although the architecture problem has been corrected, the clients still don't boot. Up to now I haven't found any solution to the "Connection refused" error. Still looking. LTSP shouldn't be this hard to install.

---

