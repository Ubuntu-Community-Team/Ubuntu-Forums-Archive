---
title: "Dual Booting and Disk Mounting"
date: 2008-02-07
forum: Hardware &amp; Laptops
---

### Post by AlanR8 on 2008-02-07
Evening

Here's the deal. My wife's Dell dual boots and she's primarily running XP. Kubuntu 7.10 is installed as well and the plan is to get her to migrate across.

When I set up the Kubuntu install it was no problem getting it to see the Windows partition, indeed, I've set it up so any documents created in Kubuntu get saved to the Windows My Documents folder. However, Windows can't see the Kubuntu partition. If I go into control panel, System Admin then Disk Management, the Kubuntu volume is "Unknown" and there are no options to run.

Where do I go from here? Am I missing something simple?

---

### Post by stoneybroke on 2008-02-07
I think I cured the problem with windows by setting up windows to networking you should then find that windows sees Ubuntu. But that's windows a right pain in the glass....

---

### Post by AlanR8 on 2008-02-08
Sorry I don't understand!!!!!

The Dell dual boots between XP and Kubuntu. When running Kubuntu it sees the XP partition but when running XP it CAN'T see the Kubuntu partition. 

I have five machines on my home network, three running Kubuntu and two XP machines. All is harmony and light, they all talk to each other perfectly. The only issue I have is as described above.

Any ideas anyone?

---

### Post by mkwerner on 2008-02-08
AlanR8,
If you want to access an EXT3 filesystem from XP, you need to get a driver for the filesystem - I use [EXT2 IFS for Windows]("http://www.fs-driver.org/") on a daily basis.  It gives you full read/write and allows you to map your Kubuntu partition(s) to a Windows drive letter.

Contrary to the name, it works with EXT3 filesystems too.

Let me know if you need any pointers.

Regards,
m.

---

### Post by AlanR8 on 2008-02-08
Thanks for that mkwerner, I'll give it a go!

Is it a "safe" program to install and run under XP?

---

### Post by mkwerner on 2008-02-08
Safe enough that I've been using it for years with no issue *knocks on wood* :)

As with any filesystem driver for Windoze, I'm sure there would be some case that would cause an issue, but I've used it on many machines without incident.

---

### Post by AlanR8 on 2008-02-08
Cheers, I'll let you know how I get on, and thanks for the quick response.

---

### Post by AlanR8 on 2008-02-13
mkwerner

Thanks for the pointer. I installed the prog in XP and it appeared in the Contol Panel. Double clicked the Icon, assigned a drive letter and it appeared in Explorer, fully accesible.

Many thanks for your help.

---

### Post by mkwerner on 2008-02-13
Awesome!

Glad I was able to offer my meager assistance :)

Take care, and enjoy!

m.

---

