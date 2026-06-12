---
title: "Canon LBP 660 &amp; Ubuntu 8.10 Intrepid HOWTO"
date: 2009-03-26
forum: Hardware
---

### Post by joseluisgomez on 2009-03-26
It works!

1. Download [http://www.boichat.ch/nicolas/lbp660/lbp660-0.3.1.tar.gz](http://www.boichat.ch/nicolas/lbp660/lbp660-0.3.1.tar.gz)
Thanks to Nicolas Boichat for make the driver.

```
wget http://www.boichat.ch/nicolas/lbp660/lbp660-0.3.1.tar.gz
```

2. Unzip 

```
tar xvfz lbp660-0.3.1.tar.gz
``` 

3. Replace content of file lbp660-0.3.1/restartcups.sh with

```
#!/bin/bash
/etc/init.d/cups restart
echo "Waiting 5 seconds..."
sleep 5
```

4. Remove file /usr/share/cups/model if exits, create the folder /usr/share/cups/model and copy Canon-LBP-660-lbp660.ppd into it.

```
sudo rm /usr/share/cups/model 
sudo mkdir /usr/share/cups/model
sudo cp lbp660-0.3.1/ppd/Canon-LBP-660-lbp660.ppd /usr/share/cups/model
```

5. Deactivate apparmor for cups

```
sudo aa-complain cupsd
```

6. Install cups driver with make cups-install-660-a4

```
cd lbp660-0.3.1
sudo make cups-install-660-a4
```


Espero que les ayude 
Luck

---

### Post by joseluisgomez on 2009-03-26
Simplest way. Create a file install.sh with this content:

```
wget http://www.boichat.ch/nicolas/lbp660/lbp660-0.3.1.tar.gz
tar xvfz lbp660-0.3.1.tar.gz
echo '#!/bin/bash' > lbp660-0.3.1/restartcups.sh
echo '/etc/init.d/cups restart' >> lbp660-0.3.1/restartcups.sh
echo 'echo "Waiting 5 seconds..."' >> lbp660-0.3.1/restartcups.sh
echo 'sleep 5' >> lbp660-0.3.1/restartcups.sh
sudo rm /usr/share/cups/model 
sudo mkdir /usr/share/cups/model
sudo cp lbp660-0.3.1/ppd/Canon-LBP-660-lbp660.ppd /usr/share/cups/model
sudo aa-complain cupsd
cd lbp660-0.3.1
sudo make cups-install-660-a4
```

and execute it.

/bin/bash install.sh

---

### Post by stardustdelux on 2009-07-21
are these drivers still working in ubuntu 9.10? followed this excellent howto but my printer doesn't show any reaction :(

---

### Post by ernetgt on 2011-08-08
Any chance it can work with Ubuntu 10.4 ???

---

### Post by rapattack1 on 2013-02-08
Hi i know this is old but it is the closest to my situation. I got about 3/4 of the way through the commands (the 2nd post) but it started to produce errors like not being able to make the dir or that it doesn't exist. I persisted anyway and now cups has a icon in it with the printer model but no test print happens. Is anyone still using this printer? I am using Ubuntustudio 12.04

---

### Post by Bucky Ball on 2013-02-08
No point. This thread has been inactive for nearly a year and a half. To improve your chances of help please post a new thread regarding your issue.

***Thread Closed***

***Reason***: Necromancy. Old thread put to bed.

---

