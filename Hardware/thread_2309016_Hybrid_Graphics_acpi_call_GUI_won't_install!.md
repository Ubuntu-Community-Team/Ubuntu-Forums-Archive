---
title: "Hybrid Graphics: acpi_call_GUI won't install!"
date: 2016-01-07
forum: Hardware
---

### Post by Leinatan on 2016-01-07
Hello,

I'm pretty new to Ubuntu, I installed version 14.04 LTS last week on my laptop ([HP pavilion DV6-i7]("http://support.hp.com/de-de/document/c03074587")), after getting sick of that crappy windows 10, and I'm having some issues with the dual GPU's, The integrated graphic card is Intel HD Graphics and the discrete  is AMD Radeon HD 6770m. After doing some research, i found this page ( [https://help.ubuntu.com/community/HybridGraphics#Fix_fans_running_at_full_speed](https://help.ubuntu.com/community/HybridGraphics#Fix_fans_running_at_full_speed) ) and I tried both the switcheroo method and the [acpi_call with GUI]("http://marcodallas.github.io/acpi_call_GUI/"), but neither of them worked.

I've downloaded the acpi_call_GUI and followed the i[nstructions]("https://www.youtube.com/watch?v=h33bvoR14x8") but it won't install successfully. At first I had some issues with some #Include stuff (which I really don't understand) on the acpi_call.c file and I kind of fixed it following [this advice]("https://github.com/mkottman/acpi_call/issues/51") (I had the same problem) and adding a line ('#define BUILDING_ACPICA') in the file . I said kind of fixed it because it's still not working. When I try to install I get this message from the log: 

fatal: le chemin de destination '/usr/local/bin/acpi_call' existe déjà et n'est pas un répertoire vide. * (It's in french, it says: "fatal: destination path '..' already exists and is not an empty repertory")*
make -C /lib/modules/3.19.0-43-generic/build M=/usr/local/bin/acpi_call modules
make[1]: entrant dans le répertoire « /usr/src/linux-headers-3.19.0-43-generic » *(make[1]: Entering in repertory ...)*
  Building modules, stage 2.
  MODPOST 1 modules
make[1]: quittant le répertoire « /usr/src/linux-headers-3.19.0-43-generic » *(Leaving ...)*
insmod: ERROR: could not insert module acpi_call.ko: File exists
Process Complete.

So the problem seems to be that the previous unsuccessful installations created some repertories and now it's confusing the installation script. Since I'm really not knowing what I'm doing and I probably shouldn't be playing around too much with hardware I'm asking for your help, if anyone can help! :D Would be great!

If it's not fixable, how do I uninstall acpi_call_GUI ?

Thanks a lot

[EDIT:] Also, if I try to deactivate discrete GPU i get this message: AE_not_found, anyone knows what this means?

---

