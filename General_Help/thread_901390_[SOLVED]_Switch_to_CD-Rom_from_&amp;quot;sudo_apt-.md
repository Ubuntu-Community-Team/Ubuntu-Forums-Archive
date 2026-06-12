---
title: "[SOLVED] Switch to CD-Rom from &amp;quot;sudo apt-get install&amp;quot; problem"
date: 2008-08-26
forum: General Help
---

### Post by BMWDriver on 2008-08-26
Every time I've run a line with the command "sudo apt-get install" after the "sudo apt-get update" with the terminal in admin mode, I get a few of the files coming down the internet, and then it asks for the Ubuntu CD-Rom (Hardy Heron). As I do insert the CD as requested, I get no response pressing enter as required, just a repeat of the line that says "please insert the CD [...] and press enter".

I have two hard drives and a zip drive installed. The CD-Rom works fine otherwise. I imagine Ubuntu is more used to a single hard drive with only one CD-Rom.

From what I know of Ubunutu and GNU Linux, it must be a "mount" thing.

Any suggestions ? Thanks.

---

### Post by sisco311 on 2008-08-26
If you have a working internet connection, then you  don't need the cdrom repository.
Disable it:
> **Disable the CD-ROM Repository**

 If you have installed Ubuntu from one of Ubuntu's CD-ROMs, the CD will be included in the list of repositories used by the package management tools. When you install a new package, **Synaptic** will check whether the package is available locally (i.e. on the CD-ROM). **Synaptic** may then ask for the CD-ROM. This can help reduce the size of downloads and speed up the installation process. If you would like **Synaptic** to rely solely on the internet repositories for package management, you can disable the CD-ROM entry with a few steps: 

[LIST]
[*]Launch Synaptic and navigate to "Settings" > "Repositories". 
 A list of software repositories or "Channels" will be shown.
[*]Locate the entry for the CD-ROM (it may say something like **CD disk with Ubuntu 6.06 LTS**). Click on the checkbox next to it to disable the CD-ROM as a software source.
[*]Click the **Close** button to save the changes you have made.
[*]You can re-enable the CD-ROM at any time using the checkbox next to its entry.
[/LIST]

From:[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by Inane_Asylum on 2008-08-26
Do you have the CD-ROM activated in your sources.list file?

---

### Post by eggdeng on 2008-08-26
Go to System -> Administration -> Software Sources & uncheck the Installable from CD Rom checkbox on the Ubuntu Software tab.

---

### Post by BMWDriver on 2008-08-26
Thanks everyone, Sisco nailed it right.

---

