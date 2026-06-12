---
title: "HOW TO solve the SD Card reader Problem on ACER ONE with UBUNTU KARMIC-KOALA"
date: 2010-02-04
forum: Hardware
---

### Post by hallucinogen on 2010-02-04
[SIZE=5][COLOR=Red]**VERSION EN ESPAÑOL AL FINAL!!!!!**[/COLOR]

Hi my dears ubuntuleros friends I'm from México and I had problems to mount a SD Card on ubuntu karmic-koala, when I tried to insert a SD Card media the system didn't recognize and did nothing I had the same problem on jaunty-jackalope but it had solved when I modified the menu.lst file this is different on karmic because there doesn't have this file. Karmic use the new GRUB2 version and somethings has changed.

Well, now the solution!!!!

- First step: To open a new console window (using ALT+F2 or go to Accesories-Terminal).

- In the console write "sudo gedit /etc/default/grub" (without the quotation marks) then the system asks for the SUPERUSER's password. 

-After that, will open a new gedit's window, here you need to looking for the next line:[/SIZE][SIZE=4][COLOR=Red]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
[SIZE=5][COLOR=Black]and modify this by this one:
[/COLOR][/SIZE][/COLOR][/SIZE][SIZE=4][COLOR=Red]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pciehp.pciehp_force=1"
[COLOR=Black][SIZE=5]save the changes and close the window.

-In the command line write "sudo update-grub". Wait until the process will finish and restart your computer.

This method has worked me when I insert a micro sd card with an adapter, I tested with a 512 MB, 2 GB and 8 GB SDHC cards. 

I hope this little "HOW TO" could help someone.  See you next friends!!!!

ENJOY THE FREE SOFTWARE!!!! :twisted:

OBVIAMENTE DEBE HABER LA **[COLOR=Red]VERSION EN ESPAÑOL[/COLOR]** DE ESTE "HOW TO" para ayudar a mis compañeros paisanos latinos:

[/SIZE][/COLOR][/COLOR][/SIZE]Ke tal mis amigos PAISANOS DE MEXICO, tengo un poco de tiempo usando UBUNTU lo utilizo desde Jaunty/Jakalope y he instalado desde cero Karmic-koala (9.1) y he notado que tiene algunas fallas al utilizar las SD Card en la muy popular ACER ONE que googleando por mucho tiempo no habia podido solucionar puesto que ahora esta nueva version incluye la version beta del GRUB2, hay muchas soluciones que indican modificar el archivo menu.lst que ahora ya no se encuentra presente en el nuevo GRUB...Perooooo tomando en cuenta esas soluciones las he analogado al nuevo GRUB y llegue a esta solucion: [IMG]http://ba-k.com/images/smilies/bakitas/chamucow.gif[/IMG]

- Primero abrimos la terminal que se encuentra en Accesorios.
- Despues tecleamos: sudo gedit /etc/default/grub y nos pedira una contraseña que hemos (o no) puesto al instalar el SO.
- Nos abrira una ventana nueva donde aparecera el contenido del GRUB.cfg el cual modificaremos como sigue.

- Dentro de la ventana del gedit buscamos una linea como esta:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
y la modificamos de la siguiente manera:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pciehp.pciehp_force=1"

- Guardamos los cambios y cerramos gedit.
- Posteriormente en la terminal escribimos: sudo update-grub
- Esperamos a que el proceso termine y reiniciamos el equipo.

Con eso al reiniciar ya nos reconocera en ambos lectores las memorias insertadas!!!! Lo he probado con una memoria micro SD de 512 MB, una de 2 GB y una micro SDHC de 8 GB con un adaptador y TOOOODAS funcionan a la perfeccion.

Espero que les quite el dolor de cabeza a muchos y sigamos felices y contentos como hasta ahora lo hemos estado haciendo con el software libre!!!!!!

CUALQUIER DUDA LA CONTESTARE A LA BREVEDAD...[IMG]http://ba-k.com/images/smilies/bakitas/metal.gif[/IMG] 
[SIZE=4][COLOR=Red][COLOR=Black][SIZE=5]
  [/SIZE][/COLOR][/COLOR][/SIZE]

---

### Post by rock.it on 2010-02-07
Hi,

Your post helped me a lot!! But I still have one problem, my PC have two slots for cards, one is the SD card and the another one is for Sony MS Pro Duo.

With the change in the grub file the SD Card reader is working, but the MS Pro Duo reader is still not working...

Do you have any idea why??

Thanks!!

rock.it

---

### Post by kermit2435 on 2010-05-11
[
Hi,  thanks for that, I don't know how, but it works Ubuntu should include it on their next release there are lots of us out here with SD slots in our Netbooks.  Thanks again Kevin:P:guitar:
QUOTE=hallucinogen;8774147][SIZE=5][COLOR=Red]**VERSION EN ESPAÑOL AL FINAL!!!!!**[/COLOR]

Hi my dears ubuntuleros friends I'm from México and I had problems to mount a SD Card on ubuntu karmic-koala, when I tried to insert a SD Card media the system didn't recognize and did nothing I had the same problem on jaunty-jackalope but it had solved when I modified the menu.lst file this is different on karmic because there doesn't have this file. Karmic use the new GRUB2 version and somethings has changed.

Well, now the solution!!!!

- First step: To open a new console window (using ALT+F2 or go to Accesories-Terminal).

- In the console write "sudo gedit /etc/default/grub" (without the quotation marks) then the system asks for the SUPERUSER's password. 

-After that, will open a new gedit's window, here you need to looking for the next line:[/SIZE][SIZE=4][COLOR=Red]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
[SIZE=5][COLOR=Black]and modify this by this one:
[/COLOR][/SIZE][/COLOR][/SIZE][SIZE=4][COLOR=Red]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pciehp.pciehp_force=1"
[COLOR=Black][SIZE=5]save the changes and close the window.

-In the command line write "sudo update-grub". Wait until the process will finish and restart your computer.

This method has worked me when I insert a micro sd card with an adapter, I tested with a 512 MB, 2 GB and 8 GB SDHC cards. 

I hope this little "HOW TO" could help someone.  See you next friends!!!!

ENJOY THE FREE SOFTWARE!!!! :twisted:

OBVIAMENTE DEBE HABER LA **[COLOR=Red]VERSION EN ESPAÑOL[/COLOR]** DE ESTE "HOW TO" para ayudar a mis compañeros paisanos latinos:

[/SIZE][/COLOR][/COLOR][/SIZE]Ke tal mis amigos PAISANOS DE MEXICO, tengo un poco de tiempo usando UBUNTU lo utilizo desde Jaunty/Jakalope y he instalado desde cero Karmic-koala (9.1) y he notado que tiene algunas fallas al utilizar las SD Card en la muy popular ACER ONE que googleando por mucho tiempo no habia podido solucionar puesto que ahora esta nueva version incluye la version beta del GRUB2, hay muchas soluciones que indican modificar el archivo menu.lst que ahora ya no se encuentra presente en el nuevo GRUB...Perooooo tomando en cuenta esas soluciones las he analogado al nuevo GRUB y llegue a esta solucion: [IMG]http://ba-k.com/images/smilies/bakitas/chamucow.gif[/IMG]

- Primero abrimos la terminal que se encuentra en Accesorios.
- Despues tecleamos: sudo gedit /etc/default/grub y nos pedira una contraseña que hemos (o no) puesto al instalar el SO.
- Nos abrira una ventana nueva donde aparecera el contenido del GRUB.cfg el cual modificaremos como sigue.

- Dentro de la ventana del gedit buscamos una linea como esta:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
y la modificamos de la siguiente manera:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pciehp.pciehp_force=1"

- Guardamos los cambios y cerramos gedit.
- Posteriormente en la terminal escribimos: sudo update-grub
- Esperamos a que el proceso termine y reiniciamos el equipo.

Con eso al reiniciar ya nos reconocera en ambos lectores las memorias insertadas!!!! Lo he probado con una memoria micro SD de 512 MB, una de 2 GB y una micro SDHC de 8 GB con un adaptador y TOOOODAS funcionan a la perfeccion.

Espero que les quite el dolor de cabeza a muchos y sigamos felices y contentos como hasta ahora lo hemos estado haciendo con el software libre!!!!!!

CUALQUIER DUDA LA CONTESTARE A LA BREVEDAD...[IMG]http://ba-k.com/images/smilies/bakitas/metal.gif[/IMG] 
[SIZE=4][COLOR=Red][COLOR=Black][SIZE=5]
  [/SIZE][/COLOR][/COLOR][/SIZE][/QUOTE]

---

