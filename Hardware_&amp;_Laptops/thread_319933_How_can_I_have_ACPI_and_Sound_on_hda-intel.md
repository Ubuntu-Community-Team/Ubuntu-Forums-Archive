---
title: "How can I have ACPI and Sound on hda-intel?"
date: 2006-12-16
forum: Hardware &amp; Laptops
---

### Post by Avian00 on 2006-12-16
Hello,

I've been troubleshooting a problem with my new laptop.  It is a Toshiba Satellite P105-S9722, and it seems that in order for me to experience sound, I must disable ACPI.  I've read and posted on several threads regarding this issue.  It appears to be a common issue with the hda-intel 82801G (ICH7 Family) High Definition Audio Controller family.  My particular model appears to be Conexant.  Here are some additional threads on this topic:

[http://ubuntuforums.org/showthread.php?t=316573](http://ubuntuforums.org/showthread.php?t=316573)
[http://ubuntuforums.org/showthread.php?t=251877](http://ubuntuforums.org/showthread.php?t=251877)
[http://ubuntuforums.org/showthread.php?t=251877](http://ubuntuforums.org/showthread.php?t=251877)

To summarize them all, the current solution appears to be disabling ACPI.  Once ACPI is disable, the sound magically starts working.  It definitely fixes the problem for me.  But at the expense of all the features which matter on a laptop.  Has ANYONE out there figured out a way to have ACPI *AND* Sound on the hda-intel Audio Controller?  I would be the happiest owner of my new Toshiba laptop if somebody could help me with this problem.  Thanks in advance!

Matt

---

### Post by LuisC-SM on 2006-12-17
> **Avian00 said:**
> Hello,

I've been troubleshooting a problem with my new laptop.  It is a Toshiba Satellite P105-S9722, and it seems that in order for me to experience sound, I must disable ACPI.  I've read and posted on several threads regarding this issue.  It appears to be a common issue with the hda-intel 82801G (ICH7 Family) High Definition Audio Controller family.  My particular model appears to be Conexant.  Here are some additional threads on this topic:

[http://ubuntuforums.org/showthread.php?t=316573](http://ubuntuforums.org/showthread.php?t=316573)
[http://ubuntuforums.org/showthread.php?t=251877](http://ubuntuforums.org/showthread.php?t=251877)
[http://ubuntuforums.org/showthread.php?t=251877](http://ubuntuforums.org/showthread.php?t=251877)

To summarize them all, the current solution appears to be disabling ACPI.  Once ACPI is disable, the sound magically starts working.  It definitely fixes the problem for me.  But at the expense of all the features which matter on a laptop.  Has ANYONE out there figured out a way to have ACPI *AND* Sound on the hda-intel Audio Controller?  I would be the happiest owner of my new Toshiba laptop if somebody could help me with this problem.  Thanks in advance!

Matt

Hi there.

First let me tell u that u r not the only one with this problem.

I have similar HW specs as u do and I have spent around 90 Hours trying to get ACPI and the sound server working together but with no avail. In this box I have WinXP, SLED 10 and Ubuntu Edgy. 

Yesterday night I hosed the sound server trying to update the alsa driver in SLED 10. So I decided to start housing ubuntu this time (anyhow if I don't get'em to work together, I'll just go back to XP :( )

FYI we are using the alsa driver version 1.0.12 rc1 in Ubuntu and the latest stable is 1.0.13 which has a lot of fixes.

I've read i very many posts that the only way to fix this was by compiling the driver as shown [here]("http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Intel&card=ICH+southbridge+HD-audio+and+modem.&chip=ICH6%2C+ICH6M%2C+ICH7%2C+ESB2&module=hda-intel").
Im not a newbie in Linux but I cannot say I'm an expert (except when I have a very precise howto I can show off :D). However, I'm all the time affraid of breaking the system that's why I do not mess around too much with a stable box.

After I finish this howto, I'll post back and will show my comments. (whish me luck :D)

Regards.

Luis C. Suárez

---

### Post by LuisC-SM on 2006-12-20
Sorry not to post on time. But I really had NOTHING  to post :( except for the fact that I got much better sound using mercurial alsa repos with the latest alsa libraries and utilities (1.0.14rc1) but obviously with ACPI OFF.

Anyhow This is beeing my own hell. with SLED and Ubuntu.

I'll drop both of them at the momment and will use just  Windowze until there is some solution for this.

By the way, I read that using "***pci=routeirq***" at kernel boot time could, in certain way, fix some of these issues by allocating the irqs but I'm not too wise for this. (this is just to mention some idea)

Sorry not to be of any help, but my linux skills are very very basic even when I have 2 years using several distros.

Regards.

Luis

---

### Post by shpang on 2007-10-09
Same things here on my p105-s9722, IRQ mess, 1st, at boot time PCI cries that there is a problem with a resource, then, in order to have sound, I disabled ACPI /acpi=off/ and the X11 cried that Nvidia could not get its irq or something like that, and if I disable the 3d /that restricted nvidia driver/ the gdm starts in "ugly mode" and there is sound....
 laptop proprietary drivers suck so BIG :(

---

### Post by LuisC-SM on 2007-10-09
> **shpang said:**
> Same things here on my p105-s9722, IRQ mess, 1st, at boot time PCI cries that there is a problem with a resource, then, in order to have sound, I disabled ACPI /acpi=off/ and the X11 cried that Nvidia could not get its irq or something like that, and if I disable the 3d /that restricted nvidia driver/ the gdm starts in "ugly mode" and there is sound....
 laptop proprietary drivers suck so BIG :(

Shpang.
This thread is very old, there are newer threds regarding the same problem with gutsy and feisty, I think this thread was for dapper or edgy.
Please, be so kind to post in a relevant thread concerning your platform. 
In case Dapper ior edgy is your platform, then I should be ](*,)
Cheers
Luis

---

