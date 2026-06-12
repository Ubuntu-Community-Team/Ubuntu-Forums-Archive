---
title: "What is the easy way to install driver for 9800GTX ?"
date: 2008-08-14
forum: Hardware
---

### Post by Haber_Nir on 2008-08-14
hi .
i want to install drivers for my 9800 gtx card
but when i go system->admin->hadrdware driver its not detecting my card.
and when i go to add/remove software i see that they have nvidia drivers (but i assume that it 169, no?)
after that i go to synaptec and i see nvidia 173.14 envy drivers.
now what is envy drivers??
and why 173 isn't it default software??
in nvidia website 173.14 it is the latest stable drivers.soo why not?

---

### Post by 5l4y3r on 2008-08-15
As it is a relatively new graphics card I think you'll have to download the drivers from the nVidia web site:
[http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)

After downloading the .run file open a terminal session, go to the folder where the .run file is and execute the following command:
sudo sh ./name_of_the_nvidiafile.run

After doing this the installation should begin. When the installation is finished, restart the system and verify if that's all OK with the graphics.

---

