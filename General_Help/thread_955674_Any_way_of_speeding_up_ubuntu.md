---
title: "Any way of speeding up ubuntu??"
date: 2008-10-22
forum: General Help
---

### Post by morbid_bean on 2008-10-22
I have a machine with Pentium 4 Either 2.4 ghz or 1.2 ghz (the reason i say OR is because bios tells me i have 1.8ghz 

windows tells me i have 
Intel(R) Pentium(R) 4 CPU 2.40Ghz
1.80 Ghz, 384 MB of Ram

Ubuntu tells me i have
Intel(R) Pentium(R) 4 Cpu 2.40 Ghz
384 MB of Ram)

But im not too concernd about, I was just wondering if anyone knew of any ways/tweaks to speed up ubuntu while i can still use normal visual settings...i am currently removing programs i do not use in hopes it will help.

---

### Post by akshay.sulakhe on 2008-10-22
Remove the Unecessary softwares...If possibleuse CLI...Disable Compiz fusion..

---

### Post by russlar on 2008-10-22
use xubuntu

---

### Post by snowpine on 2008-10-22
More ram! (384mb is the bare minimum)
Go to System->Preferences->Sessions and disable any daemons you don't need
Don't use Compiz desktop effects
Try a lightweight windows manager such as Openbox or IceWM

Deleting applications you don't use won't speed up your computer--it will just free up some space on your hard drive.

---

### Post by iheartubuntu on 2008-10-22
Windows tells you this? Ubuntu tells you that? I suggest getting rid of windows all together. Do a complete fresh re-install of the new Intrepid 8.10, wiping out any dual boot setup you have and your system will kick some major butt.

If you must have windows, just run it in Virtual Box (unless you are doing some graphics intensive games in windows that you cant get working in Ubuntu).

---

### Post by urukrama on 2008-10-22
There are several things you can do to speed things up. 

You could use lighter applications, as some suggested, possibly a lighter window manager such as Openbox (see the link in my signature if you need help to set this up). Compiz-Fusion uses a lot of resources, so disabling that will make your computer somewhat faster.

If you'd prefer not to change to other applications, or want additional ways to speed things up, have a look at K.Mandla's excellent guide ["How To Set up Hardy for Speed"]("http://kmandla.wordpress.com/2008/05/04/howto-set-up-hardy-for-speed/"). It contains a lot of information, much of which might not affect you with such a modern computer, though.

Also, have a look at [this thread]("http://ubuntuforums.org/showthread.php?t=89491"). Though this was written before Hardy, much of it still applies. You will, however, find some additional entries that are not described in that guide, but you can search the internet to find out whether it would be smart to turn it off.

Uninstalling applications won't affect performance, unless those applications are started when you start your computer. You could remove the bluetooth utils if you don't use bluetooth (search in Synaptic for it).

As I work with a *lot* older hardware than what you have, I don't know if these things will make a markeable difference for you, but it might be worth a try.

You could also buy more RAM as suggested, though I don't think that is necessary. The most RAM I have in a computer is 256 MB and Ubuntu runs pretty fine on that if you just choose the right applications.

Ubuntu Intrepid (8.10) is still in beta, so don't use it on a production machine.

---

### Post by scouser73 on 2008-10-23
> **morbid_bean said:**
> I have a machine with Pentium 4 Either 2.4 ghz or 1.2 ghz (the reason i say OR is because bios tells me i have 1.8ghz 

windows tells me i have 
Intel(R) Pentium(R) 4 CPU 2.40Ghz
1.80 Ghz, 384 MB of Ram

Ubuntu tells me i have
Intel(R) Pentium(R) 4 Cpu 2.40 Ghz
384 MB of Ram)

But im not too concernd about, I was just wondering if anyone knew of any ways/tweaks to speed up ubuntu while i can still use normal visual settings...i am currently removing programs i do not use in hopes it will help.

You can visit this website; [http://www.kshoster.net/node/22]("http://www.kshoster.net/node/22") for help with speeding the boot up process of Ubuntu.

---

