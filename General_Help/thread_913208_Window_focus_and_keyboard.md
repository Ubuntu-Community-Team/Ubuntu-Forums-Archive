---
title: "Window focus and keyboard"
date: 2008-09-07
forum: General Help
---

### Post by FirefoxRocks on 2008-09-07
I have a problem that is quite annoying. It involves a window losing focus and the keyboard not working.

Example: Typing a message in aMSN, a new contact signs in (focus is moved to the little notification thing at the bottom), the keyboard doesn't work in the window where I was typing my message.

To regain keyboard control of the original windows, I have to shift focus to another window (such as Firefox, or the aMSN contact list window, or something else) and then go back to the window where I was typing. This can be done quickly via ALT+TAB but it gets really annoying if contacts sign in consecutively one after another.

This problem does not seem to occur in Firefox, but is very noticeable in Opera, aMSN and programs running under Wine such as Notepad++. Pop-up notifications from system tray does not affect this (Software Updates Available, (the song playing in Rhythmbox), etc).

Clicking in the text field/document at another position (e.g. by moving the cursor) does not remedy the problem, the window has to be refocused upon to continue typing.

This slows down my typing A LOT. What should I do? I am running Ubuntu 8.04. I should also say that this problem does not occur in Ubuntu 7.10, which is running on an older computer currently.

Help please!!

---

### Post by FirefoxRocks on 2008-09-09
bump? help anyone? I'm avoiding typing in Ubuntu and using openSUSE right now.

---

### Post by vitcra on 2008-09-22
I have the same problem, I think, but could not solve it so far and could not find an answer yet.

I use the latest Ubuntu and experience this problem in Krusader (but in Kile as well, and I pretty sure there must be other cases, but I think it is only about KDE programs, though the problem occurs equally well in both GNOME and KDE). 

In Krusader for example, after I copy a file from one panel to the other, the keyboard stops to respond. I then click with the mouse on the panel other than where the cursor seems to be (and it is frozen) and then it starts to work again.

---

### Post by federico.boschetti on 2008-12-01
I'm experiencing the same troubles on Ubuntu 8.10 (but previously on Ubuntu 8.04).

In particular, I lose keyboard control switching from a terminal or from NetBeans to other applications.

I have an NVIDIA GeForce Go 7300 installed on an Asus A6000 laptop.

Did you discover how to fix the problem?

Tx

---

### Post by rob4jp on 2008-12-02
I also have the same problem, I think. With Ubuntu 8.10. When I use Kile to edit LaTeX files, and use it to launch KDVI the main text field in Kile stop working. It loses keyboard focus, that's OK, but clicking on the text field does not make it regain the focus. Instead I first have to click on some other window, and then on again in the Kile text field to make it regain focus.

This is very annoying... It used to work better but some time ago this problem appeared. Maybe some software update broke it. I would also be very interested in a fix to this problem...

Rob

---

### Post by DeXOR on 2008-12-03
I have a similar problem but the keyboard hangs completely in gnome. It is almost as if a modifier key(Ctrl, Alt) is stuck. I cannot access any menus in programs or on panels and i cannot type anywhere.

---

### Post by ramady on 2009-01-24
I have the same problem with kile and ubuntu 8.10. It's very annoying. It happens when I click save button. The keyboard works again after switching to another pane and come back to the editor pane in the same program.

---

### Post by cecom92 on 2009-02-10
anyone? I also have the same problem with 8.10 and kile.

---

### Post by rob4jp on 2009-03-04
No one seems to have any solution to this annoying problem... And it seems to effect many different programs so I'd say it is quite a serious bug. It should probably be reported to the developers. Does anyone know how that usual is done?

---

### Post by mkenniston on 2009-04-13
I had been experiencing this (or a very similar) problem for weeks, and today on another thread I found someone suggesting un-installing SCIM.  I tried that, rebooted, and now everything seems to work normally.  Alas, this isn't the first time that removing SCIM has fixed some obscure and annoying problem that I was having with Ubuntu.

If you're not familiar with package management, here's the basic procedure:

On the main Ubuntu menu select: "System - Administration - Synaptic Package Manager"
Click the "Search" icon and search for "SCIM".
In the list you get, find the main SCIM package, right-click, and select Remove.  It will want to uninstall a couple other packages too, and that's fine.
Click on Apply.
When it finishes, do a full reboot of Ubuntu.  (This is important; although the removal claims to be complete, the keyboard-focus-bug didn't go away for me until after I rebooted.)

Of course, this will only work if you aren't using SCIM to let you do keyboard entry of foreign-language characters.

---

### Post by l0co on 2012-03-14
Two years later I still have this problem in 10.10. I'm really angry because of that, this prevents the ordinary programmer work under this system. SCIM doesn't help. Does anybody know what the hell to do with this?

---

