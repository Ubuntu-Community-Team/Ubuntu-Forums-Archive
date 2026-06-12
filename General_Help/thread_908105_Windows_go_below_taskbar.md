---
title: "Windows go below taskbar"
date: 2008-09-02
forum: General Help
---

### Post by simonuk on 2008-09-02
Ok, I'm new but having a lot of fun!

I have solved a number of problems but one I have must be an easy one but I can't find an solution:

Problem: Any window longer in height than the screen goes down past the task bar. I can't click on any save, ok or close buttons because they are down way past the bottom task bar. Maximising the window just maximises from the top so I still can't see the buttons below.

How can I set up windows so they only use the screen size available?

I'm using an MSI wind notebook with a 1024x600 resolution if that helps.

---

### Post by arch0njw on 2008-09-02
Hello there.  Give this a try:

1. Right click on an empty place on the kicker (that's the name of the task bar)
2. Choose "Hiding" from the left column
3. Select the radio button that reads "Allow other _w_indows to cover the panel"

If that doesn't work, you can at least get to those application by either (a) setting the panel to automatically hide, or (b) display the "hide buttons" so you can manually hide the kicker.

I think you will find that once you get windows moved into the non-kicker area of the screen, they will honor the space taken up by the kicker.

Hope that helps!

---

### Post by simonuk on 2008-09-02
Many thanks for helping :)

When I right click the only options I get are "Task manager settings / Panel settings / Add widgets / Remove this task manager"

Any ideas?

---

### Post by arch0njw on 2008-09-02
simonuk, *now* I'm with you.  You're using KDE 4.x.  That explains the difference.  I still like my "stone ages" KDE 3.5.x, but I think I can still help you.

1. you can use keystrokes to move a window.  Press alt-f3, then "M".  You can then move the window.  If you, like me, have remapped the keyboard to use "windows" mappings, then this is "alt-space" then "M:.

-OR-

2. you can fiddle with the panel and make it different sizes.  You should have an icon to the far right of the panel that looks like some kind of little swirly thing (if you hover over it, it is gold/yellow).  You can click on that to resize the panel, and change its location (left, center, right).  That would help make any title bars of hidden windows more accessible.

Let me know if that helps.

---

### Post by simonuk on 2008-09-02
Hi, thanks for getting back to me.

The first option still doesn't work because I can't move the top higher than the top of the screen so I can't get to see the bottom of the windows.

Your number 2 didn't work either... or so I thought.... KDE4 has it on the left hand side and you can left or right click to bring up more options.

I still cannot easily get to the bottom of any window much bigger than the screen size but it is a little easier on windows that are only slightly larger than the screen (I can use "keep above others" and "full screen" for these).

In M$ if you have any window bigger than the screen that window gets a scroll bar so you can move up and down the window. I'm amazed that it appears k/ubuntu cannot do such a simple but vital thing....

---

### Post by arch0njw on 2008-09-02
It seems you are able to see the window borders.  What about resizing the window?

---

### Post by simonuk on 2008-09-02
I can make the window wider or narrower but not taller or smaller. On some windows like a browser or the quick launcher I have the scroll bars. Its just on windows like changing the appearance or other core windows that I have no ability to apply or OK anything I do.

---

### Post by arch0njw on 2008-09-02
What is the window?  I have a larger screen, but I can make Dolphin 360px high and I can shrink firefox down to about 27px tall (which is useless, but possible).

I'm wondering if this a limitation of the specific window.

Also, is it possible for you to increase your resolution at all (e.g., 1024x768 )?

---

### Post by simonuk on 2008-09-02
Wish I could increase the res but it's one of the new mini laptops (Google MSI wind). 

I can reduce some windows like firefox and I can scroll others but core windows like the ones to change the appearance and display are so long they go waaaaay down below the task bar. I can access maybe the top 30% of the window and that's it, everything else like the "apply" and "close" button just sit several hundred pixels below the taskbar and I just can't get to them.

---

### Post by arch0njw on 2008-09-02
Resolution:  understood.  Off-topic, when you get a chance, can you tell me what you think of that?  I'm pondering getting something like that to replace and ancient and heavy HP Pavillion.  But on to the issue at hand...

What window *exactly* are you looking at (e.g., "Display - System Settings, Display & Orientation)?  I have tried going into System Settings and I can resize that window no matter what area of it I am in (Window Behavior, Display, etc.).  I can see all of the buttons, and scroll bars appear when critical, selectable items no longer fit within the window's dimensions.

Also, please go to the KMenu, choose "Applications", scroll down to "Help", open Help, click "Help | About KDE", and post the version reported there.  I am using 4.1.  I wonder if you might be using 4.0.x -- there have been measurable improvements since then.

---

### Post by simonuk on 2008-09-03
A good example would be System settings - window behavior. Although I have a scroll bar for the options inside "Focus" I can't see or get to the bottom of the window. There is no scroll bar for the actual main window.

Likewise if I click on System settings and "Appearance" all I can see is up the "icons" option on the left. There is no scroll bar to get to the bottom of this window either.

I'm using KDE 4.0.3 which is the default for Kubuntu.

As to your question about this laptop... best thing I ever did. I spent 3 weeks researching all exisiting and up-coming notebooks and went for this one for 2 main reasons:

1. A 10" screen makes life easier.
2. A proper sized keyboard makes a massive difference if you touch type like I do.

The MSI wind is a great piece of kit and I don't regret this one over all the others (I have seen most at close hand now and still prefer this one over the others).


Only downside for me is it has the "FN" key at the end instead of the "Ctrl" key which is slightly annoying.

Hope that helps :)

---

### Post by arch0njw on 2008-09-03
I recommend you upgrade to 4.1.  Add this repository, then update:
deb [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu) hardy main

I usually install from konsole, and the packages you should make sure you upgrade are: kubuntu-kde4-desktop kdeplasma-addons

I saw a site which also recommended:   amarok-kde4 kontact-kde4 kate-kde4 kmail-kde4.  You can also query what other KDE4 packages are available from the command line:  dpkg -l *kde4*

I usually don't like it when people reply with "upgrade and it will fix it", but 4.0.x was kind of rough.  4.1 is much more refined, and well worth the upgrade.  I was *not* impressed with 4.0.x, but I could see where they were headed with it; 4.1 is definitely better.

---
Thanks for the info on the netbook.  I have been considering the newer EeePc, and I'll put the Wind on the list.

---

### Post by simonuk on 2008-09-03
Yay you're my hero!

Upgraded to KDE 4.1 and all my problems have gone away!

There was something screwy for sure in 4.0 that didn't like notebooks running in 1026x600

---

### Post by arch0njw on 2008-09-03
Hurray!  Glad to hear it.  I remember the brief encounter I had with KDE 4.0.x, and there were many things I didn't like about it -- window resizing is a vague memory.

I'm glad to hear this is working for you now.  Enjoy!

---

### Post by zeltak on 2008-09-22
Hi Guys

I have been running kde 4.1 for a few weeks on the msi wind and i love it. I still have the same problems with not being able to access the ok/apply etc..button on the kde 4 PIM. its really annoying since i cant add any new contacts appointments etc...is there any solution found for this in the meanwhile since the last post?

Thx

Zeltak

---

### Post by arch0njw on 2008-09-22
This sounds like a different issue.  The solution for simonuk was to install KDE 4.1.

I'll see what I can do to replicate this in a VM.  I'll make my resolution 1026x600 like it is on the Wind and see what happens.

---

### Post by zeltak on 2008-09-23
thx arch0njw for the effort!

its greatly appreciated, please let me know if you find any solution, kde 4.1 rocks on the msi wind and this is the only issue thats really still annoying me to death

Zeltak

---

### Post by arch0njw on 2008-09-23
@zeltak:  I didn't get ALL the way there, but I got far enough.  I tried adding a new contact to KDE4 PIM and noticed that there is a minimum size the "Edit Contact" window is allowed to be.

One thing you might try is making a few of your fonts smaller.  That might adjust everything just that crucial amount to let you get to the buttons at the bottom.  This isn't an ideal long term solution, but it should be "good enough" for now.  I will file a bug against KDE4 PIM because this could benefit from being fixed.

Also, FWIW, ctrl+enter should be the equivalent of "OK" and esc (or alt+f4) should be the equivalent of cancel.

---

### Post by arch0njw on 2008-09-25
> **zeltak said:**
> thx arch0njw for the effort!

its greatly appreciated, please let me know if you find any solution, kde 4.1 rocks on the msi wind and this is the only issue thats really still annoying me to death

Zeltak

How's it going Zeltak?  Did changing the font size help any?

---

### Post by zeltak on 2008-09-26
Hi arch0njw

Changing the fonts did help a bit (thx alot for the tip!) but on some programs (like the Kaddress contact editor and some gnome/GTK programs) its still not enough. 
Thx again for the help

Zeltak

---

### Post by arch0njw on 2008-09-26
@all:  I have now filed a bug against KDE 4's Kontact.  It is in the hands of the KDE team now.
[https://bugs.kde.org/show_bug.cgi?id=171699](https://bugs.kde.org/show_bug.cgi?id=171699)

---

