---
title: "Thinkpad X31 ACPI Issues"
date: 2005-08-16
forum: Hardware &amp; Laptops
---

### Post by jhscott on 2005-08-16
About at my wits end. I am having  "unable to resume from standby" issues with a twist. This is suspend to RAM that I'm toggling with sudo /etc/acpi/sleep.sh.

I'm using acpid-1.0.4 with kernel 2.6.10-5-686. I have an ATI Mobility M6 videocard, my xorg.conf is using the "ati" driver. This is on a IBM Thinkpad X31.

When I resume, what seems to happen is that my _HARDDRIVE_ gets messed up. Symptoms are the HDD activity light staying steady, system hang at disk access (but not otherwise - eg I can ctrl+alt to a virtual console and log in, but if I run ls, hang). acpid gives me messages (which disturbingly do not persist in /var/log/acpid - another reason I think disk is mssed up) that "Lock file present, not processing event". It also complains about Input/Output errors from the /etc/acpi/resume.sh script.

Google, forum, wiki, IRC search haven't turned up anything. Can anyone assist me? Per the advice of thinkwiki, I have added acpi_sleep=s3_bios to my kernel command line

Thanks,

Jacob

---

### Post by gngulrajani on 2005-09-06
UPDATE ***** i have not had this problem since i upgraded to breezy. ACPI for the X31 works great under breezy *****
 



I have a similar issue with my IBM X31.
 The frozen HD light crash / hang occurs after after i resume from a S3 (suspend to ram) suspend and *only* if am working off the battery.

 The other big difference i have from the parent poster  is my machine slowly hangs. For the first 3 or 4 seconds of this crash pattern my computer gets very slow ( it feels as if it is swapping constantly but i do not hear the HD moving) at this point i usually  notice the HD lamp is frozen on. I can still move the mouse and some application windows but a second or two later the machine is totally frozen and i must hard boot it. 

I do not find anything of interest in the logs ;-[
We i have some more free time i plan on disabling the CPU speed scaling module and trying to turn on ACPI debugging (if that mode exists)

-greg

---

### Post by AgenT on 2005-09-15
[Thinkwiki]("http://www.thinkwiki.org") may have your answer. They even have a section on getting ACPI/APM working with Ubuntu. Although it is a bit outdated - feel free to update it with comments if you get it working. See the section entitled [Installing Ubuntu on a Thinkpad X31]("http://www.thinkwiki.org/wiki/Installing_Ubuntu_on_a_Thinkpad_X31").

---

