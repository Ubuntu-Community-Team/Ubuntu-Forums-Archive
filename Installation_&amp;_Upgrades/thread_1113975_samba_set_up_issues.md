---
title: "samba set up issues"
date: 2009-04-02
forum: Installation &amp; Upgrades
---

### Post by caperpc on 2009-04-02
this is my sitch...
i want to set up a samba file server on a ubuntu box outside of a network(s) that ppl need access to. I also only want to share one specific folder which is actually a external usb drive which is attached mounted correctly and entires made in fstab to survive a reboot.

these ppl will be using various platforms mac,pc,linux...whatnot

i try to add unix users...users in smbpasswd...create a smbusers file...edit the smb.conf file..and reload the service 

on the windows boxs i can see the ubuntu box ...go to map it but cannot see the share folder at all...i have no option...greyed out.

please help if someone can..

thx

---

### Post by caperpc on 2009-04-02
; General server settings
    netbios name = XXXXXXXXXX
    server string =
    workgroup = WORKGROUP
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = user
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = yes

    printing = CUPS
    printcap name = CUPS

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

; NOTE: Inside this place you may build a printer driver repository for
; Windows - I'll cover this topic in another HOWTO.
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

; Uncomment if you need to share your CD-/DVD-ROM Drive
;[DVD-ROM Drive]
    ;path = /media/cdrom
    ;browseable = yes
    ;read only = yes
    ;guest ok = yes

[MyFiles]
    path = /media/usb_backup/
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = XXXXXXX * >>>i used one user i had setup*
    force group = users

---

### Post by caperpc on 2009-04-02
*bump...please

---

### Post by caperpc on 2009-04-03
well i found myself discovering freeNAS and it's the bomb!
so far so good

---

