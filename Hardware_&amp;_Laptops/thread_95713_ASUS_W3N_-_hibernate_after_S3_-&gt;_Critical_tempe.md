---
title: "ASUS W3N - hibernate after S3 -&gt; Critical temperature reached (255 C), shutting down."
date: 2005-11-27
forum: Hardware &amp; Laptops
---

### Post by andreas_ on 2005-11-27
Hi,

after installing the new ATI driver (8.19.10) my notebook [ASUS W3451NLP]("http://de.wikibooks.org/wiki/Asus_W3N-Kompendium:_Hardwarebeschreibung") can use the S3 (suspend to ram) mode.
S4 works "out of the box".

But if I use S3 and later S4 (no reboot between) the laptop doesn't woke up.
The Fan starts very loud (cold air). 
And I get the message : 
```
Nov 24 18:50:55 w3n kernel: Critical temperature reached (255 C), shutting down.
Nov 24 18:50:55 w3n kernel: ACPI: Thermal Zone [THRM] (255 C)
Nov 24 18:50:56 w3n shutdown[12621]: shutting down for system halt
```

You can find the full log and the modules before and after S3 on this link -> [W3N-Wiki]("http://de.wikibooks.org/wiki/Diskussion:Asus_W3N-Kompendium:_Ubuntu_Suspend_to_Ram")

I tried a couple of options, but success.

bootoption: acpi_os_name="Microsoft Windows XP"
stopping acpid
unload fan and thermal

---

### Post by andreas_ on 2005-12-04
Hi,

no Idea?

cu
A.

---

### Post by ranf on 2005-12-04
[QUOTE=andreas_]
I tried a couple of options, but success.

bootoption: acpi_os_name="Microsoft Windows XP"
stopping acpid
unload fan and thermal[/QUOTE]
Uh, what is this? A kernel parameter?

I'd try editing /etc/default/acpi-support:
```

# Add modules to this list to have them removed before suspend and reloaded
# on resume. An example would be MODULES="em8300 yenta_socket"
#
# Note that network cards and USB controllers will automatically be unloaded
# unless they're listed in MODULES_WHITELIST
MODULES=""

```

and put `thermal' in between the quotes.

---

### Post by andreas_ on 2005-12-05
[QUOTE=ranf]and put `thermal' in between the quotes.[/QUOTE]

It's not better :(

---

### Post by ranf on 2005-12-05
[QUOTE=andreas_]It's not better :([/QUOTE]
How about 
MODULES="fan thermal"

I don't have your box infront of me. You will have to try some stuff yourself.

---

### Post by andreas_ on 2005-12-05
a week ago I tried all combinations I thought.

It must be something else.

If I only use suspend to disk or only suspend to ram than it's OK. but not mixed ...

---

