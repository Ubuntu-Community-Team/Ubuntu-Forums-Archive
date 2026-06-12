---
title: "problems with using beamers and external monitors"
date: 2005-04-03
forum: Hardware &amp; Laptops
---

### Post by dusu on 2005-04-03
Hi,
I've installed Ubuntu on my (old) Toshiba S3000-X4 laptop, which has an Intel i810 chipset.

I had first installed Warty, and had no problems projecting my screen with a beamer.
I just had to plugg in the vga cable, and then use the Fn-F5 key combination once to redirect the video output to the beamer, or twice to get the output both on my screen and on the beamer.
Furthermore I had no resolution problems ( ie the resolution was the same as the one of my screen, 1024*768 ).

I upgraded to Hoary some time ago, and today I tried the same again. And now I get a couple of problems :
  1) If I start my computer without plugging the beamer or an external monitor, then plug one of these, the Fn-F5 key combination makes absolutely *nothing*.
  2) I then tried to first plug the beamer in, then start the computer. When doing so, I get something on the external screen, but nothing any more on my laptop.
The Fn-F5 is still inefficient. And the resolution I get on the external screen is not 1024*768, but much poorer.

Does any one have a clue why things worked in Warty and do not any more in Hoary ?
Shall I submit a bug report for this ?
And does any one know how to cure the problem ? (I looked at other threads but did not find the answer).

Thanks for any help.

---

### Post by Jindro Ruzicka on 2005-04-06
You are lucky, try i810switch 
in main or universe repository

---

### Post by dusu on 2005-04-06
Thanks a lot for the information and the help !
I installed i810switch and by doing
```
i810switch crt on/off
```
I manage to turn the external monitor on/off :D
I cannot turn the internal monitor off by i810switch lcd off, but that's a minor problem !!

Now, for my culture, could anyone tell me why the Fn-F5 feature has been disabled in Hoary ? Or is it only happening to me  :confused:

---

### Post by DaveQB on 2005-04-28
Does this app also apply to the Armada M700 ??
Its the 440BX chipset board i believe.

Maybe there's a 440BXswitcher ;)

Thanx for reading.


PS VGA out **worked** in Slackware 10.1 with kernel 2.4, **didnt work** in Mandriva 2005LE kernel 2.6.11 and **doesnt work** in Kubuntu 5.4 Kernel 2.6.10

---

