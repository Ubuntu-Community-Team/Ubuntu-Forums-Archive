---
title: "Thinkpad &quot;access ibm&quot; button"
date: 2005-10-14
forum: Hardware &amp; Laptops
---

### Post by stevetxt on 2005-10-14
Does anyone know how to install ubuntu for dual boot so that the functionality of the "access ibm" button in XP is preserved?  It seems that installing Grub in the MBR messes this up.  But when I try to install it elsewhere, Grub seems not to like being not on the first partition and I get "missing operating system" when I try to boot.

I would like to know if anyone has a solution to this problem.  I have a T43 but I think this affects a number of the Thinkpad models.

Thanks,

Steve

---

### Post by Joe_lurker on 2005-10-18
I don't know how the boot loader would affect the "Access IBM" button.  Check out this link:

[http://www.thinkwiki.org/wiki/ThinkWiki](http://www.thinkwiki.org/wiki/ThinkWiki)

I don't think there is a more thorough Thinkpad website out there.

Joe

---

### Post by mattheweast on 2005-10-30
Sadly rewriting the MBR _does_ affect the functionality of the Access IBM button, and it is also known to prevent you from booting into the rescue partition at all. See [this bug]("http://bugzilla.ubuntu.com/show_bug.cgi?id=13390") for information and some suggestions.

---

### Post by Flandry on 2005-11-01
I installed Kubuntu for dual boot and the Access IBM button still works. You must not overwrite the MBR of the Windows partition, though. When (k)ubuntu gives you that option, say NO. Install grub to the boot partition of (k)ubuntu. Then, you must record a copy of that data and somehow get it into windows. You modify the windows boot.ini file to point to the boot loader you copied over from linux, and then everything works fine. 

I imagine the place i read the instructions is at one of the links given, or if not google for "dual boot" t42 or some such. The process is convoluted, unnecessarily so. It may not be worth it.

Edit: In case you're concerned about it as i was, the hibernate functionality still works in both windows and linux.  You just select linux in the boot menu and then it will recover.  I don't think you have any option but to return to windows if you've hibernated from windows.

---

### Post by emendelson on 2005-11-01
You need an IBM repair floppy; see the link in the last paragraph of this section:

[http://www.columbia.edu/~em36/ubuntubreezythinkpadt42.html#basicguidelines](http://www.columbia.edu/~em36/ubuntubreezythinkpadt42.html#basicguidelines)

---

