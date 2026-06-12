---
title: "Install Ubuntu and use Windows Boot Manager?"
date: 2009-11-06
forum: Installation &amp; Upgrades
---

### Post by Holyjoely on 2009-11-06
Hello,

First of all I really appreciate all the help that you guys on the forums give to people and I apologies if this has already been asked, I did a quick search and couldn't find what I was looking for. I have used ubuntu for a few months on my Desktop PC but would like to dual boot it with Windows XP on my laptop. I know that this is a simple task when installing grub to manage your operating systems and have no problem with it; but I would like to use Windows Xp's boot manager to dual boot Ubuntu and XP, as I feel it is a lot easier to edit, using boot.ini. 

Is this possible, if so how?

Thanks.

---

### Post by arubislander on 2009-11-06
If you don't mind putting up with a little bit of disk access speed degradation you could install Ubuntu via wubi.

Just boot into Windows and then insert the LiveCD. You'll be presented with a menu. The entry you want reads something like.. "install under windows" ...

---

### Post by Holyjoely on 2009-11-06
Yes I did consider that, thanks for the suggestion, but I would prefer not to use Wubi if possible. Of course if it is the only option then I will use it but in the past I have had problems where after uninstalling Ubuntu that was installed by Wubi I could not remove the Ubuntu boot option from Windows Boot Manager and it was not listed in boot.ini, so if avoidable I would prefer not to use Wubi. Once again, thanks for the suggestion.

---

### Post by ak331 on 2009-11-06
> Yes I did consider that, thanks for the suggestion, but I would prefer not to use Wubi if possible. Of course if it is the only option then I will use it but in the past I have had problems where after uninstalling Ubuntu that was installed by Wubi I could not remove the Ubuntu boot option from Windows Boot Manager and it was not listed in boot.ini, so if avoidable I would prefer not to use Wubi. Once again, thanks for the suggestion.


you can edit the windows boot manager by checking properties of my computer and in advance startup click edit and it will take you to the boot.ini and you can change the option there.

---

### Post by arubislander on 2009-11-06
Wubi has never removed the Ubuntu boot option on uninstalling in my experience either. But I've never needed to edit boot.ini manually to remove it, I've just used the tools Windows provided under Computer->Properties->Advanced->Startup and Recovery->Settings.

---

### Post by Holyjoely on 2009-11-06
Maybe it was just a one off problem. I will consider using Wubi again, I would just prefer not to if possible. Thanks for your swift reply.

---

### Post by ManyBeers on 2009-11-06
> **Holyjoely said:**
> Hello,

First of all I really appreciate all the help that you guys on the forums give to people and I apologies if this has already been asked, I did a quick search and couldn't find what I was looking for. I have used ubuntu for a few months on my Desktop PC but would like to dual boot it with Windows XP on my laptop. I know that this is a simple task when installing grub to manage your operating systems and have no problem with it; but I would like to use Windows Xp's boot manager to dual boot Ubuntu and XP, as I feel it is a lot easier to edit, using boot.ini. 

Is this possible, if so how?

Thanks.

What OS is currently installed on your laptop?
Is this what you are hoing for?
[IMG]http://img682.imageshack.us/img682/765/bootscreen.jpg[/IMG]

---

### Post by Mark Phelps on 2009-11-06
MS Windows can not boot Ubuntu without some help.

If you go to the NeoSmart Technology websight and read up on EasyBCD, you'll find that free SW can be downloaded and installed.

Once you do that, you will have an option to add an entry to the MS Windows boot menu for Ubuntu.  All you have to do is select the correct partition in the configuration panel.

Best to check at their website for the SW and for support.

---

### Post by ManyBeers on 2009-11-06
> **Mark Phelps said:**
> MS Windows can not boot Ubuntu without some help.

If you go to the NeoSmart Technology websight and read up on EasyBCD, you'll find that free SW can be downloaded and installed.

Once you do that, you will have an option to add an entry to the MS Windows boot menu for Ubuntu.  All you have to do is select the correct partition in the configuration panel.

Best to check at their website for the SW and for support.

He is wanting to boot Ubuntu with XP not Vista/win7. That picture is my laptop which boots both Ubuntu 8.04 and WindowsXP using ntldr Windows bootmanager.

---

### Post by Holyjoely on 2009-11-29
Sorry for the lack of activity, I thought this thread had died earlier. Thanks for all the help, I am now running windows 7 with no ubuntu installation, I will take a look at the NeoSmart site.

---

### Post by suresnjain on 2009-11-29
actually "start up manager"works fine to modify your default loading OS.Why not try this and thus stick with Grub.I am having dual boot desktop xp/ubuntu and eversince that is  since my Intrepid days, Start up manager has served me well.

---

### Post by Holyjoely on 2009-11-29
I downloaded EasyBCD and it looks like the easiest option for me, so I think I will go ahead and try that. Thanks for all the help.

---

