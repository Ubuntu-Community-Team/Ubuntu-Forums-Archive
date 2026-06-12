---
title: "About searching file content"
date: 2008-07-26
forum: General Help
---

### Post by satimis on 2008-07-26
Hi folks,


What will be an easy and effective way searching file content?  E.G I need to find a WORD or a PHRASE on a file?  TIA


B.R.
satimis

---

### Post by caljohnsmith on 2008-07-26
You can use the "grep" command:
```
grep -i "word or phrase" /path/file
```
Note the -i flag makes the search case insensitive. Check "man grep" for more options if you like. :)

---

### Post by satimis on 2008-07-26
> **caljohnsmith said:**
> You can use the "grep" command:
```
grep -i "word or phrase" /path/file
```
Note the -i flag makes the search case insensitive. Check "man grep" for more options if you like. :)
Thanks for your advice.


If searching all files on drive what command shall I run?  TIA


B.R.
satimis

---

### Post by stevoo on 2008-07-26
ls | grep -i "word or phrase" 

should be the commnad

---

### Post by caljohnsmith on 2008-07-26
> **satimis said:**
> Thanks for your advice.


If searching all files on drive what command shall I run?  TIA


B.R.
satimis
You could use:
```
sudo grep -ri "word or phrase" /
```
That will recursively search through all directories, starting with the root directory, for "word or phrase" within all files, including files only viewable by root (or leave out the sudo in front if you don't want to look in files only viewed with root privileges).

---

### Post by ghostdog74 on 2008-07-26
> **stevoo said:**
> ls | grep -i "word or phrase" 

should be the commnad

the  more logical way to do it is through shell expansion. no need for grep
```

ls *word*

```

---

### Post by ghostdog74 on 2008-07-26
> **satimis said:**
> Hi folks,


What will be an easy and effective way searching file content?  E.G I need to find a WORD or a PHRASE on a file?  TIA


B.R.
satimis

some of the tools and techniques you can use to iterate files and search for patterns
1) egrep,fgrep, grep
2) awk eg
```

awk '/pattern/' file

```
3) bash while loop + read. eg 
```

while read line
do
 case "$line" in 
  word ) echo "found" ;;
 esac
done < file

```
see my sig for learn bash.

---

