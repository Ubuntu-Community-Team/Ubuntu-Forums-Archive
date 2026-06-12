---
title: "Partial Upgrade: No longer see Ubuntu in Grub Menu."
date: 2009-08-16
forum: Installation &amp; Upgrades
---

### Post by hardtrance on 2009-08-16
So I have somehow broken my ubuntu install.  I have been receiving an error every time I would login for a week or so that an upgrade was not possible, but a partial upgrade was availiable.  It would then crash and say that it was unable to authenticate libdb4.3 and fail to perform the partial upgrade.  
   
I got a little frustrated and finally sat down today and apparently did some real harm.  Through the package installer I install the libd4.3 packages and then ran an upgrade.  To my relief (at the time)  the partial upgrade began and things were happening.  Watching the completion bar slowly moving across the screen I felt like I had actually troubleshooted the problem and on my own!  How wrong I was.  One of the consequences of the upgrade had disconnected me from my Network here at the dorm.  This did not alarm me as I figured some network tools had been upgraded.  When I went to System > Administration however, there were no network tools listed.  I panicked and thought that perhaps I needed to reboot.  In windows this seems to work occasionally.  Well when I rebooted GRUB showed only the Linux memtest item and the XP installation.  My linux installation menu item disappeared.  
    
What do I do now?  All of my research is on my linux partition.  Sure I have the data and analysis backed up, but it took me over a week to install all of the analysis software (root, iraf, pyraf, numpy, scitools, idl, ...). Has anyone experienced a problem like this in the past?  

Thank you for your help in advance.  I have been googling libdb4.3 and apparently this is a problem for many people.  I dont know how or why it caused my upgrade to fail (not authenticated I guess), and now I am more concerned about returning my system to the way it was.

---

### Post by running_rabbit07 on 2009-08-16
Sadly, it sounds like you will have to reinstall. 

What version of Ubuntu are you using?

What is you system specs?

---

### Post by hardtrance on 2009-08-16
I am running 64bit 9.04.  I guess reinstalling is not that big of a problem, just a huge time sink.  What is the best way to avoid this problem in the future?  What did I do wrong?  Why did my GRUB menu disappear?  

Thank you for your reply!

---

### Post by wojox on 2009-08-16
Put in the Live cd and boot from there. Look for /boot/grub/menu.lst
 see what it says.

---

### Post by raymondh on 2009-08-16
> **hardtrance said:**
> I am running 64bit 9.04.  I guess reinstalling is not that big of a problem, just a huge time sink.  What is the best way to avoid this problem in the future?  What did I do wrong?  Why did my GRUB menu disappear?  

Thank you for your reply!

As you seem ready to re-install .... have you tried to recover/reinstall GRUB?  If it works, you can then try to fix the upgrade/updating problem.

[http://ubuntuforums.org/showthread.php?t=224351&highlight=fsck](http://ubuntuforums.org/showthread.php?t=224351&highlight=fsck)

---

### Post by hardtrance on 2009-08-16
Great!  I will attempt booting from the live cd and playing fixing grub.  Thank you for the LiveCD option.  Thank you.  I will let everyone know how it go's.  

Thank you!

---

### Post by hardtrance on 2009-08-16
So here is the section of the /boot/grub/menu.lst that appears to deal with which items appear on the menu:
## ## End Default Options ##

title        Ubuntu 9.04, memtest86+
uuid        135db6d7-8954-4944-b834-3cdf83518e4d
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title        Windows XP Professional
rootnoverify    (hd1,0)
savedefault
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1

My hard drive that contains my linux system is at hd0,0.  I am going to hit google and see if I can determine what the entry I have to add will look like.  Right now I am thinking:

title Ubuntu
root (hd0,0)
kernel <somepath>

Thank you all for the help!

---

### Post by raymondh on 2009-08-16
> **hardtrance said:**
> So here is the section of the /boot/grub/menu.lst that appears to deal with which items appear on the menu:
## ## End Default Options ##

title        Ubuntu 9.04, memtest86+
uuid        135db6d7-8954-4944-b834-3cdf83518e4d
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST


My hard drive that contains my linux system is at hd0,0.  I am going to hit google and see if I can determine what the entry I have to add will look like.  Right now I am thinking:

title Ubuntu
root (hd0,0)
kernel <somepath>

Thank you all for the help!

Unless you edited the menu.lst as you posted, I don't see any kernels for you to boot into.  Here's what I mean :

```
## ## End Default Options ##

title		Ubuntu 9.04, kernel 2.6.28-14-generic
uuid		10e85b73-beb7-4239-aa09-9f764551a01c
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=10e85b73-beb7-4239-aa09-9f764551a01c ro quiet splash 
initrd		/boot/initrd.img-2.6.28-14-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
uuid		10e85b73-beb7-4239-aa09-9f764551a01c
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=10e85b73-beb7-4239-aa09-9f764551a01c ro  single
initrd		/boot/initrd.img-2.6.28-14-generic

title		Ubuntu 9.04, kernel 2.6.28-13-generic
uuid		10e85b73-beb7-4239-aa09-9f764551a01c
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=10e85b73-beb7-4239-aa09-9f764551a01c ro quiet splash 
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid		10e85b73-beb7-4239-aa09-9f764551a01c
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=10e85b73-beb7-4239-aa09-9f764551a01c ro  single
initrd		/boot/initrd.img-2.6.28-13-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		10e85b73-beb7-4239-aa09-9f764551a01c
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=10e85b73-beb7-4239-aa09-9f764551a01c ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		10e85b73-beb7-4239-aa09-9f764551a01c
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=10e85b73-beb7-4239-aa09-9f764551a01c ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		10e85b73-beb7-4239-aa09-9f764551a01c
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

If this were true, then indeed a re-install is looking much 'faster' to accomplish.  Unless someone can direct you on how to recover 'lost' kernels. Sorry.

---

### Post by Rocket2DMn on 2009-08-16
You shouldn't see any Partial Upgrades in a stable Ubuntu version.  Did you install using a pre-release LiveCD, like a beta version of 9.04?

---

### Post by hardtrance on 2009-08-16
I installed the (what I believed to be) stable 64bit ubuntu I downloaded from the ubuntu site.  I am currently running ubuntu through the live CD I installed from. I looked in the /boot directory and did not see any files at all.  I figure this signifies during the last upgrade that all of the boot images went missing.  Is it possible that some other boot loader was installed during upgrade?  It seems others have experienced this exact same issue in June. [http://ubuntuforums.org/archive/index.php/t-1183182.html](http://ubuntuforums.org/archive/index.php/t-1183182.html) 

Should I just scrap the install?  Or do should I stick with it and make it work (I tend to learn more by making it work.)  

Thank you for your time.

---

### Post by hardtrance on 2009-08-16
I guess the thing that is frustrating me the most is that the update package deleted all of the kernels in my /boot directory.  Why on earth would it do that?  I realize I must have told it too in some abstract way, but when software asks to update I tend to just say yes.  This is frustrating...

---

