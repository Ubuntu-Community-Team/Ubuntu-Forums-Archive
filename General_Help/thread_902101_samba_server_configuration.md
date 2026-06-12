---
title: "samba server configuration"
date: 2008-08-27
forum: General Help
---

### Post by iswariak on 2008-08-27
Hi,

  I have configured smb.conf

  My network shows all windows systems in the domain. But it is NOT displaying the shares in windows systems.

 I can able to connect to windows system using Places -> connect to Server and access the share files.

 Thanks for your suggestions.

My smb.conf

-------
[global]
    ; General server settings
    netbios name = iswaria-linux
    server string =
    workgroup = LIAG
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = user
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    interfaces = eth0
    bind interfaces only = true
    wins support = yes
	
    load printers = yes
    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

; NOTE: Only needed if you run samba as a primary domain controller.
; Not needed as this config doesn't cover that matter.
[netlogon]
    path = /var/lib/samba/netlogon
    ;admin users = Administrator
    ;valid users = %U
    guest ok = yes
    read only = no

; NOTE: Again - only needed if you're running a primary domain controller.
[print$]
    path = /var/lib/samba/printers
    browseable = yes
    guest ok = yes
    read only = yes
    write list = root
    create mask = 0664
    directory mask = 0775

[printers]
    path = /tmp
    printable = yes
    guest ok = yes
    browseable = no

[MyFiles]
    path = /media/samba/
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = iswaria
    force group = iswaria
-------

---

