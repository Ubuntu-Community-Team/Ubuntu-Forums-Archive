---
title: "sed end of line help"
date: 2008-07-11
forum: General Help
---

### Post by spudgunman on 2008-07-11
I need some help with sed I have a list like this...

/blog
/photo
/img

and I want to make this

[http://www.example.com/blog](http://www.example.com/blog)
[http://www.example.com/photo](http://www.example.com/photo)
[http://www.example.com/img](http://www.example.com/img)

my code

```
DOMAIN=www.example.com

sed -i '/s/ \// <a href "DOMAIN/g' URL.txt
sed -i "/s/DOMAIN/http:\/\/$DOMAIN\//" URL.txt
sed -i '/s/$/">Link<\/a>/' URL.txt
```

but i get this

<a href "http://www.example.com/blog
">link</a> <br>

why do I see the ">link</a> <br> on a new line?

---

### Post by ghostdog74 on 2008-07-11
```

while read line
do
 printf "<a href \"http://www.example.com%s\">link</a> <br>\n" $line
done < "urlfile"

```

---

### Post by spudgunman on 2008-07-11
thanks for the reply 

to be a little more detail, sorry


i actually have this 


BlahBlahBlah /blog
BlahBlahBlah /img

and need to change that which is why I was using sed to read and write will chop chop the whole line not just add to the word.

---

### Post by ghostdog74 on 2008-07-12
```

while read a b
do
 printf "<a href \"http://www.example.com%s\">link</a> <br>\n" $b
done < "urlfile"

```
please read the bash  manual in my sig for more bash knowledge

---

### Post by dracayr on 2008-07-12
sed -i "s/ \/\(.*\)/<a href=\"http:\/\/www.example.com\/\1\">link<\/a> <br>/"

should work

dracayr

---

### Post by spudgunman on 2008-07-12
> **dracayr said:**
> sed -i "s/ \/\(.*\)/<a href=\"http:\/\/www.example.com\/\1\">link<\/a> <br>/"

should work

dracayr

awesome the \1 for the use of the buffer was what I couldn't figure out - quite simple now that I see it. thanks.

---

