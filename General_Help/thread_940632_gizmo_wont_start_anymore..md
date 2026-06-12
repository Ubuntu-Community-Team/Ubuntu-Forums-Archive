---
title: "gizmo wont start anymore."
date: 2008-10-07
forum: General Help
---

### Post by go_dragons on 2008-10-07
I installed gizmo5 a while back to replace my skype client. I really love how it integrates the phone with my msn instant messenger. Because of it I have been able to remove both skype and pidgin from my computer and I am much happier!

Lately however, I have encountered a problem. I wish I could pinpoint exactly what I did to cause the problem but I really have no idea. In any case here are the symptoms. When I click on the gizmo icon in the menu's nothing happens. When I open a terminal and type gizmo -d it gives me the following error:

bash-3.2$ gizmo -d
Debug: gizmo_app_version_string: LinGizmo
Error: gizmo_ipc_send_command: .ipc_fifo file does not exist


I have looked on google but I have so far been unable to determine what this file is or where it is apparently supposed to be. If I su to root I am able to open the program as root so at first I thought I might be missing a file from within my own home directory. I moved the .gizmo directory at the base of my home directory to another location but when I tried to open gizmo again it just recreated the directory and I still had the same problem.

does anyone know what this file is or what I need to do to fix this?

---

### Post by go_dragons on 2008-10-07
bump. Does anybody know what this file does?

---

