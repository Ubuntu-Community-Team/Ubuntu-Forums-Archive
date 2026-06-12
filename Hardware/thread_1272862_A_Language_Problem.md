---
title: "A Language Problem"
date: 2009-09-22
forum: Hardware
---

### Post by Luise on 2009-09-22
On the site of the brothers solution center 

[http://solutions.brother.com/linux/en_us/faq_prn.html#143](http://solutions.brother.com/linux/en_us/faq_prn.html#143)

it says: 

**I'm using Ubuntu 8.04 or greater.  I have installed the drivers, but I am still unable to print.** 


Ubuntu 8.04 or greater does not have /usr/share/cups/model directory where our driver create a ppd file.
Please follow the instruction below when the installation failed with the message about it.

1. Uninstall the cupswrapper driver.
Command : sudo  dpkg  -P  (driver name)

2. Create /usr/share/cups/model directory
Command : sudo  mkdir  /usr/share/cups/model

3. Install the cupswrapper driver
Command : sudo dpkg  -i  --force-all (driver file name) 
---------

Is the driver "file" namethe same as the driver name?

Since the --force parameter will be used, I want to be sure I'll be doing the right thing. :confused:

cu

Luise

---

### Post by sisco311 on 2009-09-22
Hi and welcome to the forums!

> **Luise said:**
> 
Is the driver "file" name the same as the driver name?


It's the name of the .deb file you downloaded. 

Make sure that the .deb package is in the current working directory or use the full path to the file.

Just type:
```
sudo dpkg -i --force-all
```
type a space, drag the .deb file in the terminal window and press Enter.

---

### Post by Luise on 2009-09-24
> **sisco311 said:**
> Hi and welcome to the forums!



It's the name of the .deb file you downloaded. 

Make sure that the .deb package is in the current working directory or use the full path to the file.

Just type:
```
sudo dpkg -i --force-all
```type a space, drag the .deb file in the terminal window and press Enter.


It does not work:(

Let me re-quote the instructions at "brothers solution"

> **"I'm using Ubuntu 8.04 or greater.  I have installed the drivers, but I am still unable to print.** 


Ubuntu 8.04 or greater does not have /usr/share/cups/model directory where our driver create a ppd file.
Please follow the instruction below when the installation failed with the message about it.

1. Uninstall the cupswrapper driver.
Command : sudo  dpkg  -P  (driver name)

2. Create /usr/share/cups/model directory
Command : sudo  mkdir  /usr/share/cups/model

3. Install the cupswrapper driver
Command : sudo dpkg  -i  --force-all (driver file name) "

As to step 1 above:

I had uninstalled the driver by using aptitude purge (driver name)

To step 2:

I made the directory

To step 3

I used the syntax given, but found out tha dpkg does not fetch from the net source ( I am not familiar with dpkg)

So I did: aptitude install driver model. It *seemed* to do so, but on "locate model) I just found it in the apt archives.

I cd'ed to the archives and used the command again.

It did an overwrite of the package in the archive:confused:

On locate model I again found it only in the archive. The /usr/share/cups/model directory is still empty.

---

