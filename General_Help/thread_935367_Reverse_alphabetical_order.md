---
title: "Reverse alphabetical order"
date: 2008-10-01
forum: General Help
---

### Post by Talorgan on 2008-10-01
Does anyone know of software which will group words in reverse alphabetical order (not sure that's the right description).

I'm not looking to put "zebra" before "aardvark" but have each word assessed by its last letter first, followed by its second last etc.

So:

table
apple
watch
pencil
penny

You'll gather that I am studying suffixes.

---

### Post by blingo on 2008-10-01
Assuming you have the words in a words.txt
open a terminal,
go to the directory of words.txt
and write:

cat words.txt | rev | sort | rev > sorted.txt

this will create a sorted words file called
sorted.txt in the same directory.

---

### Post by blingo on 2008-10-01
P.S assuming that each line contains one word in the original file.

---

### Post by Talorgan on 2008-10-01
> **blingo said:**
> P.S assuming that each line contains one word in the original file.

It does

Many thanks

---

