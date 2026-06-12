---
title: "I need help installing over a network"
date: 2009-08-31
forum: Installation &amp; Upgrades
---

### Post by Scubdup on 2009-08-31
Thanks for any help you can offer.

I have a sony vaio laptop with a broken CD drive which was put in by cretins who threaded all the screws.

It purports to be abl to boot from a removeable device but I have had no joy getting it to do so.

The CD drive broke halfway through loading Ubuntu from a liveCD and now when swithced on it says "Error finding operating system"

The only option I can see is doing a network installation (and I've tested the laptop's ability to do this and it seems to try - looking for a dhcp server to boot from)

My problem is this - I know nothing about DHCP servers and I cannot for the life of me set up this machine (a desktop running 9.04) to act as the DHCP server and allow the laptop to boot from it.

I have read a number of guides which don't quite work and I'd love some help.

Thanks

---

### Post by stlsaint on 2009-08-31
a easier way would be to create bootable usb and install from usb a few questions to better help you.what error are you getting thats stopping you from booting to media...and what have you tried to boot? is your bios setup to be able to removable media? (ie usb boot enabled) what kind of laptop are you using?

---

### Post by Scubdup on 2009-08-31
Hi there stlsaint.

The laptop is a Sony Vaio vgn-a217m with Intel Pentium-M 1.6GHz Centrino Processor, 512MB DDR SDRAM, and 80GB Hard Drive.

As I say, in the BIOS it says it can boot from a removable device, but I've tried a bootable USB and had no joy. It seems to ignore it.

I have had a look at several guides and I seem to need to:-
[LIST=1]
[*]Set up my desktop as a DHCP server
[*]Format the Boot image on the PC somewhere where it will be found by the laptop
[*]Boot the laptop from the network
[/LIST]

3 seems easy enough. I've tested the laptop and it looks for a dhcp server fr a while before giving up.

The other two seem very tricky.

I cannot figure it out because most of the guides assume some knowledge and ability and I'm utterly lacking.

[http://nixcraft.com/getting-started-tutorials/474-ubuntu-linux-network-installation-using-boot-server.html](http://nixcraft.com/getting-started-tutorials/474-ubuntu-linux-network-installation-using-boot-server.html)

I fall down in this one at "Configure DHCP server as per your requirements."

And that seems to be the sticking point with all the guides - I cannot setup the DHCP server.

I've downloaded the netboot.tar.gz from [http://archive.ubuntu.com/ubuntu/dists/jaunty/main/installer-i386/current/images/netboot/](http://archive.ubuntu.com/ubuntu/dists/jaunty/main/installer-i386/current/images/netboot/)

But don't know where to extract it to so it is found by the laptop on bootup.

Again, thanks for any help.

---

### Post by Scubdup on 2009-08-31
Also in my ham-fisted eforts I seem to have buggered-up dhcp3-server, whcih now seems to [fail] when I try to run it..

I just tried to purge it and reinstall but that didn't work either...

```
sam@ubuntudell:~$ sudo cd /var/lib/tftpboot
[sudo] password for sam: 
sudo: cd: command not found
sam@ubuntudell:~$ sudo apt-get --purge remove dhcp3-server
[sudo] password for sam: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  menu libcap1
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED
  dhcp3-server* gadmin-dhcpd*
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
After this operation, 1196kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 137798 files and directories currently installed.)
Removing gadmin-dhcpd ...
Purging configuration files for gadmin-dhcpd ...
Removing dhcp3-server ...
 * Stopping DHCP server dhcpd3                                           [fail] 
Purging configuration files for dhcp3-server ...
Processing triggers for man-db ...
Processing triggers for menu ...
sam@ubuntudell:~$ sudo apt-get dhcp3-server
E: Invalid operation dhcp3-server
sam@ubuntudell:~$ sudo apt-get install dhcp3-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  menu
Use 'apt-get autoremove' to remove them.
Suggested packages:
  dhcp3-server-ldap
The following NEW packages will be installed
  dhcp3-server
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/372kB of archives.
After this operation, 885kB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package dhcp3-server.
(Reading database ... 137773 files and directories currently installed.)
Unpacking dhcp3-server (from .../dhcp3-server_3.1.1-5ubuntu8.1_i386.deb) ...
Processing triggers for man-db ...
Setting up dhcp3-server (3.1.1-5ubuntu8.1) ...
Generating /etc/default/dhcp3-server...
 * Reloading AppArmor profiles ...                                       [ OK ] 
 * Starting DHCP server dhcpd3                                                   * check syslog for diagnostics.
                                                                         [fail]
invoke-rc.d: initscript dhcp3-server, action "start" failed.

```

---

### Post by Scubdup on 2009-09-01
Found some good instructions for using dnsmasq which sounds a lot easier than dhcp-server...

[http://blog.webworxshop.com/2009/06/24/even-easier-netboot-installation](http://blog.webworxshop.com/2009/06/24/even-easier-netboot-installation)

The only problem I envisage is sorting out my router and the DHCP settings.

My router (Huawei Echolife) has various DHCP settings and currently is set as the DHCP server. I can either turn it to "off" or "relay".

If I set up dnsmasq correctly so that the ubuntu desktop is the dhcp server, should my router be set to "off" or "relay"?

---

### Post by DFlame on 2009-09-01
Here's two alternate suggestions to what you are doing now...

[PXE boot Ubuntu from Windows](http://www.lockstockmods.net/2008/04/07/pxe-install-ubuntu-via-windows/)

And if you can remove the hard disk from the laptop and place it in another computer (with a 2.5" to 3.5" converter or using a USB caddy), you could install a unetbootin image to it, then transfer it back to the laptop to start the installation. Unetbootin would copy the essential files and make the drive bootable. There's a few tutorials on it hanging around somewhere...

---

### Post by Scubdup on 2009-09-02
Thanks DFlame,

I don't have a Windows machine, and I think the HDD in this machine is quite hard to remove, which is why I've been looking into netbooting, but as it is proving far more difficult than I thought it would be, I'm starting to consider removing the HDD.

Also, I'm thinking about trying the usb drive or external harddrive installation as a remoable device. Although it didn't work when I tried it, it seems there can be a few problems with the usb drive images.

Thanks again for taking time to reply. Much appreciated.

---

