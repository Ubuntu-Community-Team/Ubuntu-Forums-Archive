---
title: "Shreding"
date: 2008-08-03
forum: General Help
---

### Post by Uchiha_madara on 2008-08-03
I need to make shreding For The Drive , How?

---

### Post by bodhi.zazen on 2008-08-03
drive or files ?

For an entire drive, I like dban

[http://www.dban.org/](http://www.dban.org/)

for single files, try shred

---

### Post by dexter.deepak on 2008-08-03
for files, you can try this nautilus-script 
this will work in ubuntu. save this code in a file 
```
#!/bin/bash

if [[ -a /dev/urandom ]]; then
	randomizer=/dev/urandom;
elif [[ -a /dev/random ]]; then
	randomizer=/dev/random;
fi

echo $NAUTILUS_SCRIPT_SELECTED_URIS > ~/.gnome2/temp_shred_list

for file in $(cat ~/.gnome2/temp_shred_list); do

shortfile=$(echo $file | sed -e 's/\%20/\ /g' -e 's/.*\///g')

file_name=$(echo $file | sed -e 's/file:\/\///g' -e 's/\%20/\ /g')

zenity --question --title "Shredder" --text "Really shred $shortfile?"

if (( "$?" == 1 )) ; then
	exit
else
	if [[ $randomizer == "" ]]; then
		shred -u -z -n 50 "$file_name"
		if (( $? == 0 )); then
			zenity --info --text="$shortfile has been shred" --title "Success"
		else	zenity --info --text="$shortfile couldn't be shred" --title "Failure"
		fi
	else	shred -u -z -n 50 --random-source=$randomizer "$file_name"
		if (( $? == 0 )); then
			zenity --info --text="$shortfile has been shred" --title "Success"
		else	zenity --info --text="$shortfile couldn't be shred" --title "Failure"
		fi
	fi
fi;

done

rm -f ~/.gnome2/temp_shred_list

```
make it executable and place it in /home/dpak/.gnome2/nautilus-script/

PS : this isnt my script. i got it from gnome-look.org

---

