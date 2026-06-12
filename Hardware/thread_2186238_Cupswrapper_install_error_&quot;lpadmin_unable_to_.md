---
title: "Cupswrapper install error: &quot;lpadmin: unable to connect to server: Connection refused&quot;"
date: 2013-11-06
forum: Hardware
---

### Post by mr. tibbs on 2013-11-06
Printer: Brother hl 2240
 Release: Ubuntu 12.04 LTS 64 bit
 Machine: Lenovo x120e
 

 When I try to install the cupswrapper thing (using this guide: [http://ubuntuforums.org/showthread.php?t=590793&highlight=lpadmin%3A+unable+connect+server](http://ubuntuforums.org/showthread.php?t=590793&highlight=lpadmin%3A+unable+connect+server)), I receive the following error:
 

 ```

 Preparing to replace cupswrapperhl2240:i386 2.0.4-2 (using cupswrapperHL2240-2.0.4-2.i386.deb) ...
 lpadmin: Unable to connect to server: Connection refused
 Unpacking replacement cupswrapperhl2240:i386 ...
 Setting up cupswrapperhl2240:i386 (2.0.4-2) ...
 lpinfo: Connection refused
 lpinfo: Connection refused
 lpinfo: Connection refused
 lpadmin: Unable to connect to server: Connection refused
 
```
 

 Please help!

---

### Post by steeldriver on 2013-11-06
Is the cups service running? is it listening on the expected port?

```

service cups status

sudo netstat -nlp | grep cupsd

```

---

### Post by mr. tibbs on 2013-11-06
Hmm. I dunno. I typed the above code into the terminal and received:

```
cups: unrecognized service
```

I'm a total noob. I have no idea what that means, or what your question about the service running and/or listening means. ;(

---

### Post by logan17 on 2014-08-10
Hey guys I was just going through this process and got this error after installing the driver installer from here for my brother printer:[http://support.brother.com/g/b/productsearch.aspx?c=us&lang=en&content=dlI](http://support.brother.com/g/b/productsearch.aspx?c=us&lang=en&content=dlI) simply did: apt-get install cupsdas root and it installed fine, I am on a debian box but I imagine it would work fine on Ubuntu as well.So if anyone googling this has similar error make sure you have cupsd installed.

---

### Post by logan17 on 2014-08-10
command: "apt-get install cupsd" sorry formatting got messed up

---

