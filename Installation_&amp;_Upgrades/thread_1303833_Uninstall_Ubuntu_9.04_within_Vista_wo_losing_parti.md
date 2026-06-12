---
title: "Uninstall Ubuntu 9.04 within Vista w/o losing partition"
date: 2009-10-28
forum: Installation &amp; Upgrades
---

### Post by germund on 2009-10-28
Hello,

This question has probably been asked and answered before, but I am not tech savvy enough to understand and apply the solution to my own context.

I had installed Ubuntu 9.04 as a dual boot with Vista a few days ago.  I have had trouble at every step, and wanted to try a fresh install of 9.10 in a few days.  I would like to remove 9.04 without losing the partition back to windows so that I don't have to repartition Vista again.  I found this tutorial on YouTube and it seems to look easy, the only thing is I'm not sure at what point to stop so that the partition will be available for 9.10.  Do I want the partition left as "Free Space", or "Unallocated Space"?  Or does it even matter?

Thanks,

Bruce

---

### Post by Robbartz on 2009-10-29
You may as well just leave it as it is now and then re-install 9.10n into that same partition, if you delete the partition then you will only have to recreate it later.

---

### Post by presence1960 on 2009-10-29
if you installed 9.04 **within Vista** as your title says, there is no "partition" for Ubuntu, it is actually a file. You can remove Ubuntu from Vista the same way you add/remove software from within Control Panel. 

If you installed Ubuntu within windows this is called wubi. In order to install 9.10 you should uninstall 9.04 or you will probably end up with two Ubuntu installs within windows and two files taking up space within the windows filesystem, one for 9.04 & one for 9.10.

If you need a reference point see here: [https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

---

### Post by germund on 2009-10-29
> **Robbartz said:**
> You may as well just leave it as it is now and then re-install 9.10n into that same partition, if you delete the partition then you will only have to recreate it later.

I thought I had read elsewhere that 9.10 would not install over 9.04 and required it's own space?

Bruce

---

### Post by presence1960 on 2009-10-29
> **germund said:**
> I thought I had read elsewhere that 9.10 would not install over 9.04 and required it's own space?

Bruce

If linux is actually installed to a partition (not wubi- inside windows) you can install any OS over that because the partition will be formatted first by the installer unless you choose not format it.

If you used wubi you cannot install over another installation. You will have to uninstall first and then install the new version or if you install without removing the first installation you will then have 2 separate installs.

---

### Post by germund on 2009-10-29
Yes, Linux is installed to a partition (about 23 GB).  However, I can not get into it at all.  The booting options always gave me errors when I tried to get into it, (I got in once or twice, but had a pile of warning and error messages and was unable to fix them.)  Eventually, I ended up not even being able to access Vista either.  I managed to finally get Vista back, and no longer have the option of booting into Ubuntu.  I am afraid to try anything more with my Ubuntu partition for fear of messing up Windows again.  This is why I wanted to eliminate the old installation completely as when I try 9.10 I would like a clean slate.  I was wanting to do it from within Windows because the current installation of Ubuntu is inaccessible.

(In the past I have managed to successfully install earlier versions of Ubuntu on Win 98 and and Win XP computers as dual boot systems without trouble.  I'm not sure whether the problems I've had this time is because of Vista, this version of Ubuntu, or my own incompetence - perhaps a combination of all three.)

Sorry for my lack of clarity in my earlier posts.

Bruce

---

### Post by germund on 2009-10-30
I cleared the 9.04 partitions using Vista's disk management tools, and returned them to an unallocated state.  9.10 installed without any problems and seems to be working fine.

Thanks to those who offered advice.

Bruce

---

### Post by theozzlives on 2009-10-30
I'm a bit confused but I'm glad you got it working.

---

