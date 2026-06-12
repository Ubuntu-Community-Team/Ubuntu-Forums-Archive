---
title: "Error contacting apcupsd @ localhost:3551: Connection refused"
date: 2011-06-08
forum: Hardware
---

### Post by sefs on 2011-06-08
Hi all,

I am trying to get apcupsd going. I have installed it thru synaptic, set it up accordingly to the various guides one can find across the net.

When I run "acpaccess"  I get the following error.

"Error contacting apcupsd @ localhost:3551: Connection refused"

What, if anything, can I do to rectify the above situtation.

I am on Ubuntu Lucid 10.04.2 Desktop.

Thanks.

---

### Post by tgalati4 on 2011-06-08
Review the contents of:

cat /var/log/apcupsd.status
cat /var/log/apcupsd.events

You won't get a status file unless you turn it on in the config file.

Is the apcupsd daemon running?

ps -ef | grep apcupsd

If the daemon is running and you have the status file activated, you should get something like:

(for a Dumb UPS)

tgalati4@tubuntu2:~$ apcaccess
APC      : 001,020,0518
DATE     : Fri Jun 03 13:17:51 PDT 2011
HOSTNAME : tubuntu2
RELEASE  : 3.12.4
VERSION  : 3.12.4 (19 August 2006) debian
UPSNAME  : TerryLab
CABLE    : Custom Cable Simple
MODEL    : DUMB UPS Driver
UPSMODE  : Net Master
STARTTIME: Fri Jun 03 13:17:44 PDT 2011
SHARE    : NetworkUPS
STATUS   : ONLINE SLAVEDOWN
MBATTCHG : 5 Percent
MINTIMEL : 5 Minutes
MAXTIME  : 30 Seconds
NUMXFERS : 0
TONBATT  : 0 seconds
CUMONBATT: 0 seconds
XOFFBATT : N/A
STATFLAG : 0x07000808 Status Flag
END APC  : Wed Jun 08 19:51:30 PDT 2011

(Output for a Smart UPS)

tgalati4@hardy-back:~$ apcaccess
APC      : 001,055,1358
DATE     : Wed Jun 08 19:51:27 PDT 2011
HOSTNAME : hardy-back
RELEASE  : 3.14.2
VERSION  : 3.14.2 (15 September 2007) debian
UPSNAME  : BkPro470
CABLE    : Custom Cable Smart
MODEL    : BACK-UPS PRO 420
UPSMODE  : Stand Alone
STARTTIME: Sat May 14 13:05:37 PDT 2011
LINEFAIL : OK
BATTSTAT : OK
MAINS    : OK
STATFLAG : 0x07000008 Status Flag
STATUS   : ONLINE 
LINEV    : 115.9 Volts
LOADPCT  :   6.5 Percent Load Capacity
BCHARGE  : 100.0 Percent
TIMELEFT :  40.0 Minutes
MBATTCHG : 5 Percent
MINTIMEL : 2 Minutes
MAXTIME  : 180 Seconds
MAXLINEV : 117.3 Volts
MINLINEV : 115.9 Volts
OUTPUTV  : 115.9 Volts
SENSE    : High
DWAKE    : 000 Seconds
DSHUTD   : 020 Seconds
DLOWBATT : 02 Minutes
LOTRANS  : 106.0 Volts
HITRANS  : 127.0 Volts
RETPCT   : 000.0 Percent
ALARMDEL : 5 seconds
BATTV    : 13.8 Volts
LINEFREQ : 60.0 Hz
LASTXFER : Unacceptable line voltage changes
NUMXFERS : 9
XONBATT  : Fri Jun 03 18:49:44 PDT 2011
TONBATT  : 0 seconds
CUMONBATT: 22 seconds
XOFFBATT : Fri Jun 03 18:49:46 PDT 2011
LASTSTEST: Sat May 28 14:21:37 PDT 2011
SELFTEST : NO
STESTI   : 336
STATFLAG : 0x07000008 Status Flag
REG1     : 0x00 Register 1
REG2     : 0x00 Register 2
REG3     : 0x00 Register 3
MANDATE  : 04/02/98
SERIALNO : FB9814345084
BATTDATE : 10/05/11
NOMOUTV  : 115
NOMBATTV :  12.0
FIRMWARE : 11.1.D
APCMODEL : DWD
END APC  : Wed Jun 08 19:51:45 PDT 2011


So the fact that you are not getting anything could mean the daemon is not running.

Did you start the daemon?

sudo /etc/init.d/apcupsd restart

Did you set the default start flag? Set ISCONFIGURED to yes in /etc/default/apcupsd

tgalati4@hardy-back:$ cat /etc/default/apcupsd
# Defaults for apcupsd initscript

# Apcupsd-devel internal configuration
APCACCESS=/sbin/apcaccess
ISCONFIGURED=yes

These services require a little work on your part as you have discovered.

---

### Post by sefs on 2011-06-09
Hi here is what the info looks like...

cat /var/log/apcupsd.status
```

cat: /var/log/apcupsd.status: No such file or directory

```

cat /var/log/apcupsd.events
```

Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Mon Feb 14 10:25:20 AST 2011  apcupsd error shutdown completed
Mon Feb 14 18:22:49 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Mon Feb 14 18:22:49 AST 2011  apcupsd error shutdown completed
Tue Feb 15 09:15:23 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Tue Feb 15 09:15:23 AST 2011  apcupsd error shutdown completed
Tue Feb 15 18:24:45 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Tue Feb 15 18:24:45 AST 2011  apcupsd error shutdown completed
Wed Feb 16 08:31:29 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Wed Feb 16 08:31:29 AST 2011  apcupsd error shutdown completed
Wed Feb 16 18:31:57 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Wed Feb 16 18:31:57 AST 2011  apcupsd error shutdown completed
Wed Feb 16 18:52:52 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Wed Feb 16 18:52:52 AST 2011  apcupsd error shutdown completed
Wed Feb 16 20:34:55 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Wed Feb 16 20:34:55 AST 2011  apcupsd error shutdown completed
Thu Feb 17 09:35:48 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Thu Feb 17 09:35:48 AST 2011  apcupsd error shutdown completed
Thu Feb 17 16:46:55 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Thu Feb 17 16:46:55 AST 2011  apcupsd error shutdown completed
Fri Feb 18 04:31:44 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Fri Feb 18 04:31:44 AST 2011  apcupsd error shutdown completed
Fri Feb 18 08:42:48 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Fri Feb 18 08:42:48 AST 2011  apcupsd error shutdown completed
Fri Feb 18 18:18:43 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Fri Feb 18 18:18:43 AST 2011  apcupsd error shutdown completed
Sat Feb 19 08:03:26 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Sat Feb 19 08:03:26 AST 2011  apcupsd error shutdown completed
Sat Feb 19 11:19:13 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Sat Feb 19 11:19:13 AST 2011  apcupsd error shutdown completed
Sat Feb 19 11:22:36 AST 2011  apcupsd exiting, signal 15
Sat Feb 19 11:36:01 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Sat Feb 19 11:36:01 AST 2011  apcupsd error shutdown completed
Sat Feb 19 19:45:16 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Sat Feb 19 19:45:16 AST 2011  apcupsd error shutdown completed
Sat Feb 19 21:03:37 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Sat Feb 19 21:03:37 AST 2011  apcupsd error shutdown completed
Sat Feb 19 21:35:32 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Sat Feb 19 21:35:32 AST 2011  apcupsd error shutdown completed
Sun Feb 20 00:27:23 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Sun Feb 20 00:27:23 AST 2011  apcupsd error shutdown completed
Sun Feb 20 04:36:30 AST 2011  apcupsd 3.14.6 (16 May 2009) debian startup succeeded
Sun Feb 20 05:00:22 AST 2011  apcupsd exiting, signal 15
Sun Feb 20 05:00:22 AST 2011  apcupsd shutdown succeeded
Sun Feb 20 10:16:36 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Sun Feb 20 10:16:36 AST 2011  apcupsd error shutdown completed
Sun Feb 20 18:56:00 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Sun Feb 20 18:56:00 AST 2011  apcupsd error shutdown completed
Sun Feb 20 23:57:19 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Sun Feb 20 23:57:19 AST 2011  apcupsd error shutdown completed
Mon Feb 21 08:18:26 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Mon Feb 21 08:18:26 AST 2011  apcupsd error shutdown completed
Mon Feb 21 18:26:05 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Mon Feb 21 18:26:05 AST 2011  apcupsd error shutdown completed
Tue Feb 22 07:53:09 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Tue Feb 22 07:53:09 AST 2011  apcupsd error shutdown completed
Wed Feb 23 08:28:28 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Wed Feb 23 08:28:28 AST 2011  apcupsd error shutdown completed
Wed Feb 23 18:12:28 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Wed Feb 23 18:12:28 AST 2011  apcupsd error shutdown completed
Thu Feb 24 03:20:01 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Thu Feb 24 03:20:01 AST 2011  apcupsd error shutdown completed
Thu Feb 24 08:13:22 AST 2011  apcupsd 3.14.6 (16 May 2009) debian startup succeeded
Thu Feb 24 09:29:14 AST 2011  apcupsd exiting, signal 15
Thu Feb 24 09:29:14 AST 2011  apcupsd shutdown succeeded
Thu Feb 24 20:37:00 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Thu Feb 24 20:37:00 AST 2011  apcupsd error shutdown completed
Fri Feb 25 09:12:21 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Fri Feb 25 09:12:21 AST 2011  apcupsd error shutdown completed
Fri Feb 25 18:21:44 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Fri Feb 25 18:21:44 AST 2011  apcupsd error shutdown completed
Sat Feb 26 07:38:32 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Sat Feb 26 07:38:32 AST 2011  apcupsd error shutdown completed
Sat Feb 26 16:40:20 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Sat Feb 26 16:40:20 AST 2011  apcupsd error shutdown completed
Sun Feb 27 11:28:13 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Sun Feb 27 11:28:13 AST 2011  apcupsd error shutdown completed
Mon Feb 28 09:17:11 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Mon Feb 28 09:17:11 AST 2011  apcupsd error shutdown completed
Mon Feb 28 15:20:07 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Mon Feb 28 15:20:07 AST 2011  apcupsd error shutdown completed
Mon Feb 28 22:01:08 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Mon Feb 28 22:01:08 AST 2011  apcupsd error shutdown completed
Tue Mar 01 07:24:20 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Tue Mar 01 07:24:20 AST 2011  apcupsd error shutdown completed
Tue Mar 01 18:45:28 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Tue Mar 01 18:45:28 AST 2011  apcupsd error shutdown completed
Wed Mar 02 08:32:14 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Wed Mar 02 08:32:14 AST 2011  apcupsd error shutdown completed
Wed Mar 02 09:57:02 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Wed Mar 02 09:57:02 AST 2011  apcupsd error shutdown completed
Wed Mar 02 10:15:20 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Wed Mar 02 10:15:20 AST 2011  apcupsd error shutdown completed
Wed Mar 02 18:21:24 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Wed Mar 02 18:21:24 AST 2011  apcupsd error shutdown completed
Fri Mar 04 09:13:33 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Fri Mar 04 09:13:33 AST 2011  apcupsd error shutdown completed
Fri Mar 04 10:33:38 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Fri Mar 04 10:33:38 AST 2011  apcupsd error shutdown completed
Fri Mar 04 16:36:55 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Fri Mar 04 16:36:55 AST 2011  apcupsd error shutdown completed
Sat Mar 05 08:00:19 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Sat Mar 05 08:00:19 AST 2011  apcupsd error shutdown completed
Sat Mar 05 15:57:34 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Sat Mar 05 15:57:34 AST 2011  apcupsd error shutdown completed
Sun Mar 06 10:19:54 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Sun Mar 06 10:19:54 AST 2011  apcupsd error shutdown completed
Sun Mar 06 16:35:08 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Sun Mar 06 16:35:08 AST 2011  apcupsd error shutdown completed
Mon Mar 07 02:25:38 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Mon Mar 07 02:25:38 AST 2011  apcupsd error shutdown completed
Mon Mar 07 08:45:24 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Mon Mar 07 08:45:24 AST 2011  apcupsd error shutdown completed
Mon Mar 07 15:46:10 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Mon Mar 07 15:46:10 AST 2011  apcupsd error shutdown completed
Mon Mar 07 18:27:53 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Mon Mar 07 18:27:53 AST 2011  apcupsd error shutdown completed
Tue Mar 08 09:00:03 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Tue Mar 08 09:00:03 AST 2011  apcupsd error shutdown completed
Wed Mar 09 08:19:51 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Wed Mar 09 08:19:51 AST 2011  apcupsd error shutdown completed
Wed Mar 09 18:23:36 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Wed Mar 09 18:23:36 AST 2011  apcupsd error shutdown completed
Wed Mar 09 22:49:15 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Wed Mar 09 22:49:15 AST 2011  apcupsd error shutdown completed
Thu Mar 10 06:26:52 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Thu Mar 10 06:26:52 AST 2011  apcupsd error shutdown completed
Thu Mar 10 22:20:46 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Thu Mar 10 22:20:46 AST 2011  apcupsd error shutdown completed
Fri Mar 11 08:50:44 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Fri Mar 11 08:50:44 AST 2011  apcupsd error shutdown completed
Fri Mar 11 18:10:20 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Fri Mar 11 18:10:20 AST 2011  apcupsd error shutdown completed
Sat Mar 12 22:36:54 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Sat Mar 12 22:36:54 AST 2011  apcupsd error shutdown completed
Sun Mar 13 06:56:22 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Sun Mar 13 06:56:22 AST 2011  apcupsd error shutdown completed
Sun Mar 13 13:55:43 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Sun Mar 13 13:55:43 AST 2011  apcupsd error shutdown completed
Sun Mar 13 14:01:09 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Sun Mar 13 14:01:09 AST 2011  apcupsd error shutdown completed
Sun Mar 13 17:42:03 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Sun Mar 13 17:42:03 AST 2011  apcupsd error shutdown completed
Mon Mar 14 09:52:32 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Mon Mar 14 09:52:32 AST 2011  apcupsd error shutdown completed
Mon Mar 14 19:28:34 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Mon Mar 14 19:28:34 AST 2011  apcupsd error shutdown completed
Tue Mar 15 08:24:52 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Tue Mar 15 08:24:52 AST 2011  apcupsd error shutdown completed
Wed Mar 16 08:15:35 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Wed Mar 16 08:15:35 AST 2011  apcupsd error shutdown completed
Wed Mar 16 18:41:48 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Wed Mar 16 18:41:48 AST 2011  apcupsd error shutdown completed
Thu Mar 17 10:02:09 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Thu Mar 17 10:02:09 AST 2011  apcupsd error shutdown completed
Thu Mar 17 18:30:11 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Thu Mar 17 18:30:11 AST 2011  apcupsd error shutdown completed
Fri Mar 18 07:32:49 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Fri Mar 18 07:32:49 AST 2011  apcupsd error shutdown completed
Fri Mar 18 19:35:42 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Fri Mar 18 19:35:42 AST 2011  apcupsd error shutdown completed
Fri Mar 18 23:31:22 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Fri Mar 18 23:31:22 AST 2011  apcupsd error shutdown completed
Sat Mar 19 07:54:43 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Sat Mar 19 07:54:43 AST 2011  apcupsd error shutdown completed
Sun Mar 20 09:33:16 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Sun Mar 20 09:33:16 AST 2011  apcupsd error shutdown completed
Mon Mar 21 10:36:52 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Mon Mar 21 10:36:52 AST 2011  apcupsd error shutdown completed
Mon Mar 21 18:40:43 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Mon Mar 21 18:40:43 AST 2011  apcupsd error shutdown completed
Tue Mar 22 08:53:55 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Tue Mar 22 08:53:55 AST 2011  apcupsd error shutdown completed
Tue Mar 22 16:36:17 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Tue Mar 22 16:36:17 AST 2011  apcupsd error shutdown completed
Wed Mar 23 03:05:40 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Wed Mar 23 03:05:40 AST 2011  apcupsd error shutdown completed
Wed Mar 23 10:25:54 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Wed Mar 23 10:25:54 AST 2011  apcupsd error shutdown completed
Thu Mar 24 08:48:42 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Thu Mar 24 08:48:42 AST 2011  apcupsd error shutdown completed
Fri Mar 25 10:28:27 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Fri Mar 25 10:28:27 AST 2011  apcupsd error shutdown completed
Fri Mar 25 17:55:29 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Fri Mar 25 17:55:29 AST 2011  apcupsd error shutdown completed
Sat Mar 26 07:57:58 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Sat Mar 26 07:57:58 AST 2011  apcupsd error shutdown completed
Sun Mar 27 04:11:37 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Sun Mar 27 04:11:37 AST 2011  apcupsd error shutdown completed
Mon Mar 28 11:59:22 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Mon Mar 28 11:59:22 AST 2011  apcupsd error shutdown completed
Tue Mar 29 07:21:43 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Tue Mar 29 07:21:43 AST 2011  apcupsd error shutdown completed
Tue Mar 29 18:08:30 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Tue Mar 29 18:08:30 AST 2011  apcupsd error shutdown completed
Wed Mar 30 02:31:49 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Wed Mar 30 02:31:49 AST 2011  apcupsd error shutdown completed
Wed Mar 30 09:18:03 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Wed Mar 30 09:18:03 AST 2011  apcupsd error shutdown completed
Wed Mar 30 19:32:43 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Wed Mar 30 19:32:43 AST 2011  apcupsd error shutdown completed
Thu Mar 31 06:37:48 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Thu Mar 31 06:37:48 AST 2011  apcupsd error shutdown completed
Thu Mar 31 11:03:47 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Thu Mar 31 11:03:47 AST 2011  apcupsd error shutdown completed
Thu Mar 31 18:06:03 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Thu Mar 31 18:06:03 AST 2011  apcupsd error shutdown completed
Fri Apr 01 07:56:16 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Fri Apr 01 07:56:16 AST 2011  apcupsd error shutdown completed
Fri Apr 01 17:34:10 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Fri Apr 01 17:34:10 AST 2011  apcupsd error shutdown completed
Fri Apr 01 17:38:13 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Fri Apr 01 17:38:13 AST 2011  apcupsd error shutdown completed
Fri Apr 01 18:37:45 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Fri Apr 01 18:37:45 AST 2011  apcupsd error shutdown completed
Sat Apr 02 21:19:13 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Sat Apr 02 21:19:13 AST 2011  apcupsd error shutdown completed
Sun Apr 03 09:10:38 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Sun Apr 03 09:10:38 AST 2011  apcupsd error shutdown completed
Mon Apr 04 09:00:53 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Mon Apr 04 09:00:53 AST 2011  apcupsd error shutdown completed
Mon Apr 04 17:29:09 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Mon Apr 04 17:29:09 AST 2011  apcupsd error shutdown completed
Tue Apr 05 06:46:49 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Tue Apr 05 06:46:49 AST 2011  apcupsd error shutdown completed
Tue Apr 05 17:31:09 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Tue Apr 05 17:31:09 AST 2011  apcupsd error shutdown completed
Wed Apr 06 02:13:11 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Wed Apr 06 02:13:11 AST 2011  apcupsd error shutdown completed
Wed Apr 06 08:46:32 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Wed Apr 06 08:46:32 AST 2011  apcupsd error shutdown completed
Thu Apr 07 08:13:41 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Thu Apr 07 08:13:41 AST 2011  apcupsd error shutdown completed
Thu Apr 07 21:59:47 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Thu Apr 07 21:59:47 AST 2011  apcupsd error shutdown completed
Fri Apr 08 05:27:23 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Fri Apr 08 05:27:23 AST 2011  apcupsd error shutdown completed
Fri Apr 08 10:26:49 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Fri Apr 08 10:26:49 AST 2011  apcupsd error shutdown completed
Sun Apr 10 19:54:00 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Sun Apr 10 19:54:00 AST 2011  apcupsd error shutdown completed
Mon Apr 11 07:02:39 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Mon Apr 11 07:02:39 AST 2011  apcupsd error shutdown completed
Mon Apr 11 17:24:45 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Mon Apr 11 17:24:45 AST 2011  apcupsd error shutdown completed
Mon Apr 11 20:07:10 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Mon Apr 11 20:07:10 AST 2011  apcupsd error shutdown completed
Tue Apr 12 18:05:21 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Tue Apr 12 18:05:21 AST 2011  apcupsd error shutdown completed
Tue Apr 12 22:15:27 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Tue Apr 12 22:15:27 AST 2011  apcupsd error shutdown completed
Thu Apr 14 03:49:10 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Thu Apr 14 03:49:10 AST 2011  apcupsd error shutdown completed
Thu Apr 14 08:14:26 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Thu Apr 14 08:14:26 AST 2011  apcupsd error shutdown completed
Thu Apr 14 08:25:06 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Thu Apr 14 08:25:06 AST 2011  apcupsd error shutdown completed
Fri Apr 15 17:25:25 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Fri Apr 15 17:25:25 AST 2011  apcupsd error shutdown completed
Fri Apr 15 18:12:15 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Fri Apr 15 18:12:15 AST 2011  apcupsd error shutdown completed
Sat Apr 16 10:34:51 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Sat Apr 16 10:34:51 AST 2011  apcupsd error shutdown completed
Sat Apr 16 13:31:33 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Sat Apr 16 13:31:33 AST 2011  apcupsd error shutdown completed
Sat Apr 16 17:11:05 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Sat Apr 16 17:11:05 AST 2011  apcupsd error shutdown completed
Sun Apr 17 10:00:06 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Sun Apr 17 10:00:06 AST 2011  apcupsd error shutdown completed
Mon Apr 18 07:35:31 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Mon Apr 18 07:35:31 AST 2011  apcupsd error shutdown completed
Mon Apr 18 16:46:02 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Mon Apr 18 16:46:02 AST 2011  apcupsd error shutdown completed
Tue Apr 19 16:38:53 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Tue Apr 19 16:38:53 AST 2011  apcupsd error shutdown completed
Wed Apr 20 17:55:54 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Wed Apr 20 17:55:54 AST 2011  apcupsd error shutdown completed
Wed Apr 20 19:21:24 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Wed Apr 20 19:21:24 AST 2011  apcupsd error shutdown completed
Wed Apr 20 20:39:13 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Wed Apr 20 20:39:13 AST 2011  apcupsd error shutdown completed
Thu Apr 21 08:09:01 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Thu Apr 21 08:09:01 AST 2011  apcupsd error shutdown completed
Thu Apr 21 21:01:00 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Thu Apr 21 21:01:00 AST 2011  apcupsd error shutdown completed
Fri Apr 22 10:11:43 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Fri Apr 22 10:11:43 AST 2011  apcupsd error shutdown completed
Fri Apr 22 10:13:54 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Fri Apr 22 10:13:54 AST 2011  apcupsd error shutdown completed
Fri Apr 22 11:26:47 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Fri Apr 22 11:26:47 AST 2011  apcupsd error shutdown completed
Fri Apr 22 18:21:36 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Fri Apr 22 18:21:36 AST 2011  apcupsd error shutdown completed
Sun Apr 24 08:07:51 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Sun Apr 24 08:07:51 AST 2011  apcupsd error shutdown completed
Sun Apr 24 08:50:30 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Sun Apr 24 08:50:30 AST 2011  apcupsd error shutdown completed
Sun Apr 24 08:52:01 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Sun Apr 24 08:52:01 AST 2011  apcupsd error shutdown completed
Sun Apr 24 08:52:59 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Sun Apr 24 08:52:59 AST 2011  apcupsd error shutdown completed
Mon Apr 25 07:30:30 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Mon Apr 25 07:30:30 AST 2011  apcupsd error shutdown completed
Tue Apr 26 08:45:30 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Tue Apr 26 08:45:30 AST 2011  apcupsd error shutdown completed
Wed Apr 27 07:26:03 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Wed Apr 27 07:26:03 AST 2011  apcupsd error shutdown completed
Thu Apr 28 06:37:39 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Thu Apr 28 06:37:39 AST 2011  apcupsd error shutdown completed
Fri Apr 29 06:59:33 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Fri Apr 29 06:59:33 AST 2011  apcupsd error shutdown completed
Fri Apr 29 10:07:05 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Fri Apr 29 10:07:05 AST 2011  apcupsd error shutdown completed
Fri Apr 29 10:11:44 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Fri Apr 29 10:11:44 AST 2011  apcupsd error shutdown completed
Fri Apr 29 10:25:34 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Fri Apr 29 10:25:34 AST 2011  apcupsd error shutdown completed
Fri Apr 29 14:07:29 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Fri Apr 29 14:07:29 AST 2011  apcupsd error shutdown completed
Fri Apr 29 17:11:24 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Fri Apr 29 17:11:24 AST 2011  apcupsd error shutdown completed
Sat Apr 30 06:48:06 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Sat Apr 30 06:48:06 AST 2011  apcupsd error shutdown completed
Sat Apr 30 07:38:00 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Sat Apr 30 07:38:00 AST 2011  apcupsd error shutdown completed
Sat Apr 30 07:47:55 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Sat Apr 30 07:47:55 AST 2011  apcupsd error shutdown completed
Sat Apr 30 07:54:08 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Sat Apr 30 07:54:08 AST 2011  apcupsd error shutdown completed
Sat Apr 30 13:59:44 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Sat Apr 30 13:59:44 AST 2011  apcupsd error shutdown completed
Sat Apr 30 16:32:15 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Sat Apr 30 16:32:15 AST 2011  apcupsd error shutdown completed
Mon May 02 11:45:42 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Mon May 02 11:45:42 AST 2011  apcupsd error shutdown completed
Mon May 02 14:34:18 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Mon May 02 14:34:18 AST 2011  apcupsd error shutdown completed
Tue May 03 06:17:57 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Tue May 03 06:17:57 AST 2011  apcupsd error shutdown completed
Tue May 03 10:16:35 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Tue May 03 10:16:35 AST 2011  apcupsd error shutdown completed
Tue May 03 14:15:06 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Tue May 03 14:15:06 AST 2011  apcupsd error shutdown completed
Tue May 03 18:18:19 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Tue May 03 18:18:19 AST 2011  apcupsd error shutdown completed
Wed May 04 08:20:10 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Wed May 04 08:20:10 AST 2011  apcupsd error shutdown completed
Wed May 04 10:24:08 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Wed May 04 10:24:08 AST 2011  apcupsd error shutdown completed
Wed May 04 14:16:22 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Wed May 04 14:16:22 AST 2011  apcupsd error shutdown completed
Wed May 04 16:29:31 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Wed May 04 16:29:31 AST 2011  apcupsd error shutdown completed
Wed May 04 21:11:22 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Wed May 04 21:11:22 AST 2011  apcupsd error shutdown completed
Thu May 05 11:06:22 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Thu May 05 11:06:22 AST 2011  apcupsd error shutdown completed
Thu May 05 19:02:56 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Thu May 05 19:02:56 AST 2011  apcupsd error shutdown completed
Fri May 06 06:13:16 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Fri May 06 06:13:16 AST 2011  apcupsd error shutdown completed
Fri May 06 09:44:59 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Fri May 06 09:44:59 AST 2011  apcupsd error shutdown completed
Fri May 06 10:52:25 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Fri May 06 10:52:25 AST 2011  apcupsd error shutdown completed
Fri May 06 11:03:17 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Fri May 06 11:03:17 AST 2011  apcupsd error shutdown completed
Fri May 06 14:27:46 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Fri May 06 14:27:46 AST 2011  apcupsd error shutdown completed
Fri May 06 18:17:44 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Fri May 06 18:17:44 AST 2011  apcupsd error shutdown completed
Sat May 07 09:06:25 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Sat May 07 09:06:25 AST 2011  apcupsd error shutdown completed
Sat May 07 09:54:06 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Sat May 07 09:54:07 AST 2011  apcupsd error shutdown completed
Sat May 07 11:10:49 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Sat May 07 11:10:49 AST 2011  apcupsd error shutdown completed
Sat May 07 13:38:54 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Sat May 07 13:38:54 AST 2011  apcupsd error shutdown completed
Sat May 07 16:53:47 AST 2011  apcupsd exiting, signal 15
Sat May 07 20:53:56 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Sat May 07 20:53:56 AST 2011  apcupsd error shutdown completed
Sun May 08 07:16:12 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Sun May 08 07:16:12 AST 2011  apcupsd error shutdown completed
Sun May 08 17:07:06 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Sun May 08 17:07:06 AST 2011  apcupsd error shutdown completed
Sun May 08 19:00:07 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Sun May 08 19:00:07 AST 2011  apcupsd error shutdown completed
Mon May 09 08:23:45 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Mon May 09 08:23:45 AST 2011  apcupsd error shutdown completed
Mon May 09 09:46:49 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Mon May 09 09:46:49 AST 2011  apcupsd error shutdown completed
Mon May 09 10:40:41 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Mon May 09 10:40:42 AST 2011  apcupsd error shutdown completed
Mon May 09 14:20:03 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Mon May 09 14:20:03 AST 2011  apcupsd error shutdown completed
Mon May 09 16:37:00 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Mon May 09 16:37:00 AST 2011  apcupsd error shutdown completed
Wed May 11 14:52:04 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Wed May 11 14:52:04 AST 2011  apcupsd error shutdown completed
Wed May 11 16:39:21 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Wed May 11 16:39:21 AST 2011  apcupsd error shutdown completed
Wed May 11 18:12:45 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Wed May 11 18:12:45 AST 2011  apcupsd error shutdown completed
Thu May 12 08:45:45 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Thu May 12 08:45:45 AST 2011  apcupsd error shutdown completed
Thu May 12 11:04:35 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Thu May 12 11:04:35 AST 2011  apcupsd error shutdown completed
Thu May 12 13:31:45 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Thu May 12 13:31:45 AST 2011  apcupsd error shutdown completed
Thu May 12 21:10:45 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Thu May 12 21:10:45 AST 2011  apcupsd error shutdown completed
Fri May 13 09:05:40 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Fri May 13 09:05:40 AST 2011  apcupsd error shutdown completed
Fri May 13 10:52:21 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Fri May 13 10:52:21 AST 2011  apcupsd error shutdown completed
Fri May 13 10:55:58 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Fri May 13 10:55:58 AST 2011  apcupsd error shutdown completed
Fri May 13 10:59:13 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Fri May 13 10:59:13 AST 2011  apcupsd error shutdown completed
Fri May 13 12:13:58 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Fri May 13 12:13:58 AST 2011  apcupsd error shutdown completed
Fri May 13 13:02:40 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Fri May 13 13:02:40 AST 2011  apcupsd error shutdown completed
Fri May 13 18:36:13 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Fri May 13 18:36:13 AST 2011  apcupsd error shutdown completed
Sat May 14 07:33:41 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Sat May 14 07:33:41 AST 2011  apcupsd error shutdown completed
Sat May 14 16:30:55 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Sat May 14 16:30:55 AST 2011  apcupsd error shutdown completed
Sun May 15 08:53:23 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Sun May 15 08:53:23 AST 2011  apcupsd error shutdown completed
Mon May 16 06:55:33 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Mon May 16 06:55:33 AST 2011  apcupsd error shutdown completed
Mon May 16 14:25:08 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Mon May 16 14:25:08 AST 2011  apcupsd error shutdown completed
Tue May 17 08:15:16 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Tue May 17 08:15:17 AST 2011  apcupsd error shutdown completed
Tue May 17 10:07:16 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Tue May 17 10:07:16 AST 2011  apcupsd error shutdown completed
Tue May 17 14:21:51 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Tue May 17 14:21:51 AST 2011  apcupsd error shutdown completed
Tue May 17 16:31:02 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Tue May 17 16:31:02 AST 2011  apcupsd error shutdown completed
Tue May 17 18:16:33 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Tue May 17 18:16:33 AST 2011  apcupsd error shutdown completed
Wed May 18 08:28:41 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Wed May 18 08:28:41 AST 2011  apcupsd error shutdown completed
Wed May 18 10:30:13 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Wed May 18 10:30:13 AST 2011  apcupsd error shutdown completed
Wed May 18 14:16:23 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Wed May 18 14:16:23 AST 2011  apcupsd error shutdown completed
Wed May 18 18:17:21 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Wed May 18 18:17:21 AST 2011  apcupsd error shutdown completed
Thu May 19 01:16:49 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Thu May 19 01:16:49 AST 2011  apcupsd error shutdown completed
Thu May 19 08:24:23 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Thu May 19 08:24:23 AST 2011  apcupsd error shutdown completed
Thu May 19 09:28:43 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Thu May 19 09:28:43 AST 2011  apcupsd error shutdown completed
Thu May 19 10:03:45 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Thu May 19 10:03:45 AST 2011  apcupsd error shutdown completed
Thu May 19 11:17:13 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Thu May 19 11:17:13 AST 2011  apcupsd error shutdown completed
Thu May 19 13:14:42 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Thu May 19 13:14:42 AST 2011  apcupsd error shutdown completed
Thu May 19 14:35:57 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Thu May 19 14:35:57 AST 2011  apcupsd error shutdown completed
Thu May 19 21:11:13 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Thu May 19 21:11:13 AST 2011  apcupsd error shutdown completed
Fri May 20 08:22:54 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Fri May 20 08:22:54 AST 2011  apcupsd error shutdown completed
Fri May 20 15:01:36 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Fri May 20 15:01:36 AST 2011  apcupsd error shutdown completed
Fri May 20 18:22:43 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Fri May 20 18:22:43 AST 2011  apcupsd error shutdown completed
Sat May 21 10:04:57 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Sat May 21 10:04:57 AST 2011  apcupsd error shutdown completed
Sat May 21 17:12:56 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Sat May 21 17:12:56 AST 2011  apcupsd error shutdown completed
Sun May 22 09:37:38 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Sun May 22 09:37:38 AST 2011  apcupsd error shutdown completed
Sun May 22 17:43:33 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Sun May 22 17:43:33 AST 2011  apcupsd error shutdown completed
Sun May 22 17:47:57 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Sun May 22 17:47:57 AST 2011  apcupsd error shutdown completed
Mon May 23 06:59:54 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Mon May 23 06:59:54 AST 2011  apcupsd error shutdown completed
Mon May 23 08:57:30 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Mon May 23 08:57:30 AST 2011  apcupsd error shutdown completed
Mon May 23 12:26:35 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Mon May 23 12:26:35 AST 2011  apcupsd error shutdown completed
Mon May 23 13:11:09 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Mon May 23 13:11:09 AST 2011  apcupsd error shutdown completed
Mon May 23 13:29:22 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Mon May 23 13:29:22 AST 2011  apcupsd error shutdown completed
Mon May 23 15:15:57 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Mon May 23 15:15:57 AST 2011  apcupsd error shutdown completed
Mon May 23 15:49:04 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Mon May 23 15:49:04 AST 2011  apcupsd error shutdown completed
Mon May 23 18:50:49 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Mon May 23 18:50:49 AST 2011  apcupsd error shutdown completed
Tue May 24 07:49:29 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Tue May 24 07:49:29 AST 2011  apcupsd error shutdown completed
Tue May 24 11:57:04 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Tue May 24 11:57:04 AST 2011  apcupsd error shutdown completed
Tue May 24 13:49:29 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Tue May 24 13:49:29 AST 2011  apcupsd error shutdown completed
Tue May 24 15:42:08 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Tue May 24 15:42:08 AST 2011  apcupsd error shutdown completed
Tue May 24 16:10:53 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Tue May 24 16:10:53 AST 2011  apcupsd error shutdown completed
Wed May 25 07:26:57 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Wed May 25 07:26:57 AST 2011  apcupsd error shutdown completed
Wed May 25 07:43:28 AST 2011  apcupsd exiting, signal 15
Wed May 25 07:44:43 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Wed May 25 07:44:43 AST 2011  apcupsd error shutdown completed
Thu May 26 07:30:34 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Thu May 26 07:30:34 AST 2011  apcupsd error shutdown completed
Thu May 26 23:02:02 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Thu May 26 23:02:02 AST 2011  apcupsd error shutdown completed
Fri May 27 07:14:17 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Fri May 27 07:14:17 AST 2011  apcupsd error shutdown completed
Fri May 27 09:39:33 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Fri May 27 09:39:33 AST 2011  apcupsd error shutdown completed
Fri May 27 13:03:59 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Fri May 27 13:03:59 AST 2011  apcupsd error shutdown completed
Fri May 27 13:38:03 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Fri May 27 13:38:03 AST 2011  apcupsd error shutdown completed
Fri May 27 15:07:10 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Fri May 27 15:07:10 AST 2011  apcupsd error shutdown completed
Fri May 27 16:18:04 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Fri May 27 16:18:04 AST 2011  apcupsd error shutdown completed
Sat May 28 07:57:04 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Sat May 28 07:57:04 AST 2011  apcupsd error shutdown completed
Sat May 28 16:49:56 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Sat May 28 16:49:56 AST 2011  apcupsd error shutdown completed
Sun May 29 00:53:31 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Sun May 29 00:53:31 AST 2011  apcupsd error shutdown completed
Sun May 29 07:39:36 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Sun May 29 07:39:36 AST 2011  apcupsd error shutdown completed
Sun May 29 20:16:06 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Sun May 29 20:16:06 AST 2011  apcupsd error shutdown completed
Mon May 30 11:52:09 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Mon May 30 11:52:09 AST 2011  apcupsd error shutdown completed
Mon May 30 13:01:48 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Mon May 30 13:01:48 AST 2011  apcupsd error shutdown completed
Mon May 30 15:05:05 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Mon May 30 15:05:05 AST 2011  apcupsd error shutdown completed
Mon May 30 16:08:41 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Mon May 30 16:08:41 AST 2011  apcupsd error shutdown completed
Mon May 30 18:37:20 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Mon May 30 18:37:20 AST 2011  apcupsd error shutdown completed
Mon May 30 23:43:52 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Mon May 30 23:43:52 AST 2011  apcupsd error shutdown completed
Mon May 30 23:50:19 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Mon May 30 23:50:19 AST 2011  apcupsd error shutdown completed
Mon May 30 23:59:46 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Mon May 30 23:59:46 AST 2011  apcupsd error shutdown completed
Wed Jun 01 07:57:53 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Wed Jun 01 07:57:53 AST 2011  apcupsd error shutdown completed
Wed Jun 01 18:40:09 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Wed Jun 01 18:40:09 AST 2011  apcupsd error shutdown completed
Thu Jun 02 07:09:40 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Thu Jun 02 07:09:40 AST 2011  apcupsd error shutdown completed
Thu Jun 02 22:14:21 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Thu Jun 02 22:14:21 AST 2011  apcupsd error shutdown completed
Fri Jun 03 08:14:55 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Fri Jun 03 08:14:55 AST 2011  apcupsd error shutdown completed
Fri Jun 03 08:48:06 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Fri Jun 03 08:48:06 AST 2011  apcupsd error shutdown completed
Fri Jun 03 11:44:37 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Fri Jun 03 11:44:37 AST 2011  apcupsd error shutdown completed
Fri Jun 03 16:38:11 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Fri Jun 03 16:38:11 AST 2011  apcupsd error shutdown completed
Fri Jun 03 18:56:44 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Fri Jun 03 18:56:44 AST 2011  apcupsd error shutdown completed
Sat Jun 04 07:19:59 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Sat Jun 04 07:19:59 AST 2011  apcupsd error shutdown completed
Sat Jun 04 09:22:34 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Sat Jun 04 09:22:34 AST 2011  apcupsd error shutdown completed
Sat Jun 04 16:36:23 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Sat Jun 04 16:36:23 AST 2011  apcupsd error shutdown completed
Sat Jun 04 23:37:22 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Sat Jun 04 23:37:22 AST 2011  apcupsd error shutdown completed
Sun Jun 05 01:05:51 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Sun Jun 05 01:05:51 AST 2011  apcupsd error shutdown completed
Sun Jun 05 01:14:21 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Sun Jun 05 01:14:21 AST 2011  apcupsd error shutdown completed
Sun Jun 05 01:22:11 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Sun Jun 05 01:22:11 AST 2011  apcupsd error shutdown completed
Sun Jun 05 01:22:33 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Sun Jun 05 01:22:33 AST 2011  apcupsd error shutdown completed
Sun Jun 05 01:23:43 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Sun Jun 05 01:23:43 AST 2011  apcupsd error shutdown completed
Sun Jun 05 01:25:42 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Sun Jun 05 01:25:42 AST 2011  apcupsd error shutdown completed
Sun Jun 05 08:15:57 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Sun Jun 05 08:15:57 AST 2011  apcupsd error shutdown completed
Sun Jun 05 09:01:56 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Sun Jun 05 09:01:56 AST 2011  apcupsd error shutdown completed
Sun Jun 05 13:46:16 AST 2011  apcupsd exiting, signal 15
Sun Jun 05 14:09:24 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Sun Jun 05 14:09:24 AST 2011  apcupsd error shutdown completed
Sun Jun 05 14:16:35 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Sun Jun 05 14:16:35 AST 2011  apcupsd error shutdown completed
Sun Jun 05 14:18:28 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Sun Jun 05 14:18:28 AST 2011  apcupsd error shutdown completed
Sun Jun 05 14:24:01 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Sun Jun 05 14:24:01 AST 2011  apcupsd error shutdown completed
Sun Jun 05 14:30:26 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Sun Jun 05 14:30:26 AST 2011  apcupsd error shutdown completed
Sun Jun 05 14:31:23 AST 2011  apcupsd exiting, signal 15
Sun Jun 05 14:32:10 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Sun Jun 05 14:32:10 AST 2011  apcupsd error shutdown completed
Mon Jun 06 09:59:58 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Mon Jun 06 09:59:58 AST 2011  apcupsd error shutdown completed
Mon Jun 06 10:40:54 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Mon Jun 06 10:40:54 AST 2011  apcupsd error shutdown completed
Mon Jun 06 11:08:02 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Mon Jun 06 11:08:02 AST 2011  apcupsd error shutdown completed
Mon Jun 06 11:13:17 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Mon Jun 06 11:13:17 AST 2011  apcupsd error shutdown completed
Mon Jun 06 11:31:52 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Mon Jun 06 11:31:52 AST 2011  apcupsd error shutdown completed
Mon Jun 06 15:05:26 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Mon Jun 06 15:05:26 AST 2011  apcupsd error shutdown completed
Mon Jun 06 17:07:29 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Mon Jun 06 17:07:29 AST 2011  apcupsd error shutdown completed
Mon Jun 06 18:48:40 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Mon Jun 06 18:48:40 AST 2011  apcupsd error shutdown completed
Tue Jun 07 08:26:36 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Tue Jun 07 08:26:36 AST 2011  apcupsd error shutdown completed
Tue Jun 07 16:35:46 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Tue Jun 07 16:35:46 AST 2011  apcupsd error shutdown completed
Tue Jun 07 20:34:19 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Tue Jun 07 20:34:19 AST 2011  apcupsd error shutdown completed
Wed Jun 08 07:53:31 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Wed Jun 08 07:53:31 AST 2011  apcupsd error shutdown completed
Wed Jun 08 15:58:52 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Wed Jun 08 15:58:52 AST 2011  apcupsd error shutdown completed
Wed Jun 08 18:28:00 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Wed Jun 08 18:28:00 AST 2011  apcupsd error shutdown completed
Wed Jun 08 19:22:48 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Wed Jun 08 19:22:48 AST 2011  apcupsd error shutdown completed
Wed Jun 08 19:52:55 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Wed Jun 08 19:52:55 AST 2011  apcupsd error shutdown completed
Wed Jun 08 19:54:35 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Wed Jun 08 19:54:35 AST 2011  apcupsd error shutdown completed
Wed Jun 08 19:58:39 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Wed Jun 08 19:58:39 AST 2011  apcupsd error shutdown completed
Wed Jun 08 20:09:18 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Wed Jun 08 20:09:18 AST 2011  apcupsd error shutdown completed
Wed Jun 08 20:15:47 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Wed Jun 08 20:15:47 AST 2011  apcupsd error shutdown completed
Wed Jun 08 20:16:31 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Wed Jun 08 20:16:31 AST 2011  apcupsd error shutdown completed
Wed Jun 08 20:18:33 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Wed Jun 08 20:18:33 AST 2011  apcupsd error shutdown completed
Wed Jun 08 20:22:16 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Wed Jun 08 20:22:16 AST 2011  apcupsd error shutdown completed
Wed Jun 08 20:23:14 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Wed Jun 08 20:23:14 AST 2011  apcupsd error shutdown completed
Wed Jun 08 20:23:47 AST 2011  apcupsd exiting, signal 15
Wed Jun 08 20:26:27 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Wed Jun 08 20:26:27 AST 2011  apcupsd error shutdown completed
Thu Jun 09 05:37:20 AST 2011  apcupsd FATAL ERROR in linux-usb.c at line 609
Cannot find UPS device --
For a link to detailed USB trouble shooting information,
please see <http://www.apcupsd.com/support.html>.
Thu Jun 09 05:37:20 AST 2011  apcupsd error shutdown completed

```

ps -ef | grep apcupsd
```

dingoduck 15757 15694  0 06:47 pts/0    00:00:00 grep apcupsd

```

apcaccess
```

Error contacting apcupsd @ localhost:3551: Connection refused

```

cat /etc/default/apcupsd
```

# Defaults for apcupsd initscript

# Apcupsd-devel internal configuration
APCACCESS=/sbin/apcaccess
ISCONFIGURED=yes

```

cat /etc/apcupsd/apcupsd.conf
```

## apcupsd.conf v1.1 ##
# 
#  for apcupsd release 3.14.6 (16 May 2009) - debian
#
# "apcupsd" POSIX config file

#
# ========= General configuration parameters ============
#

# UPSNAME xxx
#   Use this to give your UPS a name in log files and such. This
#   is particulary useful if you have multiple UPSes. This does not
#   set the EEPROM. It should be 8 characters or less.
UPSNAME Back-UPS

# UPSCABLE <cable>
#   Defines the type of cable connecting the UPS to your computer.
#
#   Possible generic choices for <cable> are:
#     simple, smart, ether, usb
#
#   Or a specific cable model number may be used:
#     940-0119A, 940-0127A, 940-0128A, 940-0020B,
#     940-0020C, 940-0023A, 940-0024B, 940-0024C,
#     940-1524C, 940-0024G, 940-0095A, 940-0095B,
#     940-0095C, M-04-02-2000
#
UPSCABLE usb

# To get apcupsd to work, in addition to defining the cable
# above, you must also define a UPSTYPE, which corresponds to
# the type of UPS you have (see the Description for more details).
# You must also specify a DEVICE, sometimes referred to as a port.
# For USB UPSes, please leave the DEVICE directive blank. For
# other UPS types, you must specify an appropriate port or address.
#
# UPSTYPE   DEVICE           Description
# apcsmart  /dev/tty**       Newer serial character device,
#                            appropriate for SmartUPS models using
#                            a serial cable (not USB).
#
# usb       <BLANK>          Most new UPSes are USB. A blank DEVICE
#                            setting enables autodetection, which is
#                            the best choice for most installations.
#
# net       hostname:port    Network link to a master apcupsd
#                            through apcupsd's Network Information
#                            Server. This is used if you don't have
#                            a UPS directly connected to your computer.
#
# snmp      hostname:port:vendor:community
#                            SNMP Network link to an SNMP-enabled
#                            UPS device. Vendor is the MIB used by
#                            the UPS device: can be "APC", "APC_NOTRAP"
#                            or "RFC" where APC is the powernet MIB,
#                            "APC_NOTRAP" is powernet with SNMP trap
#                            catching disabled, and RFC is the IETF's 
#                            rfc1628 UPS-MIB. You usually want "APC".
#                            Port is usually 161. Community is usually
#                            "private".
#
# dumb      /dev/tty**       Old serial character device for use 
#                            with simple-signaling UPSes.
#
# pcnet    ipaddr:username:passphrase
#                            PowerChute Network Shutdown protocol
#                            which can be used as an alternative to SNMP
#                            with AP9617 family of smart slot cards.
#                            ipaddr is the IP address of the UPS mgmt
#                            card. username and passphrase are the
#                            credentials for which the card has been
#                            configured.
#
UPSTYPE usb
# DEVICE /dev/ttyS0

# POLLTIME <int>
#   Interval (in seconds) at which apcupsd polls the UPS for status. This
#   setting applies both to directly-attached UPSes (UPSTYPE apcsmart, usb, 
#   dumb) and networked UPSes (UPSTYPE net, snmp). Lowering this setting
#   will improve apcupsd's responsiveness to certain events at the cost of
#   higher CPU utilization. The default of 60 is appropriate for most
#   situations.
#POLLTIME 60

# LOCKFILE <path to lockfile>
#   Path for device lock file. Not used on Win32.
LOCKFILE /var/lock

# SCRIPTDIR <path to script directory>
#   Directory in which apccontrol and event scripts are located.
SCRIPTDIR /etc/apcupsd

# PWRFAILDIR <path to powerfail directory>
#   Directory in which to write the powerfail flag file. This file
#   is created when apcupsd initiates a system shutdown and is
#   checked in the OS halt scripts to determine if a killpower
#   (turning off UPS output power) is required.
PWRFAILDIR /etc/apcupsd

# NOLOGINDIR <path to nologin directory>
#   Directory in which to write the nologin file. The existence
#   of this flag file tells the OS to disallow new logins.
NOLOGINDIR /etc


#
# ======== Configuration parameters used during power failures ==========
#

# The ONBATTERYDELAY is the time in seconds from when a power failure
#   is detected until we react to it with an onbattery event.
#
#   This means that, apccontrol will be called with the powerout argument
#   immediately when a power failure is detected.  However, the
#   onbattery argument is passed to apccontrol only after the 
#   ONBATTERYDELAY time.  If you don't want to be annoyed by short
#   powerfailures, make sure that apccontrol powerout does nothing
#   i.e. comment out the wall.
ONBATTERYDELAY 6

# 
# Note: BATTERYLEVEL, MINUTES, and TIMEOUT work in conjunction, so
# the first that occurs will cause the initation of a shutdown.
#

# If during a power failure, the remaining battery percentage
# (as reported by the UPS) is below or equal to BATTERYLEVEL, 
# apcupsd will initiate a system shutdown.
BATTERYLEVEL 5

# If during a power failure, the remaining runtime in minutes 
# (as calculated internally by the UPS) is below or equal to MINUTES,
# apcupsd, will initiate a system shutdown.
MINUTES 3

# If during a power failure, the UPS has run on batteries for TIMEOUT
# many seconds or longer, apcupsd will initiate a system shutdown.
# A value of 0 disables this timer.
#
#  Note, if you have a Smart UPS, you will most likely want to disable
#    this timer by setting it to zero. That way, you UPS will continue
#    on batteries until either the % charge remaing drops to or below BATTERYLEVEL,
#    or the remaining battery runtime drops to or below MINUTES.  Of course,
#    if you are testing, setting this to 60 causes a quick system shutdown
#    if you pull the power plug.   
#  If you have an older dumb UPS, you will want to set this to less than
#    the time you know you can run on batteries.
TIMEOUT 0

#  Time in seconds between annoying users to signoff prior to
#  system shutdown. 0 disables.
ANNOY 300

# Initial delay after power failure before warning users to get
# off the system.
ANNOYDELAY 60

# The condition which determines when users are prevented from
# logging in during a power failure.
# NOLOGON <string> [ disable | timeout | percent | minutes | always ]
NOLOGON disable

# If KILLDELAY is non-zero, apcupsd will continue running after a
# shutdown has been requested, and after the specified time in
# seconds attempt to kill the power. This is for use on systems
# where apcupsd cannot regain control after a shutdown.
# KILLDELAY <seconds>  0 disables
KILLDELAY 0

#
# ==== Configuration statements for Network Information Server ====
#

# NETSERVER [ on | off ] on enables, off disables the network
#  information server. If netstatus is on, a network information
#  server process will be started for serving the STATUS and
#  EVENT data over the network (used by CGI programs).
NETSERVER on

# NISIP <dotted notation ip address>
#  IP address on which NIS server will listen for incoming connections.
#  This is useful if your server is multi-homed (has more than one
#  network interface and IP address). Default value is 0.0.0.0 which
#  means any incoming request will be serviced. Alternatively, you can
#  configure this setting to any specific IP address of your server and 
#  NIS will listen for connections only on that interface. Use the
#  loopback address (127.0.0.1) to accept connections only from the
#  local machine.
NISIP 127.0.0.1

# NISPORT <port> default is 3551 as registered with the IANA
#  port to use for sending STATUS and EVENTS data over the network.
#  It is not used unless NETSERVER is on. If you change this port,
#  you will need to change the corresponding value in the cgi directory
#  and rebuild the cgi programs.
NISPORT 3551

# If you want the last few EVENTS to be available over the network
# by the network information server, you must define an EVENTSFILE.
EVENTSFILE /var/log/apcupsd.events

# EVENTSFILEMAX <kilobytes>
#  By default, the size of the EVENTSFILE will be not be allowed to exceed
#  10 kilobytes.  When the file grows beyond this limit, older EVENTS will
#  be removed from the beginning of the file (first in first out).  The
#  parameter EVENTSFILEMAX can be set to a different kilobyte value, or set
#  to zero to allow the EVENTSFILE to grow without limit.
EVENTSFILEMAX 10

#
# ========== Configuration statements used if sharing =============
#            a UPS with more than one machine

#
# Remaining items are for ShareUPS (APC expansion card) ONLY
#

# UPSCLASS [ standalone | shareslave | sharemaster ]
#   Normally standalone unless you share an UPS using an APC ShareUPS
#   card.
UPSCLASS standalone

# UPSMODE [ disable | share ]
#   Normally disable unless you share an UPS using an APC ShareUPS card.
UPSMODE disable

#
# ===== Configuration statements to control apcupsd system logging ========
#

# Time interval in seconds between writing the STATUS file; 0 disables
STATTIME 0

# Location of STATUS file (written to only if STATTIME is non-zero)
STATFILE /var/log/apcupsd.status

# LOGSTATS [ on | off ] on enables, off disables
# Note! This generates a lot of output, so if         
#       you turn this on, be sure that the
#       file defined in syslog.conf for LOG_NOTICE is a named pipe.
#  You probably do not want this on.
LOGSTATS off

# Time interval in seconds between writing the DATA records to
#   the log file. 0 disables.
DATATIME 0

# FACILITY defines the logging facility (class) for logging to syslog. 
#          If not specified, it defaults to "daemon". This is useful 
#          if you want to separate the data logged by apcupsd from other
#          programs.
#FACILITY DAEMON

#
# ========== Configuration statements used in updating the UPS EPROM =========
#

#
# These statements are used only by apctest when choosing "Set EEPROM with conf
# file values" from the EEPROM menu. THESE STATEMENTS HAVE NO EFFECT ON APCUPSD.
#

# UPS name, max 8 characters 
#UPSNAME UPS_IDEN

# Battery date - 8 characters
#BATTDATE mm/dd/yy

# Sensitivity to line voltage quality (H cause faster transfer to batteries)  
# SENSITIVITY H M L        (default = H)
#SENSITIVITY H

# UPS delay after power return (seconds)
# WAKEUP 000 060 180 300   (default = 0)
#WAKEUP 60

# UPS Grace period after request to power off (seconds)
# SLEEP 020 180 300 600    (default = 20)
#SLEEP 180

# Low line voltage causing transfer to batteries
# The permitted values depend on your model as defined by last letter 
#  of FIRMWARE or APCMODEL. Some representative values are:
#    D 106 103 100 097
#    M 177 172 168 182
#    A 092 090 088 086
#    I 208 204 200 196     (default = 0 => not valid)
#LOTRANSFER  208

# High line voltage causing transfer to batteries
# The permitted values depend on your model as defined by last letter 
#  of FIRMWARE or APCMODEL. Some representative values are:
#    D 127 130 133 136
#    M 229 234 239 224
#    A 108 110 112 114
#    I 253 257 261 265     (default = 0 => not valid)
#HITRANSFER 253

# Battery charge needed to restore power
# RETURNCHARGE 00 15 50 90 (default = 15)
#RETURNCHARGE 15

# Alarm delay 
# 0 = zero delay after pwr fail, T = power fail + 30 sec, L = low battery, N = never
# BEEPSTATE 0 T L N        (default = 0)
#BEEPSTATE T

# Low battery warning delay in minutes
# LOWBATT 02 05 07 10      (default = 02)
#LOWBATT 2

# UPS Output voltage when running on batteries
# The permitted values depend on your model as defined by last letter 
#  of FIRMWARE or APCMODEL. Some representative values are:
#    D 115
#    M 208
#    A 100
#    I 230 240 220 225     (default = 0 => not valid)
#OUTPUTVOLTS 230

# Self test interval in hours 336=2 weeks, 168=1 week, ON=at power on
# SELFTEST 336 168 ON OFF  (default = 336)
#SELFTEST 336

```

sudo /etc/init.d/apcupsd restart
```

Stopping UPS power management: start-stop-daemon: warning: failed to kill 1498: No such process
1 pids were not killed
No process in pidfile '/var/run/apcupsd.pid' found running; none killed.
apcupsd.

```
it pauses here for about 10 seconds then...
```

Starting UPS power management: apcupsd.

```

---

### Post by sefs on 2011-06-09
Hi, 

Get this....

I plugged it into a different USB port and it now works.  The thing is it used to work from the USB port that it was orginally plugged into.

The thing is there seems to be nothing wrong with the original USB port as if I plug an ipod/blackberry/usb flash drive into that original port it works.  That port has simply just stopped working with this UPS.  

Do you have any idea why that would be?  I am at a loss here.

When I plug it into any other port it creates a /dev/usb/hiddev0  but not in this specific port...and this specific port as far as I can tell works as it will work when I plug in various other devices.  This port was working before with the same ups.

Thanks.

---

### Post by tgalati4 on 2011-06-09
You will get a status file by changing your apcupsd.conf file:


# Time interval in seconds between writing the STATUS file; 0 disables
STATTIME 300

As far as the USB port, try powering off the machine and unplugging for an hour.  Could be a USB controller issue.  Try a different cable as well.

I've seen USB controllers fail on motherboards.  First they go strange, then they go intermittent, then they fail completely.  Check dmesg:

dmesg | tail

Then plug in the UPS

dmesg | tail -40

Note the differences.

---

### Post by sefs on 2011-06-10
You are correct. I believe it is on it's way out.  If i plug in my mouse. Nada.  But it loads storage devices.  Tried the leaving it off for a couple of hours, but did not work.

To tell you the truth this MB is 5 years old and I think its on it's in the departure lounge so to speak.

Thanks very much for the assist!

---

### Post by tgalati4 on 2011-06-10
I just popped in a $10 USB card into a client's computer because his 6 USB devices were all acting strange.  5VDC was OK, but the controller was not happy.  New card took care of it.  His machine was about 4 years old.  Costco HP == cheap junk.  Most people don't realize that Costco computers and TV's are blems--blemished merchandise that the factories bin and send to Costco.

"But it was half the price of other computers at the time."

---

### Post by sefs on 2011-06-10
> **tgalati4 said:**
> I just popped in a $10 USB card into a client's computer because his 6 USB devices were all acting strange.  5VDC was OK, but the controller was not happy.  New card took care of it.  His machine was about 4 years old.  Costco HP == cheap junk.  Most people don't realize that Costco computers and TV's are blems--blemished merchandise that the factories bin and send to Costco.

"But it was half the price of other computers at the time."

I wish I could do that too, but all my PCI/AGP ports on this MB have failed me :)
It seems to be going a bit at a time, but I don't want to create techno waste in some dump unless I really have to just yet.

---

### Post by tgalati4 on 2011-06-12
Linux does have the meager expectation of working hardware.

---

### Post by Monotoba on 2012-03-09
FYI for those who have issues getting apcupsd to work on Ubuntu 11. 

I just built a new machine with an P9X79 Deluxe motherboard and Ubuntu 11.10 OS. I beat my head against a wall for hours trying to get my APC XS 1500 ups to work with this machine. I got very similar errors to the above. When I read that the issues was the USB port, I reach around the machine and moved the ups' usb cable to another port. When I looked back up at the monitor I saw a message in the terminal window telling me communications had been restored with the ups. I then tried moving the cable around a few times to the other usb ports on the mb. I found that while my mouse and keyboard worked just fine in any usb port on the mb, the APC XS 1500 only worked with some of the usb ports and not others.

I hope this helps others who may be experiencing the same issues. And thanks to those who diagnosed the issue above which lead me in the right direction.

---

### Post by skaramanger on 2012-06-07
> **Monotoba said:**
> FYI for those who have issues getting apcupsd to work on Ubuntu 11. 

I just built a new machine with an P9X79 Deluxe motherboard and Ubuntu 11.10 OS. I beat my head against a wall for hours trying to get my APC XS 1500 ups to work with this machine. I got very similar errors to the above. When I read that the issues was the USB port, I reach around the machine and moved the ups' usb cable to another port. When I looked back up at the monitor I saw a message in the terminal window telling me communications had been restored with the ups. I then tried moving the cable around a few times to the other usb ports on the mb. I found that while my mouse and keyboard worked just fine in any usb port on the mb, the APC XS 1500 only worked with some of the usb ports and not others.

I hope this helps others who may be experiencing the same issues. And thanks to those who diagnosed the issue above which lead me in the right direction.

I'm having the same problem.  apcupsd is running.  I tried switching usb ports, I get a system notification that connection to my XS 1500 has been restored. But I'm still getting the access denied message when attempting to run sudo apcaccess.  This has worked in the past. Hate to think that my usb controllers are starting to go.

---

### Post by skaramanger on 2012-07-24
So after several weeks I figured out why it wasn't working.  In my apcupsd.conf file nisip server was assigned the localhost address of 127.0.1.1.  I changed that to 127.0.0.1 which in my hosts file is assigned to localhost.  Perform a restart and wahla.  apcaccess works. That was simple oversite.  Below is a pasting of my hosts file.  I've been interested in why there would be two values for localhost. Would a piece of software do this?  


```
~$ cat /etc/hosts
127.0.0.1       localhost localhost.localdomain tz-desktop <-- I just added this.
127.0.1.1       my-desktop

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

```$

Later

---

### Post by finite9 on 2012-12-20
wrong wrong wrong!

There is likely nothing wrong with anyones USB controller card.  It's because of the new localhost IP address that's appeared in 12.10 (I just noticed it but maybe it came in previous versions), plus the default settings in apcupsd.conf need changing.

I have a USB device, which means the the DEVICE parameter _must_ be commented out, so that autodetection os the usb device works, otherwise, it's trying to tie the ups to a specific device that's not going to work.

Secondly, due to the new 127.0.1.1 address in /etc/hosts, the NISIP setting needs changing.  It doesn't work to change it to 127.0.0.1 without changing hosts file, but you can set it to 0.0.0.0, then apcaccess will work again.  Otherwise, you can turn off NETSERVER access completely if you don't need to access your UPS over the network (which I doubt most home owners do).

So:

```
sudo vi /etc/apcupsd/apcupsd.conf
UPSCABLE usb
UPSTYPE usb
NISIP 0.0.0.0

sudo service apcupsd restart
cat /var/log/apcupsd.events

2012-12-20 13:14:39 +0100  apcupsd exiting, signal 15
2012-12-20 13:14:39 +0100  apcupsd shutdown succeeded
2012-12-20 13:14:51 +0100  apcupsd 3.14.10 (13 September 2011) debian startup succeeded


sudo apcaccess status
```

Working.

---

### Post by piperhaggis on 2013-04-22
Just wanted to thank you all for identifying the localhost issue. I feel like I should've caught it, but just spent an hour messing around with no success before finding this post.

---

### Post by Mike_Dvorak on 2013-12-20
I am having the same problem but I think the reasoning is different.

I configured my APC PRO 1000 quite easily using the Ubuntu UPS guide. My problem is that apcupsd won't start during the normal boot sequence... but I can start the service once I have logged in. I think there must be some run level dependency that is not being met. I tried to mess with the Upstart settings by changing when the apcupsd started to run level 3 or 5, but I wasn't able to get it working.

Here's what after I login:
```

foo@bar ~ $ sudo service apcupsd status
Error contacting apcupsd @ localhost:3551: Connection refused

```

But I can successfully start the apcupsd after I login:
```

foo@bar ~ $ sudo service apcupsd start
Starting UPS power management: apcupsd.
foo@bar ~ $ sudo service apcupsd status
APC      : 001,036,0900
DATE     : 2013-12-20 18:59:10 -0800  
HOSTNAME : bar
VERSION  : 3.14.10 (13 September 2011) debian
UPSNAME  : bar
CABLE    : USB Cable
DRIVER   : USB UPS Driver
UPSMODE  : Stand Alone
STARTTIME: 2013-12-20 18:59:09 -0800  
MODEL    : Back-UPS RS1000G 
STATUS   : ONLINE 
LINEV    : 121.0 Volts
LOADPCT  :  24.0 Percent Load Capacity
BCHARGE  : 034.0 Percent
TIMELEFT :  11.6 Minutes
MBATTCHG : 15 Percent
MINTIMEL : 8 Minutes
MAXTIME  : 0 Seconds
SENSE    : Medium
LOTRANS  : 088.0 Volts
HITRANS  : 147.0 Volts
ALARMDEL : 30 seconds
BATTV    : 25.3 Volts
LASTXFER : No transfers since turnon
NUMXFERS : 0
TONBATT  : 0 seconds
CUMONBATT: 0 seconds
XOFFBATT : N/A
SELFTEST : NO
STATFLAG : 0x07000008 Status Flag
SERIALNO : 3B1336X14704  
BATTDATE : 2013-09-05
NOMINV   : 120 Volts
NOMBATTV :  24.0 Volts
NOMPOWER : 600 Watts
FIRMWARE : 868.L3 -P.D USB FW:
END APC  : 2013-12-20 18:59:13 -0800 

```

Please let me know if you need any additional information. Would be nice to have apcupsd start automatically.

---

### Post by computermed3111 on 2014-08-26
Thanks for all your posts guys. I was having the same issue using a serial to serial cable to connect a CyberPower CPS1500AVR (Older UPS). I discovered a few things that I want to share. The unit is rather older and as such setting UPSCable: usb does not work, neither does setting DEVICE: ttyS0.
So I looked to the manufacturer and on their website cyberpowersystems.com > Products > Software, they have their PowerPanel software for Linux. Different flavors. It works.
I also bought a cyberpower 625va product that does use the usb cable and was still getting the errors. What must be done is to check in the config file like the users say above and ensure that you have the following items turned on and set to a non-zero value:
STATTIME
LOGSTATS
DATATIME
You will find them near the end of the file /etc/apcupsd/apcupsd.conf 
Then restart the service, then you will see a log written in 
/var/log/apcupsd.events and /var/log/apcups.status files.
Thanks to those who contributed.

---

