---
title: "[SOLVED] Hardy (8.04) and Firefox 3"
date: 2008-07-30
forum: General Help
---

### Post by nathanv117 on 2008-07-30
After install of Firefox, when I bring up Firefox, it does not bring up any web page. I see it starting tin the task bar and dies.

I am able to use thunderbird and evolution mail systems.

Any idea what to look for?

Thanks

---

### Post by dexter.deepak on 2008-07-30
try to see, if it works in safe mode :
```
firefox --safe-mode
```

---

### Post by gvartser on 2008-07-30
Sometimes it can happen that your Firefox settings folder gets corrupt. The solution is to remove the old "~/.mozilla" directory and then restart firefox. (The directory is automatically re:created.) 

**NOTE!**
All bookmarks and other saved settings will be gone. *(But you can always get them back from the backup you made of your .mozilla dir)*

**1) Make sure Firefox is not running.**

**2) Make a backup of you old firefox settings folder "~/.mozilla"**
```
mv ~/.mozilla ~/.mozilla.bck
```

**3) Start Firefox again.**

**4) Done.**

Good luck,
/g

---

### Post by nathanv117 on 2008-07-30
Tried this. Problem still continues. Where id this .mozilla dir located?
Do you need any further info?

will try firefox --safe-mode also and let you know.

Thanks to you both.

---

### Post by lukjad on 2008-07-30
.mozilla is located in your Home folder. It is a hidden file (because of the "." in front of the file name). To see it you can to one of two things.

1) Go to the Home folder and press Ctrl+H. The file should appear.

2) Go to Application->Accessories->Terminal and since you are already by default put into the Home folder type **ls -a**. The file can will then be listed.

---

### Post by nathanv117 on 2008-07-30
> **gvartser said:**
> Sometimes it can happen that your Firefox settings folder gets corrupt. The solution is to remove the old "~/.mozilla" directory and then restart firefox. (The directory is automatically re:created.) 

**NOTE!**
All bookmarks and other saved settings will be gone. *(But you can always get them back from the backup you made of your .mozilla dir)*

**1) Make sure Firefox is not running.**

**2) Make a backup of you old firefox settings folder "~/.mozilla"**
```
mv ~/.mozilla ~/.mozilla.bck
```

**3) Start Firefox again.**

**4) Done.**

Good luck,
/g



I did something wrong. Tried again. Firefox worked.
Thanks

---

### Post by nathanv117 on 2008-07-30
> **dexter.deepak said:**
> try to see, if it works in safe mode :
```
firefox --safe-mode
```



This also worked.

Thanks

---

### Post by billgoldberg on 2008-07-30
Mark thread as solved please.

---

