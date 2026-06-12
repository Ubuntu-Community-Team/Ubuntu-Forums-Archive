---
title: "Problems with proftpd"
date: 2009-03-12
forum: Installation &amp; Upgrades
---

### Post by einar90 on 2009-03-12
Hi
I installed proftpd earlier today, and it worked fine, untill I did a reboot. Now, when I try to start it, I just get a bunch of errors:
```
einar@einar-desktop:~$ sudo /etc/init.d/proftpd start
 - notice: unable to bind to Unix domain socket at '/var/run/proftpd/test.sock': No such file or directory
 - notice: unable to listen to local socket: Operation not permitted
einar-desktop - 127.0.1.1:1980 masquerading as 77.222.188.113
einar-desktop - mod_delay/0.6: error opening DelayTable '/var/run/proftpd/proftpd.delay': No such file or directory
einar-desktop - notice: unable to listen to local socket: Operation not permitted

```
This is my proftpd.conf :
```
# To really apply changes reload proftpd after modifications.
AllowOverwrite on
AuthAliasOnly on

# Choose here the user alias you want !!!!
UserAlias blah userftp

ServerName			"einarFTP"
ServerType 			standalone
DeferWelcome			on

MultilineRFC2228 on
DefaultServer			on
ShowSymlinks			off

TimeoutNoTransfer 600
TimeoutStalled 100
TimeoutIdle 2200

DisplayFirstChdir               .message
ListOptions                	"-l"

RequireValidShell 		off

TimeoutLogin 20

RootLogin 			off

# It's better for debug to create log files ;-)
ExtendedLog 			/var/log/ftp.log
TransferLog 			/var/log/xferlog
SystemLog			/var/log/syslog.log

#DenyFilter			\*.*/

# I don't choose to use /etc/ftpusers file (set inside the users you want to ban, not useful for me)
UseFtpUsers off

# Allow to restart a download
AllowStoreRestart		on

# Port 21 is the standard FTP port, so don't use it for security reasons (choose here the port you want)
Port				1980

# To prevent DoS attacks, set the maximum number of child processes
# to 30.  If you need to allow more than 30 concurrent connections
# at once, simply increase this value.  Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd)
MaxInstances 8

# Set the user and group that the server normally runs at.
User                  nobody
Group                 nogroup

# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask				022	022

PersistentPasswd		off

MaxClients 8
MaxClientsPerHost 8
MaxClientsPerUser 8
MaxHostsPerUser 8

# Display a message after a successful login
AccessGrantMsg "Velkommen. Kontakt meg på MSN hvis du ikke finner det du leter etter."
# This message is displayed for each access good or not
ServerIdent                  on       "Hei"

# Set /home/FTP-shared directory as home directory
DefaultRoot /home/FTP-shared

# Lock all the users in home directory, ***** really important *****
DefaultRoot ~

MaxLoginAttempts    5

#VALID LOGINS
<Limit LOGIN>
AllowUser userftp
DenyALL
</Limit>

<Directory /home/FTP-shared>
Umask 022 022
AllowOverwrite off
	<Limit MKD STOR DELE XMKD RNRF RNTO RMD XRMD>
	DenyAll
	</Limit>
</Directory>

<Directory /home/FTP-shared/download/*>
Umask 022 022
AllowOverwrite off
	<Limit MKD STOR DELE XMKD RNEF RNTO RMD XRMD>
	DenyAll
	</Limit>
</Directory>

<Directory> /home/FTP-shared/upload/>
Umask 022 022
AllowOverwrite on
	<Limit READ RMD DELE>
      	DenyAll
    	</Limit>

    	<Limit STOR CWD MKD>
      	AllowAll
    	</Limit>
</Directory>
MasqueradeAddress	78.252.178.113
PassivePorts 60000 65535	# These ports should be safe...
```

And when I do proftpd -td5 I get:
```
einar@einar-desktop:~$ sudo proftpd -td5
Checking syntax of configuration file
 - notice: unable to bind to Unix domain socket at '/var/run/proftpd/test.sock': No such file or directory
 - notice: unable to listen to local socket: Operation not permitted
 - <Directory /home/FTP-shared>: deferring resolution of path
 - <Directory /home/FTP-shared/download/*>: deferring resolution of path
 - <Directory /home/FTP-shared/upload/>: deferring resolution of path
einar-desktop - 127.0.1.1:1980 masquerading as 77.222.188.113
einar-desktop - 
einar-desktop - Config for einarFTP:
einar-desktop - /home/FTP-shared/upload/
einar-desktop -  Limit
einar-desktop -   AllowAll
einar-desktop -  Limit
einar-desktop -   DenyAll
einar-desktop -  Umask
einar-desktop -  DirUmask
einar-desktop -  AllowOverwrite
einar-desktop -  AuthAliasOnly
einar-desktop -  UserAlias
einar-desktop -  ShowSymlinks
einar-desktop -  DisplayChdir
einar-desktop -  ListOptions
einar-desktop -  RequireValidShell
einar-desktop -  RootLogin
einar-desktop -  TransferLog
einar-desktop -  UseFtpUsers
einar-desktop -  AllowStoreRestart
einar-desktop -  MaxClients
einar-desktop -  MaxClientsPerHost
einar-desktop -  MaxClientsPerUser
einar-desktop -  MaxHostsPerUser
einar-desktop -  AccessGrantMsg
einar-desktop - /home/FTP-shared/download/*
einar-desktop -  Limit
einar-desktop -   DenyAll
einar-desktop -  Umask
einar-desktop -  DirUmask
einar-desktop -  AllowOverwrite
einar-desktop -  AuthAliasOnly
einar-desktop -  UserAlias
einar-desktop -  ShowSymlinks
einar-desktop -  DisplayChdir
einar-desktop -  ListOptions
einar-desktop -  RequireValidShell
einar-desktop -  RootLogin
einar-desktop -  TransferLog
einar-desktop -  UseFtpUsers
einar-desktop -  AllowStoreRestart
einar-desktop -  MaxClients
einar-desktop -  MaxClientsPerHost
einar-desktop -  MaxClientsPerUser
einar-desktop -  MaxHostsPerUser
einar-desktop -  AccessGrantMsg
einar-desktop - /home/FTP-shared
einar-desktop -  Limit
einar-desktop -   DenyAll
einar-desktop -  Umask
einar-desktop -  DirUmask
einar-desktop -  AllowOverwrite
einar-desktop -  AuthAliasOnly
einar-desktop -  UserAlias
einar-desktop -  ShowSymlinks
einar-desktop -  DisplayChdir
einar-desktop -  ListOptions
einar-desktop -  RequireValidShell
einar-desktop -  RootLogin
einar-desktop -  TransferLog
einar-desktop -  UseFtpUsers
einar-desktop -  AllowStoreRestart
einar-desktop -  MaxClients
einar-desktop -  MaxClientsPerHost
einar-desktop -  MaxClientsPerUser
einar-desktop -  MaxHostsPerUser
einar-desktop -  AccessGrantMsg
einar-desktop - Limit
einar-desktop -  AllowUser
einar-desktop -  DenyAll
einar-desktop - AllowOverwrite
einar-desktop - AuthAliasOnly
einar-desktop - UserAlias
einar-desktop - DeferWelcome
einar-desktop - DefaultServer
einar-desktop - ShowSymlinks
einar-desktop - TimeoutNoTransfer
einar-desktop - TimeoutStalled
einar-desktop - TimeoutIdle
einar-desktop - DisplayChdir
einar-desktop - ListOptions
einar-desktop - RequireValidShell
einar-desktop - TimeoutLogin
einar-desktop - RootLogin
einar-desktop - ExtendedLog
einar-desktop - TransferLog
einar-desktop - UseFtpUsers
einar-desktop - AllowStoreRestart
einar-desktop - UserID
einar-desktop - UserName
einar-desktop - GroupID
einar-desktop - GroupName
einar-desktop - Umask
einar-desktop - DirUmask
einar-desktop - MaxClients
einar-desktop - MaxClientsPerHost
einar-desktop - MaxClientsPerUser
einar-desktop - MaxHostsPerUser
einar-desktop - AccessGrantMsg
einar-desktop - ServerIdent
einar-desktop - DefaultRoot
einar-desktop - DefaultRoot
einar-desktop - MaxLoginAttempts
einar-desktop - MasqueradeAddress
einar-desktop - PassivePorts
einar-desktop - mod_delay/0.6: error opening DelayTable '/var/run/proftpd/proftpd.delay': No such file or directory
einar-desktop - notice: unable to listen to local socket: Operation not permitted
Syntax check complete.
einar-desktop - mod_delay/0.6: warning: unable to open DelayTable '/var/run/proftpd/proftpd.delay': No such file or directory

```

I've used these two guides to set it all up:
[http://ubuntuforums.org/showthread.php?t=51611](http://ubuntuforums.org/showthread.php?t=51611)
[http://www.brandonhutchinson.com/standalone_proftpd.html](http://www.brandonhutchinson.com/standalone_proftpd.html)
(I set it up as inetd first, and it took a while to get it working properly as standalone, and I'm thinking I might have messed something up in the process)

I'm hoping this is enough information.

---

### Post by einar90 on 2009-03-13
Doesn't anyone know what's wrong here, and how to fix it?
(sorry for double posting/bumping)

---

### Post by Toadinator on 2009-05-18
bump same problem.

---

### Post by hvw on 2009-10-02
I've just found issue for 9.04 one. The matter of the problem is lack of conf-files and dirs recreation after reinstalling proftpd package (may be lack of proftpd-common had been presented in the earlier versions).

When i've been installing proftpd for the first time, i choose inetd ServerType. Then, after some manipulations with server and some reboots It had broken with:
```
 - notice: unable to bind to Unix domain socket at '/var/run/proftpd/test.sock': Permission denied
 - notice: unable to listen to local socket: Operation not permitted
 - Fatal: SystemLog: unable to redirect logging to '/var/log/proftpd/proftpd.log': Permission denied on line 89 of '/etc/proftpd/proftpd.conf'
```

Then i tried to reinstall package after purging it:
```
sudo dpkg --purge proftpd
```

It doesn't help me, so i tried the second with removing conf-files in /etc/proftpd and the directories for proftpd packages (after backup):
```
rm -rd /etc/proftpd/
rm -rd /var/run/proftpd/
rm -rd /var/log/proftpd/
```

After reinstall try to start proftpd, failed with the errors, telling that there is no conf-file '/etc/proftpd/proftpd.conf', '/var/run/proftpd/test.sock' sock file and '/var/log/proftpd/proftpd.log' log file. So i tried the first to recreate only directories for them and copy '/etc/proftpd/proftpd.conf' file (as root):
```
mkdir /etc/proftpd/
cp proftpd.conf /etc/proftpd/proftpd.conf
 mkdir /var/run/proftpd/
 mkdir /var/log/proftpd/
proftpd
```

Then i've replaced ServerType from 'intetd' to 'standalone' at '/etc/proftpd/proftpd.conf' and now it works even after reboot.

---

### Post by mellthy on 2009-11-19
in my case it was enough to create directory "/var/run/proftpd/".

---

### Post by dasein.savage on 2010-09-22
Creating "/var/run/proftpd/" helps to run proftpd. But, after rebooting this directory doesn't exist again. How to keep this directory?

---

