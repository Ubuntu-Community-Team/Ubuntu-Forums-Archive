---
title: "pytrainer help please"
date: 2008-09-19
forum: General Help
---

### Post by drewk1 on 2008-09-19
I have installed pytrainer but when I try to run it I get:

location: /usr/lib/xulrunner-1.9.0.1/libxpcom.so 
before 3
Traceback (most recent call last):
  File "/usr/bin/pytr", line 44, in <module>
    main()
  File "/usr/bin/pytr", line 41, in main
    pytrainer = pyTrainer(None, data_path)
  File "/usr/lib/python2.5/site-packages/pytrainer/main.py", line 61, in __init__
    self.webservice = webService(data_path,self.refreshWaypointView,self.newRecord)
  File "/usr/lib/python2.5/site-packages/pytrainer/lib/soapUtils.py", line 33, in __init__
    self.server = SOAPpy.ThreadingSOAPServer(("localhost", 8081))
  File "/var/lib/python-support/python2.5/SOAPpy/Server.py", line 676, in __init__
    SocketServer.ThreadingTCPServer.__init__(self, addr, RequestHandler)
  File "/usr/lib/python2.5/SocketServer.py", line 330, in __init__
    self.server_bind()
  File "/usr/lib/python2.5/SocketServer.py", line 341, in server_bind
    self.socket.bind(self.server_address)
  File "<string>", line 1, in bind
socket.error: (99, 'Cannot assign requested address')

Any suggestions on how I can fix this as it seems the pytrainer website is down at the moment.

Thanks

---

### Post by drewk1 on 2008-09-23
Has anyone managed to get this working on Hardy?

---

### Post by twisted_steel on 2008-10-03
I did manage to get version 1.5.0.0.1 to start on my machine.  I haven't tried the other versions and don't have any GPS or heart rate monitors to use.  I went to the download page and clicked on the Download link for "Other GNU/Linux Users".  After extracting the file and going into the directory, I ran:

```
./setup.py build
sudo ./setup.py install
```

I tried running it and noticed that I didn't have all of the prerequisites installed, so I added python-matplotlib and python-soappy.  Here is the output of it starting up:

```
location: /usr/lib/xulrunner-1.9.0.3/libxpcom.so 
before 3
this function is obsolete, use getValue instead
this function is obsolete, use getValue instead
this function is obsolete, use getValue instead
this function is obsolete, use getValue instead
this function is obsolete, use getValue instead
this function is obsolete, use getValue instead
this function is obsolete, use getValue instead
No Active Plugins
No Active Extensions
```

---

### Post by vanhooglesnort on 2008-10-24
I really would like to get this running on Hardy as well...

---

