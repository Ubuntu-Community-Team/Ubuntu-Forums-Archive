---
title: "inktjet printer/scanner Dell V313 via usb : no printing nor scanning"
date: 2018-01-18
forum: Hardware
---

### Post by Hankbonk on 2018-01-18
I am running Lubuntu 16.04 LTS on a hp compact 32-bit PC .

I have recently bought a printer scanner : a Dell V313, which I tried to install via usb port and using the printers utility under the lubuntu main menu System Tools .

I know the printer is in fact a Lexmark S305 rebranded by Dell, so when adding the printer, I specified it was a Lexmark printer under which I selected the S300 to S400 option . When trying to print a test page from that printers utility mentioned above, it does not print anything and gives the following printer state : Idle - File "/usr/local/lexmark/v3/bin/printfilter" has insecure permissions (0100775/uid=0/gid=0).

Does anyone know what actions I should take to make this inktjet printer/scanner work ?

---

### Post by pdc on 2018-01-18
is there anything in this thread to help? [https://ubuntuforums.org/showthread.php?t=2082570](https://ubuntuforums.org/showthread.php?t=2082570)

what worked in that was 

```
sudo chmod 755 /usr/local/lexmark/v3/bin
```

```
sudo chgrp root /usr/local/lexmark/v3/bin/printfilter
```

____________________________________________________________

can I just say that Lexmark inkjet printers have been troublesome on linux forums; yes, they did supply a driver; but it was several years ago; and needed tweaking; I understood Lexmark had stopped making inkjet printers a while ago; ....... so this is a second-hand device? Just curious if Dell were now having them manufactured

...... checking on the Dell site they offer[COLOR="#0000FF"] dell-inkjet-09-driver-1.0-1.i386.deb.sh.tar.gz[/COLOR] but the assumption is this the old Lexmark 32bit driver;[COLOR="#0000FF"][/COLOR]

---

### Post by Hankbonk on 2018-01-18
Dear pdc,

I already did the following before I read your post :
> sudo chmod 755 printfilter

When trying to print a test page, I got another error :
> xmessage

The version of Java Runtime Environment (JRE) detected on your system is below the required version.
The required version for Java Runtime Environment (JRE) should be 1.6 or higher


but then I check that JRE :
> $ java -version
openjdk version "1.8.0_151"
OpenJDK Runtime Environment (build 1.8.0_151-8u151-b12-0ubuntu0.16.04.2-b12)
OpenJDK Server VM (build 25.151-b12, mixed mode)


---

### Post by him610 on 2018-01-18
I have an older Dell laserjet that I have successfully configured many times using 
> Generic PCL 5 LF Printer - CUPS+Gutenprint v5.2.11 in Settings>Printers setup utility.
It may work for you; although, you may need to find the correct generic inkjet driver. Make sure you have the correct port specified.

---

### Post by pdc on 2018-01-18
folks always have said the Lexmark lasers were fine to get to run; the inkjets were trickier

---

### Post by Hankbonk on 2018-01-19
That error :
> xmessage

The version of Java Runtime Environment (JRE) detected on your system is below the required version.
The required version for Java Runtime Environment (JRE) should be 1.6 or higher

has a wine format :

[ATTACH=CONFIG]278241[/ATTACH] 

So my question is : is there another JRE running under wine ?

---

### Post by Hankbonk on 2018-01-20
I have found that according to someone who had the same problem I have that I needed to install Java 7 instead of my Java 8 to get that JRE error out of the way .  So I did, but now I get this :

[ATTACH=CONFIG]278264[/ATTACH]

Someone any suggestions ? As you can see on that screenshot, the printer in the printers utility shows "connected to local host" .

---

### Post by Hankbonk on 2018-02-08
I need to install this printer because the scanner worked before, not the printing, so please advise !

Now the scanner doesn't work either anymore, what have I done wrong ?

---

