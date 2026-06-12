---
title: "cannot print to local CUPS printer"
date: 2006-04-14
forum: Hardware &amp; Laptops
---

### Post by arsnova on 2006-04-14
Greetings from the latest noob casualty of CUPS/SAMBA. I'm using Breezy Badger with CUPS 1.1.23 and SAMBA 3.0.14. Would someone mind helping me and let me know how off-track I am? 

It seems the looming problem is that I'm unable to print to a *local* USB printer (Epson Stylus Photo R200). The print job sends with no apparent permission problems (until I look at my log file...?), but then hangs. Originally, I could print both locally and across the network using SAMBA, but, somewhere in my installation of SSH, I broke it. I've since reinstalled UBUNTU (as a last resort, of course; after a reboot, the sytem was hanging, and I couldn't browse the file system at all.) I've also reinstalled CUPS and SAMBA, but without any luck in the printing department. I'm running a firewall (Firestarter) with port 631 allowing printing across the network.

At this point, I *can* share files through SAMBA on a networked WinXP machine. I *cannot* print from the WinXP client -- which must be obvious, since I also can't print from the local Linux machine. I have the GIMP print drivers installed, along with foomatic. I'm able to browse localhost:631 on the Linux machine, where my description -- after printing a test page as user root -- reads as:

[SIZE="1"]
>Description: Stylus-Photo-R200
>Location:
>Printer State: processing, accepting jobs.
>"USB printer is busy; will retry in 5 seconds..."
>Device URI: usb://EPSON/Stylus%20Photo%20R200
[/SIZE]

I followed precisely the tutorial found at <http://www.howtoforge.com/samba_setup_ubuntu_5.10>, which worked for me originally, but not after the reinstallation. I'm including CUPS log files and SAMBA and CUPS config files, with the hopes of being as informative as possible... I hope it's not overkill! 

-----------------------------
My CUPS error log reads as:

[SIZE="1"]
E [13/Apr/2006:23:28:45 -0500] IsAuthorized: pam_authenticate() returned 7 (Authentication failure)!
I [13/Apr/2006:23:28:51 -0500] Started "/usr/lib/cups/cgi-bin/jobs.cgi" (pid=19339)
I [13/Apr/2006:23:28:54 -0500] Started "/usr/lib/cups/cgi-bin/jobs.cgi" (pid=19341)
I [13/Apr/2006:23:28:57 -0500] Started "/usr/lib/cups/cgi-bin/printers.cgi" (pid=19342)
I [13/Apr/2006:23:29:04 -0500] Started "/usr/lib/cups/cgi-bin/printers.cgi" (pid=19345)
I [13/Apr/2006:23:29:04 -0500] Adding start banner page "none" to job 1.
I [13/Apr/2006:23:29:04 -0500] Adding end banner page "none" to job 1.
I [13/Apr/2006:23:29:04 -0500] Job 1 queued on 'Stylus-Photo-R200' by 'root'.
I [13/Apr/2006:23:29:04 -0500] Started filter /usr/lib/cups/filter/pstops (PID 19347) for job 1.
I [13/Apr/2006:23:29:04 -0500] Started filter /usr/lib/cups/filter/pstoraster (PID 19348) for job 1.
I [13/Apr/2006:23:29:04 -0500] Started filter /usr/lib/cups/filter/rastertoprinter (PID 19350) for job 1.
I [13/Apr/2006:23:29:04 -0500] Started backend /usr/lib/cups/backend/usb (PID 19351) for job 1.
I [13/Apr/2006:23:29:08 -0500] Started "/usr/lib/cups/cgi-bin/jobs.cgi" (pid=19353)
I [13/Apr/2006:23:29:12 -0500] Started "/usr/lib/cups/cgi-bin/jobs.cgi" (pid=19356)
I [13/Apr/2006:23:29:14 -0500] Started "/usr/lib/cups/cgi-bin/printers.cgi" (pid=19357)
I [13/Apr/2006:23:32:15 -0500] Started "/usr/lib/cups/cgi-bin/jobs.cgi" (pid=19437)
[/SIZE]
-----------------------------

My smb.conf file is as follows (I've removed the commented lines in the interest of space):

[SIZE="1"]
[global]

   workgroup = CONSORT
   netbios name = KAPSBERGER

   server string = %h server (Samba, Ubuntu)
   dns proxy = no

   name resolve order = wins bcast hosts
   domain logons = yes
   preferred master = yes
   wins support = yes

   log file = /var/log/samba/log.%m
   max log size = 1000
   syslog = 0

   panic action = /usr/share/samba/panic-action %d

   security = user
   username map = /etc/samba/smbusers
   encrypt passwords = true
   passdb backend = tdbsam
   obey pam restrictions = yes
   invalid users = root

   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n .

   printing = CUPS
   printcap name = CUPS

   logon drive = Z:
   logon path = \\server1\profile\%U

   socket options = TCP_NODELAY

   # Useradd scripts
   add user script = /usr/sbin/useradd -m %u
   delete user script = /usr/sbin/userdel -r %u
   add group script = /usr/sbin/groupadd %g
   delete group script = /usr/sbin/groupdel %g
   add user to group script = /usr/sbin/usermod -G %g %u
   add machine script = /usr/sbin/useradd -s /bin/false/ -d /var/lib/nobody %u
   idmap uid = 15000-20000
   idmap gid = 15000-20000

   # sync smb passwords woth linux passwords
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n .
   passwd chat debug = yes
   unix password sync = yes

   # set the loglevel
   log level = 3


[homes]
   comment = Home Directories
   browseable = no
   valid users = %S
   read only = no
   browsable = no
   writable = no
   create mask = 0700
   directory mask = 0700


[netlogon]
   comment = Network Logon Service
   path = /home/samba/netlogon
   admin users = Administrator
   valid users = %U
   read only = no

[printers]
   comment = All Printers
   path = /var/spool/samba
   printable = yes
   guest ok = yes
   browsable = yes
   browseable = yes

[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   browsable = yes
   read only = yes
   guest ok = no

[profile]
   comment = User profiles
   path = /home/samba/profiles
   valid users = %U
   create mode = 0600
   directory mode = 0700
   writable = yes
   browsable = no

[allusers]
  comment = All Users
  path = /home/shares/allusers
  valid users = @users
  force group = users 
  create mask = 0660
  directory mask = 0771
  writable = yes
[/SIZE]
-----------------------------

And, finally my cupsd.conf file (again, with comments removed):

[SIZE="1"]
ConfigFilePerm 0600
DefaultCharset notused
LogLevel info

Printcap /var/run/cups/printcap

RunAsUser Yes

Listen 127.0.0.1:631
Listen 192.168.15.100:631

Include cupsd-browsing.conf
BrowseAddress @LOCAL

<Location />
Order Deny,Allow
Deny From All
Allow From 127.0.0.1
</Location>

<Location /jobs>
AuthType Basic
AuthClass User
</Location>

<Location /admin>
AuthType Basic
AuthClass Group
## Restrict access to local domain
Order Deny,Allow
Deny From All
Allow From 127.0.0.1
Allow From 192.168.15.100
Allow From 192.168.15.101
#Encryption Required
</Location>
[/SIZE]
-----------------------------

Thank you in advance for your insights and suggestions. I'll try my best to answer any questions I've left open.

---

