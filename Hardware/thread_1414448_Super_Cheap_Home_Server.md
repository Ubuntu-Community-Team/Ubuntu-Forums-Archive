---
title: "Super Cheap Home Server"
date: 2010-02-23
forum: Hardware
---

### Post by Red Penguin on 2010-02-23
Hey, I want to put together a cheap little headless media server for my house, as much for the experience of setting it up as anything else.

I found a nice tutorial [here]("http://ubuntuforums.org/showthread.php?t=775906") which seems to cover what I want, so it'll be running 8.04 server. Since the hardware requirements don't look to be too fierce, I thought about the following. I'd be grateful if anyone experienced in such things could throw in their opinions, point out newbie errors etc.

[Barebones system]("http://www.microdirect.co.uk/Home/Product/41536/Foxconn-barebone-PC-system-R10-S1-with-integrated"): with PSU, Mobo, builtin atom processor, integrated graphics: £68

[512Mb Generic RAM]("http://www.microdirect.co.uk/Home/Product/3150/PC-memory-512MB-PC133-RAM--major-brand-"): £10 (The Mobo BUS clock rate is the *maximum *I can have  right?)

[Generic Disk drive]("http://www.microdirect.co.uk/Home/Product/44202/SONY-DVD-ROM-DDU1681S-0B-18x-Black-OEM"): £12
[URL="http://www.microdirect.co.uk/Home/Product/41497/Samsung-1-5TB--1500GB-EcoGreen-F2--SATA-II-300"]
2x 1.5 TB SATA Hard drives[/URL]: £130
(Supplemented by 2x 500GB external HDD's though 3Tb is probably enough TBH)

OS: Ubuntu 8.04 Server Edition: £Free (<3) 

Total cost around £250 including delivery etc.

Only thing I'm not sure about is ventilation, but I'll check that with the supplier if I end up ordering

Thanks

RP

---

### Post by linnyjack on 2010-02-23
it really depends on what you want to do with it, but imo an intel atom chip isnt ideal, you find those chips in netbooks and tablet pcs not servers.
 if i was you and i just wanted a box to learn with and maybe run an ftp server on i would go for a p4 chip nice and cheap (3.4ht 20 pounds ish 2nd hand) and work well i notice you linked micro direct so i presume you are in the uk for that 79 pounds for that atom box you could pick somthing up 2nd hand from cex.co.uk that i think would suit your needs better, you can also pick up cheap hdds from there imo you would be better of buying smaller cheaper disks and getting better hardware.

---

### Post by tgalati4 on 2010-02-23
Used P4's are good, but they are power hungry.  90 watts vs 12 watts.  If the system is running 24/7 then the atom will pay for itself in a year.

Other than suspend/sleep, there is no throttling on the P4 so it runs at full speed all the time.

So the P4 is a good solution if you want to have it off or on-demand, wake-on-lan use.  Atom is a good solution if you need 24/7.

Another option is the plug computer:

[http://plugcomputer.org/](http://plugcomputer.org/)

It's 2-5 watts.

---

### Post by snowpine on 2010-02-23
Hi there, I have the Foxconn R10-S4, which is the dual-core (Atom 330) of the barebones you're looking at. I installed 2gb ram and a 500gb "green caviar" hard drive. I actually use it daily as my living room web-surfing computer. I think it would be ideal for your server project, with less heat, noise, and power consumption than a Pentium 4 (in fact I bought it specifically to replace my big, noisy P4). I have not tried Ubuntu 8.04 on it, but 9.04 and 9.10 work fine in my experience. If you have ever used a netbook like the Asus eee or Dell Mini, you'll know what to expect in the way of performance. Good luck!

ps If the one you're looking at is similar to mine, ventilation/overheating will not be a problem. There are two fans pre-installed that are always on but not obnoxiously loud.

pps Double check but I don't think you can fit 2 hard drives.

---

### Post by linnyjack on 2010-02-23
fair points, personally ive never considered power usage :S i just pay the bill when it comes as for noise i didnt really consider that either as its a server i assumed it would be tucked away in a back room somewhere i only worry about noise if i can hear it, ive never used one of these low power chips isnt he going to run into problems with performance if he trying to torrent, unrar stuff and stream stuff all at once?

---

### Post by Red Penguin on 2010-02-23
Thanks for the replies, very useful feedback. I am indeed in the UK, and have no objection to going 2nd hand, so I'll have a browse through cex.co.uk. I don't mind pushing up the price if it gives results either.

Since it seems like a lot depends on how I'll be using it; I'm intending on running it 24/7, torrenting (with rtorrent auto-throttling) from around 2am-2pm and streaming TV, movies and music during the day. 

Hopefully this brings the Atom back into play since the PC won't be multitasking too much. Might as well save a few penguins and polarbears. Noise isn't an issue though, since it'll be tucked away. 

Does streaming tax the host PC or the user more? I might be streaming to 2 or 3 devices at once, and I might go for something beefier if that'll cause problems, maybe a newish but lowend intel dualcore. Will the RAM also effect this?

With regards to the 2 harddrives: I'll check with the chaps there and if I can only have one I'll upgrade to a single 2Tb HD, which is likely more thank I'll ever need anyway!

Thanks

RP

---

### Post by tgalati4 on 2010-02-23
Standard Definition streaming is not a problem.  High Def streaming presents a few problems.  For wireless, you need to make sure you have a strong signal and low interference (neighbors).  For wired performance, your drives and PC bus need to be speedy.

High Def tax both the server and the viewing box. 350 MB files for SD, few GB files for HD depending on resolution.  Dumping that much data on your network will cause some slowdowns.  You need to pay attention to RAM and cache settings.  Dual core processors are recommended for the viewing box to reduce interrupts.  

I don't have any atom devices at home to test, but High Def taxes a 2.13 GHz centrino (single core) processor on my ibm T43p thinkpad.

I also have a Pentium D (dual core) 3 GHz and it's OK for HD.  

Just adding to your confusion.

---

### Post by bpalone on 2010-02-23
I have a single core Atom running as my file and web server at home.  I once in a while will stream a AVI movie  from it over my wireless side without any hiccups.  Keep in mind though that my websites see very little traffic.

If it is any help, my prior server was an old AMD K6 333 and it handled AVI movies also.   If you stream the real deal movie, it may be another thing all together.  I haven't ever tried it, so I'm not much help there, not that I am anyway.

---

### Post by Red Penguin on 2010-02-24
Au contraire bpalone, a most helpful post, and one that gives me the confidence to go ahead with the spec in the OP.

Thanks for the advice, and I will likely be re-appearing when I mess something up on the server :D

Thanks

RP

---

### Post by Red Penguin on 2010-03-04
Well, I said I'd be back, and here I am.

I've got my server running from [here]("http://ubuntuforums.org/showthread.php?t=775906") and am operating it remotely with ssh. 

I can't get an 'outside' connection though, for example I can't ping [www.google.com](www.google.com) (although I can from other PC's connecting to the router).

Reading about it looks like something to do with my DNS not being configured. I can offer the following outputs:

```

sysadmin@media-server:~$ cat /etc/network/interfaces 
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.1.2
gateway 192.168.1.2
netmask 255.255.255.0
sysadmin@media-server:~$ 

```

```
sysadmin@media-server:~$ cat /etc/resolv.conf 
nameserver 192.168.1.1
```

```
sysadmin@media-server:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:22:68:5c:9b:85  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::222:68ff:fe5c:9b85/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:421 errors:0 dropped:0 overruns:0 frame:0
          TX packets:249 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:36417 (35.5 KB)  TX bytes:30205 (29.4 KB)
          Interrupt:17 Base address:0xc800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:28 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2960 (2.8 KB)  TX bytes:2960 (2.8 KB)

```

Thanks

RP

---

### Post by bpalone on 2010-03-05
From your post:

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.1.2
gateway 192.168.1.2
netmask 255.255.255.0
sysadmin@media-server:~$


I think you need to check your gateway address.  I'm guessing that it is 192.168.1.1 or 192.168.1.0.  See what it is on your other machines and change it to match.  I think that will get it talking to the outside world.

---

### Post by Red Penguin on 2010-03-05
Wonderful, that did the trick!

Thanks

RP

---

### Post by Red Penguin on 2010-05-15
So I've had this up and running for a while now, and through heavy ripping of my DVD collection have clocked up about 750Gb of stuff.

Right now I'm starting to get a bit paranoid about hard-drive failure. What are my options regarding backup?

I've thought about RAID 1 with the second (empty) 1.5Tb Disk, or simply tarring my media folder and storing that on the second disk.

---

### Post by tgalati4 on 2010-05-15
If you have the DVD's why would you need to make a backup?

If they are DVD's that you've borrowed, then you might only need to make a backup of those onto a second drive.

Consumer-grade drives do wear out with extensive write sessions.  The little heads get hot and can delaminate.  For reading, consumer drives can last a long time.  Spread out your write sessions to allow your drives to cool.

---

### Post by Red Penguin on 2010-05-16
Mostly because I've spent literally months ripping the things, and don't intend to do the whole collection again if one of the drives fails, particularly if I can just restore it with a few commands from a hard disk that will otherwise be unused.

Thanks for the tip about writing though.

---

### Post by Red Penguin on 2010-06-01
I found 'rsync' to be a decent choice for backing up my system.

I just mounted the second hard drive and backed up using
> sudo rsync -azvv /home/sysadmin/mediaserver/ /media/harddisk2/mediabackup/ 
Which checks which files in ~/mediaserver already exist in mediabackup and if a file doesn't, copies it into mediabackup

When everything is finished (which will take a while given tgalati4's point about disk writing) I'll set up a cron job to sync it every night or week.

The only problem is that it doesn't currently mirror ~/mediaserver, just copies stuff between the folders. So if I renamed film.avi to film1.avi 1 would end up with both files in /mediabackup/, but a small quibble

---

