---
title: "SSD or lubuntu or both?"
date: 2014-03-02
forum: Hardware
---

### Post by Odyssey1942 on 2014-03-02
I have a blue haired Lenovo laptop which I take with me when I travel. It is used mostly for checking email, traffic, getting directions, finding restaurants, weather, etc. If it goes walkabout from my hotel room, I will not lose much sleep. 

It came with XP, so have installed 12.04 Ubuntu over it as a clean install.

There are some issues which I will return to, if they remain after the following.

Specs are: 1 Gb RAM, 32 bit Celeron M CPU 420  @ 1.60GHz CPU, 1024 KB cache

It is very slow with 12.04, so I am considering either or both of re-installing with lubuntu and replacing the HDD with a SSD. 

Which of these will give me the best performance boost, and if it is lubuntu, will replacing the HDD with a SSD then add a significant improvement past lubuntu? Losing a new SSD would be more of an issue than losing the computer, so will only do this if significant

---

### Post by walterorlin on 2014-03-02
I think it matters what how the performance will happen. SSD will increase boot speed. Althought a swap partition which you may want with 1gb of ram will wear out ssd quicker but they have improved. Also the ssd will only end up mattering with input and output and mainly boot speed or loading large programs. For browsing the web there is not that much input or output from the disk. you will still be limited by the processor and ram even with an ssd. So maybe try lubuntu. Although there may be a problem running a Celeron M may not have a PAE flag which will be a problem.

---

### Post by Odyssey1942 on 2014-03-04
WO, Have done my reading. It appears that I should try to install 13.10 first to see if the PAE error surfaces, and if so, use the workaround to install 12.04.

Or if it is still available, just go for the non-PAE version of 12.04 to start with?

---

### Post by sudodus on 2014-03-04
You need not install 13.10 to find out if you have a PAE flag. Run this command in your current Ubuntu system

```
cat /proc/cpuinfo
```

and specifically

```
grep --color pae /proc/cpuinfo
```

which should show a line with **[COLOR=#ff0000]pae[/COLOR]** if the flag is there. If you have a pae flag, use the regular Lubuntu 13.10 i386 iso file, otherwise you can go via 

[Lubuntu-fake-PAE]("https://help.ubuntu.com/community/Lubuntu-fake-PAE") instead of upgrading all the way from 12.04 LTS.

---

### Post by Odyssey1942 on 2014-03-05
PAE was listed in red, so no further concern on that. Thanks for this tip.

I had planned to install lubuntu 12.04, because I originally thought that it was a LTS. Reading reveals that it is not a LTS, but being based on Ubuntu 12.04 LTS, many of the components will be supported because Ubuntu is being supported.

Does this mean that Lubuntu 12.04 is likely to be more stable than 13.10? This is important to me as I am a heavy computer user, and while curious about subsequent versions, need to spend my time getting other things done on the computer rather than dealing with all the inevitable issues surrounding upgrades, new installs, etc

Or/and, will Lubuntu 14.04 be a LTS? If not, will Ubunut 14.04 be a LTS? If yes to either of these, I will wait and go for 14.04 Lubuntu, assuming that Lubuntu 14.04 will be based on Ubuntu 14.04. (Are preview versions available now?)

Thanks to both.

---

### Post by mörgæs on 2014-03-05
All 14.04 Buntus will be long term support.

Lubuntu 13.10 is rock stable and I recommend this one. Now it's four months since release, and the few important bugs which were present have been fixed. 

I suggest staying with 13.10 until support runs out in June, then it's time for 14.04. Don't install anything at release date.

---

### Post by Odyssey1942 on 2014-03-09
Great guidance all. Thanks.

I have installed Lubuntu 13.10 and am happy as a clam with the speed (and it has made an issue with restarting and closing down go away.)

Functionality is a big downgrade from Ubuntu 12.04, but I understand that this is how lubuntu gets "light" and for the purposes that this laptop is used, it is a good trade-off.

Two quick questions. Is it possible to have multiple workspaces in 13.04 without adding a new interface that will compromise performance?

I haven't used Abiword before. Will it open .doc files and maintain the integrity of the files so that if they are worked on in AbiWord, saved, then opened in LibreOffice they will have the same formatting, and other characteristics from when they were previously saved in LO (assuming of course that those characteristics were not deliberately changed in AW)?

I haven't used AW at all yet, but assume that it does not handle spreadsheets, but in the event that it does. I have the same question about .xls files.

TIA

---

### Post by sudodus on 2014-03-09
> **Odyssey1942 said:**
> Great guidance all. Thanks.

I have installed Lubuntu 13.10 and am happy as a clam with the speed (and it has made an issue with restarting and closing down go away.)

Functionality is a big downgrade from Ubuntu 12.04, but I understand that this is how lubuntu gets "light" and for the purposes that this laptop is used, it is a good trade-off.

Two quick questions. Is it possible to have multiple workspaces in 13.04 without adding a new interface that will compromise performance?

There ***are*** two workspaces in Lubuntu. But are you really running 13.04? It has passed end of life (in January), and receives no more ssecurity updates! ***Use Lubuntu 13.10!*** If you have not done much, I think it is much better to make a fresh install compared to upgrading from 13.04.
> 
I haven't used Abiword before. Will it open .doc files and maintain the integrity of the files so that if they are worked on in AbiWord, saved, then opened in LibreOffice they will have the same formatting, and other characteristics from when they were previously saved in LO (assuming of course that those characteristics were not deliberately changed in AW)?

I haven't used AW at all yet, but assume that it does not handle spreadsheets, but in the event that it does. I have the same question about .xls files.

TIA

Abiword opens Microsoft Office files, but does not recognize all kinds of formatting. Neither does LibreOffice, although it is more powerful. You can install LibreOffice, many people do because it can do much more things than Abiword. Only if the computer is too weak for LibreOffice you should stay with Abiword. Try it out!
```

sudo apt-get install libreoffice
```

Lubuntu comes with Gnumeric (light-weight) for spreadsheets. Also in this case you can try which of them works better for you in your computer.

---

### Post by Odyssey1942 on 2014-03-09
Error Correction:

My previous post said "Is it possible to have multiple workspaces in 13.04"

That should have been 13.10 instead of 13.04.

Wow. There are indeed two workspaces, thanks. I had somehow missed that (though in my computer it is a bit hard to see. Now that I know it is there, it's much easier.)

All good for now.

Thanks again to all.

---

### Post by Rob Sayer on 2014-03-11
"Don't install anything at release date."
- damn good advice.

"[Lubuntu] functionality is a big downgrade from Ubuntu 12.04 ..."
- I actually haven't found that.  I find the ubuntu desktop for functionality is KDE myself.  But LXDE has everything you really need.

---

### Post by Odyssey1942 on 2014-03-18
Rob, Thanks for yours.

Just to clarify, I should have said "...combined with the lesser hardware capability..." On my principal desktop computer, I keep 8 workspaces open, each with multiple browser windows, each window with multiple pages, and WIP docs open all the time (allowing me to not only switch quickly and efficiently between tasks, but also to (mostly) keep track of pending items.)

So maybe I should have just limited my comments to how very pleased I am with lubuntu on the old laptop (the combination of which are just fine for the purposes that this computer is used for) and not compared it to Ubuntu on my fast principal computer, and my gratitude for all the great guidance.

robert

---

