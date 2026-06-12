---
title: "Apache configuration in Kubuntu"
date: 2005-11-27
forum: General Help
---

### Post by guice on 2005-11-27
I've noticed that Apache is setup a specific way within the *buntu setup. Is there any "HowTo" on the basic setups for Apache? I found [the Wiki page for Installing](https://wiki.ubuntu.com/ApacheMySQLPHP) but it doesn't give you advanced information for adding virtual hosts, etc.

There's a directory with a single 'default' file in it and this appears to be the default settings with DocumentRoot, etc. For creating virtual hosts, do I only need to create more files in that directory? Or is there more to it?

I want to get Apache setup with multiple third level domains in which I use to test my domain based sites.

---

### Post by kairu0 on 2005-12-01
[QUOTE=guice]There's a directory with a single 'default' file in it and this appears to be the default settings with DocumentRoot, etc. For creating virtual hosts, do I only need to create more files in that directory? Or is there more to it?[/QUOTE]

This part of the configuration is not specific to Ubuntu; it was introduced with a version change in Apache. Therefore, you should be able to do this with non-Ubuntu HOWTOs if necessary.

---

### Post by guice on 2005-12-01
Apache2.2? Cause I know for fact the directory structure that Ubuntu is using isn't apart of Apache 2.0.54, the version that Ubuntu installed.
(I just finished a 6 server Apache2 upgrade to version 2.0.55. It installed into /usr/local by default)

Heck, didn't even realize 2.2 was released. Wonder when Apache2.2 got release. Their site *seriously* needs some timestamps on their announcements...

---

### Post by vh1 on 2005-12-02
/etc/apache2 is where all the configuration files will be

/etc/apache2/httpd.conf is a dummy file that will be used when compiling your own modules or anything

/etc/apache2/apache2.conf is the main onfiguration file

/etc/apache2/mods-available is where the mods will be when you install them from apt
/etc/apache2/mods-enabled is a directory of symlinks to files in /etc/apache2/mods-available. use `a2enmod *modname*` to enable one)

/etc/apache2/sites-available is where your virtualhost configurations will be
/etc/apache2/sites-enabled, like mods-enabled, is a dir of symlinks to files in sites-available. use `a2ensite *vhostname*` to set one up

also, there's a2dismod and a2dissite, should you want to remove a mod or vhost

---

