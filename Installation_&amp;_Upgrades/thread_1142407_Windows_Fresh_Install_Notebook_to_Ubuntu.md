---
title: "Windows Fresh Install Notebook to Ubuntu"
date: 2009-04-29
forum: Installation &amp; Upgrades
---

### Post by nomnex on 2009-04-29
[LEFT][FONT=Verdana][SIZE=2]Hi,[/SIZE][/FONT][/LEFT]
 [FONT=Verdana][SIZE=2]
[/SIZE][/FONT]   [FONT=Verdana][SIZE=2]I am a windows user. Location: Japan. Language read/spoken: English. When I purchase a Notebook, I always do a fresh install with a Retail XP CD, and now Vista DVD.[/SIZE][/FONT][FONT=Verdana][SIZE=2]

[/SIZE][/FONT][FONT=Verdana][SIZE=2]Laptop fresh install procedure is not documented. It is often a pain to find/install the notebook model specific drivers (dll, .cat, .exe)[/SIZE][/FONT][FONT=Verdana][SIZE=2]

[/SIZE][/FONT][FONT=Verdana][SIZE=2]My way (clean install):[/SIZE][/FONT][FONT=Verdana][SIZE=2]

[/SIZE][/FONT][FONT=Verdana][SIZE=2](Vista only) NTFS Primary boot partition 4k &#8211; Since vista will not boot with a different cluster size. - n:\Boot[/SIZE][/FONT][FONT=Verdana][SIZE=2]
[/SIZE][/FONT]  [FONT=Verdana][SIZE=2]NTFS Primary system partition 16k &#8211; n:\WINDOW[/SIZE][/FONT][FONT=Verdana][SIZE=2]
[/SIZE][/FONT]  [FONT=Verdana][SIZE=2]NFTF Logical partition 16k for my documents&#8211; [n:\]("file:///n:/")[/SIZE][/FONT][FONT=Verdana][SIZE=2]

[/SIZE][/FONT][FONT=Verdana][SIZE=2]Once XP/Vista is up and running, I install the drivers through the Microsoft Devices Manager console. Or I double click when they are packed with an installer.[/SIZE][/FONT][FONT=Verdana][SIZE=2]

[/SIZE][/FONT]     [FONT=Verdana][SIZE=2]Pro: Bloat ware free, fast and reliable, Native English.[/SIZE][/FONT][FONT=Verdana][SIZE=2]
[/SIZE][/FONT]  [FONT=Verdana][SIZE=2]Con: Price exorbitant (Notebook + Retail OS + Retail Office Suite)[/SIZE][/FONT][FONT=Verdana][SIZE=2]

[/SIZE][/FONT][FONT=Verdana][SIZE=2]----[/SIZE][/FONT][FONT=Verdana][SIZE=2]
[/SIZE][/FONT]  [FONT=Verdana][SIZE=2]Ubuntu 9.04 + Office 3 seem mature and reliable products. I would be glad to say good-bye to $M but I have a few questions before jumping in.[/SIZE][/FONT][FONT=Verdana][SIZE=2] How can I do a full clean install using Ubuntu only? Is it possible, wise, or not?

[/SIZE][/FONT][FONT=Verdana][SIZE=2]Installation[/SIZE][/FONT][FONT=Verdana][SIZE=2]

[/SIZE][/FONT][FONT=Verdana][SIZE=2]Q1 Is ext3 or ext4 comparable to NTFS or do they need specific setting during installation?[/SIZE][/FONT][FONT=Verdana][SIZE=2]
[/SIZE][/FONT]  [FONT=Verdana][SIZE=2]Q2 How to set the cluster size upon installion?[/SIZE][/FONT][FONT=Verdana][SIZE=2]
[/SIZE][/FONT]  [FONT=Verdana][SIZE=2]Q2 Is the partitioning for 1 volume Windows like (4 primary, or up to 3 primary and 1 logical partitions)?[/SIZE][/FONT][FONT=Verdana][SIZE=2]

[/SIZE][/FONT]     [FONT=Verdana][SIZE=2]Drivers[/SIZE][/FONT][FONT=Verdana][SIZE=2]

[/SIZE][/FONT]     [FONT=Verdana][SIZE=2]Q3 How to install the notebook specific drivers:.dll library (e.g. Sony Vario), drivers with installer and without (all Windows specific)?[/SIZE][/FONT][FONT=Verdana][SIZE=2]

[/SIZE][/FONT]     [FONT=Verdana][SIZE=2]Peripherals[/SIZE][/FONT][FONT=Verdana][SIZE=2]

[/SIZE][/FONT][FONT=Verdana][SIZE=2]Q4 Buffalo Wireless NAT Broadband Router[/SIZE][/FONT][FONT=Verdana][SIZE=2]
[/SIZE][/FONT]  [FONT=Verdana][SIZE=2]Q5 Canon i6500 Printer[/SIZE][/FONT][FONT=Verdana][SIZE=2]
[/SIZE][/FONT]  [FONT=Verdana][SIZE=2]Q6 Buffalo HDD 2x500 in Raid 1 (NTFS 16k)[/SIZE][/FONT][FONT=Verdana][SIZE=2]
[/SIZE][/FONT]  [FONT=Verdana][SIZE=2]Q7 Silex Print server wireless[/SIZE][/FONT][FONT=Verdana][SIZE=2]

[/SIZE][/FONT][FONT=Verdana][SIZE=2]All are windows specific. Can I have them running under Ubuntu?[/SIZE][/FONT][FONT=Verdana][SIZE=2]

[/SIZE][/FONT][FONT=Verdana][SIZE=2]General[/SIZE][/FONT][FONT=Verdana][SIZE=2]

Q8 How do I export all my data on a backup drive NTFS to my newly installed Ubuntu?

[/SIZE][/FONT]     [FONT=Verdana][SIZE=2]Q9 A notebook runing Ubuntu (only) can access data locally/remotely in a NTFS partition &#8211; I guess the answer is NO?[/SIZE][/FONT][FONT=Verdana][SIZE=2]

Q10 Is workgroup setting as easy as using Windows (link or explanation)? So far what I have read seem complicated LDAP settings, and many command line to pass.

[/SIZE][/FONT]     [FONT=Verdana][SIZE=2]Q11 Is it possible to have a mix workgroup environment Utuntu/Windows &#8211; I guess the answer is NO?[/SIZE][/FONT][FONT=Verdana][SIZE=2]

[/SIZE][/FONT]     [FONT=Verdana][SIZE=2]Q12 any link/reading about Ubuntu linux for my information? I found this one so far: [https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows](https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows)[/SIZE][/FONT][FONT=Verdana][SIZE=2]

[/SIZE][/FONT]     [FONT=Verdana][SIZE=2]2xthank: for reading/for support.[/SIZE][/FONT]

---

### Post by Mark Phelps on 2009-04-29
Can only answer some of your questions ...

> **nomnex said:**
> How can I do a full clean install using Ubuntu only? Is it possible, wise, or not?

BEFORE you do that, suggest you boot first using a LiveCD to see how well Ubuntu detects your hardware and what functions don't work.  Anything that is not detected using the LiveCD, and any functions that don't work will required lots of post-install hacking to get working -- and some of them may never work.

That said, if you like what you experience using the LiveCD, before you exit, open the Partition Editor and remove all the partitions from your hard drive.  Then, reboot using the same LiveCd and do a default install, selecting the entire drive.
> Is ext3 or ext4 comparable to NTFS or do they need specific setting during installation? 

Would avoid Ext4 for now and stick with Ext3. Wait until the system tools and apps have been updated to work with Ext4.
>  How to set the cluster size upon installion?

Don't know how to do this and, even if I did, would not mess with it.

> Is the partitioning for 1 volume Windows like (4 primary, or up to 3 primary and 1 logical partitions)?
Ubuntu will setup its own partitions if you let it.  If you want to do manual partitioning, suggest you search this forum for posts providing the details.

> How to install the notebook specific drivers:.dll library (e.g. Sony Vario), drivers with installer and without (all Windows specific)?
Don't mean to be rude, but this is Linux, not Windows.  With the exception of NDISWrapper for networking, you can't install or use MS Windows-specific drivers.  If you need those for your hardware to work, then don't switch over to Ubuntu. (Another reason to use the LiveCD first to see what hardware works and doesn't work)

>  Buffalo Wireless NAT Broadband Router
Routers are generally administered through a web connection and don't have drivers or software.  So, this should work like any other router.

> Canon i6500 Printer
Another thing to check in LiveCD mode.  Try running "localhost:631" in your web browser and using it to install your printer.  Again, you won't be able to use MS Windows drivers or software for your printer.
> Buffalo HDD 2x500 in Raid 1
Can't install to NTFS in Linux.  Don't know about installing to RAID, but again; can't use MS Windows RAID drivers or software.
> Silex Print server wireless
Wireless is often very difficult to get working. May have to resort to using NDISWrapper and/or WiCD.  Something else to check in LiveCD mode.
> All are windows specific. Can I have them running under Ubuntu?
Apart from Wine (a software layer that allows you to run SOME MS Windows programs), the general answer is depends -- on how well Ubuntu detects the hardware and installs the proper Linux drivers.
> How do I export all my data on a backup drive NTFS to my newly installed Ubuntu?
Using the ntfs-3g package, you can mount and read NTFS volumes in Ubuntu.  An external drive plugged in via USB will automatically be detected and mounted.  You simply open it with a file manager and copy the files.
> A notebook runing Ubuntu (only) can access data locally/remotely in a NTFS partition – I guess the answer is NO?
Answer is yes -- see above.
> Is workgroup setting as easy as using Windows (link or explanation)? So far what I have read seem complicated LDAP settings, and many command line to pass.
You will have to check on the networking forum about this, but as with other MS Windows features, you can't use this natively in Linux.
> Is it possible to have a mix workgroup environment Utuntu/Windows – I guess the answer is NO?
Answer is maybe.  Samba provides a way to network with MS Windows machines.  See the Networking forum for more ingo.

General comment.  Migrating to Linux (Ubuntu or any other distro) is INTENDED to be a learning experience.  If you come here willing to use different apps (i.e., Linux apps), interested in transitioning over to doing things the "Linux way", you will find the experiences rewarding and satisfying.  The enormous variety of free stuff is simply astounding.  

But ...

If you come here intending to reuse all your MS Windows apps, and continue to do things the MS Windows way, you will be sorely disappointed and frustrated.  

The LiveCD mode gives you a chance to experience Linux without messing with your current installation.  Strongly recommend using that before you make the switch.

---

### Post by nomnex on 2009-04-29
[FONT=Verdana][SIZE=2]Mark, Thanks for your answer.[/SIZE][/FONT][FONT=Verdana][SIZE=2]
[/SIZE][/FONT] 
 *[FONT=Verdana][SIZE=2]For memo: I purchase my notebooks in Japan, where I live. When I clean-install, I have to re-install the model specific drivers/firmware manually. As aforementioned, they come in different flavor (.dll, .exe) - FN keys, fax, NIC, Touchpad, etc.[/SIZE][/FONT]*[FONT=Verdana][SIZE=2]
[/SIZE][/FONT] 
 [FONT=Verdana][SIZE=2]Installing the LiveCD next to Windows will give me a good idea using the current configuration. However my intend is to do a clean installation on an empty volume. According to your answer, it cannot be done this way?[/SIZE][/FONT]

> [FONT=Verdana][SIZE=2]You can't install or use MS Windows-specific drivers. If you need those for your hardware to work, then don't switch over to Ubuntu.[/SIZE][/FONT][FONT=Verdana][SIZE=2]
[/SIZE][/FONT] 
 [FONT=Verdana][SIZE=2]I am still in the vague. Correct if I am wrong:[/SIZE][/FONT]
 [FONT=Verdana][SIZE=2]a. Notebooks give little opportunity for component modification (fact).[/SIZE][/FONT]
 [FONT=Verdana][SIZE=2]b. Ubuntu notebooks compatibility page lists notebooks pre-installed with Windows (drivers/firmware included). It has no informative value regarding a clean installation as I would like to do?[/SIZE][/FONT]
 [FONT=Verdana][SIZE=2]c. If I install Ubuntu on a clean partition, I lose the ability to  install the notebook drivers/firmware (since they are are packed in a windows format - .exe)?[/SIZE][/FONT]
 [FONT=Verdana][SIZE=2]d. Until the makers provide Linux drivers for their given notebooks a clean-installation is not possible?[/SIZE][/FONT]
 [FONT=Verdana][SIZE=2]e. The current ONLY viable installation is:[/SIZE][/FONT][INDENT][FONT=Verdana][SIZE=2]1. a notebook with a Windows + drivers working[/SIZE][/FONT]
[FONT=Verdana][SIZE=2]2. to run the LiveCD (function check)[/SIZE][/FONT]
[FONT=Verdana][SIZE=2]3. from that point, to install Ubuntu over Windows in replacement (or in dual-boot)[/SIZE][/FONT]
[/INDENT][FONT=Verdana][SIZE=2]To conclude (need confirmation) it is not advisable for a notebook owner to part from his windows OS cd (as I would like to do) in profit of a Ubuntu CD. In some point the user might still need his windows CD. I need to sort this out before going further with the other questions.[/SIZE][/FONT][FONT=Verdana][SIZE=2]
[/SIZE][/FONT] 
 [FONT=Verdana][SIZE=2]> Migrating to Linux (Ubuntu or any other distro) is INTENDED to be a learning experience. If you come here willing to use different apps (i.e., Linux apps), interested in transitioning over to doing things the "Linux way", you will find the experiences rewarding and satisfying.[/SIZE][/FONT]
 
 [FONT=Verdana][SIZE=2]I am perfectly clear with that. If I can have my notebook fully running without any $M CD around, I do want to jump-in.[/SIZE][/FONT]

---

### Post by nomnex on 2009-05-01
Bump anyone?

Going forward with the Ubuntu documentation + re-reading this thread, do I have to understand that Ubuntu OS can detect some (if all) of my my notebook firmware/drivers (like the FN keys, the NIC card, etc) out of the box and without having to install the drivers, as it is customary to do using Windows (or they simply do not work)?

I read some posts about Ubuntu fresh install on notebooks with working sound/wireless/etc. and it seems promising, but some of the users resorted to patches to have the FN key working or wireless.

Any one with the experience of installing Ubuntu on a notebook and knowledgeable about searching/requesting/installing a patch on Ubuntu? Thanks.

---

