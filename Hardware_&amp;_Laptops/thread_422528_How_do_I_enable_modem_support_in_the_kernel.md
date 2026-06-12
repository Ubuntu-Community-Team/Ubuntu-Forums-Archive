---
title: "How do I enable modem support in the kernel?"
date: 2007-04-25
forum: Hardware &amp; Laptops
---

### Post by motin on 2007-04-25
I have a HP Pavilion with apparently a not-to-be-found-working modem in Linux. Thought modem support was a no-no on this machine. 

Now, however I see on [http://gentoo-wiki.com/HARDWARE_Gentoo_on_HP_Pavilion_dv4000#Sound_.2F_Modem](http://gentoo-wiki.com/HARDWARE_Gentoo_on_HP_Pavilion_dv4000#Sound_.2F_Modem) that there is an option in the kernel configuration "Intel/SiS/nVidia/AMD MC97 Modem (EXPERIMENTAL)" to support the modem on this laptop! I guess it isn't enabled by default since it is marked as experimental... 

Can I compile and dynamically load some module for this or do you think I have to recompile the kernel totally? Pointers appreciated.

---

### Post by motin on 2007-07-17
*Bump* Somebody ought to have some experience on this - does anyone know?

---

### Post by stchman on 2007-07-17
> **motin said:**
> I have a HP Pavilion with apparently a not-to-be-found-working modem in Linux. Thought modem support was a no-no on this machine. 

Now, however I see on [http://gentoo-wiki.com/HARDWARE_Gentoo_on_HP_Pavilion_dv4000#Sound_.2F_Modem](http://gentoo-wiki.com/HARDWARE_Gentoo_on_HP_Pavilion_dv4000#Sound_.2F_Modem) that there is an option in the kernel configuration "Intel/SiS/nVidia/AMD MC97 Modem (EXPERIMENTAL)" to support the modem on this laptop! I guess it isn't enabled by default since it is marked as experimental... 

Can I compile and dynamically load some module for this or do you think I have to recompile the kernel totally? Pointers appreciated.

If you are talking of getting a modem for dialup working it will be difficult.  Most modems you buy are PCI based Winmodems.  Winmodems have very poor support under Linux.  My recommendation is to get a hardware modem.

---

### Post by BlueNoteExpress on 2007-07-17
Since this is a laptop he's talking about, it probably isn't feasible to replace the modem.  I'm afraid I can't help with enabling modem support in the kernel though.

---

### Post by motin on 2007-07-17
After some more research, it seems like following [https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto) (Get there after searching for "PCI Winmodems Ubuntu" after your remark stchman) seems to be my best shot at the moment. Thanks for the pointers!

---

### Post by stchman on 2007-07-17
There are 56K PCMCIA hardware modems that can be used.  You will need to disable the cr@ppy Winmodem in the BIOS.

[http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=1175065&Sku=Z165-1092](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=1175065&Sku=Z165-1092)

---

### Post by BlueNoteExpress on 2007-07-17
> **stchman said:**
> [COLOR="Red"]There are 56K PCMCIA hardware modems that can be used.[/COLOR]  You will need to disable the cr@ppy Winmodem in the BIOS.

[http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=1175065&Sku=Z165-1092](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=1175065&Sku=Z165-1092)

Yeah, I thought about that after I made my post.  If you can't get the onboard modem working, a PCMCIA modem might be the only option.

---

### Post by motin on 2007-07-17
My onboard modem is now working! I needed the Smartlink Modem driver. Unfortunately the process of compiling it was broken in Feisty, but now there is a ["Feisty special instructions" section in the wiki]("https://help.ubuntu.com/community/DialupModemHowto/Smartlink"). :)

Updated [https://wiki.ubuntu.com/LaptopTestingTeam/HPDV4000](https://wiki.ubuntu.com/LaptopTestingTeam/HPDV4000) as well.

Thanks for the input!

---

