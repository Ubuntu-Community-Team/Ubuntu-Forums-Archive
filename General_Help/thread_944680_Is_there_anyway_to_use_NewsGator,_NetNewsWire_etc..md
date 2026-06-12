---
title: "Is there anyway to use NewsGator, NetNewsWire etc. with Ubuntu on Hardy?"
date: 2008-10-11
forum: General Help
---

### Post by DjMojoRisin69 on 2008-10-11
Hi,

I just started using NetNewsWire and NewsGator to read my RSS feeds, and I wanted to know if there was any RSS reader(client based) not web-based that would sync with my NewsGator Account?

They have some pretty cool synchronization functionality that allows the feeds to be synced across all computers.

I know that I could use their web-based solution, but unfortunately it's not that good. Feed Demon their windows based solution is pretty good, and their NetNewsWire for iPhone is pretty sweet as well.(These are the 2 I am currently using).

Any ideas would be appreciated.

Thanks!

---

### Post by Oceanwatcher on 2008-10-11
I have been searching high and low to find a good feed reader.

On Windows, I am now using FeedDemon, but after reading about RSS Bandit a few days ago, I am considering trying it out.

I have used RSSOwl for a while, but must admit that after using FeedDemon, I need something that will sync with Newsgator/NetNewsWire. That said, if yuo do not crave this, then you are absolutely fine going with RSSOwl as it is a wonderful feed reader with Linux support out of the box. Download it, unpack it and run it!

But the one thing that is now going around in my head isa question. What are the possibilities of finding someone that can take the sourcecode from RSS Bandit and port the program to Linux? There should be good chances of getting it to run, and from what I have seen so far, it might be the best feed reader out there!

So calling all Mono developers: Please take a look at [www.rssbandit.org](www.rssbandit.org) !

I am going to make a separate thread about this as well.

---

### Post by directhex on 2008-10-11
> **Oceanwatcher said:**
> I have been searching high and low to find a good feed reader.

On Windows, I am now using FeedDemon, but after reading about RSS Bandit a few days ago, I am considering trying it out.

I have used RSSOwl for a while, but must admit that after using FeedDemon, I need something that will sync with Newsgator/NetNewsWire. That said, if yuo do not crave this, then you are absolutely fine going with RSSOwl as it is a wonderful feed reader with Linux support out of the box. Download it, unpack it and run it!

But the one thing that is now going around in my head isa question. What are the possibilities of finding someone that can take the sourcecode from RSS Bandit and port the program to Linux? There should be good chances of getting it to run, and from what I have seen so far, it might be the best feed reader out there!

So calling all Mono developers: Please take a look at [www.rssbandit.org](www.rssbandit.org) !

I am going to make a separate thread about this as well.

Methods that are still missing in Mono: 27
P/Invokes called: 523
Methods that throw NotImplementedException: 226
Methods called marked with [MonoTodo]: 362

The most toxic ones are the P/Invokes (calls into platform-specific libraries, in this case lots of Windows DLLs like gdi32.dll and uxtheme.dll), which cannot simply be implemented by Mono.

---

### Post by dakkar9999 on 2008-11-17
Nevermind.  Just realized RSS Bandit is windows only...

---

### Post by Zill on 2008-11-17
I use [Liferea]("http://liferea.sourceforge.net/") for RSS feeds.

```
sudo apt-get install liferea
```

---

