---
title: "UEFI Boot compatible USB Drive"
date: 2015-04-09
forum: Hardware
---

### Post by Mike_Hughes on 2015-04-09
I am trying to create a USB Boot disk that will boot on a HP-15 that has UEFI Booting. Any ideas on this one? I know you use the DD command but new at this so need help. I am wanting to take HD Clone and put it on a bootable USB Drive.

---

### Post by oldfred on 2015-04-09
What do you mean by hd clone?
And dd is only for same size to same size drives. It also has the nickname Data Destroyer so should not be used unless you really know what you are doing.

 Powerful command, but often misused and then nicknamed "dd" Data Destroyer
[http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/](http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/)

Also UEFI boot uses gpt partitions which also have GUIDs. The GUIDs in partition tables must match partitions, so you cannot use dd to copy gpt partitions. If copying an entire drive it may work.

---

