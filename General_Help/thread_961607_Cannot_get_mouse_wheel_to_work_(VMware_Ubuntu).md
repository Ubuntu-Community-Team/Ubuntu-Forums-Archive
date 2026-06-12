---
title: "Cannot get mouse wheel to work (VMware Ubuntu)"
date: 2008-10-28
forum: General Help
---

### Post by Konichiwa on 2008-10-28
Hey all,

   I wanted to give linux a whirl and a friend of mine recommended ubuntu. I decided to run it as a virtual pc via vmware and I created the vmware image with no issues, ubuntu is running fine.

I am having some problems with my peripherals though, one of them being I am unable to get my middle mouse wheel to scroll up and down and my back and forward buttons on my Logitech MX518 mouse do not function.

I have a Virtual PC of Back Track 3 which is a form of linux I belive and my mouse scroll works in that, but not ubuntu.

I have try the suggestions in these threads but to no avail, I have been searching through the forums for a few hours now and cannot seem to find anything that works, and again, middle mouse scroll to works with other linux virtual pcs.

[http://ubuntuforums.org/showthread.php?t=938487](http://ubuntuforums.org/showthread.php?t=938487)

[http://ubuntuforums.org/showthread.php?t=65471&highlight=MX500](http://ubuntuforums.org/showthread.php?t=65471&highlight=MX500)

Does anyone have clues?

-Thanks

---

### Post by crazyfearme on 2010-01-02
**Rueda del Mouse no funciona BT3 - Ubuntu - Vmware**
**------------------------------------------------------------------------------------**
Parece que nadie ha respondido a este post, y la solución es muy simple:
1.- ir a /etc/x11
2.- Abrir el archivo xorg.conf
3.- Cambiar la línea:
**Option "Protocol" "ps/2"**
por la siguiente:
**Option "Protocol" "ImPS/2"**
4.- Salvar los cambios!!!! y reiniciar la máquina virtual.
5.- La rueda del mouse debe quedar activada.
Saludos!!
Fear
-----------------------------------------------------------------------------------------------------
It seems that nobody has responded to this post, and the solution is very simple: 
1 .- go to /etc/X11
2 .- Open the xorg.conf file
3 .- Change the line:
**Option "Protocol" "ps/2"**
to the following:
**Option ****"Protocol" "ImPS/2"**
4 .- Save the changes!! and restart the virtual machine.
5 .- The mouse wheel must be enabled.
Best regards!!
Fear

---

