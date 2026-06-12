---
title: "wifi on eee 901 gone after update?"
date: 2009-08-14
forum: Hardware
---

### Post by sblanzio on 2009-08-14
Hi
Big problem this morning.
I started my eee901 and began to browse the internet, everything worked like always.
I clicked on the suggested software upgrading window giving OK,and it began to download/install. In the meantime i went away, and after some time (i guess30 mins) the netbook suspended. I guess the update process was done by that time.
When I came back I and restored that my ra0 was disappeared.
Rebooting didn't fix it. It seems my wifi card is gone.
```

sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: L1e Gigabit Ethernet Adapter
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: b0
       serial: 00:22:15:6b:e9:7b
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=ATL1E driverversion=1.0.0.7-NAPI duplex=full firmware=L1e ip=192.168.69.204 latency=0 link=yes module=atl1e multicast=yes port=twisted pair speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 4e:f4:58:0d:27:ff
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

I tried to load the previous kernel but didn't fixed it.
I looked for infos around on the net and I noticed that I do not have a "/etc/Wireless" directory tree but I cannot say if it ever was there.
My wifi has always worked since my first UNR ubuntu installation.

I forgot, toggling on and off the Fn+F2 or using the eeeapplet to switch on wifi just make appear a popup cloud which says "Wifi radio ON/OFF" but doesn't affect any other thing.

Help me plz!
tnx
sblnzio

---

### Post by sblanzio on 2009-08-14
Without any apparent reason my wi-fi card had been disabled in the BIOS configuration.
I rebooted and clicked F2 during the asus screen, and here i noticed my WLAN was "DISABLED". I enabled that, rebooted and now it works again.

Why this happened is not clear. Just hope this can be useful to anyody else.


Bad side, in the meantime i installed th DKMS drivers i found here
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/339891/comments/8](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/339891/comments/8)

i guess these drivers are obsolete. how do i revert this thing?
tyvm

sblanzio

---

### Post by HankB on 2009-08-14
I found the same problem on my 901 also running UNR and 9.04. And on a subsequent boot, video became scrambled - something I've never seen on my Eee.

I didn't look at BIOS settings because I have Karmic alpha installed on an SD card and WiFi and Video worked fine with that.

This was the update that seemed to screw things up:
```
root@bonsai:~# apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following NEW packages will be installed:
  dkms fakeroot netbook-dkms patch
The following packages will be upgraded:
  eeepc-acpi-utilities
1 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 307kB of archives.
After this operation, 1102kB of additional disk space will be used.
Do you want to continue [Y/n]? 

```

I more or less backed it out by removing what I thought were offending packages:
```
sudo dpkg --purge  dkms fakeroot netbook-dkms patch eeepc-acpi-utilities eeepc-tray
```

That removes some of the Eee specific extensions but now everything seems to work OK otherwise.

Note to self - never ever update the afternoon before I have an evening meeting presentation!!! ](*,)

---

### Post by sblanzio on 2009-08-14
yes that's the same upgrade as i remember.
I'm going to try all that another couple of days before "purging" all that as well.
I must say i notice something strange in the video too. Sometimes I get short flashes or symptoms of not perfect screen refresh. However i can't say if this is caused by the update or a little option i added recently to my xorg.conf (something like "acceloption uxa"...).

What is "interesting" is that now every time i shutdown my eeepc 901 something automatically disables my wifi card in the BIOS settings and the next time it remains disabled.

So now I'm forced to open the BIOS and enable my wifi everytime i want to switch on my eeepc... not so funny indeed.

Anyone has a hint on how to solve this? Maybe i'm gonna open another thread...

---

### Post by Yer_Grannie on 2009-10-10
Please do, same problem here with a eeepc 900 running eeebuntu 9.04.

Have to re-enable WiFi after every reboot, eeebuntu disables the setting while going down.

It seems to be related to some american airplane regulation that forbids WiFi to be used on netbooks.

I'm not on an airplane :p my netbook replaces my old desktop. Still I want to use WiFi if possible.

Anybody know of a solution?

These boot options:
force-hpet pciehp.pciehp_force=1 pciehp.pciehp_poll_mode=1

added to menu.lst (grub) and changing BOOT_WIFI from 1 to 0 in /etc/default/eeepc-acpi.local

made no difference.

Tnx!

---

### Post by sblanzio on 2009-11-03
definitive solution here (at least it worked for me).
[http://ubuntuforums.org/showpost.php?p=8217468&postcount=2](http://ubuntuforums.org/showpost.php?p=8217468&postcount=2)

(edit: sorry, link was wrong, now corrected.)

thanks to Richard

---

