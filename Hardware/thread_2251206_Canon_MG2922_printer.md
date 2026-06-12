---
title: "Canon MG2922 printer"
date: 2014-11-02
forum: Hardware
---

### Post by cpeters1965 on 2014-11-02
Good evening all,
      Have a older desktop running 14.04 Ubuntu. My HP printer died so SO got me a Canon MG2922 printer to replace with. I cannot seem to get it to print for love nor money. Is there a set of drivers for the 2900 series or am I stuck?

---

### Post by pdc on 2014-11-07
Hi there cpeters; sorry for the 5 day delay; I hope you are still out there!

Yes, Canon supply linux drivers for your printer; (they supply them in rpm and debian packages and in source code) 

go here [http://support-asia.canon-asia.com/contents/ASIA/EN/0100626502.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100626502.html) and click to download and SAVE what will be cnijfilter2-5.00-1-deb.tar.gz

if you open a terminal; then copy each command below; line by line; pasting each line into a terminal; and hitting the ENTER key after each paste ..................

```
cd Downloads
tar -zxvf cnijfilter2-5.00-1-deb.tar.gz
cd cnijfilter2-5.00-1-deb
./install.sh

```


and that should install the printer driver; are you usb connected? 

-_________________________

Canon also supply [COLOR="#0000FF"]ScanGearMP[/COLOR] to run the scanner

get the programme here [http://support-asia.canon-asia.com/contents/ASIA/EN/0100627102.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100627102.html)

and you will get scangearmp2-3.00-1-deb.tar.gz

so close the terminal and then open it again and the commands are 

cd Downloads
tar -zxvf scangearmp2-3.00-1-deb.tar.gz
cd scangearmp2-3.00-1-deb
./install.sh

and crucially, run [COLOR="#0000FF"]ScanGearMP[/COLOR] with the terminal command of > [COLOR="#FF0000"]scangearmp[/COLOR]

---

### Post by Bucky Ball on 2014-11-07
> **pdc said:**
> 
```
cd Downloads

```



Just a note and to avoid confusion: This command depends on the fact you have downloaded it to the Downloads folder. ;)

If not, change it to:

```

cd /path/to/the/cannon_driver_directory
```

i.e. The path to the directory you downloaded it to. [And here's another way.]("http://ubuntuhandbook.org/index.php/2013/07/canon-drivers-for-ubuntu-and-linux-mint/")

---

### Post by Craig_Jones on 2014-12-06
> **pdc said:**
> Hi there cpeters; sorry for the 5 day delay; I hope you are still out there!

Yes, Canon supply linux drivers for your printer; (they supply them in rpm and debian packages and in source code) 

go here [http://support-asia.canon-asia.com/contents/ASIA/EN/0100626502.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100626502.html) and click to download and SAVE what will be cnijfilter2-5.00-1-deb.tar.gz

if you open a terminal; then copy each command below; line by line; pasting each line into a terminal; and hitting the ENTER key after each paste ..................

```
cd Downloads
tar -zxvf cnijfilter2-5.00-1-deb.tar.gz
cd cnijfilter2-5.00-1-deb
./install.sh

```


and that should install the printer driver; are you usb connected? 

-_________________________

Canon also supply [COLOR=#0000FF]ScanGearMP[/COLOR] to run the scanner

get the programme here [http://support-asia.canon-asia.com/contents/ASIA/EN/0100627102.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100627102.html)

and you will get scangearmp2-3.00-1-deb.tar.gz

so close the terminal and then open it again and the commands are 

cd Downloads
tar -zxvf scangearmp2-3.00-1-deb.tar.gz
cd scangearmp2-3.00-1-deb
./install.sh

and crucially, run [COLOR=#0000FF]ScanGearMP[/COLOR] with the terminal command of

I got this to work just now, but I had to run scangearmp2 in terminal instead. Figured it out once I went looking for the package ins the synaptic package manager. Thanks for the above, it helped a lot!

---

### Post by pdc on 2014-12-07
glad it works; thanks for the "heads up": about the scangearmp2 command ..........always something new! Enjoy the printer

---

