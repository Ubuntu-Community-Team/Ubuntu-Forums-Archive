---
title: "change line spacing in a pdf file"
date: 2008-10-10
forum: General Help
---

### Post by diamantis13 on 2008-10-10
Hi,
I would like to change the line spacing in a pdf file from double to single. I read about many pdf editing programs, but none seems to work! Is there any other way (e.g. convert to ps and then edit it somehow) or the only way is to convert it to text?
Thank you very much!

---

### Post by Sam on 2008-10-10
Use the commands pdf2ps, pdftohtml or pdftotext.

---

### Post by diamantis13 on 2008-10-10
Thanks,
I tried both pdftohtml and pdftotext but the lines where numbered in the manuscript and now every second line there is a number. e.g
in the pdf:
```

1 blahblah

2 blahblahblah

3 more blahblah

```
and in the html and txt it comes out like
```

1
blahblah
2
blahblahblah
3
more blahblah

```
I think I could write some script to fix the .txt file but as pdf2ps keeps the layout correct i was wondering if I can change the line spacing by editing the .ps file

---

### Post by Sam on 2008-10-10
Save the HTML output (no tags, only the text) in a file, lets say ~/test.txt
```
1
blahblah
2
blahblahblah
3
more blahblah
```

Then run
```
grep -v [[:digit:]] ~/test.txt > ~/test_treated.txt
```
Every lines containing only numbers will be stripped and saved to ~/test_treated.txt

---

### Post by diamantis13 on 2008-10-10
Grep was the solution!
so I did: 
1. pdftohtml
2. opened in browser copy and save text
3. grep

The unsolvable problems: Step 1 loses figures and some table formating, step 2 formating is lost (titles are not in bold :( ) and step 3 lost all references as they were full of numbers
But it is good enough!

---

