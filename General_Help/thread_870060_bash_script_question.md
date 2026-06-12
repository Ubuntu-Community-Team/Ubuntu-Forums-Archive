---
title: "bash script question"
date: 2008-07-25
forum: General Help
---

### Post by Ohs0Ahxi on 2008-07-25
I've spent the afternoon playing with sed and awk and I've got a bash script which does what I want, but its hard coded to use one file. How could i change it so it will run all the commands in the script for every file ending in .js in the directory.

```
#!/bin/bash
## This needs to run for every .js in the directory
# Seperates Sections of File
awk '/^var NetCircles = {/,/^var NetPoints = {/' gpsdata.js > NetCircles.txt
awk '/^var NetPoints = {/,/^var Networks = {/' gpsdata.js > NetPoints.txt
awk '/^var Networks = {/,/^};/' gpsdata.js > Networks.txt

# Removes Unwanted Text
sed -i '/var NetCircles = {/ d' NetCircles.txt
sed -i '/};/ d' NetCircles.txt
sed -i '/var NetPoints = {/ d' NetCircles.txt
sed -i '/var NetPoints = {/ d' NetPoints.txt
sed -i '/};/ d' NetPoints.txt
sed -i '/var Networks = {/ d' NetPoints.txt
sed -i '/var Networks = {/ d' Networks.txt
sed -i '$s/..$//' Networks.txt

# Remvoes Blank Lines
sed -i '/^$/d' NetCircles.txt
sed -i '/^$/d' NetPoints.txt
sed -i '/^$/d' Networks.txt


##  Cat multiple files for the same section 
## This is run on the Combined sections
# Adds Required Text
sed -i '1i\var NetCircles = {' NetCircles.txt
sed -i '$a\};' NetCircles.txt
sed -i '1i\var NetPoints = {' NetPoints.txt
sed -i '$a\};' NetPoints.txt
sed -i '1i\var Networks = {' Networks.txt
sed -i '$a\};' Networks.txt

# Combines Files into gpsdata.js for use with google Maps
cat NetCircles.txt NetPoints.txt Networks.txt > gpsdata.js


```

Each .js file contains 3 sections of information, I want to take the info from all the .js files in the directory and put them into the relevant .txt files. 
e.g file1.js > file1NetCircles.txt, file1NetPoints.txt, file1Networks.txt
cat the .txts for the same sections
e.g cat file1NetCircles file2NetCircles etc >NetCircles.txt 
And add the header info for each section that was removed previously then cat those back into a .js which contains the info from all files

This is the first time I've written any script, so any help would be appreciated. My attempts at using loops were less than successful.

---

### Post by pauper on 2008-07-25
> How could i change it so it will run all the commands in the script for every 
file ending in .js in the directory.

Try this:

```
find /path/to/directory -name *.js | xargs /path/to/script
```

Is this for wardriving? :-$

---

### Post by Ohs0Ahxi on 2008-07-25
It's to use with..[_Kismet Google maps_]("http://parknation.com/gmap/index.php")
as it only produces a file with the most recent data, it doesn't append to existing files.

My trial and error approach is slowly paying off i now have 

```
#!/bin/bash
# Separates Sections of File
for file in *.js; do
awk '/^var NetCircles = {/,/^var NetPoints = {/' $file > $file.NetCircles.txt
awk '/^var NetPoints = {/,/^var Networks = {/' $file > $file.NetPoints.txt
awk '/^var Networks = {/,/^};/' $file > $file.Networks.txt

# Removes Unwanted Text
sed -i '/var NetCircles = {/ d' $file.NetCircles.txt
sed -i '/};/ d' $file.NetCircles.txt
sed -i '/var NetPoints = {/ d' $file.NetCircles.txt
sed -i '/var NetPoints = {/ d' $file.NetPoints.txt
sed -i '/};/ d' $file.NetPoints.txt
sed -i '/var Networks = {/ d' $file.NetPoints.txt
sed -i '/var Networks = {/ d' $file.Networks.txt
sed -i '$s/..$//' $file.Networks.txt

# Removes Blank Lines
sed -i '/^$/d' $file.NetCircles.txt
sed -i '/^$/d' $file.NetPoints.txt
sed -i '/^$/d' $file.Networks.txt

done

# Cat separate files
sed -i "s/$/,/g" *.NetCircles.txt
cat *.NetCircles.txt > NetCircles.txt
sed -i '$s/.$//' NetCircles.txt
cat *.NetPoints.txt > NetPoints.txt
sed -i 's/]/]\
,/' NetPoints.txt
sed -i '$s/.$//' NetPoints.txt
# might need to add , to last line
cat *.Networks.txt > Networks.txt

# Adds Required Text
sed -i '1i\var NetCircles = {' NetCircles.txt
sed -i '$a\};' NetCircles.txt
sed -i '1i\var NetPoints = {' NetPoints.txt
sed -i '$a\};' NetPoints.txt
sed -i '1i\var Networks = {' Networks.txt
sed -i '$a\};' Networks.txt

# Combines Files into gpsdata.js for use with google Maps
cat NetCircles.txt NetPoints.txt Networks.txt > newgpsdata.js

# Adds start location for map
sed -i '1i\var NetworkCenter = [50.431581,-4.942217];' newgpsdata.js

# Delete working files
rm *.txt
```

The only thing left i havent been able to figure out is every line in Networks.txt that begins with "'channel':" has to be set to end with "," but i havent managed it with awk or sed yet.


If you see anything wrong in what i have so far, or if i'm going about tackling the problem in the wrong way please let me know.

---

### Post by ghostdog74 on 2008-07-26
just awk. As you didn't provide samples of your js file, this is just snippet. Look at my sig for learning awk
```

awk '/^var NetCircles = {/,/^var NetPoints = {/ {
    gsub(/var NetCircles = {/,"") #substitute
    gsub(/}|{/,"")
    print $0 > "Netcircles.txt"
} 
/^var NetPoints = {/,/^var Networks = {/ {
    # do the same
    print $0 > "Netcircles.txt"
}
/^var Networks = {/,/^};/{
    # do the same
    print $0 > "Netcircles.txt"
}
' *.js

```

---

