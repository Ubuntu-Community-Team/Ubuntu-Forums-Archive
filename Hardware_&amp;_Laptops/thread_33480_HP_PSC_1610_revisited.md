---
title: "HP PSC 1610 revisited"
date: 2005-05-11
forum: Hardware &amp; Laptops
---

### Post by Calgarian on 2005-05-11
I finally gave up on the install and rebuilt Kubuntu from scratch to clean up everything. I then followed the install instructions for hplip-0.9.2 exactly, except I have to use KDE Print Manager becuase the http:/localhost:631 is disabled in the browser. Now I can't get hp-toolbox to run at all. It ran once and found no HP backend devices. I did a new "make install" and now I get:

update-rc.d: error: expected runlevel [0-9S] (did you forget "." ?)
usage: update-rc.d [-n] [-f] <basename> remove
       update-rc.d [-n] <basename> defaults [NN | sNN kNN]
       update-rc.d [-n] <basename> start|stop NN runlvl [runlvl] [...] .
                -n: not really
                -f: force
make[3]: Leaving directory `/home/dick/Packages/hplip-0.9.2'
make[2]: Leaving directory `/home/dick/Packages/hplip-0.9.2'
make[1]: Leaving directory `/home/dick/Packages/hplip-0.9.2'
dick@cm-85-152-81-63:~/Packages/hplip-0.9.2$ hp-toolbox
toolbox
toolbox HP Linux Imaging and Printing System (ver. 0.9.2)
toolbox HP Device Manager ver. 4.0
toolbox
toolbox Copyright (c) 2003-5 Hewlett-Packard Development Company, LP
toolbox This software comes with ABSOLUTELY NO WARRANTY.
toolbox This is free software, and you are welcome to distribute it
toolbox under certain conditions. See COPYING file for more details.
toolbox
toolbox Listening on localhost port 32796
Traceback (most recent call last):
  File "/usr/bin/hp-toolbox", line 446, in ?
    sys.exit( main( sys.argv[1:] ) )
  File "/usr/bin/hp-toolbox", line 368, in main
    toolbox = devmgr4( toolboxCleanup )
  File "/usr/share/hplip/ui/devmgr4.py", line 244, in __init__
    self.hpiod_sock.connect( ( prop.hpiod_host, prop.hpiod_port ) )
  File "<string>", line 1, in connect
socket.error: (111, 'Connection refused')
dick@cm-85-152-81-63:~/Packages/hplip-0.9.2$

Any thoughts?

---

