---
title: "iptables stop?"
date: 2008-08-06
forum: General Help
---

### Post by shamusl on 2008-08-06
> Righto, it works

Based on the premise of "it worked for me and heres what I think I did to make it work" is a minimal guide to accessing whats on a PC from your PS3

PC: Generic Athlon64 3200 with 1Gb ram running FedoraCore 6
PS3: wireless attached

On the PC
yum install ushare (it also fetched dependancies for uPNP libraries)
mkdir /ushare
Drag and drop some content into /ushare

iptables stop
ushare -d -c /ushare

I also enabled uPNP on my router as the PS3 was saying no uPNP was available.
Now I can watch a grainy video clip of DuranDuran Girls On Film.MPG on a really big screen.
Yay, I think.

The next step is to modify the firewall config to allow uPNP to work rather than just turning everything off.

I copied that from: [http://forums.teamphoenixrising.net/showthread.php?t=46827](http://forums.teamphoenixrising.net/showthread.php?t=46827)

The discussion is dead, and the command doesn't work in ubuntu. I'm have difficulty with iptables stop in particular.

Can someone explain what this does? And why this would require it? Does anyone know of a simpler way of getting this to work? Or does anyone know of a command with this equivalence (iptables stop)?

---

### Post by jerome1232 on 2008-08-06
I usually use UFW for my firewall needs, but I think he's just turning iptables off (I'll look more into that and post back) edit: confirmed he was just turning off iptables, which wouldn't be needed in Ubuntu because iptables is configured to accept all connections by default.

to see how iptables is setup type:
```
sudo iptables -L
```

should come up with something like this:
```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
```

edit: Yup that's what he was doing, just turning off iptables

---

### Post by jerome1232 on 2008-08-06
Btw, he was writing this for a redhat based system which uses yum to install programs, debian/ubuntu uses apt, I checked if ushare was in the repos using
```
apt-cache show ushare
```
and it is, you can install it with
```
sudo apt-get install ushare
```

hope that helps

---

### Post by shamusl on 2008-08-06
Thanks so much everybody, but I'm having another problem with something. I created the directory with  sudo mkdir /home/shamus/ushare, but I can't access it. Whenever I go to put files in it, it just says permission denied. When I go to the permissions it says I'm not root. How do I enter the file browser while root?

---

### Post by mcduck on 2008-08-06
You shouldn't have used "sudo", since you already have write access to your own home. Using sudo caused that command to be run as root, and therefore the directory is owned by root.

Anyway, "sudo chown shamus:shamus /home/shamus/ushare" will make you the owner of that directory.

---

### Post by jerome1232 on 2008-08-06
Well you shouldn't have made the directory as root (using sudo)
That makes the folder owned as root. now I am writing this assuming you are user shamus.

To fix the permission you want to make yourself owner.
```
sudo chmod shamus:shamus ~/ushare
```

typing ~/ is the same as /home/shamus and a lot more convenient

edit: srry about the double post

---

### Post by shamusl on 2008-08-06
> **jerome1232 said:**
> Well you shouldn't have made the directory as root (using sudo)
That makes the folder owned as root. now I am writing this assuming you are user shamus.

To fix the permission you want to make yourself owner.
```
sudo chmod shamus:shamus ~/ushare
```

typing ~/ is the same as /home/shamus and a lot more convenient

Wow, you guys are incredibly nice. After changing permissions and creating subdirectories "Music" "Movies" ...etc, none of the files will appear on my ps3, am I doing something wrong?

Here's what the command line spits out when I enter the command to start sharing /home/shamus/ushare

```
shamus@shamus-desktop:~$ ushare -d -c /home/shamus/ushare
Interface eth0 is down.
Recheck uShare's configuration and try again !
uShare (version 1.1a), a lightweight UPnP A/V and DLNA Media Server.
Benjamin Zores (C) 2005-2007, for GeeXboX Team.
See http://ushare.geexbox.org/ for updates.
Listening on telnet port 1337
Initializing UPnP subsystem ...
Starting in DLNA compliant profile ...
UPnP MediaServer listening on 192.168.1.2:49152
Sending UPnP advertisement for device ...
Listening for control point connections ...
Building Metadata List ...
Looking for files in content directory : /home/shamus/ushare
Found 2 files and subdirectories.

```

And it never brings me back to the command line. Did I do something wrong?

---

### Post by jerome1232 on 2008-08-06
could you post the output of
```
ifconfig
```

either your connection is down or you need to configure ushare to listen on a different interface

---

### Post by shamusl on 2008-08-06
> **jerome1232 said:**
> could you post the output of
```
ifconfig
```

either your connection is down or you need to configure ushare to listen on a different interface


No problem.

```

eth0      Link encap:Ethernet  HWaddr 00:18:f3:18:17:c7  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::218:f3ff:fe18:17c7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:73966579 errors:0 dropped:0 overruns:0 frame:0
          TX packets:106783097 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:2077587543 (1.9 GB)  TX bytes:2143724816 (1.9 GB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:24430 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24430 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1235971 (1.1 MB)  TX bytes:1235971 (1.1 MB)

```

---

### Post by mcduck on 2008-08-06
> **shamusl said:**
> Wow, you guys are incredibly nice. After changing permissions and creating subdirectories "Music" "Movies" ...etc, none of the files will appear on my ps3, am I doing something wrong?

Here's what the command line spits out when I enter the command to start sharing /home/shamus/ushare

```
shamus@shamus-desktop:~$ ushare -d -c /home/shamus/ushare
Interface eth0 is down.
Recheck uShare's configuration and try again !
uShare (version 1.1a), a lightweight UPnP A/V and DLNA Media Server.
Benjamin Zores (C) 2005-2007, for GeeXboX Team.
See http://ushare.geexbox.org/ for updates.
Listening on telnet port 1337
Initializing UPnP subsystem ...
Starting in DLNA compliant profile ...
UPnP MediaServer listening on 192.168.1.2:49152
Sending UPnP advertisement for device ...
Listening for control point connections ...
Building Metadata List ...
Looking for files in content directory : /home/shamus/ushare
Found 2 files and subdirectories.

```

And it never brings me back to the command line. Did I do something wrong?

Apart from the network interface problem that sounds like it's working as it should. Ushare is running in the terminal, using the terminal for it's output.

If you want to run it in background (leaving the terminal usable for other tasks) add an "&" to the end of the command:
"ushare -d -c /home/shamus/ushare &"

..or if you want to leave it running even if you close the terminal, use nohup:
"nohup ushare -d -c /home/shamus/ushare &"

---

### Post by shamusl on 2008-08-06
> **mcduck said:**
> Apart from the network interface problem that sounds like it's working as it should. Ushare is running in the terminal, using the terminal for it's output.

If you want to run it in background (leaving the terminal usable for other tasks) add an "&" to the end of the command:
"ushare -d -c /home/shamus/ushare &"

..or if you want to leave it running even if you close the terminal, use nohup:
"nohup ushare -d -c /home/shamus/ushare &"

shamus@shamus-desktop:~$ nohup ushare -d -c /home/shamus/ushare &
nohup: ignoring input and appending output to `nohup.out'
[2] 25113
[2]+  Exit 1                  nohup ushare -d -c /home/shamus/ushare

I don't know weather that means it's working or not.

---

### Post by jerome1232 on 2008-08-06
> **shamusl said:**
> No problem.

```

eth0      Link encap:Ethernet  HWaddr 00:18:f3:18:17:c7  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::218:f3ff:fe18:17c7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:73966579 errors:0 dropped:0 overruns:0 frame:0
          TX packets:106783097 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:2077587543 (1.9 GB)  TX bytes:2143724816 (1.9 GB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:24430 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24430 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1235971 (1.1 MB)  TX bytes:1235971 (1.1 MB)

```

according to that your interfaces are configured correctly
ushare is configured to listen on eth0, which is the one that's connected

I just downloaded ushare to test it and it's working fine for me, the only thing I can add past this is the config file for ushare is /etc/ushare.conf but it's listening on the right interface for you so I wouldn't mess with that config file. Maybe mcduck has more insight to this.

---

### Post by shamusl on 2008-08-06
> **jerome1232 said:**
> according to that your interfaces are configured correctly
ushare is configured to listen on eth0, which is the one that's connected

I just downloaded ushare to test it and it's working fine for me, the only thing I can add past this is the config file for ushare is /etc/ushare.conf but it's listening on the right interface for you so I wouldn't mess with that config file. Maybe mcduck has more insight to this.

Well the PS3 uses DLNA, and maybe ushare requires some extra dependencies to add support for it?

EDIT: never mind, I added the support but it's still not showing files. Any Ideas?

---

### Post by jerome1232 on 2008-08-06
Okay I looked a little more at this and actually i'm getting the error about the interface down, but ushare seems to be listening.

I noticed ushare is listening on port 1337 so I wanted to see if it was listening:
```
telnet localhost 1337  # this is the command the rest is what it outputs on success
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
uShare (1.1a) (Built Feb 15 2008)
For a list of registered commands type "help"

```
so it's listening, I ran and tried it on another machine
```
telnet 192.168.1.4 1337  # replace that ip with your own (the one under ifconfig 192.168.1.2 if memory serves)
Trying 192.168.1.4...
Connected to 192.168.1.4.
Escape character is '^]'.
uShare (1.1a) (Built Feb 15 2008)
For a list of registered commands type "help"

```

So it's listening despite the error it seems. According to ushares man page (type man ushare to view it)
the following filetypes are supported so make sure the files you are shareing are of these types.
> FILE TYPES
       The following file formats (extensions) are supported :

       Video  asf, avi, dv, divx, wmv, mjpg, mjpeg, mpeg, mpg, mpe, mp2p, vob,
              mp2t, m1v, m2v, m4v, m4p, mp4ps, ts, ogm, mkv, rmvb, mov, qt

       Audio  aac, ac3, aif, aiff, at3p, au, snd, dts,  rmi,  mp1,  mp2,  mp3,
              mp4, mpa, ogg, wav, pcm, lpcm, l16, wma, mka, ra, rm, ram

       Images bmp,  ico,  gif,  jpeg,  jpg, jpe, pcd, png, pnm, ppm, qti, qtf,
              qtif, tif, tiff

       Playlist
              pls, m3u, asx

       Subtitles
              dks, idx, mpl, pjs, psb, scr, srt, ssa, stl, sub, tts, vsf, zeg

       Miscellaneous files
              bup, ifo

when you say you added support for dlna how did you do it? It looks to me you just need to edit the /etc/ushare.conf file to do so (sudo nano /etc/ushare.conf) and find enable_dlna and set it to yes

---

### Post by shamusl on 2008-08-06
> **jerome1232 said:**
> Okay I looked a little more at this and actually i'm getting the error about the interface down, but ushare seems to be listening.

I noticed ushare is listening on port 1337 so I wanted to see if it was listening:
```
telnet localhost 1337  # this is the command the rest is what it outputs on success
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
uShare (1.1a) (Built Feb 15 2008)
For a list of registered commands type "help"

```
so it's listening, I ran and tried it on another machine
```
telnet 192.168.1.4 1337  # replace that ip with your own (the one under ifconfig 192.168.1.2 if memory serves)
Trying 192.168.1.4...
Connected to 192.168.1.4.
Escape character is '^]'.
uShare (1.1a) (Built Feb 15 2008)
For a list of registered commands type "help"

```

So it's listening despite the error it seems. According to ushares man page (type man ushare to view it)
the following filetypes are supported so make sure the files you are shareing are of these types.


when you say you added support for dlna how did you do it? It looks to me you just need to edit the /etc/ushare.conf file to do so (sudo nano /etc/ushare.conf) and find enable_dlna and set it to yes

I added the package from here: [http://libdlna.geexbox.org/](http://libdlna.geexbox.org/)
The PS3 recognizes my PC now, but it won't show any files I put into the ushare folder. I've tried reloading it, and it just doesn't work.

---

