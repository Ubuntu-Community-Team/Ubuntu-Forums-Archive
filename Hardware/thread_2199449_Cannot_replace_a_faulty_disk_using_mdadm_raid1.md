---
title: "Cannot replace a faulty disk using mdadm raid1"
date: 2014-01-14
forum: Hardware
---

### Post by etiennenoel on 2014-01-14
[COLOR=#333333][FONT=UbuntuRegular]I have a Software Raid 1 array that I build a couple years ago. One day, after I loss current, the array became corrupted. One the drive was corrupted so, I removed it from the array and rezeroed it.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Now, I want to re-add it to the array. When I'm doing the following command :[/FONT][/COLOR]
[INDENT]mdadm --add /dev/md0 /dev/sdb1
[/INDENT][COLOR=#333333][FONT=UbuntuRegular]The command is executed and I can see if I run --detail that the drive is rebuilding but this stays for a couple of seconds and then I get the following :

[IMG]http://i.stack.imgur.com/oZtxR.png[/IMG]
I really don't know how to resolve this issue

[/FONT][/COLOR]

---

### Post by SaturnusDJ on 2014-01-14
When something goes corrupt...there is a reason most times...

Start by looking up the S.M.A.R.T. statuses for the disks.

---

### Post by etiennenoel on 2014-01-14
I decided to reinstall this disk since nothing came up in the S.M.A.R.T. analysis...

---

