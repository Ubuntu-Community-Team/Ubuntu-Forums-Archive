---
title: "lost brightness control in 8.10"
date: 2008-11-01
forum: General Help
---

### Post by jdrodrig on 2008-11-01
Hi,

I just upgraded to 8.10 from 8.04 in a toshiba m35 laptop and up to 8.04 (from 7.04) I was able to use the screen brightness control(Fn+F6,F7) but now it wont work anymore.

Any ideas?

---

### Post by prshah on 2008-11-01
> **jdrodrig said:**
> I was able to use the screen brightness control(Fn+F6,F7) but now it wont work anymore.


Can you check if the "Brightness Applet" works? That will tell us if the problem lies with the brightness/dimming capability or the key combination. Right click an empty area of the panel, choose "Add to Panel" and choose "Brightness Applet" from the dialog box that pops up, then click "Add"->"Close". When you scroll your mouse over the applet, the screen should dim down / brighten up.

---

### Post by haran_elessar on 2008-11-01
I'm having that same problem but worse. I can change the brightness level using Fn+up or down in my Dell Inspiron 6000 but if I do that gnome will crash.  The brightness image will stay in the desktop and won't fade away and I can't click on anything.  When that happens all I can do is logout using ctrl+alt+backspace.

I installed the brightness icon in the panel as you said I when I scroll the brightness doesn't change...even though the icon says the bright percentages are changing.

This is happening now that I installed Intrepid...it never happened before. Any help?

---

### Post by jdrodrig on 2008-11-02
Thanks prshah, the brightness applet worked, but the key combination is still not working.

---

### Post by wgrant on 2008-11-02
> **haran_elessar said:**
> I'm having that same problem but worse. I can change the brightness level using Fn+up or down in my Dell Inspiron 6000 but if I do that gnome will crash.  The brightness image will stay in the desktop and won't fade away and I can't click on anything.  When that happens all I can do is logout using ctrl+alt+backspace.

I installed the brightness icon in the panel as you said I when I scroll the brightness doesn't change...even though the icon says the bright percentages are changing.

This is happening now that I installed Intrepid...it never happened before. Any help?

There are at least two separate bugs here, both known. The lack of being able to focus anything else can be temporarily resolved by flipping to a VT and back (Ctrl+Alt+F1, Ctrl+Alt+F7). As for the brightness control not working, that is more hardware-specific. I'm right now preparing a version of gnome-power-manager which you should probably test.

---

### Post by wgrant on 2008-11-02
OK, it has built and seems to work fine here. Try gnome-power-manager from [my PPA](https://launchpad.net/~wgrant/+archive). You'll need to log out and in for it to start working.

Basically, some Dell video cards report that they can change LCD brightness themselves, when in reality you have to go through the BIOS. In Intrepid, gnome-power-manager trusts the video card over hal (which knows about the BIOS mechanism). My package reverses this - hal will be believed over the video card.

---

### Post by haran_elessar on 2008-11-02
Thank you very much William!  That fixed my problem.  I still can't use the Fn+up/down combination but the applet works just fine.  I must just get used to changing the brightness via the applet or the system will lock. I wonder why I didn't have this problem while running from the live cd...if it's hardware related shouldn't it had happened while running the live cd?  Do you think that if I do a fresh install the problem could be fixed?

With what you explained I believe a fresh install won't fix a thing but I'm asking just in case.  It's better to make a dumb question than not asking at all:).  Anyway thank you very much for your help.  It's always gratifying to see how fast the Ubuntu community takes good care of their userbase.  Today I just installed 8.10 on a friend's laptop and didn't have a single problem...you should've seen how happy he was...he felt like he had a new computer...right now he wrote me saying that he'll stay up late playing with his new laptop :lolflag:

keep up the good work!

---

### Post by Comhra on 2008-11-02
Thanks William, I now have Brightness Control.

---

### Post by wgrant on 2008-11-02
You did have the problem on the live CD.

We're working on the brightness key focus-stealing issue, but we're not making an awful lot of progress.

---

### Post by Comhra on 2008-11-02
Oh, I see that you're one of the developers.  Well, this means that I can congratulate you in person.

Ibex is a fine Distribution.

Great work, William.

---

### Post by haran_elessar on 2008-11-02
Yes, I did have the problem :).  Just didn't adjust the brightness control during the setup.  Thanks again!

---

### Post by mrandersonmd on 2008-11-03
This issue has anything to do with Hibernation problems too??

Well Hibernation works well when selected from power menu on top bar, but doesn't work when activated via hotkey Fn+F1 on my Inspiron 640m.

In fact it locks the keyboard and touchpad button, and the only way to unlock it is using Ctrl-Alt-F1 and Ctrl-Alt-F7 as said by wgrant.

The update for gnome-power-manager from wgrant worked well, I don't get the icon that shows how contrast changes, but it doesn't matter, to get contrast workin with Fn keys is more important. Thanks wgrant for the modification to that package.

By the way, I've added the contrast applet to top bar too, and with wgrant gnome-power-manager package the slider of the applet doesn't move in synchronism with the modification of the contrast with Fn+Up or Fn+Down... Is this normal??

Greetings from Chile.

---

### Post by klausner on 2008-11-06
> **wgrant said:**
> OK, it has built and seems to work fine here. Try gnome-power-manager from [my PPA](https://launchpad.net/~wgrant/+archive). You'll need to log out and in for it to start working.

I've got a Vaio Z-Series with 8.10, and I still can't change the screen brightness. I tried installing your new gnome-power-manager, along with the new daemon you have there. Restarted X, even re-booted the system, still no joy. :(

---

### Post by wazzzup on 2008-11-07
> **klausner said:**
> I've got a Vaio Z-Series with 8.10, and I still can't change the screen brightness. I tried installing your new gnome-power-manager, along with the new daemon you have there. Restarted X, even re-booted the system, still no joy. :(
The same situation on my Asus M51Va. Brightness control doesn't work at all and I have no chance to increase brightness which is currently very low. :(

---

### Post by smbaf1 on 2008-11-07
Same problem with Dell Inspiron 630m and 8.10.  I am able to adjust the brightness with the package from wgrant and the new panel button, and the control alt F1 and F7 allow me to not reboot when I actually use the keyboard short cut.  thanks!

---

### Post by Wrinkliez on 2008-11-10
Hey, thanks for the fix, I can now change my screen brightness with the applet.  But, on a lesser bug, it tells me that it cannot get the laptop panel brightness, even when it clearly can change it.  Any suggestions?

---

### Post by felipelavinz on 2008-11-10
This is happening to me too: 
I can decrease brightness but can't increase it with my Function keys. 

Brightness applet works, though.

I've seen many bugs like this on Launchpad, but haven't found the main ones so I can send info (if needed) or follow the changes... has anyone know which ones are?

---

### Post by wazzzup on 2008-11-15
> **wazzzup said:**
> The same situation on my Asus M51Va. Brightness control doesn't work at all and I have no chance to increase brightness which is currently very low. :(
So, I found the temporary solution [here]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/224636/comments/7"). And it works for me.

---

### Post by klausner on 2008-11-16
> **wazzzup said:**
> So, I found the temporary solution [here]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/224636/comments/7"). And it works for me.

Doesn't help those of us using other hardware. :(

---

### Post by VonTrier on 2008-11-19
Hi there! 

I have the same problem with the brigthness applet. Actually it is kind of difficult to write this message, I have just upgraded my hardy heron to 8.10 and I have quite a headache; this is really shiny! I noticed some of you solved the problem by following William's advice (Thanks Mr, Developer), but the thing is that don't know how to follow William's advice, Specifically what he said: *_"OK, it has built and seems to work fine here. Try gnome-power-manager from my PPA. You'll need to log out and in for it to start working._*
Could anybody be so kind as to walk me through while I fix this shiny problem...

Thanks a bunch!

---

### Post by Loan_Refi on 2008-11-29
Hi, I just did a fresh update to 8.10 Intrepid and brightness control worked but crash my session.

My sytem;
Dell Inspiron 300m
1gb memory

I added the applet to the menu bar but did not work either.

I tried the instructions per William Grant but this did not work either;

deb [http://ppa.launchpad.net/wgrant/ubuntu](http://ppa.launchpad.net/wgrant/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/wgrant/ubuntu](http://ppa.launchpad.net/wgrant/ubuntu) intrepid main

I loged out & in and did not work.

Can someone help me trouble shoot this problem?
Thanks!

---

### Post by haran_elessar on 2009-02-08
Hi,

I just want to say that the brightness function in my laptop is working once again.  The latest kernel currently running is 2.6.27-11...a very recent update.  I don't know if the problem was fixed during that update or before since I didn't try the keyboard combination before today. 

I have a dell inspiron 6000, intel 915GM.

I can, once again, use the keyboard combination without the system crashing.

thanks!

---

