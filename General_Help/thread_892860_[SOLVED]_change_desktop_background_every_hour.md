---
title: "[SOLVED] change desktop background every hour?"
date: 2008-08-17
forum: General Help
---

### Post by shane2peru on 2008-08-17
Ok, I have found this thread, and it sort of does what I want, however I want to be able to add more background options, and this doesn't do that for me.  Here is the link:  [http://ubuntuforums.org/showthread.php?t=285271&highlight=change+background](http://ubuntuforums.org/showthread.php?t=285271&highlight=change+background)

I'm currently using this, but if someone knows of a better way to change the desktop background every hour to only selected backgrounds, I would love to hear it!  Thanks!

Shane

---

### Post by Krydahl on 2008-08-17
What precisely do you want? 

It is relatively easy to write a bash script that will change your wallpaper at designated intervals. I've seen several examples of this.

If you're after something even more sophisticated, I noticed this thread recently:

[http://ubuntuforums.org/showthread.php?t=888746](http://ubuntuforums.org/showthread.php?t=888746)

I haven't tried the package in question myself, it seemed rather like an overkill to me and I've already written my own script which meets my needs.

---

### Post by shane2peru on 2008-08-17
> **Krydahl said:**
> What precisely do you want? 

It is relatively easy to write a bash script that will change your wallpaper at designated intervals. I've seen several examples of this.

If you're after something even more sophisticated, I noticed this thread recently:

[http://ubuntuforums.org/showthread.php?t=888746](http://ubuntuforums.org/showthread.php?t=888746)

I haven't tried the package in question myself, it seemed rather like an overkill to me and I've already written my own script which meets my needs.

Krydahl,

Perhaps you could post your bash script for me so I can see it.  If it just takes randomly any picture from a specified folder that would be great for me.  The interval could be set at every half hour, or so.  I'm not too bad at bash scripts and would love to see what you have.  I can usually tweak stuff, though I'm not that great at originating it. :)  

Shane

---

### Post by easybake on 2008-08-17
Here is a way to do it with bash
[http://ubuntuforums.org/showpost.php?p=5176548&postcount=2]("http://ubuntuforums.org/showpost.php?p=5176548&postcount=2")


Its based on a 24 hour clock. It's pretty easy to change.


There is also this if you want to do it randomly. [http://www.djlosch.com/article_Code:_Bash_Script_to_Change_Gnome_Background_Randomly_(Ubuntu)]("http://www.djlosch.com/article_Code:_Bash_Script_to_Change_Gnome_Background_Randomly_(Ubuntu)")

---

### Post by shane2peru on 2008-08-17
> **easybake said:**
> Here is a way to do it with bash
[http://ubuntuforums.org/showpost.php?p=5176548&postcount=2]("http://ubuntuforums.org/showpost.php?p=5176548&postcount=2")


Its based on a 24 hour clock. It's pretty easy to change.


There is also this if you want to do it randomly. [http://www.djlosch.com/article_Code:_Bash_Script_to_Change_Gnome_Background_Randomly_(Ubuntu)]("http://www.djlosch.com/article_Code:_Bash_Script_to_Change_Gnome_Background_Randomly_(Ubuntu)")
Ahhh, that second one looks more like what I'm looking for!  I will have to give that one a try! Thanks.

Shane

---

### Post by Krydahl on 2008-08-17
OK, my solution has got a little convoluted and is spread across 4 separate scripts. These give me the capability to have the wallpaper change randomly after any number of minutes. Wallpapers are chosen either from a lists or from a specified directory. It also gives me a way to build up lists of wallpapers. This may all be more complex than you want, but you can look through them and pick the bits you like.

Basically, I have a hidden directory in my home directory which stores the current list of wallpapers I'm selecting from and also collections of favourites. The scripts below assume this directory exists (/home/username/.wallpaperchanger and also that there are two files in there .time and .current, which contain the interval after which you want the wallpaper to change and the list of current wallpapers.

The first script just reads these two files and uses them to change the wallpaper. I have it in my local in bin and autostart it on boot. I call it startwp and some of the other scripts call it. 

```
#!/bin/bash
# This script starts my wallpaper changer running. It assumes the files
# .current and .time exist

LIST_LOCATION=/home/username/.wallpaperchanger

while [ 1 ]
do
	TOTAL=`cat ${LIST_LOCATION}/.current | wc -l`
       ((LINE=RANDOM%TOTAL+1))
        WALLPAPER=`sed -n "$LINE"p ${LIST_LOCATION}/.current`
        time=`cat ${LIST_LOCATION}/.time`
        gconftool -t str -s /desktop/gnome/background/picture_filename "${WALLPAPER}"
        if [ "$time" = "" ]; then
                exit 0
        fi
        sleep ""$time"m"
done
```

The second script does most of the work - it allows me to manage which of a selection of lists (also stored in the .wallpaperchanger directory) I want to use at the moment, change the time interval, or look at the current pictures in a list. It assumes that there is a folder within the .wallpaperchanger folder called .viewfolder which is used during list viewing. I have this in a local bin and call it from a launcher usually.

```
#! /bin/bash

# This script is the main tool for managing my wallpaper changer. It prompts the user to select a list 
# of wallpapers or a timer interval between switches or a list to view all the pictures in. If the settings
# for the changer have been changed it starts/restarts startwp to pick up the new settings.

# This script does not create wallpaper lists. That is handled by a separate nautilus script addtolist

# If startwp is to run off a directory rather than a list, then there is a separate nautilus script 
# to manage this called wpfromdir

cd /home/username/.wallpaperchanger

# Prompt user to find out what he wants to do

DESIRED_OPTIONS=$(zenity  --list  --text "Do you want to..." --checklist  --column "Pick" --column "options" TRUE "select a list?" FALSE "change wallpaper interval?" FALSE "view a list" --separator=":") 

# See if we're changing the list (default action)

if echo $DESIRED_OPTIONS | grep -q "select a list"
then 
	FILES=$(ls -w 1)
	IFS="
	"
	CHOICE=$(zenity --list --text "Pick the wallpaper list you want to use" --column "" $FILES);

	if [ "$CHOICE" != "" ]
	then
		cp $CHOICE .current
	        let "RESTART = 0"
	fi

fi

# See if we're changing the timer interval

if echo $DESIRED_OPTIONS | grep -q "change wallpaper interval"
then 
	let "RESTART = 0"
	time=$(zenity --entry --text "Enter time, in minutes, between wallpaper changes" --entry-text "10")
	echo $time > .time
fi

# See if we want to look at a list

if echo $DESIRED_OPTIONS | grep -q "view a list"
then 

# Find the list we want to view

	FILES=$(ls -w 1)
	IFS="
	"
	CHOICE=$(zenity --list --text "Pick the wallpaper list you want to view" --column "" $FILES);

# Copy each file on the list into a temp directory

	LINE=$(cat "$CHOICE" | wc -l);

	while [ $LINE != "0" ]
	do
	
	PICTURE=`sed -n "$LINE"p "$CHOICE"`
	cp "$PICTURE" .viewfolder/.
	let "LINE -= 1"

	done

# Call Eye of Gnoe to view the files

	cd .viewfolder
	eog *.*

# Now we're done, get rid of the files

	rm *
fi

# Restart startwp to pick up the new settings if we've changed them.

if [ "$RESTART" = "0" ]
then

	PID=$(ps -A | grep startwp | awk '{print $1}');

	if [ "$PID" != "" ]
		then
			kill $PID
		fi

	startwp &
fi
```

If I just want to cycle round all the pictures in a directory, I use a third script that creates a list from that directory. It needs to be put in ~/.gnome2/nautilus_scripts. You can then right click on the directory that holds the pictures in nautilus, select the script name and it sets everything going.

```
#!/bin/bash
# This script uses a file/directory argument from nautilus to create a wallpaper list. It also restarts 
# my wallpaper changing program so that it will pick up the new settings.


LIST_LOCATION=/home/username/.wallpaperchanger

# Get the selected wallpapers into a list

WALLPAPER_LOCATION=`echo -n \$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS`

find "${WALLPAPER_LOCATION}" -iname '*.jp*g' -o -iname '*.png' > ${LIST_LOCATION}/.current

# Restart startwp

PID=$(ps -A | grep startwp | awk '{print $1}');

if [ "$PID" != "" ]
	then
		kill $PID
	fi

startwp &
```

My final script, also a nautilus one, adds a picture to one of my lists. Again, right click from nautilus.

```
#!/bin/bash

# This script adds a picture to a wallpaper selection list

#First, get ourselves into the paperchanger directory and find out what file we last added a picture to

cd /home/username/.wallpaperchanger

CHOICE=$(cat .filetomod)
FILETOMOD=$CHOICE

if [ "$FILETOMOD" != "" ]
then
	
# We have a file already specified, lets see if we want to use it.

	zenity --question --text "Do you want to add to current file ($FILETOMOD)?"
	if [ "$?" != "0" ]
	then
# No, we don't. Clear FILETOMOD.
		FILETOMOD=""
	fi
fi

# If FILETOMOD is null then we need to get a file.

if [ "$FILETOMOD" = "" ]
then
	FILES=$(ls -w 1)
	IFS="
	"
	CHOICE=$(zenity --list --text "Pick the wallpaper list you want to add to" --column "" "New File" $FILES);
	if [ "$CHOICE" = "New File" ]
	then		
		CHOICE=$(zenity --entry --text "Name of new file");		
		
	fi	
	FILETOMOD=$CHOICE
fi

# Now actually write to the file. Store the path name

WALLPAPER=`echo -n \$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS`
TEMP="$WALLPAPER/$arg"

# That leaves a slash at the end of the file name. Remove it.
# First get the number of characters in the string.

numofchar=`echo -n "$TEMP" | wc -c`
let "numofchar -= 1"    

# now cut off the last char
WALLPAPER=`echo -n "$TEMP" |cut -c -$numofchar`

# Now check this file isn't already in the selected list.

TEMP=$(cat "$FILETOMOD" | grep "$WALLPAPER");

if [ "$TEMP" != "" ]
then
#	It is - but maybe we want it more than once. Ask.

	zenity --question --text "File is already in list add it anyway?"
	if [ "$?" = "0" ]
	then
		TEMP=""
	fi
fi

if [ "$TEMP" = "" ]
then
	# Now write the new wallpaper to the file. 
	echo $WALLPAPER >> "$FILETOMOD"
fi	

# Update current file to be modified.

echo $FILETOMOD > .filetomod

```

I have to apologise that the coding is a little sloppy in places - I assume that the necessary directory structure and files already exist because I wrote it for my system not for others to use.

Hope this helps you build something that works for you.

---

### Post by shane2peru on 2008-08-17
> **Krydahl said:**
> OK, my solution has got a little convoluted and is spread across 4 separate scripts. These give me the capability to have the wallpaper change randomly after any number of minutes. Wallpapers are chosen either from a lists or from a specified directory. It also gives me a way to build up lists of wallpapers. This may all be more complex than you want, but you can look through them and pick the bits you like.

Basically, I have a hidden directory in my home directory which stores the current list of wallpapers I'm selecting from and also collections of favourites. The scripts below assume this directory exists (/home/username/.wallpaperchanger and also that there are two files in there .time and .current, which contain the interval after which you want the wallpaper to change and the list of current wallpapers.

**Cut out scripts**

I have to apologise that the coding is a little sloppy in places - I assume that the necessary directory structure and files already exist because I wrote it for my system not for others to use.

Hope this helps you build something that works for you.

Wow!  I must say I'm impressed!  I cannot script to that extent, but reading through all your scripts really helped me understand a lot!  That is super cool.  At first I thought I would just use the other one that is all in one, but then my curiosity got the best of me, and I have to (for my own learning sake) try to reproduce your setup, it is very nice.  I love the nautilus additions that you have made to make it easier to add pictures to the background list on the fly.  In all reality a simple script could be written to make all those directories, and "install"  your scripts, so that it could be used by anyone.  :)  Thanks for the time you took to post your scripts and explain.  I will be tinkering with them.

Shane

**EDIT:**  Ok, I came and conquered!  Thanks for the scripts that was really cool.  They worked well I only had to change my the directory listing /home/**username**/ and presto works like a charm!  really wasn't that hard to do, probably harder to write the scripting. :)  Thanks for sharing!

---

### Post by Krydahl on 2008-08-18
My pleasure. 

Yes, I probably could write some kind of install script. Not sure how much demand there is for this kind of thing though.

---

### Post by DoctorMO on 2008-08-31
> Yes, I probably could write some kind of install script. Not sure how much demand there is for this kind of thing though. 

Or... you could help me with my overkilled app that does what this person wanted. Interesting that mashing scripts was chosen over a deb.

---

### Post by Krydahl on 2008-08-31
> **DoctorMO said:**
> Or... you could help me with my overkilled app that does what this person wanted. Interesting that mashing scripts was chosen over a deb.

Sorry, didn't mean any offence by "overkill" - it just does more I wanted (not interested in getting wallpaper automatically from rss feeds).

I wrote a script myself partly for the practice and mostly because I wasn't aware of an alternative at the time. I did point the OP at your deb first - but he asked about my script so it only seemed polite to share. Why he chose that route over your deb, I couldn't say.

Not sure what help I could offer with your app - especially since I don't know python.

---

### Post by DoctorMO on 2008-08-31
> Not sure what help I could offer with your app - especially since I don't know python.

Not sure, it depends if there was anything your code did that mine didn't. Ultimately the cron handling and general managed by debness of it makes it better than scripts. I know because my first revision was a script if you look at the history.

---

### Post by Krydahl on 2008-08-31
Yeah, my script just sleeps. Cron would be a better solution in many ways but I couldn't see how to do it without losing some flexibility/accuracy when altering the interval between wallpaper changes.

You're welcome to look through the script and use any ideas you like. 

The main capability my set up has that yours didn't obviously do (though I haven't looked at it in detail) is to allow you to put together selections of wallpapers - a little like creating an album in something like gthumb - and rotate round those. This allows me to have collections of wallpapers that fit with different themes without having to store them in separate directories and possibly have to have the same wallpaper in two different directories if I wanted it in two separate collections.

---

### Post by DoctorMO on 2008-08-31
That is interesting, linking into galleries and such so you can list through those. I'll consider adding that.

---

