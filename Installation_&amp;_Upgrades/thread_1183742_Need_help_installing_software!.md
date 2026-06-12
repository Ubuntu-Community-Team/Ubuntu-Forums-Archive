---
title: "Need help installing software!"
date: 2009-06-10
forum: Installation &amp; Upgrades
---

### Post by chazzaaa on 2009-06-10
I am completely new to linux and have found it extremely simple to use, except for the installation of packages, as well as p2p software i have tried to download.
Every time i try to install a package from synaptic package manager, there is an error at the last stage.
Along with this, i have tried to download p2p software which is supposed to be compatible with linux, and then have not been able to open it as the system does not have the application to open the software.
is there any way around this? i feel like my netbook has been a complete waste of money. the model is Dell inspiron mini 10.
Please help if you can

---

### Post by coffeecat on 2009-06-10
Actually, installing software in Ubuntu is far, far simpler than in Windows, so it sounds as though something has gone wrong.

> **chazzaaa said:**
>  as well as p2p software i have tried to download.

Until you are more experienced, try not to download software from websites. That way lies a vale of tears. You need to fix whatever's gone wrong with Synaptic.

> **chazzaaa said:**
> Every time i try to install a package from synaptic package manager, there is an error at the last stage.

Post the **exact** error message and we'll help you fix it. Synaptic is usually very reliable.

Also try Applications > Add/Remove. This is quite different from the same-named abomination in Windows, and very newcomer friendly. But it might not work until you've got Synaptic fixed, as it uses the same underlying engine.

> **chazzaaa said:**
> Along with this, i have tried to download p2p software which is supposed to be compatible with linux, and then have not been able to open it as the system does not have the application to open the software.

You've downloaded the wrong package. If you download a .deb package, all you have to do is to double-click on it. But see what I said above. Let's get Synaptic up and running first.

---

### Post by zvacet on 2009-06-10
Go to the system>admin>software sources and check all except source under ubuntu software tab and first two under updates tab.Reload.Go to the applications>Add/Remove>all available app and look for app you want to install.

---

### Post by retlolo on 2009-06-22
I need the same sort of help as chazzaa.  Synaptic manager shows that the drivers for my Brother printer are 'installed.'  But I can't find them anywhere, nor can I print.  What must I do, please?  cheers, retlolo

---

### Post by The-Don on 2009-06-22
This is what you need to view: [http://ubuntuforums.org/showthread.php?t=500020](http://ubuntuforums.org/showthread.php?t=500020)

I've been using Linux for 1x week and because of that guide I've installed Jaunty on both my laptop and PC. That guide is awesome!

---

### Post by coffeecat on 2009-06-22
> **retlolo said:**
> Synaptic manager shows that the drivers for my Brother printer are 'installed.'  But I can't find them anywhere, nor can I print.  What must I do, please?  cheers, retlolo

Connect your printer and switch it on. If it is a usb printer it should be autodetected and autoinstalled soon after it is connected. If this doesn't happen go to System > Administration > Printing (assuming you're using Ubuntu/gnome), click on the 'new' button and follow the prompts. If that doesn't work, post back with details of your printer: model number and whether it is usb or network.

---

### Post by retlolo on 2009-06-23
many thanks, coffeecat--printer works fine now.  So: this success earns you two related questions: googleearth, also 'installed' from Synaptic, cannot be found by the Terminal.  And various zip boxes, sucessfully downloaded and appearing on the Desktop, can't be opened or ran.  best regards, R.

---

### Post by Mark Phelps on 2009-06-23
> **retlolo said:**
> I need the same sort of help as chazzaa.  Synaptic manager shows that the drivers for my Brother printer are 'installed.'  But I can't find them anywhere, nor can I print.  What must I do, please?  cheers, retlolo

You do not have the same problem.  The original problem is with installing software; yours is with getting drivers to work for a specific printer.  

Please don't hijack this thread; you would do better starting your own and including the printer model in the title.  That way, folks with experience with that printer and its drivers will see your thread and be able to help you.

---

### Post by coffeecat on 2009-06-23
> **Mark Phelps said:**
> Please don't hijack this thread; you would do better starting your own and including the printer model in the title.

I agree. This thread is becoming a mess. I was torn between telling the OP the same and helping out, so...

> **retlolo said:**
> googleearth, also 'installed' from Synaptic, cannot be found by the Terminal.  And various zip boxes, sucessfully downloaded and appearing on the Desktop, can't be opened or ran.

**retlolo**, you would be much better off starting your own thread. Make sure the title is descriptive and relevant.

---

