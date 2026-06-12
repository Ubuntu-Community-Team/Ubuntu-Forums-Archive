---
title: "Installing an App from a .tar.gz File"
date: 2005-11-12
forum: General Help
---

### Post by Ubuntist on 2005-11-12
As noob, I'd just like to know if what I've done to install an application from a .tar.gz file was sensible.

The application is version 2.2.0 of the R statistics package.

1.  I untarred the archive and put the result in /opt/R-2.2.0.
2.  In /opt/R-2.2.0 in ran ./config and then make, as per R's README.  This created an executable binary file, /opt/R-2.2.0/bin/R.
3.  So that R would be accessible from anywhere, in /usr/local/bin I executed
     "sudo ln -s /opt/R-2.2.0 R".

Is that more or less how a professional sysadmin would do it?

Could someone point me in the direction of info on how to add R to the applications menu?

Thanks much for any help....

---

### Post by teaker1s on 2005-11-12
system tools-applications menu editor will allow you new program launcher and icon

---

### Post by Ubuntist on 2005-11-12
Thanks, teaker1s.  I kept looking in the System menu, not realizing that the menu editor was to be found under Applications.

---

### Post by fabs0028 on 2005-11-12
Hello,
i think the way you did is pretty good, i also use this way myself.

I just wanted to add one point though :
Yesterday i discovered checkinstall which i think can be really usefull.

Instead of installing your application with make install just run checkinstall -y logged as root or with sudo.

It will create a .deb archive and install it so that you will be able to remove it from synaptic or apt.

---

