---
title: "removing &quot;link to&quot; from symbolic links"
date: 2008-09-03
forum: General Help
---

### Post by Creat on 2008-09-03
Hey

I'm sure the answer to this question is really basic but I can't figure it out. You know when you drag and drop a file or a folder and you hold crtl+alt then nautilus creates a symbolic link. However, it puts the string "Link to" in front of the original name of the file. Is there a way of disabling that? I mean that the name of the link is exactly the same as the original file/folder name. When I have only a few to rename manually that's not a big deal, but this time I have a good hundred to do and I don't feel like doing by hand...

Thanks for your time, it will probably save mine.

---

### Post by anotherdisciple on 2008-09-03
Wow.... I'm not sure how to do that, but I have an idea on how to rename a huge batch of them... Try this on just one file and see if it works.

```
&dollar; rename Link\ to\  "" Link\ to\ *
```

If I am thinking right... that will find all the find the files that start with "Link to " and rename them to only what is after "Link to "

I'm not at a linux computer... so I can't test this!!!! Can someone confirm this for me?

---

### Post by anotherdisciple on 2008-09-03
Okay... I've done some reading... and I'm still not at my ubuntu computer, but you should be able to middle click the file and drag it to another folder and click "Link Here". That will name it the same as the original. However, that won't work if you drag it to the same folder as the original file, because you can't have two files of the same name in the same directory so it if forced to add "Link to " before the file.

If you don't have a middle click button, just right & left click at the same time will emulate a middle click.


Hope that works for you!

---

### Post by Creat on 2008-09-03
Hey,

Thanks for the reply.

I think you meant:
```
rename 's/^Link to//' Link\ to\ *
```

but in fact I was thinking more about a global solution that would avoid me to run this command every time I want to make a symbolic link.

---

### Post by Creat on 2008-09-03
I just saw your other reply about the middle click option... unfortunately it still puts this 'Link to' in front of the name... Thank you though, for taking time to look at this.

---

### Post by anotherdisciple on 2008-09-03
It doesn't work???? Sheesh... now you have me wanting to know for myself. I almost never make symbolic links, but I just want to know how to do this for the sake of knowing how to do this.

---

