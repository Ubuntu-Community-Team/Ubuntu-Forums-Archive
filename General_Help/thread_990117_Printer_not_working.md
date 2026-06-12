---
title: "Printer not working"
date: 2008-11-22
forum: General Help
---

### Post by Abbadon on 2008-11-22
Hi,

I'm switching from xp to ubuntu, one of my obstacles remains printing.

I'm running Ubuntu 8.04
I have a canon lbp2900 printer


I downloaded the drivers & install instructions from Canon & followed them. Installation seemed to go smoothly without errors.

When I try to print now the job gets stuck in "processing" and stays that way. This happens when I try to print a test page or when I try to print from Openoffice or other programs.


I checked around the forum & other sites but didn't find any straight out answers; and I'm unsure as to how to fix this. Is it a cups problem? is it a driver problem? is it an ubuntu problem? 

any help would be greatly appreciated...

---

### Post by cotcot on 2008-11-22
[[COLOR="Red"]This[/COLOR]]("https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/Canon_LBP_2900#amd64%20Steps:") might help. It is not for 8.04. But maybe the 7.10 instructions are ok.

---

### Post by Abbadon on 2008-11-22
When I try to do

$ sudo /etc/init.d/cupsys stop
(as said in step 3)


I get an error:
sudo: cupsys: command not found



so my cups-is broken?

---

### Post by cotcot on 2008-11-23
Seem to be an error in the instructions. Try
```
cd /etc/init
sudo sh cups stop

```

---

### Post by Abbadon on 2008-11-23
I don't seem to have an /etc/init folder, I do have an /etc/init.d folder. When I try the command there I get:

abbadon@Vorgoth:/etc/init.d$ sudo sh cups stop
sh: Can't open cups

---

### Post by cotcot on 2008-11-23
sorry , init had to be init.d

I am now myself on a 8.04 desktop (my previous post was from an 8.10desktop) and checked this command :
```
cd /etc/init.d
sudo sh cupsys stop
```

---

### Post by Abbadon on 2008-11-25
ok, that works, and I can work trough the rest of the howto now.

the result is the same however: when I try to print something, nothing happens with the printer, although I can see a job being qued in the printer jobs monitor.


I'm completely at a loss as to where to start fixing this... :(

---

