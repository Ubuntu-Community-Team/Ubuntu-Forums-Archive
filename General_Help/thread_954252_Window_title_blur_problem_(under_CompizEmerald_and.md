---
title: "Window title blur problem (under Compiz/Emerald and good hardware)"
date: 2008-10-21
forum: General Help
---

### Post by nahuel_89p on 2008-10-21
Hi, my problem is that I'm trying to enable blur effect in windows title bar (like vista), using emerald and compiz, but when i enable the blur plugin(from compiz settings manager), the title bar gets solid, grey-like color (I also tryied mipmap, bilinear, gauss, i also activated the mipmap option in "window decorator plugin", but nothing). Actually, no transparency blurs what is behind it, it only gets dark, and i also clarify that mi current emerald theme is transparent.
The other blur plugin (the one that blurs the window when you move it) works great, which makes me think that there are no hardware problems (ati 3100). Other effects works very smoothly, really great, and mi CPU is an AMD quad core.

Thank you, and sorry for my english in case you didn't undestand something.

---

### Post by pp7 on 2008-11-05
Exactly same problem here and annoying.  Worked fine for me on 8.04.  All of a sudden doesn't work on 8.10.  Hope someone finds a solution cos I miss my blurred title bars.

---

### Post by nahuel_89p on 2008-11-05
Up to now, we are the only three people from all around the world with that very problem (plus another guy in another forum).

No answers for us. By now...

---

### Post by Psyker7 on 2008-11-12
afaik this is an ATI driver issue - same problem here with a 4850

---

### Post by timmy334 on 2008-12-16
You're not the only ones. I have the same exact problem. EVERYTHING works except the blur plugin. Motion blur works fine and so does every other plugin. I'm using an ATI Mobility Radeon x600 on my laptop. When I ran Hardy on here, everything worked perfectly. Once I installed Intrepid, blur no longer works. I am using the latest compiz and plugins compiled from Git.

---

### Post by nahuel_89p on 2008-12-17
So we are 4... we can set a guild now haha
I'm still with hardy... and never found a solution. Lets hope this thread revival can lead to a solution... We all share the same thing: ATI.

Greetings from Argentina

---

### Post by timmy334 on 2008-12-17
> **nahuel_89p said:**
> So we are 4... we can set a guild now haha
I'm still with hardy... and never found a solution. Lets hope this thread revival can lead to a solution... We all share the same thing: ATI.

Greetings from Argentina

Blur worked perfectly under Hardy for me. It was only when I switched to Intrepid that I had this problem.

---

### Post by Wartender on 2008-12-17
oh so THAT'S what the blur plugin is supposed to do! i had no idea cause nothing changed when i activated it, i'ma go see if it works haha.

---

### Post by SorinN on 2008-12-26
We are 5 now ( I mean - me too.. ).
..the rest of the world became increasingly  smaller.

---

### Post by pp7 on 2008-12-26
Nobody solved this yet?  Worked fine for me on the same hardware with Hardy.  No idea why it doesn't work now (with ibex).  Such a cool effect.

---

### Post by Wartender on 2008-12-27
hey i found something. in emerald, undert the emerald settings tab, it says compiz decoration blur type: you can select titlebar only! does this solve it? tell me! i wanna  know if i solved the problem!

---

### Post by pp7 on 2008-12-28
Nope!  Tried that ages ago along with other obvious things and no luck :(.  I might also be something to do with the latest version of the ati drivers that I'm using.  Anyone know how to downgrade drivers using envy-ng?

---

### Post by Wartender on 2008-12-28
darn. :( i really thought that might work... oh well.

---

### Post by MusicallyInspired on 2009-01-10
Same problem here. When enabling blur windows for Vista-like effect it just goes completely opaque instead of blurring what's behind it. I have an ATI X1650. Though I never had Compiz working in 8.04 because my fglrx driver wouldn't work. When I updated to 8.10 suddenly fglrx worked so I don't think it would work if I rolled back again, unfortunately. Hopefully there's an answer to this predicament soon.

---

### Post by biogerm on 2009-01-19
Same problem here on ati card x1100 and 8.10. Just noticed this today.. it's kind of hard to notice blur and "not transparent". Also tried to change all possible settings on both compiz and emerld. 

One question, which emerld theme are you using?

mine is called "vista q", by QUASAR, using vrunner as the default glass renderer.. i noticed that there is another renderer called "truglass" which maybe i haven't seen before. could it be another solution to this problem?

---

### Post by pp7 on 2009-01-19
I'm using the fuz2y theme with vrunner 0.2 frame engine.  I too have tried every possibly configuration that I know of but no luck.  I wonder if its anything to do with direct rendering.  I can't seem to enable direct rendering with good graphics performance on my T60p with ATI graphics card.

---

### Post by jmw86069 on 2009-02-01
To help debug where the problem may be occurring, I noticed that I *can* get blur to work if I enable "Focus Blur" under CompizConfig Settings Manager. I think the problem is mainly with the Alpha Blur, at least what I'd most like to see resolved. Importantly, blur does work, just not with all the Compiz settings.

Focus Blur is calling something which works, at least it creates a blur.
Alpha Blur calls something which doesn't create a noticeable blur, even when all window type are put into the "Alpha blur windows" field (e.g. toolbar | menu | utility | normal | dialog | modaldialog).

I also think the Blur Filter section has no [noticeable] effect. Changing all sorts of settings Bilinear/Mipmap/Gaussian have no effect, nor do any of their respective slider bars.  Blur occlusion doesn't appear to have any effect.

When I turn on Alpha Blur, and "normal" is in the "Alpha blur windows" field, it does affect the level of transparency. To observe, use Terminal with a Profile that has transparent background, and for me I had to readjust the transparency to see anything through it. Alpha blur appears to make it more opaque, but still no blur.

All that to say, good news is I think this is a bug that can be fixed -- and I suspect it's in the Compiz plugin code. I'll check those forums for any activity, maybe someone has fixed it in the daily build?

(I'm still stoked that I have suspend/resume with fglrx and Compiz!! Whoohoo!)

---

### Post by pp7 on 2009-02-01
Yea I too have intermittent suspend/resume and hibernate problems.  Please keep us posted on what you find concerning the alpha blur issue.

---

### Post by Can+~ on 2009-02-24
I've been looking all day for a solution to this. Sadly, it seems that fglrx stopped supporting blur.

---

### Post by pp7 on 2009-02-24
There was definately a time when it worked though.  Does anyone know what version of fglrx it worked with?  And is it possible to downgrade to this version?

---

### Post by Timotheus on 2009-03-14
Hi Guys.

Same problem here. I had nVidia 6200 and blur worked fine. After I've replaced it with Radeon HD 3650(agp version) (and fully reinstalled intrepid) blur stopped to work.

Same sympthoms on my grandma and grandpa macine: it has some built in radeon express. While it was running hardy blur worked, now it's running intrepid with latest updates and decoration blur doesn't work.

Same problem with my girlfriend's machine at work. She has two hd 3650 with crossfire chain enabled. Machine is running intrepid with latest updates. Decoration blur does not work.

All three machines are showing same sympthoms: when blur is enabled, decoration becomes opaque and performance lowers dramatically.

My nVidia 6200 is now installed in my girlfriend's home PC and decoration blur works fine there with more than acceptable performance. Machine is running intrepid with latest updates..

So.. three more PCs. Hello from Russia =)

I think the problem is with latest [s]ATI[/s]AMD drivers and maybe with driver-to-kernel intercommunication procedure. As I understand, blur is a kinda shader, so maybe the problem is with shader model implementation.

Anyway I doubt we can fix this ourselves =(.

I see only two solutions:
1. [s]ATI[/s]AMD fixes the bug in their drivers.
2. Emerald changes blur implementation so it'll work on [s]ATI[/s]AMD adapters.

I think, first solution is more preferable, cause AMD linux videodrivers are REALLY CRAPPY and they MUST fix them. (there is another sad story how I configured dual display mode under linux with ati adapter. with nVidia it was made in two clicks.) So guys, has anyone reported this bug to AMD? If no, maybe we should do this?

---

### Post by andy16666 on 2009-10-04
I have an ATI Radeon HD 4200 and I've got this same bug. I'm going to look into reporting it to AMD, but I suspect they already know.

---

### Post by andy16666 on 2009-10-04
[http://ati.cchtml.com/show_bug.cgi?id=1488](http://ati.cchtml.com/show_bug.cgi?id=1488)

The bug seems to have been reported some time ago. It would seem this is as close to an official bug database for the fglrx drivers as I am likely to find.

---

### Post by pp7 on 2009-10-04
Bottom line is when buying a new machine make sure it has an nvidia graphics card as it's better supported on linux

---

