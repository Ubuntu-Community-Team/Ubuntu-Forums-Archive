---
title: "PCMCIA and ACPI"
date: 2005-04-15
forum: Hardware &amp; Laptops
---

### Post by WillemM on 2005-04-15
Hello,

I just installed ubuntu a few days ago on my Compaq presario 2137EA laptop. All works fine except some small things:

I can't find how to make my PCMCIA network-adapter hot-swappable. I use *modprobe * to enable the module for it and *modprobe -r* to disable it. This works fine, but is rather complex to do. Isn't there another solution for this?

Second my ACPI is acting weird, it works but it works weird. The battery monitor only updates itself when I type *acpi -V* on the console. This shouldn't be neccesary. Anyone knows how to solve this?

A tip for anyone who couldn't get the ACPI to work at all on this laptop, use *acpi=force* in the grub configuration on your kernel boot line.

---

### Post by az on 2005-04-15
Is this relevant?

[https://bugzilla.ubuntu.com/show_bug.cgi?id=8575](https://bugzilla.ubuntu.com/show_bug.cgi?id=8575)

---

### Post by eivind on 2005-04-23
[QUOTE=WillemM]

Second my ACPI is acting weird, it works but it works weird. The battery monitor only updates itself when I type *acpi -V* on the console. This shouldn't be neccesary. Anyone knows how to solve this?[/QUOTE]

This is the case on my HP ze5425ea as well. I actually didn't find out how to make the battery monitor update until I saw your post, but I still have the same problem you have. 

Seems there are (at least) two of us.

I've got one more problem of about the same sort: The cpu frequency monitor shows top frequency until I manually do a /etc/init.d/powernowd restart, even though powernowd is in the startup script directories.

Help is greatly appreciated!

Eivind

---

### Post by benrose on 2005-04-26
I have the same problem with my battery meter only updating when I run acpi -V or just very slowly if I don't run acpi -V.

So I just created a perl script to run it every 15 seconds in the background.

> 
#!/usr/bin/perl

while(1)
{
         @acpiout = `acpi -V`;
         @acpiout1 = `acpi -V`;
         #print @acpiout2;
         sleep(15);
}


I ran acpi -V twice because I noticed sometimes I had to run it twice for it to update more frequently. I just told GNOME to start this whenever it starts up and its been working like a charm!

---

