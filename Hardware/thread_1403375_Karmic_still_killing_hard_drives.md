---
title: "Karmic still killing hard drives?"
date: 2010-02-10
forum: Hardware
---

### Post by Nick_Jinn on 2010-02-10
Last I heard the problem was fixed, but I just lost my third hard drive in 4 months.

Yeah, I know what some people will say. The problem isnt Ubuntu its the hardware, they should make the hardware default settings better so that the OS doesnt have to compensate for their mistakes like Windows does....Whether that is true or not, my hard drives are getting destroyed when I install Ubuntu not when I run windows. That makes it Ubuntus problem to fix.

What is up with this? It really pains me to lose faith in Ubuntu since I support linux for ideological reasons. I want open source to overcome the mega-corporations. I am losing a bit of faith though.

Now I cant even reinstall windows and Gparted wont even work. Fortunately I am still under warranty and can still turn it in for a new one, but that means 3 weeks without a laptop.

This sucks.

---

### Post by Smith6 on 2010-02-10
I run Xubuntu. I suspect I might be running into (not the same) but similar prob. Its been only weeks since I switched from windows... Xubuntu still does not allow me to access my windows partition "32GB filesystem". 

The only "file system" I am allowed access to is the Xubuntu partition. So everytime I need to edit some word documents, I cannot simply access them via Xubuntu, instead I have got to reboot to Windows and access them.

Is there a programme that would make life easier?

---

### Post by End Us3r on 2010-02-10
I'm running 8 drives under Karmic and I have had no issues so far.

---

### Post by doas777 on 2010-02-10
if you are referring to the load cycle issue, then I think it is fixed, and more than that, I think that that problem has a somewhat slower onset than you are describing. iirc, it may reduce a drives lifespan from 3 years to 1 year, but I'd be supprised if it reduced it to less than 40  days.

here is how you can test to see if you are affected by load cycle issues. also when you replace the drive, don't use a "green" one, as the bug only affects drives with aggressive power saving control.
[http://ubuntuforums.org/showthread.php?p=5031046](http://ubuntuforums.org/showthread.php?p=5031046)
 

personally I'd suspect power issues if you are burning through them that quickly.

---

### Post by End Us3r on 2010-02-10
> **Smith6 said:**
> I run Xubuntu. I suspect I might be running into (not the same) but similar prob. Its been only weeks since I switched from windows... Xubuntu still does not allow me to access my windows partition "32GB filesystem". 

The only "file system" I am allowed access to is the Xubuntu partition. So everytime I need to edit some word documents, I cannot simply access them via Xubuntu, instead I have got to reboot to Windows and access them.

Is there a programme that would make life easier?

If your Windows partition is formated as an NTFS drive then you should install ntfs-3g via Synaptic Package Manager (System menu -> Administration). ntfs-3g provides full read-write access to NTFS formatted partitions.

---

