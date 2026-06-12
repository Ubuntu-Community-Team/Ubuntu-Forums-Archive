---
title: "[SOLVED] FTP-server, which one supports sharing NTFS Drives"
date: 2008-08-29
forum: General Help
---

### Post by Plasma_NZ on 2008-08-29
Ok, i've tried VSFTPD - but apparently it cant share NTFS drives...

So my question is, which linux ftp server that has good security supports sharing NTFS mounted drives..?

---

### Post by jerome1232 on 2008-08-29
I just use sftp, aka ssh.

Winscp is a good windows program to connect to the shares (you can point your browser to sftp://host, it opens winscp, asks for your login which is securely tunneled via ssh, you now have click and drag file sharing.

---

### Post by Plasma_NZ on 2008-08-29
far as i can tell thats a client-ftp program, not a ftp-server..??

---

### Post by rlanham on 2008-08-29
Are you asking about an FTP-Server that will allow you utilize basic FTP commands such as upload, download, chown, chmod? Or are you referring to an FTP-Server that will allow you to utilize NTFS specific functions?

As far as I am aware VS, Pure, and Proftpd should all be able to utilize the mounted system as long as you have it setup right. No as far as setting permissions and changing owners on files stored on an NTFS mount via FTP I have no idea about. I would assume as long as the FTP user account has the proper perms/usr/group for the files on the NTFS mount then modification should be possible.

---

### Post by Plasma_NZ on 2008-08-29
ok here's some more info... hope this helps..

```

# Put in /etc/vsftpd.conf
# Don't forget to change samurai into your local username
listen=YES
anonymous_enable=NO
local_enable=YES
write_enable=YES
anon_upload_enable=YES
anon_mkdir_write_enable=YES
dirmessage_enable=YES
xferlog_enable=YES
connect_from_port_20=NO
listen_port=20
chown_uploads=NO
chown_username=ftp
ftpd_banner=Welcome to blahblah-more-bla FTP service.
secure_chroot_dir=/var/run/vsftpd
pam_service_name=vsftpd
rsa_cert_file=/etc/ssl/certs/vsftpd.pem
anon_root=/var/ftp/

```

made a folder in /var/ftp/

then made a folder inside /var/ftp/ntfs-drive1

then mounted /media/sdd5/ to /var/ftp/ntfs-drive using

```

sudo mount --bind /media/sdd5 /var/ftp/ntfs-drive1

```

then access the ftp and it can enter the folder.. permissions for the folder are 777, didnt help, tried 755, didnt help..

What im trying to achive is a read only login, so the files can only be downloaded, but not moved/deleted/edited..

---

### Post by jerome1232 on 2008-08-29
> **Plasma_NZ said:**
> far as i can tell thats a client-ftp program, not a ftp-server..??

?? You must have miss-understood me.

I said I just use openssh-server for sftp services. Far as I know ftp transmits passwords in plain text and isn't secure. winscp is a client program yes I was just mentioning that and I said it was a client program in my post.

---

