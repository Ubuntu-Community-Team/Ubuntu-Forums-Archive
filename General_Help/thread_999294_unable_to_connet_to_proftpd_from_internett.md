---
title: "unable to connet to proftpd from internett"
date: 2008-12-01
forum: General Help
---

### Post by cje on 2008-12-01
I need some help to access my ubuntu server via ftp from the internet.
I'm using proftpd.

First, I'm having two networks behind my ISP router; 
- my ubuntu server is on LAN 192.168.10.x
- my home network is on LAN 192.168.0.x

I do not have any problems to ftp connect from 192.168.0.x to 192.168.10.x 

Second, on my ISP router I've forwarded port 1070:1070 to 1070:1070 at my ubuntu server

This is my proftpd configuration file
ServerType standalone
DefaultServer on
Umask 022
ServerName "192.168.10.20"
ServerIdent on "test-server"
ServerAdmin [email]my@email.com[/email]
IdentLookups off
UseReverseDNS off
Port 1070
PassivePorts 49152 65534
#MasqueradeAddress None
TimesGMT off
MaxInstances 2
MaxLoginAttempts 3
TimeoutLogin 300
TimeoutNoTransfer 120
TimeoutIdle 120
DisplayLogin welcome.msg
User myID
Group www-data
DirFakeUser off nobody
DirFakeGroup off nobody
DefaultTransferMode binary
AllowForeignAddress off
AllowRetrieveRestart on
AllowStoreRestart on
DeleteAbortedStores off
TransferRate RETR 30
TransferRate STOR 40
TransferRate STOU 40
TransferRate APPE 40
SystemLog /var/log/secure
RequireValidShell off
#gp_random_username_length 6
#gp_random_password_length 6
#gp_randomize_case lower
#gp_useradd_homedir_path /var/ftp
#gp_html_path /var/www/html/ftp.htm
#gp_welcome_name welcome.msg
<IfModule mod_tls.c>
TLSEngine off
TLSRequired off
TLSVerifyClient off
TLSProtocol TLSv1
TLSLog /var/log/proftpd_tls.log
TLSRSACertificateFile /etc/gproftpd/gproftpd.pem
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
  AllowUser myID
  DenyALL
</Limit>

<Anonymous /var/www/>
User myID
Group www-data
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
# Lock all the users in home directory, ***** really important *****
DefaultRoot ~

-----------------------------------------
Thanks for any suggestions

---

### Post by cje on 2008-12-03
anyone who knows?

---

