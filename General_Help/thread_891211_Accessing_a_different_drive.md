---
title: "Accessing a different drive?"
date: 2008-08-15
forum: General Help
---

### Post by JaxDragon on 2008-08-15
I have Ubuntu installed on my D drive. Can I access my C drive in ubuntu? D drive is not a partition, it is a seperate hard disk. I ask because I have wine and want to run a game from my windows drive(drive C).

---

### Post by peruvianfreak250 on 2008-08-15
i think you can mount the drive just like you mount anything else
i do that to the windows partition i have to access its files
just find it under /media/sda1 (its called sda1 on my pc but yours might be different)
so i use sudo mount /media/sda1
and it mounts it

but i don't know if you can run a game that is installed in another drive with wine, because wine uses a virtual c:/ drive , this c drive has its own windows folder and "program files" folder under .wine

 i would like to know how to do that too if you find out but i as far as i know you cant.

---

### Post by peruvianfreak250 on 2008-08-15
although now that i think about it, if you were to just tell wine to use the real c:/ drive instead of the virtual one, it should work.

---

### Post by JaxDragon on 2008-08-15
But wouldn't wine just make it like drive G or something?

---

### Post by avanhel on 2008-08-16
In principle you should be able to tell wine where to find the game or program on the regular c drive. But as the warning from wine tells us you should never use that method because in most cases the program will cease to work under both operating systems. 
For more in this just look in the forum about wine or on the winehq.com website.
as for mounting a drive go to the menu locations and select the network option. this opens a window where you can select the other drives.

---

### Post by peruvianfreak250 on 2008-08-16
> **JaxDragon said:**
> But wouldn't wine just make it like drive G or something?

no because its not really drive c,just a folder named C:/program files.  it can run both.
this drive c is just so that the windows programs think that it is running on a real windows.

---

### Post by dje on 2008-08-16
please post the output of from terminal (applications >> accessories >> terminal):
```
sudo fdisk -l
```
thats a lowercase L not a one on the end

dje

---

