---
title: "complex bash variable"
date: 2008-08-18
forum: General Help
---

### Post by meg23 on 2008-08-18
I want to create a variable like this:

X=elinks [www.google.com/news|grep](www.google.com/news|grep) 'tech'

How would I create a complex variable like this?

---

### Post by spin2cool on 2008-08-18
```
$> abc="asdf fdsa 'qwerty'"
$> echo $abc
asdf fdsa 'qwerty'
```

What's the problem?  Are you looking for a way to make bash execute the string you're storing? That's easy too:
```
$> a="echo \"asdf\""
$> echo $a
echo "asdf"

#to run it:
$> $a
"asdf"
```

---

### Post by ghostdog74 on 2008-08-18
> **spin2cool said:**
> ```
$> abc="asdf fdsa 'qwerty'"
$> echo $abc
asdf fdsa 'qwerty'
```

What's the problem?  Are you looking for a way to make bash execute the string you're storing? That's easy too:
```
$> a="echo \"asdf\""
$> echo $a
echo "asdf"

#to run it:
$> $a
"asdf"
```

the method won't work for other commands, eg
```

# a="echo 1+2|bc"
# $a
1+2|bc
# eval $a
3

```

---

### Post by meg23 on 2008-08-19
I am trying to redirect the output of command, for instance 

elinks [www.google.com/news](www.google.com/news) -dump | grep 'tech'

 This command, if fulfilled, will output the string tech. I want the variable to become "tech". Then, I can set up something like this: 

if x='tech' ; then
command
fi

---

### Post by ghostdog74 on 2008-08-19
if its just one command you are going to execute once "tech" is found
```

elinks www.google.com/news -dump | grep 'tech' && command

```

---

### Post by koenn on 2008-09-27
stumbled upon this thread while looking for something else. - I know it's old but it looked like an interesting question ...

meg23: maybe this is what you had in mind ?
```

links=$(elinks www.google.com/news|grep 'tech')

## do things with all links together, eg show result of elink|grep statement
echo $links

## handle each link separately
for ITEM in $links; do
    #put stuff you want to do with each link here, e.g.
    echo "processing $ITEM"
    firefox $ITEM
done



```

---

