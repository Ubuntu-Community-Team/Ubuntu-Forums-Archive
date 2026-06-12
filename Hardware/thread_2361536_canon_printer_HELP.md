---
title: "canon printer HELP"
date: 2017-05-17
forum: Hardware
---

### Post by gorgut2 on 2017-05-17
[INDENT]Hello. Last week I decided to install latest Ubuntu (not LTS) and wipe windows...now I am new at Ubuntu
PROBLEM my printer is not working now, a canon IP1700 USB.
Can someone give some step by step instructions on how to make this work? Perhaps a different driver that can be manually loaded?
Older recommendations from this forum does not work now.

Thanks,
Vitalii[/INDENT]

---

### Post by pdc on 2017-05-19
Hi gorgut; welcome to the ubuntu forums; you have done very well to keep a 10yr old printer going so well; linux has come a long way in 10yrs; and many companies now easily support devices with drivers; Canon didn't release a linux driver for the ip1700 but I saw reference that the ip1900 from Canon works: you need to download and installed the common driver then the specific driver;

COMMON driver: go here [http://support-asia.canon-asia.com/contents/ASIA/EN/0100159003.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100159003.html) and click to download and select OPEN for what will be cnijfilter-common_3.00-1_i386.deb 
SPECIFIC driver: go here [http://support-asia.canon-asia.com/contents/ASIA/EN/0100159101.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100159101.html) and click to download and select OPEN for what will be cnijfilter-ip1900series_3.00-1_i386.deb

....... OPEN should mean select Software Manager or G Debi Installer and they will install the packages 

............ have you got a 64bit system? .... because these are 32bit files ....... perhaps tell us before installing the above

_________________--

another solution is to install Turboprint [http://www.turboprint.info/](http://www.turboprint.info/) their drivers are very good: I could find your ip1700 supported ...... they charge you so they can put food on the table

---

### Post by Bucky Ball on 2017-05-19
Welcome. As above. As those files you're downloading are .deb files you should only need to double click them and they will install automatically via Software or Gdebi. You will then need to 'Add Printer' in 'Printers' menu. This is easy enough. Follow your nose and when asked, select the driver you just installed, the ip1900 by what pdc has said. 

Good luck.

---

### Post by gorgut2 on 2017-05-19
Thank you for your support. I have a 64bit system. Yesterday I tried to install drivers _i386 but terminal said that my system does not suppport that.

---

### Post by pdc on 2017-05-19
yes; as computing advances, it may leave things behind. 

[SIZE=4]***If you do what is below, can you delete any entries in your PRINTERS folder before you start please?*** [/SIZE]....... if you type PRINTERS in your DASH, it should find the folder 

.... ie if there is an entry for the IP1700, please remove it .........

_______________________________________________

1) You can use a command to force the install; 

and

2) you will likely need symbolic links; 

so if you open a terminal; 

let's install those links first of all ......... please COPY & PASTE these commands ..... right-click in the terminal, and a MENU should appear and you can select PASTE ..............

 ```
sudo ln -s /usr/lib /usr/lib64
``` .... you will need your sudo password ...........

 ```
sudo ln -s /usr/local/lib /usr/local/lib64
```


you then need to "get inside" the Downloads folder so firstly open the terminal: .......... that is assuming you downloaded and saved the two necessary files .......and they ended up in the DOWNLOADS folder ...........

then ```
cd Downloads
``` ..... hit the ENTER key each time after a paste 

then ```
sudo dpkg -i --force-all cnijfilter-common_3.00-1_i386.deb
```

then ```
sudo dpkg -i --force-all cnijfilter-ip1900series_3.00-1_i386.deb
``` .... that should install the drivers .......

that should prompt ubuntu to create a new entry in your PRINTERS folder ......... can you print yet?

---

