---
title: "Wide display on sony tr2 not working with xubuntu"
date: 2007-02-14
forum: Hardware &amp; Laptops
---

### Post by tyusoff on 2007-02-14
Hi guys,

I had just installed Xubuntu 6.10 on my sony pcg-tr2 laptop. All other stuff have been detected and installed with out any problem (except sound which i dont really need), but I have problem with display which only capable of 1024x768 resolution. Previous to Xubuntu, I had used Mandriva 2006 and to solve the display problem, I used 1280patch. Now the problem is, this is not working anymore, with 1280patch I got the screen to be right-justified and leaving a huge blank screen on my right. Then I tried another patch, 1280patch-845g-855gm-865g.c but nothing really happened. Then I tried 915resolution, also with no success. I will include the xorg.conf. I hope somebody could point out my mistake and help me to gain back my wide-screen .... :( 

ps- full xorg.conf files is attached

> Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       31.5-90
        VertRefresh     59.0-75.0
        Modeline        "1280x768" 80.14 1280 1344 1480 1680    768     769     772     795
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation 82852/855GM Integrated Graphics Device"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1280x768" "1024x768" "800x600"
        EndSubSection
EndSection


---

### Post by tyusoff on 2007-02-15
Manage to solve it. Found a japanese blog describing it, and the solution is really simple.

install 915resolution

edit /etc/default/915resolution

add 

MODE=5c
XRESO=1280
YRESO=768

then restart ... 

WIDE SCREEN AGAIN ....:biggrin:

---

### Post by schruthensis on 2007-02-22
Uggg...     I have been trying to get this working for weeks now.. 

I have a Sony Vaio PCG-TR3AP with the Intel 855GM graphics card 

I have installed Ubuntu (Debian) 6.10 Edgy Eft (testing) and have gotten all sorts of things working (sound card, DVD player, flash)

....but the full screen isn't being utilized.     I have tried just about every forum posting and How to guide i could find but still no dice.   

basically, I can't even seem to get 915resolution (v 0.5.2-4) to run at all...    I mean it runs but doesn't appear to be doing anything.  I have set the defaults in /etc/defaults/915resolution  as 

$ sudo 915resolution 5c 1280 768
$ sudo 915resolution 7c 1280 768
$ sudo 915resolution 7e 1280 768
$ sudo 915resolution -l
----------------
Mode 5c : 1280x768, 32 bits/pixel
Mode 7c : 1280x768, 8 bits/pixel
Mode 7d : 1280x768, 16 bits/pixel
Mode 7e : 1280x768, 32 bits/pixel
----------------
none of which appear to do anything even though it tells me it 
"Patch mode 7e to resolution 1280x768 complete"

i log out and log back in and nothing changes..  restarting doesn't do anything either

I can't find any useful messages in any of the logs  ( /var/logs/messages or /var/log/Xorg.0.log )

My /etc/X11/xorg.conf  settings don't seem to be affecting anything either... its as if X doesn't even read these settings...   
(I am currently using tyusoff 's X11 settings posted above)

....and the System->Preferences->Screen Resolution  settings don't seem to be affected by either X11 or 915resolution..

Any ideas?

---

### Post by schruthensis on 2007-02-22
WOW!  it finally works!    

the problem (for me)  was to use the proper BIT depth (I think)

$ sudo pico /etc/default/915resolution

MODE=5c
XRESO=1280
YRESO=768
BIT=24

and then to make sure it ran at startup

$ sudo /etc/init.d/915resolution start

then, FINALLY, the setting for 1280 by 768 showed up in my 
System->Preferences->Screen Resolution  menu!

yay!

---

### Post by spiroxlii on 2007-02-23
schruthensis, how did you get sound working on your TR?  I have a TR2A, and I still have no sound.

---

### Post by lexod on 2007-05-18
I'm having trouble saving the file after editing it.  I am a complete newbie and would appreciate it if you could give a little more detail in the process of editing the xorg.conf file.  Thanks! :)

---

### Post by jesuisn00b on 2007-06-02
I have no idea what any of the above is about and I have also installed Ubuntu on a TR2 to try out. No sound like the above posts, volume control buttons don't work, brightness wont adjust and I have the same widescreen problems. I have updated my system and google brought up 915resolution but I have not the faintest idea what I'm doing. 

I'm half an hour into using Ubuntu, my first foray into Linux. 

Would appreciate some help.

---

### Post by decktard on 2007-07-06
Has anyone gotten this laptop to run with the correct resolution after hibernation?

The above got me working in 1280x768... thanks for the help.

---

### Post by decktard on 2007-07-12
> **decktard said:**
> Has anyone gotten this laptop to run with the correct resolution after hibernation?

The above got me working in 1280x768... thanks for the help.

Scratch that request.  I was formerly running kubuntu and I got the 915resolution tarball and ran a make install from there.  This is where I had my problems resuming from hibernation.

I have since installed ubuntu (I haven't used gnome in years and figured I'd give it another shot) and ran apt-get install 915resolution.

I then edited my rc.local to include the line "915resolution 1280 768 24" I also edited the \etc\default\915resolution to reflect the settings.  Everything seems to be working fine including resume from hibernation.

I'm still not 100% sure if kubuntu will work properly but at least my gnome experience will be pleasant.

---

