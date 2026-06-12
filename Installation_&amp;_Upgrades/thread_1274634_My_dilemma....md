---
title: "My dilemma..."
date: 2009-09-24
forum: Installation &amp; Upgrades
---

### Post by mesmith on 2009-09-24
The problem is this:  I'm using xubuntu 8.10, which I have tweaked pretty extensively over the past nine months.  It is very stable with no problems.  I love it.  I had problems with two applications, AbiWord and Gnumeric.  AbiWord had a broken help system that I reported, and it was accepted, as a bug.  I was informed the fix would be made in a forthcoming xubuntu version, but that I could request a backport.  I did, but no response.  I finally figured out how to fix it myself with a work around.  Gnumeric help requests sent my second processor to 100% usage with a one to two minute delay before the help system appeared (then the processor idles back down).  Apparently this is a known bug for some configurations.

When I upgraded to 9.04 it was kind of an electronic train wreck.  Missing icons, my chosen display resolution (1280x960) had disappeared as an option, and the system would not hold a chosen resolution between boots - always reverting to max.  Scratchy sound and jerky video (yep, I have an onboard intel video chip).  Plus, after the shutdown splash screen I got a screen and a half of error messages.  I'm sure some of these are corrected, maybe all, but I just don't have the time to deal with them all.  I thought of doing an upgrade to 9.04 when 9.10 is released, and then an immediate upgrade to 9.10 and seeing where I stand.

My other thought is to just hang in there until the next LTS system and then do a clean install and banging through all my mods again.  I could save off my /home and then put it back after the clean install, but maybe the .conf files would raise havoc.  I suppose I could just restore my personal data and go from there.

Okay, I need some advice from "old hands" about the pros and cons of my choices.  Any help?

---

### Post by earthpigg on 2009-09-24
> **mesmith said:**
> Okay, I need some advice from "old hands" about the pros and cons of my choices.  Any help?

if you really want to do the extensive modifications thing:

-stick to LTS releases. then you only need to redo everything every 3 years.

-make a plain text file and document what you do and how you do it.

-instead of upgrading, back up /home, do fresh installs and selectively restore dotfiles and folders.

-maybe devote your modding efforts to distro-neutral things? easiest example is your /home/username/.bashrc



edit: also, woot for petaluma. i lived down the road in the city of sonoma for several years, am in Marin now.

---

### Post by rreese6 on 2009-09-24
I have an old laptop, Toshiba Satellite 4100XDVD runing Xubuntu 8.04
the 8.10 was buggy as you noted.
9.04 was definitely out of the question.
My philosophy has always been, if it ain't broke, don't fix it.
I am happy leaving this system running the 8.04 LTS.
and it will stay this way for the next few years...of course this is only one of 4 computers I use..

---

### Post by mesmith on 2009-09-25
Thanks to both of you.  Will likely stay where I am til the next LTS product.

Also, earthpigg, followed your link to masonux.  I like it.  Any way to make the icons in the app launch area (lower left) larger?  I'm old and like a bigger panel and icon size.  Panel's easy to enlarge, but not the icons so far.  Nice, clean distribution.

---

### Post by earthpigg on 2009-09-25
> **mesmith said:**
> 
Also, earthpigg, followed your link to masonux.  I like it.  Any way to make the icons in the app launch area (lower left) larger?  I'm old and like a bigger panel and icon size.  Panel's easy to enlarge, but not the icons so far.

thank you for the compliment :)

alas, there is no way that i am aware of to change the size of panel launcher icons with lxpanel.

you could install gnome-panel and use that, if you wanted. directions and caveats are at the website in the 'how do i' section.

---

