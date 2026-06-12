---
title: "Migrating from ATI to Nvidia"
date: 2006-11-18
forum: Hardware &amp; Laptops
---

### Post by KnevetS on 2006-11-18
I really don't like the 1024x768 restriction for beryl and my ATI card, so I went out and picked up an Nvidia card.  Now I'm looking for a safe way to upgrade.  In Windows, I'm downgrading my display drivers to vga and then I'll stick the new card in there. 

In ubuntu, I assume I need to change settings in xorg.conf to remove the ATI driver.  Is there a sample config file for basic vga access so when I switch cards I can get into ubuntu without a problem?

---

### Post by David Corrales on 2006-11-19
Just look for the section called *Driver* and change the line *[I]ati, radeon *or* fglrx*[/I] to **vesa**. That's a generic driver which will allow you to switch the card without problems. Once it's in, you can install the nvidia drivers :)

---

### Post by KnevetS on 2006-11-19
thanks.  Up and running beryl at a reasonable resolution now. 

I appreciate the help.

---

