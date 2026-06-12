---
title: "Some questions"
date: 2008-07-19
forum: General Help
---

### Post by RATM_Owns on 2008-07-19
How would you go about adding some lines into a file without overwriting any existing contents?
Specifically, I want to add these to lines to $HOME/.bashrc :
> export DEVKITPRO=$HOME/devkitPro
export DEVKITPPC=$DEVKITPRO/devkitPPC
(Yes, it is to set up a Wii homebrew development environment)

And if possible (not really needed), a get key press thing.

---

### Post by coffeecat on 2008-07-19
> **RATM_Owns said:**
> How would you go about adding some lines into a file without overwriting any existing contents?
Specifically, I want to add these to lines to $HOME/.bashrc :

Simply open gedit (Applications > Accessories > Text Editor), open ~/.bashrc with it and - um - edit the text, and then save. ~/.bashrc is owned by you so there's no problem editing it.

> **RATM_Owns said:**
> And if possible (not really needed), a get key press thing.

I don't follow you. Can you explain?

---

### Post by RATM_Owns on 2008-07-19
Oh. Oops. I forgot one thing, I want to have those in a bash script. That's what I meant.

Since echo or cat (text) > ~/.bashrc overwrites the entire file.

---

### Post by coffeecat on 2008-07-19
> **RATM_Owns said:**
> Oh. Oops. I forgot one thing, I want to have those in a bash script. That's what I meant.

I could see you were an experienced user. I must admit I hesitated before telling you to use a text editor. :lol: I'm sorry. A bash script is a bit beyond me. Good luck in your search.

---

### Post by Barrucadu on 2008-07-19
This will do the job:
```
echo "blah" >> filename
```

The ">>" appends the text to the file.

---

### Post by RATM_Owns on 2008-07-19
Thanks. Exactly what I was looking for.

@coffeecat
[http://youtube.com/watch?v=SaZJFWOEzrc](http://youtube.com/watch?v=SaZJFWOEzrc)
Are You Experienced?

(Sorry, just came to mind xP )

---

