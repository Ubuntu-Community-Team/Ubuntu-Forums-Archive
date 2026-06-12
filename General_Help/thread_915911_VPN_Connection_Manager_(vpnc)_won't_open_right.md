---
title: "VPN Connection Manager (vpnc) won't open right"
date: 2008-09-10
forum: General Help
---

### Post by fiddler616 on 2008-09-10
Hello,
So I need to access a VPN (which is powered (word choice?) by Cisco), and I came across this tutorial:[http://www.cs.umn.edu/help/offsite/vpn.php](http://www.cs.umn.edu/help/offsite/vpn.php)
So I installed vpnc from the Terminal using aptitude, and it wasn't in my menu. So after getting nervous, I right clicked Applications, saw the Edit Menu, and made it appear. And clicked on it, and got the following error message:
> 
Failed to execute child process "nm-vpn-properties" (No such file or directory)
And I reinstalled from Synaptic, and got the same thing.
So....what do I do?
Thanks in advance

---

### Post by whitethorn on 2008-09-10
you need to install kvpnc from synaptic it's the GUI to vpnc.

```
sudo apt-get update && sudo apt-get install kvpnc
```

---

### Post by fiddler616 on 2008-09-10
Thank you.
Unrelated to OP: the sudo apt-get update bit just updates the apt-get program...right? And the && is an "and" in Terminal-speak?
(It's taken me three months to realize how useful the Terminal is, and now I'm trying to, er, use it)
I'd love to mark this as solved...but it's still installing.

---

### Post by fiddler616 on 2008-09-10
Fail: Applications => Internet => vpnc
> Failed to execute child process "nm-vpn-properties" (No such file or directory)
So in Terminal:
```
tmacdonald@Stanway01:~$ sudo apt-get install nm-vpn-properties
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package nm-vpn-properties
tmacdonald@Stanway01:~$ sudo aptitude install nm-vpn-properties
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
Couldn't find any package whose name or description matched "nm-vpn-properties"
Couldn't find any package whose name or description matched "nm-vpn-properties"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      

```

---

### Post by whitethorn on 2008-09-11
After you've installed KVPNC, you should be able to open it under.

Applications -> Internet -> KVpnc

There you should be able to able to edit vpnc.  Vpnc is terminal only, so if you click on it it doesn't have a GUI (Graphical User Interface)  There's not really a way that would work.  I had a look at the howto you added above, and there's no need to install kvpnc, it's mostly all done in the terminal.  So far you've gotten pretty much 2/3 done.  You've installed vpnc, now all you need to do is setup the connection file.  

you now have to create a file in /etc/vpnc/

```
gksudo cs-vpn.conf
```

in here we copy

> IPSec gateway <Host>
IPSec ID <Username>
IPSec secret <Password>
Xauth username <your_CS_username>
Where <Host>, <Username>, and <Password> are taken from the bottom of the VPN download page  [https://wwws.cs.umn.edu/vpn/](https://wwws.cs.umn.edu/vpn/)
and <your_CS_username> is your normal CS username. (Don't include the brackets.) 
Save the file and exit.

now to connect to

```
sudo vpnc cs-vpn
```

Enter your CS password when prompted.
To disconnect, type:

```
sudo vpnc-disconnect
```

Some of this I just copied from the webpage you linked above. Clicking on vpnc from Applications won't work.  You could try setting this up with kvpn, some programs don't have a GUI and work only in the terminal.  As for nm-vpn-properties I guess it's a plugin for your network manager, If you want to try that I've find a thread about getting nm-vpn-properties to work, but it's for dapper which is a little outdated.  Found here.

[http://ubuntuforums.org/showthread.php?t=162334&highlight=nm-vpn-properties](http://ubuntuforums.org/showthread.php?t=162334&highlight=nm-vpn-properties)

Best thing is just to stay with the terminal.

---

### Post by fiddler616 on 2008-09-11
The GUI version was right there all along...how did I not see it? *Smack*.
That said, all I have is: username, password, IP address (?)(Or something that looks like one). And this is leading to problems.

---

