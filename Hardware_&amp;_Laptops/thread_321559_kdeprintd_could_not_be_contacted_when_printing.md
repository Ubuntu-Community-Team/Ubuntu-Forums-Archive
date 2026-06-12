---
title: "kdeprintd could not be contacted when printing"
date: 2006-12-19
forum: Hardware &amp; Laptops
---

### Post by kirys on 2006-12-19
It seems that often after printing using the multiple page for sheet option, kdeprind crashes and if i try to print i get "kdeprintd could not be contacted".
The driver is the foo2zjs i downloaded from foo2zjs website and the printer is hp lj1022.
Is there a problem with foo2zjs and kubuntu (i use 6.06), any way to solve that?.
How can i restart kdeprintd without restarting x?
Thank You
Kirys

---

### Post by kirys on 2006-12-26
is there noone that have my same problem?:confused:

---

### Post by GNUAXE on 2007-12-08
> **kirys said:**
> is there noone that have my same problem?:confused:
I was getting a "kdeprintd" error (can't start child process), when trying to use the Calendar Plugin of program "Gwenview" -- and trying to print to a PDF file, instead of to a listening printer.

I ensured I had all pdf-worthy things installed, such as gs-gpl, and my print services were configured 100% perfectly, etc, and I tried to mess with dcop and kded and kdeprintd.

It seemed like to was going to be a big troubleshooting and research session. Well it was not! It was EASY to fix (this time)!

What finally worked for what I was doing was to merely open a shell as the user trying to print the Gwenview PDF calendar -- and run "kded" at the command line as that user.

Lo and behold. It was like magic. Just worked instantly and easily. 

Hope this helps.

---

