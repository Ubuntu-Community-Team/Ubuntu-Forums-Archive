---
title: "Installed Cairo-Dock, Broke Print Utilities, others."
date: 2008-11-30
forum: General Help
---

### Post by myislanduniverse on 2008-11-30
This is my first post, and still a considerable neophyte, so please pardon me if I overlook any info that might be needed to give you granularity of the issue.

I decided to try my hand with the Cairo-dock today, and was very pleased with the whole thing, until an update required a restart.  Upon restart, I noticed that several of my start-up programs didn't launch (CheckGmail, HP System Tray, Print Queue Applet, and possibly others I just haven't noticed yet).  These items won't launch with their icons, now, either.

I uninstalled Cairo (apt-get remove cairo-dock) and its plug-ins, but whatever effect the installation had on these utilities/applications wasn't so easily reversed.  I also tried re-installing hplip et al.

I'm running 8.10 with both GNOME and KDE.

Thanks in advance to any insight anybody can give me!

---

### Post by myislanduniverse on 2008-11-30
Trying to execute the commands from the terminal, I get:

Print Queue Applet:

**nate@hasubi:~$ system-config-printer-applet**
Traceback (most recent call last):
  File "/usr/share/system-config-printer/applet.py", line 20, in <module>
    import cups
*ImportError: No module named cups*

HP System Tray Service:

**nate@hasubi:~$ hp-systray --qt4**
Traceback (most recent call last):
  File "/usr/bin/hp-systray", line 35, in <module>
    from prnt import cups                         
  File "/usr/share/hplip/prnt/cups.py", line 25, in <module>
    import gzip                                             
  File "/usr/local/lib/python2.6/gzip.py", line 9, in <module>
    import zlib                                               
*ImportError: No module named zlib*

CheckGmail:

**nate@hasubi:~$ checkgmail**
Warning: Gtk2::Sexy not found ...

CheckGmail uses Gtk2::Sexy for clickable URLs in mail messages
Please download and install from CPAN ([http://search.cpan.org](http://search.cpan.org)) if you want to use this feature ...


not well-formed (invalid token) at line 17, column 15, byte 530 at /usr/lib/perl5/XML/Parser.pm line 187
Perl exited with active threads:
        1 running and unjoined
        0 finished and unjoined
        0 running and detached

---

