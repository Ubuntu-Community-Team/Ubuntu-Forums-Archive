---
title: "Speed up boot time"
date: 2008-10-11
forum: General Help
---

### Post by startherepodcast on 2008-10-11
Hey everybody,

I spent yesterday eveningtrying to optimize the boot time on my Laptop that runs Ubuntu 8.04
First of all I abandoned Compiz and installed the Netbook Remix, because that reflects more what I am going to do with that machine now that I've got my new Computer.
I got the boot time down to about 1:30 from power-on (Probably less from loading the kernel). Boot to the login screen alone takes about 50s

Now, if I have logged in once and log out and log in again, login is incredibly fast. Probably because all the required files are already in the RAM.
Question: How do I make it load these files into the RAM at boot time, when the HDD is idling a lot of the time anyway?

Thanks for your answers in advance!

Leon

---

### Post by spupy on 2008-10-11
I think utilizing some sort of a [ramdisk]("http://en.wikipedia.org/wiki/Ramdisk") may help you. The files are loaded in RAM, but the programs can use them as if they were on disk.

An easier solution might be _preloading_. There was one more with similar name but I can't recall it right now.

Last, check out the program called _bootchart_. As you boot, it compiles a graphic that tells what program start when at boot, how long do they start, how much CPU and disk I/O the use. You can view this graphic after logging in. It is very handy to see what is slowing your boot process down.

---

### Post by spiderbatdad on 2008-10-11
Yeah, 1 1/2 minutes from power on is about a minute to slow...roughly 32-35 seconds is good. Perhaps you have multiple network interfaces competing for configuration? Dmesg is your friend for trouble shooting the boot process.```
dmesg > ~/Desktop/dmesg.txt
```This will write the diagnostic message from the kernel, to your desktop. You can read through it for clues, or upload it here as an archive. Right click the file ans select create an archive, then upload the zipped archive here, with the manage attachment tool, below.

Once the correct boot options are applied to the kernel...or the hardware problem is addressed, you can do a one-time profile of the boot, to shave a few more seconds off the time it takes to boot your machine.

To profile the boot, enter the grub menu by pressing esc at boot time, if necessary, to see the various kernels you have to choose from. Usually the top, highlighted one is the kernel you will profile. Press e, then use the arrow key to move down a line to the line that begins with the word kernel. Press e again, now go to the end of the kernel line...after the last word (maybe quiet splash) add the word profile. Hit enter and then press b.

Suggestions from your kernel may include things like 'try using lapic.' If you saw a suggestion like that, you would delete quiet splash from the end of the kernel line and replace with the word lapic. You would do this in the file /boot/grub/menu.lst, so that you wouldn't have to edit the kernel line every time you boot the system.

---

### Post by Goagioou on 2008-10-11
bump up   then lurk--------------------------------very good wow power leveling site:**[buy WoW Gold](http://www.gogoer.com),  [World of warcraft Power Leveling](http://www.wow-powerleveling.org/wow+power+leveling.html), [World of warcraft Power Leveling](http://www.powerlevelingweb.com), [wow power leveling](http://www.powerlevelingweb.com), [wow power level](http://www.powerleveling-wow.com/siteMap.asp)**

---

### Post by AlexBellisBrown on 2008-10-11
Its also worth pointing out Ubuntu Jaunty 9.04s main objective is to optimize boot time. :)

---

### Post by nawitus on 2008-10-11
1. Remove the splash screen
2. System -> Administration -> Services, and remove some unneeded services.
3. Most importantly, google: [http://www.google.com/search?hl=en&q=make+ubuntu+boot+faster](http://www.google.com/search?hl=en&q=make+ubuntu+boot+faster)

---

