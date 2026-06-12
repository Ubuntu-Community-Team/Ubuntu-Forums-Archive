---
title: "Install Google Earth"
date: 2008-07-27
forum: General Help
---

### Post by Tex786 on 2008-07-27
Hi,

I saw a post from 2006 on how to install google earth. I tryed to do that running ubuntu 8.04 but nothing happend.

How do I install this app today?

thanks

---

### Post by Ryadt on 2008-07-27
Add Medibuntu to your repos.
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
Then do in terminal ```
sudo apt-get install googleearth
```

---

### Post by Tex786 on 2008-07-27
I put int he code from ubuntu from that page and after that i put in the code you gave me for google earth. it said this

"E: Couldn't find package googleearth
"...

can you fix that?

---

### Post by Ryadt on 2008-07-27
Try ```
sudo apt-get update
```
```
sudo apt-get upgrade
```
```
sudo apt-get install googleearth
```

---

### Post by IusedTObeSOMEONEelse on 2008-07-28
trying to install google earth, but I can not seem to get the medibuntu repo right and also need mps codecs so amarok will play music. I have tried to follow the thread for medibuntu install but sources list won't open. Maybe I have forgotten the correct codes (been away for a year) Thanks

---

### Post by Ryadt on 2008-07-28
> **MustangSallydd said:**
> trying to install google earth, but I can not seem to get the medibuntu repo right and also need mps codecs so amarok will play music. I have tried to follow the thread for medibuntu install but sources list won't open. Maybe I have forgotten the correct codes (been away for a year) Thanks

I take it that you are using Hardy.```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
```
```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```
```
sudo apt-get install libdvdcss2
```
```
sudo apt-get install w32codecs
```

---

### Post by IusedTObeSOMEONEelse on 2008-07-28
> **Ryadt said:**
> I take it that you are using Hardy.```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
```
```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```
```
sudo apt-get install libdvdcss2
```
```
sudo apt-get install w32codecs
```
[B]
After all that I am getting this:[/B]
it [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-proposed/universe Sources
W: Failed to fetch [http://packages.medibuntu.org/dists/hardy/free/binary-i386/Packages.gz](http://packages.medibuntu.org/dists/hardy/free/binary-i386/Packages.gz)  404 Not Found [IP: 87.98.249.30 80]

W: Failed to fetch [http://packages.medibuntu.org/dists/hardy/non-free/binary-i386/Packages.gz](http://packages.medibuntu.org/dists/hardy/non-free/binary-i386/Packages.gz)  404 Not Found [IP: 87.98.249.30 80]

E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by jonian_g on 2008-07-28
Get the .bin installer from here:

[http://earth.google.com/download-earth.html](http://earth.google.com/download-earth.html)

Then open a terminal and navigate to the folder you saved the file and type:

```
./GoogleEarthLinux.bin
```

to install it for a single user (it installs in your /home folder)

To install it globaly (for all users):

```
sudo ./GoogleEarthLinux.bin
```

---

### Post by gjoellee on 2008-07-28
the [COLOR=Blue]_***easiest***_[/COLOR] way to install Google Earth and many other apps is using Ultamatix...download it here: [http://linux.softpedia.com/progDownload/Ultamatix-Download-39892.html](http://linux.softpedia.com/progDownload/Ultamatix-Download-39892.html)'
i would actually recommend Ultamatix for people who likes graphical installers....

---

### Post by compiledkernel on 2008-07-28
Automatix reborn, and really not all that necessary with mediubuntu repos enabled, easier and less hassle than depending on another application layer to handle installations for you.

---

