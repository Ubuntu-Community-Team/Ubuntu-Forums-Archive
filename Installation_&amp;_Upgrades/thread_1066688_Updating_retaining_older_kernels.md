---
title: "Updating retaining older kernels ?"
date: 2009-02-11
forum: Installation &amp; Upgrades
---

### Post by UnCola on 2009-02-11
I recently updated to 8.04 on two machines with no problems, leaving the third and most important one for last.  And that's where the problem is.

On booting up in the latest kernel (26.24) it says "vm mmap_min_addr fail" and the sound and wireless do not work.  It also takes ages to boot up.

I googled and tried the various fixes and they did not work for me.  It isn't that important now as I can boot in the earlier kernel (26.22) and everything works.   But I have two questions:

1. Will updates eventually replace the earlier kernel and leave me stuck?

2.  If I upgrade now to 8.10 will I still have the earlier kernel(s) accessible to use?

And given that this is a known issue, are updates likely to address it?
And can you reinstall an older kernel if you have to?

Thanks in advance for any help.

---

### Post by UnCola on 2009-02-11
If this isn't the right forum for this can someone tell me where should I post it?

I've tried to edit the thread title to read "Updating Problem ?" but no success.

---

### Post by oldos2er on 2009-02-11
You can keep as many kernels as you like.

 8.10 uses 2.6.27.x kernels.

---

### Post by UnCola on 2009-02-11
> **oldos2er said:**
> You can keep as many kernels as you like.

 8.10 uses 2.6.27.x kernels.
Thanks that helps, but how do I keep the kernels? 

When I boot up the grub loader gives me the choice of 3 kernels, the newest one appearing first.  So if I upgrade to 8.10 will my 3 kernels be 8.10, 8.04 and 7.10?

My concern is if I upgrade and can no longer access the earlier kernel which actually worked.  I can't face a reinstall because of all the finicky programs I've installed.

---

### Post by snova on 2009-02-11
> **UnCola said:**
> So if I upgrade to 8.10 will my 3 kernels be 8.10, 8.04 and 7.10?

Yes. They will all be kept until you explicitly remove the older ones.

---

### Post by prshah on 2009-02-12
> **UnCola said:**
> 
When I boot up the grub loader gives me the choice of 3 kernels, the newest one appearing first.  So if I upgrade to 8.10 will my 3 kernels be 8.10, 8.04 and 7.10?

Kernel versions are different from Ubuntu versions. If you upgrade to 8.10, you will lose the ability to boot from earlier (8.04) etc versions of ubuntu, and you will be using the kernel that is available with 8.10 only.

In each ubuntu versions, kernels are upgraded as and when available. These upgrades will give you the ability to retain the old (replaced) kernel, but you cannot go back to whatever kernel was last used in an earlier version of ubuntu.

I hope this explanation is clear; post back if you feel it cannot be understand.

---

### Post by Vico Vicario on 2009-02-12
Your old kernels are kept until you remove them using synaptic or the like. But bear in mind that grub will only show you a maximum (I believe 7) in the menu.

If you upgrade version, your old kernels are kept, but you might face other problems. Sometimes things like usbdev change and older kernels have problems.

If you are planning to upgrade, download a LiveCD and test your hardware.

V.

---

### Post by UnCola on 2009-02-13
> **prshah said:**
> 

In each ubuntu versions, kernels are upgraded as and when available. These upgrades will give you the ability to retain the old (replaced) kernel, but you cannot go back to whatever kernel was last used in an earlier version of ubuntu.

I hope this explanation is clear; post back if you feel it cannot be understand.

OK so this means that in 8.04 with 3 kernels offered in the grub loader menu I am choosing between the three most recent kernels within 8.04?   I know that the two older ones of these work fine, it is just the latest which has issues.  So as long as I stay with 8.04 I know I will always be able to boot.

How would you access the other (ie not the three most recent) 8.04 kernels if they exist, ie the fourth, fifth sixth etc?

---

### Post by prshah on 2009-02-13
> **UnCola said:**
> in 8.04 with 3 kernels offered in the grub loader menu I am choosing between the three most recent kernels within 8.04? 

How would you access the other (ie not the three most recent) 8.04 kernels if they exist, ie the fourth, fifth sixth etc?

Yes, when you choose from the GRUB menu, you are choosing from available (and installed) kernels for your particular version of Ubuntu (8.04 in this case).

If you now upgrade to 8.10, you will lose these kernels (and corresponding GRUB entries), and you will find your GRUB will offer you only 8.10 and one kernel (until you update to the latest updates, when GRUB will then list other available and installed kernels for 8.10).

All installed kernels for your current version of Ubuntu will be shown in the GRUB until you upgrade Ubuntu to a newer version, or until you manually uninstall that particular kernel.

---

### Post by ambdeep on 2009-02-14
I am new to ubuntu i need some help......
How do u re-download a kernel version?
How do u remove an older kernel version??

Thanks in advance.:KS

---

