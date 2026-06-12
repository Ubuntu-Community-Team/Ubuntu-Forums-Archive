---
title: "GoogleEarthLinux.bin"
date: 2009-03-12
forum: Installation &amp; Upgrades
---

### Post by holdea on 2009-03-12
Hello
In former version you could download and install GoogleEarth using Adept.
Today it seems not possible anymore. 
Does anyone know how to apply the .bin file mentioned abobe? Maybe usind the package manager?
BR-andreas

---

### Post by Neo_The_User on 2009-03-12
Um use the one in medibuntu.

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
[http://packages.medibuntu.org/intrepid/googleearth-4.3.html](http://packages.medibuntu.org/intrepid/googleearth-4.3.html)
[http://packages.medibuntu.org/intrepid/googleearth-4.3-data.html](http://packages.medibuntu.org/intrepid/googleearth-4.3-data.html)
[http://packages.medibuntu.org/intrepid/googleearth.html](http://packages.medibuntu.org/intrepid/googleearth.html)

Change intrepid to juanty if you use jaunty, change to hardy if you use hardy etc etc.

---

### Post by oldos2er on 2009-03-12
If you've already got the *.bin on your desktop, open a terminal and run these commands one at a time
```
cd Desktop
chmod a+x GoogleEarthLinux.bin
sudo ./GoogleEarthLinux.bin
```

 This will install Google Earth in /opt/google-earth .

 Exit the installer before running the program.

---

### Post by Neo_The_User on 2009-03-12
> **oldos2er said:**
> If you've already got the *.bin on your desktop, open a terminal and run these commands one at a time
```
cd Desktop
chmod a+x GoogleEarthLinux.bin
sudo ./GoogleEarthLinux.bin
```

 This will install Google Earth in /opt/google-earth .

 Exit the installer before running the program.

Or simply do it through Medibuntu.

---

### Post by Neo_The_User on 2009-03-12
> **wuxi8381 said:**
> [http://www.travelwestchina.com](http://www.travelwestchina.com/)     [tibet travel](http://www.travelwestchina.com/)    [tibet tour](http://www.travelwestchina.com/)    [tibet tours](http://www.travelwestchina.com/)[tibet permit](http://www.travelwestchina.com/)

[SIZE="7"]O[/SIZE]_o... related to Ubuntu how?

---

### Post by Declanthedork on 2009-03-12
You run it just like a   ./configure    file.  It's that easy!

---

### Post by Neo_The_User on 2009-03-12
> **Declanthedork said:**
> You run it just like a   ./configure    file.  It's that easy!

Well the idea is to do things the Ubuntu way unless its necessary to do things otherwise.

---

### Post by oldos2er on 2009-03-12
> **Neo_The_User said:**
> Or simply do it through Medibuntu.

 Yes, I read your first response. The latest version in Medibuntu is 4.3; the latest beta *.bin from Google is 5.something. Just FYI.

---

### Post by redbob on 2009-03-13
Guys:

I installed GoogleEarthLinux.bin right now. 
I followed instructions sent by oldos2er, except for don't used sudo condition. I used the following command:
> sh ./GoogleEarthLinux.bin

It worked like a charm! I'm using Jaunty Alpha 5.

---

### Post by myolbug on 2009-03-13
Never mind...

---

### Post by Steve H on 2009-03-14
> **oldos2er said:**
> If you've already got the *.bin on your desktop, open a terminal and run these commands one at a time
```
cd Desktop
chmod a+x GoogleEarthLinux.bin
sudo ./GoogleEarthLinux.bin
```

 This will install Google Earth in /opt/google-earth .

 Exit the installer before running the program.

I've just done that and now i'm getting 

```
./googleearth-bin: relocation error: /usr/lib/i686/cmov/libssl.so.0.9.8: symbol BIO_test_flags, version OPENSSL_0.9.8 not defined in file libcrypto.so.0.9.8 with link time reference
```

and it just crashes.

How do I uninstall it now?


EDIT: Doesn't matter, I've worked it out. I've successfully got rid of it!!

---

### Post by beameup on 2009-04-20
Right click on the BIn file, and tell it to open with sh 
Then you can just double click it to run

There is an uninstaller in the folder home/"yourusername"/google-earth


Read here:  [http://tombuntu.com/index.php/2009/03/20/how-to-install-google-earth-5-on-ubuntu/](http://tombuntu.com/index.php/2009/03/20/how-to-install-google-earth-5-on-ubuntu/)

---

### Post by retlolo on 2009-07-16
I followed neo the user's advice, having downloaded the googleearth bin file from synaptic, and this is what [I]I get:

[/I]rickwaswo@rickwaswo-desktop:~$ chmod a+x GoogleEarthLinux.bin
chmod: cannot access `GoogleEarthLinux.bin': No such file or directory
rickwaswo@rickwaswo-desktop:~$ cd desktop
bash: cd: desktop: No such file or directory
rickwaswo@rickwaswo-desktop:~$ sudo ./GoogleEarthLinux.bin
[sudo] password for rickwaswo: 
sudo: ./GoogleEarthLinux.bin: command not found
 
the bin file is on the desktop--I'm lost.  Any advice appreciated.  R.

---

### Post by oldos2er on 2009-07-16
You missed the first command
```
cd Desktop
```

---

