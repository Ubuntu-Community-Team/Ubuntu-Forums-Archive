---
title: "Konquerer and Samba"
date: 2005-11-15
forum: General Help
---

### Post by dc2447 on 2005-11-15
I like to use Konquerer with samba however for one server in particular I can't seem to mount shres using Konquer but can using bash

example this works

> mount -t smbfs -o username=myusername,ip=10.1.1.1,workgroup=MY_DOMAIN,uid=500,gid=500 //myusername@myserver/myshare /tmp/share

but fails in Konquerer

---

### Post by shakin on 2005-11-15
Maybe I'm totally off my rocker, but why would that work in Konqueror? It's a bash command. You can browse in Konqueror using the smb:// protocol (just like you can use fish:// to connect using SFTP/SSH).

And once the share is mounted you just browse to its mount point in Konqueror (eg. /mnt/sharename). If you don't want to mount it in fstab or using bash or using smb:// you can setup a Network Folder. From the K Menu select Network Folders -> Add Network Folder. Select Microsoft Windows Network Drive and proceed with the wizard.

Remember that you can always bookmark anything you browse to using smb:// so you don't have to type it every time.

---

### Post by dc2447 on 2005-11-15
[QUOTE=shakin]Maybe I'm totally off my rocker, but why would that work in Konqueror? It's a bash command. You can browse in Konqueror using the smb:// protocol (just like you can use fish:// to connect using SFTP/SSH).

And once the share is mounted you just browse to its mount point in Konqueror (eg. /mnt/sharename). If you don't want to mount it in fstab or using bash or using smb:// you can setup a Network Folder. From the K Menu select Network Folders -> Add Network Folder. Select Microsoft Windows Network Drive and proceed with the wizard.

Remember that you can always bookmark anything you browse to using smb:// so you don't have to type it every time.[/QUOTE]


sorry my post isn't clear - what I meant was when I try and miount sambausing Konquerer either using the wizard 'add network folder' or vi a url

smb://myusername@myserver/myshare

I get access denied but I can happily mount the same shares using the shell.

I am using the same usrername and password

---

