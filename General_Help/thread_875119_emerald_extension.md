---
title: "emerald extension"
date: 2008-07-30
forum: General Help
---

### Post by PCessna on 2008-07-30
Hey all,

Being a nuub to Compiz leaves me in question if or how to use this extension, emerald, for themes and what not.

If possible, how, Looking through settings didn't seem to help

Thanks
-PCessna

---

### Post by jimv on 2008-07-30
You need to install Emerald to use Emerald themes.  To do that, run this command in a terminal:

```
sudo apt-get install emerald
```

Then go to System > Preferences > Emerald Theme Manager and click Import to import your .emerald file.

If the window borders don't change after you install Emerald, then you need to start it.  You can do that by pressing alt+f2, and then typing

```
emerald --replace
```

You may need to add that command to System > Preferences > Sessions to get Emerald to run when you boot.

---

### Post by dexter.deepak on 2008-07-30
first of all install the emerald theme manager.
then install some of the available themes , through its GUI interface.
just google with "emerald themes" and you'll get a lot.

---

### Post by PCessna on 2008-07-30
What application should I choose to make emerald start upon boot up/ login besides the emerald --replace command.

---

### Post by PCessna on 2008-07-30
> **PCessna said:**
> What application should I choose to make emerald start upon boot up/ login besides the emerald --replace command.

never mind solved

---

### Post by steveneddy on 2008-07-30
> **PCessna said:**
> never mind solved

Please tell us what you did to solve the issue so someone else can benefit from your answer.

---

### Post by PCessna on 2008-08-06
> **steveneddy said:**
> Please tell us what you did to solve the issue so someone else can benefit from your answer.

Ah, good think I looked back.

Follow the steps about to solve the unknown emerald extension.

Once your theme is happy happy, 

System --> Preferences --> Sessions --> add

Name: Emerald
Command: emerald --replace

Now, every time you login or boot up, the emerald theme will be used, to reverse this, System --> preferences --> sessions --> find emerald, and uncheck, next login or reboot you'll be back to square 1

hope this helps some people :)

---

