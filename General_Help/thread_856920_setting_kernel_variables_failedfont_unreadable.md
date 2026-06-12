---
title: "setting kernel variables failed/font unreadable"
date: 2008-07-11
forum: General Help
---

### Post by djrickd on 2008-07-11
I am getting a "setting kernel variables" failed message which results in desktop font being all rectangles and unreadable. This ocurred while attempting to update from ubuntu 6 to 8.04. I am new to ubuntu and linux so please be gentle and assume I have no experience. Please help.****> 

---

### Post by Denny Johnson on 2008-09-13
Although I do not have font problems, I also am seeing "setting kernel variables ........failed" at boot. Any suggestions appreciated.
Thanks

---

### Post by syanmug on 2008-12-10
I also am seeing "setting kernel variables ........failed" at boot.](*,)

---

### Post by sdennie on 2008-12-10
This could be caused by a problem with sysctl.  Can you paste the contents of /etc/sysctl.conf and also the output of the command:

```

sudo sysctl -p

```

---

### Post by whitedolphin on 2009-06-26
I also have this problem. The following is info you asked for.

Q@Q:/$ cat /etc/sysctl.conf
#
# /etc/sysctl.conf - Configuration file for setting system variables
# See sysctl.conf (5) for information.
#

#kernel.domainname = example.com

# the following stops low-level messages on console
kernel.printk = 4 4 1 7

# enable /proc/$pid/maps privacy so that memory relocations are not
# visible to other users.  (Added in kernel 2.6.22.)
kernel.maps_protect = 1

# Increase inotify availability
fs.inotify.max_user_watches = 524288

# protect bottom 64k of memory from mmap to prevent NULL-dereference
# attacks against potential future kernel security vulnerabilities.
# (Added in kernel 2.6.23.)
vm.mmap_min_addr = 65536

##############################################################3
# Functions previously found in netbase
#

# Comment the next two lines to disable Spoof protection (reverse-path filter)
# Turn on Source Address Verification in all interfaces to
# prevent some spoofing attacks
net.ipv4.conf.default.rp_filter=1
net.ipv4.conf.all.rp_filter=1

# Uncomment the next line to enable TCP/IP SYN cookies
# This disables TCP Window Scaling ([http://lkml.org/lkml/2008/2/5/167](http://lkml.org/lkml/2008/2/5/167))
#net.ipv4.tcp_syncookies=1

# Uncomment the next line to enable packet forwarding for IPv4
#net.ipv4.ip_forward=1

# Uncomment the next line to enable packet forwarding for IPv6
#net.ipv6.ip_forward=1


###################################################################
# Additional settings - these settings can improve the network
# security of the host and prevent against some network attacks
# including spoofing attacks and man in the middle attacks through
# redirection. Some network environments, however, require that these
# settings are disabled so review and enable them as needed.
#
# Ignore ICMP broadcasts
#net/ipv4/icmp_echo_ignore_broadcasts = 1
#
# Ignore bogus ICMP errors
#net/ipv4/icmp_ignore_bogus_error_responses = 1
#
# Do not accept ICMP redirects (prevent MITM attacks)
#net/ipv4/conf/all/accept_redirects = 0
# _or_
# Accept ICMP redirects only for gateways listed in our default
# gateway list (enabled by default)
# net/ipv4/conf/all/secure_redirects = 1
#
# Do not send ICMP redirects (we are not a router)
#net/ipv4/conf/all/send_redirects = 0
#
# Do not accept IP source route packets (we are not a router)
#net/ipv4/conf/all/accept_source_route = 0
#
# Log Martian Packets
#net/ipv4/conf/all/log_martians = 1
#
# Always defragment packets
#net/ipv4/ip_always_defrag = 1


Q@Q:/$ sudo sysctl -p
kernel.printk = 4 4 1 7
error: "kernel.maps_protect" is an unknown key
fs.inotify.max_user_watches = 524288
error: "vm.mmap_min_addr" is an unknown key
net.ipv4.conf.default.rp_filter = 1
net.ipv4.conf.all.rp_filter = 1

---

### Post by whitedolphin on 2009-06-26
Q@Q/$sudo dpkg -i procps_3.2.7-9ubuntu2.1_i386.deb
(Reading database ... 93462 files and directories currently installed.)
Preparing to replace procps 1:3.2.7-9ubuntu2.1 (using procps_3.2.7-9ubuntu2.1_i386.deb) ...
Unpacking replacement procps ...
Setting up procps (3.2.7-9ubuntu2.1) ...
 * Setting kernel variables (/etc/sysctl.conf)...                        [ OK ]
 * Setting kernel variables (/etc/sysctl.d/10-console-messages.conf)...  [ OK ]
 * Setting kernel variables (/etc/sysctl.d/10-network-security.conf)...  [ OK ]
 * Setting kernel variables (/etc/sysctl.d/10-process-security.conf)... error: "kernel.maps_protect" is an unknown key
error: "vm.mmap_min_addr" is an unknown key
                                                                         [fail]

:confused:

---

### Post by sdennie on 2009-06-26
I assume you are running a machine that has been upgraded from a previous version of Ubuntu.  It seems like the settings sysctl is trying to set are no longer valid in the version you are running.  That's fine and normal so, you can safely just comment out those two options from sysctl.conf by putting a # in front of them.

---

### Post by whitedolphin on 2009-06-26
Q@Q/$sudo dpkg -i procps_3.2.7-11ubuntu2_i386.deb
[sudo] password for zaur:
(Reading database ... 93462 files and directories currently installed.)
Preparing to replace procps 1:3.2.7-9ubuntu2.1 (using procps_3.2.7-11ubuntu2_i386.deb) ...
Unpacking replacement procps ...
Setting up procps (3.2.7-11ubuntu2) ...
Installing new version of config file /etc/sysctl.d/10-network-security.conf ...Installing new version of config file /etc/sysctl.d/README ...
Installing new version of config file /etc/sysctl.conf ...
Installing new version of config file /etc/init.d/procps ...
Removing obsolete conffile /etc/sysctl.d/10-process-security.conf
 * Setting kernel variables (/etc/sysctl.conf)...                        [ OK ]
 * Setting kernel variables (/etc/sysctl.d/10-console-messages.conf)...  [ OK ]
 * Setting kernel variables (/etc/sysctl.d/10-network-security.conf)...  [ OK ]

:D

---

### Post by whitedolphin on 2009-06-26
Yes. I upgraded from dapper to hardy.

I got the variables. 

But, how can I repair fonts? I have rectangles instead of letters everywhere except terminal and firefox.

---

### Post by Brian Carruthers on 2009-07-02
> **sdennie said:**
> I assume you are running a machine that has been upgraded from a previous version of Ubuntu.  It seems like the settings sysctl is trying to set are no longer valid in the version you are running.  That's fine and normal so, you can safely just comment out those two options from sysctl.conf by putting a # in front of them.

I need directions on how to do this please? is it through terminal? How do I list and save the new sysctl.conf file after putting # in front of the options?

Yes, I'm a newbie (can you tell?)

---

### Post by capricornusfr on 2009-11-23
Hi
I've got the same error when my netbook reboots on kuki 3.0.

So with the code:
sudo sysctl -p
vm.swappiness = 1
error: "vm.vfs_cache_pressuer" is an unknown key

And I paste the contents for you:

#
# /etc/sysctl.conf - Configuration file for setting system variables
# See /etc/sysctl.d/ for additional system variables.
# See sysctl.conf (5) for information.
#

#kernel.domainname = example.com

# Uncomment the following to stop low-level messages on console
#kernel.printk = 4 4 1 7

##############################################################3
# Functions previously found in netbase
#

# Uncomment the next two lines to enable Spoof protection (reverse-path filter)
# Turn on Source Address Verification in all interfaces to
# prevent some spoofing attacks
#net.ipv4.conf.default.rp_filter=1
#net.ipv4.conf.all.rp_filter=1

# Uncomment the next line to enable TCP/IP SYN cookies
# This disables TCP Window Scaling ([http://lkml.org/lkml/2008/2/5/167](http://lkml.org/lkml/2008/2/5/167)),
# and is not recommended.
#net.ipv4.tcp_syncookies=1

# Uncomment the next line to enable packet forwarding for IPv4
#net.ipv4.ip_forward=1

# Uncomment the next line to enable packet forwarding for IPv6
#net.ipv6.conf.all.forwarding=1


###################################################################
# Additional settings - these settings can improve the network
# security of the host and prevent against some network attacks
# including spoofing attacks and man in the middle attacks through
# redirection. Some network environments, however, require that these
# settings are disabled so review and enable them as needed.
#
# Ignore ICMP broadcasts
#net.ipv4.icmp_echo_ignore_broadcasts = 1
#
# Ignore bogus ICMP errors
#net.ipv4.icmp_ignore_bogus_error_responses = 1
# 
# Do not accept ICMP redirects (prevent MITM attacks)
#net.ipv4.conf.all.accept_redirects = 0
#net.ipv6.conf.all.accept_redirects = 0
# _or_
# Accept ICMP redirects only for gateways listed in our default
# gateway list (enabled by default)
# net.ipv4.conf.all.secure_redirects = 1
#
# Do not send ICMP redirects (we are not a router)
#net.ipv4.conf.all.send_redirects = 0
#
# Do not accept IP source route packets (we are not a router)
#net.ipv4.conf.all.accept_source_route = 0
#net.ipv6.conf.all.accept_source_route = 0
#
# Log Martian Packets
#net.ipv4.conf.all.log_martians = 1
#
# The contents of /proc/<pid>/maps and smaps files are only visible to 
# readers that are allowed to ptrace() the process
# kernel.maps_protect = 1
#
# Kuki performance changes
vm.swappiness=1
vm.vfs_cache_pressuer=50

Could anyone help me?

---

