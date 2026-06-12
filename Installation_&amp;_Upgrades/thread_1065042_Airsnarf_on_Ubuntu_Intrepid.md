---
title: "Airsnarf on Ubuntu Intrepid?"
date: 2009-02-09
forum: Installation &amp; Upgrades
---

### Post by NCSmokeEater on 2009-02-09
Has anyone gotten Airsnarf to work on Ubuntu at all? Before I even attempt to go through code and try setting everything up, I want to know if it's even possible. The Airsnarf site says the source has been tested and works with Red Hat (and probably requires it). Anyone gotten it to work?

Here's what I got from a dry run (straight compile, then run).

```

# ./airsnarf
Airsnarf - A rogue AP setup utility.
0.2
The Shmoo Group
------------------------------------
Creating dhcpd.conf...Done.
Building the captive portal...cp: target `/var/www/html' is not a directory
chmod: cannot access `/var/www/cgi-bin/*': Not a directory
Done.
Setting the wireless parameters...Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wlan0 ; No such device.
Done.
Setting the ip address and default route...SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
Done.
./airsnarf: line 46: /etc/init.d/dhcpd: No such file or directory
./airsnarf: line 47: /etc/init.d/httpd: No such file or directory
 * Restarting Mail Transport Agent (MTA) sendmail                        [ OK ] 
Setting up firewall to redirect DNS...Done.
Starting local DNS resolver...

Creating TCP socket 0#53 - done.
Creating UDP socket 0#53 - done.
Waiting for connections...

```

Thanks for any help guys. The software seems really interesting and I'd love to learn how to use it, but I don't even know if it'll run on Ubuntu.

---

### Post by binbash on 2009-02-09
I didn't test it with ubuntu BUT for the output you have posted i can say that : 

-You didn't configure it.You can configure by editing airsnarf.cfg
-You don't have apache installed
-You don't have wireless installed or it is not enabled
-You don't have dhcpd installed

---

### Post by NCSmokeEater on 2009-02-09
I'm not sure if Apache is installed. apt-get didn't find anything for me
I'm pretty sure dhcpd isn't in my repos either. I ran apt-get and came up with the same result...

```

# apt-get install apache
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package apache is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package apache has no installation candidate

```

```

# apt-get install dhcpd
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package dhcpd is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package dhcpd has no installation candidate

```

I'm running on internal wireless (Atheros AR242x).

I changed wlan0 to wlan1 and this is now the result.

```

# ./airsnarf
Airsnarf - A rogue AP setup utility.
0.2
The Shmoo Group
------------------------------------
Creating dhcpd.conf...Done.
Building the captive portal...chmod: cannot access `/var/www/cgi-bin/*': Not a directory
Done.
Setting the wireless parameters...Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan1 ; Invalid argument.
Done.
Setting the ip address and default route...Done.
./airsnarf: line 46: /etc/init.d/dhcpd: No such file or directory
./airsnarf: line 47: /etc/init.d/httpd: No such file or directory
 * Restarting Mail Transport Agent (MTA) sendmail

```


Any ideas? I searched and searched but couldn't find a single thread, tut, or anything for Ubuntu and Airsnarf. :confused:

---

### Post by NCSmokeEater on 2009-02-13
..bump...

come on guys... :(

---

### Post by dwavidbwyant on 2009-02-24
sudo apt-get install apache2


apache is a webserver where your victims will be directed when they log in.
I am trying to get it to work too, so I will let you know when and how I got it working

---

### Post by wannadumpwindows on 2009-05-02
I'm also interested . . .

---

