---
title: "HPLIP - still an issue"
date: 2005-05-19
forum: Hardware &amp; Laptops
---

### Post by Calgarian on 2005-05-19
I have been reading all the threads on PSC printers and HPLIP. I can get the printer to work, but I can't get the scanner to work. I have uninstalled and re-installed hplip several times. I get the same error every time I try to do make install:

update-rc.d: error: expected runlevel [0-9S] (did you forget "." ?)
usage: update-rc.d [-n] [-f] <basename> remove
       update-rc.d [-n] <basename> defaults [NN | sNN kNN]
       update-rc.d [-n] <basename> start|stop NN runlvl [runlvl] [...] .
                -n: not really
                -f: force
make[3]: Leaving directory `/home/dick/Development/Packages/hplip-0.9.2'
make[2]: Leaving directory `/home/dick/Development/Packages/hplip-0.9.2'
make[1]: Leaving directory `/home/dick/Development/Packages/hplip-0.9.2'

I use the KDE Print Manager to define the device at the point in the instructions where it requests you use localhost:631 as that option is disallowed. I selected the PSC 1600 from the HP device list (not the PSC 1600 hpijs model).

If I mess around with hpoj and such I can get the scanner to work once. If I turn off the printer and turn it back on it's gone. I'm concerned about some permission issues, but not sure with what files. the hp toolkit is not in the K menu and when I use the command line it does not find any such devices when I try it. The device is not getting registered in the backend and I can't figure out why not?

---

### Post by Calgarian on 2005-05-19
I don't know why, but now it seems to work. I rebooted my system to try and clear all the various components. I still don't have toolbox on the menu, but I can fix that. However, it won't work:

toolbox
toolbox HP Linux Imaging and Printing System (ver. 0.9.2)
toolbox HP Device Manager ver. 4.0
toolbox
toolbox Copyright (c) 2003-5 Hewlett-Packard Development Company, LP
toolbox This software comes with ABSOLUTELY NO WARRANTY.
toolbox This is free software, and you are welcome to distribute it
toolbox under certain conditions. See COPYING file for more details.
toolbox
toolbox Listening on localhost port 32804
Traceback (most recent call last):
  File "/usr/share/hplip/toolbox", line 446, in ?
    sys.exit( main( sys.argv[1:] ) )
  File "/usr/share/hplip/toolbox", line 368, in main
    toolbox = devmgr4( toolboxCleanup )
  File "/usr/share/hplip/ui/devmgr4.py", line 244, in __init__
    self.hpiod_sock.connect( ( prop.hpiod_host, prop.hpiod_port ) )
  File "<string>", line 1, in connect
socket.error: (111, 'Connection refused')

Oh well, as long as the scanner and printer works I guess.

---

