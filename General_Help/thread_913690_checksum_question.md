---
title: "checksum question"
date: 2008-09-08
forum: General Help
---

### Post by PGScooter on 2008-09-08
Hi, this is not an urgent problem; I ask it mainly out of curiosity.

I have thousands of files I am going to burn to a cd. I have a text file where I have all of the checksums of those files entered. However, I would also like to have the checksum of THAT text file IN that text file. Is that possible? Obviously, if I calculate the checksum and then put it in the file, it will have changed.

Did that make sense?

Thanks

---

### Post by kidders on 2008-09-09
Hi there,

To write a file's own checksum into its content, you could construct a massive equation expressing the checksum in terms of the file's content. In theory, you could then solve the equation to predetermine your checksum. If you take RFC 1321 (the MD5 algorithm) as an example, such an equation could have up to a thousand unknowns, and may well have been intentionally designed to be unsolvable.

The best suggestions I can come up with are ...[LIST]
[*]Not to care about the checksum file's checksum. Most of the time, an indication that *something* doesn't add up is enough (without necessarily being sure exactly what).
[*]Compute your checksum file as you normally would, and rename it. Setting the name of the file to its own checksum would at least give you some sense of its reliability.
[/LIST]

I hope that helps.

---

### Post by PGScooter on 2008-09-09
Hi kidders,

what an interesting reply; thank you! I like your second idea best. I was planning on just having another file with the checksum of the checksum file, so that is at least an improvement over my idea. Someday when I have time to waste, I might look into this puzzel a little more.

Thank you

---

