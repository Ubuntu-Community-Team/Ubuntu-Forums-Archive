---
title: "unrar Error unknown option? please help ASAP"
date: 2008-07-21
forum: General Help
---

### Post by rafirf on 2008-07-21
okay i have unrar before in terminal, unrar is installed correctly and fully. but this time, i navigated to the directory of the .rar and when i use unrar i get an error. which i can't seem to solve, can you help me?

This is what i typed;
batool@home-computer:~/Downloads$ unrar Axis.Of.Evil.Comedy.Tour[ENG]DvDrip - zeroXTC.rar

this is the message terminal spit out:
ERROR: Unknown option: batool@home-computer:~/Downloads$ 

what is wrong, how can i unrar the file and watch the video, please help, thank you.

---

### Post by sisco311 on 2008-07-21
try:
```
unrar -x Axis.Of.Evil.Comedy.Tour[ENG]DvDrip - zeroXTC.rar
```
or right click on the file in the file browser and select 
the *extract here* option.

---

### Post by aminalid on 2008-11-23
I have the same error when i try to archive files using
```

rar -a archiveName pathToFolder

```

it always gives me 

```
ERROR: Unknown option: user@host:/currentPath/$
```

any ideas?

---

### Post by bobthecheese on 2011-04-06
OK, this thread is heaps old, but here's the solution.

```

rar a archiveName.rar pathToFolder

```

The key is that rar doesn't take "a" as a standard flag. ("-a" causes an error, "a" is fine).

---

### Post by aminalid on 2011-04-06
I don't remember what i was trying to do back then, but thanks!

---

