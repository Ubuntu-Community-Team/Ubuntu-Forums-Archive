---
title: "Bin file help please."
date: 2008-10-06
forum: General Help
---

### Post by stidmatt on 2008-10-06
I downloaded Google Earth for Ubuntu to use microsoft even less than I do now. You can guess why. Pop-up after POP-UP! PLEASE!!!!

It is a bin and I tried to do it with Command Prompt. I typed in:

matthew@matthew-laptop:~$ sudo apt-get install /home/matthew/Desktop/GoogleEarthLinux.bin
Reading package lists... Done
Building dependency tree        
Reading state information... Done
E: Couldn't find package 

this is weird. According to the help I did it correctly. It is almost as if it doesn't like bins.

What am I doing wrong?

---

### Post by iaculallad on 2008-10-06
On your terminal:

```
chmod a+x name_of_file.bin
sudo ./name_of_file.bin
```

---

### Post by Julius1988 on 2008-10-06
go to the directory where you have placed your bin file and type
```
sudo ./GoogleEarthLinux.bin
```
you need to run it to install it.
apt-get is used to download the package online and install it, but it seems you have already downloaded the package.

---

