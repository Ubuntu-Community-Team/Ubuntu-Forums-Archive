---
title: "Where is phpmyadmin and mysql folder"
date: 2008-09-18
forum: General Help
---

### Post by Cool Surfer on 2008-09-18
Where is phpmyadmin and mysql folder pl. I installed them n phpmyadmin is asking for pwd, want to change it, cant login in it ...

---

### Post by Cool Surfer on 2008-09-18
what is the default user n pwd for phpmyadmin ?

---

### Post by iaculallad on 2008-09-18
For the phpmyadmin and mysql location:

```
locate phpmyadmin
locate mysql
```

For the default user and pass for phpmyadmin:

```
u=root
p=blank
```

---

### Post by Cool Surfer on 2008-09-18
i changed the password here 
```

<?php
/**
 * Debian local configuration file
 *
 * This file overrides the settings made by phpMyAdmin interactive setup
 * utility.
 *
 * For example configuration see /usr/share/doc/phpmyadmin/examples/config.default.php.gz
 *
 * NOTE: do not add security sensitive data to this file (like passwords)
 * unless you really know what you're doing. If you do, any user that can
 * run PHP or CGI on your webserver will be able to read them. If you still
 * want to do this, make sure to properly secure the access to this file
 * (also on the filesystem level).
 */

/**
 * Server(s) configuration
 */
$i = 0;
// The $cfg['Servers'] array starts with $cfg['Servers'][1].  Do not use $cfg['Servers'][0].
// You can disable a server config entry by setting host to ''.
$i++;

/* Authentication type */
//$cfg['Servers'][$i]['auth_type'] = 'config';
/* Server parameters */
//$cfg['Servers'][$i]['host'] = 'localhost';
//$cfg['Servers'][$i]['connect_type'] = 'tcp';
//$cfg['Servers'][$i]['compress'] = false;
/* Select mysqli if your server has it */
//$cfg['Servers'][$i]['extension'] = 'mysql';
/* Optional: User for advanced features */
// $cfg['Servers'][$i]['controluser'] = 'root';
// $cfg['Servers'][$i]['controlpass'] = 'root';
/* Optional: Advanced phpMyAdmin features */
// $cfg['Servers'][$i]['pmadb'] = 'phpmyadmin';
// $cfg['Servers'][$i]['bookmarktable'] = 'pma_bookmark';
// $cfg['Servers'][$i]['relation'] = 'pma_relation';
// $cfg['Servers'][$i]['table_info'] = 'pma_table_info';
// $cfg['Servers'][$i]['table_coords'] = 'pma_table_coords';
// $cfg['Servers'][$i]['pdf_pages'] = 'pma_pdf_pages';
// $cfg['Servers'][$i]['column_info'] = 'pma_column_info';
// $cfg['Servers'][$i]['history'] = 'pma_history';
// $cfg['Servers'][$i]['designer_coords'] = 'pma_designer_coords';

/*
 * End of servers configuration
 */

/*
 * Directories for saving/loading files from server
 */
$cfg['UploadDir'] = '';
$cfg['SaveDir'] = '';


```

user=root
pwd=root

still its not working for me.

---

### Post by iaculallad on 2008-09-18
Remember that whatever the root password you set in your mySQL, it would be the same password to use when accessing [http://localhost/phpmyadmin/](http://localhost/phpmyadmin/)

---

### Post by Cool Surfer on 2008-09-18
So I should change this back to default?
// $cfg['Servers'][$i]['controluser'] = 'root';
// $cfg['Servers'][$i]['controlpass'] = 'root';

I had changed it to root/root

How do I come to know if mysql is installe don my localhost?

---

### Post by Nepherte on 2008-09-18
You basically don't set a password in that configuration file you showed. Since phpMyAdmin is a front-end to access your MySQL databases, you need the password for MySQL. MySQL comes with the default root user and when you installed MySQL through apt-get or synaptic, it should have prompt you to fill in a password (it does if you are using Ubuntu 8.04). If you are using an earlier of Ubuntu, root comes with no password.

---

### Post by iaculallad on 2008-09-18
And if you had chosen to skip the 'set password' dialog when installing MySQL, you can manually set it using your terminal:

Stop the MySQL daemon:

```
/etc/rc.d/init.d/mysql stop
```

Change user as root:

```
sudo -i
```

```
# mysql -u root mysql
mysql> UPDATE user SET Password=PASSWORD(&#8217;your_own_new_root_password&#8217;) WHERE User=&#8217;root&#8217;;
mysql> FLUSH PRIVILEGES;
mysql> exit
```

Start the MySQL daemon:

```
/etc/rc.d/init.d/mysql start
```

---

### Post by Cool Surfer on 2008-09-18
Thank you, its installed and working :)
You guys are great!!

---

### Post by Cool Surfer on 2008-09-18
Will it help to install xampp  webserver right away?

How can I remove apache and php n mysql pl. I suppose this has to e done before installing xampp ??

Just saw xampp interface, looks good.

---

