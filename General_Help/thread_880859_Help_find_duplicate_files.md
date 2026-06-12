---
title: "Help find duplicate files"
date: 2008-08-05
forum: General Help
---

### Post by digitalhead on 2008-08-05
I have imported thousands upon thousands of pictures from other computers and other family members. Apparently, there were several duplicates of some of these pictures. I was easily able to find the ones that f-spot renamed with "-1", "-2", "-3", and "-4" along with the basic Windows "Copy of..." renaming. How can I filter out the ones that are duplicates, but use different cases (ie: PH2100076.jpg and ph2100076.jpg). Normally, I would just do this manually, but there are thousands of pictures to deal with and I don't have the time or patience to do it manually.

Can anybody help me with a search syntax, find a utility, or a different method to get rid of these duplicates easily?

Thanks.

---

### Post by gaussian on 2008-08-05
Digikam (KDE photo management program) + kipi-plugins package would allow you to do this in Digikam.

---

### Post by HermanAB on 2008-08-05
Ugh...  I can feel your pain.

You should read up on the 'find' utility.  Between find, md5sum and sort, you should be able to get a list of filenames sorted by checksum.  Then you can look for duplicates in that list.

Find has the ability to recurse into a directory tree and call a utility or a script on each file in the tree.

Something like this:
```
find /photos -name \*.jp* -print -exec md5sum {} \;|sort>filelist
```

I haven't tried the above, but it may(!) do something like what you need - at least it should give you an idea.  Copy some files to a different spot and run your experiments there, before letting it go on the real data.

Cheers,

Herman

---

### Post by ghostdog74 on 2008-08-05
```

md5sum *.* |sort -u|awk 'x[$1]++'

```

---

### Post by ibuclaw on 2008-08-05
As much as I admire the elegance of it, what about the other file/s (as in the other duplicates)?
And hidden ones?

Shouldn't that be mentioned too?

There is an app called fdupes which can do this for you.

```
fdupes $PWD
```

[EDIT]
It also has a command argument to ignore empty files
```
fdupes -n $PWD
```
Regards
Iain

---

### Post by digitalhead on 2008-08-05
> **tinivole said:**
> As much as I admire the elegance of it, what about the other file/s (as in the other duplicates)?
And hidden ones?

Shouldn't that be mentioned too?

There is an app called fdupes which can do this for you.

```
fdupes $PWD
```

[EDIT]
Just tried out the Intrepid version, and it has a command argument to ignore empty files
```
fdupes -n $PWD
```
Regards
Iain

Thanks, this saved me a lot of time. This worked just about perfectly: ```
fdupes -r -d /home/digitalhead/Photos
``` Probably took an all day job and turned it into a 10 minute job for it to scan and for me to choose which ones to keep. Just too bad there isn't a syntax to automatically select ones to preserve, such as [capletter][capletter]######.[capext] or [capletter]#######.[capext] or automatically delete files with "-1" between the filename and extension or lower case filenames. Oh well, job is done in a matter of minutes rather than hours.

Now, what's the easiest way to update the f-spot database to remove the old files? Just delete ~/.gnome2/f-spot/photos.db and re-import without copying to ~/Photos, or is there an easier (quicker) way? It takes a long time to do the initial import of all these pictures.

---

### Post by digitalhead on 2008-08-05
For the others who replied to my question before tinivole...

> **gaussian said:**
> Digikam (KDE photo management program) + kipi-plugins package would allow you to do this in Digikam.

I know what DigiKam is. You also mentioned why I don't use it or have it installed. It's for KDE. Since I'm on dial-up internet, I don't want to take the time to download DigiKam, the KDE libraries, and the additional plugins just to get rid of duplicate files.

> **HermanAB said:**
> Ugh...  I can feel your pain.

You should read up on the 'find' utility.  Between find, md5sum and sort, you should be able to get a list of filenames sorted by checksum.  Then you can look for duplicates in that list.

Find has the ability to recurse into a directory tree and call a utility or a script on each file in the tree.

Something like this:
```
find /photos -name \*.jp* -print -exec md5sum {} \;|sort>filelist
```

I haven't tried the above, but it may(!) do something like what you need - at least it should give you an idea.  Copy some files to a different spot and run your experiments there, before letting it go on the real data.

Cheers,

Herman

I tried this and it came up with about 1/4 of the files or less. Of course, now that I think about it, it could have been because of the lowercase "*.jp*" part.

> **ghostdog74 said:**
> ```

md5sum *.* |sort -u|awk 'x[$1]++'

```

Exactly what does this do anyway?


That said, thanks to everybody for the help.

---

### Post by Confusatron on 2009-04-05
There is also a utility called fslint that does this with a nice GUI, ignoring upper/lowercase. I'm having the same issue, but I'm not sure how safe it is to delete the *-1.jpg files. Will that cause problems with F-Spot? There are several gigs of duplicates on my disk that I'd really like to remove...

---

### Post by digitalhead on 2009-04-05
> **Confusatron said:**
> There is also a utility called fslint that does this with a nice GUI, ignoring upper/lowercase. I'm having the same issue, but I'm not sure how safe it is to delete the *-1.jpg files. Will that cause problems with F-Spot? There are several gigs of duplicates on my disk that I'd really like to remove...

If it's a duplicate by the MD5 checksum, which is how a lot of programs would check, it would be perfectly safe to remove them. As for F-Spot, the most you would have to do rebuild its database, which it should do automatically when you start it after removing the duplicates.

---

### Post by Michael84 on 2009-04-05
> **digitalhead said:**
> I have imported thousands upon thousands of pictures from other computers and other family members. Apparently, there were several duplicates of some of these pictures. I was easily able to find the ones that f-spot renamed with "-1", "-2", "-3", and "-4" along with the basic Windows "Copy of..." renaming. How can I filter out the ones that are duplicates, but use different cases (ie: PH2100076.jpg and ph2100076.jpg). Normally, I would just do this manually, but there are thousands of pictures to deal with and I don't have the time or patience to do it manually.

Can anybody help me with a search syntax, find a utility, or a different method to get rid of these duplicates easily?

Thanks.
Does this [duplicate file finder]("http://www.moleskinsoft.com/duplicate-file-finder-1") help? It works for ma, at least...

---

### Post by digitalhead on 2009-04-05
I actually just used fdupes and it worked out pretty well. I've now switched to Kubuntu and Digikam has the capability built in. Thanks for the suggestion though.

---

### Post by Confusatron on 2009-05-01
Just a historical note for anyone who searches this issue in the future - F-Spot treats the ###-1.jpg files as the "original" files, and seems to just ignore what I would consider the original ###.jpg file. If you delete the ###-1.jpg files you may be in a world of hurt (or at least sql editing).

---

