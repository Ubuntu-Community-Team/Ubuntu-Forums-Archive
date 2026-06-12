---
title: "Ext3, NTFS, XFS... which one?"
date: 2008-11-06
forum: Hardware
---

### Post by zackiv31 on 2008-11-06
So I'm slowly making the final switch to completely get rid of Windows...

I'm formatting some extra drives in my computer, and I don't know which filesystem to use.  gparted gives me about 12 options to choose from... which one should I go with?

I need large file support (greater then 4 gbs)... other then that, I just want to format them to the fastest filesystem.  Consider them just for storage (not for an OS)... although if you have a suggestion that I change my OS drives to (currently using ext3, im all ears).

---

### Post by ad_267 on 2008-11-06
So does windows need to access the drive?

If it's only for Ubuntu, then ext3 is the recommended format. If windows needs to be able to access it then probably ntfs.

---

### Post by zackiv31 on 2008-11-06
we can assume no to windows.... but is ntfs a better filesystem?  there has to be a reason microsoft used it over ext3... :)

---

### Post by ad_267 on 2008-11-06
Microsoft uses it because they invented it, as for whether it is better than ext3, I wouldn't know. I'm pretty sure Ext3 is a lot faster if you're using Linux though, NTFS had to be reverse engineered for it to be supported. I'm not sure that Linux file permissions will work properly with NTFS too. NTFS is a lot more prone to fragmentation.

---

### Post by Funnnny on 2008-11-06
> we can assume no to windows.... but is ntfs a better filesystem? there has to be a reason microsoft used it over ext3... 
They use it because they made it.
You should use NTFS if:
1. Sometimes you use Windows.
2. Sometimes you plug your extra driver in your friend's computer which use Windows.
3. Still new to Ubuntu

---

