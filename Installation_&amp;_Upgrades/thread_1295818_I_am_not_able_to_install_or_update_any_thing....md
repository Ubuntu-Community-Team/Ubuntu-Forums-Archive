---
title: "I am not able to install or update any thing..."
date: 2009-10-19
forum: Installation &amp; Upgrades
---

### Post by aprashanth on 2009-10-19
I am not able to install or upgrade anything.. 
when I give the command in the terminal .. it gives the following error...

```

tsrinu@tsrinu-desktop:~$ sudo apt-get install vncserver 
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
```

---

### Post by drs305 on 2009-10-19
Open a terminal and type this:
```

sudo dpkg --configure -a

```

You won't see your password when you type it.

---

### Post by aprashanth on 2009-10-20
> **drs305 said:**
> Open a terminal and type this:
```

sudo dpkg --configure -a

```

You won't see your password when you type it.
```

tsrinu@tsrinu-desktop:~$ sudo dpkg --configure -a
Setting up odbcinst1debian1 (2.2.11-16build1) ...

Setting up msttcorefonts (2.4) ...

These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.

--12:00:40--  http://surfnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
           => `./andale32.exe'
Resolving surfnet.dl.sourceforge.net... 130.59.138.21
Connecting to surfnet.dl.sourceforge.net|130.59.138.21|:80... failed: Connection timed out.
Giving up.

--12:00:45--  http://internap.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
           => `./andale32.exe'
Resolving internap.dl.sourceforge.net... 69.88.152.3
Connecting to internap.dl.sourceforge.net|69.88.152.3|:80... failed: Connection timed out.
Giving up.

--12:00:53--  http://puzzle.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
           => `./andale32.exe'
Resolving puzzle.dl.sourceforge.net... 195.141.111.5
Connecting to puzzle.dl.sourceforge.net|195.141.111.5|:80... failed: Connection timed out.
Giving up.

--12:00:59--  http://heanet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
           => `./andale32.exe'
Resolving heanet.dl.sourceforge.net... 193.1.193.66
Connecting to heanet.dl.sourceforge.net|193.1.193.66|:80... failed: Connection timed out.
Giving up.

--12:01:09--  http://superb-west.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
           => `./andale32.exe'
Resolving superb-west.dl.sourceforge.net... 209.160.59.253
Connecting to superb-west.dl.sourceforge.net|209.160.59.253|:80... failed: Connection timed out.
Giving up.

--12:01:14--  http://superb-east.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
           => `./andale32.exe'
Resolving superb-east.dl.sourceforge.net... 209.160.66.130
Connecting to superb-east.dl.sourceforge.net|209.160.66.130|:80... 


```

what should I do next..

---

### Post by MelDJ on 2009-10-20
does synaptic work? or does it tell you to repair broken packages?

---

### Post by aprashanth on 2009-10-20
> **MelDJ said:**
> does synaptic work? or does it tell you to repair broken packages?
no its not working.. I mean to fix the broken packages...

---

### Post by K.Mandla on 2009-10-20
> **aprashanth said:**
> what should I do next..
It's trying to download the font files to install them. Are you connected to the Internet?

---

### Post by aprashanth on 2009-10-20
> **K.Mandla said:**
> It's trying to download the font files to install them. Are you connected to the Internet?
ya I tried even that.. but that was also showing the following error...

```

root@tsrinu-desktop:/home/tsrinu/Desktop# dpkg -i msttcorefonts_2.4_all
dpkg: error processing msttcorefonts_2.4_all (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 msttcorefonts_2.4_all

```

Bythe way I am connected to internet

Shall catch up with you later tomorrow..

---

