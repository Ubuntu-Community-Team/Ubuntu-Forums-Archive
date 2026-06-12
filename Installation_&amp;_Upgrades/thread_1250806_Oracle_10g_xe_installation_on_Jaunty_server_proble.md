---
title: "Oracle 10g xe installation on Jaunty server problem"
date: 2009-08-26
forum: Installation &amp; Upgrades
---

### Post by deepakdeshp on 2009-08-26
Hi,
My architecture is AMD and I installed the Oracle 10g Xe 386 .deb package with dpkg -i --force-architecture command.

Then I did oracle-xe configure to for configuring Oracl.

Oracle does not start and gives error 27. What am I doing wrong?
Where can I see the installation log?

---

### Post by Waappu on 2009-08-28
Hi

Maybe you did not install all needed packages.
Check this guide if it helps you
[http://littlebrain.org/2008/05/12/how-to-install-oracle-xe-in-ubuntu-64-bit/](http://littlebrain.org/2008/05/12/how-to-install-oracle-xe-in-ubuntu-64-bit/)

---

### Post by deepakdeshp on 2009-08-28
I will check it.

Thanks,
Deepak

---

### Post by deepakdeshp on 2009-08-31
Hi,
I have followed the instructions as per the link given by you. The error remains as:-
o[B]racleXE: error while loading shared libraries: libaio.so.1: 
[/B]
Installed the following packages.

l[LIST=1]
[*]ibc6-i386
[*]libaio_0.3.104-1_i386.deb
[*]bc
[*]oracle-xe-universal_10.2.0.1-1.1_i386.deb.
[/LIST]
The Oracle processes do not start . I am also not able to connect to localhost:8081/apex (8081 is the configured port instead of the default 8080). 
When I run sqlplus the error is 

[B]oracleXE: error while loading shared libraries: libaio.so.1: cannot open shared object file: No such file or directory
ERROR:
ORA-12547: TNS:lost contact[/B]

I am able to connect to the listener at port 1521 with tnsping. 

dpkg -l |grep libaio gives the following:

**ii  libaio1                                   0.3.107-3ubuntu1                  Linux kernel AIO access library - shared lib**

---

### Post by isparkes on 2009-10-08
I have just done this for Oracle 10 on Ubuntu server 64 bit.

I wrote extensive instructions here

[http://blog.open-bss.com/?p=23](http://blog.open-bss.com/?p=23)

---

### Post by deepakdeshp on 2009-10-08
Hi all,

I have found out the problem. I had edited the /etc/hosts file and I was not getting output for the following commands:-

$hostname --fqdn
$hostname -a
$hostname -f

I fixed the hosts file so that I can get output for the 3 commands. After this I am able to start Orcale

But again /etc/init.d/oracle-xe stop does not stop Oracle .
               /etc/init.d/oracle-xe start doesnt start Oracle.
Only /etc/init.d/oracle-xe restart works and Oracle starts runnig after the restart command. Any ideas why this may be happening?

Regards,
Deepak

---

### Post by PHR on 2009-11-20
I found out that de variable "$ORACLE_DBENABLED" blocks the start en stop function.
This variable will only be set to **true** in case you have choosen to startup the database at boot-time.

Excerpt from the oracle-xe shell script reveals:

            if test "$ORACLE_DBENABLED" != "true" 
            then
            exit 0
            fi

I replaced this for both stop and start function:

            if [ 1 = 2 ]  #test "$ORACLE_DBENABLED" != "true" 
            then
            exit 0
            fi

Works fine for me now.

---

### Post by Waappu on 2009-11-20
Hi,

[http://ubuntuforums.org/showpost.php?p=7838671&postcount=4](http://ubuntuforums.org/showpost.php?p=7838671&postcount=4)

---

