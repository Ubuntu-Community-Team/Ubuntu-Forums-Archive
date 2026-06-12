---
title: "Proftpd and Samba &quot;connection refused!&quot;"
date: 2008-09-03
forum: General Help
---

### Post by jacensolo on 2008-09-03
On my server I am getting a "connection refused!" error on both samba and proftpd. What I am trying to do is set up a server that (when home) lets me use it as basically an external drive. I want to have each user have their own folder and that's it. I want to be able to access the user's file over the internet too, but I think I need to use ftp for that. This is much like what my school has setup, without being able to access it over the internet.

Even when I connect to localhost, I get connection refused. But I'm logged in through ssh from my laptop, so I don't think it's a firewall problem.

```
  GNU nano 2.0.6           File: /etc/samba/smb.conf                            
workgroup = stone
encrypt passwords = yes
security = user

[homes]
path = /home/%u
browseable = no
writable = yes


```

```
  GNU nano 2.0.6         File: /etc/proftpd/proftpd.conf                        

#
# /etc/proftpd/proftpd.conf -- This is a basic ProFTPD configuration file.
# To really apply changes reload proftpd after modifications.
#

# Includes DSO modules
Include /etc/proftpd/modules.conf

# Set off to disable IPv6 support which is annoying on IPv4 only boxes.
UseIPv6                         off

ServerName                      "coolS"
ServerType                      inetd
DeferWelcome                    off

MultilineRFC2228                on
DefaultServer                   on
ShowSymlinks                    on
TimeoutNoTransfer               600
TimeoutStalled                  600
TimeoutIdle                     1200

DisplayLogin                    welcome.msg
DisplayFirstChdir               .message
ListOptions                     "-l"

DenyFilter                      \*.*/
# Use this to jail all users in their homes
DefaultRoot                     ~

# Users require a valid shell listed in /etc/shells to login.
# Use this directive to release that constrain.
RequireValidShell               off

# Port 21 is the standard FTP port.
# In some cases you have to specify passive ports range to by-pass
# firewall limitations. Ephemeral ports can be used for that, but
# feel free to use a more narrow range.
# PassivePorts                  49152 65534

# If your host was NATted, this option is useful in order to
# allow passive tranfers to work. You have to use your public
# address and opening the passive ports used on your firewall as well.
MasqueradeAddress               1.2.3.4

# To prevent DoS attacks, set the maximum number of child processes
# to 30.  If you need to allow more than 30 concurrent connections
# at once, simply increase this value.  Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd)
MaxInstances                    30

# Set the user and group that the server normally runs at.
User                            killian
Group                           nogroup

# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask                           022  022
# Normally, we want files to be overwriteable.
AllowOverwrite                  on

# Uncomment this if you are using NIS or LDAP to retrieve passwords:
# PersistentPasswd              off

# Be warned: use of this directive impacts CPU average load!
# Uncomment this if you like to see progress and transfer rate with ftpwho
# in downloads. That is not needed for uploads rates.

# UseSendFile                   off

# Choose a SQL backend among MySQL or PostgreSQL.
# Both modules are loaded in default configuration, so you have to specify the $
# or comment out the unused module in /etc/proftpd/modules.conf.
# Use 'mysql' or 'postgres' as possible values.
#
#<IfModule mod_sql.c>
# SQLBackend                    mysql
#</IfModule>

TransferLog /var/log/proftpd/xferlog
SystemLog   /var/log/proftpd/proftpd.log

<IfModule mod_tls.c>
TLSEngine off
</IfModule>

<IfModule mod_quota.c>
QuotaEngine on
</IfModule>

<IfModule mod_ratio.c>
Ratios on
</IfModule>


# Delay engine reduces impact of the so-called Timing Attack described in
# http://security.lss.hr/index.php?page=details&ID=LSS-2004-10-02
# It is on by default.
<IfModule mod_delay.c>
DelayEngine on
</IfModule>

<IfModule mod_ctrls.c>
ControlsEngine        on
ControlsMaxClients    2
ControlsLog           /var/log/proftpd/controls.log
ControlsInterval      5
ControlsSocket        /var/run/proftpd/proftpd.sock
</IfModule>

<IfModule mod_ctrls_admin.c>
AdminControlsEngine on
</IfModule>

```

Any ideas?

---

### Post by jacensolo on 2008-09-04
No one has an idea?

---

### Post by Peter09 on 2008-09-04
I guess you need to check how you are doing authentication. Are you using PAM?

---

### Post by jacensolo on 2008-09-04
> **Peter09 said:**
> I guess you need to check how you are doing authentication. Are you using PAM?

What is PAM?

---

### Post by Peter09 on 2008-09-04
In Samba and Proftp you have options as to how the user is authenticated. Proftp for instance gives you options to a special password file for proftp or PAM which authenticates against the servers password file.

Depending on how you want to use these applications will define how you wish to authenticate. 

Look in the config setups - it does get a bit complicated.

Note security = user means that you will need the same accounts on the local as the remote host (I think). There are several sample config files for samba in these forums, search for one and use it.

---

