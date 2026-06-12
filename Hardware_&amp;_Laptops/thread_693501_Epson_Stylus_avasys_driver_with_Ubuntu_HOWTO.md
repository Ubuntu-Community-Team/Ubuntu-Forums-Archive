---
title: "Epson Stylus avasys driver with Ubuntu HOWTO"
date: 2008-02-11
forum: Hardware &amp; Laptops
---

### Post by Axx83 on 2008-02-11
Hello everyone, since last November I own a Stylus DX4400 (same driver as CX4300 CX4400 CX4450 CX5500 CX5600 DX4450) and even tough I correctly installed the scanner driver through this procedure: [http://http://ubuntuforums.org/showthread.php?t=627471]("http://http://ubuntuforums.org/showthread.php?t=627471") I can't seem to make the official printer driver work, as hard as I can try. I KNOW thousands of people have read my guide on the forum and now happily use their scanner with Ubuntu so why not help me install the printer driver too ??? Here's what I did:

I download the driver from the avasys website
[http://www.avasys.jp/english/linux_e/dl_spc.html](http://www.avasys.jp/english/linux_e/dl_spc.html) I unpack it in a folder
```
sudo mkdir pips
mv pips-scx4450-Redhat9-3.0-CLGE.tgz pips/
cd pips
tar xfz pips-scx4450-Redhat9-3.0-CLGE.tgz 
```
and then I run the script in this way
```
sudo ./pips-scx4450-Redhat9-3.0-CLGE.install --noexec --target ./ --keep --nochown
```
at this point there will be many rpm files in the dir, i convert them with alien and install them
```
sudo alien --scripts --keep-version pips-*.rpm
sudo dpkg -i pips-*.deb
```
the terminal gives me approximately this result (I ran it a second time, but it's almost the same response)
```
raffy@raffy-desktop:~/pips$ sudo dpkg -i pips-*.deb
[sudo] password for raffy:
(Lettura del database ... 136757 file e directory attualmente installati.)
Mi preparo a sostituire pips-core 3.0-1 (con pips-core_3.0-1_i386.deb) ...
Spacchetto il sostituto di pips-core ...
Mi preparo a sostituire pips-cups 3.0-1 (con pips-cups_3.0-1_i386.deb) ...
Spacchetto il sostituto di pips-cups ...
Mi preparo a sostituire pips-extension 3.0-1 (con 
pips-extension_3.0-1_i386.deb) ...
Spacchetto il sostituto di pips-extension ...
Mi preparo a sostituire pips-gtk2 3.0-1 (con pips-gtk2_3.0-1_i386.deb) ...
Spacchetto il sostituto di pips-gtk2 ...
Mi preparo a sostituire pips-lpr 3.0-1 (con pips-lpr_3.0-1_i386.deb) ...
Spacchetto il sostituto di pips-lpr ...
Mi preparo a sostituire pips-redhat9 3.0-1 (con 
pips-redhat9_3.0-1_i386.deb) ...
Spacchetto il sostituto di pips-redhat9 ...
Mi preparo a sostituire pips-scx4450 3.0-1 (con 
pips-scx4450_3.0-1_i386.deb) ...
Spacchetto il sostituto di pips-scx4450 ...
Configuro pips-core (3.0-1) ...

Configuro pips-cups (3.0-1) ...

Configuro pips-extension (3.0-1) ...

Configuro pips-gtk2 (3.0-1) ...

Configuro pips-lpr (3.0-1) ...

Configuro pips-redhat9 (3.0-1) ...
ln: creazione del link simbolico `/etc/rc.d/rc2.d/S11ekpd' a 
`/etc/rc.d/init.d/ekpd': Nessun file o directory
ln: creazione del link simbolico `/etc/rc.d/rc3.d/S11ekpd' a 
`/etc/rc.d/init.d/ekpd': Nessun file o directory
ln: creazione del link simbolico `/etc/rc.d/rc4.d/S11ekpd' a 
`/etc/rc.d/init.d/ekpd': Nessun file o directory
ln: creazione del link simbolico `/etc/rc.d/rc5.d/S11ekpd' a 
`/etc/rc.d/init.d/ekpd': Nessun file o directory
ln: creazione del link simbolico `/etc/rc.d/rc0.d/K89ekpd' a 
`/etc/rc.d/init.d/ekpd': Nessun file o directory
ln: creazione del link simbolico `/etc/rc.d/rc1.d/K89ekpd' a 
`/etc/rc.d/init.d/ekpd': Nessun file o directory
ln: creazione del link simbolico `/etc/rc.d/rc6.d/K89ekpd' a 
`/etc/rc.d/init.d/ekpd': Nessun file o directory

Configuro pips-scx4450 (3.0-1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
raffy@raffy-desktop:~/pips$
```
Ok it's in Italian but it's very easy, everything goes fine except the last deb, it wants to create symbolic link to the ekpd file but some files are missing in a couple of dir. I tought to create a symbolic link to the real file
```
cd /
cd etc
sudo mkdir rc.d
cd rc.d
sudo mkdir init.d
sudo ln -s /etc/init.d/ekpd /etc/rc.d/init.d/ekpd
```
but nothing changes. Anyway I skipped the error message and continued, since at this point the installer wants to run a script that doesn't exist I create it with gedit
```
sudo gedit /etc/init.d/ekpd
```
I put this code in the file (suggested by a guy on the italian board)
```
# Photo Image Print System
# Copyright (C) 2002-2005 EPSON AVASYS Corporation.
# Copyright (C) SEIKO EPSON CORPORATION 2002-2005.
#
# . /etc/rc.d/init.d/functions

PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
DAEMON=/usr/local/EPAva/core/ekpd
NAME=ekpd
DESC="EPSON Avasys printing daemon"

[ -f $DAEMON ] || exit 0

OLDMASK=`umask`
umask 000

case "$1" in
start)
        pidlist=`pidof $NAME`
        if [ "x" = "x$pidlist" ]; then
                echo -n "Starting $NAME:"
          start-stop-daemon --start --exec $DAEMON 2>/dev/null
          echo
        fi
        ;;

stop)
        echo -n "Stopping ekpd:"
        start-stop-daemon --stop --name $DAEMON 2>/dev/null
        echo
        ;;

restart)
        $0 stop
        sleep 2
        $0 start
        ;;

*)
        echo "Usage: ekpd { start | stop | restart }" >&2
        exit 1
        ;;
esac

umask $OLDMASK
exit 0
```
unfortunately when I run the script
```
sudo /etc/init.d/ekpd start
```
It gives me **command not found** even tough the bin file exists and it is located in /usr/local/EPAva/core/ correctly, i even created the symbolic link through
```
ln -s /bin/pidof /sbin/pidof
```
but the result is the same, command not found, and since I NEED this deamon to run for the procedure to continue I'm preatty much stuck here...

---

### Post by oldsoundguy on 2008-02-11
have you checked for your drivers in gutenprint?  I found them for my R1800 photo unit there!

---

### Post by Axx83 on 2008-02-11
there's no gutenprint driver for this printers: CX4300 CX4400 CX4450 CX5500 CX5600 DX4400 DX4450 you can use the dx3850 or the d68 (better choice) driver and it works. but the printer is too slow and most importantly it uses DOUBLE the ink as in windows with official driver, that is VERY VERY VERY bad that's why I'm desperately trying to install the avasys driver in Ubuntu, it works with red hat, mandrake and others but not (still) with Ubuntu and/or Debian.

---

### Post by oldsoundguy on 2008-02-11
OIC, sorry, was just a suggestion.

---

### Post by thiagopc on 2008-03-02
Did you run ```
chmod +x /etc/init.d/ekpd
```?

I've just followed your instructions, and everything worked alright till this point.

---

### Post by Axx83 on 2008-03-05
MMM I will absolutely try that as soon as i can and I'll let you know, thanks

---

### Post by Spherical on 2008-03-25
Is this problem solved already?

Got me a Stylus DX4450 today, with the insurance of the salesman that "It works under Linux no problems"

But I can't get the printer to work either. I've tried everything, even hacked the redhat .deb file, but to no help.

The scanner function does work though.

---

### Post by Spherical on 2008-03-26
Ok, since I got it working, I might as well post it right?
Note that this is not with the official avasys driver! (I might wanna start a new topic for this?)
Ok, here we go:

[SIZE="4"]I assume you know how to work in the terminal, these are all terminal commands unless specified otherwise[/SIZE]
[SIZE="3"]All codes between '{' and '}' needs to be replaced with the corresponding values of the files you downloaded. Usually just hitting the [tab] button will autocomplete this[/SIZE]

Step one, remove the following:
All installed PIPS packages
```
sudo aptitude remove pips-*
```
Will tell you which are installed. You'll probably have to type them in manually.
Then, also remove
```
sudo aptitude remove libgutenprint2 foomatic-db-gutenprint cupsys-drivers-gutenprint
```

Also, you need to make sure that Ubuntu doesn't try to start the ekpd daemon when you startup your system. I have noticed not al the initialisation files aren't removed on removal. It's not an issue to leave it there, but you can remove it:
```
sudo rm /etc/init.d/ekpd
```

Now, you need to have Alien installed before you continue.
If you don't, install it with
```
sudo aptitude install alien
```

After that, get the gutenprint package, in my case the DX4450 because that's the one I have, but it's multi-printer-supported, from [openprinting.org]("http://openprinting.org/show_driver.cgi?driver=gutenprint")
Get the FHS (Printingdirs) from [here]("http://www.openprinting.org/download/printdriver/RPMS/noarch/fhs-printingdirs-0.2-1lsb3.1.noarch.rpm")

Ok, you got your packages right?
Wrong, you need to make your system LSB compliant, by installing the LSB:
```
sudo aptitude install lsb
```
Should do the job, but to be entirely sure, you can also run the following command, in stead of the previous. (I have not noticed any difference, it's up to you)
```
sudo aptitude install lsb-base lsb-core
```

Now that your system is LSB compliant, we need to get the downloaded rpm's converted to .deb files. easy job with alien:
```
sudo alien --scripts fsh-printingdirs-{versioncode}-noarch.rpm
sudo alien --scripts gutenprint-{version}-{architecture}.rpm
```

Ok, we got ourselves some nice deb files that should work. If you run into errors, you most probably don't have alien installed, or you're on the wrong architecture (64-bit or 32-bit), if that's not the case, feel free to start yelling at me for a better answer.

Ok, offcourse the .debs need installation. Easy as can be:
```
sudo dpkg -i fsh-printingdirs-{versioncode}-all.deb
sudo dpkg -i gutenprint-{version}-{architecture}.deb
```

Ok, think you're done yet?

Well, you are, but just to be sure, we're gonna run the following command once more:
```
sudo /etc/init.d/cupsys restart
```

Well, now you're all done!
At least, for the installing the driver part, we still need to tell CUPS there's a printer. But hey, we're free of the terminal now!

Just fire up (please, don't take that one literally) your printer manager (in KDE it's located in the system-settings, under Gnome I don't know)

Follow all the standard instructions (local USB/LPT printer) etc.
Now select the USB printer!!!
There should be two options for selecting the printer presented to you, one under USB and one under 'other', again, select the one under USB!

Just continue until you need to select the right driver.
Here, you select one of the following (Epson offcourse):
DX3850
DX4250
(Just because I know those two worked for me)

There might be others that work, but I haven't tried those. Feel free to experiment with which drivers you can select.

This procedure also works for printing over the network, offcourse, the location of the printer is different then, but the procedure of installing the driver stays the same.

If I'm not mistaken, all should work when you press the test button!
Most probably, the test-page won't be printed as you might want it to, but be assured that as far as my experience goes, it will work perfectly fine when you print from OpenOffice or a PDF reader or anything.

So far, I have not yet found a way to read-out the ink-levels. I might dig into the Avasys driver for that later. For now I'm just very happy I got her printing (or is a printer a 'he'?)

I hope I helped you out with this, if you still have questions, you're free to ask.

p.s.
The use of "aptitude" in stead of "apt-get" is just a habit of mine, just in case you wondered why.

---

### Post by micha137 on 2008-04-04
Hi there,
after messing around with the original epson drivers for days without succes I found the following solution:

Forget avasys, the broken(for ubuntu gutsy at least) epson drivers, and the lonesome and homeless ekpd files. dont install anything.

Just use the DX4050 driver from the Applications/settings/printing dialog box ( in my case from the xubuntu -panel ) that came with ubuntu and printing works like a charm.

I couldn't help cursing about epson after finding that  ](*,)

and praising the ubuntu team =D>

---

### Post by Spherical on 2008-04-04
It's getting weirder everyday with the Epson printers.

The procedure you describe just caused my Cups daemon to crash!

Yes, I tried it, didn't do anything but crashing down

---

### Post by Chelidon on 2008-04-04
Hmmm. This is making me apprehensive about the avasys driver that I got for my CX6000. Right now I'm using the CX5800 driver that came with my print manager, but it's very basic (I can't even change the orientation!).

I used to just use my printer through my Windows partition, since I've had such a bad time finding anything for it, but I'm even out of that option because my Windows decided to blow out its dll files a few weeks ago.

---

### Post by gavinjb on 2008-04-06
just started to try and setup my Epson DX4450, but when I try to run alien I get the following error:

```

sudo alien --scripts fhs-printingdirs-0.2-1lsb3.1.noarch.rpm
Package build failed. Here's the log:
dh_testdir
dh_testdir
dh_testroot
dh_clean -k -d
dh_installdirs
dh_installdocs
dh_installchangelogs
parsechangelog/debian: warning:     debian/changelog(l7): badly formatted heading line
LINE: - Reduced directories and links to /usr/share/ppd as standard locations
parsechangelog/debian: warning:     debian/changelog(l8): found change data where expected next heading or eof
LINE:   for PPDs. Distributions refused to ship directories in /opt and
Can't locate object method "init" via package "Dpkg::Changelog::Entry" at /usr/share/perl5/Dpkg/Changelog/Debian.pm line 260, <STDIN> line 8.
dpkg-parsechangelog: failure: changelog parser /usr/lib/dpkg/parsechangelog/debian gave error exit status 9
dh_installchangelogs: changelog parse failure
make: *** [binary-arch] Error 1
find: fhs-printingdirs-0.2: No such file or directory

```

Please note that I am currently using Ubutnu 8.04 through wubi as a test as I am looking at buying anew PC (Linux only) and I want to make sure I can get my all in one working first

---

### Post by Spherical on 2008-04-09
Looks to me as a version problem between 7.10 and 8.04

Can't really help you there, try google for newer versions is all I can think of right now.

The error produced is an Alien error, not an error in the procedure afaik

---

### Post by Hotwheelz79 on 2008-05-31
Just use the DX4050 driver from the Applications/settings/printing dialog box ( in my case from the xubuntu -panel ) that came with ubuntu and printing works like a charm.

Hi micha137,

Ok so u go the printer working using the DX4050 driver but want about scanning?

Do u have another solution for that part other than  the avasys 

Btw I will be installing 8.04 for a friend with this device.

Does that make it any easier?

Thanks.

:-)

---

