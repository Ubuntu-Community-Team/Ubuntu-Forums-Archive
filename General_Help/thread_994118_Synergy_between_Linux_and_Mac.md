---
title: "Synergy between Linux and Mac"
date: 2008-11-26
forum: General Help
---

### Post by liquidfunk on 2008-11-26
I can't seem to figure out what's wrong with my Synergy set up. I installed it both on my Mac and my Linux box.

I created a synergy.conf and moved it to /etc.

Then ran


```
synergys -f --config /etc/synergy.conf
```

Then I get this from the terminal:


```
josh@localhost /]$ synergys -f --config /etc/synergy.conf
INFO: synergys.cpp,1042: Synergy server 1.3.1 on Linux 2.6.27.5-41.fc9.x86_64 #1 SMP Thu Nov 13 20:29:07 EST 2008 x86_64
DEBUG: synergys.cpp,1051: opening configuration "/etc/synergy.conf"
ERROR: synergys.cpp,1068: cannot read configuration "/etc/synergy.conf": read error: line 3: missing argument name
synergys: no configuration available

```

Any ideas? 

 I'm running on Fedora 9, but I thought I'd post it here too.

---

### Post by kanikilu on 2008-11-26
It says there's a problem on line 3 of your configuration file...so you might want to post what that line is (or the whole file).

---

### Post by liquidfunk on 2008-11-26
This is the conf file: 
```

section: screens
  LinuxBox:
    
  MacBook:
    
end

section: links
   MacBook:
    right = LinuxBox
  LinuxBox:
    left = MacBook
end

section: aliases
  LinuxBox:
    192.168.1.4
  MacBook:
    192.168.1.2
end
```

---

### Post by kanikilu on 2008-11-26
This may be an obvious question, but have you tried removing the blank lines after the screen names?

From the Synergy configuration guide:

> screens

args is a list of screen names, **one name per line**, each followed by a colon. Names are arbitrary strings but they must be unique. The hostname of each computer is recommended.

---

### Post by liquidfunk on 2008-11-26
Ok, I think we are getting closer, I removed the spaces, now I get: 
```

[josh@localhost ~]$ synergys -f --config /etc/synergy.conf
INFO: synergys.cpp,1042: Synergy server 1.3.1 on Linux 2.6.27.5-41.fc9.x86_64 #1 SMP Thu Nov 13 20:29:07 EST 2008 x86_64
DEBUG: synergys.cpp,1051: opening configuration "/etc/synergy.conf"
DEBUG: synergys.cpp,1062: configuration read successfully
FATAL: synergys.cpp,655: unknown screen name `localhost.localdomain'
```

---

### Post by kanikilu on 2008-11-26
It sounds like Synergy wants the hostnames listed there under Screens:

> The hostname of each computer is recommended. (This is the computer's network name on win32 and the name reported by the program hostname on Unix and OS X. Note that OS X may append .local to the name you gave your computer; e.g. somehost.local.)

Maybe run "hostname" on both machines and replace "LinuxBox" and "Macbook" with those results...?

Check to see that both machines can ping each other using a hostname.

It's been over a year since I used Synergy, so I'm not really sure what else to try...

---

### Post by liquidfunk on 2008-11-26
Wahey! Got it! 

 Though I can only do it backward! I want to control my mac from my desktop mouse, but its mac to desktop using the trackpad. 

 If I try to connect the mac, I get 
```

WARNING: failed to connect to server: Connection refused
```

---

### Post by liquidfunk on 2008-11-26
Its ok, I've solved it! Thanks a bunch!

---

### Post by Dagur on 2010-09-24
How did you solve it?

---

