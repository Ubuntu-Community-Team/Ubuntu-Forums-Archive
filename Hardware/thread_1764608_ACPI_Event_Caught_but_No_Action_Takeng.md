---
title: "ACPI Event Caught but No Action Takeng"
date: 2011-05-21
forum: Hardware
---

### Post by bear820301 on 2011-05-21
Hi,  

I am a newbie to Linux and Ubuntu. I just install it on a X41 Tablet. So far I have got the screen rotation and tablet keys working. Now I am working to get the automatic screen rotation working but I did not manage to make it work. Hope  you guys can help me.

I followed the instruction here:
[http://liken.otsoa.net/blog/index.php?entry=entry080617-120522](http://liken.otsoa.net/blog/index.php?entry=entry080617-120522)

As you can see from the above, the auto rotation is achieved by detection of an ACPI event associated with the swivel, and execute appropriate script to rotate the screen. But this approach does not work for me.

I tried the command "acpi_listen" in a terminal while rotating the tablet screen, and I did see the associates event caught by Linux, like this:


mfang@IBM-X41T:~$ acpi_listen
ibm/hotkey HKEY 00000080 00005009
ibm/hotkey HKEY 00000080 0000500a
ibm/hotkey HKEY 00000080 00005009
ibm/hotkey HKEY 00000080 0000500a


It seems that the system did caught the event, but why did it not performing the associated action? I am very confused here.



BTW, I did test the scripts for rotating the screen in a terminal and it does what I want: rotating the screen.

Please help.:popcorn:

---

### Post by Favux on 2011-05-22
Hi bear820301,

Welcome to Ubuntu forums!

What release of Ubuntu are you using?

That's a pretty complicated way to go about automatic rotation.  Plus do you need to turn Compiz on and off in whatever release you are currently using?  And there is some other stuff it is doing you might not necessarily want.

That said the script is about 3 years old and it looks like it would take a while to debug.

Try the automatic rotation script in method 5 at the [Rotation HOW TO]("http://ubuntuforums.org/showthread.php?t=996830").  Or try the Magick Rotation applet linked in method 4.

Hope this helps.

---

### Post by thoand on 2011-06-07
Hi bear820301,

I have exactly the same problem. I have a Thinkpad X41 Tablet with Ubuntu 11.04 running. I created two scripts:
```

thoand@pluto:~$ cat /etc/acpi/actions/x41_portrait.sh 
#!/bin/bash
su $(who | grep ":0" | grep -v "(:0)" | cut -d " " -f1) -c 'xrandr -o right'
su $(who | grep ":0" | grep -v "(:0)" | cut -d " " -f1) -c 'xsetwacom --set "Serial Wacom Tablet stylus" Rotate CCW'

thoand@pluto:~$ cat /etc/acpi/actions/x41_normal.sh 
#!/bin/bash
su $(who | grep ":0" | grep -v "(:0)" | cut -d " " -f1) -c 'xrandr -o normal'
su $(who | grep ":0" | grep -v "(:0)" | cut -d " " -f1) -c 'xsetwacom --set "Serial Wacom Tablet stylus" Rotate NONE'

```These scripts work great, if I execute them (as root) by hand. But they are not executed by the acpid, in which I configured the following:

```

thoand@pluto:~$ cat /etc/acpi/events/thinkpad-x41t 
event=ibm/hotkey HKEY 00000080 00005009
action=/etc/acpi/actions/x41_portrait.sh

event=ibm/hotkey HKEY 00000080 0000500a
action=/etc/acpi/actions/x41_normal.sh

```The scripts are readable and executable:
```

thoand@pluto:~$ ls -lah /etc/acpi/actions/
insgesamt 16K
drwxr-xr-x 2 root root 4,0K 2011-06-07 18:42 .
drwxr-xr-x 4 root root 4,0K 2011-06-07 18:41 ..
-rwxr-xr-x 1 root root  254 2011-06-07 18:42 x41_normal.sh
-rwxr-xr-x 1 root root  254 2011-06-07 18:42 x41_portrait.sh

```@Favux, I read the article you posted, but I do not want to install any additional software, I just want acpid to do, what it should do.

regards,
thoand

PS: acpi_listen shows me, that the events are generated:
```

thoand@pluto:~$ acpi_listen 
ibm/hotkey HKEY 00000080 00005009
ibm/hotkey HKEY 00000080 0000500a

```

---

### Post by thoand on 2011-06-11
Hi,

I added a bit logging information. In x41_portrait.sh
```

echo "drehe $(date) portrait" >> /tmp/dreh.log

```
In x41_normal.sh
```

echo "drehe $(date) normal" >> /tmp/dreh.log

```

Doing so I saw, that only the last defined event gets executed:
```

root@pluto:~# cat /tmp/dreh.log 
drehe Sat Jun 11 17:08:37 CEST 2011 normal
drehe Sat Jun 11 17:09:21 CEST 2011 normal

```

So I splitted the event definitons in two files:
```

root@pluto:~# cat /etc/acpi/events/thinkpad-x41t-portrait 
event=ibm/hotkey HKEY 00000080 00005009
action=/etc/acpi/actions/x41_portrait.sh
root@pluto:~# cat /etc/acpi/events/thinkpad-x41t-normal 
event=ibm/hotkey HKEY 00000080 0000500a
action=/etc/acpi/actions/x41_normal.sh

```

Now I have in /tmp/dreh.log
```

drehe Sa 11. Jun 17:18:41 CEST 2011 portrait
drehe Sa 11. Jun 17:18:47 CEST 2011 normal
drehe Sat Jun 11 17:18:58 CEST 2011 portrait
drehe Sat Jun 11 17:19:00 CEST 2011 normal

```

So both actions get executed now. My screen does not rotate, but I am a step furhter,

regards,
thoand

---

### Post by thoand on 2011-06-11
Hi,

I now have a rotating screen, I am unsure, if the way I check who the current X user is, is optimal. But it seems to work.

My current scripts are:
```

root@pluto:~# cat /etc/acpi/actions/x41_normal.sh
#!/bin/bash
XUSER=$(who | grep "tty7" | cut -d " " -f1)
DISPLAY=":0.0" su $XUSER -c 'xrandr -o normal'
DISPLAY=":0.0" su $XUSER -c 'xsetwacom --set "Serial Wacom Tablet stylus" Rotate NONE'
root@pluto:~# cat /etc/acpi/actions/x41_portrait.sh
#!/bin/bash
XUSER=$(who | grep "tty7" | cut -d " " -f1)
DISPLAY=":0.0" su $XUSER -c 'xrandr -o right'
DISPLAY=":0.0" su $XUSER -c 'xsetwacom --set "Serial Wacom Tablet stylus" Rotate CCW'

```

regards,
thoand

---

