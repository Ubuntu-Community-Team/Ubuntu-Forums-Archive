---
title: "Hardy Couldn't visit windows network with smbclient"
date: 2008-09-03
forum: General Help
---

### Post by Kelen.Chang on 2008-09-03
sometime i couldn't visit window network with smbclient while using Netbios Name, but IP is okay. 
is there any wrong with hardy or smbd (nmbd) service?

```
firefox@ubuntu:~/work$ smbclient -L . -N
Anonymous login successful
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.0.28a]

        Sharename       Type      Comment
        ---------       ----      -------
        print$          Disk      Printer Drivers
        IPC$            IPC       IPC Service (ubuntu server (Samba, Ubuntu))
Anonymous login successful
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.0.28a]

        Server               Comment
        ---------            -------
        SONY                 windows
        UBUNTU               ubuntu server (Samba, Ubuntu)

        Workgroup            Master
        ---------            -------
        WORKGROUP            UBUNTU
&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;
firefox@ubuntu:~/work$ smbclient -L sony
timeout connecting to 61.140.3.66:445
timeout connecting to 61.140.3.66:139
Error connecting to 61.140.3.66 (Operation already in progress)
Connection to sony failed (Error NT_STATUS_ACCESS_DENIED)
&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;
firefox@ubuntu:~/work$ nmblookup sony
querying sony on 192.168.1.255 
192.168.1.4 sony<00>
&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;
firefox@ubuntu:~/work$ smbclient -L 192.168.1.4
Password:
Domain=[SONY] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]

        Sharename       Type      Comment
        ---------       ----      -------
        E$              Disk      default shares
        IPC$            IPC        IPC
        D$              Disk      default shares
        tools           Disk
        softwares       Disk
        ADMIN$          Disk      default shares
        C$              Disk      default shares
session request to 192.168.1.4 failed (Called name not present)
session request to 192 failed (Called name not present)
Domain=[SONY] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]

        Server               Comment
        ---------            -------

        Workgroup            Master
        ---------            -------
&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;
firefox@ubuntu:~/work$ smbclient //sony/tools
timeout connecting to 61.140.3.66:445
timeout connecting to 61.140.3.66:139
Error connecting to 61.140.3.66 (Operation already in progress)
Connection to sony failed (Error NT_STATUS_ACCESS_DENIED)
&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;&#65309;
firefox@ubuntu:~/work$ smbclient //192.168.1.4/tools
Password:
Domain=[SONY] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]
smb: \>
```

---

### Post by Peter09 on 2008-09-03
You need to install winbind

```
sudo apt-get install winbind
```

then edit 

/etc/nsswitch.conf and add 'wins' so that the hosts line looks something like this (order matters)

> hosts:          files mdns4_minimal [NOTFOUND=return] dns wins mdns4

then restart winbind with

```
sudo /etc/init.d/winbind restart
```

that should do it.

PC

---

### Post by Kelen.Chang on 2008-09-03
first, thank for your advice on this point. but i was follow your steps, but there is nothing changed at this problem. any idea else?

---

### Post by Peter09 on 2008-09-03
Only other thing I can suggest is to restart samba.

```
sudo /etc/init.d/samba restart
```

PC

---

### Post by Kelen.Chang on 2008-09-03
sorry, there is nothing changed anyway.

---

### Post by Peter09 on 2008-09-03
Are you using a DNS server?

PC

---

### Post by Kelen.Chang on 2008-09-03
it is automatically gained IP by DHCP, so i thought DNS is no problem in that case. 
besides, How did i know DNS server is going to worked?

---

### Post by Peter09 on 2008-09-03
Sorry, I meant to ask if you used dhcp, DNS is immaterial. You need to check that your DHCP server has identified the names of the attached machines and also that you have correctly specified the DHCP server on your Linux machine.

I had the same problem as you and what I have told you fixed it for me. The only other thing may be your samba configuration file.

PC

---

### Post by Peter09 on 2008-09-03
Just remebered in your /etc/samba/smb.conf file you need the line

```
    name resolve order = lmhosts wins bcast host
```

you may already have some of that line but you will need the wins bit as well.

---

### Post by Kelen.Chang on 2008-09-03
okay, i checked it again, DNS worked fine. 
```
firefox@ubuntu:~/work$ ping sony
PING china (59.37.71.85) 56(84) bytes of data.
64 bytes from china (59.37.71.85): icmp_seq=1 ttl=58 time=13.0 ms
64 bytes from china (59.37.71.85): icmp_seq=2 ttl=58 time=14.0 ms
64 bytes from china (59.37.71.85): icmp_seq=3 ttl=58 time=15.4 ms
64 bytes from china (59.37.71.85): icmp_seq=4 ttl=58 time=28.8 ms

--- sony ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 2998ms
rtt min/avg/max/mdev = 13.014/17.845/28.838/6.404 ms
```

---

### Post by Kelen.Chang on 2008-09-03
> **Peter09 said:**
> Just remebered in your /etc/samba/smb.conf file you need the line

```
    name resolve order = lmhosts wins bcast host
```

you may already have some of that line but you will need the wins bit as well.

yeah, i got this line and same as you, 

```
firefox@ubuntu:~/work$ cat /etc/samba/smb.conf |grep 'name resolve'
;   name resolve order = lmhosts host wins bcast
```

---

### Post by Peter09 on 2008-09-03
Not sure what you are telling me. Ping is able to resolve a local machine name, or is that a remote machine.


PC

---

### Post by Peter09 on 2008-09-03
You need to change the order in the smb.conf file, wins must be before hosts.

PC

---

### Post by Kelen.Chang on 2008-09-03
Oh, "sony" it is a local machine name.

---

### Post by Kelen.Chang on 2008-09-03
> **Peter09 said:**
> You need to change the order in the smb.conf file, wins must be before hosts.

PC
okay, try this way immediately.

---

### Post by Peter09 on 2008-09-03
That means that we have now got name resolution working ok. If you still have the problem its around you samba configuration.

PC

---

### Post by Kelen.Chang on 2008-09-03
> **Peter09 said:**
> That means that we have now got name resolution working ok. If you still have the problem its around you samba configuration.

PC
Oh, it's worked after i fixed that line and restart /etc/init.d/samba
```
firefox@ubuntu:~/work$ cat /etc/samba/smb.conf |grep 'name resolve'
   name resolve order = lmhosts wins bcast host
firefox@ubuntu:~/work$ smbclient //sony/tools
Password: 
Domain=[SONY] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]
smb: \> 
```

thanks advance :lolflag:

---

