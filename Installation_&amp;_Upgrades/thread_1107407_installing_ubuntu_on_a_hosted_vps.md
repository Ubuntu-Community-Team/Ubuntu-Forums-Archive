---
title: "installing ubuntu on a hosted vps"
date: 2009-03-26
forum: Installation &amp; Upgrades
---

### Post by Rosey on 2009-03-26
I'm lost and confused :oops:

I have a VPS (hosted) that I've been running for almost 2 years.

It's currently running fedora core 4 and apparently I need to upgrade. They won't do it for me so here I am.

They told me to get debian but my brother said ubuntu was better.

I'm downloading ubuntu right now and trying to find out how I'm sposed to install it.

I'm sorry to be a total noob :(

Can someone point me in the right direction?

---

### Post by williane on 2009-03-26
I don't know who your VPS is with, but Slicehost has some really great articles for this:
[URL="http://articles.slicehost.com/ubuntu-hardy"]
http://articles.slicehost.com/ubuntu-hardy[/URL]

---

### Post by Rosey on 2009-03-26
Well the problem is that I'm finding a lot of articles on how to do it on your computer, dual booting etc, but not how to install it on an existing vps that has something other than ubuntu. Maybe I am not looking in the right spot but it's very frustrating.

---

### Post by williane on 2009-03-26
Who is your host? You should be able to chose your OS somewhere and have it installed fresh with SSH so you can log in remotely to start doing your thing.

---

### Post by Rohan Kapoor on 2009-03-26
Honestly just follow the guide linked above, and you can't really go wrong.

---

### Post by Rosey on 2009-03-26
My host is ipower and I must be missing it because I don't see where you can change the OS.

As for those articles, I looked and I don't know which one to follow.  I don't see which one applies to me at all.

---

### Post by williane on 2009-03-26
Well I don't have any experience with ipower. But when you log in to your control panel or w/e they call it you dont see any options for resetting or reinstalling the OS? I'd contact customer support and see about it. Also ask if they have any ipower specific guides. But other than that, those Slicehost guides are about as good as it gets for basic server setup guides. 

The link I gave was for ubuntu hardy. Thats probably what you want to use for your server. Its the current LTS (long term support). Just start with "[Ubuntu Hardy setup - page 1]("http://articles.slicehost.com/2008/4/25/ubuntu-hardy-setup-page-1")" (once you get a fresh ubuntu installed of course) and go from there. Browse around. Slicehost has a lot of good articles for getting started.

---

### Post by Rosey on 2009-03-26
See that's just it, how to I get ubuntu installed to begin with. 

I did contact them and they said if I wanted to upgrade, I had to do it myself. 

I want to upgrade because fedora core 4 (they say) doesn't support mysql 5 and the newer php 5.

---

### Post by williane on 2009-03-26
[http://www.ipower.com/popups/ip_pop_features.bml?type=virtuozzo](http://www.ipower.com/popups/ip_pop_features.bml?type=virtuozzo)

Looks like VZPP is what youre looking for:

> 
[LIST]
[*]**VPS Re-install**
Reinstall the VPS from scratch, either saving or  discarding existing files
[/LIST]


I can't really help you much more. And not to be rude ( just being truthful ), if you're having trouble just finding out how to reinstall, setting it up is gonna be even worse. Even with really good guides to go off of. Good luck though. Setting up a server can be really fun and rewarding (and also a big PITA :P ).

---

### Post by Rosey on 2009-03-26
VZPP is virtuozzo and I have that already.

Not to be rude but all the guide are when you are installing is on your own machine, not remotely on a vps.

I can follow directions. I set up the vps myself (it's been running almost 2 years). I've dual booted a computer before as well. I'm not stupid, I just need to be pointed in the right direction or find some documentation that pertains to my situation. That slicehost list is not what I need, I don't think. The first guides, like I said are when you already have it installed.

All i need to know is where to upload the files and what command to run. That's what I'm missing.

I'm not trying to be rude either but I don't think you guys understand what I'm trying to do or are unwilling to help.

I told you I was I was a noob. Noob doesn't mean stupid or doomed to failure.

---

### Post by williane on 2009-03-26
You should be able to reinstall somewhere in virtuozzo. Once you do get it installed then you should be able to SSH into the server and then use those guides from there, as though it was your own computer (which is basically is). Did you not use SSH to set it up before, or were you able to do it all through virtuozzo?

---

### Post by williane on 2009-03-26
Try these maybe:
[URL="http://www.webhosting.uk.com/virtuozzo-tutorials.php"]
http://www.webhosting.uk.com/virtuozzo-tutorials.php[/URL]

"Reinstall                                                       your VPS" about halfway down

---

