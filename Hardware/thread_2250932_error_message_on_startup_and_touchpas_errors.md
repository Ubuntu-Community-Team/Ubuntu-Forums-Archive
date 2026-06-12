---
title: "error message on startup and touchpas errors"
date: 2014-10-31
forum: Hardware
---

### Post by josbarteling on 2014-10-31
Hi ubuntu community, this is my first post so I'll introduce myself. My name is Jos and im a dutch IT manager, my job consists mostly of just helpdesk problems and keep the servers running.

Now about the problem I'm having, I installed ubuntu 14.04 LTS on a chromebook (toshiba CB30). At first the touchpad didn't work at all, but a kernel update fixed it. Now I'm getting the following error message on boot: ¨[      1.625422] usb 1-4: language id specifier not provided by device, defaulting to english.¨ this message stays for about 1 minute before it disappears and continues booting into ubuntu.

I've tried to see whats going on by putting xinput in my terminal which gives me:

```
root@jos-Leon:/home/jos# xinput 
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Cypress APA Trackpad (cyapa)                id=12    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=10    [slave  keyboard (3)]
    &#8627; TOSHIBA Web Camera - HD                     id=11    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=13    [slave  keyboard (3)]

```
since number 4 is a touchpad I assume that's the problem.

when I check the device properties with xinput list-props 4 it gives me

```
root@jos-Leon:/home/jos# xinput list-props 4
Device 'Virtual core XTEST pointer':
    Device Enabled (138):    1
    Coordinate Transformation Matrix (140):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
    XTEST Device (254):    1

```

it doesn't look like its doing anything, but whenever i try to disable it by doing xinput disable 4 im getting the following message

```
root@jos-Leon:/home/jos# xinput disable 4
X Error of failed request:  BadAccess (attempt to access private resource denied)
  Major opcode of failed request:  131 (XInputExtension)
  Minor opcode of failed request:  57 ()
  Serial number of failed request:  20
  Current serial number in output stream:  21

```
with i'm trying xinput set-prop 4 138 0 i'm getting this mesage

```
root@jos-Leon:/home/jos# xinput set-prop 4 138 0
X Error of failed request:  BadAccess (attempt to access private resource denied)
  Major opcode of failed request:  131 (XInputExtension)
  Minor opcode of failed request:  57 ()
  Serial number of failed request:  19
  Current serial number in output stream:  20

```


Does anyone know how to get rid of the annoying message on boot or a way to disable that touchpad? it's really annoying to wait 1 or 2 minutes before booting.
I'd really appreciate it.


Thanks in advance.

---

### Post by Bucky Ball on 2014-11-01
Welcome. Your touchpad is working fine you say. The error message is about USB and a language identifier, which I imagine has nothing to do with your touchpad. If the touchpad ain't broke, don't fix it. I would start researching elsewhere.

Boot your machine, wait for the error message to clear and the machine to boot to a desktop, once there paste this command in a terminal:

dmesg

Post back the section at the bottom of the output which probably shows information about the error. Also, you can boot the recovery kernel will will scroll text as the machine is booting and then takey ou to an option screen. You may be able to find some clues from that. 

It is always a good idea to paste your exact error message into a search engine before posting here (not that I found much, but it is).

---

