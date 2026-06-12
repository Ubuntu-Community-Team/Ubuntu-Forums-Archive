---
title: "Yay! Latest Barry builds allow uploading java apps to your Blackberry!"
date: 2009-01-31
forum: Hardware
---

### Post by DirtDawg on 2009-01-31
Hey all. I wrote a much longer, more involved post on this in the Tips and Tutorials sub-forum before I realized there are strict guidelines over there, so I thought I would share this in the general forums as well in case my other post doesn't make the cut. 

The latest builds of Barry include a 'bjavaloader' command to upload java 'cod' files to your Blackberry. No more hunting the Net for 'jads!' I'm sure this will be included in the next release, but if you're impatient like me, you want it now!

Very complete installation instructions [here]("http://www.netdirect.ca/software/packages/barry/cvs.php") and dependencies listed [here]("http://www.netdirect.ca/software/packages/barry/dependencies.php"). You need to use cvs or git (I used git) as the completed bjavaloader code was only patched in a couple days ago. Also note that apps installed with bjavaloader can only be removed with bjavaloader. They cannot be removed directly from your Blackberry with the normal delete command.

After install, use
```
bjavaloader -h
``` for a full list of commands. Basically, 'dir', 'load' and 'erase' are probably what you'll want to use.

Remember to send your love to the Barry developers!

---

