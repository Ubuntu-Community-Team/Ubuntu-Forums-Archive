---
title: "RE-install 7.04 or install 8.04"
date: 2009-01-17
forum: Installation &amp; Upgrades
---

### Post by nichos on 2009-01-17
I was dual booting XP & Ubuntu.

Had to reinstall XP, which evidently lost me the boot.ini

Can I create that Boot.ini in windows & access ubuntu again?
Please do not waste your time giving me linux double -dutch lingo as they mean nothing to me.

I installed 7.4 from a magazine CD a coule of yrs ago, could not progress with it, but use it for the internet only.

If I cannot recover dual boot through windows, how then do I reinstall it?.

I downloaded 8.04 ISO & burned it in CD, but when I boot in CD it starts, shows me the 7 partitions I have, but when I select the one ubuntu 7 is in, it says it has no boot facilities in it.

Format is grayed, chose delete but that won't delete.

Anybody knows how to get on, BUT please no Linux jargon at all.

thanx      nick

---

### Post by Mark Phelps on 2009-01-19
OK, so it's been two days now and no one has volunteered to help you ... is it any surprise with your attitude!!!

There is literally NO WAY to fix your problem without someone providing you a minimum of "linux jargon".  You will, at very least, have to learn how to reinstall GRUB -- because your loading Windows overwrote it.  You will have to boot using a LiveCD, open a terminal, and run a few commands to restore GRUB.  

IF you're not willing to do even that, you've made the wrong choice in computing alternatives to Windows.

Best for you to stay with Windows -- where you won't be bothered with having to learn any "jargon".

---

### Post by nichos on 2009-01-22
You are very right, I just can't understand it at all. Tried for 3 yrs.

nick

---

### Post by cariboo on 2009-01-22
You can fix the problem without reinstalling, but you aren't even using the correct computer jargon. Boot.ini is the boot menu for windows, it has nothing to do with grub. Follow the steps [here]("http://ubuntuforums.org/showthread.php?t=224351"). Ignore this part:

> 
Code:

root (hd?,?)



as it doesn't do anything.

Jim

---

### Post by Mark Phelps on 2009-01-22
nichos:

Sorry if I came across a bit harsh, but here, you have to be willing to learn HOW to fix your problems, so telling folks that you don't want them to tell you anything is very discouraging.

Jim provided you an excellent link -- but as you will see, you will have to learn some "Linux jargon" to fix your problem.

Sorry, but that's how it is here.

---

