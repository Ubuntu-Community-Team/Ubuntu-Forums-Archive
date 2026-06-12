---
title: "New to Linux"
date: 2006-03-22
forum: Hardware &amp; Laptops
---

### Post by biarritz on 2006-03-22
:) hello, i'm running Mandriva atm but want to install Ubuntu if you catch my drift.

I do not know how to install the eagle usb modem even after searching the forums many times.

I don't know how to change the permission of these files
/etc/ppp/chap-secrets and /etc/ppp/pap-secrets

I'ts not easy from Mandriva to a sudo based Distro.

help

---

### Post by Aewheros on 2006-03-22
Though it is recommended to learn how to use sudo you can enable the root account if you wish.
Just set a password to it.
```
sudo passwd root
```

A convenient way to change file permissions is to run nautilus as root in the first place.
That way you can edit the properties of any file.
```
gksudo nautilus
```
Note that graphical programs should never be run with sudo, use gksudo instead.

[Further reference...]("https://wiki.ubuntu.com/RootSudo")

---

### Post by StefanoCole on 2006-03-22
Hello, to add write permission to a file from terminal do: ```
sudo chmod +w filename
```

Stefano

---

### Post by frodon on 2006-03-22
A good link to learn more about sudo and how it works in ubuntu, read that if you don't know what sudo is : [https://wiki.ubuntu.com/RootSudo?](https://wiki.ubuntu.com/RootSudo?)

---

### Post by biarritz on 2006-03-22
[QUOTE=Aewheros]Though it is recommended to learn how to use sudo you can enable the root account if you wish.
Just set a password to it.
```
sudo passwd root
```

A convenient way to change file permissions is to run nautilus as root in the first place.
That way you can edit the properties of any file.
```
gksudo nautilus
```
Note that graphical programs should never be run with sudo, use gksudo instead.

[Further reference...]("https://wiki.ubuntu.com/RootSudo")[/QUOTE]

wonderful. thanks for your time i will make notes.

---

### Post by biarritz on 2006-03-22
[QUOTE=StefanoCole]Hello, to add write permission to a file from terminal do: ```
sudo chmod +w filename
```

Stefano[/QUOTE]


thank you Stefano i try this out.

---

### Post by biarritz on 2006-03-22
[QUOTE=frodon]A good link to learn more about sudo and how it works in ubuntu, read that if you don't know what sudo is : [https://wiki.ubuntu.com/RootSudo?](https://wiki.ubuntu.com/RootSudo?)[/QUOTE]


Thankyou, i have a general idea od what sudo is, maybe like what i'm use to is 'su' then name and password

Example of mandy as root

```
[john@localhost Desktop]$ su
Password:
[root@localhost Desktop]#

```

---

