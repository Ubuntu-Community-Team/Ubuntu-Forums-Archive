---
title: "What do I do when I find a bug?"
date: 2008-11-02
forum: General Help
---

### Post by frazerr on 2008-11-02
Hi,

So I am fairly new to Ubuntu,
and was wondering what to do when I find a bug?  where do I report it?

The bug I have found is:

when changing your date and time from manual to 'keep synchronised with internet server'  it says you need to install ntp.
I clicked ok, synaptic did its thing, and it seemed to work, except date and time still would not let me choose 'keep synchronised'. When I tried to choose it, it asked me to install ntp again.

I checked what processes I had running and there was ntpd...?
then I closed the date and time box. when I again clicked to adjust date and time, it had already chosen 'keep synchronised'

So my suggested fix for the bug is that when the 'date and time config box' it instals ntp, it needs to also update its own display.

Is this the right place to report things like this?

Thanks

Frazer

---

### Post by LaRoza on 2008-11-02
First thing you should do is make sure it is a bug. It may be necessary to restart certain processes. Reading the manuals and making sure you followed all the instructions is a good place to start.

Then, check existing bug reports. If you are sure it isn't a mistake on your part, and it hasn't been reported, then you can report it.

Find the project's page to see how they handle bug reports.

---

### Post by frazerr on 2008-11-02
so, where do I find the project page for something that seems built in to the system, like 'date and time'

I dont even know what the application is called, and it is not obvious from a google search

---

### Post by frazerr on 2008-11-02
This is what I was looking for,

[https://bugs.launchpad.net/ubuntu](https://bugs.launchpad.net/ubuntu)

and the bugs has already been reported a few times:guitar:

---

### Post by editrix on 2008-11-02
Glad you found your answer. I've discovered that the easiest way to search for anything Ubuntu is uboontu.com (last link in my sig). Just try entering **bug ntp** in the search box and you'll see how powerful it is. And you can add it to your Firefox search engines.

---

