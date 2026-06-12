---
title: "laptop-&gt;close and open again the screen-&gt;all black??"
date: 2005-04-18
forum: Hardware &amp; Laptops
---

### Post by iomicifikko on 2005-04-18
i just report in the right section a msg by Mr Wonka that was not answered, i have the same problem. maybe is a common problem:

------
Hello all.

This is my first post so please bear with me. 

Firstly, Ubuntu is by far the most human friendly distro that I've had the pleasure to use. In 99% of my case 'IT JUST WORKS' (TM). After fiddling to death with fedora core 1 this is such a breeze. Nice one. A big thanks to the developers.

The problem is this. I'm setting up my laptop to use all the acpi functions. I've got suspend to hard disc and suspend to Ram working and am now trying out the LID functions. If I close my lid and then open it the screen has blanked (I'm assuming that thats correct) but it does not come back again. I have to hit Alt-f7 and then X pops back up as normal. 

After having a look at the 'lid.sh' script in the /etc/acpi directory and completly pulling it apart I can tell you why this happens. The script uses 'fgconsole' to obtain the current console and then switches the console to 12. It never gets to switch console back as it coded to do (by pulling the original console value from a variable) as the command 'fgconsole' fails.

Running 'fgconsole' in a console returns 'Couldnt get a file descriptor referring to the console'. Not the nessesary number. Running 'sudo fgconsole' returns '7' i.e. it works.

How can I get this script to utilise fgconsole correctly? It's a pain having to hit buttons to see anything.


Thanks for any help
Mr Wonka
-------


byez

---

### Post by soul_rebel on 2005-04-18
is xscreensaver working? can you manually lock the screen?

---

### Post by Mr Wonka on 2005-04-18
As far as I know it was in the right section. The problem isnt a hardware issue, it's down to the acpi control scripts.

i've filed a bug report under [https://bugzilla.ubuntu.com/show_bug.cgi?id=9869](https://bugzilla.ubuntu.com/show_bug.cgi?id=9869). It contains a simple solution to the problem that worked for me. Just comment out the lines refering to "chvt"

Oh, and it's not fgconsole thats the problem. That runs fine. I forgot that the script gets run as root anyway.  :roll:

---

### Post by awaldram on 2005-04-19
Hi,

I had the same problem on my s6010 laptop

my solution was to add acpi_sleep=s3_bios to kernel options

now when opening the lid I get the password screen  \\:D/

---

