---
title: "Strange memtest86+ problems"
date: 2008-10-13
forum: General Help
---

### Post by chrroessner on 2008-10-13
Hi,

I have strange problems with memtest86+ version 2.01 (intrepid and official ISO):

I get errors, where there are no errors. See here please:

[http://www.roessner-net.com/bilder/memtest86/](http://www.roessner-net.com/bilder/memtest86/)

The address failures are all zero. Good and bit-errors do match with a zero error-mask. I do not understand this.

The errors always occur at the same test positions.

But starting linux and using memtester with maximum available memory, I do not get any problems, errors.

Even switched to /usr/src/linux and did the most hardest test on my console:

make -j

After two hours I aborted with Ctrl+C, because there was no memory left. But I just used it for a test :-)

So it seems that I do not have memory problems, even memtest86+ says so.

And now the most interesting thing:

My friend does have exactly the same hardware components: board, cpu and RAM and he does not have any errors.

If I do play around with NB voltage, the first 2 or 3 bugs are gone, but I do not get an error free output.

What do you think about this? Should I not care about this?

Thanks very, very much in advance for comments on that

Christian

---

