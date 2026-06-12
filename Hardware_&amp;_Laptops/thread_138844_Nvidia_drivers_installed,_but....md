---
title: "Nvidia drivers installed, but..."
date: 2006-03-02
forum: Hardware &amp; Laptops
---

### Post by roncrump on 2006-03-02
Hi,

I've had Breezy installed on my Toshiba Satellite Pro TE2100
for a few weeks and thought it was about time I was brave
and installed the nVidia drivers.

lspci revealed I had a GeForce4 installed so I followed the
instructions on the wiki and installed nvidia-settings, nvidia-glx
and the linux-restricted-modules-386.

On restarting my X server, I got the nVidia splashscreen and
so was very happy.

However, I now have:
  (1) an unused (black) strip over 1cm wide down the
       righthand side of my screen;
  (2) Everything looks slightly fuzzy; and
  (3) the highest resolution available is 800x600.

I guess (3) may be responsible for (2), since the screen is no longer
in its optimal resolution.

What can I do to access a higher resolution (I think the "correct"
resolution for this screen is 1024x768 )?

And how can I get the right hand side of my screen back?

If necessary how do I remove the nVidia drivers?

Thanks,
Ron.

---

### Post by bluevoodoo1 on 2006-03-02
Have you tried...

sudo dpkg-reconfigure xserver-xorg

??

When you get to the resolution dialog, hit space bar to add 1024x768.

---

### Post by roncrump on 2006-03-02
[QUOTE=bluevoodoo1]Have you tried...

sudo dpkg-reconfigure xserver-xorg

??

When you get to the resolution dialog, hit space bar to add 1024x768.[/QUOTE]

I started to (just before I saw`your reply, actually), but got a bit scared as
there was a hell of a lot to it, and I wasn't sure that just keeping accepting
defaults was the right approach - would it have been?

Anyway, temporarily (I hope) I edited xorg.conf and changed back to the
nv drivers. This has fixed my problem, but only by undoing what I had
previously done.

I will try the reconfigure option again - should I let it autodetect
then just take the defaults throughout?

Ron.

---

### Post by bluevoodoo1 on 2006-03-02
[QUOTE=roncrump]I will try the reconfigure option again - should I let it autodetect
then just take the defaults throughout?[/QUOTE]

Yeah should be OK with that. Just when you get to the page about resolution make sure you choose the 1024x768 because it might not be highlighted.

---

### Post by roncrump on 2006-03-02
[QUOTE=bluevoodoo1]Yeah should be OK with that. Just when you get to the page about resolution make sure you choose the 1024x768 because it might not be highlighted.[/QUOTE]

Hmm. Tried that - although I also chose nvidia rather than nv (the default) 
as the driver, since it was the nvidia drivers I was trying to get working.
When I tried to re-start the X-server it woudln't - I had to log in and shutdown,
and then I had the same problems as previously - no high-res, no right hand
side, fuzziness.

Re-ran and chose nv and now I'm back to normal. Going to give up, I think.
Do I really need the nvidia drivers? (for general computing and the odd DVD)

Thanks for your help.
Ron.

---

### Post by bluevoodoo1 on 2006-03-02
[QUOTE=roncrump]Hmm. Tried that - although I also chose nvidia rather than nv (the default) 
as the driver, since it was the nvidia drivers I was trying to get working.
When I tried to re-start the X-server it woudln't - I had to log in and shutdown,
and then I had the same problems as previously - no high-res, no right hand
side, fuzziness.

Re-ran and chose nv and now I'm back to normal. Going to give up, I think.
Do I really need the nvidia drivers? (for general computing and the odd DVD)

Thanks for your help.
Ron.[/QUOTE]

If you're going to just go general computer things... surfing/office apps/DVD then you're right, the nv should be fine.

---

### Post by roncrump on 2006-03-02
[QUOTE=bluevoodoo1]If you're going to just go general computer things... surfing/office apps/DVD then you're right, the nv should be fine.[/QUOTE]
I'll just put that one in the "too hard" basket and get back to some work, then.
Cheers,
Ron.

---

### Post by bluevoodoo1 on 2006-03-02
[QUOTE=roncrump]I'll just put that one in the "too hard" basket and get back to some work, then.
Cheers,
Ron.[/QUOTE]

HAHA. I understand completely! I've finally gotten up enough guts to compile my own kernel (20 more minutes and it should be done!).

---

### Post by kakawerk on 2006-04-18
any luck in eliminating the black line? I am also on TE2100

---

### Post by mozetti on 2006-04-18
Alot of laptops use the **"Go"** versions of the nVidia cards, as in GeForce440Go. That's what my Dell C840 has in it. I seem to recall reading something in the nVidia drivers "HowTo" about these "Go" cards -- haven't done the nVidia drivers on my laptop yet, so I can't help beyond that.

---

### Post by kakawerk on 2006-04-18
I had success with FC5 wif the latest drivers but I returned to dapper as I cant stand the slowness of yum. Hopefully nvidia comes up wif a better driver soon I cant wait to try xgl

---

### Post by Tom Tiger on 2006-04-18
Same problem on a Toshiba Satellite Pro 6100, several other Toshiba models with the Nvidia Go 4x0 16mb are also affected, no idea about the 32mb models (haven't got one to test....)
But there is a new driver out the 8776 or 8767 from Nvidia, but I haven't gotten around to installing it and it ain't in automatix yet (doesn't suprise me the new Nvidia driver is only a week old 7th of april released)

But to summarize,  I've tried changing the x config file, doesn't work, it goes back to 800x600 with a 1 cm black piece on the right side of the screen.  Going back to the normal nv driver (generic debian xfree) solves this and I got 1024x768 on my 14",  which is normal,  but you loose acceleration and open GL.  

I'm not sure if the new nvidia driver will fix this.  Maybe tomorrow I'll have a go at it.

---

### Post by trent dillman on 2006-04-18
I'm using nvidia on a Geforce4 Go 5700, and I have full res.

Post your xorg.conf.

---

### Post by Tom Tiger on 2006-04-19
It isn't a xorg.conf problem.  I've allready tried that.  It all points to a problem with the Nvidia Go 4x0 series,  not the 5700.  If I have time tonight I'll try using the new Nvidia driver to see if it fixes the problem.

(which means adding gcc, make, kernelsource and probably a few other things)

---

### Post by Tom Tiger on 2006-04-20
Good news and bad news,  I've installed the new driver (thanks to a great guide here on the forum) this went without a problem,  then I wanted to adjust my xorg.conf as described in the guide (so I would be sure that I would have an exact match that should work)  and then.....  my harddrive died....  it was an old drive anyway but.... now I have to get another harddrive and then try again....   anyone else tried the new driver yet?

---

### Post by kakawerk on 2006-04-20
Today I tried loading the 8756 drivers on the dapper beta and it appears to be worse than flight 6 as the x server refuses to load at all even with the GeForce4 420 tweaks to the xorg.conf and options. I was able to get flight 6 to work with the same drivers and tweaks with the black strip on the right I guess its really a step backwards.

I am attaching the files i used here for reference

---

### Post by Crick on 2007-08-01
There is a solution to this problem (getting 1024*768 on your toshiba satellite pro 6100 or tecra 2100 with no black bar, in twinview or otherwise), it just means abandoning beryl (as far as I can tell - I'm just happy I've got a working twinview - which I find essential for work). Maybe you can try with the latest legacy drivers, however, I really can't be bothered.

Here's [how.]("http://experimentsinunix.wordpress.com/how-to-enable-twinview-on-a-toshiba-satellite-pro-6100-laptop-in-pclinuxos-linux/")

If you don't want twinview, you can just do as Ed Wiget [says]("http://www.edwiget.name/content/view/144/26/")

There are some complications in ubuntu however. Let me explain.

1. Quitting X is harder than in PCLinuxOS. There is no way to quickly do "init 3". From what I can tell, you have to follow the directions [here.]("http://www.linuxquestions.org/questions/showthread.php?t=491882")

2. Do note however, that you will need to do a synaptic search for nvidia. If you don't mark for removal the following three drivers, X will boot up the first time no problems after you have installed the NVidia driver, but then things get changed back somehow and X won't be able to boot on restart.

linux-restricted-modules-2.6.20-15-generic
linux-restricted-modules-2.6.20-16-generic
nvidia-kernel-common

There is also a slight problem, but nothing compared to the black bar of death (TM). If you want higher resolution than 1024*768 on your monitor that you are twinviewing with, you will get 1024*768 and no black bar on your laptop screen, there will just be an area you can move your mouse to but can't see. Either this situation or two 1024*768 screens are preferable for me compared to the black bar and one monitor with mega resolution.

---

