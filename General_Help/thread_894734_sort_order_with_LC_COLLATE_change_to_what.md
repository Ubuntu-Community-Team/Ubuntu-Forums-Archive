---
title: "sort order with LC_COLLATE: change to what?"
date: 2008-08-19
forum: General Help
---

### Post by martini2 on 2008-08-19
Hi
i need to change the sort order of files in the system to sort them correctly as de_DE.UTF-8 does not work for me.
I have

10.jpg
11.jpg
12.jpg
1.jpg
20.jpg
21.jpg
2.jpg

I want

1.jpg
10.jpg
11.jpg
12.jpg
2.jpg
20.jpg
21.jpg

and if possible independent from the file extension.
What should i set LC_COLLATE set to? Is there a list of options i could try to match my needs?

---

### Post by unutbu on 2008-08-19
Try 
```
LC_COLLATE=C sort FILENAME
```

I found this here:
[http://www.nedit.org/pipermail/discuss/2005-October/007556.html](http://www.nedit.org/pipermail/discuss/2005-October/007556.html)

If FILENAME contains
```
10.jpg
11.yo
12.howdy
1.jpg
20.jpg
21.jpg
2.jpg

```
```
LC_COLLATE=C sort FILENAME
``` returns

```
1.jpg
10.jpg
11.yo
12.howdy
2.jpg
20.jpg
21.jpg
```

---

### Post by martini2 on 2008-09-10
LC_COLLATE=C sort FILENAME gives me an error message but LC_COLLATE=C works and does what i want.
thank you unutbu for the help!

---

### Post by cboese on 2009-01-16
Hello!
I try to change the sort order and found some documantation about LC_* (esp.: LC_COLLATE and LC_CTYPE)

Is it possible to have a C-like sort order (case-insensitive) and still have the hidden files (.*) sorted first?
When I use LC_COLLATE=C it ignores the leading "."-sign and sorts the files according to the next character (which I dont want).
Is this possible and when yes, how?
I would appreciate any hints and urls on this :-)

greetings
         cboese

---

### Post by kung fu buntu on 2009-09-30
> **martini2 said:**
> Hi
i need to change the sort order of files in the system to sort them correctly...
I have

10.jpg
11.jpg
12.jpg
1.jpg
20.jpg
21.jpg
2.jpg

I want

1.jpg
10.jpg
11.jpg
12.jpg
2.jpg
20.jpg
21.jpg

and if possible independent from the file extension.
What should i set LC_COLLATE set to? Is there a list of options i could try to match my needs?


Additionally to this I would also like for directories to be sorted this way:```

.b
 b  
_b  
a  
b   
B  
c  
ç  
d
```

Any tips on how I might get this behaviour?
I can also give it a go at locale files... but I have no idea what and where to edit... any tips?

---

### Post by kung fu buntu on 2009-10-03
bump?

---

### Post by Jim Danner on 2010-05-13
I'm bumping this question -- on other Unix/Linux systems I have the 'hidden' files first, or last: the leading dots are not ignored but interpreted as characters. On Lucid, commands like *ls* and *sort* ignore the leading dots. How do I change the behavior? (Thanks)
> **cboese said:**
> Hello!
I try to change the sort order and found some documantation about LC_* (esp.: LC_COLLATE and LC_CTYPE)

Is it possible to have a C-like sort order (case-insensitive) and still have the hidden files (.*) sorted first?
When I use LC_COLLATE=C it ignores the leading "."-sign and sorts the files according to the next character (which I dont want).
Is this possible and when yes, how?
I would appreciate any hints and urls on this :-)

greetings
         cboese

---

### Post by Jim Danner on 2010-05-13
> **cboese said:**
> When I use LC_COLLATE=C it ignores the leading "."-sign and sorts the files according to the next character (which I dont want).
Oh, actually, what cboese says here is not true for me. With the LC_COLLATE environment variable set to "C", the hidden files are sorted before the other ones.

I still don't understand why *sort* and *ls* were configured to ignore the leading dots in the first place, but now that I've done ```
sudo echo "LC_COLLATE=C" >> /etc/environment
```the problem is solved, anyway.

---

