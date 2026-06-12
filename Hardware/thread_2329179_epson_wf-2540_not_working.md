---
title: "epson wf-2540 not working"
date: 2016-06-28
forum: Hardware
---

### Post by Robert_Litolff on 2016-06-28
hi, im new to this sight, ive been reading alot and tried some  answers to printer problems. none have worked for me.. im not very  a experienced ubuntu user.. i have the new 16.04 LTS & can not get my  printer to work, it worked in my last version 12.0 .. any chance anyone could help me out? im simply out of options w/  my knowledge of this...first there was no printer icon in my hardware. i have gotten that back, but cant add a new printer,

---

### Post by Robert_Litolff on 2016-06-28
screen shot of what i get




[ATTACH=CONFIG]269847[/ATTACH][ATTACH=CONFIG]269848[/ATTACH]

---

### Post by QDR06VV9 on 2016-06-28
[Notice]
In order to install these drivers, you need to install LSB package (version 3.2 or later) beforehand.

Ubunbu:
```
sudo apt-get install lsb
```
Then the driver should be here:[http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=45427&DSCCHK=dbd222ef019e11433beed9d553bd567029c06dd8](http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=45427&DSCCHK=dbd222ef019e11433beed9d553bd567029c06dd8)
Make sure everything match's your printer. Edit: I like to use Gdebi to install all .debs
```
sudo apt install gdebi
```

---

### Post by Robert_Litolff on 2016-06-28
```

bob@ubuntu:~$ sudo apt-get install lsb
[sudo] password for bob: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package lsb is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'lsb' has no installation candidate 
this is what i got...? 
```

---

### Post by QDR06VV9 on 2016-06-28
I did not know they had removed that for 16.04???
Refer to this site:[http://lifeofageekadmin.com/install-epson-pc-fax-linux-driver-wf-2540/](http://lifeofageekadmin.com/install-epson-pc-fax-linux-driver-wf-2540/)

---

### Post by Linuxisfast on 2016-06-29
lsb has been removed from Ubuntu repos. Best solution is to add trusty repos and install lsb from there and then remove the repo. I and many others have done that for Epson printers and Google Earth with no issues, here is the launchpad link to the missing lsb issue. [https://bugs.launchpad.net/ubuntu/+source/lsb/+bug/1536353](https://bugs.launchpad.net/ubuntu/+source/lsb/+bug/1536353)

---

### Post by QDR06VV9 on 2016-06-29
> **Linuxisfast said:**
> lsb has been removed from Ubuntu repos. Best solution is to add trusty repos and install lsb from there and then remove the repo. I and many others have done that for Epson printers and Google Earth with no issues, here is the launchpad link to the missing lsb issue. [https://bugs.launchpad.net/ubuntu/+source/lsb/+bug/1536353](https://bugs.launchpad.net/ubuntu/+source/lsb/+bug/1536353)

Thanks for the updated information..and the link.;)
I hope I have not discouraged the OP.
Regards

---

### Post by QDR06VV9 on 2016-06-29
So if you have not done this already To Add the trusty repositories.
Open a terminal and type the following command:
```
gksudo gedit /etc/apt/sources.list

```
        [B]Add the following line at the bottom of the file:
[/B]
      ```
  deb http://archive.ubuntu.com/ubuntu/ trusty main 
```

Save the file && Run the command:        

        ```
sudo apt-get update
```

Install lsb with

    ```
sudo apt-get install lsb
```
Install the printer driver. Run:

   ```
 sudo dpkg -i yourdriver.deb
```
    **Remove the trusty repos from sources.list**
Open a terminal and type the following command:

       ```
 gksudo gedit /etc/apt/sources.list
```

        [B]Remove the following line at the bottom of the file:
[/B]
        ```
deb http://archive.ubuntu.com/ubuntu/ trusty main

```

Save again && Run:       

      ```
  sudo apt-get update
```
Add your printer by going into Printers > Add.

NOTE: You may have to manually select the driver from a list.
Hope this useful.

---

### Post by Linuxisfast on 2016-06-30
lsb is back in repos, just do sudo apt install lsb and you are set.

---

