---
title: "[SOLVED] Iterate over filenames with spaces in command line"
date: 2008-10-01
forum: General Help
---

### Post by HyperHacker on 2008-10-01
I can't seem to find any way to do this. I have a program (lame, in this case) that takes one input file and one output file as arguments, i.e. 'lame foo.wav bar.mp3'. I want to call it in a loop for every .wav file in the current directory. Seems simple enough:```
for f in `ls *.wav`; do lame $f $f.mp3; done
```The problem is this fails if a filename has spaces in it. The file "music and stuff.wav" becomes three strings; "music", "and", "stuff.wav".

I've spent about an hour Googling how to avoid this, and I've found solutions that prevent the names being split into three pieces, but they still don't work, because the command that ends up being run is:```
lame music and stuff.wav music and stuff.mp3
```The spaces need to be escaped here, and I can't seem to find any way to do it. The best method I came up with was something like this:```
foo=(echo music and stuff.wav|sed -e s/' '/'\\ '/g); echo $foo
```But for some reason this doesn't work: "bash: syntax error near unexpected token `|'"

---

### Post by dagoth_pie on 2008-10-01
write it like this
```
lame\ music\ and\ stuff.wav music\ and\ stuff.mp3
```
although I tend to avoid spaces use "-" or "_" it makes it a lot easier

---

### Post by spiderbatdad on 2008-10-01
```
for f in "*.wav"; do lame $f "$f.mp3"; done
```

---

### Post by HyperHacker on 2008-10-02
Nope.
```
hyperhacker@mercury:~/music/etc$ for f in "*.wav"; do echo lame $f "$f.mp3"; done
lame ayu.wav breakdown.wav datw.wav deluxe.wav dober man.wav golden sky.wav guilty sky.wav guilty sky guitar.wav madobe nite.wav marisa.wav only star.wav supporation (FAIL).wav unite.wav *.wav.mp3
```What I need is:```
lame ayu.wav ayu.wav.mp3
lame breakdown.wav breakdown.wav.mp3
[...]
lame dober\ man.wav dober\ man.wav.mp3
```etc. (Having .mp3 instead of .wav.mp3 would be even better, but I can fix that afterward.)

I'll probably need the parentheses escaped too now that I look at the list.

---

### Post by stylishpants on 2008-10-02
spiderbatdad's solution is mostly correct.  

Try this:
```
for f in *.wav; do lame "$f" "$f.mp3"; done
```

Quoting is a better solution than trying to detect and escape certain characters in this case, your solution will be more robust and simpler to understand this way.

---

### Post by HyperHacker on 2008-10-02
That works, even though echoing the command shows "lame dober man.wav dober man.wav.mp3"... O_o Not sure how that works, but thanks anyway.

---

