---
title: "Canon LBP 2900i i-SENSYS and Ubuntu 9.04 - HowTo - tutorial"
date: 2009-10-10
forum: Hardware
---

### Post by slayer^_^ on 2009-10-10
After months of struggle i finally managed to make this printer work.

Before I go forward with the howto, YES, THIS IS THE "i" model, **_LBP2900i - i-SENSYS_**.
_The "i" model is totally different from the non "i" one and must be installed in a different way._

So, let's go !!

1 ) Be sure to have these important packages installed:

```
sudo apt-get install cups cups-common portreserve
```

2 ) Download the 1.60 driver (don't use the 1.80 one):

```
sudo wget http://files.canon-europe.com/files/soft28622/software/CAPTDRV160.tar.gz
```

3 ) Unpack it:

```
sudo tar xvf CAPTDRV160.tar.gz
```

4 ) Go into the folder:

```
cd ~/CAPTDRV160/driver/debian/
```

5 ) Install the first package:

```
sudo dpkg -i  cndrvcups-common_1.60-1_i386.deb
```

6 ) Install the second one:

```
sudo dpkg -i  cndrvcups-capt_1.60-1_i386.deb
```

7 ) Eventually install any needed dependance

```
sudo apt-get -f install
```

8 ) Restat CUPS - Common Unix Printing System

```
sudo /etc/init.d/cups restart
```

9 ) Now type this:
 
```
sudo tail /var/log/messages
```

10 ) Now this one (we're configuring the printer:

```
/usr/sbin/lpadmin -p LBP2900 -m CNCUPSLBP2900CAPTK.ppd -v ccp:/var/ccpd/fifo0 -E
```

11 ) And this one:

```
sudo /usr/sbin/ccpdadmin -p LBP2900 -o /dev/usb/lp0
```

12 ) Start ccpd:

```
sudo /etc/init.d/ccpd start
```

13 ) Set ccpd to start on boot:

```
sudo update-rc.d ccpd defaults 20
```


Now the printer should work:


The common problem right now is that if the printer is shut down or the system rebooted or whatever else, a new printer called LBP29002 appears and you're not able to print anymore.

Now, there are some ways proposed to solve this problem... some propose to execute some terminal instructions any time you need to use your  printer, some suggest to disable al power management for the printer (but you won't be able to add any new printer. I suggest to:


14 ) Create an .sh file. You'll need to execute it every time your printer is turned on in order to be able to print.

```
gksudo gedit ~/printer.sh
```

a Gedit window will appear and you'll need to paste these strings:
```

#!/bin/bash
echo yourpassword | sudo -S lpadmin -x LBP29002 
echo yourpassword | sudo /etc/init.d/ccpd restart 
echo yourpassword | sudo /etc/init.d/cups restart
```

Of course you'll need to type you administrator password instead of "yourpassword". Then save and quit

15 ) Change the permissions of the .sh file in order to be able to execute it:

```
sudo chmod +x printer.sh
```

The "printer.sh" file is located in your home folder. You can move it wherever you want.

Now, if you turn on your printer and the printer doesn't print and/or another printer called LBP29002 is appeared, just execute the printer.sh file (by double-clicking on in and then choosing execute or execute in terminal) and everything should be ok.

Please note that, with my method, your admin password is contained in the printer.sh file. If you need to hide your password you can hide the text file or edit its permissions... another way is to copy the three instructions of the text file and paste them separately in the terminal every time the printer is turned on.


I'm so happy I finally managed to be able to use this printer under linux... damn it was hard but it worked!!!

Please post your experience...



Disclaimer: Most of the info of this howto were taken [here]("http://www.unixmen.com/linux-distributions/ubuntu/229-installation-canon-lbp2900-on-linux"). The rest is coded by me...

---

### Post by kactusss on 2010-05-08
Hello, firstly =D> for your tutorial.
My english will be bad, sorry i'm french ;)

I have just a litle problem :s, maybe you can help me.
I am on Ubuntu 10.04 (it's the problem ?)

At : 5 ) Install the first package:

I have this error message:

hugo@hugo-desktop:~/Bureau/CAPTDRV160/driver/debian$ sudo dpkg -i  cndrvcups-common_1.60-1_i386.deb
Sélection du paquet cndrvcups-common précédemment désélectionné.
(Lecture de la base de données... 173085 fichiers et répertoires déjà installés.)
Dépaquetage de cndrvcups-common (à partir de cndrvcups-common_1.60-1_i386.deb) ...
dpkg : des problèmes de dépendances empêchent la configuration de cndrvcups-common :
 cndrvcups-common dépend de libcupsys2 (>= 1.1.23) ; cependant :
  Le paquet libcupsys2 n'est pas installé.
dpkg : erreur de traitement de cndrvcups-common (--install) :
 problèmes de dépendances - laissé non configuré
[B]Des erreurs ont été rencontrées pendant l'exécution :
 cndrvcups-common
[/B]

(in french sorry)

If you can help me, i don't know how to solve the problem..

Thanks
Hugo.

---

### Post by slayer^_^ on 2010-05-11
Bonjour !

This guide refers to ubuntu 9.04, it doesn't work with ubuntu 9.10 and with ubuntu 10.04 LTS.

Try the info in this page with both the newer versions of the canon driver

[https://help.ubuntu.com/community/CanonCaptDrv190](https://help.ubuntu.com/community/CanonCaptDrv190)


I'm sorry but I don't have this printer with me in order to test it with the new drivers on the new ubuntu...

Feel free to post your experience...

Au revoir !

---

### Post by kactusss on 2010-05-13
Thank you very much :)
I will try whith this and i post you the result soon ;)

---

