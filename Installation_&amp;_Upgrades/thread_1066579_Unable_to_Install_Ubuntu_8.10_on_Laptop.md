---
title: "Unable to Install Ubuntu 8.10 on Laptop"
date: 2009-02-11
forum: Installation &amp; Upgrades
---

### Post by OMMBoy on 2009-02-11
Hello!

I'm trying to install Ubuntu on an older laptop for my son. The laptop is an HP Omnibook XE2 with 600 MHz PIII, 10GB HD, 128MB RAM running XP. I realize that these specs are a bit scarce (especially for XP), but they're still above the bare minimum requirements specified [here]("https://help.ubuntu.com/community/Installation/SystemRequirements").

Here's a quick breakdown of what I did thus far:
[LIST=1]
[*]Downloaded ubuntu-8.10-desktop-i386.iso
[*]Performed MD5 checksum. Passed.
[*]Burned ISO to CD
[*]Stuck CD into laptop and attempted to run Demo
[*]Instructed to reboot to run the LiveCD. Rebooted.
[*]Selected "English" language
[*]Selected "Check CD for Defects". Passed.
[*]Selected "Test Memory". Passed.
[*]Selected "Install Ubuntu"
[/LIST]

After a couple of minutes of doing its thang, the install finally stops and displays a few lines of the following on the "command prompt" screen (I've only posted one line, but the numbers tend to be different for each line):
> [  227.582363] aufs au_xino_write:280:S99acpi-support[5987]: I/O Error, write failed (-5)

The last line reads: ubuntu@ubuntu:~$

Why is this happening, and can Ubuntu be installed on the laptop?

Thank you, in advance, for any help you are able to offer.

Chris (OMMBoy)

---

### Post by utnubuuser on 2009-02-11
Just a stab in the dark here..

Is there an F4  (or similar option) at boot start up?  I was just reading another post the other day where someone was having the same problem and one of the suggestions was to use the F4 option, (I think it was F4), and try installing with acpi-off.

AS I said, this is a stab in the dark, and completely off the top of my head, so don't be quoting me.  lol
Good Luck.

---

### Post by Partyboi2 on 2009-02-11
> **OMMBoy said:**
> Hello!

I'm trying to install Ubuntu on an older laptop for my son. The laptop is an HP Omnibook XE2 with 600 MHz PIII, 10GB HD, 128MB RAM running XP. I realize that these specs are a bit scarce (especially for XP), but they're still above the bare minimum requirements specified [here]("https://help.ubuntu.com/community/Installation/SystemRequirements").

Here's a quick breakdown of what I did thus far:
[LIST=1]
[*]Downloaded ubuntu-8.10-desktop-i386.iso
[*]Performed MD5 checksum. Passed.
[*]Burned ISO to CD
[*]Stuck CD into laptop and attempted to run Demo
[*]Instructed to reboot to run the LiveCD. Rebooted.
[*]Selected "English" language
[*]Selected "Check CD for Defects". Passed.
[*]Selected "Test Memory". Passed.
[*]Selected "Install Ubuntu"
[/LIST]

After a couple of minutes of doing its thang, the install finally stops and displays a few lines of the following on the "command prompt" screen (I've only posted one line, but the numbers tend to be different for each line):


The last line reads: ubuntu@ubuntu:~$

Why is this happening, and can Ubuntu be installed on the laptop?

Thank you, in advance, for any help you are able to offer.

Chris (OMMBoy)
With 128mb ram you would be better off using the alternate cd to install as suggested in the link you provided. In saying this you would get better performance  using a lighter distro like dsl or puppy linux.

---

### Post by snowpine on 2009-02-11
128mb of ram is not enough for Ubuntu. Give Puppy or DSL a try with those specs, you will have much better performance. Good luck!

---

