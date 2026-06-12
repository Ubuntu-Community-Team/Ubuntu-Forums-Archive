---
title: "[SOLVED] Update issue"
date: 2008-08-14
forum: General Help
---

### Post by Bucky Ball on 2008-08-14
Hi all. I seem to be getting an exclaimation mark icon from my update manager telling me to run update and click ´check´. When I do this, I get this error;

[quote=my update manager][LEFT][SIZE=2]Failed to fetch cdrom:[Xubuntu 8.04 _Hardy Heron_ - Release i386 (20080422.1)]/dists/hardy/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs[/SIZE][/LEFT]
    [LEFT][SIZE=2]Failed to fetch cdrom:[Xubuntu 8.04 _Hardy Heron_ - Release i386 (20080422.1)]/dists/hardy/multiverse/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs[/SIZE][/LEFT]
    [LEFT][SIZE=2]Failed to fetch cdrom:[Xubuntu 8.04 _Hardy Heron_ - Release i386 (20080422.1)]/dists/hardy/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs[/SIZE][/LEFT]
    [LEFT][SIZE=2]Failed to fetch cdrom:[Xubuntu 8.04 _Hardy Heron_ - Release i386 (20080422.1)]/dists/hardy/universe/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs[/SIZE][/LEFT]
[/quote][LEFT]
[SIZE=2]When I close that window, it updates as normal and tells me machine is up to date. I figure this is something to do with the install cd and the fact that when I go to ´Software Sources´ the install cd is not an option. Just tells me to insert a cd if I want to load software from it.

Any ideas?
[/SIZE][/LEFT]

---

### Post by Elfy on 2008-08-14
Have you got the cdrom enabled in software sources - I have had them appear on the 3rd part tab as well as the front. It appears tp be trying to find the cdrom

---

### Post by iaculallad on 2008-08-14
Navigate to System->Administration->Software Sources, under the "Ubuntu Software" tab, make sure that Main, Universe, Restricted, Multiverse are marked as checked. Download from Server should point to "Main Server" and be sure to uncheck "Installable from CDROM/DVD". Click on Close button and select "Reload" on the next window that pops-out.

---

### Post by Bucky Ball on 2008-08-14
Was just editing that bit into my last post when you posted. Yea, doesn´t give me the same option (tick box) as my laptop. So I don´t have the cd rom option, but that is what it is looking for, even unticked probably.

---

### Post by iaculallad on 2008-08-14
> **Bucky Ball said:**
> Was just editing that bit into my last post when you posted. Yea, doesn´t give me the same option (tick box) as my laptop. So I don´t have the cd rom option, but that is what it is looking for, even unticked probably.

Does the same error shows up when you input the command below on your terminal?

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by Bucky Ball on 2008-08-14
> **iaculallad said:**
> Does the same error shows up when you input the command below on your terminal?

```
sudo apt-get update && sudo apt-get upgrade
```

Yep. No different.

---

### Post by Nepherte on 2008-08-14
Does this list your cdrom?
```
cat /etc/apt/sources.list
```

---

### Post by Bucky Ball on 2008-08-14
this is the result of 
cat /etc/apt/sources.list
```
# 
deb cdrom:[Xubuntu 8.04 _Hardy Heron_ - Release i386 (20080422.1)]/ hardy main multiverse restricted universe

deb cdrom:[Xubuntu 8.04 _Hardy Heron_ - Release i386 (20080422.1)]/ hardy main multiverse restricted universe
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
```

Ah, ha. I see some discrepencies ...

---

### Post by Elfy on 2008-08-14
Edit the sources list and put # in front of deb cdrom. Save and close - if you don't have anything else in your sources.list you can enable the other sources from Software sources, main, universe, restricted, multiverse, partners on 3rd party tab.

I would post mine but it's all over the place ;)

---

### Post by Bucky Ball on 2008-08-14
[quote=forestpixie]I would post mine but it's all over the place :wink:[/quote]

ha, I'll give that a try in a minute and let you know, but I reckon you're on the mark with that. I wonder, where did the desire for this other cd come from? It wasn't happening when I first installed on that machine?

Yep, other stuff in sources list, just posted the important bit ... :)

---

### Post by Elfy on 2008-08-14
> Yep, other stuff in sources list, just posted the important bit ... oh good - would have deconstructed mine a bit if it helped, glad not to though ;)

> I wonder, where did the desire for this other cd come from?I never really got to the bottom of it myself.

---

### Post by Bucky Ball on 2008-08-14
Yep, that worked. And I think I might be part way to answering my own question. There is nothing else in the source.list that refers to Xubuntu. I installed Xubuntu originally from disk when that machine had 256mb of RAM and was having trouble installing Ubuntu. Then got 1GB for it and opened the Ubuntu repositories also so it is a blend; opens with the Xubuntu splash at boot but Ubuntu and Xubuntu, if you know what I mean.

So, Hardy Xubuntu repository not open by the looks of my source.list. Is it something like;

sudo apt-get install xubuntu-source

Not sure what's happening in the box, but I know my original problem is fixed so thanks ... :)

---

### Post by Vishal Agarwal on 2008-08-14
I request you to mark this thread Solved.

---

### Post by Bucky Ball on 2008-08-14
> **Vishal Agarwal said:**
> I request you to mark this thread Solved.

Not sure where you've come from but unless you have some helpful advice or you're a moderator, all I can say to you is ... 

?

You appear from nowhere having played no part in this thread requesting me to mark it solved. As I say, unless you're a moderator, not sure where you fit here.

Thanks again, forestpixie. See you round, I'm outta here ...

---

