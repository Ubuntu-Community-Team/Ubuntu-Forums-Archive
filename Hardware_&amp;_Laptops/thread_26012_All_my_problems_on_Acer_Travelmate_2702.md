---
title: "All my problems on Acer Travelmate 2702"
date: 2005-04-11
forum: Hardware &amp; Laptops
---

### Post by Eleka on 2005-04-11
Hi people!

I have installed Ubuntu Hoary today and I have problems with the soundcar, wireless integrated card and I think that the graphics card is not run properly, and I'm not sure. I don't post the lspci result because I'm under Windows (in ubuntu I don't have internet).

My devices are (its name under Win):
Realtek AC'97 Audio
acer IPN2220 Wireless Lan Card
MOBILITY RADEON 9000/9100 IGP

---

### Post by Thomas the fish guy on 2005-04-13
Hi, I have a similar problem with my laptop, it seems that software modems are the issue with Ubuntu on some laptops...there is a rather complicated text command line in the" Howto" section...if you try there it may help.  Cheers Thomas

---

### Post by Eleka on 2005-04-14
Thank you

Can you say me the url of this howto? I don't know where start to search ...

---

### Post by kaiise on 2005-07-06
just sue the search button.

and type the problem description its very easy.


my problme is that on this particular model i purchased ofr my mother,

hibernate and rebppt just hang.

---

### Post by dorris on 2005-07-06
any specific launch option used?
ie to get it to boot, are you using any switches, such as acpi=off, noapic, pci=noacpi ??

have you tries installing the wireless drivers? (ipw2200, search the forums for help)

does graphics pop up at all, or do you get black screen in place of X?

checked acpi.sourceforge.net for a dsdt table for your laptop?

---

### Post by kaiise on 2005-07-07
um i havent installed wireless drivers and x works fine. the ac97 worked after i followed forum instructions...
i am not using any of those kernel options and i have alresdy chekced that site and a new dsdt for the old bios is there but i have 1.09 as well as the fact that i also have th old dsdt i need the newer one. i may play with deocmipleing the dsdt form the kernel.
and try doing a diff.


i haven installed wirless drivers as i have no way of testing whthere they work.
no wireless here.
so it is not high on my list.



thanks ofr the reply

---

