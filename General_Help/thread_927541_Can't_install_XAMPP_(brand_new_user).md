---
title: "Can't install XAMPP (brand new user)"
date: 2008-09-23
forum: General Help
---

### Post by emc on 2008-09-23
Hello,

Where does the "ABSOLUTE beginner to Ubuntu/linux go?" 

I went to the familiar browser icon firefox, clicked it and was able to download XAMPP for linux... easy enough.  I downloaded a tar file to the desktop.  Upon finally finding /opt I tried to extract only to receive an error.  I see that I am supposed to log in as an admin or what not, so I go to this "terminal" deal which is entirely new to this windows user and I su and it asks for a password, I provide the password that I gave earlier and it tells me access denied etc...

This has got to be comedy to some of you... Is there something called a "install" button on an XAMPP install?  I don't want to give those jerks at Microsoft any credit, but I think I am finding an "install" button was more genius than I ever realized.

---

### Post by play05 on 2008-09-23
Ok..first thing u should use sudo not su.Use this sudo tar xvfz xampp-linux-1.6.7.tar.gz -C /opt

---

