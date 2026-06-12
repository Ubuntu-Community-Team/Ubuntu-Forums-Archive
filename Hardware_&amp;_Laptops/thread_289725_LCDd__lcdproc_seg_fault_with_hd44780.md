---
title: "LCDd / lcdproc seg fault with hd44780"
date: 2006-10-31
forum: Hardware &amp; Laptops
---

### Post by katzman on 2006-10-31
Hi Guys....
I have a desktop server to which i have an lcd module attached (a hd44780). I had the server upgrade to edgy from dapper and the module worked just fine. But over the weekend i did a fresh install of edgy and now it will not work. WHen i try to load the hd44780 driver with lcdproc server is just segfaults. It does this under my server and laptop (both edgy) and under my custom .18 kernel and the standard ubuntu one

I have run gdb and gotten two different results on my 18 kernel i get :
Failed to read a valid object file image from memory.

Program exited normally.
and with the standard just:
Program exited normally.

Is this something to do with the compiliers in edgy or my system (The package also gives the same results)

---

### Post by digimatic on 2006-11-25
I have the same problem.

I even built the latest version of lcdproc from source and manually copied the fresh LCDd binary and the hd44780.so lib into the right places, same problem.

All works fine if I set it up to use the curses driver, so it does seem to be something directly relating to the hd44780 driver lib.

---

