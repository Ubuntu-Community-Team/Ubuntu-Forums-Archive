---
title: "How to get the HP Color Laserjet 2600n working in color"
date: 2007-05-28
forum: Hardware &amp; Laptops
---

### Post by mpadams on 2007-05-28
1. Download and extract the Foo2zjs archive...

[http://foo2zjs.rkkda.com/foo2zjs.tar.gz]("http://foo2zjs.rkkda.com/foo2zjs.tar.gz")

2. Install the printer via CUPS ([https://localhost:631]("https://localhost:631") in your browser). Use the PPD file from the downloaded archive as your printer driver when prompted for a PPD file.

3. In "Set Printer Options," set the following...

"Color Mode" = Color
"Bits Per Plane" = 2
"ICM Color Profile" = (something like hpclj2600n-0.icm)


Alternatively, you can follow the instructions given at [http://foo2zjs.rkkda.com/]("http://foo2zjs.rkkda.com/")

---

### Post by Jefim on 2007-06-15
I can confirm this. It worked. Thanks, m8! :popcorn:

---

### Post by cleentrax on 2007-06-28
Bummer. Didn't work for me. Still printing black only.

...OK, I take it back. Third time's a charm!

---

### Post by JerMe on 2007-07-17
Updated:  Use the foothp drivers from the same site ([http://foo2hp.rkkda.com/](http://foo2hp.rkkda.com/)) but run the script instead:

> *** DON'T USE the foo2zjs package from Ubuntu, SUSE, Mandrake/Manrivia, Debian, RedHat, Gentoo, MacOSX, or BSD!
*** Download it here and follow the directions below.

Click the link, or cut and paste the whole command line below to download the driver.

        ```
$ wget -O foo2zjs.tar.gz http://foo2zjs.rkkda.com/foo2zjs.tar.gz
```

Now unpack it:

    Unpack:
        ```
$ tar zxf foo2zjs.tar.gz
```
        ```
$ cd foo2zjs
```

Now compile and install it. The INSTALL file contains more detailed instructions; please read it now.

    Compile:
        ```
$ make
```

    Get .ICM profiles for color correction:
        ```
$ ./getweb 2600n     # Get HP LaserJet 2600n .ICM files
```

    Install driver, foomatic XML files, and extra files:
        ```
$ sudo make install
```

    (Optional) If you use CUPS, restart the spooler:
        ```
$ sudo make cups
```

Run the printer wizard and follow the instructions from [http://foo2hp.rkkda.com/ubuntu/](http://foo2hp.rkkda.com/ubuntu/)

        ```
$ sudo gnome-cups-manager
```

(add a new printer, choose network printer, choose "tcp/socket, hp jetdirect, raw connection", put your printer ip in the host field, leave the port as 9100, click forward, choose "color laserjet 2600n as the printer under hp,  click apply.  right click on your newly created 2600n printer entry, choose properties.  click the advanced tab and set "bits per plane" to 1.  in the same tab, set "color mode" to "color".  set "pageregion" to whatever your paper is, probably letter.  click on the paper tab and set your "paper size" to whatever you are using, probably letter again.)

IMPORTANT: gnome-cups-manager has a BUG in it.  Run this:
        ```
$ sudo make cups
```

---

### Post by fuzzmo on 2007-08-18
Brilliant - that worked for me.  I installed it normally through Ubuntu and it wouldn't print in colour - after going through your well laid out and idiot (me) proof instructions it worked like a charm.  Cheers dude!

---

### Post by UK-Wobbie on 2007-12-16
> **mpadams said:**
> 1. Download and extract the Foo2zjs archive...

[http://foo2zjs.rkkda.com/foo2zjs.tar.gz]("http://foo2zjs.rkkda.com/foo2zjs.tar.gz")

2. Install the printer via CUPS ([https://localhost:631]("https://localhost:631") in your browser). Use the PPD file from the downloaded archive as your printer driver when prompted for a PPD file.

3. In "Set Printer Options," set the following...

"Color Mode" = Color
"Bits Per Plane" = 2
"ICM Color Profile" = (something like hpclj2600n-0.icm)


Alternatively, you can follow the instructions given at [http://foo2zjs.rkkda.com/]("http://foo2zjs.rkkda.com/")

Why not go to this site for more easy help!
[http://foo2hp.rkkda.com/ubuntu/](http://foo2hp.rkkda.com/ubuntu/) ):P](*,):mrgreen:

---

### Post by stchman on 2008-01-15
I have scripts that automate the process of getting zenographics based printers working.

[http://www.stchman.com/foo2zjs.html](http://www.stchman.com/foo2zjs.html)

Follow the instructions precisely for your Ubuntu distro.

---

