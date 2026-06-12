---
title: "Sorting RSS feeds ( so I can skip most of them )"
date: 2008-09-06
forum: General Help
---

### Post by arsenic23 on 2008-09-06
I have a setup where I can sometimes receive 1000+ RSS feeds a day, but I only need to see 1-4 of them, and I absolutely can't miss those few.  I've been installing and uninstalling RSS readers all day, but I haven't found one that will let me auto-delete, filter, or otherwise sort the contents I'm receiving.  I don't have a ton of experience with RSS feeds, because untill yesterday, I had no use for them.

SO, does anyone know of a feed reader that would do what I'm looking for, **or** does anyone know of a feed reader that stores it's information in easy to manage plain text that I could grep through with a daily script?

*( I have a terrible feeling that one (or more) of the programs I've already messed with does what I need and I just missed it. )*

---

### Post by whitethorn on 2008-09-06
> **arsenic23 said:**
> I have a setup where I can sometimes receive 1000+ RSS feeds a day, but I only need to see 1-4 of them, and I absolutely can't miss those few.  I've been installing and uninstalling RSS readers all day, but I haven't found one that will let me auto-delete, filter, or otherwise sort the contents I'm receiving.  I don't have a ton of experience with RSS feeds, because untill yesterday, I had no use for them.

SO, does anyone know of a feed reader that would do what I'm looking for, **or** does anyone know of a feed reader that stores it's information in easy to manage plain text that I could grep through with a daily script?

*( I have a terrible feeling that one (or more) of the programs I've already messed with does what I need and I just missed it. )*

Hi I use Liferea Feed Reader, it has an option to search through all the feeds, this might be what ur looking for.  It should be in Synaptic.

---

### Post by arsenic23 on 2008-09-06
> **whitethorn said:**
> Hi I use Liferea Feed Reader, it has an option to search through all the feeds, this might be what ur looking for.  It should be in Synaptic.

Hmm... I reinstalled liferea, and it is a nice setup, but I need to search for about 70 things at once, and it doesn't seem to be able to do that.  The horrbile thing is that I just need one line of text out of every 400 posts or so.  It would more then likely be easier if I could just find a feed reader that saved in plain text and scripted something to search and display the data I need and then delete the original rss posts.

---

### Post by pbotros1234 on 2008-09-06
If you can find a feed reader that would save its output into some text file, you could just:

```
cat text-file | grep (whatever you want to search for)
```

Not sure if this is what you're looking for, sorry :confused:

---

### Post by arsenic23 on 2008-09-06
> **pbotros1234 said:**
> If you can find a feed reader that would save its output into some text file, you could just:

```
cat text-file | grep (whatever you want to search for)
```

Not sure if this is what you're looking for, sorry :confused:

Yeah, that was what I was getting at, but I don't know/can't find an RSS reader that saves its data as plain text.  Also I'd need the reader to do this automatically.  hmmm, I wonder if there is an RSS library for python...  I really do know next to nothing about RSS feeds.

---

