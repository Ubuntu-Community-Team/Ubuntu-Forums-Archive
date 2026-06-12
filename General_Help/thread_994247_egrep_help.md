---
title: "egrep help"
date: 2008-11-26
forum: General Help
---

### Post by bobfeltss on 2008-11-26
I am trying to do a simple thing with egrep, and I can't get it right.  I have a 10-15 Mb logfile that I need to extract data from.  I need only a couple of line items per record from this log file and here is the failure.


I try:

egrep (User-Data|Record-Date|Record-Time) Sourcefile.txt > Result_file.txt.  

What I get is a "Syntax error near unexpected token '('." If I drop the parens and only try quoting the regexp I get a "Record-Date" : command not found error, even if I include NO whitespace around the | character. Any iteration of quotes doesn't help. (Such as "User-Name"|"Record-Date" or "User-Name|Record-Date" Etc.)

I have used txt2regex to check my syntax, but it provides the same syntax that I have already tried for egrep...

Using the | (or operator) is simply not working for me. What am I doing wrong?

Any help is appreciated!
Bob

---

