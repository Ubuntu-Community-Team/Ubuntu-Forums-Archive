---
title: "Ubuntu and Slackaware installation in parallel."
date: 2009-09-08
forum: Installation &amp; Upgrades
---

### Post by akshay.sulakhe on 2009-09-08
Hello friends. Wanted to install Slackware and Ubuntu in parallel. Right now i have Ubuntu Ultimate 2.1 and Ubuntu Ultimate 2.2 in parallel. So will be wiping my disk to do other installation(i have a different storage disk). So what shud i do,install Ubuntu first or slackware so i can boot into any via grub. If thats not the option. Does slackware identifies drives via UUID so that i can make changes in GRUB What shud i do. Pleasse help.Thanks

---

### Post by zvacet on 2009-09-08
If you want to keep Ultimate 2.2 on top of Ultimate 2.1 install Slackware.If you want to use Ubunt ugrub just reinstall it.I never used Slack so I don´t know how it works.

---

### Post by andrew.46 on 2009-09-08
Hi akshay,

> **akshay.sulakhe said:**
> Wanted to install Slackware and Ubuntu in parallel.

I note that you have not mentioned the use of a virtual machine which makes life a lot easier and eliminates various concerns with grub / lilo / mbr etc. I attach a screenshot to show my own setup of Slackware 13.0 host and Jaunty Jackalope guest under VirtualBox OSE. If you are interested there is a section of these forums devoted to Virtualization:

Virtualization
[http://ubuntuforums.org/forumdisplay.php?f=308](http://ubuntuforums.org/forumdisplay.php?f=308)

All the best,

Andrew

---

### Post by akshay.sulakhe on 2009-09-09
No virtualisation...Cant i do that directly...

---

### Post by andrew.46 on 2009-09-09
Hi akshay,

> **akshay.sulakhe said:**
> No virtualisation...Cant i do that directly...

You can certainly create a partition and install Slackware directly. There are many ways to do this but I would advise installing Ubuntu first with Grub to the MBR and then install Slackware with Lilo on the root of the slackware partition. Then chainload your Ubuntu grub to the Slackware partition.

I am sure that others will suggest a different scheme though, there are many opinions on this sort of thing :).

Andrew

---

