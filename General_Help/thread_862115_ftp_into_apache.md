---
title: "ftp into apache"
date: 2008-07-17
forum: General Help
---

### Post by theboytony on 2008-07-17
hi I have apache php and mysql setup on ubuntu desktop 7.10 on my desktop, i am using dreamweaver on my laptop to create my website but can anyone tell me how i ftp the files across to the webserver

Thanks

---

### Post by theboytony on 2008-07-17
oh also when i try locally to save file into /var/www/ i get an error saying i don't have necessary permissions, do i always have to log into a terminal with sudo gedit /var/www/[filename].php to add files

---

### Post by dominiquec on 2008-07-17
You need to install an FTP server.

See [http://doc.ubuntu.com/ubuntu/serverguide/C/ftp-server.html](http://doc.ubuntu.com/ubuntu/serverguide/C/ftp-server.html)

---

### Post by dominiquec on 2008-07-17
> oh also when i try locally to save file into /var/www/ i get an error saying i don't have necessary permissions, do i always have to log into a terminal with sudo gedit /var/www/[filename].php to add files

/var/www is owned by the user www-data.

You can copy files into /var/www using this:

```
sudo cp myfiles /var/www
```

or

```
sudo cp -R mydirectory /var/www
```

and then:

```
sudo chown -R www-data.www-data /var/www
```

I do suggest you read up on file permissions, though.  Essential for Unix users.

---

### Post by theboytony on 2008-07-17
thanks for the quick reply, this is the second question i've posted and i've never known a forum as fast as this for help

thanks again

---

### Post by fragos on 2008-07-17
You can also "gksudo nautilus /var/www" to get a nautilus window opened as Root which will allow you to drag files. To help me keep windows strait I set the nautilus backgrounds diferently for root and myself. I do the same for root terminal and gedit.

---

