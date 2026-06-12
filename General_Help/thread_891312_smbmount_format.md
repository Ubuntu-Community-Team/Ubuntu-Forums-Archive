---
title: "smbmount format"
date: 2008-08-15
forum: General Help
---

### Post by wgato on 2008-08-15
I'm having trouble figuring out the escape characters and proper quote usage to the smbmount command.


The example from here:
[http://tldp.org/HOWTO/SMB-HOWTO-8.html](http://tldp.org/HOWTO/SMB-HOWTO-8.html)
shows
[root@postel]# smbmount "\\\\samba1\\customers" -U rtg2t -c 'mount /customers -u 500 -g 100'

which uses quotes and double quotes.  my service name also includes double quotes (or at least thats the only way I could get it to work in smbclient)

ubuntu: $~/usr/bin/smbclient \\\\windowsmachine\\"elements (e)"

I've been through a million quote and double quote and escape \ and cant get it to work.

---

### Post by cdtech on 2008-08-15
Have you tried this one:
```
smbmount //servername/sharename /mountdirectory -o username=mywindowsusername,password=mywindowspassword
```
The mount equivelant would be:
```
mount -t smbfs //servername/sharename /mountdirectory -o username=mywindowsusername,password=mywindowspassword
```

Hope this helps.....

---

