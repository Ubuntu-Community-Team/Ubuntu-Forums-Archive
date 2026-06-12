---
title: "Grub Boot - XP/Vista"
date: 2009-05-25
forum: Hardware
---

### Post by Ravensound on 2009-05-25
Moving up to Hardy from Gutsy (don't ask why) with Vista on the Acer 3680 laptop, I noticed that the boot loader now correctly identifies the Vista loader drive, however, it also lists a second drive partition as Windows NT/2000/XP, without making it clear that this drive should only be booted to run restore which will erase all your windows personal stuff. There may be other machines around with similar disk layouts.

---

### Post by BiL0 on 2009-05-25
Hello,
Grub is identifying the (possibly hidden) partition but can't identify what it will do when you start it. That's impossible for any boot manager.
allot of companies now are hiding the recovery partition and sometimes to start the recovery you need to boot from cd or some kind of menu so that you can choose what kind of recovery you want.
sometimes the only recovery job is the one to re-image your partition with the original install. 
hope this helps
BiL0

---

### Post by Ravensound on 2009-05-25
I accept that the boot loader doesn't yet have intuition (who knows maybe one day?) but in the meantime perhaps it would help if some qualified advice was added to the splash page?

---

### Post by lindsay7 on 2009-05-25
If you want to get rid of this you can go into your grub menu,

type "sudo gedit /boot/grub/menu.lst"  in the terminal and delete the  lines that have to do with this restore option. Then just save the file.

---

### Post by coffeecat on 2009-05-25
> **Ravensound said:**
> I noticed that the boot loader now correctly identifies the Vista loader drive, however, it also lists a second drive partition as Windows NT/2000/XP, without making it clear that this drive should only be booted to run restore which will erase all your windows personal stuff. There may be other machines around with similar disk layouts.

When I installed Jaunty to this Sony Vaio laptop, it setup grub entries for both Vista on sda2 and the restore partition on sda1. I don't know about an Acer restore, but with a Sony one, if you boot into it by mistake it's not the end of the world because a 'cancel' causes a reboot with no harm done. In fact I was quite pleased - it gave me another way of getting into the restore utility should I need it. I simply changed the title line in the grub menu so it was clear what it was.

> **Ravensound said:**
> I accept that the boot loader doesn't yet have intuition (who knows maybe one day?) but in the meantime perhaps it would help if some qualified advice was added to the splash page?

But you make a good point. It would be an easy mistake to boot into the restore utility and start the restore utility going, especially for an inexperienced user. If you feel strongly about it, perhaps you could file a bug report on launchpad, which is where the Ubuntu devs will notice this. They are unlikely to here. 

> **Ravensound said:**
> Moving up to Hardy from Gutsy (don't ask why)

All right. Why? :p

---

### Post by Ravensound on 2009-05-27
Thanks for the advice re deleting the grub entry line - I forgot about that, originally, with Gutsy I had a real problem as the only entry was the restore boot!

Re the upgrade - how long have you got?  I had a lot of fun getting various bits of this laptop to work and was trying to avoid doing any upgrades - unfortunately I couldn't resist trying out a few streamer sources and eventually the inevitable happened...  I had noticed a few error messages on the software update side re the archives as well.  I reloaded Gutsy and upgraded to Hardy and so far everything works except for xmms which crashed when I tried to double-size it.

---

