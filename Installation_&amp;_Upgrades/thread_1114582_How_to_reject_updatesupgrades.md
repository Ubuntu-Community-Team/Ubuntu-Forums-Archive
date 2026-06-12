---
title: "How to reject updates/upgrades?"
date: 2009-04-02
forum: Installation &amp; Upgrades
---

### Post by DeMus on 2009-04-02
Through the normal updater I receive a message that a new update for a program I use is available.
Now I know that this version, which may be better, also has features I don't want since it makes working with it more complicated.
How do I prevent these updates from being installed, other than always unchecking the little checkboxes in the updater window? I like to see the items being removed from the list of updates, so even the orange icon in the top panel disappears "since there are no new updates anymore".
Who can help me?

---

### Post by unutbu on 2009-04-02
Edit (or make) /etc/apt/preferences. 

Put as its contents

```
Package: PACKAGENAME
Pin: version VERSION
Pin-Priority: 1001
```

Change PACKAGENAME and VERSION as appropriate.

Priority 1001 means that package/version will never be replaced by apt.

See [http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html](http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html)
section 3.10

---

### Post by DeMus on 2009-04-02
> **unutbu said:**
> Edit (or make) /etc/apt/preferences. 

Put as its contents

```
Package: PACKAGENAME
Pin: version VERSION
Pin-Priority: 1001
```

Change PACKAGENAME and VERSION as appropriate.

Priority 1001 means that package/version will never be replaced by apt.

See [http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html](http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html)
section 3.10

Thanks, this is what I am looking for.

---

### Post by DeMus on 2009-04-02
> **DeMus said:**
> Thanks, this is what I am looking for.

No, it isn't. It doesn't work,or I do something wrong.
I did find however another way: I unchecked the box in the Software sources windows in front of the server which gives me those updates. I only get one program from that server so I can do that without having the risk of not receiving other updates.

---

### Post by Partyboi2 on 2009-04-03
Another way is to open up Synaptic and search for the package you don't want upgraded then highlight it and go to Package>Lock Version.

---

