---
title: "Need Some Shell Help Bulk Renaming Files"
date: 2008-09-19
forum: General Help
---

### Post by DoctorDemento on 2008-09-19
I need some advise for a shell command or script to bulk rename filenames. My digital camera names files with the JPG extension capitalized, which creates big problems while coding web pages. So is there a simple way to rename all of these files with a lowercase jpg extension?

---

### Post by mb_webguy on 2008-09-19
If all of the files are in the same directory, you can use: ```
rename -v 's/\.JPG/\.jpg/' *.JPG
```

If they are in different directories, you'll have to use the following command from the topmost directory:```
find ./ -name *.JPG -exec rename -v 's/\.JPG/\.jpg/' {} \;
```

However, an easy way to rename large numbers of files is to use the GPRename program, which is an easy-to-use GUI batch file renaming utility.

---

### Post by ghostdog74 on 2008-09-19
> **DoctorDemento said:**
> I need some advise for a shell command or script to bulk rename filenames. My digital camera names files with the JPG extension capitalized, which creates big problems while coding web pages. So is there a simple way to rename all of these files with a lowercase jpg extension?

you can use the Python script [here](http://www.linuxquestions.org/linux/blog/ghostdog74/2008-09-17/Simple_Mass_File_Renamer_Deleter_Python)
eg usage

```

./filerenamer.py -p ".JPG" -e ".jpg" -l "*.JPG" #list only
./filerenamer.py -p ".JPG" -e ".jpg"  "*.JPG"  # remove -l to commit

```

or if you want to do it by hand
```

for files in *JPG
do
 mv "$files" "${files/JPG/jpg}"
done

```

---

### Post by DoctorDemento on 2008-09-19
Thank you, those both worked great.

---

### Post by OlaugeB on 2011-02-01
> **mb_webguy said:**
> However, an easy way to rename large numbers of files is to use the GPRename program, which is an easy-to-use GUI batch file renaming utility.

GPRename is excellent thank you!

---

