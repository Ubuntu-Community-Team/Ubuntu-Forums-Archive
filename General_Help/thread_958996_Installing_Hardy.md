---
title: "Installing Hardy"
date: 2008-10-26
forum: General Help
---

### Post by Rickyk on 2008-10-26
I am trying to install Ubuntu 8.04 on a old computer and when i boot up with the Ubuntu cd i the thing comes up where i select language and the options to install and try ubuntu come up and i select install and it starts to boot up and then says "ACPI: BIOs age (1999)fails cutoff (2000) ACPI: force is required to enable ACPI" 

Anything i can do to fix this? 
I think im running windows 2000 on it atm.(old peice of junk =])
:confused::confused:

---

### Post by drs305 on 2008-10-26
There used to be an option to enter F6 during the install to change certain settings. You might try that, navigate or toggle to the acpi=xxxxxx setting (whatever it is set to) and change it to acpi=force (using the same case as the default entry).

---

### Post by Rickyk on 2008-10-26
> **drs305 said:**
> There used to be an option to enter F6 during the install to change certain settings. You might try that, navigate or toggle to the acpi=xxxxxx setting (whatever it is set to) and change it to acpi=force (using the same case as the default entry).


I don't even get to the install it tells me that error then loads up and i see the desktop and nothing els just the picture and my mouse is a black x?

---

### Post by drs305 on 2008-10-26
> **Rickyk said:**
> I don't even get to the install it tells me that error then loads up and i see the desktop and nothing els just the picture and my mouse is a black x?

when i boot up with the Ubuntu cd i the thing comes up where i select language and the options to install and try ubuntu come up and i select install and it starts to boot up and then says "ACPI: BIOs age (1999)fails cutoff (2000) ACPI: force is required to enable ACPI"


At the point you get to the second paragraph above is where I thought F6 may come into play.

---

### Post by Rickyk on 2008-10-26
So during the error or the "menu"?? 
Ill try Both.

---

### Post by Rickyk on 2008-10-26
When the comp boots up and the menu comes up there is a F6 and the options in it are:
acpi=off
noacpi
nolacpi
edd=on
free software only


And when you press enter on any of them its puts an x next to it, I dont see where i could changes its "value"?

---

### Post by Rickyk on 2008-10-26
Bump

Still need help

---

### Post by drs305 on 2008-10-26
Here is a quote from someone who had the same problem and did what I suggested you try. The link is [http://linux.derkeiler.com/Mailing-Lists/Ubuntu/2008-09/msg01887.html]("http://http://linux.derkeiler.com/Mailing-Lists/Ubuntu/2008-09/msg01887.html")

I have highlighted what he did. Note that *if* you get it installed you would place the "acpi=force" line into the grub boot instructions to make it permanent.

```
    I have a old Compaq Presario 4160 that I was going to try to put xubuntu on it I am getting the message:

    [0.000000] ACPI: no DMI bios year acpi = force is required to enable the acpi.

    When I am starting the xubuntu install I see that f6 allows for options and it's see to acpi=off but I press the enter key and a little "x" appears next to the acpi=off line. I don't see how to change the option to force. I guess this is what is called a boot option? Anyway, any ideas on what I should do to attempt to install xubuntu on this machine.

    Thanks

I have a couple of older systems that say that. I run the installations
without changes, then add acpi=force to the GRUB menu boot line where
it has "quiet splash".

[B]To add it during the installation, hit F6, use arrows to get to
acpi=off, backspace or delete *off*, type using insert mode *force*.[/B]

*One system failed install though, when I didn't keep acpi=off*
```

If you still have questions and want to find information about the F6 acpi=force option, do a Google search for: F6 acpi=off acpi=force install

---

### Post by ukera on 2008-10-26
hmm, select "boot with no changes done", then open up GParted, make a partition, then use the GUI installed.  since installing in command line is so damn hard now and days -_-

---

