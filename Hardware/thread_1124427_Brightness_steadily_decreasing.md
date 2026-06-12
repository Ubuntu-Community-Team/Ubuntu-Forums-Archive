---
title: "Brightness steadily decreasing"
date: 2009-04-13
forum: Hardware
---

### Post by CCSaar on 2009-04-13
I had what seems to be a common problem with Ubuntu on laptop: My brightness control was completely haywire.

I found on the internet a forum that suggested the following:

> Edit the two files:

/usr/lib/hal/scripts/linux/hal-system-lcd-get-brightness-linux

and

/usr/lib/hal/scripts/linux/hal-system-lcd-get-brightness-linux

Change the first line of each file from

#!/bin/sh

to

#!/bin/bash

I did that, and at first all seems well. I can use my Fn+Up/Down keys to adjust brightness without error. But after waiting a minute or so, I notice the brightness getting steadily dimmer. 

For some reason, through no input of my own, the brightness will steadily fade all the way down to the lowest level in about a minute. I can bring it back up again with Fn+Up, but it just does it again a minute later. 

Even as I'm typing I'm pausing every now and again to bring the brightness back up.

What's going on, and how do I fix it??

I'm on a Dell XPS M140 running Ubuntu Intrepid Ibex

---

