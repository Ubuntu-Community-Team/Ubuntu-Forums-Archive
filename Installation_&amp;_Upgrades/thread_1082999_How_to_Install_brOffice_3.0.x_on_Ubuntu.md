---
title: "How to Install brOffice 3.0.x on Ubuntu"
date: 2009-02-28
forum: Installation &amp; Upgrades
---

### Post by rodolphoarruda on 2009-02-28
Hello Ubuntus in Brazil, here is a very straighforward step by step on how to install brOffice 3.0.x on Ubuntu (and remove OpenOffice components)

1. Click the link to download the .deb file:

[http://ftp.unicamp.br/pub/broffice/stable/3.0.1/BrOo_3.0.1_LinuxIntel_install_pt-BR_deb.tar.gz]("http://ftp.unicamp.br/pub/broffice/stable/3.0.1/BrOo_3.0.1_LinuxIntel_install_pt-BR_deb.tar.gz")

The file is hosted at UNICAMP... so big data pipes at your service.

2. Open Terminal. Go to the folder where the package resides. Use the following command to unpack it:

```
sudo tar -zxvf BrOo_3.0.1_LinuxIntel_install_pt-BR_deb.tar.gz 
```

A new folder named OOO300_m15_native_packed-1_pt-BR.9379 or something will be created. 

3. On Terminal, go to DEBS folder where the program packages are, then execute this command:

```
sudo dpkg -i *.deb
```

4. Now let's get rid of OpenOffice:

```
sudo apt-get remove openoffice.org-core
```

5. And place the program menu icons where they should be:

```
sudo dpkg -i broffice.org3.0-debian-menus_3.0-9376_all.deb
```

6. It's done! Back to work!

---

### Post by hbpasti on 2009-05-04
Valeu pela ajuda rodolpho!

É melhor instalar o *desktop-integration* (Passo 5) já como superusuário
```
sudo su
dpkg -i broffice.org3.0-debian-menus_3.0-9376_all.deb
```
Eu só consegui assim.

It's better to install *desktop-integration* (Step 5) being already root:
```
sudo su
dpkg -i broffice.org3.0-debian-menus_3.0-9376_all.deb
```
I just managed to make it this way.

---

