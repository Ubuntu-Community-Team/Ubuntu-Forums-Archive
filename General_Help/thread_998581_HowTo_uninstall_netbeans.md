---
title: "HowTo uninstall netbeans ?"
date: 2008-11-30
forum: General Help
---

### Post by megazayed on 2008-11-30
Hello 
i installed netbeans 6.5 in ubuntu 8.4, but i does not work fine so i want to uninstall it,
i installed netbeans in /opt , so when i wrote this command to uninstall it :
/opt/netbeans-6.5/uninstall.sh 
shell tells me :
Configuring the installer...
Searching for JVM on the system...
Extracting installation data...
Running the installer wizard...

and nothing else !!!!

How can i overcome this problem ?!!

---

### Post by megazayed on 2008-12-01
i'm still waiting for reply !!!!!

---

### Post by taurus on 2008-12-01
Did you log in as root when you ran that command to uninstall it?  Otherwise, try putting sudo in front of the command.

```
sudo /opt/netbeans-6.5/uninstall.sh 
```

---

### Post by megazayed on 2008-12-01
i tried :
sudo /opt/netbeans-6.5/uninstall.sh

but it gives me the same result !!!

---

### Post by megazayed on 2008-12-01
i'm wondring why when i run :

sudo /opt/netbeans-6.5/uninstall.sh

shell tells me running installer and nothing happend !!

that happens in every uninstall.sh and install.sh also 

plz me 
i'm about to re-install the system

---

### Post by Joeb454 on 2008-12-01
How long have you left it at that prompt?

---

### Post by megazayed on 2008-12-01
finally i found the reason 
i have to write command in this way :
sudo /opt/netbeans-6.5/uninstall.sh --javahome /opt/jdk1.6.0_05/

becouse i have installed jdk in /opt

thanks all

---

### Post by LepeKaname on 2009-09-27
Mine was located at: /usr/local/share/netbeans-6.5/uninstall.sh

---

### Post by vhof on 2009-11-04
My NetBeans 6.5 was in /home/my_username/netbeans-6.5.1
so just 
```
cd ~/netbeans-6.5.1
```
and 
```
./uninstall.sh
```

---

