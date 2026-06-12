---
title: "Hopefully a simple one - File associations"
date: 2008-08-12
forum: General Help
---

### Post by TimboUK on 2008-08-12
I hope this is a simple one.

I removed Openoffice as I prefer Abiword and I dont need all the extras.

After installing I doubled clicked on one of my abiword documents (.abw) however it didnt open with Abiword and simply gave me the option to either display it or open it with another program.

I selected the later, only to find abiword wasnt in the list of programs, although it does display under my applications>office menu.

Can anyone help?

Thanks in advance.

EDIT*  Sorry, I dont know what happened, I know this should not be posted in this section.

(Ubuntu 8.04)

---

### Post by WRDN on 2008-08-12
Find the application name for the application you want to open the file with. To do this, right click on the Applications / Places / System menu and click Edit Menu. Now, find the entry for the program, right click on it and select Properties. The name will be listed next to "Command:".

Now, right click on the file you want to open, select Properties and the Open With tab. Next, click the "Add" button, and enter a "custom command" in the box at the bottom of the window.

---

### Post by armandh on 2008-08-12
some are easy and found in system/preference/preferred application
such as selecting thunderbird rather than evolution for when a valid@address is clicked

some applications are not as fully integrated and the file icon may require a right mouse click selecting "open with other application" and a pick from the list.

very poorly integrated applications you may have to open and then open the file or follow the procedure above.

---

### Post by kerry_s on 2008-08-12
right click the file> properties> open with, click add, put abiword.
after that it will use abiword for all files of that type.

---

### Post by p_quarles on 2008-08-13
> **TimboUK said:**
> EDIT*  Sorry, I dont know what happened, I know this should not be posted in this section.
Fixed. :)

---

### Post by TimboUK on 2008-08-13
Cheers all,

I can now run it in abiword.  However the requester box with the "run,display,cancel." always appears first before I select display and abiword loads.

Is there anyway so that double clicking on the file will automatically load abiword and the file without that requester box coming up?  At the moment the only way I can do that is by right clicking on the file and selecting "open with Abiword"

Cheers.

---

### Post by derrick81787 on 2008-08-13
> **TimboUK said:**
> I selected the later, only to find abiword wasnt in the list of programs, although it does display under my applications>office menu.

Can anyone help?

Thanks in advance.


Under the list of programs, go to "Use custom command", or something like that, and just type "abiword" (without the quotes).  That is exactly the same as choosing it from the list (if it had been on the list).

- Derrick

---

### Post by kerry_s on 2008-08-13
> **TimboUK said:**
> Cheers all,

I can now run it in abiword.  However the requester box with the "run,display,cancel." always appears first before I select display and abiword loads.

Is there anyway so that double clicking on the file will automatically load abiword and the file without that requester box coming up?  At the moment the only way I can do that is by right clicking on the file and selecting "open with Abiword"

Cheers.

that means the file your viewing is executable, happens when stored on fat file system.  right click> properties> permissions, uncheck execute

---

