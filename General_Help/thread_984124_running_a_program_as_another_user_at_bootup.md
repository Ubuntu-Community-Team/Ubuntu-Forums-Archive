---
title: "running a program as another user at bootup"
date: 2008-11-16
forum: General Help
---

### Post by graysky on 2008-11-16
I need to execute the command to start my vncserver as another user in a startup script.  Since I planned to put it in my /etc/init.d/local, root will be running the command BUT I do not want the root being the owner of the resulting vncserver. I thought I could use sudo -u USERNAME /path/to/vncserver but that gives an error when I tested it from a root shell:

```
# sudo -u spartan /usr/bin/vncserver -geometry 1280x1024 -alwaysshared
Wrong type or access mode of /root/.vnc.
```

It's as if vncserver is ignoring the sudo command and attempting to run at root... this command works with other programs such as xcalc:

```
# sudo -u spartan xcalc
```

Now xcalc is loaded and I checked to see the user owner via:

```
# ps aux | grep xcalc
spartan  5152  0.7  0.2   5532  2308 pts/0    S    11:03   0:00 xcalc
```

What am I doing wrong with vncserver?

---

### Post by Peter09 on 2008-11-16
The thing to remember is that although the program runs as a different user it still looks in /root for its home path. Is this the problem?

---

### Post by graysky on 2008-11-16
> **Peter09 said:**
> The thing to remember is that although the program runs as a different user it still looks in /root for its home path. Is this the problem?

Yeah... the contents of /home/spartan/.vnc are unique and the vncserver writes a log to that same dir... if the sudo command is running the program as 'spartan' but using the /root/.vnc for the log and pid lock file, etc. that won't work.  Is there nothing I can do to accomplish this in my startup script?

---

### Post by Peter09 on 2008-11-16
I had a similar problem, in the end I put a link from the file in /root directory to the file in the directory in the user files system.

---

### Post by graysky on 2008-11-16
No need for that.  Just added this to my /etc/init.d/local

```
su -c '/usr/bin/vncserver -geometry 1280x960 -alwaysshared' squishy
```

Be sure to:

```
# chmod a+x /etc/init.d/local
# update-rc.d local defaults
```

That's it... works at boot under the right username!

---

