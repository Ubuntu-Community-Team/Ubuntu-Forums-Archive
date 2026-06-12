---
title: "disable suspend"
date: 2006-06-17
forum: Hardware &amp; Laptops
---

### Post by lex1 on 2006-06-17
havea labtop with fluxbox when computer goes into suspend after about 30 to 45 minutes of inactivity this kills ssh and i cannot connect from remote host.

I have seen this in the wiki(see below) but how to disable suspend?

lex1

ACPI

To suspend to disk, choose "Hibernate" from the GNOME logout menu. To suspend to RAM, edit

/etc/default/acpi-support

and uncomment the second line by deleting the # character, to read:

ACPI_SLEEP=true

Ubuntu 6.06

Dapper needs another step to enable suspend. Execute gconf-editor, and visit apps/gnome-powermanager and enable "can_suspend". You can enable/disable suspend and/or hibernation from there.

---

### Post by 5-HT on 2006-06-17
Not sure, but what about just following the reverse of that information?

i.e., in  /etc/default/acpi-support you'd want to have your commenting like so:

```
# Uncomment the next line to enable ACPI suspend to RAM
#ACPI_SLEEP=true

# Comment the next line to disable suspend to disk
#ACPI_HIBERNATE=true 
``` 

[quote=lex1]Dapper needs another step to enable suspend. Execute gconf-editor, and visit apps/gnome-powermanager and enable "can_suspend". You can enable/disable suspend and/or hibernation from there.[/quote] 
You may also need to disable the appropriate options in gconf-editor as mentioned in the quote above.

Hope that helps.

---

### Post by lex1 on 2006-06-18
there is no
i.e., in /etc/default/acpi-support on my system

what is apcid?

lex1

---

