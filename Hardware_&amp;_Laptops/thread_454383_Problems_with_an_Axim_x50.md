---
title: "Problems with an Axim x50"
date: 2007-05-25
forum: Hardware &amp; Laptops
---

### Post by chriskasurak on 2007-05-25
Hey there,

First off, i'll preface this by saying that i'm a noob with less than a month of linux experience. I just switched from windows. I can do things like installing stuff from source and editing config files, but not very easily. Just so you know where i stand.

I'm trying to sync my axim. This morning, i had it working using arun's tutorial here: [http://www.blog.arun-prabha.com/2007/02/21/how-to-sync-your-pocket-pc-with-ubuntu/](http://www.blog.arun-prabha.com/2007/02/21/how-to-sync-your-pocket-pc-with-ubuntu/)

i could poke around in the axim's directories etc. But, this is the only time out of maybe ten times i've sat down and tried to get it set up that it worked. Usually, i get stopped at the first step, dmesg |tail because either there's an ehci "device not accepting address" error, or what i'm getting now, which is that dmesg doesn't even detect the axim being plugged in. In short, i have no idea how i made it work.

I've been installing all kinds of other things as well, i've lost track, and i don't know whether those things might have some effect on the usb detection. Right now lsusb doesn't show the axim, but it did this morning. 

can anyone offer any help or ideas here?

I'm sure this is a totally seperate problem, but is there some way i can get around having to load the ipaq module every time i boot? my guess is compiling it into the kernel, but i have zero idea how to do that.

---

### Post by chriskasurak on 2007-05-25
ok, so i've made some progress. It seems to matter when i turn the device on: if i turn it on and then put it in the cradle, as i would with windows activesync, nothing happens. If i turn it on while it's already in the cradle, it got detected and everything works! I'm pretty sure i've tried that more than once with mixed results though, so it may not be the key.

---

