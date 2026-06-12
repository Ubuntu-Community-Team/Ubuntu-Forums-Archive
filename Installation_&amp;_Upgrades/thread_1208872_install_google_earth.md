---
title: "install google earth"
date: 2009-07-09
forum: Installation &amp; Upgrades
---

### Post by burrhead1 on 2009-07-09
I have been trying to install Google Earth without any success. I download the Linux version of GE and it appears as a binary file icon on my desktop. When I try to open the file a get a message that "the file is of unknown type"  Also I have tried using the Synaptics Package manger and the file seems to download but I cannot find it in Application, Places or System. Any advise on how to install Google Earth would be appreicated.

---

### Post by wojox on 2009-07-09
Open a terminal:

Go to where the file is 

```
chmod +x GoogleEarthLinux.bin
```

Then

```
./GoogleEarthLinux.bin
```

Then look in Applications > Internet

---

### Post by blur xc on 2009-07-09
Also, in case you hit the same bug as I did- [http://ubuntuforums.org/showpost.php?p=7491640&postcount=1](http://ubuntuforums.org/showpost.php?p=7491640&postcount=1)

the solution- [http://ubuntuforums.org/showpost.php?p=7501478&postcount=6](http://ubuntuforums.org/showpost.php?p=7501478&postcount=6)

BM

---

### Post by burrhead1 on 2009-07-09
> **wojox said:**
> Open a terminal:

Go to where the file is 

```
chmod +x GoogleEarthLinux.bin
```Then

```
./GoogleEarthLinux.bin
```Then look in Applications > Internet

Opened a terminal and cut/pasted in the above and got "No such file or directory exists."

How do I "to where file is".

---

### Post by burrhead1 on 2009-07-10
For what its worth I easily installed Google Earth using instructions at the following web site. IF yo'u get a very pale blue screen when you go to a location, you will need to uncheck the Show Atmosphere option under View.



[http://tombuntu.com/index.php/2009/03/20/how-to-install-google-earth-5-on-ubuntu/](http://tombuntu.com/index.php/2009/03/20/how-to-install-google-earth-5-on-ubuntu/)

---

### Post by Freezing on 2009-07-10
did u by any chance change the name of the file?

open terminal type

chmod +x file.bin <-(locate the file /home/.... )
then type just the directory /home/............/Desktop/GoogleEarthLinux.bin (or whatever you named the file)

There should be instructions on the web page too.
and thats about it. :)

---

