---
title: "firefox problem"
date: 2005-11-18
forum: General Help
---

### Post by krcm on 2005-11-18
I have done something kinda stupid:(  last night, wanted to do an update via konsole but accidentaly typed upgrade. Since then I've noticed another stupid mistake, in my sources list there were a few lines for breezy.

So I must have installed some breezy stuff over the hoary, for example there is no more 'root konsole' in the applications list. That is not exactly a problem but that is what started me thinking that I probably had some breezy stuff .

The only real problem I have come across since then is that firefox doesn't work properly anymore, the pages do not load completely but without giving any error.

Hopefully you lot can help me especially with the firefox but any help on getting rid of the breezy stuff is welcome as well.
I already changed the breezy lines in the sources list into hoary and did another upgrade.

thx 
greetz
An

---

### Post by AmboyGuy on 2005-11-19
For your FireFox problem try creating a new firefox profile .
The way I did it was I right clicked on the firefox globe in the panel and clicked properties. Change the command from "...firefox %u"  to " firefox -profilemanager ".
 
Make sure you've exited firefox and click on the globe to restart. 
When the Profile Manager pops up chose rename and name your existing profile something like orig or old. 
Now choose create new profile, give it a name ( I usually add a date ie. FF1.5-20051119 )
When your finished click Start Firefox. You'll notice that all your bookmarks are gone.
( Don't panic !!! ) ( I can already feel my ears burning " nice f___ing trick there AmboyGuy " ).
Using your Filemanager, enable show hidden files, and get to the **.mozilla** folder.
In .mozilla/firefox you'll find two profile folders ( something like "u1iuzgy7.old" or your original profile) and a new one. Copy your bookmarks.html file to your new profile folder. I use Gentoo as my filemanager, but you should be able to figure it out.
Restart firefox and see that everything is working.

Other files you can also copy over :
Cookies.txt ( Gmail, Yahoo, MSN cookies etc.), Signons.txt (passwords)
Hostperm1 (cookies & image blocking stuff) .

Any extensions or themes you'll have to reload. 
[http://www.extensionsmirror.nl/](http://www.extensionsmirror.nl/) is a good place to look.

95% of the time a new profile will fix any problems in firefox. Re-installing almost never works.

I have firefox start up with the profile manager and select which profile I want to use. I have one for general browsing, one setup for Forum browsing ( with it's own extensions & theme ) etc.

Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8 ) Gecko/20051119 Firefox/1.5 - Build ID: 2005111904

---

### Post by krcm on 2005-11-19
it didn't work, should have specified the problem more.
firefox seems to be working alright but with almost all of the normal text missing as you can see in the attachment.
this was also the case in the window of the profile manager.

I've now been thinking that maybe firefox just can't reach the fonts anymore but I don't know how to check that and what to do about it.

An

---

### Post by AmboyGuy on 2005-11-19
You could try using the synaptic package manager to re-install the version of firefox you're using.
Start Synaptic and search firefox. Mark each package you have installed for re-installation and apply.
My system has three :  mozilla-firefox (1.0.7), mozilla-firefox-gnome-support (1.0.7), & mozilla-firefox-locale-en_gb.

 I also installed Firefox 1.5 in my home directory and pretty much use it all the time.
Gmail works fine for me. Is Gmail the only site giving you the problem ?

---

### Post by krcm on 2005-11-20
Hi, 
no it's not just gmail that gives the problem but every site and also other stuff to do with firefox like the profile manager.
I have already reinstalled everything, even did a force install to a previous version through synaptic but the problem isn't solved yet.
greetz
An

---

### Post by thomax on 2005-11-22
Try to do a complete removal first (with synaptic), and then reinstall, that might work. Maybe you should also remove all mozilla libs and reinstall the, the problem could also be there.

Contact me for further help ;)

Thomas

---

### Post by krcm on 2005-11-24
I've been looking at those libs and other dependencies for firefox and it seems that for a lot of them it's not the hoary-version witch is installed. 
I've tried force installing the hoary version but for that synaptic would have to remove a lot of other stuff as well, like gstreamer etc.
I don't really want to do that, is there a way to do this downgrading of certain files without other programms being deleted? Maybe through the konsole?

Or maybe it would be easier to just install breezy but i've been reading from quite a few people that they've had problems installing breezy, anybody has some tips for me on that subject?

thx
An

en bedankt hé Thomas :smile:

---

