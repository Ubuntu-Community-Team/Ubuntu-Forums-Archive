---
title: "MySQL wont start at boot."
date: 2008-08-05
forum: General Help
---

### Post by matmcnic on 2008-08-05
MySQL fails to start at boot up [[COLOR="Red"]fail[/COLOR]] 

But then I can manually start it by: *sudo /etc/init.d/mysql start*

Before manually starting it I check and there is nothing listening on 3306.

-----
I look in syslog and I see:

mysqld_safe[4766]: started

mysqld[4770]: 080805 17:14:38  InnoDB: Started; log sequence number 0 43685

mysqld[4770]: 080805 17:14:38 [ERROR] Can't start server: Bind on TCP/IP port: Cannot assign requested address

mysqld[4770]: 080805 17:14:38 [ERROR] Do you already have another mysqld server running on port: 3306 ?

mysqld[4770]: 080805 17:14:38 [ERROR] Aborting

mysqld[4770]: 

mysqld[4770]: 080805 17:14:38  InnoDB: Starting shutdown...

mysqld[4770]: 080805 17:14:40  InnoDB: Shutdown completed; log sequence number 0 43685

mysqld[4770]: 080805 17:14:40 [Note] /usr/sbin/mysqld: Shutdown complete

mysqld[4770]: 

mysqld_safe[4800]: ended

/etc/init.d/mysql[4930]: 0 processes alive and '/usr/bin/mysqladmin --defaults-file=/etc/mysql/debian.cnf ping' resulted in

/etc/init.d/mysql[4930]: ^G/usr/bin/mysqladmin: connect to server at 'localhost' failed

/etc/init.d/mysql[4930]: error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
/etc/init.d/mysql[4930]: Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!

/etc/init.d/mysql[4930]: 
-----

Can you help me determine why this happening -- especially why it fails to start at boot but then can be started with */etc/init.d/mysql start*

Thank you!

---

### Post by imon9 on 2008-09-26
same thing happening to me... possible bug?
(i'm running intrepid)

---

### Post by moloth on 2008-10-01
The simple answer is your DHCP server hasn't given you an ip address when mysqld starts up. The best solution is to give your server a static ip.

See also [http://ubuntuforums.org/showthread.php?t=821010](http://ubuntuforums.org/showthread.php?t=821010)

---

### Post by kev82 on 2008-11-27
Thought I'd chime in because this is the first thread to pop up when searching for this problem.

I got the same error just recently. I have 2 network adapters in my computer, and when I switched the network cable to the adapter I'm not normally using I couldn't start mysqld. Moved the cable to the old adapter and I could start mysqld again.

---

### Post by reality1011 on 2008-11-27
I just resolved this problem a couple of days ago... here is the thread: 
[http://ubuntuforums.org/showthread.php?t=975203](http://ubuntuforums.org/showthread.php?t=975203) 


this is what I did.... 


My /etc/hosts file needed to have the following line in it to resolve the bind address (below) in /etc/mysql/my.cnf:
> 
127.0.0.1 localhost


I made sure my /etc/mysql/my.cnf file stated the bind address of:
> 
bind-address            =127.0.0.1
**[COLOR="Red"]#bind-address            =localhost ==> this will work if you dont put the above line in /etc/hosts[/COLOR]**


Then I created a start and stop script, which I placed in /etc/init.d
> 
**cappetta@Linux-Box:~$ cat /etc/init.d/start_mysql**
#! /bin/sh
# Reload the Mysql server when an interface comes up, to allow it to start
# listening on new addresses.
log="/tmp/mysql_network.log"
set -e
echo "DATE TIME STARTED: `date`" >> $log

# Is /usr mounted?
if [ ! -e /usr/sbin/mysqld ]; then
        echo " /usr/sbin/mysqld not exist "  >> $log
#       exit 0
fi

/etc/init.d/mysql start  >> log
echo " " >> $log
echo " searching for process " >> $log
echo " `ps -eaf | grep -i mysql`" >> $log
exit 0


The stop Script is almost identical:

> 
**cappetta@Linux-Box:~$ cat /etc/init.d/stop_mysql**
#! /bin/sh
# Reload the Mysql server when an interface comes up, to allow it to start
# listening on new addresses.
log="/tmp/mysql_network.log"
set -e
echo "DATE TIME STARTED: `date`" >> $log

# Is /usr mounted?
if [ ! -e /usr/sbin/mysqld ]; then
        echo " /usr/sbin/mysqld not exist "  >> $log
#       exit 0
fi

/etc/init.d/mysql stop >> log
echo " " >> $log
echo " searching for process " >> $log
echo " `ps -eaf | grep -i mysql`" >> $log
exit 0





Then you need to active these scripts... best way to do that is the following command :

> 
cappetta@Linux-Box:/etc$ [COLOR="Red"]**sudo update-rc.d start_mysql  start 90 2 3 4 5 .**[/COLOR]
 Adding system startup for /etc/init.d/start_mysql ...
   /etc/rc2.d/S90start_mysql -> ../init.d/start_mysql
   /etc/rc3.d/S90start_mysql -> ../init.d/start_mysql
   /etc/rc4.d/S90start_mysql -> ../init.d/start_mysql
   /etc/rc5.d/S90start_mysql -> ../init.d/start_mysql


cappetta@Linux-Box:/etc$ **[COLOR="Red"]sudo update-rc.d  stop_mysql  stop 20 0 1 6 .[/COLOR]**
 Adding system startup for /etc/init.d/stop_mysql ...
   /etc/rc0.d/K20stop_mysql -> ../init.d/stop_mysql
   /etc/rc1.d/K20stop_mysql -> ../init.d/stop_mysql
   /etc/rc6.d/K20stop_mysql -> ../init.d/stop_mysql




Just to touch upon the thought of making your address static to resolve this problems.... I tried that, it didn't help... the above works:


> 
cappetta@Linux-Box:/etc/network$ cat interfaces
auto lo
iface lo inet loopback


iface eth0 inet static
address 192.168.0.134
netmask 255.255.255.0
network 192.168.0.1
broadcase 192.168.0.255
gateway 192.168.0.1

#auto eth1
#iface eth1 inet static
#address 192.168.0.134
#netmask 255.255.255.0
#gateway 192.168.0.1

#auto eth2
iface eth2 inet static
address 192.168.0.134
netmask 255.255.255.0
gateway 192.168.0.1

auto ath0
#iface ath0 inet dhcp

auto wlan0
#iface wlan0 inet dhcp

auto eth2
cappetta@Linux-Box:/etc/network$


---

### Post by NiteOwls on 2009-07-11
Hi All,
 
same story with my MySQL.
 
matmcnic I tried your solution and no luck, 
 
I have a static address and it worked fine with that one before this failure started. The only clue I have regarding where it start to fail is after I applied the auto updates, which cause me on Windows headaches enough, now on Linux as well :)
 
any way, I notice that the system fails on boot, however when I used the /etc/init.d/mysql start, My SQL starts fine! so what on earth is broken? because on boot it complains that the socket is already in use, by what?
 
The MySQL logs are all empty, so it is to me a guess as to what is wrong.
 
I am not explicit looking for re-installing MySQL but think more and more about it.
 
Lucky that this is a test machine, so if I have to trash it it is not going to be a major issue, but still I would rather like to solve the issue then to just re-install.
 
Any additional thoughts??
 
Oh, I am not quite a expert on Linux, I worked 8 years ago with SUN Solaris, not quite the same and after that I worked mainly with Windows, so I am brushing up my skills on Linux (UBUNTY 9.04) as I am in to the deployment of the astriks telephony server.
 
So I hope that I can fix this issue without losing the MySQL DB as I didn't take a backup yet, as I still was installing the machine......

Thanks for your thoughts.
 
~JH

---

