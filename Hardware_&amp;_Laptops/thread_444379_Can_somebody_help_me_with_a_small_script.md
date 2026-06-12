---
title: "Can somebody help me with a small script?"
date: 2007-05-15
forum: Hardware &amp; Laptops
---

### Post by loathsome on 2007-05-15
Hi,

I finally found a way to adjust the brightness on my VAIO notebook :KS 
Basically, the brightness has eight levels, 1-8. This is how I adjust it:
```

[FONT="Fixedsys"]echo > 5 /proc/acpi/sony/brightness[/FONT]
```

Works flawlessy! But it can be a bother to input the command in the terminal every time I'm going to change the brightness, so I was wondering if anybody could tell me an easier way / write a small script or something?

Many, many thanks!

loathsome

---

### Post by KIAaze on 2007-05-15
I don't see any problems since you already know the command.
You could write a short script like this:
> echo > $1 /proc/acpi/sony/brightness

Here is a more complete script:
> #! /bin/bash

# Check if all parameters are present
# If no, exit
if [ $# -ne 1 ]
then
        echo
        echo "incorrect number of arguments"
        echo "usage :"
        echo "$0 <number between 1 and 8>"
        echo
        exit 0
fi

#check if level between 1 and 8
if [ $1 -lt 1 -o $1 -gt 8 ]
then
        echo
        echo "incorrect value for brightness"
        echo "usage :"
        echo "$0 <number between 1 and 8>"
        echo
        exit 0
fi

#change brightness
echo > $1 /proc/acpi/sony/brightness


Just save it with the name you would like to use as a command (ending with ".sh" is recommended) and then make it executable by doing:
```
chmod +x script.sh
```

Now place it either in "/usr/bin" (available for all users) or "~/bin" (only available to you).

If you place it in ~/bin, you'll have to add it to the PATH variable by doing:
```
export PATH=$PATH:~/bin
```

To renew the PATH variable automatically at every startup/login, just add the previous line at the end of the file ".bashrc"  which is in your home directory.

Note: To see what's in the PATH variable, do:
```
echo $PATH
```

---

