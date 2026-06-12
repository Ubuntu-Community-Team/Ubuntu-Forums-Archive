---
title: "Annoying gnome mouse pointer in fullscreen games"
date: 2008-09-20
forum: General Help
---

### Post by Vagueism on 2008-09-20
Hello

When I play certain games in fullscreen the Gnome mouse pointer doesn't hide but instead sits stuck in the middle of the screen. I can get rid of it only by toggling fullscreen mode on and off while trying to drag the pointer to the side, it usually takes a few tries. While it's no showstopper it's definately an annoyance.

Not all games are affected, but Scummvm is and Secret Maryo Chronicles, Frozen Bubble, Urquan Masters. Wine applications are not affected.

I use Ubuntu 8.04 on an Eee PC 701 without desktop effects. I don't have this problem when I log in from GDM to a failsafe terminal and launch the game from there (instead of from a Gnome session). 

Any ideas?

---

### Post by skroops on 2008-09-21
I have this problem too on a dell mini 9.  It happens with scummvm and dosbox.

edit: after playing around with the dosbox options, it appears that the problem is specific to opengl.

Any way to get a newer version?

---

### Post by skroops on 2008-09-21
bump

---

### Post by poldie on 2008-10-01
> **skroops said:**
> bump

Yeah, I get this too. Ubuntu 8.4.1 on Aspire One netbook, on OpenArena and Liquid Wars. It's not `the` mouse icon as that one moves around as normal. It's an extra icon.

---

### Post by platykurtic on 2008-10-18
Also happens on my eee1000. But thanks for the failsafe terminal thing, that works fine. Now back to playing roms

---

### Post by Kethinov on 2008-11-16
I'm also experiencing this both with Mupen64 and Frozen Bubble. When I make the game full screen, the mouse cursor remains in the center of the screen, will not disappear, and cannot be moved.

My hardware: a Dell Latitude D620

Note: this appears to be a regression. This bug did NOT occur on my laptop in Hardy Heron.

---

### Post by quanumphaze on 2008-11-23
This bug is very annoying, let's try to get to the bottom of this so a detailed bug report can be filed.
[LIST]
[*]I'm using an Intel 945GM graphics chipset, everyone else seems to be using an Intel too
[*]Occurs in fullscreen games
[*]games use OpenGL/SDL, unsure which specifically
[*]If the cursor isn't visible, changing to windowed then fullscreen will usually make it show
[*]Everyone seems to be using Gnome
[*]Members ([from this thread]("http://ubuntuforums.org/showthread.php?t=988573")) have reported this occurring in Wine games too (Starcraft and Fallout primarily use DirectDraw)
[/LIST]
If anyone can try this in KDE (Kubuntu) or another distro on the same hardware and it works, we and dismiss a driver/X problem.

---

### Post by jeSah8ci on 2008-11-24
I have a hp dv4170us with an Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller, using GNOME on Ubuntu 8.10.

I'm playing The Dig on ScummVM and managed to find a workaround for this bug. You just have to toggle aspect correction (ctrl + alt + a) and the mouse pointer isn't shown anymore on fullscreen.

I don't know if this 'fix' will work on other games.

I installed Obsidian with Wine (also the included version of Quicktime, which was 2.x something) and the game worked fine (it did require for me to switch to 16 bit color depth). The pointer bug didn't show up, but the game's pointer did have an ugly shadow effect that I don't remember seeing previously.

---

### Post by quanumphaze on 2008-11-25
Thanks for that rolandog

Do other games do the same? Namely Frozen Bubble and Starfighter always did this when you toggle fullscreen back and forth.

Unfortunately many games don't alt+return or alt+tab (why doesn't X handle this?) so it can be annoying trying to move quickly into the lower right corner when you have to close and start the whole game.

I'll try some games in the recovery Xterm session to see if it's a WM problem, this happens with both Compiz and Metacity on Gnome.

Edit: After running Frozen Bubble in the failsafe terminal (after running 'metacity &') the mouse cursor is nowhere to be seen. Interesting.
Feel free to start randomly (and safely) killing Gnome processes to see if it helps.

---

### Post by AmyRose on 2008-12-18
Has there been any news on this bug? I just got a new Dell Inspiron 1525 with Ubuntu preinstalled (Intel Mobile GM965/GL960 graphics) and have this same problem on Intrepid.

This problem does NOT occur when I run the game under Fluxbox. It only happens in GNOME.

---

### Post by AmyRose on 2008-12-19
Sorry to post again, but I figured out where the problem lies. Disabling or killing the GNOME power manager daemon fixes the SDL problem.

Will report this bug on LP.

Edit: Never mind... it only fixes some games. ](*,)

---

### Post by jspenguin on 2009-04-23
I found a temporary solution:

Add 'Option "SWCursor" "True"' to the device section of xorg.conf:

```

Section "Device"
        Identifier      "Configured Video Device"
        Driver "intel"
        Option          "SWCursor" "True"
EndSection

```

This may cause the cursor to flicker over windowed OpenGL apps that don't hide the cursor, but it works great for fullscreen.

Hope that helps.

Edit: Nevermind, this disables OpenGL acceleration...

I'm using Xfce, if that makes a difference.


Edit 2: Another workaround, if you can recompile the game:

Add a delay between calling SDL_SetVideoMode and SDL_ShowCursor:

```

.
.
.
screen = SDL_SetVideoMode(1024, 768, ...)
SDL_Delay(300);
SDL_ShowCursor(SDL_ENABLE);
SDL_ShowCursor(SDL_DISABLE);
.
.
.

```

Alternatively, you could set a timer, or have a hotkey that calls SDL_ShowCursor. You have to call it with SDL_ENABLE first, or it won't do anything.

---

### Post by lariosa42 on 2009-04-25
It happens to me too.  Specs:

VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)

OS: Ubuntu 8.04, 8.10, 9.04 (It has happened on all of them so far).



One workaround I've found, at least on openarena, it to move the cursor to one side really fast when the game opens.  Then it gets "stuck off screen."  If you're timing is off, it will get stuck on an even worse part of the screen.

---

### Post by Vagueism on 2009-04-26
I've a semi-workaround too, related to moving the cursor to one side really fast. I launch games like this, it works in many cases:

**xwit -warp 800 480 && scummvm -f sword 1**

The "xwit -warp" moves the cursor to the specified location. My screen is only 800x480 so you'll probably want to change that. Don't touch the mouse until the game has launched.

---

### Post by lariosa42 on 2009-04-26
Thanks Vagueism!  

(BTW, your post is very non-vague, especially when compared to my earlier post.)

---

### Post by Devi 710 on 2009-06-02
Thanks for the help guys! I am having the same problem on my Eee Pc 701 4G Surf running Easy Peasy v1.1 and SCUMMVM.

The xwit -warp didn't work for me, but moving the mouse off screen during the switch to full screen does. Also logging into a terminal session, but it was scary getting back to a gnome session.

devi

---

