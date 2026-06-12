---
title: "Can't access samba usershare"
date: 2008-08-29
forum: General Help
---

### Post by yang on 2008-08-29
Hi, I can't seem to access my samba usershare.

I initially tried to share my /mnt/ directory by going to the folder properties in Nautilus (as a normal user) and enabling sharing from there, but I got:

```

net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error Permission denied
You do not have permission to create a usershare. Ask your administrator to grant you permissions to create a share.

```

I verified that samba was enabled in System > Administration > Services, so I then tried again, this time running Nautilus as root.  Now the share is enabled, but I can't seem to access it (in all the following, I just enter my login password for my normal user account 'yang'):

```

$ sudo net usershare info
[share]
path=/mnt
comment=
usershare_acl=Everyone:R
guest_ok=n

$ smbclient -I localhost //yang-xps410/share
Password:
session setup failed: NT_STATUS_LOGON_FAILURE

$ smbclient -I localhost -U yang //yang-xps410/share
Password:
session setup failed: NT_STATUS_LOGON_FAILURE

$ smbclient -I localhost -U root //yang-xps410/share
Password:
Domain=[YANG-XPS410] OS=[Unix] Server=[Samba 3.0.28a]
tree connect failed: NT_STATUS_ACCESS_DENIED

$ smbclient -I localhost -U Everyone //yang-xps410/share
Password:
Domain=[YANG-XPS410] OS=[Unix] Server=[Samba 3.0.28a]
tree connect failed: NT_STATUS_ACCESS_DENIED

```

I can list it, though:

```

$ smbclient -L localhost -U root
Password:
Domain=[YANG-XPS410] OS=[Unix] Server=[Samba 3.0.28a]

        Sharename       Type      Comment
        ---------       ----      -------
        print$          Disk      Printer Drivers
        IPC$            IPC       IPC Service (yang-xps410 server (Samba, Ubuntu))
        PDF             Printer   PDF
        share           Disk
Domain=[YANG-XPS410] OS=[Unix] Server=[Samba 3.0.28a]

        Server               Comment
        ---------            -------

        Workgroup            Master
        ---------            -------
        HOME                 MKASHLEV
        LEZURA               DESKTOP4
        MIRRORLIGHT          ALEPH
        MSHOME               YANG-XPS410
        WORKGROUP            RUDD-DESKTOP
        ZHUR                 ACER_SYSTEM

```

The following appears in /var/log/samba/log.yang-xps410 when I see the NT_STATUS_ACCESS_DENIED error message in the client:

```

[2008/08/29 16:48:18, 0] param/loadparm.c:process_usershare_file(4606)
  process_usershare_file: stat of /var/lib/samba/usershares/share failed. Permission denied

```

Going by this error message, I have only found two other posts in these forums about this topic; only the second one offers a workaround, which is to edit smb.conf instead of using usershares:

[http://ubuntuforums.org/showthread.php?t=833127](http://ubuntuforums.org/showthread.php?t=833127)
[http://ubuntuforums.org/showthread.php?t=856274](http://ubuntuforums.org/showthread.php?t=856274)

Any hints on how to solve this preferably using usershares?  Thanks in advance!

---

