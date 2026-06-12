---
title: "Dual screen / compiz problem"
date: 2008-09-20
forum: General Help
---

### Post by hofa on 2008-09-20
I tried to set up dual screens a few times but I always gave up rather fast. Last week I received the latest copy of LinuxMagazine (dutch) in wich was a tutorial for setting up dual screens, so I checked it out.

By using nvidia-settings, I now finally got what I wanted: Separate X Screens but I can move windows from the first to the second and backwards. Also when I maximize a window, it stays in one of the screens and doesn't take up my two screens (Like in TwinView)

Okay, so far so good.

My problem now is that compiz won't work anymore... Wobly windows, desktop cube, app switcher, scale etc. (but in ccsm there seems to be no problem at all)
I had a nice compiz setup going on and I would really like to keep it in dual screen.

Can anyone help me please?


ps: I have an nVidia geForce go 7900gtx in my laptop running 1920x1200 on my native 17" screen and 1280x1024 on my separate 17" screen
nvidia settings are separate X screens with Xinerama enabled

---

### Post by designsedge on 2008-09-20
Search these forums for compiz-icon.  Once it is installed, run it, right-click the icon and choose windows manager- compiz.  Worked well for me, if you still have trouble - post back.

(PS - Using Hardy Heron with GeForce 8500 - Compiz - 2GB RAM)

---

### Post by hofa on 2008-09-21
compiz-icon = fusion-icon? I suppose it is =)

It didn't do anything for me. Don't get me wrong, everything worked and still works perfectly in SINGLE screen mode. But when I use 2 screens, there's no more eyecandy... When I move windows, I get a wireframe for instance =/

Also non-eye-candy plugins (like maximumize) stop working, so I can conclude it's compiz that just can't handle the setup. I really hope there's a solution for this

---

### Post by SirGraniteHead on 2008-09-21
I've had a similar issue, and from what I understand, the problem lies with Xinerama (the option that gives you seperate xscreens but you can move apps between them). Apparently Xinerama and Compiz are incompatible, as Xinerama disables something that Compiz needs (don't recall exactly what).

From what I know, these are your options:

Disable Xinerama, keep two xScreens: This option is annoying, since you cannot move apps and windows between screens, and if you have something like firefox open one one screen, you can't have it open on the other. Also, I had issues with some of the fancy stuff like fire draw and raindrop, but everything else compiz seemed to work.

Use Twinview: I don't use this, since my two monitors are different sizes (I'm on a laptop with an external) so the panels get lost, and if you maximize it will spread across both screens.

Or get by without compiz. This is what I do. If there is someway to magically modify twinview to handle different resolution/size monitors, and not maximize across them both, this would be ideal. Unfortunately, I have no idea if this can be done, nevermind how. 

last time I tried, I pushed the wrong button and ended up with the lowest resolution possible and no easy way to fix it. I don't know enough to not use trial and error, and linux lets your errors get pretty big.

---

### Post by hofa on 2008-09-22
Thanks for your input.

I'll guess I'm gonna keep my single screen setup after all.

No way I'm disabling Xinerama 'cause I just can't work like that
No way I'm using twinview because of the reasons you said
No way I'm disabling compiz because I got used to it and I hate working without it

So I guess I have a nice 17" screen I can put in the closet until there's a solution to my problem =(

---

### Post by thefluxster on 2009-05-28
Can anyone confirm if this is still a problem on Jaunty?  I've always thought there was just something wrong with how I installed or something I upgraded/added...  None of the cool compiz functions work for me (maximumize chief among them).  I always use dual screens, sometimes of different size (Dell D430 laptop install).

---

### Post by sirlancelot on 2009-06-11
This is still a problem. One in which I'm still searching for a solution :-/

---

### Post by MeduZa on 2009-06-21
same problem here, compiz on JJ have this problem :(

---

### Post by ryanhaigh on 2009-07-22
Just stumbled onto this thread while trying to sort out something related (unable to get maximumize working on dual/singgle under Debian lenny if anyone wants to be helpful).

I have seen a few posts in the past about people wanting to configure their dual screen nvidia system and having problems with twinview treating the setup as one huge display. This is one such thread: [http://ubuntuforums.org/archive/index.php/t-771501.html](http://ubuntuforums.org/archive/index.php/t-771501.html)

Hope this helps. At some point I will see if I can add it to the wiki [https://help.ubuntu.com/community/NvidiaMultiMonitors](https://help.ubuntu.com/community/NvidiaMultiMonitors) unless someone else does it first.

---

