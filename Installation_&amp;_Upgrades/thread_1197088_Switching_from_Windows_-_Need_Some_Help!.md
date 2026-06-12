---
title: "Switching from Windows - Need Some Help!"
date: 2009-06-25
forum: Installation &amp; Upgrades
---

### Post by TheBurningCrown on 2009-06-25
So, the long/sad story:

Earlier this year my laptop (Dell Inspiron 6000)'s hard drive died, along with my copy of Windows XP, since Dell doesn't provide you with your own copy, only a "recovery disk."  I could go out and buy another copy, but I don't really want to.  I thought this would be the perfect opportunity to install Ubuntu and switch over to linux!

Using my trusty Intrepid Ibex disk which I had received a few months back, I happily popped it into my laptop's dying disk drive, and a few moments later it was installed!  The only issue was, my GPU (ATI Mobile Radeon X300) wasn't really playing well with the software.  The restricted drivers refused to install, and so I figured I might as well try to get them through the update manager.  Three hundred some updates later, I was up to date!  The GPU drivers still weren't installed and there were some problems, but I figured while I was at it I might as well upgrade to the most recent release (9.xx)!

Big mistake.

I booted to a garbled black screen.  After some brief fiddling with the recovery screen, I reformatted and reinstalled.  I reinstalled all updates from the update manager, and DIDN'T choose to upgrade to the most recent release.  Through this process, I got the restricted drivers installed and enabled.

My issue:  All off the fonts look wrong.  They're either not spaced properly (letters too close together) or too wide.  Is this an issue with my GPU, a setting I need to adjust, or what?

I'm relatively computer savvy but a linux virgin, so I'd appreciate any advice you gurus have to give!

I'll be waiting :popcorn: :D.

---

### Post by izizzle on 2009-06-25
Maybe there is something wrong with your DPI setting?

Upgrades can break these types of things. I would suggest downloading and installing 9.04. Clean and fresh.

---

### Post by wpshooter on 2009-06-25
What do you mean when you say "my hard drive died" ?

If there is something wrong with the hard drive, then it/that should be fixed or replaced first before you attempt to install any other O/S and anything else !!!

---

### Post by The-Don on 2009-06-25
I would recommend ignoring 8.10 and just download 9.04. Those 300 updates were between 8.10 and 9.04, so skip all that and download 9.04.

I did just over a week ago and have 9.04 on my laptop (Nvidia) and desktop (ATi). I would NOT recommend those damn closed-source proprietary drivers...I made the mistake on my desktop to 'Activate' it - and boom! No matter how many (uninstalls / xorg.conf rewrites / dkpg configure) no-one could fix it. Luckily I booted with Live CD, backed up files and reinstalled 9.04. No more propretary drivers on my system.

---

### Post by TheBurningCrown on 2009-06-25
Thanks for the comments!

> **izizzle said:**
> Maybe there is something wrong with your DPI setting?

Upgrades can break these types of things. I would suggest downloading and installing 9.04. Clean and fresh.

How would I go about adjusting the DPI settings in Ubuntu?

> **wpshooter said:**
> What do you mean when you say "my hard drive died" ?

If there is something wrong with the hard drive, then it/that should be fixed or replaced first before you attempt to install any other O/S and anything else !!!Booted one day to a repeated blue screen, after installing Intrepid Ibex it booted again to an "OS Missing" screen, ran some tests on the hard drive and it revealed many bad sectors.

I forgot to mention in the first post (I guess I took it for granted) but yeah, I replaced the hard drive.  And now with a blank one, I don't have a copy of Windows.  Which is what put me in this position to try out Ubuntu with a clean slate! :D

> **The-Don said:**
> I would recommend ignoring 8.10 and just download 9.04. Those 300 updates were between 8.10 and 9.04, so skip all that and download 9.04.

I did just over a week ago and have 9.04 on my laptop (Nvidia) and desktop (ATi). I would NOT recommend those damn closed-source proprietary drivers...I made the mistake on my desktop to 'Activate' it - and boom! No matter how many (uninstalls / xorg.conf rewrites / dkpg configure) no-one could fix it. Luckily I booted with Live CD, backed up files and reinstalled 9.04. No more propretary drivers on my system.Well as I mentioned in my first post, I tried 9.04.  It resulted in a garbled black screen and I had to reinstall to get the computer operating again.  So if I could install 9.04 and avoid that, I would gladly try it.

---

### Post by TheBurningCrown on 2009-06-27
Anyone?

---

### Post by TheBurningCrown on 2009-06-28
Could really use some help on this :(

---

### Post by buzzmandt on 2009-06-28
you say the fonts are bad?  have you installed mscorefonts?  search in synaptic.

---

### Post by presence1960 on 2009-06-28
I would suggest doing a clean install of 9.04. the reason why is if you take the time to go back in this section of our forum you will find many threads dealing with the upgrade process to jaunty leaving a non-working 9.04. For whatever reason there seems to be a lot of problems with the upgrade process to Jaunty. I would steer clear and do a clean install.

---

### Post by Mark Phelps on 2009-06-28
You're not going to get restricted drivers for a Radeon x300 running Ubuntu 9.04; you'll have to make due with the open source drivers.  If you want accelerated drivers, you have to install nothing newer than Ubuntu 8.10.

---

### Post by TheBurningCrown on 2009-06-28
Yes, I *think* I installed MS Core Fonts.  I was following a "new user" guide (X amount of things you should do when you first get Ubuntu sort-of-a-thing), so I have no idea whether I did it properly or not.

So as it is I have one user telling me to upgrade to 9.04 via a clean install, and one user telling me I need to stay with my current version if I want the graphics card to work properly.

Which, judging from the text, isn't.

Couple days to get this right, so hopefully I can get Ubuntu running (third time's the charm...).  If this fails I guess linux isn't as "mass market ready" as everyone was proclaiming it to be...

---

### Post by presence1960 on 2009-06-29
> **TheBurningCrown said:**
> Yes, I *think* I installed MS Core Fonts.  I was following a "new user" guide (X amount of things you should do when you first get Ubuntu sort-of-a-thing), so I have no idea whether I did it properly or not.

So as it is I have one user telling me to upgrade to 9.04 via a clean install, and one user telling me I need to stay with my current version if I want the graphics card to work properly.

Which, judging from the text, isn't.

Couple days to get this right, so hopefully I can get Ubuntu running (third time's the charm...).  If this fails I guess linux isn't as "mass market ready" as everyone was proclaiming it to be...

Your ATI is not going to get proprietary drivers because the manufacturer stopped support for that, they just dropped it. if you are going to survive with open source drivers for your vid card then I suggest a clean install vs. an upgrade. There have been mega problems with the upgrade process to Jaunty.

Don't make the statement that everyone has proclaimed Linux "mass market ready". I and more than a good number of members in here could not care any less if anyone else decides to use Linux. We use it because we want to use it. We will gladly help others who want to try it, but really if no one else decides to use it that is OK. There are some zealots who feel the need to shout from the rooftops about Linux. Experience shows most of those have an axe to grind or feel the need to think they are superior to windows users. Maybe you listened to that group, I don't know.

The bottom line is if you aren't willing to invest the time, effort & work required to learn Linux then it is just a waste of your time. There is a steep learning curve coming from windows. Think back and try to remember how it was when you first started using windows. You didn't know jack, did you? Well unfortunately all of us who pick up Linux to give it a real shot are back to that point again, regardless of how much we know about windows. Good luck and hopefully you will stick it out. But if not use whatever OS makes you happy.

BTW open a terminal and run > sudo apt-get install ttf-mscorefonts-installer to install ms core fonts

---

### Post by TheBurningCrown on 2009-06-29
Thanks for the to-the-point post.

I've just been hearing a lot of chatter about linux finally "breaking the barrier" and what not, penetrating the general computer-illiterate community.

I would be happy to invest the time, effort, and everything else needed to get a version of linux running well on my PC.  But I sincerely doubt I can do all of it by myself.  But if I can't fix my issues (or get any help in doing so), then I might as well go back to Windows.  It may not function as well to a well configured linux distribution, but at least I know what I'm doing, and out of the box at least I know it works (not well, but it does).

I don't remember the first time I DIDN'T know how to use Windows (to be perfectly honest).  But right now, Ubuntu feels faster, more responsive, and (as a major plus) is free.

After doing some scrounging on the forum, I've gone into the Appearance preferences and adjusted the DPI to 80 under the Fonts section.  I also changed the font appearance to monochrome and most of the default fonts to Times New Roman.  In addition, I followed some links and completed the steps on this page: [http://www.sharpfonts.com/](http://www.sharpfonts.com/).  Now the font distances are corrected, fonts are much smaller, and they're all much sharper.

If someone could explain to me what I did on the "sharpfonts" page I would appreciate it.  I'm the kind of guy that wants to know what's I'm doing, and not just the end result.

Step 1: Download packages (got that).
Step 2: Create directory (got that, what's the -p designation?).
Step 3: Extract to directory (got that, what's the -d designation?)
Step 4: Extract configuration files to directory (little confused, what's "xvjpf", what's the -C designation, and what did this do exactly (besides make it all work)?)

Also (sorry to belabor the newbish point) my touchpad seems overly sensitive to touch clicks, while touch-scrolling seems jerky - any way to fix that?

Sorry for the long post :(

---

### Post by presence1960 on 2009-06-29
I hardly ever use windows anymore, maybe once a month. That is because I have to for work. They made it clear to me no Open office- something about formatting not 100% between the two (OO & MS Office). I used to need it for Adobe Acrobat professional, but I have learned how to create pdf from Scribus. Maybe if I can find another job I can ditch windows entirely...

But I dual boot and maybe you can do the same. Download the Windows 7 RC and register to get a product key. You can use it until 6/10/2010. Not a bad deal to hold you over until you can get comfortable with Linux.

If you decide to go that route, you do not have to install windows first! You can easily install windows after Linux. If you need help come back here.

---

