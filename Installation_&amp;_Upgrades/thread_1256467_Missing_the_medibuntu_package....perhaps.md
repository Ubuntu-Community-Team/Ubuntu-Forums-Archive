---
title: "Missing the medibuntu package???....perhaps"
date: 2009-09-02
forum: Installation &amp; Upgrades
---

### Post by mimitam on 2009-09-02
I am trying to get Video working on my Ubuntu 9.04. I followed HOW-TO instructions but came to a block.

**Problem**

When Ubuntu tried to download the latest software, it failed - Failed to find file. Here's what I did:

gksudo gedit /etc/apt/sources.list

Instruction: Add the following two lines to the bottom of the list, remembering to change the Ubuntu version accordingly:

deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) jaunty free non-free
deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) jaunty free non-free

As I close the panel, it did a reload of the latest software. Here's what I got as error:

[COLOR=Red]Could not download all repository indexes

Failed to fetch [http://packages.medibuntu.org/dists/jaunty/Release](http://packages.medibuntu.org/dists/jaunty/Release)  Unable to find expected entry  deb-src/binary-i386/Packages in Meta-index file (malformed Release file?)
Some index files failed to download, they have been ignored, or old ones used instead.
[/COLOR]
The words "malformed release file" on the error msg caught my eyes. The instruction did specify "...to change the Ubuntu version accordingly" on the 2 links above.

What does that mean? And, what would be my two correct deb lines to add?

Please help.

Many Thanks...Mimi

---

### Post by drs305 on 2009-09-02
I would just get rid of your entries in sources.list and let medibuntu add the entries and import the public keys automatically with this set of commands:
```

sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list && sudo apt-get -q update && sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring && sudo apt-get -q update

```

Taken from this site:
[https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

---

### Post by mimitam on 2009-09-02
Thank you so much! The install went to the end without failure, as far as I am concerned.

But, I still cannot see this video: [B]
[http://movies1.vtc.com/player/hbMoviePlayer.php?cipher=1|80x30-2||ti|p3|4||su3el-en|hg&size=large](http://movies1.vtc.com/player/hbMoviePlayer.php?cipher=1|80x30-2||ti|p3|4||su3el-en|hg&size=large)[/B]

I could see this video however: **[http://www.nfb.ca/film/battle_of_arras_3/](http://www.nfb.ca/film/battle_of_arras_3/).**

The first video opens up to a VTC player. How can I fix this?

I really appreciate your help.

Many Thanks...Mimi

---

