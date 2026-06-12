---
title: "Cant access Restricted Driver Manager"
date: 2008-03-30
forum: Hardware &amp; Laptops
---

### Post by jonask on 2008-03-30
**This post could be related to an Ubuntu bug filed at**: [http://ubuntuforums.org/showthread.php?p=4618013#post4618013](http://ubuntuforums.org/showthread.php?p=4618013#post4618013) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I have a HP dv9700t laptop and tried to install virtualbox. Apparently something happend to my graphic driver after that. I have removed virtualbox. Now I cant access the restricted drivers manager (get message):
****************************************
You need to install the package

linux-restricted-modules-2.6.22-14-server

for this program to work.
****************************************

However I already have this package installed, and I have also tried to reinstall it. 

When I go to "System, Preferences, Appearence, Visual Effects" I am only able to choose none effects. (not normal)

Any suggestions would really be appreciated? Sorry for double posting.

Jonas




Thank you very much

---

### Post by Oldsoldier2003 on 2008-03-31
> **jonask said:**
> **This post could be related to an Ubuntu bug filed at**: [http://ubuntuforums.org/showthread.php?p=4618013#post4618013](http://ubuntuforums.org/showthread.php?p=4618013#post4618013) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I have a HP dv9700t laptop and tried to install virtualbox. Apparently something happend to my graphic driver after that. I have removed virtualbox. Now I cant access the restricted drivers manager (get message):
****************************************
You need to install the package

linux-restricted-modules-2.6.22-14-server

for this program to work.
****************************************

However I already have this package installed, and I have also tried to reinstall it. 

When I go to "System, Preferences, Appearence, Visual Effects" I am only able to choose none effects. (not normal)

Any suggestions would really be appreciated? Sorry for double posting.

Jonas




Thank you very much

now that you have the kernel restricted modules reinstalled- reinstall your restricted drivers using Restricted driver manager. If you can't do it through there you might try [Envy]("http://albertomilone.com/nvidia_scripts1.html")

---

