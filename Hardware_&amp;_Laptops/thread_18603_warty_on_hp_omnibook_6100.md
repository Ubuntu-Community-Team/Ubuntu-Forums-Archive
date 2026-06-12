---
title: "warty on hp omnibook 6100"
date: 2005-03-07
forum: Hardware &amp; Laptops
---

### Post by antimatter on 2005-03-07
Hi!
Ubuntus running really good on this laptop. the only thing that bugs me, is that acpi is not working. when i first tried to install ubuntu it would crash when loading the kernel. i deactivated acpi and then it worked fine. after i got everything working i modified the grub menu and added acpi back in but it would crash when loading the kernel. any way to get acpi working? (the volume buttons on the side arent working either, but thats another story i guess)

i cant even switch the laptop off properly in this state. i have to either unplug it/remove the battery or press the reset button with a sharp pencil. (doing this after computer - log out - shutdown of course) 

any help would be appreciated!  :-?

---

### Post by lucan on 2005-03-10
hi,
i have the same problem with my laptop too. but after i upgrade my bios, the battery work and shut down just like windows. try upgrading your laptop BIOS.

[compaq problem](http://ubuntuforums.org/showthread.php?t=17328)

---

### Post by ph00dz on 2005-03-10
I had the exact same problem with an HP Pavilion ze4560... but now it works.

I added the appropriate kernel module for my processor... just like this person: [http://ubuntuforums.org/showthread.php?t=3267](http://ubuntuforums.org/showthread.php?t=3267)

With that done, acpi works. I boot up with: acpi=on loapic nolapic

---

### Post by antimatter on 2005-03-12
hi!

almost solved this problem. first i added the apm module to /etc/modules. then set the kernel to boot with acpi=off apm=off. now it shows me the battery state and stuff like that(which it didnt before). when shutting down now. it switches everything off but its still on somehow. the green lights on and i cant switch it on anymore. this means i still have to press the off button with a pencil. think it goes into hibernation mode? help?

---

