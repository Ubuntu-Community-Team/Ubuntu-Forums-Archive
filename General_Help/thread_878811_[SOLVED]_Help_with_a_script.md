---
title: "[SOLVED] Help with a script"
date: 2008-08-03
forum: General Help
---

### Post by jmvidalvia on 2008-08-03
Hi!
I need to move all files to a new directory, avoiding moving directories
I am able to find all files with:
```
find . -maxdepth 1 -type f
```
My problem appears when I want to add the exec command. For instance, I do:
```
find . -maxdepth 1 -type f -exec mv '{}' \; files\
```
But there's something wrong..:(
I don't know where and how to point the destination folder "files\"
Thanks a lot!:)

---

### Post by sisco311 on 2008-08-03
```
find . -maxdepth 1 -type f -exec mv {} ./files/ \;
```assuming ./file is the directory where you want to 
move the files.

---

### Post by Yannick Le Saint kyncani on 2008-08-03
> **sisco311 said:**
> ```
find . -maxdepth 1 -type f -exec mv {} ./files \;
```
assuming ./file is the directory where you want to 
move the files.

```
find . -maxdepth 1 -type f -exec mv {} ./files/ \;
```

Because if you omit the trailing / and "files" is not a directory or does not exist, then you loose all your files but one, because they each get renamed to a file named "files" one after each other, overwriting themselves.

---

### Post by jmvidalvia on 2008-08-03
Works!
Thanks a lot!:)

PS: by the way, what is the meaning of the end of the script "\ ;"?

---

### Post by sisco311 on 2008-08-03
> **jmvidalvia said:**
> Works!
Thanks a lot!:)

PS: by the way, what is the meaning of the end of the script "\ ;"?

separates one mv command from the next.

---

### Post by jmvidalvia on 2008-08-03
Thanks.
:)

---

### Post by sisco311 on 2008-08-03
If you don't have more questions, then please mark the thread SOLVED using the Thread Tools link at the top right of the first post.

---

### Post by Claus7 on 2008-08-03
> **sisco311 said:**
> separates one mv command from the next.

Hello,

the "\;" has two characters which have the following meaning :
[LIST]
[*]the "\" is the escape character 
[*]the ";", which is the semicolon and is the command separator
[/LIST]

Here we want to escape the semicolon so that it is not interpreted by bash but is given as an argument to find.
In the 
```
find . -maxdepth 1 -type f -exec mv {} ./files \;
```
command, it denotes where the arguments of the exec command end. 
The escape character before a special one, is used in order not the later to be expaned by bash, yet to be used by the command and the corresponding operation. For example here the ";" is the end separator of the parameter exec. 
Also in combination to some characters, example "\t", they give an entirely different meaning. Here "\t" means tab. So for bash to understand the tab, t should have backslash in front. So it "escapes" t as to be recognised as tab.

There is also ";;" as well. Just FYI:
[http://snippets.dzone.com/posts/show/2692](http://snippets.dzone.com/posts/show/2692)
[http://www.network-theory.co.uk/docs/bashref/EscapeCharacter.html](http://www.network-theory.co.uk/docs/bashref/EscapeCharacter.html)
[http://www.gnu.org/software/bash/manual/bashref.html](http://www.gnu.org/software/bash/manual/bashref.html)
[http://en.wikipedia.org/wiki/%3B](http://en.wikipedia.org/wiki/%3B)

Regards!

---

