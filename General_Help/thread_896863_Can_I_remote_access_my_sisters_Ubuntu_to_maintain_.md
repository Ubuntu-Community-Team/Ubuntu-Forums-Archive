---
title: "Can I remote access my sisters Ubuntu to maintain it for her?"
date: 2008-08-21
forum: General Help
---

### Post by phil81uk on 2008-08-21
I don't live with my little sister and she frequently telephones me asking for help with her Ubuntu machine. I can probably SSH into it, but is there a way to access it, not using the command prompt, but into her desktop environment?

Do I need a special router for this? I understand that in windows you need a VPN capable router, set up a tunnel, and then remote desktop. I'm hoping that maybe Ubuntu doesn't require a special router!!

Thanks !!

---

### Post by WRDN on 2008-08-21
In Ubuntu, you can use VNC (Virtual Network). However, this is very insecure, so you should [tunnel the VNC Connection through SSH]("https://help.ubuntu.com/community/SSHHowto#Tunneling%20VNC%20connections%20through%20ssh") (this is much more secure, and allows you to view the PC in a window). You could also send X over SSH in the Terminal.

---

### Post by Peter09 on 2008-08-21
I have found the best way is to use a call-back on X11vnc, this means that X11vnc is not running anywhere until needed and only you will need to change your firewall settings, not your sister. This means that it is a lot more secure because your sisters machine is not open on a normal basis to VNC.

Basically, you issue the command - 

```
vncviewer -listen
```

then she issues the command

```
x11vnc -noxdamage -nowf -norc -notruecolour -connect <your IP> -bg
```

The best way of doing this is to create a launcher on her desktop called say 'Support'. She clicks on it and you will be able to see her desktop and be able to control her mouse.

I use this to support a couple of friends who I introduced to Ubuntu.

There is an how to on this, but I do not know the location.

If you have a firewall/router you will need to redirect the port 5500 to your machine.

PC

---

### Post by lintoon on 2008-08-21
Look into free nxserver.  It's more secure than vnc and very fast.

Here's an installation guide:

[http://michigantelephone.wordpress.com/2006/09/18/how-to-install-nx-server-and-client-under-ubuntukubuntu-linux-2/](http://michigantelephone.wordpress.com/2006/09/18/how-to-install-nx-server-and-client-under-ubuntukubuntu-linux-2/)

---

### Post by krunge on 2008-08-21
> **Peter09 said:**
> 

then she issues the command

```
x11vnc -noxdamage -nowf -norc -notruecolour -connect <your IP> -bg
```


The -notruecolor option is unnecessary (I think it only applies to some old SGI or SCO machines)

The -norc option is unnecessary unless she has created a ~/.x11vncrc file, which sounds unlikely from the description.

---

