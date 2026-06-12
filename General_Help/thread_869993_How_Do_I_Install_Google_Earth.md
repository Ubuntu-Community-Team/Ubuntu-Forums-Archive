---
title: "How Do I Install Google Earth?"
date: 2008-07-25
forum: General Help
---

### Post by Killtodie on 2008-07-25
The linux version downloads a .bin file and I cant do anything with it...

---

### Post by gimlithedwarf on 2008-07-25
open a terminal and type 
```

chmod +x *filename.bin*
./*filename.bin*

```

you dont have to re-type chmod +x every time, because doing it once flags the file as executable from then on you can just execute by using the second line ./filename.bin (where filename is the name of the file you want to execute)

---

### Post by LowSky on 2008-07-25
i would instal the menibuntu repos, makes things easier
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

then go to Synaptic Package manager and search for google earth and install and enjoy

---

### Post by Seisen on 2008-07-25
You can also add the Medibuntu repository and install it.

[https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

---

### Post by Killtodie on 2008-07-25
> **gimlithedwarf said:**
> open a terminal and type 
```

chmod +x *filename.bin*
./*filename.bin*

```

you dont have to re-type chmod +x every time, because doing it once flags the file as executable from then on you can just execute by using the second line ./filename.bin (where filename is the name of the file you want to execute)

sorry. total noob. its on the desktop, how do I point to it?

---

### Post by gimlithedwarf on 2008-07-25
killtodie:
go applications->accesories->terminal and type
```

cd /home/*username*/Desktop/
chmod +x *filename.bin*
./*filename.bin*

```

where filename.bin is the name of the file and username is the username of the user trying to execute the file

---

### Post by Killtodie on 2008-07-25
> **Seisen said:**
> You can also add the Medibuntu repository and install it.

[https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

i added it, google earth doesnt show up in the installer

---

### Post by Killtodie on 2008-07-25
THanks... forgot ubuntu is case sensitive

---

### Post by steveneddy on 2008-07-25
> **Killtodie said:**
> The linux version downloads a .bin file and I cant do anything with it...

It's in the repos.

Just install it from there.

---

### Post by drs305 on 2008-07-25
Install Medibuntu Repository from [https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu"):

For Hardy:
```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

```

Install Google Earth (this is a metapackage, no version number required. current version 4.3):
```
sudo apt-get install googleearth
```

---

