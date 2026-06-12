---
title: "no compiz in 9.04 upgrade with other problems"
date: 2009-04-26
forum: Installation &amp; Upgrades
---

### Post by fibo112358 on 2009-04-26
Hi everyone,

I noticed that I could update to 9.04 in the update manager, so I did. 

When I rebooted, my usual desktop tried to load but compiz couldn't run. Usually AWN, the dock at the bottom loads too, but couldn't since compiz wasn't running. I tried compiz --replace in the terminal, but I got some error message that didn't make any sense. 

I thought ok, this is just cosmetic stuff, let's see if any programs run. I tried tvtime and a few other programs. They briefly came up, but then disappeared. I tried reinstalling compiz, but nothing works except firefox and terminal. I was expecting a nice fresh theme or something, but it was just a disappointment and the great desktop and programs I had are now in an unusable state. 

Is there anyway I can undo the upgrade? I am not sure why they aren't telling people to be more careful if this is a development version or something, since the net effect of this "upgrade" was to take what I had and screw it up.

---

### Post by Wi7ahc4l on 2009-04-26
$20 says you, just like me have an ATI graphics card. Which means that you have no fglrx support because of ubuntu updating xserver to 1.6. Seemingly They don't plan to do anything about this. I will update with a fix if I find any more info on this. For the first time ever in my history of using ubuntu I feel left in the dark. It wouldn't be that bad if there was some sort of post or topic or even blog stating that there is a solution or workaround to this but there isn't.

---

### Post by fibo112358 on 2009-04-30
They really ought to test this stuff first before releasing it. A little bird whispered the following code into my ear:

sudo dpkg -reconfigure -phigh xserver -xorg

i don't know what this does, but maybe it updates the drivers or something for the graphics card. i really wish they would publish a book that explains how a linux system works and how to troubleshoot it in an intelligent way. it is not a good way to disseminate knowledge when it is just dispersed through a community and no one knows what it does.

---

