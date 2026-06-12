---
title: "Network server hard drive"
date: 2005-11-26
forum: General Help
---

### Post by Seminoles on 2005-11-26
I have a Sereniti SHS 2000 home server router which has a hard drive it works with windows I'm beta testing it for AOL I have it set up for windows now working fine. I read some where the server runs on Linux inside what I was wonting to do was to be able to mount the hard drive in it while running Ubuntu and also use the printer which is plugged in the usb port on the back of it. Any help would be greatly appreciated since I'm a newbie to Ubuntu or Linux,

Thanks,
Robert  :confused:

---

### Post by amohanty on 2005-11-27
Can you ssh or (tux-forbid) telnet into the machine?

AM

---

### Post by Seminoles on 2005-11-27
[QUOTE=amohanty]Can you ssh or (tux-forbid) telnet into the machine?

AM[/QUOTE]

No I haven't tried them I'm very new at this this is the first time I have heard of them I havent even done any telnet in windows. I'll try to do some reading on them. Thanks :)

---

### Post by amohanty on 2005-11-27
OK let me see if I understand your situation:

1. you have a router/server with an HDD.
2. you can connect and use it under windows (do you have access to a web based adminstrative interface?)
3. you would like to be able to use the HDD in the router/server

Now if you access it via  web based admin interface (ie to manage it you goto: [http://192.168.0.1/](http://192.168.0.1/) or something like that, just hit a non existant page like so in your browser:

[http://192.168.0.1/lkjasdflkjasdf](http://192.168.0.1/lkjasdflkjasdf)

To see what it can return try hitting this link:
[http://www.apache.org/kljasdkjflasdf](http://www.apache.org/kljasdkjflasdf)

That should tell you what server its running on and what OS it has (at least at the basic level)

Then to find out what ports on the box are open you can use nmap

sudo apt-get install nmap
sudo nmap -sS -p 1-65535 -vv 192.168.0.1

IMPORTANT: please keep in mind that I am using 192.168.0.1 as an example ip, replace it with the ip of the router/server.

To find out what hosts are there on your network do:
arp -v

If nmap returns something like this:

root@kandinsky:/home/aseem# nmap -vv -sS -p1-65535 192.168.0.1

Starting nmap 3.81 ( [http://www.insecure.org/nmap/](http://www.insecure.org/nmap/) ) at 2005-11-27 19:59 PST
Initiating SYN Stealth Scan against 192.168.0.1 [65535 ports] at 19:59
Discovered open port 22/tcp on 192.168.0.1
Discovered open port 23/tcp on 192.168.0.1
Discovered open port 80/tcp on 192.168.0.1
The SYN Stealth Scan took 41.99s to scan 65535 total ports.
Host 192.168.0.1 appears to be up ... good.
Interesting ports on 192.168.0.1:
(The 65532 ports scanned but not shown below are in state: closed)
PORT     STATE    SERVICE
80/tcp   open     http
23/tcp   open     telnet
22/tcp   open     ssh
MAC Address: 00:00:00:00:00:00

Nmap finished: 1 IP address (1 host up) scanned in 42.687 seconds
               Raw packets sent: 65681 (2.63MB) | Rcvd: 65534 (3.01MB)


That means you have a web server, telnet server and ssh server available. You can then try to ssh into the box using the admin username and password. 

Also try and locate the documentation for it and see if it has any details.

HTH
AM

---

### Post by Seminoles on 2005-11-29
When I try to log in it says need command center.exe click here to download it is windows supported only according to Sereniti little documents on it tried the links with my ip address comes up with file not found or 404 file not found. installed nmap and ran it coming up with the following.

robert@mainframe:~$ sudo nmap -sS -p 1-65535 -vv 192.168.50.1

Starting nmap 3.81 ( [http://www.insecure.org/nmap/](http://www.insecure.org/nmap/) ) at 2005-11-29 08:00 EST
Initiating SYN Stealth Scan against sereniti (192.168.50.1) [65535 ports] at 08:00
Discovered open port 53/tcp on 192.168.50.1
Discovered open port 80/tcp on 192.168.50.1
Discovered open port 22/tcp on 192.168.50.1
Discovered open port 30006/tcp on 192.168.50.1
Discovered open port 1113/tcp on 192.168.50.1
Discovered open port 40006/tcp on 192.168.50.1
Discovered open port 5431/tcp on 192.168.50.1
Discovered open port 81/tcp on 192.168.50.1
Discovered open port 139/tcp on 192.168.50.1
Discovered open port 9000/tcp on 192.168.50.1
Discovered open port 7777/tcp on 192.168.50.1
Discovered open port 3200/tcp on 192.168.50.1
Discovered open port 445/tcp on 192.168.50.1
The SYN Stealth Scan took 23.13s to scan 65535 total ports.
Host sereniti (192.168.50.1) appears to be up ... good.
Interesting ports on sereniti (192.168.50.1):
(The 65521 ports scanned but not shown below are in state: closed)
PORT      STATE    SERVICE
22/tcp    open     ssh
23/tcp    filtered telnet
53/tcp    open     domain
80/tcp    open     http
81/tcp    open     hosts2-ns
139/tcp   open     netbios-ssn
445/tcp   open     microsoft-ds
1113/tcp  open     unknown
3200/tcp  open     unknown
5431/tcp  open     unknown
7777/tcp  open     unknown
9000/tcp  open     unknown
30006/tcp open     unknown
40006/tcp open     unknown
MAC Address: 00:03:2F:30:D1:94 (Global Sun Technology)

Nmap finished: 1 IP address (1 host up) scanned in 23.799 seconds
               Raw packets sent: 66371 (2.65MB) | Rcvd: 65536 (3.01MB)


[QUOTE=amohanty]OK let me see if I understand your situation:

1. you have a router/server with an HDD.
2. you can connect and use it under windows (do you have access to a web based adminstrative interface?)
3. you would like to be able to use the HDD in the router/server

Now if you access it via  web based admin interface (ie to manage it you goto: [http://192.168.0.1/](http://192.168.0.1/) or something like that, just hit a non existant page like so in your browser:

[http://192.168.0.1/lkjasdflkjasdf](http://192.168.0.1/lkjasdflkjasdf)

To see what it can return try hitting this link:
[http://www.apache.org/kljasdkjflasdf](http://www.apache.org/kljasdkjflasdf)

That should tell you what server its running on and what OS it has (at least at the basic level)

Then to find out what ports on the box are open you can use nmap

sudo apt-get install nmap
sudo nmap -sS -p 1-65535 -vv 192.168.0.1

IMPORTANT: please keep in mind that I am using 192.168.0.1 as an example ip, replace it with the ip of the router/server.

To find out what hosts are there on your network do:
arp -v

If nmap returns something like this:

root@kandinsky:/home/aseem# nmap -vv -sS -p1-65535 192.168.0.1

Starting nmap 3.81 ( [http://www.insecure.org/nmap/](http://www.insecure.org/nmap/) ) at 2005-11-27 19:59 PST
Initiating SYN Stealth Scan against 192.168.0.1 [65535 ports] at 19:59
Discovered open port 22/tcp on 192.168.0.1
Discovered open port 23/tcp on 192.168.0.1
Discovered open port 80/tcp on 192.168.0.1
The SYN Stealth Scan took 41.99s to scan 65535 total ports.
Host 192.168.0.1 appears to be up ... good.
Interesting ports on 192.168.0.1:
(The 65532 ports scanned but not shown below are in state: closed)
PORT     STATE    SERVICE
80/tcp   open     http
23/tcp   open     telnet
22/tcp   open     ssh
MAC Address: 00:00:00:00:00:00

Nmap finished: 1 IP address (1 host up) scanned in 42.687 seconds
               Raw packets sent: 65681 (2.63MB) | Rcvd: 65534 (3.01MB)


That means you have a web server, telnet server and ssh server available. You can then try to ssh into the box using the admin username and password. 

Also try and locate the documentation for it and see if it has any details.

HTH
AM[/QUOTE]

---

### Post by Seminoles on 2005-11-29
Follow up:

I tried ssh first time it came up not recognizing license do you still wont to connect so I answered yes when I type ssh 192.168.50.1 it ask for a password I used all of the one I know none will work sent an email to Sereniti to see if the have a different one and if it was ok to use it will see what they say I'm at a stand still know.

---

### Post by Seminoles on 2005-12-01
This is the responce I got from Serenitit.

BTW, there is no user functionality provided by the ssh interface to the SHS.



Nut, you can still mount the shared drives on your linux box.  To do this become root and run the following commands (note: only the lines preceded with "#" are commands,the rest is output from the commands, or comments).



-- this will show what shares are available.

# smbclient -L 192.168.50.1

(hit <enter> with no password)





Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.0.11]



        Sharename       Type      Comment

        ---------       ----      -------

        backup          Disk      Backup Files

        public          Disk      Public Share

        installer       Disk      Installer Software

        media           Disk      Media Cache

        IPC$            IPC       IPC Service (Sereniti Smart Home Server)

        ADMIN$          IPC       IPC Service (Sereniti Smart Home Server)



-- create a mount point for the public share

# mkdir /mnt/sereniti/



-- mount the disk

# smbmount //192.168.50.1/public /mnt/sereniti/



-- check that it's mounted

# mount

//192.168.50.1/public on /mnt/sereniti type smbfs (0)



-- see what's in the share.  At this point you can use /mnt/sereniti as a normal file system



# ls -al /mnt/sereniti/

total 2368

drwxr-xr-x  1 root root    4096 Nov 30 13:00 .

drwxr-xr-x  7 root root     192 Nov 30 12:48 ..

-rwxr-xr-x  1 root root    3101 Nov 30 12:47 sushil-laptop.tar.gz

-rwxr-xr-x  1 root root 2409713 Nov 30 12:47 tests.zip



You can add the following line to your /etc/fstab so that you can just type "mount /mnt/sereniti" to have access to your share:



//192.168.50.1/public   /mnt/sereniti   smbfs   password="",rw  0 0



   



Tom Scanlan

Sereniti, Inc.

---

