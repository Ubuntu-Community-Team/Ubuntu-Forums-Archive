---
title: "[SOLVED] Rearranging PDF pages"
date: 2008-07-24
forum: General Help
---

### Post by Th3Professor on 2008-07-24
Anybody know of any quick ways to rearrange pages in a PDF?

Here's what I'm looking at doing. The first number is the current page, the second number is the page that I would like it to become:

```

 1 =>  1;  4 =>  2; 19 =>  3; 16 =>  4; 22 =>  5; 13 =>  6;  7 =>  7; 10 =>  8;
 2 =>  9;  5 => 10; 20 => 11; 17 => 12; 23 => 13; 14 => 14;  8 => 15; 11 => 16;
 3 => 17;  6 => 18; 21 => 19; 18 => 20; 24 => 21; 15 => 22;  9 => 23; 12 => 24;
25 => 25

```Thanks! :D

---

### Post by brian_p on 2008-07-24
> **Th3Professor said:**
> Anybody know of any quick ways to rearrange pages in a PDF?

Here's what I'm looking at doing. The first number is the current page, the second number is the page that I would like it to become:

```

 1 =>  1;  4 =>  2; 19 =>  3; 16 =>  4; 22 =>  5; 13 =>  6;  7 =>  7; 10 =>  8;
 2 =>  9;  5 => 10; 20 => 11; 17 => 12; 23 => 13; 14 => 14;  8 => 15; 11 => 16;
 3 => 17;  6 => 18; 21 => 19; 18 => 20; 24 => 21; 15 => 22;  9 => 23; 12 => 24;
25 => 25

```Thanks! :D

I am unable to spot the pattern but can point you towards pdfedit.

---

### Post by tacutu on 2008-07-24
pdftk does the job. it's in the repos

---

### Post by Th3Professor on 2008-07-26
> **brian_p said:**
> I am unable to spot the pattern but can point you towards pdfedit.

I suppose it doesn't have to have pattern if I need to manually rearrange each page, though maybe it does? Not sure. In any case, here's the rearranging followed by where the pattern is, not that it matters but it's interesting in the geeky :D way I suppose:

```

 1 =>  1;  4 =>  2; 19 =>  3; 16 =>  4; 22 =>  5; 13 =>  6;  7 =>  7; 10 =>  8;
 2 =>  9;  5 => 10; 20 => 11; 17 => 12; 23 => 13; 14 => 14;  8 => 15; 11 => 16;
 3 => 17;  6 => 18; 21 => 19; 18 => 20; 24 => 21; 15 => 22;  9 => 23; 12 => 24;
25 => 25

```The original:
```

 1,  2,  3,  4,  5,  6,  7,  8,
 9, 10, 11, 12, 13, 14, 15, 16,
17, 18, 19, 20, 21, 22, 23, 24,
25

```becomes:
```

 1,  4, 19, 16, 22, 13,  7, 10,
 2,  5, 20, 17, 23, 14,  8, 11,
 3,  6, 21, 18, 24, 15,  9, 12,
25

```Actually that's backwards, lol. The 2nd group there consists of the original page numbers in the order that they will be in, as presented in the 1st group, after they have been rearranged. :twisted:

The original 1-25 has basically been regrouped into 8 groups of 3 plus one on the end.

Anyway, I'll try pdfedit. Thanks :D
> **tacutu said:**
> pdftk does the job. it's in the repos

I'll try pdftk also. Thanks :D

---

### Post by Th3Professor on 2008-07-27
Would it be easier if I just separated the pages in the single PDF into 25 separate PDFs, and then re-merge them together into a new PDF in their new order?

Or is there a way to just do it in one step, or just one command, via the console?

---

### Post by Th3Professor on 2008-07-27
nevermind, i figured it out :D

here it is:

```

pdftk in.pdf cat 1 4 19 16 22 13 7 10 2 5 20 17 23 14 8 11 3 6 21 18 24 15 9 12 25 output out.pdf

```

:KS

---

