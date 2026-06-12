---
title: "Jaunty RC-Can't right-click copy in Evolution. Pastes blank"
date: 2009-04-19
forum: Installation &amp; Upgrades
---

### Post by Kirk M on 2009-04-19
Brand new Ubuntu user here. Haven't filled out my profile yet but I'm an older guy, disabled vet, and old geek (computers, R&D, etc).

I just updated to Ubuntu 9.04 RC from 8.10 (smooth, no problems seen so far except...) and I noticed that "right-click>Copy" in Evolution 2.26.1 out of the message content area does not work in either "plain text" or "HTML" mode. Attempting to paste (any way of pasting) the copy in Evolution or in any other application just pastes nothing. Funny thing is that the "right-click>Paste" is not grayed out as if something was actually in the clipboard.

It does work using the "CTRL-C" and from the"Edit>Copy" drop down menu in Evo. Probably had the same problem in the previous version of Evo. in 8.10 but didn't  come across it until after the upgrade?

I checked to forums for this problem before this post but although similar problems exists, they exists in so many varied forms (including crashing the entire client) over the past months I decided to go ahead and post here.

Lovin' this Ubuntu! :popcorn:

---

### Post by Kirk M on 2009-04-20
I've had a chance to look at this a bit closer and I've found a rather unique glitch.

If you read my post above I stated that *right-click>Copy* did not work out of the content area of a message. With further troubleshooting I've found this:

*Right-click>Copy* does not work only in messages that are being composed i.e. *new messages*, *replies* and *forwards*. *Right-clicking* on highlighted text de-selects the highlight so effectively you're copying nothing.

Now I'm hoping I make myself clear here since this is a bit unusual.

In *new messages*, *replies* and *forwards*, if the highlighted text extends all the way to the left hand side of the content area so that there's no letters, numbers or spaces left between the end of the highlight and the left side of the content area, *right-click>Copy* works as it should.

However, if the highlighted text *does not* extend all the way to the left hand side of the content area, *right-click>Copy* does not work as *right-clicking* de-selects the highlighted text as I described above.



*Right-click>Copy* works normally in received messages.

Can anyone verify this, please? I'd like to know if this is just an isolated problem.

---

