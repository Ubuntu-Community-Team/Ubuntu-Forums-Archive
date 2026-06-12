---
title: "possible to somehow search a 600meg mysql database i have local?"
date: 2008-08-09
forum: General Help
---

### Post by srossnz on 2008-08-09
I have a 600meg database that I need to grab a few lines of code from.  The db is on my ubuntu desktop.  I tried renaming it to .txt opened it but the search would not work its just too big.  I have no linux skills, is there some sort of app i can use to search the db?  Like a local phpmyadmin that i can startup and simply load the db? Thanks!

---

### Post by Diabolis on 2008-08-09
You can filter the contents of a file with a combination of the commands **cat** and **grep**.

Example:
```
cat file.txt | grep apple
```

This will print out all the lines that contain the word "apple" in file.txt.

---

### Post by srossnz on 2008-08-09
> **Diabolis said:**
> You can filter the contents of a file with a combination of the commands **cat** and **grep**.

Example:
```
cat file.txt | grep apple
```

This will print out all the lines that contain the word "apple" in file.txt.

That sounds cool but I should have been more specific.  I had a vbulletin plugin that was accidentally deleted.  I know the block of code for it is somewhere in the 600meg db so I need to be able to search for example "sidebar" and then see that block of code to copy.  If i use the above method it may leave out blocks -but maybe this code you supplied can be made to show 50 lines before and after the keyword searched on?

---

### Post by Diabolis on 2008-08-09
Yes, you can:
```
cat file.txt | grep -B 25 -A 25  apple
```

grep is a powerful command:
```
man grep
```

---

### Post by srossnz on 2008-08-09
> **Diabolis said:**
> Yes, you can:
```
cat file.txt | grep -B 25 -A 25  apple
```

grep is a powerful command:
```
man grep
```

ok tried all that and couldn't find anything.  if i could get phpmyadmin running local and just open it but i dont think thats possible without also running mysql server etc ugh

---

