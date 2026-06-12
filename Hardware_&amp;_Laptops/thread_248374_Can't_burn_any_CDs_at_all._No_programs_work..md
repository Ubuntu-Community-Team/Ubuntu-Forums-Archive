---
title: "Can't burn any CDs at all. No programs work."
date: 2006-09-01
forum: Hardware &amp; Laptops
---

### Post by SZF2001 on 2006-09-01
OK, so I've recently installed Kubuntu 6.06. Before I had Breezy and my USB DVD burner worked before - I remember I would go days just burning CD after CD.

After I get done, I remember I need to burn a CD for a friend. I try to open up K3b... I can't. No graphical loading screen shows, nothing - just the K3B logo bouncing on my mouse for a minute then it just stops. I try running it from the terminal with sudo, and literally let it sit there a day - nothing happened.

So I install graveman.

It sits there and tries to find any CD writable devices. I literally left it up for two hours and it didn't get past zero percent. After I tell it to close, I get this bubbled message:

```
Cannot save configuration file !
I have tried on those files:
/home/coleman/.config/graveman/graveman.conf
/etc/xdg/graveman/graveman.conf
```

Huh. Odd. I figure I'll give K3B another try, and try some new things. I uninstalled and reinstalled it - the same thing happened.

Then I remember in Breezy there is a K3B setup, right? So I try to get it to open from the terminal and this is what I get:

```
Password:
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kdeinit: Can't connect to the X Server.
kdeinit: Might not terminate at end of session.
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kded: cannot connect to X server :0.0
DCOP aborting call from 'anonymous-9423' to 'kded'
kded: ERROR: Communication problem with kded, it probably crashed.
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kcontrol: cannot connect to X server :0.0
DCOP aborting call from 'anonymous-9414' to 'kcontrol'
ERROR: Communication problem with kcontrol, it probably crashed.
coleman@coleman-desktop:~$ kdesu kcontrol
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Creating link /root/.kde/socket-coleman-desktop.
Created link from "/root/.kde/socket-coleman-desktop" to "/tmp/ksocket-root"
Creating link /root/.kde/tmp-coleman-desktop.
Created link from "/root/.kde/tmp-coleman-desktop" to "/tmp/kde-root"
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kbuildsycoca running...
Link points to "/var/tmp/kdecache-root"
Invalid entry (missing '=') at /tmp/kde-root/kconf_updatejFB2uc.tmp:1
kdeinit: Shutting down running client.
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
---------------------------------
It looks like dcopserver is already running. If you are sure
that it is not already running, remove /root/.DCOPserver_coleman-desktop__0
and start dcopserver again.
---------------------------------

KDE Daemon (kded) already running.
```

I get the KDE Setup page, go to Administrative settings, and go to K3B Setup. I leave it there while I go to school, right? I come back and it's still sitting there, "trying" to load up.

WHAT. THE. HELL. ](*,)

My DVD drive is fine. I've not even had it for a year, it works on my other Windows XP (not on the same machine) and worked with K/Ubuntu 5.10 and Ubuntu 6.06. Why won't it do crap now? Is there just a simple file I've not configured? This is a real hassle for me guys... Please help.

---

### Post by encompass on 2006-09-01
Have your tried running the programs as root?  If it works we know your issue.

---

### Post by SZF2001 on 2006-09-01
Yes, I have...

---

### Post by encompass on 2006-09-01
And it didn't work?  If it still didn't work... I have gone as far as I know... sorry I can't help you any further.

---

### Post by back2ubuntu on 2006-09-01
Hello,

For me it does work with root, but as a user I can launch k3b but cannot burn a cd/dvd.

thanks for any help.

---

### Post by SZF2001 on 2006-09-01
Can anyone help me please please PLEASE? I don't wanna resort to going to Gnome...

---

### Post by encompass on 2006-09-02
It works in Gnome!?
I thought it just didn't ever work.
I haven't a clue now.  Sorry...
As for the other statement... I would be hijacking this thread if I answered here.  Please start a new thread as it will help more people that way.  Sorry.  (Hit, it has to do with your user rights...(duh))

---

### Post by encompass on 2006-09-02
Make sure that when you uninstall it you do a Fully remove option AND you will have a (odds are) K3B DIR in your home directory... delete that.
Does it help?
You could also check to see if you can mount an ordinary cd in the drive.
It may be you don't ahve the settings in your fstab.  It can happen.

---

### Post by SZF2001 on 2006-09-02
I'm going to try the full uninstall in a minute. My computer is a little slow.

But to answer the other question - yes, this is what makes things even weirder. The drive is fully functional - I can read CDs off of it, rip CDs and put music on my computer with it, but it is just having the crappiest time opening K3B or even wanting to burn any CDs.

Is there a terminal based burner? Maybe I could install that, and paste everything it says if there are problems.

---

### Post by encompass on 2006-09-02
If I am not mistaken all burning software in linux basicly uses the terminal program cdrecord.... look it up here on the forums and other places.  It is very powerful... I have a slow computer too and love to use the console for everything.  Post your favorite howto or link aobut it here to help others.

---

### Post by tatimmer on 2006-09-02
I have a script on my website that uses cdrecord and mkisofs to burn a data-cd of an entire directory.

---

