---
title: "Unknown Telnet"
date: 2008-10-30
forum: General Help
---

### Post by belaviyo on 2008-10-30
Hi

I have a telnet program which only support standard commands(Ascii control codes)(without color,...), But it does not send its supporting type to server

is there any way to send some command manually to server(after login) to tell it that telnet program support which type of screen ?

P.S: I cant use any other telnet softwares like putty,.. :)

---

### Post by cariboo on 2008-10-30
If you install openssh-server on the server then you can use ssh. Telnet is not a safe service to use, especially if you server is facing the internet.

Jim

---

