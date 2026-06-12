---
title: "how to compare two text files to get the identical lines"
date: 2008-11-09
forum: General Help
---

### Post by honglou on 2008-11-09
[FONT="Arial Narrow"]Hi,there.I am asking for help here.I get two text files of products number.I need to compare the 2 files to get the identical products number.

The two files are attached below here.[/FONT]

---

### Post by mjpatey on 2008-11-09
There is a command called "diff" which will show the differences between two files, if that helps at all.  The syntax, I believe, is:

diff file1.txt file2.txt

I hope this gets you on track, at least!

---

### Post by mjpatey on 2008-11-09
... also, if you use the -y modifier, it will display the files side by side, which would help you see the similarities.

---

### Post by honglou on 2008-11-09
> **mjpatey said:**
> ... also, if you use the -y modifier, it will display the files side by side, which would help you see the similarities.

hi,mjpatey.Thx.And the advice doesn't work for my problem here.

---

### Post by iponeverything on 2008-11-09
```
cat file1.txt|sed s/\"//g |awk -F\- '{print "grep "$2 " file2.txt"}' |sh >> dups.txt
```

---

### Post by mjpatey on 2008-11-09
OK.  Sorry, gave it my best shot!  After some searching, I don't see a command to do exactly what you're asking.  But you could try the manpage for diff:

```
 man diff
```

and see if any of the options would get you close.

---

### Post by lovinglinux on 2008-11-09
You could use "Meld" from the repositories. It is a very nice GUI diff tool, that highlight different lines from both files.

---

### Post by honglou on 2008-11-10
> **iponeverything said:**
> ```
cat file1.txt|sed s/\"//g |awk -F\- '{print "grep "$2 " file2.txt"}' |sh >> dups.txt
```

:guitar::KS
Thank you,iponeverything.I am done with the problem after the command issued.And thank you all.May GNU-Linux be with you.

---

### Post by honglou on 2008-11-10
> **honglou said:**
> :guitar::KS
Thank you,iponeverything.I am done with the problem after the command issued.And thank you all.May GNU-Linux be with you.

hi,iponeverything.Thank you for your nice and kind advice.
And I still get a problem here since I am not famillar with the commands of 'sed' or 'awk'.I want to check out the products number in file2 ,but not in file1 which are products already on the website.So after the comparison,i would update the the website with the missing products.
I wish you would get time and trouble to help me.Thank you in advance!

---

### Post by iponeverything on 2008-11-10
> **honglou said:**
> hi,iponeverything.Thank you for your nice and kind advice.
And I still get a problem here since I am not famillar with the commands of 'sed' or 'awk'.I want to check out the products number in file2 ,but not in file1 which are products already on the website.So after the comparison,i would update the the website with the missing products.
I wish you would get time and trouble to help me.Thank you in advance!

Not quite sure what your asking.You need the product numbers uniq to file2?

If that is the case then just do:


```
diff dups.txt file2.txt| grep \> |sed s/\>//g |sed s/\"//g|awk '{print "\"HJ-"$1"\""}' > uniq-to-file2.txt
```

---

### Post by iponeverything on 2008-11-10
BTW -- it is no trouble at all. Solving problems like this for me is like sudoku is for my wife.

---

### Post by honglou on 2008-11-10
> **iponeverything said:**
> Not quite sure what your asking.You need the product numbers uniq to file2?

If that is the case then just do:


```
diff dups.txt file2.txt| grep \> |sed s/\>//g |sed s/\"//g|awk '{print "\"HJ-"$1"\""}' > uniq-to-file2.txt
```

Thank you,iponeverything.You helped me a lot.Thanks again!
Nice wishes to you.
:guitar:

---

