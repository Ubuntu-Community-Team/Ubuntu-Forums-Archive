---
title: "unable to install printer"
date: 2007-11-10
forum: Hardware &amp; Laptops
---

### Post by leifwi on 2007-11-10
I deleted the old printer and want to install a new, but when I try to open the printer configuration tool, an empty window is opened, but after that the configuration tool stop responding.
How can I fix this?

---

### Post by erginemr on 2007-11-10
Hello there. To begin with, what is the brand and type of the printer you are planning to install?  

Second question, are you planning to re-install the same printer or are you planning to ditch an old printer to replace with a new one?

Third question, which version of Ubuntu are you using?

---

### Post by leifwi on 2007-11-10
The printer is a HP840c,
I plan to re-install the same printer. It is connected to a samba computer.
Ubuntu version is 7.10 on a IBM thinkpad 600.

---

### Post by erginemr on 2007-11-10
Sorry, I never used a printer under Linux, which is connected to a Windows machine under a network environment. Maybe, someone else, who is more knowledgeable on the subject may help.

All I can say is that, Ubuntu uses Cups backend to configure and run printers. If your regular printer config applet does not work, you may alternatively try using the cups configuration tool, which you can reach by entering the following virtual web address (it is actually the cups server) in Firefox or any other web browser:

[http://localhost:631/](http://localhost:631/)

You may be able to reinstall and configure your printer from there.

Good Luck...

---

### Post by leifwi on 2007-11-11
I can see the printer, but not modify or remove or do anything else. It does not seem to respond. Is there a file somewhere on my ubuntu computer I can modify to remove all printer setings and maybe get the configuration tool to work again?

---

### Post by leifwi on 2007-11-11
Some progress. I restored previous versions of /etc/cupsd.conf and /etc/printers.conf. Now I can change setting using the cups configuration tool, but I am not able to print a testpage. Any suggestions on what to do next????

---

### Post by leifwi on 2007-11-18
Problem solved. Probably typing error in password.

---

### Post by erginemr on 2007-11-18
Glad to hear that.

Now that your problem has been resolved, could you please mark your thread as SOLVED from under the "Thread Tools" menu at the top of this page?

On a side note, can you now use your printer configuration dialog? If not, I have discovered something that may be useful to you if your mother tongue is not English.

My mother tongue is Turkish, so is the language of my Ubuntu system. In Gutsy, I had trouble opening Totem media player, and the bug happened to be related to the language settings. I could overcome the problem by adding

env LC_CTYPE="en_US.utf-8" 

to the beginning of the Totem shortcut in the Application Menu. The same with the printer config settings. It refused to open just after I installed the virtual PDF writer, which I overcame by adding the above language directive to its shortcut as:

env LC_CTYPE="en_US.utf-8" /usr/bin/system-config-printer

So, in case your mother tongue is not English and you are still having problems with the config tool, you may give a try to this work-around solution.

---

