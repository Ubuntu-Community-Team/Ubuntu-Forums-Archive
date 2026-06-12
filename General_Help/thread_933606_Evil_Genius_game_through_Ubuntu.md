---
title: "Evil Genius game through Ubuntu?"
date: 2008-09-29
forum: General Help
---

### Post by College_Trained on 2008-09-29
Hey all,

I don't know if anyone has heard of the game Evil Genius but it is a Windows game that I would love to play using Ubuntu. This is really the only thing keeping me from trashing XP off the other partition, as I am an occational gamer. I'm just way too lazy to restart into Windows just to play it.
Anyway, it's installed on my XP partition and needs the CD for it to play properly in Windows.
Does anyone know how I can get it to play in Ubuntu? I tried opening the executable with wine and it told me to check that the CD was an original. The CD is the one that came in the original packaging from the store.
Anyone have any ideas?

Thanks,
~College_trained

---

### Post by eZtaR on 2008-09-29
[The wine AppDB](http://appdb.winehq.org/objectManager.php?sClass=version&iId=2945) is always a good place to start when you're having troubles with windows apps :)
[quote=HOWTO]After two or three years of waiting, I am glad to say that this game finally works almost perfectly. Hope this howto is helpful.

For the game to run properly you need native quartz.dll and msvcrt.dll. You can get these online.

Once downloaded place these under: home/youusername/.wine/drive_c/windows/system32

Perhaps you dont need to do the following step but I did it anyway which is to rename the existing quartz.dll and msvcrt.dll in the same directory for backup and just to be sure that wine picks up the native copies.

 With the files placed in the system32 directory run wine configuration usually accessible from the ubuntu applications menu. You can always type winecfg at the terminal to run it.

Next step is to tell wine to use native dls. Goto the libraries tab and from the drop down menu select quartz and cick add. Do the same for msvcrt. Once these are added you need to select each file in the list (i-e: quartz and msvcrt) and click Edit from the options given select "Native (Windows)" for both of them.

That covers pretty much everything. Apart from the minor sound glitches here and there the game runs perfectly (worthy of a Platinum but I'll keep it at Gold unless suggested otherwise.[/quote]

---

