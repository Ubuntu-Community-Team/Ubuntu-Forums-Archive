---
title: "keyboard multimedia keys not working in 8.10"
date: 2008-10-31
forum: General Help
---

### Post by ilovelinux33467 on 2008-10-31
Hi I downloaded 8.10 and installed it (fresh install). Everything works fine except the multimedia keys on my keyboard (Its a Microsoft Wireless Laser Keyboard v2.0). What I find strange is that it worked on hardy 8.04. Help?? :confused:

---

### Post by ilovelinux33467 on 2008-10-31
I hate to bump this but I am really desperate to get this working

---

### Post by Izkata on 2008-11-01
Same here, except I did an upgrade.

*Volume Down worked by default for some reason
*Volume Up I fixed by re-binding it with gnome-keybinding-properties
*Back/Stop/Play/Pause/Forward are correctly bound according to gnome-keybinding-properties, but they do nothing.

All of them worked perfectly in Hardy.

64-bit processor, Dell Studio 1535.

---

### Post by ferronica on 2008-11-06
i am too facing same problem using microsoft wireless laser keyboard 6000 v.2.0 worked on ubuntu 8.10 gnome 32bit, after fresh install ubuntu gnome 64bit multimedia not working please help :confused::confused::confused::confused:

---

### Post by scampiuk on 2008-11-08
Hi,

I can report the same problem.  Dell pre-installed Hardy worked fine with my wireless microsoft setup, however after upgrade no media keys work. 

Can't re-map the media keys, even after changing the set keyboard from a generic keyboard to a microsoft one.

Someone please, lets all get our Calculator buttons back! :)

Scampi -.

---

### Post by Izkata on 2008-11-08
I did a clean install of Hardy then upgraded it again and this problem was fixed.

However, I'm back to using Hardy again due to many, many other problems I was having - so I can't show you my settings...

---

### Post by ilovelinux33467 on 2008-11-14
I think that I'll file this as a bug. It is kind of annoying having to upgrade to get the multimedia keys to work

---

### Post by scampiuk on 2008-11-14
I think one of us should :)

I've been keeping my eye's out for a updated package for the last week and nothings hit the scene yet. 

Scampi -.

---

### Post by scorp123 on 2008-11-15
Same here:  Hewlett-Packard dv2108ea Laptop. The multimedia keys worked tip top in Gutsy, Feisty and Hardy. But not on Intrepid anymore ... :(

---

### Post by fogelfink on 2008-11-15
Same in my case, I did a clean install of 8.10.  I use a microsoft wireless multimedia keyboard 1.1.  This used to work fine in hardy when I chose it from the keyboard layout list in the preferences/keyboard.  When I choose the keyboard layout now, nothing seems to change and I can't acces my calculator keys. Does that mean I have to remap them?  And how would I do that, since the keyboard shortcuts that I can define and with which I was able to set the mutimedia keys of the keyboard, does not give me an option to define 1,2,3,etc.
Strange...

---

### Post by scampiuk on 2008-11-17
Hi again,

I've created / appended this to a bug on the bugtracker...

[https://bugs.launchpad.net/ubuntu/+source/xkeyboard-config/+bug/230354](https://bugs.launchpad.net/ubuntu/+source/xkeyboard-config/+bug/230354)

Thanks,

Scampi -.

---

### Post by Izkata on 2008-11-17
This is not related to the keyboard in that bugreport.

We are talking about the built-in keyboard for Dell Studios, in Intrepid Ibex (8.10)

---

### Post by scampiuk on 2008-11-18
Iztaka,

The first thread in this report says..

> Its a Microsoft Wireless Laser Keyboard v2.0

and the bug ticket says



> Upgraded to Hardy Heron 8.04 and now Microsoft Wireless Keyboard 6000 v2.0 does not work correctl

Scampi -.

---

### Post by scorp123 on 2008-11-18
This seems to affect a wide range of keyboards with multimedia buttons, not just Micrsoft or Dell keyboards. I for example have the same problem with the built-in multimedia keys on my HP Pavilion laptop. So I guess the fundamental problem here is somewhere somehow in the current kernel and the way it is now (pre-) configured by Canonical.

---

### Post by jorgitow on 2008-11-19
Yeah I'll just jump in here and concur with the MS Wireless Laser Keyboard 6000 v2.0 problem. I was surprised to find that my volume buttons didn't at least work like they did in Hardy. I've never been able to get all the buttons on the keyboard working in any distro, but usually had the volume and play/back/forward buttons functioning.

---

### Post by kpiascik on 2008-11-20
I have a wireless keyboard, mouse combo from Microsoft and am having the exact same issue.  I did a fresh install of Intrepid and the multimedia keys just don't work.

I tried changing the keyboard to layout, but it did nothing.  I was hoping that my first ever linux install would be a little more driver fiendly :(

---

### Post by ferronica on 2008-11-29
have you guys checked after installing ubuntu  2.6.27-9-generic  does it worked for anyone?

---

### Post by zigx on 2008-12-02
ferronica

still an issue for me on  2.6.27-9-generic #1 SMP

---

### Post by skyline_GT_R34 on 2008-12-03
Same annoying issue here, I have a Microsoft wireless laser desktop 6000 keyboard, I have upgraded hardy to intrepid, and now all the extra buttons which aren't included in the 105 standard layout don't even send event to X (I realized that with the xev command). 
So it should not be a "mapping" issue, it seems that the settings that worked great in Hardy (by itself, without any intervention! ) remained (for what I can see in the settings files and from the keyboard shortcuts).
I have also tried to set many different layouts (among which all the Microsoft's and the evdev as someone indicated...) without success.

I hope somebody succeeds in understanding at least a workaround for that...

---

### Post by whitethunder922 on 2008-12-04
I am running 8.10, kernel 2.6.27-9-generic #1. on an HP Pavilion dv9000 laptop. The multimedia keys work fine on the laptop itself, but the external keyboard's (Microsoft Wireless Comfort Keyboard 4000) multimedia keys don't work.

---

### Post by skyline_GT_R34 on 2008-12-05
I forgot to explain that I have an Acer Aspire 9513 notebook running kernel 2.6.27-9-generic #1 and also for me the *notebook* media keys are working, as the Fn's (brightness,...). Those of the *external* Microsoft Wireless Desktop 6000 keyboard don't.

---

### Post by crshman on 2008-12-06
I'm having the same issue, have we found a fix for it yet?

---

### Post by skyline_GT_R34 on 2008-12-07
The issue is even more strange, for if I use another 113-keys super-economic Labtec keyboard, all the 9 extra buttons work! :o 
The multimedia ones in a perfect manner, the other 2 aren't automatically right mapped but it is a very minor thing...:D
I hope my Microsoft keyboard also will work soon! in Hardy it was alright!

---

### Post by stylishpants on 2008-12-07
Keyboard handling has changed significantly in Ubuntu 8.10.  The X server is now supposed to automatically detect your keyboard and set it up.

Some people have had their issues fixed by the following procedure:
Select System->Preferences->Keyboard
Visit the Layouts tab.  Set the Vendor to "Generic", and the Model to "Evdev Managed Keyboard".


There are other threads with similar problems, spending some time hunting through the Ubuntu forums might yield something useful.

Good luck.

---

### Post by scorp123 on 2008-12-07
> **stylishpants said:**
>  Keyboard handling has changed significantly in Ubuntu 8.10.  Was it broken or something? Nope. So why in the world did they change that?? I sometimes really don't get it. "Don't fix it if it ain't broken" ... My laptop's keyboard and all its multimedia keys worked tip top under Ubuntu 8.04 ... Under 8.10: no joy.

I really wish they'd stop doing such things. If someting isn't broken: leave it alone ...

> **stylishpants said:**
>  Some people have had their issues fixed by the following procedure:
Select System->Preferences->Keyboard
Visit the Layouts tab.  Set the Vendor to "Generic", and the Model to "Evdev Managed Keyboard". Thanks for the suggestion but that didn't help me unfortunately. Maybe the others here have more luck with this?

---

### Post by crshman on 2008-12-07
> **scorp123 said:**
> 
 Thanks for the suggestion but that didn't help me unfortunately. Maybe the others here have more luck with this?

I tried that, it didn't work for me unfortunately =(

---

### Post by stylishpants on 2008-12-07
> **scorp123 said:**
> Was it broken or something? Nope. So why in the world did they change that?? I sometimes really don't get it. "Don't fix it if it ain't broken" ... My laptop's keyboard and all its multimedia keys worked tip top under Ubuntu 8.04 ... Under 8.10: no joy.

I really wish they'd stop doing such things. If someting isn't broken: leave it alone ...



It wasn't broken but it lacked important features.  Now instead of having a configuration file that specifies how your keyboard should work, and having to make sure that file is correct, X is supposed to autodetect your keyboard type and use whatever configuration is appropriate.

Progress marches on.  It's a bumpy road sometimes though.

---

### Post by ilovelinux33467 on 2008-12-07
Has anyone found a solution for this yet? Or is there some way to install 8.04 and still get the latest gnome and other packages just like 8.10?

---

### Post by skyline_GT_R34 on 2008-12-09
> There are other threads with similar problems, spending some time hunting through the Ubuntu forums might yield something usefulThanks, I've already spent some days of forum-surfing and tried the (few) 'procedures' that I've read around...That's why I posted in this thread.:-o
> Some people have had their issues fixed by the following procedure:
Select System->Preferences->Keyboard
Visit the Layouts tab. Set the Vendor to "Generic", and the Model to "Evdev Managed Keyboard".
Already tried...:sad:
> X is supposed to autodetect your keyboard type and use whatever configuration is appropriateThat makes me slightly laugh, if so many people are experiencing this issue, it means that X is BAD supposed to properly set keyboards! in the sense that many keyboard aren't "recognized" and then right configured.
So, why diffuse a thing not enough working? It would have been better not to change this keyboards settings issue, I agree with scorp123. :twisted: Or at least until it doesn't guarantee full functionalities...

---

### Post by scorp123 on 2008-12-10
> **skyline_GT_R34 said:**
>  It would have been better not to change this keyboards settings issue, I agree with scorp123. :twisted:  Welcome to the club. I tried some other stuff ... and nothing works.

According to various bug reports that I was able to find on lauchpad they indeed changed something in the kernel that handles USB HID devices ... which unfortunately includes most present-day multimedia keyboards. That explains why some special keys have stopped to work.

Oh well ... Let's hope there is a patch soon ... :(

---

### Post by ferronica on 2008-12-19
so no solution right now available :( i am missing so much my multimedia keys in ubuntu8.10 :(

---

### Post by nbayiha on 2008-12-20
If someone find a fix , please let us know. I have try almost everything and i think i will just wait till they release a fix .But if someone has a workaround ... :P

---

### Post by linfidel on 2008-12-23
It seems like some of you are having the same problem I had.  I did a full install to Intrepid, except for my home directory.  I found that my volumn buttons worked, but not mute.  However, after creating a new user, and logging into that account, they did work, so I assumed it was something in my home directory.

I finally got it fixed on my system:  I deleted this file:  ~/.gconf/desktop/gnome/peripherals/mouse/%gconf.xml, then restarted X using ctrl-alt-backspace.  I assume logging out or restarting would also work.  

I've since learned some new tricks for getting keys to work that don't even register in programs like xev, but I haven't learned enough to figure it out completely, but it's using things like /var/log/messages, dumpkeys, setkeycodes, etc.  I had some initial success, but there's some confusing interactions that I haven't sorted out yet.

Hope this helps some of you.

---

### Post by ferronica on 2009-01-08
ubuntu 8.04 much better then 8.10:(hope next release will support multimedia keys

---

### Post by lightxx on 2009-02-17
this bug is annoying to an extent which makes 8.10  + Rythmbox a no go for me.

i need to remote-control Rythmbox when i'm on my ergometer. with the multimedia keys gone and the global hotkeys not working (except for vol up/down) this is next to impossible :(

i've spent hours searching google, to no avail :(

thank god Amarok seems to use a different method to handle keyboard shortcuts

---

### Post by lightxx on 2009-02-17
this worked for me on the very first occasion i tried. on the next reboot it ceased working, re-deleting the file won't change a thing.

> **linfidel said:**
> 
I finally got it fixed on my system:  I deleted this file:  ~/.gconf/desktop/gnome/peripherals/mouse/%gconf.xml, then restarted X using ctrl-alt-backspace.  I assume logging out or restarting would also work. 

---

### Post by lightxx on 2009-02-19
some of dem über-nerds post a solution already!!!!:evil:

---

### Post by crshman on 2009-02-28
GREAT NEWS!

I just upgrade to the latest kernel 2.6.27-13

rnavarro@mcepc:~$ uname -a
Linux mcepc 2.6.27-13-generic #1 SMP Thu Feb 26 07:26:43 UTC 2009 i686 GNU/Linux

All my media keys work again! Damn uber nerds did it!

I'm using a Microsoft Wireless Comfort 4000

---

### Post by beercz on 2009-03-01
> **crshman said:**
> GREAT NEWS!

I just upgrade to the latest kernel 2.6.27-13

rnavarro@mcepc:~$ uname -a
Linux mcepc 2.6.27-13-generic #1 SMP Thu Feb 26 07:26:43 UTC 2009 i686 GNU/Linux

All my media keys work again! Damn uber nerds did it!

I'm using a Microsoft Wireless Comfort 4000
Didn't work for me :-(

Lenova 3000 N200 laptop.

If I boot and run from an Ubuntu 8.10 live CD the media keys work fine.

---

### Post by kpiascik on 2009-03-20
I'm in the same boat.  I'm using the Microsoft Wireless Comfort 4000 but I'm using 64bit ubuntu.  Does anyone know if there's an update for my kernel too?
2.6.27-11-generic #1 SMP Thu Jan 29 19:28:32 UTC 2009 x86_64 GNU/Linux

---

### Post by kpiascik on 2009-04-17
I have the Wireless Comfort Desktop 4000 (mouse and keyboard) and I can't get anything beyond the basics to work.  Play, Pause, Stop, Next, Prev, Favourites, etc... DO NOT WORK.  I'm running 8.10(Intrepid x64) and I can't seem to be able to find any solutions.

I even went into the terminal, some app to find the keycode number, I forget what app it was.  The only keys that register are the numbers 1-5 but all other keys don't even produce an output.

I did try and change the keyboard to microsoft in the preferences but nothing worked.

I have been trying to solve this for months....any help would be appreciated.

---

### Post by whitethunder922 on 2009-04-17
Kpiascik, I have the exact same keyboard but using 32 bit Ubuntu. You can try updating your kernel by doing this:

System > Administration > Software Sources
Updates Tab
Tick "Pre-released Updates"

It should then refresh once you close the window and you can see if a newer kernel is in the list of available updates. Updating to 2.6.27-14 fixed the problem for me.

---

### Post by xmacxmac on 2009-07-06
> **linfidel said:**
> It seems like some of you are having the same problem I had.  I did a full install to Intrepid, except for my home directory.  I found that my volumn buttons worked, but not mute.  However, after creating a new user, and logging into that account, they did work, so I assumed it was something in my home directory.

I finally got it fixed on my system:  I deleted this file:  ~/.gconf/desktop/gnome/peripherals/mouse/%gconf.xml, then restarted X using ctrl-alt-backspace.  I assume logging out or restarting would also work.  

I've since learned some new tricks for getting keys to work that don't even register in programs like xev, but I haven't learned enough to figure it out completely, but it's using things like /var/log/messages, dumpkeys, setkeycodes, etc.  I had some initial success, but there's some confusing interactions that I haven't sorted out yet.

Hope this helps some of you.

it worked for me, thanx pal. AT LAST!!!!!!!!!!!!!!!!!!!!!!!
I use 9.04 with microsoft multimedia keyboard 1.0A
for some reason the calculator key, the mute and the alt+ctrl+Delete were disabled.
Now they are back and working!

---

### Post by skyline_GT_R34 on 2009-07-23
Finally my Microsoft wireless laser desktop 6000 keyboard FULLY works after updating to Ubuntu 9.04!! without any intervention! \\:D/

Hope to you all, too. ;)

---

### Post by usererror on 2009-07-28
> **skyline_GT_R34 said:**
> Finally my Microsoft wireless laser desktop 6000 keyboard FULLY works after updating to Ubuntu 9.04!! without any intervention! \\:D/

Hope to you all, too. ;)

What!? that's not fair! :)

My FN and Multi Media keys work fine but my number pad with NUM LOCK turned ON does nothing!

If I run "xev" they do register...so is it just a Gnome problem for me?

---

### Post by whitethunder922 on 2009-07-28
> **usererror said:**
> What!? that's not fair! :)

My FN and Multi Media keys work fine but my number pad with NUM LOCK turned ON does nothing!

If I run "xev" they do register...so is it just a Gnome problem for me?

See: [http://ubuntuforums.org/showpost.php?p=4444700&postcount=5](http://ubuntuforums.org/showpost.php?p=4444700&postcount=5)

---

### Post by hyperAura on 2009-07-28
is every1 having problems only with the 64bit editions or 32bit as well?

---

### Post by whitethunder922 on 2009-07-28
> **hyperAura said:**
> is every1 having problems only with the 64bit editions or 32bit as well?

I had problems on 32 bit, but 9.04 fixed them all.

---

