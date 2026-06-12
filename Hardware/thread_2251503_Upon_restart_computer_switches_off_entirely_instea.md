---
title: "Upon restart computer switches off entirely instead of rebooting"
date: 2014-11-04
forum: Hardware
---

### Post by tigrefurry on 2014-11-04
Hey all, this is my first post on the Ubuntu forums, even though I've already got some years of experience with different Linuxen/*BSDs. It's the first time though that I run across a problem like the following:

(BTW: Note that [I already posted the same question on askubuntu]("http://askubuntu.com/questions/544662/upon-restart-computer-switches-off-entirely-instead-of-rebooting") which has been downvoted and, probably as a result, not received any answers. I've no clue why it got downvoted - so if anyone could give me a hint on what's wrong with it, that would be great! :-) )

I'm not entirely sure but I think it began with switching to  the Xubuntu desktop from the standard Ubuntu one that I first  encountered this issue - that was still under 14.04. I've since switched  to 14.10 but the problem persists:


  When I restart the computer, it doesn't do so immediately but first  switches off entirely. If I'm lucky it will switch back on after some  seconds, sometimes it just doesn't and stays dead. This has nothing to  do with the actual method used to initiate the reboot, the behaviour is  the same regardless of wether I use the Xfce menu -> shutdown options  -> restart, do so from the login screen or from the console using  'shutdown -r now'.

  
I dual boot with Windows 8.1 and Windows doesn't have that problem so  I suspect it must be (X)Ubuntu specific and not a hardware or BIOS/EFI  issue.

  My system is an Acer Aspire V3-771G laptop. During the last two years  that I've worked with this system I'd had installed OpenSUSE, Cent OS,  Mint and different flavours of Ubuntu and haven't come about this issue  before.

  
Maybe on here there's somebody who can indicate what might be wrong as I'm really clueless here!

Thanks!

---

### Post by WinEunuchs2Unix on 2014-11-04
Interesting.
o  What type of computer is it?
o  What Ubuntu version are you using?
o  What Kernel version are you using?
o  What does /var/log/syslog say when your "shutdown -r now" is entered?  

As an aside, in "normal" Ubuntu, "sudo reboot" is used to restart.  Don't know the actual "turn off" console command as this is a laptop connect to AC 24/7.

---

### Post by tigrefurry on 2014-11-06
First of all thanks for your reply and sorry that it took me while to answer it!

- Type of computer: Acer Aspire V3-771G, 64 bit, 8GB RAM, 120GB SSD drive, 750GB HDD, Primary Intel Graphics card with Optimus NVIDIA GeForce GT 630M
- Ubuntu Version: 14.10
- Kernel: 3.16.0-24-generic #32-Ubuntu
- syslog: Will add this information after having another go at it

As far as I understand it, reboot and shutdown -r now do the same thing under the bonnet.

---

### Post by tigrefurry on 2014-11-06
Now, here goes. These seem to be the last few messages in syslog after having invoked "shutdown -r now":

```

Nov   6 20:32:36 perpignan kernel: [ 1176.778132] dconf worker[2815]:  segfault at 4c4 ip 00007f178523b46f sp 00007f1775a46130 error 4 in  libperl.so.5.20.1[7f1785194000+1ac000]
Nov  6 20:32:36 perpignan dbus[1084]: [system] Activating service name='org.freedesktop.systemd1' (using servicehelper)
Nov  6 20:32:36 perpignan dbus[1084]: [system] Successfully activated service 'org.freedesktop.systemd1'
Nov   6 20:32:37 perpignan kernel: [ 1177.287062]  [drm:cpt_set_fifo_underrun_reporting] *ERROR* uncleared pch fifo  underrun on pch transcoder B
Nov  6 20:32:38 perpignan acpid: client connected from 3697[0:0]
Nov  6 20:32:38 perpignan acpid: 1 client rule loaded
Nov  6 20:32:44 perpignan dbus[1084]: [system] Activating service name='org.freedesktop.ConsoleKit' (using servicehelper)
Nov  6 20:32:44 perpignan dbus[1084]: [system] Successfully activated service 'org.freedesktop.ConsoleKit'
Nov   6 20:32:50 perpignan kernel: [ 1190.328546] [UFW BLOCK] IN=eth0 OUT=  MAC=4c:72:b9:fe:16:d3:00:1c:4a:73:40:da:08:00 SRC=192.168.178.1  DST=192.168.178.53 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=16530 DF  PROTO=TCP SPT=2090 DPT=14013 WINDOW=5840 RES=0x00 SYN URGP=0 
Nov  6  20:32:54 perpignan rsyslogd: [origin software="rsyslogd"  swVersion="7.4.4" x-pid="1156" x-info="http://www.rsyslog.com"] exiting  on signal 15.

```

And these are the first lines on rebooting:
```

Nov  6 20:33:35 perpignan rsyslogd: [origin  software="rsyslogd" swVersion="7.4.4" x-pid="1200"  x-info="http://www.rsyslog.com"] start
Nov  6 20:33:35 perpignan rsyslogd: rsyslogd's groupid changed to 104
Nov  6 20:33:35 perpignan rsyslogd: rsyslogd's userid changed to 101
Nov  6 20:33:35 perpignan kernel: [    0.000000] Initializing cgroup subsys cpuset
Nov  6 20:33:35 perpignan kernel: [    0.000000] Initializing cgroup subsys cpu
Nov  6 20:33:35 perpignan kernel: [    0.000000] Initializing cgroup subsys cpuacct

```

These kernel errors do look suspicious but I'm not enough of an expert to know how to interpret them... Thanks for everybody's help in advance!

---

### Post by MIJ-VI on 2014-11-07
IME a clean install rules every time (as does an LTS release of Ubuntu and its derivatives). It's why I use separate partitions for **/**, **swap** and **/home**. After deleting the invisible .folders and .preference files in the target drive's *home* folder, a clean install can be done without reformatting the **/home** partition. 
 
Xubuntu 14.10 (Utopic Unicorn)
[http://cdimage.ubuntu.com/xubuntu/releases/14.10/release/](http://cdimage.ubuntu.com/xubuntu/releases/14.10/release/)

If you can, consider doing a clean install of Xubuntu 14.10 on to an external USB hard drive (and installing the GRUB to the USB drive as well) for testing first before further risking your Windows 8.1 install.

Hmm... According to this, your notebook can take two hard drives:

"...Linux kernel needs these boot options: acpi_osi=Linux acpi_backlight=vendor. If the screen goes black during booting it is just because the backlight turned off. Try to turn it back on using Fn+RIGHT..."

Acer Aspire V3-771G [Linux Laptop Wiki]
[http://www.linlap.com/acer_aspire_v3-771g](http://www.linlap.com/acer_aspire_v3-771g)

My $0.02

As for dual booting Windows and GNU/Linux on the same hard drive? I got fed up with Windows updates repeatedly overwriting the GRUB and found that it was easier to use a separate hard drive for each OS, and after a while, even easier just to dump Windows all together.

---

### Post by WinEunuchs2Unix on 2014-11-08
> **tigrefurry said:**
> First of all thanks for your reply and sorry that it took me while to answer it!

- Type of computer: Acer Aspire V3-771G, 64 bit, 8GB RAM, 120GB SSD drive, 750GB HDD, Primary Intel Graphics card with Optimus NVIDIA GeForce GT 630M
- Ubuntu Version: 14.10
- Kernel: 3.16.0-24-generic #32-Ubuntu
- syslog: Will add this information after having another go at it

As far as I understand it, reboot and shutdown -r now do the same thing under the bonnet.

You're most welcome.  My apologies in turn for my slow response.

I don't have any experience with acer since the mid 90's when the ctrl+F2 key combination was a little wacky.

The shutdown instead of rebooting issue has been found with Asus computers and Ubuntu so this link my give you some clues: [http://www.asus.com/support/FAQ/1003769/](http://www.asus.com/support/FAQ/1003769/)

---

