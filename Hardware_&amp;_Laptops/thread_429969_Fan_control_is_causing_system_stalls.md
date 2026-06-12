---
title: "Fan control is causing system stalls"
date: 2007-05-01
forum: Hardware &amp; Laptops
---

### Post by glennric on 2007-05-01
Ever since upgrading to Feisty on one of my computers there have been system stalls at regular intervals.  Basically the machine quits responing for a few seconds, continues for a few seconds, and then repeats.  The computer is an EMachines T2240.  It has a 2.2 gig celeron processor with an Intel 82845G/GL integrated video card.  I believe this is an issue with the 2.6.20 kernel.  I had compiled this kernel while it was still running edgy and had the same problem.  I am not sure what needs to be compiled in or left out to stop the problem.  Although I believe it has something to do with the fan control.

The output of "dmesg | tail" after this happens is

[30667.083156] ACPI: Unable to turn cooling device [de478798] 'off'
[30667.088464] ACPI: Transitioning device [FAN1] to D3
[30667.088474] ACPI: Transitioning device [FAN1] to D3
[30667.088477] ACPI: Unable to turn cooling device [de478798] 'off'
[30667.094844] ACPI: Transitioning device [FAN1] to D3
[30667.094854] ACPI: Transitioning device [FAN1] to D3
[30667.094858] ACPI: Unable to turn cooling device [de478798] 'off'
[30667.100432] ACPI: Transitioning device [FAN1] to D3
[30667.100442] ACPI: Transitioning device [FAN1] to D3
[30667.100446] ACPI: Unable to turn cooling device [de478798] 'off'

If I look at the file /var/log/messages the entire file is filled from start to finish with just this and it is more than 700,000 lines long.  

Does anyone have any ideas how to fix this?  Has anyone filed a bug on this?  Anyone know of any workarounds?  I just want to stop the computer from trying to turn the fan off for now.

---

### Post by glennric on 2007-05-02
bump.

Does anyone have any clue how to stop ACPI from attempting to turn off a fan that can not be turned off?

---

### Post by glennric on 2007-05-03
Never mind.  I compiled the 2.6.21 kernel, and this bug has been fixed in that release.

---

### Post by jhf on 2007-06-24
How is your T2240 working for you under Ubuntu?  Is it showing the same problems as [danramos describes at this link?]("http://ubuntuforums.org/showpost.php?p=2418776&postcount=16")

---

