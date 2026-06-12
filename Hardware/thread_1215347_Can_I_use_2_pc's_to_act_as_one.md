---
title: "Can I use 2 pc's to act as one?"
date: 2009-07-17
forum: Hardware
---

### Post by nix-n00b on 2009-07-17
Like say I have two boxes, one which is pretty new duo core 4gb ram, 160 hd, with ubuntu juanty, can i combine that with another box say if i buy another dual core box with 6 gb ram, 640 gb hd, ect.. to create one node that will have 4 + 6 gb ram from both boxes, for a 10gb ram box, and combine the pc's to act as one, a "cluster" i guess?

How do i go about doing this, any tutorials and links would be appriciated, thanks in advance :-)

---

### Post by lisati on 2009-07-17
Although I've never done it myself, I suspect that you can probably do *something* like what you propose. You might want to read up on [muliprocessing]("http://en.wikipedia.org/wiki/Multiprocessing").

---

### Post by brettg on 2009-07-17
Technically, the correct answer is yes.

However it will be useful only for a very narrow range of uses. Large number crunching intensive apps such as CGI rendering or large scale scientific modeling etc. Such clusters can only run software that is written specifically to run in a clustered environment. 

[http://www.beowulf.org/overview/index.html](http://www.beowulf.org/overview/index.html)

It will be totally unsuitable for anything you are likely to do such as web surfing, playing games, editing documents etc.

So, the real answer is, unfortunately, no.

---

