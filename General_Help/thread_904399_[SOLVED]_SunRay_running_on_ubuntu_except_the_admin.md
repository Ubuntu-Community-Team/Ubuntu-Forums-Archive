---
title: "[SOLVED] SunRay running on ubuntu except the administrative web pages :("
date: 2008-08-29
forum: General Help
---

### Post by VolvoPunch on 2008-08-29
I have installed SunRay Administrative software on my ubutnu server but I am unable to get the web services (port 1660) running. I am bit lost and could use some guidance. Thanks

```
root@test-corp-esx-03:/opt/SUNWut/sbin# 
ls
 
utadm        utcapture  utcrypto   
utdssync  utfwsync    utinstall        utlicenseadm  utpolicy    utquery    
utresadm   utsession  utwall
 
utadminuser  utcard     utdesktop  
utfwadm   utgroupsig  utkiosk          utmhadm       utpreserve  utreader   
utresdef   utusbadm
 
utamghadm    utconfig   utdevadm   
utfwload  utgstatus   utkioskoverride  utmhconfig    utpw        utreplica  
utrestart  utuser
 
root@test-corp-esx-03:/opt/SUNWut/sbin# 
netstat -napt
 
Active Internet connections (servers 
and established)
 
Proto Recv-Q Send-Q Local 
Address           Foreign Address         State       PID/Program 
name
 
tcp        0      0 
0.0.0.0:7008            0.0.0.0:*               LISTEN      
4647/inetd
 
tcp        0      0 
0.0.0.0:7011            0.0.0.0:*               LISTEN      
5482/utdevmgrd
 
tcp        0      0 
0.0.0.0:7012            0.0.0.0:*               LISTEN      
25185/utdsd
 
tcp        0      0 
0.0.0.0:389             0.0.0.0:*               LISTEN      
29836/slapd
 
tcp        0      0 
127.0.0.1:3306          0.0.0.0:*               LISTEN      
4513/mysqld
 
tcp        0      0 
0.0.0.0:80              0.0.0.0:*               LISTEN      
13790/apache2
 
tcp        0      0 
127.0.0.1:631           0.0.0.0:*               LISTEN      
4612/cupsd
 
tcp        0      0 
0.0.0.0:7007            0.0.0.0:*               LISTEN      
5451/utsessiond
 
tcp6       0      0 
:::389                  :::*                    LISTEN      
29836/slapd
 
tcp6       0      0 
127.0.0.1:8005          :::*                    LISTEN      
5498/java
 
tcp6       0      0 
:::8009                 :::*                    LISTEN      
4887/jsvc
 
tcp6       0      0 
:::8010                 :::*                    LISTEN      
5498/java
 
tcp6       0      0 
:::8080                 :::*                    LISTEN      
5498/java
 
tcp6       0      0 
:::8180                 :::*                    LISTEN      
4887/jsvc
 
tcp6       0      0 
:::22                   :::*                    LISTEN      
12699/sshd
 
tcp6       0    148 
10.3.225.56:22          10.3.226.45:2805        ESTABLISHED 
19454/0
 
root@test-corp-esx-03:/opt/SUNWut/sbin# 
./utconfig
 
 
 
Configuration of Sun Ray Core 
Services Software
 
 
 
This script automates the 
configuration of the Sun Ray Core Services
 
software and related software 
products.  Before proceeding, you should
 
have read the Sun Ray Core Services 
4.0 Installation Guide and filled out
 
the Configuration Worksheet.  This 
script will prompt you for the values
 
you filled out on the Worksheet.  
For your convenience, default values
 
(where applicable) are shown in 
brackets.
 
 
 
WARNING: SunRay Datastore is 
enabled. This script may clobber the current 
configuration.
 
 
 
 
 
Continue (y/[n])? 
y
 
 
 
Configure Sun Ray Web 
Administration? ([y]/n)? y
 
Enter Apache Tomcat installation 
directory [/usr/local/tomcat]:
 
Enter HTTP port number 
[1660]:
 
Enable secure connections? ([y]/n)? 
n
 
Enter Tomcat process username 
[utwww]:
 
Enable remote server administration? 
(y/[n])? y
 
 
 
Previous Sun Ray Kiosk Mode 
configuration:
 
Current kiosk user account 
settings:
 
  user name prefix:   
utku
 
  first account uid:  
150000
 
  number of accounts: 
25
 
  kiosk group name:   
utkiosk
 
  kiosk group gid:    
auto
 
Do you wish to preserve this 
configuration? ([y]/n)? y
 
 
 
Configure this server for a failover 
group? (y/[n])? n
 
 
 
About to configure the following 
software products:
 
 
 
Sun Ray Data Store 
3.0
 
    Hostname: 
test-corp-esx-03
 
    Sun Ray root entry: 
o=utdata
 
    Sun Ray root name: 
utdata
 
    Sun Ray utdata admin password: 
(not shown)
 
    SRDS 'rootdn': 
cn=admin,o=utdata
 
 
 
Sun Ray Web 
Administration
 
    Apache Tomcat installation 
directory: /usr/local/tomcat
 
    HTTP port number: 
1660
 
    HTTPS port: 
Disabled
 
    Tomcat process username: 
utwww
 
    Remote server administration: 
Enabled
 
 
 
Sun Ray Core Services 
4.0
 
    Failover group: 
no
 
    Sun Ray Kiosk Mode: 
yes
 
 
 
Continue ([y]/n)? 
y
 
 
 
Creating Sun Ray Core Services 
Configuration ...
 
Sun Ray Web Administration enabled 
to start at system boot.
 
 
 
Saving /etc/opt/SUNWut/gmSignature 
to /etc/opt/SUNWut/gmSignature.bak
 
 
 
Unique "/etc/opt/SUNWut/gmSignature" 
has been generated.
 
 
 
Restarting Sun Ray Data Store 
...
 
Stopping Sun Ray Data Store 
daemon
 
Sun Ray Data Store daemon 
stopped
 
Starting Sun Ray Data Store daemon 
.
 
Wed Aug 27 13:08 : utdsd 
starting
 
Adding user admin 
...
 
Failed to add user(s) to the 
list
 
ERROR: Could not retrieve 
policy.
 
ERROR: Could not retrieve 
policy.
 
 
 
***********************************************************
 
The current policy has been 
modified.  You must restart the
 
authentication manager to activate 
the changes.
 
***********************************************************
 
 
 
 
 
Configuration of Sun Ray Core 
Services has completed.  Please check
 
the log file, 
/var/log/SUNWut/utconfig.2008_08_27_13:07:46.log, for 
errors.
 
root@test-corp-esx-03:/opt/SUNWut/sbin#

```

---

### Post by VolvoPunch on 2008-09-02
Bump? Does anyone have experience with running SunRay on Ubuntu? :(

---

### Post by VolvoPunch on 2008-09-03
Alright I figured out what was casing the problem. It was the location I had set for the Java Runtime Enviroment webadmin.conf file.



I was getting this error message
```

root@test-corp-esx-03:/opt/SUNWut/webadmin/conf# /opt/SUNWut/lib/utwebadmin start
No Java Runtime Environment (JRE) found at /usr/share/java.
root@test-corp-esx-03:/opt/SUNWut/webadmin/conf#
```

This is my print out of my now working the webadmin.conf file located at /opt/SUNWut/webadmin/conf
```

#
# ident "$Id$ SMI"
#
# Copyright 2007 Sun Microsystems, Inc.  All rights reserved.
# Use is subject to license terms.
#

# =============================================================================
# Configuration settings for the Sun Ray Administration GUI
#
# Configuration settings should be adapted via the utconfig -w command that
# automatically takes care of the necessary adaptations in this file. Any manual
# changes in this file will require a restart of the Admin GUI using the
# /opt/SUNWut/lib/utwebadmin restart command. The restart ensures that the
# Tomcat configuration files (server.xml and web.xml) are updated accordingly.
#
# =============================================================================

# =============================================================================
# General environment settings
# =============================================================================

# The location of the Java Runtime Environment (should be JRE 1.5 and above)
jre.home=/usr/lib/jvm/java-6-sun-1.6.0.06

# Any Java options (e.g. memory allocation) that should be applied
jre.options=

# The location of the Apache Tomcat binaries (should be Tomcat 5.5)
catalina.home=/usr/local/tomcat

# Any additional options that should be applied to Tomcat
catalina.options=

# The location of the log file for utwebadmin
log.file=/var/opt/SUNWut/log/utwebadmin.log

# The logging level (e.g. FINEST, FINER, FINE, CONFIG, INFO, WARNING, SEVERE)
log.level=SEVERE

# The automatic start of the tomcat daemon during system startup
# (default is true)
auto.start=true

# =============================================================================
# Tomcat Web server settings
# =============================================================================

# The Unix user account which will be used by Tomcat
process.username=utwww

# The Unix group name which will be used by Tomcat
process.groupname=utadmin

# The session timeout (specified in minutes)
session.timeout=30

# Secure HTTP port number (default is 1661)
https.port=0

# Unsecure HTTP port number (default is 1660)
http.port=1660

# Remote administration (default is 127.0.0.1 - localhost only),
# use ".*" to enable remote access from any host.
remote.access=.*

# Shutdown port (default is 50505), this setting will automatically be
# adapted, if the port is already occupied by another application
shutdown.port=50505
{code}

utwebadmin is running! See port 1660!
{code}root@test-corp-esx-03:/opt/SUNWut/webadmin/conf# netstat -napt
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:7008            0.0.0.0:*               LISTEN      4647/inetd
tcp        0      0 0.0.0.0:7011            0.0.0.0:*               LISTEN      5482/utdevmgrd
tcp        0      0 0.0.0.0:7012            0.0.0.0:*               LISTEN      19939/utdsd
tcp        0      0 0.0.0.0:389             0.0.0.0:*               LISTEN      29836/slapd
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN      4513/mysqld
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN      2786/apache2
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      4612/cupsd
tcp        0      0 0.0.0.0:7007            0.0.0.0:*               LISTEN      5451/utsessiond
tcp6       0      0 :::389                  :::*                    LISTEN      29836/slapd
tcp6       0      0 127.0.0.1:8005          :::*                    LISTEN      5498/java
tcp6       0      0 127.0.0.1:50505         :::*                    LISTEN      2653/java
tcp6       0      0 :::8009                 :::*                    LISTEN      4887/jsvc
tcp6       0      0 :::8010                 :::*                    LISTEN      5498/java
tcp6       0      0 :::8080                 :::*                    LISTEN      5498/java
tcp6       0      0 :::8180                 :::*                    LISTEN      4887/jsvc
tcp6       0      0 :::22                   :::*                    LISTEN      12699/sshd
tcp6       0      0 :::1660                 :::*                    LISTEN      2653/java
tcp6       0    740 10.3.225.56:22          10.3.226.45:1644        ESTABLISHED 2415/1
root@test-corp-esx-03:/opt/SUNWut/webadmin/conf#

```

---

### Post by cjawcrusher512 on 2008-09-09
[[size=2][color=#006699]How to buy a ball mill with quality at reasonable price in China  ?[/color][/size]](http://answers.yahoo.com/question/index?qid=20080826203448AAVEOrl)

---

### Post by mbj20 on 2008-10-15
o,well goodhould to go in the forum Good ServicesAbout all go to [wow gold](http://www.powerleveling-wowgold.com) Good Services ok!sites where they can express&#65281;[Auto Shock Absorber](http://www.shockabsorber-piston.org/)-The best shock absorber manufacturer[china escort](http://www.sh-escort.com/)-beautiful Chinese girls  are high class[massage in beijing](http://www.full-body-massage.cn/)-service for  massage in beijing[shanghai escort](http://www.escortinshanghai.com/)-China female agencies escort

---

