---
title: "Input Method don't work when using X11Forward"
date: 2008-09-08
forum: General Help
---

### Post by breaddawson on 2008-09-08
I'm using Ubuntu 8.04 and SCIM because i need to type Chinese

I set up X11Forwarding when i ssh to another computer which is running rhel3
everything is fine but i found that i can not use input method in the apps which was running on the remote ssh server.

For example, i was running gedit by type 
$ gedit &
after i log in the remote server using ssh
then i can see the gedit window, type words into it
But when i want to type Chinese, Ctrl+Space does not work which will certainly call SCIM out.

Has someone encountered this problem? Help!!

---

### Post by regala on 2008-09-08
> **breaddawson said:**
> I'm using Ubuntu 8.04 and SCIM because i need to type Chinese

I set up X11Forwarding when i ssh to another computer which is running rhel3
everything is fine but i found that i can not use input method in the apps which was running on the remote ssh server.

For example, i was running gedit by type 
$ gedit &
after i log in the remote server using ssh
then i can see the gedit window, type words into it
But when i want to type Chinese, Ctrl+Space does not work which will certainly call SCIM out.

Has someone encountered this problem? Help!!

This is not a problem. It is the expected behaviour. Your using SCIM is configured on the local machine. you have to setup scim on the remote machine: apps detect when to use scim by use of environment variables, or so. Environment is generally local. You have to setup the remote shell with the same environment variables and make sure scim is installed remotely. X11Forwarding is no more than a specific tcp tunnel setup between two machines, no more, no less.

---

### Post by breaddawson on 2008-09-08
thank u for ur reply.
I don't have privileges to install softwares on the server, so i need to do testing on another computer later.

---

