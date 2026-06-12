---
title: "Wifi Asus VivoBook S400CA"
date: 2013-08-14
forum: Hardware
---

### Post by aledruetta on 2013-08-14
Hola Comunidad!

Compré un ultrabook Asus S400CA (VivoBook), saqué el Win8 que traía de fábrica e insalé Ubuntu 13.04. Anda todo muy bien, incluso la pantalla touch, pero la señal del wifi es muy débil y fluctuante, no me puedo alejar mucho del router en casa, y en el trabajo directamente quedo offline.
Googleando encontré que es un bug que ya fue notificado:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1160188](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1160188)
En la página de Launchpad aparece un procedimiento para intentar resolver el problema. Lo probé, algo mejora, pero no resuelve. A 2 metros del router tengo buena señal donde antes tenía apenas dos rayitas, pero si me alejo a 5 metros ya no capta nada.
Bueno, la consulta es por si alguien tiene más información al respecto y se le ocurre alguna solución.

Gracias!

[HTML][COLOR=#333333][FONT=Ubuntu Mono]Gerry and others: I'll try to give instructions that don't "skip" any steps, hopefully it'll help. Steps 2-7 are commands you should just copy paste in terminal.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]1. Open Dash and search for Terminal and open it
2. wget https://www.kernel.org/pub/linux/kernel/projects/backports/2013/06/18/backports-20130618.tar.xz
3. tar xvf backports-20130618.tar.xz
4. cd backports-20130618
5. make defconfig-ath9k
6. make
7. sudo make install
8. (insert your password when sudo asks it).
9. Ready! Reboot the computer.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]The new drivers should then be in use, but note you will need to do the steps 4-7 again if a Linux kernel update comes as a security update or otherwise.[/FONT][/COLOR]
[/HTML]

---

### Post by Jerome_Rosset on 2013-08-16
Works perfectly for me, dont forget to blacklist/remove/delete all your ndisgtk, ndiswrapper previous installations...

---

### Post by brucedunn on 2013-10-25
I had Ubuntu 13.04 installed on an S400CA, and it had the WiFi problem, solveable only by applying the patch noted above.  After upgrading to 13.10, the problems seems to have been permanently solved.

---

