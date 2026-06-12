---
title: "trying to install ubuntu 8.1 on Everex StepNote SA2052T"
date: 2009-01-07
forum: Hardware
---

### Post by ubum on 2009-01-07
I am trying to install ubuntu 8.1 on Everex StepNote SA2052T and intall is stuck.

I have tried the following instructions mentioned by this blog:
> 
[http://www.poplarware.com/everexlinux.html]("http://www.poplarware.com/everexlinux.html")

Press F6 and add "sdhci.blacklist=yes" to the prompt (without quotes). If you are using Ubuntu 8.10 or later, you will also need to add "sdhci_pci.blacklist=yes" (without the quotes) -- the SDHCI driver was split into two kernel modules in this version of Ubuntu.

Press f6

Then I do this

file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity initrd=/casper/initrd.gz quiet splash sdhci.blacklist=yes sdhci_pci.blacklist=yes

What I get is the following:

Unknown boot option. Ignoring sdhci.blacklist=yes sdhci_pci.blacklist=yes

I also tried without removing "--" as follows:

file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity initrd=/casper/initrd.gz quiet splash -- sdhci.blacklist=yes sdhci_pci.blacklist=yes
 
I still get unknown boot option.
Can someone help get this to work

---

### Post by wykedengel on 2009-01-10
From what I read in the link you posted. You need to use the Alternate install cd.

---

### Post by wykedengel on 2009-01-10
Scratch that...it didn't work.

---

