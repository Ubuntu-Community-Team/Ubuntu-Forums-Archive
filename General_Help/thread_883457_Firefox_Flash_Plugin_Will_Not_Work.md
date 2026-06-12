---
title: "Firefox Flash Plugin Will Not Work"
date: 2008-08-08
forum: General Help
---

### Post by yoman258 on 2008-08-08
I went to install my flash plugin and I must of clicked on a wrong one then the one I wanted. The one I have doesn't seem to work, the place a video should be shows up as a gray box with a play arrow and when I click it, it never loads or plays. I wanted to install the other flash plugin but I clicked the wrong one. I have searched all over the forums and google to find something to tell me how to remove this plugin or reinstall firefox to get back to defaults.

Any help please?

---

### Post by niyonk on 2008-08-08
in firefox, 
go to tools->addons and 'plugins' should be one of the main categories :) 

also look at [this page]("https://help.ubuntu.com/community/RestrictedFormats/Flash#freealternatives")

there you will find the names of the packages you might have installed and remove them.

Cheers! :biggrin:

---

### Post by yoman258 on 2008-08-08
Yea I have already been through this, that was one of the first things that I did. I am not THAT dumb :p. But yea I can view the stuff but I can not uninstall the plug in from there. So it doesn't much help me. I can disable it but then it doesn't give me the option to reinstall another flash viewer when I go to a flash video. Any tips?

---

### Post by mb_webguy on 2008-08-08
Open up Synaptic, and search for "flash".  The packages you want are flashplugin-nonfree, libflashsupport, and possibly ubuntu-restricted-extras (which will install the flashplugin-nonfree package and a number of others).  Mark those for installation (or reinstallation).  If any others are installed, such as libflash-mozplugin, mozilla-plugin-gnash, or swfdec-mozilla, mark them for removal.  If you want, you can mark the firefox package for reinstallation, as well.  Click apply to install and/or remove the packages, and you *should* be able to view Flash in Firefox.

---

### Post by niyonk on 2008-08-08
> **yoman258 said:**
> Yea I have already been through this, that was one of the first things that I did. I am not THAT dumb :p. But yea I can view the stuff but I can not uninstall the plug in from there. So it doesn't much help me. I can disable it but then it doesn't give me the option to reinstall another flash viewer when I go to a flash video. Any tips?

Well I did tell you to go to the link i posted and see what plugins you might have installed them to know their exact package names to be able to uninstall them like the above poster said.

No one said you are dumb, you should have read my post carefully. I was clear to say that you needed to find the names of those packages and i gave you suggestions to what they might be--> in the link, so that you can know what to UNINSTALL.

---

### Post by sirant on 2008-10-07
For what its worth......

I have been having this issue for a long time now. Been driving me nuts actually. I decided earlier today, for the first time in a year since 100% removing winblows from my system, if this flash issue wasn't resolved today, I would wipe ubuntu and go back to microsoft.

How rotten is that?

I was having the same issues as soo many others it seems. I tried EVERY fix I could read, and I couldnt even possibly begin to list them, to fix the nagging flash video problem in Firefox 3. It seemed to first start when I installed Americas Army to check it out. The videos still worked, but sometimes crashed. Then I installed Google Earth and bang, I got a white box where videos used to be. Not just youtube, but every flash site....

So I followed every forum post and walkthrough, all they did was turn my white blank box into a grey box with a play icon in the middle that did nothing. Arrrggggghh!!! of course it did not play.

In desperation I did this:

In synaptic I searched gnash and swfdec.

swfdec was installed, gnash was not. So I installed gnash too... No joy.

So I removed swfdec... Lo-and-behold, the box was white again, no Grey box with a circle and a triangle (typical play button)....

Went back to synaptic and uninstalled (complete removal for both) gnash....

Bam, flash videos are back and work great.....

I have heard rumors that Americas Army installs a flash player and perhaps Google Earth does too, which mess with Firefox. I have no idea. 

All I do know is by fully removing gnash and swfdec I got my flash back, hours before resorting to going back to the dark side....

I hope this works for others, and if it does, please spread it around the net! I know there are too many ubuntu'ites out there suffering this same problem. 

Hopefully the fix is this easy for everyone. (And hopefully they wont jump through hoops for 3 days like I did....

Maybe if I am feeling lucky I will install Google Earth again just to see if it mucks it up, but as for Americas Army, meh..... Urban Terror and so many other FPS are so much better. So wont bother testing that one.

Hope that helped some of you.

sirant

---

### Post by jamoo1980 on 2008-10-09
> **mb_webguy said:**
> Open up Synaptic, and search for "flash".  The packages you want are flashplugin-nonfree, libflashsupport, and possibly ubuntu-restricted-extras (which will install the flashplugin-nonfree package and a number of others).  Mark those for installation (or reinstallation).  If any others are installed, such as libflash-mozplugin, mozilla-plugin-gnash, or swfdec-mozilla, mark them for removal.  If you want, you can mark the firefox package for reinstallation, as well.  Click apply to install and/or remove the packages, and you *should* be able to view Flash in Firefox.

...this worked for me using Firefox-3.0. Thanks mb_webguy! (I don't know how to use the 'thanks' feature in this forum, anyone know?!)

---

