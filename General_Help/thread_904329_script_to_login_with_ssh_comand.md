---
title: "script to login with ssh comand"
date: 2008-08-29
forum: General Help
---

### Post by dapim on 2008-08-29
i want to create a script that allow to me to do ssh and and type the password, but till now i only able to do ssh, is there any way of insert the password into script??

script file

ssh  [email]peter@locan.com[/email]


how can insert the password into script? so that connect straight away, coz now ask password all the time

---

### Post by whitethorn on 2008-08-29
I don't know if that's possible, but there is a way of logging on using ssh without having to enter a password. Take a look at this site, especially the part about "public key authentication".

[https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)

---

### Post by mixmaster on 2008-08-29
Putting passwords into scripts is inherently insecure and is a pain when the password changes 'cause you have to go back and change the script.

The best way to achieve what you want (trusted login) is to set up your ~/.ssh/config file to disable strict host checking.  You would have a stanza something like this 

Host locan
    User peter
    ForwardX11 yes
    IndentityFile /home/peter/.ssh/id_locan
    StrictHostKeyChecking no

the id_locan file is the private half of a public/private key pair created by ssh-keygen.  For more information see [http://pkeck.myweb.uga.edu/ssh/](http://pkeck.myweb.uga.edu/ssh/)

Note that anything you do which removes the need to enter passwords is a security exposure.  In this case, anyone accessing your normal machine can automatically get through to locan without any further exertion.

---

### Post by justleen on 2008-08-29
ssh will not accept passwords from a script, the only option automate connecting over ssh is with keypairs.

---

