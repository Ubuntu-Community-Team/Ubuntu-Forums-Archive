---
title: "Bash Script Looping"
date: 2008-07-12
forum: General Help
---

### Post by shp on 2008-07-12
I wrote this script to convert videos for a phone. However it doesn't loop properly

```
while read file;
do
bfile=${file%.*}
echo Converting $file to $bfile.mp4
ffmpeg -i "$file" -y -s 320x240 "$bfile.mp4"
echo Converted;
done
```

Running with the ffmpeg part commented out it loops fine with a command like
```
find . -type f | grep avi | convertor
```

However with out the commenting it only converts one video before ending

---

