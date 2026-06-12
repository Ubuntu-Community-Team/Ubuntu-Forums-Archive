---
title: "Error everytime I run update!"
date: 2008-10-02
forum: General Help
---

### Post by markedmanner on 2008-10-02
I am using Hard Heron and every single time I download updates they seemed to install but once it is done I get the following error message. I know it has to do with a printer driver. How can I fix this error so it doesnt happen anymore? When I was installing my printer driver I remember installing it twice accidentally. I dont know if that has to do with it or not. any help is appreciated.

[IMG]http://img231.imageshack.us/img231/4715/screenshotkb1.png[/IMG]

---

### Post by Ryadt on 2008-10-02
Try```
sudo dpkg --configure -a
```

---

### Post by markedmanner on 2008-10-02
> **Ryadt said:**
> Try```
sudo dpkg --configure -a
```

when I did I got:

Setting up cupswrapperhl2070n (2.0.1-2) ...
ERROR : Brother LPD filter is not installed.
/usr/local/Brother/cupswrapper/cupswrapperHL2070N-2.0.1: 64: cannot create /usr/share/cups/model/HL2070N.ppd: Directory nonexistent
chmod: cannot access `/usr/local/Brother/inf/brHL2070Nrc': No such file or directory
chmod: cannot access `/usr/local/Brother/inf': No such file or directory
 * Restarting Common Unix Printing System: cupsd                         [ OK ] 
cp: cannot stat `/usr/share/cups/model/HL2070N.ppd': No such file or directory
dpkg: error processing cupswrapperhl2070n (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 cupswrapperhl2070n

---

### Post by Ryadt on 2008-10-02
Try```
sudo apt-get install -f
```

---

### Post by markedmanner on 2008-10-02
> **Ryadt said:**
> Try```
sudo apt-get install -f
```

I got this:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up cupswrapperhl2070n (2.0.1-2) ...
ERROR : Brother LPD filter is not installed.
/usr/local/Brother/cupswrapper/cupswrapperHL2070N-2.0.1: 64: cannot create /usr/share/cups/model/HL2070N.ppd: Directory nonexistent
chmod: cannot access `/usr/local/Brother/inf/brHL2070Nrc': No such file or directory
chmod: cannot access `/usr/local/Brother/inf': No such file or directory
 * Restarting Common Unix Printing System: cupsd                                cp: cannot stat `/usr/share/cups/model/HL2070N.ppd': No such file or directory
dpkg: error processing cupswrapperhl2070n (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 cupswrapperhl2070n
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by Ryadt on 2008-10-02
Try```
sudo apt-get autoclean
``````
sudo apt-get autoremove
```

---

### Post by markedmanner on 2008-10-11
I have totally uninstalled CUPS and tried deleting my printers and reinstalling. I am still getting the same error. If anyone can advise me on how to uninstall cupswrapperhl2070n it would be of great assistance. All I want to do is uninstall cupswrapperhl2070n which seems to be causing the problem.

---

### Post by plucky on 2008-10-11
> **markedmanner said:**
> I have totally uninstalled CUPS and tried deleting my printers and reinstalling. I am still getting the same error. If anyone can advise me on how to uninstall cupswrapperhl2070n it would be of great assistance. All I want to do is uninstall cupswrapperhl2070n which seems to be causing the problem.

You probably need to install it properly first.Try to follow this [tutorial](http://ubuntuforums.org/showthread.php?t=590793) for installing Brother printers,but adjust the name of the .deb package to suit the one you are installing.

Is it 32 bit or 64 bit system install?
Are you on 8.04.1 Hardy Heron?


In Hardy,the Brother printer dirvers are packaged in Synaptic.See this [link](https://wiki.ubuntu.com/BrotherDriverPackaging)


Good Luck

---

### Post by Ryadt on 2008-10-11
Try to see if this will help```
sudo dpkg -P cupswrapperhl2070n
```

---

