---
title: "Acpi"
date: 2005-11-28
forum: Hardware &amp; Laptops
---

### Post by markr on 2005-11-28
I have my Dell Inspiron 5150 running Ubuntu 5.10.

At the moment I'm note sure what laptop 'features' are working and what is not.  I have a battery indicator so I assume that's okay. My hibernate doesn't seem to work, but I need to look at it in more detail.

What I'm looking at is getting as much as I can working, including:

1. Fan
2. Battery
3. Suspend/Hibernate
4. Temperature
5. CPU throttling

What I'm not sure about is what is working at the moment.  Does any software exist that will show me if the above stuff is working properly?

Anyone else have a 5150 that can provide advice?

Finally,  I've seem in the forums people talking about various ACPI parameters that can be past to the kernel to help solve varous problems.  Does anyone know of a list (with descriptions) of these commands so I can try some out if I can't get various things working.

I've also been trying to locate a working copy of a DSDT for the 5150 (tried google and acpi.sourceforge) with no success,  any pointers greatfully accepted.

Sorry for all the questions, but I thought I'd get them all out in the open.

Mark.

---

### Post by Raoul Duke on 2005-11-29
[QUOTE=markr]I have my Dell Inspiron 5150 running Ubuntu 5.10.

At the moment I'm note sure what laptop 'features' are working and what is not.  I have a battery indicator so I assume that's okay. My hibernate doesn't seem to work, but I need to look at it in more detail.

What I'm looking at is getting as much as I can working, including:

1. Fan
2. Battery
3. Suspend/Hibernate
4. Temperature
5. CPU throttling

What I'm not sure about is what is working at the moment.  Does any software exist that will show me if the above stuff is working properly?

Anyone else have a 5150 that can provide advice?

Finally,  I've seem in the forums people talking about various ACPI parameters that can be past to the kernel to help solve varous problems.  Does anyone know of a list (with descriptions) of these commands so I can try some out if I can't get various things working.

I've also been trying to locate a working copy of a DSDT for the 5150 (tried google and acpi.sourceforge) with no success,  any pointers greatfully accepted.

Sorry for all the questions, but I thought I'd get them all out in the open.

Mark.[/QUOTE]

I don't know about software, but you can see if the acpi stuff is working in /proc/acpi/*.

One good way to see the acpi/kernel doc is to install the kernel source package and look in the Documntation subdirectory.
 
Hope that helps

---

