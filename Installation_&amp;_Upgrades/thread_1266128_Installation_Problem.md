---
title: "Installation Problem"
date: 2009-09-14
forum: Installation &amp; Upgrades
---

### Post by LinuxRiot on 2009-09-14
hey guys,

im new to Linux and just wanna use an alternative to windows.
However , im not that good computers gernerally which means it would be nice to explain the solution to my problem in a simple way :)

So, what happened :

I just downloaded wubi vers. 9.04, followd the installion instructions and got finally the finished notice. Following that i rebootet my PC , entered the "Ubuntu" name right below Windows XP but then a notice appeared : 

Endless fallback loop detected(entry=347798780)! Press any key...

after typing "any key" ;) another screen appeared with a highlighted line where at the top was written "GRUB4DOS 0.4.4 2009-04-21, Memory: 69k / 524545M, MenuEnd; ...

well, i was able to klick anything but nothing happens, which seems broken...

Right now im using a AMD Athlon Dual Core 7750; Windwos Home; 3,5GB Ram.

Thanks for any help :)

:KS

---

### Post by LinuxRiot on 2009-09-14
no one any idea?

---

### Post by LinuxRiot on 2009-09-15
*bump*

---

### Post by stlsaint on 2009-09-15
Perhaps a faulty install...please boot into windows and remove ubuntu via add/remove programs.
Then try install again.

---

### Post by LinuxRiot on 2009-09-15
already did a couple of times. Didnt help.. :(

---

### Post by LinuxRiot on 2009-09-16
90 views and no real help ... thats at least one reason why no one uses Linux.

---

### Post by tomBorgia on 2009-09-16
> **LinuxRiot said:**
> 90 views and no real help ... thats at least one reason why no one uses Linux.

I'll bite ;-)

I suspect most people here will use the full install cd and not wubi - maybe no-one has come across your problem before.

If wubi's not working at all I'd suggest you try the full install from the liveCD - You can boot the LiveCD first and see if you like it... 

(If you are going to install make sure you have a backup before resizing your disk partitions, and run a windows defrag first - Ideally install on a second hard disk drive).

---

### Post by LinuxRiot on 2009-09-16
Thanks for answering :)
However, i already installed Ubuntu with a live CD on my second PC but , and thats why i wanna use wubi, on my "main pc" id also like still having windows.
Which means, even if ubuntu works with a live CD im not able to use it as it would fully overwrite Windows -right?

---

### Post by TheStroj on 2009-09-16
If you want both Windows and Ubuntu installed, download Ubuntu from [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download), then burn it to a CD and simply install it. 
If you already have windows installed, it will recognize it during Ubuntu installation and will ask you if you want to create Dual Boot. You choose that option and select how much space should Ubuntu use. That's it, and nothing can go wrong.

---

### Post by tomBorgia on 2009-09-16
> **TheStroj said:**
> If you want both Windows and Ubuntu installed, download Ubuntu from [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download), then burn it to a CD and simply install it. 
If you already have windows installed, it will recognize it during Ubuntu installation and will ask you if you want to create Dual Boot. You choose that option and select how much space should Ubuntu use. That's it, and nothing can go wrong.

What he said...

Except the nothing can go wrong bit... tempting fate methinks!

---

### Post by presence1960 on 2009-09-16
> **LinuxRiot said:**
> 90 views and no real help ... thats at least one reason why no one uses Linux.
with that attitude it is surprising anyone even posts. 

We are not paid support on here. We all do it basically out of the kindness within us. You have to learn to be patient because someone who knows the answer to your problem has to log in and notice your thread.

If you want on demand help and the ability to trash those helping you then I kindly suggest you go back to windows.

Now if you want help with linux you need to understand what i wrote above. We are not being compensated for our help and as such will not accept attitudes such as yours. Again please be patient. it may take some time to sort out your problem.

---

### Post by bobbob1016 on 2009-09-16
-Remove Wubi the way you did before, through Add/Remove.

-Take the LiveCD, put it in your computer, and reboot.

-MAKE SURE Windows shuts down normally, not holding the power button or anything.

-Select "Install or Try Out"

-Make sure everything works (Graphics drivers might not in the LiveCD)

-Double-click Install on the desktop

-It can "safely" move your Windows partition aside a bit to install Ubuntu, but if you could put a new HDD in the PC, it won't even have to touch your Windows install which is safe

---

### Post by presence1960 on 2009-09-16
> **TheStroj said:**
>  That's it, and nothing can go wrong.

Don't believe that for a minute! When ever installing an OS or partitioning there is always an outside chance someting can go wrong. That is why there are good sense things to do before attempting such operations:

1. back up all data you don't want to lose.
2. defrag windows at least once or twice. Turn off system restore in    windows until after the installation is successfully completed.
3. If using Vista do not use the Ubuntu live CD or gparted or any third party partioning utility to resize Vista. use Vista's disk management utility to shrink Vista's partition to create room for Ubuntu. Then do the install.

There is an unresolved bug that renders vista unbootable if it is resized with anything other than it's own disk management utility. Sometimes it will work and others it won't. Do you want to chance it?

here is a link to that bug report which is still not solved:
[http://bugzilla.gnome.org/show_bug.cgi?id=379482](http://bugzilla.gnome.org/show_bug.cgi?id=379482)

---

### Post by LinuxRiot on 2009-09-16
First : Thanks to all of you :D It helped a lot and im going to try out your ideas right now.

"We are not paid support on here. We all do it basically out of the kindness within us."

Well, thats right but if you didnt want to help others, you shouldnt have registered on a ubuntu forum that helps others with problems, right ? ;)

" If you want on demand help and the ability to trash those helping you then I kindly suggest you go back to windows."

I didnt ever say that ill trash your "helpings", furthermore i thanked you for every tip and help i got.
But, whatever, there were many others who were more nice helping me :D

---

### Post by LinuxRiot on 2009-09-16
ok, new problem.
I put in live CD, klicked on "try and install" but , whyle trying to get on desktop a message appeared which says that there were troubles with my graphiccard. I declined a diagnosis but after that, it hang up. nothing happened. 
My graphiccard is a GeForce 9500 GT ..

---

### Post by bigboy_pdb on 2009-09-16
> **LinuxRiot said:**
> 
"We are not paid support on here. We all do it basically out of the kindness within us."

Well, thats right but if you didnt want to help others, you shouldnt have registered on a ubuntu forum that helps others with problems, right ? ;)


I was intending on helping you because I figured that your initial comments were made out of frustration, but after reading all of your abrasive responses I don't intend on doing so.

I hope others follow this example as well.

Also, saying "thank you" doesn't mean anything if you insult people before, after, and in between saying it.

---

### Post by LinuxRiot on 2009-09-16
"Also, saying "thank you" doesn't mean anything if you insult people before, after, and in between saying it."

Could you please quote, where i insulte others?

---

### Post by juliusk on 2009-09-16
I am new to ubuntu, and have not yet installed.  Does anyone know whether under 9.04 or 9.10 i can continue to use or find acceptable replacements for the following programs:  Microsoft money; taxact; swordsearcher; bible explorer4; skype; microsoft encarta; encyclopedia britannica 2008 ultimate; winzip; microsoft streets?

---

### Post by presence1960 on 2009-09-16
> **LinuxRiot said:**
> 

Well, thats right but if you didnt want to help others, you shouldnt have registered on a ubuntu forum that helps others with problems, right ? ;)

" If you want on demand help and the ability to trash those helping you then I kindly suggest you go back to windows."

I didnt ever say that ill trash your "helpings", furthermore i thanked you for every tip and help i got.
But, whatever, there were many others who were more nice helping me :D

you made the comment when you didn't receive help as fast as you thought it should come **> 90 views and no real help ... thats at least one reason why no one uses Linux.  Am I correct?**

I stand by my words. You must be patient, we are not paid support!

You really don't know if I am helpful or not since you just joined no more than 16 days ago. Maybe you should go to my profile and view my more than 2,200 (Edit: oops, now more than 2,300) posts to see just how helpful I may or may not be.

---

### Post by LinuxRiot on 2009-09-16
"[B]                              90 views and no real help ... thats at least one reason why no one uses Linux."
[/B]This was out of frustraion, right.But im missing the insulting.

"Well, thats right but if you didnt want to help others, you shouldnt have registered on a ubuntu forum that helps others with problems, right ? :wink:"

This aint an insult, its a clarificatio.

"f I am helpful or not"

I dont know if youre helpful or not, but your post wasnt at least. You werent even friendly and thats why i respond the same way you did.

Edit : and 2300 posts doenst mean youre helpful, its the contant that makes posts more or less helpfull : in the case of this thread - you werent.

---

### Post by presence1960 on 2009-09-16
I never said insulting. show me where I wrote that.

You made the statement whether out of frustration or something else. I responded to that statement you made. I think your feelings are hurt. Suck it up and move on friend. As the old saying goes "Don't ask the question if you don't want to hear the answer".

See how quick you are to absolve yourself of responsibility for what you said, extend the same to me.

if you never posted that would we even be having this discussion?

---

### Post by presence1960 on 2009-09-16
I had a big back & forth run in with mikewhatever (community member here). it went on for like 15 posts or so because i didn't like how mikewhatever was speaking to someone looking for help. The moderators removed all of our posts. After I calmed down I went to mikewhatever's profile and started reading  a bunch of his posts. I was surprised  (because I already had my mind made up based on 1 experience with mikewhatever) at just how helpful he is on this forum.

I learned that day don't judge someone by 1 post, sentence or word. I must take all into account before making an assessment.

I didn't judge you today, I said that attitude won't be helpful.

---

### Post by LinuxRiot on 2009-09-16
" Also, saying "thank you" doesn't mean anything if you insult people before, after, and in between saying it." But it wasnt you, my request was linked to the person who said it.

" I learned that day don't judge someone by 1 post, sentence or word. I must take all into account before making an assessment."

I didnt judghe anyone. I only asked a question, were more or less suprised or frustrated that no one respoded and thats it.

I dont understand this whole discussing anyway. So, it would still be nice if you got a hint for me

---

### Post by presence1960 on 2009-09-16
> **LinuxRiot said:**
> " Also, saying "thank you" doesn't mean anything if you insult people before, after, and in between saying it." But it wasnt you, my request was linked to the person who said it.

" I learned that day don't judge someone by 1 post, sentence or word. I must take all into account before making an assessment."

I didnt judghe anyone. I only asked a question, were more or less suprised or frustrated that no one respoded and thats it.

I dont understand this whole discussing anyway. So, it would still be nice if you got a hint for me

I would say it is best if we chalk this up as a misunderstanding. One thing is that in forums all we have to go by is the printed word. there are no body language or other signals. So in here more than anywhere else you are taken at your "word".

I stand by my posts in here. I think if you go through some of them you will have a different opinion of me. But that is neither here nor there. it does not matter what anyone thinks of me for I know the truth about myself and can look myself in the mirror in the morning.

We don't have to like everyone in here to get help. 

Enjoy Ubuntu!

---

