---
title: "unable to install"
date: 2009-04-05
forum: Installation &amp; Upgrades
---

### Post by spm1370 on 2009-04-05
I am unable to install ubuntu 8.10.......from cd rom which i got mailed...........
the computer boots from the cd and shows the initial screen asking for live mode or install and other options........
then when i press either live mode or install....either way the system stops responding and only shows the background screen........i even waited 45 minutes but there was no change on the screen..
i am new to linux and has choosen ubuntu to be my first linux.........
my system specs are.
intel pentium 4 2.24 GHz, Gigabyte 81845G motherboard, 256 MB ram, intel integrated graphics, 40 gb seagate hard disk.
is my system specs enough to run ubuntu........
if not enough i would like to go for xubuntu.
is there any way to install the xubuntu directly from ubuntu cd which i have.....

---

### Post by taurus on 2009-04-05
You don't have enough RAM to run the LiveCD.  Therefore, you have to use the alternate CD if you want to install Ubuntu (or even Xubuntu) on your machine.

[http://www.xubuntu.org](http://www.xubuntu.org)

---

### Post by Mark Phelps on 2009-04-06
Also, be aware that 256MB of memory is right on the fringe regarding minimum needed for useful performance.  I forced an install of 7.10 on a 256MB laptop and the result was so slow as to be useless.  I had to resort to using Xubuntu, but even that was painfully slow.  Others have reported better responses with their 256MB machines.

So, if it installs but is then very slow, that's the best you're going to get unless you switch over to Xubuntu -- and then you lose the GNome desktop and its features.

---

### Post by coffeecat on 2009-04-06
> **spm1370 said:**
> intel pentium 4 2.24 GHz, Gigabyte 81845G motherboard, 256 MB ram, intel integrated graphics, 40 gb seagate hard disk.

If you had enough RAM, Ubuntu would run quite nicely on that setup, although you might want to search the forum for that 81845G Intel graphics chipset. I used to have a machine with that chipset and it ran the Ubuntu of around 2006 well enough, but I seem to remember reading about some problems with the Intel 8X5 chipset and the current Intel driver. I could be wrong though, but something to check out.

All you need is 512MB for Ubuntu to run reasonably well enough. 768 would be better and 1GB would be ideal. Your machine probably takes the now obsolete DDR RAM which if you had to buy new would now be more expensive than the later DDR2. See if you can get hold of some secondhand. Perhaps from a scrapped machine of a similar age. Then if you could upgrade the RAM, you could run the Ubuntu CD live and see if there really is any issue with the Intel graphics driver.

> **spm1370 said:**
> is there any way to install the xubuntu directly from ubuntu cd which i have.....

Sorry, no. You'll have to get hold of the Xubuntu CD.

---

### Post by alasdairm on 2009-04-06
i have exactly the same problem and i have 3gb of ram.

i downloaded ubuntu 8.10 and boot from the cd. i get to the title screen and select 'install ubuntu'. i choose english from the language menu then it just hangs up. sometimes, it will get to the location screen, then hang up. i have to reboot.

i've tried about 10 times now and no luck.

i'd hate to give up so early in my attempt to learn about linux but this is already pretty frustrating

regards and thanks

alasdair

---

### Post by taurus on 2009-04-06
> **alasdairm said:**
> i have exactly the same problem and i have 3gb of ram.

i downloaded ubuntu 8.10 and boot from the cd. i get to the title screen and select 'install ubuntu'. i choose english from the language menu then it just hangs up. sometimes, it will get to the location screen, then hang up. i have to reboot.

i've tried about 10 times now and no luck.

i'd hate to give up so early in my attempt to learn about linux but this is already pretty frustrating

regards and thanks

alasdair

How fast did you burn the CD?

At the initial screen, run the check cd for defects option to make sure your CD is good first.

---

### Post by Madvil on 2009-04-06
I thought about making this question in this thread.

I tried 6 out of 6 times to install Ubuntu 64 but the installer stucks on the "Checking hardware" 94% without doing anything else.
I managed to pass this phase by installing grub on /sda5 which I put the OS in, but then of course it didn't detected the GRUB and used the Vista loader, which fails to boot Ubuntu.

Help...

---

### Post by alasdairm on 2009-04-06
> **taurus said:**
> How fast did you burn the CD?

At the initial screen, run the check cd for defects option to make sure your CD is good first.i burned the cd as slow as 6x.

i checked the cd and the cd is good.

alasdair

---

### Post by taurus on 2009-04-06
> **alasdairm said:**
> i burned the cd as slow as 6x.

i checked the cd and the cd is good.

alasdair

At the initial screen, press F4 for safe graphics mode.

---

### Post by alasdairm on 2009-04-06
^ i did that and i did get a little further. now i can progress beyond the dialog where i choose my location then it hangs as it is starting the partitioner.

i tried again a few times and sometimes it gets that far, sometimes it hangs on the brown background image with just a mouse cursor showing.

alasdair

---

### Post by taurus on 2009-04-06
> **alasdairm said:**
> ^ i did that and i did get a little further. now i can progress beyond the dialog where i choose my location then it hangs as it is starting the partitioner.

i tried again a few times and sometimes it gets that far, sometimes it hangs on the brown background image with just a mouse cursor showing.

alasdair

Another option is to use the alternate CD to install Ubuntu on your machine.  It's a text based installer but should be real easy to follow.

---

### Post by alasdairm on 2009-04-07
^ thanks, taurus.

i downloaded and used the alternate (text-based) installer. everything went fine - partitioning, setup, etc. when i restarted my pc, i was asked to login with my username and password.

then i see a brown desktop with a mouse cursor. my pc freezes and has to be rebooted every time. if i can't progress past this point, how can i troubleshoot what's causing this?

alasdair

---

### Post by larytet on 2009-04-07
likely one of the drivers does not feel good

try to Alt-Ctrl-F1 
should bring white on black terminal window and prompt for password
after that type the following

```

sudo passwd

```
Enter and reenter your root user password - can be the same as your user password.
After that 
```

dmesg | more

```
Check if there is any failures closer to the end of the output
also try
```

dmesg | grep fail

```
or
```

dmesg | grep error

```

Try to write down the output and copy it here. you do not have to be precise. Something like "EHCI: BIOS handoff failed"  is already a good lead

---

### Post by alasdairm on 2009-04-08
i got to the desktop - this time with a menu bar across top - but the pc still freezes. alt+control+f1 has no effect.

alasdair

---

### Post by alasdairm on 2009-04-08
when the pc freezes, control+alt+f1 has no effect (nor does control+alt+backspace which somebody elsewhere suggested).

somebody elsewhere suggested adding the 'noacpi' option to the boot. it had no effect.

alasdair

---

### Post by larytet on 2009-04-09
Grub - booter which brings Linux (Ubuntu) up has it's own menu

power down the box, power up and Press [Esc] while the system boots.

You are going to enter a short menu - white on black with 3-5 options. One of the option is going to be "kernel 2.6.xx-generic (recover)

Choose the "recover" option.
After Linux boots you will get color ASCII menu (blue background, gray box, black text). Choose "drop to root shell prompt with networking)" and see what happens
If fails try the "drop to root shell" but without networking.

If you chose with networking make sure that networking works by ping to google, for example
```

ping 209.85.129.99

```
and
```

ping www.google.com

```

When and if you get command prompt try dmesg i suggested before.

If you see no problems so far
```

startx  

```
will start Gnome (Ubuntu desktop manager) and bring GUI interface


If still nothing helps, run through the memory tests and file system tests in the "recovery menu" and Grub menus.
If the memory is Ok, try to remove all xPCI cards from the box. Do you have Intel integrated graphic or a separate graphic board ?

---

### Post by larytet on 2009-04-09
> **Madvil said:**
> I thought about making this question in this thread.

I tried 6 out of 6 times to install Ubuntu 64 but the installer stucks on the "Checking hardware" 94% without doing anything else.
I managed to pass this phase by installing grub on /sda5 which I put the OS in, but then of course it didn't detected the GRUB and used the Vista loader, which fails to boot Ubuntu.

Help...

Are you trying to create a double boot setup - Vista and Linux coexisting on the same disk ? If this is the case try to download  SystemRescueCD and boot from the CD. The tools on the disk will help you to create Linux partition. 

Another alternative is to run Linux under Virtual machine - see Ubuntu Wubi.

---

### Post by alasdairm on 2009-04-11
thanks for all the help - i really appreciate it.

i tried the dmesg stuff you listed above and, while there is a lot of text, i cannot seem to see any fail or error-related messages. i grep'ed "handoff" with no results.

> **larytet said:**
> Do you have Intel integrated graphic or a separate graphic board ?i have an ati radeon x300 card. a brief search on the internet suggests that this could be a driver issue with this hardware. assuming i locate a recent driver, how would i install it?

thanks

alasdair

---

### Post by alasdairm on 2009-04-13
well, i think this is the point at which i give up. i consider myself reasonably computer literate but this has been a very frustrating experience and the full extent of my linux experience has been a desktop featuring a frozen mouse cursor.

oh well. thanks for the help.

alasdair

---

### Post by kf6tac on 2009-04-18
> **alasdairm said:**
> ^ i did that and i did get a little further. now i can progress beyond the dialog where i choose my location then it hangs as it is starting the partitioner.

i tried again a few times and sometimes it gets that far, sometimes it hangs on the brown background image with just a mouse cursor showing.

alasdair

Mine gets hung up on the "Starting the Partitioner" dialog box too - the progress bar reaches 100% but the box stays stuck on the screen and the animated "swirl" mouse cursor stops swirling (but doesn't change back to an arrow).  I'm trying the alternative CD now in hopes of better success.

---

