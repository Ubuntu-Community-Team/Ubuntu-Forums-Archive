---
title: "Command lines loading?"
date: 2008-11-26
forum: General Help
---

### Post by 123456789mike on 2008-11-26
Well, I don't quite know what is wrong.
I already had a Dual Boot system... I had Vista and XP installed and it loaded from Windows Boot manager.

Now,  installed Ubuntu 8.10, and I have the GRUB. When I first start up the computer, it is BIOS by the way, it gives me the options of 3 Ubuntu uhm things, Vista/Longhorn, and Older components, sorry I can't remember what that string was.

So, I chose Vista/Longhorn, it gives me the option of Vista, XP, and Ubuntu. Then, I chose XP, it gave me the option of Ubuntu or XP.
I thought that was quite strange, but that isn't really the problem, it is just somewhat inconvenient.

Well, my problem is, whenever I chose the the Ubuntu from the Vista option(Vista, XP, or Ubuntu) well I think this happens to each Ubuntu option, BUT... Ubuntu will do the standard load screen, the orange bar bouncing back and forth through the black bar with the Ubuntu title... After this has finished loading, it shows a typical BIOS screen with a flashing _ for a few seconds.
Then it loads into command lines. Before, I could boot up Ubuntu fine and enter my username/password. I have had to hardboot everytime the command lines come up. 

Well, thanks, help is MUCH appreciated.

---

### Post by cdtech on 2008-11-26
Which option are you aiming for? Boot the Windows for a menu option or boot Ubuntu for a menu option? When you installed Ubuntu it took over your MBR of the primary drive and you had Windows setup with a boot option menu itself.

You would need to change the Windows boot menu to boot only that particular Windows OS, then reinstall grub from a Live CD to the primary drives MBR, if you wanted the bootloader as GRUB.

You'll probably also need to reconfigure the &#8220;/boot/grub/menu.lst&#8221; after which, to tell GRUB where the Windows drives are (device configuration).

Let us know which way you want it.........

---

### Post by 123456789mike on 2008-11-26
Oh my gosh. Thank you so much, I just understood haha.

---

