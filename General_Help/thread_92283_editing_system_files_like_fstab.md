---
title: "editing system files like fstab"
date: 2005-11-19
forum: General Help
---

### Post by Optiker on 2005-11-19
I've been having problems editing files like fstab. I understand that I have to edit as sudo, but have tried in a console, sudo kate /etc/fstab but get the error message...

------------------
Error: "/var/tmp/kdecache-chuck" is owned by uid 1000 instead of uid 0.
Link points to "/var/tmp/kdecache-root"
kate: ERROR: Communication problem with kate, it probably crashed.
------------------

I thought I read once that I can edit as sudo by right-clicking the file icon and selecting something like "edit as sudo" but I don't see any such option in the dropdown menu.

Since I have had to manually edit fstab to get access to my Windows drives and automount them on boot, and have had to edit the boot list to default boot Windows (sorry...still primarily using Windows until I get all of these issues resolved), I've had to boot Windows, then using the Ext2 utility, edit the files in Windows. That works, but it cumbersome to have to exit Kubuntu, open Windows, edit, exit Windows, and reboot Kubuntu.

Can anybody help?

Thanks!
Optiker

---

### Post by manicka on 2005-11-19
try kwrite instead of kate

sudo kwrite /etc/fstab

I think the right click options you have read about are nautilus scripts for gnome/nautilus

---

### Post by Optiker on 2005-11-19
OK - kwrite works, but when I run it from the konsole, I get the following errors...

-------------------
Error: "/var/tmp/kdecache-chuck" is owned by uid 1000 instead of uid 0.
Link points to "/var/tmp/kdecache-root"
Error: "/tmp/kde-chuck" is owned by uid 1000 instead of uid 0.
Link points to "/tmp/kde-root"
-------------------

Although it did save, with the following error....
-------------------
Error: "/tmp/ksocket-chuck" is owned by uid 1000 instead of uid 0.
Link points to "/tmp/ksocket-root"
-------------------

Saving again saved wit no errors.

I can live with all of that, but what's causing the errors and how do I fix it?

Why doesn't Kate work?

Thanks!
Optiker

---

### Post by manicka on 2005-11-19
[QUOTE=Optiker]
Why doesn't Kate work?
[/QUOTE]

I'm not sure, it's been ages since I've used kde on a regular basis. I have a vague recollection that others have had similar problems with kate

---

### Post by noigeaR on 2005-11-21
you can use kdesu instead of sudo to start kde programs as root. it somehow doesn't work without errors for kate though. if you don't need to run kate from a console you can use konqueror. if you use **konqueror** you can easily edit files in root mode with kate by right clicking on the file, then choosing **actions** and then **edit as root**.

---

### Post by samx on 2005-11-21
You can't easily start a KDE application with root privileges. This is the default setting for the X server I think. You surely can change this somehow, but it's a good idea to keep this as it is - it's not the best idea to start KDE (or gtk or whatever graphical) applications with root privileges normally.
You have two possibilities:
There is a kde application which takes care for the problems with the X server:
```
kdesu kate /etc/fstab
```
Or you use just a simple editor without graphical userface:
```
sudo pico /etc/fstab
```

---

### Post by dubz on 2005-11-21
your best option is probably to use a program called vi.. sudo vi /etc/fstab

here are the commands needed
i --- insert
esc -- exits editing mode(insert,etc)

to save :w
save and exit :wq

make sure your in insert mode to type things in :)

hopes this helps

thanks.

---

### Post by samx on 2005-11-21
[QUOTE=dubz]your best option is probably to use a program called vi.. sudo vi /etc/fstab[/QUOTE]
If you wanna get Unix leet freak this is right. If you wanna be an advanced and reasonable linux user, use at least vim (=vi improved), there is no reason to use vi if you have vim. (But one can be an advanced linux user without knowing vi(m) ;) )
But if you just want to edit a simple file, use pico or something like that, because vi(m) is kinda... "unintuitive" if you have never used it.

---

### Post by dubz on 2005-11-21
try vi is tough. type vimtutor at prompt for a tutorial.

p.s - vi is normally linked to vim :)

thanks.

---

### Post by Optiker on 2005-11-21
Thanks all...now I'm thoroughly confused!  :)

It's beginning to sound easier to exit Linux, run WinXP, use Ext2 to edit any of those kinds of files in XP, exit WinXP and reboot into Linux! That doesn't make sense, does it...but it's less confusing than the the replies to a novice like me.

I have a feeling that I'll try kdesu first, then Konqueror, though I thought I tried that once and couldn't find that method, and somebody said it was in Gnome, not KDE.

Thanks for replies...will give it a try tonight.

Optiker

---

### Post by noigeaR on 2005-11-22
the method i've described for konqueror works fine on a standard kubuntu install. just *right click the file* you want to edit, select *actions* and then select *edit as root*. this has nothing to do with gnome. it's a kde/konqueror feature.

---

### Post by dubz on 2005-11-22
Do anything except for rebooting to doze.
That will mean you have lost.
Don't giveup...dammit.
*tell my mother that i love her...gasp*

---

### Post by Optiker on 2005-11-22
noigeaR...OK - did the Konqueror/Actions/Edit as root approach and that works fine, and is easy enough...if I can remember where it is!   :)  That was the problem previously when I heard that...couldn't remember how to get to it.

dubz...at the risk of extending this thread as a Linux vs Windows war, it's not about winning or losing. It's about usability. I've now installed or participated in installing one or another Linux distribution (Mandrake, Kubuntu, Red Hat and Libranet come to mind) approximately 10 times on at least five different computers, "used" several different releases of Knoppix, al in my desire to migrate to Linux. I have installed Windows (95, 98, 2000, XP) at least that many times on at least that many computers. Only once did a Linux installation result in a clean installation where _almost_ everything worked - only thing that didn't was  one or more printers. Only trhat once did the sound work "out of the box". Any one of the ones where the sound didn't work  took at least as much time, and effort and frustration as any three WIndows installations. Some never did work and I gave up. That's why I'm still using Windows. Incidentally, the lone exception where most everything worked was Mandrake 10.1. Even that followed a failed installation of MDK 10.0 by "the experts" in my local Linux users' group.

I'm not a champion of Windows or Linux. I want an OS that works for my needs. I like Linux very much, would prefer to use it, and have tried repeatedly to go there, but everytime exceeded my tolerance for tweak this and that to get basic, everyday functions (printing, graphics, sound) to work. I'm neither a computer dummy nor expert. But, I've been using PCs since 640 KB of RAM was an option and took a third-party board to accommodate - in fact, since 8" (or whatever they were) floppies, and mainframes before that.

It doesn't matter y'all Linux advocates see it as clean and simple because for the general public, until it can install and work for at least the basic operations (printing, sound, graphics, access to digital cameras and scanners) out of the box, as reliably as Windows, it won't become the desktop of choice for the general public. That's disappointing to me because I really do like it, and I really have tried to migrate, but it's just too cumbersome.

Sorry for the long rant. Replies optionsl, flames not appreciated.  :)

Otherwise, this thread can be considered closed since my original questions has been resolved.

Thanks!
Optiker

---

### Post by dubz on 2005-11-27
ahhhh, much like you i have installed various flavours of linux for 6 years now.(thats a lot of boxen).I must say that each and every time ,from redhat 6.2, sound worked flawlesly straight out of the box.....this is not an insult, you just must have been working with dodgy hardware!

Cant be much dodgier than a 486 with 32MB of RAM using a soundblaster 16.
I hope your next install is much more successful.

---

### Post by Topsiho on 2005-11-28
I tried some of the options mentioned in the earlier posts and will recapitulate the results here for clarity: I entered in a console (text screen)

sudo kate /etc/fstab
This one starts up kate which then crashes, so this does not work

sudo kwrite /etc/fstab
This one starts up kwrite OK, with some errors in the console.
Changing the file and then saving it works OK however and that is what you need
Of course one should enter one's user password if asked.

sudo vim /etc/fstab
This one works correctly, is my favourite way, but as someone stated in an earlier post: vim is not the most user friendly editor. One must get used to it and learn some of it's idiosyncrasies to use it with confidence

So I suggest you use kwrite and ignore the errors in the console :)

Pity though that kate crahes used in this way as it's super..... though it's a developers paradise.

Hope the confusion has subsided now :p 

Topsiho

---

### Post by bin on 2005-11-28
There is of course a much less painful way.

Install mc - midnight commander

Open a konsole
sudo mc
blah

navigate to the file
F3 to read or 
F4 to edit
edit
F2 to save

It's a terrific file manager, allows you to check out .debs for file locations, is great for creating and editing symlinks, makes a mean ftp client - oh and it makes the tea as well:) 

in light

bin

---

### Post by guice on 2005-11-28
> sudo vim /etc/fstab
This one works correctly, is my favourite way, but as someone stated in an earlier post: vim is not the most user friendly editor. One must get used to it and learn some of it's idiosyncrasies to use it with confidence
My prefered way
(Although I just use 'vi' for personal compatability with Solaris systems that don't have have 'vim' installed)

And yes, it's not the most friendliest, but I do highly suggest you learn it's abilities. Once you do, you'll never look at a text editor the same. Pickup O'Reilly's VI desktop reference.

---

### Post by Brando569 on 2005-11-29
it took me awhile to figure out how to use vi and vim, i always felt "trapped" in it :lol: ive had those errors too with kate idk what causes them though, whenever it does that i just used kwrite or kedit instead. kedit it a simple text editor that launches really fast. this should work for you: click the K -> click Run -> type kdesu kate /etc/fstab and type in your password, if that doesnt work replace kate with kwrite

---

### Post by Optiker on 2005-11-29
Thank you all for your replies. I only wish that the replies to my "no sound" post were as successful!

I've found the suggestion to, in Konqueror, right-click --> actions --> edit as root to be the simplest and adequate for my needs. That opens the file in KWrite, and that works fine. I acknowledge that some of the other suggestions might be technically much better, especially for developers, but for my needs, and much preferring a GUI to command line, Konqueror to KWrite works!

Thanks again for your help. This thread is closed for my purposes.
Optiker

---

