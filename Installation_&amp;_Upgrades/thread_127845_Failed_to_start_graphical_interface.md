---
title: "Failed to start graphical interface"
date: 2006-02-09
forum: Installation &amp; Upgrades
---

### Post by dspring on 2006-02-09
Hi, I'm here for help of course. Very new to Linux. For starters I couldn't get the live install dvd to boot in live mode so I trashed windoze and partitioned the hard drive for all plus swap, reinstalled windoze and my software. Started the Ubuntu dvd install and all went well until it tried to boot first time. It got to the login and tried it a couple times but I had no time to log in as it went to a screen telling me FAILED TO START X SERVER GRAPHICAL INTERFACE. I know what it is, but the windows I viewed for info really didn't give a good explanation other than to fix the problem and restart the GDM. Is this a module? Anyway I could log in but I know not where to look or what commands to enter to do a fix. ANYONE help with this or steer me to the info? 

My system is a HP/Compaq nx9600/3.2ghz/1g ram/80ghd/ATI X600,128megmem/Broadcom Wifi....may need some help with wifi later?

I really want to slip away from windoze, help would be greatly appreciated from all replying!!

Thanks, David.

---

### Post by jason.b.c on 2006-02-10
did you say that you can log in ?, so then the system runs?  I read somewhere in here ( and i hope i've got this right ) from the terminal your supposed to type edit/etc/default/rcs
and then 
fxck fix =yes

i hope this helps you at all , and like i said i hope i'm right about that that!:o

---

### Post by dspring on 2006-02-10
[QUOTE=jason.b.c]did you say that you can log in ?, so then the system runs?  I read somewhere in here ( and i hope i've got this right ) from the terminal your supposed to type edit/etc/default/rcs
and then 
fxck fix =yes

i hope this helps you at all , and like i said i hope i'm right about that that!:o[/QUOTE]


Yes I can log in. I tried what you said but without any change, maybe I did it wrong. What is the proper way to get the terminal up after login just to be sure I'm doing this correctly? Is there somewhere else I should try to get help? Hardly  any of the live cd/dvds that I got would even work for me to try. The only other installer I have is Gentoo and it is more complicated to get running for me right now, maybe later, so I tried the Ubuntu. Disappointed you can't get a basic system running easily. Oh well keep trying I guess.
David

---

### Post by dspring on 2006-02-11
FIXED !!! Got this problem fixed!!
I believe I went into verbose before it booted and must have detected the ati board which seemed to be the problem. It has it as generic now, but I don't know if any accelleration of 3D is there though. Maybe need some help with that too.
Now onto modem and wireless!
david

---

