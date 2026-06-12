---
title: "HP PSC 1310 all-in-one: HOORAY!"
date: 2005-09-05
forum: Hardware &amp; Laptops
---

### Post by robins_web on 2005-09-05
Yippee! After nearly being driven crazy for almost a month by not being able to print, I finally succeeded.

My old printer was a Canon S300 inkjet. Ubuntu found the printer all right, and configured it properly, but nothing ever printed. I even installed a different distro (SuSE 9.3) on a second machine, to se if that would work (it did, but it didn't detect my DSL setup, so I went back to Windoze).

Today I happened to be in Sam's Club looking for something else when I spied a display featuring the HP PCS 1310 Series All-In-One (printer, scanner, copier). At less than $65 bucks, I couldn't resist. So I bought one, brought it home, and went through the nearly half-hour installation routine. It worked perfectly under Windoze.

Next, I booted up my Ubuntu system. After I conected the printer, I launched Printing Manager, installed the printer and successfully printed a test page, all in less than 5 minutes.

If you need a reliable printer under Ubuntu, HP is the way to go.

Now I'm off to try scanning something....

---

### Post by evanc on 2005-09-18
i just set up a hp psc 1210 in about 30 seconds. amazing.


any luck getting the scanner working? I had it before, but I forget what i did...

---

### Post by matthew on 2005-09-18
[QUOTE=evanc]i just set up a hp psc 1210 in about 30 seconds. amazing.


any luck getting the scanner working? I had it before, but I forget what i did...[/QUOTE]
I had the same problem with my HP1210 and got the scanner working in this thread. Hope it helps you as well!!  [http://www.ubuntuforums.org/showthread.php?t=49288](http://www.ubuntuforums.org/showthread.php?t=49288)

---

### Post by ofpc on 2005-09-19
My english is not perfect. I speak spanish but i need install that printer HP1210.
How can i do that?
I hope you can help me.
Thanks and greetings.

---

### Post by matthew on 2005-09-19
[QUOTE=ofpc]My english is not perfect. I speak spanish but i need install that printer HP1210.
How can i do that?
I hope you can help me.
Thanks and greetings.[/QUOTE]
No hay problema. Yo puedo entender un poquito de espanol...

I will try to keep this simple.

1. Using Synaptic install "hplip" and "xsane"
2. a. at a command line type: sudo gedit etc/sane.d/dll.conf
    b. find "hpoj" in the file and insert a new line after it containing "hpaio" *make sure you are using the printer listed under "other" in the file.
    c. save and exit
3. Turn the printer off and turn it back on
4. a. System-->Administration-->Printing (or the spanish equivalent menu items)
    b. click new printer
    c. your printer should be detected, just follow the menu items

That is what worked for me. To scan use the program xsane. I hope that works well for you too.

---

