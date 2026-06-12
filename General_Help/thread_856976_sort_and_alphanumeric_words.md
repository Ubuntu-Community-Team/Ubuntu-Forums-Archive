---
title: "sort and alphanumeric words"
date: 2008-07-12
forum: General Help
---

### Post by samrat1985 on 2008-07-12
Hello people
	I cannot use 'sort command' effectively when using
it on alphanumeric words. 

Ex. I have three files HL_1.html, HL_2.html, HL_10.html 
and I want to merge them in sequence into one file HL-ALL.html.

$ cat `ls -1 | sort -g` > HL-ALL.html

Yet this doesn't work. I have read in an ebook  "Unix Power Tools" 
that this is a limitation  of sort command when using alphanumeric 
words. So is there a way around it? or am I missing something?

PS: I have limited web access & am being charged on my neck to use the internet.
Please keep the thread alive as I can only be online for 1 hr daily.

---

### Post by jonlemur on 2008-07-12
This [site]("http://www.unix.com/shell-programming-scripting/30614-sort-command-alphanumeric.html") seems to have just what you're looking for.  If they all begin with HL_ you should be able to sort them with ```

cat `ls -1 | sort -k1.4n` > HL-ALL.html
```  
From the above site, this would sort from the 4th character in the first field treating it as numeric.

---

### Post by samrat1985 on 2008-07-17
Thanks man, i have been trying this for long time. Thank again

---

