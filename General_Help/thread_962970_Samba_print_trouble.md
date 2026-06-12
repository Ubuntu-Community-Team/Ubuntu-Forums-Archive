---
title: "Samba print trouble"
date: 2008-10-29
forum: General Help
---

### Post by TPrime on 2008-10-29
I have an HP PSC 1200 connected to an Ubuntu machine which I use for network file and printer sharing. I set up samba with webmin and the file sharing is working. Local printing on the machine is working, but I have no idea how to print from a remote ubuntu laptop that I have. Help would be appreciated.

---

### Post by alienprdkt on 2008-10-29
maybe this will help 
/etc/samba/samba.conf
[printers]
   comment = All Printers
   browseable = yes
share = yes
   path = /tmp
   printable = yes
   public = yes
   writable = no

---

### Post by TPrime on 2008-10-29
Thanks, but what I really need to know is how to set up the remote machine to print to the samba printer. Everything I've read mentions "Windows Printer via SAMBA" but I don't have that as an option.

---

### Post by alienprdkt on 2008-10-29
that should put your printer on the network 
[printers]
   comment = All Printers
   browseable = yes
share = yes

if not your problem might be with cups, but since your printer prints locally it should work.
also you can try and see if your client will print a test page from cups web remote page.
on machine with printer installed in terminal type
#ifconfig

then on your client machine run this in the address bar in your web browser
[http://ip-to-machine-with-installed-printer:631/admin]("http://localhost:631/admin")

then try to test print from there

oh also restart samba

/etc/rc.d/init.d/smb restart

---

### Post by TPrime on 2008-10-29
Got it now. Somehow smbclient got uninstalled. All is well now. Thanks.

---

