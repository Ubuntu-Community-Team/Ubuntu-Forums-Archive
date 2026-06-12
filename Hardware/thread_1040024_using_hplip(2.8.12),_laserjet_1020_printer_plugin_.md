---
title: "using hplip(2.8.12), laserjet 1020 printer: plugin installation not working"
date: 2009-01-15
forum: Hardware
---

### Post by azr on 2009-01-15
The Hp Laserjet 1020 printer works at odd times after combinations of powering it on and off, uploading firmware to it and installing the (required) plugin.

After installing the plugin *successfully*, the output of hp-check has only one error (and no warnings): the plugin is not installed. This is the case every time I do a successful plugin install.

I have tried removing and reinstalling the printer with hp-setup. 

Any suggestions?

---

### Post by azr on 2009-01-20
This may possibly be a bug with the hp printer manager or I may have set up it up  incorrectly. (The installation guide does mention that this printer is only partially supported.)

My solution:

remove hp manager. (You can also remove installed printers first to avoid confusion) If installed with synaptic:

```
sudo apt-get remove --purge hplip
```

if you installed it by compiling it (if you don't know what this is you probably didn't do it - it invovled issuing commands like 'make'), navigate to the directory of the source code and:

```
sudo make uninstall
```

And this is quoted from the [the driver installation guide]("http://foo2zjs.rkkda.com/INSTALL") (my edits in italics)

>     
    Install build-essential FIRST:
```

	$ sudo apt-get install build-essential
	$ wget -O foo2zjs.tar.gz [http://foo2zjs.rkkda.com/foo2zjs.tar.gz](http://foo2zjs.rkkda.com/foo2zjs.tar.gz)
	$ tar zxf foo2zjs.tar.gz
	$ cd foo2zjs
	$ sudo make uninstall
	$ make
	$ ./getweb 1020

```
	    *replace 1020 with your printer - consult link above*
```

	$ sudo make install install-hotplug cups

```
        *over here it is advised to restart cups*
```

        $ sudo /etc/init.d/cups restart

```

*Now we add the printer, using either ubuntu's printer manager or the web interface manager for cups. If you're connected your printer to usb, and a usb connection doesn't show up try restarting cups again.*

   For 7.10 and later users (with gnome installed):
```

	    $ sudo system-config-printer

```

    If that doesn't work, then fire up:
```

	$ firefox [http://localhost:631](http://localhost:631)

```


One last step: we need to upload the firmware to the printer with the following command:

```

$ sudo cat /usr/share/foo2zjs/firmware/sihp1020.dl > /dev/usb/lp0

```

The device at end (/dev/usb) may need to be edited to your setup - again see the installation guide.  If it works the printer will make its whirring noises.

*IMPORTANT NOTE* 
This command will have to run whenever the printer is turned on. To make the computer do it automatically on startup add the above line of code to 
/etc/init.d/rc.local (without the sudo)

---

