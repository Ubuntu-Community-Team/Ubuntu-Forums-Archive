---
title: "Installing Canon MG5600 series Printer/Scanner/Copier"
date: 2015-02-01
forum: Hardware
---

### Post by greg_arbour on 2015-02-01
For anyone who might be installaing a Canon MG5600 series printer I hope this will save you the 8 hours I spent trying to find a solution.  I have an MG5620 and am using a wireless connection to Lubuntu.  Both printing and scanning work.  In addtion to the proceedures below I installed cnijfilter2-5.00-1.i386.rpm using Alien, but nothing worked until I found this gem on [http://forum.ubuntuusers.de/topic/canon-pixma-mg-5650/#post-7324948](http://forum.ubuntuusers.de/topic/canon-pixma-mg-5650/#post-7324948)  All of the credit goes to the original author!!!

Canon Pixma MG5600 Series Scanner Installation


Start terminal and copy/paste the following commands:

1)    Create the download directory and switch to it:
    ```
mkdir -p ~/Downloads/canon/pixma_mg5600/
```

2)    Change the active directory:
    ```
cd ~/Downloads/canon/pixma_mg5600/
```

3)    Download the archive:
    ```
wget http://gdlp01.c-wss.com/gds/1/0100006271/01/scangearmp2-3.00-1-deb.tar.gz
```

4)    Unpack the archive:
    ```
tar -xzvf scangearmp2*.tar.gz
```

5)    Change the active directory:
    ```
cd scangearmp2*/packages/
```

6)    Check if Ubuntu is installed in 64 bit or 32:
    ```
uname -m
```

7)    Install the appropriate package:
    # for 64 bit:
    ```
sudo dpkg -i scangearmp2*amd64.deb
```
    # for 32 bit:
    ```
sudo dpkg -i scangearmp2*i386.deb
```

8)    Test your scanner:
    ```
scangearmp2
```

---

### Post by coffeecat on 2015-02-01
Not a Forum Feedback & Help thread.

*Thread moved to **Hardware**.*

---

### Post by pdc on 2015-02-01
thanks Greg; the kind person whose post you read; could do it more simply;

.............using the install script that Canon provides.................that automates the install.....................

________________

[B]PRINTER DRIVER
[/B]
so one could get the printer driver from here [http://support-asia.canon-asia.com/contents/ASIA/EN/0100626502.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100626502.html) and it comes down as [COLOR="#008000"]cnijfilter2-5.00-1-deb.tar.gz[/COLOR]

so the commands would be:

[COLOR="#FF0000"]cd Downloads  [/COLOR]                                     (where it should end up by default..................)
[COLOR="#FF0000"]tar -zxvf cnijfilter2-5.00-1-deb.tar.gz
cd cnijfilter2-5.00-1-deb
./install.sh[/COLOR]

..................so that last command runs the install script and it should do all for you ............

________________

SCANNER DRIVER

comes from here [http://support-asia.canon-asia.com/contents/ASIA/EN/0100627102.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100627102.html) and comes down as [COLOR="#008000"]scangearmp2-3.00-1-deb.tar.gz[/COLOR]

so commands in a terminal are

[COLOR="#FF0000"]cd Downloads
tar -zxvf scangearmp2-3.00-1-deb.tar.gz
cd scangearmp2-3.00-1-deb
./install.sh[/COLOR]

and one runs it with ```
scangearmp2
```

_________________

you did very well to document all you did; and it worked well for you; 

however as the intent is for a newcomer to find help; I document the above here; as I think it is simpler than the thread you used

---

### Post by mats-gbproject on 2015-08-14
scangearmp2? Is this really the only option?!
I can only scan low resolution images...
Is it not possible to connect this with simple scan?

---

### Post by botux2 on 2016-06-18
> **mats-gbproject said:**
> scangearmp2? Is this really the only option?!
I can only scan low resolution images...
Is it not possible to connect this with simple scan?

You can add the sane dev ppa : [https://launchpad.net/~rolfbensch/+archive/ubuntu/sane-git](https://launchpad.net/~rolfbensch/+archive/ubuntu/sane-git)
via : 
```
sudo add-apt-repository ppa:rolfbensch/sane-git
sudo apt update
sudo apt upgrade
```

Then re-install your printer the usual way.
The printer and scanner should be working without the crap apps from canon !

Cf : [https://askubuntu.com/questions/641261/how-can-i-link-my-canon-mg5650-scanner-to-ubuntu?answertab=votes#tab-top](https://askubuntu.com/questions/641261/how-can-i-link-my-canon-mg5650-scanner-to-ubuntu?answertab=votes#tab-top)

---

