---
title: "ATI 6970m HD x2 on 11.04"
date: 2011-12-05
forum: Hardware
---

### Post by RageLtMan on 2011-12-05
I have a clevo x7200 and have been unable to get both of my ATI 6970m HD MXM3b cards to work properly. I got them last week to use for hash analysis with tools like pyrit and oclhashcat, but am having some serious issues.

Upon installing the 11.11 driver from the generated debs i ran 'sudo aticonfig --adapter=all -f --initial' and rebooted to a frozen system. Some research later i found i have to issue a 'sudo --acpi-services=off' after the first command to get past the hard lock.

X still will not start like this, i have to go into the generated xorg.conf and disable disable the second 'screen' entry or change the 'Device' entry inside the second screen entry to point to the first device ("aticonfig-Device[0]-0"). Now i can get into X.

However, pyrit and hashcat only see one card. When i enable crossfire they both see two cards, but oclhashcat runs slower on crossfire, and pyrit states that there are PMK computation errors.

Every article i read tells me to NOT run in crossfire under linux, but then my second GPU is just an expensive power draining piece of uselessness in my laptop. How do i get around this? Does anyone have 2 6970m's running in ubuntu? i think the issue is that they can't both register as having a display, but need to in order to be seen. In the default configuration my feeling is that the blank screen (not a hard lock) is caused by them fighting over the primary display output and failing miserably.

Suggestions? Thanks in advance

---

### Post by RageLtMan on 2011-12-06
Anyone?

---

