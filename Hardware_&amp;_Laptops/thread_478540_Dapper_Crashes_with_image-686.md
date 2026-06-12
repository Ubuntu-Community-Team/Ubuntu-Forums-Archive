---
title: "Dapper Crashes with image-686"
date: 2007-06-19
forum: Hardware &amp; Laptops
---

### Post by thavid on 2007-06-19
Hi there!
I've been having a problem with dapper that I don't know how to solve, and since things are starting to get messy here at work because of it, I decided to ask the experts of the community for help... So here it goes:

We are managing about 300 restaurants and we are using Dapper Drake on the BackOffice Computer (to access e-mail, office stuff, etc etc, nothing very specific). In the past, these machines had Windows 2000 installed. We starded the migration, everything was going fine, we had already migrated some 80 machines to Dapper, until we started to migrate computers with these specs* that were at some stores,

With kernel 686, machine freezes all the time (for exemple, when I try to open Network applet in the System -> Administration menu). Then, I changed to 386 (althrough 686 would be the correct one for this cpu, but whatever) and what happens now it freezes while using firefox (navigation on a lan portal, no Java, no Flash, no Shockwave, just plain old HTML with some JavaScript!), and still, it gets a little unstable!

* The specs:
Intel Pentium4 3000mhz
512 MB Ram
MotherBoard GigaByte GA8S648FX-775


PS: This machine was running fine with Windows, but I know that something doesn't fit well, and since we aren't the hardware dealer, we've got to have arguments to fight back!

PS2: This also happens in some ASRock motherboards, with Pentium 4 CPU's (/proc/cpuinfo says 3015mhz or 2800mhz - Still lwith label Intel Pentium 4 3000mhz)

PS3: There is nothing wrong with the Intranet portal. It runs fine on every other machine, with every other operating system, in every browser, on every point of our network.

---

### Post by thavid on 2007-12-28
Got it solved... Some weird problem with this ASRock Boards + P4 3GH CPU, only works fine when I add "noapic acpi=off" in the kernel initialization string

---

