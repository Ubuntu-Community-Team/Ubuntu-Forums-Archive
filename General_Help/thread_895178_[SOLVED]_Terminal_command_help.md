---
title: "[SOLVED] Terminal command help"
date: 2008-08-19
forum: General Help
---

### Post by Piccy on 2008-08-19
I would like help with a terminal command that will output all files and sub directories to a text file.

I am not very familiar with Linux terminal command but have experience using DOS.

The DOS command would be eg
[FONT="Courier New"]DIR /s > c:\list.txt[/FONT]

I have no idea how to do this with Linux

I know [FONT="Courier New"]ls[/FONT] but how to get the output to a text file is unknown

---

### Post by Vivaldi Gloria on 2008-08-19
```

ls > list.txt
ls -R > list2.txt
```

The second one is recursive, i.e. lists also subfolders. Use >> if you want to add to the list.

See

```
man ls
```

for different forms of ls.

You can also use

```
find . > list.txt
```

to get a list of files in the current directory & its subdirectories.

Btw, find is a very powerful command. you can execute commands on the results with the -exec option. For example, the command

```
find /path/folder -name "*.mp3" -exec rm -f {} \;
```

deletes all the mp3 files in /path/folder & its subdirectories. See 

```
man find
```

for more info.

---

### Post by Cheesehead on 2008-08-19
```
ls > Desktop/file_list.txt
```

---

