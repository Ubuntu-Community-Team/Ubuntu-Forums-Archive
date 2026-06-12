---
title: "HOWTO: Install Brother Laser Printer (Hardy - 8.04)"
date: 2008-07-08
forum: Hardware
---

### Post by musther on 2008-07-08
First you'll need to go to the Brother website and download the linux LPR driver, and the CUPS Wrapper driver for your printer, be suer to get the debian versions:
[http://solutions.brother.com/linux/en_us/index.html](http://solutions.brother.com/linux/en_us/index.html)

If you already have the printer in System --> Administration --> Printing, then be sure to delete it before continuing.

Next, open a terminal and use the cd command to get to the directory to which you downloaded the files:

eg:
```
cd Desktop/brother/
```

Now install the LPR driver, note that your filename will be different from mine:
```
sudo dpkg -i --force-all brhl2040lpr-2.0.1-1.i386.deb
```

Now, you'll need to do three little things to make everything work before you install the wrapper driver:

```
sudo mkdir /usr/share/cups/model/
```

Then:

```
sudo ln -s /etc/init.d/cupsys /etc/init.d/cups
```

And finally (being sure to change it for your printer model):

```
sudo mkdir /var/spool/lpd/HL2040
```

Finally, install the wrapper driver (again, your filename will differ from mine):

```
sudo dpkg -i --force-all cupswrapperHL2040-2.0.1-2.i386.deb
``` 

That's the printer installed.

Go to System --> Administration --> Printing

You'll see your new printer there if all has gone well.  You can then make it default and change the options.  One thing you may need to change is where it says 'Device URI'.  Mine was a network printer, but the install set it up as USB, so I simply clicked change, and then selected the correct location.

Hopefully that'll have you all set up.

Have Fun :-)

---

