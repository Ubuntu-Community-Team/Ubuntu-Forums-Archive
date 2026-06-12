---
title: "Not seeing Login Dialog on Kubuntu Thin Client"
date: 2008-08-19
forum: General Help
---

### Post by ssaes on 2008-08-19
I am trying to get a Thin Client GUI (KDE) to appear on a Dell laptop with a Kubuntu (8.04) server.  I have installed LTSP (and openssh), TFTP, and DHCP and they are all running.

When I boot the laptop it does a PXE Boot, obtains an IP address via DHCP, and downloads the pxelinux.0 file.

On the laptop screen I see pxelinux.cfg files being installed, vmlinuz loading, and then initrd.img runs.  This is followed by the introductory "Kubuntu" screen.  After this I was expecting a graphical login dialog (GUI) to be displayed; however, a terminal prompt is displayed instead.  I didnt see any error messages displayed during the process.

The terminal prompt reads "BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in shell (ash)" followed by the command line prompt "(initramfs)".

From a packet trace (Wireshark) I see that the PC is also requesting lts.conf file but from what I've read this is not required.

I am new to Ubuntu (my background is in TCP/IP networking) so I think I'm missing something basic.  I have done some Googling but cant find the missing piece.  I am hoping there is an expert out there that can help me out.

Thank You.

---

### Post by ssaes on 2008-08-19
I told you I was a beginner.  I rebooted the Ubuntu server and now the thin client is working properly.  Sorry about that.

---

### Post by nirmalraj on 2009-03-11
> **ssaes said:**
> I told you I was a beginner.  I rebooted the Ubuntu server and now the thin client is working properly.  Sorry about that.

i was messed-up with the thin client config file in ubuntu 8.10 intrepid, could you send me the configuration's to make it successfully!


regards
nirmal

---

