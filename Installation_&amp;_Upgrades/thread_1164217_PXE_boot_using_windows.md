---
title: "PXE boot using windows"
date: 2009-05-19
forum: Installation &amp; Upgrades
---

### Post by ffixcollector on 2009-05-19
I read this thread on how to pxe boot ubuntu
[HTML]http://ubuntuforums.org/showthread.php?t=327597&highlight=tftpd32[/HTML]

For the most part it makes sense, but a lot of the links no longer work, and a lot of the software has been updated.

Can anyone give me help on using this method of pxe-boot using the 9.04 ubuntu release and a XP release?

---

### Post by dstew on 2009-05-19
To start, here is the Jaunty netboot archive: [http://archive.ubuntu.com/ubuntu/dists/jaunty/main/installer-i386/current/images/netboot/](http://archive.ubuntu.com/ubuntu/dists/jaunty/main/installer-i386/current/images/netboot/)

The Windows tftpd32 software link in that How-To seems to work. Overall, the instructions in the How-To seem correct. Give it a try and see how far you get. I have done a PXE install before, but I used a Linux machine as the tftpd server instead of a Windows machine.

---

### Post by ffixcollector on 2009-05-19
I got a bit further. DHCP initiates, but then a prompt line starts blinking, and nothing happens. Here is the tftpd32 log
```
Rcvd DHCP Discover Msg for IP 0.0.0.0, Mac 00:0D:9D:80:AB:2E [19/05 13:09:32.890]
DHCP: proposed address 192.168.1.10 [19/05 13:09:34.853]
1240 Request 2 not processed [19/05 13:09:34.903]
Rcvd DHCP Rqst Msg for IP 0.0.0.0, Mac 00:0D:9D:80:AB:2E [19/05 13:09:36.916]
Previously allocated address 192.168.1.10 acked [19/05 13:09:38.859]
Connection received from 192.168.1.10 on port 2070 [19/05 13:09:38.859]
Read request for file <pxelinux.0>. Mode octet [19/05 13:09:38.869]
OACK: <blksize=1456,> [19/05 13:09:38.869]
Using local port 1085 [19/05 13:09:38.879]
1240 Request 2 not processed [19/05 13:09:38.909]
<pxelinux.0>: sent 1 blk, 0 bytes in 0 s. 0 blk resent [19/05 13:09:38.959]
```

---

### Post by ffixcollector on 2009-05-19
Is there any way to PXE boot from an existing .iso, say 9.04-desktop, or XP.iso?

---

### Post by dstew on 2009-05-19
The first post, about the DHCP dialog, looks OK generally. The BIOS sent two requests, the first was answered and an IP address given, the second ignored. For some reason the pxelinux.0 file transfer did not work. Is it possible the pxelinux.0 file is not in the correct directory? Maybe the DHCP server won't give a "File not found" error, but only a "zero bytes sent" error, I don't know.

The second part, can you use a CD or .iso, I think you can. I did not do it that way, but I have seen others that have. Usually, when someone has a network with a lot of similar computers, like at a school, the server has an .iso so all the PXE machines get the same system. You still need to set up the PXE boot as you are trying to do, you just have the installer get the system from the .iso instead of the over the internet.

---

### Post by ffixcollector on 2009-05-19
Got past that, 7-zip wasn't extracting the archive correctly. but now I get this after it boots to a blank screen

```
Connection received from 192.168.1.10 on port 57111 [19/05 15:20:57.768]
Read request for file <ubuntu-installer/i386/boot-screens/vesamenu.c32>. Mode octet [19/05 15:20:57.778]
OACK: <tsize=144392,blksize=1408,> [19/05 15:20:57.778]
Using local port 1052 [19/05 15:20:57.778]
<ubuntu-installer\i386\boot-screens\vesamenu.c32>: sent 103 blks, 144392 bytes in 0 s. 0 blk resent [19/05 15:20:57.949]
Connection received from 192.168.1.10 on port 57112 [19/05 15:21:00.232]
Read request for file <pxelinux.cfg/default>. Mode octet [19/05 15:21:00.232]
OACK: <tsize=131,blksize=1408,> [19/05 15:21:00.232]
Using local port 1053 [19/05 15:21:00.242]
TIMEOUT waiting for Ack block #0  [19/05 15:21:15.313]

```

---

### Post by dstew on 2009-05-19
Does the pxelinux.cfg/default file exist?

---

### Post by ffixcollector on 2009-05-19
Yes, here is the output
```
include ubuntu-installer/i386/boot-screens/menu.cfg

default ubuntu-installer/i386/boot-screens/vesamenu.c32

prompt 0

timeout 0
```

---

### Post by ffixcollector on 2009-05-19
When my client connect, the host tries to send pxelinux.cfg/default Afer a few seconds the window closes and nothing happens.
I tried using a different client and everything worked fine. Maybe its the computer.....is there an older netboot that might work?

---

### Post by ffixcollector on 2009-05-19
Anyone?

---

### Post by ffixcollector on 2009-05-20
> Hi,

Is it possible to extract the contents of an Ubuntu CD into a local folder on the Windows pc, and have the PXE laptop boot up and install from this folder rather than off the internet?

Or alternatively, find a way to 'share' the CDROM on the windows pc and have the laptop instal from there?

Thanks, hope to hear from someone soon

Cheers Steve

[http://ubuntuforums.org/showthread.php?t=327597&highlight=tftpd32&page=2](http://ubuntuforums.org/showthread.php?t=327597&highlight=tftpd32&page=2)

Considering this post is 2 years old........is there an answer?

---

### Post by dstew on 2009-05-20
Well, the answer is what you are working on -- trying to get a PXE BIOS to boot a Linux install image.

As far as your last question, if another client works (different PXE BIOS), maybe there is some BIOS setting that needs to be changed. Sounds like the connection is timing out before the configuration file is transmitted. Check your BIOS to see what options are there.

---

### Post by ffixcollector on 2009-05-20
Unfortunately its a hp-ze4560, with a limited BIOS and a broken cd drive.

---

### Post by dstew on 2009-05-20
If it does not have a PXE bios, but has another OS already installed, and can connect to the internet, you can try [unetbootin]("http://unetbootin.sourceforge.net/#install"). I have never done it, but it can install some form of Linux onto your local hard drive or USB stick over the internet.

---

### Post by septagent on 2009-06-02
Thank you guys for your work in this.  It helped me a ton with an experiment i am working on.  I would have been stuck for a long time if I didn't see your comment on 7-zip messing up the file.  


I believe that you can correct the most recent issue on your PXE boot by putting your TFTP server in "PXE Compatibility mode".  For example, I am using TFTpd32 on a windows box as the server, and had to set "PXE Compatibility" under the settings before my machine would accept the pxelinux.0 file.  

Let me know if you have any questions. Thanks,

---

