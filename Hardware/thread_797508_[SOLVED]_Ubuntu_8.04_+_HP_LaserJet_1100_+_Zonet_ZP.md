---
title: "[SOLVED] Ubuntu 8.04 + HP LaserJet 1100 + Zonet ZPS3603 printer server = Does not pri"
date: 2008-05-17
forum: Hardware
---

### Post by GiveLove on 2008-05-17
Hello people,

I've run into a problem since doing a fresh install of Ubuntu 8.04 recently. I cannot print over the network to my HP LaserJet 1100 which is connected to a Zonet ZPS3603 print server. 

This same setup worked just fine on Ubuntu 7.04 & 6.10, and also Fedora versions 5 & 6. 

I created a new printer in System-->Administration-->Printing.
For the connection, I tried both "Appsocket/HP JetDirect", and "LPD/LPR Host or Printer" using the static IP of 192.168.1.100 of the print server. Those did not work. I tried the other driver options besides the recommended one for this printer and those did not work either. 

When sending a "Print Test Page", the job gets sent and the printer light starts blinking, you wait and wait, but nothing happens. When I manually clear the printer buffer, after a few minutes the printer light starts blinking again, like it's getting ready to print. But nothing happens.

I confirmed it is not a hardware problem, as this setup still prints correctly from Windows 2000. 

It's a real bummer not to be able to print.

Any ideas?

Thanks. :)

---

### Post by adonet on 2008-06-01
> **GiveLove said:**
> Hello people,

I've run into a problem since doing a fresh install of Ubuntu 8.04 recently. I cannot print over the network to my HP LaserJet 1100 which is connected to a Zonet ZPS3603 print server. 

This same setup worked just fine on Ubuntu 7.04 & 6.10, and also Fedora versions 5 & 6. 

I created a new printer in System-->Administration-->Printing.
For the connection, I tried both "Appsocket/HP JetDirect", and "LPD/LPR Host or Printer" using the static IP of 192.168.1.100 of the print server. Those did not work. I tried the other driver options besides the recommended one for this printer and those did not work either. 

When sending a "Print Test Page", the job gets sent and the printer light starts blinking, you wait and wait, but nothing happens. When I manually clear the printer buffer, after a few minutes the printer light starts blinking again, like it's getting ready to print. But nothing happens.

I confirmed it is not a hardware problem, as this setup still prints correctly from Windows 2000. 

It's a real bummer not to be able to print.

Any ideas?

Thanks. :)
Its the same problem I'm discussing in thread [http://ubuntuforums.org/showthread.php?t=787166](http://ubuntuforums.org/showthread.php?t=787166)

we concluded that's something in the kernel, allthough we're no experts .

Jeroen

---

### Post by adonet on 2008-06-02
I reported a bug at [https://bugs.launchpad.net/ubuntu/+bug/235197](https://bugs.launchpad.net/ubuntu/+bug/235197)

Please add you issue there

---

### Post by adonet on 2008-06-04
Another kernel update to 2.6.24-18 doesn't solve the problem either.

---

### Post by GiveLove on 2008-06-17
As of 2.6.24-19-generic I am finally able to print!!!!

Hurray!!!!

---

### Post by GiveLove on 2008-06-19
Well an interesting thing happened this morning. I was suddenly not able to print over the network again. I tried a work around posted by pschuel on another thread that made it able for me to print again. 

> I had the same problem as mentioned above - printing to IP printer doesn't work (or is so slow that it takes days to print 1 page) with Hardy and 2.6.24 kernel (-19-rt here). Printing from a Windows XP virtual machine (virtualbox) on the same machine worked. Downgrade to 2.6.22 kernel from Gutsy repos worked also.

After some further research I found that the bug mentioned further up in this thread is a duplicate of bug #213081 and also occurs in other distros (Debian, Gentoo, ...) with the 2.6.24 kernel.

In the bug report of #213081 there is also a workaround mentioned:
with your favourite editor, add a line with

net.ipv4.tcp_frto = 0

to /etc/sysctl.conf (as usual, back it up before changing). Reboot or 'sudo sysctl -p' and probably also 'sudo /etc/init.d/cupsys restart' and enjoy (but ensure there aren't 20 documents in the queue before trying this )...

I tried this workaround and can finally print with the 2.6.24 kernel

Hope this helps
Patrick

I removed this thread as being solved, as I don't really consider a bug work around to be the final answer for this even though it allows me to print.

---

### Post by hangfire on 2008-10-14
I have this problem now, with my two network printers, both Brother Int'l. There is no printer server in the middle. Both are installed as socket devices. I used the exact same setup as 7.10 64-bit, and it worked just as well, at first.

Printing worked 3 weeks ago when I installed 8.0.4.1 64 bit and the printer drivers, and 2 weeks ago. Today (after several updates since last print), the printer will start to warm up, but never print.

I also get the apparmor error message in /var/log/messages.

I have tried the following:

1. sudo aa-complain cupsd   
sudo /etc/init.d/cupsys restart

2. Add username to /etc/groups hplip group

3. add "net.ipv4.tcp_frto = 0" to /etc/sysctl.conf (no quotes)
sudo sysctl -p
sudo /etc/init.d/cupsys restart

I absolutely need to print, and something has me dead in the water.

-HF

PS I can ping both printers, and print to them from a Windows PC.

---

### Post by GiveLove on 2008-10-17
Hello hangfire,

I wish I had a definite answer for you. 

Have you looked on the following thread?
[http://ubuntuforums.org/showthread.php?t=787166]("http://ubuntuforums.org/showthread.php?t=787166")

One other thing to question is whether this is a fresh install of 8.04.1 or an upgrade. Some people have had similar problems for different reasons if they have done an upgrade. 

I'm still able to print from both of my computers using the "net.ipv4.tcp_frto = 0" work around. But I am using 32bit 8.04 Ubuntu.

The recent update to 2.6.24-21-generic kernel did not fix the problem for me without using the work around. 

Have you looked on Launchpad to see if anyone has filled a bug specific to your issue? 

I wish I could be of more help.
Take care. :)

---

### Post by GiveLove on 2008-11-06
This bug appears to now be officially be fixed with Ubuntu 8.10 Intrepid Ibex. I'm assuming it is because it using kernel 2.6.27-7-generic. Anyways, I was able to do a "Test Print" with no problems after setting up the printer for the first time. 

Unfortunately, this fix comes with a host of other bugs. Man, if you thought 8.04 was buggy. Wait till you try 8.10. I don't know what Canonical is thinking. If they are trying to drive off new and long time users alike to other distributions, they sure are doing a good job. This is one of the reasons I jumped ship from Fedora to Ubuntu quite a while ago. I can't believe I'm considering another distribution again. Shame on you Canonical! :mad:

You need to re-think the method that you put out final releases. In my mind, it is far more important that you put out as solid and bug free release as possible rather than hold to a specific release date. At this point, if I stay with Ubuntu, I'll have to wait till the x.xx.1 version comes out before using any future releases. Which reminds me exactly of how Microsoft releases operating systems. Where it is not worth using until service pack 1, due to bugs. 

As it stands, these are the bugs that I have noticed so far in a fresh install of Ubuntu 8.10 32bit:

Weird graphical glitches where the title bar partially disappears in a window.

Network manager refuses to saves the settings for a static IP on wired ethernet. Thus having to re-enter the network settings at every boot.

During the shutdown process the screen goes blank except for a cursor blinking in the top left hand corner and the system freezes. Thus having to either reset or force the computer off with the power button. 

Some bizarre behavior of the page up/down and space bar keys in Firefox where it will jump more than one page. Seems to be random. Sometimes does it more often than others.

Amarok no longer provides gapless playback between songs. Serious bummer! :(

---

### Post by GiveLove on 2008-11-06
> During the shutdown process the screen goes blank except for a cursor blinking in the top left hand corner and the system freezes. Thus having to either reset or force the computer off with the power button. 
This appears to have been fixed with some updates that installed on November 6th 2008.

---

### Post by GiveLove on 2008-11-06
> Amarok no longer provides gapless playback between songs. Serious bummer!
Never mind. I just found out that Rhythmbox Music Player now supports that feature. They call it crossfading, but it is turned off by default. It is in the "Preferences" section in the "Edit" menu. It seems to work quite nicely.

---

### Post by GiveLove on 2008-11-07
> 
Quote:
During the shutdown process the screen goes blank except for a cursor blinking in the top left hand corner and the system freezes. Thus having to either reset or force the computer off with the power button.
This appears to have been fixed with some updates that installed on November 6th 2008. 

I spoke to soon. My computer shutdown correctly once after installing some updates. Then went right back to doing the same thing, Bah! :P

---

### Post by metamute on 2008-12-04
Hi,

I have had a similar problem with 8.04.1

Before we installed 8.04.1 our Ubuntu machines could print to a LRP network print bridge with a Brother HL-5140 printer on the other end.

After installing 8.04.1 printing no longer works.

Our setup is a Brother HL-5140 with a ethernet print bridge, we then use LPR print method.

I have tried selecting the different drivers Ubuntu offers for the Brother HL-5140 but none work.

Our print problems are that half a page will print, the remainder of the page comes out blank.

This then prevents other Windows machines on our network being able to print on the Brother HL-5140, until we power down/up the print driver and clear the Ubuntu machines print queue.

Help appreciated

Simon

---

