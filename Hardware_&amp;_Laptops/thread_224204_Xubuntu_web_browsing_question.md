---
title: "Xubuntu web browsing question"
date: 2006-07-27
forum: Hardware &amp; Laptops
---

### Post by Metacarpal on 2006-07-27
Hi guys,

After running Ubuntu on my kinda-old laptop for a few months, I decided to give Xubuntu a try to see if it would make an appreciable difference.  And I gotta say, I notice a difference in the response times.

Just one problem - for some reason, my web browser is running slower now.  It opens quickly, but then the page loads are taking longer, particularly in the stage where it first locates and contacts a site and waits for a reply.  Has anyone else run into this, and is there an easy fix?

I'm running Xubuntu 6.06 on a Toshiba Tecra 8200 (1000MHz processor, 256MB RAM) over wireless internet (CompUSA-brand 802.11G PC-card, rebranded RealTek chipset that Just Works).

---

### Post by ekeefe41 on 2006-07-27
I was thinking about switching to Xubuntu on my laptop as well. Mine is almose the same spec's as yours. Is it worth it?

---

### Post by Metacarpal on 2006-07-27
> **ekeefe41 said:**
> I was thinking about switching to Xubuntu on my laptop as well. Mine is almose the same spec's as yours. Is it worth it?

I'm thinking about things, and I'm wondering if maybe the fact that I'm running a highly tricked-out copy of Swiftfox instead of the regular Firefox might have something to do with my issue. :rolleyes:  lol

I'm finding installing new themes to be a pain, but if you're not worried about that, the performance difference is definitely noticeable.  If you're already running Ubuntu, just open a terminal (Applications > Accessories > Terminal) and enter:
```
sudo aptitude install xubuntu-desktop
```
and you can switch between XFCE and Gnome.  If you end up not liking XFCE, getting rid of it is as easy as 
```
sudo aptitude remove xubuntu-desktop
```

(When it prompts for a password, give it the same password you use when logging on.)

It's at least worth trying, IMO

---

### Post by ekeefe41 on 2006-07-27
Thank you so much, i just finished copying all my music and photo's last night and was not looking forward to a new install. 

You are the man. :)

---

### Post by jISh on 2006-07-27
I use Xubuntu on both a 667 Mhz Dell laptop with 128MB RAM and a 667 MHZ Celeron desktop with 192MB RAM, and Xubuntu runs like a dream on both machines.

---

### Post by ekeefe41 on 2006-07-28
If i fall in love with xubuntu can i uninstal Gnome like so

*sudo aptitude install gnome-desktop*

---

### Post by Metacarpal on 2006-07-28
> **ekeefe41 said:**
> If i fall in love with xubuntu can i uninstal Gnome like so

*sudo aptitude install gnome-desktop*

That only really works if you installed using aptitude.  Here's a page showing the code to paste into a Terminal to remove Gnome if you decide to go [pure Xubuntu]("http://www.psychocats.net/ubuntu/purexfce.php")

Yeah, you'll seriously have to copy and paste that whole thing - but it beats typing it out!

(Note: in Terminal, paste is Shift+Insert, not Ctrl+v)

---

### Post by Metacarpal on 2006-07-28
> **Metacarpal said:**
> Hi guys,

After running Ubuntu on my kinda-old laptop for a few months, I decided to give Xubuntu a try to see if it would make an appreciable difference.  And I gotta say, I notice a difference in the response times.

Just one problem - for some reason, my web browser is running slower now.  It opens quickly, but then the page loads are taking longer, particularly in the stage where it first locates and contacts a site and waits for a reply.  Has anyone else run into this, and is there an easy fix?

I'm running Xubuntu 6.06 on a Toshiba Tecra 8200 (1000MHz processor, 256MB RAM) over wireless internet (CompUSA-brand 802.11G PC-card, rebranded RealTek chipset that Just Works).


As much as I'm enjoying the Xubuntu-switch discussion, anybody want to take a stab at my actual question? :rolleyes:

---

### Post by ekeefe41 on 2006-07-28
Sorry for the thread hijack :-& 

Since my switch i have noticed no loss in speed as far as web surfing goes. The application launch is slightly faster. 
I do have 2 questions

Did you change any networking settings? Duplexing always slows down the web if messed with

Also have you changed any Firefox settings?

---

### Post by Metacarpal on 2006-07-28
Yeah, I'd followed instructions in another thread to speed up Firefox.  It worked well enough in Gnome...  But since you mentioned it, I completely uninstalled and reinstalled, and it seems fine now.

---

### Post by ekeefe41 on 2006-07-28
Hi-jack back on.. sry

You seem to know your stuff.. so here is an other question. I installed VLC for DVD playback on my laptop. I was wondering if there was a way to auto play the a DVD as soon as it is placed in the drive. 

This was easy enough to do in ubunto *(already removed gnome)*

**System tab ---> Preferences ---> Removable Drives and Media **

I can't seem to find any settings for removable media in xubuntu..

Sorry for the hi-jack again, but you seem to be the only person attempting to answer my questions :)

[http://ubuntuforums.org/showthread.php?p=1311532#post1311532](http://ubuntuforums.org/showthread.php?p=1311532#post1311532)
[http://forum.videolan.org/viewtopic.php?p=75917#75917](http://forum.videolan.org/viewtopic.php?p=75917#75917)

---

### Post by b_martinez on 2006-07-28
I know you stated that you are running a 'tricked out Swiftfox', yet have you considered a lighter browser? How about 'Epiphany'? I may be totally off the wall on this, but if it installs, it may be faster than what you are using. Of course, since I am just starting to learn (X)- (K)- Ubuntu, I don't know if it is possible to install 'Epiphany'.
Bill
p.s. feel free to kick me back into the beginner forums,as I was just browsing when I hit this topic.
B

---

### Post by K.Mandla on 2006-07-29
The initial lag you mention might be Firefox checking ipv6. [Disabling it ]("http://www.ubuntuforums.org/showthread.php?t=202838")might help a little; I do this on all my Xubuntu machines and it's a night-and-day difference.

I was going to suggest Swiftfox, but I see you've already found that. ... :)

---

