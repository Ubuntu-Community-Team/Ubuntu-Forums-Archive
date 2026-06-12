---
title: "reading dvds"
date: 2005-01-29
forum: Hardware &amp; Laptops
---

### Post by gogodidi on 2005-01-29
is there a way to make linux be able to read dvds?

I can read cd's fine, I can play music off them, and burn to them (on my second drive) but, I can not read dvds on my first drive. )

is there some way to let the machine boot the thing?

thanks for any answers

---

### Post by lt_kije on 2005-01-30
Can you be a bit more specific about your setup? From your post, it seems like you have two (IDE?) optical drives -- one CD, one DVD. I have a similar set up; in order to read DVDs, I simply insert the disk and use the mount command to mount it:

$ mount /dev/hdc

Then I navigate the folder as usual. I have automounting of removable storage turned off; if you have that on, you shouldn't even need to manually mount the disk.

lt_kije

---

