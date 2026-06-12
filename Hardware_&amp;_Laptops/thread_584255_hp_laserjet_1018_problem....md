---
title: "hp laserjet 1018 problem..."
date: 2007-10-20
forum: Hardware &amp; Laptops
---

### Post by Maxster on 2007-10-20
hello,
i really need help with my printer.
printer: hp laserjet 1018
running: ubuntu 7.10
status: frustrated.

so the computer sees the printer, but the printer does not budge wen I want to print something. 
i tried setting up the printer with hplip, but it did not work, it did not find a printer on usb.

it wasent printing  in 7.04, i was hopping 7.10 would work the printing (with all the supposable printer compatibility)

my sister wanted me to install 7.10 on her laptop, she goes to school, she really needs to print, althought i will be sharing this printer over the network.


please help!
i just dont want my sister to bott xp wen she wants to print stuff.

thanks!

---

### Post by Sef on 2007-10-20
Read [Openprinting's]("http://openprinting.org/show_printer.cgi?recnum=HP-LaserJet_1018") take on your printer.

---

### Post by Maxster on 2007-10-21
thank you very much
it works goood!

i really apreciate your help!

---

### Post by frosty.ptz on 2007-10-29
It works, but why ubuntu developers are not including this drivers into repository? They are open source and tested by many people. It's to difficult for most people and I thinks it's not right way to install software from sources in package-based distro.

---

### Post by lhever on 2007-11-15
This method not working anymore since the location of the firmware changed: 
```

$ getweb 1018
--22:27:14--  http://foo2zjs.rkkda.com/sihp1018.tar.gz
           => `sihp1018.tar.gz'
Resolving foo2zjs.rkkda.com... 74.208.41.246
Connecting to foo2zjs.rkkda.com|74.208.41.246|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
22:27:15 ERROR 404: Not Found.

getweb: Couldn't download http://foo2zjs.rkkda.com/sihp1018.tar.gz
```

So I had to do it manually with the new location:

```

$ wget http://foo2zjs.rkkda.com/firmware/sihp1018.tar.gz
$ tar xvzf sihp1018.tar.gz
$ arm2hpdl sihp1018.img  > sihp1018.dl
$ sudo cp ./sihp1018.dl /usr/share/foo2zjs/firmware/sihp1018.dl
$ sudo  cat /usr/share/foo2zjs/firmware/sihp1018.dl >  /dev/usb/lp0

```

At this point the printer engine should start and the print test page should work from both cups and printer manager. 

Tested on Gutsy.

Regards,
Lorinc

---

### Post by guga31bb on 2007-11-19
hey, i tried these commands and this is what happened: 

ben@lappy2:~$ tar xvzf sihp1018.tar.gz
sihp1018.img
ben@lappy2:~$ arm2hpdl sihp1018.img  ./sihp1018.dl
Usage:
        arm2hpdl [options] sihp1005.img > sihp1005.dl

        Add HP download header/trailer to an ARM ELF binary.
        If the file already has an HP header, just copy it to stdout.

Options:
       -D lvl      Set Debug level [0]
ben@lappy2:~$ sudo cp ./sihp1018.dl /usr/share/foo2zjs/firmware/sihp1018.dl
[sudo] password for ben:
cp: cannot stat `./sihp1018.dl': No such file or directory

Printing is making me sad =(

---

### Post by lhever on 2007-11-20
I'm made a typo, the correct arm2hpdl is:
$ arm2hpdl sihp1018.img  > sihp1018.dl

---

### Post by IanB2 on 2008-04-12
> **lhever said:**
> This method not working anymore since the location of the firmware changed: 
```

$ getweb 1018
--22:27:14--  http://foo2zjs.rkkda.com/sihp1018.tar.gz
           => `sihp1018.tar.gz'
Resolving foo2zjs.rkkda.com... 74.208.41.246
Connecting to foo2zjs.rkkda.com|74.208.41.246|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
22:27:15 ERROR 404: Not Found.

getweb: Couldn't download http://foo2zjs.rkkda.com/sihp1018.tar.gz
```

So I had to do it manually with the new location:

```

$ wget http://foo2zjs.rkkda.com/firmware/sihp1018.tar.gz
$ tar xvzf sihp1018.tar.gz
$ arm2hpdl sihp1018.img  > sihp1018.dl
$ sudo cp ./sihp1018.dl /usr/share/foo2zjs/firmware/sihp1018.dl
$ sudo  cat /usr/share/foo2zjs/firmware/sihp1018.dl >  /dev/usb/lp0

```

At this point the printer engine should start and the print test page should work from both cups and printer manager. 

Tested on Gutsy.

Regards,
Lorinc

I too cannot get a HP Laserjet 1018 to work ...... the printer is recognised in Gutsy but nothing happens when I send things to the print queue.

I've tried to above and get a 'permission denied' when trying to execute the last line 'sudo  cat /usr/share/foo2zjs/firmware/sihp1018.dl >  /dev/usb/lp0'

Help would be much appreciated as I bought this printer after researching carefully and thought it would work with no problems ...... I'm sure there is a solution??

---

### Post by IanB2 on 2008-04-12
> **IanB2 said:**
> I too cannot get a HP Laserjet 1018 to work ...... the printer is recognised in Gutsy but nothing happens when I send things to the print queue.

I've tried to above and get a 'permission denied' when trying to execute the last line 'sudo  cat /usr/share/foo2zjs/firmware/sihp1018.dl >  /dev/usb/lp0'

Help would be much appreciated as I bought this printer after researching carefully and thought it would work with no problems ...... I'm sure there is a solution??

This worked for me see [https://answers.launchpad.net/ubuntu/+question/5062](https://answers.launchpad.net/ubuntu/+question/5062)

---

