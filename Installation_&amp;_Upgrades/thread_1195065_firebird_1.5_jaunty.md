---
title: "firebird 1.5 jaunty"
date: 2009-06-23
forum: Installation &amp; Upgrades
---

### Post by webik on 2009-06-23
Hi

I've got problem with firebird 1.5 instalation on Ubuntu Server jaunty.

I downloaded proper version 1.5.4 from official page ([www.firebirdsql.org](www.firebirdsql.org)), unpack archive and run install script.

After that I try:

```

sudo /etc/init.d/firebird start
Starting Firebird server: start-stop-daemon: Unable to start /opt/firebird/bin/fbmgr.bin: No such file or directory (No such file or directory)

```

but 

```
ls -lah /opt/firebird/bin/fbmgr.bin
-rwxrwxrwx 1 root root 16K 2007-01-30 10:16 /opt/firebird/bin/fbmgr.bin

```

I've got no idea??

I also tried to install using packages from launchpad and I also getting errors:
```


(Odczytywanie bazy danych ... 18092 plików i katalogów obecnie zainstalowanych.)                                             
Przygotowanie do zast&#261;pienia firebird1.5-super 1.5.4.4910rel-6 (wykorzystuj&#261;c firebird1.5-super_1.5.4.4910rel-6_amd64.deb) ...
 * Firebird 1.5 server manager not running.                                                                                   
Rozpakowanie pakietu zast&#281;puj&#261;cego firebird1.5-super ...                                                                      
Configurnig firebird1.5-super (1.5.4.4910rel-6) ...                                                                        
dpkg: error during processing firebird1.5-super (--install):                                                                       
 subprocess post-installation script returned error exit status 1                                                                       
Wyst&#261;pi&#322;y b&#322;&#281;dy podczas przetwarzania:                                                                                        
 firebird1.5-super 

```

I translate only error message (I've got polish locale on my machine)

Thanks in advance

webik

---

