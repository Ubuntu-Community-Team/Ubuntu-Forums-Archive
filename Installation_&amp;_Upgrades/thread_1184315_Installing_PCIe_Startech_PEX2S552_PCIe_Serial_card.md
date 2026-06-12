---
title: "Installing PCIe Startech PEX2S552 PCIe Serial card / MosChip MSC9001 chipset on Ubunt"
date: 2009-06-11
forum: Installation &amp; Upgrades
---

### Post by eldiabolosk on 2009-06-11
Installing PCIe Startech PEX2S552 PCIe Serial card / MosChip MSC9001 chipset on Ubuntu 8.10 Intrepid.



The drivers are both available from the Startech.com website and the instalation CD.



The manual encourages to check on card detection from the terminal using:



```


 lspci -v



```
Next copy the  "starex.tar.gz" tar file in a desired directory and un-tar it by executing:


  ```
tar -xzvf starex.tar.gz


```

Before you procede with "make" a number of changes needs to be done since the "9900.c" file was most likely written and tested on an older Red Hat kernel version.



Moste likely you will need to make some changes.

to test you can proceed with:




```
 make
```



if you run a Ubuntu 8.04 (Hardy) with a kernel 2.6.24-23. you may not run into this problem.

Running 8.10 (Intrepid) in kernel 2.6.27-11 or 2.6.27-14 and 9.04 (Jaunty) kernel 2.6.28-11, you will most likely get this error: "error: ‘struct uart_info’ has no member named ‘tty’" in three functions. Most likely on lines 622, 852, and 957.



To fix this one replace the next code in the 9900.c file:

```
*tty=up->port.info->tty

```


to 

```
*tty=up->port.info->port.tty 

```


The next error was common to all the tested Ubuntu versions:

ERROR:

‘SA_SHIRQ’ undeclared (first use in this function)



To fix the installer edit the 9900.c again

exchange the following


```
‘SA_SHIRQ’

```


with


```
‘IRQF_SHARED’ 

```


At this point run "```
make
```"





Before running "make install"



remove in INSTALLER AND UNINSTALLER the the "rc.d" part

Original INSTALLER CODE:



```
ln -s /etc/init.d/mcs9900 /etc/rc.d/rc3.d/Smcs9900 || true  	

ln -s /etc/init.d/mcs9900 /etc/rc.d/rc5.d/Smcs9900 || true

```


Edited



```
ln -s /etc/init.d/mcs9900 /etc/rc3.d/Smcs9900 || true  	

ln -s /etc/init.d/mcs9900 /etc/rc5.d/Smcs9900 || true
```



UNINSTALLER:

Original CODE:

```
rm -f /etc/rc.d/rc3.d/Smcs9900

rm -f /etc/rc.d/rc5.d/Smcs9900
```

Edited CODE:

```
rm -f /etc/rc3.d/Smcs9900

rm -f /etc/rc5.d/Smcs9900

```


This is needed since the structure in UBUNTU is most likely different to Red Hat.



Nov it is time to run the "```
sudo make install
```" command.



NOTE: No sudo privileges were not necessary for make.



After the driver is compiled most likely a few more steps will be needed. 

I will post the "setserial" steps as soon as I get it working.



If you have any questions, post a Reply on this POST.

Edited drivers available on [www.opengeolog.com/moschip9900/](www.opengeolog.com/moschip9900/)

---

### Post by tfiska on 2009-06-13
Hi,

Thank you for this, I have the exact same problem with the MCS9901 chipset.

---

### Post by eldiabolosk on 2009-06-15
Did you get it working? 

I spoke with the guys from Startech and they are going to be commiting the very same changes to their new drivers.  

Which distribution are you running?

What seems to be the problem?

Does the card work for you now?

I still have some problems with the card, but they seems to be more OS/ setup problems than driver compilation problems. I will try to get on it in the next few days. Please, let me know  what you problem seems to be. 

Ed.

---

### Post by iczerjones on 2010-05-07
I have solved this issue on a Debian 2.6.26-2 based system, so I figured I would pass along the steps I followed in hopes it may help someone else solve the issue in the future. 

This was performed on a Startech dual port PCIe serial card using the mcs9900/9901 chip.

Before beginning, be sure you have all required build tools. (kernel source / headers, build-essentials, etc..)

1) Download the patch in the post above.  Unpack the driver..

```
 tar xzf starex.tar.gz
``` 

..navigate to that directory..

```
 cd starex
```

..and copy the patch there as well.

```
jones@jones-laptop:~/Desktop/starex$ ls
9900.c  9900-isa.c  Makefile  readme
9900.h  9900-isa.h  mcs9900   starex_2.6.28.patch

```

3) Apply the patch to the 9900.c source.

```
 patch < starex_2.6.28.patch
```

4) Edit the following lines:

Line 622:

--> Old code:
```
struct tty_struct *tty = up->port.info->port.tty; 
``` --> New code:
```
struct tty_struct *tty = up->port.info->tty; 
``` 

Line 852:

--> Old code:
```
struct tty_struct *tty = up->port.info->port.tty; 
``` --> New code:
```
struct tty_struct *tty = up->port.info->tty; 
``` 

And finally line 957:

--> Old code:
```
struct tty_struct *tty = up->port.info->port.tty; 
``` --> New code:
```
struct tty_struct *tty = up->port.info->tty; 
``` 


In case you were noticing, yes, those are the same exact lines and changes.  It appears that the patch places an object (port) as part of the usage of the function that is not defined as part of those functions in the context of 'tty'.  Remove it and move on to building the module.

Because of this, you could alternatively just sed the change globally:

```
  sed -i s/port\.tty/tty/g 9900.c 
```


5) Build the module:

```
 jones@jones-laptop:~/Desktop/starex$ sudo -s make 
```

6) Remove all instances of 'rc.d' from the Makefile INSTALL and UNINSTALL functions (as stated above):

INSTALL
Old code:
```
ln -s /etc/init.d/mcs9900 /etc/rc.d/rc3.d/Smcs9900 || true 
ln -s /etc/init.d/mcs9900 /etc/rc.d/rc5.d/Smcs9900 || true
```
New code:
```
ln -s /etc/init.d/mcs9900 /etc/rc3.d/Smcs9900 || true 
ln -s /etc/init.d/mcs9900 /etc/rc5.d/Smcs9900 || true
```

UNINSTALL
Old code:
```
rm -f /etc/rc.d/rc3.d/Smcs9900
rm -f /etc/rc.d/rc5.d/Smcs9900
```
New code:
```
rm -f /etc/rc3.d/Smcs9900
rm -f /etc/rc5.d/Smcs9900
```

Same thing for this one, you can alternatively just perform an inline substitution:

```
  sed -i 's/\/rc\.d//g' Makefile 
```
 

7) Once that's done, go ahead and perform the install:

```
jones@jones-laptop:~/Desktop/starex$ sudo -s make install
```



Hope that helps someone out.  Thank you guys in turn for pointing me in the right direction in the first place! :KS

---

