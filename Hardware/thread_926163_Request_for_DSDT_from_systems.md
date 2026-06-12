---
title: "Request for DSDT from systems"
date: 2008-09-21
forum: Hardware
---

### Post by postfail on 2008-09-21
Hi all -- I was attempting to find a DSDT archive with sample DSDT
from a variety of systems.
The closest thing I have found was the archive that was at
[http://acpi.sourceforge.net](http://acpi.sourceforge.net) ; if anyone
knows of another DSDT archive please let me know.

Since a current one doesn't seem to exist, I am attempting to put
my own database together up on the
internets at [http://www.fileandstream.com/proc/acpi/dsdt.htm](http://www.fileandstream.com/proc/acpi/dsdt.htm) .

I am looking for folks to send me the DSDT from their systems.  Gathering your system DSDT takes less than about 2 minutes by running the following (or longer if you want to try the 'expert' instructions at [http://www.fileandstream.com/proc/acpi/iasl.htm:](http://www.fileandstream.com/proc/acpi/iasl.htm:)

Windows:
1. extract acpica tools from acpica.org; latest as of this writing
is [http://acpica.org/download/iasl-win-20080829.zip](http://acpica.org/download/iasl-win-20080829.zip)
2. run 'iasl -g' to extract all acpi tables.
3. send all '.dsl' and '.dat' files extracted

Linux:
1. file is at /proc/acpi/dsdt
2. may need to, as sudo or root, cp and then 'chown' the file to a
non-root id to email.

If anyone is interested, please send the files (or url link),
hardware make/model, and your name/email (if you want credited), to
[email]postfail@hushmail.com[/email],

Thanks in advance...

---------------------------------------
Scott Thompson / [email]postfail@hushmail.com[/email]
---------------------------------------

---

### Post by lisati on 2008-09-21
Don't panic! your question has been noticed! (I'm sorry I can't help any further at the present)

---

