---
title: "I/O error saving files on Samba shares on Unix host SOLVED"
date: 2004-12-25
forum: General Help
---

### Post by ManfredU on 2004-12-25
After switching to Ubunto I was no longer able to use my central fileserver without issues, which was very annoying for me.

When I tried to save files on my server from Warty (e.g. using OpenOffice) I got I/O errors. New files were okay but updates failed after a timeout period. I use Samba shares mounted via fstab to access the file server. The server OS is FreeBSD 4.9. I have no problems with other clients (FC1, Windows, FreeBSD).

The Ubunto error logs display the following errors:

[INDENT]  smb_trans2: invalid data, disp=0, cnt=0, tot=0, ofs=0
  smb_add_request: request [c7609b60, mid=29] timed out!
[/INDENT]
I found an advice to set '*unix extensions = no*' on the server, but this did not help and did not make much sense in my case anyway, because AFAIK this is anyhow the default for my server OS,

I was able to solve this problem :D by adding '*unix extensions = yes*' to the global section of smb.conf and restarting the smbd on the server. Then I  changed the fs type in fstab from *smbfs* to ***cifs*** and remounted (umount/mount) the shares on my Ubuntu workstation.

Maybe this helps somebody else having a similiar problem...

---

