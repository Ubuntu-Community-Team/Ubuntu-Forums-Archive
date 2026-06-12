---
title: "Search and replace text strings - multiple directories"
date: 2008-11-05
forum: General Help
---

### Post by KhipuX on 2008-11-05
Afternoon folks,

My head just can't take this this afternoon so I hope you can help me out.

I have two folders on my desktop. Inside each folder is a bunch of other folders and so on. In various folders I've got .html and .htm files everywhere. Now some clever guy decided to include some code in some of these files with an & character which should clearly be &amp;

I've got over 6500 files and I'm sure about 300 of them have the wrong code in. I have an exact string which is:

&l

which needs replacing with:

&amp;l

How do I do this from the linux command line? I'm not going through all these files and changing each one individually. I started with Bluefish's find and replace but then I discovered how many directories these people have programmed in and I just need to change the code. Any quick help would be appreciated.

---

### Post by KhipuX on 2008-11-05
Sorry, I forgot. I need to output a list of the changed files and their directories to a text file as well. That might make things just a little more complicated.

---

### Post by geirha on 2008-11-05
I think these two one-liners should do the trick. First one should recursively find all files ending with .html or .htm, then pipe it to grep to filter the ones that contain '&l':

```
find . -type f \( -iname "*.html" -o -iname "*.htm" \) -print0 | xargs -0 grep -l '&l'  > files_with_ampersand_l.txt
```

Now we have the list of files we need to change, so let's pipe that further to sed to replace all occurances of '&l' in those files with '&amp;l' :

```
find . -type f \( -iname "*.html" -o -iname "*.htm" \) -print0 | xargs -0 grep -lZ '&l' | xargs -0 sed -i 's/&l/\&amp;l/g'
```

---

### Post by ad_267 on 2008-11-05
You could also try regexxer from the repositories. It is a graphical tool that lets you view the changes before applying them if you like.

---

### Post by KhipuX on 2008-11-05
Guys, thanks so much. Both solutions are pretty good, you've just saved me a lot of time. I think there gonna have to invent a 'big thanks' option to the forum options.

---

