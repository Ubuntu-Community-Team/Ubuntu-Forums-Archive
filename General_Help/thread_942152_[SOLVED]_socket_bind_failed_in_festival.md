---
title: "[SOLVED] socket: bind failed in festival"
date: 2008-10-08
forum: General Help
---

### Post by sjbaugh on 2008-10-08
I have written a program (in python) that uses festival. I start festival in server mode:

```
festival --server
``` 

and get it to talk using festival_client

This has been working well but now I get:
socket: bind failed
I assume that the IP Port that festival uses in in use.
I have checked that festival is not running (using System Monitor in gnome) before I issue the command in terminal. I have re-booted (more than once).

I have had the occasional lock-up and I wonder if the port has become "stuck".
I have found that festival uses port 1314. When I do a port scan on my machine in Network Tools I find that port 1314 is open all the time to service:
xtelw
and port 1313 is always open to service xtel. I can find no process running with these names. On an Ubuntu 8.04 running in VirtualBox neither of these ports are in use.

Is there anything I can do about this?

Thanks, Steve

---

### Post by sjbaugh on 2008-10-09
I have also checked that festival works when not in server mode:

echo "hello" | festival --tts

works correctly.

---

### Post by sjbaugh on 2008-10-28
Bump please!

---

### Post by Portmanteaufu on 2008-10-28
I think if you read through this it may help:

[http://www.cstr.ed.ac.uk/projects/festival/manual/festival_28.html](http://www.cstr.ed.ac.uk/projects/festival/manual/festival_28.html)

I'm not very experienced with Festival, but it appears you can configure the server to use a different port, then run the client with a --port flag. If the only problem is that the default port is already taken, you should be set.

---

### Post by sjbaugh on 2008-10-28
Portmanteaufu,

Thanks for that info. After reading the url you suggested I think I can see how to do that and it will get me going again.

It is, though, masking the stuck port problem which I would like to know how to free. As the ports remain stuck after a re-boot it would seem that the port usage is stored in the file system somewhere. Is this perhaps a kernel issue or is the IP stack located somewhere else?

Any further help from someone would be appreciated.

Steve

---

### Post by Portmanteaufu on 2008-10-28
I think perhaps the first thing to try might be stopping the service that seems to be bogarting port 1314. I checked with the Ubuntu package repository listings -- apparently xtel is an X client for the French Minitel system. I didn't realize that Minitel was still in use! Who knew?

Anyway, if you didn't install that package yourself, maybe you can just get rid of it through Synaptic and reboot? Or if you do actually need it, just prevent it from running at boot time. Either way it won't start up so it won't sit on 1314.

Hope that helps!

---

### Post by sjbaugh on 2008-10-28
No Luck! I found that xtel was not installed. To see if it would free the ports, I installed xtel, ran it, closed it and uninstalled it (Complete removal). The ports are still stuck as above.

---

### Post by Portmanteaufu on 2008-10-28
Hm. Upon further reading, it seems like 1313 and 1314 are just reserved in general for Minitel, much the same way port 22 is reserved in general for ssh. I think (but I'm not certain) that in cases like this, you can still use reserved ports if you ask for them as root... so you could try running the festival server with sudo? The same link I gave earlier listed a number of security concerns about the server though, so I would read that carefully before running it as root.

---

### Post by sjbaugh on 2008-10-28
Thanks for all the suggestions, but when I tried:

sudo festival --server

I still got "socket: bind failed".

Steve

---

### Post by podex_at on 2008-11-01
Hi!

Today I had exactly the same problem. (FYI, I want xastir to speak with me)

~$ sudo netstat -ln --program|grep 1314

this gives the reason:
tcp        0      0 0.0.0.0:1314     0.0.0.0:*    LISTEN      5036/aprsd  

It's the APRS-daemon! But I want that it works, so I have to find out how to circumvent this port issue.

grx,
Christof

---

### Post by Portmanteaufu on 2008-11-01
Just found this: 

There's a command called "lsof" (list open files) that can be used to determine which program is currently holding a socket.

Try 

```
lsof -i
``` or ```
lsof -i TCP:1314
```

and see if it doesn't tell you which process to shut down to get your port back. For those that don't know, when you find the process id (pid) of what you want to kill, you can kill it with: 

```
kill -9 [pid]
```

---

### Post by sjbaugh on 2008-11-01
Christof,

Thanks!

I have just uninstalled the APRS software (complete removal) which I installed recently, including aprsd, and there is now no sign of the ports being used!

I am running Ubuntu 64 bit and I have a VirtualBox running 32 bit Ubuntu for 32 bit only software, and I will re-install the APRS on that. Would this be an option for you?

Thanks again,

Steve (G4AUC)

---

