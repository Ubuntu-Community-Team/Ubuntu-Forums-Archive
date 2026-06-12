---
title: "Printing to XP machine"
date: 2005-10-18
forum: Hardware &amp; Laptops
---

### Post by majkmil on 2005-10-18
Under Hoary I was able to print to my Canon I850 with cups by just entering the IP of the windows comp that the printer us connected. Now I have a fresh install of Breezy I cant get it to print. I have tried cups, samba(windows) printing, nothing works! I can share files and ping all computers on the network. I have followed a couple of how to's in the threads but I must be missing something. I love UBUNTU but I just need this last thing to work. PLEASE help if you can.     Thanks Mark

---

### Post by davidknibb on 2005-10-18
Presumably you started with the obvious ??

System > Administration > Printing

and then 

Printer > Add Printer

and then answer the questions ??

David

---

### Post by majkmil on 2005-10-18
yes, I tried cups first with ip of the xp machine with the printer connected to it. I get errors saying BAD NETWORK NAME in my cups log, I even tried using the NAME of the the networked computer. Then I tried samba printing and it would ask for login info for the other computers on the network. I used the  ip of the comp with the printer again but nothing. I am sure I am missing something, it is just frostrating bacause it was so easy under hoary.

---

### Post by davidknibb on 2005-10-18
So, when you use the printer wizard, you choose Network Printer - and then in the drop down box choose Windows Printer(SMB) ??

In Host, find the relevant server computer in the drop down box, and then in fill in the rest of the stuff.  The next screen allows you to choose the specific printer.

If it isn't then working - then sorry I cannot help any more

David

---

