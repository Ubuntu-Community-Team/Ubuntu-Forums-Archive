---
title: "Japanese characters on vim"
date: 2008-11-10
forum: General Help
---

### Post by vevo on 2008-11-10
I have installed ubuntu 8.10 with US language on a desktop pc.
I would like to use vim as an editor of .tex file to be compiled with latex.

I can write Japanese characters using vim (and gvim). 
When I try to open using vim (or gvim) a document containing Japanese characters edited in another pc, a lot of strange symbols appear.
The same document show the japanese character if opened with open office.

any solution?
thank you very much,
vevo

---

### Post by Mazin on 2008-11-10
What encoding are the files in that won't open correctly?
My vim install seems to handle Unicode without any problem.

---

### Post by vevo on 2008-11-10
I do not know, I just have the file .tex coming from a japanese windows computer.
How can I change the encoding in vim? What type of encoding do you think will be ok?

thanks,
vevo

---

### Post by Mazin on 2008-11-10
Your documents from your Japanese Windows computer may be in Shift JIS encoding, which is a special encoding for only Japanese.  UTF8 can handle any language and is the most widely supported.

Try this:

```
iconv originalfile.tex -f SHIFT-JIS -t UTF8 -c -o newfile.tex
```

and then open it in vim.  HTH. :)

---

### Post by vevo on 2008-11-11
I worked out perfectly, except for one "little" thing:

all the "\" character where trasformed in "¥".

I solved it typing from vim :%s/¥/\\/g , but I had to do it for three documents.. is there some way to do it within the command you suggested from the bash?

thanks a lot,
vevo

---

### Post by geirha on 2008-11-11
sed is your friend.
```
sed -i 's/¥/\\/g' file1.tex file2.tex ...
```

---

### Post by vevo on 2008-11-11
works perfectly

iconv file.tex -f SHIFT-JIS -t UTF8 -c -o file.tex && sed -i 's/¥/\\/g' file.tex

thanks a lot,
vevo

---

