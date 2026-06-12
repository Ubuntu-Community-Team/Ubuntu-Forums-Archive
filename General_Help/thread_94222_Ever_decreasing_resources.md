---
title: "Ever decreasing resources???"
date: 2005-11-23
forum: General Help
---

### Post by tomski on 2005-11-23
since i installed breezy & linux-image 2.6.12-10-k7
 i have found that
firefox is less responsive (takes longer to load pages and startup, since new ati driver)
cpu usage in gkrellm is higher (since new linux image)

I think some other apps are misbehaving too!
 
I've been using linux for about 3-4 yrs now & i have to say that my current machine used to fly when using linux (thats why i got into it) & be a dog in windows but other the years it seems that something in linux is starting to hog resources (or my cpu is dying).
I noticed this first whilst using suse 9 so i changed to debian based distro's and that seemed ok but now this resource hog has found me again.

Has any one else seen a drop in resources/performance? or is this due to the fact that linux is beginning to get a grip in GUI land (move closer to windows)
or maybe just a combination of :

my outdated h/ware + bad ati drivers + issue with latest kernel + bloated gui

i currently have this h/ware setup :   (dont laugh)

mobo = jetway v266b
cpu = amd athlon 1.1ghz (Tbird)
ram = 768mb pc133 sdram (1x512 + 1x256)
gfx = ati radeon 9200SE 128mb ddr
monitor = hansol 920p (1600x1200)
h/drv's = 2 maxtor diamondmax 9 1x160gb + 1x80gb
cd/dvd = sony dru500a
2x win xp pro install's (standard hda1 ,games hda2)
1x ubuntu (hda6 + 1gb swap hda7)       is this too big??

i know i need a hardware upgrade but finances have put a hold on that

if you know of any issues or are having the same thoughts please reply to this post

---

### Post by JustRandomName on 2005-11-23
Hi,

I think one the major reasons that linux is feeling sluggish is indeed GNOME. As GNOME add's more features, the more resources it uses.

You could try using a lighter DM (XFCE?) and there is a great ubuntu port of this: 

apt-get install xubuntu-desktop

XFCE is great, it's just that I am a GNOME addict, but it is a sad fact that the better GNOME gets, the better machine you need to run it smoothly.

To try and find out exactly what is hogging the resources (it may be just an app that is behaving badly) try and examine the RAM and CPU usage of different applications, and then try to find a lighterweight alternative.

GNOME MEnu -> System Tools -> System Monitor

If you click on "% CPU" label it will order the applications by the amount of CPU power it is using (I am guessing where this is where the bottle neck lays since you have a lot of RAM/Swap space).

---

### Post by RAOF on 2005-11-23
The Gnome devs are working on lots of performance gains for the next Gnome release (2.14).  Apparently the Gnome in Dapper (currently one of the 2.13.? snapshots) is appreciably faster.

While this doesn't really help you (unless you're willing to try the Dapper development release ;)),  Gnome **has** been steadily increasing it's resource usage.  At least there is hope for the future.

---

### Post by tomski on 2005-11-23
i am willing to try the daper release but i tend to wait a good 3 month after most  linux distro's have gone official before i upgrade, which was confirmed to me as a good idea because last week i tried to upgrade from hoary to breezy & it went horibly wrong even though i had resolved all dependacies prior to dist-upgrade.

 so i now have a fresh install with some hoary configs,scripts,alias' 

but as i have some spare drive space i may add a daper install to test
 (heind sight slapped me as i typed this..should have did this with breezy!!)
 then if it works.. switch over

---

### Post by Eleaf on 2005-11-23
How much of a slow down are you noticing?  Like how long does it take to open firefox and what is your average idle cpu % etc.  I have computers with lower hardware stats than yours but they run snappily.  But if it happend right after you installed a new kernel, that could be why....

---

### Post by kennethb on 2005-11-23
I'm using Ubuntu Breezy 5.10 on an Intel P3 with 512MB of RAM (laptop). The GNOME desktop is working fine for me. I have noticed that OpenOffice 2.0 takes up a lot of cpu% when it launches, when it closes, and when I'm using it; any were between 7% and 50% of my cpu. 

I too, need to upgrade my laptop, but I prefer not to - I'm kind of a reduce-reuse-recycle kind of nut :)

---

### Post by tomski on 2005-11-28
[QUOTE=Eleaf]How much of a slow down are you noticing?  Like how long does it take to open firefox and what is your average idle cpu % etc.  I have computers with lower hardware stats than yours but they run snappily.  But if it happend right after you installed a new kernel, that could be why....[/QUOTE]


as soon as i open firefox my cpu jumps to 80% and it takes about 2 min to open

and gnome just genrally feels slower as i have just come from hoary literaly last weds was when i made the change and i noticed the slow down more or lees instantly

---

### Post by meriva on 2005-11-30
I have a fresh Breezy install (did not upgrade from the previous one, I preferred to re do it from the beginning) so that it's almost clean.
But I guess Firefox is a big resource eater, too many megs each time you surf the web,don't you think?
Another thing is Gnome, I don't like other DM, I like Gnome, so that I want to keep it (I tried XFCE but it's not soo easy to customize and I don't want to spend too much time on it) but I feel it's slow on my machine.

Here are my specs:

Toshiba Satellite 1410-304
Celeron 1.8, 512MB ram, 40Gb HD, 1 GB SWAP, Breezy fresh installed

I felt in Hoary as fresh installation it rocks....:???:

---

### Post by Mizzou_Engineer on 2005-11-30
I know that the Firefox 1.0.7 used in Ubuntu 5.10 has memory leakage issues and is not nearly as fast as the version gotten from Mozilla. I run FF 1.5 from Mozilla just from my home directory and left the 1.0.7 installed to not cause ubuntu-desktop to be removed and future compatibility problems to occur. I specified 1.5 to be the default browser in the "Preferred Applications" menu where I entered its location manually. 

And no, your CPU is not dying, it's the increase in features of almost all DEs that makes a once-fast computer run slowly. It happens to everybody. If it didn't, most of us would still be using 486s. 

Oh, and if you disable Java in OpenOffice's options panel, it starts a lot quicker. You can't see Java applets in your Writer documents anymore is the only downside.

---

### Post by Mizzou_Engineer on 2005-11-30
I always do a fresh install of any new distro. I just have /home on its own partition and make sure it does not get formatted in the setup and make sure it gets mounted as /home in the new install. 

This takes care of all of the upgrade-compatibility bugs but you do have to reinstall not-in-the-standard-config apps and restore your settings. I figure it's a small price for me to pay as I use more or less of a stock setup.

---

