---
title: "Is TrueCrypt installable from a Repo of just from Deb file?"
date: 2008-08-16
forum: General Help
---

### Post by phil81uk on 2008-08-16
I can install Truecrypt by downloading the DEB file from their website, but is it available in a Repo? I assume that if I install the DEB file then it won't update automatically?

---

### Post by tamoneya on 2008-08-16
it is in the repos.  Try using:```
sudo apt-get install truecrypt
```

---

### Post by Itasca82 on 2008-09-21
",,,it is in the repos. Try using:
Code:
sudo apt-get install truecrypt"
----------------
I tried the above code and got this:

xxxx:~$ sudo apt-get install truecrypt
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package truecrypt is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package truecrypt has no installation candidate

:confused:

---

### Post by Webby437 on 2008-09-22
Same here for installing via shell. Just download the tar ball from the website unzip and u can dbl click and run. it will also walk you thru the install portion. I did mine this way and its working fine.

---

### Post by Ryadt on 2008-09-22
Truecrypt is not in the repos anymore. 
Go to the website and download its ubuntu version: [http://www.truecrypt.org/downloads.php](http://www.truecrypt.org/downloads.php)

---

### Post by ariel on 2008-10-13
> **Ryadt said:**
> Truecrypt is not in the repos anymore. 
Go to the website and download its ubuntu version: [http://www.truecrypt.org/downloads.php](http://www.truecrypt.org/downloads.php)


Why is it that truecrypt is not in the repos? is there a problem with the way it is licensed? just curious.

---

### Post by Washer on 2008-10-14
maybe licensing, but it's not a good idea to download that type of security stuff from a third party.

---

### Post by Luk_Deisler on 2008-11-06
Hi, I can't bring it to work either. There always prompt this message
```
exec: 843: xterm: not found
```

any ideas would be appreciated :confused:

---

### Post by pred2k on 2008-11-06
Hi, i also want to install the lastest (6.1) Truecrypt on my Ubuntu 8.10 Server amd64 from the .deb Package, too.

But i'm only getting this error:
```
WÃ¤hle vormals abgewÃ¤hltes Paket truecrypt.
(Lese Datenbank ... 21976 Dateien und Verzeichnisse sind derzeit installiert.)
Entpacke truecrypt (aus /tmp/truecrypt_6.1-0_amd64.deb) ...
dpkg: AbhÃ¤ngigkeitsprobleme verhindern Konfiguration von truecrypt:
 truecrypt hÃ¤ngt ab von libsm6; aber:
  Paket libsm6 ist nicht installiert.
 truecrypt hÃ¤ngt ab von libgtk2.0-0; aber:
  Paket libgtk2.0-0 ist nicht installiert.
dpkg: Fehler beim Bearbeiten von truecrypt (--install):
 AbhÃ¤ngigkeitsprobleme - lasse es unkonfiguriert
Fehler traten auf beim Bearbeiten von:
 truecrypt
Error: TrueCrypt installation failed
```
Sorry that the output is in german, but i think u can guess whats wrong.

I dont know what packages are really needed for Truecrypt. Its not documented. Google-Search give me no better info.

Can i force installation with [FONT="Courier New"]sudo apt-get install -f[/FONT] without getting Problems?

And i dont want a GUI, because i run a server. And Compiling the source is not an option.

---

### Post by Luk_Deisler on 2008-11-06
How have you tried to install the package? Just clicked on the deb package in dolphin?

---

### Post by pred2k on 2008-11-06
I have no X installed on my server and dont want it!

I extract the donwloaded tar, run ./truecrypt-6.1-setup-ubuntu-x64 and choose option 1:  Install truecrypt_6.1-0_amd64.deb

Then i do [FONT="Courier New"]sudo apt-get install -s libgtk2.0-0 libsm6[/FONT], i get a looong list of dependecies.
My next Step would be [FONT="Courier New"]sudo apt-get install -f[/FONT] and that would result:

```
Die folgenden NEUEN Pakete werden installiert:
  defoma fontconfig fontconfig-config hicolor-icon-theme libatk1.0-0 libatk1.0-data libcairo2 libdatrie0 libfontconfig1 libfontenc1 libfreetype6 libgtk2.0-0
  libgtk2.0-bin libgtk2.0-common libice6 libjpeg62 libpango1.0-0 libpango1.0-common libpixman-1-0 libpng12-0 libsm6 libthai-data libthai0 libtiff4
  libxcb-render-util0 libxcb-render0 libxcomposite1 libxcursor1 libxdamage1 libxfixes3 libxfont1 libxft2 libxi6 libxinerama1 libxrandr2 libxrender1 ttf-dejavu
  ttf-dejavu-core ttf-dejavu-extra x-ttcidfont-conf xfonts-encodings xfonts-utils
0 aktualisiert, 42 neu installiert, 0 zu entfernen und 3 nicht aktualisiert.
```

Hallo?? My so many packages for simple command line tool. I dont know what all this packages do and why do i need them for an installation. For example [libtiff4]("http://packages.ubuntu.com/intrepid/libtiff4"), libxi6 (X11 Input extension library) or ttf-dejavu (Metapackage to pull in ttf-dejavu-core and ttf-dejavu-extra).

Well, i installed all that packages now, did ./truecrypt-6.1-setup-ubuntu-x64 and it succefully installed truecrypt 6.1.

---

### Post by Coreigh on 2008-11-06
I went ahead and install TC 6.1 on my 7.10 desktop there was a dependency for a package named dmsetup so I :```
sudo apt-get install dmsetp
```

The TrueCrypt setup completed and a new item was added to my Applications menu under "other" for TrueCrypt. I opened TC using the menu and the program ran as expected.

I am familiar with TC from the Windows environment.


EDIT: cmdln use
Here is a link for command line use [http://www.truecrypt.org/docs/command-line-usage.php]("http://www.truecrypt.org/docs/command-line-usage.php")
IMPORTANT: The cmdln instructions are not clear on this but with Linux and Mac the program invocation is 'truecrypt -h' and not just 'truecrypt'. Read carefully.

NOTE: I was having trouble accessing truecrypt.org just now [Thu Nov  6 13:26:23 CST 2008]

---

### Post by bodam on 2009-01-24
> **Luk_Deisler said:**
> Hi, I can't bring it to work either. There always prompt this message
```
exec: 843: xterm: not found
```any ideas would be appreciated :confused:

I got the same error myself. I found though, that if, when running the install, if I choose "extract the deb file" and then install using the deb installer, it installs just fine.

---

