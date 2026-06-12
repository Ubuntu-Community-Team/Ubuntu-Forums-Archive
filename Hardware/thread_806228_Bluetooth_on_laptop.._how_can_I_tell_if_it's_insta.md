---
title: "Bluetooth on laptop.. how can I tell if it's installed?"
date: 2008-05-24
forum: Hardware
---

### Post by Spoonboy on 2008-05-24
That worked great!! (the script below)

Thanks so much, this community is invaluable.

---

### Post by sdennie on 2008-05-24
You should be able to see if it's enabled by going to System->Preferences->Bluetooth->General and select Only when adapter is present.  If you don't see a little bluetooth icon show up in the panel, it's probably not working.  One thing to check would be if your laptop has a bluetooth switch.  I frequently forget to turn mine on and then wonder why it isn't working.

---

### Post by Spoonboy on 2008-05-24
Hi there, thanks. 

It doesn't appear. Apparently toshiba BT seems like a pain to get working :/

---

### Post by hotweiss on 2008-05-24
> **Spoonboy said:**
> Hi there, thanks. 

It doesn't appear. Apparently toshiba BT seems like a pain to get working :/

Try my solution that I used for my Toshiba R200:

[B][U]
Bluetooth & Brightness Control[/U][/B]

Thanks to Tim Anderson's blog I was able to get my Bluetooth and brightness controls working:

[http://www.itwriting.com/blog/?p=333#comment-35858](http://www.itwriting.com/blog/?p=333#comment-35858)

You see, the driver that enables your Bluetooth also enables your brightness control. This is done by creating a script file that turns it on  at start-up.


**Step 1:** Change to the directory where we are going to have the script file.

> 
cd /etc/init.d

**Step 2:** Creat the script file.

> sudo nano tosh-bluetooth

**Step 3:** Paste this script.

> 
#! /bin/bash

# script to start/stop Toshiba Bluetooth adapter
# requires toshset

case "$1" in
 start)
 /usr/bin/toshset -bluetooth on
 ;;
 stop)
 /usr/bin/toshset -bluetooth off
 ;;
 *)
 echo "Usage: /etc/init.d/tosh-bluetooth {start|stop}" >&2
 exit 1
 ;;

esac

exit 0



Make sure that there is an empty line after exit 0.

**Step 4:** Save and exit Nano.

Type Ctrl-O to exit and Ctrl-X to exit.

**Step 5:** Make the script executable.

> 
sudo chmod 755 tosh-bluetooth

**Step 6:** Add it to the startup scripts.

> sudo update-rc.d tosh-bluetooth defaults

**Step 7:** Reboot.

Your Bluetooth should now be working as expected.

---

### Post by Spoonboy on 2008-05-24
sorted.

---

### Post by hotweiss on 2008-05-24
PLZ mark the thread as solved using the thread tools menu at the top.

---

