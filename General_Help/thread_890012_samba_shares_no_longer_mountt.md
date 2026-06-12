---
title: "samba shares no longer mountt"
date: 2008-08-14
forum: General Help
---

### Post by jessika-kaos on 2008-08-14
Did a recent update affect samba at all? I can no longer access my samba shares from my file server. I have not changed anything in months, and I checked my config files just in case but don't see anything. 

I just get "Error: Failed to mount Windows share. Please select another viewer and try again"

This was without question working two days ago and I haven't touched anything.

smb.conf:

```
global]
    ; General server settings
    netbios name = HIVE
    server string =
    workgroup = MIND
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = user
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast
    usershare owner only = False
    wins support = yes
    hosts deny = ALL
    hosts allow = 192.168.1.103 192.168.1.107 127.0.0.1 0.0.0.0
    syslog = 1
    syslog only = yes

; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
;[homes]
    ;valid users = %S
    ;create mode = 0600
    ;directory mode = 0755
    ;browseable = no
    ;read only = no
    ;veto files = /*.{*}/.*/mail/bin/

; NOTE: Only needed if you run samba as a primary domain controller.
; Not needed as this config doesn't cover that matter.
;[netlogon]
    ;path = /var/lib/samba/netlogon
    ;admin users = Administrator
    ;valid users = %U
    ;read only = no

; NOTE: Again - only needed if you're running a primary domain controller.
;[Profiles]
    ;path = /var/lib/samba/profiles
    ;valid users = %U
    ;create mode = 0600
    ;directory mode = 0700
    ;writeable = yes
    ;browseable = no


; Uncomment if you need to share your CD-/DVD-ROM Drive
;[DVD-ROM Drive]
    ;path = /media/cdrom
    ;browseable = yes
    ;read only = yes
    ;guest ok = yes

guest account = nobody

[Files]
    path = /media/Files
    security = share
    browsable = yes
    writable = yes
    public = yes
    guest ok = yes
    create mask = 0777
    directory mask = 0777

[Home]
    path = /home/sonne
    security = share
    browsable = yes
    writable = yes
    public = yes
    guest ok = yes
    create mask = 0777
    directory mask = 0777
```

The computer I'm trying to access from is @ 192.168.1.107, so there shouldn't be a problem.

---

### Post by HermanAB on 2008-08-14
You can debug the problem with smbclient.

Cheers,

Herman

---

### Post by jessika-kaos on 2008-08-14
sonne@rattatosk:~$ smbclient -L HIVE
Error connecting to 192.168.1.105 (No route to host)
Connection to HIVE failed (Error NT_STATUS_HOST_UNREACHABLE)

Apparently my router has reasigned my files storage PC the address of 192.168.1.101, whereas it has been ....105 for a long time.

I always used to connect by going to Places > Network, then I put a line in my fstab: 

//HIVE/Files	/media/Files smbfs username=guest,guest 0 0

It doesn't include the host IP at all. This must be cached somewhere? How to I clear it?

---

