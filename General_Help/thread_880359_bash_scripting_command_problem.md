---
title: "bash scripting command problem"
date: 2008-08-04
forum: General Help
---

### Post by uncannybuzzard on 2008-08-04
ok, so i can run this command on the command line just fine:

```
sed '1,/Season $season_/ d' $tmpfile | sed '1,/Season $(($season_ + 1))/ !d' | sed 's/Season $(($season_ + 1))//' | sed '/^$/ d'
```

it runs fine with actual values, or if i assign values to the variables. however, when i run it inside of a script. . . i.e.,

```
sed_=$(sed '1,/Season $season_/ d' $tmpfile | sed '1,/Season $(($season_ + 1))/ !d' | sed 's/Season $(($season_ + 1))//' | sed '/^$/ d')

$sed_

```

i get an error. any ideas?

---

### Post by koenn on 2008-08-05
> **uncannybuzzard said:**
> 
i get an error. any ideas?

which error ?

---

### Post by ghostdog74 on 2008-08-05
that's a messy one liner. Tell us what you are actually wanting to do. There are better ways to do it.

---

### Post by uncannybuzzard on 2008-08-05
i realized i could get away with just this:

```
sed '1,/Season $season_/ d' $tmpfile | sed '/^$/ d'
```

even still, now my script is now returning a blank value for the command, even at the command line.

here's the script in it's entirety(so far)
i have another script that will rename tv episode files for me, i thought i'd write something to automatically parse the webpage where i pull my titles from and merge the two.

```

#!/bin/bash

#VARIABLES

tmpFile=$RANDOM
tmpFile2=$RANDOM

read -p "URL of epguides.com page: " url
lynx -dump -nomargins $url > $tmpFile

read -p "Season (inclue '0' if single digit. i.e., '04'): " season

Season=$(echo $season | sed 's/^0//') #remove the '0' if present

#FUNCTIONS

remTmp ()
{
	#clean up temp files
	rm -rf $tmpFile $tmpFile2
}

#CODE

tmpResult=`sed '1,/Season $Season/ d' $tmpFile | sed '/^$/ d'`

echo $tmpResult

remTmp

exit 0

```

---

