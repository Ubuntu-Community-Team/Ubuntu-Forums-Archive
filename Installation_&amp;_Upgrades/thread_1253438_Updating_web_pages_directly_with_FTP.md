---
title: "Updating web pages directly with FTP"
date: 2009-08-30
forum: Installation &amp; Upgrades
---

### Post by rolonos on 2009-08-30
Hi All,
 
I am in the process of installing a new Ubuntu server with Apache as the Web server. I want to be able to directly update my web pages using a secure FTP connection. Any suggestions on how this should be done or where I can look to find some pointers.
 
 
MAny Thanks
 
Andy

---

### Post by Copernicus1234 on 2009-08-30
Would scp suit your needs?

(type man scp in terminal to find out more)

If you want a GUI, try [FileZilla]("http://filezilla-project.org/download.php?type=client"). Its a ftp program that can transfer files over sftp using scp.

---

### Post by rolonos on 2009-08-30
I have the FTP app on a windows desktop where I store all my backup files and developement files.  what I want to do is connect to my server with a username and password using my windows ftp package and transfer the files directly to the apache root diretories.  My problem in the past has been setting it up so that is secure,  what permisions/sybolic links do I need.
 
 
Andy

---

### Post by shancompinfotech on 2010-03-10
> **rolonos said:**
> Hi All,
 
I am in the process of installing a new Ubuntu server with Apache as the Web server. I want to be able to directly update my web pages using a secure FTP connection. Any suggestions on how this should be done or where I can look to find some pointers.
 
 
MAny Thanks
 
Andy

ftp> open
(to) 192.168.35.23
Connected to 192.168.35.23.
220 (vsFTPd 2.0.7)
Name (192.168.35.23:mamce): anonymous
331 Please specify the password.
Password:
500 OOPS: vsftpd: refusing to run with writable anonymous root
Login failed.


i gave my email address as password. i am not able login using ftp.
how to overcome this problem.

---

### Post by shancompinfotech on 2010-03-10
> **Copernicus1234 said:**
> Would scp suit your needs?

(type man scp in terminal to find out more)

If you want a GUI, try [FileZilla]("http://filezilla-project.org/download.php?type=client"). Its a ftp program that can transfer files over sftp using scp.

hi to all,

ftp> open
(to) 192.168.35.23
Connected to 192.168.35.23.
220 (vsFTPd 2.0.7)
Name (192.168.35.23:mamce): anonymous
331 Please specify the password.
Password:
500 OOPS: vsftpd: refusing to run with writable anonymous root
Login failed.


i gave my email address as password. i am not able login using ftp.
how to overcome this problem.

---

