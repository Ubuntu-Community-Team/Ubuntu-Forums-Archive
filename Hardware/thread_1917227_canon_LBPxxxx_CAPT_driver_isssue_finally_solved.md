---
title: "canon LBPxxxx CAPT driver isssue finally solved"
date: 2012-01-29
forum: Hardware
---

### Post by frank.s on 2012-01-29
Hi Guys, pardon my cheerful title on this article, but I have finally solved my Canon CAPT - or LPTxxxx driver problem, after nearly 3 years of constant frustrations.

I have, over the years, downloaded the official debian drivers from canons official support sites since version 1.90 with no luck at all. My wife and kids all run MS Windows, and no one have had any problems with the windows drivers for our newly bought (in 2009) Canon LBP5050n LAN attached color iSENSYS printer - except me and my newly installed Ubuntu Karmic of course. Pretty damn humiliating! 

Everyone could use our new color laser printer except me. The time went on to Oneiric and CAPT drivers version 2.40, and I tried them all - still no joy! I even installed Oneiric on a complete vanilla PC to make my printer work - no luck at all.

A couple of days ago I gave it another try by running [Radu Cotescu]("http://radu.cotescu.com/how-to-install-canon-lbp-printers-in-ubuntu/")'s excellent script. I was very happy to see my Ubuntubox print its first printer test page ever on our LBP5050n - but alas, my luck ran out when I restarted my machine, and it had forgotten all about printing again.

Fortunately I decided to investigate it, and I stumbled upon [this page on help.ubuntu.com]("https://help.ubuntu.com/community/CanonCaptDrv190?action=show&redirect=HardwareSupportComponentsPrinters%2FCanonPrinters%2FCanon_LBP_2900"), and I noticed a small paragraph under the section "Restart and verify" that said: > This shows the process Id's for the two ccpd processes that should now be running. If you only see one then you still have a problem with the way the ccpd daemon is starting. Please check carefully you have completed all the steps above.
I promptly entered 
```
pidof ccpd
```
from the command line, and behold: Only one PID!
Then it dawned on me that the script that started the ccpd-daemon could be flawed.

I tried to install the script devised at [this page]("http://ubuntuforums.org/showthread.php?t=1315665") and it worked fine, except when I tried to run the ubuntu command ```
sudo service ccpd stop
```
It had no effect what so ever, so I wrote a highly incompatible script to fix the problem. Now I finally got my Canon printer to work as it is supposed to - service scripts and all (you don't even have to run update-rc.d, since the ccpd-driver script is already installed if you run Radu's script). Thanks to Radu, and a lot of other guys that have been fighting this problem for so many years. I'm now the happy owner of a Canon LBP5050n printer, that prints like a breeze from my Ubuntu Natty. I really hope that this will help someone out there.

I'm sorry to say, that I'm rather pissed off with Canon, since they have been reluctant to solve this problem on a popular platform as Ubuntu. I have informed them about this problem on more than one occasion, as I'm sure many others have, and I still can't imagine why this could be such a big issue to them, unless their programmers are complete idiots, which I find it hard to believe. Next time I go for HP, that's for sure.

Regards

- Frank

P.S. BTW, my script in /etc/init.d/ccpd now looks like this: ```

#!/bin/sh
# startup script for Canon Printer Daemon for CUPS (ccpd)
# Modified for Debian GNU/Linux


DAEMON=/usr/sbin/ccpd
LOCKFILE=/var/lock/subsys/ccpd
NAME=ccpd
DESC="Canon Printer Daemon for CUPS"

test -f $DAEMON || exit 0

. /lib/lsb/init-functions

export PATH=$PATH:/usr/local/sbin:/usr/local/bin

PIDS=`pidof ccpd`
test "z${PIDS}" != "z" && RUNNING=true || RUNNING=false

ccpd_start ()
{
  ccpd
  echo "ccpd started"
}

ccpd_stop ()
{
  for PID in `pidof ccpd`
  do
    kill -TERM $PID
  done
  echo "ccpd stopped"
}


case $1 in

    start)
        $RUNNING && echo "Already running" || ccpd_start
        ;;
        
    stop)
        $RUNNING && ccpd_stop || echo "ccpd is not running"
        ;;
    
    status)
        $RUNNING && echo "ccpd: "`pidof ccpd` || echo "ccpd is not running"
        ;;
    
    restart)
        ccpd_stop
        sleep 2
        ccpd_start
        ;;
    
    *)
            echo "Usage: ccpd {start|stop|restart|status}"
        exit 1
        ;;
esac
exit 0
```

---

### Post by frank.s on 2012-09-09
ALAS!! I have now purchased a new computer AMD64 bits with 4 cores, and I have tried to install the CAPT driver on this machine too.

Unfornunately I have had no luck what so ever. I have tried a million different ways to make the LBP printer driver work on this new machine, and I can't get any lifesigns out of the printer at all. It works fine on our Windows machines though :(

Now I'm fed up with Canon. I'm just waiting for the toners to run dry. Then I will buy a HP color laser instead, and ditch the Canon printer all together.

I don't want to waste more time and grief trying to make the &#"%/&#¤! Canon drivers work :mad:

---

### Post by pdc on 2012-09-10
so you have installed 64bit Ubuntu on this new " AMD64 bits with 4 cores" machine?

in post #11, 

[http://ubuntuforums.org/showthread.php?t=1982917&page=2](http://ubuntuforums.org/showthread.php?t=1982917&page=2)

Sivella provided guidance on installing 64bit drivers for the LBP series of printers; (in an earlier post, he provided successful guidance for 32bit); he says he is the french maintainer for the canon lbp series

he also provided guidance on 

> Due to a new cups update, it seems that usblp module is now blacklisted

I wonder if any of this would help you?

---

### Post by frank.s on 2012-09-20
Hi pdc,

Thanks for pointing me to Sivella's posting, but my printer is a LBP5050n, that is a networking printer, so the USB blacklist doesn't apply to my situation. I have had problems with the Linux drivers for this printer on my older 32 bit machine, every time there has been an distro-upgrade, and now it all starts over, and frankly I'm fed up.

I have installed several HP printers on Linux boxes, and thier driver setup works every time, with no hassle. Canon makes great hardware and fair drivers for the Windows platform, but their drivers, even for the most popular Linux distro (Ubuntu), sucks!

Sorry Canon, but it's not good enough, and I don't want to pull my hair out over again over this Canon driver, the next time Ubuntu decides that it time for a major upgrade.

But thanks again pdc, for trying to help. I really appreciate it :)

---

### Post by zazuge on 2012-09-21
thank you so much
me too i had problems with these damned canon drivers
but in oneiric radutesco driver was working
albeit i had to restart the printer and pc frequently
and in precise the LBP6000 worked yet the LBP5050 didn't 
yes you're right the problem was there was only one pid
thank you again for you tip
now i'll provide a tip to anyone here who may mistakenly think the problem is the driver when its the printer
pay attention to warning leds on the printer, if the printer react and you see change in the leds (a warning yellow or red light) then its not the driver its another problem (ink, paper) and sometimes the printer sleep so restart the printer frequently

---

