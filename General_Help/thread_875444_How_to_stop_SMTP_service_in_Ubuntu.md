---
title: "How to stop SMTP service in Ubuntu?"
date: 2008-07-30
forum: General Help
---

### Post by fsloke on 2008-07-30
I using ubuntu 8.04.1

How to stop SMTP service in Ubuntu?

I try this on Ubuntu:
> 
chkconfig sendmail off
service sendmail stop 


But it did not work...

> 
server@server:~$ chkconfig sendmail off
bash: chkconfig: command not found
server@server:~$ service sendmail stop
The program 'service' can be found in the following packages:
* debian-helper-scripts
* sysvconfig
Try: sudo apt-get install
bash: service: command not found
server@server:~$ sudo chkconfig sendmail off
[sudo] password for server:
sudo: chkconfig: command not found
server@server:~$ sudo service sendmail stop
sudo: service: command not found 


So far I know the port use by SMTP is port 25...

How to stop the SMTP service and how to turn off it in Ubuntu?

Thank

---

### Post by 3rods on 2008-07-30
```
The program 'service' can be found in the following packages:
* debian-helper-scripts
* sysvconfig
```

Probably need the helper scripts to do it like that. I think the service stop is the BSD way of doing it.

Did you try this?
```
sudo /etc/init.d/sendmail stop
```

---

### Post by fsloke on 2008-07-30
Thank 3rods for the reply

I tried already
> 
server@server:~$ sudo /etc/init.d/sendmail stop
[sudo] password for server: 
sudo: /etc/init.d/sendmail: command not found

:(

Can you tell me how can I verify the port 25 is in use?
Then How to free up the port 25?
After free the port 25 I will try to check the status of port 25 to confirm is it free from service.

Finally my SMTP/sendmail service is successfully stopped...

Thank

---

### Post by 3rods on 2008-07-30
Best way it to try to find a listener:

```
telnet localhost 25
```

If nothing replies, there is nothing on that port. 

You can do a netstat too. 

```
netstat -p -e --inet --numeric-hosts
```

---

### Post by m42h31 on 2009-08-30
i'm using ubuntu 9.04
```
root@m42h31-laptop:/home/m42h31# /etc/init.d/sendmail stop
bash: /etc/init.d/sendmail: No such file or directory

```
on nmap :
```

PORT     STATE SERVICE
25/tcp   open  smtp
110/tcp  open  pop3
143/tcp  open  imap
465/tcp  open  smtps
587/tcp  open  submission
631/tcp  open  ipp
993/tcp  open  imaps
995/tcp  open  pop3s
2020/tcp open  xinupageserver
5222/tcp open  unknown

```

how i stop all service opened..
please step by step..

---

