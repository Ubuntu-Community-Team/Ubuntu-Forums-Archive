---
title: "changing soource list"
date: 2008-11-26
forum: General Help
---

### Post by steve984 on 2008-11-26
I screwed up my source list and the repositories woon't read.  I know what lines to delete but when I open it thhru the file system it says I don't have permission.  I used nautilus in hardy but I can't download it(or anything else. does anyone know the cammand line to open up the source list in teerminal. thanks

---

### Post by steve984 on 2008-11-26
I solved it

---

### Post by tang0delta on 2008-11-26
open a terminal and type 

```
sudo gedit /etc/apt/sources.list
```

you'll be prompted for your admin password. The lines you want to delete are probably at the bottom of the file 

Hope I understood what you were looking for :P

--
tang0delta

---

### Post by nothingspecial on 2008-11-26
Glad you solved it.

When you solve something even if it`s on your own with no help, it`s kind of nice if you say how you`ve done it. That way someone else searching about the problem will know what to do if they come across your thread.

Also it`s nice if you mark your thread as solved so that people can see that the solution is contained within your thread. And people just spending their 15mins a day trying to help don`t have their time wasted reading a thread that is already solved.

No offence meant, just thought I`d mention it.:)

---

