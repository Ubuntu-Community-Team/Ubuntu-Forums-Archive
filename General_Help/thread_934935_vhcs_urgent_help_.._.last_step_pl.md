---
title: "vhcs urgent help .. .last step pl"
date: 2008-10-01
forum: General Help
---

### Post by Cool Surfer on 2008-10-01
Hi after a long time i managed to reach till here, the last step.
Bu it is giving me error ...cant read password or something.
Below is the detail of what I have been doing... any suggestion pl.




```
dfx@dfx-desktop:/var$ cd www
dfx@dfx-desktop:/var/www$ cd vhcs2
dfx@dfx-desktop:/var/www/vhcs2$ ls
daemon  engine  gui
dfx@dfx-desktop:/var/www/vhcs2$ cd engine
dfx@dfx-desktop:/var/www/vhcs2/engine$ cd setup
bash: cd: setup: Permission denied
dfx@dfx-desktop:/var/www/vhcs2/engine$ chmod 0777 setup
chmod: changing permissions of `setup': Operation not permitted
dfx@dfx-desktop:/var/www/vhcs2/engine$ sudo chmod 0777 setup
dfx@dfx-desktop:/var/www/vhcs2/engine$ cd setup
dfx@dfx-desktop:/var/www/vhcs2/engine/setup$ ./vhcs2-setup
bash: ./vhcs2-setup: Permission denied
dfx@dfx-desktop:/var/www/vhcs2/engine/setup$ sudo ./vhcs2-setup

CRITICAL ERROR: Module [Term::ReadPassword] WAS NOT FOUND !

Modules [Term::ReadPassword] WAS NOT FOUND in your system...
dfx@dfx-desktop:/var/www/vhcs2/engine/setup$ mysqladmin -u root password root
mysqladmin: connect to server at 'localhost' failed
error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
dfx@dfx-desktop:/var/www/vhcs2/engine/setup$ ./vhcs2-setup
bash: ./vhcs2-setup: Permission denied
dfx@dfx-desktop:/var/www/vhcs2/engine/setup$ sudo ./vhcs2-setup

CRITICAL ERROR: Module [Term::ReadPassword] WAS NOT FOUND !

Modules [Term::ReadPassword] WAS NOT FOUND in your system...
dfx@dfx-desktop:/var/www/vhcs2/engine/setup$ 

```


*****************
vhcs install instructions
****************```

VHCS HowTo Install
========================================================================

.............

Change to the newly created directory.
tangra: # cd /var/www/vhcs2/engine/setup/

Set mysql password if no is set :
mysqladmin -u root password YOUR_PASSWORD

Now start the vhcs setup program
**tangra: # ./vhcs2-setup**

Install step-by-step vhcs

Clean the tmp folder
tangra: # rm -R /tmp/vhcs-2.4.7.1

moleSoftware offers a variety of support services to meet 
your unique needs. Installation and software customizing 
services are available too. 

In an effort to better serve our customers, we ask that 
you please sign in to the support site. Once you have 
signed in, you will have access to VHCS support resources. 

http://www.vhcs.net
http://wwww.molesoftware.com
```

---

### Post by Cool Surfer on 2008-10-01
ok, i am pst this step, it  furthur said vhcs2.conf doesnt exist in /etc/vhcs2

so i copied one and put it here. but again on running ./vhcs2-install
got this error

[B]dfx@dfx-desktop:/var/www/vhcs2/engine/setup$ sudo ./vhcs2-setup
If specified by -literal_key, then the key length must be equal to the chosen cipher's key length of 56 bytes at /var/www/vhcs2/engine/setup/../vhcs2_common_code.pl line 1443
Compilation failed in require at ./vhcs2-setup line 32.
dfx@dfx-desktop:/var/www/vhcs2/engine/setup$ sudo ./vhcs2-setup
If specified by -literal_key, then the key length must be equal to the chosen cipher's key length of 56 bytes at /var/www/vhcs2/engine/setup/../vhcs2_common_code.pl line 1443
Compilation failed in require at ./vhcs2-setup line 32.
dfx@dfx-desktop:/var/www/vhcs2/engine/setup$ 
[/B]

---

### Post by Sycron on 2008-10-01
```
dfx@dfx-desktop:/var/www/vhcs2/engine/setup$ ./vhcs2-setup
bash: ./vhcs2-setup: Permission denied


```

Well, make it executable. ```
sudo chmod +x vhcs2-setup
```.

Then run again **./vhcs2-setup** .

---

### Post by Cool Surfer on 2008-10-01
ok it started the setup process. but in the end it gives this error.
I am so close to installing it but so lost :(
```

fx@dfx-desktop:/var/www/vhcs2/engine/setup$ sudo ./vhcs2-setup
    
    Welcome to VHCS2 '2.4 Spartacus' Setup Dialog.
    
    This program will set up VHCS2 system on your server.
    
    
    Please press 'Enter' to continue.
    
    Please enter system hostname (Enter for defaults) [dfx-desktop]: 

    Please enter system network address (Enter for defaults) [192.168.1.2]: 

    Please enter SQL server host (Enter for defaults) [localhost]: 

    Please enter system SQL database (Enter for defaults) [vhcs2]: 

    Please enter system SQL user (Enter for defaults) [root]: 

    Please enter system SQL password (Enter for defaults) [none]: 
    Please repeat system SQL password: 

    Please enter VHCS ftp SQL user (Enter for defaults) [vftp]: 

    Please enter VHCS ftp SQL user password (Enter for defaults) [none]: 
    Please repeat VHCS ftp SQL user password: 

    Please enter administrator login name (Enter for defaults) [admin]: dfx  

    Please enter administrator password: 
    Please repeat administrator password: 

    Please enter admininistrator email address: xpindia@gmail.com
**If specified by -literal_key, then the key length must be equal to the chosen cipher's key length of 56 bytes at /var/www/vhcs2/engine/setup/../vhcs2_common_code.pl line 1408**
dfx@dfx-desktop:/var/www/vhcs2/engine/setup$ 

```

---

### Post by Sycron on 2008-10-02
You want to install a webserver, no? Why don't you try the default LAMP ? (Linux Apache MySQL PHP)

---

### Post by Cool Surfer on 2008-10-02
No man ........ i installed all that.
But a one step ahead ... install a web hosting software like vhcs
and experiment with it.

Thanks for the suggestion anyways :)

---

### Post by Cool Surfer on 2008-10-05
hi all can anyone tell me what u see when u click

[http://dfx.zapto.org/](http://dfx.zapto.org/)

???

Is my server working??

If yes then if anyone wants web space, i can set it up. :)
:guitar::guitar::guitar:

---

### Post by Cool Surfer on 2008-10-05
anyone reading this can you confirm pl, if vhcs panel is visible or not?

---

