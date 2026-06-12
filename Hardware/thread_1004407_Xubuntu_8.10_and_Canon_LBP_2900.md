---
title: "Xubuntu 8.10 and Canon LBP 2900"
date: 2008-12-07
forum: Hardware
---

### Post by RomanIvanov on 2008-12-07
Hello All,

I have Xubuntu 8.10 with all updates up to (2008/12/03) on Dell Vostro 1510. I need to install printer Cannon LBP 2900 to it.

No luck in:
[https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/Canon_LBP_2900](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/Canon_LBP_2900)
[http://ph.ubuntuforums.com/showthread.php?t=967483](http://ph.ubuntuforums.com/showthread.php?t=967483)

But approach that is described in articles above worked like a charm for my Xubuntu 8.04. So my printer worked perfectly before update.

Question:
 - Does any body have a success story of installing LBP2900 on Xubuntu 8.10 ?
  
 - I noticed that some article are not strict to path of USB - /dev/usb/lp0 or /dev/usblp0. What is correct path for Ubuntu(Xubuntu) ?

Please help.

---

### Post by RomanIvanov on 2008-12-07
Here is my script of install: install_Cannon.sh (it was made after reading articles and practising in install\uninstall for hours).

I downloaded drivers from Canon official site([http://software.canon-europe.com/software/0031118.asp](http://software.canon-europe.com/software/0031118.asp)), and event tried new version of drivers - 1.80. No luck.

I still cant print neither from mousepad nor test page from properties of printer(Applications - Settings - Printing).

---

### Post by RomanIvanov on 2008-12-07
Strange behaviour after installation + reboot and command: 
 captstatusui -P LBP2900 
It shows window with no messages at all and my CPU become work up to 100% and never stop.

 captstatusui -P LBP2900 -e  - 100% of CPU but without UI window.

Does anybody know how to solve this ?

---

### Post by RomanIvanov on 2008-12-07
I even tried web interface "http://127.0.0.1:631" to set up the printer - behaviour is the same :
test page was sent to printer but printer does not print anything.


Sorry for flood of replies of me to myself - but I am little in despare :(.

---

### Post by RomanIvanov on 2008-12-08
dump, still pain :(.

---

### Post by RomanIvanov on 2008-12-14
I partly resolved the issue, ONLY FOR DESKTOP PC with Xubuntu 8.10:

1. Apply all steps from:
[https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/Canon_LBP_2900](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/Canon_LBP_2900)

2.  If you have the problem:
romani@romani-desktop:~$ captstatusui -P LBP2900
*** captstatusui Socket Error ***

run command : sudo /etc/init.d/ccpd restart

and now,
command : captstatusui -P LBP2900
have a right response.
With message "ready to print"

Printing proceeded successfully!

---

### Post by giruzz on 2009-04-28
> **RomanIvanov said:**
> I partly resolved the issue, ONLY FOR DESKTOP PC with Xubuntu 8.10:

run command : sudo /etc/init.d/ccpd restart



I found the same solution. Is there a way to automate this?

I'm asking because my dad uses this printer and he is 2000km away and he doesn't want to learn how to reset the daemon....so every time he has to print I need to connect using VNC and reset it manually :-(

thank you

giruzz

---

### Post by RomanIvanov on 2009-07-01
I have additional problem with printing after each restart - documents are not printed but added in queue.
As workaround I used 
```
sudo /etc/init.d/ccpd restart
```

Final Solution is, to make it work always without any cmd:
from the console type
```
sudo mousepad /etc/rc.local
```
and add at the end, before "exit 0"
```
/etc/init.d/ccpd start
```

---

### Post by bogyit on 2009-08-13
Doesn't work for me, when I give **sudo /etc/init.d/ccpd start** I receive **fail** message, even if I restart, with stop gives me OK. Permissions are set on the new script **ccpd** as the howto says, and I've also tried to remove everything and redo but nothing changes.. What can I do?

I'm on Xubuntu 8.10. Thanks.

---

### Post by RomanIvanov on 2009-08-13
Yes, in Xubuntu 9.04 I need to restart ccpd each time from command line. Did not found workaround.

---

### Post by RomanIvanov on 2009-11-24
I switched to Ubuntu 9.10.

Here is how to install the printer:

Read and do this, step by step attentively:
[https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/LBP3010](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/LBP3010)

I used 1.80 version of cannon drivers from cannon site [http://software.canon-europe.com/software/0031118.asp?model=](http://software.canon-europe.com/software/0031118.asp?model=) .

To install 1.80 you need additional packages that are absent in standard repository:
for (cndrvcups-common_1.80-1_i386) - [https://launchpad.net/ubuntu/karmic/i386/libcupsys2/1.3.9-17ubuntu1](https://launchpad.net/ubuntu/karmic/i386/libcupsys2/1.3.9-17ubuntu1)
for (cndrvcups-capt_1.80-1_i386) - [https://launchpad.net/ubuntu/karmic/i386/libstdc++5/1:3.3.6-17ubuntu1](https://launchpad.net/ubuntu/karmic/i386/libstdc++5/1:3.3.6-17ubuntu1)

Here is my log after installing drivers:
```
sudo /etc/init.d/cups restart
/usr/sbin/lpadmin -p LBP2900 -m CNCUPSLBP2900CAPTK.ppd -v ccp:/var/ccpd/fifo0 -E
sudo /usr/sbin/lpadmin -p LBP2900 -m CNCUPSLBP2900CAPTK.ppd -v ccp:/var/ccpd/fifo0 -E
sudo /usr/sbin/ccpdadmin -p LBP2900 -o /dev/usb/lp0
sudo cp /etc/init.d/ccpd /etc/init.d/ccpd.orig
gedit /etc/init.d/ccpd
sudo /etc/init.d/ccpd restart
sudo update-rc.d ccpd defaults 50
sudo /etc/init.d/ccpd restart

```

**Nuances:** 
if printer was switched on after PC is turned on - you need do
```
sudo /etc/init.d/ccpd restart
```
to begin print, else all print jobs are handled.

One more printer is appeared "LPB2900-2" just ignore it, and make "LBP2900" as default

---

### Post by RomanIvanov on 2010-11-14
It works for Ubuntu 10.04 without restarting ccpd and other problems!
Use [http://rosinka.rosix.ru/index.php?topic=292.msg1385;boardseen#new](http://rosinka.rosix.ru/index.php?topic=292.msg1385;boardseen#new)
(unfortunately it is in Russian, but you can translate it by google)

Here all steps but in English:
1. Switch off Printer 

1. install pre-install packages
```
sudo apt-get install libcupsys2
sudo apt-get install libstdc++5
```

2. Download Cannon drivers from official site unzip them install packages 
```
sudo dpkg -i cndrvcups-common_2.00-2_i386.deb
sudo dpkg -i cndrvcups-capt_2.00-2_i386.deb
```

3. Run
 ```
sudo /etc/init.d/cups restart
```
output:
```
 [OK]
```
             
4. Run
```
sudo /usr/sbin/lpadmin -p LBP2900 -m CNCUPSLBP2900CAPTK.ppd -v ccp:/var/ccpd/fifo0 -E
```
         
5. Run (registration of drinter in domain)
```
sudo /usr/sbin/ccpdadmin -p LBP2900 -o /dev/usb/lp0
```
Output:     
> CUPS_ConfigPath = /etc/cups/
 LOG Path        = None
 UI Port         = 59787

 Entry Num  : Spooler   : Backend   : FIFO path      : Device Path    : Status
 ----------------------------------------------------------------------------
     [0]    : LBP2900    : ccp       : /var/ccpd/fifo0    : /dev/usb/lp0 : New!!     
     
6. Switch ON Printer.

    
7.1 Backup /etc/init.d/ccpd
7.2 Run
```
gksudo gedit /etc/init.d/ccpd
```
and put new content for file         
```
#!/bin/sh
    # startup script for Canon Printer Daemon for CUPS (ccpd)

### BEGIN INIT INFO
# Provides:         ccpd
# Required-Start:   $local_fs $remote_fs $syslog $network $named
# Should-Start:     $ALL
# Required-Stop:    $syslog $remote_fs
# Default-Start:    2 3
# Default-Stop:     0 1 4 5 6
# Description:      Start Canon Printer Daemon for CUPS
### END INIT INFO


DAEMON=/usr/sbin/ccpd
LOCKFILE=/var/lock/subsys/ccpd
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
NAME=ccpd
DESC="Canon Printer Daemon for CUPS"

test -f $DAEMON || exit 0

. /lib/lsb/init-functions

case $1 in
  start)
        log_begin_msg "Starting $DESC: $NAME"
        start-stop-daemon --start --quiet --exec $DAEMON
        log_end_msg $?
        ;;
  stop)
        log_begin_msg "Stopping $DESC: $NAME"
        start-stop-daemon --stop --quiet --oknodo --exec $DAEMON
        log_end_msg $?
        ;;
  status)
        echo "$DESC: $NAME:" `pidof $NAME`
        ;;
  restart)
        log_begin_msg "Restarting $DESC: $NAME"
        start-stop-daemon --stop --quiet --oknodo --exec $DAEMON
        sleep 1
        start-stop-daemon --start --quiet --exec $DAEMON
        log_end_msg $?
        ;;
  *)
        echo "Usage: ccpd {start|stop|restart|status}"
        exit 1
        ;;
esac

exit 0

```

8. Run
```
sudo /etc/init.d/ccpd restart
```
output:
```
        * Restarting Canon Printer Daemon for CUPS: ccpd                        [ OK ]

```       

9. Run
```
sudo update-rc.d ccpd defaults 50
```
(selecting of non standard value for default is explaned in help)
Output:                     
>   update-rc.d: warning: ccpd start runlevel arguments (2 3 4 5) do not match LSB Default-Start values (2 3)
update-rc.d: warning: ccpd stop runlevel arguments (0 1 6) do not match LSB Default-Stop values (0 1 4 5 6)
 Adding system startup for /etc/init.d/ccpd ...
   /etc/rc0.d/K50ccpd -> ../init.d/ccpd
   /etc/rc1.d/K50ccpd -> ../init.d/ccpd
   /etc/rc6.d/K50ccpd -> ../init.d/ccpd
   /etc/rc2.d/S50ccpd -> ../init.d/ccpd
   /etc/rc3.d/S50ccpd -> ../init.d/ccpd
   /etc/rc4.d/S50ccpd -> ../init.d/ccpd
   /etc/rc5.d/S50ccpd -> ../init.d/ccpd               

Ignore warnings and go further
               
10. Open nemu -- Administration -- Printing, you can see two printers there LBP2900 &#1080; LBP2900-2.
According to Help we need to ignore second printer, BUT DO NOT remove it,
Right click over LBP2900 -> "Properties" and "Print test page"
         
11. Switch Off Printer.
   
12. Reboot PC
   
13. Switch on Printer. run
```
sudo /etc/init.d/ccpd status
```
output:
>   Canon Printer Daemon for CUPS: ccpd: 1818 1689              
You will have different numbers. It is important thet you have 2 numbers.
In you have only one number you have problem with ccpd demon.

14. Run
```
sudo captstatusui -P LBP2900
```
Output:
UI application should be opened with message "Ready to Print". It is OK.

15. Open System - Preferences - Startup Applications 
Press "Add" and put 
Name = "Canon Printing Status Monitor" 
Command = ```
captstatusui -e -P LBP2900
```
Info:
"-e" parameter make motinor be hidden till error is appear, for example "paper is absent"
                             
16. Make LBP2900 as default printer
manu Administration -> Printing. Select LBP2900, right click, "Set as Default"

---

