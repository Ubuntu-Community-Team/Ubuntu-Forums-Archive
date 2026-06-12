---
title: "Resuming a stopped unattended install (via preseed)"
date: 2009-04-16
forum: Installation &amp; Upgrades
---

### Post by jesperronn on 2009-04-16
Hi there.

My preseeded installation stopped (at 27% progress) and via ALT+F4 I found that there was an unanswered question i need to fill in (hudson insecure installation) -- see screenshot of log window.

[IMG]http://img4.imageshack.us/img4/844/picture12s.png[/IMG]

```
in-target: WARNING: The following packages cannot be authenticated
in-target:  Hudson
in-target: Install these packages without verification [y/N]?

```

Now how do I answer that question? How do i force the installation to continue?

I already tried the following:
[LIST]
[*]Opened a new console and ran "apt-get install hudson". Answering the question installs hudson but the preseeded installation still hangs
[/LIST]

Any help or links will be greatly appreciated!

/Jesper

---

### Post by jesperronn on 2009-04-16
Oh i forgot to mention that I tried to run debconf-get-selections on a running machine after I installed hudson via apt-get install. But debconf-get-selections and debconf-get-selections --installer showed no lines with the text "hudson"

---

