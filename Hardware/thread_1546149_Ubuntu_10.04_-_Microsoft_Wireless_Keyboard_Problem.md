---
title: "Ubuntu 10.04 - Microsoft Wireless Keyboard Problems"
date: 2010-08-04
forum: Hardware
---

### Post by bluec10 on 2010-08-04
I just installed Ubuntu 10.04 and I've got problems with my Microsoft Wireless Keyboard and Mouse. Did a clean install of Ubuntu.

The keyboard allows me to type 2 or 3 letters after log-in, then stops working.  The mouse works fine to that point, then starts acting weird.  It doesn't allow me to click items on the control bar on the desktop, but allows me to click links in the browser window.  

The keyboard and mouse work 100% in a Windows 7 environment.

Suggestions?

---

### Post by Ozitraveller on 2010-08-04
Something along these lines?

Ubuntu 10.04 (Lucid Lynx) Random Freeze / Hang-up
[http://ubuntuforums.org/showthread.php?t=1478787](http://ubuntuforums.org/showthread.php?t=1478787)

---

### Post by utilitytrack on 2010-08-04
> **bluec10 said:**
> The keyboard allows me to type 2 or 3 letters after log-in, then stops working

Your keyboard understand suddenly that it's not Windows and declare a strike :))
I'm absolutely sure that it's Steve Ballmer's provocation.

---

### Post by VeeDubb on 2010-08-05
Just a sanity check here, and no offense intended.

Have you replaced the batteries in your keyboard?

My MS Wireless keyboard works like a champ.  As much as I dislike their OS offerings, I'm a big fan of most other MS products.  Every MS branded mouse or keyboard I have ever owned has worked flawlessly with linux, and performed/lasted extremely well.

The only trouble I've ever had is that some of the MS keyboards have more "extra" keys than the current linux kernel knows what to do with.

---

### Post by theozzlives on 2010-08-05
Yeah, I'd say it sounds like batteries. My MS Wireless keyboard and mouse work without a hitch, except when the batteries are low.

I'd also consider the placement of the receiver.

---

### Post by Jeztastic on 2010-08-11
I have this exact same problem, and have had it in every install since 8.04. It is emphatically NOT the batteries. It is most irritating.

---

### Post by LeandroMattioli on 2010-08-11
Similar problem here.

After one key press event on my wireless keyboard on Ubuntu 10.04, and without holding the key, the OS will continue getting the press event forever!!!

An example just to clarify:
You type letter "a" in a gnome terminal, you release the key but it goes "aaa...." . You can close the terminal, you can actually unplug the keyboard, it will still do "aaa...." .

This didn't used to happend in 9.10 .

I believe it is related to some updates in the kernel.

Maybe "Redmond" is corrupting the kernel :)

---

### Post by bluec10 on 2010-08-12
The problem is not batteries or the placement of the receiver - the keyboard and mouse work flawlessly in a Windows 7 environment.

I've seen a lot of posts about this issue where people complain, but has anyone found a solution?

---

### Post by dimospap on 2010-10-23
hello everyone,
I am facing a similar problem with a microsoft wireless keyboard. it used to work fine but -I guess after a kernel update- it just behaves weird. I managed to log in a secondary user account that requires no password. And then I checked what effect do the key strokes have in a text editor: a nightmare... examples: backspace function is located in "f", letter "A" is in "8". Any ideas what is going wrong?

---

### Post by singho on 2010-11-07
**SOLVED SOLVED SOLVED !!!!!!**

After suffering the same problem starting from 10.04 release, think I hit on the workaround.

My MSFT Wireless keyboard receiver was connected using the PS2 connectors (Purple for Keyboard and Green for Mouse)

[COLOR=DarkRed]**Solution is to disconnect both the PS2 connections and connect the Wireless receiver using the [COLOR=DarkGreen]USB connector ONLY[/COLOR]. NO PS2 keyboard or mouse connected. **[/COLOR]

:guitar:

---

### Post by scrambled egg on 2010-12-07
> **singho said:**
> **SOLVED SOLVED SOLVED !!!!!!**

After suffering the same problem starting from 10.04 release, think I hit on the workaround.

My MSFT Wireless keyboard receiver was connected using the PS2 connectors (Purple for Keyboard and Green for Mouse)

[COLOR=DarkRed]**Solution is to disconnect both the PS2 connections and connect the Wireless receiver using the [COLOR=DarkGreen]USB connector ONLY[/COLOR]. NO PS2 keyboard or mouse connected. **[/COLOR]

:guitar:

Spose it works in your case but not mine.i am running ubuntu 9.10 (linux kernel2.6.31-22-generic). i have tried to install 10.10 and 10.04 from a live disc 
(mouse freezes and keyboard fails completely in both instances). tried upgrade from 9.04 with system>Administration>Update manager. system froze running a pentium 4 (3.06ghz) 2 gig Ram. I am using microsoft media desktop 1000 wireless keyboard and mouse CONNECTED to a USB HUB. The BATTERIES DONT need changing cause well i am writing this using them on my Karmic machine. Luckily i kept all back ups on a removable hd so the reinstall of Karmic went relatively smooth and painless. Is there anybody who can give me some helpful advise other than telling me to go and buy a cheap keyboard and mouse (defeats the object of this problem):popcorn:.
.

---

### Post by eldamario on 2011-05-27
I have the exact same problem were the key is locked and repeats infinit until pressed again. This went away a short period in 10.10 and now it's back again in 11.04.

---

### Post by fixeon on 2011-07-11
> **eldamario said:**
> I have the exact same problem were the key is locked and repeats infinit until pressed again. This went away a short period in 10.10 and now it's back again in 11.04.

Same here

---

### Post by grigglestone on 2011-09-15
So this workaround works in my setup, not sure if it would work in yours. A savvy engineer could probably infer what is going on based on the workaround, but unfortunately I'm not that savvy!

So I never have issues at the login prompt. One time while testing the issue we are all talking about I typed a bad password (had something resting on a key) .. I erased it, then logged in and noticed I did not get the normal failure (I was testing this by immediately opening a console and start typing). Now on each boot I type maybe 30 to 40 characters to the login prompt, erase them, repeat, then login properly and hey presto, no issue (well maybe once in 100 logins it hangs in the same way) .. but otherwise ok.

I am using a Dell laptop:

[LIST]
[*]I don't get the issue when I use the laptop keyboard
[*]I don't get the issue when I use a wired keyboard
[*]I didn't get the issue when using 9.10
[/LIST]
PITA .. something changed and I can't work out what.

---

### Post by grigglestone on 2011-09-15
fyi .. just tried connecting via USB only (using PS2 to USB adapter for  the keyboard that was PS2) and have not seen a problem since

so the issue is somewhere in the PS2 handlers

---

### Post by fitz318is on 2012-09-14
Bringing back an old thread,

Same problem on 12.04, well mint 13 actually and on new raspberry pi.

Changed the proximity and the batteries, no change.

I dont want to go back to wired.

---

