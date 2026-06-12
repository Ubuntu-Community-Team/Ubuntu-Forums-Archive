---
title: "how do you redirect a cat/grep output into middle/specific spot of an exisiting file?"
date: 2008-11-28
forum: General Help
---

### Post by fooey on 2008-11-28
I have a html file that has some lines that are too long for my current screen, and I want to add them into another html file. I can't copy paste manually so I was going to grep/cat it out & append it (yes i know how to append) it into the middle of the other html file.

I know how to # the nonempty lines with cat output of course. So is there a way to take certain #'s & append em in the middle(specific spot) of another file?
Same question w/ grep?

Is there an easier way to do this maybe?

 :-?

---

### Post by jpeddicord on 2008-11-28
No, not really. What you could do is split the HTML file into a header and footer, and then cat them all together in the end. For example:

header.html:
[HTML]<html>
<head><title>Title!</title></head>
<body>
Results:[/HTML]

footer.html:
[HTML]</body></html>[/HTML]

And then you could do something like this:
```
cat header.html textlog footer.html > fullpage.html
```where textlog is the file with the information you want to put inside the final HTML document.

---

### Post by fooey on 2008-11-28
yeah. could do it that way. thx

---

### Post by bodhi.zazen on 2008-11-28
You do not need to pipe cat to grep, just use grep.

I am not certain exactly what you are doing, just take a look at the grep man pages

grep -A 

grep -B

and regular expressions

You can use egrep if you prefer.

If you know the line numbers you can head / tail or just use grep with a large -A or -B .

---

### Post by fooey on 2008-11-29
Huh? Yeah I know I don't need to pipe cat to grep. Maybe I confused you with what I was trying to say.

Thanks for the reply though :)

---

### Post by bodhi.zazen on 2008-11-29
There is no need to 

cat file | grep foo > output.txt

just

grep foo file > output.txt

---

### Post by fooey on 2008-11-29
> **fooey said:**
> huh? Yeah i know _**i don't need to**_ pipe cat to grep.

 " "

---

### Post by jpeddicord on 2008-11-29
> **fooey said:**
> " "

lol... let's blame it on the weekend.

---

