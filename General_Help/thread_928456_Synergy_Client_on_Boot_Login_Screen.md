---
title: "Synergy Client on Boot Login Screen"
date: 2008-09-24
forum: General Help
---

### Post by moloth on 2008-09-24
Found this [http://ubuntuforums.org/showthread.php?t=48196 Post #9]("http://ubuntuforums.org/showthread.php?t=48196") to get your client working on the login screen.

It works flawlessly for _Reboot_ and _Log Out_ :KS:KS:KS:KS:KS. 

Just wondering if you can get it working for _Switch User_?

> Starting the Synergy CLIENT on boot up.

These instructions should work for running the synergy client on your UBUNTU machine to connect to a locally networked computer running the synergy server. (I've not actually tried them myself.)
Let us know how you get on.

NOTE:
The <address of server machine> will probably be an ip address that looks something like 192.168.0.1 (DON'T put in the exact string <address of server machine>)

To make the client run when gdm runs, but before anyone has logged in:

edit /etc/gdm/Init/Default:

```
sudo gedit /etc/gdm/Init/Default
```

Added the following lines in the middle of the file **BEFORE** the "sysmodmap=/etc/X11/Xmodmap" line:

```
SYNERGYC=`gdmwhich synergyc`
if [ x$SYNERGYC != x ] ; then
        $SYNERGYC <address of server machine>
fi
```

The only problem with that is once you log in it kills off the client, so you need to make it start again for you.

edited /etc/gdm/PreSession/Default:

```
sudo gedit /etc/gdm/PreSession/Default
```

Added the following lines in the middle of the file **BEFORE** the "XSETROOT=`gdmwhich xsetroot`" line:

```
SYNERGYC=`gdmwhich synergyc`
if [ x$SYNERGYC != x ] ; then
        $SYNERGYC <address of server machine>
fi
```

Log out and back in again.

The synergy client should now startup and run whenever your gdm session does.

NOTE:
The <address of server machine> will probably be an ip address that looks something like 192.168.0.1 (DON'T put in the exact string <address of server machine>)


---

### Post by SergeantScar on 2009-02-20
I see I am really late in replying to this thread, but i was having a lot of troubles getting synergy to work on startup. What you have posed didn't work for me, here is what did.

1. Went to System > Preferences > Sessions
   On the Startup Programs tab click Add
   Set the name to "Synergy Startup" (again minus the quotes)
   Set the command to "/usr/bin/synergyc <server address>"

2. Opened terminal and typed 

```
sudo /etc/gdm/Init/Default
```

Then added the following to the beginning of the file

```
/usr/bin/killall synergyc
sleep 1
/usr/bin/synergyc <name_of_server/IP_of_server>
```

Next, 

```
sudo /etc/gdm/PreSession/Default
```

Then added the following to the file RIGHT BEFORE 

# Set background color
XSETROOT=`gdmwhich xsetroot`

```
/usr/bin/killall synergyc
sleep 1
/usr/bin/synergyc --restart -n <name_of_server/IP_of_server>
```

After this I restarted and i was able to use my XP keyboard and mouse in the login screen and any other time i log out.

It took me forever to get this all working on Intrepid Ibex..

---

