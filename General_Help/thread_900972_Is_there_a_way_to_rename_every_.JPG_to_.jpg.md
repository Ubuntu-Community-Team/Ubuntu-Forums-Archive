---
title: "Is there a way to rename every .JPG to .jpg?"
date: 2008-08-25
forum: General Help
---

### Post by Roasted on 2008-08-25
Photobucket, MySpace, and several other sites don't pick up the jpg extension when it's in all caps. Is there some kind of a script I can run to automatically rename every SINGLE picture on my computer to be lowercase?

I have 15,000 pictures, so renaming each one is simply out of the question. I'd rather eat glass than do that.

---

### Post by Taxman415a on 2008-08-25
If you write the script correctly this can be done in a bash or other shell script, in perl, sed, or awk. I don't know these off the top of my head to give you a script to do it, but you can google and you may be able to find one or someone seeing this may b able to find one.

Otherwise it's not exactly automatic, but it is very easy to use something like krename (use sudo aptitude install krename or synaptic if you like a gui instead of aptitude). Just run krename, add the files you want to rename then add a find/replace rule from JPG to jpg. I tested it and it works fine.

---

### Post by jpkotta on 2008-08-25
```
sudo aptitude install renameutils
```

```
rename s/JPG$/jpg/ *
```

There are similar utilities in some filemanagers.  I think thunar has one.  I like rename though.

If these are in several directories, you can use find, e.g.
```
find -type f -exec rename s/JPG$/jpg/ '{}' ';'
```
There are more efficient ways to implement this, but the above is easy and will most likely work.  Remember to back up the files first.

---

### Post by mssever on 2008-08-25
> **Roasted said:**
> Photobucket, MySpace, and several other sites don't pick up the jpg extension when it's in all caps. Is there some kind of a script I can run to automatically rename every SINGLE picture on my computer to be lowercase?

I have 15,000 pictures, so renaming each one is simply out of the question. I'd rather eat glass than do that.
I know there are mass renamers available. I think that Xfce or Xubuntu comes with one. If you want to write your own, it's pretty easy. Here's some untested code to type into the command line: ```
function recursiveRename {
  local dir="$1"
  for i in "$dir"/*; do
    if [ -d "$i" ]; then recursiveRename "$i"
    elif [[ $i =~ \.JPG$ ]]; then mv "$i" "${i/JPG/jpg}"
    fi
  done
}
recursiveRename /your/starting/directory
```

---

### Post by Roasted on 2008-08-28
I'd rather use a pre-existing application instead of doctoring up my own thing.

What is the best app to use for this?

---

### Post by Raffles10 on 2008-08-28
[pyRenamer]("http://www.infinicode.org/code/pyrenamer/") is a very good mass renaming utility for Gnome.

---

### Post by Taxman415a on 2008-08-28
The best is up to you. Try opening synaptic then search for rename. You'll get a lot of applications that you can try and pick the best one for you. jpkotta's code will work just fine though.

---

### Post by Roasted on 2008-08-28
Installed pyRenamer. Looks like a decent application.

Thing is, I get "could not rename" with every file I try.

In the pattern section, should I be setting .JPG and .jpg accordingly? I'm not really sure how to set this up properly...

---

### Post by ghostdog74 on 2008-09-16
> **Roasted said:**
> Installed pyRenamer. Looks like a decent application.

Thing is, I get "could not rename" with every file I try.

In the pattern section, should I be setting .JPG and .jpg accordingly? I'm not really sure how to set this up properly...

you want to rename every uppercase picture files to lowercase?
you can try the script [here](http://www.linuxquestions.org/linux/blog/ghostdog74/2008-09-13/Mass_File_Renamer_Changing_Cases_Upper_Lower)

eg usage

```

# touch UPPERCASE.JPEG
# ./script.sh -p ".*" -d "*.JPEG" 
mv -u "/tmp/UPPERCASE.JPEG" "/tmp/uppercase.jpeg"
# ./script.sh -p ".*" "*.JPEG" #remove -d to rename.


```

---

### Post by infinito on 2008-09-18
> **Roasted said:**
> Installed pyRenamer. Looks like a decent application.

Thing is, I get "could not rename" with every file I try.

In the pattern section, should I be setting .JPG and .jpg accordingly? I'm not really sure how to set this up properly...

With pyRenamer, for changing .JPG to .jpg, just go to the substitutions tab, select "Replace" and enter ".JPG" in first field, and ".jpg" in second. Then click "Preview", and if everythings look ok, then click "Rename".

Screenshot attached.

---

