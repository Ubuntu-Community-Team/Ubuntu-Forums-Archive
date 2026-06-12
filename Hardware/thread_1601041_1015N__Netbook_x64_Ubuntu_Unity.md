---
title: "1015N  Netbook x64 Ubuntu Unity"
date: 2010-10-19
forum: Hardware
---

### Post by Techrocket9 on 2010-10-19
This is a little embarrassing, but I honestly don't know what to do. I have a 1015N Netbook. I installed Netbook Remix x64 from the x64 mini install CD loaded onto a flash drive. I finally have it booted, but it dumps me at a command line. I enter username and password and then have the typical @Netbook-Ubuntu:~$

I *think* that I just need some command to kickstart Unity, but I'm not sure what. I tried sudo start /etc/init.d/unity , but that did not work. (Unknown Job)

I'd appreciate any help you could provide me.


P.S. I am aware of the following:

1. I'd have fewer problems on x32 (I want x64 anyway)

2. I could run the full desktop OS b/c the 1015N is almost a full-blown laptop (I want to run Unity)

---

### Post by mikewhatever on 2010-10-19
The command you are looking for is probably **sudo startx** or **sudo service gdm start** . That said, you shouldn't need to do that, and since xserver doesn't autostart, something must be wrong.

---

### Post by Techrocket9 on 2010-10-19
> **mikewhatever said:**
> The command you are looking for is probably **sudo startx** or **sudo service gdm start** . That said, you shouldn't need to do that, and since xserver doesn't autostart, something must be wrong.

**sudo startx (output):**
```
command not found
```

**sudo service gdm start (output):**
```
gdm: unrecognized service
```

Any more ideas? Could it be something else because it is the Netbook version? Is Unity just a gnome derivative?

---

### Post by mikewhatever on 2010-10-20
I don't know about something else. What exactly did you install on top of the CLI system?
PS: Unity is Canonical's in house product that utilizes Gnome's new windows manager, Mutter.

---

### Post by Techrocket9 on 2010-10-20
I did the mini x64 10.10 install disk (the one where it downloads all the files at the time of install). Part way through it asks you which Ubuntu package you want to install (Desktop, server, Netbook, and a few others). I chose Netbook, and it spent 15 min or so pulling and installing more packages. No errors were reported by the installer.

---

### Post by Techrocket9 on 2010-10-21
Bump for more advice.

---

### Post by mikewhatever on 2010-10-21
Check if you have gdm and Xorg installed with the following command:
```
dpkg -l | grep "gdm\|Xorg"
```

The output should look something like this
```

ii  gdm       2.28.1-0ubuntu2.2      GNOME Display Manager
ii  gdm-guest-session  0.14         gdm extension for guest session
ii  xserver-xorg-core   2:1.6.4-2ubuntu4.3     Xorg X server - core server

```

'ii' signifies the package is installed.

---

### Post by Techrocket9 on 2010-10-21
> **mikewhatever said:**
> Check if you have gdm and Xorg installed with the following command:
```
dpkg -l | grep "gdm\|Xorg"
```

The output should look something like this
```

ii  gdm       2.28.1-0ubuntu2.2      GNOME Display Manager
ii  gdm-guest-session  0.14         gdm extension for guest session
ii  xserver-xorg-core   2:1.6.4-2ubuntu4.3     Xorg X server - core server

```

'ii' signifies the package is installed.

Both ```
dpkg -l | grep "gdm\|Xorg"
``` and ```
sudo dpkg -l | grep "gdm\|Xorg"
``` produce no output. ](*,)

---

### Post by mikewhatever on 2010-10-21
How about **dpkg -l | grep ubuntu-netbook**? Ubuntu-netbook is the metapackage that pulls in all the required components, graphics, tools, programs, etc. Try installing it again.

---

### Post by Techrocket9 on 2010-10-22
A ```
sudo apt-get install ubuntu-netbook
``` has it pulling and installing dozens of packages, so my hopes are high.

[s]**Preliminary Thanks Awarded**[/s]

Full thanks awarded. Issue resolved!

---

