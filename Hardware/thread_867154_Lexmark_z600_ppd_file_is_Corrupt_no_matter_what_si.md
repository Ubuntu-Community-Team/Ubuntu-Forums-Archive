---
title: "Lexmark z600 ppd file is Corrupt no matter what site i download it from"
date: 2008-07-22
forum: Hardware
---

### Post by slayr007 on 2008-07-22
I have a Dell A920 (Lexmark z600) printer and i followed the directions from the ubuntu documetation and when i go to System > Admin> printing and try and use the ppd file i downloaded I keep getting a message that says the file is corrupt. Does anybody know what to do?

---

### Post by phidia on 2008-07-22
Have you tried downloading from the openprinting page for that printer [here]("http://openprinting.org/show_printer.cgi?recnum=Lexmark-Z600_Series")? Perhaps follow the guide there too.

---

### Post by slayr007 on 2008-07-23
yes I have:confused: and before my comp corrupted i got it to work just fine

---

### Post by phidia on 2008-07-23
Can you post or search the _exact_ error message?

---

### Post by nickdangerthirdeye on 2009-05-16
I got it working on jaunty, get the driver from here [http://www.autostatic.com/linux/](http://www.autostatic.com/linux/) and save them some place safe, you will want both tar.gz files,  then get libstdc++.so.5 I used this ver [http://ftp.us.debian.org/debian/pool/main/g/gcc-3.3/libstdc++5_3.3.6-18_i386.deb](http://ftp.us.debian.org/debian/pool/main/g/gcc-3.3/libstdc++5_3.3.6-18_i386.deb)

but there is apparently and older version in the repository that should probably work too, and I just used gdebi to install libstdc++5...

after that open a terminal windows and get to the folder you saved the tar.gz files in and run

sudo [FONT=ms sans serif, helvetica]tar -xvzf z600cups-1.0-1.i386.tar.gz -C /
and
sudo [/FONT][FONT=ms sans serif, helvetica]tar -xvzf z600llpddk-2.0-1.i386.tar.gz -C /[/FONT]

after that you may need to restart cups, but I don't think I did, and go to System -> administration -> printing and add your printer, you should see it listed, when you get to the part about selecting a driver choose the z600 driver.

this worked for me with a Lexmark z510.


[URL="http://www.autostatic.com/linux/"]
[/URL]

---

### Post by slayr007 on 2009-05-17
I got it working to using a shell i found on the internet.

---

