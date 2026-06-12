---
title: "Quick sed question"
date: 2008-09-20
forum: General Help
---

### Post by mcai8sh4 on 2008-09-20
Just a quick question, this has been confusing me for a while.
(and I am still learning sed)

Say I run
```
id3 -l file_name | grep Title
```
I get returned
```
Title  : Through The Fire And Flames     Artist: Dragonforce
```

I can make this nicer using
```
id3 -l file_name | grep Title | sed -e s/Title\ *:\ // -e s/\ *Artist:/,\ by/
```

BUT if we just concentrate on removing the title part, the way I see it I should just be able to remove all things before ':' eg
```
... sed -e s/.*:// 
```
But this removes everything upto the second (Artist: ) ':' leaving just Dragonforce

I suppose what I'm asking is how do I remove al the characters up to and including the first instance of ':'

Any help, explanation would be most appreciated.

Thanks for your time.

Steve

This isn't the only example I want to know this for - this method would be useful to me for some other things. My question could've been easier if I'd just asked "How do I use sed to remove everything before the first occurence of ':' (or '$' '\' etc)?"

---

### Post by squaregoldfish on 2008-09-20
By default, regular expressions are 'greedy', which means each term will match as much as it can while still keeping an overall match. Since there are two colons in your string, the '.*:' portion of your regex will match all the way up to the second colon.

Depending on your regex parser, there may be ways to insist that your expression isn't greedy. I don't know if this is possible for sed (others may be able to help there), but since you're looking for the first colon, you can do the following:

```
sed -e s/[^:]*://
```

The [^:] portion means 'match any character that's not a colon'. Consequently, the above expression will match a whole bunch of characters that aren't colons, followed by a colon. This will make sure the regex doesn't run past the first colon.

Hope this helps, and also that my explanation is vaguely understandable.

Steve.

This works for the afterthought case as well :)

---

### Post by mcai8sh4 on 2008-09-20
Squaregoldfish: Thanks, works a treat AND excellant explanation, really helps.

Many thanks for the assistance.

Going back to my initial example...

To remove the '    Artist:' part, it's clear what I've done.
I can improve this with 
```
... -e s/\ *[Aa-Zz]*:/,\ by/ 
```

but why can I not use [:alpha:] or [:alnum:] - does this only work with certain versions or am I just missing somthing. (it seems to remove random characters)

EDIT - the 'random characters' are not really that random... if I use [:alnum:] it removes (or substitutes would be a better word) :,a,l,n,u,m 
so does this mean there are no predefined character classes (I should just stick with [Aa-Zz] )


Thanks again

---

### Post by squaregoldfish on 2008-09-20
You're spot on - the :alpha: and :alnum: are special tags that some regex parsers may understand (never seen them myself), but sed only thinks they're the characters you want to remove. I've learned that it's easier to stick with the basics at all times - that way you don't get confused when you switch to a different regex parser.

Steve.

---

### Post by mcai8sh4 on 2008-09-20
Great stuff, I'm getting to know enough that makes it useful now. Thanks fot the help.

Final one... suppose I want to print only that part matching the expression.

I read if I did
```
sed -n -e /Title/p 
```
it should print 'Title' (no use I know but /[Aa-Zz]*:/p or more complex expression could be useful)

Why do I get the full line printed - again I'm guessing it may be a version thing. Is there a way to print just things matching the expression?

Steve

---

### Post by ghostdog74 on 2008-09-20
when doing string manipulations, its easier to use fields and field delimiters. If you look at your output, you can see ":" is a good candidate for a field delimiter
```

id3 -l file_name | awk -F":" '/Title/{ print $2}' file #this will print second field

```
use $2, $3 and so on to get each field. Unless your string operation is very complex, otherwise, KISS.

---

### Post by mcai8sh4 on 2008-09-20
HAha, I knew awk would pop up sooner or later - I've only VERY briefly look at awk.

Thanks for all the help, 

Time for food then 'man awk' :)

cheers

---

### Post by bingoUV on 2008-09-20
> **ghostdog74 said:**
> when doing string manipulations, its easier to use fields and field delimiters. If you look at your output, you can see ":" is a good candidate for a field delimiter
```

id3 -l file_name | awk -F":" '/Title/{ print $2}' file #this will print second field

```
use $2, $3 and so on to get each field. Unless your string operation is very complex, otherwise, KISS.

Going with your KISS philosophy, cut is even better. On my system, it is a 44kB binary, as compared with the 332kB for awk. Library dependencies are same.
```

id3 -l file_name | cut -d":" -f 2-

```

The above will print everything after the first colon, :

---

### Post by squaregoldfish on 2008-09-20
ghostdog's suggestion will get you close, but you end up with the word Artist on the end of your title. However, a bit of monkeying with the field specifier to awk will do the trick:

```
awk -F" *[Aa-Zz]*: " '{print $2}'
```

for the title and 

```
awk -F" *[Aa-Zz]*: " '{print $3}'
```

for the artist.

Because we're splitting on characters and colons, the first field will be the word Title, so we need fields 2 and 3.

The addition to the field specifier are:

[Aa-Zz]*  As you had it before, this matches the word before the colon, and so eliminates it from the field when you come to print it.

The ' *' and ' ' around the characters and colon just get rid of any spare whitespace.

So your full line will end up being:

```
id3 -l file_name | grep Title | awk -F" *[Aa-Zz]*: *" '{print $2 ", by " $3}'
```

Sorry to nick your idea ghostdog, but I saw an opportunity to learn something :)

---

### Post by ghostdog74 on 2008-09-20
> **bingoUV said:**
> Going with your KISS philosophy, cut is even better. On my system, it is a 44kB binary, as compared with the 332kB for awk. Library dependencies are same.
```

id3 -l file_name | cut -d":" -f 2-

```

The above will print everything after the first colon, :
i don't use id3, so i don't know what the output is like. If it has many lines of output and OP wants to get the line with "Title", then awk is more suitable as it greps for patterns as well. awk can do much more than just one liners.

---

### Post by ghostdog74 on 2008-09-20
> **squaregoldfish said:**
> 
```
id3 -l file_name | grep Title | awk -F" *[Aa-Zz]*: *" '{print $2 ", by " $3}'
```

like i said, awk is not merely for one liners. it can do more, such as the work of grep. (and sed/wc/tr/cat and many more)
```

id3 -l file_name | awk -F"..." '/Title/{ print .... }'

```

---

### Post by mcai8sh4 on 2008-09-20
This is a great education for me - thanks everyone!

Whilst my id3 exmple was just a simple way to show the type of thing I wanted, I had other things in mind. Since the initial problem was solved for me, I've really started playing around.

Staying with the id3 example... since not many people may be familiar with the output....
```
 $ id3 -l faf
faf:
Title  : Through The Fire And Flames     Artist: Dragonforce                   
Album  : Inhuman Rampage                 Year: 2006, Genre: Other (12)
Comment:                                 Track: 1

```

There's an example of the output I was playing with. As with many things using CLI I realise there are many ways to skin a penguin, so all the various examples are most helpful to me.

If I wanted to change the filename of my file 'faf' to 'Artist - Title', 
in theory I could use somthing along the lines of
```
new_name=$(id3 -l file_name | grep Title | awk -F" *[Aa-Zz]*: *" '{print $3 " - " $2}'); cp faf $new_name 
```

Obviously I'd throw this into a little bash script.
I know this may seem like a waste of time, I use pointless examples to help me learn.

Looks like I may have to spend more time with awk - looks useful for the type of things I do!!

Cheers, Steve

---

### Post by ghostdog74 on 2008-09-20
> **mcai8sh4 said:**
> This is a great education for me - thanks everyone!

Whilst my id3 exmple was just a simple way to show the type of thing I wanted, I had other things in mind. Since the initial problem was solved for me, I've really started playing around.

Staying with the id3 example... since not many people may be familiar with the output....
```
 $ id3 -l faf
faf:
Title  : Through The Fire And Flames     Artist: Dragonforce                   
Album  : Inhuman Rampage                 Year: 2006, Genre: Other (12)
Comment:                                 Track: 1

```

There's an example of the output I was playing with. As with many things using CLI I realise there are many ways to skin a penguin, so all the various examples are most helpful to me.

If I wanted to change the filename of my file 'faf' to 'Artist - Title', 
in theory I could use somthing along the lines of
```
new_name=$(id3 -l file_name | grep Title | awk -F" *[Aa-Zz]*: *" '{print $3 " - " $2}'); cp faf $new_name 
```

Obviously I'd throw this into a little bash script.
I know this may seem like a waste of time, I use pointless examples to help me learn.

Looks like I may have to spend more time with awk - looks useful for the type of things I do!!

Cheers, Steve

you can do everything in awk. Since "Artist" name is at the last field
```

awk -F":" 'BEGIN{
 dq="\042" #code for double quotes
}
/Artist/{ 
 # trim spaces for last field
 gsub( /[[:space:]]/ , "" ,$NF ) 
 cmd = "mv "dq FILENAME dq " "dq $NF dq
 print cmd
 # system(cmd) #uncomment to use
}'


```

---

