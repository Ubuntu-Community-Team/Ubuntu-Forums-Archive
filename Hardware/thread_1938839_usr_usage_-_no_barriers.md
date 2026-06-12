---
title: "/usr usage - no barriers?"
date: 2012-03-10
forum: Hardware
---

### Post by ivanmmj on 2012-03-10
Good morning, all.

Does much ever get written to /usr unless you are installing something? Is /usr usually only being read from?

I'm thinking of moving /usr to its own partition and making it a btrfs partition compressed with LZO with barriers disabled. I'm trying to speed up my laptop's boot and the overall speed of opening programs. (Without having to upgrade the hard drive.)
The issue is that having no barriers can be dangerous to data integrity. I figured that if I use no barriers but /usr isn't written to often, I would be safe. Is that a correct assumption? (Or is it foolish?)

Also, would EXT4 with barriers disabled be better than btrfs with LZO compression and barriers disabled?

---

