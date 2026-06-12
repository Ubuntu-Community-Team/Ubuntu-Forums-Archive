---
title: "Sabayon 3.26 Torrents"
date: 2007-01-07
forum: Gentoo and derivatives
---

### Post by RAV TUX on 2007-01-07
**Sabayon Linux x86 3.26 DVD**

[B][http://linuxtracker.org/torrents-details.php?id=3406](http://linuxtracker.org/torrents-details.php?id=3406)
[/B]


**Sabayon Linux x86-64 3.26 DVD**

[B][http://linuxtracker.org/torrents-details.php?id=3407](http://linuxtracker.org/torrents-details.php?id=3407)
[/B]

---

### Post by pay on 2007-01-07
Sabayon seems to get updated every two weeks or so and it seems abit much to download a dvd so often. The miniedition seems out of date.

---

### Post by Rodneyck on 2007-01-07
So, if you update the 3.2 mini CD with the 3.26 DVD, will that install all the other programs on the DVD or just the ones on your system?  I can not find a straight answer to this question on their forum.

If you do not use the DVD to update, how do you update to the latest?  Will emerge layman, etc do the trick?  How are you updating RAV?  

Sorry for all the questions, but this seems to be a topic that is not clear to a lot of people and every answer is vague at best. They devs really need to post something on their website, especially since they update about every week.

---

### Post by rsambuca on 2007-01-07
Whoa!  Very sloooooooooow torrents.  Unless they really pick up speed, I'll be installing in about 3 weeks:confused:

---

### Post by manmower on 2007-01-08
> **Rodneyck said:**
> So, if you update the 3.2 mini CD with the 3.26 DVD, will that install all the other programs on the DVD or just the ones on your system?  I can not find a straight answer to this question on their forum.

If you do not use the DVD to update, how do you update to the latest?  Will emerge layman, etc do the trick?  How are you updating RAV?  

Sorry for all the questions, but this seems to be a topic that is not clear to a lot of people and every answer is vague at best. They devs really need to post something on their website, especially since they update about every week.

What happens when you
```

emerge --sync
emerge --update
```
It seems weird to base a distro off of Gentoo only to remove one of its killer features, ie. fluent upgrading, so I think this should work.

Note: I've never tried Sabayon and it's been quite a while since I used Gentoo (about three years in fact) and I only played with it shortly. But I presume Gentoo docs will have the answers you're looking for.

---

### Post by RAV TUX on 2007-01-08
> **Rodneyck said:**
> So, if you update the 3.2 mini CD with the 3.26 DVD, will that install all the other programs on the DVD or just the ones on your system?  I can not find a straight answer to this question on their forum.

If you do not use the DVD to update, how do you update to the latest?  Will emerge layman, etc do the trick?  How are you updating RAV?  

Sorry for all the questions, but this seems to be a topic that is not clear to a lot of people and every answer is vague at best. They devs really need to post something on their website, especially since they update about every week.

I just did a fresh install of 3.25 DVD....

here is a [HOWTO: Use xdelta patches]("http://www.sabayonlinux.org/forum/viewtopic.php?t=917&start=0&postdays=0&postorder=asc&highlight=xdelta")

[http://www.sabayonlinux.org/forum/viewtopic.php?t=917&highlight=xdelta](http://www.sabayonlinux.org/forum/viewtopic.php?t=917&highlight=xdelta)

agian: simply go to irc.oftc.net #sabayon and ask...

---

### Post by RAV TUX on 2007-01-08
> **pay said:**
> Sabayon seems to get updated every two weeks or so and it seems abit much to download a dvd so often. The miniedition seems out of date.

as far as the update, don't be ridiculous....it is a patch update,...similar to the one KNOPPIX just released....

do I need to remind you about the ubuntu x scenario.....

If you need to submit a patch update...like KNOPPIX or Sabayon just did....even Ubuntu has had to issue patches....

this is only normal

the miniedition will be updated with 3.3 in a few months

---

### Post by RAV TUX on 2007-01-08
> **manmower said:**
> What happens when you
```

emerge --sync
emerge --update
```It seems weird to base a distro off of Gentoo only to remove one of its killer features, ie. fluent upgrading, so I think this should work.

Note: I've never tried Sabayon and it's been quite a while since I used Gentoo (about three years in fact) and I only played with it shortly. But I presume Gentoo docs will have the answers you're looking for.

Exactely Sabayon is Gentoo whatever works in Gentoo works in Sabayon...

Simple search the Gentoo docs...to find your answer.....don't fear the Google!

I will be the first to admit that if your expecting to have your hand held and be spoon fed then Sabayon and Gentoo are not for you....

If you can utilize a search engine like Google....read documentation and follow Howto's then this is the perfect OS for you

Also to expect Sabayon to repost and duplicate Gentoo documentation is ridiculous.....Sabayon is Gentoo.....Gentoo is the most documented distro on the planet......

search the Gentoo documentation, Wikis, handbook, even the #gentoo IRC chanel or forum for your answers...

I have learned more in the short time I have been using Sabayon then I have my whole time using Linux simply because they don't spoonfeed you the answers

They do expect you to think, to reason, and to use a simple search engine tool like Google...

Again, Don't fear the Google!

---

### Post by Rodneyck on 2007-01-09
> **rsambuca said:**
> Whoa!  Very sloooooooooow torrents.  Unless they really pick up speed, I'll be installing in about 3 weeks:confused:

Same here. I am lucky if I get 1 KB/s. I may have to give up on the 3.26 DVD. I can't figure out how to do the Xdelta updating thing RAV posted.  I think my option is just to install the 3.2a CD and wait for the 3.3 mini release to update.

---

### Post by mips on 2007-01-09
I'll also wait for the 3.3 cd.

---

### Post by rsambuca on 2007-01-09
Well, I tried the 3.26 x86.  Still doesn't boot.  Tried to update the kernel using lxnay's instructions from one of the SL forums.  Now I have completely borked the system!  Oh well, guess it is a good thing I have six different OS's on my rig right now.  Using my favorite one, ubuntu Edgy.  When I have a chance I will try the 3.26 64bit, but I doubt it will work, given what has happened so for.  As much as I liked it, I will probably not bother re-installing 3.2, and will wait for a new SL version instead.

---

### Post by RAV TUX on 2007-01-09
> **Rodneyck said:**
> Same here. I am lucky if I get 1 KB/s. I may have to give up on the 3.26 DVD. I can't figure out how to do the Xdelta updating thing RAV posted.  I think my option is just to install the 3.2a CD and wait for the 3.3 mini release to update.

took about 2 days for 3.26 x86....I have been seeding the torrent since lastnight;)

---

### Post by pichalsi on 2007-01-10
I dont download torrents often but this somehow jumps up and down. I get speeds from 0 to 1500KB/s in both upload and download...

---

### Post by RAV TUX on 2007-01-10
> **pichalsi said:**
> I dont download torrents often but this somehow jumps up and down. I get speeds from 0 to 1500KB/s in both upload and download...
seems normal.....maybe you should just adjust your settings.

---

