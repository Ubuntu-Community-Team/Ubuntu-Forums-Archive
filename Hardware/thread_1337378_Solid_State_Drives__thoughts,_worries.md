---
title: "Solid State Drives:  thoughts, worries?"
date: 2009-11-25
forum: Hardware
---

### Post by pw_f100_220 on 2009-11-25
My lappy's hard drive is failing so I need a new hd.  I generally use no more than thirty gigs in my internal, so I don't feel like upgrading the size, just the speed if possible.  So I decided to look into solid state.  Black Friday is nearing so I would like to make a snappy decision, but there's a lot of controversy and confusion about Linux and filesystems and all that.  

Anyone have any pleasant experiences or trouble?  ext4 "healthier" than ext3?  faster?   are Super Talent drives as lame as the name and low price implies (100 for 32 gb with much faster claimed speeds than i've seen)?  

Thoughts?  Thanks

---

### Post by wilee-nilee on 2009-11-25
I have no experience with a built in solid state, but my usb thumbs run as fast as the standard HD on my new netbook, and the thumbs have just the iso not a unpacked uncompressed install.

---

### Post by pw_f100_220 on 2009-11-25
On filesystems, i keep hearing about limited writing on ssd's and the filesystem's journaling/writing methods make a difference...

in other words, i'm a little worried about longevity

---

### Post by movieman on 2009-11-25
> **pw_f100_220 said:**
> On filesystems, i keep hearing about limited writing on ssd's and the filesystem's journaling/writing methods make a difference...

Here's an interesting article on the subject:

[http://thunk.org/tytso/blog/2009/03/01/ssds-journaling-and-noatimerelatime/](http://thunk.org/tytso/blog/2009/03/01/ssds-journaling-and-noatimerelatime/)

I'm not sure whether it reached a consensus conclusion, but there are a lot of interesting comments as well as the benchmarks :).

Personally I'd mount with noatime and try to reduce writes as much as possible (e.g. reduce logging, don't sync when logging, etc).

---

