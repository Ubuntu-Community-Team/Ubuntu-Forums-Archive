---
title: "Ati Radeon RV250 (Mobility fire gl 9000)"
date: 2009-01-08
forum: Hardware
---

### Post by TekmonX on 2009-01-08
Hello Ubuntu fourms, I'm in need of drivers for my Ati Radeon RV250 (Mobility fire gl 9000) graphics card, because I'm really wanting to run some games.

However, I've heard that getting this graphics card to work can be a pain in the ****, but I have plenty of free time every day, so...

If anyone knows where I can find the drivers for this, I'd really appreciate it.

Thanks in Advance,
Tekmon Xonic

---

### Post by TekmonX on 2009-01-08
If anyone has suggestions or advice, that would be really nice :).

---

### Post by hivelocitydd on 2009-01-08
You can download the driver from the following link
hope this helps

[http://www.radarsync.com/driver/d205643-radeon_rv250](http://www.radarsync.com/driver/d205643-radeon_rv250)

---

### Post by TekmonX on 2009-01-09
> **hivelocitydd said:**
> You can download the driver from the following link
hope this helps

[http://www.radarsync.com/driver/d205643-radeon_rv250](http://www.radarsync.com/driver/d205643-radeon_rv250)

The page you gave me does show up, but no downloads are shown, a window said (this page is currently under maintenance, I'll be sure to check back later. Thanks :)

---

### Post by hivelocitydd on 2009-01-09
Pls see the below link

[http://www.radarsync.com/driver/r](http://www.radarsync.com/driver/r)
you can find the driver in the list

---

### Post by TekmonX on 2009-01-09
> **hivelocitydd said:**
> Pls see the below link

[http://www.radarsync.com/driver/r](http://www.radarsync.com/driver/r)
you can find the driver in the list

Just brings me to the same page with no downloads. Like I said, the site said its under maintenance.

---

### Post by TekmonX on 2009-01-09
Okay, the page isn't working, and I really need those drivers.

---

### Post by TekmonX on 2009-01-09
Isn't there some sort of installer program that you can download? I've find it while looking on Google.

---

### Post by vanadium101 on 2009-01-09
try here 

[http://ati.amd.com/support/drivers/linux/linux-radeon.html](http://ati.amd.com/support/drivers/linux/linux-radeon.html)

---

### Post by TekmonX on 2009-01-10
> **vanadium101 said:**
> try here 

[http://ati.amd.com/support/drivers/linux/linux-radeon.html](http://ati.amd.com/support/drivers/linux/linux-radeon.html)

I've downloaded it, but the run program won't run :(, I'll try downloading it again.

---

### Post by TekmonX on 2009-01-10
No Luck, it just won't run :(

---

### Post by TekmonX on 2009-01-10
Any suggestions? I'm not really sure what to do from here.

---

### Post by zika on 2009-01-10
> **TekmonX said:**
> Any suggestions? I'm not really sure what to do from here.
```
sudo chmod +x path/the_name_of_the_file
```
```
sh path/name_of_the_file
```

---

### Post by TekmonX on 2009-01-10
> **zika said:**
> ```
sudo chmod +x path/the_name_of_the_file
```
```
sh path/name_of_the_file
```

What are these commands for? You really didn't provide enough details :(.

---

### Post by zika on 2009-01-10
> **TekmonX said:**
> What are these commands for? You really didn't provide enough details :(.
these are commands for Terminal.
assume You've dl-ed the file from ati site. let us call it **ati.bin**
```
sudo chmod +x ~/Desktop/ati.bin (in order to make it "executable")
sudo sh ~/Desktop/ati.bin (in order to run that file)
```(I've assumed You've been following ATI instructions for the file from their site, sorry, and assuming You've got stuck with problem executing the file. if that is not the case please explain in more details)

---

### Post by TekmonX on 2009-01-10
> **zika said:**
> these are commands for Terminal.
assume You've dl-ed the file from ati site. let us call it **ati.bin**
```
sudo chmod +x ~/Desktop/ati.bin (in order to make it "executable")
sudo sh ~/Desktop/ati.bin (in order to run that file)
```(I've assumed You've been following ATI instructions for the file from their site, sorry, and assuming You've got stuck with problem executing the file. if that is not the case please explain in more details)

Alright, it successfully installed, now  I need the required packages for it, but I  don't know where to find them...

---

### Post by jocko on 2009-01-10
> **TekmonX said:**
> I've downloaded it, but the run program won't run :(, I'll try downloading it again.

Don't even try to install ati's proprietary driver on that card, it's not supported. It supports only cards from radeon 9500 and better.
The open source driver that is already installed and activated by default in ubuntu is the ONLY driver that support your card.

---

### Post by el generico on 2009-01-11
Did you receive an error of some kind when you tried to run it?  Did you run it from command line?  Like so:

sudo sh ati-driver-installer-8-12-x86.x86_64.run

---

### Post by jocko on 2009-01-11
> **el generico said:**
> Did you receive an error of some kind when you tried to run it?  Did you run it from command line?  Like so:

sudo sh ati-driver-installer-8-12-x86.x86_64.run

DON'T tell him/her to install that driver! It DOES NOT SUPPORT such an old card. Period.

---

### Post by orawax on 2009-04-22
See if this works for you:
[http://ubuntuforums.org/showthread.php?p=7119713#post7119713](http://ubuntuforums.org/showthread.php?p=7119713#post7119713)

---

### Post by orawax on 2009-09-30
Forget the above, this seems to work perfectly:
[http://ubuntuforums.org/showpost.php?p=7804812&postcount=2](http://ubuntuforums.org/showpost.php?p=7804812&postcount=2)

(See also postcount=3...)

---

