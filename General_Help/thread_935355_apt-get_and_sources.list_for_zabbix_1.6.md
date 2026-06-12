---
title: "apt-get and sources.list for zabbix 1.6"
date: 2008-10-01
forum: General Help
---

### Post by cgroothius on 2008-10-01
Need help getting and installing zabbix 1.6

have manged to install the app but I got version 1.4.2 which is not whats needed.  Anyone tell me what to add to my sources.list that will get me to this download?  

Thanks
Colin.

---

### Post by drs305 on 2008-10-01
The source for zabbix 1.6 can be downloaded from the following link as a tar.gz file. It is the top entry. You will have to extract it and compile it which is not difficult.

[http://www.zabbix.com/download.php]("http://www.zabbix.com/download.php")

Here is the ubuntu community page on compiling:
[Compiling Software]("https://help.ubuntu.com/community/CompilingSoftware")

---

### Post by cgroothius on 2008-10-02
can you give me the syntax?  

trying sudo wget [http://www.zabbix.com/download.php](http://www.zabbix.com/download.php) and not having success...

I only have command line available to me...

---

### Post by drs305 on 2008-10-02
> **cgroothius said:**
> can you give me the syntax?  

trying sudo wget [http://www.zabbix.com/download.php](http://www.zabbix.com/download.php) and not having success...

I only have command line available to me...

I was able to download the source and manual with:
```
wget http://prdownloads.sourceforge.net/zabbix/zabbix-1.6.tar.gz?download
wget http://www.zabbix.com/downloads/ZABBIX%20Manual%20v1.6.pdf
```

The install commands are in the manual. Compiling instructions begin around page 41.* There are some fairly specific switches the manual gives to be used with the "./configure" command so I will refer you to the manual for the install instructions.*

---

### Post by Elfy on 2008-10-02
I downloaded it ok with 

```
wget http://prdownloads.sourceforge.net/zabbix/zabbix-1.6.tar.gz?download
```
               
It will download to wherever you are, then extract it with 

```
tar -xvf zabbix-1.6.tar.gz
```

Once that has been done, change into the directory and compile it.

```
cd zabbix-1.6
./configure
make
sudo make install
```

However, I would prefer to use checkinstall as it produces a package which can be manipulated with dpkg - [https://help.ubuntu.com/community/CheckInstall](https://help.ubuntu.com/community/CheckInstall)

```
sudo apt-get install checkinstall
```

then to install the package once make has been run

```
sudo checkinstall
```

There are other options with checkinstall eg auto-apt.


Edit - not to self - refresh page, if you wander off in between starting and finishing.

---

### Post by cgroothius on 2008-10-07
This worked great.  Thanks very much for the assist!

Colin.

---

### Post by cgroothius on 2008-10-07
Looks like I have another question.  Originally I was going to to run
#apt-get install zabbix-frontend-php zabbix-server zabbix-agent

Since we ran wget and downloaded the package then compiled it, how do I complete the "install zabbix-frontend-php zabbix-server zabbix agent" piece?

I see it is not installed as i get apache page not found when trying to reach the app home page.

Any thoughts?

Thanks
C.

---

