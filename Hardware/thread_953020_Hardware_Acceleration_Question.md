---
title: "Hardware Acceleration Question"
date: 2008-10-19
forum: Hardware
---

### Post by riodemes on 2008-10-19
Hello,

I recently have been having trouble with setting compiz, and playing games. I got compiz working (I have no idea how) but the games do not work. 

When I started Enemy Territory in terminal, however, I saw this:

 You are using software Mesa (no hardware acceleration)!   
 Driver DLL used: libGL.so.1
 If this is intentional, add
       "+set r_allowSoftwareGL 1"
 to the command line when starting the game.

I have a x3100 integrated graphics thing on my Acer Extensa 5620-4025. How do i switch to something that is 3d acceleration via hardware and not software so I can play open arena and enemy territory again?

---

### Post by cariboo on 2008-10-19
What happens when you add the following:

> +set r_allowSoftwareGL 1

to the command line when starting the game, like the error suggested?

Jim

---

### Post by riodemes on 2008-10-19
it starts the game, but plays extremely slow because the graphics are being done through a software acceleration method (mesa). I just don't know how to enable hardware acceleration of graphics for my intel x3100

---

### Post by linux newbie2 on 2009-07-02
go to system>administration>hardware drivers

click the latest version, then click activate.


you should be done


linux newbie2):P

---

### Post by yunone on 2009-09-06
> **linux newbie2 said:**
> go to system>administration>hardware drivers

click the latest version, then click activate.


you should be done


linux newbie2):P

thanks newbie....fixed my poor performance issue

---

