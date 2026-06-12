---
title: "spell check multiple text documents"
date: 2008-08-20
forum: General Help
---

### Post by paxmanchris on 2008-08-20
Problem:
Need to search through multiple files of php code, javascript code, and pick put spelling errors in between double and single quotes,

Solution tried:
Aspell.

Question:
is there any way to go trough all my files and spell check them?

---

### Post by pytheas22 on 2008-08-20
Do you know how to program at all?  I don't know of any applications that can do this easily, but if you don't mind a build-it-yourself solution, it would be pretty easy to write a short script in Python or Perl (maybe even bash) that would do this for you.  You just need to write something that basically looks like:
```

for file in directory:
   for word in file
      if !(word in dictionary):
          replace word with "word" (or 'word')
```

Then it would cycle through all of the files and put misspelled words with in quotes (you'd need obviously to make sure that all of the coding tags and things are not recognized as spelling errors).

If you don't know how to program at all, let me know; I had to solve a similar task for a programming class once and could probably convert my solution to do what you need with minimal effort.

Of course, maybe someone else will respond with a solution that doesn't require programming at all, which would be ideal, since the point of free software is not to have to waste time rewriting what's already been written.

---

### Post by paxmanchris on 2008-08-20
Thanks for the quick response.

yes, i can code. i like python the best.

i think i might just go through each file with Aspell.

by the time im done programming something good, i would have solved my problem by then.

but it you would like to post code, the please do.

---

