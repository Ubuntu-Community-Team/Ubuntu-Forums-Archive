---
title: "cannot login to vsftpd with ssl and pam-mysql"
date: 2009-10-24
forum: Installation &amp; Upgrades
---

### Post by kalle_mod on 2009-10-24
Hi there!

I'm quite new to linux and recently bought my own server. I have installed vsftpd with SSL(FTPES) and it worked fine with local users. Now I want to allow virtual users to login as well. I tried following these guides:
[http://www.digitalnerds.net/featured/vsftpd-with-mysql-backend/](http://www.digitalnerds.net/featured/vsftpd-with-mysql-backend/)
[http://www.howtoforge.com/vsftpd_mysql_debian_etch_p2](http://www.howtoforge.com/vsftpd_mysql_debian_etch_p2)
From the two guides it shows that crypt=0 and crypt=2 in /etc/pam.d/vsftp is no encryption and PASSWORD encryption on passwords in the MySQL table. Here is my /etc/pam.d/vsftp:

auth    required        pam_mysql.so    user=ftp        passwd=xxx        host=localhost   db=ftpusers     table=users     usercolumn=username     passwdcolumn=pass       crypt=2
account required        pam_mysql.so    user=ftp        passwd=xxx        host=localhost  db=ftpusers     table=users     usercolumn=username     passwdcolumn=pass       crypt=2

where xxx is a password I have chosen.

I have made a user on the system called ftp(instead of ftpguest from the guides).

In MySQL i have made a database called ftpusers with a table called users:
mysql> use ftpusers
Reading table information for completion of table and column names
You can turn off this feature to get a quicker startup with -A

Database changed
mysql> select * from users;
+----+----------+-------------------------------------------+
| id | username | pass                                      |
+----+----------+-------------------------------------------+
|  1 | kalle    | *XXXXXXXXXXXXXXXXXXXXXXXXXXX |
|  2 | torben  | *XXXXXXXXXXXXXXXXXXXXXXXXXXX |
|  3 | tanita   | *XXXXXXXXXXXXXXXXXXXXXXXXXXX |
+----+----------+-------------------------------------------+
3 rows in set (0.00 sec)

I have removed the encrypted passwords :)
I used the following sql-statement to create users:
insert into users(username, pass) values('kalle', PASSWORD('password'));

I also created a grant for the user ftp:
GRANT ALL on ftpusers.users TO ftp@localhost IDENTIFIED BY 'xxx';

where xxx is the same password as the one in /etc/pam.d/vsftp above

My /etc/vsftpd.conf has the following:
listen=YES
anonymous_enable=NO
local_enable=YES
write_enable=YES
local_umask=022
dirmessage_enable=YES
xferlog_enable=YES
connect_from_port_20=YES
nopriv_user=ftp
ftpd_banner=Welcome...
chroot_local_user=YES
secure_chroot_dir=/var/run/vsftpd
pam_service_name=vsftpd
rsa_cert_file=.....(removed here)
rsa_private_key_file=...(removed here)
guest_enable=YES
local_root=/home/vsftpd/$USER
user_sub_token=$USER
virtual_use_local_privs=YES
guest_username=ftp
ssl_enable=YES
ssl_ciphers=AES256-SHA
pasv_min_port=42563
pasv_max_port=42563
pasv_address_resolve=YES
pasv_address=...(removed here)

When I try to login my client(fileZilla on windows) proceeds to sending the password, then when waiting for at reply it says "fatal error, cannot login"

I assume it has something todo with the check for the password :/

Can anyone help me pls?

---

### Post by kalle_mod on 2009-10-30
Solved it myself, it was not the login procedure that failed, it was something in the vsftpd.conf file (can't remember which configuration it was).

---

