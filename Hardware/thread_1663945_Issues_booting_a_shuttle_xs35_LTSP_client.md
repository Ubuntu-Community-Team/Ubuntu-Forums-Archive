---
title: "Issues booting a shuttle xs35 LTSP client"
date: 2011-01-10
forum: Hardware
---

### Post by vocoder42 on 2011-01-10
Not sure if this is the correct forum to post this question, but here goes:

I am running a Ubuntu LTSP server and it has been working great - using Shuttle x27d as the client.  They no longer make this model of shuttle, so I have ordered a different model, which is the x35.

The Shuttle x27d clients still boot without issue, but I can't seem to get the xs35 clients to boot - the xs35 clients start loading ubuntu, it shows Loading initrd.img, then Loading...and then usually just hangs (once or twice it's gone as far as showing the Ubuntu logo..but then always hangs there as well).

Any ideas how to troubleshoot what is going on? (or any ideas what may be happening?)  I'm really at a loss how to troubleshoot this.

---

### Post by vocoder42 on 2011-01-10
more information - after disabling the splash screen, this is what happens:

ipconfig: no devices to configure
/init: .: line 1: can't open /tmp/net-eth0.conf
3.498747 Kernel panic - not syncing: Attempted to kill init!
3.498819 Dumping ftrace buffer:
3.498874 (ftrace buffer empty)

any ideas???  could it be that the ltsp-image doesn't have the correct network device driver?  if this is the case, how do I add it?  looks like its a Realtek RTL8191SE

---

### Post by variona on 2011-02-03
You probably will need to add the module for the NIC to the initramdisk.
(use lspci to find out which, JMicron I guess, then you would need the jme module) 

HTH

variona

PS: I just looked it up on my LTSP client: RTL8191SE is the WLAN NIC, eth0 is jme!

that's what I did back then:
#++++++++modules for shuttle xs35 ++++++++++++++++++++++++++++++++
echo jme | sudo tee -a /opt/ltsp/i386/etc/initramfs-tools/modules
echo mii | sudo tee -a /opt/ltsp/i386/etc/initramfs-tools/modules
sudo chroot /opt/ltsp/i386/ update-initramfs -u
sudo chroot /opt/ltsp/i386/ /usr/share/ltsp/update-kernels
sudo ltsp-update-kernels
#++++++++modules for shuttle xs35 END+++++++++++++++++++++++++++++

---

