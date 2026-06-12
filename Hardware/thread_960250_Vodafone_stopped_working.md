---
title: "Vodafone stopped working"
date: 2008-10-27
forum: Hardware
---

### Post by klaasvanschelven on 2008-10-27
I'm having a problem with vodafone described here:
[http://www.betavine.net/bvportal/auth/forums/index.html?threadId=ff8080811d1a8b7b011d1ebd7f995aee](http://www.betavine.net/bvportal/auth/forums/index.html?threadId=ff8080811d1a8b7b011d1ebd7f995aee)

FOr some reason I can't post long texts on there forum so I'm using Ubuntu's forum instead. Not quite unrelated, since I'm using Ubuntu.

```

klaas@lenovo:~$ sudo dpkg -i /home/klaas/Desktop/downloads/dpkg/vodafone-mobile-                                                                             connect-card-driver-for-linux_1.99.17_i386.deb
[sudo] password for klaas:
Selecting previously deselected package vodafone-mobile-connect-card-driver-for-                                                                             linux.
(Reading database ... 135363 files and directories currently installed.)
Unpacking vodafone-mobile-connect-card-driver-for-linux (from .../vodafone-mobil                                                                             e-connect-card-driver-for-linux_1.99.17_i386.deb) ...
Setting up vodafone-mobile-connect-card-driver-for-linux (1.99.17) ...

klaas@lenovo:~$ sudo vodafone-mobile-connect-card-driver-for-linux-debug
2008/10/27 14:38 +0200 [-] Log opened.
2008/10/27 14:38 +0200 [-] twistd 2.5.0 (/usr/bin/python 2.5.1) starting up
2008/10/27 14:38 +0200 [-] reactor class: <class 'twisted.internet.gtk2reactor.Gtk2Reactor'>
2008/10/27 14:38 +0200 [-] Loading /usr/share/vodafone-mobile-connect-card-driver-for-linux/gtk-tap.py...
2008/10/27 14:38 +0200 [-] Loaded.
2008/10/27 14:38 +0200 [-] Changing process name to VMCCdfL
2008/10/27 14:38 +0200 [-] Log opened.
2008/10/27 14:38 +0200 [-] twistd 2.5.0 (/home/klaas/ 2.5.1) starting up
2008/10/27 14:38 +0200 [-] reactor class: <class 'twisted.internet.gtk2reactor.Gtk2Reactor'>
2008/10/27 14:38 +0200 [-] Loading /usr/share/vodafone-mobile-connect-card-driver-for-linux/gtk-tap.py...
2008/10/27 14:38 +0200 [-] Loaded.
2008/10/27 14:38 +0200 [-] twisted.conch.manhole_ssh.ConchFactory starting on 2222
2008/10/27 14:38 +0200 [-] Starting factory <twisted.conch.manhole_ssh.ConchFactory instance at 0x8b295ec>
2008/10/27 14:38 +0200 [-] Unhandled Error
        Traceback (most recent call last):
          File "/usr/lib/python2.5/site-packages/vmc/gtk/startup.py", line 152, in init
            self.detect_hardware()
          File "/usr/lib/python2.5/site-packages/vmc/gtk/startup.py", line 239, in detect_hardware
            d.addErrback(device_lacks_extractinfo_eb)
          File "/usr/lib/python2.5/site-packages/twisted/internet/defer.py", line 200, in addErrback
            errbackKeywords=kw)
          File "/usr/lib/python2.5/site-packages/twisted/internet/defer.py", line 182, in addCallbacks
            self._runCallbacks()
        --- <exception caught here> ---
          File "/usr/lib/python2.5/site-packages/twisted/internet/defer.py", line 317, in _runCallbacks
            self.result = callback(self.result, *args, **kw)
          File "/usr/lib/python2.5/site-packages/vmc/gtk/startup.py", line 218, in device_lacks_extractinfo_eb
            shutdown_core(delay=.2)
          File "/usr/lib/python2.5/site-packages/vmc/common/shutdown.py", line 32, in shutdown_core
            from vmc.common.phonebook import get_phonebook
          File "/usr/lib/python2.5/site-packages/vmc/common/phonebook.py", line 138, in <module>
            _phonebook = PhoneBook()
          File "/usr/lib/python2.5/site-packages/vmc/common/phonebook.py", line 44, in __init__
            self.cmanager = ContactsManager()
          File "/usr/lib/python2.5/site-packages/vmc/common/persistent.py", line 168, in __init__
            super(ContactsManager, self).__init__(path)
          File "/usr/lib/python2.5/site-packages/vmc/common/persistent.py", line 156, in __init__
            self.store = store.Store(path)
          File "/usr/lib/python2.5/site-packages/vmc/contrib/axiom/store.py", line 1132, in __init__
            self.transact(self._startup)
          File "/usr/lib/python2.5/site-packages/vmc/contrib/axiom/store.py", line 1674, in transact
            result = f(*a, **k)
          File "/usr/lib/python2.5/site-packages/vmc/contrib/axiom/store.py", line 1216, in _startup
            self.checkTypeSchemaConsistency(cls)
          File "/usr/lib/python2.5/site-packages/vmc/contrib/axiom/store.py", line 1384, in checkTypeSchemaConsistency
            onDiskSchema, inMemorySchema))
        exceptions.RuntimeError: Schema mismatch on already-loaded <class 'vmc.common.persistent.DBContact'> <'DBContact'> object version 1: [(u'TEXT COLLATE NOCASE', u'group'), (u'TEXT COLLATE NOCASE', u'name'), (u'TEXT COLLATE NOCASE', u'number')] != [('TEXT COLLATE NOCASE', 'name'), ('TEXT COLLATE NOCASE', 'number')]

2008/10/27 14:39 +0200 [-] Traceback (most recent call last):
2008/10/27 14:39 +0200 [-]   File "/usr/lib/python2.5/site-packages/vmc/gtk/controllers/splash.py", line 37, in on_cancel_button_clicked
2008/10/27 14:39 +0200 [-]     shutdown_core()
2008/10/27 14:39 +0200 [-]   File "/usr/lib/python2.5/site-packages/vmc/common/shutdown.py", line 32, in shutdown_core
2008/10/27 14:39 +0200 [-]     from vmc.common.phonebook import get_phonebook
2008/10/27 14:39 +0200 [-]   File "/usr/lib/python2.5/site-packages/vmc/common/phonebook.py", line 138, in <module>
2008/10/27 14:39 +0200 [-]     _phonebook = PhoneBook()
2008/10/27 14:39 +0200 [-]   File "/usr/lib/python2.5/site-packages/vmc/common/phonebook.py", line 44, in __init__
2008/10/27 14:39 +0200 [-]     self.cmanager = ContactsManager()
2008/10/27 14:39 +0200 [-]   File "/usr/lib/python2.5/site-packages/vmc/common/persistent.py", line 168, in __init__
2008/10/27 14:39 +0200 [-]     super(ContactsManager, self).__init__(path)
2008/10/27 14:39 +0200 [-]   File "/usr/lib/python2.5/site-packages/vmc/common/persistent.py", line 156, in __init__
2008/10/27 14:39 +0200 [-]     self.store = store.Store(path)
2008/10/27 14:39 +0200 [-]   File "/usr/lib/python2.5/site-packages/vmc/contrib/axiom/store.py", line 1132, in __init__
2008/10/27 14:39 +0200 [-]     self.transact(self._startup)
2008/10/27 14:39 +0200 [-]   File "/usr/lib/python2.5/site-packages/vmc/contrib/axiom/store.py", line 1674, in transact
2008/10/27 14:39 +0200 [-]     result = f(*a, **k)
2008/10/27 14:39 +0200 [-]   File "/usr/lib/python2.5/site-packages/vmc/contrib/axiom/store.py", line 1216, in _startup
2008/10/27 14:39 +0200 [-]     self.checkTypeSchemaConsistency(cls)
2008/10/27 14:39 +0200 [-]   File "/usr/lib/python2.5/site-packages/vmc/contrib/axiom/store.py", line 1384, in checkTypeSchemaConsistency
2008/10/27 14:39 +0200 [-]     onDiskSchema, inMemorySchema))
2008/10/27 14:39 +0200 [-] RuntimeError: Schema mismatch on already-loaded <class 'vmc.common.persistent.DBContact'> <'DBContact'> object version 1: [(u'TEXT COLLATE NOCASE', u'group'), (u'TEXT COLLATE NOCASE', u'name'), (u'TEXT COLLATE NOCASE', u'number')] != [('TEXT COLLATE NOCASE', 'name'), ('TEXT COLLATE NOCASE', 'number')]


```

---

### Post by klaasvanschelven on 2008-10-27
And again, with 2.0 beta 1:
I guess the most interesting part is all the way down.

```

sudo dpkg -i /home/klaas/Desktop/downloads/dpkg/vodafone-mobile-                                                                             connect-card-driver-for-linux_2.0.beta1_i386.deb
Selecting previously deselected package vodafone-mobile-connect-card-driver-for-                                                                             linux.
(Reading database ... 135380 files and directories currently installed.)
Unpacking vodafone-mobile-connect-card-driver-for-linux (from .../vodafone-mobil                                                                             e-connect-card-driver-for-linux_2.0.beta1_i386.deb) ...
Setting up vodafone-mobile-connect-card-driver-for-linux (2.0.beta1) ...

klaas@lenovo:~$ sudo vodafone-mobile-connect-card-driver-for-linux-debug
Another twistd server is running, PID 20065

This could either be a previously started instance of your application or a
different application entirely. To start a new one, either run it in some other
directory, or use the --pidfile and --logfile parameters to avoid clashes.

klaas@lenovo:~$ sudo kill 20065
klaas@lenovo:~$ sudo vodafone-mobile-connect-card-driver-for-linux-debug
Another twistd server is running, PID 20065

This could either be a previously started instance of your application or a
different application entirely. To start a new one, either run it in some other
directory, or use the --pidfile and --logfile parameters to avoid clashes.

klaas@lenovo:~$ sudo kill -9 20065
klaas@lenovo:~$ sudo vodafone-mobile-connect-card-driver-for-linux-debug
Removing stale pidfile /tmp/vmc.pid
2008/10/27 15:00 +0200 [-] Log opened.
2008/10/27 15:00 +0200 [-] twistd 2.5.0 (/usr/bin/python 2.5.1) starting up
2008/10/27 15:00 +0200 [-] reactor class: <class 'twisted.internet.gtk2reactor.Gtk2Reactor'>
2008/10/27 15:00 +0200 [-] Loading /usr/share/vodafone-mobile-connect-card-driver-for-linux/gtk-tap.py...
2008/10/27 15:00 +0200 [-] Loaded.
2008/10/27 15:00 +0200 [-] Changing process name to VMCCdfL
2008/10/27 15:00 +0200 [-] Log opened.
2008/10/27 15:00 +0200 [-] twistd 2.5.0 (/home/klaas/ 2.5.1) starting up
2008/10/27 15:00 +0200 [-] reactor class: <class 'twisted.internet.gtk2reactor.Gtk2Reactor'>
2008/10/27 15:00 +0200 [-] Loading /usr/share/vodafone-mobile-connect-card-driver-for-linux/gtk-tap.py...
2008/10/27 15:00 +0200 [-] Loaded.
2008/10/27 15:00 +0200 [-] twisted.conch.manhole_ssh.ConchFactory starting on 2222
2008/10/27 15:00 +0200 [-] Starting factory <twisted.conch.manhole_ssh.ConchFactory instance at 0x8b0d74c>
2008/10/27 15:00 +0200 [-] Shutting down...
2008/10/27 15:00 +0200 [-] (Port 2222 Closed)
2008/10/27 15:00 +0200 [-] Stopping factory <twisted.conch.manhole_ssh.ConchFactory instance at 0x8b0d74c>
2008/10/27 15:00 +0200 [-] Server Shut Down.
klaas@lenovo:~$ sudo vodafone-mobile-connect-card-driver-for-linux-debug
2008/10/27 15:02 +0200 [-] Log opened.
2008/10/27 15:02 +0200 [-] twistd 2.5.0 (/usr/bin/python 2.5.1) starting up
2008/10/27 15:02 +0200 [-] reactor class: <class 'twisted.internet.gtk2reactor.Gtk2Reactor'>
2008/10/27 15:02 +0200 [-] Loading /usr/share/vodafone-mobile-connect-card-driver-for-linux/gtk-tap.py...
2008/10/27 15:02 +0200 [-] Loaded.
2008/10/27 15:02 +0200 [-] Changing process name to VMCCdfL
2008/10/27 15:02 +0200 [-] Log opened.
2008/10/27 15:02 +0200 [-] twistd 2.5.0 (/home/klaas/ 2.5.1) starting up
2008/10/27 15:02 +0200 [-] reactor class: <class 'twisted.internet.gtk2reactor.Gtk2Reactor'>
2008/10/27 15:02 +0200 [-] Loading /usr/share/vodafone-mobile-connect-card-driver-for-linux/gtk-tap.py...
2008/10/27 15:02 +0200 [-] Loaded.
2008/10/27 15:02 +0200 [-] twisted.conch.manhole_ssh.ConchFactory starting on 2222
2008/10/27 15:02 +0200 [-] Starting factory <twisted.conch.manhole_ssh.ConchFactory instance at 0x8b0d74c>
2008/10/27 15:02 +0200 [-] SIMCardConnAdapter: SENDING ATCMD 'AT+CGMM\r\n'
2008/10/27 15:02 +0200 [-] SIMCardConnAdapter: NEW STATE: waiting
2008/10/27 15:02 +0200 [-] SIMCardConnAdapter::WAITING DATA_RCV: 'AT+CGMM\r'
2008/10/27 15:02 +0200 [-] "SIMCardConnAdapter::WAITING: Data AT+CGMM\r didn't match my regexp"
2008/10/27 15:02 +0200 [-] SIMCardConnAdapter::WAITING DATA_RCV: '\r\nE17X\r\n\r\nOK\r\n'
2008/10/27 15:02 +0200 [-] SIMCardConnAdapter::WAITING: EOR detected, firing deferred
2008/10/27 15:02 +0200 [-] SIMCardConnAdapter::WAITING: CBK = [('E17X',), ('OK',)]
2008/10/27 15:02 +0200 [-] SIMCardConnAdapter: NEW STATE: idle
2008/10/27 15:02 +0200 [-] SIMCardConnAdapter: SENDING ATCMD 'AT+CGMM\r\n'
2008/10/27 15:02 +0200 [-] SIMCardConnAdapter: NEW STATE: waiting
2008/10/27 15:02 +0200 [-] SIMCardConnAdapter::WAITING DATA_RCV: 'AT+CGMM\r'
2008/10/27 15:02 +0200 [-] "SIMCardConnAdapter::WAITING: Data AT+CGMM\r didn't match my regexp"
2008/10/27 15:02 +0200 [-] SIMCardConnAdapter::WAITING DATA_RCV: '\r\nE17X\r\n\r\nOK\r\n'
2008/10/27 15:02 +0200 [-] SIMCardConnAdapter::WAITING: EOR detected, firing deferred
2008/10/27 15:02 +0200 [-] SIMCardConnAdapter::WAITING: CBK = [('E17X',), ('OK',)]
2008/10/27 15:02 +0200 [-] SIMCardConnAdapter: NEW STATE: idle
2008/10/27 15:02 +0200 [-] SIMCardConnAdapter: SENDING ATCMD 'AT+CGMM\r\n'
2008/10/27 15:02 +0200 [-] SIMCardConnAdapter: NEW STATE: waiting
2008/10/27 15:02 +0200 [-] SIMCardConnAdapter::WAITING DATA_RCV: 'AT+CGMM\r'
2008/10/27 15:02 +0200 [-] "SIMCardConnAdapter::WAITING: Data AT+CGMM\r didn't match my regexp"
2008/10/27 15:02 +0200 [-] SIMCardConnAdapter::WAITING DATA_RCV: '\r\nE17X\r\n\r\nOK\r\n'
2008/10/27 15:02 +0200 [-] SIMCardConnAdapter::WAITING: EOR detected, firing deferred
2008/10/27 15:02 +0200 [-] SIMCardConnAdapter::WAITING: CBK = [('E17X',), ('OK',)]
2008/10/27 15:02 +0200 [-] SIMCardConnAdapter: NEW STATE: idle
2008/10/27 15:02 +0200 [-] SIMCardConnAdapter: SENDING ATCMD 'AT+CGMM\r\n'
2008/10/27 15:02 +0200 [-] SIMCardConnAdapter: NEW STATE: waiting
2008/10/27 15:02 +0200 [-] SIMCardConnAdapter::WAITING DATA_RCV: 'AT+CGMM\r'
2008/10/27 15:02 +0200 [-] "SIMCardConnAdapter::WAITING: Data AT+CGMM\r didn't match my regexp"
2008/10/27 15:02 +0200 [-] SIMCardConnAdapter::WAITING DATA_RCV: '\r\nE17X\r\n\r\nOK\r\n'
2008/10/27 15:02 +0200 [-] SIMCardConnAdapter::WAITING: EOR detected, firing deferred
2008/10/27 15:02 +0200 [-] SIMCardConnAdapter::WAITING: CBK = [('E17X',), ('OK',)]
2008/10/27 15:02 +0200 [-] /usr/lib/python2.5/site-packages/vmc/gtk/views/application.py:291: gtk.GtkWarning: gtk_widget_size_allocate(): attempt to allocate widget with width 588 and height -14
2008/10/27 15:02 +0200 [-] ADAPTING <vmc.common.plugins.huawei_e270.HuaweiE270 object at 0x8d42bcc> to <class 'vmc.common.hardware.huawei.HuaweiE2XXAdapter'>
2008/10/27 15:02 +0200 [-] DAEMONS: DAEMON SignalQualityDaemon started...
2008/10/27 15:02 +0200 [-] HuaweiE2XXAdapter: SENDING ATCMD 'AT+CSQ\r\n'
2008/10/27 15:02 +0200 [-] HuaweiE2XXAdapter: NEW STATE: waiting
2008/10/27 15:02 +0200 [-] DAEMONS: executing <bound method SignalQualityDaemon.function of <vmc.common.daemon.SignalQualityDaemon object at 0x8e1acac>> every 60 seconds
2008/10/27 15:02 +0200 [-] SIMCardConnAdapter: NEW STATE: idle
2008/10/27 15:02 +0200 [-] HuaweiE2XXAdapter::WAITING DATA_RCV: '\r\n+CME ERROR: SIM PIN required\r\n'
2008/10/27 15:02 +0200 [-] "HuaweiE2XXAdapter::WAITING: ERROR received '\\r\\n+CME ERROR: SIM PIN required\\r\\n'"
2008/10/27 15:02 +0200 [-] Unhandled error in Deferred:
2008/10/27 15:02 +0200 [-] Unhandled Error
        Traceback (most recent call last):
        Failure: vmc.common.exceptions.CMEErrorSIMPINRequired: +CME ERROR: SIM PIN required

2008/10/27 15:02 +0200 [-] HuaweiE2XXAdapter: NEW STATE: idle
2008/10/27 15:02 +0200 [-] HuaweiE2XXAdapter: SENDING ATCMD 'ATZ\r\n'
2008/10/27 15:02 +0200 [-] HuaweiE2XXAdapter: NEW STATE: waiting
2008/10/27 15:02 +0200 [-] HuaweiE2XXAdapter::WAITING DATA_RCV: 'ATZ\r'
2008/10/27 15:02 +0200 [-] "HuaweiE2XXAdapter::WAITING: Data ATZ\r didn't match my regexp"
2008/10/27 15:02 +0200 [-] HuaweiE2XXAdapter::WAITING DATA_RCV: '\r\nOK\r\n'
2008/10/27 15:02 +0200 [-] HuaweiE2XXAdapter::WAITING: EOR detected, firing deferred
2008/10/27 15:02 +0200 [-] HuaweiE2XXAdapter::WAITING: CBK = [()]
2008/10/27 15:02 +0200 [-] HuaweiE2XXAdapter: NEW STATE: idle
2008/10/27 15:02 +0200 [-] HuaweiE2XXAdapter: SENDING ATCMD 'ATE0\r\n'
2008/10/27 15:02 +0200 [-] HuaweiE2XXAdapter: NEW STATE: waiting
2008/10/27 15:02 +0200 [-] HuaweiE2XXAdapter::WAITING DATA_RCV: 'ATE0\r\r\nOK\r\n'
2008/10/27 15:02 +0200 [-] HuaweiE2XXAdapter::WAITING: EOR detected, firing deferred
2008/10/27 15:02 +0200 [-] HuaweiE2XXAdapter::WAITING: CBK = [()]
2008/10/27 15:02 +0200 [-] GTKBehaviour: LEAVING PreInit AND ENTERING INTO Auth

** (twistd:20489): WARNING **: couldn't read 4 bytes from gnome-keyring socket: Connection reset by peer
2008/10/27 15:02 +0200 [-] Instantiating AuthStateMachine ...
2008/10/27 15:02 +0200 [-] AuthStateMachine: Instantiating get_pin_status mode....
2008/10/27 15:02 +0200 [-] HuaweiE2XXAdapter: NEW STATE: idle
2008/10/27 15:02 +0200 [-] HuaweiE2XXAdapter: SENDING ATCMD 'AT+CPIN?\r\n'
2008/10/27 15:02 +0200 [-] HuaweiE2XXAdapter: NEW STATE: waiting
2008/10/27 15:02 +0200 [-] HuaweiE2XXAdapter::WAITING DATA_RCV: '\r\n+CPIN: SIM PIN\r\n\r\nOK\r\n'
2008/10/27 15:02 +0200 [-] HuaweiE2XXAdapter::WAITING: EOR detected, firing deferred
2008/10/27 15:02 +0200 [-] HuaweiE2XXAdapter::WAITING: CBK = [('SIM PIN',)]
2008/10/27 15:02 +0200 [-] HuaweiE2XXAdapter: NEW STATE: idle
2008/10/27 15:02 +0200 [-] HuaweiE2XXAdapter::IDLE DATA_RCV: '\r\n^BOOT:22633994,0,0,0,64\r\n'
2008/10/27 15:02 +0200 [-] HuaweiE2XXAdapter::Huawei E270 NOTIFICATION: '\r\n^BOOT:22633994,0,0,0,64\r\n'
2008/10/27 15:02 +0200 [-] AuthStateMachine: Instantiating pin_needed_status mode....
2008/10/27 15:02 +0200 [-] HuaweiE2XXAdapter: SENDING ATCMD 'AT+CPIN=0000\r\n'
2008/10/27 15:02 +0200 [-] HuaweiE2XXAdapter: NEW STATE: waiting
2008/10/27 15:02 +0200 [-] HuaweiE2XXAdapter::WAITING DATA_RCV: '\r\nOK\r\n'
2008/10/27 15:02 +0200 [-] HuaweiE2XXAdapter::WAITING: EOR detected, firing deferred
2008/10/27 15:02 +0200 [-] HuaweiE2XXAdapter::WAITING: CBK = [('OK',)]
2008/10/27 15:02 +0200 [-] AuthStateMachine: Giving 45 seconds to settle the SIM card...
2008/10/27 15:02 +0200 [-] HuaweiE2XXAdapter: NEW STATE: idle
2008/10/27 15:02 +0200 [-] HuaweiE2XXAdapter::IDLE DATA_RCV: '\r\n^RSSI:27\r\n'
2008/10/27 15:02 +0200 [-] HuaweiE2XXAdapter::Huawei E270 NOTIFICATION: '\r\n^RSSI:27\r\n'
2008/10/27 15:02 +0200 [-] HuaweiE2XXAdapter: QUEING <class 'vmc.common.notifications.UnsolicitedNotification'> args=('rssi', 27) kwds={}
2008/10/27 15:02 +0200 [-] HuaweiE2XXAdapter::IDLE DATA_RCV: '\r\n^MODE:5,4\r\n'
2008/10/27 15:02 +0200 [-] HuaweiE2XXAdapter::Huawei E270 NOTIFICATION: '\r\n^MODE:5,4\r\n'
2008/10/27 15:02 +0200 [-] HuaweiE2XXAdapter: QUEING <class 'vmc.common.notifications.UnsolicitedNotification'> args=('new_conn_mode', 'UMTS_SIGNAL') kwds={}
2008/10/27 15:02 +0200 [-] HuaweiE2XXAdapter::IDLE DATA_RCV: '\r\n^SIMST:1\r\n'
2008/10/27 15:02 +0200 [-] HuaweiE2XXAdapter::Huawei E270 NOTIFICATION: '\r\n^SIMST:1\r\n'
2008/10/27 15:02 +0200 [-] HuaweiE2XXAdapter::IDLE DATA_RCV: '\r\n^SRVST:2\r\n'
2008/10/27 15:02 +0200 [-] HuaweiE2XXAdapter::Huawei E270 NOTIFICATION: '\r\n^SRVST:2\r\n'
2008/10/27 15:02 +0200 [-] HuaweiE2XXAdapter::IDLE DATA_RCV: '\r\n^RSSI:15\r\n'
2008/10/27 15:02 +0200 [-] HuaweiE2XXAdapter::Huawei E270 NOTIFICATION: '\r\n^RSSI:15\r\n'
2008/10/27 15:02 +0200 [-] HuaweiE2XXAdapter: QUEING <class 'vmc.common.notifications.UnsolicitedNotification'> args=('rssi', 15) kwds={}
2008/10/27 15:02 +0200 [-] HuaweiE2XXAdapter::IDLE DATA_RCV: '\r\n^BOOT:22633994,0,0,0,64\r\n'
2008/10/27 15:02 +0200 [-] HuaweiE2XXAdapter::Huawei E270 NOTIFICATION: '\r\n^BOOT:22633994,0,0,0,64\r\n'
2008/10/27 15:02 +0200 [-] Shutting down...
2008/10/27 15:02 +0200 [-] (Port 2222 Closed)
2008/10/27 15:02 +0200 [-] Stopping factory <twisted.conch.manhole_ssh.ConchFactory instance at 0x8b0d74c>
2008/10/27 15:02 +0200 [-] Server Shut Down.
klaas@lenovo:~$ sudo vodafone-mobile-connect-card-driver-for-linux-debug
2008/10/27 15:02 +0200 [-] Log opened.
2008/10/27 15:02 +0200 [-] twistd 2.5.0 (/usr/bin/python 2.5.1) starting up
2008/10/27 15:02 +0200 [-] reactor class: <class 'twisted.internet.gtk2reactor.Gtk2Reactor'>
2008/10/27 15:02 +0200 [-] Loading /usr/share/vodafone-mobile-connect-card-driver-for-linux/gtk-tap.py...
2008/10/27 15:03 +0200 [-] Loaded.
2008/10/27 15:03 +0200 [-] Changing process name to VMCCdfL
2008/10/27 15:03 +0200 [-] Log opened.
2008/10/27 15:03 +0200 [-] twistd 2.5.0 (/home/klaas/ 2.5.1) starting up
2008/10/27 15:03 +0200 [-] reactor class: <class 'twisted.internet.gtk2reactor.Gtk2Reactor'>
2008/10/27 15:03 +0200 [-] Loading /usr/share/vodafone-mobile-connect-card-driver-for-linux/gtk-tap.py...
2008/10/27 15:03 +0200 [-] Loaded.
2008/10/27 15:03 +0200 [-] twisted.conch.manhole_ssh.ConchFactory starting on 2222
2008/10/27 15:03 +0200 [-] Starting factory <twisted.conch.manhole_ssh.ConchFactory instance at 0x8b0e74c>
2008/10/27 15:03 +0200 [-] SIMCardConnAdapter: SENDING ATCMD 'AT+CGMM\r\n'
2008/10/27 15:03 +0200 [-] SIMCardConnAdapter: NEW STATE: waiting
2008/10/27 15:03 +0200 [-] SIMCardConnAdapter::WAITING DATA_RCV: '\r\nE17X\r\n\r\nOK\r\n'
2008/10/27 15:03 +0200 [-] SIMCardConnAdapter::WAITING: EOR detected, firing deferred
2008/10/27 15:03 +0200 [-] SIMCardConnAdapter::WAITING: CBK = [('E17X',), ('OK',)]
2008/10/27 15:03 +0200 [-] SIMCardConnAdapter: NEW STATE: idle
2008/10/27 15:03 +0200 [-] SIMCardConnAdapter: SENDING ATCMD 'AT+CGMM\r\n'
2008/10/27 15:03 +0200 [-] SIMCardConnAdapter: NEW STATE: waiting
2008/10/27 15:03 +0200 [-] SIMCardConnAdapter::WAITING DATA_RCV: '\r\nE17X\r\n\r\nOK\r\n'
2008/10/27 15:03 +0200 [-] SIMCardConnAdapter::WAITING: EOR detected, firing deferred
2008/10/27 15:03 +0200 [-] SIMCardConnAdapter::WAITING: CBK = [('E17X',), ('OK',)]
2008/10/27 15:03 +0200 [-] SIMCardConnAdapter: NEW STATE: idle
2008/10/27 15:03 +0200 [-] SIMCardConnAdapter: SENDING ATCMD 'AT+CGMM\r\n'
2008/10/27 15:03 +0200 [-] SIMCardConnAdapter: NEW STATE: waiting
2008/10/27 15:03 +0200 [-] SIMCardConnAdapter::WAITING DATA_RCV: '\r\nE17X\r\n\r\nOK\r\n'
2008/10/27 15:03 +0200 [-] SIMCardConnAdapter::WAITING: EOR detected, firing deferred
2008/10/27 15:03 +0200 [-] SIMCardConnAdapter::WAITING: CBK = [('E17X',), ('OK',)]
2008/10/27 15:03 +0200 [-] SIMCardConnAdapter: NEW STATE: idle
2008/10/27 15:03 +0200 [-] SIMCardConnAdapter: SENDING ATCMD 'AT+CGMM\r\n'
2008/10/27 15:03 +0200 [-] SIMCardConnAdapter: NEW STATE: waiting
2008/10/27 15:03 +0200 [-] SIMCardConnAdapter::WAITING DATA_RCV: '\r\nE17X\r\n\r\nOK\r\n'
2008/10/27 15:03 +0200 [-] SIMCardConnAdapter::WAITING: EOR detected, firing deferred
2008/10/27 15:03 +0200 [-] SIMCardConnAdapter::WAITING: CBK = [('E17X',), ('OK',)]
2008/10/27 15:03 +0200 [-] /usr/lib/python2.5/site-packages/vmc/gtk/views/application.py:291: gtk.GtkWarning: gtk_widget_size_allocate(): attempt to allocate widget with width 588 and height -14
2008/10/27 15:03 +0200 [-] ADAPTING <vmc.common.plugins.huawei_e270.HuaweiE270 object at 0x8d41c6c> to <class 'vmc.common.hardware.huawei.HuaweiE2XXAdapter'>
2008/10/27 15:03 +0200 [-] DAEMONS: DAEMON SignalQualityDaemon started...
2008/10/27 15:03 +0200 [-] HuaweiE2XXAdapter: SENDING ATCMD 'AT+CSQ\r\n'
2008/10/27 15:03 +0200 [-] HuaweiE2XXAdapter: NEW STATE: waiting
2008/10/27 15:03 +0200 [-] DAEMONS: executing <bound method SignalQualityDaemon.function of <vmc.common.daemon.SignalQualityDaemon object at 0x8f26dcc>> every 60 seconds
2008/10/27 15:03 +0200 [-] SIMCardConnAdapter: NEW STATE: idle
2008/10/27 15:03 +0200 [-] HuaweiE2XXAdapter::WAITING DATA_RCV: '\r\n+CSQ: 16,99\r\n\r\nOK\r\n'
2008/10/27 15:03 +0200 [-] HuaweiE2XXAdapter::WAITING: EOR detected, firing deferred
2008/10/27 15:03 +0200 [-] HuaweiE2XXAdapter::WAITING: CBK = [('16', '99')]
2008/10/27 15:03 +0200 [-] HuaweiE2XXAdapter: NEW STATE: idle
2008/10/27 15:03 +0200 [-] HuaweiE2XXAdapter: SENDING ATCMD 'ATZ\r\n'
2008/10/27 15:03 +0200 [-] HuaweiE2XXAdapter: NEW STATE: waiting
2008/10/27 15:03 +0200 [-] HuaweiE2XXAdapter::WAITING DATA_RCV: '\r\nOK\r\n'
2008/10/27 15:03 +0200 [-] HuaweiE2XXAdapter::WAITING: EOR detected, firing deferred
2008/10/27 15:03 +0200 [-] HuaweiE2XXAdapter::WAITING: CBK = [()]
2008/10/27 15:03 +0200 [-] HuaweiE2XXAdapter: NEW STATE: idle
2008/10/27 15:03 +0200 [-] HuaweiE2XXAdapter: SENDING ATCMD 'ATE0\r\n'
2008/10/27 15:03 +0200 [-] HuaweiE2XXAdapter: NEW STATE: waiting
2008/10/27 15:03 +0200 [-] HuaweiE2XXAdapter::WAITING DATA_RCV: 'ATE0\r\r\nOK\r\n'
2008/10/27 15:03 +0200 [-] HuaweiE2XXAdapter::WAITING: EOR detected, firing deferred
2008/10/27 15:03 +0200 [-] HuaweiE2XXAdapter::WAITING: CBK = [()]
2008/10/27 15:03 +0200 [-] GTKBehaviour: LEAVING PreInit AND ENTERING INTO Auth

** (twistd:20597): WARNING **: couldn't read 4 bytes from gnome-keyring socket: Connection reset by peer
2008/10/27 15:03 +0200 [-] Instantiating AuthStateMachine ...
2008/10/27 15:03 +0200 [-] AuthStateMachine: Instantiating get_pin_status mode....
2008/10/27 15:03 +0200 [-] HuaweiE2XXAdapter: NEW STATE: idle
2008/10/27 15:03 +0200 [-] HuaweiE2XXAdapter: SENDING ATCMD 'AT+CPIN?\r\n'
2008/10/27 15:03 +0200 [-] HuaweiE2XXAdapter: NEW STATE: waiting
2008/10/27 15:03 +0200 [-] HuaweiE2XXAdapter::WAITING DATA_RCV: '\r\n+CPIN: READY\r\n\r\nOK\r\n'
2008/10/27 15:03 +0200 [-] HuaweiE2XXAdapter::WAITING: EOR detected, firing deferred
2008/10/27 15:03 +0200 [-] HuaweiE2XXAdapter::WAITING: CBK = [('READY',)]
2008/10/27 15:03 +0200 [-] GTKBehaviour: LEAVING Auth AND ENTERING INTO PostInit
2008/10/27 15:03 +0200 [-] HuaweiE2XXAdapter: NEW STATE: idle
2008/10/27 15:03 +0200 [-] HuaweiE2XXAdapter: SENDING ATCMD 'AT+CSCS=?\r\n'
2008/10/27 15:03 +0200 [-] HuaweiE2XXAdapter: NEW STATE: waiting
2008/10/27 15:03 +0200 [-] HuaweiE2XXAdapter::WAITING DATA_RCV: '\r\n+CSCS: ("IRA","GSM","UCS2")\r\n\r\nOK\r\n'
2008/10/27 15:03 +0200 [-] HuaweiE2XXAdapter::WAITING: EOR detected, firing deferred
2008/10/27 15:03 +0200 [-] HuaweiE2XXAdapter::WAITING: CBK = [('IRA',), ('GSM',), ('UCS2',)]
2008/10/27 15:03 +0200 [-] HuaweiE2XXAdapter: NEW STATE: idle
2008/10/27 15:03 +0200 [-] HuaweiE2XXAdapter: SENDING ATCMD 'AT+CNMI=2,1,0,0,0\r\n'
2008/10/27 15:03 +0200 [-] HuaweiE2XXAdapter: NEW STATE: waiting
2008/10/27 15:03 +0200 [-] HuaweiE2XXAdapter::WAITING DATA_RCV: '\r\nOK\r\n'
2008/10/27 15:03 +0200 [-] HuaweiE2XXAdapter::WAITING: EOR detected, firing deferred
2008/10/27 15:03 +0200 [-] HuaweiE2XXAdapter::WAITING: CBK = [()]
2008/10/27 15:03 +0200 [-] HuaweiE2XXAdapter: NEW STATE: idle
2008/10/27 15:03 +0200 [-] HuaweiE2XXAdapter: SENDING ATCMD 'AT+CMGF=0\r\n'
2008/10/27 15:03 +0200 [-] HuaweiE2XXAdapter: NEW STATE: waiting
2008/10/27 15:03 +0200 [-] HuaweiE2XXAdapter::WAITING DATA_RCV: '\r\nOK\r\n'
2008/10/27 15:03 +0200 [-] HuaweiE2XXAdapter::WAITING: EOR detected, firing deferred
2008/10/27 15:03 +0200 [-] HuaweiE2XXAdapter::WAITING: CBK = [()]
2008/10/27 15:03 +0200 [-] HuaweiE2XXAdapter: NEW STATE: idle
2008/10/27 15:03 +0200 [-] HuaweiE2XXAdapter: SENDING ATCMD 'AT+CPBR=?\r\n'
2008/10/27 15:03 +0200 [-] HuaweiE2XXAdapter: NEW STATE: waiting
2008/10/27 15:03 +0200 [-] HuaweiE2XXAdapter::WAITING DATA_RCV: '\r\nERROR\r\n'
2008/10/27 15:03 +0200 [-] "HuaweiE2XXAdapter::WAITING: ERROR received '\\r\\nERROR\\r\\n'"
2008/10/27 15:03 +0200 [-] HuaweiE2XXAdapter: NEW STATE: idle
2008/10/27 15:03 +0200 [-] HuaweiE2XXAdapter: SENDING ATCMD 'AT+CSCS?\r\n'
2008/10/27 15:03 +0200 [-] HuaweiE2XXAdapter: NEW STATE: waiting
2008/10/27 15:03 +0200 [-] HuaweiE2XXAdapter::WAITING DATA_RCV: '\r\n+CSCS: "IRA
2008/10/27 15:03 +0200 [-] HuaweiE2XXAdapter::WAITING: EOR detected, firing defe
2008/10/27 15:03 +0200 [-] HuaweiE2XXAdapter::WAITING: CBK = [('IRA',)]
2008/10/27 15:03 +0200 [-] HuaweiE2XXAdapter: NEW STATE: idle
2008/10/27 15:03 +0200 [-] HuaweiE2XXAdapter: SENDING ATCMD 'AT+CSCS="UCS2"\r\n'
2008/10/27 15:03 +0200 [-] HuaweiE2XXAdapter: NEW STATE: waiting
2008/10/27 15:03 +0200 [-] HuaweiE2XXAdapter::WAITING DATA_RCV: '\r\nOK\r\n'
2008/10/27 15:03 +0200 [-] HuaweiE2XXAdapter::WAITING: EOR detected, firing defe
2008/10/27 15:03 +0200 [-] HuaweiE2XXAdapter::WAITING: CBK = [()]
2008/10/27 15:03 +0200 [-] HuaweiE2XXAdapter: NEW STATE: idle
2008/10/27 15:03 +0200 [-] HuaweiE2XXAdapter::IDLE DATA_RCV: '\r\n^BOOT:22633994
2008/10/27 15:03 +0200 [-] HuaweiE2XXAdapter::Huawei E270 NOTIFICATION: '\r\n^BO
2008/10/27 15:03 +0200 [-] HuaweiE2XXAdapter::IDLE DATA_RCV: '\r\n^BOOT:22633994
2008/10/27 15:03 +0200 [-] HuaweiE2XXAdapter::Huawei E270 NOTIFICATION: '\r\n^BO
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter: SENDING ATCMD 'AT+CSQ\r\n'
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter: NEW STATE: waiting
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter::WAITING DATA_RCV: '\r\n+CSQ: 16,99
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter::WAITING: EOR detected, firing defe
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter::WAITING: CBK = [('16', '99')]
2008/10/27 15:04 +0200 [-] AuthStateMachine: notification <UnsolicitedNotificati
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter: NEW STATE: idle
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter::IDLE DATA_RCV: '\r\n^BOOT:22633994
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter::Huawei E270 NOTIFICATION: '\r\n^BO
2008/10/27 15:04 +0200 [-] Shutting down...
2008/10/27 15:04 +0200 [-] (Port 2222 Closed)
2008/10/27 15:04 +0200 [-] Stopping factory <twisted.conch.manhole_ssh.ConchFactory instance at 0x8b0e74c>
2008/10/27 15:04 +0200 [-] Server Shut Down.
klaas@lenovo:~$ sudo vodafone-mobile-connect-card-driver-for-linux-debug
2008/10/27 15:04 +0200 [-] Log opened.
2008/10/27 15:04 +0200 [-] twistd 2.5.0 (/usr/bin/python 2.5.1) starting up
2008/10/27 15:04 +0200 [-] reactor class: <class 'twisted.internet.gtk2reactor.Gtk2Reactor'>
2008/10/27 15:04 +0200 [-] Loading /usr/share/vodafone-mobile-connect-card-driver-for-linux/gtk-tap.py...
2008/10/27 15:04 +0200 [-] Loaded.
2008/10/27 15:04 +0200 [-] Changing process name to VMCCdfL
2008/10/27 15:04 +0200 [-] Log opened.
2008/10/27 15:04 +0200 [-] twistd 2.5.0 (/home/klaas/ 2.5.1) starting up
2008/10/27 15:04 +0200 [-] reactor class: <class 'twisted.internet.gtk2reactor.Gtk2Reactor'>
2008/10/27 15:04 +0200 [-] Loading /usr/share/vodafone-mobile-connect-card-driver-for-linux/gtk-tap.py...
2008/10/27 15:04 +0200 [-] Loaded.
2008/10/27 15:04 +0200 [-] twisted.conch.manhole_ssh.ConchFactory starting on 2222
2008/10/27 15:04 +0200 [-] Starting factory <twisted.conch.manhole_ssh.ConchFactory instance at 0x8b0d74c>
2008/10/27 15:04 +0200 [-] SIMCardConnAdapter: SENDING ATCMD 'AT+CGMM\r\n'
2008/10/27 15:04 +0200 [-] SIMCardConnAdapter: NEW STATE: waiting
2008/10/27 15:04 +0200 [-] SIMCardConnAdapter::WAITING DATA_RCV: '\r\nE17X\r\n\r\nOK\r\n'
2008/10/27 15:04 +0200 [-] SIMCardConnAdapter::WAITING: EOR detected, firing deferred
2008/10/27 15:04 +0200 [-] SIMCardConnAdapter::WAITING: CBK = [('E17X',), ('OK',)]
2008/10/27 15:04 +0200 [-] SIMCardConnAdapter: NEW STATE: idle
2008/10/27 15:04 +0200 [-] SIMCardConnAdapter: SENDING ATCMD 'AT+CGMM\r\n'
2008/10/27 15:04 +0200 [-] SIMCardConnAdapter: NEW STATE: waiting
2008/10/27 15:04 +0200 [-] SIMCardConnAdapter::WAITING DATA_RCV: '\r\nE17X\r\n\r\nOK\r\n'
2008/10/27 15:04 +0200 [-] SIMCardConnAdapter::WAITING: EOR detected, firing deferred
2008/10/27 15:04 +0200 [-] SIMCardConnAdapter::WAITING: CBK = [('E17X',), ('OK',)]
2008/10/27 15:04 +0200 [-] SIMCardConnAdapter: NEW STATE: idle
2008/10/27 15:04 +0200 [-] SIMCardConnAdapter: SENDING ATCMD 'AT+CGMM\r\n'
2008/10/27 15:04 +0200 [-] SIMCardConnAdapter: NEW STATE: waiting
2008/10/27 15:04 +0200 [-] SIMCardConnAdapter::WAITING DATA_RCV: '\r\nE17X\r\n\r\nOK\r\n'
2008/10/27 15:04 +0200 [-] SIMCardConnAdapter::WAITING: EOR detected, firing deferred
2008/10/27 15:04 +0200 [-] SIMCardConnAdapter::WAITING: CBK = [('E17X',), ('OK',)]
2008/10/27 15:04 +0200 [-] SIMCardConnAdapter: NEW STATE: idle
2008/10/27 15:04 +0200 [-] SIMCardConnAdapter: SENDING ATCMD 'AT+CGMM\r\n'
2008/10/27 15:04 +0200 [-] SIMCardConnAdapter: NEW STATE: waiting
2008/10/27 15:04 +0200 [-] SIMCardConnAdapter::WAITING DATA_RCV: '\r\nE17X\r\n\r\nOK\r\n'
2008/10/27 15:04 +0200 [-] SIMCardConnAdapter::WAITING: EOR detected, firing deferred
2008/10/27 15:04 +0200 [-] SIMCardConnAdapter::WAITING: CBK = [('E17X',), ('OK',)]
2008/10/27 15:04 +0200 [-] /usr/lib/python2.5/site-packages/vmc/gtk/views/application.py:291: gtk.GtkWarning: gtk_widget_size_allocate(): attempt to allocate widget with width 588 and height -14
2008/10/27 15:04 +0200 [-] ADAPTING <vmc.common.plugins.huawei_e270.HuaweiE270 object at 0x8d3ec6c> to <class 'vmc.common.hardware.huawei.HuaweiE2XXAdapter'>
2008/10/27 15:04 +0200 [-] DAEMONS: DAEMON SignalQualityDaemon started...
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter: SENDING ATCMD 'AT+CSQ\r\n'
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter: NEW STATE: waiting
2008/10/27 15:04 +0200 [-] DAEMONS: executing <bound method SignalQualityDaemon.function of <vmc.common.daemon.SignalQualityDaemon object at 0x8f26dcc>> every 60 seconds
2008/10/27 15:04 +0200 [-] SIMCardConnAdapter: NEW STATE: idle
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter::WAITING DATA_RCV: '\r\n+CSQ: 16,99\r\n\r\nOK\r\n'
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter::WAITING: EOR detected, firing deferred
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter::WAITING: CBK = [('16', '99')]
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter: NEW STATE: idle
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter: SENDING ATCMD 'ATZ\r\n'
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter: NEW STATE: waiting
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter::WAITING DATA_RCV: '\r\nOK\r\n'
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter::WAITING: EOR detected, firing deferred
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter::WAITING: CBK = [()]
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter: NEW STATE: idle
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter: SENDING ATCMD 'ATE0\r\n'
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter: NEW STATE: waiting
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter::WAITING DATA_RCV: 'ATE0\r\r\nOK\r\n'
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter::WAITING: EOR detected, firing deferred
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter::WAITING: CBK = [()]
2008/10/27 15:04 +0200 [-] GTKBehaviour: LEAVING PreInit AND ENTERING INTO Auth

** (twistd:20625): WARNING **: couldn't read 4 bytes from gnome-keyring socket: Connection reset by peer
2008/10/27 15:04 +0200 [-] Instantiating AuthStateMachine ...
2008/10/27 15:04 +0200 [-] AuthStateMachine: Instantiating get_pin_status mode....
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter: NEW STATE: idle
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter: SENDING ATCMD 'AT+CPIN?\r\n'
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter: NEW STATE: waiting
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter::WAITING DATA_RCV: '\r\n+CPIN: READY\r\n\r\nOK\r\n'
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter::WAITING: EOR detected, firing deferred
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter::WAITING: CBK = [('READY',)]
2008/10/27 15:04 +0200 [-] GTKBehaviour: LEAVING Auth AND ENTERING INTO PostInit
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter: NEW STATE: idle
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter: SENDING ATCMD 'AT+CSCS=?\r\n'
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter: NEW STATE: waiting
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter::WAITING DATA_RCV: '\r\n+CSCS: ("IRA","GSM","UCS2")\r\n\r\nOK\r\n'
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter::WAITING: EOR detected, firing deferred
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter::WAITING: CBK = [('IRA',), ('GSM',), ('UCS2',)]
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter: NEW STATE: idle
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter: SENDING ATCMD 'AT+CNMI=2,1,0,0,0\r\n'
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter: NEW STATE: waiting
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter::WAITING DATA_RCV: '\r\nOK\r\n'
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter::WAITING: EOR detected, firing deferred
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter::WAITING: CBK = [()]
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter: NEW STATE: idle
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter: SENDING ATCMD 'AT+CMGF=0\r\n'
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter: NEW STATE: waiting
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter::WAITING DATA_RCV: '\r\nOK\r\n'
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter::WAITING: EOR detected, firing deferred
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter::WAITING: CBK = [()]
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter: NEW STATE: idle
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter: SENDING ATCMD 'AT+CPBR=?\r\n'
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter: NEW STATE: waiting
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter::WAITING DATA_RCV: '\r\n+CPBR: (1-250),24,20\r\n\r\nOK\r\n'
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter::WAITING: EOR detected, firing deferred
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter::WAITING: CBK = [('250',)]
2008/10/27 15:04 +0200 [-] /usr/lib/python2.5/site-packages/vmc/gtk/controllers/application.py:236: gtk.GtkWarning: gtk_widget_set_events: assertion `!GTK_WIDGET_REALIZED (widget)' failed
2008/10/27 15:04 +0200 [-] GTKBehaviour: LEAVING PostInit AND ENTERING INTO NetReg
2008/10/27 15:04 +0200 [-] Instantiating NetworkRegStateMachine ....
2008/10/27 15:04 +0200 [-] NetworkRegStateMachine: NEW MODE: check_registered
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter: NEW STATE: idle
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter: SENDING ATCMD 'AT+CSCS?\r\n'
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter: NEW STATE: waiting
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter::WAITING DATA_RCV: '\r\n+CSCS: "IRA"\r\n\r\nOK\r\n'
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter::WAITING: EOR detected, firing deferred
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter::WAITING: CBK = [('IRA',)]
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter: NEW STATE: idle
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter: SENDING ATCMD 'AT+CPBR=1,250\r\n'
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter: NEW STATE: waiting
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter::WAITING DATA_RCV: '\r\n+CPBR: 1,"+31654501233",145,"Voicemail bellen"\r\n+CPBR: 2,"+31654500200",145,"Vodafone nummerinfo"\r\n+CPBR: 3,"+31654500100",145,"Klantenservice"\r\n+CPBR: 4,"+*#100#",255,"Mijn telefoonnummer"\r\n+CPBR: 5,"112",129,"Alarm nummer"\r\n+CPBR: 6,"09008844",129,"Politie Algemeen"\r\n+CPBR: 7,"+31654501231",145,"Voicemail aan"\r\n+CPBR: 8,"+31654501230",145,"Voicemail uit"\r\n\r\nOK\r\n'
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter::WAITING: EOR detected, firing deferred
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter::WAITING: CBK = [('1', '+31654501233', '145', 'Voicemail bellen'), ('2', '+31654500200', '145', 'Vodafone nummerinfo'), ('3', '+31654500100', '145', 'Klantenservice'), ('5', '112', '129', 'Alarm nummer'), ('6', '09008844', '129', 'Politie Algemeen'), ('7', '+31654501231', '145', 'Voicemail aan'), ('8', '+31654501230', '145', 'Voicemail uit')]
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter: NEW STATE: idle
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter: SENDING ATCMD 'AT+CSCS="IRA"\r\n'
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter: NEW STATE: waiting
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter::WAITING DATA_RCV: '\r\nOK\r\n'
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter::WAITING: EOR detected, firing deferred
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter::WAITING: CBK = [()]
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter: NEW STATE: idle
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter: SENDING ATCMD 'AT+CREG?\r\n'
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter: NEW STATE: waiting
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter::WAITING DATA_RCV: '\r\n+CREG: 0,1\r\n\r\nOK\r\n'
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter::WAITING: EOR detected, firing deferred
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter::WAITING: CBK = [('0', '1')]
2008/10/27 15:04 +0200 [-] NetworkRegStateMachine: NEW MODE: registration_finished
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter: NEW STATE: idle
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter: SENDING ATCMD 'AT+CSCS="UCS2"\r\n'
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter: NEW STATE: waiting
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter::WAITING DATA_RCV: '\r\nOK\r\n'
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter::WAITING: EOR detected, firing deferred
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter::WAITING: CBK = [()]
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter: NEW STATE: idle
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter: SENDING ATCMD 'AT+CMGL=4\r\n'
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter: NEW STATE: waiting
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter::WAITING DATA_RCV: '\r\nOK\r\n'
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter::WAITING: EOR detected, firing deferred
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter::WAITING: CBK = []
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter: NEW STATE: idle
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter: SENDING ATCMD 'AT+CSCS="UCS2"\r\n'
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter: NEW STATE: waiting
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter::WAITING DATA_RCV: '\r\nOK\r\n'
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter::WAITING: EOR detected, firing deferred
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter::WAITING: CBK = [()]
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter: NEW STATE: idle
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter: SENDING ATCMD 'AT+COPS?\r\n'
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter: NEW STATE: waiting
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter::WAITING DATA_RCV: '\r\n+COPS: 0,2,"20404",2\r\n\r\nOK\r\n'
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter::WAITING: EOR detected, firing deferred
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter::WAITING: CBK = [('0,2,"20404",2', None, '20404', '2')]
2008/10/27 15:04 +0200 [-] GTKBehaviour: LEAVING NetReg AND ENTERING INTO ImDone
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter: NEW STATE: idle
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter: SENDING ATCMD 'AT+CLCK="SC",2\r\n'
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter: NEW STATE: waiting
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter::WAITING DATA_RCV: '\r\n+CLCK: 1\r\n\r\nOK\r\n'
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter::WAITING: EOR detected, firing deferred
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter::WAITING: CBK = [('1',)]
2008/10/27 15:04 +0200 [-] /usr/lib/python2.5/site-packages/vmc/gtk/controllers/application.py:399: gobject.Warning: unable to set property `text' of type `gchararray' from value of type `PyObject'
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter: NEW STATE: idle
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter: SENDING ATCMD 'AT^SYSCFG=2,2,3FFFFFFF,2,4\r\n'
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter: NEW STATE: waiting
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter::WAITING DATA_RCV: '\r\n^BOOT:22633994,0,0,0,64\r\n'
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter::Huawei E270 NOTIFICATION: '\r\n^BOOT:22633994,0,0,0,64\r\n'
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter::WAITING DATA_RCV: '\r\nOK\r\n'
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter::WAITING: EOR detected, firing deferred
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter::WAITING: CBK = [()]
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter: NEW STATE: idle
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter: SENDING ATCMD 'AT+CSQ\r\n'
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter: NEW STATE: waiting
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter::WAITING DATA_RCV: '\r\n+CSQ: 16,99\r\n\r\nOK\r\n'
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter::WAITING: EOR detected, firing deferred
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter::WAITING: CBK = [('16', '99')]
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter: NEW STATE: idle
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter: SENDING ATCMD 'AT+COPS?\r\n'
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter: NEW STATE: waiting
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter::WAITING DATA_RCV: '\r\n+COPS: 0,2,"20404",2\r\n\r\nOK\r\n'
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter::WAITING: EOR detected, firing deferred
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter::WAITING: CBK = [('0,2,"20404",2', None, '20404', '2')]
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter: NEW STATE: idle
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter: SENDING ATCMD 'AT+COPS?\r\n'
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter: NEW STATE: waiting
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter::WAITING DATA_RCV: '\r\n+COPS: 0,2,"20404",2\r\n\r\nOK\r\n'
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter::WAITING: EOR detected, firing deferred
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter::WAITING: CBK = [('0,2,"20404",2', None, '20404', '2')]
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter: NEW STATE: idle
2008/10/27 15:04 +0200 [-] WVDIAL: DATA RECV WvDial<*1>: WvDial: Internet dialer version 1.56

2008/10/27 15:04 +0200 [-] WVDIAL: DATA RECV WvModem<*1>: Cannot get information for serial port.
2008/10/27 15:04 +0200 [-] WVDIAL: DATA RECV
        WvDial<*1>: Initializing modem.

2008/10/27 15:04 +0200 [-] WVDIAL: DATA RECV WvDial<*1>: Sending: ATZ

2008/10/27 15:04 +0200 [-] WVDIAL: DATA RECV WvDial Modem<*1>: OK
        WvDial<*1>: Sending: ATZ

2008/10/27 15:04 +0200 [-] WVDIAL: DATA RECV WvDial Modem<*1>: ATZ
        WvDial Modem<*1>: OK
        WvDial<*1>: Sending: ATQ0 V1 E0 S0=0 &C1 &D2 +FCLASS=0

2008/10/27 15:04 +0200 [-] WVDIAL: DATA RECV WvDial Modem<*1>: ATQ0 V1 E0 S0=0 &C1 &D2 +FCLASS=0
        WvDial Modem<*1>: OK
        WvDial<*1>: Sending: AT+CGDCONT=1,"IP","office.vodafone.nl"

2008/10/27 15:04 +0200 [-] WVDIAL: DATA RECV WvDial Modem<*1>: OK
        WvDial<*1>: Modem initialized.

2008/10/27 15:04 +0200 [-] WVDIAL: DATA RECV WvDial<*1>: Sending: ATDT*99***1#
        WvDial<*1>: Waiting for carrier.

2008/10/27 15:04 +0200 [-] WVDIAL: DATA RECV WvDial Modem<*1>: CONNECT
        WvDial<*1>: Carrier detected.  Starting PPP immediately.
        WvDial<Notice>: Starting pppd at Mon Oct 27 14:04:38 2008
        WvDial<Notice>: Pid of pppd: 20650

2008/10/27 15:04 +0200 [-] WVDIAL: DATA RECV WvDial<*1>: pppd: &#65533;{[06][08]&#65533;{[06][08]&#65533;&#65533;[06][08]
        WvDial<*1>: Using interface ppp0
        WvDial<*1>: pppd: &#65533;{[06][08]&#65533;{[06][08]&#65533;&#65533;[06][08]
        WvDial<*1>: pppd: &#65533;{[06][08]&#65533;{[06][08]&#65533;&#65533;[06][08]
        WvDial<*1>: pppd: &#65533;{[06][08]&#65533;{[06][08]&#65533;&#65533;[06][08]
        WvDial<*1>: pppd: &#65533;{[06][08]&#65533;{[06][08]&#65533;&#65533;[06][08]
        WvDial<*1>: pppd: &#65533;{[06][08]&#65533;{[06][08]&#65533;&#65533;[06][08]
        WvDial<*1>: pppd: &#65533;{[06][08]&#65533;{[06][08]&#65533;&#65533;[06][08]
        WvDial<*1>: pppd: &#65533;{[06][08]&#65533;{[06][08]&#65533;&#65533;[06][08]
        WvDial<*1>: pppd: &#65533;{[06][08]&#65533;{[06][08]&#65533;&#65533;[06][08]
        WvDial<*1>: pppd: &#65533;{[06][08]&#65533;{[06][08]&#65533;&#65533;[06][08]
        WvDial<*1>: pppd: &#65533;{[06][08]&#65533;{[06][08]&#65533;&#65533;[06][08]
        WvDial<*1>: pppd: &#65533;{[06][08]&#65533;{[06][08]&#65533;&#65533;[06][08]
        WvDial<*1>: Authentication (CHAP) started
        WvDial<*1>: pppd: &#65533;{[06][08]&#65533;{[06][08]&#65533;&#65533;[06][08]
        WvDial<*1>: pppd: &#65533;{[06][08]&#65533;{[06][08]&#65533;&#65533;[06][08]
        WvDial<*1>: pppd: &#65533;{[06][08]&#65533;{[06][08]&#65533;&#65533;[06][08]
        WvDial<*1>: pppd: &#65533;{[06][08]&#65533;{[06][08]&#65533;&#65533;[06][08]
        WvDial<*1>: Authentication (CHAP) successful
        WvDial<*1>: pppd: &#65533;{[06][08]&#65533;{[06][08]&#65533;&#65533;[06][08]
        WvDial<*1>: pppd: &#65533;{[06][08]&#65533;{[06][08]&#65533;&#65533;[06][08]
        WvDial<*1>: pppd: &#65533;{[06][08]&#65533;{[06][08]&#65533;&#65533;[06][08]
        WvDial<*1>: pppd: &#65533;{[06][08]&#65533;{[06][08]&#65533;&#65533;[06][08]

2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter::IDLE DATA_RCV: '\r\n^BOOT:22633994,0,0,0,64\r\n'
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter::Huawei E270 NOTIFICATION: '\r\n^BOOT:22633994,0,0,0,64\r\n'
2008/10/27 15:04 +0200 [-] WVDIAL: DATA RECV WvDial<*1>: pppd: &#65533;{[06][08]&#65533;{[06][08]&#65533;&#65533;[06][08]
        WvDial<*1>: pppd: &#65533;{[06][08]&#65533;{[06][08]&#65533;&#65533;[06][08]

2008/10/27 15:04 +0200 [-] WVDIAL: DATA RECV WvDial<*1>: pppd: &#65533;{[06][08]&#65533;{[06][08]&#65533;&#65533;[06][08]
        WvDial<*1>: pppd: &#65533;{[06][08]&#65533;{[06][08]&#65533;&#65533;[06][08]

2008/10/27 15:04 +0200 [-] WVDIAL: DATA RECV WvDial<*1>: pppd: &#65533;{[06][08]&#65533;{[06][08]&#65533;&#65533;[06][08]
        WvDial<*1>: pppd: &#65533;{[06][08]&#65533;{[06][08]&#65533;&#65533;[06][08]

2008/10/27 15:04 +0200 [-] WVDIAL: DATA RECV WvDial<*1>: pppd: &#65533;{[06][08]&#65533;{[06][08]&#65533;&#65533;[06][08]
        WvDial<*1>: pppd: &#65533;{[06][08]&#65533;{[06][08]&#65533;&#65533;[06][08]

2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter::IDLE DATA_RCV: '\r\n^MODE:5,5\r\n'
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter::Huawei E270 NOTIFICATION: '\r\n^MODE:5,5\r\n'
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter: QUEING <class 'vmc.common.notifications.UnsolicitedNotification'> args=('new_conn_mode', 'HSDPA_SIGNAL') kwds={}
2008/10/27 15:04 +0200 [-] WVDIAL: DATA RECV WvDial<*1>: pppd: &#65533;{[06][08]&#65533;{[06][08]&#65533;&#65533;[06][08]
        WvDial<*1>: pppd: &#65533;{[06][08]&#65533;{[06][08]&#65533;&#65533;[06][08]

2008/10/27 15:04 +0200 [-] WVDIAL: DATA RECV WvDial<*1>: pppd: &#65533;{[06][08]&#65533;{[06][08]&#65533;&#65533;[06][08]
        WvDial<*1>: pppd: &#65533;{[06][08]&#65533;{[06][08]&#65533;&#65533;[06][08]

2008/10/27 15:04 +0200 [-] WVDIAL: DATA RECV WvDial<*1>: Disconnecting at Mon Oct 27 14:04:44 2008

2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter::IDLE DATA_RCV: '\r\n^MODE:5,4\r\n'
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter::Huawei E270 NOTIFICATION: '\r\n^MODE:5,4\r\n'
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter: QUEING <class 'vmc.common.notifications.UnsolicitedNotification'> args=('new_conn_mode', 'UMTS_SIGNAL') kwds={}
2008/10/27 15:04 +0200 [-] WVDIAL: DATA RECV WvDial<*1>: The PPP daemon has died: A modem hung up the phone (exit code = 16)
        WvDial<*1>: man pppd explains pppd error codes in more detail.
        WvDial<Notice>: Try again and look into /var/log/messages and the wvdial and pppd man pages for more information.
        WvDial<Notice>: Auto Reconnect will be attempted in 5 seconds

libnotify-Message: Unable to get session bus: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

** (twistd:20625): CRITICAL **: dbus_g_proxy_connect_signal: assertion `DBUS_IS_G_PROXY (proxy)' failed

** (twistd:20625): CRITICAL **: dbus_g_proxy_connect_signal: assertion `DBUS_IS_G_PROXY (proxy)' failed

** (twistd:20625): CRITICAL **: dbus_g_proxy_call: assertion `DBUS_IS_G_PROXY (proxy)' failed
2008/10/27 15:04 +0200 [-] "Notification <ConnectionNotification at 0x8f435ec status: disconnected> not in {'rssi': <bound method ApplicationController._change_signal_level of <vmc.gtk.controllers.application.ApplicationController object at 0x8e16f4c>>, 'new_conn_mode': <bound method ApplicationController._conn_mode_changed of <vmc.gtk.controllers.application.ApplicationController object at 0x8e16f4c>>, 'sms': <bound method ApplicationController._on_sms_received of <vmc.gtk.controllers.application.ApplicationController object at 0x8e16f4c>>, 'speed': <bound method ApplicationController._change_net_stats_cb of <vmc.gtk.controllers.application.ApplicationController object at 0x8e16f4c>>, 'call': None}"
2008/10/27 15:04 +0200 [-] WVDIAL: DATA RECV WvModem<*1>: Cannot get information for serial port.Caught signal 15:  Attempting to exit gracefully...

2008/10/27 15:04 +0200 [-] 'EXIT CODE 1'
2008/10/27 15:04 +0200 [-] WVDIAL: DATA RECV
        WvDial<*1>: Initializing modem.

2008/10/27 15:04 +0200 [-] WVDIAL: DATA RECV WvDial<*1>: Sending: ATZ

2008/10/27 15:04 +0200 [-] WVDIAL: DATA RECV WvDial Modem<*1>: OK
        WvDial<*1>: Sending: ATZ

2008/10/27 15:04 +0200 [-] WVDIAL: DATA RECV WvDial Modem<*1>: ATZ
        WvDial Modem<*1>: OK
        WvDial<*1>: Sending: ATQ0 V1 E0 S0=0 &C1 &D2 +FCLASS=0

2008/10/27 15:04 +0200 [-] WVDIAL: DATA RECV WvDial Modem<*1>: ATQ0 V1 E0 S0=0 &C1 &D2 +FCLASS=0
        WvDial Modem<*1>: OK
        WvDial<*1>: Sending: AT+CGDCONT=1,"IP","office.vodafone.nl"

2008/10/27 15:04 +0200 [-] WVDIAL: DATA RECV WvDial Modem<*1>: OK
        WvDial<*1>: Modem initialized.

2008/10/27 15:04 +0200 [-] WVDIAL: DATA RECV WvDial<*1>: Disconnecting at Mon Oct 27 14:04:45 2008

2008/10/27 15:04 +0200 [-] WVDIAL: pppd closed their stdout!
2008/10/27 15:04 +0200 [-] WVDIAL: pppd closed their stderr.
2008/10/27 15:04 +0200 [-] WVDIAL: quitting
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter::IDLE DATA_RCV: '\r\n^BOOT:22633994,0,0,0,64\r\n'
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter::Huawei E270 NOTIFICATION: '\r\n^BOOT:22633994,0,0,0,64\r\n'
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter: SENDING ATCMD 'AT+COPS?\r\n'
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter: NEW STATE: waiting
2008/10/27 15:04 +0200 [-] WVDIAL: DATA RECV WvDial<*1>: WvDial: Internet dialer version 1.56

2008/10/27 15:04 +0200 [-] WVDIAL: DATA RECV WvModem<*1>: Cannot get information for serial port.
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter::WAITING DATA_RCV: '\r\n+COPS: 0,2,"20404",2\r\n\r\nOK\r\n'
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter::WAITING: EOR detected, firing deferred
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter::WAITING: CBK = [('0,2,"20404",2', None, '20404', '2')]
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter: NEW STATE: idle
2008/10/27 15:04 +0200 [-] WVDIAL: DATA RECV

2008/10/27 15:04 +0200 [-] WVDIAL: DATA RECV WvDial<*1>:
2008/10/27 15:04 +0200 [-] WVDIAL: DATA RECV Initializing modem.
2008/10/27 15:04 +0200 [-] WVDIAL: DATA RECV

2008/10/27 15:04 +0200 [-] WVDIAL: DATA RECV WvDial<*1>: Sending: ATZ

2008/10/27 15:04 +0200 [-] WVDIAL: DATA RECV WvDial Modem<*1>: OK
        WvDial<*1>: Sending: ATZ

2008/10/27 15:04 +0200 [-] WVDIAL: DATA RECV WvDial Modem<*1>: ATZ
        WvDial Modem<*1>: OK
        WvDial<*1>: Sending: ATQ0 V1 E0 S0=0 &C1 &D2 +FCLASS=0

2008/10/27 15:04 +0200 [-] WVDIAL: DATA RECV WvDial Modem<*1>: ATQ0 V1 E0 S0=0 &C1 &D2 +FCLASS=0
        WvDial Modem<*1>: OK
        WvDial<*1>: Sending: AT+CGDCONT=1,"IP","office.vodafone.nl"

2008/10/27 15:04 +0200 [-] WVDIAL: DATA RECV WvDial Modem<*1>: OK
        WvDial<*1>: Modem initialized.
        WvDial<*1>: Sending: ATDT*99***1#
        WvDial<*1>: Waiting for carrier.

2008/10/27 15:04 +0200 [-] WVDIAL: DATA RECV WvDial Modem<*1>: CONNECT
        WvDial<*1>: Carrier detected.  Starting PPP immediately.

2008/10/27 15:04 +0200 [-] WVDIAL: DATA RECV WvDial<Notice>: Starting pppd at Mon Oct 27 14:04:55 2008

2008/10/27 15:04 +0200 [-] WVDIAL: DATA RECV WvDial<Notice>: Pid of pppd: 20674

2008/10/27 15:04 +0200 [-] WVDIAL: DATA RECV WvDial<*1>: pppd: &#65533;{[06][08]&#65533;{[06][08]&#65533;&#65533;[06][08]
        WvDial<*1>: Using interface ppp0
        WvDial<*1>: pppd: &#65533;{[06][08]&#65533;{[06][08]&#65533;&#65533;[06][08]
        WvDial<*1>: pppd: &#65533;{[06][08]&#65533;{[06][08]&#65533;&#65533;[06][08]
        WvDial<*1>: pppd: &#65533;{[06][08]&#65533;{[06][08]&#65533;&#65533;[06][08]
        WvDial<*1>: pppd: &#65533;{[06][08]&#65533;{[06][08]&#65533;&#65533;[06][08]
        WvDial<*1>: pppd: &#65533;{[06][08]&#65533;{[06][08]&#65533;&#65533;[06][08]
        WvDial<*1>: pppd: &#65533;{[06][08]&#65533;{[06][08]&#65533;&#65533;[06][08]
        WvDial<*1>: pppd: &#65533;{[06][08]&#65533;{[06][08]&#65533;&#65533;[06][08]
        WvDial<*1>: pppd: &#65533;{[06][08]&#65533;{[06][08]&#65533;&#65533;[06][08]
        WvDial<*1>: pppd: &#65533;{[06][08]&#65533;{[06][08]&#65533;&#65533;[06][08]
        WvDial<*1>: pppd: &#65533;{[06]
2008/10/27 15:04 +0200 [-] WVDIAL: DATA RECV [08]&#65533;{[06][08]&#65533;&#65533;[06][08]
        WvDial<*1>: pppd: &#65533;{[06][08]&#65533;{[06][08]&#65533;&#65533;[06][08]
        WvDial<*1>: Authentication (CHAP) started
        WvDial<*1>: pppd: &#65533;{[06][08]&#65533;{[06][08]&#65533;&#65533;[06][08]
        WvDial<*1>: pppd: &#65533;{[06][08]&#65533;{[06][08]&#65533;&#65533;[06][08]
        WvDial<*1>: pppd: &#65533;{[06][08]&#65533;{[06][08]&#65533;&#65533;[06][08]
        WvDial<*1>: pppd: &#65533;{[06][08]&#65533;{[06][08]&#65533;&#65533;[06][08]
        WvDial<*1>: Authentication (CHAP) successful
        WvDial<*1>: pppd: &#65533;{[06][08]&#65533;{[06][08]&#65533;&#65533;[06][08]
        WvDial<*1>: pppd: &#65533;{[06][08]&#65533;{[06][08]&#65533;&#65533;[06][08]
        WvDial<*1>: pppd: &#65533;{[06][08]&#65533;{[06][08]&#65533;&#65533;[06][08]
        WvDial<*1>: pppd: &#65533;{[06][08]&#65533;{[06][08]&#65533;&#65533;[06][08]

2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter::IDLE DATA_RCV: '\r\n^BOOT:22633994,0,0,0,64\r\n'
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter::Huawei E270 NOTIFICATION: '\r\n^BOOT:22633994,0,0,0,64\r\n'
2008/10/27 15:04 +0200 [-] WVDIAL: DATA RECV WvDial<*1>: pppd: &#65533;{[06][08]&#65533;{[06][08]&#65533;&#65533;[06][08]
        WvDial<*1>: pppd: &#65533;{[06][08]&#65533;{[06][08]&#65533;&#65533;[06][08]

2008/10/27 15:04 +0200 [-] WVDIAL: DATA RECV WvDial<*1>: pppd: &#65533;{[06][08]&#65533;{[06][08]&#65533;&#65533;[06][08]
        WvDial<*1>: pppd: &#65533;{[06][08]&#65533;{[06][08]&#65533;&#65533;[06][08]

2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter::IDLE DATA_RCV: '\r\n^MODE:5,5\r\n'
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter::Huawei E270 NOTIFICATION: '\r\n^MODE:5,5\r\n'
2008/10/27 15:04 +0200 [-] HuaweiE2XXAdapter: QUEING <class 'vmc.common.notifications.UnsolicitedNotification'> args=('new_conn_mode', 'HSDPA_SIGNAL') kwds={}
2008/10/27 15:04 +0200 [-] WVDIAL: DATA RECV WvDial<*1>: pppd: &#65533;{[06][08]&#65533;{[06][08]&#65533;&#65533;[06][08]
        WvDial<*1>: pppd: &#65533;{[06][08]&#65533;{[06][08]&#65533;&#65533;[06][08]

2008/10/27 15:04 +0200 [-] WVDIAL: DATA RECV WvDial<*1>: pppd: &#65533;{[06][08]&#65533;{[06][08]&#65533;&#65533;[06][08]
        WvDial<*1>: pppd: &#65533;{[06][08]&#65533;{[06][08]&#65533;&#65533;[06][08]

2008/10/27 15:04 +0200 [-] WVDIAL: DATA RECV WvDial<*1>: Disconnecting at Mon Oct 27 14:04:59 2008

2008/10/27 15:04 +0200 [-] WVDIAL: DATA RECV WvDial<*1>: The PPP daemon has died: A modem hung up the phone (exit code = 16)
        WvDial<*1>: man pppd explains pppd error codes in more detail.
        WvDial<Notice>: Try again and look into /var/log/messages and the wvdial and pppd man pages for more information.
        WvDial<Notice>: Auto Reconnect will be attempted in 5 seconds


** (twistd:20625): CRITICAL **: dbus_g_proxy_call: assertion `DBUS_IS_G_PROXY (proxy)' failed

** (twistd:20625): CRITICAL **: dbus_g_proxy_disconnect_signal: assertion `DBUS_IS_G_PROXY (proxy)' failed

** (twistd:20625): CRITICAL **: dbus_g_proxy_disconnect_signal: assertion `DBUS_IS_G_PROXY (proxy)' failed
libnotify-Message: Unable to get session bus: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

** (twistd:20625): CRITICAL **: dbus_g_proxy_connect_signal: assertion `DBUS_IS_G_PROXY (proxy)' failed

** (twistd:20625): CRITICAL **: dbus_g_proxy_connect_signal: assertion `DBUS_IS_G_PROXY (proxy)' failed

** (twistd:20625): CRITICAL **: dbus_g_proxy_call: assertion `DBUS_IS_G_PROXY (proxy)' failed
2008/10/27 15:04 +0200 [-] "Notification <ConnectionNotification at 0x8b14d2c status: disconnected> not in {'rssi': <bound method ApplicationController._change_signal_level of <vmc.gtk.controllers.application.ApplicationController object at 0x8e16f4c>>, 'new_conn_mode': <bound method ApplicationController._conn_mode_changed of <vmc.gtk.controllers.application.ApplicationController object at 0x8e16f4c>>, 'sms': <bound method ApplicationController._on_sms_received of <vmc.gtk.controllers.application.ApplicationController object at 0x8e16f4c>>, 'speed': <bound method ApplicationController._change_net_stats_cb of <vmc.gtk.controllers.application.ApplicationController object at 0x8e16f4c>>, 'call': None}"
2008/10/27 15:04 +0200 [-] WVDIAL: DATA RECV Caught signal 15:  Attempting to exit gracefully...
        WvModem<*1>: Cannot get information for serial port.
2008/10/27 15:04 +0200 [-] 'EXIT CODE 1'
2008/10/27 15:04 +0200 [-] WVDIAL: DATA RECV
        WvDial<*1>: Initializing modem.

2008/10/27 15:04 +0200 [-] WVDIAL: DATA RECV WvDial<*1>: Sending: ATZ

2008/10/27 15:05 +0200 [-] WVDIAL: DATA RECV WvDial Modem<*1>: OK
        WvDial<*1>: Sending: ATZ

2008/10/27 15:05 +0200 [-] WVDIAL: DATA RECV WvDial Modem<*1>: ATZ
        WvDial Modem<*1>: OK
        WvDial<*1>: Sending: ATQ0 V1 E0 S0=0 &C1 &D2 +FCLASS=0

2008/10/27 15:05 +0200 [-] WVDIAL: DATA RECV WvDial Modem<*1>: ATQ0 V1 E0 S0=0 &C1 &D2 +FCLASS=0
        WvDial Modem<*1>: OK
        WvDial<*1>: Sending: AT+CGDCONT=1,"IP","office.vodafone.nl"

2008/10/27 15:05 +0200 [-] HuaweiE2XXAdapter::IDLE DATA_RCV: '\r\n^MODE:5,4\r\n'
2008/10/27 15:05 +0200 [-] HuaweiE2XXAdapter::Huawei E270 NOTIFICATION: '\r\n^MODE:5,4\r\n'
2008/10/27 15:05 +0200 [-] HuaweiE2XXAdapter: QUEING <class 'vmc.common.notifications.UnsolicitedNotification'> args=('new_conn_mode', 'UMTS_SIGNAL') kwds={}
2008/10/27 15:05 +0200 [-] WVDIAL: DATA RECV WvDial Modem<*1>: OK
        WvDial<*1>: Modem initialized.

2008/10/27 15:05 +0200 [-] WVDIAL: DATA RECV WvDial<*1>: Disconnecting at Mon Oct 27 14:05:00 2008

2008/10/27 15:05 +0200 [-] WVDIAL: pppd closed their stdout!
2008/10/27 15:05 +0200 [-] WVDIAL: pppd closed their stderr.
2008/10/27 15:05 +0200 [-] WVDIAL: quitting
2008/10/27 15:05 +0200 [-] HuaweiE2XXAdapter::IDLE DATA_RCV: '\r\n^BOOT:22633994,0,0,0,64\r\n'
2008/10/27 15:05 +0200 [-] HuaweiE2XXAdapter::Huawei E270 NOTIFICATION: '\r\n^BOOT:22633994,0,0,0,64\r\n'

```

---

### Post by GeorgeVita on 2008-10-28
Can you give some info for "other readers" of this forum?

> **klaasvanschelven said:**
> 
...t quite unrelated, since I'm using Ubuntu.


What version of Ubuntu are you using?

> **klaasvanschelven said:**
> 
WVDIAL: DATA RECV WvDial<*1>: WvDial: Internet dialer version 1.56

2008/10/27 15:04 +0200 [-] WVDIAL: DATA RECV WvModem<*1>: Cannot get information for serial port.
2008/10/27 15:04 +0200 [-] WVDIAL: DATA RECV...


You are using an old version of wvdial (1.56 as swown above). Is this your selection?

Also why you need a 'heavy' s/w to connect? What are the benefits (easy to use, information about data traffic, details for the quality of connection)?

Regards
GeorgeVita

---

