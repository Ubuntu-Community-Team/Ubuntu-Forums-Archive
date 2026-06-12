---
title: "Rename command confusion"
date: 2008-11-25
forum: General Help
---

### Post by detroit/zero on 2008-11-25
I'm afraid after reading through the rename man page and the help file, I'm still completely lost about how to make rename do what I want it to do. This is probably because of a complete lack of understanding about PERL..

I have a camera that for some reason saves it's pictures with a **.JPG **extension. I can't find anything on the camera to change this behavior, so until I do, I'm forced to use a rename command to make the extensions **.jpg** (lowercase) so mogrify commands will work on them (resizing, rotating, etc..)

Obviously, the rename command is what I want to use so I don't have to right-click each one in Nautilus and change them one-by-one, but I'm not sure how to put the command together. Something about all the front-/back-slashes and dollar signs throws me off.

Can someone:

[LIST=1]
[*]Show me how to structure a rename command that will change the extensions on a bunch of pictures in a particular folder from uppercase to lowercase.
[*]Point me in a good direction to learn about/read up on PERL as far as it relates to being used in the rename command.
[/LIST]
Thanks a million.

---

### Post by kaibob on 2008-11-25
You can accomplish what you want by entering the following in a terminal window:

```
for file in *.JPG ; do mv "$file" "${file/%JPG/jpg}" ; done
```

I have always found that the mogrify command will accept files with capitalized file extensions. For example, the following worked for me:

```
mogrify -resize 112x112 splash.JPG
```

---

