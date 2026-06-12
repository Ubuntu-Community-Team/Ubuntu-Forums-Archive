---
title: "Command line help for renaming many files at once"
date: 2008-07-27
forum: General Help
---

### Post by mwade on 2008-07-27
ello,

I am trying to rename a LARGE number of files in one dir and have the new file keep a part of their name.  For instance I have about 300 files named something like this:

foo.00
foo.01
foo.02
foo.03

I want to change their name to:

foobar.00
foobar.01
foobar.02
foobar.03

I think you get the idea.  I have gone over the man page and can't find a solution.  I obviously do not want to rename one by one.

Thanks

---

### Post by brian_p on 2008-07-27
> **mwade said:**
> ello,

I am trying to rename a LARGE number of files in one dir and have the new file keep a part of their name. 

```
man rename
```

Ideal for what you want to do.

---

### Post by ryanhaigh on 2008-07-27
I'm not on my ubuntu computer at the moment to try and come up with the bash script required to do this but I do have a suggestion. Assuming this isn't a server and you have a GUI installed you can use a program called pyrenamer to do what you want.

[apt://pyrenamer]("apt://pyrenamer")

It's a great tool to have available particularly for instances such as this where a bash script, while more than capable, is probably not warranted for one time use.

---

### Post by ghostdog74 on 2008-07-27
> **mwade said:**
> ello,

I am trying to rename a LARGE number of files in one dir and have the new file keep a part of their name.  For instance I have about 300 files named something like this:

foo.00
foo.01
foo.02
foo.03

I want to change their name to:

foobar.00
foobar.01
foobar.02
foobar.03

I think you get the idea.  I have gone over the man page and can't find a solution.  I obviously do not want to rename one by one.

Thanks

Its always good to learn a bit of shell scripting. What happens when rename or pyrenamer or whatever tools you need are not available?
```

for files in *bar*
do
 mv "$files" "${files/bar/}"
done

```
see my sig for learning bash links

---

### Post by sengines on 2008-07-27
look for gprename in synaptic

---

### Post by kaibob on 2008-07-27
I'm a noob at this, but I came up with the following based on posting 3 in the referenced thread. TRY IT WITH SOME TEST FILES FIRST.

```
for FILES in foo.* ; do 
newfile=${FILES/foo/foobar}
mv "$FILES" "$newfile"
done
```

[http://ubuntuforums.org/showthread.php?t=845455&highlight=script+rename](http://ubuntuforums.org/showthread.php?t=845455&highlight=script+rename)

---

### Post by kaibob on 2008-07-27
> **ghostdog74 said:**
> Its always good to learn a bit of shell scripting. What happens when rename or pyrenamer or whatever tools you need are not available?
```

for files in *bar*
do
 mv "$files" "${files/bar/}"
done

```

Ghostdog74,

I wrote my posting without seeing yours. In fact, the posting I referenced in my thread was yours.

Anyway, I'm new at this and wondered why the line of your script as shown below would work because the source files do not have "bar" in them:

```
for files in *bar*
```

kaibob

---

### Post by ghostdog74 on 2008-07-27
no it will not work if there's no "bar" in your file names. I misread your requirement, so 
```

for files in foo.* 

```
should be correct.

---

