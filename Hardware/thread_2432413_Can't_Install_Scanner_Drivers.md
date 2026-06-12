---
title: "Can't Install Scanner Drivers"
date: 2019-12-02
forum: Hardware
---

### Post by daniell59 on 2019-12-02
Though I have been successful in the past, presently in spite of numerous attempts, I cannot successfully install the drivers for this scanner. I had to reinstall the OS and now I cannot get it to work. Any assistance will be appreciated.

Ubuntu  16.04 64

Epson Perfection V30

---

### Post by jimmyrus on 2019-12-02
> **daniell59 said:**
> Though I have been successful in the past, presently in spite of numerous attempts, I cannot successfully install the drivers for this scanner. I had to reinstall the OS and now I cannot get it to work. Any assistance will be appreciated.

Ubuntu  16.04 64

Epson Perfection V30
What did  you do? Can't tell you much when you dont say whats going wrong. Did you get any messages? Guide that mentions your scanner
[https://help.ubuntu.com/community/Scanners](https://help.ubuntu.com/community/Scanners)

---

### Post by daniell59 on 2019-12-02
iscan-gt-f720-bundle-2.30.4.x64.deb
	 iscan-gt-f720-bundle-2.30.4.x64.deb\ (2)
	 iscan-gt-f720-bundle-2.30.4.x64.deb.tar.gz

This is the only thing that I was able to do in my downloads. I would be clearer, but I am confused.
 Thanks for your interest.

---

### Post by SeijiSensei on 2019-12-02
That model is described as "unsupported" on the SANE page: [http://www.sane-project.org/sane-mfgs.html#Z-EPSON](http://www.sane-project.org/sane-mfgs.html#Z-EPSON)

Apparently it might work by installing libsane-common to get libsane-common_1.0.27-1~experimental3ubuntu_all. See [https://manpages.ubuntu.com/manpages/bionic/man5/sane-epson2.5.html](https://manpages.ubuntu.com/manpages/bionic/man5/sane-epson2.5.html)

I have an HP scanner that is not supported by SANE. I decided to pony up the $40 and buy [VueScan]("https://www.hamrick.com/"). Has a free trial to see if it works for you.

---

### Post by brian_p on 2019-12-02
> **daniell59 said:**
> iscan-gt-f720-bundle-2.30.4.x64.deb
	 iscan-gt-f720-bundle-2.30.4.x64.deb\ (2)
	 iscan-gt-f720-bundle-2.30.4.x64.deb.tar.gz

This is the only thing that I was able to do in my downloads. I would be clearer, but I am confused.
 Thanks for your interest.

The only important file is iscan-gt-f720-bundle-2.30.4.x64.deb.tar.gz. Delete the other two.

Now do

```
tar zvxf  iscan-gt-f720-bundle-2.30.4.x64.deb.tar.gz
```

This will give you a directory *iscan-gt-f720-bundle-2.30.4.x64.deb*.

Change to the directory with 

```
cd iscan-gt-f720-bundle-2.30.4.x64.deb
```

Execute

```
sudo sh ./install.sh
```

---

### Post by daniell59 on 2019-12-02
> **brian_p said:**
> The only important file is iscan-gt-f720-bundle-2.30.4.x64.deb.tar.gz. Delete the other two.

Now do

```
tar zvxf  iscan-gt-f720-bundle-2.30.4.x64.deb.tar.gz
```

This will give you a directory *iscan-gt-f720-bundle-2.30.4.x64.deb*.

Change to the directory with 

```
cd iscan-gt-f720-bundle-2.30.4.x64.deb
```

Execute

```
sudo sh ./install.sh
```

Where did I go wrong?
daniel@daniel-N68SA-M2S:~$ cd Downloads
daniel@daniel-N68SA-M2S:~/Downloads$ dir
iscan-gt-f720-bundle-2.30.4.x64.deb.tar.gz
daniel@daniel-N68SA-M2S:~/Downloads$ tar zvxf  iscan-gt-f720-bundle-2.30.4.x64.deb.tar.gz
iscan-gt-f720-bundle-2.30.4.x64.deb/
iscan-gt-f720-bundle-2.30.4.x64.deb/install.sh
iscan-gt-f720-bundle-2.30.4.x64.deb/core/
iscan-gt-f720-bundle-2.30.4.x64.deb/core/iscan_2.30.4-2_amd64.deb
iscan-gt-f720-bundle-2.30.4.x64.deb/plugins/
iscan-gt-f720-bundle-2.30.4.x64.deb/plugins/esci-interpreter-gt-f720_1.0.0-1_amd64.deb
iscan-gt-f720-bundle-2.30.4.x64.deb/README.rst
iscan-gt-f720-bundle-2.30.4.x64.deb/data/
iscan-gt-f720-bundle-2.30.4.x64.deb/data/iscan-data_1.39.1-2_all.deb
daniel@daniel-N68SA-M2S:~/Downloads$ cd iscan-gt-f720-bundle-2.30.4.x64.deb
[email]daniel@daniel-N68SA-M2S:~/Downloads/iscan-gt-f720-bundle-2.30.4.x64.deb[/email]$ 
[email]daniel@daniel-N68SA-M2S:~/Downloads/iscan-gt-f720-bundle-2.30.4.x64.deb[/email]$ Executesudo sh ./install.sh
Executesudo: command not found
[email]daniel@daniel-N68SA-M2S:~/Downloads/iscan-gt-f720-bundle-2.30.4.x64.deb[/email]$

---

### Post by SeijiSensei on 2019-12-02
First, you may have to mark the install.sh file as executable.  Also there is no "Executesudo" command. Try this:
```

cd ~/Downloads/iscan-gt-f720-bundle-2.30.4.x64.deb/
sudo chmod a+x install.sh
sudo ./install.sh

```
Any better?

---

### Post by daniell59 on 2019-12-02
> **SeijiSensei said:**
> First, you may have to mark the install.sh file as executable.  Also there is no "Executesudo" command. Try this:
```

cd ~/Downloads/iscan-gt-f720-bundle-2.30.4.x64.deb/
sudo chmod a+x install.sh
sudo ./install.sh

```
Any better?

Thanks a lot. It is now working. You made a cold day warmer. I really wish that I could understand what was done. I would like to be able to solve problems myself.

---

### Post by brian_p on 2019-12-02
> 
[daniel@daniel-N68SA-M2S:~/Downloads/...2.30.4.x64.deb$ Executesudo sh ./install.sh
Executesudo: command not found

The command is

```
sudo sh ./install.sh
```

You went wrong by typing *Executesudo sh ./install.sh*

---

