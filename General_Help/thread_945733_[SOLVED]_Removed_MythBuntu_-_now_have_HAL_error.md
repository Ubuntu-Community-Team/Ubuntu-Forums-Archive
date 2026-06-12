---
title: "[SOLVED] Removed MythBuntu - now have HAL error"
date: 2008-10-12
forum: General Help
---

### Post by *B* on 2008-10-12
First off, excuse any tone you may sense......... Im more than a little cheesed off. After a day and a half of trying to get the backend to connect to the database on MythTV (I dont care what ANYONE says..... that was ridiculous, nothing, I repeat NOTHING should be THAT difficult to set up) and reading countless posts and tutorials (where countless paople had the same problem and never got it resolved) I gave up. I used synaptic to remove MythTv and then install MythBuntu because I read how much easier it was to set up. Horsehockey. (it used the same identical backend database setup page)

I then wasted a  day and a half trying to get Mythbuntu to connect to the database, no luck. And, from what i read, its a VERY common problem.

Anyway, I digress......... I was fed up with the entire idea and decided to remove Mythbuntu and just boot back to XP to watch or record TV. After using synaptic to remove mythbuntu, I now get the "Hal failed to initialize" error.

I then wasted 3 hours looking around the forums and trying different suggestions, but nothing works. I am running a fully updated 32bit version of Ubuntu. 

When I try to re-install HAL through synaptic I receive:
```
E: hal: subprocess post-installation script returned error exit status 1
E: hal-cups-utils: dependency problems - leaving unconfigured"
```

If I try to do it via terminal I get:
```
usernamehere@Tower1-Ubuntu:~$ sudo apt-get install hal
Reading package lists... Done
Building dependency tree       
Reading state information... Done
hal is already the newest version.
The following packages were automatically installed and are no longer required:
  pwgen libconvert-binhex-perl libwildmidi0 libmpich1.0gf libsoap-lite-perl
  apache2-utils libxml-libxml-common-perl libnet-daemon-perl libsoundtouch1c2
  libcrypt-ssleay-perl libnet-ssleay-perl libqt3-mt-mysql
  libxml-namespacesupport-perl libxml-perl python-mysqldb libgfortran2 fftw2
  php5 libdbi-perl libdbd-mysql-perl libopenspc0 libapr1 mysql-common
  libmyth-0.21-0 libcarp-clan-perl libxml-xql-perl apache2-mpm-prefork
  libossp-uuid-perl libmime-tools-perl libplrpc-perl libparse-yapp-perl
  libemail-date-perl libmysqlclient15off apache2 libossp-uuid15
  libxml-dom-perl libfile-temp-perl libemail-simple-perl libtime-piece-perl
  apache2.2-common libemail-abstract-perl libio-stringy-perl
  libxml-libxml-perl libxml-sax-perl libdate-manip-perl libmime-perl
  libcdaudio1 libmime-lite-perl libxml-simple-perl libfcgi-perl libmyth-perl
  libmodule-pluggable-perl libimage-size-perl libpq5 php5-mysql
  libio-socket-ssl-perl libxml-regexp-perl libnet-upnp-perl
  libapache2-mod-php5 libaprutil1 php5-common libmms0 libiptcdata0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up hal (0.5.11~rc2-1ubuntu8.2) ...
Reloading system message bus config...Failed to open connection to system message bus: Failed to connect to socket /var/run/dbus/system_bus_socket: No such file or directory
invoke-rc.d: initscript dbus, action "force-reload" failed.
polkit-auth: This operation requires the system message bus and ConsoleKit to be running
polkit-auth: AuthorizationAlreadyExists: An authorization for uid 107 for the action org.freedesktop.policykit.read with constraint '' already exists
dpkg: error processing hal (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of hal-cups-utils:
 hal-cups-utils depends on hal; however:
  Package hal is not configured yet.
dpkg: error processing hal-cups-utils (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 hal
 hal-cups-utils
E: Sub-process /usr/bin/dpkg returned an error code (1)

usernamehere@Tower1-Ubuntu:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  pwgen libconvert-binhex-perl libwildmidi0 libmpich1.0gf libsoap-lite-perl apache2-utils libxml-libxml-common-perl
  libnet-daemon-perl libsoundtouch1c2 libcrypt-ssleay-perl libnet-ssleay-perl libqt3-mt-mysql libxml-namespacesupport-perl
  libxml-perl python-mysqldb libgfortran2 fftw2 php5 libdbi-perl libdbd-mysql-perl libopenspc0 libapr1 mysql-common
  libmyth-0.21-0 libcarp-clan-perl libxml-xql-perl apache2-mpm-prefork libossp-uuid-perl libmime-tools-perl libplrpc-perl
  libparse-yapp-perl libemail-date-perl libmysqlclient15off apache2 libossp-uuid15 libxml-dom-perl libfile-temp-perl
  libemail-simple-perl libtime-piece-perl apache2.2-common libemail-abstract-perl libio-stringy-perl libxml-libxml-perl
  libxml-sax-perl libdate-manip-perl libmime-perl libcdaudio1 libmime-lite-perl libxml-simple-perl libfcgi-perl libmyth-perl
  libmodule-pluggable-perl libimage-size-perl libpq5 php5-mysql libio-socket-ssl-perl libxml-regexp-perl libnet-upnp-perl
  libapache2-mod-php5 libaprutil1 php5-common libmms0 libiptcdata0
The following packages will be REMOVED:
  apache2 apache2-mpm-prefork apache2-utils apache2.2-common fftw2 libapache2-mod-php5 libapr1 libaprutil1 libcarp-clan-perl
  libcdaudio1 libconvert-binhex-perl libcrypt-ssleay-perl libdate-manip-perl libdbd-mysql-perl libdbi-perl
  libemail-abstract-perl libemail-date-perl libemail-simple-perl libfcgi-perl libfile-temp-perl libgfortran2 libimage-size-perl
  libio-socket-ssl-perl libio-stringy-perl libiptcdata0 libmime-lite-perl libmime-perl libmime-tools-perl libmms0
  libmodule-pluggable-perl libmpich1.0gf libmysqlclient15off libmyth-0.21-0 libmyth-perl libnet-daemon-perl libnet-ssleay-perl
  libnet-upnp-perl libopenspc0 libossp-uuid-perl libossp-uuid15 libparse-yapp-perl libplrpc-perl libpq5 libqt3-mt-mysql
  libsoap-lite-perl libsoundtouch1c2 libtime-piece-perl libwildmidi0 libxml-dom-perl libxml-libxml-common-perl
  libxml-libxml-perl libxml-namespacesupport-perl libxml-perl libxml-regexp-perl libxml-sax-perl libxml-simple-perl
  libxml-xql-perl mysql-common php5 php5-common php5-mysql pwgen python-mysqldb
0 upgraded, 0 newly installed, 63 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 54.5MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 193309 files and directories currently installed.)
Removing apache2 ...
Removing php5 ...
Removing php5-mysql ...
Removing libapache2-mod-php5 ...
Module php5 disabled; run /etc/init.d/apache2 force-reload to fully disable.
Removing apache2-mpm-prefork ...
Stopping web server: apache2apache2: Could not reliably determine the server's fully qualified domain name, using 192.168.1.13 for ServerName
httpd (no pid file) not running
.
Removing apache2.2-common ...
Removing apache2-utils ...
Removing fftw2 ...
Removing libaprutil1 ...
Removing libapr1 ...
Removing libcarp-clan-perl ...
Removing libcdaudio1 ...
Removing libsoap-lite-perl ...
Removing libmime-perl ...
Removing libmime-tools-perl ...
Removing libconvert-binhex-perl ...
Removing libcrypt-ssleay-perl ...
Removing libxml-xql-perl ...
Removing libdate-manip-perl ...
Removing libmyth-perl ...
Removing libdbd-mysql-perl ...
Removing libdbi-perl ...
Removing libmime-lite-perl ...
Removing libemail-date-perl ...
Removing libemail-abstract-perl ...
Removing libemail-simple-perl ...
Removing libfcgi-perl ...
Removing libfile-temp-perl ...
Removing libmpich1.0gf ...
Removing libgfortran2 ...
Removing libimage-size-perl ...
Removing libio-socket-ssl-perl ...
Removing libio-stringy-perl ...
Removing libiptcdata0 ...
Removing libmms0 ...
Removing libmodule-pluggable-perl ...
Removing python-mysqldb ...
Removing libmyth-0.21-0 ...
Removing libqt3-mt-mysql ...
Removing libmysqlclient15off ...
Removing libplrpc-perl ...
Removing libnet-daemon-perl ...
Removing libnet-ssleay-perl ...
Removing libnet-upnp-perl ...

Removing libopenspc0 ...
Removing libossp-uuid-perl ...
Removing libossp-uuid15 ...
Removing libparse-yapp-perl ...
Removing libpq5 ...
Removing libsoundtouch1c2 ...
Removing libtime-piece-perl ...
Removing libwildmidi0 ...
Removing libxml-dom-perl ...
Removing libxml-simple-perl ...
Removing libxml-libxml-perl ...
update-perl-sax-parsers: Removing Perl SAX parser module info file of XML::LibXML::SAX::Parser...
update-perl-sax-parsers: Removing Perl SAX parser module info file of XML::LibXML::SAX...
update-perl-sax-parsers: Updating overall Perl SAX parser modules info file...
Removing libxml-libxml-common-perl ...
Removing libxml-sax-perl ...
Removing libxml-namespacesupport-perl ...
Removing libxml-perl ...
Removing libxml-regexp-perl ...
Removing mysql-common ...
Removing php5-common ...
Removing pwgen ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Setting up hal (0.5.11~rc2-1ubuntu8.2) ...
Reloading system message bus config...Failed to open connection to system message bus: Failed to connect to socket /var/run/dbus/system_bus_socket: No such file or directory
invoke-rc.d: initscript dbus, action "force-reload" failed.
polkit-auth: This operation requires the system message bus and ConsoleKit to be running
polkit-auth: AuthorizationAlreadyExists: An authorization for uid 107 for the action org.freedesktop.policykit.read with constraint '' already exists
dpkg: error processing hal (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of hal-cups-utils:
 hal-cups-utils depends on hal; however:
  Package hal is not configured yet.
dpkg: error processing hal-cups-utils (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 hal
 hal-cups-utils
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

My system still has internet and network, but wont shut down now. When I click on the shut down button, nothing happens. I end up having to do a ctrl-alt-backspace to bring me to login screen, then tell it to shut down.

Any and all help is GREATLY appreciated.

---

### Post by cariboo on 2008-10-12
Have you tried System-->Administration-->Synaptic Package Manager-->Edit-->Fix broken packages?

Jim

---

### Post by *B* on 2008-10-12
Yes. Sorry, I forgot to mention that in the OP. When I try to "fix broken packages" by highlighting HAL  in synaptic, I get a response on the bottom bar that says "successfully fixed dependency problems"....... but the problem still exists.

---

### Post by Yellow Pasque on 2008-10-12
The problem isn't so much with HAL as with dbus. 
> Reloading system message bus config...Failed to open connection to system message bus: Failed to connect to socket /var/run/dbus/system_bus_socket: No such file or directory

-Is the file present? (This command should show "system_bus_socket" as a file)
```
ls /var/run/dbus
```
If not, what does it give you?

---

### Post by *B* on 2008-10-12
No, that file is gone. When I ran the command, nothing happened. Nautilus shows the /var/run/dbus folder empty. I have it set to show hidden files. I searched "file system" for "system_bus_socket" and came up with nothing. I also have a laptop with Ubuntu on it, but cannot transfer the file across the network or even to a thumb drive to replace it on this system.

---

### Post by Yellow Pasque on 2008-10-12
Ok, try this command. What output does it give you?
```
sudo /etc/init.d/dbus start
```

---

### Post by *B* on 2008-10-12
OK, I re-installed dbus
```
sudo aptitude reinstall dbus
```

I then verified in file browser that pid & system_socket_bus were in /var/run/dbus

then ran your command to start dbus
```
sudo /etc/init.d/dbus start
```


and got the following
```
system message bus already started; not starting.
```

so, I am going to try to restart and see what happens.

EDIT: No go........ I did a ctrl-alt-backspc to restart session, logged in..... no HEL error message and files were where they should be.

RESTART the computer, and files are gone and HAL error is back :-(

EDIT #2: I reinstalled dbus & hal (again) I started them both (they were already running) but am afraid to reboot the system and lose what I have accomplished... again  lol

---

### Post by *B* on 2008-10-12
Finally rebooted and lost the /var/run/dbus files again, which brings back the HAL error. I dont get it. I can restart the session with ctrl-alt-bckspc and everything is fine. I reboot or shut the system off and start it back up, and the files disappear, and the HAL error is there. Any ideas? This passed aggravating 6 states ago lol.

---

### Post by Yellow Pasque on 2008-10-13
Perhaps something screwed up your /etc/rc2.d directory. What is output from:
```
ls /etc/rc2.d
```

---

### Post by *B* on 2008-10-13
ls /etc/rc2.d
```
K50ntp                       S20hotkey-setup       S25bluetooth
README                       S20makedev            S25pulseaudio
S01policykit                 S20nbd-client         S30gdm
S05vbesave                   S20nbd-server         S40dhcp3-server
S10acpid                     S20nfs-common         S50alsa-utils
S10powernowd.early           S20nfs-kernel-server  S51lirc
S10sysklogd                  S20nvidia-kernel      S51mythtv-status
S10xserver-xorg-input-wacom  S20nvtv               S89anacron
S11klogd                     S20openbsd-inetd      S89atd
S12dbus                      S20powernowd          S89cron
S17mysql-ndb-mgm             S20rsync              S90binfmt-support
S17portmap                   S20samba              S91apache2
S18avahi-daemon              S20tftpd-hpa          S98usplash
S18mysql-ndb                 S20vdr                S99acpi-support
S19cupsys                    S20winbind            S99laptop-mode
S19mysql                     S24dhcdbd             S99rc.local
S20apmd                      S24hal                S99rmnologin
S20apport                    S24mythtv-backend     S99stop-readahead
```

---

### Post by Yellow Pasque on 2008-10-13
I don't know what else to tell you then, except maybe restarting your computer and looking for relevant error messages with dmesg | grep dbus

At least Synaptic/apt-get works now, after you manually start dbus & hal, right?

---

### Post by *B* on 2008-10-13
```
dmesg | grep dbus
```

returned nothing at all. When I pasted it into a terminal, I couldnt even tell anythig happened. So, Im guessing there are no messages related to dbus.

As far as I know, apt-get & synaptic never stopped working at any time. They work fine right now (just checked) and I havent reinstalled dbus or hal yet (after reboot & checking for messages). I couldnt use synaptic to reinstall hal at first, btu that was the dbus problem preventing it, not synaptic itself.... I think...lol.

---

### Post by Yellow Pasque on 2008-10-13
Ok, so if HAL installed, what is the problem then? Still not shutting down properly?

---

### Post by *B* on 2008-10-13
when I reinstall HAL & dbus it then recreates the pids & system_bus_socket files in /var/run/dbus. I can restart a session w/ctrl-alt-bckspc and those 2 files are still there and functioning when I log back in..... no "HAL failed to initialize" error.

As soon as I do a reboot or shut the machine off and turn it back on (anything other than restarting the session) I get the HAL error, and those 2 files have somehow vanished from /var/run/dbus again after booting. I then reinstall dbus & HAL & make sure they are started, and the files are there and working properly again.

Its a vicious cycle. Every time I turn the machine on or reboot it, I get the error and have to reload dbus & HAL and everything is fine till the next shutdown or reboot. Somehow these files are getting deleted during a shutdown or boot process

And BTW.......... THANK YOU for all your thoughts and help. It is GREATLY appreciated!

---

### Post by Yellow Pasque on 2008-10-14
> Somehow these files are getting deleted during a shutdown or boot process
 Think of them as temporary files. The problem is that they're not being created at startup because dbus isn't starting. I'm not sure where to direct you from here (except for perhaps filing a bug on Launchpad)

YOu might want to try booting into recovery mode and seeing if dbus starts with:
```
cd /etc/init.d
./dbus start
```

---

### Post by *B* on 2008-10-14
Ah, well, that makes sense I guess.

I booted to recovery and dbus does start.

Ill look into posting the bug. 

Thanks again.

---

### Post by *B* on 2008-10-14
UPDATE: As of 10:30pm CST, the system is stable. Evidently either the dbus update or kernel 21 update fixed whatever the problem was. I have rebooted the machine at least 6 times now with no HAL error at all. Thanks for your help, and I will mark this solved.

---

### Post by Giuca on 2009-08-08
Hi all.
I had the same problem with
"/var/run/dbus/system_bus_socket: No such file or directory"
caused by the avahi-daemon.

Everything happened just as you stated in your threads. No files under dbus directory, etc.

The workaround was simply let the avahi-dnsconfd run on startup, which unexpectedly was set to "Off".

Hope it helps others.

Thanks

---

