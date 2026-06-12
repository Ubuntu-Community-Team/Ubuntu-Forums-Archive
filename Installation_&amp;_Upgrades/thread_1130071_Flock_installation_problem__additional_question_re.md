---
title: "Flock installation problem // additional question related to the fonts"
date: 2009-04-19
forum: Installation &amp; Upgrades
---

### Post by Anthalion on 2009-04-19
Hello everyone,

first of all, sorry if this question has been answered previously; I searched the forums and I did, yes, found few discussions related to the Ubuntu & Flock, and I went through the all the methods that were discussed and recommended there however I got no real gain or results.

(maybe it has to do with the fact that most of the threads related to the this Flock & Ubutnu issue are over 1, even 2 years old)

Anyway, I think I gabbered enough... so, to the facts.

I just cannot install Flock in a manner that is consistent with my regular Ubuntu installations. Precisely:

- I did downloaded tar.bz2 (or whtvr the name is) file on my machine, and I extracted it, and it works if I simply run it from there. I manually made a starter in my main menu, and it runs OK, however there's problem with flash & other plugins probably cause I dont know how to set this Flock to look for the flash and other plugins in the same folder where all of mine net browseres are taking data for plugin's mentioned above and similar.

So, I gave that up. Its still there, tho. I just dont use it anymore, heh.

- Second thing I tried is: I found through some site ([www.getdeb.com](www.getdeb.com) ro something like that, I think) a .deb file which would then handle all the installation stuff itself.
Well, he did installed itself alone heh, however, I need to install the flash specially for him (wtf?), and that installation - fails. It reports to me that I need to install flash manually for this Flock, and I just dont know how. Offcourse, all my other browsers have all the necessary plugins so its obvious that this Flock is also ****** up concerning this.

So, its obvious that this .deb installation wasn't adjusted or aimed for Ubuntu at all. This version was 2.0.0 Flock, a release 8 to 9 months old, so maybe something changed and that .deb file didnt reflected the change that happened in the meantime or whatever...


In any case, there's two questions related to Flock that I am interested in:

- Well, how can I install Flock in my Ubuntu without having to bother with some additional flash/any plugin installation or manual installation and if that's impossible, could you just explain to me how should I add flash and other plugin's to any of those Flock installations mentionead above and second questions is...

- ... well, Flock is very respected and good browser. I searched through the repositories and upgrades, and there's not even a trace of any kind "get-" Flock command.
How's that? I think FLock really deserves this !


***

OK, now to my second question: I am having problem with my fonts under Ubuntu. Since I am VERY fresh Linux user (I think's this is pretty obvious so far heh), I still dont get the whole Linux/Unix concept however I learn something new every day... and its pleasure.

It kinda border's with sadomasochistic pleasure, heh ^^, but hey...

Anyway, I copied my fonts from Windows to Ubuntu, and yes - now I see all the fonts I am suppose too see on the pages, however, some fonts are still weird, and not very... well, definitely not fonts I am supposed to see.

Namely, wikipedia font definitely isnt the one that Is supposed to be, and  cannot found out at all so far what font is showing me instead of the one that he supposed to. Is there any program where I can found out which font wikipedia is showing to me, so I can SHUT IT DOWN with Fontmatrix? I disabled "freesans" and similar fonts already cause I already activated MSS truetype fonts in Fontmatrix, but still I get that weird font in Wikipedia.

There's also some sites where I get some really weird fonts instead font I usually see in Windows.

I am using Ubuntu 8.10. I used to have 9.04 few months ago, but It was simply too buggy at the time, so I decided to switch back to 8.10.

Before 8.10, I was using Kubuntu 8.10 for some time but KDE is way to slow for my machine.

Any suggestions?

Oh and P.S.

I actived microsoft's "sans" font's as the font for the system however seems that both metacity and Compiz bold this font very roughly and very bad. I never seen such a bad bold effect in Windows. Its barely readable, and I REFUSE to use any blur or other shite's for letters.

I like my letters raw however sans's bold effect in Ubuntu is just criminaly bad.


Thanks for all the help in advance,
-David
[www.elektronation.com](www.elektronation.com) (up in a month or two; I am industrial music journalist btw)

---

### Post by gamerchick02 on 2009-04-19
Flock on Ubuntu... I do this all the time.

Grab your tar.bz2 file, copy it to your home directory.  Unzip it there.  I've used it there with no problems.  This way it will update without having to run it as root (via sudo).

For your plugins, go to:

/usr/lib/mozilla/plugins

and grab all of the .so files and COPY them to your flock folder in your /home directory.

Restart flock, and you should have all the same plugins as Firefox has.

NOTE: Do NOT "MOVE" the .so files from the mozilla folder to the flock folder, as you won't have the plugins in Firefox if you do.

Also, make sure you have all the plugins installed in Firefox that you want to use in flock.

I have no clue on your font problem.  Try the flock install that way and it should work.

Amy

---

### Post by Anthalion on 2009-04-19
Thanks but this still doesnt answers my question properly, heh.

For instance, when you said that "it will update itself without having run it as sudo" - well, did you mean that it will update itself in terms of .so plugins I copy to Flock directory also?

Also, the plugins problem is then still, well - *ucked. I mean, thank you, but really - as I see by your avatar, if you like Flock so much - why dont you make a repository for Flock? I am not sure then that Flock will automatically upgrade plugins I copy there as you said it.

I would rather have a Flock showing in my repository programs neatly just like all the other programs do, cause I am virgo in zodiac (lol), and I like neatnees.

Really, why there isnt any Flock repo, and if there isnt, well, should I ask the guy who did that unsuccessful .deb file to try to make repo .deb file for us Ubuntuers?


***

As for font, no, you didnt read the post carefully enough. After It failes, I did downloaded all the fonts through repos and this problem still persists.
It also has to do with the way Ubuntu makes bold letters. Can that be upgraded/changed, cause Ubuntu sucks at making my sans font bold. Its unreadable, and windows didnt had that problem.

Thanks'
-David

---

### Post by Anthalion on 2009-04-19
Seems people forgat about this thread. :(

---

### Post by gamerchick02 on 2009-04-19
You know how Firefox and Flock update themselves in Windows?  They search for the new version of the program and update.  That's what I meant by not having to update it as sudo.

The plugins will stay there and once you install them via the method I outlined, you should have no issues with them.

If you're talking about plugins, those are the flash and other stuff... once those are installed, you don't need to do anything with them.  Extensions (flashblock, adblock, scribefire, etc) will automatically update like they do in Firefox.

I'm not in charge of repos. 

~~~~~~

I offered support for your Flock problem, not your font problem.  Fonts aren't my forte, so to speak.

---

### Post by tmsbrdrs on 2009-07-24
[https://launchpad.net/~fta/+archive/ppa](https://launchpad.net/~fta/+archive/ppa)

This allows Flock to be added to Synaptic. The version is 2.0.

I came across it by accident and, since I use Flock as well, decided I'd spread the word.

---

