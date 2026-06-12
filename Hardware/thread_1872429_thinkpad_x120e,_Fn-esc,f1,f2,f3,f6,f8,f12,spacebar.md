---
title: "thinkpad x120e, Fn-esc,f1,f2,f3,f6,f8,f12,spacebar"
date: 2011-10-30
forum: Hardware
---

### Post by linuxcss on 2011-10-30
anybody got solution to getting any of the following Fn keys working on 11.10 xubuntu on
the thinkpad x120e: Fn ... esc,f1,f2,f3,f6,f8,,spacebar

and Fn-F12 I see it invokes hibernate but It never completes have to power cycle the machine
Fn-Esc flashes mute and unmute meter but does not mute or unmute

thanks

---

### Post by linuxcss on 2012-02-16
anybody got fn-f12 for hibernation working ?

i'm currently running xubuntu 11.10 with updates as of feb 14,2012

---

### Post by Toz on 2012-02-16
> **linuxcss said:**
> anybody got fn-f12 for hibernation working ?

i'm currently running xubuntu 11.10 with updates as of feb 14,2012

See here: [http://ubuntuforums.org/showpost.php?p=10584171&postcount=124]("http://ubuntuforums.org/showpost.php?p=10584171&postcount=124")

---

### Post by linuxcss on 2012-02-17
Jimmy  

seems like it should be in the kernel by now right?
I'm running 3.0.0.16  (fetched on feb 14,2012)

if this is true, with regards to the config.d/file (see below)
what does file have to called (or doesn't it matter) and does the
contents only need 
HIBERNATE_MODE="shutdown"[FONT=monospace]in it?

=========================
[/FONT]The hibernate issue is being addressed.  Seems there's a kernel update  coming, plus it needs a file added to /etc/pm/config.d with the  contents:

 	Code:
 	HIBERNATE_MODE="shutdown"

---

### Post by Toz on 2012-02-17
> **linuxcss said:**
> Jimmy  

seems like it should be in the kernel by now right?
I'm running 3.0.0.16  (fetched on feb 14,2012)

if this is true, with regards to the config.d/file (see below)
what does file have to called (or doesn't it matter) and does the
contents only need 
HIBERNATE_MODE="shutdown"[FONT=monospace]in it?[/font]
I don't believe the file needs to be called by any particular name, as they are all read. Try calling the file **defaults**

---

