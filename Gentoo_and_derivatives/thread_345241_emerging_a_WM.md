---
title: "emerging a WM"
date: 2007-01-24
forum: Gentoo and derivatives
---

### Post by MoxJet on 2007-01-24
Hello, I'm trying out gentoo, and I managed to pull off an installation yesterday (hooray!)

Now, what WM would you recommend?

How long time would it take to emerge gnome, kde or fluxbox respectively? I'm on a 1,7ghz intel. What could be clever to emerge before a window manager?

Thanks in advance,
Dan

---

### Post by runningwithscissors on 2007-01-24
> **MoxJet said:**
> Hello, I'm trying out gentoo, and I managed to pull off an installation yesterday (hooray!)

Now, what WM would you recommend?

How long time would it take to emerge gnome, kde or fluxbox respectively? I'm on a 1,7ghz intel. What could be clever to emerge before a window manager?

Thanks in advance,
Dan
While you can emerge either KDE or GNOME (both will take an entire night at least, with the X Server). If you have the same toolchain built on a faster machine, you can easily use portage with distcc to compile the packages on the faster machine.

Xfce is a good choice for a 1.7Ghz machine.

---

### Post by mips on 2007-01-24
> **MoxJet said:**
> Hello, I'm trying out gentoo, and I managed to pull off an installation yesterday (hooray!)

Now, what WM would you recommend?

How long time would it take to emerge gnome, kde or fluxbox respectively? I'm on a 1,7ghz intel. What could be clever to emerge before a window manager?

Thanks in advance,
Dan

Fluxbox should be very fast to compile. It's what I would emerge first. Can always others later.

---

### Post by fuscia on 2007-01-24
openbox. very fast.

---

### Post by zaratustra on 2007-01-24
you should make a choice... Use KDE instead of Gnome, beacese new Qt is fast and optimized. Linus himself also says that KDE is better. If you want a something between complete DE and total minimalism, use XFCE or even Enlightenment DR17 if you want your box to be more eye-candy. Remember that DR stands for Development Release, so don't expect everything to work flawlessly. My choice is XFCE. And if you are total minimalism phreak, use {Open|Flux|Black}Box. I would recommend OpenBox because of better configurability.

All in all, do not use something what is fastest to compile, but something you would like to use for a longer time. Don't waste time trying different stuff. You can do that with other non-sourced-based distro or LiveCds. Don't consider that as me disliking Gentoo. I run Gentoo and only Gentoo:)... Ok, ok, a have windows on dual boot:D

My personal choice is XFCE. I compiled KDE 3.5 and I must say that it is good and fast but I removed it because of personal religious reasons. :) Phuckin K is iritating me:)
I run gentoo 2.6.18 @ 1.5 GHz Celeron M. Thinkpad Z60m with integrated Intel graphics

---

### Post by mysticrider92 on 2007-01-25
Fluxbox and its related versions usually compile very quickly (most likely less than an hour, plus some X configuration), so if you want to get it up and running, that is a good choice. Gnome will take longer, but I prefer it in the long run. KDE will take what seems like forever, but is fun to use later. Also, be sure to run 'emerge --sync' and 'emerge portage' if you havn't already, otherwise it will try to install packages that don't exist or are outdated.

There are some very useful guides on the [Gentoo documentation]("http://www.gentoo.org/doc/en/index.xml?catid=desktop") on getting everything set up, so you will probably want to check those out too.

---

### Post by mips on 2007-01-25
> **zaratustra said:**
> 
All in all, do not use something what is fastest to compile, but something you would like to use for a longer time. Don't waste time trying different stuff. 

I always do a fluxbox install first, this gives me a gui where I can work from and launch stuff like firefox & xchat.

After that I would install my DE of choice, in my case KDE.

My reasoning behind this is that should KDE or Gnome or whatever ever freak out I can get into fluxbox and search/ask for help on the net via a firefox & irc.

Fortunately I have only been in this situation once and it was nice to have a backup, besides that I actually like fluxbox.

---

### Post by runningwithscissors on 2007-01-25
> **mips said:**
> I always do a fluxbox install first, this gives me a gui where I can work from and launch stuff like firefox & xchat.

After that I would install my DE of choice, in my case KDE.

My reasoning behind this is that should KDE or Gnome or whatever ever freak out I can get into fluxbox and search/ask for help on the net via a firefox & irc.

Fortunately I have only been in this situation once and it was nice to have a backup, besides that I actually like fluxbox.
Why emerge Fluxbox just for that? You already have TWM which you can use to lauch graphical stuff. Or even if you dont, since it is an optional component in modular X, it is only 148K or so, so it will compile much quicker than Fluxbox.

---

### Post by pay on 2007-01-25
> **zaratustra said:**
> Linus himself also says that KDE is better.hmm... let's all do what someone else tells us to do. I don't want to sound rude but it seems abit like off picking what software to choice soley by someone else telling you what to choose. With that same arguement I could say use Gnome because Ubuntu/Fedora use it has default. The only way you will know what WM you want is to test out the different ones and decide for yourself.

---

### Post by po0f on 2007-01-26
MoxJet,

If you go with KDE, make sure to use the split-ebuild approach.  It's been a couple of months, but AFAIK, it is still not the default.  To get a fairly light KDE install, just `emerge kdm kwin konqueror kdesktop`.  Apart from that, I suggest ark (archive manager), kopete (IM), and amarok (music player).  You'll find more apps to emerge as you need them.  ;)

Also, FluxBox was a fairly quick (~23 min) compile on my old 800Mhz Pentium 3 box if I remember right.  If you don't know how to use a *box environment, the configuration time, or even the time spent learning how to add stuff to the menu, might offset the quick compile though.

---

### Post by zaratustra on 2007-01-26
> **pay said:**
> hmm... let's all do what someone else tells us to do. I don't want to sound rude but it seems abit like off picking what software to choice soley by someone else telling you what to choose. With that same arguement I could say use Gnome because Ubuntu/Fedora use it has default. The only way you will know what WM you want is to test out the different ones and decide for yourself.Don't pull my words out of context. I wrote that as a additional argument. I wrote that I tried it myself and I think that it is faster an better than gnome. You don't sound rude, you sound like you aren't reading whole posts.

---

### Post by mips on 2007-01-26
> **runningwithscissors said:**
> Why emerge Fluxbox just for that? You already have TWM which you can use to lauch graphical stuff. Or even if you dont, since it is an optional component in modular X, it is only 148K or so, so it will compile much quicker than Fluxbox.

I happen to LIKE fluxbox.

---

