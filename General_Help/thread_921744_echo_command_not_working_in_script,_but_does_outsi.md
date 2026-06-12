---
title: "echo command not working in script, but does outside?"
date: 2008-09-16
forum: General Help
---

### Post by starkes on 2008-09-16
Hi there.

I've been making a bash script to take in a bunch of information, read it into a maya file, convert the paths in it to UNIX paths, and send it out to the maya render command. Seems though, for the logging, I'm able to run the echo lines i use from the script below and they work, as long as they arent in the script.

The script is run by the www-data user (apache's user), but I've logged into the machine where the script resides as www-data and run the script and it produces no log files. Each individual line, when run from the terminal outside the script as the www-data user, works just fine. Also, the script is working well enough that along with some other stuff, it works as a web interface to submit render jobs and it is working, producing frames, so the script is running all the way through.

Any ideas?

also if someone could show me how to combine all those sed commands into one... i'm a noob at sed too! haha


```
!/bin/sh

# read in all the options from the user
show="$1"
episode="$2"
scene="$3"
framestart="$4"
frameend="$5"
framepath="/frames/$episode/$scene"
mayafilepath="$1linux.ma"

echo "$(date): Job Caught by $(hostname)" >> /db/PSIrender/jobs.log
echo "$(date): Job Added. Starting Conversion to UNIX paths..." >> /db/PSIrender/$(hostname).log
echo "Converting to linux paths..."

# Convert the paths to UNIX format
sed -e '/X:/s,X:/,/db/,g' "$1" > "$1linux2.ma"
sed -e '/x:/s,x:/,/db/,g' "$1linux2.ma" > "$1linux.ma"
sed -e '/Y:/s,Y:/,/asm/,g' "$1linux.ma" > "$1linux2.ma"
sed -e '/Y:/s,y:/,/asm/,g' "$1linux2.ma" > "$1linux.ma"
rm -rf "$1linux2.ma"

echo "$(date): Conversion complete. Starting Render..." >> /db/PSIrender/$(hostname).log

# Render the scene
echo "Starting render process..."
Render -n 0 -s "$framestart" -e "$frameend" -rd "$framepath" "$mayafilepath" > /db/PSIrender/$(hostname).maya.log

echo "$(date): Render Complete. Frames deposited in $framepath" >> /db/PSIrender/$(hostname).log
echo "$(date): Job completed by $(hostname)" >> /db/PSIrender/jobs.log
echo "Removing linux paths version of scene..."

# Remove the linux paths version of the file
rm -rf "$1linux.ma"

echo "Done."
exit 0
```

---

### Post by bodhi.zazen on 2008-09-16
I can not spot why the echo statements are not working.

As to the sed ... use a pipe

cat in.file | sed_1 | sed_2 | sed_3 | sed-4 > out.file

you can also edit a file directly with the -i switch

sed -i -e 's_old_new_g' file_2_edit

---

