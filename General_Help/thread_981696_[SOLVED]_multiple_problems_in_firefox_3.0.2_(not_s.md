---
title: "[SOLVED] multiple problems in firefox 3.0.2 (not sure if they are related)"
date: 2008-11-14
forum: General Help
---

### Post by alisonjo2786 on 2008-11-14
**Note: I haven't been able to get any help with this problem, and this is my second time posting a thread, and I've been "bump"-ing this thread or the previous version of it for over 2 days, so... I'm not sure if I'm doing a poor job explaining it or if I'm posting in the wrong place or what, but anyone, please, even if you don't have an answer for me, please, I'm open to any advice at all -- about how to get help with this or anything else.  Thank you.**

Recently I've been having problems like never before in Firefox. I don't know if the problems are related, so I'm putting everything in one post just in case. Please let me know if I should put any of this in its own post, and thank you in advance for any help you can offer.

(In case any of this information helps, this all the info about my version of Firefox...)[INDENT]Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.4) Gecko/2008110400 Ubuntu/8.04 (hardy) Firefox/3.0.2pre
[/INDENT]Starting maybe 7-10 days ago, every time I started Firefox (regardless of whether I was starting new or restoring old sessions), it opened itself up in un-maximized windows (same size each time, just not maximized), even though I didn't quit from an un-maximized window in my previous session or anything like that. **(--> see screenshot)**

Then, maybe 4-7 days ago, the toolbar that's part of this add-on I have, Linkwad, started showing up every time I started Firefox (whether starting new or restoring old sessions), even though every session I would uncheck the box for "Linkwad toolbar" in View > Toolbars (and until this started happening about a week ago, I'd had the Linkwad toolbar continuously disabled for many months).

So I figured I'll just uninstall this add-on, since I never use it anyway, and now it's being temperamental.  But, when I went to Tools > Add-ons, nothing was there -- the "Add-ons" window popped up, but all the fields were empty.  I clicked through all the tab/buttons in the Add-ons window, and they were all just empty.[B] (--> see screenshot)
[/B] 
So that was obnoxious, but I was pretty busy, so I let it go for a few days more.

But then... starting two nights ago, things got much worse.  At one point I tried to "Bookmark all tabs", and when I hit the enter key/clicked "Add bookmarks," the pop-up "add bookmarks" window didn't go away.  I thought nothing had happened, so I kept hitting enter, and then I tried closing the "Add bookmarks" window and trying again, still no luck -- then I realized it had sort of been working, in that every time I hit enter, a folder was created in my Bookmarks menu (however, only some of the tabs I had open were in this folder, and a couple of the folders were simply empty).  So I went to "organize bookmarks" to delete all the stupid folders I made, but, the "Organize bookmarks" window that popped up had the same problem as the "Add-ons" window -- all the fields were empty. ** (--> see screenshot)** Mind you, all my existing bookmarks are still in the Bookmarks menu (and all my Add-ons are still working, at least, the ones I've tried to use are working).

Also, if I tried to add a Bookmark into a specific Bookmarks folder, my bookmark folders didn't show up in the "add bookmark" pop-up windo thing. **(--> see screenshot)**

And, finally, only today, I haven't been able to add a bookmark at all.  If I do "Ctrl + D" or if I click on Bookmarks > Bookmark This Page, either way, no window pops up and no Bookmark gets added.

So. That's pretty much it I think. Thank you so much for any help you can offer, and please let me know what other info I should provide. (I'm not 100% new with Ubuntu, but I've never posted a question before.) (except for when I posted a longer version of this question about 26 hours ago.)

(Obviously, let me know if I should split this thread up, I'm not at all sure that these problems are related.)

:confused:

---

### Post by alisonjo2786 on 2008-11-14
bump (just because I added screenshots and a couple of lines)

---

### Post by alisonjo2786 on 2008-11-14
bump

---

### Post by alisonjo2786 on 2008-11-14
bump

---

### Post by alisonjo2786 on 2008-11-15
bump

---

### Post by alisonjo2786 on 2008-11-15
bump

---

### Post by detroit/zero on 2008-11-15
If it were me and I was having problems like that and not getting any help, the first thing I would do is a complete uninstall/reinstall.

If your bookmark file is intact as you say, you can find a copy of it in *~/.mozilla/firefox/yourprofile.default/bookmarks.html*, or *~/.mozilla/firefox/yourprofile.default/bookmarks.bak*. There's also a folder named *bookmark backups* that's going to have multiple copies of your bookmarks file from the last several days/weeks/whatever.

I'd verify that the file has what you want in it and make a copy and stick it somewhere like your desktop, then go ahead and remove everything from synaptic using the right-click>completely remove option. Then go back and delete the .mozilla folder from your home directory. Then reinstall it.

Maybe it's not the solution you want/expect, but it's all I can offer because, man, that stuff is pretty damn weird. 

I've had to go through it with FF3 a couple times. FF3 is crap, IMHO. It hogs more rsources than FF2 ever did, I have problems with flash and java plugins, and extension/theme development for Linux versions is pretty lacking compared to Windows and even Apple versions. I mean, [Firefox 3 has been around for five solid months now]("http://www.efluxmedia.com/news_Firefox_3_To_Make_Its_Debut_On_Tuesday_June_17_18925.html").. I can't believe the state that it's in.

When you get around to reinstalling (assuming that you listen to me), you might want to go ahead and roll it back to FF2 and save yourself some headache. Seriously: what features are you really going to miss out on?

Sorry to rant. I'll shut up. Best of luck to you. Hope it works out.

---

### Post by alisonjo2786 on 2008-11-15
I greatly appreciate your advice and candor/ranting :)  Sure, I don't want to uninstall/reinstall, but it's a good idea and maybe it will work.  You know what is weird, something related to FF3 (3.0 and 3.1 actually) has been listed in Update Manager for a while and it's always been unchecked for some reason; in fact, every time I've run Update Manager for at least a couple months, I've gotten a "Not all updates can be installed" error message, and I've only been able to run "partial upgrades".  No idea what impact that has had, but I'm going to post another thread about this update manager thing, just to see if there's anything else wrong as well before I uninstall and reinstall FF.

thank you for the suggestions, and for the instructions on uninstalling/reinstalling FF while keeping my bookmarks.  I'll check back in this thread after getting anything (or not) out of the other thread about my update manager and uninstalling/reinstalling FF (depending on what I end up doing).  until then...

---

### Post by detroit/zero on 2008-11-16
> **alisonjo2786 said:**
>   You know what is weird, something related to FF3 (3.0 and 3.1 actually) has been listed in Update Manager for a while and it's always been unchecked for some reason; in fact, every time I've run Update Manager for at least a couple months, I've gotten a "Not all updates can be installed" error message, and I've only been able to run "partial upgrades". 
You might want to try switching to a closer mirror for your downloads.

Open up System> Administration> Software Sources. Underneath all your checked sources, there's a drop-down menu named "*Download From*:". Drop it down and select "Other". A new window will pop up showing all the mirrors around the world. In the top right corner is a box named "Select Best Server". First, make sure your email program and torrent program and anything else that hogs bandwidth isn't running, and then click that box. It'll ping all the mirrors and stop at the best/closest one, and give you that as your selection.

---

### Post by CatKiller on 2008-11-16
If you rename your ~/.mozilla folder to something else (when Firefox isn't running), you'll get a fresh Firefox profile (when you restart Firefox). You can copy your bookmarks file from the old profile to the new one. Use the new profile for a while to see if the problem is just some configuration quirk or whether it is something more fundamental.

---

### Post by mgol on 2008-11-16
Maybe it isn't the best place to do that, but...
1) Fx3 uses LESS resources than Fx2. Less a lot, at least for me. Moreover, this is Fx2 which is slow and resource-demanding
2) I haven't seen any problems with Flash and Java
3) It has a lot of useful features, and one of the most useful is the Awesomebar. I cannot live without it now
4) Fx 3.1 is about to be released within a month. It is how should Fx 3.0 look like, but developers didn't manage to do everything on time. You can download a new version and try it

Why do I say it? I know there are people that prefer Fx2 to Fx3. But: I consider Fx3 A LOT better than Fx2, and a lot people does the same. So don't post things like "Fx3 is a crap", since there are a lot of people than don't agree with You; besides, You're not helping this way.

EOT.

And I agree with CatKiller, in most cases just renaming .mozilla folder works.

---

### Post by detroit/zero on 2008-11-16
> **mgol said:**
> Maybe it isn't the best place to do that, but...
1) Fx3 uses LESS resources than Fx2. Less a lot, **at least for me.** Moreover, this is Fx2 which is slow and resource-demandingWell, that's you. I observe just the opposite on my system.> **mgol said:**
> 2) I haven't seen any problems with Flash and JavaYou don't, I do. Some other people don't, some other people do. What's your point?> **mgol said:**
>  3) It has a lot of useful features, and one of the most useful is the Awesomebar. I cannot live without it nowGood for you. Oh, by the way - yawn.> **mgol said:**
>  4) Fx 3.1 is about to be released within a month. It is how should Fx 3.0 look like, but developers didn't manage to do everything on time. You can download a new version and try itI hope you're right and it's an improvement over the current release. 3.03 works; I use it. I think the main problem I have with it is the lack of theming and extension options - everything seems to be stuck in the FF2 phase.

[[IMG]http://img379.imageshack.us/img379/5096/screenshotaquatintblackdl7.png[/IMG]]("http://img379.imageshack.us/my.php?image=screenshotaquatintblackdl7.png")> **mgol said:**
>  Why do I say it? I know there are people that prefer Fx2 to Fx3. But: I consider Fx3 A LOT better than Fx2, and a lot people does the same. So don't post things like "Fx3 is a crap", since there are a lot of people than don't agree with You; besides, You're not helping this way.Some people don't, some people do. You don't, but I do. Again - what's your point? Opinions are like buttholes - everybody has one. Who are you to deride me for having mine?> **mgol said:**
>  EOT.

And I agree with CatKiller, in most cases just renaming .mozilla folder works.Sometimes yes, sometimes no. Where were all you guys with your advice when OP was bumping his second thread on the topic for two days? I figured he might just as well skip a step and go for what will most likely work, rather than the minimal-effort, probably-might-sorta-kinda-work (we hope) option.

---

### Post by CatKiller on 2008-11-16
> **detroit/zero said:**
> Where were all you guys with your advice when OP was bumping his second thread on the topic for two days?

Playing a gig and engineering a gig, respectively. What's your point? Let's just keep it civil, shall we, and concentrate on helping people the best we can?

---

### Post by detroit/zero on 2008-11-16
> **CatKiller said:**
> Playing a gig and engineering a gig, respectively. What's your point? The point is that the guy had been bumping a thread for a couple days and hadn't gotten any advice, so I gave him a solution that I can 99% guarantee will work.

Duh.

---

### Post by CatKiller on 2008-11-16
> **detroit/zero said:**
> The point is that the guy had been bumping a thread for a couple days and hadn't gotten any advice, so I gave him a solution that I can 99% guarantee will work.

Duh.

I'm certain that you read my suggestion to be civil.

It is generally frowned upon to create multiple threads on the same topic, and bumping a thread too frequently is just rude.

We are all volunteers here. No one is asking you what was so important that you couldn't help this particular poster at any point in the last few days. Why do you feel the need to criticise others?

A debate on the relative merits of Firefox 3 to Firefox 2 is not really relevant in this thread. If the two of you want to discuss that, then there are many other threads that you can participate in.

Re-installing the firefox package won't necessarily achieve anything, since the configuration is in ~/.mozilla, and isn't touched by that process. You suggested deleting that folder, I suggested just calling it something else. Both methods achieve the same result - getting a fresh profile. There's no source of conflict here. The only difference is that if the problem persists, because it's caused by something completely different, perhaps, the old profile is easy to restore if the folder is still there.

Please stay on-topic.

---

### Post by mgol on 2008-11-16
> **detroit/zero said:**
> Opinions are like buttholes - everybody has one. Who are you to deride me for having mine?

I didn't intend to deride You. I just wanted to say that some people prefer Fx3 to Fx2, others Fx2 to Fx3. And just saying that Fx3 is a crap and this is a source of all the problems wasn't were appropriate, IMHO. But ok, maybe I overdid with that all; I didn't want to offend anybody - If I did, I'm sorry for that.

I don't consider bumping to be nice. Many people have problems and they just wait until there is sb to help. Bumping is like saying 'Hurry up, how long do I have to wait?!?', and - IMHO - it offends all those people that tries to help others every day.

---

### Post by alisonjo2786 on 2008-11-16
Wow, before I was checking my thread like every 1-3 hours, and now, the first time I don't check my thread for like a day it gets exciting, haha.  I guess it's true what they say about how "a watched pot never boils" :)

First of all, thank you, everyone, for the advice, suggestions, input, etc.  I'm sorry that things got negative, I hope I didn't say anything provocative.  I am new at posting threads of my own and I want to do things right, so I've taken note of everything everyone said and will keep it in mind in the future.

As far as the bumping and multiple threads go, I do apologize if I did anything rude.  I read and reread the Forums Code of Conduct because I didn't want to do anything annoying or wrong, and I was very hesitant to bump or re-post, but someone who has done more posting than I told me it's ok to bump or re-post as long as you aren't doing it constantly.  I don't think I did it excessively, and I know I tried to do it sensibly, but I apologize if my behavior was in any way inappropriate.  (And if you have any suggestions/guidelines about this to offer, I'm all ears/eyes.)

**Back to the main topic:** A friend of mine happened to make the same suggestion as CatKiller, and he indicated that even if I uninstall/reinstall FF, I wouldn't be starting fresh as far as my User Profile goes, and he said he thought it sounded like I had User Profile issues.  So, I think I will try that first.  I also want to try what detroit/zero suggested about my mirrors.  I will post back here soon when I have done this.

Thank you again for all the input, and sorry I was AWOL for a few hours!

---

### Post by alisonjo2786 on 2008-11-17
So, I re-named the directory, started over, imported my old bookmarks, re-installed my favorite add-ons, and so far, so good :)  When I closed and re-started Firefox, it opened maximized like normal, and I can add Bookmarks (and "All Tabs") I can Organize Bookmarks, and everything.  The only thing left to try out is Update Manager, but I have a different thread going for that.

Thank you, everyone, for all your suggestions and input.  I still may try the "Software Sources" mirrors thing, especially if I still can't install all updates and so on.

SOLVED :)  (for now...)

---

### Post by CatKiller on 2008-11-17
Glad to hear it.

You can mark the thread as Solved with the Thread Tools at the top of the page.

---

### Post by alisonjo2786 on 2008-11-17
Oh crap, sorry.  I meant to and forgot.  Doing now!

---

