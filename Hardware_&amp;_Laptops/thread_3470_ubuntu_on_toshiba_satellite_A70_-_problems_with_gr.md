---
title: "ubuntu on toshiba satellite A70 - problems with graphics ATI card and sound cards"
date: 2004-11-06
forum: Hardware &amp; Laptops
---

### Post by duboz on 2004-11-06
Hi,

i am a newbie with ubuntu but i enjoy using it. Nevertheless, I have some trouble with my sound and graphics cards that drivers are not found... so no games and no music... ](*,) , that is sad no ?
Is sombody can help me ?

thanks,

Raph

---

### Post by humberto on 2004-11-06
[QUOTE=duboz]
I have some trouble with my sound and graphics cards that drivers are not found... so no games and no music... 
[/QUOTE]

We need more information. What graphics card and sound card does the machine have. You may get some of this information from the lspci command.

Also, information on specific hardware may be found on the ubuntu wiki:

Laptops: [http://www.ubuntulinux.org/wiki/HardwareSupportMachinesLaptops](http://www.ubuntulinux.org/wiki/HardwareSupportMachinesLaptops)

Video Cards: [http://www.ubuntulinux.org/wiki/HardwareSupportComponentsVideoCards](http://www.ubuntulinux.org/wiki/HardwareSupportComponentsVideoCards)

Audio: [http://www.ubuntulinux.org/wiki/HardwareSupportComponentsSoundCards](http://www.ubuntulinux.org/wiki/HardwareSupportComponentsSoundCards)

Good luck.

Humberto

---

### Post by duboz on 2004-11-19
[QUOTE=humberto]We need more information. What graphics card and sound card does the machine have. You may get some of this information from the lspci command.

Also, information on specific hardware may be found on the ubuntu wiki:

Laptops: [http://www.ubuntulinux.org/wiki/HardwareSupportMachinesLaptops](http://www.ubuntulinux.org/wiki/HardwareSupportMachinesLaptops)

Video Cards: [http://www.ubuntulinux.org/wiki/HardwareSupportComponentsVideoCards](http://www.ubuntulinux.org/wiki/HardwareSupportComponentsVideoCards)

Audio: [http://www.ubuntulinux.org/wiki/HardwareSupportComponentsSoundCards](http://www.ubuntulinux.org/wiki/HardwareSupportComponentsSoundCards)

Good luck.

Humberto[/QUOTE]


the graphic card is an ATI mobility radeon 9000
I can't see it in the list of aviable driver on the unbuntu site ??

Thanks for your help

---

### Post by humberto on 2004-11-24
[QUOTE=duboz]the graphic card is an ATI mobility radeon 9000
I can't see it in the list of aviable driver on the unbuntu site ??
[/QUOTE]

What does lspci say? My laptop has:

```

0000:00:14.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M6 LY

```

Ubuntu just works, with the radeon module. Man radeon says the Radeon 9000 should be supported as well.

Look in ```
/var/log/XFree86.0.log
``` to see if there are any errors.

---

### Post by SwordAngel on 2005-10-13
duboz, how did you manage to install Ubuntu in the first place? When I boot up from the Ubuntu installation CD on my Toshiba Satellite A70, I get a black screen after the loading of some components. I can't even start the installation process.

---

### Post by Elv13 on 2005-11-13
it say:
"ATI Technologies, Inc. Radeon Mobility 9100 U3 (R200 IGP)"
i have the same laptop and the same problem
sound:
ati xp150, the driver work

---

### Post by rdario on 2005-11-14
[QUOTE=SwordAngel]duboz, how did you manage to install Ubuntu in the first place? When I boot up from the Ubuntu installation CD on my Toshiba Satellite A70, I get a black screen after the loading of some components. I can't even start the installation process.[/QUOTE]

use this option when boot:
vga=771

---

