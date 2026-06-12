---
title: "Plaintext Frequency Analyzer"
date: 2008-10-24
forum: General Help
---

### Post by altonbr on 2008-10-24
I'm playing around with cryptography and want to use a frequency analyzer[1] to test encrypted messages. Is there any graphical piece of software that exists for Ubuntu for this purpose?

I'm sure I, or someone, could write a simple script in PHP, Python or BASH, but I'm wondering if such a program already exists.

(off-topic): and what about one for sound?

[1] [http://en.wikipedia.org/wiki/Frequency_analysis](http://en.wikipedia.org/wiki/Frequency_analysis)

---

### Post by mikjp on 2008-10-24
If your encrypted files are plain text, you can use the normal unix tools for analysing frequencies of characters. See, for example the following sites:

[1] [http://tldp.org/LDP/abs/html/textproc.html](http://tldp.org/LDP/abs/html/textproc.html)
[2] [http://www.ai.rug.nl/~lambert/unix.html](http://www.ai.rug.nl/~lambert/unix.html)
[3] [http://www.ida.liu.se/~lensa/nikolaj/egrep_for_linguists.html](http://www.ida.liu.se/~lensa/nikolaj/egrep_for_linguists.html)

[2] gives the following oneliner for counting character frequencies:

      cat hfinn10.txt \
        | sed 's/./&~/g' \
        | tr '~' '\012' \
        | sort -n \
        | uniq -c \
        | sort -n \
        | tail -20

---

