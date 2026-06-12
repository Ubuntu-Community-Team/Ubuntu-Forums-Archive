---
title: "Wibi install on Vista 64-bit stops at grub prompt?"
date: 2008-11-01
forum: General Help
---

### Post by mutlus on 2008-11-01
Hi.

First of all i'm a newbie. I've downloaded the Wubi for Ubuntu 8.10. I've installed it then restarted the computer, at boot screen i've picked the Ubuntu then at "grub" prompt it's just stopped.

I've seen some threads about this problem but most of them can't help me because i'm using Vista. And can't have a "boot.ini" :) At Advanced System Settings-System Recovery/Boot section, i can see "Ubuntu" but when i run the "msconfig" command and try to change Boot thing i can't see the Ubuntu, just Vista.

System;
HP Pavilion DV9780et on Vista 64-bit Ultimate

Can anyone help?

---

### Post by caljohnsmith on 2008-11-01
One thing that you can do that might solve your problem is to make sure all your antivirus/antimalware programs are completely disabled when you install Ubuntu. And I'm not familiar enough with Vista to know how to disable Vista's built-in defenses, but you should do that too before the install. In order to modify Vista's boot manager, Ubuntu has to do things that will most likely appear as malicious to an antivirus program or the like, so you really need to disable them first. You can uninstall Ubuntu from the "Add/Remove Programs" in Windows (or whatever the equivalent is in Vista), and after disabling all antivirus programs and such, reinstall. Give that a shot and let me know how it goes.

---

### Post by mutlus on 2008-11-02
I've tried to uninstall Wubi from the /ubuntu folder but it's just removed the boot file (.mbr ). While restarting the computer i still must choose Vista or Ubuntu  and when i pick Ubuntu it says "No operating system found". /ubuntu folder's size is 10GB (as i wanted at Wubi setup) 

Now what should I? Try to install Wubi again as you've said or manually delete /ubuntu folder and remove "Ubuntu" from boot file and then install again?

---

### Post by caljohnsmith on 2008-11-02
Did you run the Ubuntu uninstaller through Vista's equivalent of "Add/Remove Programs" in the Vista control panel? I'm only familiar with Windows XP, so I don't know if Vista has a similarly named "Add/Remove Programs" application like XP uses. Or also, somewhere in the /ubuntu folder there should be the Ubuntu uninstaller application, and you could manually run it. As a last resort you could just delete the entire /ubuntu folder, and then manually fix your Vista boot menu with [EasyBCD]("http://neosmart.net/dl.php?id=1") so that it doesn't include the invalid option to boot Ubuntu. Once Ubuntu is completely uninstalled, then you could try installing it again with all antivirus-type programs disabled.

---

### Post by DeltaUK on 2008-11-02
i also have the same problem with 32bit vista home premium.. 
i have tried adding neogrub for wubi in easybcd and that dont work either, the error is file not found. so it cant access my drive.. is there any way around this?

---

### Post by mutlus on 2008-11-02
Now i'm giving the last updates,

Vista has something like "Add/Remove Programs" but Ubuntu isn't listed there. So as i've mentioned before i uninstalled it via /ubuntu-Uninstall. But it only erased .mbr file not /ubuntu folder and not Boot entry of Ubuntu. 
Today i've installed Wubi again without erasing old /ubuntu. This time i've used downloaded .iso Becasue last time Wubi downloaded .iso. And this time Nod32 was closed and after install i restart computer directly. Last time i did it 30 min. later.
At boot screen, i've Vista and two Ubuntu setup. I've picked the one at the bottom. And everything went smoothly. Now i've Ubuntu.

But i think, i'll do it all over again. Because neither EasyBCD nor VistaBOOTPro see Ubuntu setups at Boot file. And two Ubuntu entry make me insane :) 

In conclusion, i don't know how i've made this work. I don't think Nod32 would prevent something. Best guess is this time i've restarted computer 	immediately. Because waiting could have changed something. After reinstall, we will see whether it will work or not...

Thanks for everything by the way... I hope after installation, i could ask a lot of questions about ubuntu :)

---

### Post by DeltaUK on 2008-11-02
i also have nod32 but disabling it didnt make any difference.. i also have tried restarting immediatly..  i have tried a different version of grub4dos. i have also tried defragging.. now i am out of ideas =[  :confused::confused::confused:

---

### Post by meierfra. on 2008-11-02
[QUOTE=mutlus]Because neither EasyBCD nor VistaBOOTPro see Ubuntu setups at Boot file. And two Ubuntu entry make me insane[/QUOTE]

You should be able to delete the old Ubuntu entry from the Vista command line. For further help, open a terminal in Vista (click on "Start", type "cmd" and press "Ctrl+SHIFT+ENTER")

and post the output of 

```
bcdedit
```

---

