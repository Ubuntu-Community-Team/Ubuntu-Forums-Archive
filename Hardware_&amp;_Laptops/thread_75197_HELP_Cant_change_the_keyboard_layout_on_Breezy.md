---
title: "HELP: Cant change the keyboard layout on Breezy"
date: 2005-10-13
forum: Hardware &amp; Laptops
---

### Post by The_Saint on 2005-10-13
Dear people,

I have a really big problem. I just installed Breezy final and like with the RC, I still cannot change the keyboard layout.

I did a clean install, didnt upgrade or anything, pure clean install.

And now, I cant chnage the keyboard layout to Estonian. From System->Preferences->Keyboard I change it into Estonian layout, it understands me, it even shows me the real and right Estonian layout, and nothing. Doesnt help if I delete U.S. from there or not, nothing happens - it says Estonian, but keyboard in fact is U.S.

The machine I use is based on Compal CL56, but that doesnt necessarily have anything to do with it. Hoary worked just fine and well.

I would really appreciate some suggestions...

Thanks.

---

### Post by bored2k on 2005-10-13
You could forcibly change it with 
```
sudo dpkg-reconfigure xserver-xorg
``` and manually type your keyboard layout when asked to (in my case, i chose ES for spanish layout).

---

### Post by The_Saint on 2005-10-13
Well, I think I did it, but do I now neet to reboot or something or not...

---

### Post by The_Saint on 2005-10-13
Damn.. now that i did it, i get this: Error activating XKB configuration.
It can happen under various circumstances:
- a bug in libxklavier library
- a bug in X server (xkbcomp, xmodmap utilities)
- X server with incompatible libxkbfile implementation

X server version data:
The X.Org Foundation
60802000

If you report this situation as a bug, please include:
- The result of xprop -root | grep XKB
- The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd

And I don't still have all the keys of the keyboard :(

---

### Post by LCID Fire on 2005-10-13
Me and a thousand other people, too
I wonder why this bug was not release stopping because it is a REAL big problem on non us machines.:confused:

---

### Post by daniels on 2005-10-13
if you're using multiple layouts: [http://bugzilla.ubuntu.com/show_bug.cgi?id=15372](http://bugzilla.ubuntu.com/show_bug.cgi?id=15372)

---

### Post by takuzinis on 2005-10-16
I had the same problem. Since I installed my 5.04 very recently and for the test purposes I was ready to make clean install of 5.10 to look for the eventual solution. I propose the following:

Choose U.S. English keyboard layout as default and delete any other from the list (System – Preferences – Keyboard)

Take a look at 2 folders:

/usr/X11R6/lib/X11/xkb/symbols/

and 

/etc/X11/xkb/symbols/

Delete folder “pc” from both

Reboot and try to add your specific keyboard layout.

How it looks now?

---

### Post by LCID Fire on 2005-10-16
I don't even have the folders.

xprop -root | grep XKB gives
_XKB_RULES_NAMES_BACKUP(STRING) = "base", "pc101", "us", "", ""

---

### Post by alesko on 2005-10-26
HEY! I got the same problem. Couldn't change keyboard layout from US to SI (Slovenian).
Just go to command prompt and type :
$ setxkbmap -layout 'si,us' -model pc105
that's it!
If you want to run that everytime you boot, go to 
system -> preferences -> sessions  ->  
/startup commands/  ,  /add/  and write the same line to /command/

works fine fo me

---

### Post by xinelo on 2005-11-18
xinelo@micho:~$ sudo setxkbmap -layout 'es,us' -model pc105
Password:
Error loading new keyboard description

---

### Post by Peter77 on 2005-12-11
[QUOTE=alesko]HEY! I got the same problem. Couldn't change keyboard layout from US to SI (Slovenian).
Just go to command prompt and type :
$ setxkbmap -layout 'si,us' -model pc105
that's it!
If you want to run that everytime you boot, go to 
system -> preferences -> sessions  ->  
/startup commands/  ,  /add/  and write the same line to /command/

works fine fo me[/QUOTE]

Thanks, finally a solution!!
I had major problems with alt gr key but now it works, you really made my day, mate :)

look, now i can make @@@@@ and €€€€ and |||| :D

/P

---

### Post by Commuto on 2006-03-07
[QUOTE=daniels]if you're using multiple layouts: [http://bugzilla.ubuntu.com/show_bug.cgi?id=15372](http://bugzilla.ubuntu.com/show_bug.cgi?id=15372)[/QUOTE]Thanks indeed for this link. That did the trick for me!:-D

---

### Post by xinelo on 2006-03-08
xinelo@micho:~$ setxkbmap -layout 'es,us' -model pc105
Error loading new keyboard description

---

### Post by Nikiforos on 2006-03-15
sudo mv /etc/X11/xkb/symbols/pc /etc/X11/xkb/symbols/pc_old
sudo cp /etc/X11/xkb/symbols/pc.dpkg-new /etc/X11/xkb/symbols/pc
These works for me!!! finally!!!!:p :p \\:D/ \\:D/ \\:D/ \\:D/ I have dapper drake flight 5 btw.

---

### Post by Corvair on 2006-04-16
Hi,
I am new on Ubuntu Linux  ](*,)  and I am trying to change my keyboard display to Canadian display. I go to System, preferences and keyboard and I get the right display on the screen but the us keyboard stays on. I have found information on this forum on how to do it....but I dont know where to go to type in the information.

Does anyone have the patience to show me how to proceed?

Claude

---

### Post by ftmichael on 2006-05-26
michael@jeezychreezy:~$ setxkbmap -layout 'uk,us' -model pc105
Error loading new keyboard description
michael@jeezychreezy:~$ setxkbmap -layout 'uk,us' -model pc104
Error loading new keyboard description

I want the UK English layout; should I be putting something other than uk?

Michael

---

### Post by towsonu2003 on 2006-06-08
damn stupid thing... fresh up-to-date breezy and this is what I get w. TR keyboard... fxes packages in bg report + moving pc didn't work

grrr

---

### Post by ftmichael on 2006-06-08
Fixed with [http://ubuntuforums.org/showpost.php?p=465307&postcount=13](http://ubuntuforums.org/showpost.php?p=465307&postcount=13) !

Note also that upgrading to Dapper may fix it automatically; I got it to work before upgrading though.

Michael

---

### Post by towsonu2003 on 2006-06-08
[QUOTE=ftmichael]Fixed with [https://wiki.ubuntu.com/Spca5xx](https://wiki.ubuntu.com/Spca5xx) !

Michael[/QUOTE]
u fixed the keyboard layout problem with a webcam driver? :confused:

---

### Post by ice60 on 2006-08-27
> **ftmichael said:**
> michael@jeezychreezy:~$ setxkbmap -layout 'uk,us' -model pc105
Error loading new keyboard description
michael@jeezychreezy:~$ setxkbmap -layout 'uk,us' -model pc104
Error loading new keyboard description

I want the UK English layout; should I be putting something other than uk?

Michael

hi, i'm just setting up arch and was trying to remember the above command. this is what it should be for the UK
```
sudo setxkbmap -layout 'gb,us' -model pc105

```i suppose the 105 bit is about how many keys you have :)

---

