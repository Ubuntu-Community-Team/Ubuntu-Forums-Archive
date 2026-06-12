---
title: "windows registry, linux command line"
date: 2008-10-21
forum: General Help
---

### Post by aaronmarsh632 on 2008-10-21
Hi, is it possible to delete something from the windows registry using the terminal on an ubuntu boot disk?

For example if my windows xp had a virus and there was something in the registry which was part of the virus but the xp opps was taking forever to boot, can the registry item be deleted from linux?

Thanks

---

### Post by oldos2er on 2008-10-21
Is the Windows registry a text file? If so, you should be able to edit it from the Live CD. You'll need to mount the partition it's on first.

---

### Post by aaronmarsh632 on 2008-10-21
Thanks for the reply. The registry file isnt a text file, im not sure what you would say it is but it is located at HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Run "Antivirus" in regedit.

How would you go about removing this?

tnx

---

### Post by TreeFinger on 2008-10-21
[http://www.easydesksoftware.com/regfiles.htm](http://www.easydesksoftware.com/regfiles.htm)

---

### Post by mckinley on 2008-10-21
There is a tool in windows called Reg, it should be located in the System32 folder, you run it from cmd & can also use this in safe mode, or by booting with a windows boot disk / windows cd
if you type reg /? in the cmd window it will give you a list of option / commands. you can add / delete / modify registry settings with this. some viruses now lock the registry by adding a key, you can remove this setting / disable it via reg.

---

### Post by aaronmarsh632 on 2008-10-21
thats gr8 info thanks

---

