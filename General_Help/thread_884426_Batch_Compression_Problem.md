---
title: "Batch Compression Problem"
date: 2008-08-09
forum: General Help
---

### Post by aNgGaCKt on 2008-08-09
I want to do some batch compression using 7z in linux with terminal. When i'm still in M$ environment, i usually use

```
for %%i in * do 7za.exe a -tzip -mx9 "%%~ni.zip" "%%i" 
```

the "%%~ni.zip" expression is used in regards to prevent the filetype being include in the zipped filename

So, i'm trying to do the same in Ubuntu by using :

```
for i in *; do 7za a -tzip -mx9 "$~ni.zip" "$i"; done
```

But unfortunately, it failed to exclude the filetype and worse, it only create one zip file with the name ~ni.zip

if i wrote it like this :

```
for i in *; do 7z a -tzip -mx9 "$i.zip" "$i"; done
```

The progress done smoothly but it still included the filetype on the zipped file

Can anyone help me please? 

I hope this time someone will help me since all of my previous post is still goes unanswered :lolflag:

EDIT :
Naaah, nevermind again, solved it myself :P . I'm using this one to successfully remove the file type from the zipped name :)

```

for files in *
do
proses=`echo $files | cut -f1 -d.`
7z a -tzip -mx9 "$proses.zip" "$files"
done

```

---

