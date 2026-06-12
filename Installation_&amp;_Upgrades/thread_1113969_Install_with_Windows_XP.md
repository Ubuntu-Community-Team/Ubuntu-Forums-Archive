---
title: "Install with Windows XP"
date: 2009-04-02
forum: Installation &amp; Upgrades
---

### Post by hbradshaw on 2009-04-02
Hello:

I have a laptop with Windows XP already loaded.  In addition, I have SQL Server, MySQL Server and Oracle installed under Windows.

I would like to install Ubuntu as well.

Is it possible to have both installed?  If so, how do I go about doing this?

Thanks.

---

### Post by horseradish on 2009-04-02
I am a novice on ubuntu, so I don't know of any hazards or easier methods.

but I used wubi to add ubuntu alongside my windows OS. Then I could choose at startup which OS to use.

[http://wubi-installer.org/](http://wubi-installer.org/)

---

### Post by hbradshaw on 2009-04-02
Was it difficult to install?

Have you encountered any issues with both Windows and Ubuntu on the same machine?

---

### Post by manishtech on 2009-04-02
When you install, both are different OS and only one of them would run at a time.
Normally, you won't face any problems unless and until you mess up with the partitions. Messing up with the partitions requires you to experiment with your system. Normal Ubuntu Install is very intelligent. Just follow the steps shown in the installer

You have an option of installing it by partitioning it and installing it from the LiveCD itself or use Wubi. Wubi is a new tool using which you can install Ubuntu right from inside windows, it manages all the installation stuff. It adds Ubuntu to add remove programs such that Ubuntu can be removed as and when required.

---

### Post by hbradshaw on 2009-04-02
Hi,

I completely understand the trouble I can get into once I start messing with the partitions.  I don't want to mess with any of that.

I want to do a straight, simple install of Ubuntu.  

You say this Wubi will do all the work and configurations without my needing to do anything, correct?

That would be nice.

---

### Post by Therion on 2009-04-02
What you want to do is call "Dual Booting".  It's a very common setup.  

When you dual-boot you are prompted at restart which OS you would like to use; a default is selected after x-number of seconds.

Since you already have Windows installed all you need do is follow this tutorial to install Ubuntu alongside it.

[http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm?page=2](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm?page=2)



Personally, I do NOT suggest using Wubi.  That's just me though.

---

### Post by manishtech on 2009-04-02
> **Therion said:**
> 
Personally, I do NOT suggest using Wubi.  That's just me though.

Neither me, but still this is the last option when it comes to extremely n00bs. If a person fears that he might screw up his system due to less knowledge, wubi is the way to go.

---

### Post by pieisgood4589 on 2009-04-02
As mentioned above, dual booting is EXTREMELY easy with Ubuntu, the install by default automatically sets the dual-boot option to GRUB, the bootloader.

---

