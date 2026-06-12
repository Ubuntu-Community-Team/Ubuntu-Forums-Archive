---
title: "Printing to Epson Stylus S20 T20 T20E T23 T26 T10 T11 Printers"
date: 2008-10-31
forum: Hardware
---

### Post by c_c on 2008-10-31
Hi All,
  Well the Epson Stylus series of printers has new additions - a lower end group which includes the following :-

  1. Stylus S20
  2. Stylus T20
  3. Stylus T20E
  4. Stylus T23
  5. Stylus T26
  6. Stylus T10
  7. Stylus T11

 Currently the openprinting database indicates that these printers are mostly 'paperweight'. However, there are divers available at avasys.jp that allow these printers to be used under Linux. The site has rpm based drivers available. But getting them to work on hardy was a little problematic since the documentation is written in a pretty obscure manner.

  Since I've managed to get these drivers going - I thought a small howto would be in order.

1.  To begin with - download the Fedora 9 rpms from the [site]("http://www.avasys.jp/lx-bin2/linux_e/ink/DL1.do").
2.  convert these packages into .debs with the command 'alien --scripts --keep-version pips-*.rpm'
3.  Install the debs with the command 'sudo dpkg -i ./pips-*.deb' or download from [here]("http://rapidshare.com/files/167463640/pips.tar.gz.html").
4.  You get a few errors like below :-

install: cannot create regular file `/etc/rc.d/init.d': No such file or directory
ln: creating symbolic link `/etc/rc.d/rc2.d/S11ekpd': No such file or directory
ln: creating symbolic link `/etc/rc.d/rc3.d/S11ekpd': No such file or directory
ln: creating symbolic link `/etc/rc.d/rc4.d/S11ekpd': No such file or directory
ln: creating symbolic link `/etc/rc.d/rc5.d/S11ekpd': No such file or directory
ln: creating symbolic link `/etc/rc.d/rc0.d/K89ekpd': No such file or directory
ln: creating symbolic link `/etc/rc.d/rc1.d/K89ekpd': No such file or directory
ln: creating symbolic link `/etc/rc.d/rc6.d/K89ekpd': No such file or directory

5.  Now create a file by running 'sudo vim /etc/init.d/ekpd'
6.  Copy the following into it

x-----------------------------------------------------------x
# Photo Image Print System
# Copyright (C) 2002-2005 EPSON AVASYS Corporation.
# Copyright (C) SEIKO EPSON CORPORATION 2002-2005.
#
# . /etc/rc.d/init.d/functions

PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
DAEMON=/usr/local/EPAva/core/ekpd
NAME=ekpd
PIDFILE=/var/run/$NAME.pid
DESC="EPSON Avasys printing daemon"

unset TMPDIR

test  -f $DAEMON || exit 0

OLDMASK=`umask`
umask 000

case "$1" in
start)
        pidlist=`pidof $NAME`
        if [ "x" = "x$pidlist" ]; then
                echo -n "Starting $NAME:"
          start-stop-daemon --start --quiet --pidfile "$PIDFILE" --exec $DAEMON
        fi
        ;;

stop)
        echo -n "Stopping ekpd:"
        start-stop-daemon --stop --retry 5  --name $NAME 
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
x----------------------------------------------------------------x

7.  'sudo chmod +x /etc/init.d/ekpd'
8.  Now install a few libraries by doing 'sudo apt-get install libtiff4 libpng2'
9.  make a link with this commands
    'sudo ln -s /usr/lib/libtiff.so.4.2.1 /usr/lib/libtiff.so.3'
10. and copy the config file for ekpd by 'sudo cp /usr/local/EPAva/printer/st20/ekpdrc_st20 /etc/ekpdrc'
11. Run 'sudo ekpd-tool' and check that the parameters are set to
    Printer Name : st<your printer number>
    Connection Method : <USB>
    Device Path : lp0
    Select the Defualt Printer checkbox if this is your default printer.
12. Now start ekpd with 'sudo /etc/init.d/ekpd start'
13. Add the printer using the cups web interface -> Start Firefox and use the url 'localhost:631'
14. Select Administration, Add Printer
15. Set a name, location and description
16. Select Epson Stylus Txx USB #1 from the dropdown list
17. Select Epson Stylus Txx Photo Image Print System (en) as the model
18. Now send a test page to the printer.

This should get your printer printing fine. I haven't tested too much the test page is quite ok.
Run 'ekpstm' to see a graphical output that shows the printer status and the ink levels.
Hope this helps.

---

### Post by t_eivind on 2008-12-20
> **c_c said:**
> Hi All,
  Well the Epson Stylus series of printers has new additions - a lower end group which includes the following :-

  1. Stylus S20
  2. Stylus T20
  3. Stylus T20E
  4. Stylus T23
  5. Stylus T26
  6. Stylus T10
  7. Stylus T11

 Currently the openprinting database indicates that these printers are mostly 'paperweight'. However, there are divers available at avasys.jp that allow these printers to be used under Linux. The site has rpm based drivers available. But getting them to work on hardy was a little problematic since the documentation is written in a pretty obscure manner.

  Since I've managed to get these drivers going - I thought a small howto would be in order.
.
.
.
This should get your printer printing fine. I haven't tested too much the test page is quite ok.
Run 'ekpstm' to see a graphical output that shows the printer status and the ink levels.
Hope this helps.

IT WORKS!!! My printer works. I think I faint! Thanks so very much c_c. Eternally thankful. :guitar:

---

### Post by swudee on 2008-12-27
OK

Sorry to be a bit of a nube here.
I have installed Alien and tried to convert the package from avasys,
but get errors.
The package unzips as pips-st20-Fedora9-3.1.0-CG.install rather than a .rpm file. Below is the error.

xoyffk@xoyffk-desktop:~$ sudo alien --scripts --keep-version pips-*.rpmFile "pips-*.rpm" not found.

or 

xoyffk@xoyffk-desktop:~$ sudo alien pips-st20-Fedora9-3.1.0-CG.install --scripts --keep-version pips-*.rpm

Please can someone advise where I am going wrong:confused:

Thanks

---

### Post by swudee on 2009-01-03
OK I finally noticed what I had missed

3. Install the debs with the command 'sudo dpkg -i ./pips-*.deb' or download from here.

I had missed the part where he said you could download them from here.
Also there seems to be a typo in line 8?

8. Now install a few libraries by doing 'sudo apt-get install libtiff4 libpng2'

Or is it just different in Intrepid 8.10 ?
anyway I made it libpng3, 2 being obsolete in 8.10.

AVASYS seem to have updated there drivers since C_C downloaded them, so unless they will make the rpm's available as well as the .install files, Alien it seems won't work.

---

### Post by JustinChuTw on 2009-01-08
> **c_c said:**
> 
The Epson Stylus series of printers has new additions - a lower end group which includes the following:

   1. Stylus S20
   2. Stylus T20
   3. Stylus T20E
   4. Stylus T23
   5. Stylus T26
   6. Stylus T10
   7. Stylus T11

.
.
.

5.  Now create a file by running 'sudo vim /etc/init.d/ekpd'
6.  Copy the following into it

x-----------------------------------------------------------x
# Photo Image Print System
# Copyright (C) 2002-2005 EPSON AVASYS Corporation.
# Copyright (C) SEIKO EPSON CORPORATION 2002-2005.
#
# . /etc/rc.d/init.d/functions

PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
DAEMON=/usr/local/EPAva/core/ekpd
NAME=ekpd
PIDFILE=/var/run/$NAME.pid
DESC="EPSON Avasys printing daemon"

unset TMPDIR

test  -f $DAEMON || exit 0

OLDMASK=`umask`
umask 000

case "$1" in
start)
        pidlist=`pidof $NAME`
        if [ "x" = "x$pidlist" ]; then
                echo -n "Starting $NAME:"
          start-stop-daemon --start --quiet --pidfile "$PIDFILE" --exec $DAEMON
        fi
        ;;

stop)
        echo -n "Stopping ekpd:"
        start-stop-daemon --stop --retry 5  --name $NAME 
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
x----------------------------------------------------------------x



I am new to Ubuntu and will appreciate it if someone can provide detailed instructions on how I can carry out the above.

Thank you very much for your assistance.

---

### Post by JunCTionS on 2009-01-30
Thanks for the great tutorial... really helped me in a moment of crisis (printing a thesis ;) )

As for the simplified instructions... I'll give it a try:

All codes in quotes are to be typed in a terminal (or console) window unless stated otherwise

--skip steps 1 & 2 if you wish to keep it simple--

3.0.1 [Download the .deb files from here]("http://rapidshare.com/files/167463640/pips.tar.gz.html") (too bad this forum has a filesize limit just below the largest file here, so please bear with the file hosting page... and whisper to the Original Poster if the link becomes broken, or try to do steps 1 & 2)
3.0.2 untar them with 'tar -xvf pips.tar.gz' or with your favorite compressed files application such as Ark.

3. Install the debs with the command 'sudo dpkg -i ./pips-*.deb' 
4. You get a few messages (ignore them ^_^)
5. write in the terminal 'sudo vim /etc/init.d/ekpd'
6. Copy the following into it

```

# Photo Image Print System
# Copyright (C) 2002-2005 EPSON AVASYS Corporation.
# Copyright (C) SEIKO EPSON CORPORATION 2002-2005.
#
# . /etc/rc.d/init.d/functions

PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
DAEMON=/usr/local/EPAva/core/ekpd
NAME=ekpd
PIDFILE=/var/run/$NAME.pid
DESC="EPSON Avasys printing daemon"

unset TMPDIR

test -f $DAEMON || exit 0

OLDMASK=`umask`
umask 000

case "$1" in
start)
pidlist=`pidof $NAME`
if [ "x" = "x$pidlist" ]; then
echo -n "Starting $NAME:"
start-stop-daemon --start --quiet --pidfile "$PIDFILE" --exec $DAEMON
fi
;;

stop)
echo -n "Stopping ekpd:"
start-stop-daemon --stop --retry 5 --name $NAME
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

6.a. This is not evident: Press Esc, then type ':w' (without quotes) then ':q' (and enter)
7. Type in the terminal 'sudo chmod +x /etc/init.d/ekpd'
8. Now install a few libraries by doing 'sudo apt-get install libtiff4 libpng3' (thanks swudee for updating the 2 to 3)
9. make a link with this commands
'sudo ln -s /usr/lib/libtiff.so.4.2.1 /usr/lib/libtiff.so.3'
10. and copy the config file for ekpd by 'sudo cp /usr/local/EPAva/printer/st20/ekpdrc_st20 /etc/ekpdrc'
11. Run 'sudo ekpd-tool' and check that the parameters are set to
Printer Name : st<your printer number>
Connection Method : <USB>
Device Path : lp0
Select the Defualt Printer checkbox if this is your default printer.
12. Now start ekpd with 'sudo /etc/init.d/ekpd start'

Here I got the following error
 /etc/init.d/ekpd: 2: to: not found
 Starting ekpd
which I safely ignored

13 Open Firefox and write 'localhost:631' in the address bar.
14. Select Administration, Add Printer
15. Set a name, location and description
16. Select Epson Stylus Txx USB #1 from the dropdown list
17. Select Epson Stylus Txx Photo Image Print System (en) as the model
18. Now if you want send a test page to the printer, or just start printing whatever you want... this test page can be time and ink consuming, particularly important if you're ink-stingy ;)

---

### Post by Paul Crawford on 2009-02-03
I installed a S20 with ubuntu 8.10 and it found the Epson '2000' driver that was automatically selected simply did not work - no sign of printer activity. I tried the above suggestions and now it works for open office printing, and fine for the CUPS test page, but not from firefox!

Looking through syslog I see this message:

Feb  3 10:43:34 ubuntu kernel: [ 3888.812235] pips-filter[7768]: segfault at 0 ip b7c8bda0 sp bfc2cbd0 error 4 in libc-2.8.90.so[b7c15000+158000]

Any ideas of what is broken here?

---

### Post by etau on 2009-02-03
Just want to say a **thank you**!

---

### Post by jbuczek on 2009-02-06
These tutorials are broken.

The Avasys.jp site referenced in the first message by C_C has replaced the RPM files with an INSTALL file so alien fails and the process fails at step 2.

The alternate site recommended in a following message by JunCTionS:

rapidshare.com

times out every time if you try to use it as a "free user".  I assume it will work if you cough up the cash for  a membership.

---

### Post by cariboo on 2009-02-06
The .install file is an executeable all you have to is make it executeable by opening a terminal and cding it to the directory where the file is located and typing:

```
chmod +x *install
```

then type:

```
sudo ./*install
```

The above command assumes there are no aother files in the directory with an install extension.

Jim

---

### Post by djk_srs on 2009-03-25
Hi all, if you want T20/T20E work with simple way, try this :
simply choose C64 driver in the list of Epson printer driver
I have try with my T20E and its working good as I want.....
This C64 driver can use on C90 and C53 printer.

---

### Post by dave66 on 2009-06-30
Thanks for the thread/posts. Have Epson S20 working with my Dell Mini-9. One thing to note for Mini-9 owners/users when you extract the pips you will need to repackage the .deb as lpia's, to do this use this handy script:

[http://ubuntuforums.org/showpost.php?p=6528287&postcount=28](http://ubuntuforums.org/showpost.php?p=6528287&postcount=28)

---

### Post by dave66 on 2009-06-30
> **dave66 said:**
> Thanks for the thread/posts. Have Epson S20 working with my Dell Mini-9. One thing to note for Mini-9 owners/users when you extract the pips you will need to repackage the .deb as lpia's, to do this use this handy script:

[http://ubuntuforums.org/showpost.php?p=6528287&postcount=28](http://ubuntuforums.org/showpost.php?p=6528287&postcount=28)

Spoke too soon :(

What I should have written is the Mini-9 will print a test page on the Epson S20 but if I try print from an application (gedit/firefox) or from the command line (lpr <filename>) I get nadda, zip, nothing ... eventually print manager claims the printer may not be connected!

Any ideas?

---

### Post by dave66 on 2009-07-06
Ok, so something strange is happening. I have installed the printer and I can get it print a file from terminal using lp filename.txt it works fine but if I try print from any application (such as gedit) the job is sent and in "Manage Print Jobs" I see the job but that status is listed as Stopped.

I feel I'm so close, yet so far :confused:

I'd really appreciate any help, please ....

---

### Post by c_c on 2009-07-09
Hi,
  Well jaunty supports these printers. Just install the printer with the Epson Stylus 20 CUPS+Gutenprint v5.2.3 driver.
  I can't figure out a way of getting the ink levels though.

---

### Post by dave66 on 2009-07-09
> **c_c said:**
> Hi,
  Well jaunty supports these printers. Just install the printer with the Epson Stylus 20 CUPS+Gutenprint v5.2.3 driver.
  I can't figure out a way of getting the ink levels though.

Many, Many thanks for your reply, it is really appreciate, I'm at a point where either the printer or me is going to be killed!

I'm a noob, but fairly literate and I'm learning quickly. Is there any chance you could explain how to do what you suggest (using the Gutenprint driver). I'm up against the proverbial 8 ball today as I'm supposed to be sending out 10 PCs with the printers.

---

### Post by mindaslab on 2009-09-03
[http://www.avasys.jp](http://www.avasys.jp) is no longer available! I think one must download the deb files and continue

---

### Post by Tjawi on 2009-09-26
Hi There,

I used Ubuntu 9.04 Jaunty, and I just installed driver for T11 last night.

When I plugged in the USB cable to my computer, the computer automatically recognized it that the printer was T11. Great! Then I just follow the OS's recommendations to use T20 driver, and I have no problem at all!

The one significant feature that I miss in this driver (compare to Window's driver) it the menu to calibrate the printhead position (line allignment). In Windows' I could ask the printer to print some alignment reference, and then adjust accordingly. Does anybody know how to do it in Linux?

Or should I calibrate in Windows, then use it in Ubuntu? Does anybody know if the calibration value is stored within the printer (or stored in computer)?

Thanks!

---

### Post by Screwbottle on 2009-11-24
> **mindaslab said:**
> [http://www.avasys.jp](http://www.avasys.jp) is no longer available! I think one must download the deb files and continue

Hey there Mindaslab

AVASYS is there, just drop the www. so full URL is [http://avasys.jp/eng](http://avasys.jp/eng) (if you are wanting the page in English). I've just downloaded the latest drivers as of 18:57 CAT / SAST time Tuesday 24th November 2009.

I've just received this printer today as a gift from my wife :p:), so the first thing I did was look for drivers to get it to work on Ubuntu 9.10 Karmic Koala

Cheers
Screwbottle

---

### Post by Screwbottle on 2009-11-24
> **Tjawi said:**
> Does anybody know if the calibration value is stored within the printer (or stored in computer)?


Hi Tjawi

It is stored in both printer and Windows registry, not too sure why this is so for Windows. The calibration is mainly used when one changes the cartridges and at a later time the print head. The slight specification differences between the original fitted cartridge/printhead and the replacements is minute but does affect the print. So this is why the calibration option is available, to align these micrometer differences between the cartridges/printheads.

So your logic is sound, adjust in windows, and all should be fine in Linux. But here's my fly in the ointment, what do you do if you only use Linux. Hmmmmmmm!!!!! will have to talk to AVASYS about this ;).

Cheers

---

### Post by leandromartinez98 on 2010-01-24
I bought a T24, which is essentially identical to the T23, and I got it working with the suggested T20 driver. However, instead of printing at 26 ppm as it says, it is printing very slowly, about 0.5 ppm. Even in economy-fast mode it takes more than a minute per page. 

Is this a driver problem? Should I try installing other drivers or the available T20 driver from Ubuntu is the one described here? 

If not, do you also experience this kind of printing speed (or slowness)?

---

### Post by rider_sss on 2010-01-31
I have the T23 and with 9.04 everything was alright. I changed the URL to: "epson:/dev/usb/lp0" and selected "cx 5600 cups + guteprint v5.0.2 simplified"

Now with Ubuntu Karmic it doesnt work anymore. 
I also tried this howto but without success.. 

any ideas ? I would really like to get it working with ubuntu Karmic.

thanks !

---

### Post by leandromartinez98 on 2010-01-31
I'm using the Stylus T20 driver. It works, but I think the printer
is too slow. But I tried in Windows and it is slow too, so I think
the problem is that the printer is bad indeed. I have just accepted
that and I suggest other people not to buy the T23/T24 printers if
they want some speed.

---

