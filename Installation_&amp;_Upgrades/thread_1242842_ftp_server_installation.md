---
title: "ftp server installation"
date: 2009-08-17
forum: Installation &amp; Upgrades
---

### Post by ahtasham82 on 2009-08-17
hi guys,

Im new, I need to install ftp server on my online ubuntu server...I am a developer and I need to setup ftp on my server. We have a dedicated server on which UBUNTU 8 is installed. I have installed vsftp and its running...but I cannot connect to my server via FTP...vsftpd is installed and I still cannot connect using my FTP Client...

I really need to set it up...I need your help guys...its very urgent....

looking forward to your quick reply...

Thanks in advance...

Ahtasham

---

### Post by Bachstelze on 2009-08-17
You don't give enough information. Are you trying to connect using an account or anonymously? Are you using SSL? Etc.

Anyway, the vsftpd config file is well documented, you should try and read it.

---

### Post by ahtasham82 on 2009-08-17
I am trying to connect via one of the ubuntu user....here are the vsftpd.conf contents....


```
# Example config file /etc/vsftpd.conf
#
# The default compiled in settings are fairly paranoid. This sample file
# loosens things up a bit, to make the ftp daemon more usable.
# Please see vsftpd.conf.5 for all compiled in defaults.
#
# READ THIS: This example file is NOT an exhaustive list of vsftpd options.
# Please read the vsftpd.conf.5 manual page to get a full idea of vsftpd's
# capabilities.
#
#
# Run standalone?  vsftpd can run either from an inetd or as a standalone
# daemon started from an initscript.
listen=YES
#
# Run standalone with IPv6?
# Like the listen parameter, except vsftpd will listen on an IPv6 socket
# instead of an IPv4 one. This parameter and the listen parameter are mutually
# exclusive.
#listen_ipv6=YES
#
# Allow anonymous FTP? (Beware - allowed by default if you comment this out).
anonymous_enable=NO
#
# Uncomment this to allow local users to log in.
local_enable=YES
#
# Uncomment this to enable any form of FTP write command.
write_enable=YES
#
# Default umask for local users is 077. You may wish to change this to 022,
# if your users expect that (022 is used by most other ftpd's)
#local_umask=022
#
# Uncomment this to allow the anonymous FTP user to upload files. This only
# has an effect if the above global write enable is activated. Also, you will
# obviously need to create a directory writable by the FTP user.
#anon_upload_enable=YES
#
# Uncomment this if you want the anonymous FTP user to be able to create
# new directories.
#anon_mkdir_write_enable=YES
#
# Activate directory messages - messages given to remote users when they
# go into a certain directory.
dirmessage_enable=YES
#
# Activate logging of uploads/downloads.
xferlog_enable=YES
#
# Make sure PORT transfer connections originate from port 20 (ftp-data).
connect_from_port_20=YES
#
# If you want, you can arrange for uploaded anonymous files to be owned by
# a different user. Note! Using "root" for uploaded files is not
# recommended!
#chown_uploads=YES
#chown_username=whoever
#
# You may override where the log file goes if you like. The default is shown
# below.
#xferlog_file=/var/log/vsftpd.log
#
# If you want, you can have your log file in standard ftpd xferlog format
#xferlog_std_format=YES
#
# You may change the default value for timing out an idle session.
#idle_session_timeout=600
#
# You may change the default value for timing out a data connection.
#data_connection_timeout=120
#
# It is recommended that you define on your system a unique user which the
# ftp server can use as a totally isolated and unprivileged user.
#nopriv_user=ftpsecure
#
# Enable this and the server will recognise asynchronous ABOR requests. Not
# recommended for security (the code is non-trivial). Not enabling it,
# however, may confuse older FTP clients.
#async_abor_enable=YES
#
# By default the server will pretend to allow ASCII mode but in fact ignore
# the request. Turn on the below options to have the server actually do ASCII
# mangling on files when in ASCII mode.
# Beware that on some FTP servers, ASCII support allows a denial of service
# attack (DoS) via the command "SIZE /big/file" in ASCII mode. vsftpd
# predicted this attack and has always been safe, reporting the size of the
# raw file.
# ASCII mangling is a horrible feature of the protocol.
#ascii_upload_enable=YES
#ascii_download_enable=YES
#
# You may fully customise the login banner string:
#ftpd_banner=Welcome to blah FTP service.
#
# You may specify a file of disallowed anonymous e-mail addresses. Apparently
# useful for combatting certain DoS attacks.
#deny_email_enable=YES
# (default follows)
#banned_email_file=/etc/vsftpd.banned_emails
#
# You may restrict local users to their home directories.  See the FAQ for
# the possible risks in this before using chroot_local_user or
# chroot_list_enable below.
#chroot_local_user=YES
#
# You may specify an explicit list of local users to chroot() to their home
# directory. If chroot_local_user is YES, then this list becomes a list of
# users to NOT chroot().
#chroot_list_enable=YES
# (default follows)
#chroot_list_file=/etc/vsftpd.chroot_list
#
# You may activate the "-R" option to the builtin ls. This is disabled by
# default to avoid remote users being able to cause excessive I/O on large
# sites. However, some broken FTP clients such as "ncftp" and "mirror" assume
# the presence of the "-R" option, so there is a strong case for enabling it.
#ls_recurse_enable=YES
#
#
# Debian customization
#
# Some of vsftpd's settings don't fit the Debian filesystem layout by
# default.  These settings are more Debian-friendly.
#
# This option should be the name of a directory which is empty.  Also, the
# directory should not be writable by the ftp user. This directory is used
# as a secure chroot() jail at times vsftpd does not require filesystem
# access.
secure_chroot_dir=/var/run/vsftpd
#
# This string is the name of the PAM service vsftpd will use.
pam_service_name=vsftpd
#
# This option specifies the location of the RSA certificate to use for SSL
# encrypted connections.
rsa_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
# This option specifies the location of the RSA key to use for SSL
# encrypted connections.
rsa_private_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
```

---

### Post by Bachstelze on 2009-08-17
No problem here. You have restarted vsftpd, right?

---

### Post by ahtasham82 on 2009-08-17
How can I link the installed ftp server to live domain of mine....I just discovered that I have a different IP for the OS...and a different IP for the my domain that is mapped to that server....

I got the IP of the OS by the ifconfig command....and IP of the domain by pinging the domain....

I usually do the updating of the website but I need to setup FTP Server because client of my client need to push a data onto our server....

please let me know...thanks again....

---

### Post by memyself on 2009-08-17
Hy

I did it like this:

 _FTP Server_

How to install FTP Server for File Transfer service


sudo apt-get install proftpd


How to configure FTP user to be "jailed" (chrooted) into their home directory

 

sudo cp /etc/proftpd/proftpd.conf /etc/proftpd/proftpd.conf_backup
gksudo gedit /etc/proftpd/proftpd.conf

    * Find this section 

...
DenyFilter           \*.*/
...

    * Add the following line below it 

DefaultRoot           ~


    * Save the edited file 

sudo /etc/init.d/proftpd restart


How to configure FTP Server to allow anonymous FTP user to read only



sudo cp /etc/proftpd/proftpd.conf /etc/proftpd/proftpd.conf_backup
gksudo gedit /etc/proftpd/proftpd.conf

    * Append the following lines at the end of file 

<Anonymous ~ftp>
 User            ftp
 Group            nogroup
 UserAlias          anonymous ftp
 DirFakeUser on ftp
 DirFakeGroup on ftp
 RequireValidShell      off
 MaxClients         10
 DisplayLogin        welcome.msg
 DisplayFirstChdir      .message
 <Directory *>
  <Limit WRITE>
   DenyAll
  </Limit>
 </Directory>
</Anonymous>

    * Save the edited file 

sudo /etc/init.d/proftpd restart


How to configure FTP Server to allow anonymous FTP user to read/write

 

sudo cp /etc/proftpd/proftpd.conf /etc/proftpd/proftpd.conf_backup
gksudo gedit /etc/proftpd/proftpd.conf

    * Append the following lines at the end of file 

<Anonymous ~ftp>
 User            ftp
 Group            nogroup
 UserAlias          anonymous ftp
 DirFakeUser on ftp
 DirFakeGroup on ftp
 RequireValidShell      off
 MaxClients         10
 DisplayLogin        welcome.msg
 DisplayFirstChdir      .message
</Anonymous>

    * Save the edited file 

sudo /etc/init.d/proftpd restart


How to map anonymous FTP user to folders outside /home/ftp/

    * Read #General Notes
    * Read #How to install FTP Server for File Transfer service 

sudo cp /etc/proftpd/proftpd.conf /etc/proftpd/proftpd.conf_backup
gksudo gedit /etc/proftpd/proftpd.conf

    * Append the following lines at the end of file 

<Anonymous /location_of_folder/>
 User            ftp
 Group            nogroup
 UserAlias          anonymous ftp
 DirFakeUser on ftp
 DirFakeGroup on ftp
 RequireValidShell      off
 MaxClients         10
 DisplayLogin        welcome.msg
 DisplayFirstChdir      .message
 <Directory *>
  <Limit WRITE>
   DenyAll
  </Limit>
 </Directory>
</Anonymous>

    * Save the edited file 

sudo /etc/init.d/proftpd restart


How to change the default port number for FTP Server

     

    e.g. Assumed that new port number is 77 

sudo cp /etc/proftpd/proftpd.conf /etc/proftpd/proftpd.conf_backup
gksudo gedit /etc/proftpd/proftpd.conf

    * Find this line 

Port              21

    * Replace with the following line 

Port              77

    * Save the edited file 

sudo /etc/init.d/proftpd restart


++++++++++++++++++++++++++

This works fine for me on my "home"-server.

Maybe this helps a little step foward...

greets....

---

### Post by ahtasham82 on 2009-08-17
yes i did stoped and again started...I can do it again if you want... :D

root@UBS804FRH:/home/firstrelease# /etc/init.d/vsftpd restart
 * Stopping FTP server: vsftpd                                                  No /usr/sbin/vsftpd found running; none killed.
                                                                         [ OK ]
 * Starting FTP server: vsftpd                                           [ OK ]
root@UBS804FRH:/home/firstrelease#

---

### Post by ahtasham82 on 2009-08-17
so do you want me to install proftpd now....can we do this on vsftpd or do you really want me to uninstall vsftpd and install proftpd.... :)

---

### Post by MeumFidet on 2009-08-17
> **ahtasham82 said:**
> yes i did stoped and again started...I can do it again if you want... :D

root@UBS804FRH:/home/firstrelease# /etc/init.d/vsftpd restart
 * Stopping FTP server: vsftpd                                                  No /usr/sbin/vsftpd found running; none killed.
                                                                         [ OK ]
 * Starting FTP server: vsftpd                                           [ OK ]
root@UBS804FRH:/home/firstrelease#


Hi ahtasham,

What ftp client are you using and what error do you get when you try to log in?

MF

---

### Post by ahtasham82 on 2009-08-17
okay...no I have uninstalled vsftpd....and installed proftpd....

okay now how can I connect to this ftp server....

I also added the following line...
DefaultRoot           ~

Also I dont want anonymous user access....so I only added the above line....so what now....

I am using filezilla as a ftp client...and am getting the following error...

Status:    Resolving address of firstreleasehomes.com
Status:    Connecting to 216.218.175.11:21...
Error:    Connection timed out
Error:    Could not connect to server
Status:    Waiting to retry...
Status:    Resolving address of firstreleasehomes.com
Status:    Connecting to 216.218.175.11:21...

Thanks,
Ahtasham

---

### Post by ahtasham82 on 2009-08-17
hey...what is this section for....

# In some cases you have to specify passive ports range to by-pass
# firewall limitations. Ephemeral ports can be used for that, but
# feel free to use a more narrow range.
# PassivePorts                  49152 65534

# If your host was NATted, this option is useful in order to
# allow passive tranfers to work. You have to use your public
# address and opening the passive ports used on your firewall as well.
# MasqueradeAddress        1.2.3.4

I think I will need this to edit....Because My server IP is different to the domain IP....

any Idea ???

let me know....

Ahtasham

---

### Post by snteran on 2009-09-18
Were you guys able to fix your ftp server.  I have installed PROftpd and have ran into some issues myself.

```
ServerType standalone
DefaultServer on
Umask 022
ServerName "192.168.110.15"
ServerIdent on "CB_FTP"
ServerAdmin support@ftpserver.com
IdentLookups off
UseReverseDNS off
Port 1980
PassivePorts 49152 65534
MasqueradeAddress 77.6.46.20
TimesGMT off
MaxInstances 30
MaxLoginAttempts 3
TimeoutLogin 300
TimeoutNoTransfer 120
TimeoutIdle 120
DisplayLogin welcome.msg
DisplayChdir .message
User nobody
Group nobody
DirFakeUser off nobody
DirFakeGroup off nobody
DefaultTransferMode binary
AllowForeignAddress off
AllowRetrieveRestart on
AllowStoreRestart on
DeleteAbortedStores off
TransferRate RETR 220
TransferRate STOR 250
TransferRate STOU 250
TransferRate APPE 250
SystemLog /var/log/secure
RequireValidShell off
<IfModule mod_tls.c>
TLSEngine off
TLSRequired off
TLSVerifyClient off
TLSProtocol SSLv23
TLSLog /var/log/proftpd_tls.log
TLSRSACertificateFile /etc/gadmin-proftpd/certs/cert.pem
TLSRSACertificateKeyFile /etc/gadmin-proftpd/certs/key.pem
TLSCACertificateFile /etc/gadmin-proftpd/certs/cacert.pem
TLSRenegotiate required off
</IfModule>
<IfModule mod_ratio.c>
Ratios off
SaveRatios off
RatioFile "/restricted/proftpd_ratios"
RatioTempFile "/restricted/proftpd_ratios_temp"
CwdRatioMsg "Please upload first!"
FileRatioErrMsg "FileRatio limit exceeded, upload something first..."
ByteRatioErrMsg "ByteRatio limit exceeded, upload something first..."
LeechRatioMsg "Your ratio is unlimited."
</IfModule>
<Limit LOGIN>
  AllowUser cb_ftp0
  AllowUser cb_ftp1
  DenyALL
</Limit>

<Anonymous /home/FTP-shared>
User cb_ftp0
Group CB
AnonRequirePassword on
MaxClients 5 "The server is full, hosting %m users"
DisplayLogin welcome.msg
<Limit LOGIN>
Allow from all
Deny from all
</Limit>
AllowOverwrite on
<Limit LIST NLST  STOR STOU  APPE  RETR  RNFR RNTO  DELE  MKD XMKD SITE_MKDIR  RMD XRMD SITE_RMDIR  SITE  SITE_CHMOD  SITE_CHGRP  MTDM  PWD XPWD  SIZE  STAT  CWD XCWD  CDUP XCUP >
 AllowAll
</Limit>
<Limit NOTHING >
 DenyAll
</Limit>
</Anonymous>

<Anonymous /home/FTP-shared>
User cb_ftp1
Group CB
AnonRequirePassword on
MaxClients 5 "The server is full, hosting %m users"
DisplayLogin welcome.msg
<Limit LOGIN>
Allow from all
Deny from all
</Limit>
<Limit LIST NLST  STOR STOU  RETR  PWD XPWD  SIZE  STAT  CWD XCWD  CDUP XCUP >
 AllowAll
</Limit>
<Limit APPE  RNFR RNTO  DELE  MKD XMKD SITE_MKDIR  RMD XRMD SITE_RMDIR  SITE  SITE_CHMOD  SITE_CHGRP  MTDM >
 DenyAll
</Limit>
</Anonymous>
```

I seem to be able to ftp fine within the network but not from outside the network.  It's not a firewall issue, I have added the needed access-list and static forwards.  I think it has to do something with the Certs I tried to install or just the configuration of the server.  I would be happy removing the certs if I knew how.

Please let me know what other information is needed to help resolve.

Thanks,

---

### Post by snteran on 2009-09-21
Does anyone have any suggestions on the reasons that I might not be able to access the ftp site from without side the domain?

Thanks

---

