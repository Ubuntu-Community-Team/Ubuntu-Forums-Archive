---
title: "I want it back to normal!"
date: 2008-11-01
forum: General Help
---

### Post by TimboUK on 2008-11-01
Hi everyone!

I was wondering if anyone can help.

Over the last two months, I was messing around with colours, windows etc.

Now this problem I have ignored for the last few weeks, however now I would like a little advise.

Since I have changed the colours on my windows, all my themes fail to display the correct ones.  I am stuck with windows of blue (which is fine) but I want to revert back to the original Ubuntu colour scheme.  Ive tried going to the "appearance" and selecting default, it doesnt work.

Can anyone give me Terminal advise on how to just revert the colours back to the original ones?  A terminal command or series of commands.

I have just installed Intrep (updated 8.04) and I had hoped that would solve it.  It hasnt, as all my colour schemes.

Thanks in advance.

---

### Post by OrangeCrate on 2008-11-01
> **TimboUK said:**
> Hi everyone!

I was wondering if anyone can help.

Over the last two months, I was messing around with colours, windows etc.

Now this problem I have ignored for the last few weeks, however now I would like a little advise.

Since I have changed the colours on my windows, all my themes fail to display the correct ones.  I am stuck with windows of blue (which is fine) but I want to revert back to the **original Ubuntu colour scheme**.  Ive tried going to the "appearance" and selecting default, it doesnt work.

Can anyone give me Terminal advise on how to just revert the colours back to the original ones?  A terminal command or series of commands.

I have just installed Intrep (updated 8.04) and I had hoped that would solve it.  It hasnt, as all my colour schemes.

Thanks in advance.

Have you tried reinstalling the Human Theme (human-theme) from Synaptic?

---

### Post by Alaric on 2008-11-01
Well, you could try moving all of your settings to a backup folder and restarting gnome.  This should work

mkdir ~/backup
mv ~/.gnome ~/.gnome2 ~/.gconf ~/.gconfd ~/.metacity ~/.compiz ~/backup
sudo /etc/init.d/gdm restart

---

### Post by TimboUK on 2008-11-01
Thanks for the advice.

Niether option makes any difference.

I still have the blue windows frame.  Does anyone have any other ideas before I consider a complete re-install?

Thanks alot.

Kind regards.

---

### Post by OrangeCrate on 2008-11-01
Sorry, nothing from me.

:(

---

### Post by ARhere on 2008-11-01
The first step to troubleshoot this is to try changing the window frame itself.

Goto [http://art.gnome.org/themes/metacity/](http://art.gnome.org/themes/metacity/) and download a windows boarder theme. 

Goto **System --> Preferences --> Appearance**

Click and drag the extracted folder to this box and select, "Keep current theme"

Under Theme Tab click **Customize** and click the "Windows Boarder" tab.

Scroll down and click on the new boarder and see if it is still blue.

***NOTE:** I have just noticed all of the default window boarders are all BLUE!?!?  I have 8.10 loaded so maybe this is an odd bug?  Someone else confirm please.*

-AR

---

### Post by OrangeCrate on 2008-11-01
> **ARhere said:**
> The first step to troubleshoot this is to try changing the window frame itself.

Goto [http://art.gnome.org/themes/metacity/](http://art.gnome.org/themes/metacity/) and download a windows boarder theme. 

Goto **System --> Preferences --> Appearance**

Click and drag the extracted folder to this box and select, "Keep current theme"

Under Theme Tab click **Customize** and click the "Windows Boarder" tab.

Scroll down and click on the new boarder and see if it is still blue.

***NOTE:**** I have just noticed all of the default window boarders are all BLUE!?!?  I have 8.10 loaded so maybe this is an odd bug?  Someone else confirm please.***

-AR

Not here, they're normal on Intrepid.

---

### Post by TimboUK on 2008-11-01
Thanks all.

That gnome.art advise was great, Ive now changed my mind again!!! I dont want to go back to the original colours! Thanks very much.

One other question, if I may just sneak it in????

Why do we have the add/remove packages feature when the Synaptic Package manager does the same thing and has more software?

---

### Post by OrangeCrate on 2008-11-01
> **TimboUK said:**
> Thanks all.

That gnome.art advise was great, Ive now changed my mind again!!! I dont want to go back to the original colours! Thanks very much.

One other question, if I may just sneak it in????

**Why do we have the add/remove packages feature when the Synaptic Package manager does the same thing and has more software?**

That's a question that's been debated many times on the forums, without a definitive answer. Here's just one thread, there are more...

[http://ubuntuforums.org/showthread.php?t=433516](http://ubuntuforums.org/showthread.php?t=433516)

---

### Post by ARhere on 2008-11-04
> **TimboUK said:**
> Thanks all.

That gnome.art advise was great, Ive now changed my mind again!!! I dont want to go back to the original colours! Thanks very much.

One other question, if I may just sneak it in????

Why do we have the add/remove packages feature when the Synaptic Package manager does the same thing and has more software?

I have a simple answer, but it is just a weak opinion.  

The Synaptic Package manager is just a GUI version of apt-get to me.  *I know they are not exactly the same but that is just how I look at it.*  Add/Remove is a complete software package add or removal tool.

I have an example, go to ADD/REMOVE and search for Tux Paint.  If you install it there it will add the base program plus effects package.  Now go to Synaptic Package manager and search for Tux paint as well and you have the ability to add or remove the individual packages, like the extra stamp package and parental control.

-AR

---

