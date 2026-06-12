---
title: "HELP!! Completely inactive system upon startup! Happens randomly, whats going on!?"
date: 2008-08-18
forum: General Help
---

### Post by UbubtuGuru on 2008-08-18
I have been using Ubuntu Hardy Heron 8.04 for about 5 months now. About 2 months ago, my system began to randomly glitch out and not load*** anything*** upon booting from being shutdown, except for the desktop picture. No icons, screenlets, menus, cursor preferences, nothing. I noticed that when the computer decided to not boot properly, there would be no startup music (the ubuntu drums) so I would go ahead and shut down, restarting as many times necessary, until it decided to load properly. There must be a reason for this, right? Any suggestions would be appreciated greatly. I looked on the forums but couldn't find any info about a situation like this one. Thanks for your help.

---

### Post by Naatan on 2008-08-18
Try checking the system log at /etc/log/syslog when this problem occurs again, feel free to post the contents here.. look for errors that might be related.

As an alternative to restarting your computer you can try just restarting X by pressing ctrl+alt+backspace ([COLOR=Red]**ONLY use this with an unresponsive system, doing this right now will restart your X window system and you will loose all your data**[/COLOR])

---

### Post by UbubtuGuru on 2008-08-18
> **Naatan said:**
> Try checking the system log at /etc/log/syslog when this problem occurs again[/B][/COLOR])


Here's the contents of /syslog:

.\" syslog.txt -  -*- Indented-Text -*-
$RoughId: syslog.txt,v 1.18 2002/02/25 08:20:14 knu Exp $
$Id: syslog.txt 11708 2007-02-12 23:01:19Z shyouhei $

UNIX Syslog extension for Ruby
Amos Gouaux, University of Texas at Dallas
<amos+ruby@utdallas.edu>
&
Akinori MUSHA
<knu@ruby-lang.org>

** Syslog(Module)

Included Modules: Syslog::Constants

require 'syslog'

A Simple wrapper for the UNIX syslog system calls that might be handy
if you're writing a server in Ruby.  For the details of the syslog(8)
architecture and constants, see the syslog(3) manual page of your
platform.

Module Methods:

   open(ident = $0, logopt = Syslog::LOG_PID | Syslog::LOG_CONS,
		facility = Syslog::LOG_USER) [{ |syslog| ... }]

	Opens syslog with the given options and returns the module
	itself.  If a block is given, calls it with an argument of
	itself.  If syslog is already opened, raises RuntimeError.

	Example:
	  Syslog.open('ftpd', Syslog::LOG_PID | Syslog::LOG_NDELAY,
			      Syslog::LOG_FTP)

   open!(ident = $0, logopt = Syslog::LOG_PID | Syslog::LOG_CONS,
		facility = Syslog::LOG_USER)
   reopen(ident = $0, logopt = Syslog::LOG_PID | Syslog::LOG_CONS,
		facility = Syslog::LOG_USER)

	Same as open, but does a close first.

   opened?

	Returns true if syslog opened, otherwise false.

   ident
   options
   facility

	Returns the parameters given in the last open, respectively.
	Every call of Syslog::open resets these values.

   log(pri, message, ...)

	Writes message to syslog.

	Example:
	  Syslog.log(Syslog::LOG_CRIT, "the sky is falling in %d seconds!", 10)

   crit(message, ...)
   emerg(message, ...)
   alert(message, ...)
   err(message, ...)
   warning(message, ...)
   notice(message, ...)
   info(message, ...)
   debug(message, ...)

	These are shortcut methods of Syslog::log().  The lineup may
	vary depending on what priorities are defined on your system.

	Example:
	  Syslog.crit("the sky is falling in %d seconds!", 5)
 
   mask
   mask=(mask)

	Returns or sets the log priority mask.  The value of the mask
	is persistent and will not be reset by Syslog::open or
	Syslog::close.

	Example:
	  Syslog.mask = Syslog::LOG_UPTO(Syslog::LOG_ERR)

   close 

	Closes syslog.

   inspect

	Returns the "inspect" string of the Syslog module.

   instance

	Returns the module itself. (Just for backward compatibility)

   LOG_MASK(pri)

	Creates a mask for one priority.

   LOG_UPTO(pri)

	Creates a mask for all priorities up to pri.

** Syslog::Constants(Module)

require 'syslog'
include Syslog::Constants

This module includes the LOG_* constants available on the system.

Module Methods:

   LOG_MASK(pri)

	Creates a mask for one priority.

   LOG_UPTO(pri)

	Creates a mask for all priorities up to pri.



I'm not experienced enough to really know what all this means. Anyone see any problems with it?

Thanks!

---

### Post by indiv on 2008-08-18
I'm not the original poster, but I've seen this happen twice since I installed last week.  After looking through my syslog, I suspect a gnome desktop manager crash caused the desktop not to appear.

The logs are /var/log/syslog*.  I collected them all into 1 file for easy searching with this command:
**cat /var/log/syslo*[!z] > allsyslog & zcat /var/log/syslog*.gz >> allsyslog**

Then I browsed the file and searched for keywords like "error" and "segfault" (well, *grep error allsyslog* in reality).  I saw **gdm[xxxx]: segfault at 6e61745f eip b76e4e66 esp bfe03f28 error 4**.  Google searching that turned up an open bug report, but it didn't provide any insight as to the cause.

---

### Post by UbubtuGuru on 2008-08-19
There were a few instances in syslog where "error" was present in the search. All of them read: 
"Aug 18 13:39:08 christian-laptop kernel: [ 8211.295032] APIC error on CPU1: 40(40)
Aug 18 13:39:08 christian-laptop kernel: [ 8211.311931] APIC error on CPU0: 40(40)"

Any ideas?

---

### Post by FluffyElmo on 2008-08-19
For the APIC errors you can try booting with APIC disabled. From a terminal window:

```
sudo nano /boot/grub/menu.lst
```

Find this line and add *noapic* to the end.
```
# defoptions= quiet splash
```

It should look like this:
```
# defoptions= quiet splash noapic
```

Save the file (Ctrl-O) and exit nano (Ctrl-X). Then update grub and reboot.
```
sudo update-grub
sudo shutdown -r now
```

Hopefully when the system reboots you won't have any more problems, though it may just help narrow things down. Good Luck!

---

### Post by UbubtuGuru on 2008-08-19
I entered "sudo nano /boot/grub/menu.lst" into the terminal and it returned a blank screen with commands at the bottom, such as ^X (exit) and ^N (new page). I tried entering the commands but it was unresponsive. How do I find the line you said I needed?

Thanks

---

### Post by Naatan on 2008-08-19
Don't use nano, it screws up your character encoding.. if you want to use a terminal based file editor try getting into vim.

In this case you can simply use gedit (as long as you are in gnome)

$ sudo gedit /boot/grub/menu.lst

Or use vim if you are working from the console

$ sudo vim /boot/grub/menu.lst

In vim you have to press "I" to enter editing mode, when you are done press ESC and write **:wq** (write & quit) to save the file.

---

