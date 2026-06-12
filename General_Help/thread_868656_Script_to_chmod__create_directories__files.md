---
title: "Script to chmod / create directories / files"
date: 2008-07-24
forum: General Help
---

### Post by mech7 on 2008-07-24
Hi Does anybody know how I can make a script to chmod certain dirs and files.. and create them if they don't exists relative from where I put the script?

---

### Post by justleen on 2008-07-24
find is your friend if you need to do something to specific files.

```
 find . -name filename -exec chmod a+rwx {} \; 
```
the {} stands for the found file. mind the \; at the end.

to test if a dir exists, use the -d in a test statement
```

 if [[ -d /path/to/test"$count" ]] ; then
            echo '/path/to/test'"$count"  'exists'

```

---

### Post by mech7 on 2008-07-25
Thanks I will try it out, and how can i create a dir or file when it does not exists :D

---

### Post by mech7 on 2008-07-25
Ummm another question... what language is this hehe :lolflag:

Also why doesn't something like this work:

```

$check = 'test';

if [ !-d $check ]; then
	echo $check 'Does not exists';
	mkdir $check;	
fi

```

Also where is the reference for this language? I would like to put some list of dirs and files in an array and let it go through a foreach loop.

---

### Post by mech7 on 2008-07-26
hehe ok i think i figured it out...

```

# Dirs 
dirs="upload upload/thumbs templates/templates_c templates/cache  admin/templates/cache admin/templates/templates_c";

# Files
files="access.log error.log"

for dir in ${dirs}
do
	if [ -d $dir ] 
	then
		# Dir exists CHMOD
		find . -samefile $dir -exec chmod a+rwx {} \;
	else
		# Dir not exists create and CHMOO
		mkdir -m 776 $dir;
		echo  $dir ' created';
	fi   
done


for file in ${files}
do
	if [ -f $file ]
	then
		# Create file
		chmod a+rwx $file;	
	else
		# Create file
		touch $file;
		chmod a+rwx $file;
		echo $file ' created';
	fi 
done

```

Too bad its a bit limited :(

---

### Post by ghostdog74 on 2008-07-26
you need to learn more. See my sig for learning bash

---

### Post by mech7 on 2008-07-27
> **ghostdog74 said:**
> you need to learn more. See my sig for learning bash

Ah thanks its helpfull... i was already looking if it was possible to have functions :D

---

### Post by mech7 on 2008-07-28
:confused:Mmm it works ok in ubuntu.. but in debian the webserver it tells me:

srv-webhost1:/var/www/_usr/chris/test_cms/public_html# sh ./install.sh
: command not found2:
: command not found3:
: command not found6:
'/install.sh: line 8: syntax error near unexpected token `do
'/install.sh: line 8: `do

----------------------------------------------

Edit aha it was because i created it on windows :p

---

