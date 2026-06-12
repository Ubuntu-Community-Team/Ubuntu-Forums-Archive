---
title: "Please help with my Dock/AWN Manager - cant add icons/programs"
date: 2008-09-07
forum: General Help
---

### Post by PsychedelicWonders on 2008-09-07
Alright I've tried to drag and drop icons/programs right onto the dock and that doesnt work.

Anyone know what I'm doing wrong?

I've also tried going to preferences>applets and tried adding the icons via that route and still a no go, dont have the programs I'm looking for...

Opera, frostwire, terminal etc.

Also, I want my dock to look like the dock in the following screenshot... does anyone know how I go about making it look like that?

---

### Post by zipperback on 2008-09-07
It would be best if you provided an actual screenshot of your desktop, "Applications -> Accessories -> Take Screenshot", and not use a screenshot of your browser showing the screenshot of a web page.

It just makes more sense to show your actual desktop.

---

### Post by PsychedelicWonders on 2008-09-07
here is my screenshot with what my dock looks like.

I want it to look like the other one and be able to add programs to it.

---

### Post by dai_vernon on 2008-09-08
You don't add applets to your dock to get applications to go, you use launchers.  Drag and Drop isn't supported like OSX's dock.

Instructions:
1) Go to your gnome menu and navigate to the app you want
2) right click > add launcher to panel (launcher should add to your top pane)
3) right click on new launcher > properties.
4) Copy the 'command' section (example: openoffice.org writer is ooffice -writer %U)
5) Open AWN manager
6) Launchers
7) Add
8) Choose name, paste command from top pane launcher into the command area, click on icon spot to navigate to proper icon.
9) OK
10) Position where you want in the app list on the Launcher page of AWN manager
11) restart Avant Window Navigator (I ususally use the force quit applet that you can add to your top pane)
12) Enjoy
13) ????
14) Profit

---

### Post by dai_vernon on 2008-09-08
Also, the dock in that screenshot has a special theme, is set to 3D bar, and the icons are positioned further up the bar (offset).  As to what the theme is I don't know, but gnome-look.org, google, or the AWN forums might help.

---

### Post by tuxxy on 2008-09-08
[QUOTE=dai_vernon;5747946]You don't add applets to your dock to get applications to go, you use launchers.  Drag and Drop isn't supported like OSX's dock.


Weird, I can drag & drop fine :confused:

---

### Post by PsychedelicWonders on 2008-09-08
> **dai_vernon said:**
> You don't add applets to your dock to get applications to go, you use launchers.  Drag and Drop isn't supported like OSX's dock.

Instructions:
1) Go to your gnome menu and navigate to the app you want
2) right click > add launcher to panel (launcher should add to your top pane)
3) right click on new launcher > properties.
4) Copy the 'command' section (example: openoffice.org writer is ooffice -writer %U)
5) Open AWN manager
6) Launchers
7) Add
8) Choose name, paste command from top pane launcher into the command area, click on icon spot to navigate to proper icon.
9) OK
10) Position where you want in the app list on the Launcher page of AWN manager
11) restart Avant Window Navigator (I ususally use the force quit applet that you can add to your top pane)
12) Enjoy
13) ????
14) Profit

I seem to be getting everything... but when I go to click on an icon spot it brings up nautilus and I dont know where to navigate to find opera to find an icon?

If this works, then great, but there has got to be an easier way?

It once allowed me to drag and drop icons, but they never stuck... but it still allowed me?

---

### Post by PsychedelicWonders on 2008-09-08
> **dai_vernon said:**
> Also, the dock in that screenshot has a special theme, is set to 3D bar, and the icons are positioned further up the bar (offset).  As to what the theme is I don't know, but gnome-look.org, google, or the AWN forums might help.

So should I just post that screenshot in the AWN forums to see what they think it is?

---

### Post by dai_vernon on 2008-09-08
> **PsychedelicWonders said:**
> I seem to be getting everything... but when I go to click on an icon spot it brings up nautilus and I dont know where to navigate to find opera to find an icon?

If this works, then great, but there has got to be an easier way?

It once allowed me to drag and drop icons, but they never stuck... but it still allowed me?

I don't know what the deal is with drag and drop; it never worked for me.

For the icon thing, I just googled for an icon of whatever program I wanted.  Look for a pic with all transparent but the icon itself so you don't get splotches of white.

Attatched pic is a highly outdated version of my dock.

---

### Post by dai_vernon on 2008-09-08
Also, if you right click on the launcher when its on your top pane and go to properties and click on the icon, you will find the path to the icon.

Also also, I found that dragging and dropping the launcher from the top pane to the dock seems to work sometimes.

Try that too.

---

### Post by PsychedelicWonders on 2008-09-08
> **dai_vernon said:**
> I don't know what the deal is with drag and drop; it never worked for me.

For the icon thing, I just googled for an icon of whatever program I wanted.  Look for a pic with all transparent but the icon itself so you don't get splotches of white.

Attatched pic is a highly outdated version of my dock.

I tried and kept getting all different sizes of icons.

There has to be something built-in that I can just activate?

---

### Post by PsychedelicWonders on 2008-09-08
> **dai_vernon said:**
> Also, if you right click on the launcher when its on your top pane and go to properties and click on the icon, you will find the path to the icon.

Also also, I found that dragging and dropping the launcher from the top pane to the dock seems to work sometimes.

Try that too.

Alright I found the area... but the opera icon is invisable and doesnt seem to let me click it?

---

### Post by dai_vernon on 2008-09-08
That I don't know - perhaps duplicate the file and try on the copy?

---

### Post by PsychedelicWonders on 2008-09-08
yeah I tried yours, but couldnt select the icon.. it was invisable?

Check out my screenshot right above your last post...

---

### Post by PsychedelicWonders on 2008-09-08
> **dai_vernon said:**
> That I don't know - perhaps duplicate the file and try on the copy?

how should I go about that one?

---

### Post by dai_vernon on 2008-09-08
ctrl-click and drag the image to another directory, this copies it.

now try to load that image

---

### Post by PsychedelicWonders on 2008-09-08
right now I just have the icon saved on my desktop... what file should I move this to so that it is no longer on my desktop?

Should I just make a new dock icon folder?

If so, where exactly should I create it?

---

### Post by dai_vernon on 2008-09-08
Doesn't really matter, man.  Any directory you can write to so you can save the files there.  I made an icons folder in my pictures folder, so the path was /home/name/Pictures/Icons

just make it something you'll remember

---

### Post by PsychedelicWonders on 2008-09-08
wait... I think i got it to work.

But its not showing up in my dock?

Do I need to log in/out?

Hmm.  Logged in/out and its still not showing up?

It shows it under launchers?

---

### Post by dai_vernon on 2008-09-08
Try using this opera icon instead.  Perhaps yours is corrupted.

If this doesn't work, I'm out of ideas - if you still can't load icons into your thing go ask on AWN forums.

---

### Post by dai_vernon on 2008-09-08
Restart AWN

---

### Post by PsychedelicWonders on 2008-09-08
No I got it.. check my above post now for a new problem...

I logged out/in... that didnt do anything.

How do I restart just the awn program?

---

### Post by dai_vernon on 2008-09-08
> **PsychedelicWonders said:**
> wait... I think i got it to work.

But its not showing up in my dock?

Do I need to log in/out?

Hmm.  Logged in/out and its still not showing up?

It shows it under launchers?

Your AWN doesn't appear to be on.  And yes, it should show under launchers.  Delete those two launhers without any use - they can be causing AWN to get confused.  AWN is not bug-free.

---

### Post by PsychedelicWonders on 2008-09-08
It wont let me delete or remove them?

How do I turn the awn on then?

fyi I added those launchers via the awn managers list... so they should work fine?

But the funny thing is, the trash can doesnt register there is trash to be emptied?

The otherone is a "desktop" icon and seems to work fine.

---

### Post by dai_vernon on 2008-09-08
> **PsychedelicWonders said:**
> No I got it.. check my above post now for a new problem...

I logged out/in... that didnt do anything.

How do I restart just the awn program?

I added a force quit applet to my top pane (right click, add to panel, force quit) that you click on and then click into a window you want to kill.  Afterwards, I restart it from the gnome menu

---

### Post by dai_vernon on 2008-09-08
> **PsychedelicWonders said:**
> It wont let me delete or remove them?

How do I turn the awn on then?

Gnome menu > Accessories > Avant Window Navigator

---

### Post by PsychedelicWonders on 2008-09-08
sorry it is on, I just have it hide below the screen until I scroll my mouse over it.

I've logged out several time, no new opera icon?

---

### Post by PsychedelicWonders on 2008-09-08
fyi those two icons on my dock were applets, not launchers.. does this make a difference?

---

### Post by dai_vernon on 2008-09-08
> **PsychedelicWonders said:**
> sorry it is on, I just have it hide below the screen until I scroll my mouse over it.

I've logged out several time, no new opera icon?

Did you try it with my opera icon I gave you?  If not, do that and then restart AWN.  If so, I'm out of ideas and you're on your own.

---

### Post by dai_vernon on 2008-09-08
> **PsychedelicWonders said:**
> fyi those two icons on my dock were applets, not launchers.. does this make a difference?

I don't think so - if they were in your launcher section it could be messing things up.

---

### Post by PsychedelicWonders on 2008-09-08
I didnt use your icon, but I was able to finally activate my duplicate icon and as you can see here...

It shows the opera program ready... but ive restarted awn and it isnt showing up?

Now i removed those two applets and still one of them shows up on the dock (desktop) whats up with that?

---

### Post by PsychedelicWonders on 2008-09-08
> **dai_vernon said:**
> I don't think so - if they were in your launcher section it could be messing things up.

well I loaded them under the applet screen, but apparently it put some type of ghost file under launchers... and now they arent letting me delete or remove them.

How do I force it to do so?

If I'm trying to make my dock look like that one from my original thread... do I need to delete this version of the awn dock manager I have?

Or is it more like a "skin" to get the particular looking dock I want?

---

### Post by dai_vernon on 2008-09-08
> **PsychedelicWonders said:**
> I didnt use your icon, but I was able to finally activate my duplicate icon and as you can see here...

It shows the opera program ready... but ive restarted awn and it isnt showing up?

Now i removed those two applets and still one of them shows up on the dock (desktop) whats up with that?

I don't know.  As I say, AWN is buggy.  Try this whole thing again with a different app than opera.  If it keeps going on, then its systemic and you need to talk to the AWN people.

If it does keep going, go to Synaptic and do a complete removal of all the AWN libraries and reinstall them.  If it keeps going then, go bug AWN

---

### Post by dai_vernon on 2008-09-08
> **PsychedelicWonders said:**
> well I loaded them under the applet screen, but apparently it put some type of ghost file under launchers... and now they arent letting me delete or remove them.

How do I force it to do so?

If I'm trying to make my dock look like that one from my original thread... do I need to delete this version of the awn dock manager I have?

Or is it more like a "skin" to get the particular looking dock I want?

AWN occasionally forgets to garbage collect and leaves crap in your launcher section - those things aren't the applets, its just AWN being queer.

You should be able to skin it just fine if you find the proper theme.

---

### Post by dai_vernon on 2008-09-08
> **PsychedelicWonders said:**
> well I loaded them under the applet screen, but apparently it put some type of ghost file under launchers... and now they arent letting me delete or remove them.

How do I force it to do so?

If I'm trying to make my dock look like that one from my original thread... do I need to delete this version of the awn dock manager I have?

Or is it more like a "skin" to get the particular looking dock I want?

Also, please respond with new posts instead of edits.  it makes it very easy for me to miss new developments if you edit your posts instead of making new ones

---

### Post by PsychedelicWonders on 2008-09-08
alright, thanks for everyting, I've got to call it a night now and will attempt a removal and new installation of it tomorrow.

I'll report my findings here.

Thanks.

---

### Post by dai_vernon on 2008-09-08
> **PsychedelicWonders said:**
> alright, thanks for everyting, I've got to call it a night now and will attempt a removal and new installation of it tomorrow.

I'll report my findings here.

Thanks.

Its cool man - I hope everything goes well tomorrow.  If not I'll be here, perhaps having thought of something new while not doing organic chemistry studying.

---

### Post by PsychedelicWonders on 2008-09-08
Organic chemistry huh?  I like you even more now.  :)

Focus on finding some good alkaloids in animals from the ocean... there is a vast psychedelic garden that is untouched...

:)

What is the most effective way for me to delete this dock I have and install a new one... perhaps one with less bugs?

I dont remember which dock I downloaded... but I do remember it had all the the extras, all the gadgets and everything else... so I would def like the same style... just no bugs.

And then I'd like a new skin... the one I have is very boring.

---

### Post by dai_vernon on 2008-09-09
Go to synaptic and search for avant and awn.  Mark all packages relevant to avant / awn for 'complete removal'.

Then download them again - I use all the ones appended with -trunk as they get updated more often.

For skins, googling for Avant WIndow Navigator themes or some such will turn up plenty

---

### Post by PsychedelicWonders on 2008-09-09
I dont know what happened, but after a total system restart, it seems my dock is working properly.

It seems that those applets I had installed were messing it all up.

I can even drag and drop application icons onto the dock.... which is sooooooooo much easier.

Now it seems I have 2 sections to my dock?

The left side seems to be icons of applications that I just have shortcuts for, and the right hand side seems to be applications I have open?

Is there anything else to it?

I have an icon for my 2nd hdd on my desktop, I really want to keep my desktop totally clean, and I want to put this hdd icon on my dock as well.

Now this one did not allow me to drag and drop it... anyone have any ideas how to get this done?

I will search for a new skin now with that google search... thanks.

Will there be a walkthru on how to install the skin with the actual skin usually?

I've never done it before and dont know what to do?

Also, how do I re-arrange the icons on the dock how I want them?

Thanks for everything.

---

### Post by PsychedelicWonders on 2008-09-09
does this look like a safe download site... I believe this is the style of dock I am looking for...

[http://www.queervisions.com/img/awn/awn_3dglass.jpg](http://www.queervisions.com/img/awn/awn_3dglass.jpg)

Seems to be on par with the one I posted in this original thread doesnt it? (see screenshot again)

I mean are there really any other dock skins out there than what is listed on this page?...

[http://www.queervisions.com/arch/2007/10/awn_avantwindow.html](http://www.queervisions.com/arch/2007/10/awn_avantwindow.html)

Do the icons come with each new skin?

Or am I able to also get different icons for various applications with any dock skin?

---

### Post by PsychedelicWonders on 2008-09-15
Hmm just went to that site to try and download the Glass 3D and I clicked on the name, which is supposed to be the file and get this...

---

### Post by PsychedelicWonders on 2008-12-05
anyone know where I can download a safe version of this kind of dock...

[http://www.queervisions.com/img/awn/awn_3dglass.jpg](http://www.queervisions.com/img/awn/awn_3dglass.jpg)

Perhaps in Cario instead of AWN?

---

