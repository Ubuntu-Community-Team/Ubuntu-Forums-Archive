---
title: "Epson Printer does nothing"
date: 2005-09-02
forum: Hardware &amp; Laptops
---

### Post by Ikzann on 2005-09-02
I have an Epson Stylus Color 740.  I haven't installed any extra drivers or anything. I have selected the Gimp-Print driver. However, when I try to print something, Ubuntu says it is printing and then finishes but nothing happens with the Printer. It's connected via USB to my Mac.

---

### Post by Zeroedout on 2005-09-02
hi, i have the exact same printer, but connected to my debian box, though i do print from my ubuntu box over the network. First thing, make sure you are using cups and not another backend, then make sure you are using the stcolor driver, not gimp-print. That's what works for me, so hope this helps.

---

### Post by Ikzann on 2005-09-02
Setting it to stcolor doesn't do anything. How do I make sure I am using CUPS?

---

### Post by Zeroedout on 2005-09-02
go to synaptic, and look for cupsys, hit package and configure, make sure all the right backends are selected. I personally have alot of the foomatic packes installed cause i used to have another printer, but i can't be sure if they are relevent. Keep trying, and **** around with the settings, you'll get it. I think i also had to mess around with the cups config file quite a bit before i got it working (that was on debian though). I'm in a bit of a hurry now so when i get back home, i'll post my config file, if you still havn't got it working.

---

### Post by Ikzann on 2005-09-02
Thanks so much. I'm a Linux newbie, if you hadn't noticed already. Which backends should I choose? I know USB, but I do have the eventual goal of sharing the printer.

---

### Post by Zeroedout on 2005-09-04
okay, here is my cupsd.conf from /etc/cups:
#

# Server

# Server name (ServerName)
# 
# The hostname of your server, as advertised to the world.
# By default CUPS will use the hostname of the system.
# 
# To set the default server used by clients, see the client.conf file.
# 
# ex: myhost.domain.com
#
#ServerName myhost.domain.com


# Server administrator (ServerAdmin)
# 
# The email address to send all complaints or problems to.
# By default CUPS will use "root@hostname".
# 
# ex: [email]root@myhost.com[/email]
#
#ServerAdmin [email]root@your.domain.com[/email]


# Classification (Classification)
# 
# The classification level of the server.  If set, this
# classification is displayed on all pages, and raw printing is disabled.
# The default is the empty string.
# 
# ex: confidential
#
#Classification classified

Classification none

# Allow overrides (ClassifyOverride)
# 
# Whether to allow users to override the classification
# on printouts. If enabled, users can limit banner pages to before or
# after the job, and can change the classification of a job, but cannot
# completely eliminate the classification or banners.
# 
# The default is off.
#
#ClassifyOverride off


# Default character set (DefaultCharset)
# 
# The default character set to use. If not specified,
# defaults to utf-8.  Note that this can also be overridden in
# HTML documents...
# 
# ex: utf-8
#
#DefaultCharset utf-8

DefaultCharset UTF-8

# Default language (DefaultLanguage)
# 
# The default language if not specified by the browser.
# If not specified, the current locale is used.
# 
# ex: en
#
#DefaultLanguage en

DefaultLanguage en

# Printcap file (Printcap)
# 
# The name of the printcap file.  Default is no filename.
# Leave blank to disable printcap file generation.
# 
# ex: /etc/printcap
#
#Printcap /etc/printcap

Printcap /var/run/cups/printcap


PrintcapFormat BSD

# Security

# Remote root user (RemoteRoot)
# 
# The name of the user assigned to unauthenticated accesses
# from remote systems.  By default "remroot".
# 
# ex: remroot
#
#RemoteRoot remroot

RemoteRoot remroot

# System group (SystemGroup)
# 
# The group name for "System" (printer administration)
# access.  The default varies depending on the operating system, but
# will be sys, system, or root (checked for in that order).
# 
# ex: lpadmin
#
#SystemGroup lpadmin

SystemGroup lpadmin

# Encryption certificate (ServerCertificate)
# 
# The file to read containing the server's certificate.
# Defaults to "/etc/cups/ssl/server.crt".
# 
# ex: /etc/cups/ssl/server.crt
#
#ServerCertificate /etc/cups/ssl/server.crt

ServerCertificate /etc/cups/ssl/server.crt

# Encryption key (ServerKey)
# 
# The file to read containing the server's key.
# Defaults to "/etc/cups/ssl/server.key".
# 
# ex: /etc/cups/ssl/server.key
#
#ServerKey /etc/cups/ssl/server.key

ServerKey /etc/cups/ssl/server.key

# Access permissions
#
# Access permissions for each directory served by the scheduler.
# Locations are relative to DocumentRoot...
#
# AuthType: the authorization to use:
#
#    None   - Perform no authentication
#    Basic  - Perform authentication using the HTTP Basic method.
#    Digest - Perform authentication using the HTTP Digest method.
#
#    (Note: local certificate authentication can be substituted by
#           the client for Basic or Digest when connecting to the
#           localhost interface)
#
# AuthClass: the authorization class; currently only Anonymous, User,
# System (valid user belonging to group SystemGroup), and Group
# (valid user belonging to the specified group) are supported.
#
# AuthGroupName: the group name for "Group" authorization.
#
# Order: the order of Allow/Deny processing.
#
# Allow: allows access from the specified hostname, domain, IP address, or
# network.
#
# Deny: denies access from the specified hostname, domain, IP address, or
# network.
#
# Both "Allow" and "Deny" accept the following notations for addresses:
#
#     All
#     None
#     *.domain.com
#     .domain.com
#     host.domain.com
#     nnn.*
#     nnn.nnn.*
#     nnn.nnn.nnn.*
#     nnn.nnn.nnn.nnn
#     nnn.nnn.nnn.nnn/mm
#     nnn.nnn.nnn.nnn/mmm.mmm.mmm.mmm
#
# The host and domain address require that you enable hostname lookups
# with "HostNameLookups On" above.
#
# Encryption: whether or not to use encryption; this depends on having
# the OpenSSL library linked into the CUPS library and scheduler.
#
# Possible values:
#
#     Always       - Always use encryption (SSL)
#     Never        - Never use encryption
#     Required     - Use TLS encryption upgrade
#     IfRequested  - Use encryption if the server requests it
#
# The default value is "IfRequested".
#
#<Location [resource_name]>
#
# You may wish to limit access to printers and classes, either with Allow
# and Deny lines, or by requiring a username and password.
#
#
## Anonymous access (default)
#AuthType None
#
## Require a username and password (Basic authentication)
#AuthType Basic
#AuthClass User
#
## Require a username and password (Digest/MD5 authentication)
#AuthType Digest
#AuthClass User
#
## Restrict access to local domain
#Order Deny,Allow
#Deny From All
#Allow From .mydomain.com
#
## Use encryption if requested
#Encryption IfRequested
#</Location>

<Location />
Encryption IfRequested
Satisfy All
Order deny,allow
Deny From All
Allow From 127.0.0.1
Allow From 192.168.0.*
</Location>
<Location /jobs>
AuthType Basic
AuthClass User
Encryption IfRequested
Satisfy All
Order allow,deny
</Location>
<Location /admin>
AuthType Basic
AuthClass System
Encryption IfRequested
Satisfy All
Order deny,allow
Deny From All
Allow From 127.0.0.1
Allow From 192.168.0.*
</Location>

# Network

# Hostname lookups (HostNameLookups)
# 
# Whether or not to do lookups on IP addresses to get a
# fully-qualified hostname.  This defaults to Off for performance reasons...
# 
# ex: On
#
#HostNameLookups On

HostnameLookups On

# Keep alive (KeepAlive)
# 
# Whether or not to support the Keep-Alive connection
# option.  Default is on.
# 
# ex: On
#
#KeepAlive On

KeepAlive On

# Keep-alive timeout (KeepAliveTimeout)
# 
# The timeout (in seconds) before Keep-Alive connections are
# automatically closed.  Default is 60 seconds.
# 
# ex: 60
#
#KeepAliveTimeout 60

KeepAliveTimeout 60

# Max clients (MaxClients)
# 
# Controls the maximum number of simultaneous clients that
# will be handled.  Defaults to 100.
# 
# ex: 100
#
#MaxClients 100

MaxClients 100

# Max request size (MaxRequestSize)
# 
# Controls the maximum size of HTTP requests and print files.
# Set to 0 to disable this feature (defaults to 0).
# 
# ex: 0
#
#MaxRequestSize 0

MaxRequestSize 0m

# Client timeout (Timeout)
# 
# The timeout (in seconds) before requests time out.  Default is 300 seconds.
# 
# ex: 300
#
#Timeout 300

Timeout 300

# Listen to (Port/Listen)
# 
# Ports/addresses that are listened to.  The default port 631 is reserved
# for the Internet Printing Protocol (IPP) and is what is used here.
# 
# You can have multiple Port/Listen lines to listen to more than one
# port or address, or to restrict access.
# 
# Note: Unfortunately, most web browsers don't support TLS or HTTP Upgrades
# for encryption.  If you want to support web-based encryption you will
# probably need to listen on port 443 (the "HTTPS" port...).
# 
# ex: 631, myhost:80, 1.2.3.4:631
#
#    Port 80
#    Port 631
#    Listen hostname
#    Listen hostname:80
#    Listen hostname:631
#    Listen 1.2.3.4
#    Listen 1.2.3.4:631
#
#Port 631

Listen *:631

# Log

# Access log (AccessLog)
# 
# The access log file; if this does not start with a leading /
# then it is assumed to be relative to ServerRoot.  By default set to
# "/var/log/cups/access_log".
# 
# You can also use the special name syslog to send the output to the
# syslog file or daemon.
# 
# ex: /var/log/cups/access_log
#
#AccessLog /var/log/cups/access_log

AccessLog /var/log/cups/access_log

# Error log (ErrorLog)
# 
# The error log file; if this does not start with a leading /
# then it is assumed to be relative to ServerRoot.  By default set to
# "/var/log/cups/error_log".
# 
# You can also use the special name syslog to send the output to the
# syslog file or daemon.
# 
# ex: /var/log/cups/error_log
#
#ErrorLog /var/log/cups/error_log

ErrorLog /var/log/cups/error_log

# Page log (PageLog)
# 
# The page log file; if this does not start with a leading /
# then it is assumed to be relative to ServerRoot.  By default set to
# "/var/log/cups/page_log".
# 
# You can also use the special name syslog to send the output to the
# syslog file or daemon.
# 
# ex: /var/log/cups/page_log
#
#PageLog /var/log/cups/page_log

PageLog /var/log/cups/page_log

# Max log size (MaxLogSize)
# 
# Controls the maximum size of each log file before they are
# rotated.  Defaults to 1048576 (1MB).  Set to 0 to disable log rotating.
# 
# ex: 1048576
#
#MaxLogSize 0

MaxLogSize 1m

# Log level (LogLevel)
# 
# Controls the number of messages logged to the ErrorLog
# file and can be one of the following:
# 
#     debug2:     Log everything.
#     debug:     Log almost everything.
#     info:      Log all requests and state changes.
#     warn:      Log errors and warnings.
#     error:     Log only errors.
#     none:      Log nothing.
# 
# ex: info
#
#LogLevel info

LogLevel info

# Jobs

# Preserve job history (PreserveJobHistory)
# 
# Whether or not to preserve the job history after a
# job is completed, canceled, or stopped.  Default is Yes.
# 
# ex: Yes
#
#PreserveJobHistory Yes

PreserveJobHistory On

# Preserve job files (PreserveJobFiles)
# 
# Whether or not to preserve the job files after a
# job is completed, canceled, or stopped.  Default is No.
# 
# ex: No
#
#PreserveJobFiles No

PreserveJobFiles Off

# Auto purge jobs (AutoPurgeJobs)
# 
# Automatically purge jobs when not needed for quotas.
# Default is No.
#
#AutoPurgeJobs No

AutoPurgeJobs No

# Max jobs (MaxJobs)
# 
# Maximum number of jobs to keep in memory (active and completed).
# Default is 0 (no limit).
#
#MaxJobs 0

MaxJobs 0

# Max jobs per printer (MaxJobsPerPrinter)
# 
# The MaxJobsPerPrinter directive controls the maximum number of active
# jobs that are allowed for each printer or class. Once a printer or class
# reaches the limit, new jobs will be rejected until one of the active jobs
# is completed, stopped, aborted, or canceled.
# 
# Setting the maximum to 0 disables this functionality.
# Default is 0 (no limit).
# 
#
#MaxJobsPerPrinter 0

MaxJobsPerPrinter 0

# Max jobs per user (MaxJobsPerUser)
# 
# The MaxJobsPerUser directive controls the maximum number of active
# jobs that are allowed for each user. Once a user reaches the limit, new
# jobs will be rejected until one of the active jobs is completed, stopped,
# aborted, or canceled.
# 
# Setting the maximum to 0 disables this functionality.
# Default is 0 (no limit).
# 
#
#MaxJobsPerUser 0

MaxJobsPerUser 0

# Filter

# User (User)
# 
# The user the server runs under.  Normally this
# must be lp, however you can configure things for another user
# as needed.
# 
# Note: the server must be run initially as root to support the
# default IPP port of 631.  It changes users whenever an external
# program is run...
# 
# ex: lp
#
#User lp

User lp

# Group (Group)
# 
# The group the server runs under.  Normally this
# must be lpadmin, however you can configure things for another
# group as needed.
# 
# ex: lpadmin
#
#Group lpadmin

Group lpadmin

# RIP cache (RIPCache)
# 
# The amount of memory that each RIP should use to cache
# bitmaps.  The value can be any real number followed by "k" for
# kilobytes, "m" for megabytes, "g" for gigabytes, or "t" for tiles
# (1 tile = 256x256 pixels).  Defaults to "8m" (8 megabytes).
# 
# ex: 8m
#
#RIPCache 8m

RIPCache 8m

# Filter limit (FilterLimit)
# 
# Sets the maximum cost of all job filters that can be run
# at the same time.  A limit of 0 means no limit.  A typical job may need
# a filter limit of at least 200; limits less than the minimum required
# by a job force a single job to be printed at any time.
# 
# The default limit is 0 (unlimited).
# 
# ex: 200
#
#FilterLimit 0

FilterLimit 0

# Directories

# Data directory (DataDir)
# 
# The root directory for the CUPS data files.
# By default /usr/share/cups.
# 
# ex: /usr/share/cups
#
#DataDir /usr/share/cups

DataDir /usr/share/cups

# Document directory (DocumentRoot)
# 
# The root directory for HTTP documents that are served.
# By default the compiled-in directory.
# 
# ex: /usr/share/cups/doc-root
#
#DocumentRoot /usr/share/cups/doc-root

DocumentRoot /usr/share/cups/doc-root

# Font path (FontPath)
# 
# The path to locate all font files (currently only for pstoraster).
# By default /usr/share/cups/fonts.
# 
# ex: /usr/share/cups/fonts
#
#FontPath /usr/share/cups/fonts


# Request directory (RequestRoot)
# 
# The directory where request files are stored.
# By default /var/spool/cups.
# 
# ex: /var/spool/cups
#
#RequestRoot /var/spool/cups

RequestRoot /var/spool/cups

# Server binaries (ServerBin)
# 
# The root directory for the scheduler executables.
# By default /usr/lib/cups or /usr/lib32/cups (IRIX 6.5).
# 
# ex: /usr/lib/cups
#
#ServerBin /usr/lib/cups

ServerBin /usr/lib/cups

# Server files (ServerRoot)
# 
# The root directory for the scheduler.
# By default /etc/cups.
# 
# ex: /etc/cups
#
#ServerRoot /etc/cups

ServerRoot /etc/cups

# Temporary files (TempDir)
# 
# The directory to put temporary files in. This directory must be
# writable by the user defined above!  Defaults to "/var/spool/cups/tmp" or
# the value of the TMPDIR environment variable.
# 
# ex: /var/spool/cups/tmp
#
#TempDir /var/spool/cups/tmp

TempDir /var/spool/cups/tmp

# Browsing

# Use browsing (Browsing)
# 
# Whether or not to listen to printer 
# information from other CUPS servers.  
# 
# 
# Enabled by default.
# 
# 
# Note: to enable the sending of browsing
# information from this CUPS server to the LAN,
# specify a valid BrowseAddress.
# 
# 
# ex: On
#
#Browsing On

Browsing On

# Browse protocols (BrowseProtocols)
# 
# Which protocols to use for browsing.  Can be
# any of the following separated by whitespace and/or commas:
# 
#     all  - Use all supported protocols.
#     cups - Use the CUPS browse protocol.
#     slp  - Use the SLPv2 protocol.
# 
# The default is cups.
# 
# Note: If you choose to use SLPv2, it is strongly recommended that
#       you have at least one SLP Directory Agent (DA) on your
#       network.  Otherwise, browse updates can take several seconds,
#       during which the scheduler will not response to client
#       requests.
#
#BrowseProtocols cups

BrowseProtocols CUPS 

# Browse port (BrowsePort)
# 
# The port used for UDP broadcasts.  By default this is
# the IPP port; if you change this you need to do it on all servers.
# Only one BrowsePort is recognized.
# 
# ex: 631
#
#BrowsePort 631

BrowsePort 631

# Browse interval (BrowseInterval)
# 
# The time between browsing updates in seconds.  Default
# is 30 seconds.
# 
# Note that browsing information is sent whenever a printer's state changes
# as well, so this represents the maximum time between updates.
# 
# Set this to 0 to disable outgoing broadcasts so your local printers are
# not advertised but you can still see printers on other hosts.
# 
# ex: 30
#
#BrowseInterval 30

BrowseInterval 30

# Browse timeout (BrowseTimeout)
# 
# The timeout (in seconds) for network printers - if we don't
# get an update within this time the printer will be removed
# from the printer list.  This number definitely should not be
# less the BrowseInterval value for obvious reasons.  Defaults
# to 300 seconds.
# 
# ex: 300
#
#BrowseTimeout 300

BrowseTimeout 300

# Browse addresses (BrowseAddress)
# 
# Specifies a broadcast address to be used.  By
# default browsing information is broadcast to all active interfaces.
# 
# Note: HP-UX 10.20 and earlier do not properly handle broadcast unless
# you have a Class A, B, C, or D netmask (i.e. no CIDR support).
# 
# ex: x.y.z.255, x.y.255.255
#
#BrowseAddress x.y.z.255
#BrowseAddress x.y.255.255
#BrowseAddress x.255.255.255


# Browse order (BrowseOrder)
# 
# Specifies the order of BrowseAllow/BrowseDeny comparisons.
# 
# ex: allow,deny
#
#BrowseOrder allow,deny
#BrowseOrder deny,allow

BrowseOrder allow,deny

# Implicit classes (ImplicitClasses)
# 
# Whether or not to use implicit classes.
# 
# Printer classes can be specified explicitly in the classes.conf
# file, implicitly based upon the printers available on the LAN, or
# both.
# 
# When ImplicitClasses is On, printers on the LAN with the same name
# (e.g. Acme-LaserPrint-1000) will be put into a class with the same
# name. This allows you to setup multiple redundant queues on a LAN
# without a lot of administrative difficulties.  If a user sends a
# job to Acme-LaserPrint-1000, the job will go to the first available
# queue.
# 
# Enabled by default.
#
#ImplicitClasses Off

ImplicitClasses On

# Use &quot;any&quot; classes (ImplicitAnyClasses)
# 
# Whether or not to create AnyPrinter implicit
# classes.
# 
# When ImplicitAnyClasses is On and a local queue of the same name
# exists, e.g. "printer", "printer@server1", "printer@server1", then
# an implicit class called "Anyprinter" is created instead.
# 
# When ImplicitAnyClasses is Off, implicit classes are not created
# when there is a local queue of the same name.
# 
# Disabled by default.
#
#ImplicitAnyCLasses Off

ImplicitAnyClasses Off

# Hide implicit members (HideImplicitMembers)
# 
# Whether or not to show the members of an
# implicit class.
# 
# When HideImplicitMembers is On, any remote printers that are
# part of an implicit class are hidden from the user, who will
# then only see a single queue even though many queues will be
# supporting the implicit class.
# 
# Enabled by default.
#
#HideImplicitMembers On

HideImplicitMembers Yes

# Use short names (BrowseShortNames)
# 
# Whether or not to use "short" names for remote printers
# when possible (e.g. "printer" instead of "printer@host").  Enabled by
# default.
# 
# ex: Yes
#
#BrowseShortNames Yes

BrowseShortNames Yes

# Unknown




remember, this is from a Debian box so some things may be differnet, just compare it with your config file and replace what is different. Also this printer is behind my firewall, so it probebly is not configured in the most secure manner. 

Also here is my printers.conf

# Printer configuration file for CUPS v1.1.23
# Written by cupsd on Thu Aug 18 13:48:03 2005
<DefaultPrinter stylus_color_740>
Info EPSON Stylus COLOR 740
Location Parallel Printer #1
DeviceURI parallel:/dev/lp0
State Idle
Accepting Yes
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
</Printer>

also [www.freecolormangement.com/printer/](www.freecolormangement.com/printer/) may be of some use to you

---

### Post by Ikzann on 2005-09-04
> **Zeroedout]okay, here is my cupsd.conf from /etc/cups:
#

# Server

# Server name (ServerName)
# 
# The hostname of your server, as advertised to the world.
# By default CUPS will use the hostname of the system.
# 
# To set the default server used by clients, see the client.conf file.
# 
# ex: myhost.domain.com
#
#ServerName myhost.domain.com


# Server administrator (ServerAdmin)
# 
# The email address to send all complaints or problems to.
# By default CUPS will use "root@hostname".
# 
# ex: [email]root@myhost.com[/email]
#
#ServerAdmin [email]root@your.domain.com[/email]


# Classification (Classification)
# 
# The classification level of the server.  If set, this
# classification is displayed on all pages, and raw printing is disabled.
# The default is the empty string.
# 
# ex: confidential
#
#Classification classified

Classification none

# Allow overrides (ClassifyOverride)
# 
# Whether to allow users to override the classification
# on printouts. If enabled, users can limit banner pages to before or
# after the job, and can change the classification of a job, but cannot
# completely eliminate the classification or banners.
# 
# The default is off.
#
#ClassifyOverride off


# Default character set (DefaultCharset)
# 
# The default character set to use. If not specified,
# defaults to utf-8.  Note that this can also be overridden in
# HTML documents...
# 
# ex: utf-8
#
#DefaultCharset utf-8

DefaultCharset UTF-8

# Default language (DefaultLanguage)
# 
# The default language if not specified by the browser.
# If not specified, the current locale is used.
# 
# ex: en
#
#DefaultLanguage en

DefaultLanguage en

# Printcap file (Printcap)
# 
# The name of the printcap file.  Default is no filename.
# Leave blank to disable printcap file generation.
# 
# ex: /etc/printcap
#
#Printcap /etc/printcap

Printcap /var/run/cups/printcap


PrintcapFormat BSD

# Security

# Remote root user (RemoteRoot)
# 
# The name of the user assigned to unauthenticated accesses
# from remote systems.  By default "remroot".
# 
# ex: remroot
#
#RemoteRoot remroot

RemoteRoot remroot

# System group (SystemGroup)
# 
# The group name for "System" (printer administration)
# access.  The default varies depending on the operating system, but
# will be sys, system, or root (checked for in that order).
# 
# ex: lpadmin
#
#SystemGroup lpadmin

SystemGroup lpadmin

# Encryption certificate (ServerCertificate)
# 
# The file to read containing the server's certificate.
# Defaults to "/etc/cups/ssl/server.crt".
# 
# ex: /etc/cups/ssl/server.crt
#
#ServerCertificate /etc/cups/ssl/server.crt

ServerCertificate /etc/cups/ssl/server.crt

# Encryption key (ServerKey)
# 
# The file to read containing the server's key.
# Defaults to "/etc/cups/ssl/server.key".
# 
# ex: /etc/cups/ssl/server.key
#
#ServerKey /etc/cups/ssl/server.key

ServerKey /etc/cups/ssl/server.key

# Access permissions
#
# Access permissions for each directory served by the scheduler.
# Locations are relative to DocumentRoot...
#
# AuthType: the authorization to use:
#
#    None   - Perform no authentication
#    Basic  - Perform authentication using the HTTP Basic method.
#    Digest - Perform authentication using the HTTP Digest method.
#
#    (Note: local certificate authentication can be substituted by
#           the client for Basic or Digest when connecting to the
#           localhost interface)
#
# AuthClass: the authorization class said:**
> >
#
# You may wish to limit access to printers and classes, either with Allow
# and Deny lines, or by requiring a username and password.
#
#
## Anonymous access (default)
#AuthType None
#
## Require a username and password (Basic authentication)
#AuthType Basic
#AuthClass User
#
## Require a username and password (Digest/MD5 authentication)
#AuthType Digest
#AuthClass User
#
## Restrict access to local domain
#Order Deny,Allow
#Deny From All
#Allow From .mydomain.com
#
## Use encryption if requested
#Encryption IfRequested
#</Location>

<Location />
Encryption IfRequested
Satisfy All
Order deny,allow
Deny From All
Allow From 127.0.0.1
Allow From 192.168.0.*
</Location>
<Location /jobs>
AuthType Basic
AuthClass User
Encryption IfRequested
Satisfy All
Order allow,deny
</Location>
<Location /admin>
AuthType Basic
AuthClass System
Encryption IfRequested
Satisfy All
Order deny,allow
Deny From All
Allow From 127.0.0.1
Allow From 192.168.0.*
</Location>

# Network

# Hostname lookups (HostNameLookups)
# 
# Whether or not to do lookups on IP addresses to get a
# fully-qualified hostname.  This defaults to Off for performance reasons...
# 
# ex: On
#
#HostNameLookups On

HostnameLookups On

# Keep alive (KeepAlive)
# 
# Whether or not to support the Keep-Alive connection
# option.  Default is on.
# 
# ex: On
#
#KeepAlive On

KeepAlive On

# Keep-alive timeout (KeepAliveTimeout)
# 
# The timeout (in seconds) before Keep-Alive connections are
# automatically closed.  Default is 60 seconds.
# 
# ex: 60
#
#KeepAliveTimeout 60

KeepAliveTimeout 60

# Max clients (MaxClients)
# 
# Controls the maximum number of simultaneous clients that
# will be handled.  Defaults to 100.
# 
# ex: 100
#
#MaxClients 100

MaxClients 100

# Max request size (MaxRequestSize)
# 
# Controls the maximum size of HTTP requests and print files.
# Set to 0 to disable this feature (defaults to 0).
# 
# ex: 0
#
#MaxRequestSize 0

MaxRequestSize 0m

# Client timeout (Timeout)
# 
# The timeout (in seconds) before requests time out.  Default is 300 seconds.
# 
# ex: 300
#
#Timeout 300

Timeout 300

# Listen to (Port/Listen)
# 
# Ports/addresses that are listened to.  The default port 631 is reserved
# for the Internet Printing Protocol (IPP) and is what is used here.
# 
# You can have multiple Port/Listen lines to listen to more than one
# port or address, or to restrict access.
# 
# Note: Unfortunately, most web browsers don't support TLS or HTTP Upgrades
# for encryption.  If you want to support web-based encryption you will
# probably need to listen on port 443 (the "HTTPS" port...).
# 
# ex: 631, myhost:80, 1.2.3.4:631
#
#    Port 80
#    Port 631
#    Listen hostname
#    Listen hostname:80
#    Listen hostname:631
#    Listen 1.2.3.4
#    Listen 1.2.3.4:631
#
#Port 631

Listen *:631

# Log

# Access log (AccessLog)
# 
# The access log file; if this does not start with a leading /
# then it is assumed to be relative to ServerRoot.  By default set to
# "/var/log/cups/access_log".
# 
# You can also use the special name syslog to send the output to the
# syslog file or daemon.
# 
# ex: /var/log/cups/access_log
#
#AccessLog /var/log/cups/access_log

AccessLog /var/log/cups/access_log

# Error log (ErrorLog)
# 
# The error log file; if this does not start with a leading /
# then it is assumed to be relative to ServerRoot.  By default set to
# "/var/log/cups/error_log".
# 
# You can also use the special name syslog to send the output to the
# syslog file or daemon.
# 
# ex: /var/log/cups/error_log
#
#ErrorLog /var/log/cups/error_log

ErrorLog /var/log/cups/error_log

# Page log (PageLog)
# 
# The page log file; if this does not start with a leading /
# then it is assumed to be relative to ServerRoot.  By default set to
# "/var/log/cups/page_log".
# 
# You can also use the special name syslog to send the output to the
# syslog file or daemon.
# 
# ex: /var/log/cups/page_log
#
#PageLog /var/log/cups/page_log

PageLog /var/log/cups/page_log

# Max log size (MaxLogSize)
# 
# Controls the maximum size of each log file before they are
# rotated.  Defaults to 1048576 (1MB).  Set to 0 to disable log rotating.
# 
# ex: 1048576
#
#MaxLogSize 0

MaxLogSize 1m

# Log level (LogLevel)
# 
# Controls the number of messages logged to the ErrorLog
# file and can be one of the following:
# 
#     debug2:     Log everything.
#     debug:     Log almost everything.
#     info:      Log all requests and state changes.
#     warn:      Log errors and warnings.
#     error:     Log only errors.
#     none:      Log nothing.
# 
# ex: info
#
#LogLevel info

LogLevel info

# Jobs

# Preserve job history (PreserveJobHistory)
# 
# Whether or not to preserve the job history after a
# job is completed, canceled, or stopped.  Default is Yes.
# 
# ex: Yes
#
#PreserveJobHistory Yes

PreserveJobHistory On

# Preserve job files (PreserveJobFiles)
# 
# Whether or not to preserve the job files after a
# job is completed, canceled, or stopped.  Default is No.
# 
# ex: No
#
#PreserveJobFiles No

PreserveJobFiles Off

# Auto purge jobs (AutoPurgeJobs)
# 
# Automatically purge jobs when not needed for quotas.
# Default is No.
#
#AutoPurgeJobs No

AutoPurgeJobs No

# Max jobs (MaxJobs)
# 
# Maximum number of jobs to keep in memory (active and completed).
# Default is 0 (no limit).
#
#MaxJobs 0

MaxJobs 0

# Max jobs per printer (MaxJobsPerPrinter)
# 
# The MaxJobsPerPrinter directive controls the maximum number of active
# jobs that are allowed for each printer or class. Once a printer or class
# reaches the limit, new jobs will be rejected until one of the active jobs
# is completed, stopped, aborted, or canceled.
# 
# Setting the maximum to 0 disables this functionality.
# Default is 0 (no limit).
# 
#
#MaxJobsPerPrinter 0

MaxJobsPerPrinter 0

# Max jobs per user (MaxJobsPerUser)
# 
# The MaxJobsPerUser directive controls the maximum number of active
# jobs that are allowed for each user. Once a user reaches the limit, new
# jobs will be rejected until one of the active jobs is completed, stopped,
# aborted, or canceled.
# 
# Setting the maximum to 0 disables this functionality.
# Default is 0 (no limit).
# 
#
#MaxJobsPerUser 0

MaxJobsPerUser 0

# Filter

# User (User)
# 
# The user the server runs under.  Normally this
# must be lp, however you can configure things for another user
# as needed.
# 
# Note: the server must be run initially as root to support the
# default IPP port of 631.  It changes users whenever an external
# program is run...
# 
# ex: lp
#
#User lp

User lp

# Group (Group)
# 
# The group the server runs under.  Normally this
# must be lpadmin, however you can configure things for another
# group as needed.
# 
# ex: lpadmin
#
#Group lpadmin

Group lpadmin

# RIP cache (RIPCache)
# 
# The amount of memory that each RIP should use to cache
# bitmaps.  The value can be any real number followed by "k" for
# kilobytes, "m" for megabytes, "g" for gigabytes, or "t" for tiles
# (1 tile = 256x256 pixels).  Defaults to "8m" (8 megabytes).
# 
# ex: 8m
#
#RIPCache 8m

RIPCache 8m

# Filter limit (FilterLimit)
# 
# Sets the maximum cost of all job filters that can be run
# at the same time.  A limit of 0 means no limit.  A typical job may need
# a filter limit of at least 200; limits less than the minimum required
# by a job force a single job to be printed at any time.
# 
# The default limit is 0 (unlimited).
# 
# ex: 200
#
#FilterLimit 0

FilterLimit 0

# Directories

# Data directory (DataDir)
# 
# The root directory for the CUPS data files.
# By default /usr/share/cups.
# 
# ex: /usr/share/cups
#
#DataDir /usr/share/cups

DataDir /usr/share/cups

# Document directory (DocumentRoot)
# 
# The root directory for HTTP documents that are served.
# By default the compiled-in directory.
# 
# ex: /usr/share/cups/doc-root
#
#DocumentRoot /usr/share/cups/doc-root

DocumentRoot /usr/share/cups/doc-root

# Font path (FontPath)
# 
# The path to locate all font files (currently only for pstoraster).
# By default /usr/share/cups/fonts.
# 
# ex: /usr/share/cups/fonts
#
#FontPath /usr/share/cups/fonts


# Request directory (RequestRoot)
# 
# The directory where request files are stored.
# By default /var/spool/cups.
# 
# ex: /var/spool/cups
#
#RequestRoot /var/spool/cups

RequestRoot /var/spool/cups

# Server binaries (ServerBin)
# 
# The root directory for the scheduler executables.
# By default /usr/lib/cups or /usr/lib32/cups (IRIX 6.5).
# 
# ex: /usr/lib/cups
#
#ServerBin /usr/lib/cups

ServerBin /usr/lib/cups

# Server files (ServerRoot)
# 
# The root directory for the scheduler.
# By default /etc/cups.
# 
# ex: /etc/cups
#
#ServerRoot /etc/cups

ServerRoot /etc/cups

# Temporary files (TempDir)
# 
# The directory to put temporary files in. This directory must be
# writable by the user defined above!  Defaults to "/var/spool/cups/tmp" or
# the value of the TMPDIR environment variable.
# 
# ex: /var/spool/cups/tmp
#
#TempDir /var/spool/cups/tmp

TempDir /var/spool/cups/tmp

# Browsing

# Use browsing (Browsing)
# 
# Whether or not to listen to printer 
# information from other CUPS servers.  
# 
# 
# Enabled by default.
# 
# 
# Note: to enable the sending of browsing
# information from this CUPS server to the LAN,
# specify a valid BrowseAddress.
# 
# 
# ex: On
#
#Browsing On

Browsing On

# Browse protocols (BrowseProtocols)
# 
# Which protocols to use for browsing.  Can be
# any of the following separated by whitespace and/or commas:
# 
#     all  - Use all supported protocols.
#     cups - Use the CUPS browse protocol.
#     slp  - Use the SLPv2 protocol.
# 
# The default is cups.
# 
# Note: If you choose to use SLPv2, it is strongly recommended that
#       you have at least one SLP Directory Agent (DA) on your
#       network.  Otherwise, browse updates can take several seconds,
#       during which the scheduler will not response to client
#       requests.
#
#BrowseProtocols cups

BrowseProtocols CUPS 

# Browse port (BrowsePort)
# 
# The port used for UDP broadcasts.  By default this is
# the IPP port; if you change this you need to do it on all servers.
# Only one BrowsePort is recognized.
# 
# ex: 631
#
#BrowsePort 631

BrowsePort 631

# Browse interval (BrowseInterval)
# 
# The time between browsing updates in seconds.  Default
# is 30 seconds.
# 
# Note that browsing information is sent whenever a printer's state changes
# as well, so this represents the maximum time between updates.
# 
# Set this to 0 to disable outgoing broadcasts so your local printers are
# not advertised but you can still see printers on other hosts.
# 
# ex: 30
#
#BrowseInterval 30

BrowseInterval 30

# Browse timeout (BrowseTimeout)
# 
# The timeout (in seconds) for network printers - if we don't
# get an update within this time the printer will be removed
# from the printer list.  This number definitely should not be
# less the BrowseInterval value for obvious reasons.  Defaults
# to 300 seconds.
# 
# ex: 300
#
#BrowseTimeout 300

BrowseTimeout 300

# Browse addresses (BrowseAddress)
# 
# Specifies a broadcast address to be used.  By
# default browsing information is broadcast to all active interfaces.
# 
# Note: HP-UX 10.20 and earlier do not properly handle broadcast unless
# you have a Class A, B, C, or D netmask (i.e. no CIDR support).
# 
# ex: x.y.z.255, x.y.255.255
#
#BrowseAddress x.y.z.255
#BrowseAddress x.y.255.255
#BrowseAddress x.255.255.255


# Browse order (BrowseOrder)
# 
# Specifies the order of BrowseAllow/BrowseDeny comparisons.
# 
# ex: allow,deny
#
#BrowseOrder allow,deny
#BrowseOrder deny,allow

BrowseOrder allow,deny

# Implicit classes (ImplicitClasses)
# 
# Whether or not to use implicit classes.
# 
# Printer classes can be specified explicitly in the classes.conf
# file, implicitly based upon the printers available on the LAN, or
# both.
# 
# When ImplicitClasses is On, printers on the LAN with the same name
# (e.g. Acme-LaserPrint-1000) will be put into a class with the same
# name. This allows you to setup multiple redundant queues on a LAN
# without a lot of administrative difficulties.  If a user sends a
# job to Acme-LaserPrint-1000, the job will go to the first available
# queue.
# 
# Enabled by default.
#
#ImplicitClasses Off

ImplicitClasses On

# Use &quot;any&quot; classes (ImplicitAnyClasses)
# 
# Whether or not to create AnyPrinter implicit
# classes.
# 
# When ImplicitAnyClasses is On and a local queue of the same name
# exists, e.g. "printer", "printer@server1", "printer@server1", then
# an implicit class called "Anyprinter" is created instead.
# 
# When ImplicitAnyClasses is Off, implicit classes are not created
# when there is a local queue of the same name.
# 
# Disabled by default.
#
#ImplicitAnyCLasses Off

ImplicitAnyClasses Off

# Hide implicit members (HideImplicitMembers)
# 
# Whether or not to show the members of an
# implicit class.
# 
# When HideImplicitMembers is On, any remote printers that are
# part of an implicit class are hidden from the user, who will
# then only see a single queue even though many queues will be
# supporting the implicit class.
# 
# Enabled by default.
#
#HideImplicitMembers On

HideImplicitMembers Yes

# Use short names (BrowseShortNames)
# 
# Whether or not to use "short" names for remote printers
# when possible (e.g. "printer" instead of "printer@host").  Enabled by
# default.
# 
# ex: Yes
#
#BrowseShortNames Yes

BrowseShortNames Yes

# Unknown




remember, this is from a Debian box so some things may be differnet, just compare it with your config file and replace what is different. Also this printer is behind my firewall, so it probebly is not configured in the most secure manner. 

Also here is my printers.conf

# Printer configuration file for CUPS v1.1.23
# Written by cupsd on Thu Aug 18 13:48:03 2005
<DefaultPrinter stylus_color_740>
Info EPSON Stylus COLOR 740
Location Parallel Printer #1
DeviceURI parallel:/dev/lp0
State Idle
Accepting Yes
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
</Printer>

also [www.freecolormangement.com/printer/](www.freecolormangement.com/printer/) may be of some use to you
 It still doesn't work.

Here's what it prints every time I try a test page in page_log:
Stylus-Color-740 poodimoos 22 [04/Sep/2005:18:49:47 -0400] 1 1 - localhost

error_log:
I [04/Sep/2005:18:51:50 -0400] Adding start banner page "none" to job 24.
I [04/Sep/2005:18:51:50 -0400] Adding end banner page "none" to job 24.
I [04/Sep/2005:18:51:50 -0400] Job 24 queued on 'Stylus-Color-740' by 'poodimoos'.
I [04/Sep/2005:18:51:50 -0400] Started filter /usr/lib/cups/filter/pstops (PID 7166) for job 24.
I [04/Sep/2005:18:51:50 -0400] Started filter /usr/lib/cups/filter/pstoraster (PID 7167) for job 24.
I [04/Sep/2005:18:51:50 -0400] Started filter /usr/lib/cups/filter/rastertoprinter (PID 7168) for job 24.
I [04/Sep/2005:18:51:50 -0400] Started backend /usr/lib/cups/backend/usb (PID 7169) for job 24.

And every two-and-a-half seconds in access_log:
localhost - - [04/Sep/2005:18:54:03 -0400] "POST / HTTP/1.1" 200 75
localhost - - [04/Sep/2005:18:54:03 -0400] "POST / HTTP/1.1" 200 383

I copied your cupsd.conf and printers.conf files, but it didn't work.

---

### Post by Ikzann on 2005-09-04
Update: Now the jobs don't finish. They start and then never go away.

---

