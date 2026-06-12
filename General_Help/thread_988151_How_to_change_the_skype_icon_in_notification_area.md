---
title: "How to change the skype icon in notification area?"
date: 2008-11-20
forum: General Help
---

### Post by olavjunior on 2008-11-20
I'm using the Moomex ultimatum theme, so the skype icon is much smaller then all the rest. I want to remove or change it, so does anyone know where it's located? (Tried locate skype, but no luck with the icon)

---

### Post by eternalnewbee on 2008-11-20
Hi there. Right-click on the icon, click on properties, and take it from there. Either choose No icon, or navigate to a folder where you have another icon which you want to replace it with.
Hope this helps you.

---

### Post by olavjunior on 2008-11-20
Ehh.... have you actually tried this with Skype? Right-clicking doesn't show "properties", but there's "options" though, but I can't find any choices about icons in Skypes "options"

---

### Post by eternalnewbee on 2008-11-20
> Ehh....
No I haven't.

---

### Post by eternalnewbee on 2008-11-20
Check this out: (notice the cursor)

---

### Post by eternalnewbee on 2008-11-20
Now this:

---

### Post by eternalnewbee on 2008-11-20
And:

---

### Post by eternalnewbee on 2008-11-20
And now (I clicked on the icon)

---

### Post by eternalnewbee on 2008-11-20
I double-clicked on the Amarok icon. Can you see the cursor? Look at the panel.
Hope this helps...

---

### Post by eternalnewbee on 2008-11-20
So. Add skype to laucher panel, and change it there, and see whether it effects the icon in the notification area.
This is the best I can do for you...

---

### Post by olavjunior on 2008-11-20
No, it doesn't. Even though a launcher is placed on the panel with a custom icon, it doesn't affect the notification icon...

---

### Post by fuzZzball on 2008-12-27
He does not mean the Desktop icon, but the icon used in the notification area's, as in the Ring Switcher or the default Notification Area on a gnome-panel. When you change the Skype item with some icon set, the icon on all .desktop shortcuts get replaced, but in some occasions the old icon is still used. I've been struggling for this one for the last few days. Have search the Filesystem for all *.png, *.xpm, *.svg, *.svgz, but no luck. 

If you know where the icon is located, please let me know :D ..
Cheers :D

---

### Post by k3ttc4r on 2009-02-22
sorry to open up a dead thread, but -- does anybody have a solution for this problem that ACTUALLY WORKS? i've been googling this sh*t for quite a while now, and i can't seem to find a solution. i'm starting to guess that the icons are hard-coded into skype.

anybody got experience with reshacker under wine? ;)

---

### Post by tenzinphoto on 2010-03-21
seems no one has an answer for this yet???  i still have no idea how to replace the default icons for items in the notification area (eg: gnome-power-manager, compiz fusion icon, etc).

been struggling for weeks on this.  has no one ever tried customizing this panel???

---

### Post by Apache0c on 2010-03-22
I've been searching google for answers as well.

My icon theme changed all the icons in my whole system except for that one and two others.

If I just knew where the icon was stored, I could swap it out...

Any attention from advanced users to this issue would be much appreciated. Especially because it's gone on so long without being solved and it seems to be such a simple issue.


*edit* Why is this marked solved? Can we get a mod to change that?

---

### Post by Schmal on 2010-04-29
Okay, I'm having the same problems, but I think I'm getting somewhere. I don't have a solution to post, but as soon as I find one, you'll know. My theory is that it is in a SVG file in the notification panel directory. I might be wrong, but it's worth a shot.

---

### Post by Apache0c on 2010-05-02
> **Schmal said:**
> Okay, I'm having the same problems, but I think I'm getting somewhere. I don't have a solution to post, but as soon as I find one, you'll know. My theory is that it is in a SVG file in the notification panel directory. I might be wrong, but it's worth a shot.
Awesome. Let us know. :popcorn:

---

### Post by Vince N on 2010-05-02
Also interested in this.  I want to create a Skype Notification Icon that matches the white and grey look of the rest of the notification icons in the new Lucid Release.

---

### Post by techunit on 2010-05-02
Some one needs to contact skype about changing some of the setting surrounding themeing becaus of incompatibilities with the latest releases.

---

### Post by Vince N on 2010-05-03
> **techunit said:**
> Some one needs to contact skype about changing some of the setting surrounding themeing becaus of incompatibilities with the latest releases.

Besides the Notification Icon were working on what theming issues are you refering too?

I did note that it doesn't play well by default with dark themes (the text in some menu's is also dark) but that can be fixed by going to Options -> General -> Choose Style and selecting "System Settings".  It would be nice if Skype used that as the default.

---

### Post by CujoAK47 on 2010-06-13
I figured out the solution to this problem, made an account and everything just for you guys! xD


Anyways, I was having trouble finding out how to change the Skype icon as well because the option "Change Icon..." was grayed out.
The solution is quite simple actually.

Unfortunately, I still use windows, so heres how to do it in there.. hopefully you can figure out what to do in ubuntu however that works.

1. Delete the shortcut your using (the one with grayed out option)
2. Go to X:\Program Files\Skype\Phone and make a shortcut of Skype.exe (send to desktop)
3. Go to properties of newly created shortcut and it should have the option to "Change Icon..." available.
4. ...
5. Success!


Hope this works for you guys! :D

---

### Post by Egor Zvukov on 2010-06-14
> **CujoAK47 said:**
> I figured out the solution to this problem, made an account and everything just for you guys! xD


Anyways, I was having trouble finding out how to change the Skype icon as well because the option "Change Icon..." was grayed out.
The solution is quite simple actually.

Unfortunately, I still use windows, so heres how to do it in there.. hopefully you can figure out what to do in ubuntu however that works.

1. Delete the shortcut your using (the one with grayed out option)
2. Go to X:\Program Files\Skype\Phone and make a shortcut of Skype.exe (send to desktop)
3. Go to properties of newly created shortcut and it should have the option to "Change Icon..." available.
4. ...
5. Success!


Hope this works for you guys! :D

WTF??? #-o

---

### Post by cespinal on 2010-06-17
LMAO I just had a blast reading this 2 year old topic.... lets do a shameless bump up this b..... that skype icon has been bothering us for sooooooo long....

---

### Post by redman5087 on 2010-06-30
It's clearly that the skype notification icon is hard coded in the the skype binary.
Does someone now how to extract it and put a new one back into the binary?

---

### Post by Vince N on 2010-07-02
I doubt it.
 
This is one reason I hate skype. It's closed and propriatary. We have no access to the source and there probobly isn't an easy way do extract the icon.  Even if there is, it's proboably a violation of the EULA.  Unfortunatly I know too many people who use skype to dump it and go with something more open source and because the codec is so closed theres really no good open source implimentation of the client.

---

### Post by floopy1962 on 2010-07-07
I hate skype for that ugly icon:o can i just remove from there? i use pidgin now...

---

### Post by Thomas B. on 2010-07-18
WTF?? WE'VE BEEN DEALING WITH THIS ISSUE FOR 2 YEARS!! I want a sexy Skype icon!!

---

### Post by Zookalicious on 2010-09-07
> **Thomas B. said:**
> WTF?? WE'VE BEEN DEALING WITH THIS ISSUE FOR 2 YEARS!! I want a sexy Skype icon!!

That's what happens when software is closed.

---

### Post by rajadain on 2010-10-14
Bump. Faenza actually comes with gorgeous icons for Skype statuses (statii?). They're just sitting there, waiting to be included.
At least Dropbox is doing it soon. I hear the experimental build has customizable icons. Too bad my data is too valuable to run experimental builds :P

---

### Post by Vince N on 2010-10-15
What does dropbox have to do with skype?  Or did I miss something?

---

### Post by agarciamog on 2010-11-11
Discouraging. ](*,)

We should put a bounty on this.

---

### Post by tora201 on 2010-11-27
Yeah, sucks... wish we could have a nice skype notification icon that does not reside in that horrible Gnome "notification area"....

---

### Post by daniel.r.roberts on 2011-01-15
Well I have the solution if this worries you. The software you need for this kind of thing is called a disassembler. You take the Skype binary open it in a software program such as PE Explorer or Linux equivalent. 

Before you start make a backup of the original binary. It is located on my system in usr/bin.

Then you extract the resource you want to change, in this case the icon (one of the easiest to change). Then you change it to your needs using something like gimp (can it so icons?). Once this is done you replace the icon using your disassembler. Now for everyones benefit you should also use a program called a patch maker to make a patch by comparing the original to the new. Release patch, job done.

I mite do this later if I can find a decent disassembler for Ubuntu.

---

### Post by daniel.r.roberts on 2011-01-15
Well I have the solution if this worries you. The software you need for this kind of thing is called a disassembler. You take the Skype binary open it in a software program such as PE Explorer or Linux equivalent.

Before you start make a backup of the original binary. It is located on my system in usr/bin.

Then you extract the resource you want to change, in this case the icon (one of the easiest to change). Then you change it to your needs using something like gimp (can it do icons?). Once this is done you replace the icon using your disassembler. Now for everyones benefit you should also use a program called a patch maker to make a patch by comparing the original to the new. Release patch, job done.

I might do this later if I can find a decent disassembler for Ubuntu. Hope this helps

---

### Post by vendetta red on 2011-02-12
> **daniel.r.roberts said:**
> Well I have the solution if this worries you. The software you need for this kind of thing is called a disassembler. You take the Skype binary open it in a software program such as PE Explorer or Linux equivalent.

Before you start make a backup of the original binary. It is located on my system in usr/bin.

Then you extract the resource you want to change, in this case the icon (one of the easiest to change). Then you change it to your needs using something like gimp (can it do icons?). Once this is done you replace the icon using your disassembler. Now for everyones benefit you should also use a program called a patch maker to make a patch by comparing the original to the new. Release patch, job done.

I might do this later if I can find a decent disassembler for Ubuntu. Hope this helps

While I'm not certain of the legality of doing so, I'd certainly be happy to see the ugly skype defauly notification icon(s) gone and replaced with the faenza theme.

---

### Post by Habitual on 2011-02-12
```
cd /usr/share
find `pwd` -name skype.* -type f

```

It's one of those.
Perhaps GIMP can give you a color shade to suit your theme?

My best guess is a skype.svg since the Notification Area icon does change size if the panel is re-sized.

---

